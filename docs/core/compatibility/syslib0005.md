---
title: SYSLIB0005 警告
description: コンパイル時の警告 SYSLIB0005 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: 8a9893d81c781335014c8b970c460b5a4241ed18
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333128"
---
# <a name="syslib0005-the-global-assembly-cache-gac-is-not-supported"></a>SYSLIB0005: グローバル アセンブリ キャッシュ (GAC) はサポートされていません

.NET Core および .NET 5.0 以降のバージョンでは、.NET Framework に存在していたグローバル アセンブリ キャッシュ (GAC) の概念がなくなりました。 開発者がこれらの API を使用しないようにするために、.NET 5.0 以降、一部の GAC 関連の API は古いものとしてマークされています。 これらの API を使用すると、コンパイル時に警告 `SYSLIB0005` が生成されます。

次の GAC 関連の API は古いものとしてマークされています。

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType>

  ライブラリとアプリで実行時の動作を決定するために <xref:System.Reflection.Assembly.GlobalAssemblyCache> API を使用することはできません。これは、.NET Core および .NET 5 以降では常に `false` が返されるためです。

## <a name="workaround"></a>回避策

アプリケーションによって <xref:System.Reflection.Assembly.GlobalAssemblyCache> プロパティのクエリが実行される場合は、呼び出しを削除することを検討してください。 <xref:System.Reflection.Assembly.GlobalAssemblyCache> 値を使用して、実行時に "GAC のアセンブリ" フローと "GAC に存在しないアセンブリ" フローのどちらかを選択する場合は、フローが .NET 5 以降のアプリケーションで引き続き意味を持つかどうかを再検討してください。

## <a name="see-also"></a>関連項目

- [グローバル アセンブリ キャッシュ](../../framework/app-domains/gac.md)
