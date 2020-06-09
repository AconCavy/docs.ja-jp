---
title: ストリーム
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: a482c27dfd0970b319a605a480b5f54689e42d48
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589839"
---
# <a name="stream"></a><span data-ttu-id="d0891-102">ストリーム</span><span class="sxs-lookup"><span data-stu-id="d0891-102">Stream</span></span>
<span data-ttu-id="d0891-103">このストリーム サンプルでは、ストリーミング転送モードの通信を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d0891-103">The Stream sample demonstrates the use of streaming transfer mode communication.</span></span> <span data-ttu-id="d0891-104">サービスは、ストリームを送受信する複数の操作を公開します。</span><span class="sxs-lookup"><span data-stu-id="d0891-104">The service exposes several operations that send and receive streams.</span></span> <span data-ttu-id="d0891-105">このサンプルは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="d0891-105">This sample is self-hosted.</span></span> <span data-ttu-id="d0891-106">クライアントとサービスはどちらもコンソール プログラムです。</span><span class="sxs-lookup"><span data-stu-id="d0891-106">Both the client and service are console programs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0891-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0891-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d0891-108">Windows Communication Foundation (WCF) は、バッファーまたはストリーミングの2つの転送モードで通信できます。</span><span class="sxs-lookup"><span data-stu-id="d0891-108">Windows Communication Foundation (WCF) can communicate in two transfer modes—buffered or streaming.</span></span> <span data-ttu-id="d0891-109">既定のバッファー転送モードでは、受信側がメッセージを読むためにはメッセージを完全に送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0891-109">In the default buffered transfer mode, a message must be completely delivered before a receiver can read it.</span></span> <span data-ttu-id="d0891-110">ストリーミング転送モードでは、メッセージを完全に送信しなくても、受信側がメッセージの処理を開始できます。</span><span class="sxs-lookup"><span data-stu-id="d0891-110">In the streaming transfer mode, the receiver can begin to process the message before it is completely delivered.</span></span> <span data-ttu-id="d0891-111">ストリーミング モードは、渡される情報が長い場合、または連続的に処理する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d0891-111">The streaming mode is useful when the information that is passed is lengthy and can be processed serially.</span></span> <span data-ttu-id="d0891-112">ストリーミング モードは、メッセージが大きすぎてすべてをバッファーできない場合にも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="d0891-112">Streaming mode is also useful when the message is too large to be entirely buffered.</span></span>  
  
