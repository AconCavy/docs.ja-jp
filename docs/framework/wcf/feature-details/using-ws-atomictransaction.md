---
title: WS-AtomicTransaction の使用
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: e01f5b683bebe1f4cdf282c56aa3049b6da794ee
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637473"
---
# <a name="using-ws-atomictransaction"></a>WS-AtomicTransaction の使用
WS-AtomicTransaction (WS-AT) は、相互運用が可能なトランザクション プロトコルです。 Web サービス メッセージを使用して分散トランザクションをフローできるようにすると共に、異種のトランザクション インフラストラクチャ間で相互運用できるように調整します。 WS-AT では、2 フェーズ コミット プロトコルを使用して、分散アプリケーション、トランザクション マネージャー、およびリソース マネージャー間でアトミックな結果を実現します。  
  
 Windows Communication Foundation (WCF) は、WS-AT 実装には、Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクション マネージャーに組み込まれたプロトコル サービスが含まれます。 WCF アプリケーションは、WS-AT を使用して、サード パーティのテクノロジを使用して構築された Web サービスの相互運用可能ななど、他のアプリケーションにトランザクションをフローできます。  
  
 クライアント アプリケーションとサーバー アプリケーション間でトランザクションをフローさせるときに使用されるトランザクション プロトコルは、クライアントが選択したエンドポイントでサーバーが公開するバインディングによって決定されます。 指定することによって WCF システム指定のバインディングの既定、 `OleTransactions` WS-AT を指定する既定の他のユーザーに、トランザクションの伝達形式としてプロトコル。 特定のバインディング内部でのトランザクション プロトコルの選択は、プログラムによって変更することもできます。  
  
 プロトコルの選択は、次の内容に影響を与えます。  
  
- トランザクションをクライアントからサーバーにフローさせるために使用されるメッセージ ヘッダーの形式。  
  
- トランザクションの結果を解決するために、クライアントのトランザクション マネージャーとサーバーのトランザクション マネージャーの間で 2 フェーズ コミット プロトコルを実行するために使用されるネットワーク プロトコル。  
  
 場合は、サーバーとクライアントは、WCF を使用して記述されて、WS-AT を使用する必要はありません。 その代わりに、`NetTcpBinding` プロトコルを使用する `TransactionFlow` 属性を有効にして `OleTransactions` の既定の設定を使用できます。 詳細については、次を参照してください。 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)します。 ただし、サードパーティのテクノロジで構築された Web サービスにトランザクションをフローさせる場合は、WS-AT を使用する必要があります。  
  
## <a name="see-also"></a>関連項目

- [WS-AtomicTransaction サポートの構成](../../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
