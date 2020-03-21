---
title: Pooling
ms.date: 03/30/2017
ms.assetid: 688dfb30-b79a-4cad-a687-8302f8a9ad6a
ms.openlocfilehash: 46abc2c9c667ea7614581d7fafaa8e174db7f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183402"
---
# <a name="pooling"></a><span data-ttu-id="0d72f-102">Pooling</span><span class="sxs-lookup"><span data-stu-id="0d72f-102">Pooling</span></span>
<span data-ttu-id="0d72f-103">このサンプルでは、オブジェクト プーリングをサポートするために、Wcf (WCF) を拡張する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-103">This sample demonstrates how to extend Windows Communication Foundation (WCF) to support object pooling.</span></span> <span data-ttu-id="0d72f-104">サンプルでは、エンタープライズ サービスの`ObjectPoolingAttribute` 属性機能と、構文および意味が同じ属性を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-104">The sample demonstrates how to create an attribute that is syntactically and semantically similar to the `ObjectPoolingAttribute` attribute functionality of Enterprise Services.</span></span> <span data-ttu-id="0d72f-105">オブジェクト プールにより、アプリケーションのパフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-105">Object pooling can provide a dramatic boost to an application's performance.</span></span> <span data-ttu-id="0d72f-106">ただし、適切に使用しないと逆効果になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-106">However, it can have the opposite effect if it is not used properly.</span></span> <span data-ttu-id="0d72f-107">オブジェクト プールは、負荷のかかる初期化が要求される、使用頻度の高いオブジェクトの再作成によるオーバーヘッドを減少させます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-107">Object pooling helps reduce the overhead of recreating frequently used objects that require extensive initialization.</span></span> <span data-ttu-id="0d72f-108">ただし、プールされたオブジェクト上のメソッドへの呼び出しが完了するのに非常に時間がかかる場合、オブジェクト プールは、最大プール サイズに達するとすぐに追加要求をキューに置きます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-108">However, if a call to a method on a pooled object takes a considerable amount of time to complete, object pooling queues additional requests as soon as the maximum pool size is reached.</span></span> <span data-ttu-id="0d72f-109">そのため、タイムアウト例外がスローされることによって、いくつかのオブジェクトの作成要求が失敗する場合があります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-109">Thus it may fail to serve some object creation requests by throwing a timeout exception.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d72f-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d72f-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0d72f-111">WCF 拡張機能を作成する最初の手順は、使用する拡張ポイントを決定することです。</span><span class="sxs-lookup"><span data-stu-id="0d72f-111">The first step in creating a WCF extension is to decide the extensibility point to use.</span></span>  
  
 <span data-ttu-id="0d72f-112">WCF では *、dispatcher*という用語は、受信メッセージをユーザーのサービスでメソッド呼び出しに変換し、そのメソッドからそのメソッドから送信メッセージに戻り値を変換するランタイム コンポーネントを指します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-112">In WCF the term *dispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="0d72f-113">WCF サービスは、各エンドポイントのディスパッチャーを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-113">A WCF service creates a dispatcher for each endpoint.</span></span> <span data-ttu-id="0d72f-114">WCF クライアントは、そのクライアントに関連付けられているコントラクトが双方向コントラクトである場合、ディスパッチャーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-114">A WCF client must use a dispatcher if the contract associated with that client is a duplex contract.</span></span>  
  
 <span data-ttu-id="0d72f-115">チャネル ディスパッチャとエンドポイント ディスパッチャでは、ディスパッチャの動作を制御するさまざまなプロパティが公開されているため、チャネル全体の拡張とコントラクト全体の拡張を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-115">The channel and endpoint dispatchers offer channel-and contract-wide extensibility by exposing various properties that control the behavior of the dispatcher.</span></span> <span data-ttu-id="0d72f-116">さらに <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> プロパティにより、ディスパッチ処理を検査、変更、またはカスタマイズすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-116">The <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.DispatchRuntime%2A> property also enables you to inspect, modify, or customize the dispatching process.</span></span> <span data-ttu-id="0d72f-117">このサンプルでは、サービス クラスのインスタンスを提供するオブジェクトをポイントする <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> プロパティに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="0d72f-117">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="the-iinstanceprovider"></a><span data-ttu-id="0d72f-118">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="0d72f-118">The IInstanceProvider</span></span>  
 <span data-ttu-id="0d72f-119">WCF では、ディスパッチャーは、インターフェイスを実装する<xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>を使用して、サービス<xref:System.ServiceModel.Dispatcher.IInstanceProvider>クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-119">In WCF, the dispatcher creates instances of the service class using a <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A>, which implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="0d72f-120">このインターフェイスには、次の 3 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d72f-120">This interface has three methods:</span></span>  
  