## <a name="streaming-and-service-contracts"></a><span data-ttu-id="d0891-113">ストリーミングとサービス コントラクト</span><span class="sxs-lookup"><span data-stu-id="d0891-113">Streaming and Service Contracts</span></span>  
 <span data-ttu-id="d0891-114">サービス コントラクトを設計する際は、ストリーミングを考慮します。</span><span class="sxs-lookup"><span data-stu-id="d0891-114">Streaming is something to be considered when designing a service contract.</span></span> <span data-ttu-id="d0891-115">操作により大量のデータが受信されたり返されたりする場合、このデータをストリーミングして、入力または出力メッセージのバッファによりメモリの使用率が高くなるのを回避することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="d0891-115">If an operation receives or returns large amounts of data, you should consider streaming this data to avoid high memory utilization due to buffering of input or output messages.</span></span> <span data-ttu-id="d0891-116">データをストリーミングするには、メッセージ内のパラメータが、データを保持するパラメータだけになるようにします。</span><span class="sxs-lookup"><span data-stu-id="d0891-116">To stream data, the parameter that holds that data must be the only parameter in the message.</span></span> <span data-ttu-id="d0891-117">たとえば、入力メッセージをストリーミングする場合、厳密に 1 つの入力パラメーターが操作に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0891-117">For example, if the input message is the one to be streamed, the operation must have exactly one input parameter.</span></span> <span data-ttu-id="d0891-118">同様に、出力メッセージをストリーミングする場合、厳密に 1 つの出力パラメーターまたは戻り値が操作に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0891-118">Similarly, if the output message is to be streamed, the operation must have either exactly one output parameter or a return value.</span></span> <span data-ttu-id="d0891-119">いずれの場合も、パラメータまたは戻り値の型は `Stream`、`Message`、または `IXmlSerializable` のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0891-119">In either case, the parameter or return value type must be either `Stream`, `Message`, or `IXmlSerializable`.</span></span> <span data-ttu-id="d0891-120">このストリーミングのサンプルに使用されているサービス コントラクトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d0891-120">The following is the service contract used in this streaming sample.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 <span data-ttu-id="d0891-121">`GetStream` 操作は、一部の入力データを文字列として受信 (バッファ) し、`Stream` (ストリーミング) を返します。</span><span class="sxs-lookup"><span data-stu-id="d0891-121">The `GetStream` operation receives some input data as a string, which is buffered, and returns a `Stream`, which is streamed.</span></span> <span data-ttu-id="d0891-122">逆に言えば、`UploadStream` は `Stream` (ストリーミング) を取り込んで、`bool` (バッファー) を返します。</span><span class="sxs-lookup"><span data-stu-id="d0891-122">Conversely, `UploadStream` takes in a `Stream` (streamed) and returns a `bool` (buffered).</span></span> <span data-ttu-id="d0891-123">`EchoStream` は `Stream` を出し入れします。これは、入力および出力メッセージがどちらもストリーミングされる操作の例です。</span><span class="sxs-lookup"><span data-stu-id="d0891-123">`EchoStream` takes and returns `Stream` and is an example of an operation whose input and output messages are both streamed.</span></span> <span data-ttu-id="d0891-124">最後に、`GetReversedStream` は入力を行わずに `Stream` (ストリーミング) を返します。</span><span class="sxs-lookup"><span data-stu-id="d0891-124">Finally, `GetReversedStream` takes no inputs and returns a `Stream` (streamed).</span></span>  
  
