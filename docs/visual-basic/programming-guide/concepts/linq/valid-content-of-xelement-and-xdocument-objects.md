---
title: XElement オブジェクトと XDocument オブジェクトの有効なコンテンツ 2
ms.date: 07/20/2015
ms.assetid: 400bb692-478a-40b6-ac1b-4ccbb4cbbd02
ms.openlocfilehash: d222f19f6f588968a3ef1515dca522a4a80e1ffb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364345"
---
# <a name="valid-content-of-xelement-and-xdocument-objects"></a><span data-ttu-id="4f850-102">XElement オブジェクトと XDocument オブジェクトの有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="4f850-102">Valid Content of XElement and XDocument Objects</span></span>
<span data-ttu-id="4f850-103">ここでは、コンストラクターやメソッドに渡すことができる有効な引数について説明します。これらのコンストラクターやメソッドは、コンテンツを要素やドキュメントに追加するためのものです。</span><span class="sxs-lookup"><span data-stu-id="4f850-103">This topic describes the valid arguments that can be passed to constructors and methods that you use to add content to elements and documents.</span></span>  
  
## <a name="valid-content"></a><span data-ttu-id="4f850-104">有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="4f850-104">Valid Content</span></span>  
 <span data-ttu-id="4f850-105">多くのクエリは、<xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> または <xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XAttribute> に評価されます。</span><span class="sxs-lookup"><span data-stu-id="4f850-105">Queries often evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement> or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="4f850-106"><xref:System.Xml.Linq.XElement> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトのコレクションを <xref:System.Xml.Linq.XElement> コンストラクターに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4f850-106">You can pass collections of <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> objects to the <xref:System.Xml.Linq.XElement> constructor.</span></span> <span data-ttu-id="4f850-107">したがって、XML ツリーの設定に使用するメソッドとコンストラクターに対して、クエリの結果をコンテンツとして渡すと便利です。</span><span class="sxs-lookup"><span data-stu-id="4f850-107">Therefore, it is convenient to pass the results of a query as content into methods and constructors that you use to populate XML trees.</span></span>  
  
 <span data-ttu-id="4f850-108">単純コンテンツを追加するときに、さまざまな型をこのメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4f850-108">When adding simple content, various types can be passed to this method.</span></span> <span data-ttu-id="4f850-109">有効な型は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4f850-109">Valid types include the following:</span></span>  
  
- <xref:System.String>  
  
- <xref:System.Double>  
  
- <xref:System.Single>  
  
- <xref:System.Decimal>  
  
- <xref:System.Boolean>  
  
- <xref:System.DateTime>  
  
- <xref:System.TimeSpan>  
  
- <xref:System.DateTimeOffset>  
  
- <span data-ttu-id="4f850-110">`Object.ToString` を実装する任意の型</span><span class="sxs-lookup"><span data-stu-id="4f850-110">Any type that implements `Object.ToString`.</span></span>  
  
- <span data-ttu-id="4f850-111"><xref:System.Collections.Generic.IEnumerable%601> を実装する任意の型</span><span class="sxs-lookup"><span data-stu-id="4f850-111">Any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
 <span data-ttu-id="4f850-112">複合コンテンツを追加するときは、次のような型をこのメソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="4f850-112">When adding complex content, various types can be passed to this method:</span></span>  
  
- <xref:System.Xml.Linq.XObject>  
  
- <xref:System.Xml.Linq.XNode>  
  
- <xref:System.Xml.Linq.XAttribute>  
  
