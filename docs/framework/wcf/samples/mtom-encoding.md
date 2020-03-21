---
title: MTOM エンコーディング
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144384"
---
# <a name="mtom-encoding"></a><span data-ttu-id="07024-102">MTOM エンコーディング</span><span class="sxs-lookup"><span data-stu-id="07024-102">MTOM Encoding</span></span>
<span data-ttu-id="07024-103">このサンプルでは、WSHttpBinding で Message Transmission Optimization Mechanism (MTOM) メッセージ エンコーディングを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="07024-103">This sample demonstrates the use of the Message Transmission Optimization Mechanism (MTOM) message encoding with a WSHttpBinding.</span></span> <span data-ttu-id="07024-104">MTOM は、大きなサイズのバイナリ添付データを、SOAP メッセージを使用して未処理のバイトとして転送するための機構です。これにより、メッセージのサイズを縮小できます。</span><span class="sxs-lookup"><span data-stu-id="07024-104">MTOM is a mechanism for transmitting large binary attachments with SOAP messages as raw bytes, allowing for smaller messages.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="07024-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="07024-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="07024-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="07024-106">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="07024-107">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="07024-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07024-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="07024-108">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 <span data-ttu-id="07024-109">既定では、WSHttpBinding はメッセージを標準のテキスト XML として送受信します。</span><span class="sxs-lookup"><span data-stu-id="07024-109">By default, the WSHttpBinding sends and received messages as normal text XML.</span></span> <span data-ttu-id="07024-110">MTOM メッセージの送受信を有効にするには、バインディングの構成で `messageEncoding` 属性を設定するか (次のコード サンプルを参照)、または `MessageEncoding` プロパティを使用して、バインディング上で直接有効にします。</span><span class="sxs-lookup"><span data-stu-id="07024-110">To enable sending and receiving MTOM messages, set the `messageEncoding` attribute on the binding's configuration (as in the following example code), or directly on the binding using the `MessageEncoding` property.</span></span> <span data-ttu-id="07024-111">これにより、サービスまたはクライアントで MTOM メッセージを送受信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="07024-111">The service or client can now send and receive MTOM messages.</span></span>  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 <span data-ttu-id="07024-112">MTOM エンコーダでは、バイト配列とストリームを最適化できます。</span><span class="sxs-lookup"><span data-stu-id="07024-112">The MTOM encoder can optimize arrays of bytes and streams.</span></span> <span data-ttu-id="07024-113">このサンプルでは、操作に `Stream` パラメータを使用して、最適化できるようにします。</span><span class="sxs-lookup"><span data-stu-id="07024-113">In this sample, the operation uses a `Stream` parameter and can therefore be optimized.</span></span>  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 <span data-ttu-id="07024-114">このサンプル用に選択されたコントラクトは、バイナリ データをサービスに転送し、アップロードされたバイト数を戻り値として受け取ります。</span><span class="sxs-lookup"><span data-stu-id="07024-114">The contract chosen for this sample transmits binary data to the service and receives the number of bytes uploaded as the return value.</span></span> <span data-ttu-id="07024-115">サービスをインストールしてクライアントを実行すると、数字の 1000 が出力されます。これは、合計 1,000 バイトのデータが受信されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="07024-115">When the service is installed and the client is run, it prints out the number 1000, which indicates that all 1000 bytes were received.</span></span> <span data-ttu-id="07024-116">出力の残りの部分には、さまざまなペイロードの最適化されたメッセージのサイズと最適化されなかったメッセージのサイズが表示されます。</span><span class="sxs-lookup"><span data-stu-id="07024-116">The remainder of the output lists optimized and non-optimized message sizes for various payloads.</span></span>  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="07024-117">MTOM を使用する目的は、大きいサイズのバイナリ ペイロードの転送を最適化することです。</span><span class="sxs-lookup"><span data-stu-id="07024-117">The purpose for using MTOM is to optimize the transmission of large binary payloads.</span></span> <span data-ttu-id="07024-118">MTOM を使用して SOAP メッセージを送信すると、小さなサイズのバイナリ ペイロードでオーバーヘッドが顕著に表れますが、数千バイトを越すようになるとオーバーヘッドは大きく減少します。</span><span class="sxs-lookup"><span data-stu-id="07024-118">Sending a SOAP message using MTOM has a noticeable overhead for small binary payloads, but becomes a great savings when they grow over a few thousand bytes.</span></span> <span data-ttu-id="07024-119">この理由は、標準のテキスト XML が Base64 を使用してバイナリ データをエンコードするためです。このエンコードには 3 バイトごとに 4 文字が必要で、データのサイズは 3 分の 1 増加します。</span><span class="sxs-lookup"><span data-stu-id="07024-119">The reason for this is that normal text XML encodes binary data using Base64, which requires four characters for every three bytes, and increases the size of the data by one third.</span></span> <span data-ttu-id="07024-120">MTOM はバイナリ データを未処理のバイトとして転送できます。これによりエンコードとデコードの時間が節約でき、その結果メッセージのサイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="07024-120">MTOM is able to transmit binary data as raw bytes, saving the encoding/decoding time and resulting is smaller messages.</span></span> <span data-ttu-id="07024-121">数千バイトというしきい値は、現在のビジネス ドキュメントやデジタル写真のサイズを考えると小さい値です。</span><span class="sxs-lookup"><span data-stu-id="07024-121">The threshold of a few thousand bytes is small when compared to today's business documents and digital photographs.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07024-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="07024-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="07024-123">次のコマンドASP.NET使用して、4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="07024-123">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="07024-124">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="07024-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="07024-125">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="07024-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="07024-126">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="07024-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
