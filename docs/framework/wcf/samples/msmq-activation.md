---
title: MSMQ アクティベーション
ms.date: 03/30/2017
ms.assetid: e3834149-7b8c-4a54-806b-b4296720f31d
ms.openlocfilehash: 805ab78908b4d1146cce94cac5357bafbb35c832
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744791"
---
# <a name="msmq-activation"></a><span data-ttu-id="47733-102">MSMQ アクティベーション</span><span class="sxs-lookup"><span data-stu-id="47733-102">MSMQ Activation</span></span>

<span data-ttu-id="47733-103">このサンプルでは、メッセージ キューから読み取ったアプリケーションを、Windows プロセス アクティブ化サービス (WAS) でホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="47733-103">This sample demonstrates how to host applications in Windows Process Activation Service (WAS) that are read from a message queue.</span></span> <span data-ttu-id="47733-104">このサンプルでは、`netMsmqBinding` を使用し、[双方向の通信](../../../../docs/framework/wcf/samples/two-way-communication.md)のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="47733-104">This sample uses the `netMsmqBinding` and is based on the [Two-Way Communication](../../../../docs/framework/wcf/samples/two-way-communication.md) sample.</span></span> <span data-ttu-id="47733-105">この場合、サービスは Web ホスト アプリケーションの 1 つであり、クライアントは自己ホスト型です。クライアントはコンソールに出力して、送信された発注書のステータスを確認します。</span><span class="sxs-lookup"><span data-stu-id="47733-105">The service in this case is a Web-hosted application and the client is self-hosted and outputs to the console to observe the status of purchase orders submitted.</span></span>