- <span data-ttu-id="0d72f-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: メッセージが到着すると、このディスパッチャは <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> メソッドを呼び出し、メッセージを処理するためのサービス クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-121"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29>: When a message arrives the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="0d72f-122">このメソッドの呼び出し頻度は <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-122">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="0d72f-123">たとえば <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティが <xref:System.ServiceModel.InstanceContextMode.PerCall> に設定されている場合、サービス クラスの新しいインスタンスが作成され、到着する各メッセージが処理されます。したがって、<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> はメッセージが到着するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-123">For example, if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall> a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="0d72f-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: 前のメソッドと同じです。ただし、このメソッドが呼び出されるのは Message 引数がない場合です。</span><span class="sxs-lookup"><span data-stu-id="0d72f-124"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%29>: This is identical to the previous method, except this is invoked when there is no Message argument.</span></span>  
  
- <span data-ttu-id="0d72f-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: サービス インスタンスの有効期間が経過すると、ディスパッチャは <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-125"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29>: When a service instance's lifetime has elapsed, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%28System.ServiceModel.InstanceContext%2CSystem.Object%29> method.</span></span> <span data-ttu-id="0d72f-126"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> メソッドと同様、このメソッドへの呼び出し頻度は <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-126">Just like for the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="0d72f-127">オブジェクト プール</span><span class="sxs-lookup"><span data-stu-id="0d72f-127">The Object Pool</span></span>  
 <span data-ttu-id="0d72f-128">カスタム <xref:System.ServiceModel.Dispatcher.IInstanceProvider> の実装により、サービスに必要なオブジェクト プールの意味が提供されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-128">A custom <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation provides the required object pooling semantics for a service.</span></span> <span data-ttu-id="0d72f-129">したがって、このサンプルにはプール用の `ObjectPoolingInstanceProvider` のカスタム実装を提供する <xref:System.ServiceModel.Dispatcher.IInstanceProvider> 型が用意されています。</span><span class="sxs-lookup"><span data-stu-id="0d72f-129">Therefore, this sample has an `ObjectPoolingInstanceProvider` type that provides custom implementation of <xref:System.ServiceModel.Dispatcher.IInstanceProvider> for pooling.</span></span> <span data-ttu-id="0d72f-130">`Dispatcher` が、新しいインスタンスを作成する代わりに <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> メソッドを呼び出すと、カスタム実装はメモリ内プールで既存のオブジェクトを検索します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-130">When the `Dispatcher` calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%28System.ServiceModel.InstanceContext%2CSystem.ServiceModel.Channels.Message%29> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="0d72f-131">検索されたオブジェクトが使用可能な場合は、そのオブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-131">If one is available, it is returned.</span></span> <span data-ttu-id="0d72f-132">それ以外の場合は、新しいオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-132">Otherwise, a new object is created.</span></span> <span data-ttu-id="0d72f-133">`GetInstance` の実装を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-133">The implementation for `GetInstance` is shown in the following sample code.</span></span>  
  
```csharp  
object IInstanceProvider.GetInstance(InstanceContext instanceContext, Message message)  
{  
    object obj = null;  
  
    lock (poolLock)  
    {  
        if (pool.Count > 0)  
        {  
            obj = pool.Pop();  
        }  
        else  
        {  
            obj = CreateNewPoolObject();  
        }  
        activeObjectsCount++;  
    }  
  
    WritePoolMessage(ResourceHelper.GetString("MsgNewObject"));  
  
    idleTimer.Stop();  
  
    return obj;
}  
```  
  
 <span data-ttu-id="0d72f-134">カスタム `ReleaseInstance` 実装は、解放されたインスタンスをプールに戻し、`ActiveObjectsCount` 値をデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="0d72f-134">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="0d72f-135">`Dispatcher` はこれらのメソッドをさまざまなスレッドから呼び出すので、`ObjectPoolingInstanceProvider` クラスのクラス レベル メンバーへの同期アクセスが必要となります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-135">The `Dispatcher` can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolingInstanceProvider` class is required.</span></span>  
  
