---
title: XML ツリーからの要素、属性、およびノードの削除
ms.date: 07/20/2015
ms.assetid: 5cf21919-4360-4b49-b29d-58ea3164ac72
ms.openlocfilehash: 4cce1eff469c1f737e18b88cce30155547d9f11b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348947"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-visual-basic"></a><span data-ttu-id="c19c6-102">XML ツリーからの要素、属性、およびノードの削除 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c19c6-102">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="c19c6-103">要素、属性、およびその他の種類のノードを削除して、XML ツリーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="c19c6-103">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>  
  
 <span data-ttu-id="c19c6-104">1 つの要素または 1 つの属性は XML ドキュメントから簡単に削除できます。</span><span class="sxs-lookup"><span data-stu-id="c19c6-104">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="c19c6-105">一方、要素または属性のコレクションを削除する場合は、まずコレクションをリストに具体化し、そのリストから要素または属性を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c19c6-105">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="c19c6-106">最適な方法は、これを自動的に行う <xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用することです。</span><span class="sxs-lookup"><span data-stu-id="c19c6-106">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>  
  
 <span data-ttu-id="c19c6-107">このような方法でコレクションの削除を実行する主な理由は、XML ツリーから取得するコレクションのほとんどが遅延実行を使用して生成されるからです。</span><span class="sxs-lookup"><span data-stu-id="c19c6-107">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="c19c6-108">最初にコレクションをリストに具体化せず、拡張メソッドも使用しない場合、特定の種類のバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c19c6-108">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="c19c6-109">詳細については、「[宣言型コードと命令型コードの混在のバグ (LINQ to XML)」 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c19c6-109">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c19c6-110">ノードおよび属性を XML ツリーから削除するメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-110">The following methods remove nodes and attributes from an XML tree.</span></span>  
  
|<span data-ttu-id="c19c6-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="c19c6-111">Method</span></span>|<span data-ttu-id="c19c6-112">説明</span><span class="sxs-lookup"><span data-stu-id="c19c6-112">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-113"><xref:System.Xml.Linq.XAttribute> をその親から削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-113">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|  
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-114">子ノードを <xref:System.Xml.Linq.XContainer> から削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-114">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-115">コンテンツおよび属性を <xref:System.Xml.Linq.XElement> から削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-115">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-116"><xref:System.Xml.Linq.XElement> の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-116">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-117">`null` を値に受け取ると、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-117">If you pass `null` for value, then removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-118">`null` を値に受け取ると、子要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-118">If you pass `null` for value, then removes the child element.</span></span>|  
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-119"><xref:System.Xml.Linq.XNode> をその親から削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-119">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|  
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="c19c6-120">ソース コレクション内のすべての属性または要素をその親要素から削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-120">Removes every attribute or element in the source collection from its parent element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c19c6-121">例</span><span class="sxs-lookup"><span data-stu-id="c19c6-121">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c19c6-122">説明</span><span class="sxs-lookup"><span data-stu-id="c19c6-122">Description</span></span>  
 <span data-ttu-id="c19c6-123">この例では、要素を削除する 3 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-123">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="c19c6-124">まず、1 つの要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-124">First, it removes a single element.</span></span> <span data-ttu-id="c19c6-125">次に、要素のコレクションを取得し、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 演算子を使用して要素を具体化して、コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-125">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="c19c6-126">最後に、要素のコレクションを取得し、<xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用して要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="c19c6-126">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>  
  
 <span data-ttu-id="c19c6-127"><xref:System.Linq.Enumerable.ToList%2A> 演算子の詳細については、「[データ型の変換 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c19c6-127">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/converting-data-types.md).</span></span>  
  
### <a name="code"></a><span data-ttu-id="c19c6-128">コード</span><span class="sxs-lookup"><span data-stu-id="c19c6-128">Code</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root>  
        <Child1>  
            <GrandChild1/>  
            <GrandChild2/>  
            <GrandChild3/>  
        </Child1>  
        <Child2>  
            <GrandChild4/>  
            <GrandChild5/>  
            <GrandChild6/>  
        </Child2>  
        <Child3>  
            <GrandChild7/>  
            <GrandChild8/>  
            <GrandChild9/>  
        </Child3>  
    </Root>  
root.<Child1>.<GrandChild1>.Remove()  
root.<Child2>.Elements().ToList().Remove()  
root.<Child3>.Elements().Remove()  
Console.WriteLine(root)  
```  
  
### <a name="comments"></a><span data-ttu-id="c19c6-129">コメント</span><span class="sxs-lookup"><span data-stu-id="c19c6-129">Comments</span></span>  
 <span data-ttu-id="c19c6-130">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c19c6-130">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child1>  
    <GrandChild2 />  
    <GrandChild3 />  
  </Child1>  
  <Child2 />  
  <Child3 />  
</Root>  
```  
  
 <span data-ttu-id="c19c6-131">最初の孫要素が `Child1` から削除されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="c19c6-131">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="c19c6-132">すべての孫要素が、`Child2` と `Child3` から削除されています。</span><span class="sxs-lookup"><span data-stu-id="c19c6-132">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c19c6-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c19c6-133">See also</span></span>

- [<span data-ttu-id="c19c6-134">XML ツリーの変更 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c19c6-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
