---
title: ルーティングの概要
ms.date: 03/30/2017
ms.assetid: bf6ceb38-6622-433b-9ee7-f79bc93497a1
ms.openlocfilehash: 8ce98aab2ed14401fa7c2cbf43eb92a633fa96b0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746466"
---
# <a name="routing-introduction"></a><span data-ttu-id="d1721-102">ルーティングの概要</span><span class="sxs-lookup"><span data-stu-id="d1721-102">Routing Introduction</span></span>

<span data-ttu-id="d1721-103">ルーティング サービスは、メッセージの内容を基にメッセージをルーティングできる、プラグ可能な汎用の SOAP 中継局を提供します。</span><span class="sxs-lookup"><span data-stu-id="d1721-103">The Routing Service provides a generic pluggable SOAP intermediary that is capable of routing messages based on message content.</span></span> <span data-ttu-id="d1721-104">ルーティング サービスを使用すると、サービスの集計、サービスのバージョン管理、優先度ルーティング、マルチキャスト ルーティングなどのシナリオを実装できる複雑なルーティング ロジックを作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-104">With the Routing Service, you can create complex routing logic that allows you to implement scenarios such as service aggregation, service versioning, priority routing, and multicast routing.</span></span> <span data-ttu-id="d1721-105">また、ルーティング サービスは、バックアップ エンドポイントのリストを設定できるエラー処理機能も提供します。バックアップ エンドポイントは、プライマリ送信先エンドポイントへの送信時に障害が発生した場合に、メッセージの送信先になります。</span><span class="sxs-lookup"><span data-stu-id="d1721-105">The Routing Service also provides error handling that allows you to set up lists of backup endpoints, to which messages are sent if a failure occurs when sending to the primary destination endpoint.</span></span>

<span data-ttu-id="d1721-106">このトピックでは、ルーティング サービスをご存じない方を対象としています。ここでは、ルーティング サービスの基本的な構成とホストについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d1721-106">This topic is intended for those new to the Routing Service and covers basic configuration and hosting of the Routing Service.</span></span>

## <a name="configuration"></a><span data-ttu-id="d1721-107">の構成</span><span class="sxs-lookup"><span data-stu-id="d1721-107">Configuration</span></span>

<span data-ttu-id="d1721-108">ルーティング サービスは、1 つ以上のサービス エンドポイントを公開する WCF サービスとして実装されます。サービス エンドポイントは、クライアント アプリケーションからメッセージを受信し、受信したメッセージを 1 つ以上の送信先エンドポイントにルーティングします。</span><span class="sxs-lookup"><span data-stu-id="d1721-108">The Routing Service is implemented as a WCF service that exposes one or more service endpoints that receive messages from client applications and route the messages to one or more destination endpoints.</span></span> <span data-ttu-id="d1721-109">ルーティング サービスには <xref:System.ServiceModel.Routing.RoutingBehavior> があります。これは、このサービスによって公開されるサービス エンドポイントに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-109">The service provides a <xref:System.ServiceModel.Routing.RoutingBehavior>, which is applied to the service endpoints exposed by the service.</span></span> <span data-ttu-id="d1721-110">この動作を使用して、サービスの稼働方法について詳細を構成します。</span><span class="sxs-lookup"><span data-stu-id="d1721-110">This behavior is used to configure various aspects of how the service operates.</span></span> <span data-ttu-id="d1721-111">構成ファイルを使用する場合の構成を容易にするために、パラメーターは**Routingbehavior**に指定されています。</span><span class="sxs-lookup"><span data-stu-id="d1721-111">For ease of configuration when using a configuration file, the parameters are specified on the **RoutingBehavior**.</span></span> <span data-ttu-id="d1721-112">コードベースのシナリオでは、これらのパラメーターは <xref:System.ServiceModel.Routing.RoutingConfiguration> オブジェクトの一部として指定されます。これは、 **Routingbehavior**に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="d1721-112">In code-based scenarios, these parameters would be specified as part of a <xref:System.ServiceModel.Routing.RoutingConfiguration> object, which can then be passed to a **RoutingBehavior**.</span></span>

<span data-ttu-id="d1721-113">開始時に、この動作はメッセージの SOAP 処理の実行に使用される <xref:System.ServiceModel.Routing.SoapProcessingBehavior> をクライアントのエンドポイントに追加します。</span><span class="sxs-lookup"><span data-stu-id="d1721-113">When starting, this behavior adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior>, which is used to perform SOAP processing of messages, to the client endpoints.</span></span> <span data-ttu-id="d1721-114">これにより、ルーティングサービスは、メッセージを受信したエンドポイントとは異なる**MessageVersion**を必要とするエンドポイントにメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-114">This allows the Routing Service to transmit messages to endpoints that require a different **MessageVersion** than the endpoint the message was received over.</span></span> <span data-ttu-id="d1721-115">また、 **Routingbehavior**は、サービス拡張 (<xref:System.ServiceModel.Routing.RoutingExtension>) も登録します。これにより、実行時にルーティングサービスの構成を変更するためのユーザー補助ポイントが提供されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-115">The **RoutingBehavior** also registers a service extension, the <xref:System.ServiceModel.Routing.RoutingExtension>, which provides an accessibility point for modifying the Routing Service configuration at run time.</span></span>

<span data-ttu-id="d1721-116">**Routingconfiguration**クラスは、ルーティングサービスの構成を構成および更新するための一貫した手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="d1721-116">The **RoutingConfiguration** class provides a consistent means of configuring and updating the configuration of the Routing Service.</span></span>  <span data-ttu-id="d1721-117">これには、ルーティングサービスの設定として機能するパラメーターが含まれており、サービスの開始時に**Routingbehavior**を構成するために使用されるか、または実行時にルーティング構成を変更するために**routingbehavior**に渡されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-117">It contains parameters that act as the settings for the Routing Service and is used to configure the **RoutingBehavior** when the service starts, or is passed to the **RoutingExtension** to modify routing configuration at run time.</span></span>

<span data-ttu-id="d1721-118">メッセージのコンテンツ ベースのルーティングを実行するために使用するルーティング ロジックは、複数の <xref:System.ServiceModel.Dispatcher.MessageFilter> オブジェクトをフィルター テーブル (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> オブジェクト) にまとめて定義します。</span><span class="sxs-lookup"><span data-stu-id="d1721-118">The routing logic used to perform content-based routing of messages is defined by grouping multiple <xref:System.ServiceModel.Dispatcher.MessageFilter> objects together into filter tables (<xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> objects).</span></span> <span data-ttu-id="d1721-119">受信メッセージは、フィルターテーブルに含まれるメッセージフィルターと、メッセージに一致する各**Messagefilter**に対して評価され、送信先エンドポイントに転送されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-119">Incoming messages are evaluated against the message filters contained in the filter table, and for each **MessageFilter** that matches the message, forwarded to a destination endpoint.</span></span> <span data-ttu-id="d1721-120">メッセージのルーティングに使用するフィルターテーブルは、構成で**Routingbehavior**を使用するか、 **routingbehavior**オブジェクトを使用してコードを使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="d1721-120">The filter table that should be used to route messages is specified by using either the **RoutingBehavior** in configuration or through code by using the **RoutingConfiguration** object.</span></span>

### <a name="defining-endpoints"></a><span data-ttu-id="d1721-121">エンドポイントの定義</span><span class="sxs-lookup"><span data-stu-id="d1721-121">Defining Endpoints</span></span>

<span data-ttu-id="d1721-122">構成を行うには、使用するルーティング ロジックの定義から始めるように思えますが、実際には、まず、メッセージのルーティング先になるエンドポイントの形状を決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-122">While it may seem that you should start your configuration by defining the routing logic you will use, your first step should actually be to determine the shape of the endpoints you will be routing messages to.</span></span> <span data-ttu-id="d1721-123">ルーティング サービスは、メッセージの送受信に使用するチャネルの形状を定義するコントラクトを使用するため、入力チャネルの形状と出力チャネルの形状が一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-123">The Routing Service uses contracts that define the shape of the channels used to receive and send messages, and therefore the shape of the input channel must match that of the output channel.</span></span>  <span data-ttu-id="d1721-124">たとえば、要求/応答チャネル形状を使用するエンドポイントにルーティングする場合は、<xref:System.ServiceModel.Routing.IRequestReplyRouter> など、着信エンドポイントでも、互換性のあるコントラクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-124">For example, if you are routing to endpoints that use the request-reply channel shape, then you must use a compatible contract on the inbound endpoints, such as the <xref:System.ServiceModel.Routing.IRequestReplyRouter>.</span></span>

