---
title: 初期化のインスタンス化
ms.date: 03/30/2017
ms.assetid: 154d049f-2140-4696-b494-c7e53f6775ef
ms.openlocfilehash: 44cd278fb0e48e07562b0b8ad52855b4a3f70761
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975863"
---
# <a name="instancing-initialization"></a><span data-ttu-id="9b814-102">初期化のインスタンス化</span><span class="sxs-lookup"><span data-stu-id="9b814-102">Instancing Initialization</span></span>
<span data-ttu-id="9b814-103">このサンプルは、インターフェイスを定義することで[プール](../../../../docs/framework/wcf/samples/pooling.md)のサンプルを拡張します。 `IObjectControl`は、オブジェクトのアクティブ化と非アクティブ化によってオブジェクトの初期化をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="9b814-103">This sample extends the [Pooling](../../../../docs/framework/wcf/samples/pooling.md) sample by defining an interface, `IObjectControl`, which customizes the initialization of an object by activating and deactivating it.</span></span> <span data-ttu-id="9b814-104">クライアントは、オブジェクトをプールに返すメソッドや、プールに返さないメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9b814-104">The client invokes methods that return the object to the pool and that do not return the object to the pool.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b814-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b814-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="extensibility-points"></a><span data-ttu-id="9b814-106">拡張ポイント</span><span class="sxs-lookup"><span data-stu-id="9b814-106">Extensibility Points</span></span>  
 <span data-ttu-id="9b814-107">Windows Communication Foundation (WCF) 拡張機能を作成する最初の手順は、使用する機能拡張ポイントを決定することです。</span><span class="sxs-lookup"><span data-stu-id="9b814-107">The first step in creating a Windows Communication Foundation (WCF) extension is to decide the extensibility point to use.</span></span> <span data-ttu-id="9b814-108">WCF では、 *Endpointdispatcher*という用語は、受信メッセージをユーザーのサービスのメソッド呼び出しに変換し、そのメソッドの戻り値を送信メッセージに変換する実行時コンポーネントを指します。</span><span class="sxs-lookup"><span data-stu-id="9b814-108">In WCF, the term *EndpointDispatcher* refers to a run-time component responsible for converting incoming messages into method invocations on the user’s service and for converting return values from that method to an outgoing message.</span></span> <span data-ttu-id="9b814-109">WCF サービスは、エンドポイントごとに EndpointDispatcher を作成します。</span><span class="sxs-lookup"><span data-stu-id="9b814-109">A WCF service creates an EndpointDispatcher for each endpoint.</span></span>  
  
 <span data-ttu-id="9b814-110">EndpointDispatcher は <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> クラスを使用して、(サービスによって送受信されるすべてのメッセージの) エンドポイント スコープ拡張を提供します。</span><span class="sxs-lookup"><span data-stu-id="9b814-110">The EndpointDispatcher offers endpoint scope (for all messages received or sent by the service) extensibility using the <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> class.</span></span> <span data-ttu-id="9b814-111">このクラスにより、EndpointDispatcher の動作を制御するさまざまなプロパティをカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="9b814-111">This class allows you to customize various properties that control the behavior of the EndpointDispatcher.</span></span> <span data-ttu-id="9b814-112">このサンプルでは、サービス クラスのインスタンスを提供するオブジェクトをポイントする <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> プロパティに焦点を当てています。</span><span class="sxs-lookup"><span data-stu-id="9b814-112">This sample focuses on the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property that points to the object that provides the instances of the service class.</span></span>  
  
## <a name="iinstanceprovider"></a><span data-ttu-id="9b814-113">IInstanceProvider</span><span class="sxs-lookup"><span data-stu-id="9b814-113">IInstanceProvider</span></span>  
 <span data-ttu-id="9b814-114">WCF では、EndpointDispatcher は、<xref:System.ServiceModel.Dispatcher.IInstanceProvider> インターフェイスを実装するインスタンスプロバイダーを使用して、サービスクラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b814-114">In WCF, the EndpointDispatcher creates instances of a service class by using an instance provider that implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface.</span></span> <span data-ttu-id="9b814-115">このインターフェイスに含まれるメソッドは、次の 2 つのみです。</span><span class="sxs-lookup"><span data-stu-id="9b814-115">This interface has only two methods:</span></span>  
  
