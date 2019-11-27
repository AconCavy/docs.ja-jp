---
title: グローバル名前空間の使用 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 0a8064d5-e02f-4315-ad48-6deaa443a2f0
ms.openlocfilehash: 80510e370e0a9c7ab27cb5177d9b547ead82715c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350996"
---
# <a name="working-with-global-namespaces-visual-basic-linq-to-xml"></a><span data-ttu-id="91da2-102">グローバル名前空間の使用 (Visual Basic) (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="91da2-102">Working with Global Namespaces (Visual Basic) (LINQ to XML)</span></span>
<span data-ttu-id="91da2-103">Visual Basic の XML リテラルの主な機能の1つに、`Imports` ステートメントを使用して XML 名前空間を宣言する機能があります。</span><span class="sxs-lookup"><span data-stu-id="91da2-103">One of the key features of XML literals in Visual Basic is the capability to declare XML namespaces by using the `Imports` statement.</span></span> <span data-ttu-id="91da2-104">この機能を使用することで、プレフィックスを使用する XML 名前空間または既定の XML 名前空間を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="91da2-104">Using this feature, you can declare an XML namespace that uses a prefix, or you can declare a default XML namespace.</span></span>  
  
 <span data-ttu-id="91da2-105">この機能は 2 つの状況で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="91da2-105">This capability is useful in two situations.</span></span> <span data-ttu-id="91da2-106">1 つは、XML リテラルで宣言された名前空間が組み込み式に引き継がれない場合です。</span><span class="sxs-lookup"><span data-stu-id="91da2-106">First, namespaces declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="91da2-107">グローバル名前空間を宣言すると、名前空間を伴う組み込み式を使用する必要がある場合の作業が軽減されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-107">Declaring global namespaces reduces the amount of work that you have to do to use embedded expressions with namespaces.</span></span> <span data-ttu-id="91da2-108">もう 1 つは、名前空間と XML プロパティを併用するためにグローバル名前空間を宣言する必要がある場合です。</span><span class="sxs-lookup"><span data-stu-id="91da2-108">Second, you must declare global namespaces in order to use namespaces with XML properties.</span></span>  
  
 <span data-ttu-id="91da2-109">グローバル名前空間はプロジェクト レベルで宣言できます。</span><span class="sxs-lookup"><span data-stu-id="91da2-109">You can declare global namespaces at the project level.</span></span> <span data-ttu-id="91da2-110">また、モジュール レベルでもグローバル名前空間を宣言できます。その場合、プロジェクト レベルのグローバル名前空間はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="91da2-110">You can also declare global namespaces at the module level, which overrides the project-level global namespaces.</span></span> <span data-ttu-id="91da2-111">最終的に、グローバル名前空間は XML リテラルでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="91da2-111">Finally, you can override global namespaces in an XML literal.</span></span>  
  
 <span data-ttu-id="91da2-112">グローバルに宣言された名前空間に含まれる XML リテラルまたは XML プロパティを使用する場合は、Visual Studio で XML リテラルまたはプロパティにカーソルを合わせることで、それらの展開名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-112">When using XML literals or XML properties that are in globally-declared namespaces, you can see the expanded name of XML literals or properties by hovering over them in Visual Studio.</span></span> <span data-ttu-id="91da2-113">拡張名はツールヒントに表示されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-113">You will see the expanded name in a tooltip.</span></span>  
  
 <span data-ttu-id="91da2-114">グローバル名前空間に対応する <xref:System.Xml.Linq.XNamespace> オブジェクトを取得するには、`GetXmlNamespace` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="91da2-114">You can get an <xref:System.Xml.Linq.XNamespace> object that corresponds to a global namespace using the `GetXmlNamespace` method.</span></span>  
  
## <a name="examples-of-global-namespaces"></a><span data-ttu-id="91da2-115">グローバル名前空間の例</span><span class="sxs-lookup"><span data-stu-id="91da2-115">Examples of Global Namespaces</span></span>  
 <span data-ttu-id="91da2-116">次の例では、`Imports` ステートメントを使用して既定のグローバル名前空間を宣言し、XML リテラルを使用してその名前空間内の <xref:System.Xml.Linq.XElement> オブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="91da2-116">The following example declares a default global namespace by using the `Imports` statement, and then uses an XML literal to initialize an <xref:System.Xml.Linq.XElement> object in that namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="91da2-117">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-117">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com" />  
```  
  
 <span data-ttu-id="91da2-118">次の例では、プレフィックスを持つグローバル名前空間を宣言し、XML リテラルを使用して要素を初期化します。</span><span class="sxs-lookup"><span data-stu-id="91da2-118">The following example declares a global namespace with a prefix, and then uses an XML literal to initialize an element:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="91da2-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-119">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com" />  
```  
  
## <a name="global-namespaces-and-embedded-expressions"></a><span data-ttu-id="91da2-120">グローバル名前空間と組み込み式</span><span class="sxs-lookup"><span data-stu-id="91da2-120">Global Namespaces and Embedded Expressions</span></span>  
 <span data-ttu-id="91da2-121">XML リテラルで宣言される名前空間は、組み込み式に引き継がれません。</span><span class="sxs-lookup"><span data-stu-id="91da2-121">Namespaces that are declared in XML literals do not carry over into embedded expressions.</span></span> <span data-ttu-id="91da2-122">次の例では、既定の名前空間を宣言しています。</span><span class="sxs-lookup"><span data-stu-id="91da2-122">The following example declares a default namespace.</span></span> <span data-ttu-id="91da2-123">さらに、`Child` 要素に組み込み式を使用しています。</span><span class="sxs-lookup"><span data-stu-id="91da2-123">It then uses an embedded expression for the `Child` element.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="91da2-124">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-124">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="" />  
