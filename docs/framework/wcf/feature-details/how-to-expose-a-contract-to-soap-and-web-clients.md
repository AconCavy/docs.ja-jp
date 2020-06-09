---
title: '方法: コントラクトを SOAP クライアントおよび Web クライアントに公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: bb765a48-12f2-430d-a54d-6f0c20f2a23a
ms.openlocfilehash: fa02260976c710401a05cce3d723cc0f66804c6e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593134"
---
# <a name="how-to-expose-a-contract-to-soap-and-web-clients"></a><span data-ttu-id="bd838-102">方法: コントラクトを SOAP クライアントおよび Web クライアントに公開する</span><span class="sxs-lookup"><span data-stu-id="bd838-102">How to: Expose a Contract to SOAP and Web Clients</span></span>

<span data-ttu-id="bd838-103">既定では、Windows Communication Foundation (WCF) は、エンドポイントを SOAP クライアントのみに使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bd838-103">By default, Windows Communication Foundation (WCF) makes endpoints available only to SOAP clients.</span></span> <span data-ttu-id="bd838-104">[「方法: 基本的な WCF WEB HTTP サービスを作成](how-to-create-a-basic-wcf-web-http-service.md)する」では、SOAP 以外のクライアントがエンドポイントを使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="bd838-104">In [How to: Create a Basic WCF Web HTTP Service](how-to-create-a-basic-wcf-web-http-service.md), an endpoint is made available to non-SOAP clients.</span></span> <span data-ttu-id="bd838-105">状況によっては、同じコントラクトを Web エンドポイントと SOAP エンドポイントのどちらとしても利用できることが望ましい場合があります。</span><span class="sxs-lookup"><span data-stu-id="bd838-105">There may be times when you want to make the same contract available both ways, as a Web endpoint and as a SOAP endpoint.</span></span> <span data-ttu-id="bd838-106">ここでは、これを実現する方法の例について示します。</span><span class="sxs-lookup"><span data-stu-id="bd838-106">This topic shows an example of how to do this.</span></span>

## <a name="to-define-the-service-contract"></a><span data-ttu-id="bd838-107">サービス コントラクトを定義するには</span><span class="sxs-lookup"><span data-stu-id="bd838-107">To define the service contract</span></span>

