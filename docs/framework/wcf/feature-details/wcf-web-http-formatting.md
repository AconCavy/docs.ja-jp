---
title: WCF Web HTTP 書式設定
ms.date: 03/30/2017
ms.assetid: e2414896-5463-41cd-b0a6-026a713eac2c
ms.openlocfilehash: 011ff4f2e667268fac1aa2d82c0a2c4ffefc8dde
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585559"
---
# <a name="wcf-web-http-formatting"></a><span data-ttu-id="9928f-102">WCF Web HTTP 書式設定</span><span class="sxs-lookup"><span data-stu-id="9928f-102">WCF Web HTTP formatting</span></span>
<span data-ttu-id="9928f-103">WCF Web HTTP プログラミング モデルでは、サービス操作で返す応答の最適な形式を動的に判断できます。</span><span class="sxs-lookup"><span data-stu-id="9928f-103">The WCF Web HTTP programming model allows you to dynamically determine the best format for a service operation to return its response in.</span></span> <span data-ttu-id="9928f-104">適切な形式を判断するための方法として、自動と明示的の 2 つがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9928f-104">Two methods for determining an appropriate format are supported: automatic and explicit.</span></span>  
  
## <a name="automatic-formatting"></a><span data-ttu-id="9928f-105">自動書式</span><span class="sxs-lookup"><span data-stu-id="9928f-105">Automatic formatting</span></span>  
 <span data-ttu-id="9928f-106">有効にした場合は、応答を返す最適な形式が自動選択によって選択されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-106">When enabled, automatic formatting chooses the best format in which to return the response.</span></span> <span data-ttu-id="9928f-107">最適な形式の判断は、次の項目をこの順序で確認することで行われます。</span><span class="sxs-lookup"><span data-stu-id="9928f-107">It determines the best format by checking the following, in order:</span></span>  
  
1. <span data-ttu-id="9928f-108">要求メッセージの Accept ヘッダーのメディアの種類。</span><span class="sxs-lookup"><span data-stu-id="9928f-108">The media types in the request message’s Accept header.</span></span>  
  
2. <span data-ttu-id="9928f-109">要求メッセージのコンテンツの種類。</span><span class="sxs-lookup"><span data-stu-id="9928f-109">The content-type of the request message.</span></span>  
  
3. <span data-ttu-id="9928f-110">その処理での既定の形式設定。</span><span class="sxs-lookup"><span data-stu-id="9928f-110">The default format setting in the operation.</span></span>  
  
4. <span data-ttu-id="9928f-111">WebHttpBehavior での既定の形式設定。</span><span class="sxs-lookup"><span data-stu-id="9928f-111">The default format setting in the WebHttpBehavior.</span></span>  
  
 <span data-ttu-id="9928f-112">要求メッセージに Accept ヘッダーが含まれている場合は、Windows Communication Foundation (WCF) インフラストラクチャによって、サポートされている型が検索されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-112">If the request message contains an Accept header the Windows Communication Foundation (WCF) infrastructure searches for a type that it supports.</span></span> <span data-ttu-id="9928f-113">`Accept` ヘッダーにメディアの種類のプロパティが指定されている場合は、それに従います。</span><span class="sxs-lookup"><span data-stu-id="9928f-113">If the `Accept` header specifies priorities for its media types, they are honored.</span></span> <span data-ttu-id="9928f-114">適切な形式が `Accept` ヘッダーで見つからない場合は、要求メッセージのコンテンツの種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-114">If no suitable format is found in the `Accept` header, the content-type of the request message is used.</span></span> <span data-ttu-id="9928f-115">適切なコンテンツの種類が指定されていない場合は、その操作の既定の形式設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-115">If no suitable content-type is specified, the default format setting for the operation is used.</span></span> <span data-ttu-id="9928f-116">既定の形式は、`ResponseFormat` の <xref:System.ServiceModel.Web.WebGetAttribute> パラメーターおよび <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性で設定されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-116">The default format is set with the `ResponseFormat` parameter of the <xref:System.ServiceModel.Web.WebGetAttribute> and <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes.</span></span> <span data-ttu-id="9928f-117">その操作に既定の形式が指定されていない場合は、<xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> プロパティの値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-117">If no default format is specified on the operation, the value of the <xref:System.ServiceModel.Description.WebHttpBehavior.DefaultOutgoingResponseFormat%2A> property is used.</span></span> <span data-ttu-id="9928f-118">形式の自動選択は、<xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> プロパティに依存します。</span><span class="sxs-lookup"><span data-stu-id="9928f-118">Automatic formatting relies on the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property.</span></span> <span data-ttu-id="9928f-119">このプロパティが `true` に設定されている場合は、使用する最適な形式が WCF インフラストラクチャで決定されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-119">When this property is set to `true`, the WCF infrastructure determines the best format to use.</span></span> <span data-ttu-id="9928f-120">形式の自動選択は、既定で、下位互換性のために無効になっています。</span><span class="sxs-lookup"><span data-stu-id="9928f-120">Automatic format selection is disabled by default for backwards compatibility.</span></span> <span data-ttu-id="9928f-121">形式の自動選択は、プログラムで有効にすることも、構成ファイルを使用して有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9928f-121">Automatic format selection can be enabled programmatically or through configuration.</span></span> <span data-ttu-id="9928f-122">形式の自動選択をコードで有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9928f-122">The following example shows how to enable automatic format selection in code.</span></span>  
  