> [!NOTE]
> <span data-ttu-id="47733-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47733-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!NOTE]
> <span data-ttu-id="47733-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="47733-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="47733-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="47733-108">Check for the following (default) directory before continuing.</span></span>
>
> <span data-ttu-id="47733-109">\<InstallDrive >:\ WF_WCF_Samples</span><span class="sxs-lookup"><span data-stu-id="47733-109">\<InstallDrive>:\WF_WCF_Samples</span></span>
>
> <span data-ttu-id="47733-110">このディレクトリが存在しない場合は、 [.NET Framework 4 の Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプル](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WCF と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="47733-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all WCF and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="47733-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="47733-111">This sample is located in the following directory.</span></span>
>
> <span data-ttu-id="47733-112">\<InstallDrive >: \Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span><span class="sxs-lookup"><span data-stu-id="47733-112">\<InstallDrive>:\Samples\WCFWFCardSpace\WCF\Basic\Services\Hosting\WASHost\MsmqActivation.</span></span>

<span data-ttu-id="47733-113">Windows プロセスアクティブ化サービス (WAS) は、Windows Server 2008 用の新しいプロセスアクティブ化機構であり、以前は HTTP ベースのアプリケーションのみが http 以外のプロトコルを使用するアプリケーションに対して使用できるようになった IIS に似た機能を提供しています。</span><span class="sxs-lookup"><span data-stu-id="47733-113">Windows Process Activation Service (WAS), the new process activation mechanism for Windows Server 2008, provides IIS-like features that were previously only available to HTTP-based applications to applications that use non-HTTP protocols.</span></span> <span data-ttu-id="47733-114">Windows Communication Foundation (WCF) は、リスナーアダプターインターフェイスを使用して、WCF でサポートされている HTTP 以外のプロトコル (TCP、名前付きパイプ、MSMQ など) を介して受信されるアクティブ化要求を伝達します。</span><span class="sxs-lookup"><span data-stu-id="47733-114">Windows Communication Foundation (WCF) uses the Listener Adapter interface to communicate activation requests that are received over the non-HTTP protocols supported by WCF, such as TCP, Named Pipes, and MSMQ.</span></span> <span data-ttu-id="47733-115">HTTP 以外のプロトコルを介して要求を受信する機能は、SMSvcHost.exe で実行されるマネージド Windows サービスによってホストされます。</span><span class="sxs-lookup"><span data-stu-id="47733-115">The functionality for receiving requests over non-HTTP protocols is hosted by managed Windows services running in SMSvcHost.exe.</span></span>

<span data-ttu-id="47733-116">Net.Msmq リスナ アダプタ サービス (NetMsmqActivator) は、キュー内のメッセージに基づいてキューに置かれたアプリケーションをアクティブ化します。</span><span class="sxs-lookup"><span data-stu-id="47733-116">The Net.Msmq Listener Adapter service (NetMsmqActivator) activates queued applications based on messages in the queue.</span></span>

<span data-ttu-id="47733-117">クライアントはトランザクションのスコープ内から発注書をサービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="47733-117">The client sends purchase orders to the service from within the scope of a transaction.</span></span> <span data-ttu-id="47733-118">サービスはトランザクション内で注文を受信して、処理します。</span><span class="sxs-lookup"><span data-stu-id="47733-118">The service receives the orders in a transaction and processes them.</span></span> <span data-ttu-id="47733-119">その後、サービスは注文ステータスをクライアントに返信します。</span><span class="sxs-lookup"><span data-stu-id="47733-119">The service then calls back the client with the status of the order.</span></span> <span data-ttu-id="47733-120">双方向通信を使用するには、クライアントとサービスの両方がキューを使用して、発注書や注文ステータスをキューに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47733-120">To facilitate two-way communication the client and service both use queues to enqueue purchase orders and order status.</span></span>

<span data-ttu-id="47733-121">`IOrderProcessor` サービス コントラクトは、キューを使用する一方向サービス操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="47733-121">The service contract `IOrderProcessor` defines the one-way service operations that work with queuing.</span></span> <span data-ttu-id="47733-122">サービス操作は、注文ステータスをクライアントに送信するために応答エンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="47733-122">The service operation uses the reply endpoint to send order statuses to the client.</span></span> <span data-ttu-id="47733-123">応答エンドポイントのアドレスは、注文ステータスをクライアントに返信する際に使用されるキューの URI です。</span><span class="sxs-lookup"><span data-stu-id="47733-123">The reply endpoint's address is the URI of the queue used to send the order status back to the client.</span></span> <span data-ttu-id="47733-124">注文処理アプリケーションは、このコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="47733-124">The order processing application implements this contract.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true)]
    void SubmitPurchaseOrder(PurchaseOrder po,
                                           string reportOrderStatusTo);
}
```

<span data-ttu-id="47733-125">注文ステータスを送信する応答コントラクトは、クライアントが指定します。</span><span class="sxs-lookup"><span data-stu-id="47733-125">The reply contract to send order status to is specified by the client.</span></span> <span data-ttu-id="47733-126">クライアントは注文ステータス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="47733-126">The client implements the order status contract.</span></span> <span data-ttu-id="47733-127">サービスは、このコントラクトについて生成されたクライアントを使用して、注文ステータスをクライアントに返信します。</span><span class="sxs-lookup"><span data-stu-id="47733-127">The service uses the generated client of this contract to send order status back to the client.</span></span>

```csharp
[ServiceContract]
public interface IOrderStatus
{
    [OperationContract(IsOneWay = true)]
    void OrderStatus(string poNumber, string status);
}
```

<span data-ttu-id="47733-128">サービス操作は、送信された発注書を処理します。</span><span class="sxs-lookup"><span data-stu-id="47733-128">The service operation processes the submitted purchase order.</span></span> <span data-ttu-id="47733-129"><xref:System.ServiceModel.OperationBehaviorAttribute> はサービス操作に適用され、キューからのメッセージの受信に使用されるトランザクション内で登録リストを自動で作成し、サービス操作が完了したときにトランザクションを自動で完了するように指定します。</span><span class="sxs-lookup"><span data-stu-id="47733-129">The <xref:System.ServiceModel.OperationBehaviorAttribute> is applied to the service operation to specify automatic enlistment in the transaction that is used to receive the message from the queue and automatic completion of the transaction on completion of the service operation.</span></span> <span data-ttu-id="47733-130">`Orders` クラスは、注文処理機能をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="47733-130">The `Orders` class encapsulates order processing functionality.</span></span> <span data-ttu-id="47733-131">この例では、発注書をディクショナリに追加します。</span><span class="sxs-lookup"><span data-stu-id="47733-131">In this case, it adds the purchase order to a dictionary.</span></span> <span data-ttu-id="47733-132">このサービス操作が帰属するしているトランザクションは、`Orders` クラス内の操作で使用できます。</span><span class="sxs-lookup"><span data-stu-id="47733-132">The transaction that the service operation enlisted in is available to the operations in the `Orders` class.</span></span>

<span data-ttu-id="47733-133">サービス操作は、送信された発注書を処理するだけでなく、注文ステータスをクライアントに戻します。</span><span class="sxs-lookup"><span data-stu-id="47733-133">The service operation, in addition to processing the submitted purchase order, replies back to the client about the status of the order.</span></span>

```csharp
public class OrderProcessorService : IOrderProcessor
{
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po, string reportOrderStatusTo)
    {
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
        Console.WriteLine("Sending back order status information");
        NetMsmqBinding msmqCallbackBinding = new NetMsmqBinding();
        msmqCallbackBinding.Security.Mode = NetMsmqSecurityMode.None;
        OrderStatusClient client = new OrderStatusClient(msmqCallbackBinding, new EndpointAddress(reportOrderStatusTo));
        // please note that the same transaction that is used to dequeue purchase order is used
        // to send back order status
        using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))
        {
            client.OrderStatus(po.PONumber, po.Status);
            scope.Complete();
        }
    }
}
```

<span data-ttu-id="47733-134">使用するクライアント バインディングの指定には、構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="47733-134">The client binding to use is specified using a configuration file.</span></span>

<span data-ttu-id="47733-135">MSMQ キュー名は、構成ファイルの appSettings セクションで指定されます。</span><span class="sxs-lookup"><span data-stu-id="47733-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="47733-136">サービスのエンドポイントは、構成ファイルの System.serviceModel セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="47733-136">The endpoint for the service is defined in the System.serviceModel section of the configuration file.</span></span>

> [!NOTE]
> <span data-ttu-id="47733-137">MSMQ のキュー名とエンドポイント アドレスでは、若干異なるアドレス表記が使用されています。</span><span class="sxs-lookup"><span data-stu-id="47733-137">The MSMQ queue name and endpoint address use slightly different addressing conventions.</span></span> <span data-ttu-id="47733-138">MSMQ のキュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="47733-138">The MSMQ queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="47733-139">WCF エンドポイントアドレスは、net.tcp: scheme を指定し、ローカルコンピューターに "localhost" を使用して、パスにスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="47733-139">The WCF endpoint address specifies a net.msmq: scheme, uses "localhost" for the local computer, and uses forward slashes in its path.</span></span> <span data-ttu-id="47733-140">リモート コンピューターでホストされているキューからの読み出しを行うには、"." や "localhost" をリモート コンピューター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="47733-140">To read from a queue that is hosted on the remote computer, replace the "." and "localhost" to the remote computer name.</span></span>

<span data-ttu-id="47733-141">クラスの名前が付いた .svc ファイルは、WAS でのサービス コードのホストに使用されます。</span><span class="sxs-lookup"><span data-stu-id="47733-141">A .svc file with the name of the class is used to host the service code in WAS.</span></span>

<span data-ttu-id="47733-142">Service.svc ファイル自体には、`OrderProcessorService` を作成するディレクティブが含まれます。</span><span class="sxs-lookup"><span data-stu-id="47733-142">The Service.svc file itself contains a directive to create the `OrderProcessorService`.</span></span>

`<%@ServiceHost language="c#" Debug="true" Service="Microsoft.ServiceModel.Samples.OrderProcessorService"%>`

<span data-ttu-id="47733-143">さらに、Service.svc ファイルには、System.Transactions.dll を読み込むためのアセンブリ ディレクティブも含まれます。</span><span class="sxs-lookup"><span data-stu-id="47733-143">The Service.svc file also contains an assembly directive to ensure that System.Transactions.dll is loaded.</span></span>

`<%@Assembly name="System.Transactions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"%>`

<span data-ttu-id="47733-144">クライアントはトランザクション スコープを作成します。</span><span class="sxs-lookup"><span data-stu-id="47733-144">The client creates a transaction scope.</span></span> <span data-ttu-id="47733-145">サービスとの通信はトランザクションのスコープ内で実行され、すべてのメッセージが成功か失敗かを示すアトミックな単位として扱われます。</span><span class="sxs-lookup"><span data-stu-id="47733-145">Communication with the service takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="47733-146">トランザクションは、トランザクション スコープで `Complete` を呼び出すことでコミットされます。</span><span class="sxs-lookup"><span data-stu-id="47733-146">The transaction is committed by calling `Complete` on the transaction scope.</span></span>

```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderStatusService)))
{
    // Open the ServiceHostBase to create listeners and start listening
    // for order status messages.
    serviceHost.Open();

    // Create a proxy with given client endpoint configuration
    OrderProcessorClient client = new OrderProcessorClient();

    // Create the purchase order
    PurchaseOrder po = new PurchaseOrder();
    po.CustomerId = "somecustomer.com";
    po.PONumber = Guid.NewGuid().ToString();

    PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();
    lineItem1.ProductId = "Blue Widget";
    lineItem1.Quantity = 54;
    lineItem1.UnitCost = 29.99F;

    PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();
    lineItem2.ProductId = "Red Widget";
    lineItem2.Quantity = 890;
    lineItem2.UnitCost = 45.89F;

    po.orderLineItems = new PurchaseOrderLineItem[2];
    po.orderLineItems[0] = lineItem1;
    po.orderLineItems[1] = lineItem2;

    //Create a transaction scope.
    using (TransactionScope scope = new
        TransactionScope(TransactionScopeOption.Required))
    {
        // Make a queued call to submit the purchase order
        client.SubmitPurchaseOrder(po,
       "net.msmq://localhost/private/ServiceModelSamplesOrder/OrderStatus");
        // Complete the transaction.
        scope.Complete();
    }

    //Closing the client gracefully closes the connection and cleans up
    //resources
    client.Close();

    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();

    // Close the ServiceHostBase to shutdown the service.
    serviceHost.Close();
    }
