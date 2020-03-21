---
title: ServiceModel トランザクションの構成
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 79772d19ddaec041aa1fac936b9951731507b6e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184450"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="407c0-102">ServiceModel トランザクションの構成</span><span class="sxs-lookup"><span data-stu-id="407c0-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="407c0-103">Wcf (WCF) には、サービスのトランザクションを構成するための 3 つの`transactionFlow`属性`transactionProtocol`があります`transactionTimeout`。</span><span class="sxs-lookup"><span data-stu-id="407c0-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="407c0-104">transactionFlow の構成</span><span class="sxs-lookup"><span data-stu-id="407c0-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="407c0-105">WCF が提供する定義済みバインドのほとんどには`transactionFlow`、`transactionProtocol`属性が含まれているので、特定のトランザクション フロー プロトコルを使用して特定のエンドポイントの受信トランザクションを受け入れるようにバインドを構成できます。</span><span class="sxs-lookup"><span data-stu-id="407c0-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="407c0-106">さらに、`transactionFlow` 要素とその `transactionProtocol` 属性を使用して、ユーザー独自のカスタム バインドを構築できます。</span><span class="sxs-lookup"><span data-stu-id="407c0-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="407c0-107">構成要素の設定の詳細については、「 [ \<>のバインド](../../configure-apps/file-schema/wcf/bindings.md)と[WCF 構成スキーマ](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="407c0-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="407c0-108">`transactionFlow` 属性は、バインディングを使用するサービス エンドポイントに対してトランザクション フローを有効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="407c0-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="407c0-109">transactionProtocol の構成</span><span class="sxs-lookup"><span data-stu-id="407c0-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="407c0-110">`transactionProtocol` 属性は、バインディングを使用するサービス エンドポイントで使用されるトランザクション プロトコルを指定します。</span><span class="sxs-lookup"><span data-stu-id="407c0-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="407c0-111">以下に、指定したバインディングがトランザクション フローをサポートし、WS-AtomicTransaction プロトコルを使用するように構成する構成セクションの例を示します。</span><span class="sxs-lookup"><span data-stu-id="407c0-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="407c0-112">transactionTimeout の構成</span><span class="sxs-lookup"><span data-stu-id="407c0-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="407c0-113">構成ファイルの`transactionTimeout`要素で、WCF サービスの`behavior`属性を構成できます。</span><span class="sxs-lookup"><span data-stu-id="407c0-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="407c0-114">次のコードでは、この設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="407c0-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="407c0-115">`transactionTimeout` 属性は、サービスで作成された新しいトランザクションを完了させる期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="407c0-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="407c0-116">この属性は、新しいトランザクションを確立するすべての操作の <xref:System.Transactions.TransactionScope> タイムアウトとして使用され、<xref:System.ServiceModel.OperationBehaviorAttribute> が適用されている場合、<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> プロパティは `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="407c0-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="407c0-117">このタイムアウトは、2 フェーズ コミット プロトコルにおける、トランザクションの作成からフェーズ 1 の完了までの期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="407c0-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="407c0-118">この属性を `service` 構成セクション内に設定する場合は、対応するサービスの 1 つ以上のメソッドで、<xref:System.ServiceModel.OperationBehaviorAttribute> プロパティが <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> に設定された `true` を適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="407c0-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="407c0-119">使用されるタイムアウト値は常に、この `transactionTimeout` 構成設定と <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> プロパティの小さい方の値になります。</span><span class="sxs-lookup"><span data-stu-id="407c0-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="407c0-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="407c0-120">See also</span></span>

- [<span data-ttu-id="407c0-121">\<バインド></span><span class="sxs-lookup"><span data-stu-id="407c0-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="407c0-122">WCF 構成スキーマ</span><span class="sxs-lookup"><span data-stu-id="407c0-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
