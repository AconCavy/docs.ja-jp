---
title: '方法 : 省略可能な要素をフィルター処理する'
ms.date: 07/20/2015
ms.assetid: a74b76ad-6889-4185-a189-d6ef2c63841e
ms.openlocfilehash: e67cb58710d49a19f322b3555efa96ac69b9f654
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353051"
---
# <a name="how-to-filter-on-an-optional-element-visual-basic"></a><span data-ttu-id="8787d-102">How to: Filter on an Optional Element (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8787d-102">How to: Filter on an Optional Element (Visual Basic)</span></span>
<span data-ttu-id="8787d-103">要素に対するフィルター処理が、その要素が XML ドキュメント内に存在しているかどうか明確でない場合でも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="8787d-103">Sometimes you want to filter for an element even though you are not sure it exists in your XML document.</span></span> <span data-ttu-id="8787d-104">特定の要素が子要素を持たない場合、その要素に対するフィルター処理によって null 参照例外が発生しないように検索を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8787d-104">The search should be executed so that if the particular element does not have the child element, you do not trigger a null reference exception by filtering for it.</span></span> <span data-ttu-id="8787d-105">次の例では、`Child5` 要素には `Type` 子要素はありませんが、クエリは正常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="8787d-105">In the following example, the `Child5` element does not have a `Type` child element, but the query still executes correctly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8787d-106">例</span><span class="sxs-lookup"><span data-stu-id="8787d-106">Example</span></span>  
 <span data-ttu-id="8787d-107">この例では、<xref:System.Xml.Linq.Extensions.Elements%2A> 拡張メソッドを使用しています。</span><span class="sxs-lookup"><span data-stu-id="8787d-107">This example uses the <xref:System.Xml.Linq.Extensions.Elements%2A> extension method.</span></span>  
  
```vb  
Dim root As XElement = _   
    <Root>  
        <Child1>  
            <Text>Child One Text</Text>  
            <Type Value="Yes"/>  
        </Child1>  
        <Child2>  
            <Text>Child Two Text</Text>  
            <Type Value="Yes"/>  
        </Child2>  
        <Child3>  
            <Text>Child Three Text</Text>  
            <Type Value="No"/>  
        </Child3>  
        <Child4>  
            <Text>Child Four Text</Text>  
            <Type Value="Yes"/>  
        </Child4>  
        <Child5>  
            <Text>Child Five Text</Text>  
        </Child5>  
    </Root>  
Dim cList As IEnumerable(Of String) = _  
    From typeElement In root.Elements().<Type> _  
    Where typeElement.@Value = "Yes" _  
    Select typeElement.Parent.<Text>.Value  
Dim str As String  
For Each str In cList  
    Console.WriteLine(str)  
Next  
```  
  
 <span data-ttu-id="8787d-108">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8787d-108">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="example"></a><span data-ttu-id="8787d-109">例</span><span class="sxs-lookup"><span data-stu-id="8787d-109">Example</span></span>  
 <span data-ttu-id="8787d-110">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="8787d-110">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="8787d-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="8787d-111">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child1>  
                    <Text>Child One Text</Text>  
                    <Type Value="Yes"/>  
                </Child1>  
                <Child2>  
                    <Text>Child Two Text</Text>  
                    <Type Value="Yes"/>  
                </Child2>  
                <Child3>  
                    <Text>Child Three Text</Text>  
                    <Type Value="No"/>  
                </Child3>  
                <Child4>  
                    <Text>Child Four Text</Text>  
                    <Type Value="Yes"/>  
                </Child4>  
                <Child5>  
                    <Text>Child Five Text</Text>  
                </Child5>  
            </Root>  
        Dim cList As IEnumerable(Of String) = _  
            From typeElement In root.Elements().<Type> _  
            Where typeElement.@Value = "Yes" _  
            Select typeElement.Parent.<Text>.Value  
        Dim str As String  
        For Each str In cList  
            Console.WriteLine(str)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="8787d-112">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8787d-112">This code produces the following output:</span></span>  
  
```console  
Child One Text  
Child Two Text  
Child Four Text  
```  
  
## <a name="see-also"></a><span data-ttu-id="8787d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="8787d-113">See also</span></span>

- <xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.Extensions.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="8787d-114">Basic Queries (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8787d-114">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
- [<span data-ttu-id="8787d-115">XML 子軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="8787d-115">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="8787d-116">XML 属性軸プロパティ</span><span class="sxs-lookup"><span data-stu-id="8787d-116">XML Attribute Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)
- [<span data-ttu-id="8787d-117">XML Value プロパティ</span><span class="sxs-lookup"><span data-stu-id="8787d-117">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="8787d-118">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8787d-118">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8787d-119">Projection Operations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8787d-119">Projection Operations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/projection-operations.md)
