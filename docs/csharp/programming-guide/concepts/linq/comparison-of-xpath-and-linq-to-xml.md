---
title: XPath と LINQ to XML の比較
description: C# での XPath と LINQ to XML との間の機能の類似点と相違点について学習します。 この両方を使用して、XML ツリーのクエリを実行できます。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104007"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a><span data-ttu-id="4edb6-104">XPath と LINQ to XML の比較</span><span class="sxs-lookup"><span data-stu-id="4edb6-104">Comparison of XPath and LINQ to XML</span></span>
<span data-ttu-id="4edb6-105">XPath と LINQ to XML の機能はある程度似ています。</span><span class="sxs-lookup"><span data-stu-id="4edb6-105">XPath and LINQ to XML offer some similar functionality.</span></span> <span data-ttu-id="4edb6-106">どちらも XML ツリーに対してクエリを実行するために使用され、結果として、要素のコレクション、属性のコレクション、ノードのコレクション、要素や属性の値などを返します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-106">Both can be used to query an XML tree, returning such results as a collection of elements, a collection of attributes, a collection of nodes, or the value of an element or attribute.</span></span> <span data-ttu-id="4edb6-107">ただし、相違点もいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4edb6-107">However, there are also some differences.</span></span>  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a><span data-ttu-id="4edb6-108">XPath と LINQ to XML の違い</span><span class="sxs-lookup"><span data-stu-id="4edb6-108">Differences Between XPath and LINQ to XML</span></span>  
 <span data-ttu-id="4edb6-109">XPath では、新しい型を射影できません。</span><span class="sxs-lookup"><span data-stu-id="4edb6-109">XPath does not allow projection of new types.</span></span> <span data-ttu-id="4edb6-110">XPath では、ツリーからノードのコレクションが返されるだけですが、LINQ to XML では、クエリを実行し、オブジェクト グラフまたは XML ツリーを新しい構造に射影できます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-110">It can only return collections of nodes from the tree, whereas LINQ to XML can execute a query and project an object graph or an XML tree in a new shape.</span></span> <span data-ttu-id="4edb6-111">LINQ to XML クエリは、XPath 式と比べて、はるかに多機能かつ強力です。</span><span class="sxs-lookup"><span data-stu-id="4edb6-111">LINQ to XML queries encompass much more functionality and are much more powerful than XPath expressions.</span></span>  
  
 <span data-ttu-id="4edb6-112">XPath 式は、文字列内に独立して存在します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-112">XPath expressions exist in isolation within a string.</span></span> <span data-ttu-id="4edb6-113">C# コンパイラは、コンパイル時に XPath 式を解析できません。</span><span class="sxs-lookup"><span data-stu-id="4edb6-113">The C# compiler cannot help parse the XPath expression at compile time.</span></span> <span data-ttu-id="4edb6-114">一方 LINQ to XML クエリは、C# コンパイラによって解析され、コンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-114">By contrast, LINQ to XML queries are parsed and compiled by the C# compiler.</span></span> <span data-ttu-id="4edb6-115">コンパイラを使用することにより、多くのクエリ エラーを検出できます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-115">The compiler is able to catch many query errors.</span></span>  
  
 <span data-ttu-id="4edb6-116">XPath の結果は厳密に型指定されません。</span><span class="sxs-lookup"><span data-stu-id="4edb6-116">XPath results are not strongly typed.</span></span> <span data-ttu-id="4edb6-117">多くの場合、XPath 式を評価した結果はオブジェクトであり、開発者が適切な型を決定し、必要に応じて結果をキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4edb6-117">In a number of circumstances, the result of evaluating an XPath expression is an object, and it is up to the developer to determine the proper type and cast the result as necessary.</span></span> <span data-ttu-id="4edb6-118">一方、LINQ to XML クエリからの射影は厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-118">By contrast, the projections from a LINQ to XML query are strongly typed.</span></span>  
  
