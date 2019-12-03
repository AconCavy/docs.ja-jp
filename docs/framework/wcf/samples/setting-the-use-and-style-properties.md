---
title: 使用とスタイルのプロパティの設定-WCF サンプル
ms.date: 03/30/2017
ms.assetid: c09a0600-116f-41cf-900a-1b7e4ea4e300
ms.openlocfilehash: f92b25144759692c54aa7a1730a9bb85cab4f15f
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714439"
---
# <a name="setting-the-use-and-style-properties"></a><span data-ttu-id="6a5c4-102">Use および Style プロパティの設定</span><span class="sxs-lookup"><span data-stu-id="6a5c4-102">Setting the Use and Style Properties</span></span>

<span data-ttu-id="6a5c4-103">このサンプルでは、<xref:System.ServiceModel.XmlSerializerFormatAttribute> と <xref:System.ServiceModel.DataContractFormatAttribute> で Use および Style プロパティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-103">This sample demonstrates how to use the Use and Style properties on the <xref:System.ServiceModel.XmlSerializerFormatAttribute> and the <xref:System.ServiceModel.DataContractFormatAttribute>.</span></span> <span data-ttu-id="6a5c4-104">これらのプロパティは、メッセージの書式設定の方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-104">These properties affect how messages are formatted.</span></span> <span data-ttu-id="6a5c4-105">既定では、メッセージの本文は、<xref:System.ServiceModel.OperationFormatStyle.Document> に設定されたスタイルを使用して書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-105">By default, the message body is formatted with the style set to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span> <span data-ttu-id="6a5c4-106">こうした設定は、サービス コントラクト レベルと操作コントラクト レベルのどちらのレベルでも指定できます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-106">These settings can be specified at either the service contract level or the operation contract level.</span></span>

> [!NOTE]
> <span data-ttu-id="6a5c4-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="6a5c4-108"><xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> スタイル プロパティは、サービスの WSDL メタデータの書式設定を決定します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-108">The <xref:System.ServiceModel.DataContractFormatAttribute.Style%2A> style property determines how the WSDL metadata for the service is formatted.</span></span> <span data-ttu-id="6a5c4-109">使用可能な値は <xref:System.ServiceModel.OperationFormatStyle.Document> と <xref:System.ServiceModel.OperationFormatStyle.Rpc> です。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-109">Possible values are <xref:System.ServiceModel.OperationFormatStyle.Document>, and <xref:System.ServiceModel.OperationFormatStyle.Rpc>.</span></span> <span data-ttu-id="6a5c4-110">RPC は、操作で交換されるメッセージの WSDL 表現がリモート プロシージャ コールである場合と同様のパラメータを含むことを意味します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-110">RPC means that the WSDL representation of messages exchanged for an operation contains parameters as if it were a remote procedure call.</span></span> <span data-ttu-id="6a5c4-111">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-111">The following is an example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="n1" type="xsd:double"/>
  <wsdl:part name="n2" type="xsd:double"/>
</wsdl:message>
```

<span data-ttu-id="6a5c4-112">スタイルに対する <xref:System.ServiceModel.OperationFormatStyle.Document> への設定は、WSDL 表現には操作で交換されるドキュメントを表す単一の要素が含まれることを意味します。この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-112">Setting the style to <xref:System.ServiceModel.OperationFormatStyle.Document> means that the WSDL representation contains a single element that represents the document that is exchanged for an operation as shown in the following example.</span></span>

```xml
<wsdl:message name="IUseAndStyleCalculator_Add_InputMessage">
  <wsdl:part name="parameters" element="tns:Add"/>
</wsdl:message>
```

<span data-ttu-id="6a5c4-113"><xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> プロパティは、メッセージの書式を決定します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-113">The <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property determines the format of the message.</span></span> <span data-ttu-id="6a5c4-114">使用可能な値は <xref:System.ServiceModel.OperationFormatUse.Literal> と <xref:System.ServiceModel.OperationFormatUse.Encoded> で、既定値は <xref:System.ServiceModel.OperationFormatUse.Literal> です。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-114">Possible values are <xref:System.ServiceModel.OperationFormatUse.Literal> and <xref:System.ServiceModel.OperationFormatUse.Encoded>; the default value is <xref:System.ServiceModel.OperationFormatUse.Literal>.</span></span> <span data-ttu-id="6a5c4-115">Literal は、メッセージが WSDL 内のスキーマのリテラル インスタンスであることを意味します。Document/Literal の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-115">Literal means that the message is a literal instance of the schema in the WSDL as shown in the following Document/ Literal example.</span></span>

```xml
<Add xmlns="http://Microsoft.ServiceModel.Samples">
  <n1>100</n1>
  <n2>15.99</n2>
</Add>
```

<span data-ttu-id="6a5c4-116">Encoded は、WSDL 内のスキーマが、SOAP 1.1 のセクション 5 に規定されているルールに従ってエンコードされる抽象仕様であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-116">Encoded means that the schemas in the WSDL are abstract specifications that are encoded according to the rules found in SOAP 1.1 section 5.</span></span> <span data-ttu-id="6a5c4-117">RPC/Encoded の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-117">The following is an RPC/Encoded example.</span></span>

```xml
<q1:Add xmlns:q1="http://Microsoft.ServiceModel.Samples">
  <n1 xsi:type="xsd:double" xmlns="">100</n1>
  <n2 xsi:type="xsd:double" xmlns="">15.99</n2>