```csharp  
void IInstanceProvider.ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        pool.Push(instance);  
        activeObjectsCount--;  
  
        WritePoolMessage(  
        ResourceHelper.GetString("MsgObjectPooled"));  
  
        // When the service goes completely idle (no requests
        // are being processed), the idle timer is started  
        if (activeObjectsCount == 0)  
            idleTimer.Start();
    }  
}  
```  
  
 <span data-ttu-id="0d72f-136">この`ReleaseInstance`メソッドは、「初期化のクリーンアップ」機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-136">The `ReleaseInstance` method provides a "clean up initialization" feature.</span></span> <span data-ttu-id="0d72f-137">通常は、プールにはその有効期間中に最小限の数のオブジェクトが保持されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-137">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="0d72f-138">ただし、使用率が非常に高くなり、プールでオブジェクトを追加作成する必要が生じて、その数が構成に指定されている上限に達する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-138">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="0d72f-139">プールが最終的にアクティブでなくなると、そうした過剰なオブジェクトは余分なオーバーヘッドになります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-139">Eventually, when the pool becomes less active, those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="0d72f-140">したがって、`activeObjectsCount` がゼロに達すると、アイドル タイマが起動し、クリーンアップ サイクルがトリガされて実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-140">Therefore, when the `activeObjectsCount` reaches zero, an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
## <a name="adding-the-behavior"></a><span data-ttu-id="0d72f-141">動作の追加</span><span class="sxs-lookup"><span data-stu-id="0d72f-141">Adding the Behavior</span></span>  
 <span data-ttu-id="0d72f-142">ディスパッチャのレイヤ拡張は、次の動作を使用してフックされます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-142">Dispatcher-layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="0d72f-143">サービスの動作。</span><span class="sxs-lookup"><span data-stu-id="0d72f-143">Service Behaviors.</span></span> <span data-ttu-id="0d72f-144">サービス ランタイム全体のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-144">These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="0d72f-145">エンドポイントの動作。</span><span class="sxs-lookup"><span data-stu-id="0d72f-145">Endpoint Behaviors.</span></span> <span data-ttu-id="0d72f-146">サービス エンドポイントのカスタマイズ、特にチャネル ディスパッチャとエンドポイント ディスパッチャのカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-146">These allow for the customization of service endpoints, specifically a Channel and Endpoint Dispatcher.</span></span>  
  
- <span data-ttu-id="0d72f-147">コントラクトの動作。</span><span class="sxs-lookup"><span data-stu-id="0d72f-147">Contract Behaviors.</span></span> <span data-ttu-id="0d72f-148">クライアント上およびサービス上で、それぞれ <xref:System.ServiceModel.Dispatcher.ClientRuntime> クラスと <xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラスのカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-148">These allow for the customization of both <xref:System.ServiceModel.Dispatcher.ClientRuntime> and <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client and the service respectively.</span></span>  
  
 <span data-ttu-id="0d72f-149">オブジェクト プール拡張を行うには、サービスの動作を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-149">For the purpose of an object pooling extension a service behavior must be created.</span></span> <span data-ttu-id="0d72f-150">サービス動作を作成するには、<xref:System.ServiceModel.Description.IServiceBehavior> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-150">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="0d72f-151">サービス モデルにカスタム動作を認識させるには、次のようないくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-151">There are several ways to make the service model aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="0d72f-152">カスタム属性を使用する。</span><span class="sxs-lookup"><span data-stu-id="0d72f-152">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="0d72f-153">カスタム動作をサービス説明の動作コレクションに強制的に追加する。</span><span class="sxs-lookup"><span data-stu-id="0d72f-153">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="0d72f-154">構成ファイルを拡張する。</span><span class="sxs-lookup"><span data-stu-id="0d72f-154">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="0d72f-155">このサンプルではカスタム属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-155">This sample uses a custom attribute.</span></span> <span data-ttu-id="0d72f-156"><xref:System.ServiceModel.ServiceHost> が構築されると、サービスの種類の定義で使用されている属性が調べられ、使用可能な動作がサービス説明の動作コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-156">When the <xref:System.ServiceModel.ServiceHost> is constructed it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="0d72f-157">インターフェイス <xref:System.ServiceModel.Description.IServiceBehavior> には、<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>、<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>、および <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> の 3 つのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-157">The interface <xref:System.ServiceModel.Description.IServiceBehavior> has three methods in it -- <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>, <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>, and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="0d72f-158"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> メソッドを使用すると、確実に動作をサービスに適用できます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-158">The <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A> method is used to ensure that the behavior can be applied to the service.</span></span> <span data-ttu-id="0d72f-159">このサンプルでは、これを実装することによって、サービスが <xref:System.ServiceModel.InstanceContextMode.Single> を使用して構成されないようにします。</span><span class="sxs-lookup"><span data-stu-id="0d72f-159">In this sample, the implementation ensures that the service is not configured with <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span> <span data-ttu-id="0d72f-160"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> メソッドは、サービスのバインディングの構成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-160">The <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A> method is used to configure the service's bindings.</span></span> <span data-ttu-id="0d72f-161">このシナリオでは、このメソッドは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="0d72f-161">It is not required in this scenario.</span></span> <span data-ttu-id="0d72f-162"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> はサービスのディスパッチャの構成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-162">The <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A> is used to configure the service's dispatchers.</span></span> <span data-ttu-id="0d72f-163">このメソッドは、初期化中に<xref:System.ServiceModel.ServiceHost>WCF によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-163">This method is called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="0d72f-164">このメソッドには次のパラメータが渡されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-164">The following parameters are passed into this method:</span></span>  
  