## <a name="result-ordering"></a><span data-ttu-id="4edb6-119">結果の順序付け</span><span class="sxs-lookup"><span data-stu-id="4edb6-119">Result Ordering</span></span>  
 <span data-ttu-id="4edb6-120">XPath 1.0 勧告には、XPath 式の評価結果であるコレクションは順序付けされないことが記載されています。</span><span class="sxs-lookup"><span data-stu-id="4edb6-120">The XPath 1.0 Recommendation states that a collection that is the result of evaluating an XPath expression is unordered.</span></span>  
  
 <span data-ttu-id="4edb6-121">ただし、LINQ to XML の XPath 軸メソッドから返されるコレクションを反復処理すると、コレクション内のノードがドキュメント順に返されます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-121">However, when iterating through a collection returned by a LINQ to XML XPath axis method, the nodes in the collection are returned in document order.</span></span> <span data-ttu-id="4edb6-122">これは、ドキュメントの逆順として述語が表現されている `preceding` や `preceding-sibling` などの XPath 軸にアクセスする場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="4edb6-122">This is the case even when accessing the XPath axes where predicates are expressed in terms of reverse document order, such as `preceding` and `preceding-sibling`.</span></span>  
  
 <span data-ttu-id="4edb6-123">一方、LINQ to XML 軸のほとんどではコレクションがドキュメント順に返されますが、<xref:System.Xml.Linq.XNode.Ancestors%2A> と <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> の 2 つでは、コレクションがドキュメントの逆順で返されます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-123">By contrast, most of the LINQ to XML axes return collections in document order, but two of them, <xref:System.Xml.Linq.XNode.Ancestors%2A> and <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, return collections in reverse document order.</span></span> <span data-ttu-id="4edb6-124">次の表では、軸を列挙し、それぞれのコレクションの順序を示します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-124">The following table enumerates the axes, and indicates collection order for each:</span></span>  
  
|<span data-ttu-id="4edb6-125">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="4edb6-125">LINQ to XML axis</span></span>|<span data-ttu-id="4edb6-126">並べ替え</span><span class="sxs-lookup"><span data-stu-id="4edb6-126">Ordering</span></span>|  
|----------------------|--------------|  
|<span data-ttu-id="4edb6-127">XContainer.DescendantNodes</span><span class="sxs-lookup"><span data-stu-id="4edb6-127">XContainer.DescendantNodes</span></span>|<span data-ttu-id="4edb6-128">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-128">Document order</span></span>|  
|<span data-ttu-id="4edb6-129">XContainer.Descendants</span><span class="sxs-lookup"><span data-stu-id="4edb6-129">XContainer.Descendants</span></span>|<span data-ttu-id="4edb6-130">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-130">Document order</span></span>|  
|<span data-ttu-id="4edb6-131">XContainer.Elements</span><span class="sxs-lookup"><span data-stu-id="4edb6-131">XContainer.Elements</span></span>|<span data-ttu-id="4edb6-132">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-132">Document order</span></span>|  
|<span data-ttu-id="4edb6-133">XContainer.Nodes</span><span class="sxs-lookup"><span data-stu-id="4edb6-133">XContainer.Nodes</span></span>|<span data-ttu-id="4edb6-134">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-134">Document order</span></span>|  
|<span data-ttu-id="4edb6-135">XContainer.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-135">XContainer.NodesAfterSelf</span></span>|<span data-ttu-id="4edb6-136">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-136">Document order</span></span>|  
|<span data-ttu-id="4edb6-137">XContainer.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-137">XContainer.NodesBeforeSelf</span></span>|<span data-ttu-id="4edb6-138">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-138">Document order</span></span>|  
|<span data-ttu-id="4edb6-139">XElement.AncestorsAndSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-139">XElement.AncestorsAndSelf</span></span>|<span data-ttu-id="4edb6-140">ドキュメントの逆順</span><span class="sxs-lookup"><span data-stu-id="4edb6-140">Reverse document order</span></span>|  
|<span data-ttu-id="4edb6-141">XElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="4edb6-141">XElement.Attributes</span></span>|<span data-ttu-id="4edb6-142">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-142">Document order</span></span>|  
|<span data-ttu-id="4edb6-143">XElement.DescendantNodesAndSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-143">XElement.DescendantNodesAndSelf</span></span>|<span data-ttu-id="4edb6-144">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-144">Document order</span></span>|  
|<span data-ttu-id="4edb6-145">XElement.DescendantsAndSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-145">XElement.DescendantsAndSelf</span></span>|<span data-ttu-id="4edb6-146">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-146">Document order</span></span>|  
|<span data-ttu-id="4edb6-147">XNode.Ancestors</span><span class="sxs-lookup"><span data-stu-id="4edb6-147">XNode.Ancestors</span></span>|<span data-ttu-id="4edb6-148">ドキュメントの逆順</span><span class="sxs-lookup"><span data-stu-id="4edb6-148">Reverse document order</span></span>|  
|<span data-ttu-id="4edb6-149">XNode.ElementsAfterSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-149">XNode.ElementsAfterSelf</span></span>|<span data-ttu-id="4edb6-150">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-150">Document order</span></span>|  
|<span data-ttu-id="4edb6-151">XNode.ElementsBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-151">XNode.ElementsBeforeSelf</span></span>|<span data-ttu-id="4edb6-152">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-152">Document order</span></span>|  
|<span data-ttu-id="4edb6-153">XNode.NodesAfterSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-153">XNode.NodesAfterSelf</span></span>|<span data-ttu-id="4edb6-154">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-154">Document order</span></span>|  
|<span data-ttu-id="4edb6-155">XNode.NodesBeforeSelf</span><span class="sxs-lookup"><span data-stu-id="4edb6-155">XNode.NodesBeforeSelf</span></span>|<span data-ttu-id="4edb6-156">ドキュメント順</span><span class="sxs-lookup"><span data-stu-id="4edb6-156">Document order</span></span>|  
  
