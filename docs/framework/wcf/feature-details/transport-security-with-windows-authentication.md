---
title: トランスポート セキュリティと Windows 認証
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
ms.openlocfilehash: 6392ea0f17596406a8671a039bd78777d9e11e42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742649"
---
# <a name="transport-security-with-windows-authentication"></a><span data-ttu-id="e5fd9-102">トランスポート セキュリティと Windows 認証</span><span class="sxs-lookup"><span data-stu-id="e5fd9-102">Transport Security with Windows Authentication</span></span>
<span data-ttu-id="e5fd9-103">次のシナリオは、Windows セキュリティによって保護された Windows Communication Foundation (WCF) クライアントとサービスを示しています。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-103">The following scenario shows a Windows Communication Foundation (WCF) client and service secured by Windows security.</span></span> <span data-ttu-id="e5fd9-104">プログラミングの詳細については、「[方法: Windows 資格情報を使用してサービスをセキュリティで保護](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-104">For more information about programming, see [How to: Secure a Service with Windows Credentials](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md).</span></span>  
  
 <span data-ttu-id="e5fd9-105">イントラネットの Web サービスでは人事情報を表示しています。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-105">An intranet Web service displays human resources information.</span></span> <span data-ttu-id="e5fd9-106">クライアントは Windows フォーム アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-106">The client is a Windows Form application.</span></span> <span data-ttu-id="e5fd9-107">このアプリケーションは、Kerberos コントローラーで保護されたドメインに展開されています。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-107">The application is deployed in a domain with a Kerberos controller securing the domain.</span></span>  
  
 ![Windows 認証を利用したトランスポート セキュリティ](./media/transport-security-with-windows-authentication/secured-windows-authentication.gif)  
  
|<span data-ttu-id="e5fd9-109">特徴</span><span class="sxs-lookup"><span data-stu-id="e5fd9-109">Characteristic</span></span>|<span data-ttu-id="e5fd9-110">説明</span><span class="sxs-lookup"><span data-stu-id="e5fd9-110">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="e5fd9-111">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="e5fd9-111">Security Mode</span></span>|<span data-ttu-id="e5fd9-112">Transport</span><span class="sxs-lookup"><span data-stu-id="e5fd9-112">Transport</span></span>|  
|<span data-ttu-id="e5fd9-113">相互運用性</span><span class="sxs-lookup"><span data-stu-id="e5fd9-113">Interoperability</span></span>|<span data-ttu-id="e5fd9-114">WCF のみ</span><span class="sxs-lookup"><span data-stu-id="e5fd9-114">WCF only</span></span>|  
|<span data-ttu-id="e5fd9-115">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="e5fd9-115">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="e5fd9-116">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="e5fd9-116">Authentication (Client)</span></span>|<span data-ttu-id="e5fd9-117">○ (Windows 統合認証を使用)</span><span class="sxs-lookup"><span data-stu-id="e5fd9-117">Yes (using Windows integrated authentication)</span></span><br /><br /> <span data-ttu-id="e5fd9-118">○ (Windows 統合認証を使用)</span><span class="sxs-lookup"><span data-stu-id="e5fd9-118">Yes (using Windows integrated authentication)</span></span>|  
|<span data-ttu-id="e5fd9-119">整合性</span><span class="sxs-lookup"><span data-stu-id="e5fd9-119">Integrity</span></span>|<span data-ttu-id="e5fd9-120">○</span><span class="sxs-lookup"><span data-stu-id="e5fd9-120">Yes</span></span>|  
|<span data-ttu-id="e5fd9-121">機密性</span><span class="sxs-lookup"><span data-stu-id="e5fd9-121">Confidentiality</span></span>|<span data-ttu-id="e5fd9-122">○</span><span class="sxs-lookup"><span data-stu-id="e5fd9-122">Yes</span></span>|  
|<span data-ttu-id="e5fd9-123">Transport</span><span class="sxs-lookup"><span data-stu-id="e5fd9-123">Transport</span></span>|<span data-ttu-id="e5fd9-124">NET.TCP</span><span class="sxs-lookup"><span data-stu-id="e5fd9-124">NET.TCP</span></span>|  
|<span data-ttu-id="e5fd9-125">バインディング</span><span class="sxs-lookup"><span data-stu-id="e5fd9-125">Binding</span></span>|<xref:System.ServiceModel.NetTcpBinding>|  
  
