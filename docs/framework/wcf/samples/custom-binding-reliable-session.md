---
title: カスタム バインディングの信頼できるセッション
ms.date: 03/30/2017
ms.assetid: c5fcd409-246f-4f3e-b3f1-629506ca4c04
ms.openlocfilehash: 76c701aaae368171bc7047784e1dc126937c84f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463936"
---
# <a name="custom-binding-reliable-session"></a><span data-ttu-id="48f38-102">カスタム バインディングの信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="48f38-102">Custom Binding Reliable Session</span></span>

<span data-ttu-id="48f38-103">カスタム バインドは、個々のバインド要素の順序付きリストとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="48f38-103">A custom binding is defined by an ordered list of discrete binding elements.</span></span> <span data-ttu-id="48f38-104">このサンプルでは、さまざまなトランスポートとメッセージ エンコーディング要素を使用し、特に信頼できるセッションを有効化することによって、カスタム バインディングを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="48f38-104">This sample demonstrates how to configure a custom binding with various transport and message encoding elements, especially enabling reliable sessions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48f38-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="48f38-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="48f38-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="48f38-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="48f38-107">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="48f38-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="48f38-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="48f38-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSession`

## <a name="sample-details"></a><span data-ttu-id="48f38-109">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="48f38-109">Sample Details</span></span>

<span data-ttu-id="48f38-110">信頼できるセッションは、信頼できるメッセージとセッションに関する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="48f38-110">Reliable sessions provide features for reliable messaging and sessions.</span></span> <span data-ttu-id="48f38-111">信頼できるメッセージは、エラー時に通信を再試行するほか、メッセージの順次到着などの配信の保証を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="48f38-111">Reliable messaging retries communication on failure and allows delivery assurances such as in-order arrival of messages to be specified.</span></span> <span data-ttu-id="48f38-112">セッションでは、呼び出し間でクライアントの状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="48f38-112">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="48f38-113">サンプルでは、クライアントの状態を保持するセッションを実装し、配信順序を保証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="48f38-113">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span> <span data-ttu-id="48f38-114">このサンプルは、電卓サービスを実装する[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="48f38-114">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="48f38-115">信頼できるセッション機能は、クライアントとサービスのアプリケーション構成ファイルで有効化され、構成されています。</span><span class="sxs-lookup"><span data-stu-id="48f38-115">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>

> [!NOTE]
> <span data-ttu-id="48f38-116">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48f38-116">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="48f38-117">バインド要素の順序付けは、チャネル スタック内のレイヤーを表すカスタム バインドを定義する際に重要です (「[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)」を参照)。</span><span class="sxs-lookup"><span data-stu-id="48f38-117">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span>

<span data-ttu-id="48f38-118">サンプルのサービス構成は、次のコード例のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="48f38-118">The service configuration for the sample is defined as shown in the following code example.</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc  -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                     requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous" bypassProxyOnLocal="false"
                        hostNameComparisonMode="StrongWildcard"
                        proxyAuthenticationScheme="Anonymous" realm=""
                        useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

<span data-ttu-id="48f38-119">複数コンピュータのシナリオで実行する場合は、クライアントのエンドポイント アドレスをサービスのホスト名に合わせて変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="48f38-119">When running in a cross-machine scenario, you must change client's endpoint address to reflect the host name of the service.</span></span>

<span data-ttu-id="48f38-120">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="48f38-120">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="48f38-121">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="48f38-121">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="48f38-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="48f38-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="48f38-123">次のコマンドASP.NET使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="48f38-123">Install ASP.NET 4.0 using the following command:</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="48f38-124">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="48f38-124">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="48f38-125">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="48f38-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="48f38-126">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="48f38-126">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="48f38-127">クロスマシン構成でクライアントを実行する場合は、次の例に示すように、[\<エンドポイント>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素の`address``clientBaseAddress`属性と[\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)の属性の両方で"localhost" を適切なマシンの名前に置き換えてください。</span><span class="sxs-lookup"><span data-stu-id="48f38-127">When running the client in a cross-machine configuration, be sure to replace "localhost" in both the `address` attribute of the [\<endpoint>](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element and the `clientBaseAddress` attribute of the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) with the name of the appropriate machine, as shown in the following example.</span></span>

    ```xml
    <endpoint name = ""
    address="http://service_machine_name/servicemodelsamples/service.svc" />
    <compositeDuplex clientBaseAddress="http://client_machine_name:8000/myClient/" />
    ```