</q1:Add>
```

<span data-ttu-id="6a5c4-118">WS-I Basic Profile 1.0 では <xref:System.ServiceModel.OperationFormatUse.Encoded> の使用が禁止されています。したがって、これを使用するのは従来のサービスで必要な場合に限ります。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-118">The WS-I Basic Profile 1.0 prohibits the use of <xref:System.ServiceModel.OperationFormatUse.Encoded> and you should only use it when required by legacy services.</span></span> <span data-ttu-id="6a5c4-119">`Encoded` メッセージ形式は、XmlSerializer を使用する場合にのみ利用可能です。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-119">The `Encoded` message format is only available when using the XmlSerializer.</span></span>

<span data-ttu-id="6a5c4-120">このサンプルは、送受信されるメッセージを確認できるように、[トレースとメッセージログ](tracing-and-message-logging.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-120">To allow you to see the messages being sent and received, this sample is based on the [Tracing and Message Logging](tracing-and-message-logging.md).</span></span> <span data-ttu-id="6a5c4-121">サービス構成とソース コードは、トレースとメッセージ ログを有効化して利用できるように変更されています。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-121">The service configuration and source code have been modified to enable and utilize tracing and message logging.</span></span> <span data-ttu-id="6a5c4-122">さらに、<xref:System.ServiceModel.WSHttpBinding> はセキュリティを無効にして構成されているので、ログに記録されたメッセージは暗号化されていない状態で表示できます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-122">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, so the logged messages can be viewed in an unencrypted format.</span></span> <span data-ttu-id="6a5c4-123">生成されたトレースログ (e2e と .log) は、[サービストレースビューアーツール (svctraceviewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)を使用して表示する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-123">The resulting trace logs (System.ServiceModel.e2e and Message.log) should be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="6a5c4-124">トレースは、C:\LOGS フォルダーに作成されるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-124">The traces are configured to be created in the C:\LOGS folder.</span></span> <span data-ttu-id="6a5c4-125">サンプルを実行する前に、このフォルダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-125">Create the folder before running the sample.</span></span> <span data-ttu-id="6a5c4-126">トレースビューアーツールでメッセージの内容を表示するには、ツールの左側と右側の両方のウィンドウで **[メッセージ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-126">To view message contents in the Trace Viewer tool, select **Messages** in both the left and the right panes of the tool.</span></span>

<span data-ttu-id="6a5c4-127">次のコードでは、サービス コントラクトの <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> プロパティが <xref:System.ServiceModel.OperationFormatUse> に設定され、メッセージ本文の形式が既定の <xref:System.ServiceModel.OperationFormatStyle> から <xref:System.ServiceModel.OperationFormatStyle.Document> に変更されています。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-127">The following code shows the service contract with the <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> property set to <xref:System.ServiceModel.OperationFormatUse> and the format of the message body changed from the default <xref:System.ServiceModel.OperationFormatStyle> to <xref:System.ServiceModel.OperationFormatStyle.Document>.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"),
XmlSerializerFormat(Style = OperationFormatStyle.Rpc, 
                                 Use = OperationFormatUse.Encoded)]
public interface IUseAndStyleCalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="6a5c4-128">それぞれの <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> 設定と <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> 設定との違いを示すには、これらの設定をサービス内で変更してクライアントを再生成し、サンプルを実行します。その後、サービス ビューア ツールを使用して c:\logs\message.logs ファイルを調べます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-128">To see the difference between the different <xref:System.ServiceModel.XmlSerializerFormatAttribute.Use%2A> and <xref:System.ServiceModel.XmlSerializerFormatAttribute.Style%2A> settings, modify them in the service, regenerate the client, run the sample, and examine the c:\logs\message.logs file with the Service Trace Viewer tool.</span></span> <span data-ttu-id="6a5c4-129">また、`http://localhost/ServiceModelSamples/service.svc?wsdl`を表示して、メタデータへの影響についても確認します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-129">Also observe the impact on the metadata by viewing `http://localhost/ServiceModelSamples/service.svc?wsdl`.</span></span> <span data-ttu-id="6a5c4-130">通常、サービスのメタデータは複数のページに分割されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-130">The metadata for services is typically broken up into multiple pages.</span></span> <span data-ttu-id="6a5c4-131">メイン wsdl ページには WSDL バインドが含まれていますが、メッセージ定義を監視するための `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-131">The main wsdl page contains the WSDL bindings, but view `http://localhost/ServiceModelSamples/service.svc?wsdl=wsdl0` to observe the message definitions.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6a5c4-132">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="6a5c4-132">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6a5c4-133">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6a5c4-134">メッセージのログ記録用に C:\LOGS ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-134">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="6a5c4-135">ユーザー Network Service にそのディレクトリの書き込み権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-135">Give the user Network Service write permissions for this directory.</span></span>

3. <span data-ttu-id="6a5c4-136">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-136">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

4. <span data-ttu-id="6a5c4-137">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-137">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6a5c4-138">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6a5c4-139">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-139">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="6a5c4-140">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6a5c4-141">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="6a5c4-141">This sample is located in the following directory.</span></span>
> 
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\UseAndStyle`
