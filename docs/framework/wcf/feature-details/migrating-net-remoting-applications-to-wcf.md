---
title: .NET リモート処理アプリケーションの WCF への移行
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 2cfaebd064d10e5b331412d177929ecb20117a07
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248215"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>.NET リモート処理アプリケーションの WCF への移行

**このトピックは、既存のアプリケーションとの下位互換性を維持するために残されているレガシテクノロジに固有のものであり、新規開発にはお勧めしません。これで、分散アプリケーションを WCF を使用して開発する必要があります。**  
  
 既存の .NET リモート処理アプリケーションで WCF を利用するには、統合と移行という2つの方法があります。 統合を使用すると、.NET リモート処理2.0 と WCF を並行して実行できるため、既存の .NET リモート処理2.0 コードを変更しなくても、両方のテクノロジで同じビジネスオブジェクトを同時に公開できます。 統合を行うには .NET Framework 2.0 以上で実行している必要があります。 WCF 機能を利用し、リモート処理2.0 システムとのワイヤ互換性を必要としない場合は、サービス全体を WCF に移行することができます。 .NET リモート処理2.0 から WCF への移行では、リモートオブジェクトのインターフェイスとその構成設定を変更する必要があります。 これらのトピックはどちらも [、「リモート処理から Windows Communication Foundation へ](/previous-versions/aa730857(v=vs.80))」で説明されています。  
  
## <a name="see-also"></a>関連項目

- [概念の概要](../conceptual-overview.md)