- <span data-ttu-id="0d72f-165">`Description`: この引数は、サービス全体のサービスの説明を提供します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-165">`Description`: This argument provides the service description for the entire service.</span></span> <span data-ttu-id="0d72f-166">これを使用すると、サービスのエンドポイント、コントラクト、バインディング、およびその他のデータに関する説明データを検査できます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-166">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data.</span></span>  
  
- <span data-ttu-id="0d72f-167">`ServiceHostBase`: この引数は、現在初期化中の <xref:System.ServiceModel.ServiceHostBase> を提供します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-167">`ServiceHostBase`: This argument provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="0d72f-168">カスタム <xref:System.ServiceModel.Description.IServiceBehavior> 実装では、`ObjectPoolingInstanceProvider` の新しいインスタンスがインスタンス化され、ServiceHostBase の各 <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> 内の <xref:System.ServiceModel.Dispatcher.DispatchRuntime> プロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-168">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation a new instance of `ObjectPoolingInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.DispatchRuntime> in the ServiceHostBase.</span></span>  
  
```csharp  
void IServiceBehavior.ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    // Create an instance of the ObjectPoolInstanceProvider.  
    ObjectPoolingInstanceProvider instanceProvider = new  
           ObjectPoolingInstanceProvider(description.ServiceType,
                                                    minPoolSize);  
  
    // Forward the call if we created a ServiceThrottlingBehavior.  
    if (this.throttlingBehavior != null)  
    {  
        ((IServiceBehavior)this.throttlingBehavior).ApplyDispatchBehavior(description, serviceHostBase);  
    }  
  
    // In case there was already a ServiceThrottlingBehavior
    // (this.throttlingBehavior==null), it should have initialized
    // a single ServiceThrottle on all ChannelDispatchers.
    // As we loop through the ChannelDispatchers, we verify that
    // and modify the ServiceThrottle to guard MaxPoolSize.  
    ServiceThrottle throttle = null;  
  
    foreach (ChannelDispatcherBase cdb in
            serviceHostBase.ChannelDispatchers)  
    {  
        ChannelDispatcher cd = cdb as ChannelDispatcher;  
        if (cd != null)  
        {  
            // Make sure there is exactly one throttle used by all
            // endpoints. If there were others, we could not enforce
            // MaxPoolSize.  
            if ((this.throttlingBehavior == null) &&
                        (this.maxPoolSize != Int32.MaxValue))  
            {  
                throttle ??= cd.ServiceThrottle;
                if (cd.ServiceThrottle == null)  
                {  
                    throw new
InvalidOperationException(ResourceHelper.GetString("ExNullThrottle"));  
                }  
                if (throttle != cd.ServiceThrottle)  
                {  
                    throw new InvalidOperationException(ResourceHelper.GetString("ExDifferentThrottle"));  
                }  
             }  
  
             foreach (EndpointDispatcher ed in cd.Endpoints)  
             {  
                 // Assign it to DispatchBehavior in each endpoint.  
                 ed.DispatchRuntime.InstanceProvider =
                                      instanceProvider;  
             }  
         }  
     }  
  
     // Set the MaxConcurrentInstances to limit the number of items
     // that will ever be requested from the pool.  
     if ((throttle != null) && (throttle.MaxConcurrentInstances >
                                      this.maxPoolSize))  
     {  
         throttle.MaxConcurrentInstances = this.maxPoolSize;  
     }  
}  
```  
  
 <span data-ttu-id="0d72f-169"><xref:System.ServiceModel.Description.IServiceBehavior> 実装のほかにも、<xref:System.EnterpriseServices.ObjectPoolingAttribute> クラスには属性引数を使用してオブジェクト プールをカスタマイズするいくつかのメンバがあります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-169">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the <xref:System.EnterpriseServices.ObjectPoolingAttribute> class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="0d72f-170">こうしたメンバには <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>、<xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>、<xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A> などがあり、.NET Enterprise Services で提供されるオブジェクト プール機能のセットに一致します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-170">These members include <xref:System.EnterpriseServices.ObjectPoolingAttribute.MaxPoolSize%2A>, <xref:System.EnterpriseServices.ObjectPoolingAttribute.MinPoolSize%2A>, and <xref:System.EnterpriseServices.ObjectPoolingAttribute.CreationTimeout%2A>, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="0d72f-171">新しく作成されたカスタム`ObjectPooling`属性を使用してサービスの実装に注意を付けて、オブジェクト プールの動作を WCF サービスに追加できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="0d72f-171">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxPoolSize=1024, MinPoolSize=10, CreationTimeout=30000)]
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="0d72f-172">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="0d72f-172">Running the Sample</span></span>  
 <span data-ttu-id="0d72f-173">このサンプルでは、特定のシナリオでオブジェクト プールを使用することによって得られるパフォーマンス上の利点を示します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-173">The sample demonstrates the performance benefits that can be gained by using object pooling in certain scenarios.</span></span>  
  
 <span data-ttu-id="0d72f-174">サービス アプリケーションは、`WorkService` と `ObjectPooledWorkService` の 2 つのサービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-174">The service application implements two services -- `WorkService` and `ObjectPooledWorkService`.</span></span> <span data-ttu-id="0d72f-175">どちらのサービスも同じ実装を共有し、負荷のかかる初期化を必要とします。さらに、比較的負荷の少ない `DoWork()` メソッドを公開します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-175">Both services share the same implementation -- they both require expensive initialization and then expose a `DoWork()` method that is relatively cheap.</span></span> <span data-ttu-id="0d72f-176">両者の唯一の違いは、`ObjectPooledWorkService` ではオブジェクト プールが次のように構成されるという点です。</span><span class="sxs-lookup"><span data-stu-id="0d72f-176">The only difference is that the `ObjectPooledWorkService` has object pooling configured:</span></span>  
  
```csharp  
[ObjectPooling(MinPoolSize = 0, MaxPoolSize = 5)]  
public class ObjectPooledWorkService : IDoWork  
{  
    public ObjectPooledWorkService()  
    {  
        Thread.Sleep(5000);  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService instance created.");  
    }  
  