<span data-ttu-id="d1721-125">つまり、複数の送信先エンドポイントが、複数の通信パターン (一方向の操作と双方向の操作の混合など) のコントラクトを使用している場合は、すべての送信先エンドポイントへのメッセージの受信とルーティングを行う単一のサービス エンドポイントを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="d1721-125">This means that if your destination endpoints use contracts with multiple communication patterns (such as mixing one-way and two-way operations,) you cannot create a single service endpoint that can receive and route messages to all of them.</span></span> <span data-ttu-id="d1721-126">互換性のある形状を使用するエンドポイントを特定し、送信先エンドポイントにルーティングされるメッセージの受信に使用するサービス エンドポイントを 1 つ以上定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-126">You must determine which endpoints have compatible shapes and define one or more service endpoints that will be used to receive messages to be routed to the destination endpoints.</span></span>

> [!NOTE]
> <span data-ttu-id="d1721-127">複数の通信パターン (一方向の操作と双方向の操作の混合など) を指定するコントラクトを使用している場合は、<xref:System.ServiceModel.Routing.IDuplexSessionRouter> など、二重のコントラクトをルーティング サービスで使用して対処します。</span><span class="sxs-lookup"><span data-stu-id="d1721-127">When working with contracts that specify multiple communication patterns (such as a mix of one-way and two-way operations,) a workaround is to use a duplex contract at the Routing Service such as <xref:System.ServiceModel.Routing.IDuplexSessionRouter>.</span></span> <span data-ttu-id="d1721-128">ただし、この場合は、バインドが二重通信に対応可能である必要があり、シナリオによっては、それが可能でない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d1721-128">However this means that the binding must be capable of duplex communication, which may not be possible for all scenarios.</span></span> <span data-ttu-id="d1721-129">対応が不可能なシナリオでは、複数のエンドポイントに通信をファクタリングするか、アプリケーションの変更が必要になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-129">In scenarios where this is not possible, factoring the communication into multiple endpoints or modifying the application may be necessary.</span></span>