- <span data-ttu-id="9b814-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: メッセージが到着すると、このディスパッチャは <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> メソッドを呼び出し、メッセージを処理するためのサービス クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b814-116"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A>: When a message arrives, the Dispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method to create an instance of the service class to process the message.</span></span> <span data-ttu-id="9b814-117">このメソッドの呼び出し頻度は <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="9b814-117">The frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span> <span data-ttu-id="9b814-118">たとえば <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティが <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType> に設定されている場合、サービス クラスの新しいインスタンスが作成され、到着する各メッセージが処理されます。したがって、<xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> はメッセージが到着するたびに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-118">For example if the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property is set to <xref:System.ServiceModel.InstanceContextMode.PerCall?displayProperty=nameWithType>, a new instance of service class is created to process each message that arrives, so <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> is called whenever a message arrives.</span></span>  
  
- <span data-ttu-id="9b814-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: サービス インスタンスがメッセージの処理を完了すると、EndpointDispatcher は <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9b814-119"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A>: When the service instance finishes processing the message, the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.ReleaseInstance%2A> method.</span></span> <span data-ttu-id="9b814-120"><xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> メソッドと同様、このメソッドへの呼び出し頻度は <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="9b814-120">As in the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, the frequency of the calls to this method is determined by the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property.</span></span>  
  
## <a name="the-object-pool"></a><span data-ttu-id="9b814-121">オブジェクト プール</span><span class="sxs-lookup"><span data-stu-id="9b814-121">The Object Pool</span></span>  
 <span data-ttu-id="9b814-122">`ObjectPoolInstanceProvider` クラスには、オブジェクト プールの実装が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9b814-122">The `ObjectPoolInstanceProvider` class contains the implementation for the object pool.</span></span> <span data-ttu-id="9b814-123">このクラスは、サービス モデルのレイヤと対話する <xref:System.ServiceModel.Dispatcher.IInstanceProvider> インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="9b814-123">This class implements the <xref:System.ServiceModel.Dispatcher.IInstanceProvider> interface to interact with the service model layer.</span></span> <span data-ttu-id="9b814-124">EndpointDispatcher が、新しいインスタンスを作成する代わりに <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> メソッドを呼び出すと、カスタム実装はメモリ内プールで既存のオブジェクトを検索します。</span><span class="sxs-lookup"><span data-stu-id="9b814-124">When the EndpointDispatcher calls the <xref:System.ServiceModel.Dispatcher.IInstanceProvider.GetInstance%2A> method, instead of creating a new instance, the custom implementation looks for an existing object in an in-memory pool.</span></span> <span data-ttu-id="9b814-125">検索されたオブジェクトが使用可能な場合は、そのオブジェクトが返されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-125">If one is available, it is returned.</span></span> <span data-ttu-id="9b814-126">使用可能なオブジェクトがない場合、`ObjectPoolInstanceProvider` は `ActiveObjectsCount` プロパティ (プールから返されるオブジェクト数) が最大プール サイズに達しているかどうかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="9b814-126">Otherwise, `ObjectPoolInstanceProvider` checks whether the `ActiveObjectsCount` property (number of objects returned from the pool) has reached the maximum pool size.</span></span> <span data-ttu-id="9b814-127">最大サイズに達していない場合は、新しいインスタンスが作成されて呼び出し元に返され、その後 `ActiveObjectsCount` がインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="9b814-127">If not, a new instance is created and returned to the caller and `ActiveObjectsCount` is subsequently incremented.</span></span> <span data-ttu-id="9b814-128">最大サイズに達していると、構成期間中、オブジェクト作成要求がキューに置かれます。</span><span class="sxs-lookup"><span data-stu-id="9b814-128">Otherwise an object creation request is queued for a configured period of time.</span></span> <span data-ttu-id="9b814-129">`GetObjectFromThePool` の実装を次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="9b814-129">The implementation for `GetObjectFromThePool` is shown in the following sample code.</span></span>  
  
