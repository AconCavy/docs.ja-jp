---
title: '方法: 単一の属性を取得する (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 34c390fbffc1aea68a2fd8ae64b17d2637a1f4f1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397857"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="6594a-102">方法: 単一の属性を取得する (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6594a-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="6594a-103">このトピックでは、属性名を指定して要素の単一の属性を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6594a-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="6594a-104">これは、特定の属性を持つ要素を検索するクエリ式を記述する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="6594a-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="6594a-105"><xref:System.Xml.Linq.XElement.Attribute%2A> クラスの <xref:System.Xml.Linq.XElement> メソッドは、指定された名前を持つ <xref:System.Xml.Linq.XAttribute> を返します。</span><span class="sxs-lookup"><span data-stu-id="6594a-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6594a-106">例</span><span class="sxs-lookup"><span data-stu-id="6594a-106">Example</span></span>  
 <span data-ttu-id="6594a-107">次の例では、<xref:System.Xml.Linq.XElement.Attribute%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6594a-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="6594a-108">この例では、`Phone` という名前のツリー内のすべての子孫を検索し、次に `type` という名前の属性を検索します。</span><span class="sxs-lookup"><span data-stu-id="6594a-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="6594a-109">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6594a-109">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="6594a-110">例</span><span class="sxs-lookup"><span data-stu-id="6594a-110">Example</span></span>  
 <span data-ttu-id="6594a-111">属性の値を取得する場合は、<xref:System.Xml.Linq.XElement> オブジェクトを使用して行う場合と同じように、その属性をキャストできます。</span><span class="sxs-lookup"><span data-stu-id="6594a-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="6594a-112">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6594a-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="6594a-113">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6594a-113">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="6594a-114">では、`string`、`bool`、`bool?`、`int`、`int?`、`uint`、`uint?`、`long`、`long?`、`ulong`、`ulong?`、`float`、`float?`、`double`、`double?`、`decimal`、`decimal?`、`DateTime`、`DateTime?`、`TimeSpan`、`TimeSpan?`、`GUID`、および `GUID?` に対する <xref:System.Xml.Linq.XAttribute> クラスのための明示的なキャスト演算子が用意されています。</span><span class="sxs-lookup"><span data-stu-id="6594a-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6594a-115">例</span><span class="sxs-lookup"><span data-stu-id="6594a-115">Example</span></span>  
 <span data-ttu-id="6594a-116">上記と同じコードを使用して、名前空間内の属性を取得する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6594a-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="6594a-117">詳細については、「[名前空間の概要 (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6594a-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6594a-118">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="6594a-118">This code produces the following output:</span></span>  
  
```console  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="6594a-119">参照</span><span class="sxs-lookup"><span data-stu-id="6594a-119">See also</span></span>

- [<span data-ttu-id="6594a-120">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6594a-120">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
