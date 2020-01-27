---
title: 構成サンプル
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: eb02b5d01b3f95ef741aa689cc66616fd598577b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741956"
---
# <a name="configuration-sample"></a><span data-ttu-id="554af-102">構成サンプル</span><span class="sxs-lookup"><span data-stu-id="554af-102">Configuration Sample</span></span>
<span data-ttu-id="554af-103">このサンプルでは、構成ファイルを使用してサービスを探索可能にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="554af-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="554af-104">このサンプルでは、探索を構成ファイルで実装しています。</span><span class="sxs-lookup"><span data-stu-id="554af-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="554af-105">コードに検出を実装するサンプルについては、「 [Basic](../../../../docs/framework/wcf/samples/basic-sample.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="554af-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="554af-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="554af-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="554af-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="554af-107">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="554af-108">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="554af-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="554af-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="554af-109">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="554af-110">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="554af-110">Service Configuration</span></span>  
 <span data-ttu-id="554af-111">このサンプルの構成ファイルでは、次の 2 つの機能を示します。</span><span class="sxs-lookup"><span data-stu-id="554af-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="554af-112">標準の <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> を介してサービスを探索できるようにします。</span><span class="sxs-lookup"><span data-stu-id="554af-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="554af-113">サービスのアプリケーション エンドポイントに対する探索関連の情報を調整し、標準エンドポイントに対する探索関連の設定を調整します。</span><span class="sxs-lookup"><span data-stu-id="554af-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="554af-114">探索を有効にするには、サービスのアプリケーション構成ファイルで次の変更を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="554af-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="554af-115">探索エンドポイントを `<service>` 要素に追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="554af-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="554af-116">これは標準の <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> エンドポイントです。</span><span class="sxs-lookup"><span data-stu-id="554af-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="554af-117">このエンドポイントが、ランタイムによって探索サービスに関連付けられるシステム エンドポイントになります。</span><span class="sxs-lookup"><span data-stu-id="554af-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="554af-118">探索サービスは、このエンドポイント上でメッセージをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="554af-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="554af-119">`<serviceDiscovery>` 動作を `<serviceBehaviors>` セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="554af-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="554af-120">これにより、サービスが実行時に探索されるようになり、前述の探索エンドポイントを使用して探索の `Probe` メッセージおよび `Resolve` メッセージをリッスンするようになります。</span><span class="sxs-lookup"><span data-stu-id="554af-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="554af-121">この 2 つの追加により、指定した探索エンドポイントでサービスが探索可能になります。</span><span class="sxs-lookup"><span data-stu-id="554af-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="554af-122">次の構成スニペットでは、アプリケーション エンドポイントのサービスと定義された探索エンドポイントが示されています。</span><span class="sxs-lookup"><span data-stu-id="554af-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="554af-123">アナウンスを活用するために、アナウンス エンドポイントを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="554af-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="554af-124">これを実行するために、次のコードに示すように構成ファイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="554af-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="554af-125">アナウンス エンドポイントを探索サービス動作に追加することにより、サービスの既定のアナウンス クライアントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="554af-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="554af-126">これによって、サービスは、サービスが開いたときおよび閉じたときにそれぞれオンラインおよびオフラインのアナウンスを送信することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="554af-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="554af-127">この構成ファイルは、さらに動作を変更することによって、より高度な機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="554af-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="554af-128">特定のエンドポイントを使用することで、探索関連の情報を制御できます。</span><span class="sxs-lookup"><span data-stu-id="554af-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="554af-129">つまり、ユーザーは、エンドポイントを探索できるかどうかを制御できるだけでなく、そのエンドポイントを <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> およびカスタム XML メタデータでマークすることもできます。</span><span class="sxs-lookup"><span data-stu-id="554af-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="554af-130">これを行うには、`behaviorConfiguration` プロパティをアプリケーション エンドポイントに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="554af-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="554af-131">この場合、次のプロパティをアプリケーション エンドポイントに追加します。</span><span class="sxs-lookup"><span data-stu-id="554af-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="554af-132">これで、この動作構成要素を通じて、探索関連の属性を制御できます。</span><span class="sxs-lookup"><span data-stu-id="554af-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="554af-133">この場合、2 つのスコープがアプリケーション エンドポイントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="554af-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="554af-134">スコープの詳細については、「[検出検索と FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="554af-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="554af-135">探索エンドポイントに固有の詳細を制御することもできます。</span><span class="sxs-lookup"><span data-stu-id="554af-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="554af-136">この制御には <xref:System.ServiceModel.Configuration.StandardEndpointsSection> を使用します。</span><span class="sxs-lookup"><span data-stu-id="554af-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="554af-137">このサンプルでは、次のコード例に示すように、使用するプロトコルのバージョンを変更し、`maxResponseDelay` 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="554af-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="554af-138">この例で使用されている構成ファイルの全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="554af-138">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="554af-139">クライアント構成</span><span class="sxs-lookup"><span data-stu-id="554af-139">Client Configuration</span></span>  
 <span data-ttu-id="554af-140">クライアントのアプリケーション構成ファイルでは、`standardEndpoint` 型の `dynamicEndpoint` を使用して次の構成スニペットに示すように探索を利用します。</span><span class="sxs-lookup"><span data-stu-id="554af-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="554af-141">クライアントで `dynamicEndpoint` を使用する場合、探索は自動的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="554af-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="554af-142">探索時にはさまざまな設定が使用されます。たとえば、使用する探索エンドポイントの型を指定する、`discoveryClientSettings` セクションで定義される設定などがあります。</span><span class="sxs-lookup"><span data-stu-id="554af-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="554af-143">サービスの検索に使用する検索基準。</span><span class="sxs-lookup"><span data-stu-id="554af-143">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="554af-144">このサンプルでは、この機能を拡張し、クライアントで使用される <xref:System.ServiceModel.Discovery.FindCriteria>、および探索に使用される標準の `updDiscoveryEndpoint` の一部のプロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="554af-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="554af-145"><xref:System.ServiceModel.Discovery.FindCriteria> は、スコープと特定の `scopeMatchBy` アルゴリズム、およびカスタムの終了条件を使用するように変更します。</span><span class="sxs-lookup"><span data-stu-id="554af-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="554af-146">さらに、このサンプルでは、クライアントで `Probe` メッセージを使用して XML 要素を送信する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="554af-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="554af-147">最後に、次の構成ファイルに示すように、使用するプロトコルのバージョンや UDP 固有の設定など、<xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> の変更をいくつか行います。</span><span class="sxs-lookup"><span data-stu-id="554af-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="554af-148">サンプルで使用されているクライアント構成の全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="554af-148">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="554af-149">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="554af-149">To use this sample</span></span>  
  
1. <span data-ttu-id="554af-150">このサンプルでは HTTP エンドポイントを使用します。このサンプルを実行するには、適切な URL ACL を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="554af-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="554af-151">詳細については、「 [HTTP および HTTPS の構成](../feature-details/configuring-http-and-https.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="554af-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="554af-152">管理特権で次のコマンドを実行すると、適切な ACL が追加されます。</span><span class="sxs-lookup"><span data-stu-id="554af-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="554af-153">そのままではコマンドが動作しない場合は、代わりに、ドメインとユーザー名を引数に指定して実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="554af-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="554af-154">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="554af-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="554af-155">ビルド ディレクトリからサービス実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="554af-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="554af-156">クライアント実行可能ファイルを実行します。</span><span class="sxs-lookup"><span data-stu-id="554af-156">Run the client executable.</span></span> <span data-ttu-id="554af-157">クライアントでサービスを検索できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="554af-157">Note that the client is able to locate the service.</span></span>  
