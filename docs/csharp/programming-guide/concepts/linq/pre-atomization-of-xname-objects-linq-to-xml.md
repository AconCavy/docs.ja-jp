---
title: XName オブジェクトの事前アトミック化 (LINQ to XML) (C#)
description: XName オブジェクトの事前アトミック化について説明します。 オブジェクトの事前アトミック化によって、特定の名前が繰り返される大きな XML ツリーを作成する場合のパフォーマンスが向上します。
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 4d217f6c78dc5d83ce424fb3ba95785f2dac0b73
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302829"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="874ad-104">XName オブジェクトの事前アトミック化 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="874ad-104">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="874ad-105">LINQ to XML でパフォーマンスを向上させる方法の 1 つは、<xref:System.Xml.Linq.XName> オブジェクトの事前アトミック化です。</span><span class="sxs-lookup"><span data-stu-id="874ad-105">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="874ad-106">事前アトミック化とは、<xref:System.Xml.Linq.XName> クラスと <xref:System.Xml.Linq.XElement> クラスのコンストラクターを使用して XML ツリーを作成する前に、文字列を <xref:System.Xml.Linq.XAttribute> オブジェクトに割り当てる操作です。</span><span class="sxs-lookup"><span data-stu-id="874ad-106">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="874ad-107">次に、(文字列から <xref:System.Xml.Linq.XName> への暗黙的な変換を使用する) コンストラクターに文字列を渡す代わりに、初期化された <xref:System.Xml.Linq.XName> オブジェクトを渡します。</span><span class="sxs-lookup"><span data-stu-id="874ad-107">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="874ad-108">これによって、特定の名前が繰り返される大きい XML ツリーを作成するときにパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="874ad-108">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="874ad-109">これを行うには、XML ツリーを構築する前に、<xref:System.Xml.Linq.XName> オブジェクトを宣言して初期化し、次に要素名と属性名に文字列を指定する代わりに <xref:System.Xml.Linq.XName> オブジェクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="874ad-109">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="874ad-110">この手法では、同じ名前の多数の要素や属性を作成する場合に、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="874ad-110">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="874ad-111">各自のシナリオで事前アトミック化をテストし、使用すべきかどうかを判断してください。</span><span class="sxs-lookup"><span data-stu-id="874ad-111">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="874ad-112">例</span><span class="sxs-lookup"><span data-stu-id="874ad-112">Example</span></span>  
 <span data-ttu-id="874ad-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="874ad-113">The following example demonstrates this.</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="874ad-114">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="874ad-114">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="874ad-115">次の例は同じ手法を示し、XML ドキュメントが名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="874ad-115">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="874ad-116">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="874ad-116">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="874ad-117">次に示すのは、より実働環境に近い例です。</span><span class="sxs-lookup"><span data-stu-id="874ad-117">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="874ad-118">この例では、要素の内容がクエリによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="874ad-118">In this example, the content of the element is supplied by a query:</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 <span data-ttu-id="874ad-119">前の例では、名前が事前アトミック化されていない次の例に比べて良いパフォーマンスが得られます。</span><span class="sxs-lookup"><span data-stu-id="874ad-119">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="874ad-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="874ad-120">See also</span></span>

- [<span data-ttu-id="874ad-121">アトミック化された XName および XNamespace オブジェクト (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="874ad-121">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
