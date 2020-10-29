---
title: SYSLIB0010 警告
description: コンパイル時の警告 SYSLIB0010 が生成される旧型式について説明します。
ms.topic: reference
ms.date: 10/20/2020
ms.openlocfilehash: dcd331aa5c68381ea29848bc54ee4b1a5e75330d
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333075"
---
# <a name="syslib0010-unsupported-remoting-apis"></a>SYSLIB0010:サポートされていないリモート処理 API

[.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))は従来のテクノロジであり、インフラストラクチャは .NET Framework にのみ存在します。 .NET 5.0 以降、次のリモート処理関連の API は古いものとしてマークされています。 これらをコードで使用すると、コンパイル時に警告 `SYSLIB0010` が生成されます。

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType>

## <a name="workaround"></a>回避策

他のアプリケーションの、または複数のコンピューターのオブジェクトと通信する場合は、WCF または HTTP ベースの REST サービスの使用を検討してください。 詳細については、[.NET Core で使用できない .NET Framework テクノロジ](../porting/net-framework-tech-unavailable.md)に関するページを参照してください。

## <a name="see-also"></a>関連項目

- [.NET リモート処理](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71))
