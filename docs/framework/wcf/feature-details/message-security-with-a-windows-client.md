---
title: Windows クライアントとのメッセージ セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 01e7d0b8-10f9-45c3-a4c5-53d44dc61eb8
ms.openlocfilehash: bcfeb5f863b1dd6cf9171a7fc53c8984ea68ecb3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184625"
---
# <a name="message-security-with-a-windows-client"></a><span data-ttu-id="6ca12-102">Windows クライアントとのメッセージ セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6ca12-102">Message Security with a Windows Client</span></span>
<span data-ttu-id="6ca12-103">このシナリオでは、メッセージ セキュリティ モードによってセキュリティで保護された Windows 通信基盤 (WCF) クライアントとサーバーを示します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-103">This scenario shows a Windows Communication Foundation (WCF) client and server secured by message security mode.</span></span> <span data-ttu-id="6ca12-104">クライアントとサービスは、Windows 資格情報を使用して認証します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-104">The client and service are authenticated using Windows credentials.</span></span>  
  
 <span data-ttu-id="6ca12-105">![Windows クライアントによるメッセージ セキュリティ](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span><span class="sxs-lookup"><span data-stu-id="6ca12-105">![Message security with a Windows client](../../../../docs/framework/wcf/feature-details/media/1c8618d4-0005-4022-beb6-32fd087a8c3c.gif "1c8618d4-0005-4022-beb6-32fd087a8c3c")</span></span>  
  
|<span data-ttu-id="6ca12-106">特徴</span><span class="sxs-lookup"><span data-stu-id="6ca12-106">Characteristic</span></span>|<span data-ttu-id="6ca12-107">説明</span><span class="sxs-lookup"><span data-stu-id="6ca12-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="6ca12-108">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="6ca12-108">Security Mode</span></span>|<span data-ttu-id="6ca12-109">Message</span><span class="sxs-lookup"><span data-stu-id="6ca12-109">Message</span></span>|  
|<span data-ttu-id="6ca12-110">相互運用性</span><span class="sxs-lookup"><span data-stu-id="6ca12-110">Interoperability</span></span>|<span data-ttu-id="6ca12-111">WCF のみ</span><span class="sxs-lookup"><span data-stu-id="6ca12-111">WCF Only</span></span>|  
|<span data-ttu-id="6ca12-112">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="6ca12-112">Authentication (Server)</span></span>|<span data-ttu-id="6ca12-113">サーバーとクライアントの相互認証</span><span class="sxs-lookup"><span data-stu-id="6ca12-113">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="6ca12-114">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="6ca12-114">Authentication (Client)</span></span>|<span data-ttu-id="6ca12-115">サーバーとクライアントの相互認証</span><span class="sxs-lookup"><span data-stu-id="6ca12-115">Mutual authentication of the server and client</span></span>|  
|<span data-ttu-id="6ca12-116">整合性</span><span class="sxs-lookup"><span data-stu-id="6ca12-116">Integrity</span></span>|<span data-ttu-id="6ca12-117">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="6ca12-117">Yes, using shared security context</span></span>|  
|<span data-ttu-id="6ca12-118">機密情報</span><span class="sxs-lookup"><span data-stu-id="6ca12-118">Confidentiality</span></span>|<span data-ttu-id="6ca12-119">はい、共有のセキュリティ コンテキストを使用します</span><span class="sxs-lookup"><span data-stu-id="6ca12-119">Yes, using shared security context</span></span>|  
|<span data-ttu-id="6ca12-120">トランスポート</span><span class="sxs-lookup"><span data-stu-id="6ca12-120">Transport</span></span>|<span data-ttu-id="6ca12-121">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="6ca12-121">NET.TCP</span></span>|  
|<span data-ttu-id="6ca12-122">バインド</span><span class="sxs-lookup"><span data-stu-id="6ca12-122">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="6ca12-123">サービス</span><span class="sxs-lookup"><span data-stu-id="6ca12-123">Service</span></span>  
 <span data-ttu-id="6ca12-124">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-124">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="6ca12-125">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6ca12-125">Do one of the following:</span></span>  
  
- <span data-ttu-id="6ca12-126">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-126">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="6ca12-127">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="6ca12-127">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="6ca12-128">コード</span><span class="sxs-lookup"><span data-stu-id="6ca12-128">Code</span></span>  
 <span data-ttu-id="6ca12-129">次のコードでは、メッセージ セキュリティを使用するサービス エンドポイントを作成し、Windows コンピューターとの間にセキュリティで保護されたコンテキストを確立する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-129">The following code shows how to create a service endpoint that uses message security to establish a secure context with a Windows machine.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#11)]
 [!code-vb[C_SecurityScenarios#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#11)]  
  
### <a name="configuration"></a><span data-ttu-id="6ca12-130">構成</span><span class="sxs-lookup"><span data-stu-id="6ca12-130">Configuration</span></span>  
 <span data-ttu-id="6ca12-131">コードの代わりに次の構成を使用して、サービスをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="6ca12-131">The following configuration can be used instead of the code to set up the service:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration=""  
               name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"  
                  binding="netTcpBinding"  
                  bindingConfiguration="Windows"  
                  name="WindowsOverMessage"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="Windows">  
          <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="6ca12-132">Client</span><span class="sxs-lookup"><span data-stu-id="6ca12-132">Client</span></span>  
 <span data-ttu-id="6ca12-133">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-133">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="6ca12-134">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="6ca12-134">Do one of the following:</span></span>  
  
- <span data-ttu-id="6ca12-135">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-135">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="6ca12-136">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-136">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="6ca12-137">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-137">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="6ca12-138">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-138">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="6ca12-139">コード</span><span class="sxs-lookup"><span data-stu-id="6ca12-139">Code</span></span>  
 <span data-ttu-id="6ca12-140">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-140">The following code creates a client.</span></span> <span data-ttu-id="6ca12-141">バインディングはメッセージ モード セキュリティに対して行い、クライアント資格情報の種類は `Windows` に設定します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-141">The binding is to Message mode security, and the client credential type is set to `Windows`.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#18](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#18)]
 [!code-vb[C_SecurityScenarios#18](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#18)]  
  
### <a name="configuration"></a><span data-ttu-id="6ca12-142">構成</span><span class="sxs-lookup"><span data-stu-id="6ca12-142">Configuration</span></span>  
 <span data-ttu-id="6ca12-143">次の構成を使用してクライアントのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6ca12-143">The following configuration is used to set the client properties.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
         <security mode="Message">  
            <message clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://machineName:8008/Calculator"
                binding="netTcpBinding"  
                bindingConfiguration="NetTcpBinding_ICalculator"  
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6ca12-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ca12-144">See also</span></span>

- [<span data-ttu-id="6ca12-145">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="6ca12-145">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="6ca12-146">[Windows Server AppFabric のセキュリティ モデル](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="6ca12-146">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
