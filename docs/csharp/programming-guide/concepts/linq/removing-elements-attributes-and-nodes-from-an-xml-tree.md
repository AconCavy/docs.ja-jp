---
title: XML ツリーからの要素、属性、およびノードの削除 (C#)
description: XML ツリーから要素、属性、およびノードを削除する方法について説明します。 削除方法の一覧とコード例を参照してください。
ms.date: 07/20/2015
ms.assetid: 07dd06d6-1117-4077-bf98-9120cf51176e
ms.openlocfilehash: 4e753c3d96c4cbc050b08076ca8bff8c17b2e252
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87300047"
---
# <a name="removing-elements-attributes-and-nodes-from-an-xml-tree-c"></a><span data-ttu-id="f1d31-104">XML ツリーからの要素、属性、およびノードの削除 (C#)</span><span class="sxs-lookup"><span data-stu-id="f1d31-104">Removing Elements, Attributes, and Nodes from an XML Tree (C#)</span></span>

<span data-ttu-id="f1d31-105">要素、属性、およびその他の種類のノードを削除して、XML ツリーを変更できます。</span><span class="sxs-lookup"><span data-stu-id="f1d31-105">You can modify an XML tree, removing elements, attributes, and other types of nodes.</span></span>

<span data-ttu-id="f1d31-106">1 つの要素または 1 つの属性は XML ドキュメントから簡単に削除できます。</span><span class="sxs-lookup"><span data-stu-id="f1d31-106">Removing a single element or a single attribute from an XML document is straightforward.</span></span> <span data-ttu-id="f1d31-107">一方、要素または属性のコレクションを削除する場合は、まずコレクションをリストに具体化し、そのリストから要素または属性を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f1d31-107">However, when removing collections of elements or attributes, you should first materialize a collection into a list, and then delete the elements or attributes from the list.</span></span> <span data-ttu-id="f1d31-108">最適な方法は、これを自動的に行う <xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用することです。</span><span class="sxs-lookup"><span data-stu-id="f1d31-108">The best approach is to use the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method, which will do this for you.</span></span>

<span data-ttu-id="f1d31-109">このような方法でコレクションの削除を実行する主な理由は、XML ツリーから取得するコレクションのほとんどが遅延実行を使用して生成されるからです。</span><span class="sxs-lookup"><span data-stu-id="f1d31-109">The main reason for doing this is that most of the collections you retrieve from an XML tree are yielded using deferred execution.</span></span> <span data-ttu-id="f1d31-110">最初にコレクションをリストに具体化せず、拡張メソッドも使用しない場合、特定の種類のバグが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f1d31-110">If you do not first materialize them into a list, or if you do not use the extension methods, it is possible to encounter a certain class of bugs.</span></span> <span data-ttu-id="f1d31-111">詳細については、「[宣言型コードと命令型コードの混在のバグ (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d31-111">For more information, see [Mixed Declarative Code/Imperative Code Bugs (LINQ to XML) (C#)](./mixed-declarative-code-imperative-code-bugs-linq-to-xml.md).</span></span>

<span data-ttu-id="f1d31-112">ノードおよび属性を XML ツリーから削除するメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-112">The following methods remove nodes and attributes from an XML tree.</span></span>

|<span data-ttu-id="f1d31-113">メソッド</span><span class="sxs-lookup"><span data-stu-id="f1d31-113">Method</span></span>|<span data-ttu-id="f1d31-114">説明</span><span class="sxs-lookup"><span data-stu-id="f1d31-114">Description</span></span>|
|------------|-----------------|
|<xref:System.Xml.Linq.XAttribute.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-115"><xref:System.Xml.Linq.XAttribute> をその親から削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-115">Removes an <xref:System.Xml.Linq.XAttribute> from its parent.</span></span>|
|<xref:System.Xml.Linq.XContainer.RemoveNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-116">子ノードを <xref:System.Xml.Linq.XContainer> から削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-116">Removes the child nodes from an <xref:System.Xml.Linq.XContainer>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-117">コンテンツおよび属性を <xref:System.Xml.Linq.XElement> から削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-117">Removes content and attributes from an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-118"><xref:System.Xml.Linq.XElement> の属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-118">Removes the attributes of an <xref:System.Xml.Linq.XElement>.</span></span>|
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-119">`null` を値に受け取ると、属性を削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-119">If you pass `null` for value, then removes the attribute.</span></span>|
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-120">`null` を値に受け取ると、子要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-120">If you pass `null` for value, then removes the child element.</span></span>|
|<xref:System.Xml.Linq.XNode.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-121"><xref:System.Xml.Linq.XNode> をその親から削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-121">Removes an <xref:System.Xml.Linq.XNode> from its parent.</span></span>|
|<xref:System.Xml.Linq.Extensions.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="f1d31-122">ソース コレクション内のすべての属性または要素をその親要素から削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-122">Removes every attribute or element in the source collection from its parent element.</span></span>|

## <a name="example"></a><span data-ttu-id="f1d31-123">例</span><span class="sxs-lookup"><span data-stu-id="f1d31-123">Example</span></span>

### <a name="description"></a><span data-ttu-id="f1d31-124">説明</span><span class="sxs-lookup"><span data-stu-id="f1d31-124">Description</span></span>

<span data-ttu-id="f1d31-125">この例では、要素を削除する 3 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-125">This example demonstrates three approaches to removing elements.</span></span> <span data-ttu-id="f1d31-126">まず、1 つの要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-126">First, it removes a single element.</span></span> <span data-ttu-id="f1d31-127">次に、要素のコレクションを取得し、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> 演算子を使用して要素を具体化して、コレクションを削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-127">Second, it retrieves a collection of elements, materializes them using the <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> operator, and removes the collection.</span></span> <span data-ttu-id="f1d31-128">最後に、要素のコレクションを取得し、<xref:System.Xml.Linq.Extensions.Remove%2A> 拡張メソッドを使用して要素を削除します。</span><span class="sxs-lookup"><span data-stu-id="f1d31-128">Finally, it retrieves a collection of elements and removes them using the <xref:System.Xml.Linq.Extensions.Remove%2A> extension method.</span></span>

<span data-ttu-id="f1d31-129"><xref:System.Linq.Enumerable.ToList%2A> 演算子の詳細については、「[データ型の変換 (C#)](./converting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f1d31-129">For more information on the <xref:System.Linq.Enumerable.ToList%2A> operator, see [Converting Data Types (C#)](./converting-data-types.md).</span></span>

### <a name="code"></a><span data-ttu-id="f1d31-130">コード</span><span class="sxs-lookup"><span data-stu-id="f1d31-130">Code</span></span>

```csharp
XElement root = XElement.Parse(@"<Root>
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
</Root>");
root.Element("Child1").Element("GrandChild1").Remove();
root.Element("Child2").Elements().ToList().Remove();
root.Element("Child3").Elements().Remove();
Console.WriteLine(root);
```

### <a name="comments"></a><span data-ttu-id="f1d31-131">コメント</span><span class="sxs-lookup"><span data-stu-id="f1d31-131">Comments</span></span>

<span data-ttu-id="f1d31-132">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="f1d31-132">This code produces the following output:</span></span>

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

<span data-ttu-id="f1d31-133">最初の孫要素が `Child1` から削除されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="f1d31-133">Notice that the first grandchild element has been removed from `Child1`.</span></span> <span data-ttu-id="f1d31-134">すべての孫要素が、`Child2` と `Child3` から削除されています。</span><span class="sxs-lookup"><span data-stu-id="f1d31-134">All grandchildren elements have been removed from `Child2` and from `Child3`.</span></span>
