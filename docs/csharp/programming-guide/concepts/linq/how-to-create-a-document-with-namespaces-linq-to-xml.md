---
title: 名前空間を持つドキュメントを作成する方法 (C#) (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 37e63c57-f86d-47ac-88a7-2c2d107def30
ms.openlocfilehash: 429b0b0b41f2201b983f931e469b25ff406b91ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141324"
---
# <a name="how-to-create-a-document-with-namespaces-c-linq-to-xml"></a><span data-ttu-id="20c0e-102">名前空間を持つドキュメントを作成する方法 (C#) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="20c0e-102">How to create a document with namespaces (C#) (LINQ to XML)</span></span>
<span data-ttu-id="20c0e-103">このトピックでは、名前空間を持つドキュメントを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-103">This topic shows how to create documents with namespaces.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20c0e-104">例</span><span class="sxs-lookup"><span data-stu-id="20c0e-104">Example</span></span>  
 <span data-ttu-id="20c0e-105">名前空間にある要素や属性を作成するには、最初に <xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して初期化します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-105">To create an element or an attribute that is in a namespace, you first declare and initialize an <xref:System.Xml.Linq.XNamespace> object.</span></span> <span data-ttu-id="20c0e-106">次に、加算演算子オーバーロードを使用して名前空間をローカル名に連結し、文字列として表します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-106">You then use the addition operator overload to combine the namespace with the local name, expressed as a string.</span></span>  
  
 <span data-ttu-id="20c0e-107">次の例では、1 つの名前空間を持つドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-107">The following example creates a document with one namespace.</span></span> <span data-ttu-id="20c0e-108">既定では、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] によって、このドキュメントが既定の名前空間でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-108">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] serializes this document with a default namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="20c0e-109">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-109">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child>child content</Child>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="20c0e-110">例</span><span class="sxs-lookup"><span data-stu-id="20c0e-110">Example</span></span>  
 <span data-ttu-id="20c0e-111">次の例では、1 つの名前空間を持つドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-111">The following example creates a document with one namespace.</span></span> <span data-ttu-id="20c0e-112">名前空間プレフィックスを持つ名前空間を宣言する属性も作成します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-112">It also creates an attribute that declares the namespace with a namespace prefix.</span></span> <span data-ttu-id="20c0e-113">プレフィックス付きの名前空間を宣言する属性を作成するには、属性名が名前空間プレフィックスで、この名前が <xref:System.Xml.Linq.XNamespace.Xmlns%2A> 名前空間にある属性を作成します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-113">To create an attribute that declares a namespace with a prefix, you create an attribute where the name of the attribute is the namespace prefix, and this name is in the <xref:System.Xml.Linq.XNamespace.Xmlns%2A> namespace.</span></span> <span data-ttu-id="20c0e-114">この属性の値は名前空間の URI です。</span><span class="sxs-lookup"><span data-stu-id="20c0e-114">The value of this attribute is the URI of the namespace.</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement(aw + "Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="20c0e-115">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-115">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="20c0e-116">例</span><span class="sxs-lookup"><span data-stu-id="20c0e-116">Example</span></span>  
 <span data-ttu-id="20c0e-117">次の例では、2 つの名前空間が含まれるドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-117">The following example shows the creation of a document that contains two namespaces.</span></span> <span data-ttu-id="20c0e-118">1 つは既定の名前空間です。</span><span class="sxs-lookup"><span data-stu-id="20c0e-118">One is the default namespace.</span></span> <span data-ttu-id="20c0e-119">もう 1 つは、プレフィックスを持つ名前空間です。</span><span class="sxs-lookup"><span data-stu-id="20c0e-119">Another is a namespace with a prefix.</span></span>  
  
 <span data-ttu-id="20c0e-120">ルート要素に名前空間属性を含めることによって名前空間がシリアル化され、`http://www.adventure-works.com` が既定の名前空間となり、`www.fourthcoffee.com` はプレフィックス "fc" でシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-120">By including namespace attributes in the root element, the namespaces are serialized so that `http://www.adventure-works.com` is the default namespace, and `www.fourthcoffee.com` is serialized with a prefix of "fc".</span></span> <span data-ttu-id="20c0e-121">既定の名前空間を宣言する属性を作成するには、"xmlns" という名前の属性を、名前空間を指定せずに作成します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-121">To create an attribute that declares a default namespace, you create an attribute with the name "xmlns", without a namespace.</span></span> <span data-ttu-id="20c0e-122">属性の値は、既定の名前空間 URI です。</span><span class="sxs-lookup"><span data-stu-id="20c0e-122">The value of the attribute is the default namespace URI.</span></span>  
  
