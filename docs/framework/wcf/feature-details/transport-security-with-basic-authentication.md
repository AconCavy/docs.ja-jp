---
title: 基本認証でのトランスポート セキュリティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b54f491d-196b-4279-876c-76b83ec0442c
ms.openlocfilehash: 7c83de70e404fe8304bc2e35c1bb5df9e42f95b7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576097"
---
# <a name="transport-security-with-basic-authentication"></a><span data-ttu-id="3ddb8-102">基本認証でのトランスポート セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3ddb8-102">Transport Security with Basic Authentication</span></span>
<span data-ttu-id="3ddb8-103">次の図は、Windows Communication Foundation (WCF) サービスとクライアントを示しています。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-103">The following illustration shows a Windows Communication Foundation (WCF) service and client.</span></span> <span data-ttu-id="3ddb8-104">サーバーには、SSL (Secure Sockets Layer) に使用できる有効な X509 証明書が必要であり、クライアントはサーバーの証明書を信頼する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-104">The server needs a valid X.509 certificate that can be used for Secure Sockets Layer (SSL), and the clients must trust the server’s certificate.</span></span> <span data-ttu-id="3ddb8-105">さらに、Web サービスには使用可能な SSL が既に実装されています。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-105">Further, the Web service already has an SSL implementation that can be used.</span></span> <span data-ttu-id="3ddb8-106">インターネットインフォメーションサービス (IIS) で基本認証を有効にする方法の詳細については、「」を参照してください <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication> 。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-106">For more information about enabling basic authentication on Internet Information Services (IIS), see <https://docs.microsoft.com/iis/configuration/system.webserver/security/authentication/basicauthentication>.</span></span>  
  
 ![基本認証を使用したトランスポートセキュリティを示すスクリーンショット。](./media/transport-security-with-basic-authentication/transport-security-basic-authentication.gif)  
  
|<span data-ttu-id="3ddb8-108">特徴</span><span class="sxs-lookup"><span data-stu-id="3ddb8-108">Characteristic</span></span>|<span data-ttu-id="3ddb8-109">説明</span><span class="sxs-lookup"><span data-stu-id="3ddb8-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3ddb8-110">セキュリティ モード</span><span class="sxs-lookup"><span data-stu-id="3ddb8-110">Security Mode</span></span>|<span data-ttu-id="3ddb8-111">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3ddb8-111">Transport</span></span>|  
|<span data-ttu-id="3ddb8-112">相互運用性</span><span class="sxs-lookup"><span data-stu-id="3ddb8-112">Interoperability</span></span>|<span data-ttu-id="3ddb8-113">既存の Web サービス クライアントとサービスを使用する</span><span class="sxs-lookup"><span data-stu-id="3ddb8-113">With existing Web service clients and services</span></span>|  
|<span data-ttu-id="3ddb8-114">認証 (サーバー)</span><span class="sxs-lookup"><span data-stu-id="3ddb8-114">Authentication (Server)</span></span><br /><br /> <span data-ttu-id="3ddb8-115">認証 (クライアント)</span><span class="sxs-lookup"><span data-stu-id="3ddb8-115">Authentication (Client)</span></span>|<span data-ttu-id="3ddb8-116">○ (HTTPS を使用)</span><span class="sxs-lookup"><span data-stu-id="3ddb8-116">Yes (using HTTPS)</span></span><br /><br /> <span data-ttu-id="3ddb8-117">○ (ユーザー名とパスワードを使用)</span><span class="sxs-lookup"><span data-stu-id="3ddb8-117">Yes (through User name/Password)</span></span>|  
|<span data-ttu-id="3ddb8-118">整合性</span><span class="sxs-lookup"><span data-stu-id="3ddb8-118">Integrity</span></span>|<span data-ttu-id="3ddb8-119">はい</span><span class="sxs-lookup"><span data-stu-id="3ddb8-119">Yes</span></span>|  
|<span data-ttu-id="3ddb8-120">機密情報</span><span class="sxs-lookup"><span data-stu-id="3ddb8-120">Confidentiality</span></span>|<span data-ttu-id="3ddb8-121">はい</span><span class="sxs-lookup"><span data-stu-id="3ddb8-121">Yes</span></span>|  
|<span data-ttu-id="3ddb8-122">トランスポート</span><span class="sxs-lookup"><span data-stu-id="3ddb8-122">Transport</span></span>|<span data-ttu-id="3ddb8-123">HTTPS</span><span class="sxs-lookup"><span data-stu-id="3ddb8-123">HTTPS</span></span>|  
|<span data-ttu-id="3ddb8-124">バインド</span><span class="sxs-lookup"><span data-stu-id="3ddb8-124">Binding</span></span>|<xref:System.ServiceModel.WSHttpBinding>|  
  
## <a name="service"></a><span data-ttu-id="3ddb8-125">サービス</span><span class="sxs-lookup"><span data-stu-id="3ddb8-125">Service</span></span>  
 <span data-ttu-id="3ddb8-126">次のコードと構成は、別々に実行します。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-126">The following code and configuration are meant to run independently.</span></span> <span data-ttu-id="3ddb8-127">次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-127">Do one of the following:</span></span>  
  
