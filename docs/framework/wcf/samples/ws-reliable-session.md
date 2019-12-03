---
title: WS 信頼できるセッション
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 1b1878b5e3d04968ae13527a594bb2520891c6e5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714605"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="1fcb5-102">WS 信頼できるセッション</span><span class="sxs-lookup"><span data-stu-id="1fcb5-102">WS Reliable Session</span></span>
<span data-ttu-id="1fcb5-103">このサンプルでは、信頼できるセッションの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="1fcb5-104">信頼できるセッションは、信頼できるメッセージとセッションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="1fcb5-105">信頼できるメッセージは、エラー時に通信を再試行するほか、メッセージの順次到着などの配信の保証を指定できるようにします。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="1fcb5-106">セッションでは、呼び出し間でクライアントの状態が保持されます。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="1fcb5-107">サンプルでは、クライアントの状態を保持するセッションを実装し、配信順序を保証することを指定します。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1fcb5-108">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1fcb5-109">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-109">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="1fcb5-110">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1fcb5-111">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-111">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="1fcb5-112">このサンプルは、電卓サービスを実装する[はじめに](../../../../docs/framework/wcf/samples/getting-started-sample.md)に基づいています。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="1fcb5-113">信頼できるセッション機能は、クライアントとサービスのアプリケーション構成ファイルで有効化され、構成されています。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="1fcb5-114">このサンプルでは、サービスはインターネット インフォメーション サービス (IIS) によってホストされており、クライアントはコンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1fcb5-115">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="1fcb5-116">このサンプルでは、`wsHttpBinding` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="1fcb5-117">バインディングは、クライアントとサービスの両方の構成ファイルに指定されます。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="1fcb5-118">バインディングの種類はエンドポイント要素の `binding` 属性に指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="1fcb5-119">エンドポイントには、"Binding1" という名前のバインド構成を参照する `bindingConfiguration` 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="1fcb5-120">バインディング構成は、 [\<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md)の `enabled` 属性を `true`に設定することによって、信頼できるセッションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="1fcb5-121">順序付きセッションの配信の保証は、ordered 属性を `true` または `false` に設定することによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="1fcb5-122">既定値は、 `true`です。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="1fcb5-123">サービス実装クラスは、クライアントごとに個別のクラスのインスタンスをインスタンス化して保持する <xref:System.ServiceModel.InstanceContextMode.PerSession> を実装します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="1fcb5-124">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="1fcb5-125">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="1fcb5-126">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="1fcb5-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="1fcb5-127">次のコマンドを使用して、ASP.NET 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="1fcb5-128">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="1fcb5-129">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="1fcb5-130">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="1fcb5-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