## <a name="service"></a><span data-ttu-id="e5fd9-126">サービス</span><span class="sxs-lookup"><span data-stu-id="e5fd9-126">Service</span></span>  
 <span data-ttu-id="e5fd9-127">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-127">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e5fd9-128">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-128">Do one of the following:</span></span>  
  
- <span data-ttu-id="e5fd9-129">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-129">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="e5fd9-130">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-130">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e5fd9-131">コード</span><span class="sxs-lookup"><span data-stu-id="e5fd9-131">Code</span></span>  
 <span data-ttu-id="e5fd9-132">次のコードは、Windows セキュリティを使用するサービス エンドポイントの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-132">The following code shows how to create a service endpoint that uses a Windows security.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### <a name="configuration"></a><span data-ttu-id="e5fd9-133">の構成</span><span class="sxs-lookup"><span data-stu-id="e5fd9-133">Configuration</span></span>  
 <span data-ttu-id="e5fd9-134">コードの代わりに次の構成を使用して、サービス エンドポイントをセットアップできます。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-134">The following configuration can be used instead of the code to set up the service endpoint:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="e5fd9-135">クライアント</span><span class="sxs-lookup"><span data-stu-id="e5fd9-135">Client</span></span>  
 <span data-ttu-id="e5fd9-136">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-136">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="e5fd9-137">以下のいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-137">Do one of the following:</span></span>  
  
- <span data-ttu-id="e5fd9-138">コード (およびクライアント コード) を使用してスタンドアロン クライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-138">Create a stand-alone client using the code (and client code).</span></span>  
  
- <span data-ttu-id="e5fd9-139">エンドポイント アドレスを定義しないクライアントを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-139">Create a client that does not define any endpoint addresses.</span></span> <span data-ttu-id="e5fd9-140">代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-140">Instead, use the client constructor that takes the configuration name as an argument.</span></span> <span data-ttu-id="e5fd9-141">例:</span><span class="sxs-lookup"><span data-stu-id="e5fd9-141">For example:</span></span>  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### <a name="code"></a><span data-ttu-id="e5fd9-142">コード</span><span class="sxs-lookup"><span data-stu-id="e5fd9-142">Code</span></span>  
 <span data-ttu-id="e5fd9-143">クライアントを作成する場合のコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-143">The following code creates the client.</span></span> <span data-ttu-id="e5fd9-144">バインディングは、クライアントの資格情報の種類が Windows に設定された、TCP トランスポートによるトランスポート モード セキュリティを使用するように構成されます。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-144">The binding is configured to use the Transport mode security, with the TCP transport, with the client credential type set to Windows.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### <a name="configuration"></a><span data-ttu-id="e5fd9-145">の構成</span><span class="sxs-lookup"><span data-stu-id="e5fd9-145">Configuration</span></span>  
 <span data-ttu-id="e5fd9-146">コードの代わりに次の構成を使用して、クライアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="e5fd9-146">The following configuration can be used instead of the code to create the client.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5fd9-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5fd9-147">See also</span></span>

- [<span data-ttu-id="e5fd9-148">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="e5fd9-148">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="e5fd9-149">方法: Windows 資格情報でサービスをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="e5fd9-149">How to: Secure a Service with Windows Credentials</span></span>](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)
- <span data-ttu-id="e5fd9-150">[Windows Server App Fabric のセキュリティモデル](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="e5fd9-150">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