```

<span data-ttu-id="47733-147">クライアント コードは `IOrderStatus` コントラクトを実装して、サービスからの注文ステータスを受信します。</span><span class="sxs-lookup"><span data-stu-id="47733-147">The client code implements the `IOrderStatus` contract to receive order status from the service.</span></span> <span data-ttu-id="47733-148">この場合は、注文ステータスを出力します。</span><span class="sxs-lookup"><span data-stu-id="47733-148">In this case, it prints out the order status.</span></span>

```csharp
[ServiceBehavior]
public class OrderStatusService : IOrderStatus
{
    [OperationBehavior(TransactionAutoComplete = true,
                        TransactionScopeRequired = true)]
    public void OrderStatus(string poNumber, string status)
    {
        Console.WriteLine("Status of order {0}:{1} ",
                                         poNumber , status);
    }
}
```

<span data-ttu-id="47733-149">注文ステータス キューは `Main` メソッド内で作成します。</span><span class="sxs-lookup"><span data-stu-id="47733-149">The order status queue is created in the `Main` method.</span></span> <span data-ttu-id="47733-150">クライアント構成には、注文ステータス サービスをホストするための注文ステータス サービス構成が含まれています。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="47733-150">The client configuration includes the order status service configuration to host the order status service, as shown in the following sample configuration.</span></span>

```xml
<appSettings>
    <!-- use appSetting to configure MSMQ queue name -->
    <add key="targetQueueName" value=".\private$\ServiceModelSamples/service.svc" />
    <add key="responseQueueName" value=".\private$\ServiceModelSamples/OrderStatus" />
  </appSettings>

