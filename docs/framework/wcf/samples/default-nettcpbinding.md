---
title: 既定の NetTcpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- Net profile TCP
ms.assetid: e8475fe6-0ecd-407a-8e7e-45860561bb74
ms.openlocfilehash: dc417300eb6f62b89a1c07a4f2291b7366e410b1
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716548"
---
# <a name="default-nettcpbinding"></a><span data-ttu-id="aaf6d-102">既定の NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="aaf6d-102">Default NetTcpBinding</span></span>
<span data-ttu-id="aaf6d-103">このサンプルは、<xref:System.ServiceModel.NetTcpBinding> バインディングの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-103">This sample demonstrates the use of the <xref:System.ServiceModel.NetTcpBinding> binding.</span></span> <span data-ttu-id="aaf6d-104">このサンプルは、電卓サービスを実装する[はじめに](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="aaf6d-105">このサンプルでは、サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-105">In this sample, the service is self-hosted.</span></span> <span data-ttu-id="aaf6d-106">クライアントとサービスは両方ともコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-106">Both the client and service are console applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="aaf6d-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="aaf6d-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="aaf6d-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-109">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="aaf6d-110">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="aaf6d-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-111">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\Default`  
  
 <span data-ttu-id="aaf6d-112">バインディングは、クライアントとサービスの構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-112">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="aaf6d-113">バインドの種類は、次のサンプル構成に示すように、 [\<エンドポイント >](../../configure-apps/file-schema/wcf/endpoint-element.md)要素の `binding` 属性で指定します。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-113">The binding type is specified in the `binding` attribute of the [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="aaf6d-114">前のサンプルでは、`netTcpBinding` バインディングを既定の設定で使用するようエンドポイントを構成する手順を示しました。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-114">The previous sample shows how to configure an endpoint to use the `netTcpBinding` binding with the default settings.</span></span> <span data-ttu-id="aaf6d-115">`netTcpBinding` バインディングを構成してその設定の一部を変更する場合は、バインド構成を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-115">If you want to configure the `netTcpBinding` binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="aaf6d-116">エンドポイントは、バインディング構成を `bindingConfiguration` 属性を使用して名前で参照します。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-116">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="aaf6d-117">このサンプルでは、バインド構成の名前は `Binding1` です。これは次のサンプル構成のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-117">In this sample, the binding configuration is named `Binding1` and is defined as shown in the following sample configuration.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
    <endpoint address=""  
              binding="netTcpBinding"  
              bindingConfiguration="Binding1"   
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
  
<bindings>  
  <netTcpBinding>  
    <binding name="Binding1"   
             closeTimeout="00:01:00"  
             openTimeout="00:01:00"   
             receiveTimeout="00:10:00"   
             sendTimeout="00:01:00"  
             transactionFlow="false"   
             transferMode="Buffered"   
             transactionProtocol="OleTransactions"  
             hostNameComparisonMode="StrongWildcard"   
             listenBacklog="10"  
             maxBufferPoolSize="524288"   
             maxBufferSize="65536"   
             maxConnections="10"  
             maxReceivedMessageSize="65536">  
      <readerQuotas maxDepth="32"   
                    maxStringContentLength="8192"   
                    maxArrayLength="16384"  
                    maxBytesPerRead="4096"   
                    maxNameTableCharCount="16384" />  
      <reliableSession ordered="true"   
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />  
      </security>  
    </binding>  
  </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="aaf6d-118">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-118">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="aaf6d-119">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-119">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press ENTER to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="aaf6d-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="aaf6d-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="aaf6d-121">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-121">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="aaf6d-122">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="aaf6d-123">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-123">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="aaf6d-124">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="aaf6d-125">サーバーは自己ホスト型なので、このサンプルを複数コンピューター構成で実行する場合は、次のようにクライアントの App.config ファイルで ID を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aaf6d-125">Because the server is self-hosted, you must specify an identity in the client's App.config file to run the sample in a cross-machine configuration.</span></span>  
  
    ```xml  
    <client>  
      <endpoint name=""  
          address="net.tcp://servername:9000/servicemodelsamples/service"   
          binding="netTcpBinding"   
          contract="Microsoft.ServiceModel.Samples.ICalculator">  
            <identity>  
              <userPrincipalName value = "user_name@service_domain"/>  
            </identity>  
      </endpoint>  
    </client>  
    ```  
