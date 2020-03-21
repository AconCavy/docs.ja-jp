---
title: 動作を使用したランタイムの構成と拡張
ms.date: 03/30/2017
helpviewer_keywords:
- attaching extensions using behaviors [WCF]
ms.assetid: 149b99b6-6eb6-4f45-be22-c967279677d9
ms.openlocfilehash: 67db06649d6059ff6b6e6fb8d84058621fcc7dab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185653"
---
# <a name="configuring-and-extending-the-runtime-with-behaviors"></a><span data-ttu-id="adede-102">動作を使用したランタイムの構成と拡張</span><span class="sxs-lookup"><span data-stu-id="adede-102">Configuring and Extending the Runtime with Behaviors</span></span>
<span data-ttu-id="adede-103">動作を使用すると、既定の動作を変更したり、サービス構成を検査および検証したり、Windows 通信基盤 (WCF) クライアントおよびサービス アプリケーションでランタイム動作を変更したりするカスタム拡張機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="adede-103">Behaviors enable you to modify default behavior and add custom extensions that inspect and validate service configuration or modify runtime behavior in Windows Communication Foundation (WCF) client and service applications.</span></span> <span data-ttu-id="adede-104">ここでは、動作インターフェイスとその実装方法について説明します。また、動作インターフェイスをサービスの説明 (サービス アプリケーションの場合) またはエンドポイント (クライアント アプリケーションの場合) にプログラムによって追加する方法と、構成ファイル内で追加する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="adede-104">This topic describes the behavior interfaces, how to implement them, and how to add them to the service description (in a service application) or endpoint (in a client application) programmatically or in a configuration file.</span></span> <span data-ttu-id="adede-105">システム指定の動作の使用の詳細については、「[サービスランタイム動作の指定](../specifying-service-run-time-behavior.md)」および「クライアントランタイム[動作の指定](../specifying-client-run-time-behavior.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adede-105">For more information about using system-provided behaviors, see [Specifying Service Run-Time Behavior](../specifying-service-run-time-behavior.md) and [Specifying Client Run-Time Behavior](../specifying-client-run-time-behavior.md).</span></span>  
  
## <a name="behaviors"></a><span data-ttu-id="adede-106">動作</span><span class="sxs-lookup"><span data-stu-id="adede-106">Behaviors</span></span>  
 <span data-ttu-id="adede-107">動作の種類は、WCF サービスまたは WCF クライアントを実行するランタイムを作成する Windows 通信基盤 (WCF) によってこれらのオブジェクトを使用する前に、サービスまたはサービス エンドポイントの記述オブジェクト (それぞれサービスまたはクライアント) に追加されます。</span><span class="sxs-lookup"><span data-stu-id="adede-107">Behavior types are added to the service or service endpoint description objects (on the service or client, respectively) before those objects are used by Windows Communication Foundation (WCF) to create a runtime that executes a WCF service or a WCF client.</span></span> <span data-ttu-id="adede-108">ランタイムの構築プロセスでこれらの動作を呼び出すと、コントラクト、バインディング、およびアドレスによって構築されたランタイムを変更するランタイム プロパティやランタイム メソッドにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="adede-108">When these behaviors are called during the runtime construction process they are then able to access runtime properties and methods that modify the runtime constructed by the contract, bindings, and addresses.</span></span>  
  
### <a name="behavior-methods"></a><span data-ttu-id="adede-109">動作メソッド</span><span class="sxs-lookup"><span data-stu-id="adede-109">Behavior Methods</span></span>  
 <span data-ttu-id="adede-110">すべての動作で、`AddBindingParameters` メソッド、`ApplyDispatchBehavior` メソッド、`Validate` メソッド、および `ApplyClientBehavior` メソッドを使用できます。ただし、<xref:System.ServiceModel.Description.IServiceBehavior> には、例外が 1 つあります。`ApplyClientBehavior` はクライアントで実行できないため、このメソッドを実装していません。</span><span class="sxs-lookup"><span data-stu-id="adede-110">All behaviors have an `AddBindingParameters` method, an `ApplyDispatchBehavior` method, a `Validate` method, and an `ApplyClientBehavior` method with one exception: Because <xref:System.ServiceModel.Description.IServiceBehavior> cannot execute in a client, it does not implement `ApplyClientBehavior`.</span></span>  
  
- <span data-ttu-id="adede-111">カスタム オブジェクトを変更したり、ランタイム構築時に使用するためにカスタム バインディングがアクセスできるコレクションにカスタム オブジェクトを追加したりするには、`AddBindingParameters` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-111">Use the `AddBindingParameters` method to modify or add custom objects to a collection that custom bindings can access for their use when the runtime is constructed.</span></span> <span data-ttu-id="adede-112">たとえば、これによって、チャネルを構築する方法に影響するが、チャネル開発者には知られていない保護要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="adede-112">For example, this how protection requirements are specified that affect the way the channel is built, but are not known by the channel developer.</span></span>  
  
- <span data-ttu-id="adede-113">説明ツリーと対応するランタイム オブジェクトを検査し、特定の基準セットに従っていることを確認するには、`Validate` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-113">Use the `Validate` method to examine the description tree and corresponding runtime object to ensure it conforms to some set of criteria.</span></span>  
  
- <span data-ttu-id="adede-114">説明ツリーを検査し、サービスまたはクライアントの特定のスコープのランタイムを変更するには、`ApplyDispatchBehavior` メソッドと `ApplyClientBehavior` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-114">Use the `ApplyDispatchBehavior` and `ApplyClientBehavior` methods to examine the description tree and modify the runtime for a particular scope on either the service or the client.</span></span> <span data-ttu-id="adede-115">また、拡張オブジェクトを挿入することもできます。</span><span class="sxs-lookup"><span data-stu-id="adede-115">You can also insert extension objects as well.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="adede-116">これらのメソッドでは説明ツリーが提供されますが、説明ツリーは検査にのみ使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-116">Although a description tree is provided in these methods, it is for examination only.</span></span> <span data-ttu-id="adede-117">説明ツリーを変更すると、動作は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="adede-117">If a description tree is modified, the behavior is undefined.</span></span>  
  
 <span data-ttu-id="adede-118">変更できるプロパティと実装できるカスタマイズ インターフェイスには、サービスおよびクライアントのランタイム クラスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="adede-118">The properties you can modify and the customization interfaces you can implement are accessed through the service and client runtime classes.</span></span> <span data-ttu-id="adede-119">サービス型は、<xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラスと <xref:System.ServiceModel.Dispatcher.DispatchOperation> クラスです。</span><span class="sxs-lookup"><span data-stu-id="adede-119">The service types are the <xref:System.ServiceModel.Dispatcher.DispatchRuntime> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes.</span></span> <span data-ttu-id="adede-120">クライアント型は、<xref:System.ServiceModel.Dispatcher.ClientRuntime> クラスと <xref:System.ServiceModel.Dispatcher.ClientOperation> クラスです。</span><span class="sxs-lookup"><span data-stu-id="adede-120">The client types are the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.ClientOperation> classes.</span></span> <span data-ttu-id="adede-121"><xref:System.ServiceModel.Dispatcher.ClientRuntime> クラスと <xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラスは、それぞれクライアント全体またはサービス全体のランタイム プロパティと拡張コレクションにアクセスするための拡張エントリ ポイントです。</span><span class="sxs-lookup"><span data-stu-id="adede-121">The <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes are the extensibility entry points to access client-wide and service-wide runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="adede-122">同様に、<xref:System.ServiceModel.Dispatcher.ClientOperation> クラスと <xref:System.ServiceModel.Dispatcher.DispatchOperation> クラスは、それぞれクライアント操作またはサービス操作のランタイム プロパティと拡張コレクションを公開します。</span><span class="sxs-lookup"><span data-stu-id="adede-122">Similarly, the <xref:System.ServiceModel.Dispatcher.ClientOperation> and  <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes expose client operation and service operation runtime properties and extension collections, respectively.</span></span> <span data-ttu-id="adede-123">ただし、必要に応じて、操作ランタイム オブジェクトからより広いスコープのランタイム オブジェクトにアクセスできます。また、逆の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="adede-123">You can, however, access the wider scoped runtime object from the operation runtime object and vice versa if need be.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adede-124">クライアントの実行動作を変更するために使用できるランタイム プロパティと拡張機能の種類については、「[クライアントの拡張](extending-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adede-124">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a client, see [Extending Clients](extending-clients.md).</span></span> <span data-ttu-id="adede-125">サービス ディスパッチャの実行動作を変更するために使用できるランタイム プロパティと拡張機能の種類については、「[ディスパッチャーの拡張](extending-dispatchers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adede-125">For a discussion of runtime properties and extension types that you can use to modify the execution behavior of a service dispatcher, see [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
 <span data-ttu-id="adede-126">ほとんどの WCF ユーザーは、ランタイムと直接対話しません。代わりに、エンドポイント、コントラクト、バインディング、アドレス、およびクラスまたは構成ファイルの動作の動作属性などのコア プログラミング モデルの構成を使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-126">Most WCF users do not interact with the runtime directly; instead they use core programming model constructs like endpoints, contracts, bindings, addresses, and behavior attributes on classes or behaviors in configuration files.</span></span> <span data-ttu-id="adede-127">これらの構成要素は *、説明ツリーで記述*されるサービスまたはクライアントをサポートするランタイムを構築するための完全な仕様である記述ツリーを構成します。</span><span class="sxs-lookup"><span data-stu-id="adede-127">These constructs make up the *description tree*, which is the complete specification for constructing a runtime to support a service or client described by the description tree.</span></span>  
  
 <span data-ttu-id="adede-128">WCF には、次の 4 種類の動作があります。</span><span class="sxs-lookup"><span data-stu-id="adede-128">There are four kinds of behaviors in WCF:</span></span>  
  
- <span data-ttu-id="adede-129">サービスの動作 (<xref:System.ServiceModel.Description.IServiceBehavior> 型) : <xref:System.ServiceModel.ServiceHostBase> を含むサービス ランタイム全体のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="adede-129">Service behaviors (<xref:System.ServiceModel.Description.IServiceBehavior> types) enable the customization of the entire service runtime including <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
- <span data-ttu-id="adede-130">エンドポイントの動作 (<xref:System.ServiceModel.Description.IEndpointBehavior> 型) : サービス エンドポイントと、関連する <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> オブジェクトのカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="adede-130">Endpoint behaviors (<xref:System.ServiceModel.Description.IEndpointBehavior> types) enable the customization of service endpoints and their associated <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> objects.</span></span>  
  
- <span data-ttu-id="adede-131">コントラクトの動作 (<xref:System.ServiceModel.Description.IContractBehavior> 型) : <xref:System.ServiceModel.Dispatcher.ClientRuntime> クラス (クライアント アプリケーションの場合) と、<xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラス (サービス アプリケーションの場合) のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="adede-131">Contract behaviors (<xref:System.ServiceModel.Description.IContractBehavior> types) enable the customization of both the <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes in client and service applications, respectively.</span></span>  
  
- <span data-ttu-id="adede-132">操作の動作 (<xref:System.ServiceModel.Description.IOperationBehavior> 型) : <xref:System.ServiceModel.Dispatcher.ClientOperation> クラス (クライアントの場合) と、<xref:System.ServiceModel.Dispatcher.DispatchOperation> クラス (サービスの場合) のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="adede-132">Operation behaviors (<xref:System.ServiceModel.Description.IOperationBehavior> types) enable the customization of the <xref:System.ServiceModel.Dispatcher.ClientOperation> and <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes, again, on the client and service.</span></span>  
  
 <span data-ttu-id="adede-133">カスタム属性を実装するか、アプリケーション構成ファイルを使用することにより、これらの動作をさまざまな説明オブジェクトに追加できます。また、適切な説明オブジェクトの動作コレクションに直接追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="adede-133">You can add these behaviors to the various description objects by implementing custom attributes, using application configuration files, or directly by adding them to the behaviors collection on the appropriate description object.</span></span> <span data-ttu-id="adede-134">ただし、<xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.ServiceHost> で <xref:System.ServiceModel.ChannelFactory%601> を呼び出す前に、サービス説明オブジェクトまたはサービス エンドポイント説明オブジェクトに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adede-134">The must, however, be added to a service description or service endpoint description object prior to calling <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on the <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>.</span></span>  
  
### <a name="behavior-scopes"></a><span data-ttu-id="adede-135">動作のスコープ</span><span class="sxs-lookup"><span data-stu-id="adede-135">Behavior Scopes</span></span>  
 <span data-ttu-id="adede-136">4 種類の動作があり、それぞれランタイム アクセスの特定のスコープに対応しています。</span><span class="sxs-lookup"><span data-stu-id="adede-136">There are four behavior types, each of which corresponds to a particular scope of runtime access.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="adede-137">サービスの動作</span><span class="sxs-lookup"><span data-stu-id="adede-137">Service Behaviors</span></span>  
 <span data-ttu-id="adede-138"><xref:System.ServiceModel.Description.IServiceBehavior> を実装するサービスの動作は、サービス ランタイム全体を変更する主要機構です。</span><span class="sxs-lookup"><span data-stu-id="adede-138">Service behaviors, which implement <xref:System.ServiceModel.Description.IServiceBehavior>, are the primary mechanism by which you modify the entire service runtime.</span></span> <span data-ttu-id="adede-139">サービスの動作をサービスに追加する場合、3 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="adede-139">There are three mechanisms for adding service behaviors to a service.</span></span>  
  
1. <span data-ttu-id="adede-140">サービス クラスの属性を使用する方法。</span><span class="sxs-lookup"><span data-stu-id="adede-140">Using an attribute on the service class.</span></span>  <span data-ttu-id="adede-141"><xref:System.ServiceModel.ServiceHost> を構築すると、<xref:System.ServiceModel.ServiceHost> 実装は、リフレクションを使用してそのサービス型の属性セットを検出します。</span><span class="sxs-lookup"><span data-stu-id="adede-141">When a <xref:System.ServiceModel.ServiceHost> is constructed, the <xref:System.ServiceModel.ServiceHost> implementation uses reflection to discover the set of attributes on the type of the service.</span></span> <span data-ttu-id="adede-142">これらの属性のいずれかが <xref:System.ServiceModel.Description.IServiceBehavior> の実装である場合、<xref:System.ServiceModel.Description.ServiceDescription> の動作コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="adede-142">If any of those attributes are implementations of <xref:System.ServiceModel.Description.IServiceBehavior>, they are added to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="adede-143">これにより、これらの動作はサービス ランタイムの構築に参加できます。</span><span class="sxs-lookup"><span data-stu-id="adede-143">This allows those behaviors to participate in the construction of the service run time.</span></span>  
  
2. <span data-ttu-id="adede-144">プログラムによって、<xref:System.ServiceModel.Description.ServiceDescription> の動作コレクションに動作を追加する方法。</span><span class="sxs-lookup"><span data-stu-id="adede-144">Programmatically adding the behavior to the behaviors collection on <xref:System.ServiceModel.Description.ServiceDescription>.</span></span> <span data-ttu-id="adede-145">これを行うには、次のコード行を使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-145">This can be accomplished with the following lines of code:</span></span>  
  
    ```csharp
    ServiceHost host = new ServiceHost(/* Parameters */);  
    host.Description.Behaviors.Add(/* Service Behavior */);  
    ```  
  
3. <span data-ttu-id="adede-146">構成を拡張するカスタムの <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を実装する方法。</span><span class="sxs-lookup"><span data-stu-id="adede-146">Implementing a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span> <span data-ttu-id="adede-147">これにより、アプリケーション構成ファイルからサービスの動作を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="adede-147">This enables the use of the service behavior from application configuration files.</span></span>  
  
 <span data-ttu-id="adede-148">WCF のサービス動作の例には、<xref:System.ServiceModel.ServiceBehaviorAttribute>属性<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>、、および動作が<xref:System.ServiceModel.Description.ServiceMetadataBehavior>含まれます。</span><span class="sxs-lookup"><span data-stu-id="adede-148">Examples of service behaviors in WCF include the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute, the <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>, and the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="adede-149">コントラクトの動作</span><span class="sxs-lookup"><span data-stu-id="adede-149">Contract Behaviors</span></span>  
 <span data-ttu-id="adede-150"><xref:System.ServiceModel.Description.IContractBehavior> インターフェイスを実装するコントラクトの動作は、コントラクト全体にわたり、クライアント ランタイムとサービス ランタイムを拡張する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-150">Contract behaviors, which implement the <xref:System.ServiceModel.Description.IContractBehavior> interface, are used to extend both the client and service runtime across a contract.</span></span>  
  
 <span data-ttu-id="adede-151">コントラクトの動作をコントラクトに追加する場合、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="adede-151">There are two mechanisms for adding contract behaviors to a contract.</span></span>  <span data-ttu-id="adede-152">1 つは、コントラクト インターフェイスで使用するカスタム属性を作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="adede-152">The first mechanism is to create a custom attribute to be used on the contract interface.</span></span> <span data-ttu-id="adede-153">コントラクト インターフェイスが<xref:System.ServiceModel.ServiceHost><xref:System.ServiceModel.ChannelFactory%601>または に渡されると、WCF はインターフェイスの属性を調べます。</span><span class="sxs-lookup"><span data-stu-id="adede-153">When a contract interface is passed to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory%601>, WCF examines the attributes on the interface.</span></span> <span data-ttu-id="adede-154">属性のいずれかが <xref:System.ServiceModel.Description.IContractBehavior> の実装である場合、そのインターフェイス用に作成された <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> の動作コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="adede-154">If any attributes are implementations of <xref:System.ServiceModel.Description.IContractBehavior>, those are added to the behaviors collection on the <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType> created for that interface.</span></span>  
  
 <span data-ttu-id="adede-155">カスタム コントラクトの動作属性に <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> を実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="adede-155">You can also implement the <xref:System.ServiceModel.Description.IContractBehaviorAttribute?displayProperty=nameWithType> on the custom contract behavior attribute.</span></span> <span data-ttu-id="adede-156">この場合、適用先に応じて動作は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="adede-156">In this case, the behavior is as follows when applied to:</span></span>  
  
 <span data-ttu-id="adede-157">•コントラクト インターフェイスに適用した場合。</span><span class="sxs-lookup"><span data-stu-id="adede-157">•A contract interface.</span></span> <span data-ttu-id="adede-158">この場合、動作は、任意のエンドポイントでその型のすべてのコントラクトに適用され、WCF は、プロパティの値を<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType>無視します。</span><span class="sxs-lookup"><span data-stu-id="adede-158">In this case, the behavior is applied to all contracts of that type in any endpoint and WCF ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="adede-159">•サービス クラスに適用した場合。</span><span class="sxs-lookup"><span data-stu-id="adede-159">•A service class.</span></span> <span data-ttu-id="adede-160">この場合、動作はコントラクトが <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> プロパティの値であるエンドポイントにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-160">In this case, the behavior is applied only to endpoints the contract of which is the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="adede-161">•コールバック クラスに適用した場合。</span><span class="sxs-lookup"><span data-stu-id="adede-161">•A callback class.</span></span> <span data-ttu-id="adede-162">この場合、動作は双方向クライアントのエンドポイントに適用され、WCF はプロパティの値を<xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A>無視します。</span><span class="sxs-lookup"><span data-stu-id="adede-162">In this case, the behavior is applied to the duplex client's endpoint and WCF ignores the value of the <xref:System.ServiceModel.Description.IContractBehaviorAttribute.TargetContract%2A> property.</span></span>  
  
 <span data-ttu-id="adede-163">2 番目の方法として、<xref:System.ServiceModel.Description.ContractDescription> の動作コレクションに動作を追加する方法があります。</span><span class="sxs-lookup"><span data-stu-id="adede-163">The second mechanism is to add the behavior to the behaviors collection on a <xref:System.ServiceModel.Description.ContractDescription>.</span></span>  
  
 <span data-ttu-id="adede-164">WCF のコントラクト動作の例には、<xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType>属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="adede-164">Examples of contract behaviors in WCF include the <xref:System.ServiceModel.DeliveryRequirementsAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="adede-165">詳細および例については、リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="adede-165">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="endpoint-behaviors"></a><span data-ttu-id="adede-166">エンドポイントの動作</span><span class="sxs-lookup"><span data-stu-id="adede-166">Endpoint Behaviors</span></span>  
 <span data-ttu-id="adede-167"><xref:System.ServiceModel.Description.IEndpointBehavior> を実装するエンドポイントの動作は、特定のエンドポイントのサービス ランタイムまたはクライアント ランタイム全体を変更する主要機構です。</span><span class="sxs-lookup"><span data-stu-id="adede-167">Endpoint behaviors, which implement <xref:System.ServiceModel.Description.IEndpointBehavior>, are the primary mechanism by which you modify the entire service or client run time for a specific endpoint.</span></span>  
  
 <span data-ttu-id="adede-168">エンドポイントの動作をサービスに追加する場合、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="adede-168">There are two mechanisms for adding endpoint behaviors to a service.</span></span>  
  
1. <span data-ttu-id="adede-169"><xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> プロパティに動作を追加する方法。</span><span class="sxs-lookup"><span data-stu-id="adede-169">Add the behavior to the <xref:System.ServiceModel.Description.ServiceEndpoint.Behaviors%2A> property.</span></span>  
  
2. <span data-ttu-id="adede-170">構成を拡張するカスタムの <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を実装する方法。</span><span class="sxs-lookup"><span data-stu-id="adede-170">Implement a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> that extends configuration.</span></span>  
  
 <span data-ttu-id="adede-171">詳細および例については、リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="adede-171">For more information and an example, see the reference topic.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="adede-172">操作の動作</span><span class="sxs-lookup"><span data-stu-id="adede-172">Operation Behaviors</span></span>  
 <span data-ttu-id="adede-173"><xref:System.ServiceModel.Description.IOperationBehavior> インターフェイスを実装する操作の動作は、各操作のクライアント ランタイムとサービス ランタイムを拡張する際に使用します。</span><span class="sxs-lookup"><span data-stu-id="adede-173">Operation behaviors, which implement the <xref:System.ServiceModel.Description.IOperationBehavior> interface, are used to extend both the client and service runtime for each operation.</span></span>  
  
 <span data-ttu-id="adede-174">操作の動作を操作に追加する場合、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="adede-174">There are two mechanisms for adding operation behaviors to an operation.</span></span> <span data-ttu-id="adede-175">1 つは、操作をモデル化するメソッドで使用するカスタム属性を作成する方法です。</span><span class="sxs-lookup"><span data-stu-id="adede-175">The first mechanism is to create a custom attribute to be used on the method that models the operation.</span></span> <span data-ttu-id="adede-176">または に操作が追加<xref:System.ServiceModel.ServiceHost>されると、WCF<xref:System.ServiceModel.ChannelFactory>は、その操作<xref:System.ServiceModel.Description.IOperationBehavior>のために作成された動作コレクションに属性を<xref:System.ServiceModel.Description.OperationDescription>追加します。</span><span class="sxs-lookup"><span data-stu-id="adede-176">When an operation is added to either a <xref:System.ServiceModel.ServiceHost> or a <xref:System.ServiceModel.ChannelFactory>, WCF adds any  <xref:System.ServiceModel.Description.IOperationBehavior> attributes to the behaviors collection on the <xref:System.ServiceModel.Description.OperationDescription> created for that operation.</span></span>  
  
 <span data-ttu-id="adede-177">2 番目の機構は、構成された <xref:System.ServiceModel.Description.OperationDescription> の動作コレクションに動作を直接追加します。</span><span class="sxs-lookup"><span data-stu-id="adede-177">The second mechanism is by directly adding the behavior to the behaviors collection on a constructed <xref:System.ServiceModel.Description.OperationDescription>.</span></span>  
  
 <span data-ttu-id="adede-178">WCF での操作の動作の例<xref:System.ServiceModel.OperationBehaviorAttribute>として、<xref:System.ServiceModel.TransactionFlowAttribute>および が含まれます。</span><span class="sxs-lookup"><span data-stu-id="adede-178">Examples of operation behaviors in WCF include the <xref:System.ServiceModel.OperationBehaviorAttribute> and the <xref:System.ServiceModel.TransactionFlowAttribute>.</span></span>  
  
 <span data-ttu-id="adede-179">詳細および例については、リファレンス トピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="adede-179">For more information and an example, see the reference topic.</span></span>  
  
### <a name="using-configuration-to-create-behaviors"></a><span data-ttu-id="adede-180">構成を使用した動作の作成</span><span class="sxs-lookup"><span data-stu-id="adede-180">Using Configuration to Create Behaviors</span></span>  
 <span data-ttu-id="adede-181">サービス、エンドポイント、およびコントラクトの動作は、コードまたは属性を使用して指定するように設計できます。アプリケーション構成ファイルまたは Web 構成ファイルを使用して構成できるのは、サービスの動作とエンドポイントの動作だけです。</span><span class="sxs-lookup"><span data-stu-id="adede-181">Service and endpoint, and contract behaviors can by designed to be specified in code or using attributes; only service and endpoint behaviors can be configured using application or Web configuration files.</span></span> <span data-ttu-id="adede-182">属性を使用して動作を公開した場合、開発者は、実行時に追加、削除、または変更できない動作をコンパイル時に指定できます。</span><span class="sxs-lookup"><span data-stu-id="adede-182">Exposing behaviors using attributes allows developers to specify a behavior at compilation-time that cannot be added, removed, or modified at runtime.</span></span> <span data-ttu-id="adede-183">多くの場合、これはサービスの適切な操作のために常に必要となる動作に適しています (<xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> 属性に対するトランザクション関連のパラメーターなど)。</span><span class="sxs-lookup"><span data-stu-id="adede-183">This is often suitable for behaviors that are always required for the correct operation of a service (for example, the transaction-related parameters to the <xref:System.ServiceModel.ServiceBehaviorAttribute?displayProperty=nameWithType> attribute).</span></span> <span data-ttu-id="adede-184">構成を使用して動作を公開すると、開発者はサービス展開者に動作の仕様と構成を委ねることができます。</span><span class="sxs-lookup"><span data-stu-id="adede-184">Exposing behaviors using configuration allows developers to leave the specification and configuration of those behaviors to those who deploy the service.</span></span> <span data-ttu-id="adede-185">これは、動作がオプション コンポーネント、または他の展開固有の構成 (サービスまたはサービスの特定の承認構成についてメタデータを公開するかどうかなど) である場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="adede-185">This is suitable for behaviors that are optional components or other deployment-specific configuration, such as whether metadata is exposed for the service or the particular authorization configuration for a service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adede-186">企業のアプリケーション ポリシーを machine.config 構成ファイルに挿入し、これらの項目をロックダウンすることで、ポリシーを適用する構成をサポートする動作を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="adede-186">You can also use behaviors that support configuration to enforce company application policies by inserting them into the machine.config configuration file and locking those items down.</span></span> <span data-ttu-id="adede-187">説明と例については、「[方法 : エンタープライズのエンドポイントをロックダウン](how-to-lock-down-endpoints-in-the-enterprise.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="adede-187">For a description and an example, see [How to: Lock Down Endpoints in the Enterprise](how-to-lock-down-endpoints-in-the-enterprise.md).</span></span>  
  
 <span data-ttu-id="adede-188">構成を使用して動作を公開するには、開発者は <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> の派生クラスを作成し、その拡張を構成に登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adede-188">To expose a behavior using configuration, a developer must create a derived class of <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> and then register that extension with configuration.</span></span>  
  
 <span data-ttu-id="adede-189"><xref:System.ServiceModel.Description.IEndpointBehavior> で <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を実装する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="adede-189">The following code example shows how an  <xref:System.ServiceModel.Description.IEndpointBehavior> implements <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>:</span></span>  
  
```csharp
// BehaviorExtensionElement members  
public override Type BehaviorType  
{  
  get { return typeof(EndpointBehaviorMessageInspector); }  
}  
  
protected override object CreateBehavior()  
{  
  return new EndpointBehaviorMessageInspector();  
}  
```  
  
 <span data-ttu-id="adede-190">構成システムでカスタムの <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> を読み込むには、拡張として登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adede-190">In order for the configuration system to load a custom <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>, it must be registered as an extension.</span></span> <span data-ttu-id="adede-191">上記のエンドポイントの動作の構成ファイルを次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="adede-191">The following code example shows the configuration file for the preceding endpoint behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
        name="Microsoft.WCF.Documentation.SampleService"  
        behaviorConfiguration="metadataSupport"  
      >  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8080/ServiceMetadata" />  
          </baseAddresses>  
        </host>  
        <endpoint  
          address="/SampleService"  
          binding="wsHttpBinding"  
          behaviorConfiguration="withMessageInspector"
          contract="Microsoft.WCF.Documentation.ISampleService"  
        />  
        <endpoint  
           address="mex"  
           binding="mexHttpBinding"  
           contract="IMetadataExchange"  
        />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="metadataSupport">  
        <serviceMetadata httpGetEnabled="true" httpGetUrl=""/>  
      </behavior>  
      </serviceBehaviors>  
      <endpointBehaviors>  
        <behavior name="withMessageInspector">  
          <endpointMessageInspector />  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <extensions>  
      <behaviorExtensions>  
        <add
          name="endpointMessageInspector"  
          type="Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector, HostApplication, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"  
        />  
      </behaviorExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="adede-192">動作`Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector`拡張型`HostApplication`は、そのクラスがコンパイルされたアセンブリの名前です。</span><span class="sxs-lookup"><span data-stu-id="adede-192">Where `Microsoft.WCF.Documentation.EndpointBehaviorMessageInspector` is the behavior extension type and `HostApplication` is the name of the assembly into which that class has been compiled.</span></span>  
  
### <a name="evaluation-order"></a><span data-ttu-id="adede-193">評価順序</span><span class="sxs-lookup"><span data-stu-id="adede-193">Evaluation Order</span></span>  
 <span data-ttu-id="adede-194"><xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> と <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> は、プログラミング モデルと記述からランタイムを構築します。</span><span class="sxs-lookup"><span data-stu-id="adede-194">The <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> and the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> are responsible for building the runtime from the programming model and description.</span></span> <span data-ttu-id="adede-195">前述のように、動作は、サービス、エンドポイント、コントラクト、および操作でランタイムの構築プロセスを支援します。</span><span class="sxs-lookup"><span data-stu-id="adede-195">Behaviors, as previously described, contribute to that build process at the service, endpoint, contract, and operation.</span></span>  
  
 <span data-ttu-id="adede-196"><xref:System.ServiceModel.ServiceHost> は次の順序で動作を適用します。</span><span class="sxs-lookup"><span data-stu-id="adede-196">The <xref:System.ServiceModel.ServiceHost> applies behaviors in the following order:</span></span>  
  
1. <span data-ttu-id="adede-197">サービス</span><span class="sxs-lookup"><span data-stu-id="adede-197">Service</span></span>  
  
2. <span data-ttu-id="adede-198">コントラクト</span><span class="sxs-lookup"><span data-stu-id="adede-198">Contract</span></span>  
  
3. <span data-ttu-id="adede-199">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="adede-199">Endpoint</span></span>  
  
4. <span data-ttu-id="adede-200">Operation</span><span class="sxs-lookup"><span data-stu-id="adede-200">Operation</span></span>  
  
 <span data-ttu-id="adede-201">動作のどのコレクション内でも、順序が保証されるというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="adede-201">Within any collection of behaviors, no order is guaranteed.</span></span>  
  
 <span data-ttu-id="adede-202"><xref:System.ServiceModel.ChannelFactory%601> は次の順序で動作を適用します。</span><span class="sxs-lookup"><span data-stu-id="adede-202">The <xref:System.ServiceModel.ChannelFactory%601> applies behaviors in the following order:</span></span>  
  
1. <span data-ttu-id="adede-203">コントラクト</span><span class="sxs-lookup"><span data-stu-id="adede-203">Contract</span></span>  
  
2. <span data-ttu-id="adede-204">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="adede-204">Endpoint</span></span>  
  
3. <span data-ttu-id="adede-205">Operation</span><span class="sxs-lookup"><span data-stu-id="adede-205">Operation</span></span>  
  
 <span data-ttu-id="adede-206">この場合も、動作のどのコレクション内でも、順序が保証されるというわけではありません。</span><span class="sxs-lookup"><span data-stu-id="adede-206">Within any collection of behaviors, again, no order is guaranteed.</span></span>  
  
### <a name="adding-behaviors-programmatically"></a><span data-ttu-id="adede-207">プログラムによる動作の追加</span><span class="sxs-lookup"><span data-stu-id="adede-207">Adding Behaviors Programmatically</span></span>  
 <span data-ttu-id="adede-208"><xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> メソッドの後で、サービス アプリケーションの <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType> の各プロパティを変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="adede-208">Properties of the <xref:System.ServiceModel.Description.ServiceDescription?displayProperty=nameWithType> in the service application must not be modified subsequent to the <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A?displayProperty=nameWithType> method on <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>.</span></span> <span data-ttu-id="adede-209">このメソッドの後で変更すると、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> および `AddServiceEndpoint` の <xref:System.ServiceModel.ServiceHostBase> プロパティや <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> メソッドなどの一部のメンバーは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="adede-209">Some members, like the <xref:System.ServiceModel.ServiceHostBase.Credentials%2A?displayProperty=nameWithType> property and the `AddServiceEndpoint` methods on <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>, throw an exception if modified past that point.</span></span> <span data-ttu-id="adede-210">変更を許可するメンバーもありますが、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="adede-210">Others permit you to modify them, but the result is undefined.</span></span>  
  
 <span data-ttu-id="adede-211">同様に、クライアントで、<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> の <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> 呼び出しの後で、<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> 値を変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="adede-211">Similarly, on the client the <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType> values must not be modified after the call to <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> on the <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>.</span></span> <span data-ttu-id="adede-212">この呼び出しの後で変更すると、<xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> プロパティは例外をスローします。その他のクライアント記述値は、エラーを発生させずに変更できます。</span><span class="sxs-lookup"><span data-stu-id="adede-212">The <xref:System.ServiceModel.ChannelFactory.Credentials%2A?displayProperty=nameWithType> property throws an exception if modified past that point, but the other client description values can be modified without error.</span></span> <span data-ttu-id="adede-213">ただし、結果は未定義の状態になります。</span><span class="sxs-lookup"><span data-stu-id="adede-213">The result, however, is undefined.</span></span>  
  
 <span data-ttu-id="adede-214">サービスとクライアントのどちらの場合も、<xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType> の呼び出しの前に記述を変更することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="adede-214">Whether for the service or client, it is recommended that you modify the description prior to calling <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="inheritance-rules-for-behavior-attributes"></a><span data-ttu-id="adede-215">動作属性の継承ルール</span><span class="sxs-lookup"><span data-stu-id="adede-215">Inheritance Rules for Behavior Attributes</span></span>  
 <span data-ttu-id="adede-216">4 種類の動作はすべて、属性 (サービスの動作とコントラクトの動作) を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="adede-216">All four types of behaviors can be populated using attributes – service behaviors and contract behaviors.</span></span> <span data-ttu-id="adede-217">属性はマネージド オブジェクトとメンバーで定義され、マネージド オブジェクトとメンバーは継承をサポートしているため、継承のコンテキストでの動作属性の機能を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="adede-217">Because attributes are defined on managed objects and members, and managed objects and members support inheritance, it is necessary to define how behavior attributes work in the context of inheritance.</span></span>  
  
 <span data-ttu-id="adede-218">大まかに言えば、特定のスコープ (サービス、コントラクト、操作など) については、そのスコープの継承階層内のすべての動作属性が適用されるという継承ルールになります。</span><span class="sxs-lookup"><span data-stu-id="adede-218">At a high level, the rule is that for a particular scope (for example, service, contract, or operation), all behavior attributes in the inheritance hierarchy for that scope are applied.</span></span> <span data-ttu-id="adede-219">同じ種類の 2 つの動作属性がある場合、最も多く派生された種類だけが使用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-219">If there are two behavior attributes of the same type, only the most-derived type is used.</span></span>  
  
#### <a name="service-behaviors"></a><span data-ttu-id="adede-220">サービスの動作</span><span class="sxs-lookup"><span data-stu-id="adede-220">Service Behaviors</span></span>  
 <span data-ttu-id="adede-221">サービス クラスの場合、指定のクラスとその親のすべてのサービス動作属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-221">For a given service class, all service behavior attributes on that class, and on parents of that class, are applied.</span></span> <span data-ttu-id="adede-222">継承階層の複数の場所に同じ種類の属性が適用されている場合は、最も多く派生された種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-222">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
```csharp  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple)]  
[AspNetCompatibilityRequirementsAttribute(  
    AspNetCompatibilityRequirementsMode = AspNetCompatibilityRequirementsMode.Allowed)]  
public class A { /* … */ }  
  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.Single)]  
public class B : A { /* … */}  
```  
  
 <span data-ttu-id="adede-223">たとえば、上記の例では、最終的にサービス B は、<xref:System.ServiceModel.InstanceContextMode> が <xref:System.ServiceModel.InstanceContextMode.Single>、<xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> が <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>、<xref:System.ServiceModel.ConcurrencyMode> が <xref:System.ServiceModel.ConcurrencyMode.Single> になります。</span><span class="sxs-lookup"><span data-stu-id="adede-223">For example, in the preceding case, the service B ends up with an <xref:System.ServiceModel.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.Single>, an <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode> mode of <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed>, and a <xref:System.ServiceModel.ConcurrencyMode> of <xref:System.ServiceModel.ConcurrencyMode.Single>.</span></span> <span data-ttu-id="adede-224"><xref:System.ServiceModel.ConcurrencyMode> が <xref:System.ServiceModel.ConcurrencyMode.Single> になるのは、サービス B の <xref:System.ServiceModel.ServiceBehaviorAttribute> 属性の方がサービス A よりも多く派生されているためです。</span><span class="sxs-lookup"><span data-stu-id="adede-224">The <xref:System.ServiceModel.ConcurrencyMode> is <xref:System.ServiceModel.ConcurrencyMode.Single>, because <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute on service B is on "more derived" than that on service A.</span></span>  
  
#### <a name="contract-behaviors"></a><span data-ttu-id="adede-225">コントラクトの動作</span><span class="sxs-lookup"><span data-stu-id="adede-225">Contract Behaviors</span></span>  
 <span data-ttu-id="adede-226">コントラクトの場合、指定のインターフェイスとその親のすべてのコントラクト動作属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-226">For a given contract, all contract behavior attributes on that interface and on parents of that interface, are applied.</span></span> <span data-ttu-id="adede-227">継承階層の複数の場所に同じ種類の属性が適用されている場合は、最も多く派生された種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-227">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>  
  
#### <a name="operation-behaviors"></a><span data-ttu-id="adede-228">操作の動作</span><span class="sxs-lookup"><span data-stu-id="adede-228">Operation Behaviors</span></span>  
 <span data-ttu-id="adede-229">指定の操作が既存の抽象操作または仮想操作をオーバーライドしない場合、継承ルールは適用されません。</span><span class="sxs-lookup"><span data-stu-id="adede-229">If a given operation does not override an existing abstract or virtual operation, no inheritance rules apply.</span></span>  
  
 <span data-ttu-id="adede-230">操作が既存の操作をオーバーライドする場合は、その操作とその親のすべての操作動作属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-230">If an operation does override an existing operation, then all operation behavior attributes on that operation and on parents of that operation, are applied.</span></span>  <span data-ttu-id="adede-231">継承階層の複数の場所に同じ種類の属性が適用されている場合は、最も多く派生された種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="adede-231">If the same type of attribute is applied at multiple places in the inheritance hierarchy, the most-derived type is used.</span></span>