## <a name="positional-predicates"></a><span data-ttu-id="4edb6-157">位置述語</span><span class="sxs-lookup"><span data-stu-id="4edb6-157">Positional Predicates</span></span>  
 <span data-ttu-id="4edb6-158">XPath 式では、多くの軸で位置述語がドキュメント順として表現されますが、逆方向軸つまり `preceding`、`preceding-sibling`、`ancestor`、および `ancestor-or-self` の場合は、ドキュメントの逆順で表現されます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-158">Within an XPath expression, positional predicates are expressed in terms of document order for many axes, but are expressed in reverse document order for reverse axes, which are `preceding`, `preceding-sibling`, `ancestor`, and `ancestor-or-self`.</span></span> <span data-ttu-id="4edb6-159">たとえば、XPath 式 `preceding-sibling::*[1]` は、直前の兄弟を返します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-159">For example, the XPath expression `preceding-sibling::*[1]` returns the immediately preceding sibling.</span></span> <span data-ttu-id="4edb6-160">これは、最終的な結果セットがドキュメント順で表される場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="4edb6-160">This is the case even though the final result set is presented in document order.</span></span>  
  
 <span data-ttu-id="4edb6-161">一方、LINQ to XML の位置述語は、常に軸の順序として表現されます。</span><span class="sxs-lookup"><span data-stu-id="4edb6-161">By contrast, all positional predicates in LINQ to XML are always expressed in terms of the order of the axis.</span></span> <span data-ttu-id="4edb6-162">たとえば、`anElement.ElementsBeforeSelf().ElementAt(0)` は、直前の兄弟ではなく、クエリされる要素の親の最初の子要素を返します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-162">For example, `anElement.ElementsBeforeSelf().ElementAt(0)` returns the first child element of the parent of the queried element, not the immediate preceding sibling.</span></span> <span data-ttu-id="4edb6-163">別の例として、`anElement.Ancestors().ElementAt(0)` は親要素を返します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-163">Another example: `anElement.Ancestors().ElementAt(0)` returns the parent element.</span></span>  
  
 <span data-ttu-id="4edb6-164">LINQ to XML で直前の要素を検索する場合は、次の式を記述します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-164">If you wanted to find the immediately preceding element in LINQ to XML, you would write the following expression:</span></span>  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a><span data-ttu-id="4edb6-165">パフォーマンスの違い</span><span class="sxs-lookup"><span data-stu-id="4edb6-165">Performance Differences</span></span>  
 <span data-ttu-id="4edb6-166">LINQ to XML 内の XPath 機能を使用する XPath クエリのパフォーマンスは、LINQ to XML クエリよりも低くなります。</span><span class="sxs-lookup"><span data-stu-id="4edb6-166">XPath queries that use the XPath functionality in LINQ to XML will not perform as well as LINQ to XML queries.</span></span>  
  