```csharp
private object GetObjectFromThePool()  
{  
    bool didNotTimeout =   
       availableCount.WaitOne(creationTimeout, true);  
    if(didNotTimeout)  
    {  
         object obj = null;  
         lock (poolLock)  
        {  
             if (pool.Count != 0)  
             {  
                   obj = pool.Pop();  
                   activeObjectsCount++;  
             }  
             else if (pool.Count == 0)  
             {  
                   if (activeObjectsCount < maxPoolSize)  
                   {  
                        obj = CreateNewPoolObject();  
                        activeObjectsCount++;  
  
                        #if (DEBUG)  
                        WritePoolMessage(  
                             ResourceHelper.GetString("MsgNewObject"));  
                       #endif  
                   }                          
            }  
           idleTimer.Stop();  
      }  
     // Call the Activate method if possible.  
    if (obj is IObjectControl)  
   {  
         ((IObjectControl)obj).Activate();  
   }  
   return obj;  
}  
throw new TimeoutException(  
ResourceHelper.GetString("ExObjectCreationTimeout"));  
}  
```  
  
 <span data-ttu-id="9b814-130">カスタム `ReleaseInstance` 実装は、解放されたインスタンスをプールに戻し、`ActiveObjectsCount` 値をデクリメントします。</span><span class="sxs-lookup"><span data-stu-id="9b814-130">The custom `ReleaseInstance` implementation adds the released instance back to the pool and decrements the `ActiveObjectsCount` value.</span></span> <span data-ttu-id="9b814-131">EndpointDispatcher はこれらのメソッドをさまざまなスレッドから呼び出すので、`ObjectPoolInstanceProvider` クラスのクラス レベル メンバーへの同期アクセスが必要となります。</span><span class="sxs-lookup"><span data-stu-id="9b814-131">The EndpointDispatcher can call these methods from different threads, and therefore synchronized access to the class level members in the `ObjectPoolInstanceProvider` class is required.</span></span>  
  
```csharp
public void ReleaseInstance(InstanceContext instanceContext, object instance)  
{  
    lock (poolLock)  
    {  
        // Check whether the object can be pooled.   
        // Call the Deactivate method if possible.  
        if (instance is IObjectControl)  
        {  
            IObjectControl objectControl = (IObjectControl)instance;  
            objectControl.Deactivate();  
  
            if (objectControl.CanBePooled)  
            {  
                pool.Push(instance);  
  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectPooled"));  
                #endif                          
            }  
            else  
            {  
                #if(DEBUG)  
                WritePoolMessage(  
                    ResourceHelper.GetString("MsgObjectWasNotPooled"));  
                #endif  
            }  
        }  
        else  
        {  
            pool.Push(instance);  
  
            #if(DEBUG)  
            WritePoolMessage(  
                ResourceHelper.GetString("MsgObjectPooled"));  
            #endif   
        }  
  
        activeObjectsCount--;  
  
        if (activeObjectsCount == 0)  
        {  
            idleTimer.Start();                       
        }  
    }  
  
    availableCount.Release(1);  
}  
```  
  
 <span data-ttu-id="9b814-132">`ReleaseInstance` メソッドは、*初期化のクリーンアップ*機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="9b814-132">The `ReleaseInstance` method provides a *clean up initialization* feature.</span></span> <span data-ttu-id="9b814-133">通常は、プールにはその有効期間中に最小限の数のオブジェクトが保持されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-133">Normally the pool maintains a minimum number of objects for the lifetime of the pool.</span></span> <span data-ttu-id="9b814-134">ただし、使用率が非常に高くなり、プールでオブジェクトを追加作成する必要が生じて、その数が構成に指定されている上限に達する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9b814-134">However, there can be periods of excessive usage that require creating additional objects in the pool to reach the maximum limit specified in the configuration.</span></span> <span data-ttu-id="9b814-135">プールが最終的にアクティブでなくなると、そうした過剰なオブジェクトは余分なオーバーヘッドになります。</span><span class="sxs-lookup"><span data-stu-id="9b814-135">Eventually when the pool becomes less active those surplus objects can become an extra overhead.</span></span> <span data-ttu-id="9b814-136">したがって、`activeObjectsCount` がゼロに達すると、アイドル タイマが起動し、クリーンアップ サイクルがトリガされて実行されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-136">Therefore when the `activeObjectsCount` reaches zero an idle timer is started that triggers and performs a clean-up cycle.</span></span>  
  
