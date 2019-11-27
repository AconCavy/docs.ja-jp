---
title: XAttribute クラスの概要
ms.date: 07/20/2015
ms.assetid: 7781580a-9583-4a1b-ae1e-91c5936eb0b1
ms.openlocfilehash: 00aeeec3f251ecd1d21a313290326b3ba49d63d3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349326"
---
# <a name="xattribute-class-overview-visual-basic"></a><span data-ttu-id="d54bd-102">XAttribute クラスの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d54bd-102">XAttribute Class Overview (Visual Basic)</span></span>
<span data-ttu-id="d54bd-103">属性は、要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="d54bd-103">Attributes are name/value pairs that are associated with an element.</span></span> <span data-ttu-id="d54bd-104"><xref:System.Xml.Linq.XAttribute> クラスは、XML 属性を表します。</span><span class="sxs-lookup"><span data-stu-id="d54bd-104">The <xref:System.Xml.Linq.XAttribute> class represents XML attributes.</span></span>  
  
## <a name="overview"></a><span data-ttu-id="d54bd-105">概要</span><span class="sxs-lookup"><span data-stu-id="d54bd-105">Overview</span></span>  
 <span data-ttu-id="d54bd-106">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] での属性の操作は、要素の操作に似ています。</span><span class="sxs-lookup"><span data-stu-id="d54bd-106">Working with attributes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is similar to working with elements.</span></span> <span data-ttu-id="d54bd-107">コンストラクターはほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="d54bd-107">Their constructors are similar.</span></span> <span data-ttu-id="d54bd-108">それぞれのコレクションの取得に使用するメソッドもほぼ同じです。</span><span class="sxs-lookup"><span data-stu-id="d54bd-108">The methods that you use to retrieve collections of them are similar.</span></span> <span data-ttu-id="d54bd-109">属性のコレクションの [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式は、要素のコレクションの [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ式とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="d54bd-109">A [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of attributes looks very similar to a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression for a collection of elements.</span></span>  
  
 <span data-ttu-id="d54bd-110">属性が要素に追加された順序は保持されます。</span><span class="sxs-lookup"><span data-stu-id="d54bd-110">The order in which attributes were added to an element is preserved.</span></span> <span data-ttu-id="d54bd-111">つまり、属性を反復処理する場合、属性は追加された順序と同じ順序で表示されます。</span><span class="sxs-lookup"><span data-stu-id="d54bd-111">That is, when you iterate through the attributes, you see them in the same order that they were added.</span></span>  
  
## <a name="the-xattribute-constructor"></a><span data-ttu-id="d54bd-112">XAttribute コンストラクター</span><span class="sxs-lookup"><span data-stu-id="d54bd-112">The XAttribute Constructor</span></span>  
 <span data-ttu-id="d54bd-113">最もよく使用する <xref:System.Xml.Linq.XAttribute> クラスのコンストラクターを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d54bd-113">The following constructor of the <xref:System.Xml.Linq.XAttribute> class is the one that you will most commonly use:</span></span>  
  
|<span data-ttu-id="d54bd-114">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="d54bd-114">Constructor</span></span>|<span data-ttu-id="d54bd-115">説明</span><span class="sxs-lookup"><span data-stu-id="d54bd-115">Description</span></span>|  
|-----------------|-----------------|  
|`XAttribute(XName name, object content)`|<span data-ttu-id="d54bd-116"><xref:System.Xml.Linq.XAttribute> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d54bd-116">Creates an <xref:System.Xml.Linq.XAttribute> object.</span></span> <span data-ttu-id="d54bd-117">`name` 引数には属性の名前を指定し、`content` には属性のコンテンツを指定します。</span><span class="sxs-lookup"><span data-stu-id="d54bd-117">The `name` argument specifies the name of the attribute; `content` specifies the content of the attribute.</span></span>|  
  
### <a name="creating-an-element-with-an-attribute"></a><span data-ttu-id="d54bd-118">属性を持つ要素の作成</span><span class="sxs-lookup"><span data-stu-id="d54bd-118">Creating an Element with an Attribute</span></span>  
 <span data-ttu-id="d54bd-119">次のコードは、Visual Basic で XML リテラルを使用して属性を含む要素を示しています。</span><span class="sxs-lookup"><span data-stu-id="d54bd-119">The following code shows an element that contains an attribute using XML literals in Visual Basic:</span></span>  
  
```vb  
Dim phone As XElement = <Phone Type="Home">555-555-5555</Phone>  
Console.WriteLine(phone)  
```  
  
 <span data-ttu-id="d54bd-120">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d54bd-120">This example produces the following output:</span></span>  
  
```xml  
<Phone Type="Home">555-555-5555</Phone>  
```  
  
### <a name="functional-construction-of-attributes"></a><span data-ttu-id="d54bd-121">属性の関数型構築</span><span class="sxs-lookup"><span data-stu-id="d54bd-121">Functional Construction of Attributes</span></span>  
 <span data-ttu-id="d54bd-122"><xref:System.Xml.Linq.XAttribute> オブジェクトは、<xref:System.Xml.Linq.XElement> オブジェクトの構築と共にインラインで構築できます。</span><span class="sxs-lookup"><span data-stu-id="d54bd-122">You can construct <xref:System.Xml.Linq.XAttribute> objects in-line with the construction of <xref:System.Xml.Linq.XElement> objects, as follows:</span></span>  
  
```vb  
Dim c As XElement = _  
    <Customers>  
        <Customer>  
            <Name>John Doe</Name>  
            <PhoneNumbers>  
                <Phone type="home">555-555-5555</Phone>  
                <Phone type="work">666-666-6666</Phone>  
            </PhoneNumbers>  
        </Customer>  
    </Customers>  
Console.WriteLine(c)  
```  
  
 <span data-ttu-id="d54bd-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d54bd-123">This example produces the following output:</span></span>  
  
```xml  
<Customers>  
  <Customer>  
    <Name>John Doe</Name>  
    <PhoneNumbers>  
      <Phone type="home">555-555-5555</Phone>  
      <Phone type="work">666-666-6666</Phone>  
    </PhoneNumbers>  
  </Customer>  
</Customers>  
```  
  
### <a name="attributes-are-not-nodes"></a><span data-ttu-id="d54bd-124">属性はノードではない</span><span class="sxs-lookup"><span data-stu-id="d54bd-124">Attributes Are Not Nodes</span></span>  
 <span data-ttu-id="d54bd-125">属性と要素には、いくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="d54bd-125">There are some differences between attributes and elements.</span></span> <span data-ttu-id="d54bd-126"><xref:System.Xml.Linq.XAttribute> オブジェクトは、XML ツリーのノードではありません。</span><span class="sxs-lookup"><span data-stu-id="d54bd-126"><xref:System.Xml.Linq.XAttribute> objects are not nodes in the XML tree.</span></span> <span data-ttu-id="d54bd-127">属性は、XML 要素に関連付けられている名前と値のペアです。</span><span class="sxs-lookup"><span data-stu-id="d54bd-127">They are name/value pairs associated with an XML element.</span></span> <span data-ttu-id="d54bd-128">ドキュメント オブジェクト モデル (DOM) とは異なり、XML の構造をより密接に反映します。</span><span class="sxs-lookup"><span data-stu-id="d54bd-128">In contrast to the Document Object Model (DOM), this more closely reflects the structure of XML.</span></span> <span data-ttu-id="d54bd-129"><xref:System.Xml.Linq.XAttribute> オブジェクトは実際には XML ツリーのノードではありませんが、<xref:System.Xml.Linq.XAttribute> オブジェクトの操作は <xref:System.Xml.Linq.XElement> オブジェクトの操作とよく似ています。</span><span class="sxs-lookup"><span data-stu-id="d54bd-129">Although <xref:System.Xml.Linq.XAttribute> objects are not actually nodes in the XML tree, working with <xref:System.Xml.Linq.XAttribute> objects is very similar to working with <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="d54bd-130">属性と要素の区別は主に、ノード レベルで XML ツリーを操作するコードを記述する開発者にとってのみ重要な意味を持ちます。</span><span class="sxs-lookup"><span data-stu-id="d54bd-130">This distinction is primarily important only to developers who are writing code that works with XML trees at the node level.</span></span> <span data-ttu-id="d54bd-131">多くの開発者は、この区別を考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d54bd-131">Many developers will not be concerned with this distinction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54bd-132">参照</span><span class="sxs-lookup"><span data-stu-id="d54bd-132">See also</span></span>

- [<span data-ttu-id="d54bd-133">LINQ to XML プログラミングの概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d54bd-133">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