```csharp  
// The http://www.adventure-works.com namespace is forced to be the default namespace.  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute("xmlns", "http://www.adventure-works.com"),  
    new XAttribute(XNamespace.Xmlns + "fc", "www.fourthcoffee.com"),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="20c0e-123">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-123">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <DifferentChild>other content</DifferentChild>  
  </fc:Child>  
  <Child2>c2 content</Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</Root>  
```  
  
## <a name="example"></a><span data-ttu-id="20c0e-124">例</span><span class="sxs-lookup"><span data-stu-id="20c0e-124">Example</span></span>  
 <span data-ttu-id="20c0e-125">次の例では、名前空間プレフィックスのある名前空間を 2 つ含むドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-125">The following example creates a document that contains two namespaces, both with namespace prefixes.</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XNamespace fc = "www.fourthcoffee.com";  
XElement root = new XElement(aw + "Root",  
    new XAttribute(XNamespace.Xmlns + "aw", aw.NamespaceName),  
    new XAttribute(XNamespace.Xmlns + "fc", fc.NamespaceName),  
    new XElement(fc + "Child",  
        new XElement(aw + "DifferentChild", "other content")  
    ),  
    new XElement(aw + "Child2", "c2 content"),  
    new XElement(fc + "Child3", "c3 content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="20c0e-126">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-126">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" xmlns:fc="www.fourthcoffee.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="example"></a><span data-ttu-id="20c0e-127">例</span><span class="sxs-lookup"><span data-stu-id="20c0e-127">Example</span></span>  
 <span data-ttu-id="20c0e-128"><xref:System.Xml.Linq.XNamespace> オブジェクトを宣言して作成する代わりに、展開名を使用しても同じ結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-128">Another way to accomplish the same result is to use expanded names instead of declaring and creating an <xref:System.Xml.Linq.XNamespace> object.</span></span>  
  
 <span data-ttu-id="20c0e-129">ただし、この方法はパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-129">This approach has performance implications.</span></span> <span data-ttu-id="20c0e-130">拡張名が含まれた文字列を [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] に渡すたびに、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] は名前を解析して、アトミック化された名前空間を検索し、アトミック化された名前を見つける必要があります。</span><span class="sxs-lookup"><span data-stu-id="20c0e-130">Each time you pass a string that contains an expanded name to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] must parse the name, find the atomized namespace, and find the atomized name.</span></span> <span data-ttu-id="20c0e-131">この処理は CPU 時間を消費します。</span><span class="sxs-lookup"><span data-stu-id="20c0e-131">This process takes CPU time.</span></span> <span data-ttu-id="20c0e-132">パフォーマンスが重要な場合には、<xref:System.Xml.Linq.XNamespace> オブジェクトを明示的に宣言して使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="20c0e-132">If performance is important, you might want to declare and use an <xref:System.Xml.Linq.XNamespace> object explicitly.</span></span>  
  
 <span data-ttu-id="20c0e-133">パフォーマンスが重要な場合、詳細については、「[XName オブジェクトの事前アトミック化 (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="20c0e-133">If performance is an important issue, see [Pre-Atomization of XName Objects (LINQ to XML) (C#)](./pre-atomization-of-xname-objects-linq-to-xml.md) for more information</span></span>  
  
```csharp  
// Create an XML tree in a namespace, with a specified prefix  
XElement root = new XElement("{http://www.adventure-works.com}Root",  
    new XAttribute(XNamespace.Xmlns + "aw", "http://www.adventure-works.com"),  
    new XElement("{http://www.adventure-works.com}Child", "child content")  
);  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="20c0e-134">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="20c0e-134">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Child>child content</aw:Child>  
</aw:Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20c0e-135">参照</span><span class="sxs-lookup"><span data-stu-id="20c0e-135">See also</span></span>

- [<span data-ttu-id="20c0e-136">名前空間の概要 (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="20c0e-136">Namespaces Overview (LINQ to XML) (C#)</span></span>](namespaces-overview-linq-to-xml.md)