    public void DoWork()  
    {  
        ColorConsole.WriteLine(ConsoleColor.Blue, "ObjectPooledWorkService.GetData() completed.");  
    }
}  
```  
  
 <span data-ttu-id="0d72f-177">クライアントを実行すると、`WorkService` への呼び出し時間が 5 回計算されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-177">When you run the client, it times calling the `WorkService` 5 times.</span></span> <span data-ttu-id="0d72f-178">次に、`ObjectPooledWorkService` への呼び出し時間が 5 回計算されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-178">It then times calling the `ObjectPooledWorkService` 5 times.</span></span> <span data-ttu-id="0d72f-179">その後、時間の違いが次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-179">The difference in time is then displayed:</span></span>  
  
```console
Press <ENTER> to start the client.  
  
Calling WorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling WorkService took: 26722 ms.  
Calling ObjectPooledWorkService:  
1 - DoWork() Done  
2 - DoWork() Done  
3 - DoWork() Done  
4 - DoWork() Done  
5 - DoWork() Done  
Calling ObjectPooledWorkService took: 5323 ms.  
Press <ENTER> to exit.  
```  
  
> [!NOTE]
> <span data-ttu-id="0d72f-180">クライアントを最初に実行したときには、両方のサービスにかかった時間は同じように見えます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-180">The first time the client is run both services appear to take about the same amount of time.</span></span> <span data-ttu-id="0d72f-181">サンプルを再実行すると、`ObjectPooledWorkService` の戻り時間の方が早いことがわかります。オブジェクトのインスタンスが既にプール内に存在しているからです。</span><span class="sxs-lookup"><span data-stu-id="0d72f-181">If you re-run the sample, you can see that the `ObjectPooledWorkService` returns much quicker because an instance of that object already exists in the pool.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0d72f-182">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="0d72f-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0d72f-183">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0d72f-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0d72f-184">ソリューションをビルドするには、「 [Windows コミュニケーション ファウンデーション のサンプルの構築](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0d72f-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0d72f-185">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="0d72f-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0d72f-186">Svcutil.exe を使用してこのサンプルの構成を再生成した場合は、クライアント コードに一致するように、クライアント構成内のエンドポイント名を変更してください。</span><span class="sxs-lookup"><span data-stu-id="0d72f-186">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d72f-187">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0d72f-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0d72f-188">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0d72f-188">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0d72f-189">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="0d72f-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0d72f-190">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0d72f-190">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Pooling`  