```csharp
// This code assumes the service name is MyService and the service contract is IMyContract
Uri baseAddress = new Uri("http://localhost:8000");  
  
WebServiceHost host = new WebServiceHost(typeof(MyService), baseAddress)  
try  
{  
   ServiceEndpoint sep = host.AddServiceEndpoint(typeof(IMyContract), new WebHttpBinding(), "");  
   // Check it see if the WebHttpBehavior already exists  
   WebHttpBehavior whb = sep.Behaviors.Find<WebHttpBehavior>();  
  
   if (whb != null)  
   {  
      whb.AutomaticFormatSelectionEnabled = true;  
   }  
   else  
   {  
      WebHttpBehavior webBehavior = new WebHttpBehavior();  
      webBehavior.AutomaticFormatSelectionEnabled = true;  
      sep.Behaviors.Add(webBehavior);  
   }  
         // Open host to start listening for messages  
   host.Open();
  
  // ...  
}  
  catch(CommunicationException ex)  
  {  
     Console.WriteLine("An exception occurred: " + ex.Message());  
  }  
```  
  
 <span data-ttu-id="9928f-123">形式の自動選択は、構成ファイルを使用して有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9928f-123">Automatic formatting can also be enabled through configuration.</span></span> <span data-ttu-id="9928f-124"><xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> プロパティは、<xref:System.ServiceModel.Description.WebHttpBehavior> で直接、または <xref:System.ServiceModel.Description.WebHttpEndpoint> を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="9928f-124">You can set the <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A> property directly on the <xref:System.ServiceModel.Description.WebHttpBehavior> or using the <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span> <span data-ttu-id="9928f-125">形式の自動選択を <xref:System.ServiceModel.Description.WebHttpBehavior> で有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9928f-125">The following example shows how to enable the automatic format selection on the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <endpointBehaviors>  
      <behavior>  
        <webHttp automaticFormatSelectionEnabled="true" />  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
      <standardEndpoint name="" helpEnabled="true" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="9928f-126">形式の自動選択を、<xref:System.ServiceModel.Description.WebHttpEndpoint> を使用して有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="9928f-126">The following example shows how to enable automatic format selection using <xref:System.ServiceModel.Description.WebHttpEndpoint>.</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>  
      <webHttpEndpoint>  
        <!-- the "" standard endpoint is used by WebServiceHost for auto creating a web endpoint. -->  
        <standardEndpoint name="" helpEnabled="true" automaticFormatSelectionEnabled="true"  />  
      </webHttpEndpoint>  
    </standardEndpoints>  
  </system.serviceModel>  
