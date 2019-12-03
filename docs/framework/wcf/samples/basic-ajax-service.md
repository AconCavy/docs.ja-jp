---
title: 基本的な AJAX サービス
ms.date: 03/30/2017
ms.assetid: d66d0c91-0109-45a0-a901-f3e4667c2465
ms.openlocfilehash: 334cc9e53d7d9746c204abe37e7c30d00baa824b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716118"
---
# <a name="basic-ajax-service"></a><span data-ttu-id="e890b-102">基本的な AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="e890b-102">Basic AJAX Service</span></span>

<span data-ttu-id="e890b-103">このサンプルでは、Windows Communication Foundation (WCF) を使用して、基本的な ASP.NET 非同期 JavaScript and XML (AJAX) サービス (Web ブラウザークライアントから JavaScript コードを使用してアクセスできるサービス) を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e890b-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access using JavaScript code from a Web browser client).</span></span> <span data-ttu-id="e890b-104">このサービスは、<xref:System.ServiceModel.Web.WebGetAttribute> 属性を使用してサービスが HTTP GET 要求に応答し、JSON (JavaScript Object Notation) データ形式を使用して応答するように構成されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e890b-104">The service uses the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to ensure that the service responds to HTTP GET requests and is configured to use the JavaScript Object Notation (JSON) data format for responses.</span></span>

<span data-ttu-id="e890b-105">WCF での AJAX サポートは、`ScriptManager` コントロールを介して ASP.NET AJAX で使用できるように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="e890b-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="e890b-106">ASP.NET AJAX で WCF を使用する例については、 [ajax のサンプル](ajax.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e890b-106">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e890b-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e890b-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="e890b-108">次のコードでは、サービスが確実に HTTP GET 要求に応答するように <xref:System.ServiceModel.Web.WebGetAttribute> 属性が `Add` 操作に適用されています。</span><span class="sxs-lookup"><span data-stu-id="e890b-108">In the following code, the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is applied to the `Add` operation to ensure that the service responds to HTTP GET requests.</span></span> <span data-ttu-id="e890b-109">このコードでは、簡単にするために GET を使用します (すべての Web ブラウザーから HTTP GET 要求を構築できます)。</span><span class="sxs-lookup"><span data-stu-id="e890b-109">The code uses GET for simplicity (you can construct an HTTP GET request from any Web browser).</span></span> <span data-ttu-id="e890b-110">また、GET を使用してキャッシングを有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="e890b-110">You can also use GET to enable caching.</span></span> <span data-ttu-id="e890b-111">HTTP POST は `WebGetAttribute` 属性を使用しない場合の既定です。</span><span class="sxs-lookup"><span data-stu-id="e890b-111">HTTP POST is the default in the absence of the `WebGetAttribute` attribute.</span></span>

```csharp
[ServiceContract(Namespace = "SimpleAjaxService")]
public interface ICalculator
{
    [WebGet]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="e890b-112">サンプルの .svc ファイルでは <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> が使用され、それによって <xref:System.ServiceModel.Description.WebScriptEndpoint> 標準エンドポイントがサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e890b-112">The sample .svc file uses <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, which adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="e890b-113">エンドポイントは、.svc ファイルに相対する空のアドレス位置に設定されます。</span><span class="sxs-lookup"><span data-stu-id="e890b-113">The endpoint is configured at an empty address relative to the .svc file.</span></span> <span data-ttu-id="e890b-114">これは、サービスのアドレスが `http://localhost/ServiceModelSamples/service.svc`、操作名以外の追加のサフィックスがないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="e890b-114">This means that the address of the service is `http://localhost/ServiceModelSamples/service.svc`, with no additional suffixes other than the operation name.</span></span>

`<%@ServiceHost language="C#" Debug="true" Service="Microsoft.Samples.SimpleAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory" %>`

<span data-ttu-id="e890b-115"><xref:System.ServiceModel.Description.WebScriptEndpoint> は、ASP.NET AJAX クライアント ページからサービスにアクセスできるように事前に構成されています。</span><span class="sxs-lookup"><span data-stu-id="e890b-115">The <xref:System.ServiceModel.Description.WebScriptEndpoint> is pre-configured to make the service accessible from an ASP.NET AJAX client page.</span></span> <span data-ttu-id="e890b-116">Web.config 内の次のセクションを使用して、エンドポイントに対する構成変更を追加できます。</span><span class="sxs-lookup"><span data-stu-id="e890b-116">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="e890b-117">追加の変更が不要な場合は、このセクションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="e890b-117">It can be removed if no extra changes are required.</span></span>

```xml
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <!-- Use this element to configure the endpoint -->
      <standardEndpoint name=""  />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```

<span data-ttu-id="e890b-118"><xref:System.ServiceModel.Description.WebScriptEndpoint> は、サービスの既定のデータ形式を XML ではなく JSON に設定します。</span><span class="sxs-lookup"><span data-stu-id="e890b-118">The <xref:System.ServiceModel.Description.WebScriptEndpoint> sets the default data format for the service to JSON instead of XML.</span></span> <span data-ttu-id="e890b-119">サービスを呼び出すには、このトピックで後述するセットアップとビルドの手順を完了した後に `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` に移動します。</span><span class="sxs-lookup"><span data-stu-id="e890b-119">To invoke the service, navigate to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` after completing the set up and build steps shown later in this topic.</span></span> <span data-ttu-id="e890b-120">このテスト機能は、HTTP GET 要求を使用することによって有効になります。</span><span class="sxs-lookup"><span data-stu-id="e890b-120">This testing functionality is enabled by the use of a HTTP GET request.</span></span>

<span data-ttu-id="e890b-121">クライアントの Web ページの SimpleAjaxClientPage.aspx には、ユーザーがページ上のいずれかの操作ボタンをクリックするとサービスを呼び出す ASP.NET コードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e890b-121">The client Web page SimpleAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="e890b-122">`ScriptManager` コントロールは、JavaScript を使用してサービスからプロキシにアクセスできるようにする場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="e890b-122">The `ScriptManager` control is used to make a proxy to the service accessible through JavaScript.</span></span>

```aspx-csharp
<asp:ScriptManager ID="ScriptManager" runat="server">
    <Services>
        <asp:ServiceReference Path="service.svc" />
    </Services>
</asp:ScriptManager>
```

<span data-ttu-id="e890b-123">次の JavaScript コードを使用してローカル プロキシをインスタンス化し、操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e890b-123">The local proxy is instantiated and operations are invoked using the following JavaScript code.</span></span>

```javascript
// Code for extracting arguments n1 and n2 omitted…
// Instantiate a service proxy
var proxy = new SimpleAjaxService.ICalculator();
// Code for selecting operation omitted…
proxy.Add(parseFloat(n1), parseFloat(n2), onSuccess, onFail, null);
```

<span data-ttu-id="e890b-124">サービス呼び出しが成功すると、コードは `onSuccess` ハンドラーを呼び出し、操作の結果がテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e890b-124">If the service call succeeds, the code invokes the `onSuccess` handler and the result of the operation is displayed in a text box.</span></span>

```javascript
function onSuccess(mathResult){
     document.getElementById("result").value = mathResult;
}
```

> [!IMPORTANT]
> <span data-ttu-id="e890b-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e890b-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e890b-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e890b-126">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e890b-127">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="e890b-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e890b-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e890b-128">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\SimpleAjaxService`
