---
title: ETW を使用した分析トレース
ms.date: 03/30/2017
helpviewer_keywords:
- diagnostics [WCF], analytic tracing
- administration [WCF], analytic tracing
- analytic tracing [WCF]
ms.assetid: 1d518e47-a38d-41e8-93d7-8c3b361f6a56
ms.openlocfilehash: 4bb31eeac7c5d3c8c30f66090b07de9f8af4d5a4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274622"
---
# <a name="analytic-tracing-with-etw"></a>ETW を使用した分析トレース

Windows Communication Foundation (WCF) 分析トレースには、WCF サービスの実行中に診断情報をキャプチャする方法が用意されています。 Wcf 分析トレースイベントは、運用環境での WCF サービスのトラブルシューティングを可能にするために、WCF スタックの主要なポイントで生成されます。 WCF サービスの分析トレースは、wcf サービスをホストする製品サーバーのパフォーマンスにほとんど影響を与え [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] ません。これらのイベントは、Windows イベントトレーシング (ETW) セッションに非常に効率的に出力されるためです。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [分析トレースの概要](analytic-tracing-overview.md)  
 での WCF 分析トレースの動作について説明 [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] します。  
  
 [分析トレースの動的な有効化](dynamically-enabling-analytic-tracing.md)  
 ETW を使用してトレースを動的に有効化または無効化する方法について説明します。  
  
 [メッセージ フローのトレースの構成](configuring-message-flow-tracing.md)  
 メッセージ フローのトレースを構成する方法について説明します。  
  
 [分析トレース イベント リファレンス](analytic-trace-event-reference.md)  
 イベント ID とそれらのイベント レベル、イベント メッセージ、およびキーワードを表で示します。  
  
## <a name="see-also"></a>関連項目

- [WCF サービスと Event Tracing for Windows](../../samples/wcf-services-and-event-tracing-for-windows.md)
- [Windows のイベント トレースへの追跡イベント](../../../windows-workflow-foundation/samples/tracking-events-into-event-tracing-in-windows.md)