```csharp  
if (activeObjectsCount == 0)  
{  
    idleTimer.Start();   
}  
```  
  
 <span data-ttu-id="9b814-137">ServiceModel のレイヤ拡張は、次の動作を使用してフックされます。</span><span class="sxs-lookup"><span data-stu-id="9b814-137">ServiceModel layer extensions are hooked up using the following behaviors:</span></span>  
  
- <span data-ttu-id="9b814-138">サービスの動作 : サービス ランタイム全体のカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="9b814-138">Service Behaviors: These allow for the customization of the entire service runtime.</span></span>  
  
- <span data-ttu-id="9b814-139">エンドポイントの動作 : EndpointDispatcher を含む、特定のサービス エンドポイントのカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="9b814-139">Endpoint Behaviors: These allow for the customization of a particular service endpoint, including the EndpointDispatcher.</span></span>  
  
- <span data-ttu-id="9b814-140">コントラクトの動作 : クライアント上またはサービス上で、それぞれ <xref:System.ServiceModel.Dispatcher.ClientRuntime> クラスまたは <xref:System.ServiceModel.Dispatcher.DispatchRuntime> クラスのカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="9b814-140">Contract Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientRuntime> or <xref:System.ServiceModel.Dispatcher.DispatchRuntime> classes on the client or the service respectively.</span></span>  
  
- <span data-ttu-id="9b814-141">操作の動作 : クライアント上またはサービス上のいずれかで、それぞれ <xref:System.ServiceModel.Dispatcher.ClientOperation> クラスまたは <xref:System.ServiceModel.Dispatcher.DispatchOperation> クラスのカスタマイズを実現します。</span><span class="sxs-lookup"><span data-stu-id="9b814-141">Operation Behaviors: These allow for the customization of either <xref:System.ServiceModel.Dispatcher.ClientOperation> or <xref:System.ServiceModel.Dispatcher.DispatchOperation> classes on the client or the service respectively.</span></span>  
  
 <span data-ttu-id="9b814-142">オブジェクト プール拡張を行うには、エンドポイントの動作またはサービスの動作のどちらかを作成します。</span><span class="sxs-lookup"><span data-stu-id="9b814-142">For the purpose of an object pooling extension, either an endpoint behavior or a service behavior can be created.</span></span> <span data-ttu-id="9b814-143">この例ではサービスの動作を使用します。この動作では、オブジェクト プール機能がサービスの各エンドポイントに適用されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-143">In this example, we use a service behavior, which applies object pooling ability to every endpoint of the service.</span></span> <span data-ttu-id="9b814-144">サービス動作を作成するには、<xref:System.ServiceModel.Description.IServiceBehavior> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="9b814-144">Service behaviors are created by implementing the <xref:System.ServiceModel.Description.IServiceBehavior> interface.</span></span> <span data-ttu-id="9b814-145">ServiceModel にカスタム動作を認識させるには、次のようにいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="9b814-145">There are several ways to make the ServiceModel aware of the custom behaviors:</span></span>  
  
- <span data-ttu-id="9b814-146">カスタム属性を使用する。</span><span class="sxs-lookup"><span data-stu-id="9b814-146">Using a custom attribute.</span></span>  
  
- <span data-ttu-id="9b814-147">カスタム動作をサービス説明の動作コレクションに強制的に追加する。</span><span class="sxs-lookup"><span data-stu-id="9b814-147">Imperatively adding it to the service description’s behaviors collection.</span></span>  
  
