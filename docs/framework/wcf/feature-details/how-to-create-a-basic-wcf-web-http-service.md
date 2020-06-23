---
title: '方法: 基本的な WCF Web HTTP サービスを作成する'
description: WCF で web エンドポイントを公開するサービスを作成する方法について説明します。 Web エンドポイントは、XML または JSON を使用してデータを送信します。 SOAP エンベロープがありません。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 877662d3-d372-4e08-b417-51f66a0095cd
ms.openlocfilehash: 7481367f27d973ba809dff5ca1c4a4f168fbbb98
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247105"
---
# <a name="how-to-create-a-basic-wcf-web-http-service"></a><span data-ttu-id="66315-105">方法: 基本的な WCF Web HTTP サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="66315-105">How to: Create a Basic WCF Web HTTP Service</span></span>

<span data-ttu-id="66315-106">Windows Communication Foundation (WCF) を使用すると、Web エンドポイントを公開するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="66315-106">Windows Communication Foundation (WCF) allows you to create a service that exposes a Web endpoint.</span></span> <span data-ttu-id="66315-107">Web エンドポイントは、XML または JSON でデータを送信します。SOAP エンベロープはありません。</span><span class="sxs-lookup"><span data-stu-id="66315-107">Web endpoints send data by XML or JSON, there is no SOAP envelope.</span></span> <span data-ttu-id="66315-108">ここでは、このようなエンドポイントを公開する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="66315-108">This topic demonstrates how to expose such an endpoint.</span></span>

> [!NOTE]
> <span data-ttu-id="66315-109">Web エンドポイントをセキュリティで保護する唯一の方法は、トランスポート セキュリティを使用する HTTPS を介してエンドポイントを公開することです。</span><span class="sxs-lookup"><span data-stu-id="66315-109">The only way to secure a Web endpoint is to expose it through HTTPS, using transport security.</span></span> <span data-ttu-id="66315-110">メッセージ ベースのセキュリティを使用する場合、セキュリティ情報は通常 SOAP ヘッダーに配置されます。SOAP 以外のエンドポイントに送信するメッセージには SOAP エンベロープが含まれないため、セキュリティ情報を配置する場所がなく、トランスポート セキュリティに依存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="66315-110">When using message-based security, security information is usually placed in SOAP headers and because the messages sent to non-SOAP endpoints contain no SOAP envelope, there is nowhere to place the security information and you must rely on transport security.</span></span>

## <a name="to-create-a-web-endpoint"></a><span data-ttu-id="66315-111">Web エンドポイントを作成するには</span><span class="sxs-lookup"><span data-stu-id="66315-111">To create a Web endpoint</span></span>