- <span data-ttu-id="4f850-113"><xref:System.Collections.Generic.IEnumerable%601> を実装する任意の型</span><span class="sxs-lookup"><span data-stu-id="4f850-113">Any type that implements <xref:System.Collections.Generic.IEnumerable%601></span></span>  
  
 <span data-ttu-id="4f850-114">オブジェクトが <xref:System.Collections.Generic.IEnumerable%601> を実装している場合、オブジェクト内のコレクションが列挙され、コレクション内のすべての項目が追加されます。</span><span class="sxs-lookup"><span data-stu-id="4f850-114">If an object implements <xref:System.Collections.Generic.IEnumerable%601>, the collection in the object is enumerated, and all items in the collection are added.</span></span> <span data-ttu-id="4f850-115">コレクションに <xref:System.Xml.Linq.XNode> オブジェクトまたは <xref:System.Xml.Linq.XAttribute> オブジェクトが含まれている場合、コレクション内の各項目が個別に追加されます。</span><span class="sxs-lookup"><span data-stu-id="4f850-115">If the collection contains <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, each item in the collection is added separately.</span></span> <span data-ttu-id="4f850-116">コレクションにテキスト (またはテキストに変換されるオブジェクト) が含まれている場合、コレクション内のテキストが連結され、1 つのテキスト ノードとして追加されます。</span><span class="sxs-lookup"><span data-stu-id="4f850-116">If the collection contains text (or objects that are converted to text), the text in the collection is concatenated and added as a single text node.</span></span>  
  
 <span data-ttu-id="4f850-117">コンテンツが `null` の場合は、何も追加されません。</span><span class="sxs-lookup"><span data-stu-id="4f850-117">If content is `null`, nothing is added.</span></span> <span data-ttu-id="4f850-118">コレクションを渡すとき、コレクション内の項目は `null` にできます。</span><span class="sxs-lookup"><span data-stu-id="4f850-118">When passing a collection items in the collection can be `null`.</span></span> <span data-ttu-id="4f850-119">コレクション内の `null` 項目は、ツリーに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="4f850-119">A `null` item in the collection has no effect on the tree.</span></span>  
  
 <span data-ttu-id="4f850-120">追加する属性の名前は、そのコンテナー要素内で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="4f850-120">An added attribute must have a unique name within its containing element.</span></span>  
  
 <span data-ttu-id="4f850-121"><xref:System.Xml.Linq.XNode> オブジェクトや <xref:System.Xml.Linq.XAttribute> オブジェクトを追加するとき、新しいコンテンツに親がない場合、単にオブジェクトが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="4f850-121">When adding <xref:System.Xml.Linq.XNode> or <xref:System.Xml.Linq.XAttribute> objects, if the new content has no parent, then the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="4f850-122">新しいコンテンツに既に親があり、別の XML ツリーの一部となっている場合は、新しいコンテンツが複製され、新しく複製されたコンテンツが XML ツリーにアタッチされます。</span><span class="sxs-lookup"><span data-stu-id="4f850-122">If the new content already is parented and is part of another XML tree, then the new content is cloned, and the newly cloned content is attached to the XML tree.</span></span>  
  
## <a name="valid-content-for-documents"></a><span data-ttu-id="4f850-123">ドキュメントの有効なコンテンツ</span><span class="sxs-lookup"><span data-stu-id="4f850-123">Valid Content for Documents</span></span>  
 <span data-ttu-id="4f850-124">属性と単純コンテンツをドキュメントに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="4f850-124">Attributes and simple content cannot be added to a document.</span></span>  
  
 <span data-ttu-id="4f850-125"><xref:System.Xml.Linq.XDocument> の作成が必要となるシナリオは多くありません。</span><span class="sxs-lookup"><span data-stu-id="4f850-125">There are not many scenarios that require you to create an <xref:System.Xml.Linq.XDocument>.</span></span> <span data-ttu-id="4f850-126">通常、その代わりに <xref:System.Xml.Linq.XElement> ルート ノードを使用して XML ツリーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4f850-126">Instead, you can usually create your XML trees with an <xref:System.Xml.Linq.XElement> root node.</span></span> <span data-ttu-id="4f850-127">ドキュメントを作成する要件 (処理命令とコメントを最上位に作成する必要がある、ドキュメント型をサポートする必要がある、など) が特にない限り、<xref:System.Xml.Linq.XElement> をルート ノードとして使用する方が便利です。</span><span class="sxs-lookup"><span data-stu-id="4f850-127">Unless you have a specific requirement to create a document (for example, because you have to create processing instructions and comments at the top level, or you have to support document types), it is often more convenient to use <xref:System.Xml.Linq.XElement> as your root node.</span></span>  
  
 <span data-ttu-id="4f850-128">ドキュメントの有効なコンテンツは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4f850-128">Valid content for a document includes the following:</span></span>  
  