<span data-ttu-id="d1721-130">ルーティングコントラクトの詳細については、「[ルーティングコントラクト](routing-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1721-130">For more information about routing contracts, see [Routing Contracts](routing-contracts.md).</span></span>

<span data-ttu-id="d1721-131">サービスエンドポイントを定義した後は、 **Routingbehavior**を使用して、特定の**routingbehavior**をエンドポイントに関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="d1721-131">After the service endpoint is defined, you can use the **RoutingBehavior** to associate a specific **RoutingConfiguration** with the endpoint.</span></span> <span data-ttu-id="d1721-132">構成ファイルを使用してルーティングサービスを構成するときに、 **Routingbehavior**を使用して、このエンドポイントで受信したメッセージを処理するために使用されるルーティングロジックを含むフィルターテーブルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1721-132">When configuring the Routing Service by using a configuration file, the **RoutingBehavior** is used to specify the filter table that contains the routing logic used to process messages received on this endpoint.</span></span> <span data-ttu-id="d1721-133">ルーティングサービスをプログラムで構成する場合は、 **Routingconfiguration**を使用してフィルターテーブルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-133">If you are configuring the Routing Service programmatically you can specify the filter table by using the **RoutingConfiguration**.</span></span>

<span data-ttu-id="d1721-134">以下に、プログラムによる方法と構成ファイルを使用する方法の両方で、ルーティング サービスが使用するサービスおよびクライアント エンドポイントを定義する例を示します。</span><span class="sxs-lookup"><span data-stu-id="d1721-134">The following example defines the service and client endpoints that are used by the Routing Service both programmatically and by using a configuration file.</span></span>

```xml
<services>
  <!--ROUTING SERVICE -->
  <service behaviorConfiguration="routingData"
            name="System.ServiceModel.Routing.RoutingService">
    <host>
      <baseAddresses>
        <add baseAddress="http://localhost:8000/routingservice/router"/>
      </baseAddresses>
    </host>
    <!-- Define the service endpoints that are receive messages -->
    <endpoint address=""
              binding="wsHttpBinding"
              name="reqReplyEndpoint"
              contract="System.ServiceModel.Routing.IRequestReplyRouter" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<client>
<!-- Define the client endpoint(s) to route messages to -->
  <endpoint name="CalculatorService"
            address="http://localhost:8000/servicemodelsamples/service"
            binding="wsHttpBinding" contract="*" />
</client>
```

```csharp
//set up some communication defaults
string clientAddress = "http://localhost:8000/servicemodelsamples/service";
string routerAddress = "http://localhost:8000/routingservice/router";
Binding routerBinding = new WSHttpBinding();
Binding clientBinding = new WSHttpBinding();
//add the endpoint the router uses to receive messages
serviceHost.AddServiceEndpoint(
     typeof(IRequestReplyRouter),
     routerBinding,
     routerAddress);
//create the client endpoint the router routes messages to
ContractDescription contract = ContractDescription.GetContract(
     typeof(IRequestReplyRouter));
ServiceEndpoint client = new ServiceEndpoint(
     contract,
     clientBinding,
     new EndpointAddress(clientAddress));
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
….
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
//attach the behavior to the service host
serviceHost.Description.Behaviors.Add(
     new RoutingBehavior(rc));
```

<span data-ttu-id="d1721-135">この例では、ルーティングサービスを構成して、`http://localhost:8000/routingservice/router`のアドレスを持つ単一のエンドポイントを公開します。これは、ルーティングされるメッセージを受信するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-135">This example configures the Routing Service to expose a single endpoint with an address of `http://localhost:8000/routingservice/router`, which is used to receive messages to be routed.</span></span> <span data-ttu-id="d1721-136">メッセージは要求/応答エンドポイントにルーティングされるため、サービス エンドポイントは <xref:System.ServiceModel.Routing.IRequestReplyRouter> コントラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="d1721-136">Because the messages are routed to request-reply endpoints, the service endpoint uses the <xref:System.ServiceModel.Routing.IRequestReplyRouter> contract.</span></span> <span data-ttu-id="d1721-137">この構成では、メッセージのルーティング先となる `http://localhost:8000/servicemodelsample/service` の単一のクライアントエンドポイントも定義します。</span><span class="sxs-lookup"><span data-stu-id="d1721-137">This configuration also defines a single client endpoint of `http://localhost:8000/servicemodelsample/service` that messages are routed to.</span></span> <span data-ttu-id="d1721-138">"RoutingTable1" という名前のフィルターテーブルは、メッセージのルーティングに使用されるルーティングロジックを含み、 **Routingbehavior** (構成ファイルの場合) または**routingbehavior** (プログラムによる構成の場合) を使用してサービスエンドポイントに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="d1721-138">The filter table (not shown) named "routingTable1" contains the routing logic used to route messages, and is associated with the service endpoint by using the **RoutingBehavior** (for a configuration file) or **RoutingConfiguration** (for programmatic configuration).</span></span>

### <a name="routing-logic"></a><span data-ttu-id="d1721-139">ルーティング ロジック</span><span class="sxs-lookup"><span data-stu-id="d1721-139">Routing Logic</span></span>

<span data-ttu-id="d1721-140">メッセージのルーティングに使用されるルーティング ロジックを定義するには、受信メッセージに含まれるデータのうち、一意に識別して処理できるものを特定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-140">To define the routing logic used to route messages, you must determine what data contained within the incoming messages can be uniquely acted upon.</span></span> <span data-ttu-id="d1721-141">たとえば、ルーティング先のすべてのエンドポイントが同じ SOAP アクションを共有する場合、メッセージに含まれる Action の値は、メッセージのルーティング先となる特定のエンドポイントを示す値としては不適切です。</span><span class="sxs-lookup"><span data-stu-id="d1721-141">For example, if all the destination endpoints you are routing to share the same SOAP Actions, the value of the Action contained within the message is not a good indicator of which specific endpoint the message should be routed to.</span></span> <span data-ttu-id="d1721-142">ある特定のエンドポイントにメッセージを一意にルーティングする必要がある場合は、メッセージのルーティング先エンドポイントを一意に識別できるデータを基に、フィルター処理を行います。</span><span class="sxs-lookup"><span data-stu-id="d1721-142">If you must uniquely route messages to one specific endpoint, you should filter upon data that uniquely identifies the destination endpoint that the message is routed to.</span></span>

<span data-ttu-id="d1721-143">ルーティングサービスには、アドレス、アクション、エンドポイント名、XPath クエリなど、メッセージ内の特定の値を検査するいくつかの**Messagefilter**実装が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d1721-143">The Routing Service provides several **MessageFilter** implementations that inspect specific values within the message, such as the address, action, endpoint name, or even an XPath query.</span></span> <span data-ttu-id="d1721-144">これらの実装のいずれも要件を満たしていない場合は、カスタム**Messagefilter**実装を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-144">If none of these implementations meet your needs you can create a custom **MessageFilter** implementation.</span></span> <span data-ttu-id="d1721-145">メッセージフィルターと、ルーティングサービスで使用される実装の比較の詳細については、「[メッセージフィルター](message-filters.md) 」と「[フィルターの選択](choosing-a-filter.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1721-145">For more information about message filters and a comparison of the implementations used by the Routing Service, see [Message Filters](message-filters.md) and [Choosing a Filter](choosing-a-filter.md).</span></span>

<span data-ttu-id="d1721-146">複数のメッセージフィルターは、フィルターテーブルにまとめられています。これにより、各**Messagefilter**が送信先エンドポイントに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="d1721-146">Multiple message filters are organized together into filter tables, which associate each **MessageFilter** with a destination endpoint.</span></span> <span data-ttu-id="d1721-147">または、フィルター テーブルを使用して、通信エラーが発生した場合に、ルーティング サービスがメッセージを送信するバックアップ エンドポイントのリストを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d1721-147">Optionally, the filter table can also be used to specify a list of back-up endpoints that the Routing Service will attempt to send the message to in the event of a transmission failure.</span></span>

<span data-ttu-id="d1721-148">既定では、フィルター テーブル内のすべてのメッセージ フィルターが同時に評価されます。ただし、<xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> を指定すると、特定の順序でメッセージ フィルターが評価されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="d1721-148">By default all message filters within a filter table are evaluated simultaneously; however, you can specify a <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement.Priority%2A> that causes the message filters to be evaluated in a specific order.</span></span> <span data-ttu-id="d1721-149">優先度が最も高いすべてのエントリが最初に評価されます。優先度レベルが高いフィルターの中に一致するものが見つかった場合、それよりも優先度の低いメッセージ フィルターは評価されません。</span><span class="sxs-lookup"><span data-stu-id="d1721-149">All entries with the highest priority are evaluated first, and message filters of lower priorities are not evaluated if a match is found at a higher priority level.</span></span> <span data-ttu-id="d1721-150">フィルターテーブルの詳細については、「[メッセージフィルター](message-filters.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1721-150">For more information about filter tables, see [Message Filters](message-filters.md).</span></span>

<span data-ttu-id="d1721-151">次の例では <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> を使用しています。これは、すべてのメッセージに対して `true` に評価されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-151">The following examples use the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter>, which evaluates to `true` for all messages.</span></span> <span data-ttu-id="d1721-152">この**messagefilter**は、"routingTable1" フィルターテーブルに追加されます。これにより、 **Messagefilter**が "電卓 atorservice" という名前のクライアントエンドポイントに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="d1721-152">This **MessageFilter** is added to the "routingTable1" filter table, which associates the **MessageFilter** with the client endpoint named "CalculatorService".</span></span> <span data-ttu-id="d1721-153">次に、 **Routingbehavior**は、このテーブルを使用して、サービスエンドポイントによって処理されるメッセージをルーティングする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d1721-153">The **RoutingBehavior** then specifies that this table should be used to route messages processed by the service endpoint.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="routingData">
      <serviceMetadata httpGetEnabled="True"/>
      <!-- Add the RoutingBehavior and specify the Routing Table to use -->
      <routing filterTableName="routingTable1" />
    </behavior>
  </serviceBehaviors>
</behaviors>
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
//create a new routing configuration object
RoutingConfiguration rc = new RoutingConfiguration();
//create the endpoint list that contains the endpoints to route to
//in this case we have only one
List<ServiceEndpoint> endpointList = new List<ServiceEndpoint>();
endpointList.Add(client);
//add a MatchAll filter to the Router's filter table
//map it to the endpoint list defined earlier
//when a message matches this filter, it is sent to the endpoint contained in the list
rc.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
```

> [!NOTE]
> <span data-ttu-id="d1721-154">既定でルーティング サービスによって評価されるのは、メッセージのヘッダーのみです。</span><span class="sxs-lookup"><span data-stu-id="d1721-154">By default, the Routing Service only evaluates the headers of the message.</span></span> <span data-ttu-id="d1721-155">フィルターがメッセージ本文にアクセスできるようにするには、<xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="d1721-155">To allow the filters to access the message body, you must set <xref:System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly%2A> to `false`.</span></span>

<span data-ttu-id="d1721-156">**スコープ**</span><span class="sxs-lookup"><span data-stu-id="d1721-156">**Multicast**</span></span>

<span data-ttu-id="d1721-157">多くのルーティング サービス構成では、特定の 1 つのエンドポイントにのみメッセージをルーティングする排他的なフィルター ロジックが使用されますが、特定のメッセージを、複数の送信先エンドポイントにルーティングすることが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d1721-157">While many Routing Service configurations use exclusive filter logic that routes messages to only one specific endpoint, you may need to route a given message to multiple destination endpoints.</span></span> <span data-ttu-id="d1721-158">メッセージを複数の送信先にマルチキャストするには、次の条件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-158">To multicast a message to multiple destinations, the following conditions must be true:</span></span>

- <span data-ttu-id="d1721-159">要求への応答時にクライアント アプリケーションが受信できるのは 1 つの応答のみであるため、チャネル形状が要求/応答でない (一方向または二重のどちらでもよい) ことが必要である。</span><span class="sxs-lookup"><span data-stu-id="d1721-159">The channel shape must not be request-reply (though may be one-way or duplex,) because only one reply can be received by the client application in response to the request.</span></span>

- <span data-ttu-id="d1721-160">複数のフィルターが、メッセージの評価時に `true` を返す必要がある。</span><span class="sxs-lookup"><span data-stu-id="d1721-160">Multiple filters must return `true` when evaluating the message.</span></span>

<span data-ttu-id="d1721-161">これらの条件が満たされる場合は、メッセージが、`true` に評価されたすべてのフィルターのすべてのエンドポイントにルーティングされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-161">If these conditions are met, the message is routed to all endpoints of all filters that evaluate to `true`.</span></span> <span data-ttu-id="d1721-162">次の例は、結果、メッセージ内のエンドポイント アドレスがある場合、両方のエンドポイントにルーティングされるメッセージ ルーティングの構成を定義 `http://localhost:8000/routingservice/router/rounding` です。</span><span class="sxs-lookup"><span data-stu-id="d1721-162">The following example defines a routing configuration that results in messages being routed to both endpoints if the endpoint address in the message is `http://localhost:8000/routingservice/router/rounding`.</span></span>

```xml
<!--ROUTING SECTION -->
<routing>
  <filters>
    <filter name="MatchAllFilter1" filterType="MatchAll" />
    <filter name="RoundingFilter1" filterType="EndpointAddress"
            filterData="http://localhost:8000/routingservice/router/rounding" />
  </filters>
  <filterTables>
    <table name="routingTable1">
      <filters>
        <add filterName="MatchAllFilter1" endpointName="CalculatorService" />
        <add filterName="RoundingFilter1" endpointName="RoundingCalcService" />
      </filters>
    </table>
  </filterTables>
</routing>
```

```csharp
rc.FilterTable.Add(new MatchAllMessageFilter(), calculatorEndpointList);
rc.FilterTable.Add(new EndpointAddressMessageFilter(new EndpointAddress(
    "http://localhost:8000/routingservice/router/rounding")),
    roundingCalcEndpointList);
```

### <a name="soap-processing"></a><span data-ttu-id="d1721-163">SOAP 処理</span><span class="sxs-lookup"><span data-stu-id="d1721-163">SOAP Processing</span></span>

<span data-ttu-id="d1721-164">異なるプロトコル間でのメッセージのルーティングをサポートするために、 **Routingbehavior**は既定では、メッセージのルーティング先となるすべてのクライアントエンドポイントに <xref:System.ServiceModel.Routing.SoapProcessingBehavior> を追加します。</span><span class="sxs-lookup"><span data-stu-id="d1721-164">To support the routing of messages between dissimilar protocols, the **RoutingBehavior** by default adds the <xref:System.ServiceModel.Routing.SoapProcessingBehavior> to all client endpoint(s) that messages are routed to.</span></span> <span data-ttu-id="d1721-165">この動作により、エンドポイントにメッセージをルーティングする前に新しい**MessageVersion**が自動的に作成され、要求元のクライアントアプリケーションに返される前に、応答ドキュメントに対して互換性のある**MessageVersion**が作成されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-165">This behavior automatically creates a new **MessageVersion** before routing the message to the endpoint, as well as creating a compatible **MessageVersion** for any response document before returning it to the requesting client application.</span></span>

<span data-ttu-id="d1721-166">送信メッセージの新しい**MessageVersion**を作成するための手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d1721-166">The steps taken to create a new **MessageVersion** for the outbound message are as follows:</span></span>

<span data-ttu-id="d1721-167">**要求の処理**</span><span class="sxs-lookup"><span data-stu-id="d1721-167">**Request processing**</span></span>

- <span data-ttu-id="d1721-168">送信バインド/チャネルの**MessageVersion**を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1721-168">Get the **MessageVersion** of the outbound binding/channel.</span></span>

- <span data-ttu-id="d1721-169">元のメッセージの本文のリーダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d1721-169">Get the body reader for the original message.</span></span>

- <span data-ttu-id="d1721-170">同じアクション、本文閲覧者、および新しい**MessageVersion**を使用して、新しいメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1721-170">Create a new message with the same action, body reader, and a new **MessageVersion**.</span></span>

- <span data-ttu-id="d1721-171"><xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = FaultTo の場合**は、to**、From、、および RelatesTo の各ヘッダーを新しいメッセージにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d1721-171">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="d1721-172">新しいメッセージにすべてのメッセージ プロパティをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d1721-172">Copy all message properties to the new message.</span></span>

- <span data-ttu-id="d1721-173">応答の処理時に使用するために、元の要求メッセージを保存します。</span><span class="sxs-lookup"><span data-stu-id="d1721-173">Store the original request message to use when processing the response.</span></span>

- <span data-ttu-id="d1721-174">新しい要求メッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="d1721-174">Return the new request message.</span></span>

<span data-ttu-id="d1721-175">**応答処理**</span><span class="sxs-lookup"><span data-stu-id="d1721-175">**Response processing**</span></span>

- <span data-ttu-id="d1721-176">元の要求メッセージの**MessageVersion**を取得します。</span><span class="sxs-lookup"><span data-stu-id="d1721-176">Get the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="d1721-177">受信した応答メッセージの本文のリーダーを取得します。</span><span class="sxs-lookup"><span data-stu-id="d1721-177">Get the body reader for the received response message.</span></span>

- <span data-ttu-id="d1721-178">同じアクション、本文閲覧者、および元の要求メッセージの**MessageVersion**を使用して、新しい応答メッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1721-178">Create a new response message with the same action, body reader, and the **MessageVersion** of the original request message.</span></span>

- <span data-ttu-id="d1721-179"><xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A>! = FaultTo の場合**は、to**、From、、および RelatesTo の各ヘッダーを新しいメッセージにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d1721-179">If <xref:System.ServiceModel.Channels.MessageVersion.Addressing%2A> != **Addressing.None**, copy the To, From, FaultTo, and RelatesTo headers to the new message.</span></span>

- <span data-ttu-id="d1721-180">新しいメッセージにメッセージ プロパティをコピーします。</span><span class="sxs-lookup"><span data-stu-id="d1721-180">Copy the message properties to the new message.</span></span>

- <span data-ttu-id="d1721-181">新しい応答メッセージを返します。</span><span class="sxs-lookup"><span data-stu-id="d1721-181">Return the new response message.</span></span>

<span data-ttu-id="d1721-182">既定では、 **Soapprocessingbehavior**は、サービスの開始時に <xref:System.ServiceModel.Routing.RoutingBehavior> によってクライアントエンドポイントに自動的に追加されます。ただし、<xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> プロパティを使用して、すべてのクライアントエンドポイントに SOAP 処理を追加するかどうかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-182">By default, the **SoapProcessingBehavior** is automatically added to the client endpoints by the <xref:System.ServiceModel.Routing.RoutingBehavior> when the service starts; however, you can control whether SOAP processing is added to all client endpoints by using the <xref:System.ServiceModel.Routing.RoutingConfiguration.SoapProcessingEnabled%2A> property.</span></span> <span data-ttu-id="d1721-183">また、この動作を直接特定のエンドポイントに追加したり、SOAP 処理をより細かく制御する必要がある場合に、エンドポイント レベルでこの動作を無効にしたりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d1721-183">You can also add the behavior directly to a specific endpoint and enable or disable this behavior at the endpoint level if a more granular control of SOAP processing is required.</span></span>

> [!NOTE]
> <span data-ttu-id="d1721-184">元の要求メッセージとは異なる MessageVersion を必要とするエンドポイントで SOAP 処理を無効にする場合は、送信先エンドポイントにメッセージを送信する前に必要な SOAP の変更を実行するカスタムのメカニズムを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-184">If SOAP processing is disabled for an endpoint that requires a different MessageVersion than that of the original request message, you must provide a custom mechanism for performing any SOAP modifications that are required before sending the message to the destination endpoint.</span></span>

<span data-ttu-id="d1721-185">次の例では、 **Soapprocessingenabled**プロパティを使用して、 **soapprocessingenabled**がすべてのクライアントエンドポイントに自動的に追加されないようにしています。</span><span class="sxs-lookup"><span data-stu-id="d1721-185">In the following examples, the **soapProcessingEnabled** property is used to prevent the **SoapProcessingBehavior** from being automatically added to all client endpoints.</span></span>

```xml
<behaviors>
  <!--default routing service behavior definition-->
  <serviceBehaviors>
    <behavior name="routingConfiguration">
      <routing filterTableName="filterTable1" soapProcessingEnabled="false"/>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

```csharp
//create the default RoutingConfiguration
RoutingConfiguration rc = new RoutingConfiguration();
rc.SoapProcessingEnabled = false;
```

### <a name="dynamic-configuration"></a><span data-ttu-id="d1721-186">動的構成</span><span class="sxs-lookup"><span data-stu-id="d1721-186">Dynamic Configuration</span></span>

<span data-ttu-id="d1721-187">追加のクライアント エンドポイントを追加する場合、またはメッセージのルーティングに使用されるフィルターを変更する必要がある場合は、ルーティング サービスを介してメッセージを現在受信しているエンドポイントへのサービスを中断しないように、実行時に動的に構成を更新できる手段を用意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-187">When you add additional client endpoints, or need to modify the filters that are used to route messages, you must have a way to update the configuration dynamically at run time to prevent interrupting the service to the endpoints currently receiving messages through the Routing Service.</span></span> <span data-ttu-id="d1721-188">ホスト アプリケーションの構成ファイルまたはコードを変更するだけでは、不十分な場合があります。どちらの方法にもアプリケーションのリサイクルが必要で、現在転送中のメッセージが失われたり、サービスの再起動の処理中にダウンタイムが発生したりする可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="d1721-188">Modifying a configuration file or the code of the host application is not always sufficient, because either method requires recycling the application, which would lead to the potential loss of any messages currently in transit and the potential for downtime while waiting on the service to restart.</span></span>

<span data-ttu-id="d1721-189">**Routingconfiguration**はプログラムによってのみ変更できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-189">You can only modify the **RoutingConfiguration** programmatically.</span></span> <span data-ttu-id="d1721-190">構成ファイルを使用してサービスを初期構成できますが、新しい**Routingconfiguration**を構築し、それをパラメーターとして <xref:System.ServiceModel.Routing.RoutingExtension> サービス拡張機能によって公開されている <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> メソッドに渡すことで、構成を実行時にのみ変更できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-190">While you can initially configure the service by using a configuration file, you can only modify the configuration at run time by constructing a new **RoutingConfiguration** and passing it as a parameter to the <xref:System.ServiceModel.Routing.RoutingExtension.ApplyConfiguration%2A> method exposed by the <xref:System.ServiceModel.Routing.RoutingExtension> service extension.</span></span> <span data-ttu-id="d1721-191">現在転送中のメッセージは、前の構成を使用して引き続きルーティングされますが、 **ApplyConfiguration**の呼び出し後に受信されたメッセージは新しい構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="d1721-191">Any messages currently in transit continue to be routed using the previous configuration, while messages received after the call to **ApplyConfiguration** use the new configuration.</span></span> <span data-ttu-id="d1721-192">次の例では、ルーティング サービスのインスタンスを作成し、次に、構成を変更しています。</span><span class="sxs-lookup"><span data-stu-id="d1721-192">The following example demonstrates creating an instance of the Routing Service and then subsequently modifying the configuration.</span></span>

```csharp
RoutingConfiguration routingConfig = new RoutingConfiguration();
routingConfig.RouteOnHeadersOnly = true;
routingConfig.FilterTable.Add(new MatchAllMessageFilter(), endpointList);
RoutingBehavior routing = new RoutingBehavior(routingConfig);
routerHost.Description.Behaviors.Add(routing);
routerHost.Open();
// Construct a new RoutingConfiguration
RoutingConfiguration rc2 = new RoutingConfiguration();
ServiceEndpoint clientEndpoint = new ServiceEndpoint();
ServiceEndpoint clientEndpoint2 = new ServiceEndpoint();
// Add filters to the FilterTable in the new configuration
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint });
rc2.FilterTable.add(new MatchAllMessageFilter(),
       new List<ServiceEndpoint>() { clientEndpoint2 });
rc2.RouteOnHeadersOnly = false;
// Apply the new configuration to the Routing Service hosted in
routerHost.routerHost.Extensions.Find<RoutingExtension>().ApplyConfiguration(rc2);
```

> [!NOTE]
> <span data-ttu-id="d1721-193">この場合は、新しい構成を渡すことが、ルーティング サービスを更新する唯一の方法です。</span><span class="sxs-lookup"><span data-stu-id="d1721-193">When updating the Routing Service in this manner it is only possible to pass a new configuration.</span></span> <span data-ttu-id="d1721-194">現在の構成から選択した要素のみを変更することも、新しいエントリを現在の構成に追加することもできません。既存の構成に代わる新しい構成を作成して、これを渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-194">It is not possible to modify only select elements of the current configuration or append new entries to the current configuration; you must create and pass a new configuration that replaces the existing one.</span></span>

> [!NOTE]
> <span data-ttu-id="d1721-195">以前の構成を使用して開かれているセッションでは、引き続き、以前の構成が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-195">Any sessions opened using the previous configuration continue using the previous configuration.</span></span> <span data-ttu-id="d1721-196">新しい構成は、新しいセッションでのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-196">The new configuration is only used by new sessions.</span></span>

## <a name="error-handling"></a><span data-ttu-id="d1721-197">エラー処理</span><span class="sxs-lookup"><span data-stu-id="d1721-197">Error Handling</span></span>

<span data-ttu-id="d1721-198">メッセージの送信時に <xref:System.ServiceModel.CommunicationException> が発生した場合は、エラー処理が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-198">If any <xref:System.ServiceModel.CommunicationException> is encountered while attempting to send a message, error handling take place.</span></span> <span data-ttu-id="d1721-199">これらの例外は、一般的に、<xref:System.ServiceModel.EndpointNotFoundException>、<xref:System.ServiceModel.ServerTooBusyException>、<xref:System.ServiceModel.CommunicationObjectFaultedException> など、定義されているクライアント エンドポイントとの通信を試みている間に問題が発生したことを示します。</span><span class="sxs-lookup"><span data-stu-id="d1721-199">These exceptions typically indicate that a problem was encountered while attempting to communicate with the defined client endpoint, such as an <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException>, or <xref:System.ServiceModel.CommunicationObjectFaultedException>.</span></span> <span data-ttu-id="d1721-200">また、エラー処理コードは、<xref:System.TimeoutException> が発生したときに送信を試行します。これは、 **CommunicationException**から派生した別の一般的な例外です。</span><span class="sxs-lookup"><span data-stu-id="d1721-200">The error handling-code will also catch and attempt to retry sending when a <xref:System.TimeoutException> occurs, which is another common exception that is not derived from **CommunicationException**.</span></span>

<span data-ttu-id="d1721-201">上記の例外のいずれかが発生した場合、ルーティング サービスは、バックアップ エンドポイントのリストにフェールオーバーします。</span><span class="sxs-lookup"><span data-stu-id="d1721-201">When one of the preceding exceptions occurs, the Routing Service fails over to a list of backup endpoints.</span></span> <span data-ttu-id="d1721-202">すべてのバックアップ エンドポイントで通信エラーが発生した場合、または、送信先サービス内でのエラーを示す例外がエンドポイントから返された場合は、ルーティング サービスがクライアント アプリケーションにエラーを返します。</span><span class="sxs-lookup"><span data-stu-id="d1721-202">If all backup endpoints fail with a communications failure, or if an endpoint returns an exception that indicates a failure within the destination service, the Routing Service returns a fault to the client application.</span></span>

> [!NOTE]
> <span data-ttu-id="d1721-203">エラー処理機能は、メッセージの送信時とチャネルの終了時に発生した例外をキャプチャーし、処理します。</span><span class="sxs-lookup"><span data-stu-id="d1721-203">The error-handling functionality captures and handles exceptions that occur when attempting to send a message and when attempting to close a channel.</span></span> <span data-ttu-id="d1721-204">エラー処理コードは、通信しているアプリケーションエンドポイントによって作成された例外を検出または処理するためのものではありません。サービスによってスローされた <xref:System.ServiceModel.FaultException> は、 **Faultmessage**としてルーティングサービスで表示され、クライアントにフローバックされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-204">The error-handling code is not intended to detect or handle exceptions created by the application endpoints it is communicating with; a <xref:System.ServiceModel.FaultException> thrown by a service appears at the Routing Service as a **FaultMessage** and is flowed back to the client.</span></span>
>
> <span data-ttu-id="d1721-205">ルーティング サービスによってメッセージを転送しようとしてエラーが発生した場合、通常、ルーティング サービスが行われない場合に受け取る <xref:System.ServiceModel.FaultException> ではなく、<xref:System.ServiceModel.EndpointNotFoundException> をクライアント サイドで受け取る可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-205">If an error occurs when the routing service tries to relay a message, you may  get a <xref:System.ServiceModel.FaultException> on the client side, rather than a <xref:System.ServiceModel.EndpointNotFoundException> you would normally get in the absence of the routing service.</span></span> <span data-ttu-id="d1721-206">入れ子になった例外を調べないと、このようにルーティング サービスによって例外がマスクされて完全な透過性が提供されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-206">A routing service may thus mask exceptions and not provide full transparency unless you examine nested exceptions.</span></span>

### <a name="tracing-exceptions"></a><span data-ttu-id="d1721-207">例外のトレース</span><span class="sxs-lookup"><span data-stu-id="d1721-207">Tracing Exceptions</span></span>

<span data-ttu-id="d1721-208">リスト内のエンドポイントにメッセージを送信できない場合、ルーティングサービスは、結果として生成される例外データをトレースし、例外の詳細をメッセージプロパティとし**て例外と**してアタッチします。</span><span class="sxs-lookup"><span data-stu-id="d1721-208">When sending a message to an endpoint in a list fails, the Routing Service traces the resulting exception data and attaches the exception details as a message property named **Exceptions**.</span></span> <span data-ttu-id="d1721-209">これで、例外データを保存し、ユーザーがメッセージ インスペクターを利用して、プログラムでアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="d1721-209">This preserves the exception data and allows a user programmatic access through a message inspector.</span></span>  <span data-ttu-id="d1721-210">例外データは、メッセージごとにディクショナリに格納されます。ディクショナリでは、エンドポイント名と、そのエンドポイントにメッセージを送信する際に発生した例外の詳細がマップされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-210">The exception data is stored per message in a dictionary that maps the endpoint name to the exception details encountered when trying to send a message to it.</span></span>

### <a name="backup-endpoints"></a><span data-ttu-id="d1721-211">バックアップ エンドポイント</span><span class="sxs-lookup"><span data-stu-id="d1721-211">Backup Endpoints</span></span>

<span data-ttu-id="d1721-212">フィルター テーブル内の各フィルター エントリには、必要に応じて、バックアップ エンドポイントのリストを指定できます。バックアップ エンドポイントは、プライマリ エンドポイントへの送信時に通信エラーが発生した場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-212">Each filter entry within the filter table can optionally specify a list of backup endpoints, which are used in the event of a transmission failure when sending to the primary endpoint.</span></span> <span data-ttu-id="d1721-213">このようなエラーが発生した場合、ルーティング サービスでは、このバックアップ エンドポイントのリスト内の最初のエントリに対して、メッセージの転送を試みます。</span><span class="sxs-lookup"><span data-stu-id="d1721-213">If such a failure occurs, the Routing Service attempts to transmit the message to the first entry in the backup endpoint list.</span></span> <span data-ttu-id="d1721-214">この送信でも通信エラーが発生した場合は、バックアップ リスト内の次のエンドポイントが試されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-214">If this send attempt also encounters a transmission failure, the next endpoint in the backup list is tried.</span></span> <span data-ttu-id="d1721-215">ルーティング サービスは、メッセージの受信が成功するか、すべてのエンドポイントが通信エラーを返すか、またはエンドポイントによって通信エラー以外のエラーが返されるまで、リスト内の各エンドポイントに対してメッセージの送信を続行します。</span><span class="sxs-lookup"><span data-stu-id="d1721-215">The Routing Service continues sending the message to each endpoint in the list until the message is successfully received, all endpoints return a transmission failure, or a non-transmission failure is returned by an endpoint.</span></span>

<span data-ttu-id="d1721-216">次の例では、バックアップ リストを使用するようにルーティング サービスを構成しています。</span><span class="sxs-lookup"><span data-stu-id="d1721-216">The following examples configure the Routing Service to use a backup list.</span></span>

```xml
<routing>
  <filters>
    <!-- Create a MatchAll filter that catches all messages -->
    <filter name="MatchAllFilter1" filterType="MatchAll" />
  </filters>
  <filterTables>
    <!-- Set up the Routing Service's Message Filter Table -->
    <filterTable name="filterTable1">
        <!-- Add an entry that maps the MatchAllMessageFilter to the dead destination -->
        <!-- If that endpoint is down, tell the Routing Service to try the endpoints -->
        <!-- Listed in the backupEndpointList -->
        <add filterName="MatchAllFilter1" endpointName="deadDestination" backupList="backupEndpointList"/>
    </filterTable>
  </filterTables>
  <!-- Create the backup endpoint list -->
  <backupLists>
    <!-- Add an endpoint list that contains the backup destinations -->
    <backupList name="backupEndpointList">
      <add endpointName="realDestination" />
      <add endpointName="backupDestination" />
    </backupList>
  </backupLists>
</routing>
```

```csharp
//create the endpoint list that contains the service endpoints we want to route to
List<ServiceEndpoint> backupList = new List<ServiceEndpoint>();
//add the endpoints in the order that the Routing Service should contact them
//first add the endpoint that we know is down
//clearly, normally you wouldn't know that this endpoint was down by default
backupList.Add(fakeDestination);
//then add the real Destination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationException when sending
//to the previous endpoint in the list.
backupList.Add(realDestination);
//add the backupDestination endpoint
//the Routing Service attempts to send to this endpoint only if it
//encounters a TimeOutException or CommunicationsException when sending
//to the previous endpoints in the list
backupList.Add(backupDestination);
//create the default RoutingConfiguration option
RoutingConfiguration rc = new RoutingConfiguration();
//add a MatchAll filter to the Routing Configuration's filter table
//map it to the list of endpoints defined above
//when a message matches this filter, it is sent to the endpoints in the list in order
//if an endpoint is down or does not respond (which the first endpoint won't
//since the client does not exist), the Routing Service automatically moves the message
//to the next endpoint in the list and try again.
rc.FilterTable.Add(new MatchAllMessageFilter(), backupList);
```

### <a name="supported-error-patterns"></a><span data-ttu-id="d1721-217">サポートされるエラー パターン</span><span class="sxs-lookup"><span data-stu-id="d1721-217">Supported Error Patterns</span></span>

<span data-ttu-id="d1721-218">次の表に、バックアップ エンドポイント リストを使用できるパターンと、各パターンのエラー処理の詳細な説明を示します。</span><span class="sxs-lookup"><span data-stu-id="d1721-218">The following table describes the patterns that are compatible with the use of backup endpoint lists, along with notes describing the details of error handling for specific patterns.</span></span>

|<span data-ttu-id="d1721-219">[パターン]</span><span class="sxs-lookup"><span data-stu-id="d1721-219">Pattern</span></span>|<span data-ttu-id="d1721-220">セッション</span><span class="sxs-lookup"><span data-stu-id="d1721-220">Session</span></span>|<span data-ttu-id="d1721-221">トランザクション</span><span class="sxs-lookup"><span data-stu-id="d1721-221">Transaction</span></span>|<span data-ttu-id="d1721-222">受信コンテキスト</span><span class="sxs-lookup"><span data-stu-id="d1721-222">Receive Context</span></span>|<span data-ttu-id="d1721-223">サポートされるバックアップ リスト</span><span class="sxs-lookup"><span data-stu-id="d1721-223">Backup List Supported</span></span>|<span data-ttu-id="d1721-224">メモ</span><span class="sxs-lookup"><span data-stu-id="d1721-224">Notes</span></span>|
|-------------|-------------|-----------------|---------------------|---------------------------|-----------|
|<span data-ttu-id="d1721-225">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-225">One-Way</span></span>||||<span data-ttu-id="d1721-226">○</span><span class="sxs-lookup"><span data-stu-id="d1721-226">Yes</span></span>|<span data-ttu-id="d1721-227">バックアップ エンドポイントでメッセージの再送を試みます。</span><span class="sxs-lookup"><span data-stu-id="d1721-227">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="d1721-228">このメッセージがマルチキャストされる場合は、エラーが発生したチャネルのメッセージのみが、バックアップ先に移動されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-228">If this message is being multicast, only the message on the failed channel is moved to its backup destination.</span></span>|
|<span data-ttu-id="d1721-229">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-229">One-Way</span></span>||<span data-ttu-id="d1721-230">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-230">✔️</span></span>||<span data-ttu-id="d1721-231">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1721-231">No</span></span>|<span data-ttu-id="d1721-232">例外がスローされ、トランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-232">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="d1721-233">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-233">One-Way</span></span>|||<span data-ttu-id="d1721-234">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-234">✔️</span></span>|<span data-ttu-id="d1721-235">○</span><span class="sxs-lookup"><span data-stu-id="d1721-235">Yes</span></span>|<span data-ttu-id="d1721-236">バックアップ エンドポイントでメッセージの再送を試みます。</span><span class="sxs-lookup"><span data-stu-id="d1721-236">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="d1721-237">メッセージの受信が成功したら、すべての受信コンテキストを完了します。</span><span class="sxs-lookup"><span data-stu-id="d1721-237">After the message is successfully received, complete all receive contexts.</span></span> <span data-ttu-id="d1721-238">どのエンドポイントでもメッセージを受信できなかった場合は、受信コンテキストを完了しません。</span><span class="sxs-lookup"><span data-stu-id="d1721-238">If the message is not successfully received by any endpoint, do not complete the receive context.</span></span><br /><br /> <span data-ttu-id="d1721-239">このメッセージがマルチキャストされる場合は、少なくとも 1 つのエンドポイント (プライマリでもバックアップでも) でメッセージが受信された場合にのみ、受信コンテキストが完了されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-239">When this message is being multicast, the receive context is only completed if the message is successfully received by at least one endpoint (primary or backup).</span></span> <span data-ttu-id="d1721-240">どのマルチキャスト パスのエンドポイントでもメッセージを受信できなかった場合は、受信コンテキストを完了しません。</span><span class="sxs-lookup"><span data-stu-id="d1721-240">If none of the endpoints in any of the multicast paths successfully receive the message, do not complete the receive context.</span></span>|
|<span data-ttu-id="d1721-241">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-241">One-Way</span></span>||<span data-ttu-id="d1721-242">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-242">✔️</span></span>|<span data-ttu-id="d1721-243">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-243">✔️</span></span>|<span data-ttu-id="d1721-244">○</span><span class="sxs-lookup"><span data-stu-id="d1721-244">Yes</span></span>|<span data-ttu-id="d1721-245">前のトランザクションを中止し、新しいトランザクションを作成して、すべてのメッセージを再送します。</span><span class="sxs-lookup"><span data-stu-id="d1721-245">Abort the previous transaction, create a new transaction, and resend all messages.</span></span> <span data-ttu-id="d1721-246">エラーが発生したメッセージは、バックアップ先に転送されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-246">Messages that encountered an error are transmitted to a backup destination.</span></span><br /><br /> <span data-ttu-id="d1721-247">すべての転送が成功するトランザクションが作成されたら、受信コンテキストを完了して、転送をコミットします。</span><span class="sxs-lookup"><span data-stu-id="d1721-247">After a transaction has been created in which all transmissions succeed, complete the receive contexts and commit the transaction.</span></span>|
|<span data-ttu-id="d1721-248">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-248">One-Way</span></span>|<span data-ttu-id="d1721-249">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-249">✔️</span></span>|||<span data-ttu-id="d1721-250">○</span><span class="sxs-lookup"><span data-stu-id="d1721-250">Yes</span></span>|<span data-ttu-id="d1721-251">バックアップ エンドポイントでメッセージの再送を試みます。</span><span class="sxs-lookup"><span data-stu-id="d1721-251">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="d1721-252">マルチキャスト セッションの場合は、エラーが発生したセッションまたはセッションを終了できなかったセッションのメッセージのみが、バックアップ先に送信されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-252">In a multicast scenario only the messages in a session that encountered an error or in a session whose session close failed are resent to backup destinations.</span></span>|
|<span data-ttu-id="d1721-253">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-253">One-Way</span></span>|<span data-ttu-id="d1721-254">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-254">✔️</span></span>|<span data-ttu-id="d1721-255">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-255">✔️</span></span>||<span data-ttu-id="d1721-256">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1721-256">No</span></span>|<span data-ttu-id="d1721-257">例外がスローされ、トランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-257">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="d1721-258">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-258">One-Way</span></span>|<span data-ttu-id="d1721-259">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-259">✔️</span></span>||<span data-ttu-id="d1721-260">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-260">✔️</span></span>|<span data-ttu-id="d1721-261">○</span><span class="sxs-lookup"><span data-stu-id="d1721-261">Yes</span></span>|<span data-ttu-id="d1721-262">バックアップ エンドポイントでメッセージの再送を試みます。</span><span class="sxs-lookup"><span data-stu-id="d1721-262">Attempts to resend the message on a backup endpoint.</span></span> <span data-ttu-id="d1721-263">エラーが発生せずに、すべてのメッセージ送信が完了したら、セッションが他にメッセージがないことを通知して、ルーティング サービスがすべての送信セッション チャネルを終了します。また、受信コンテキストが完了し、受信セッション チャネルが終了します。</span><span class="sxs-lookup"><span data-stu-id="d1721-263">After all message sends complete without error, the session indicates no more messages and the Routing Service successfully closes all outbound session channel(s), all receive contexts are completed, and the inbound session channel is closed.</span></span>|
|<span data-ttu-id="d1721-264">一方向</span><span class="sxs-lookup"><span data-stu-id="d1721-264">One-Way</span></span>|<span data-ttu-id="d1721-265">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-265">✔️</span></span>|<span data-ttu-id="d1721-266">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-266">✔️</span></span>|<span data-ttu-id="d1721-267">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-267">✔️</span></span>|<span data-ttu-id="d1721-268">○</span><span class="sxs-lookup"><span data-stu-id="d1721-268">Yes</span></span>|<span data-ttu-id="d1721-269">現在のトランザクションを中止し、新しいトランザクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d1721-269">Abort the current transaction and create a new one.</span></span> <span data-ttu-id="d1721-270">セッションに含まれる、以前のメッセージをすべて再送します。</span><span class="sxs-lookup"><span data-stu-id="d1721-270">Resend all previous messages in the session.</span></span> <span data-ttu-id="d1721-271">すべてのメッセージ送信が成功したトランザクションが作成され、セッションが他にメッセージがないことを通知すると、すべての送信セッション チャネルが終了します。また、そのトランザクションのすべての受信コンテキストが完了し、受信セッション チャネルが終了して、トランザクションがコミットされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-271">After a transaction has been created in which all messages have been successfully sent and the session indicates no more messages, all the outbound session channels are closed, receive contexts are all completed with the transaction, the inbound session channel is closed, and the transaction is committed.</span></span><br /><br /> <span data-ttu-id="d1721-272">セッションがマルチキャストされる場合は、エラーが発生していないメッセージが、前回と同じ送信先に再送され、エラーが発生したメッセージはバックアップ先に送信されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-272">When the sessions are being multicast the messages that had no error are resent to the same destination as before, and messages that encountered an error are sent to backup destinations.</span></span>|
|<span data-ttu-id="d1721-273">双方向</span><span class="sxs-lookup"><span data-stu-id="d1721-273">Two-Way</span></span>||||<span data-ttu-id="d1721-274">○</span><span class="sxs-lookup"><span data-stu-id="d1721-274">Yes</span></span>|<span data-ttu-id="d1721-275">バックアップ先に送信します。</span><span class="sxs-lookup"><span data-stu-id="d1721-275">Send to a backup destination.</span></span>  <span data-ttu-id="d1721-276">チャネルが応答メッセージを返した後に、元のクライアントに応答を返します。</span><span class="sxs-lookup"><span data-stu-id="d1721-276">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="d1721-277">双方向</span><span class="sxs-lookup"><span data-stu-id="d1721-277">Two-Way</span></span>|<span data-ttu-id="d1721-278">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-278">✔️</span></span>|||<span data-ttu-id="d1721-279">○</span><span class="sxs-lookup"><span data-stu-id="d1721-279">Yes</span></span>|<span data-ttu-id="d1721-280">チャネルのすべてのメッセージをバックアップ先に送信します。</span><span class="sxs-lookup"><span data-stu-id="d1721-280">Send all messages on the channel to a backup destination.</span></span>  <span data-ttu-id="d1721-281">チャネルが応答メッセージを返した後に、元のクライアントに応答を返します。</span><span class="sxs-lookup"><span data-stu-id="d1721-281">After a channel returns a response message, return the response to the original client.</span></span>|
|<span data-ttu-id="d1721-282">双方向</span><span class="sxs-lookup"><span data-stu-id="d1721-282">Two-Way</span></span>||<span data-ttu-id="d1721-283">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-283">✔️</span></span>||<span data-ttu-id="d1721-284">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1721-284">No</span></span>|<span data-ttu-id="d1721-285">例外がスローされ、トランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-285">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="d1721-286">双方向</span><span class="sxs-lookup"><span data-stu-id="d1721-286">Two-Way</span></span>|<span data-ttu-id="d1721-287">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-287">✔️</span></span>|<span data-ttu-id="d1721-288">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-288">✔️</span></span>||<span data-ttu-id="d1721-289">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1721-289">No</span></span>|<span data-ttu-id="d1721-290">例外がスローされ、トランザクションがロールバックされます。</span><span class="sxs-lookup"><span data-stu-id="d1721-290">An exception is thrown and the transaction is rolled back.</span></span>|
|<span data-ttu-id="d1721-291">[両面印刷]</span><span class="sxs-lookup"><span data-stu-id="d1721-291">Duplex</span></span>||||<span data-ttu-id="d1721-292">いいえ</span><span class="sxs-lookup"><span data-stu-id="d1721-292">No</span></span>|<span data-ttu-id="d1721-293">セッションのない二重通信は、現在サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d1721-293">Non-session duplex communication is not currently supported.</span></span>|
|<span data-ttu-id="d1721-294">[両面印刷]</span><span class="sxs-lookup"><span data-stu-id="d1721-294">Duplex</span></span>|<span data-ttu-id="d1721-295">✔️</span><span class="sxs-lookup"><span data-stu-id="d1721-295">✔️</span></span>|||<span data-ttu-id="d1721-296">○</span><span class="sxs-lookup"><span data-stu-id="d1721-296">Yes</span></span>|<span data-ttu-id="d1721-297">バックアップ先に送信します。</span><span class="sxs-lookup"><span data-stu-id="d1721-297">Send to a backup destination.</span></span>|

## <a name="hosting"></a><span data-ttu-id="d1721-298">ホスティング</span><span class="sxs-lookup"><span data-stu-id="d1721-298">Hosting</span></span>

<span data-ttu-id="d1721-299">ルーティング サービスは WCF サービスとして実装されるため、アプリケーション内に自己ホストされるか、IIS または WAS によってホストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-299">Because the Routing Service is implemented as a WCF service, it must be either self-hosted within an application or hosted by IIS or WAS.</span></span> <span data-ttu-id="d1721-300">ルーティング サービスは、IIS、WAS、または Windows サービス アプリケーションにホストし、これらのホスト環境で提供される自動開始機能やライフ サイクル管理機能を利用できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d1721-300">It is recommended that the Routing Service be hosted in either IIS, WAS, or a Windows Service application to take advantage of the automatic start and life-cycle management features available in these hosting environments.</span></span>

<span data-ttu-id="d1721-301">次の例では、アプリケーションでルーティング サービスをホストしています。</span><span class="sxs-lookup"><span data-stu-id="d1721-301">The following example demonstrates hosting the Routing Service in an application.</span></span>

```csharp
using (ServiceHost serviceHost =
                new ServiceHost(typeof(RoutingService)))
```

<span data-ttu-id="d1721-302">ルーティング サービスを IIS または WAS 内でホストするには、サービス ファイル (.svc) を作成するか、サービスの構成ベースのアクティブ化を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-302">To host the Routing Service within IIS or WAS, you must either create a service file (.svc) or use configuration-based activation of the service.</span></span> <span data-ttu-id="d1721-303">サービス ファイルを使用する場合は、Service パラメーターを使用して <xref:System.ServiceModel.Routing.RoutingService> を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-303">When using a service file, you must specify the <xref:System.ServiceModel.Routing.RoutingService> using the Service parameter.</span></span> <span data-ttu-id="d1721-304">次の例は、IIS または WAS によるルーティング サービスのホストに使用できるサンプルのサービス ファイルです。</span><span class="sxs-lookup"><span data-stu-id="d1721-304">The following example contains a sample service file that can be used to host the Routing Service with IIS or WAS.</span></span>

```aspx-csharp
<%@ ServiceHost Language="C#" Debug="true" Service="System.ServiceModel.Routing.RoutingService,
     System.ServiceModel.Routing, version=4.0.0.0, Culture=neutral,
     PublicKeyToken=31bf3856ad364e35" %>
```

## <a name="routing-service-and-impersonation"></a><span data-ttu-id="d1721-305">ルーティング サービスと偽装</span><span class="sxs-lookup"><span data-stu-id="d1721-305">Routing Service and Impersonation</span></span>

<span data-ttu-id="d1721-306">WCF ルーティング サービスは、メッセージの送受信両方の偽装で使用できます。</span><span class="sxs-lookup"><span data-stu-id="d1721-306">The WCF Routing Service can be used with impersonation for both sending and receiving messages.</span></span> <span data-ttu-id="d1721-307">偽装に関する通常の Windows のすべての制約が適用されます。</span><span class="sxs-lookup"><span data-stu-id="d1721-307">All of the usual Windows constraints of impersonation apply.</span></span> <span data-ttu-id="d1721-308">独自のサービスを作成する際、偽装を使用するためにサービスまたはアカウントのアクセス許可を設定する必要があった場合は、ルーティング サービスで偽装を使用する場合と同じ手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-308">If you would have needed to set up service or account permissions to use impersonation when writing your own service, then you’ll have to do those same steps to use impersonation with the routing service.</span></span> <span data-ttu-id="d1721-309">詳細については、「[委任と偽装](delegation-and-impersonation-with-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1721-309">For more information, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>

<span data-ttu-id="d1721-310">ルーティング サービスでの偽装には、ASP.NET 互換モードで ASP.NET の偽装を使用するか、偽装を許可するように構成された Windows 資格情報を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-310">Impersonation with the routing service requires either the use of ASP.NET impersonation while in ASP.NET compatibility mode or the use of Windows credentials that have been configured to allow impersonation.</span></span> <span data-ttu-id="d1721-311">ASP.NET 互換モードの詳細については、「 [WCF Services と ASP.NET](wcf-services-and-aspnet.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d1721-311">For more information about ASP.NET compatibility mode, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span>

> [!WARNING]
> <span data-ttu-id="d1721-312">WCF ルーティング サービスは、基本認証での偽装をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="d1721-312">The WCF Routing Service does not support impersonation with basic authentication.</span></span>

<span data-ttu-id="d1721-313">ルーティング サービスで ASP.NET の偽装を使用するには、サービス ホスティング環境で ASP.NET 互換モードを有効にします。</span><span class="sxs-lookup"><span data-stu-id="d1721-313">To use ASP.NET impersonation with the routing service, enable ASP.NET compatibility mode on the service hosting environment.</span></span> <span data-ttu-id="d1721-314">ルーティング サービスは既に ASP.NET 互換モードを許可するようにマークされているため、偽装が自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="d1721-314">The routing service has already been marked as allowing ASP.NET compatibility mode and impersonation will automatically be enabled.</span></span> <span data-ttu-id="d1721-315">偽装は、ルーティング サービスとの ASP.NET 統合で唯一サポートされている用法です。</span><span class="sxs-lookup"><span data-stu-id="d1721-315">Impersonation is the only supported use of ASP.NET integration with the routing service.</span></span>

<span data-ttu-id="d1721-316">ルーティング サービスで Windows 資格情報の偽装を使用するには、資格情報とサービスの両方を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-316">To use Windows credential impersonation with the routing service you need to configure both the credentials and the service.</span></span> <span data-ttu-id="d1721-317">クライアント資格情報オブジェクト (<xref:System.ServiceModel.Security.WindowsClientCredential> からアクセス可能な <xref:System.ServiceModel.ChannelFactory>) は、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> プロパティを定義します。偽装を許可するには、このプロパティを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-317">The client credentials object (<xref:System.ServiceModel.Security.WindowsClientCredential>, accessable from the <xref:System.ServiceModel.ChannelFactory>) defines an <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property that must be set to permit impersonation.</span></span> <span data-ttu-id="d1721-318">最後に、サービスで、<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 動作を構成して、`ImpersonateCallerForAllOperations` を `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d1721-318">Finally, on the service you need to configure the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> behavior to set `ImpersonateCallerForAllOperations` to `true`.</span></span> <span data-ttu-id="d1721-319">ルーティング サービスでは、偽装が有効になっているメッセージを転送するためのクライアントを作成するかどうかを、このフラグを使用して決定します。</span><span class="sxs-lookup"><span data-stu-id="d1721-319">The routing service uses this flag to decide whether to create the clients for forwarding messages with impersonation enabled.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1721-320">関連項目</span><span class="sxs-lookup"><span data-stu-id="d1721-320">See also</span></span>

- [<span data-ttu-id="d1721-321">メッセージ フィルター</span><span class="sxs-lookup"><span data-stu-id="d1721-321">Message Filters</span></span>](message-filters.md)
- [<span data-ttu-id="d1721-322">ルーティング コントラクト</span><span class="sxs-lookup"><span data-stu-id="d1721-322">Routing Contracts</span></span>](routing-contracts.md)
- [<span data-ttu-id="d1721-323">フィルターの選択</span><span class="sxs-lookup"><span data-stu-id="d1721-323">Choosing a Filter</span></span>](choosing-a-filter.md)