<system.serviceModel>

    <services>
      <service
         name="Microsoft.ServiceModel.Samples.OrderStatusService">
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamples/OrderStatus"
                  binding="netMsmqBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderStatus" />
      </service>
    </services>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint name="OrderProcessorEndpoint"
                address="net.msmq://localhost/private/ServiceModelSamples/service.svc"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
    </client>

  </system.serviceModel>
```

<span data-ttu-id="47733-151">サンプルを実行すると、クライアントとサービスのアクティビティがサーバーとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="47733-151">When you run the sample, the client and service activities are displayed in both the server and client console windows.</span></span> <span data-ttu-id="47733-152">サーバーがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="47733-152">You can see the server receive messages from the client.</span></span> <span data-ttu-id="47733-153">どちらかのコンソールで Enter キーを押すと、サーバーとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="47733-153">Press ENTER in each console window to shut down the server and client.</span></span>

<span data-ttu-id="47733-154">クライアントには、サーバーから送信された注文ステータス情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="47733-154">The client displays the order status information sent by the server:</span></span>

```console
Press <ENTER> to terminate client.
Status of order 70cf9d63-3dfa-4e69-81c2-23aa4478ebed :Pending
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="47733-155">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="47733-155">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="47733-156">WAS のアクティブ化に必要な IIS 7.0 がインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="47733-156">Ensure that IIS 7.0 is installed, as it is required for WAS activation.</span></span>