## <a name="enabling-streamed-transfers"></a><span data-ttu-id="d0891-125">ストリーミング転送の有効化</span><span class="sxs-lookup"><span data-stu-id="d0891-125">Enabling Streamed Transfers</span></span>  
 <span data-ttu-id="d0891-126">前述のように操作コントラクトを定義することにより、プログラミング モデル レベルでのストリーミングが実現します。</span><span class="sxs-lookup"><span data-stu-id="d0891-126">Defining operation contracts as previously described provides streaming at the programming model level.</span></span> <span data-ttu-id="d0891-127">ここで作業を終えても、トランスポートはメッセージ全体の内容をバッファします。</span><span class="sxs-lookup"><span data-stu-id="d0891-127">If you stop there, the transport still buffers the entire message content.</span></span> <span data-ttu-id="d0891-128">トランスポートのストリーミングを有効にするには、トランスポートのバインディング要素で転送モードを選択します。</span><span class="sxs-lookup"><span data-stu-id="d0891-128">To enable transport streaming, select a transfer mode on the binding element of the transport.</span></span> <span data-ttu-id="d0891-129">バインディング要素には、`TransferMode` プロパティがあり、`Buffered`、`Streamed`、`StreamedRequest`、または `StreamedResponse` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="d0891-129">The binding element has a `TransferMode` property that can be set to `Buffered`, `Streamed`, `StreamedRequest`, or `StreamedResponse`.</span></span> <span data-ttu-id="d0891-130">転送モードを `Streamed` に設定すると、両方向のストリーミング通信が可能になります。</span><span class="sxs-lookup"><span data-stu-id="d0891-130">Setting the transfer mode to `Streamed` enables streaming communication in both directions.</span></span> <span data-ttu-id="d0891-131">転送モードを `StreamedRequest` または `StreamedResponse` に設定すると、それぞれ要求または応答のみでのストリーミング通信が可能になります。</span><span class="sxs-lookup"><span data-stu-id="d0891-131">Setting the transfer mode to `StreamedRequest` or `StreamedResponse` enables streaming communication in only the request or response, respectively.</span></span>  
  
 <span data-ttu-id="d0891-132">`basicHttpBinding` は、`TransferMode` および `NetTcpBinding` と同様に、バインディングで `NetNamedPipeBinding` プロパティを開示します。</span><span class="sxs-lookup"><span data-stu-id="d0891-132">The `basicHttpBinding` exposes the `TransferMode` property on the binding as does `NetTcpBinding` and `NetNamedPipeBinding`.</span></span> <span data-ttu-id="d0891-133">他のトランスポートの場合、転送モードを設定するにはカスタム バインドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0891-133">For other transports, you must create a custom binding to set the transfer mode.</span></span>  
  
 <span data-ttu-id="d0891-134">次のサンプルの構成コードでは、`TransferMode` とカスタム HTTP バインディングで、`basicHttpBinding` プロパティをストリーミングに設定しています。</span><span class="sxs-lookup"><span data-stu-id="d0891-134">The following configuration code from the sample shows setting the `TransferMode` property to streaming on the `basicHttpBinding` and a custom HTTP binding:</span></span>  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 <span data-ttu-id="d0891-135">上の構成コードでは、`transferMode` を `Streamed` に設定することに加え、`maxReceivedMessageSize` を 64 MB に設定しています。</span><span class="sxs-lookup"><span data-stu-id="d0891-135">In addition to setting the `transferMode` to `Streamed`, the previous configuration code sets the `maxReceivedMessageSize` to 64MB.</span></span> <span data-ttu-id="d0891-136">防御機構として、`maxReceivedMessageSize` では受信可能なメッセージの最大サイズが決められます。</span><span class="sxs-lookup"><span data-stu-id="d0891-136">As a defense mechanism, `maxReceivedMessageSize` places a cap on the maximum allowable size of messages on receive.</span></span> <span data-ttu-id="d0891-137">既定の `maxReceivedMessageSize` は 64 KB です。これは、多くの場合ストリーミングを行うには小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="d0891-137">The default `maxReceivedMessageSize` is 64 KB, which is usually too low for streaming scenarios.</span></span>  
  