1. <span data-ttu-id="66315-112"><xref:System.ServiceModel.ServiceContractAttribute>、<xref:System.ServiceModel.Web.WebInvokeAttribute>、および <xref:System.ServiceModel.Web.WebGetAttribute> の各属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="66315-112">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes.</span></span>

     [!code-csharp[htBasicService#0](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#0)]
     [!code-vb[htBasicService#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="66315-113">既定では、<xref:System.ServiceModel.Web.WebInvokeAttribute> は POST 呼び出しを操作にマッピングします。</span><span class="sxs-lookup"><span data-stu-id="66315-113">By default, <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="66315-114">ただし、"method=" パラメーターを指定することで、操作にマッピングする HTTP メソッド (HEAD、PUT、DELETE など) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="66315-114">You can, however, specify the HTTP method (for example, HEAD, PUT, or DELETE) to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="66315-115"><xref:System.ServiceModel.Web.WebGetAttribute> には "method=" パラメーターがないため、サービス操作には GET 呼び出しのみがマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="66315-115"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="66315-116">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="66315-116">Implement the service contract.</span></span>

     [!code-csharp[htBasicService#1](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#1)]
     [!code-vb[htBasicService#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="66315-117">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="66315-117">To host the service</span></span>

1. <span data-ttu-id="66315-118"><xref:System.ServiceModel.Web.WebServiceHost> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="66315-118">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span>

     [!code-csharp[htBasicService#2](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#2)]
     [!code-vb[htBasicService#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#2)]

2. <span data-ttu-id="66315-119"><xref:System.ServiceModel.Description.ServiceEndpoint> を持つ <xref:System.ServiceModel.Description.WebHttpBehavior> を追加します。</span><span class="sxs-lookup"><span data-stu-id="66315-119">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with the <xref:System.ServiceModel.Description.WebHttpBehavior>.</span></span>

     [!code-csharp[htBasicService#3](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#3)]
     [!code-vb[htBasicService#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#3)]

    > [!NOTE]
    > <span data-ttu-id="66315-120">エンド ポイントを追加しない場合は、<xref:System.ServiceModel.Web.WebServiceHost> が自動的に既定のエンド ポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="66315-120">If you do not add an endpoint, <xref:System.ServiceModel.Web.WebServiceHost> automatically creates a default endpoint.</span></span> <span data-ttu-id="66315-121"><xref:System.ServiceModel.Web.WebServiceHost> は、他にも <xref:System.ServiceModel.Description.WebHttpBehavior> を追加し、HTTP ヘルプ ページと Web サービス記述言語 (WSDL) GET 機能を無効にすることによって、メタデータ エンドポイントが既定の HTTP エンドポイントに干渉しないようにします。</span><span class="sxs-lookup"><span data-stu-id="66315-121"><xref:System.ServiceModel.Web.WebServiceHost> also adds <xref:System.ServiceModel.Description.WebHttpBehavior> and disables the HTTP Help page and the Web Services Description Language (WSDL) GET functionality so the metadata endpoint does not interfere with the default HTTP endpoint.</span></span>
    >
    >  <span data-ttu-id="66315-122">URL が "" である SOAP 以外のエンドポイントを追加すると、エンドポイント上の操作の呼び出しを行うときに予期しない動作が発生します。</span><span class="sxs-lookup"><span data-stu-id="66315-122">Adding a non-SOAP endpoint with a URL of "" causes unexpected behavior when an attempt is made to call an operation on the endpoint.</span></span> <span data-ttu-id="66315-123">これは、エンドポイントのリッスン URI が、ヘルプページ (WCF サービスのベースアドレスを参照するときに表示されるページ) と同じであるためです。</span><span class="sxs-lookup"><span data-stu-id="66315-123">The reason for this is the listen URI of the endpoint is the same as the URI for the help page (the page that is displayed when you browse to the base address of a WCF service).</span></span>

     <span data-ttu-id="66315-124">これを回避するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="66315-124">You can do one of the following actions to prevent this from happening:</span></span>

    - <span data-ttu-id="66315-125">SOAP 以外のエンドポイントについては、空ではない URI を指定するようにします。</span><span class="sxs-lookup"><span data-stu-id="66315-125">Always specify a non-blank URI for a non-SOAP endpoint.</span></span>

    - <span data-ttu-id="66315-126">ヘルプ ページを無効にします。</span><span class="sxs-lookup"><span data-stu-id="66315-126">Turn off the help page.</span></span> <span data-ttu-id="66315-127">これは、次のコードを使用して行うことができます。</span><span class="sxs-lookup"><span data-stu-id="66315-127">This can be done with the following code:</span></span>

     [!code-csharp[htBasicService#4](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#4)]
     [!code-vb[htBasicService#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#4)]

3. <span data-ttu-id="66315-128">サービス ホストを開き、ユーザーが Enter キーを押すのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="66315-128">Open the service host and wait until the user presses ENTER.</span></span>

     [!code-csharp[htBasicService#5](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/snippets.cs#5)]
     [!code-vb[htBasicService#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/snippets.vb#5)]

     <span data-ttu-id="66315-129">このサンプルでは、コンソール アプリケーションで Web スタイル サービスをホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="66315-129">This sample demonstrates how to host a Web-Style service with a console application.</span></span> <span data-ttu-id="66315-130">IIS からこのようなサービスをホストすることもできます。</span><span class="sxs-lookup"><span data-stu-id="66315-130">You can also host such a service within IIS.</span></span> <span data-ttu-id="66315-131">これを行うには、次のコードに示すように、.svc ファイルで <xref:System.ServiceModel.Activation.WebServiceHostFactory> クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="66315-131">To do this, specify the <xref:System.ServiceModel.Activation.WebServiceHostFactory> class in a .svc file as the following code demonstrates.</span></span>

    ```text
    <%ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Samples.Service"
        Factory=System.ServiceModel.Activation.WebServiceHostFactory%>
    ```

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="66315-132">Internet Explorer で GET にマッピングされたサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="66315-132">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="66315-133">Internet Explorer を開き、「 `http://localhost:8000/EchoWithGet?s=Hello, world!` 」と入力して、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="66315-133">Open Internet Explorer and type "`http://localhost:8000/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="66315-134">URL には、サービスのベースアドレス ( `http://localhost:8000/` )、エンドポイントの相対アドレス ("")、呼び出すサービス操作 ("EchoWithGet")、アンパサンド (&) で区切られた名前付きパラメーターのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="66315-134">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-in-code"></a><span data-ttu-id="66315-135">コードからサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="66315-135">To call service operations in code</span></span>

1. <span data-ttu-id="66315-136"><xref:System.ServiceModel.ChannelFactory%601> ブロック内で `using` のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="66315-136">Create an instance of <xref:System.ServiceModel.ChannelFactory%601> within a `using` block.</span></span>

     [!code-csharp[htBasicService#6](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#6)]
     [!code-vb[htBasicService#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#6)]

2. <span data-ttu-id="66315-137"><xref:System.ServiceModel.Description.WebHttpBehavior> が呼び出すエンドポイントに <xref:System.ServiceModel.ChannelFactory%601> を追加します。</span><span class="sxs-lookup"><span data-stu-id="66315-137">Add <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint the <xref:System.ServiceModel.ChannelFactory%601> calls.</span></span>

     [!code-csharp[htBasicService#7](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#7)]
     [!code-vb[htBasicService#7](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#7)]

3. <span data-ttu-id="66315-138">チャネルを作成し、サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="66315-138">Create the channel and call the service.</span></span>

     [!code-csharp[htBasicService#8](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#8)]
     [!code-vb[htBasicService#8](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#8)]

4. <span data-ttu-id="66315-139"><xref:System.ServiceModel.Web.WebServiceHost> を閉じます。</span><span class="sxs-lookup"><span data-stu-id="66315-139">Close the <xref:System.ServiceModel.Web.WebServiceHost>.</span></span>

     [!code-csharp[htBasicService#9](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#9)]
     [!code-vb[htBasicService#9](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#9)]

## <a name="example"></a><span data-ttu-id="66315-140">例</span><span class="sxs-lookup"><span data-stu-id="66315-140">Example</span></span>

<span data-ttu-id="66315-141">この例の完全なコードの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="66315-141">The following is the full code listing for this example.</span></span>

[!code-csharp[htBasicService#10](~/samples/snippets/csharp/VS_Snippets_CFX/htbasicservice/cs/service.cs#10)]
[!code-vb[htBasicService#10](~/samples/snippets/visualbasic/VS_Snippets_CFX/htbasicservice/vb/service.vb#10)]

## <a name="compiling-the-code"></a><span data-ttu-id="66315-142">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="66315-142">Compiling the code</span></span>

<span data-ttu-id="66315-143">Service.cs のコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll が参照されます。</span><span class="sxs-lookup"><span data-stu-id="66315-143">When compiling Service.cs reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="66315-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="66315-144">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="66315-145">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="66315-145">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
