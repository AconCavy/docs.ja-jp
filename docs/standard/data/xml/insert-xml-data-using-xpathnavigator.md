---
title: XPathNavigator による XML データの挿入
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 2ed8c28b-b88d-4be7-9c87-92df01f0821f
ms.openlocfilehash: 68c003467d837fe79d5e275968e47fa5dc3490cc
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710727"
---
# <a name="insert-xml-data-using-xpathnavigator"></a><span data-ttu-id="e5702-102">XPathNavigator による XML データの挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-102">Insert XML Data using XPathNavigator</span></span>
<span data-ttu-id="e5702-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、XML ドキュメント内に兄弟ノード、子ノード、および属性ノードを挿入するためのメソッドのセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="e5702-103">The <xref:System.Xml.XPath.XPathNavigator> class provides a set of methods used to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="e5702-104">これらのメソッドを使用するには、<xref:System.Xml.XPath.XPathNavigator> オブジェクトが編集可能である必要があります。つまり、その <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> プロパティを `true` にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e5702-104">In order to use these methods, the <xref:System.Xml.XPath.XPathNavigator> object must be editable, that is, its <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> property must be `true`.</span></span>  
  
 <span data-ttu-id="e5702-105">XML ドキュメントを編集できる <xref:System.Xml.XPath.XPathNavigator> オブジェクトは、<xref:System.Xml.XmlDocument.CreateNavigator%2A> クラスの <xref:System.Xml.XmlDocument> メソッドによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-105"><xref:System.Xml.XPath.XPathNavigator> objects that can edit an XML document are created by the <xref:System.Xml.XmlDocument.CreateNavigator%2A> method of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="e5702-106"><xref:System.Xml.XPath.XPathNavigator> クラスによって作成される <xref:System.Xml.XPath.XPathDocument> オブジェクトは読み取り専用であり、<xref:System.Xml.XPath.XPathNavigator> オブジェクトによって作成される <xref:System.Xml.XPath.XPathDocument> オブジェクトの編集メソッドを使用しようとすると、<xref:System.NotSupportedException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="e5702-106"><xref:System.Xml.XPath.XPathNavigator> objects created by the <xref:System.Xml.XPath.XPathDocument> class are read-only and any attempt to use the editing methods of an <xref:System.Xml.XPath.XPathNavigator> object created by an <xref:System.Xml.XPath.XPathDocument> object results in a <xref:System.NotSupportedException>.</span></span>  
  
 <span data-ttu-id="e5702-107">編集可能な <xref:System.Xml.XPath.XPathNavigator> オブジェクトの作成方法については、「[XPathDocument および XmlDocument を使用した XML データの読み取り](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5702-107">For more information about creating editable <xref:System.Xml.XPath.XPathNavigator> objects, see [Reading XML Data using XPathDocument and XmlDocument](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).</span></span>  
  
## <a name="inserting-nodes"></a><span data-ttu-id="e5702-108">ノードの挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-108">Inserting Nodes</span></span>  
 <span data-ttu-id="e5702-109"><xref:System.Xml.XPath.XPathNavigator> クラスは、XML ドキュメント内に兄弟ノード、子ノード、および属性ノードを挿入するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e5702-109">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to insert sibling, child, and attribute nodes in an XML document.</span></span> <span data-ttu-id="e5702-110">これらのメソッドによって、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置に関連した異なる場所にノードまたは属性を挿入できます。これらのメソッドについて以下に説明します。</span><span class="sxs-lookup"><span data-stu-id="e5702-110">These methods allow you to insert nodes and attributes in different locations in relation to the current position of an <xref:System.Xml.XPath.XPathNavigator> object and are described in the following sections.</span></span>  
  
### <a name="inserting-sibling-nodes"></a><span data-ttu-id="e5702-111">兄弟ノードの挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-111">Inserting Sibling Nodes</span></span>  
 <span data-ttu-id="e5702-112"><xref:System.Xml.XPath.XPathNavigator> クラスは、兄弟ノードを挿入する次のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e5702-112">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert sibling nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A>  
  
 <span data-ttu-id="e5702-113">これらのメソッドは <xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にあるノードの前と後に兄弟ノードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="e5702-113">These methods insert sibling nodes before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="e5702-114"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> および <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> メソッドは、オーバーロードされ、`string`、<xref:System.Xml.XmlReader> オブジェクト、または追加する兄弟ノードをパラメーターとして含む <xref:System.Xml.XPath.XPathNavigator> オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e5702-114">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> methods are overloaded and accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the sibling node to add as parameters.</span></span> <span data-ttu-id="e5702-115">両方のメソッドは、兄弟ノードの挿入に使用される <xref:System.Xml.XmlWriter> オブジェクトも返します。</span><span class="sxs-lookup"><span data-stu-id="e5702-115">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert sibling nodes.</span></span>  
  
 <span data-ttu-id="e5702-116"><xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> および <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> メソッドは、パラメーターとして指定された名前空間プレフィックス、ローカル名、名前空間 URI、および値を使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にあるノードの前と後に、1 つの兄弟ノードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="e5702-116">The <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods insert a single sibling node before and after the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="e5702-117">次の例では、新しい `pages` 要素が `price` ファイル内の最初の `book` 要素の `contosoBooks.xml` 子要素の前に挿入されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-117">In the following example a new `pages` element is inserted before the `price` child element of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#19](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#19)]
 [!code-csharp[XPathNavigatorMethods#19](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#19)]
 [!code-vb[XPathNavigatorMethods#19](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#19)]  
  
 <span data-ttu-id="e5702-118">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e5702-118">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="e5702-119"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A>、および <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> メソッドの詳細については、<xref:System.Xml.XPath.XPathNavigator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5702-119">For more information about the <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertElementAfter%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertElementBefore%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-child-nodes"></a><span data-ttu-id="e5702-120">子ノードの挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-120">Inserting Child Nodes</span></span>  
 <span data-ttu-id="e5702-121"><xref:System.Xml.XPath.XPathNavigator> クラスは、子ノードを挿入する次のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e5702-121">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert child nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A>  
  
 <span data-ttu-id="e5702-122">これらのメソッドは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にあるノードの一連の子ノードの最後と最初に、子ノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e5702-122">These methods append and prepend child nodes to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="e5702-123">「兄弟ノードの挿入」のメソッドと同様、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> および <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> メソッドは、`string`、<xref:System.Xml.XmlReader> オブジェクト、または追加する子ノードをパラメーターとして含む <xref:System.Xml.XPath.XPathNavigator> オブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e5702-123">Like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods accept a `string`, <xref:System.Xml.XmlReader> object, or <xref:System.Xml.XPath.XPathNavigator> object containing the child node to add as parameters.</span></span> <span data-ttu-id="e5702-124">両方のメソッドは、子ノードの挿入に使用される <xref:System.Xml.XmlWriter> オブジェクトも返します。</span><span class="sxs-lookup"><span data-stu-id="e5702-124">Both methods also return an <xref:System.Xml.XmlWriter> object used to insert child nodes.</span></span>  
  
 <span data-ttu-id="e5702-125">また、「兄弟ノードの挿入」のメソッドと同様、<xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> および <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> メソッドは、パラメーターとして指定された名前空間プレフィックス、ローカル名、名前空間 URI、および値を使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にあるノードの一連の子ノードの最初と最後に 1 つの子ノードを追加します。</span><span class="sxs-lookup"><span data-stu-id="e5702-125">Also like the methods in the "Inserting Sibling Nodes" section, the <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods insert a single child node to the end of and the beginning of the list of child nodes of the node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span>  
  
 <span data-ttu-id="e5702-126">次の例では、新しい `pages` 子要素が `book` ファイル内の最初の `contosoBooks.xml` 要素の一連の子要素に追加されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-126">In the following example, a new `pages` child element is appended to the list of child elements of the first `book` element in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#2](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#2)]
 [!code-csharp[XPathNavigatorMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#2)]
 [!code-vb[XPathNavigatorMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#2)]  
  
 <span data-ttu-id="e5702-127">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e5702-127">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="e5702-128"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A>、および <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> メソッドの詳細については、<xref:System.Xml.XPath.XPathNavigator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5702-128">For more information about the <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChildElement%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChildElement%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
### <a name="inserting-attribute-nodes"></a><span data-ttu-id="e5702-129">属性ノードの挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-129">Inserting Attribute Nodes</span></span>  
 <span data-ttu-id="e5702-130"><xref:System.Xml.XPath.XPathNavigator> クラスは、属性ノードを挿入する次のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="e5702-130">The <xref:System.Xml.XPath.XPathNavigator> class provides the following methods to insert attribute nodes.</span></span>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>  
  
 <span data-ttu-id="e5702-131">これらのメソッドは <xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある要素ノードに属性ノードを挿入します。</span><span class="sxs-lookup"><span data-stu-id="e5702-131">These methods insert attribute nodes on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="e5702-132"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> メソッドは、パラメーターとして指定された名前空間プレフィックス、ローカル名、名前空間 URI、および値を使用して <xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある要素ノードに、属性ノードを作成します。</span><span class="sxs-lookup"><span data-stu-id="e5702-132">The <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> method creates an attribute node on the element node an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on using the namespace prefix, local name, namespace URI, and value specified as parameters.</span></span> <span data-ttu-id="e5702-133"><xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> メソッドは、属性ノードの挿入に使用される <xref:System.Xml.XmlWriter> オブジェクトも返します。</span><span class="sxs-lookup"><span data-stu-id="e5702-133">The <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method returns an <xref:System.Xml.XmlWriter> object used to insert attribute nodes.</span></span>  
  
 <span data-ttu-id="e5702-134">次の例では、`discount` メソッドから返された `currency` オブジェクトを使用して、新しい `price` および `book` 属性が `contosoBooks.xml` ファイル内の最初の <xref:System.Xml.XmlWriter> 要素の <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> 子要素に作成されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-134">In the following example, new `discount` and `currency` attributes are created on the `price` child element of the first `book` element in the `contosoBooks.xml` file using the <xref:System.Xml.XmlWriter> object returned from the <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> method.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#8](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#8)]
 [!code-csharp[XPathNavigatorMethods#8](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#8)]
 [!code-vb[XPathNavigatorMethods#8](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#8)]  
  
 <span data-ttu-id="e5702-135">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e5702-135">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="e5702-136"><xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> および <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> メソッドの詳細については、<xref:System.Xml.XPath.XPathNavigator> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5702-136">For more information about the <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods, see the <xref:System.Xml.XPath.XPathNavigator> class reference documentation.</span></span>  
  
## <a name="copying-nodes"></a><span data-ttu-id="e5702-137">ノードのコピー</span><span class="sxs-lookup"><span data-stu-id="e5702-137">Copying Nodes</span></span>  
 <span data-ttu-id="e5702-138">別の XML ドキュメントの内容を使用して XML ドキュメントを作成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="e5702-138">In certain cases you may want to populate an XML document with the contents from another XML document.</span></span> <span data-ttu-id="e5702-139"><xref:System.Xml.XPath.XPathNavigator> クラスおよび <xref:System.Xml.XmlWriter> クラスは、既存の <xref:System.Xml.XmlDocument> オブジェクトまたは <xref:System.Xml.XmlReader> オブジェクトから <xref:System.Xml.XPath.XPathNavigator> オブジェクトへノードをコピーできます。</span><span class="sxs-lookup"><span data-stu-id="e5702-139">Both the <xref:System.Xml.XPath.XPathNavigator> class and the <xref:System.Xml.XmlWriter> class can copy nodes to an <xref:System.Xml.XmlDocument> object from an existing <xref:System.Xml.XmlReader> object or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="e5702-140"><xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、および <xref:System.Xml.XPath.XPathNavigator> メソッドにはすべて、パラメーターとして <xref:System.Xml.XPath.XPathNavigator> オブジェクトまたは <xref:System.Xml.XmlReader> オブジェクトの受け取りが可能なオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="e5702-140">The <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> and <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class all have overloads that can accept an <xref:System.Xml.XPath.XPathNavigator> object or an <xref:System.Xml.XmlReader> object as a parameter.</span></span>  
  
 <span data-ttu-id="e5702-141"><xref:System.Xml.XmlWriter.WriteNode%2A> クラスの <xref:System.Xml.XmlWriter> メソッドには、<xref:System.Xml.XmlNode>、<xref:System.Xml.XmlReader>、または <xref:System.Xml.XPath.XPathNavigator> オブジェクトの受け取りが可能なオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="e5702-141">The <xref:System.Xml.XmlWriter.WriteNode%2A> method of the <xref:System.Xml.XmlWriter> class has overloads that can accept an <xref:System.Xml.XmlNode>, <xref:System.Xml.XmlReader>, or <xref:System.Xml.XPath.XPathNavigator> object.</span></span>  
  
 <span data-ttu-id="e5702-142">次の例では、あるドキュメントからすべての `book` 要素を別のドキュメントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="e5702-142">The following example copies all the `book` elements from one document to another.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
  
Dim newBooks As XPathDocument = New XPathDocument("newBooks.xml")  
Dim newBooksNavigator As XPathNavigator = newBooks.CreateNavigator()  
  
Dim nav As XPathNavigator  
For Each nav in newBooksNavigator.SelectDescendants("book", "", false)  
    navigator.AppendChild(nav)  
Next  
  
document.Save("newBooks.xml");  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
  
XPathDocument newBooks = new XPathDocument("newBooks.xml");  
XPathNavigator newBooksNavigator = newBooks.CreateNavigator();  
  
foreach (XPathNavigator nav in newBooksNavigator.SelectDescendants("book", "", false))  
{  
    navigator.AppendChild(nav);  
}  
  
document.Save("newBooks.xml");  
```  
  
## <a name="inserting-values"></a><span data-ttu-id="e5702-143">値の挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-143">Inserting Values</span></span>  
 <span data-ttu-id="e5702-144"><xref:System.Xml.XPath.XPathNavigator> クラスは、<xref:System.Xml.XPath.XPathNavigator.SetValue%2A> オブジェクトにノードの値を挿入する <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> および <xref:System.Xml.XmlDocument> メソッドを提供しています。</span><span class="sxs-lookup"><span data-stu-id="e5702-144">The <xref:System.Xml.XPath.XPathNavigator> class provides the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> and <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> methods to insert values for a node into an <xref:System.Xml.XmlDocument> object.</span></span>  
  
### <a name="inserting-untyped-values"></a><span data-ttu-id="e5702-145">型指定されていない値の挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-145">Inserting Untyped Values</span></span>  
 <span data-ttu-id="e5702-146"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> メソッドは、パラメーターとして渡された型指定されていない `string` 値を挿入するだけです。このパラメーターは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にあるノードの値です。</span><span class="sxs-lookup"><span data-stu-id="e5702-146">The <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method simply inserts the untyped `string` value passed as a parameter as the value of the node the <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span> <span data-ttu-id="e5702-147">値に型は設定されず、スキーマ情報が使用可能な場合でも、ノードの型に対して新しい値が有効どうかを検証せずに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-147">The value is inserted without any type or without verifying that the new value is valid according to the type of the node if schema information is available.</span></span>  
  
 <span data-ttu-id="e5702-148"><xref:System.Xml.XPath.XPathNavigator.SetValue%2A> メソッドを使用して `price` フィァイル内のすべての `contosoBooks.xml` 要素を更新する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e5702-148">In the following example, the <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> method is used to update all `price` elements in the `contosoBooks.xml` file.</span></span>  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 <span data-ttu-id="e5702-149">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e5702-149">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="inserting-typed-values"></a><span data-ttu-id="e5702-150">型指定された値の挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-150">Inserting Typed Values</span></span>  
 <span data-ttu-id="e5702-151">ノードの型が W3C XML スキーマの単純型の場合、<xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> メソッドによって挿入される新しい値は、値の設定前に、単純型のファセットに対してチェックされます。</span><span class="sxs-lookup"><span data-stu-id="e5702-151">When the type of a node is a W3C XML Schema simple type, the new value inserted by the <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> method is checked against the facets of the simple type before the value is set.</span></span> <span data-ttu-id="e5702-152">新しい値がノードの型に対して無効な場合 (たとえば、型が `-1` の要素に、値 `xs:positiveInteger` を設定するような場合)、例外が返されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-152">If the new value is not valid according to the type of the node (for example, setting a value of `-1` on an element whose type is `xs:positiveInteger`), it results in an exception.</span></span>  
  
 <span data-ttu-id="e5702-153">次の例では、`price` ファイル内の最初の `book` 要素の `contosoBooks.xml` 要素の値を <xref:System.DateTime> 値に変更しようとしています。</span><span class="sxs-lookup"><span data-stu-id="e5702-153">The following example attempts to change the value of the `price` element of the first `book` element in the `contosoBooks.xml` file to a <xref:System.DateTime> value.</span></span> <span data-ttu-id="e5702-154">`price` 要素の XML スキーマ型は、`xs:decimal` ファイル内で `contosoBooks.xsd` として定義されているため、結果は例外になります。</span><span class="sxs-lookup"><span data-stu-id="e5702-154">Because the XML Schema type of the `price` element is defined as `xs:decimal` in the `contosoBooks.xsd` files, this results in an exception.</span></span>  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 <span data-ttu-id="e5702-155">この例は、`contosoBooks.xml` ファイルを入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e5702-155">The example takes the `contosoBooks.xml` file as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 <span data-ttu-id="e5702-156">また、`contosoBooks.xsd` ファイルも入力として使用します。</span><span class="sxs-lookup"><span data-stu-id="e5702-156">The example also takes the `contosoBooks.xsd` as an input.</span></span>  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
## <a name="the-innerxml-and-outerxml-properties"></a><span data-ttu-id="e5702-157">InnerXml および OuterXml プロパティ</span><span class="sxs-lookup"><span data-stu-id="e5702-157">The InnerXml and OuterXml Properties</span></span>  
 <span data-ttu-id="e5702-158"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> および <xref:System.Xml.XPath.XPathNavigator> プロパティは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="e5702-158">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties of the <xref:System.Xml.XPath.XPathNavigator> class change the XML markup of the nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on.</span></span>  
  
 <span data-ttu-id="e5702-159"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティは、与えられた XML <xref:System.Xml.XPath.XPathNavigator> の解析済みの内容を使用して `string` オブジェクトの現在位置にある子ノードの XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="e5702-159">The <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on with the parsed contents of the given XML `string`.</span></span> <span data-ttu-id="e5702-160">同様に、<xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティは、<xref:System.Xml.XPath.XPathNavigator> オブジェクトの現在位置にある子ノードと現在のノード自体の XML マークアップを変更します。</span><span class="sxs-lookup"><span data-stu-id="e5702-160">Similarly, the <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> property changes the XML markup of the child nodes an <xref:System.Xml.XPath.XPathNavigator> object is currently positioned on as well as the current node itself.</span></span>  
  
 <span data-ttu-id="e5702-161">このトピックで説明したメソッドに加えて、<xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティと <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティは、XML ドキュメントからノードに値を挿入するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="e5702-161">In addition to the methods described in this topic, the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties can be used to insert nodes and values in an XML document.</span></span> <span data-ttu-id="e5702-162"><xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> プロパティと <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> プロパティを使用してノードと値を挿入する方法の詳細については「[XpathNavigator による XML データの変更](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5702-162">For more information about using the <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> and <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> properties to insert nodes and values, see the [Modify XML Data using XPathNavigator](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) topic.</span></span>  
  
## <a name="namespace-and-xmllang-conflicts"></a><span data-ttu-id="e5702-163">名前空間と xml:lang の競合</span><span class="sxs-lookup"><span data-stu-id="e5702-163">Namespace and xml:lang Conflicts</span></span>  
 <span data-ttu-id="e5702-164">パラメーターとして `xml:lang` オブジェクトを受け取る <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、および <xref:System.Xml.XPath.XPathNavigator> メソッドを使用して XML データを挿入する場合、名前空間のスコープと <xref:System.Xml.XmlReader> 宣言に関連する競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5702-164">Certain conflicts related to the scope of namespace and `xml:lang` declarations can occur when inserting XML data using the <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A> and <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class that take <xref:System.Xml.XmlReader> objects as parameters.</span></span>  
  
 <span data-ttu-id="e5702-165">発生する可能性のある名前空間の競合は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e5702-165">The following are the possible namespace conflicts.</span></span>  
  
- <span data-ttu-id="e5702-166"><xref:System.Xml.XmlReader> オブジェクトのコンテキスト内のスコープに名前空間があり、プレフィックスから名前空間 URI へのマッピングが <xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内にない場合、新たに挿入されたノードに関する新しい名前空間宣言が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-166">If there is a namespace in-scope within the <xref:System.Xml.XmlReader> object's context, where the prefix to namespace URI mapping is not in the <xref:System.Xml.XPath.XPathNavigator> object's context, a new namespace declaration is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="e5702-167"><xref:System.Xml.XmlReader> オブジェクトのコンテキスト内と <xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内の両方のスコープに同じ名前空間 URI があるが、両方のコンテキスト内で別のプレフィックスにマップされている場合、<xref:System.Xml.XmlReader> オブジェクトからのプレフィックスと名前空間 URI を使用して、新たに挿入されたノードに対する新しい名前空間宣言が追加されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-167">If the same namespace URI is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different prefix mapped to it in both contexts, a new namespace declaration is added to the newly inserted node, with the prefix and namespace URI taken from the <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="e5702-168"><xref:System.Xml.XmlReader> オブジェクトのコンテキスト内と <xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内の両方のスコープに同じ名前空間プレフィックスがあるが、両方のコンテキスト内で別の名前空間 URI にマップされている場合、新たに挿入されたノードに対する新しい名前空間宣言が追加され、<xref:System.Xml.XmlReader> オブジェクトからの名前空間 URI を使用してそのプレフィックスを再宣言します。</span><span class="sxs-lookup"><span data-stu-id="e5702-168">If the same namespace prefix is in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but has a different namespace URI mapped to it in both contexts, a new namespace declaration is added to the newly inserted node which re-declares that prefix with the namespace URI taken from <xref:System.Xml.XmlReader> object.</span></span>  
  
- <span data-ttu-id="e5702-169"><xref:System.Xml.XmlReader> オブジェクトのコンテキスト内と <xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内の両方で、プレフィックスと名前空間 URI が同じ場合、新たに挿入されたノードに対する新しい名前空間宣言は追加されません。</span><span class="sxs-lookup"><span data-stu-id="e5702-169">If the prefix as well as the namespace URI in both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context is the same, no new namespace declaration is added to the newly inserted node.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5702-170">上記の説明は、プレフィックスとして空の `string` (たとえば、既定の名前空間宣言) を使用した名前空間宣言にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-170">The description above also applies to namespace declarations with the empty `string` as a prefix (for example, the default namespace declaration).</span></span>  
  
 <span data-ttu-id="e5702-171">発生する可能性のある `xml:lang` の競合は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e5702-171">The following are the possible `xml:lang` conflicts.</span></span>  
  
- <span data-ttu-id="e5702-172">`xml:lang` 属性が <xref:System.Xml.XmlReader> オブジェクトのコンテキスト内のスコープにあるが、<xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内にはない場合、`xml:lang` オブジェクトから受け取った値を持つ <xref:System.Xml.XmlReader> 属性が、新たに挿入されたノードに対して追加されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-172">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XmlReader> object's context but not in the <xref:System.Xml.XPath.XPathNavigator> object's context, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="e5702-173">`xml:lang` 属性が <xref:System.Xml.XmlReader> オブジェクトのコンテキスト内と <xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内の両方のスコープにあるが、それぞれの値が異なる場合、`xml:lang` オブジェクトから受け取った値を持つ <xref:System.Xml.XmlReader> 属性が、新たに挿入されたノードに対して追加されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-173">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each has a different value, an `xml:lang` attribute whose value is taken from the <xref:System.Xml.XmlReader> object is added to the newly inserted node.</span></span>  
  
- <span data-ttu-id="e5702-174">`xml:lang` 属性が <xref:System.Xml.XmlReader> オブジェクトのコンテキスト内と <xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内の両方のスコープにあるが、それぞれの値が同じ場合、新たに挿入されたノードに対して新しい `xml:lang` 属性は追加されません。</span><span class="sxs-lookup"><span data-stu-id="e5702-174">If there is an `xml:lang` attribute in-scope within both the <xref:System.Xml.XmlReader> object's context and the <xref:System.Xml.XPath.XPathNavigator> object's context, but each with the same value, no new `xml:lang` attribute is added on the newly inserted node.</span></span>  
  
- <span data-ttu-id="e5702-175">`xml:lang` 属性が <xref:System.Xml.XPath.XPathNavigator> オブジェクトのコンテキスト内のスコープにあるが、<xref:System.Xml.XmlReader> オブジェクトのコンテキスト内にはない場合、新たに挿入されたノードに対して `xml:lang` 属性は追加されません。</span><span class="sxs-lookup"><span data-stu-id="e5702-175">If there is an `xml:lang` attribute in-scope within the <xref:System.Xml.XPath.XPathNavigator> object's context, but none existing in the <xref:System.Xml.XmlReader> object's context, no `xml:lang` attribute is added to the newly inserted node.</span></span>  
  
## <a name="inserting-nodes-with-xmlwriter"></a><span data-ttu-id="e5702-176">XmlWriter によるノードの挿入</span><span class="sxs-lookup"><span data-stu-id="e5702-176">Inserting Nodes with XmlWriter</span></span>  
 <span data-ttu-id="e5702-177">「ノードと値の挿入」に記載されている兄弟ノード、子ノード、および属性ノードの挿入に使用されるメソッドはオーバーロードされます。</span><span class="sxs-lookup"><span data-stu-id="e5702-177">The methods used to insert sibling, child and attribute nodes described in the "Inserting Nodes and Values" section are overloaded.</span></span> <span data-ttu-id="e5702-178"><xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A> クラスの <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>、<xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>、<xref:System.Xml.XPath.XPathNavigator.PrependChild%2A>、<xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A>、および <xref:System.Xml.XPath.XPathNavigator> メソッドは、ノードの挿入に使用される <xref:System.Xml.XmlWriter> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="e5702-178">The <xref:System.Xml.XPath.XPathNavigator.InsertAfter%2A>, <xref:System.Xml.XPath.XPathNavigator.InsertBefore%2A>, <xref:System.Xml.XPath.XPathNavigator.AppendChild%2A>, <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> and <xref:System.Xml.XPath.XPathNavigator.CreateAttributes%2A> methods of the <xref:System.Xml.XPath.XPathNavigator> class return an <xref:System.Xml.XmlWriter> object used to insert nodes.</span></span>  
  
### <a name="unsupported-xmlwriter-methods"></a><span data-ttu-id="e5702-179">サポートされていない XmlWriter メソッド</span><span class="sxs-lookup"><span data-stu-id="e5702-179">Unsupported XmlWriter Methods</span></span>  
 <span data-ttu-id="e5702-180">XPath データ モデルとドキュメント オブジェクト モデル (DOM) には相違点があるため、<xref:System.Xml.XmlWriter> クラスによる XML ドキュメントへの情報の書き込みで使用されるメソッドのすべてが <xref:System.Xml.XPath.XPathNavigator> クラスによってサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e5702-180">Not all of the methods used for writing information to an XML document using the <xref:System.Xml.XmlWriter> class are supported by the <xref:System.Xml.XPath.XPathNavigator> class due to difference between the XPath data model and the Document Object Model (DOM).</span></span>  
  
 <span data-ttu-id="e5702-181"><xref:System.Xml.XmlWriter> クラスによってサポートされない <xref:System.Xml.XPath.XPathNavigator> クラス メソッドについて次の表で説明します。</span><span class="sxs-lookup"><span data-stu-id="e5702-181">The following table describes the <xref:System.Xml.XmlWriter> class methods not supported by the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>  
  
|<span data-ttu-id="e5702-182">メソッド</span><span class="sxs-lookup"><span data-stu-id="e5702-182">Method</span></span>|<span data-ttu-id="e5702-183">説明</span><span class="sxs-lookup"><span data-stu-id="e5702-183">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.XmlWriter.WriteEntityRef%2A>|<span data-ttu-id="e5702-184"><xref:System.NotSupportedException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="e5702-184">Throws a <xref:System.NotSupportedException> exception.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteDocType%2A>|<span data-ttu-id="e5702-185">ルート レベルでは無視され、XML ドキュメント内の他のレベルで呼び出された場合は、<xref:System.NotSupportedException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="e5702-185">Ignored at the root level and throws a <xref:System.NotSupportedException> exception if called at any other level in the XML document.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCData%2A>|<span data-ttu-id="e5702-186">同じ文字または文字列についての <xref:System.Xml.XmlWriter.WriteString%2A> メソッドの呼び出しとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="e5702-186">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteCharEntity%2A>|<span data-ttu-id="e5702-187">同じ文字または文字列についての <xref:System.Xml.XmlWriter.WriteString%2A> メソッドの呼び出しとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="e5702-187">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
|<xref:System.Xml.XmlWriter.WriteSurrogateCharEntity%2A>|<span data-ttu-id="e5702-188">同じ文字または文字列についての <xref:System.Xml.XmlWriter.WriteString%2A> メソッドの呼び出しとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="e5702-188">Treated as a call to the <xref:System.Xml.XmlWriter.WriteString%2A> method for the equivalent character or characters.</span></span>|  
  
 <span data-ttu-id="e5702-189"><xref:System.Xml.XmlWriter> クラスに関する詳細については、<xref:System.Xml.XmlWriter> クラスのリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5702-189">For more information about the <xref:System.Xml.XmlWriter> class, see the <xref:System.Xml.XmlWriter> class reference documentation.</span></span>  
  
### <a name="multiple-xmlwriter-objects"></a><span data-ttu-id="e5702-190">複数の XmlWriter オブジェクト</span><span class="sxs-lookup"><span data-stu-id="e5702-190">Multiple XmlWriter Objects</span></span>  
 <span data-ttu-id="e5702-191">1 つ以上の開いた <xref:System.Xml.XPath.XPathNavigator> オブジェクトを使用して、XML ドキュメントの異なる部分を指す複数の <xref:System.Xml.XmlWriter> オブジェクトを持つことができます。</span><span class="sxs-lookup"><span data-stu-id="e5702-191">It is possible to have multiple <xref:System.Xml.XPath.XPathNavigator> objects pointing to different parts of an XML document with one or more open <xref:System.Xml.XmlWriter> objects.</span></span> <span data-ttu-id="e5702-192">複数の <xref:System.Xml.XmlWriter> オブジェクトは、単一スレッドのシナリオで許可されサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e5702-192">Multiple <xref:System.Xml.XmlWriter> objects are allowed and supported in single-threaded scenarios.</span></span>  
  
 <span data-ttu-id="e5702-193">以下は、複数の <xref:System.Xml.XmlWriter> オブジェクト使用時の重要な注意事項です。</span><span class="sxs-lookup"><span data-stu-id="e5702-193">The following are important notes to consider when using multiple <xref:System.Xml.XmlWriter> objects.</span></span>  
  
- <span data-ttu-id="e5702-194">それぞれの <xref:System.Xml.XmlWriter> オブジェクトの <xref:System.Xml.XmlWriter.Close%2A> メソッドが呼び出されるときに、<xref:System.Xml.XmlWriter> オブジェクトによって書き込まれる XML フラグメントが XML ドキュメントに追加されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-194">XML fragments written by <xref:System.Xml.XmlWriter> objects are added to the XML document when the <xref:System.Xml.XmlWriter.Close%2A> method of each <xref:System.Xml.XmlWriter> object is called.</span></span> <span data-ttu-id="e5702-195">その時点まで、<xref:System.Xml.XmlWriter> オブジェクトは、まとまっていないフラグメントを書き込んでいます。</span><span class="sxs-lookup"><span data-stu-id="e5702-195">Until that point, the <xref:System.Xml.XmlWriter> object is writing a disconnected fragment.</span></span> <span data-ttu-id="e5702-196">XML ドキュメントに対する操作が実行される場合、<xref:System.Xml.XmlWriter> の呼び出し前に <xref:System.Xml.XmlWriter.Close%2A> オブジェクトによって書き込まれているフラグメントは影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="e5702-196">If an operation is performed on the XML document, any fragments being written by an <xref:System.Xml.XmlWriter> object, before the <xref:System.Xml.XmlWriter.Close%2A> has been called, are not affected.</span></span>  
  
- <span data-ttu-id="e5702-197">特定の XML サブツリー上に、開いた <xref:System.Xml.XmlWriter> オブジェクトがあり、そのサブツリーが削除された場合、<xref:System.Xml.XmlWriter> オブジェクトが引き続きそのサブツリーに追加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e5702-197">If there is an open <xref:System.Xml.XmlWriter> object on a particular XML subtree and that subtree is deleted, the <xref:System.Xml.XmlWriter> object may still add to the sub-tree.</span></span> <span data-ttu-id="e5702-198">サブツリーは単に削除済みフラグメントになります。</span><span class="sxs-lookup"><span data-stu-id="e5702-198">The subtree simply becomes a deleted fragment.</span></span>  
  
- <span data-ttu-id="e5702-199">XML ドキュメント内の同じ位置で、複数の <xref:System.Xml.XmlWriter> オブジェクトが開かれた場合、<xref:System.Xml.XmlWriter> オブジェクトが開かれた順序ではなく、それらが閉じられる順序で XML ドキュメントにそれらが追加されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-199">If multiple <xref:System.Xml.XmlWriter> objects are opened at the same point in the XML document, they are added to the XML document in the order in which the <xref:System.Xml.XmlWriter> objects are closed, not in the order in which they were opened.</span></span>  
  
 <span data-ttu-id="e5702-200">次の例では、<xref:System.Xml.XmlDocument> オブジェクトを作成し、<xref:System.Xml.XPath.XPathNavigator> オブジェクトを作成した後、<xref:System.Xml.XmlWriter> メソッドによって返される <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> オブジェクトを使用して、`books.xml` ファイル内に最初の book 構造体を作成します。</span><span class="sxs-lookup"><span data-stu-id="e5702-200">The following example creates an <xref:System.Xml.XmlDocument> object, creates an <xref:System.Xml.XPath.XPathNavigator> object, and then uses the <xref:System.Xml.XmlWriter> object returned by the <xref:System.Xml.XPath.XPathNavigator.PrependChild%2A> method to create the structure of the first book in the `books.xml` file.</span></span> <span data-ttu-id="e5702-201">この例は、それを `book.xml` ファイルとして保存します。</span><span class="sxs-lookup"><span data-stu-id="e5702-201">The example then saves it as the `book.xml` file.</span></span>  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Using writer As XmlWriter = navigator.PrependChild()  
  
    writer.WriteStartElement("bookstore")  
    writer.WriteStartElement("book")  
    writer.WriteAttributeString("genre", "autobiography")  
    writer.WriteAttributeString("publicationdate", "1981-03-22")  
    writer.WriteAttributeString("ISBN", "1-861003-11-0")  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin")  
    writer.WriteStartElement("author")  
    writer.WriteElementString("first-name", "Benjamin")  
    writer.WriteElementString("last-name", "Franklin")  
    writer.WriteElementString("price", "8.99")  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
    writer.WriteEndElement()  
  
End Using  
  
document.Save("book.xml")  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
XPathNavigator navigator = document.CreateNavigator();  
  
using (XmlWriter writer = navigator.PrependChild())  
{  
    writer.WriteStartElement("bookstore");  
    writer.WriteStartElement("book");  
    writer.WriteAttributeString("genre", "autobiography");  
    writer.WriteAttributeString("publicationdate", "1981-03-22");  
    writer.WriteAttributeString("ISBN", "1-861003-11-0");  
    writer.WriteElementString("title", "The Autobiography of Benjamin Franklin");  
    writer.WriteStartElement("author");  
    writer.WriteElementString("first-name", "Benjamin");  
    writer.WriteElementString("last-name", "Franklin");  
    writer.WriteElementString("price", "8.99");  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
    writer.WriteEndElement();  
}  
document.Save("book.xml");  
```  
  
## <a name="saving-an-xml-document"></a><span data-ttu-id="e5702-202">XML ドキュメントの保存</span><span class="sxs-lookup"><span data-stu-id="e5702-202">Saving an XML Document</span></span>  
 <span data-ttu-id="e5702-203">ここに記載されているメソッドによる <xref:System.Xml.XmlDocument> オブジェクトに対する変更の保存は、<xref:System.Xml.XmlDocument> クラスのメソッドを使用して実行されます。</span><span class="sxs-lookup"><span data-stu-id="e5702-203">Saving changes made to an <xref:System.Xml.XmlDocument> object as the result of the methods described in this topic is performed using the methods of the <xref:System.Xml.XmlDocument> class.</span></span> <span data-ttu-id="e5702-204"><xref:System.Xml.XmlDocument> オブジェクトに対する変更の保存に関する詳細については、「[ドキュメントの保存と書き込み](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5702-204">For more information about saving changes made to an <xref:System.Xml.XmlDocument> object, see [Saving and Writing a Document](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5702-205">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5702-205">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="e5702-206">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="e5702-206">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="e5702-207">XpathNavigator による XML データの変更</span><span class="sxs-lookup"><span data-stu-id="e5702-207">Modify XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="e5702-208">XPathNavigator による XML データの削除</span><span class="sxs-lookup"><span data-stu-id="e5702-208">Remove XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
