---
title: '方法: 属性のコレクションを取得する (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: a07e9645-b45b-403b-b698-f652f904c7d2
ms.openlocfilehash: ff260660057c3b75f4cc92c37c67fca0a0b7f192
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347568"
---
# <a name="how-to-retrieve-a-collection-of-attributes-linq-to-xml-visual-basic"></a><span data-ttu-id="18ea5-102">方法: 属性のコレクションを取得する (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18ea5-102">How to: Retrieve a Collection of Attributes (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="18ea5-103">このトピックでは、<xref:System.Xml.Linq.XElement.Attributes%2A> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="18ea5-103">This topic introduces the <xref:System.Xml.Linq.XElement.Attributes%2A> method.</span></span> <span data-ttu-id="18ea5-104">このメソッドは、要素の属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="18ea5-104">This method retrieves the attributes of an element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18ea5-105">例</span><span class="sxs-lookup"><span data-stu-id="18ea5-105">Example</span></span>  
 <span data-ttu-id="18ea5-106">次の例では、要素の属性のコレクションを反復処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="18ea5-106">The following example shows how to iterate through the collection of attributes of an element.</span></span>  
  
```vb  
Dim val = _  
    <Value ID="1243" Type="int" ConvertableTo="double">100</Value>  
Dim listOfAttributes As IEnumerable(Of XAttribute) = _  
    From att In val.Attributes() _  
    Select att  
For Each att As XAttribute In listOfAttributes  
    Console.WriteLine(att)  
Next  
```  
  
 <span data-ttu-id="18ea5-107">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="18ea5-107">This code produces the following output:</span></span>  
  
```console  
ID="1243"  
Type="int"  
ConvertableTo="double"  
```  
  
## <a name="see-also"></a><span data-ttu-id="18ea5-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="18ea5-108">See also</span></span>

- [<span data-ttu-id="18ea5-109">LINQ to XML 軸 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18ea5-109">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
