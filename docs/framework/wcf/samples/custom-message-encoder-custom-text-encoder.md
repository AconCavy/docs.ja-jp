---
title: 'カスタム メッセージ エンコーダー : カスタム テキスト エンコーダー'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88aeeb4f1d09795b768441d2a572d959f27e0226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145112"
---
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="5219c-102">カスタム メッセージ エンコーダー : カスタム テキスト エンコーダー</span><span class="sxs-lookup"><span data-stu-id="5219c-102">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="5219c-103">このサンプルでは、Windows 通信基盤 (WCF) を使用してカスタム テキスト メッセージ エンコーダーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5219c-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="5219c-104">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="5219c-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5219c-105">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="5219c-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5219c-106">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="5219c-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5219c-107">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="5219c-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="5219c-108">WCF<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>のは、UTF-8、UTF-16、およびビッグ エンディアン Unicode エンコーディングのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5219c-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="5219c-109">このサンプルのカスタム テキスト メッセージ エンコーダーでは、相互運用性に必要なプラットフォームでサポートされるすべての文字エンコーディングがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="5219c-109">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="5219c-110">このサンプルは、クライアント コンソール プログラム (.exe) 、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (.dll) 、およびテキスト メッセージ エンコーダー ライブラリ (.dll) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="5219c-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="5219c-111">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="5219c-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5219c-112">このコントラクトは `ICalculator` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。</span><span class="sxs-lookup"><span data-stu-id="5219c-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="5219c-113">クライアントは指定された算術演算を同期要求し、サービスは結果と共に応答します。</span><span class="sxs-lookup"><span data-stu-id="5219c-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="5219c-114">クライアントとサービスはどちらも、既定の `CustomTextMessageEncoder` の代わりに <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> を使用します。</span><span class="sxs-lookup"><span data-stu-id="5219c-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="5219c-115">カスタム エンコーダーの実装は、メッセージ エンコーダー ファクトリ、メッセージ エンコーダー、メッセージ エンコーディング バインド要素、および構成ハンドラーで構成され、次が示されます。</span><span class="sxs-lookup"><span data-stu-id="5219c-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="5219c-116">カスタム エンコーダーおよびエンコーダー ファクトリの作成。</span><span class="sxs-lookup"><span data-stu-id="5219c-116">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="5219c-117">カスタム エンコーダーのバインド要素の作成。</span><span class="sxs-lookup"><span data-stu-id="5219c-117">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="5219c-118">カスタム バインド要素を統合するためのカスタム バインド構成の使用。</span><span class="sxs-lookup"><span data-stu-id="5219c-118">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="5219c-119">カスタム バインド要素のファイル構成を可能にするカスタム構成ハンドラーの開発。</span><span class="sxs-lookup"><span data-stu-id="5219c-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5219c-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="5219c-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5219c-121">次のコマンドASP.NET使用して、4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="5219c-121">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="5219c-122">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="5219c-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="5219c-123">ソリューションをビルドするには、「 [Windows コミュニケーション ファウンデーション のサンプルの構築](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5219c-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="5219c-124">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="5219c-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="5219c-125">メッセージ エンコーダー ファクトリとメッセージ エンコーダー</span><span class="sxs-lookup"><span data-stu-id="5219c-125">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="5219c-126"><xref:System.ServiceModel.ServiceHost> またはクライアント チャネルが開かれると、デザイン時コンポーネント `CustomTextMessageBindingElement` は `CustomTextMessageEncoderFactory` を作成します。</span><span class="sxs-lookup"><span data-stu-id="5219c-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="5219c-127">このファクトリは、`CustomTextMessageEncoder` を作成します。</span><span class="sxs-lookup"><span data-stu-id="5219c-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="5219c-128">メッセージ エンコーダーは、ストリーミング モードとバッファー モードの両方で動作し、</span><span class="sxs-lookup"><span data-stu-id="5219c-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="5219c-129"><xref:System.Xml.XmlReader> と <xref:System.Xml.XmlWriter> を使用してメッセージの読み取りと書き込みを行います。</span><span class="sxs-lookup"><span data-stu-id="5219c-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="5219c-130">最適化された XML リーダーと UTF-8、UTF-16、およびビッグ エンディアン Unicode のみをサポートする WCF のライターとは対照的に、これらのリーダーとライターは、すべてのプラットフォームサポートエンコーディングをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5219c-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="5219c-131">カスタム テキスト メッセージ エンコーダーのコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5219c-131">The following code example shows the CustomTextMessageEncoder.</span></span>

```csharp
public class CustomTextMessageEncoder : MessageEncoder
{
    private CustomTextMessageEncoderFactory factory;
    private XmlWriterSettings writerSettings;
    private string contentType;

    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)
    {
        this.factory = factory;

        this.writerSettings = new XmlWriterSettings();
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
    }

    public override string ContentType
    {
        get
        {
            return this.contentType;
        }
    }

    public override string MediaType
    {
        get
        {
            return factory.MediaType;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.factory.MessageVersion;
        }
    }

    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)
    {
        byte[] msgContents = new byte[buffer.Count];
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);
        bufferManager.ReturnBuffer(buffer.Array);

        MemoryStream stream = new MemoryStream(msgContents);
        return ReadMessage(stream, int.MaxValue);
    }

    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)
    {
        XmlReader reader = XmlReader.Create(stream);
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);
    }

    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)
    {
        MemoryStream stream = new MemoryStream();
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();

        byte[] messageBytes = stream.GetBuffer();
        int messageLength = (int)stream.Position;
        stream.Close();

        int totalLength = messageLength + messageOffset;
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);

        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);
        return byteArray;
    }

    public override void WriteMessage(Message message, Stream stream)
    {
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);
        message.WriteMessage(writer);
        writer.Close();
    }
}
```

<span data-ttu-id="5219c-132">メッセージ エンコーダー ファクトリを作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5219c-132">The following code example shows how to build the message encoder factory.</span></span>

```csharp
public class CustomTextMessageEncoderFactory : MessageEncoderFactory
{
    private MessageEncoder encoder;
    private MessageVersion version;
    private string mediaType;
    private string charSet;

    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,
        MessageVersion version)
    {
        this.version = version;
        this.mediaType = mediaType;
        this.charSet = charSet;
        this.encoder = new CustomTextMessageEncoder(this);
    }

    public override MessageEncoder Encoder
    {
        get
        {
            return this.encoder;
        }
    }

    public override MessageVersion MessageVersion
    {
        get
        {
            return this.version;
        }
    }

    internal string MediaType
    {
        get
        {
            return this.mediaType;
        }
    }

    internal string CharSet
    {
        get
        {
            return this.charSet;
        }
    }
}
```

## <a name="message-encoding-binding-element"></a><span data-ttu-id="5219c-133">メッセージ エンコーディング バインディング要素</span><span class="sxs-lookup"><span data-stu-id="5219c-133">Message Encoding Binding Element</span></span>

<span data-ttu-id="5219c-134">バインド要素は、WCF ランタイム スタックの構成を許可します。</span><span class="sxs-lookup"><span data-stu-id="5219c-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="5219c-135">WCF アプリケーションでカスタム メッセージ エンコーダーを使用するには、バインディング要素が必要です、メッセージ エンコーダー ファクトリを作成し、ランタイム スタック内の適切なレベルで適切な設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="5219c-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="5219c-136">`CustomTextMessageBindingElement` は <xref:System.ServiceModel.Channels.BindingElement> 基本クラスから派生し、<xref:System.ServiceModel.Channels.MessageEncodingBindingElement> クラスを継承します。</span><span class="sxs-lookup"><span data-stu-id="5219c-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="5219c-137">これにより、他の WCF コンポーネントは、このバインド要素をメッセージ エンコーディング バインド要素として認識できます。</span><span class="sxs-lookup"><span data-stu-id="5219c-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="5219c-138"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> を実装すると、一致するメッセージ エンコーダー ファクトリのインスタンスが適切に設定されて返されます。</span><span class="sxs-lookup"><span data-stu-id="5219c-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="5219c-139">`CustomTextMessageBindingElement` は、プロパティを介して `MessageVersion`、`ContentType`、および `Encoding` の設定を公開します。</span><span class="sxs-lookup"><span data-stu-id="5219c-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="5219c-140">エンコーダーは、Soap11Addressing と Soap12Addressing1 の両方のバージョンをサポートします。</span><span class="sxs-lookup"><span data-stu-id="5219c-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="5219c-141">既定値は Soap11Addressing1 です。</span><span class="sxs-lookup"><span data-stu-id="5219c-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="5219c-142">また、`ContentType` の既定値は "text/xml" です。</span><span class="sxs-lookup"><span data-stu-id="5219c-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="5219c-143">`Encoding` プロパティでは、必要な文字エンコーディングの値を設定できます。</span><span class="sxs-lookup"><span data-stu-id="5219c-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="5219c-144">サンプル クライアントとサービスは、WCF でサポートされていない ISO-8859-1 (Latin1) 文字<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>エンコーディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="5219c-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="5219c-145">カスタム テキスト メッセージ エンコーダーを使用してプログラムでバインディングを作成する方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="5219c-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="5219c-146">メッセージ エンコーディング バインド要素へのメタデータのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="5219c-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="5219c-147"><xref:System.ServiceModel.Channels.MessageEncodingBindingElement> から派生するすべての型は、サービスに対して生成される WSDL ドキュメント内の SOAP バインドのバージョンを更新します。</span><span class="sxs-lookup"><span data-stu-id="5219c-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="5219c-148">これを行うには、`ExportEndpoint` インターフェイス上に <xref:System.ServiceModel.Description.IWsdlExportExtension> メソッドを実装し、生成された WSDL を変更します。</span><span class="sxs-lookup"><span data-stu-id="5219c-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="5219c-149">このサンプルでは、`CustomTextMessageBindingElement` は `TextMessageEncodingBindingElement` からの WSDL エクスポート ロジックを使用します。</span><span class="sxs-lookup"><span data-stu-id="5219c-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="5219c-150">このサンプルの場合、クライアント構成は手動構成です。</span><span class="sxs-lookup"><span data-stu-id="5219c-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="5219c-151">Svcutil.exe を使用してクライアント構成を生成することはできません。`CustomTextMessageBindingElement` では、動作を記述するポリシー アサーションがエクスポートされないからです。</span><span class="sxs-lookup"><span data-stu-id="5219c-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="5219c-152">通常は、カスタム バインド要素上に <xref:System.ServiceModel.Description.IPolicyExportExtension> インターフェイスを実装して、バインド要素によって実装される動作または機能を記述するカスタム ポリシー アサーションをエクスポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5219c-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="5219c-153">カスタム バインド要素のポリシー アサーションをエクスポートする方法の例については[、「Transport: UDP」](../../../../docs/framework/wcf/samples/transport-udp.md)サンプルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="5219c-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="5219c-154">メッセージ エンコーディング バインド構成ハンドラー</span><span class="sxs-lookup"><span data-stu-id="5219c-154">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="5219c-155">前のセクションでは、カスタム テキスト メッセージ エンコーダーをプログラムによって使用する方法を示しました。</span><span class="sxs-lookup"><span data-stu-id="5219c-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="5219c-156">`CustomTextMessageEncodingBindingSection` は構成ハンドラーを実装します。この構成ハンドラーにより、カスタム テキスト メッセージ エンコーダーを構成ファイル内で使用することを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5219c-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="5219c-157">`CustomTextMessageEncodingBindingSection` クラスは <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> クラスから派生します。</span><span class="sxs-lookup"><span data-stu-id="5219c-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="5219c-158">`BindingElementType` プロパティでは、このセクション用に作成するバインディング要素の型が構成システムに通知されます。</span><span class="sxs-lookup"><span data-stu-id="5219c-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="5219c-159">`CustomTextMessageBindingElement` によって定義されたすべての設定は、`CustomTextMessageEncodingBindingSection` のプロパティとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="5219c-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="5219c-160"><xref:System.Configuration.ConfigurationPropertyAttribute> は、構成要素の属性をプロパティにマップしたり、属性がない場合は既定値を設定する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="5219c-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="5219c-161">構成から値が読み込まれて型のプロパティに適用されると、<xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> メソッドが呼び出されます。このメソッドは、プロパティをバインド要素の具体的なインスタンスに変換します。</span><span class="sxs-lookup"><span data-stu-id="5219c-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="5219c-162">この構成ハンドラーは、サービスまたはクライアントの App.config または Web.config の次の表現にマップされます。</span><span class="sxs-lookup"><span data-stu-id="5219c-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="5219c-163">このサンプルでは、ISO-8859-1 エンコーディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="5219c-163">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="5219c-164">この構成ハンドラーを使用するには、次の構成要素を使用して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5219c-164">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
