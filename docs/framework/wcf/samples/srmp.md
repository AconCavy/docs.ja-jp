---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 0ee11b67dcd9c7251df17dc7523dc20765e157c5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716689"
---
# <a name="srmp"></a><span data-ttu-id="f868e-102">SRMP</span><span class="sxs-lookup"><span data-stu-id="f868e-102">SRMP</span></span>
<span data-ttu-id="f868e-103">このサンプルでは、HTTP 経由でメッセージ キュー (MSMQ) を使用して、トランザクション キューによる通信を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f868e-103">This sample demonstrates how to perform transacted queued communication by using Message Queuing (MSMQ) over HTTP.</span></span>  
  
 <span data-ttu-id="f868e-104">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="f868e-104">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="f868e-105">厳密には、クライアントはメッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="f868e-105">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="f868e-106">サービスは、メッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="f868e-106">The service receives messages from the queue.</span></span> <span data-ttu-id="f868e-107">したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="f868e-107">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="f868e-108">MSMQ は HTTP (HTTPS を含む) を使用できるようにして、メッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="f868e-108">MSMQ enables the use of HTTP (including the use of HTTPS) to send messages to a queue.</span></span> <span data-ttu-id="f868e-109">この例では、Windows Communication Foundation (WCF) のキューに置かれた通信の使用方法と、HTTP 経由でメッセージを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f868e-109">In this example, we demonstrate using Windows Communication Foundation (WCF) queued communication and how to send messages over HTTP.</span></span> <span data-ttu-id="f868e-110">MSMQ では SRMP というプロトコルを使用します。これは、HTTP 経由の通信に使用する SOAP ベースのプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="f868e-110">MSMQ uses a protocol called SRMP, which is a SOAP-based protocol for communication over HTTP.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f868e-111">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="f868e-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f868e-112">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="f868e-112">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="f868e-113">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f868e-113">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="f868e-114">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f868e-114">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
4. <span data-ttu-id="f868e-115">「 **Windows コンポーネントの追加と削除**」でサンプルを実行する前に、MSMQ が HTTP サポートと共にインストールされていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f868e-115">Before running the sample in **Add/Remove Windows Components**, ensure that MSMQ is installed with HTTP support.</span></span> <span data-ttu-id="f868e-116">HTTP サポートをインストールすると、インターネット インフォメーション サービス (IIS) が自動的にインストールされ、MSMQ 用のプロトコル サポートが IIS に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f868e-116">Installing HTTP support automatically installs Internet Information Services (IIS) and adds the protocol support in IIS for MSMQ.</span></span>  
  
5. <span data-ttu-id="f868e-117">HTTP が通信に使用されていることを確認するには、MSMQ を強化モードで実行します。</span><span class="sxs-lookup"><span data-stu-id="f868e-117">If you want to be certain that HTTP is used for communication, you can enable MSMQ to run in hardened mode.</span></span> <span data-ttu-id="f868e-118">これにより、HTTP 以外のトランスポートを使用した場合は、コンピュータ上でホストされているすべてのキューにメッセージが到着できないようになります。</span><span class="sxs-lookup"><span data-stu-id="f868e-118">This ensures that no messages to any queue hosted on the machine can arrive using any non-HTTP transport.</span></span>  
  
6. <span data-ttu-id="f868e-119">[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] では、MSMQ を強化モードで実行するように選択した後でコンピュータを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f868e-119">After you have selected MSMQ to run in hardened mode, the machine requires a re-boot on [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].</span></span>  
  
7. <span data-ttu-id="f868e-120">サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="f868e-120">Run the service.</span></span>  
  