- <span data-ttu-id="3ddb8-128">構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-128">Create a stand-alone service using the code with no configuration.</span></span>  
  
- <span data-ttu-id="3ddb8-129">提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-129">Create a service using the supplied configuration, but do not define any endpoints.</span></span>  
  
### <a name="code"></a><span data-ttu-id="3ddb8-130">コード</span><span class="sxs-lookup"><span data-stu-id="3ddb8-130">Code</span></span>  
 <span data-ttu-id="3ddb8-131">次のコードでは、転送セキュリティ用の Windows ドメイン ユーザー名とパスワードを使用するサービス エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-131">The following code shows how to create a service endpoint that uses a Windows domain user name and password for transfer security.</span></span> <span data-ttu-id="3ddb8-132">サービスには、クライアントに対する認証を行うための X 509 証明書が必要になります。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-132">Note that the service requires an X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="3ddb8-133">詳細については、「[証明書の](working-with-certificates.md)使用」および「[方法: SSL 証明書を使用してポートを構成する](how-to-configure-a-port-with-an-ssl-certificate.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-133">For more information, see [Working with Certificates](working-with-certificates.md) and [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
 [!code-csharp[C_SecurityScenarios#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#1)]
 [!code-vb[C_SecurityScenarios#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#1)]  
  
## <a name="configuration"></a><span data-ttu-id="3ddb8-134">構成</span><span class="sxs-lookup"><span data-stu-id="3ddb8-134">Configuration</span></span>  
 <span data-ttu-id="3ddb8-135">次の例では、トランスポート レベルのセキュリティの基本認証を使用するサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-135">The following configures a service to use basic authentication with transport-level security:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <wsHttpBinding>  
                <binding name="UsernameWithTransport">  
                    <security mode="Transport">  
                        <transport clientCredentialType="Basic" />  
                    </security>  
                </binding>  
            </wsHttpBinding>  
        </bindings>  
        <services>  
            <service name="BasicAuthentication.Calculator">  
                <endpoint address="https://localhost/Calculator"  
                          binding="wsHttpBinding"
                          bindingConfiguration="UsernameWithTransport"  
                          name="BasicEndpoint"
                          contract="BasicAuthentication.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client"></a><span data-ttu-id="3ddb8-136">クライアント</span><span class="sxs-lookup"><span data-stu-id="3ddb8-136">Client</span></span>  
  
### <a name="code"></a><span data-ttu-id="3ddb8-137">コード</span><span class="sxs-lookup"><span data-stu-id="3ddb8-137">Code</span></span>  
 <span data-ttu-id="3ddb8-138">次のコードは、ユーザー名とパスワードが含まれるクライアント コードを示しています。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-138">The following code shows the client code that includes the user name and password.</span></span> <span data-ttu-id="3ddb8-139">ユーザーは、有効な Windows ユーザー名とパスワードを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-139">Note that the user must provide a valid Windows user name and password.</span></span> <span data-ttu-id="3ddb8-140">ユーザー名とパスワードを返すコードは、ここに示されていません。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-140">The code to return the user name and password is not shown here.</span></span> <span data-ttu-id="3ddb8-141">ダイアログボックスまたは他のインターフェースを使用して、ユーザーにこれらの情報を照会してください。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-141">Use a dialog box or other interface to query the user for the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ddb8-142">ユーザー名とパスワードは、コードを使ってのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-142">User name and password can only be set using code.</span></span>  
  
 [!code-csharp[C_SecurityScenarios#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#2)]
 [!code-vb[C_SecurityScenarios#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#2)]  
  
### <a name="configuration"></a><span data-ttu-id="3ddb8-143">構成</span><span class="sxs-lookup"><span data-stu-id="3ddb8-143">Configuration</span></span>  
 <span data-ttu-id="3ddb8-144">次のコードは、クライアントの構成を示しています。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-144">The following code shows the client configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ddb8-145">構成を使用してユーザー名とパスワードを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-145">You cannot use configuration to set the user name and password.</span></span> <span data-ttu-id="3ddb8-146">ここに示した構成には、ユーザー名とパスワードを設定するためのコードを補う必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ddb8-146">The configuration shown here must be augmented using code to set the user name and password.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Basic" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ddb8-147">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ddb8-147">See also</span></span>

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>
- [<span data-ttu-id="3ddb8-148">証明書の使用</span><span class="sxs-lookup"><span data-stu-id="3ddb8-148">Working with Certificates</span></span>](working-with-certificates.md)
- [<span data-ttu-id="3ddb8-149">方法: SSL 証明書を使用してポートを構成する</span><span class="sxs-lookup"><span data-stu-id="3ddb8-149">How to: Configure a Port with an SSL Certificate</span></span>](how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="3ddb8-150">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="3ddb8-150">Security Overview</span></span>](security-overview.md)
- [\<clientCredentials>](../../configure-apps/file-schema/wcf/clientcredentials.md)
- <span data-ttu-id="3ddb8-151">[Windows Server AppFabric のセキュリティ モデル](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3ddb8-151">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