## <a name="processing-data-as-it-is-streamed"></a><span data-ttu-id="d0891-138">ストリーミングされる際のデータの処理</span><span class="sxs-lookup"><span data-stu-id="d0891-138">Processing Data As It Is Streamed</span></span>  
 <span data-ttu-id="d0891-139">`GetStream`、`UploadStream`、および `EchoStream` の各操作はすべて、ファイルからデータを直接送信したり、データをファイルに直接受信したりします。</span><span class="sxs-lookup"><span data-stu-id="d0891-139">The operations `GetStream`, `UploadStream` and `EchoStream` all deal with sending data directly from a file or saving received data directly to a file.</span></span> <span data-ttu-id="d0891-140">ただし場合によっては、大量のデータを送信または受信し、データの送受信時に一部の処理をデータのチャンク上で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0891-140">However in some cases, there is a requirement to send or receive large amounts of data and perform some processing on chunks of the data as it is being sent or received.</span></span> <span data-ttu-id="d0891-141">このようなシナリオに対応する 1 つの方法は、データの読み取りまたは書き込み時にデータを処理するカスタム ストリーム (<xref:System.IO.Stream> から派生するクラス) を記述することです。</span><span class="sxs-lookup"><span data-stu-id="d0891-141">One way to address such scenarios is to write a custom stream (a class that derives from <xref:System.IO.Stream>) that processes data as it is read or written.</span></span> <span data-ttu-id="d0891-142">`GetReversedStream` 操作と `ReverseStream` クラスがこの例です。</span><span class="sxs-lookup"><span data-stu-id="d0891-142">The `GetReversedStream` operation and `ReverseStream` class are an example of this.</span></span>  
  
 <span data-ttu-id="d0891-143">`GetReversedStream` では、`ReverseStream` の新しいインスタンスを作成して返します。</span><span class="sxs-lookup"><span data-stu-id="d0891-143">`GetReversedStream` creates and returns a new instance of `ReverseStream`.</span></span> <span data-ttu-id="d0891-144">実際の処理は、システムが `ReverseStream` オブジェクトの読み取りを行うときに発生します。</span><span class="sxs-lookup"><span data-stu-id="d0891-144">The actual processing happens as the system reads from that `ReverseStream` object.</span></span> <span data-ttu-id="d0891-145">`ReverseStream.Read` の実装により、基になるファイルからバイトのチャンクが読み取られ、バイトが反転され、その反転されたバイトが返されます。</span><span class="sxs-lookup"><span data-stu-id="d0891-145">The `ReverseStream.Read` implementation reads a chunk of bytes from the underlying file, reverses them, then returns the reversed bytes.</span></span> <span data-ttu-id="d0891-146">この処理ではファイル全体の内容は反転されません。一度に 1 つのバイトのチャンクが反転されます。</span><span class="sxs-lookup"><span data-stu-id="d0891-146">This does not reverse the entire file content; it reverses one chunk of bytes at a time.</span></span> <span data-ttu-id="d0891-147">これは、ストリームの内容を読み取ったりストリームに内容を書き込んだりするときに、ストリーミング処理を実行する方法を示す例です。</span><span class="sxs-lookup"><span data-stu-id="d0891-147">This is an example to show how you can perform stream processing as the content is being read or written from and to the stream.</span></span>  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="d0891-148">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="d0891-148">Running the Sample</span></span>  
 <span data-ttu-id="d0891-149">サンプルを実行するには、最初に、このドキュメントの最後にある指示に従ってサービスとクライアントの両方をビルドします。</span><span class="sxs-lookup"><span data-stu-id="d0891-149">To run the sample, first build both the service and the client by following the directions at the end of this document.</span></span> <span data-ttu-id="d0891-150">次に、サービスとクライアントを 2 つの異なるコンソール ウィンドウで開始します。</span><span class="sxs-lookup"><span data-stu-id="d0891-150">Then start the service and the client in two different console windows.</span></span> <span data-ttu-id="d0891-151">クライアントが開始したら待機状態になるので、サービスの準備ができたら Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d0891-151">When the client starts, it waits for you to press ENTER when the service is ready.</span></span> <span data-ttu-id="d0891-152">その後、クライアントはまず HTTP を経由し、次に TCP を経由して、メソッド `GetStream()`、`UploadStream()`、および `GetReversedStream()` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d0891-152">The client then calls the methods `GetStream()`, `UploadStream()` and `GetReversedStream()` first over HTTP and then over TCP.</span></span> <span data-ttu-id="d0891-153">サービスからの出力例、続いてクライアントからの出力例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d0891-153">Here is an example output from the service followed by example output from the client:</span></span>  
  
 <span data-ttu-id="d0891-154">サービスからの出力 :</span><span class="sxs-lookup"><span data-stu-id="d0891-154">Service Output:</span></span>  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 <span data-ttu-id="d0891-155">クライアントからの出力 :</span><span class="sxs-lookup"><span data-stu-id="d0891-155">Client Output:</span></span>  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d0891-156">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d0891-156">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d0891-157">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0891-157">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d0891-158">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d0891-158">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d0891-159">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d0891-159">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0891-160">Svcutil.exe を使用してこのサンプルの構成を再生成した場合は、クライアント コードに一致するように、クライアント構成内のエンドポイント名を変更してください。</span><span class="sxs-lookup"><span data-stu-id="d0891-160">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d0891-161">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d0891-161">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0891-162">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d0891-162">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d0891-163">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="d0891-163">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0891-164">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d0891-164">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