8. <span data-ttu-id="f868e-121">クライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="f868e-121">Run the client.</span></span> <span data-ttu-id="f868e-122">エンドポイント アドレスは、localhost ではなくコンピュータ名または IP アドレスを指定するように変更してください。</span><span class="sxs-lookup"><span data-stu-id="f868e-122">Ensure that you change the endpoint address to point to the machine name or IP address instead of localhost.</span></span> <span data-ttu-id="f868e-123">クライアントはメッセージを送信して終了します。</span><span class="sxs-lookup"><span data-stu-id="f868e-123">The client sends a message and exits.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f868e-124">要件</span><span class="sxs-lookup"><span data-stu-id="f868e-124">Requirements</span></span>  
 <span data-ttu-id="f868e-125">このサンプルを実行するには、MSMQ に加え、IIS をサービス コンピュータとクライアント コンピュータの両方にインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="f868e-125">To run this sample, IIS must be installed on both the service and the client machines in addition to MSMQ.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="f868e-126">例</span><span class="sxs-lookup"><span data-stu-id="f868e-126">Demonstrates</span></span>  
 <span data-ttu-id="f868e-127">このサンプルでは、HTTP 経由で MSMQ を使用して WCF キューメッセージを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f868e-127">The sample demonstrates sending WCF queued messages using MSMQ over HTTP.</span></span> <span data-ttu-id="f868e-128">これは、SRMP メッセージングとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="f868e-128">This is also called SRMP messaging.</span></span> <span data-ttu-id="f868e-129">キューに置かれたメッセージが送信されると、送信元コンピュータの MSMQ は、このメッセージを TCP または HTTP トランスポート経由で受信キュー マネージャに転送します。</span><span class="sxs-lookup"><span data-stu-id="f868e-129">When a queued message is sent, MSMQ on the sending machine transfers the messages to the receiving queue manager over TCP or HTTP transport.</span></span> <span data-ttu-id="f868e-130">SRMP を選択すると、HTTP をキュー転送用のトランスポートとして選択したことになります。</span><span class="sxs-lookup"><span data-stu-id="f868e-130">By choosing SRMP, the user indicates the choice of HTTP as a transport for queue transfer.</span></span> <span data-ttu-id="f868e-131">SRMP Secure を選択すると、HTTPS を使用できます。</span><span class="sxs-lookup"><span data-stu-id="f868e-131">SRMP Secure enables the use of HTTPS.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f868e-132">使用例</span><span class="sxs-lookup"><span data-stu-id="f868e-132">Example</span></span>  
 <span data-ttu-id="f868e-133">このサンプル コードはトランザクションのサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="f868e-133">The sample code is based on the transacted sample.</span></span> <span data-ttu-id="f868e-134">SRMP を使用してキューにメッセージを送信したり、キューからメッセージを受信したりする方法は、ネイティブ プロトコルを使用してメッセージを送受信する方法と同じです。</span><span class="sxs-lookup"><span data-stu-id="f868e-134">How you send a message to the queue and receive a message from the queue using SRMP is the same as sending and receiving messages using a Native protocol.</span></span>  
  
 <span data-ttu-id="f868e-135">クライアントの構成は、キュー転送プロトコルの選択を示すように変更されます。</span><span class="sxs-lookup"><span data-stu-id="f868e-135">The configuration for the client is changed to indicate the choice of the queue transfer protocol.</span></span> <span data-ttu-id="f868e-136">キュー転送プロトコルには、ネイティブ、SRMP、または SRMP Secure のいずれか 1 つを選択できます。</span><span class="sxs-lookup"><span data-stu-id="f868e-136">The queue transfer protocol can be one of Native, SRMP or SrmpSecure.</span></span> <span data-ttu-id="f868e-137">既定の転送プロトコルはネイティブです。</span><span class="sxs-lookup"><span data-stu-id="f868e-137">By default, the transfer protocol is Native.</span></span> <span data-ttu-id="f868e-138">この例では、クライアントとサービスの構成で SRMP を使用するように指定されます。</span><span class="sxs-lookup"><span data-stu-id="f868e-138">The client and service specify in the configuration to use SRMP in this example.</span></span>  
  
 <span data-ttu-id="f868e-139">セキュリティの関係で、SRMP には制限があります。</span><span class="sxs-lookup"><span data-stu-id="f868e-139">There are limitations to SRMP in relation to transport security.</span></span> <span data-ttu-id="f868e-140">既定の MSMQ トランスポート セキュリティには Active Directory が必要です。Active Directory では、送信キュー マネージャと受信キュー マネージャが同じ Windows ドメインに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f868e-140">The default MSMQ transport security requires Active Directory that requires that the sending queue manager and the receiving queue manager reside in the same Windows domain.</span></span> <span data-ttu-id="f868e-141">HTTP 境界を越えてメッセージを送信する場合、これは不可能です。</span><span class="sxs-lookup"><span data-stu-id="f868e-141">This is not possible when sending messages over HTTP boundary.</span></span> <span data-ttu-id="f868e-142">このため、既定のトランスポート セキュリティは機能しません。</span><span class="sxs-lookup"><span data-stu-id="f868e-142">As such, the default transport security does not work.</span></span> <span data-ttu-id="f868e-143">トランスポート セキュリティが必要な場合は、トランスポート セキュリティを Certificate に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f868e-143">The transport security must be set to Certificate if transport security is desired.</span></span> <span data-ttu-id="f868e-144">また、メッセージのセキュリティ保護にメッセージ セキュリティを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f868e-144">Message security can also be used to secure the message.</span></span> <span data-ttu-id="f868e-145">このサンプルでは SRMP メッセージングを説明するために、トランスポート セキュリティとメッセージ セキュリティはどちらも無効になっています。</span><span class="sxs-lookup"><span data-stu-id="f868e-145">In this sample, both transport and message security is turned off to illustrate SRMP messaging.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"   
           bindingConfiguration="srmpBinding"   
           binding="netMsmqBinding"   
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 <span data-ttu-id="f868e-146">このサンプルを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f868e-146">Running the sample yields the following output.</span></span>  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
> <span data-ttu-id="f868e-147">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f868e-147">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f868e-148">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f868e-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f868e-149">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="f868e-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f868e-150">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f868e-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