## <a name="comparison-of-composition"></a><span data-ttu-id="4edb6-167">構成の比較</span><span class="sxs-lookup"><span data-stu-id="4edb6-167">Comparison of Composition</span></span>  
 <span data-ttu-id="4edb6-168">LINQ to XML クエリの構成は、XPath 式の構成に似ている部分がありますが、構文はかなり異なります。</span><span class="sxs-lookup"><span data-stu-id="4edb6-168">Composition of a LINQ to XML query is somewhat parallel to composition of an XPath expression, although very different in syntax.</span></span>  
  
 <span data-ttu-id="4edb6-169">たとえば、`customers` という変数に要素があり、`CompanyName` というすべての子要素の下で `Customer` という孫要素を検索する場合は、次のように XPath 式を記述します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-169">For example, if you have an element in a variable named `customers`, and you want to find a grandchild element named `CompanyName` under all child elements named `Customer`, you would write an XPath expression as follows:</span></span>  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 <span data-ttu-id="4edb6-170">同等の LINQ to XML クエリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4edb6-170">The equivalent LINQ to XML query is:</span></span>  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 <span data-ttu-id="4edb6-171">同様の対応関係が XPath 軸ごとに存在します。</span><span class="sxs-lookup"><span data-stu-id="4edb6-171">There are similar parallels for each of the XPath axes.</span></span>  
  
|<span data-ttu-id="4edb6-172">XPath 軸</span><span class="sxs-lookup"><span data-stu-id="4edb6-172">XPath axis</span></span>|<span data-ttu-id="4edb6-173">LINQ to XML 軸</span><span class="sxs-lookup"><span data-stu-id="4edb6-173">LINQ to XML axis</span></span>|  
|----------------|----------------------|  
|<span data-ttu-id="4edb6-174">child (既定の軸)</span><span class="sxs-lookup"><span data-stu-id="4edb6-174">child (the default axis)</span></span>|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-175">Parent (..)</span><span class="sxs-lookup"><span data-stu-id="4edb6-175">Parent (..)</span></span>|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-176">attribute 軸 (@)</span><span class="sxs-lookup"><span data-stu-id="4edb6-176">attribute axis (@)</span></span>|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="4edb6-177">or</span><span class="sxs-lookup"><span data-stu-id="4edb6-177">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-178">ancestor 軸</span><span class="sxs-lookup"><span data-stu-id="4edb6-178">ancestor axis</span></span>|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-179">ancestor-or-self 軸</span><span class="sxs-lookup"><span data-stu-id="4edb6-179">ancestor-or-self axis</span></span>|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-180">descendant 軸 (//)</span><span class="sxs-lookup"><span data-stu-id="4edb6-180">descendant axis (//)</span></span>|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="4edb6-181">、または</span><span class="sxs-lookup"><span data-stu-id="4edb6-181">or</span></span><br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-182">descendant-or-self</span><span class="sxs-lookup"><span data-stu-id="4edb6-182">descendant-or-self</span></span>|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="4edb6-183">、または</span><span class="sxs-lookup"><span data-stu-id="4edb6-183">or</span></span><br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-184">following-sibling</span><span class="sxs-lookup"><span data-stu-id="4edb6-184">following-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="4edb6-185">、または</span><span class="sxs-lookup"><span data-stu-id="4edb6-185">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-186">preceding-sibling</span><span class="sxs-lookup"><span data-stu-id="4edb6-186">preceding-sibling</span></span>|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> <span data-ttu-id="4edb6-187">or</span><span class="sxs-lookup"><span data-stu-id="4edb6-187">or</span></span><br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="4edb6-188">following</span><span class="sxs-lookup"><span data-stu-id="4edb6-188">following</span></span>|<span data-ttu-id="4edb6-189">同等の軸はありません。</span><span class="sxs-lookup"><span data-stu-id="4edb6-189">No direct equivalent.</span></span>|  
|<span data-ttu-id="4edb6-190">preceding</span><span class="sxs-lookup"><span data-stu-id="4edb6-190">preceding</span></span>|<span data-ttu-id="4edb6-191">同等の軸はありません。</span><span class="sxs-lookup"><span data-stu-id="4edb6-191">No direct equivalent.</span></span>|  
  