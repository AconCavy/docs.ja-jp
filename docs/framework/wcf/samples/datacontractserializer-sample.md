---
title: DataContractSerializer サンプル
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 59bbeb4091c101efeac4e0562f0e3cbd5a8b5f79
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716363"
---
# <a name="datacontractserializer-sample"></a><span data-ttu-id="7ec62-102">DataContractSerializer サンプル</span><span class="sxs-lookup"><span data-stu-id="7ec62-102">DataContractSerializer Sample</span></span>
<span data-ttu-id="7ec62-103">DataContractSerializer サンプルでは、<xref:System.Runtime.Serialization.DataContractSerializer> を示して、データ コントラクト クラスに対応した一般的なシリアル化および逆シリアル化の各サービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-103">The DataContractSerializer sample demonstrates the <xref:System.Runtime.Serialization.DataContractSerializer>, which performs general serialization and deserialization services for the data contract classes.</span></span> <span data-ttu-id="7ec62-104">このサンプルでは、`Record` オブジェクトを作成し、それをメモリストリームにシリアル化し、メモリストリームを別の `Record` オブジェクトに逆シリアル化して、<xref:System.Runtime.Serialization.DataContractSerializer>の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-104">The sample creates a `Record` object, serializes it to a memory stream and deserializes the memory stream back to another `Record` object to demonstrate the use of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="7ec62-105">サンプルではその後、バイナリ ライタを使用して `Record` オブジェクトをシリアル化し、バイナリ ライタがシリアル化にどのように影響するかを示します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-105">The sample then serializes the `Record` object using a binary writer to demonstrate how the writer affects serialization.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ec62-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ec62-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7ec62-107">`Record` のデータ コントラクトを次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-107">The data contract for `Record` is shown in the following sample code.</span></span>  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return $"Record: {n1} {operation} {n2} = {result}";
    }  
}  
```  
  
 <span data-ttu-id="7ec62-108">このサンプル コードは `Record` という `record1` オブジェクトを作成し、これを表示します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-108">The sample code creates a `Record` object named `record1` then displays the object.</span></span>  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 <span data-ttu-id="7ec62-109">次に、<xref:System.Runtime.Serialization.DataContractSerializer> を使用して `record1` をメモリ ストリームにシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-109">The sample then uses the <xref:System.Runtime.Serialization.DataContractSerializer> to serialize `record1` into a memory stream.</span></span>  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 <span data-ttu-id="7ec62-110">さらに、<xref:System.Runtime.Serialization.DataContractSerializer> を使用してメモリ ストリームを新しい `Record` オブジェクトに逆シリアル化し、これを表示します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-110">Next, the sample uses the <xref:System.Runtime.Serialization.DataContractSerializer> to deserialize the memory stream back into a new `Record` object and displays it.</span></span>  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 <span data-ttu-id="7ec62-111">既定では、`DataContractSerializer` は XML のテキスト表現を使用して、オブジェクトをストリームにエンコードします。</span><span class="sxs-lookup"><span data-stu-id="7ec62-111">By default, the `DataContractSerializer` encodes objects into a stream using a textual representation of XML.</span></span> <span data-ttu-id="7ec62-112">ただし、別のライタを渡すことによって XML のエンコーディングを制御できます。</span><span class="sxs-lookup"><span data-stu-id="7ec62-112">However, you can influence the encoding of the XML by passing in a different writer.</span></span> <span data-ttu-id="7ec62-113">このサンプルでは、<xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A> を呼び出してバイナリ ライタを作成します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-113">The sample creates a binary writer by calling <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>.</span></span> <span data-ttu-id="7ec62-114">その後、<xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A> を呼び出す際に、このライタと Record オブジェクトをシリアライザに渡します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-114">It then passes the writer and the record object to the serializer when it calls <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>.</span></span> <span data-ttu-id="7ec62-115">最後に、ライタをフラッシュしてストリームの長さを報告します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-115">Finally, the sample flushes the writer and reports on the length of the streams.</span></span>  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 <span data-ttu-id="7ec62-116">このサンプルを実行すると、元の Record オブジェクトと逆シリアル化された Record オブジェクトが表示され、続いてテキスト エンコーディングの長さとバイナリ エンコーディングの長さとが比較されます。</span><span class="sxs-lookup"><span data-stu-id="7ec62-116">When you run the sample, the original record and the deserialized record are displayed, followed by the comparison between the length of the text encoding and the binary encoding.</span></span> <span data-ttu-id="7ec62-117">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-117">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7ec62-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7ec62-118">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="7ec62-119">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-119">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="7ec62-120">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7ec62-120">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="7ec62-121">このサンプルを実行するには、コマンド プロンプトで「client\bin\client.exe」と入力してクライアントを開始します。</span><span class="sxs-lookup"><span data-stu-id="7ec62-121">To run the sample, start the client from the command prompt by typing client\bin\client.exe.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7ec62-122">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7ec62-122">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7ec62-123">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7ec62-123">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="7ec62-124">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7ec62-124">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7ec62-125">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7ec62-125">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
