---
title: WS-AtomicTransaction の使用
ms.date: 03/30/2017
helpviewer_keywords:
- WS-AT protocol [WCF]
ms.assetid: 04a4c200-0af0-4c5d-a3d9-87cb7339e054
ms.openlocfilehash: 71090efbb096bc3b7b3d6bcf40ff496b78ac6252
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600686"
---
# <a name="using-ws-atomictransaction"></a><span data-ttu-id="8d55b-102">WS-AtomicTransaction の使用</span><span class="sxs-lookup"><span data-stu-id="8d55b-102">Using WS-AtomicTransaction</span></span>
<span data-ttu-id="8d55b-103">WS-AtomicTransaction (WS-AT) は、相互運用が可能なトランザクション プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="8d55b-103">WS-AtomicTransaction (WS-AT) is an interoperable transaction protocol.</span></span> <span data-ttu-id="8d55b-104">Web サービス メッセージを使用して分散トランザクションをフローできるようにすると共に、異種のトランザクション インフラストラクチャ間で相互運用できるように調整します。</span><span class="sxs-lookup"><span data-stu-id="8d55b-104">It enables you to flow distributed transactions by using Web service messages, and coordinate in an interoperable manner between heterogeneous transaction infrastructures.</span></span> <span data-ttu-id="8d55b-105">WS-AT では、2 フェーズ コミット プロトコルを使用して、分散アプリケーション、トランザクション マネージャー、およびリソース マネージャー間でアトミックな結果を実現します。</span><span class="sxs-lookup"><span data-stu-id="8d55b-105">WS-AT uses the two-phase commit protocol to drive an atomic outcome between distributed applications, transaction managers, and resource managers.</span></span>  
  
 <span data-ttu-id="8d55b-106">WS-AT 実装 Windows Communication Foundation (WCF) には、Microsoft 分散トランザクションコーディネーター (MSDTC) トランザクションマネージャーに組み込まれているプロトコルサービスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="8d55b-106">The WS-AT implementation Windows Communication Foundation (WCF) provides includes a protocol service built into the Microsoft Distributed Transaction Coordinator (MSDTC) transaction manager.</span></span> <span data-ttu-id="8d55b-107">WS-AT を使用すると、WCF アプリケーションは、サードパーティのテクノロジを使用して構築された相互運用可能な Web サービスを含む、他のアプリケーションにトランザクションをフローさせることができます。</span><span class="sxs-lookup"><span data-stu-id="8d55b-107">Using WS-AT, WCF applications can flow transactions to other applications, including interoperable Web services built using third-party technology.</span></span>  
  
 <span data-ttu-id="8d55b-108">クライアント アプリケーションとサーバー アプリケーション間でトランザクションをフローさせるときに使用されるトランザクション プロトコルは、クライアントが選択したエンドポイントでサーバーが公開するバインディングによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="8d55b-108">When flowing a transaction between a client application and a server application, the transaction protocol used is determined by the binding that the server exposes on the endpoint the client selected.</span></span> <span data-ttu-id="8d55b-109">WCF システム指定のバインディングの中には、既定では、 `OleTransactions` プロトコルをトランザクションの伝達形式として指定するものと、ws-at を指定するものがあります。</span><span class="sxs-lookup"><span data-stu-id="8d55b-109">Some WCF system-provided bindings default to specifying the `OleTransactions` protocol as the transaction propagation format, while others default to specifying WS-AT.</span></span> <span data-ttu-id="8d55b-110">特定のバインディング内部でのトランザクション プロトコルの選択は、プログラムによって変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="8d55b-110">You can also programmatically modify the choice of transaction protocol inside a given binding.</span></span>  
  
 <span data-ttu-id="8d55b-111">プロトコルの選択は、次の内容に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="8d55b-111">The choice of protocol influences:</span></span>  
  
- <span data-ttu-id="8d55b-112">トランザクションをクライアントからサーバーにフローさせるために使用されるメッセージ ヘッダーの形式。</span><span class="sxs-lookup"><span data-stu-id="8d55b-112">The format of the message headers used to flow the transaction from client to server.</span></span>  
  
- <span data-ttu-id="8d55b-113">トランザクションの結果を解決するために、クライアントのトランザクション マネージャーとサーバーのトランザクション マネージャーの間で 2 フェーズ コミット プロトコルを実行するために使用されるネットワーク プロトコル。</span><span class="sxs-lookup"><span data-stu-id="8d55b-113">The network protocol used to run the two-phase commit protocol between the client's transaction manager and the server's transaction, in order to resolve the outcome of the transaction.</span></span>  
  
 <span data-ttu-id="8d55b-114">サーバーとクライアントが WCF を使用して記述されている場合は、WS-AT を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="8d55b-114">If the server and client are written using WCF, you do not need to use WS-AT.</span></span> <span data-ttu-id="8d55b-115">その代わりに、`NetTcpBinding` プロトコルを使用する `TransactionFlow` 属性を有効にして `OleTransactions` の既定の設定を使用できます。</span><span class="sxs-lookup"><span data-stu-id="8d55b-115">Instead, you can use the default settings of `NetTcpBinding` with the `TransactionFlow` attribute enabled, which will use the `OleTransactions` protocol instead.</span></span> <span data-ttu-id="8d55b-116">詳細については、「[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d55b-116">For more information, see [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md).</span></span> <span data-ttu-id="8d55b-117">ただし、サードパーティのテクノロジで構築された Web サービスにトランザクションをフローさせる場合は、WS-AT を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d55b-117">Otherwise, if you are flowing transactions to Web services built on third-party technologies, you must use WS-AT.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d55b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d55b-118">See also</span></span>

- [<span data-ttu-id="8d55b-119">WS-AtomicTransaction サポートの構成</span><span class="sxs-lookup"><span data-stu-id="8d55b-119">Configuring WS-Atomic Transaction Support</span></span>](configuring-ws-atomic-transaction-support.md)