2. <span data-ttu-id="47733-157">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="47733-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span> <span data-ttu-id="47733-158">さらに、WCF 非 HTTP アクティブ化コンポーネントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="47733-158">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="47733-159">**[スタート]** メニューの **[コントロール パネル]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47733-159">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="47733-160">**[プログラムと機能]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47733-160">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="47733-161">[ **Windows の機能の有効化または無効化] を**クリックします。</span><span class="sxs-lookup"><span data-stu-id="47733-161">Click **Turn Windows Features on or off**.</span></span>

    4. <span data-ttu-id="47733-162">**[機能の概要]** で、 **[機能の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47733-162">Under **Features Summary**, click **Add Features**.</span></span>

    5. <span data-ttu-id="47733-163">**[Microsoft .NET Framework 3.0]** ノードを展開し、 **[WINDOWS COMMUNICATION FOUNDATION の非 HTTP アクティブ化]** 機能をオンにします。</span><span class="sxs-lookup"><span data-stu-id="47733-163">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="47733-164">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="47733-164">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="47733-165">コマンド ウィンドウで client.exe を実行することにより、クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="47733-165">Run the client by executing client.exe from a command window.</span></span> <span data-ttu-id="47733-166">これによってキューが作成され、メッセージがそのキューに送信されます。</span><span class="sxs-lookup"><span data-stu-id="47733-166">This creates the queue and sends a message to it.</span></span> <span data-ttu-id="47733-167">クライアントを実行しながら、メッセージを読み取るサービスの結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="47733-167">Leave the client running to see the result of the service reading the message</span></span>

5. <span data-ttu-id="47733-168">MSMQ アクティベーション サービスは、既定では NETWORK SERVICE として動作します。</span><span class="sxs-lookup"><span data-stu-id="47733-168">The MSMQ activation service runs as Network Service by default.</span></span> <span data-ttu-id="47733-169">そのため、アプリケーションのアクティブ化に使用されるキューには、NETWORK SERVICE アカウントによる受信およびピーク権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="47733-169">Therefore, the queue that is used to activate the application must have receive and peek permissions for Network Service.</span></span> <span data-ttu-id="47733-170">この権限は、メッセージ キュー MMC を使用して追加できます。</span><span class="sxs-lookup"><span data-stu-id="47733-170">This can be added by using the Message Queuing MMC:</span></span>

    1. <span data-ttu-id="47733-171">**[スタート]** メニューの **[実行]** をクリックし、「`Compmgmt.msc`」と入力して、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="47733-171">From the **Start** menu, click **Run**, then type `Compmgmt.msc` and press ENTER.</span></span>

    2. <span data-ttu-id="47733-172">**[サービスとアプリケーション]** で、 **[メッセージキュー]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="47733-172">Under **Services and Applications**, expand **Message Queuing**.</span></span>

    3. <span data-ttu-id="47733-173">**[専用キュー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="47733-173">Click **Private Queues**.</span></span>

    4. <span data-ttu-id="47733-174">キュー (servicemodelsamples/Service .svc) を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47733-174">Right-click the queue (servicemodelsamples/Service.svc) and choose **Properties**.</span></span>

    5. <span data-ttu-id="47733-175">**セキュリティ** タブで **追加** をクリックし、ネットワークサービスに対して ピーク および 受信 アクセス許可を付与します。</span><span class="sxs-lookup"><span data-stu-id="47733-175">On the **Security** tab, click **Add** and give peek and receive permissions to Network Service.</span></span>

6. <span data-ttu-id="47733-176">MSMQ アクティブ化をサポートするよう Windows プロセス アクティブ化サービス (WAS) を設定します。</span><span class="sxs-lookup"><span data-stu-id="47733-176">Configure the Windows Process Activation Service (WAS) to support MSMQ activation.</span></span>

    <span data-ttu-id="47733-177">便宜上次の 2 つの手順が、サンプル ディレクトリにある AddMsmqSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="47733-177">As a convenience, the following steps are implemented in a batch file called AddMsmqSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="47733-178">net.msmq アクティベーションをサポートするには、既定の Web サイトをあらかじめ net.msmq プロトコルにバインドしておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="47733-178">To support net.msmq activation, the default Web site must first be bound to the net.msmq protocol.</span></span> <span data-ttu-id="47733-179">これは、IIS7.0 管理ツール セットと共にインストールされる appcmd.exe を使用して行います。</span><span class="sxs-lookup"><span data-stu-id="47733-179">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="47733-180">権限のレベルが高い (管理者の) コマンド プロンプトで、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="47733-180">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="47733-181">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="47733-181">This command is a single line of text.</span></span>

        <span data-ttu-id="47733-182">このコマンドによって、既定の Web サイトに net.msmq サイト バインディングを追加します。</span><span class="sxs-lookup"><span data-stu-id="47733-182">This command adds a net.msmq site binding to the default Web site.</span></span>

    2. <span data-ttu-id="47733-183">サイト内のすべてのアプリケーションが同じ net.msmq バインディングを共有しますが、net.msmq サポートの有効化はアプリケーションごとに指定できます。</span><span class="sxs-lookup"><span data-stu-id="47733-183">Although all applications within a site share a common net.msmq binding, each application can enable net.msmq support individually.</span></span> <span data-ttu-id="47733-184">/servicemodelsamples アプリケーションで net.msmq を有効にするには、権限のレベルが高いコマンド プロンプトから、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="47733-184">To enable net.msmq for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.msmq
        ```

        > [!NOTE]
        > <span data-ttu-id="47733-185">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="47733-185">This command is a single line of text.</span></span>

        <span data-ttu-id="47733-186">このコマンドにより、`http://localhost/servicemodelsamples` と `net.msmq://localhost/servicemodelsamples`を使用して/servicemodelsamples アプリケーションにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="47733-186">This command enables the /servicemodelsamples application to be accessed using `http://localhost/servicemodelsamples` and `net.msmq://localhost/servicemodelsamples`.</span></span>

7. <span data-ttu-id="47733-187">まだ確認していない場合は、MSMQ アクティベーション サービスが有効になっていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="47733-187">If you have not done so previously, ensure that the MSMQ activation service is enabled.</span></span> <span data-ttu-id="47733-188">**[スタート]** メニューの **[実行]** をクリックし、「`Services.msc`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="47733-188">From the **Start** menu, click **Run**, and type `Services.msc`.</span></span> <span data-ttu-id="47733-189">サービスの一覧で、 **Net.tcp リスナーアダプター**を検索します。</span><span class="sxs-lookup"><span data-stu-id="47733-189">Search the list of services for the **Net.Msmq Listener Adapter**.</span></span> <span data-ttu-id="47733-190">右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47733-190">Right-click and select **Properties**.</span></span> <span data-ttu-id="47733-191">**[スタートアップの種類]** を **[自動]** に設定し、 **[適用]** をクリックして、 **[開始]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="47733-191">Set the **Startup Type** to **Automatic**, click **Apply** and click the **Start** button.</span></span> <span data-ttu-id="47733-192">この手順は、Net.Msmq リスナー アダプター サービスを初めて使用する前に 1 回だけ実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="47733-192">This step must only be done once prior to the first usage of the Net.Msmq Listener Adapter service.</span></span>

8. <span data-ttu-id="47733-193">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="47733-193">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="47733-194">さらに、発注書を送信するときのキューの URI 内のコンピューター名を反映するように、発注書を送信するクライアントのコードを変更します。</span><span class="sxs-lookup"><span data-stu-id="47733-194">Additionally, change the code on the client that submits the purchase order to reflect the computer name in the URI of the queue when submitting the purchase order.</span></span> <span data-ttu-id="47733-195">次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="47733-195">Use the following code:</span></span>

    ```csharp
    client.SubmitPurchaseOrder(po, "net.msmq://localhost/private/ServiceModelSamples/OrderStatus");
    ```

9. <span data-ttu-id="47733-196">このサンプル用に追加した net.msmq サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="47733-196">Remove the net.msmq site binding you added for this sample.</span></span>

    <span data-ttu-id="47733-197">便宜上次の 2 つの手順が、サンプル ディレクトリにある RemoveMsmqSiteBinding.cmd というバッチ ファイルに実装されています。</span><span class="sxs-lookup"><span data-stu-id="47733-197">As a convenience, the following steps are implemented in a batch file called RemoveMsmqSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="47733-198">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、有効なプロトコルの一覧から net.msmq を削除します。</span><span class="sxs-lookup"><span data-stu-id="47733-198">Remove net.msmq from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="47733-199">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="47733-199">This command is a single line of text.</span></span>

    2. <span data-ttu-id="47733-200">権限のレベルが高いコマンド プロンプトから次のコマンドを実行して、net.msmq サイト バインディングを削除します。</span><span class="sxs-lookup"><span data-stu-id="47733-200">Remove the net.msmq site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.msmq',bindingInformation='localhost']
        ```

        > [!NOTE]
        > <span data-ttu-id="47733-201">このコマンドはテキスト 1 行です。</span><span class="sxs-lookup"><span data-stu-id="47733-201">This command is a single line of text.</span></span>

    > [!WARNING]
    > <span data-ttu-id="47733-202">バッチ ファイルを実行すると、DefaultAppPool がリセットされて .NET Framework Version 2.0 で実行されます。</span><span class="sxs-lookup"><span data-stu-id="47733-202">Running the batch file will reset the DefaultAppPool to run using .NET Framework version 2.0.</span></span>

<span data-ttu-id="47733-203">`netMsmqBinding` バインディング トランスポートを使用する場合の既定では、セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="47733-203">By default with the `netMsmqBinding` binding transport, security is enabled.</span></span> <span data-ttu-id="47733-204">トランスポート セキュリティの種類は、`MsmqAuthenticationMode` と `MsmqProtectionLevel` の 2 つのプロパティで決まります。</span><span class="sxs-lookup"><span data-stu-id="47733-204">Two properties, `MsmqAuthenticationMode` and `MsmqProtectionLevel`, together determine the type of transport security.</span></span> <span data-ttu-id="47733-205">既定の設定では、認証モードは `Windows`、保護レベルは `Sign` です。</span><span class="sxs-lookup"><span data-stu-id="47733-205">By default the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="47733-206">MSMQ の認証および署名の機能を利用するには、ドメインに属している必要があります。</span><span class="sxs-lookup"><span data-stu-id="47733-206">For MSMQ to provide the authentication and signing feature, it must be part of a domain.</span></span> <span data-ttu-id="47733-207">このサンプルをドメインに属していないコンピューターで実行すると、"ユーザーの内部メッセージ キュー認証情報は存在しません" というエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="47733-207">If you run this sample on a computer that is not part of a domain, the following error is received: "User's internal message queuing certificate does not exist".</span></span>

### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup"></a><span data-ttu-id="47733-208">ワークグループに参加しているコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="47733-208">To run the sample on a computer joined to a workgroup</span></span>

1. <span data-ttu-id="47733-209">ドメインに属していないコンピューターを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを "none" に設定します。サンプル構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="47733-209">If your computer is not part of a domain, turn off transport security by setting the authentication mode and protection level to none as shown in the following sample configuration.</span></span>

    ```xml
    <bindings>
        <netMsmqBinding>
            <binding configurationName="TransactedBinding">
                <security mode="None"/>
            </binding>
        </netMsmqBinding>
    </bindings>
    ```

2. <span data-ttu-id="47733-210">サンプルを実行する前に、サーバーとクライアントの両方の構成を変更します。</span><span class="sxs-lookup"><span data-stu-id="47733-210">Change the configuration on both the server and the client before you run the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="47733-211">`security mode` を `None` に設定することは、`MsmqAuthenticationMode`、`MsmqProtectionLevel`、および `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="47733-211">Setting `security mode` to `None` is equivalent to setting `MsmqAuthenticationMode`, `MsmqProtectionLevel` and `Message` security to `None`.</span></span>

3. <span data-ttu-id="47733-212">ワークグループに参加しているコンピューターでアクティブ化を有効にするには、アクティベーション サービスとワーカー プロセスの両方を特定のユーザー アカウントで実行する必要があります (どちらも同じアカウントを使用する必要があります)。さらに、キューはその特定のユーザー アカウントの ACL に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="47733-212">To enable activation in a computer joined to a workgroup, both the activation service and the worker process must be run with a specific user account (must be same for both) and the queue must have ACLs for the specific user account.</span></span>

     <span data-ttu-id="47733-213">ワーカー プロセスが実行される ID を変更するには</span><span class="sxs-lookup"><span data-stu-id="47733-213">To change the identity that the worker process runs under:</span></span>

    1. <span data-ttu-id="47733-214">Inetmgr.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="47733-214">Run Inetmgr.exe.</span></span>

    2. <span data-ttu-id="47733-215">**[アプリケーションプール]** で、 **AppPool** (通常は**DefaultAppPool**) を右クリックし、 **[アプリケーションプールの既定値の設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47733-215">Under **Application Pools**, right-click the **AppPool** (typically **DefaultAppPool**) and choose **Set Application Pool Defaults…**.</span></span>

    3. <span data-ttu-id="47733-216">特定のユーザー アカウントを使用するように、[ID] プロパティを変更します。</span><span class="sxs-lookup"><span data-stu-id="47733-216">Change the Identity properties to use the specific user account.</span></span>

     <span data-ttu-id="47733-217">アクティブ化サービスが実行される ID を変更するには</span><span class="sxs-lookup"><span data-stu-id="47733-217">To change the identity that the Activation Service runs under:</span></span>

    1. <span data-ttu-id="47733-218">Services.msc を実行します。</span><span class="sxs-lookup"><span data-stu-id="47733-218">Run Services.msc.</span></span>

    2. <span data-ttu-id="47733-219">**Net.tcp リスナーアダプター**を右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="47733-219">Right-click the **Net.MsmqListener Adapter**, and choose **Properties**.</span></span>

4. <span data-ttu-id="47733-220">**[ログオン]** タブでアカウントを変更します。</span><span class="sxs-lookup"><span data-stu-id="47733-220">Change the account in the **LogOn** tab.</span></span>

5. <span data-ttu-id="47733-221">ワークグループでは、無制限のトークンを使用してサービスを実行する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="47733-221">In workgroup, the service must also run using an unrestricted token.</span></span> <span data-ttu-id="47733-222">この操作を行うには、コマンド ウィンドウから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="47733-222">To do this, run the following in a command window:</span></span>

    ```console
    sc sidtype netmsmqactivator unrestricted
    ```

## <a name="see-also"></a><span data-ttu-id="47733-223">関連項目</span><span class="sxs-lookup"><span data-stu-id="47733-223">See also</span></span>

- <span data-ttu-id="47733-224">[AppFabric のホスティングと永続化のサンプル](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="47733-224">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
