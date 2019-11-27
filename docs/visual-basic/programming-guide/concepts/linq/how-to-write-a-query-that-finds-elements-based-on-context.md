---
title: '方法 : コンテキストに基づいて要素を検索するクエリを記述する'
ms.date: 07/20/2015
ms.assetid: 0b085290-ddc1-4126-aaa0-e4c95a3d9a09
ms.openlocfilehash: d25c6d47eee2ae092c84c3db3c08c3e21e7d98d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346215"
---
# <a name="how-to-write-a-query-that-finds-elements-based-on-context-visual-basic"></a><span data-ttu-id="73620-102">方法: コンテキストに基づいて要素を検索するクエリを記述する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73620-102">How to: Write a Query that Finds Elements Based on Context (Visual Basic)</span></span>
<span data-ttu-id="73620-103">コンテキストに基づいて要素を選択するクエリの記述が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="73620-103">Sometimes you might have to write a query that selects elements based on their context.</span></span> <span data-ttu-id="73620-104">つまり、前の兄弟要素や次の兄弟要素に基づいてフィルターしたり、</span><span class="sxs-lookup"><span data-stu-id="73620-104">You might want to filter based on preceding or following sibling elements.</span></span> <span data-ttu-id="73620-105">子要素や祖先要素に基づいてフィルターすることが必要になる場合が考えられます。</span><span class="sxs-lookup"><span data-stu-id="73620-105">You might want to filter based on child or ancestor elements.</span></span>  
  
 <span data-ttu-id="73620-106">これを実現するには、クエリを記述し、そのクエリの結果を `where` 句で使用します。</span><span class="sxs-lookup"><span data-stu-id="73620-106">You can do this by writing a query and using the results of the query in the `where` clause.</span></span> <span data-ttu-id="73620-107">最初に NULL に対してテストし、次に値をテストする必要がある場合は、`let` 句でクエリを実行し、次にその結果を `where` 句で使用する方が便利です。</span><span class="sxs-lookup"><span data-stu-id="73620-107">If you have to first test against null, and then test the value, it is more convenient to do the query in a `let` clause, and then use the results in the `where` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73620-108">例</span><span class="sxs-lookup"><span data-stu-id="73620-108">Example</span></span>  
 <span data-ttu-id="73620-109">次の例では、`p` 要素の直前の `ul` 要素をすべて選択します。</span><span class="sxs-lookup"><span data-stu-id="73620-109">The following example selects all `p` elements that are immediately followed by a `ul` element.</span></span>  
  
```vb  
Dim doc As XElement = _  
    <Root>  
        <p id='1'/>  
        <ul>abc</ul>  
        <Child>  
            <p id='2'/>  
            <notul/>  
            <p id='3'/>  
            <ul>def</ul>  
            <p id='4'/>  
        </Child>  
        <Child>  
            <p id='5'/>  
            <notul/>  
            <p id='6'/>  
            <ul>abc</ul>  
            <p id='7'/>  
        </Child>  
    </Root>  
  
Dim items As IEnumerable(Of XElement) = _  
    From e In doc...<p> _  
    Let z = e.ElementsAfterSelf().FirstOrDefault() _  
    Where z IsNot Nothing AndAlso z.Name.LocalName = "ul" _  
    Select e  
  
For Each e As XElement In items  
    Console.WriteLine("id = {0}", e.@<id>)  
Next  
```  
  
 <span data-ttu-id="73620-110">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="73620-110">This code produces the following output:</span></span>  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="example"></a><span data-ttu-id="73620-111">例</span><span class="sxs-lookup"><span data-stu-id="73620-111">Example</span></span>  
 <span data-ttu-id="73620-112">次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。</span><span class="sxs-lookup"><span data-stu-id="73620-112">The following example shows the same query for XML that is in a namespace.</span></span> <span data-ttu-id="73620-113">詳細については、「[名前空間の概要」 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="73620-113">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns='http://www.adatum.com'>  
  
Module Module1  
    Sub Main()  
        Dim doc As XElement = _  
            <Root>  
                <p id='1'/>  
                <ul>abc</ul>  
                <Child>  
                    <p id='2'/>  
                    <notul/>  
                    <p id='3'/>  
                    <ul>def</ul>  
                    <p id='4'/>  
                </Child>  
                <Child>  
                    <p id='5'/>  
                    <notul/>  
                    <p id='6'/>  
                    <ul>abc</ul>  
                    <p id='7'/>  
                </Child>  
            </Root>  
  
        Dim items As IEnumerable(Of XElement) = _  
            From e In doc...<p> _  
            Let z = e.ElementsAfterSelf().FirstOrDefault() _  
            Where z IsNot Nothing AndAlso z.Name = GetXmlNamespace().GetName("ul") _  
            Select e  
  
        For Each e As XElement In items  
            Console.WriteLine("id = {0}", e.@<id>)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="73620-114">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="73620-114">This code produces the following output:</span></span>  
  
```console  
id = 1  
id = 3  
id = 6  
```  
  
## <a name="see-also"></a><span data-ttu-id="73620-115">参照</span><span class="sxs-lookup"><span data-stu-id="73620-115">See also</span></span>

- <xref:System.Xml.Linq.XElement.Parse%2A>
- <xref:System.Xml.Linq.XContainer.Descendants%2A>
- <xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A>
- <xref:System.Linq.Enumerable.FirstOrDefault%2A>
- [<span data-ttu-id="73620-116">基本的なクエリ (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73620-116">Basic Queries (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
