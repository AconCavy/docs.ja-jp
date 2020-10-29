---
title: SYSLIB0001 警告
description: コンパイル時の警告 SYSLIB0001 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 58c16879b7d91598ea0848bb0ba95f8fa0200cfe
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333137"
---
# <a name="syslib0001-the-utf-7-encoding-is-insecure"></a>SYSLIB0001: UTF-7 エンコードは安全ではない

UTF-7 エンコードがアプリケーション間で広く使用されることはなくなりました。多くの仕様では、現在インターチェンジでの[使用が禁止されています](https://security.stackexchange.com/a/68609/3573)。 また、UTF-7 でエンコードされたデータの使用を予測していないアプリケーションでは、[攻撃ベクトルとして使用される](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7)こともあります。 Microsoft では、<xref:System.Text.UTF7Encoding?displayProperty=nameWithType> の使用に対して警告が行われます。エラー検出が提供されないためです。

そのため、.NET 5.0 以降、次の API は古いものとしてマークさていれます。 これらの API を使用すると、コンパイル時に警告 `SYSLIB0001` が生成されます。

- <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> プロパティ
- <xref:System.Text.UTF7Encoding.%23ctor%2A> コンストラクター

## <a name="workarounds"></a>回避策

- 独自のプロトコルまたはファイル形式内で <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> または <xref:System.Text.UTF7Encoding> を使用している場合:

  <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> または <xref:System.Text.UTF8Encoding> の使用に切り替えます。 UTF-8 は業界標準であり、各言語、オペレーティング システム、およびランタイム間で広くサポートされています。 UTF-8 を使用すると、将来のコードの保守が容易になり、エコシステムの他の部分との相互運用性が高まります。

- <xref:System.Text.Encoding> インスタンスを <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> と比較している場合:

  代わりに、既知の UTF-7 コード ページ (`65000`) に対してチェックを実行することを検討してください。 コード ページと比較することによって、警告を回避し、一部のエッジ ケースを処理することもできます。たとえば、他のユーザーが `new UTF7Encoding()` を呼び出した場合や、型をサブクラス化した場合などです。

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

## <a name="see-also"></a>関連項目

- [UTF-7 コード パスが古い形式に](3.1-5.0.md#utf-7-code-paths-are-obsolete)