```  
  
## <a name="explicit-formatting"></a><span data-ttu-id="9928f-127">明示的な書式設定</span><span class="sxs-lookup"><span data-stu-id="9928f-127">Explicit formatting</span></span>  
 <span data-ttu-id="9928f-128">名前が示すように、形式の明示的な選択では、操作コード内に使用する最適な形式を開発者が判断します。</span><span class="sxs-lookup"><span data-stu-id="9928f-128">As the name implies, in explicit formatting the developer determines the best format to use within the operation code.</span></span> <span data-ttu-id="9928f-129">最適な形式が XML または JSON の場合は、開発者が <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> を <xref:System.ServiceModel.Web.WebMessageFormat.Xml> または <xref:System.ServiceModel.Web.WebMessageFormat.Json> のいずれかに設定します。</span><span class="sxs-lookup"><span data-stu-id="9928f-129">If the best format is XML or JSON the developer sets <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> to either <xref:System.ServiceModel.Web.WebMessageFormat.Xml> or <xref:System.ServiceModel.Web.WebMessageFormat.Json>.</span></span> <span data-ttu-id="9928f-130"><xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> プロパティが明示的に設定されていない場合は、その操作の既定の形式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-130">If the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> property is not explicitly set, then the operation’s default format is used.</span></span>  
  
 <span data-ttu-id="9928f-131">次の例では、使用する形式に対する形式クエリ文字列パラメーターを確認します。</span><span class="sxs-lookup"><span data-stu-id="9928f-131">The following example checks the format query string parameter for a format to use.</span></span> <span data-ttu-id="9928f-132">指定されている場合、その操作の形式は <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> を使用して設定されます。</span><span class="sxs-lookup"><span data-stu-id="9928f-132">If it has been specified, it sets the operation’s format using <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A>.</span></span>  
  
```csharp
public class Service : IService  
{  
    [WebGet]  
     public string EchoWithGet(string s)  
    {  
        // if a format query string parameter has been specified, set the response format to that. If no such
        // query string parameter exists the Accept header will be used
        string formatQueryStringValue = WebOperationContext.Current.IncomingRequest.UriTemplateMatch.QueryParameters["format"];  
        if (!string.IsNullOrEmpty(formatQueryStringValue))  
        {  
            if (formatQueryStringValue.Equals("xml", System.StringComparison.OrdinalIgnoreCase))  
            {
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Xml;
            }
            else if (formatQueryStringValue.Equals("json", System.StringComparison.OrdinalIgnoreCase))  
            {  
                WebOperationContext.Current.OutgoingResponse.Format = WebMessageFormat.Json;  
            }  
            else  
            {  
                throw new WebFaultException<string>($"Unsupported format '{formatQueryStringValue}'",   HttpStatusCode.BadRequest);
            }  
        }  
        return "You said " + s;  
    }  
```  
  
 <span data-ttu-id="9928f-133">XML または JSON 以外の形式をサポートする必要がある場合は、操作に <xref:System.ServiceModel.Channels.Message> の戻り値の型があるように定義します。</span><span class="sxs-lookup"><span data-stu-id="9928f-133">If you need to support formats other than XML or JSON, define your operation to have a return type of <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="9928f-134">操作コード内で、使用する適切な形式を決定し、次のメソッドのいずれかを使用して <xref:System.ServiceModel.Channels.Message> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9928f-134">Within the operation code, determine the appropriate format to use and then create a <xref:System.ServiceModel.Channels.Message> object using one of the following methods:</span></span>  
  
- `WebOperationContext.CreateAtom10Response`  
  
- `WebOperationContext.CreateJsonResponse`  
  
- `WebOperationContext.CreateStreamResponse`  
  
- `WebOperationContext.CreateTextResponse`  
  
- `WebOperationContext.CreateXmlResponse`  
  
 <span data-ttu-id="9928f-135">これらの各メソッドでは、この適切な形式でコンテンツを取得してメッセージを作成します。</span><span class="sxs-lookup"><span data-stu-id="9928f-135">Each of these methods takes content and creates a message with the appropriate format.</span></span> <span data-ttu-id="9928f-136">`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` メソッドは、クライアントで優先される形式の一覧を優先度が高い順に取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9928f-136">The `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` method can be used to get a list of formats preferred by the client in order of decreasing preference.</span></span> <span data-ttu-id="9928f-137">次の例では、`WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` を使用して使用形式を決定し、適切な作成応答メソッドを使用して応答メッセージを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9928f-137">The following example shows how to use `WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements` to determine the format to use and then uses the appropriate create response method to create the response message.</span></span>  
  
```csharp
public class Service : IService  
{  
    public Message EchoListWithGet(string list)  
    {  
        List<string> returnList = new List<string>(list.Split(new char[] { ',' }, StringSplitOptions.RemoveEmptyEntries));  
        IList<ContentType> acceptHeaderElements = WebOperationContext.Current.IncomingRequest.GetAcceptHeaderElements();  
        for (int x = 0; x < acceptHeaderElements.Count; x++)  
        {  
            string normalizedMediaType = acceptHeaderElements[x].MediaType.ToLowerInvariant();  
            switch (normalizedMediaType)  
            {  
                case "image/jpeg": return CreateJpegResponse(returnList);  
                case "application/xhtml+xml": return CreateXhtmlResponse(returnList);  
                case "application/atom+xml": return CreateAtom10Response(returnList);  
                case "application/xml": return CreateXmlResponse(returnList);  
                case "application/json": return CreateJsonResponse(returnList);  
          }  
    }  
  
    // Default response format is XML  
    return CreateXmlResponse(returnList);  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="9928f-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="9928f-138">See also</span></span>

- <xref:System.UriTemplate>
- <xref:System.UriTemplateMatch>
- [<span data-ttu-id="9928f-139">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="9928f-139">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
- [<span data-ttu-id="9928f-140">UriTemplate と UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="9928f-140">UriTemplate and UriTemplateTable</span></span>](uritemplate-and-uritemplatetable.md)
- [<span data-ttu-id="9928f-141">WCF Web HTTP プログラミング モデルの概要</span><span class="sxs-lookup"><span data-stu-id="9928f-141">WCF Web HTTP Programming Model Overview</span></span>](wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="9928f-142">WCF Web HTTP プログラミング オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="9928f-142">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