</Root>  
```  
  
 <span data-ttu-id="91da2-125">このように、結果の XML では、`Child` 要素がどの名前空間にも属さないように、既定の名前空間の宣言が含まれています。</span><span class="sxs-lookup"><span data-stu-id="91da2-125">As you can see, the resulting XML includes a declaration of a default namespace so that the `Child` element is in no namespace.</span></span>  
  
 <span data-ttu-id="91da2-126">次のように、組み込み式で名前空間を再宣言できます。</span><span class="sxs-lookup"><span data-stu-id="91da2-126">You could re-declare the namespace in the embedded expression, as follows:</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <%= <Child xmlns="http://www.adventure-works.com"/> %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 <span data-ttu-id="91da2-127">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-127">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child xmlns="http://www.adventure-works.com" />  
</Root>  
```  
  
 <span data-ttu-id="91da2-128">ただし、この方法は既定のグローバル名前空間よりも使い方が複雑であり、既定のグローバル名前空間を使用するアプローチの方がより適切です。</span><span class="sxs-lookup"><span data-stu-id="91da2-128">However, this is more cumbersome to use than the global default namespace, which is a better approach.</span></span> <span data-ttu-id="91da2-129">既定のグローバル名前空間を使用すると、名前空間を宣言せずに XML リテラルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="91da2-129">With the global default namespace, you can use XML literals without declaring namespaces.</span></span> <span data-ttu-id="91da2-130">結果の XML は、グローバルに宣言された既定の名前空間に含まれることになります。</span><span class="sxs-lookup"><span data-stu-id="91da2-130">The resulting XML will be in the globally-declared default namespace.</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <Root>  
                                   <%= <Child/> %>  
                               </Root>  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="91da2-131">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-131">This example produces the following output:</span></span>  
  
```xml  
<Root xmlns="http://www.adventure-works.com">  
  <Child />  
</Root>  
```  
  
## <a name="using-namespaces-with-xml-properties"></a><span data-ttu-id="91da2-132">名前空間と XML プロパティの併用</span><span class="sxs-lookup"><span data-stu-id="91da2-132">Using Namespaces with XML Properties</span></span>  
 <span data-ttu-id="91da2-133">名前空間に含まれている XML ツリーを操作する場合に XML プロパティを使用するときは、XML プロパティが正しい名前空間に含まれるように、グローバル名前空間を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="91da2-133">If you are working with an XML tree that is in a namespace, and you use XML properties, then you must use a global namespace so that the XML properties will also be in the correct namespace.</span></span> <span data-ttu-id="91da2-134">次の例では、名前空間内で XML ツリーを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="91da2-134">The following example declares an XML tree in a namespace.</span></span> <span data-ttu-id="91da2-135">さらに、`Child` 要素の数を出力しています。</span><span class="sxs-lookup"><span data-stu-id="91da2-135">It then prints the count of `Child` elements.</span></span>  
  
```vb  
Dim root As XElement = _  
    <Root xmlns="http://www.adventure-works.com">  
        <Child>content</Child>  
    </Root>  
Console.WriteLine(root.<Child>.Count())  
```  
  
 <span data-ttu-id="91da2-136">この例は `Child` 要素が存在しないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="91da2-136">This example indicates that there are no `Child` elements.</span></span> <span data-ttu-id="91da2-137">生成される出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="91da2-137">It produces the following output:</span></span>  
  
```console  
0  
```  
  
 <span data-ttu-id="91da2-138">ただし、既定のグローバル名前空間を宣言すると、XML リテラルと XML プロパティの両方が既定のグローバル名前空間に含まれます。</span><span class="sxs-lookup"><span data-stu-id="91da2-138">If, however, you declare a default global namespace, then both the XML literal and the XML property are in the default global namespace:</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root>  
                <Child>content</Child>  
            </Root>  
        Console.WriteLine(root.<Child>.Count())  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="91da2-139">この例は、`Child` 要素が 1 つ存在することを示しています。</span><span class="sxs-lookup"><span data-stu-id="91da2-139">This example indicates that there is one `Child` element.</span></span> <span data-ttu-id="91da2-140">生成される出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="91da2-140">It produces the following output:</span></span>  
  
```console  
1  
```  
  
 <span data-ttu-id="91da2-141">プレフィックスを持つグローバル名前空間を宣言すると、そのプレフィックスを XML リテラルと XML プロパティの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="91da2-141">If you declare a global namespace that has a prefix, you can use the prefix for both XML literals and XML properties:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <aw:Child>content</aw:Child>  
            </aw:Root>  
        Console.WriteLine(root.<aw:Child>.Count())  
    End Sub  
End Module  
```  
  
## <a name="xnamespace-and-global-namespaces"></a><span data-ttu-id="91da2-142">XNamespace とグローバル名前空間</span><span class="sxs-lookup"><span data-stu-id="91da2-142">XNamespace and Global Namespaces</span></span>  
 <span data-ttu-id="91da2-143"><xref:System.Xml.Linq.XNamespace> オブジェクトを取得するには、`GetXmlNamespace` メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="91da2-143">You can get an <xref:System.Xml.Linq.XNamespace> object by using the `GetXmlNamespace` method:</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = <aw:Root/>  
        Dim xn As XNamespace = GetXmlNamespace(aw)  
        Console.WriteLine(xn)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="91da2-144">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="91da2-144">This example produces the following output:</span></span>  
  
```console  
http://www.adventure-works.com  
```  
  
## <a name="see-also"></a><span data-ttu-id="91da2-145">参照</span><span class="sxs-lookup"><span data-stu-id="91da2-145">See also</span></span>

- [<span data-ttu-id="91da2-146">名前空間の概要 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="91da2-146">Namespaces Overview (LINQ to XML) (Visual Basic)</span></span>](namespaces-overview-linq-to-xml.md)