- <span data-ttu-id="9b814-148">構成ファイルを拡張する。</span><span class="sxs-lookup"><span data-stu-id="9b814-148">Extending the configuration file.</span></span>  
  
 <span data-ttu-id="9b814-149">このサンプルではカスタム属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="9b814-149">This sample uses a custom attribute.</span></span> <span data-ttu-id="9b814-150"><xref:System.ServiceModel.ServiceHost> が構築されると、サービスの種類の定義で使用されている属性が調べられ、使用可能な動作がサービス説明の動作コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-150">When the <xref:System.ServiceModel.ServiceHost> is constructed, it examines the attributes used in the service’s type definition and adds the available behaviors to the service description’s behaviors collection.</span></span>  
  
 <span data-ttu-id="9b814-151"><xref:System.ServiceModel.Description.IServiceBehavior> インターフェイスには、<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` と <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>の3つのメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="9b814-151">The <xref:System.ServiceModel.Description.IServiceBehavior> interface has three methods: <xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A>`,` <xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A>`,` and <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A>.</span></span> <span data-ttu-id="9b814-152">これらのメソッドは、<xref:System.ServiceModel.ServiceHost> の初期化時に WCF によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-152">These methods are called by WCF when the <xref:System.ServiceModel.ServiceHost> is being initialized.</span></span> <span data-ttu-id="9b814-153">最初に、<xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> が呼び出されます。このメソッドによってサービスの不整合性を検査できます。</span><span class="sxs-lookup"><span data-stu-id="9b814-153"><xref:System.ServiceModel.Description.IServiceBehavior.Validate%2A?displayProperty=nameWithType> is called first; it allows the service to be inspected for inconsistencies.</span></span> <span data-ttu-id="9b814-154">次に、<xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> が呼び出されます。このメソッドは、非常に高度なシナリオでのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="9b814-154"><xref:System.ServiceModel.Description.IServiceBehavior.AddBindingParameters%2A?displayProperty=nameWithType> is called next; this method is only required in very advanced scenarios.</span></span> <span data-ttu-id="9b814-155">最後に、<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> が呼び出されます。このメソッドはランタイムを構成します。</span><span class="sxs-lookup"><span data-stu-id="9b814-155"><xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> is called last and is responsible for configuring the runtime.</span></span> <span data-ttu-id="9b814-156">次のパラメータは、<xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType> に渡されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-156">The following parameters are passed into <xref:System.ServiceModel.Description.IServiceBehavior.ApplyDispatchBehavior%2A?displayProperty=nameWithType>:</span></span>  
  
- <span data-ttu-id="9b814-157">`Description` : このパラメータは、サービス全体のサービスの説明を提供します。</span><span class="sxs-lookup"><span data-stu-id="9b814-157">`Description`: This parameter provides the service description for the entire service.</span></span> <span data-ttu-id="9b814-158">これを使用すると、サービスのエンドポイント、コントラクト、バインディング、およびサービスに関連するその他のデータに関する説明データを検査できます。</span><span class="sxs-lookup"><span data-stu-id="9b814-158">This can be used to inspect description data about the service’s endpoints, contracts, bindings, and other data associated with the service.</span></span>  
  
- <span data-ttu-id="9b814-159">`ServiceHostBase` : このパラメータは、現在初期化中の <xref:System.ServiceModel.ServiceHostBase> を提供します。</span><span class="sxs-lookup"><span data-stu-id="9b814-159">`ServiceHostBase`: This parameter provides the <xref:System.ServiceModel.ServiceHostBase> that is currently being initialized.</span></span>  
  
 <span data-ttu-id="9b814-160">カスタム <xref:System.ServiceModel.Description.IServiceBehavior> 実装では、`ObjectPoolInstanceProvider` の新しいインスタンスがインスタンス化され、<xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> に関連付けられた各 <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> 内の <xref:System.ServiceModel.ServiceHostBase> プロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="9b814-160">In the custom <xref:System.ServiceModel.Description.IServiceBehavior> implementation, a new instance of `ObjectPoolInstanceProvider` is instantiated and assigned to the <xref:System.ServiceModel.Dispatcher.DispatchRuntime.InstanceProvider%2A> property in each <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> that is attached to the <xref:System.ServiceModel.ServiceHostBase>.</span></span>  
  
```csharp
public void ApplyDispatchBehavior(ServiceDescription description, ServiceHostBase serviceHostBase)  
{  
    if (enabled)  
    {  
        // Create an instance of the ObjectPoolInstanceProvider.  
        instanceProvider = new ObjectPoolInstanceProvider(description.ServiceType,  
        maxPoolSize, minPoolSize, creationTimeout);  
  
        // Assign our instance provider to Dispatch behavior in each   
        // endpoint.  
        foreach (ChannelDispatcherBase cdb in serviceHostBase.ChannelDispatchers)  
        {  
             ChannelDispatcher cd = cdb as ChannelDispatcher;  
             if (cd != null)  
             {  
                 foreach (EndpointDispatcher ed in cd.Endpoints)  
                 {  
                        ed.DispatchRuntime.InstanceProvider = instanceProvider;  
                 }  
             }  
         }  
     }  
}   
```  
  
 <span data-ttu-id="9b814-161"><xref:System.ServiceModel.Description.IServiceBehavior> 実装のほかにも、`ObjectPoolingAttribute` クラスには属性引数を使用してオブジェクト プールをカスタマイズするいくつかのメンバがあります。</span><span class="sxs-lookup"><span data-stu-id="9b814-161">In addition to an <xref:System.ServiceModel.Description.IServiceBehavior> implementation the `ObjectPoolingAttribute` class has several members to customize the object pool using the attribute arguments.</span></span> <span data-ttu-id="9b814-162">こうしたメンバには `MaxSize`、`MinSize`、`Enabled`、`CreationTimeout` などがあり、.NET Enterprise Services で提供されるオブジェクト プール機能のセットに一致します。</span><span class="sxs-lookup"><span data-stu-id="9b814-162">These members include `MaxSize`, `MinSize`, `Enabled` and `CreationTimeout`, to match the object pooling feature set provided by .NET Enterprise Services.</span></span>  
  
 <span data-ttu-id="9b814-163">新しく作成されたカスタム `ObjectPooling` 属性を使用してサービス実装に注釈を付けることにより、オブジェクトプール動作を WCF サービスに追加できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9b814-163">The object pooling behavior can now be added to a WCF service by annotating the service implementation with the newly created custom `ObjectPooling` attribute.</span></span>  
  
```csharp  
[ObjectPooling(MaxSize=1024, MinSize=10, CreationTimeout=30000]      
public class PoolService : IPoolService  
{  
  // …  
}  
```  
  
## <a name="hooking-activation-and-deactivation"></a><span data-ttu-id="9b814-164">アクティブ化と非アクティブ化のフック</span><span class="sxs-lookup"><span data-stu-id="9b814-164">Hooking Activation and Deactivation</span></span>  
 <span data-ttu-id="9b814-165">オブジェクト プールの主な目的は、比較的負荷のかかる作成および初期化を伴う有効期間の短いオブジェクトを最適化することです。</span><span class="sxs-lookup"><span data-stu-id="9b814-165">The primary objective of object pooling is to optimize short-lived objects with relatively expensive creation and initialization.</span></span> <span data-ttu-id="9b814-166">そのため、オブジェクト プールが適切に使用された場合は、アプリケーションのパフォーマンスを大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="9b814-166">Therefore it can give a dramatic performance boost to an application if properly used.</span></span> <span data-ttu-id="9b814-167">オブジェクトはプールから返されるので、コンストラクタが呼び出されるのは 1 回だけです。</span><span class="sxs-lookup"><span data-stu-id="9b814-167">Because the object is returned from the pool, the constructor is called only once.</span></span> <span data-ttu-id="9b814-168">ただし一部のアプリケーションでは、単一のコンテキスト内で使用されるリソースを初期化してクリーンアップできるようにするために、ある一定のレベルの制御が必要になります。</span><span class="sxs-lookup"><span data-stu-id="9b814-168">However, some applications require some level of control so that they can initialize and clean-up the resources used during a single context.</span></span> <span data-ttu-id="9b814-169">たとえば、一連の計算に使用されているオブジェクトは、次の計算を実行する前に、そのオブジェクトのプライベート フィールドをリセットできます。</span><span class="sxs-lookup"><span data-stu-id="9b814-169">For example, an object being used for a set of calculations can reset its private fields before processing the next calculation.</span></span> <span data-ttu-id="9b814-170">Enterprise Services では、オブジェクト開発者が `Activate` ベース クラスの `Deactivate` メソッドおよび <xref:System.EnterpriseServices.ServicedComponent> メソッドをオーバーライドすることにより、コンテキスト固有のこの種の初期化が実現されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-170">Enterprise Services enabled this kind of context-specific initialization by letting the object developer override `Activate` and `Deactivate` methods from the <xref:System.EnterpriseServices.ServicedComponent> base class.</span></span>  
  
 <span data-ttu-id="9b814-171">オブジェクト プールは、オブジェクトがプールから返される直前に `Activate` メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9b814-171">The object pool calls the `Activate` method just before returning the object from the pool.</span></span> <span data-ttu-id="9b814-172">オブジェクトがプールに返される際には `Deactivate` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-172">`Deactivate` is called when the object returns back to the pool.</span></span> <span data-ttu-id="9b814-173"><xref:System.EnterpriseServices.ServicedComponent> ベース クラスには、`boolean` という `CanBePooled` プロパティもあります。このプロパティを使用すると、オブジェクトをさらにプールできるかどうかをプールに通知できます。</span><span class="sxs-lookup"><span data-stu-id="9b814-173">The <xref:System.EnterpriseServices.ServicedComponent> base class also has a `boolean` property called `CanBePooled`, which can be used to notify the pool whether the object can be pooled further.</span></span>  
  
 <span data-ttu-id="9b814-174">このサンプルではこの機能に似た動作が行われるように、前述のメンバを持つパブリック インターフェイス (`IObjectControl`) を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="9b814-174">To mimic this functionality, the sample declares a public interface (`IObjectControl`) that has the aforementioned members.</span></span> <span data-ttu-id="9b814-175">このインターフェイスは、コンテキスト固有の初期化を提供するためのサービス クラスによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-175">This interface is then implemented by service classes intended to provide context specific initialization.</span></span> <span data-ttu-id="9b814-176"><xref:System.ServiceModel.Dispatcher.IInstanceProvider> の実装は、これらの要件を満たすように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b814-176">The <xref:System.ServiceModel.Dispatcher.IInstanceProvider> implementation must be modified to meet these requirements.</span></span> <span data-ttu-id="9b814-177">次に、`GetInstance` メソッドを呼び出してオブジェクトを取得するたびに、オブジェクトが `IObjectControl.` を実装しているかどうかを確認する必要があります。実行されている場合は、`Activate` メソッドを適切に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b814-177">Now, each time you get an object by calling the `GetInstance` method, you must check whether the object implements `IObjectControl.` If it does, you must call the `Activate` method appropriately.</span></span>  
  
```csharp  
if (obj is IObjectControl)  
{  
    ((IObjectControl)obj).Activate();  
}  
```  
  
 <span data-ttu-id="9b814-178">オブジェクトをプールに返すときには、そのオブジェクトをプールに追加し直す前に、`CanBePooled` プロパティのチェックが必要です。</span><span class="sxs-lookup"><span data-stu-id="9b814-178">When returning an object to the pool, a check is required for the `CanBePooled` property before adding the object back to the pool.</span></span>  
  
```csharp  
if (instance is IObjectControl)  
{  
    IObjectControl objectControl = (IObjectControl)instance;  
    objectControl.Deactivate();  
    if (objectControl.CanBePooled)  
    {  
       pool.Push(instance);  
    }  
}  
```  
  
 <span data-ttu-id="9b814-179">オブジェクトをプールできるかどうかはサービス開発者が決定できるので、指定時間におけるプール内のオブジェクト数は、最低サイズ未満になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9b814-179">Because the service developer can decide whether an object can be pooled, the object count in the pool at a given time can go below the minimum size.</span></span> <span data-ttu-id="9b814-180">したがって、オブジェクト数が最低レベル未満になっているかどうかをチェックし、クリーンアップ手順において必要な初期化を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b814-180">Therefore you must check whether the object count has gone below the minimum level and perform the necessary initialization in the clean-up procedure.</span></span>  
  
```csharp  
// Remove the surplus objects.  
if (pool.Count > minPoolSize)  
{  
  // Clean the surplus objects.  
}                      
else if (pool.Count < minPoolSize)  
{  
  // Reinitialize the missing objects.  
  while(pool.Count != minPoolSize)  
  {  
    pool.Push(CreateNewPoolObject());  
  }  
}  
```  
  
 <span data-ttu-id="9b814-181">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-181">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="9b814-182">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="9b814-182">Press Enter in each console window to shut down the service and client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9b814-183">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="9b814-183">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9b814-184">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9b814-184">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9b814-185">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9b814-185">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="9b814-186">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9b814-186">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9b814-187">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9b814-187">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9b814-188">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9b814-188">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="9b814-189">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9b814-189">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9b814-190">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9b814-190">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Instancing\Initialization`  
