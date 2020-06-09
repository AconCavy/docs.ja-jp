---
title: '方法: Atom および RSS の両方としてフィードを公開する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fe374932-67f5-487d-9325-f868812b92e4
ms.openlocfilehash: e4ce1fa7b494c2317a1bddc57ee6b150c84b9a96
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593147"
---
# <a name="how-to-expose-a-feed-as-both-atom-and-rss"></a><span data-ttu-id="9705a-102">方法: Atom および RSS の両方としてフィードを公開する</span><span class="sxs-lookup"><span data-stu-id="9705a-102">How to: Expose a Feed as Both Atom and RSS</span></span>
<span data-ttu-id="9705a-103">Windows Communication Foundation (WCF) を使用すると、配信フィードを公開するサービスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9705a-103">Windows Communication Foundation (WCF) allows you to create a service that exposes a syndication feed.</span></span> <span data-ttu-id="9705a-104">このトピックでは、Atom 1.0 と RSS 2.0 の両方を使用して配信フィードを公開する配信サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9705a-104">This topic discusses how to create a syndication service that exposes a syndication feed using both Atom 1.0 and RSS 2.0.</span></span> <span data-ttu-id="9705a-105">このサービスは、どちらかの配信フォーマットを返すエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="9705a-105">This service exposes one endpoint that can return either syndication format.</span></span> <span data-ttu-id="9705a-106">簡略化のため、この例で使用するサービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="9705a-106">For simplicity the service used in this sample is self hosted.</span></span> <span data-ttu-id="9705a-107">運用環境では、このタイプのサービスは IIS または WAS でホストされます。</span><span class="sxs-lookup"><span data-stu-id="9705a-107">In a production environment a service of this type would be hosted under IIS or WAS.</span></span> <span data-ttu-id="9705a-108">さまざまな WCF ホスティングオプションの詳細については、「[ホスティング](hosting.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9705a-108">For more information about the different WCF hosting options, see [Hosting](hosting.md).</span></span>  
  
### <a name="to-create-a-basic-syndication-service"></a><span data-ttu-id="9705a-109">基本的な配信サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="9705a-109">To create a basic syndication service</span></span>  
  
1. <span data-ttu-id="9705a-110"><xref:System.ServiceModel.Web.WebGetAttribute> 属性でマークされたインターフェイスを使用して、サービス コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="9705a-110">Define a service contract using an interface marked with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute.</span></span> <span data-ttu-id="9705a-111">配信フィードとして公開される各操作は、<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="9705a-111">Each operation that is exposed as a syndication feed returns a <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> object.</span></span> <span data-ttu-id="9705a-112"><xref:System.ServiceModel.Web.WebGetAttribute> のパラメーターに注意してください。</span><span class="sxs-lookup"><span data-stu-id="9705a-112">Note the parameters for the <xref:System.ServiceModel.Web.WebGetAttribute>.</span></span> <span data-ttu-id="9705a-113">`UriTemplate` は、このサービス操作を呼び出すために使用される URL を指定します。</span><span class="sxs-lookup"><span data-stu-id="9705a-113">`UriTemplate` specifies the URL used to invoke this service operation.</span></span> <span data-ttu-id="9705a-114">このパラメーターの文字列には、リテラルと変数が中かっこ ({*format*}) で格納されています。</span><span class="sxs-lookup"><span data-stu-id="9705a-114">The string for this parameter contains literals and a variable in braces ({*format*}).</span></span> <span data-ttu-id="9705a-115">この変数は、サービス操作の `format` パラメーターに対応します。</span><span class="sxs-lookup"><span data-stu-id="9705a-115">This variable corresponds to the service operation's `format` parameter.</span></span> <span data-ttu-id="9705a-116">詳細については、「<xref:System.UriTemplate>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9705a-116">For more information, see <xref:System.UriTemplate>.</span></span> <span data-ttu-id="9705a-117">`BodyStyle` は、このサービス操作が送受信するメッセージの書き方に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="9705a-117">`BodyStyle` affects how the messages that this service operation sends and receives are written.</span></span> <span data-ttu-id="9705a-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> は、このサービス操作に送受信されるデータが、インフラストラクチャにより定義された XML 要素でラップされないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="9705a-118"><xref:System.ServiceModel.Web.WebMessageBodyStyle.Bare> specifies that the data sent to and from this service operation are not wrapped by infrastructure-defined XML elements.</span></span> <span data-ttu-id="9705a-119">詳細については、「<xref:System.ServiceModel.Web.WebMessageBodyStyle>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9705a-119">For more information, see <xref:System.ServiceModel.Web.WebMessageBodyStyle>.</span></span>  
  
     [!code-csharp[htAtomRss#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#0)]
     [!code-vb[htAtomRss#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#0)]  
  
    > [!NOTE]
    > <span data-ttu-id="9705a-120">このインターフェイスのサービス操作により返される型を指定するには、<xref:System.ServiceModel.ServiceKnownTypeAttribute> を使用します。</span><span class="sxs-lookup"><span data-stu-id="9705a-120">Use the <xref:System.ServiceModel.ServiceKnownTypeAttribute> to specify the types that are returned by the service operations in this interface.</span></span>  
  
2. <span data-ttu-id="9705a-121">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="9705a-121">Implement the service contract.</span></span>  
  
     [!code-csharp[htAtomRss#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#1)]
     [!code-vb[htAtomRss#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#1)]  
  
3. <span data-ttu-id="9705a-122"><xref:System.ServiceModel.Syndication.SyndicationFeed> オブジェクトを作成し、作成者、カテゴリ、および説明を追加します。</span><span class="sxs-lookup"><span data-stu-id="9705a-122">Create a <xref:System.ServiceModel.Syndication.SyndicationFeed> object and add an author, category, and description.</span></span>  
  
     [!code-csharp[htAtomRss#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#2)]
     [!code-vb[htAtomRss#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#2)]  
  
4. <span data-ttu-id="9705a-123">複数の <xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9705a-123">Create several <xref:System.ServiceModel.Syndication.SyndicationItem> objects.</span></span>  
  
     [!code-csharp[htAtomRss#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#3)]
     [!code-vb[htAtomRss#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#3)]  
  
5. <span data-ttu-id="9705a-124"><xref:System.ServiceModel.Syndication.SyndicationItem> オブジェクトをフィードに追加します。</span><span class="sxs-lookup"><span data-stu-id="9705a-124">Add the <xref:System.ServiceModel.Syndication.SyndicationItem> objects to the feed.</span></span>  
  
     [!code-csharp[htAtomRss#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#4)]
     [!code-vb[htAtomRss#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#4)]  
  
6. <span data-ttu-id="9705a-125">format パラメーターを使用して、要求された形式を返します。</span><span class="sxs-lookup"><span data-stu-id="9705a-125">Use the format parameter to return the requested format.</span></span>  
  
     [!code-csharp[htAtomRss#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#5)]
     [!code-vb[htAtomRss#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#5)]  
  
### <a name="to-host-the-service"></a><span data-ttu-id="9705a-126">サービスをホストするには</span><span class="sxs-lookup"><span data-stu-id="9705a-126">To host the service</span></span>  
  
1. <span data-ttu-id="9705a-127"><xref:System.ServiceModel.Web.WebServiceHost> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9705a-127">Create a <xref:System.ServiceModel.Web.WebServiceHost> object.</span></span> <span data-ttu-id="9705a-128"><xref:System.ServiceModel.Web.WebServiceHost> クラスは、エンドポイントがコードまたは構成で指定されない限り、自動的にエンドポイントをサービスのベース アドレスで追加します。</span><span class="sxs-lookup"><span data-stu-id="9705a-128">The <xref:System.ServiceModel.Web.WebServiceHost> class automatically adds an endpoint at the service's base address unless one is specified in code or configuration.</span></span> <span data-ttu-id="9705a-129">次の例は、既定のエンドポイントが公開されるので、エンドポイントは指定されません。</span><span class="sxs-lookup"><span data-stu-id="9705a-129">In this sample, no endpoints are specified so the default endpoint is exposed.</span></span>  
  
     [!code-csharp[htAtomRss#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#6)]
     [!code-vb[htAtomRss#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#6)]  
  
2. <span data-ttu-id="9705a-130">サービス ホストを開き、サービスからフィードを読み込み、フィードを表示してから、ユーザーが Enter キーを押すのを待ちます。</span><span class="sxs-lookup"><span data-stu-id="9705a-130">Open the service host, load the feed from the service, display the feed, and wait for the user to press ENTER.</span></span>  
  
     [!code-csharp[htAtomRss#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#8)]
     [!code-vb[htAtomRss#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/program.vb#8)]  
  
### <a name="to-call-getblog-with-an-http-get"></a><span data-ttu-id="9705a-131">HTTP GET を使用して GetBlog を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="9705a-131">To call GetBlog with an HTTP GET</span></span>  
  
1. <span data-ttu-id="9705a-132">Internet Explorer を開き、次の URL を入力して、enter キーを押します `http://localhost:8000/BlogService/GetBlog` 。</span><span class="sxs-lookup"><span data-stu-id="9705a-132">Open Internet Explorer, type the following URL, and press ENTER: `http://localhost:8000/BlogService/GetBlog`.</span></span>
  
     <span data-ttu-id="9705a-133">URL には、サービスのベースアドレス ( `http://localhost:8000/BlogService` )、エンドポイントの相対アドレス、および呼び出すサービス操作が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9705a-133">The URL contains the base address of the service (`http://localhost:8000/BlogService`), the relative address of the endpoint, and the service operation to call.</span></span>  
  
### <a name="to-call-getblog-from-code"></a><span data-ttu-id="9705a-134">コードから GetBlog() を呼び出すには</span><span class="sxs-lookup"><span data-stu-id="9705a-134">To call GetBlog() from code</span></span>  
  
1. <span data-ttu-id="9705a-135">ベース アドレスと呼び出すメソッドを使用して <xref:System.Xml.XmlReader> を作成します。</span><span class="sxs-lookup"><span data-stu-id="9705a-135">Create an <xref:System.Xml.XmlReader> with the base address and the method you are calling.</span></span>  
  
     [!code-csharp[htAtomRss#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#9)]
     [!code-vb[htAtomRss#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#9)]  
  
2. <span data-ttu-id="9705a-136">静的な <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> メソッドを呼び出し、作成した <xref:System.Xml.XmlReader> を渡します。</span><span class="sxs-lookup"><span data-stu-id="9705a-136">Call the static <xref:System.ServiceModel.Syndication.SyndicationFeed.Load%28System.Xml.XmlReader%29> method, passing in the <xref:System.Xml.XmlReader> you just created.</span></span>  
  
     [!code-csharp[htAtomRss#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#10)]
     [!code-vb[htAtomRss#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#10)]  
  
     <span data-ttu-id="9705a-137">これにより、サービス操作が呼び出され、サービス操作から返されたフォーマッタが新しい <xref:System.ServiceModel.Syndication.SyndicationFeed> に設定されます。</span><span class="sxs-lookup"><span data-stu-id="9705a-137">This invokes the service operation and populates a new <xref:System.ServiceModel.Syndication.SyndicationFeed> with the formatter returned from the service operation.</span></span>  
  
3. <span data-ttu-id="9705a-138">フィード オブジェクトにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="9705a-138">Access the feed object.</span></span>  
  
     [!code-csharp[htAtomRss#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/snippets.cs#11)]
     [!code-vb[htAtomRss#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/htatomrss/vb/snippets.vb#11)]  
  
## <a name="example"></a><span data-ttu-id="9705a-139">例</span><span class="sxs-lookup"><span data-stu-id="9705a-139">Example</span></span>  
 <span data-ttu-id="9705a-140">この例の完全なコードの一覧を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="9705a-140">The following is the full code listing for this example.</span></span>  
  
 [!code-csharp[htAtomRss#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/htatomrss/cs/program.cs#12)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9705a-141">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9705a-141">Compiling the Code</span></span>  
 <span data-ttu-id="9705a-142">上記のコードのコンパイル時には、System.ServiceModel.dll と System.ServiceModel.Web.dll が参照されます。</span><span class="sxs-lookup"><span data-stu-id="9705a-142">When compiling the preceding code, reference System.ServiceModel.dll and System.ServiceModel.Web.dll.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9705a-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="9705a-143">See also</span></span>

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