- <span data-ttu-id="4f850-129">0 個または 1 個の <xref:System.Xml.Linq.XDocumentType> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="4f850-129">Zero or one <xref:System.Xml.Linq.XDocumentType> objects.</span></span> <span data-ttu-id="4f850-130">ドキュメントの型は、要素の前に置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f850-130">The document types must come before the element.</span></span>  
  
- <span data-ttu-id="4f850-131">0 個または 1 個の要素。</span><span class="sxs-lookup"><span data-stu-id="4f850-131">Zero or one element.</span></span>  
  
- <span data-ttu-id="4f850-132">0 個以上のコメント。</span><span class="sxs-lookup"><span data-stu-id="4f850-132">Zero or more comments.</span></span>  
  
- <span data-ttu-id="4f850-133">0 個以上の処理命令。</span><span class="sxs-lookup"><span data-stu-id="4f850-133">Zero or more processing instructions.</span></span>  
  
- <span data-ttu-id="4f850-134">空白のみを含む、0 個以上のテキスト ノード。</span><span class="sxs-lookup"><span data-stu-id="4f850-134">Zero or more text nodes that contain only white space.</span></span>  
  
## <a name="constructors-and-functions-that-allow-adding-content"></a><span data-ttu-id="4f850-135">コンテンツの追加が可能なコンストラクターと関数</span><span class="sxs-lookup"><span data-stu-id="4f850-135">Constructors and Functions that Allow Adding Content</span></span>  
 <span data-ttu-id="4f850-136">次のメソッドを使用すると、<xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> に子コンテンツを追加できます。</span><span class="sxs-lookup"><span data-stu-id="4f850-136">The following methods allow you to add child content to an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XDocument>:</span></span>  
  
|<span data-ttu-id="4f850-137">メソッド</span><span class="sxs-lookup"><span data-stu-id="4f850-137">Method</span></span>|<span data-ttu-id="4f850-138">説明</span><span class="sxs-lookup"><span data-stu-id="4f850-138">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.%23ctor%2A>|<span data-ttu-id="4f850-139"><xref:System.Xml.Linq.XElement> を構築します。</span><span class="sxs-lookup"><span data-stu-id="4f850-139">Constructs an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XDocument.%23ctor%2A>|<span data-ttu-id="4f850-140"><xref:System.Xml.Linq.XDocument> を構築します。</span><span class="sxs-lookup"><span data-stu-id="4f850-140">Constructs a <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.Add%2A>|<span data-ttu-id="4f850-141"><xref:System.Xml.Linq.XElement> または <xref:System.Xml.Linq.XDocument> の子コンテンツの末尾に追加します。</span><span class="sxs-lookup"><span data-stu-id="4f850-141">Adds to the end of the child content of the <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddAfterSelf%2A>|<span data-ttu-id="4f850-142"><xref:System.Xml.Linq.XNode> の後にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f850-142">Adds content after the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XNode.AddBeforeSelf%2A>|<span data-ttu-id="4f850-143"><xref:System.Xml.Linq.XNode> の前にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f850-143">Adds content before the <xref:System.Xml.Linq.XNode>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.AddFirst%2A>|<span data-ttu-id="4f850-144"><xref:System.Xml.Linq.XContainer> の子コンテンツの冒頭にコンテンツを追加します。</span><span class="sxs-lookup"><span data-stu-id="4f850-144">Adds content at the beginning of the child content of the <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A>|<span data-ttu-id="4f850-145"><xref:System.Xml.Linq.XElement> のすべてのコンテンツ (子ノードおよび属性) を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4f850-145">Replaces all content (child nodes and attributes) of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A>|<span data-ttu-id="4f850-146"><xref:System.Xml.Linq.XElement> の属性を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4f850-146">Replaces the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A>|<span data-ttu-id="4f850-147">子ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4f850-147">Replaces the children nodes with new content.</span></span>|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A>|<span data-ttu-id="4f850-148">ノードを新しいコンテンツに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="4f850-148">Replaces a node with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f850-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f850-149">See also</span></span>

- [<span data-ttu-id="4f850-150">XML ツリーの作成 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f850-150">Creating XML Trees (Visual Basic)</span></span>](creating-xml-trees.md)
