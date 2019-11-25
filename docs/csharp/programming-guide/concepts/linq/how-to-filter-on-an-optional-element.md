---
title: 省略可能な要素をフィルター処理する方法 (C#)
ms.date: 07/20/2015
ms.assetid: f99e2f93-fca5-403f-8a0c-770761d4905a
ms.openlocfilehash: c9f844619cbb3d7a66ca66989baa900e0fd7bc2f
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141252"
---
# <a name="how-to-filter-on-an-optional-element-c"></a><span data-ttu-id="c1ab6-102">省略可能な要素をフィルター処理する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="c1ab6-102">How to filter on an optional element (C#)</span></span>
<span data-ttu-id="c1ab6-103">要素に対するフィルター処理が、その要素が XML ドキュメント内に存在しているかどうか明確でない場合でも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="c1ab6-104">特定の要素が子要素を持たない場合、その要素に対するフィルター処理によって null 参照例外が発生しないように検索を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="c1ab6-105">次の例では、`Child5` 要素には `Type` 子要素はありませんが、クエリは正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1ab6-106">例</span><span class="sxs-lookup"><span data-stu-id="c1ab6-106">Example</span></span>  
 <span data-ttu-id="c1ab6-107">この例では、<xref:System.Xml.Linq.Extensions.Elements%2A> 拡張メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
var cList =  
    from typeElement in root.Elements().Elements("Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element("Text");  
foreach(string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="c1ab6-108">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-108">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="c1ab6-109">例</span><span class="sxs-lookup"><span data-stu-id="c1ab6-109">Example</span></span>  
 <span data-ttu-id="c1ab6-110">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="c1ab6-111">詳細については、「[名前空間の概要 (LINQ to XML)](namespaces-overview-linq-to-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-111">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```csharp  
XElement root = XElement.Parse(@"<Root xmlns='http://www.adatum.com'>  
  <Child1>  
    <Text>Child One Text</Text>  
    <Type Value=""Yes""/>  
  </Child1>  
  <Child2>  
    <Text>Child Two Text</Text>  
    <Type Value=""Yes""/>  
  </Child2>  
  <Child3>  
    <Text>Child Three Text</Text>  
    <Type Value=""No""/>  
  </Child3>  
  <Child4>  
    <Text>Child Four Text</Text>  
    <Type Value=""Yes""/>  
  </Child4>  
  <Child5>  
    <Text>Child Five Text</Text>  
  </Child5>  
</Root>");  
XNamespace ad = "http://www.adatum.com";  
var cList =  
    from typeElement in root.Elements().Elements(ad + "Type")  
    where (string)typeElement.Attribute("Value") == "Yes"  
    select (string)typeElement.Parent.Element(ad + "Text");  
foreach (string str in cList)  
    Console.WriteLine(str);  
```  
  
 <span data-ttu-id="c1ab6-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c1ab6-112">This code produces the following output:</span></span>  
  
```output  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="c1ab6-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1ab6-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c1ab6-114">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="c1ab6-114">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="c1ab6-115">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="c1ab6-115">Projection Operations (C#)</span></span>](./projection-operations.md)