1. <span data-ttu-id="bd838-108"><xref:System.ServiceModel.ServiceContractAttribute> <xref:System.ServiceModel.Web.WebInvokeAttribute> 次のコードに示すように、、、および属性でマークされたインターフェイスを使用して、サービスコントラクトを定義し <xref:System.ServiceModel.Web.WebGetAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="bd838-108">Define a service contract using an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.Web.WebInvokeAttribute> and the <xref:System.ServiceModel.Web.WebGetAttribute> attributes, as shown in the following code:</span></span>

    [!code-csharp[htSoapWeb#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#0)]
    [!code-vb[htSoapWeb#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#0)]

    > [!NOTE]
    > <span data-ttu-id="bd838-109">既定では、<xref:System.ServiceModel.Web.WebInvokeAttribute> は POST 呼び出しを操作にマッピングします。</span><span class="sxs-lookup"><span data-stu-id="bd838-109">By default <xref:System.ServiceModel.Web.WebInvokeAttribute> maps POST calls to the operation.</span></span> <span data-ttu-id="bd838-110">ただし、"method=" パラメーターを指定することで、操作にマッピングするメソッドを指定できます。</span><span class="sxs-lookup"><span data-stu-id="bd838-110">You can, however, specify the method to map to the operation by specifying a "method=" parameter.</span></span> <span data-ttu-id="bd838-111"><xref:System.ServiceModel.Web.WebGetAttribute> には "method=" パラメーターがないため、サービス操作には GET 呼び出しのみがマッピングされます。</span><span class="sxs-lookup"><span data-stu-id="bd838-111"><xref:System.ServiceModel.Web.WebGetAttribute> does not have a "method=" parameter and only maps GET calls to the service operation.</span></span>

2. <span data-ttu-id="bd838-112">次のコードに示すように、サービスコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="bd838-112">Implement the service contract, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#1)]
     [!code-vb[htSoapWeb#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#1)]

## <a name="to-host-the-service"></a><span data-ttu-id="bd838-113">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="bd838-113">To host the service</span></span>

1. <span data-ttu-id="bd838-114">次の <xref:System.ServiceModel.ServiceHost> コードに示すように、オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="bd838-114">Create a <xref:System.ServiceModel.ServiceHost> object, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#2)]
     [!code-vb[htSoapWeb#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#2)]

2. <span data-ttu-id="bd838-115">次の <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.BasicHttpBinding> コードに示すように、SOAP エンドポイントに対してを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd838-115">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.BasicHttpBinding> for the SOAP endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#3)]
     [!code-vb[htSoapWeb#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#3)]

3. <span data-ttu-id="bd838-116">次の <xref:System.ServiceModel.Description.ServiceEndpoint> <xref:System.ServiceModel.WebHttpBinding> コードに示すように、SOAP 以外のエンドポイントに対してを追加し、 <xref:System.ServiceModel.Description.WebHttpBehavior> エンドポイントにを追加します。</span><span class="sxs-lookup"><span data-stu-id="bd838-116">Add a <xref:System.ServiceModel.Description.ServiceEndpoint> with <xref:System.ServiceModel.WebHttpBinding> for the non-SOAP endpoint and add the <xref:System.ServiceModel.Description.WebHttpBehavior> to the endpoint, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#4)]
     [!code-vb[htSoapWeb#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#4)]

4. <span data-ttu-id="bd838-117">`Open()` <xref:System.ServiceModel.ServiceHost> 次のコードに示すように、インスタンスでを呼び出して、サービスホストを開きます。</span><span class="sxs-lookup"><span data-stu-id="bd838-117">Call `Open()` on a <xref:System.ServiceModel.ServiceHost> instance to open the service host, as shown in the following code:</span></span>

     [!code-csharp[htSoapWeb#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#5)]
     [!code-vb[htSoapWeb#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#5)]

## <a name="to-call-service-operations-mapped-to-get-in-internet-explorer"></a><span data-ttu-id="bd838-118">Internet Explorer で GET にマッピングされたサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="bd838-118">To call service operations mapped to GET in Internet Explorer</span></span>

1. <span data-ttu-id="bd838-119">Internet Explorer を開き、「 `http://localhost:8000/Web/EchoWithGet?s=Hello, world!` 」と入力して、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="bd838-119">Open Internet Explorer and type "`http://localhost:8000/Web/EchoWithGet?s=Hello, world!`" and press ENTER.</span></span> <span data-ttu-id="bd838-120">URL には、サービスのベースアドレス ( `http://localhost:8000/` )、エンドポイントの相対アドレス ("")、呼び出すサービス操作 ("EchoWithGet")、アンパサンド (&) で区切られた名前付きパラメーターのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bd838-120">The URL contains the base address of the service (`http://localhost:8000/`), the relative address of the endpoint (""), the service operation to call ("EchoWithGet"), and a question mark followed by a list of named parameters separated by an ampersand (&).</span></span>

## <a name="to-call-service-operations-on-the-web-endpoint-in-code"></a><span data-ttu-id="bd838-121">コードから Web エンドポイントにあるサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="bd838-121">To call service operations on the Web endpoint in code</span></span>

1. <span data-ttu-id="bd838-122">次のコードに示すように、<xref:System.ServiceModel.Web.WebChannelFactory%601> のインスタンスを `using` ブロック内に作成します。</span><span class="sxs-lookup"><span data-stu-id="bd838-122">Create an instance of <xref:System.ServiceModel.Web.WebChannelFactory%601> within a `using` block, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#6)]
     [!code-vb[htSoapWeb#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#6)]

> [!NOTE]
> <span data-ttu-id="bd838-123">`Close()` は `using` ブロックの末尾のチャネルで自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="bd838-123">`Close()` is automatically called on the channel at the end of the `using` block.</span></span>

1. <span data-ttu-id="bd838-124">次のコードに示すように、チャネルを作成してサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bd838-124">Create the channel and call the service, as shown in the following code.</span></span>

     [!code-csharp[htSoapWeb#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#8)]
     [!code-vb[htSoapWeb#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#8)]

## <a name="to-call-service-operations-on-the-soap-endpoint"></a><span data-ttu-id="bd838-125">SOAP エンドポイントにあるサービス操作を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="bd838-125">To call service operations on the SOAP endpoint</span></span>

1. <span data-ttu-id="bd838-126">次のコードに示すように、<xref:System.ServiceModel.ChannelFactory> のインスタンスを `using` ブロック内に作成します。</span><span class="sxs-lookup"><span data-stu-id="bd838-126">Create an instance of <xref:System.ServiceModel.ChannelFactory> within a `using` block, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#10)]
    [!code-vb[htSoapWeb#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#10)]

2. <span data-ttu-id="bd838-127">次のコードに示すように、チャネルを作成してサービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="bd838-127">Create the channel and call the service, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#11)]
    [!code-vb[htSoapWeb#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#11)]

## <a name="to-close-the-service-host"></a><span data-ttu-id="bd838-128">サービス ホストを閉じるは</span><span class="sxs-lookup"><span data-stu-id="bd838-128">To close the service host</span></span>

1. <span data-ttu-id="bd838-129">次のコードに示すように、サービス ホストを閉じます。</span><span class="sxs-lookup"><span data-stu-id="bd838-129">Close the service host, as shown in the following code.</span></span>

    [!code-csharp[htSoapWeb#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#9)]
    [!code-vb[htSoapWeb#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#9)]

## <a name="example"></a><span data-ttu-id="bd838-130">例</span><span class="sxs-lookup"><span data-stu-id="bd838-130">Example</span></span>

<span data-ttu-id="bd838-131">このトピックの完全なコードリストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bd838-131">The following is the full code listing for this topic:</span></span>

[!code-csharp[htSoapWeb#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/htsoapweb/cs/program.cs#13)]
[!code-vb[htSoapWeb#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htsoapweb/vb/program.vb#13)]

## <a name="compiling-the-code"></a><span data-ttu-id="bd838-132">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="bd838-132">Compiling the code</span></span>

 <span data-ttu-id="bd838-133">Service.cs のコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll を参照します。</span><span class="sxs-lookup"><span data-stu-id="bd838-133">When compiling Service.cs, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd838-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="bd838-134">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Web.WebServiceHost>
- <xref:System.ServiceModel.ChannelFactory>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- [<span data-ttu-id="bd838-135">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="bd838-135">WCF Web HTTP Programming Model</span></span>](wcf-web-http-programming-model.md)
