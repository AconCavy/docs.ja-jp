---
title: LINQ to XML の概要
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ to XML [Visual Basic], about LINQ to XML
- LINQ [Visual Basic], LINQ to XML
ms.assetid: 01c62a79-6d58-468e-84fb-039c05947701
ms.openlocfilehash: 4ec1c96bdca96a6e9b68b240c147b70536514d85
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91099191"
---
# <a name="overview-of-linq-to-xml-in-visual-basic"></a><span data-ttu-id="5ee08-102">Visual Basic における LINQ to XML の概要</span><span class="sxs-lookup"><span data-stu-id="5ee08-102">Overview of LINQ to XML in Visual Basic</span></span>

<span data-ttu-id="5ee08-103">Visual Basic は、XML リテラルおよび XML 軸プロパティを使用した [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] のサポートを提供しています。</span><span class="sxs-lookup"><span data-stu-id="5ee08-103">Visual Basic provides support for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] through XML literals and XML axis properties.</span></span> <span data-ttu-id="5ee08-104">これにより、使い慣れた便利な構文を使用して、Visual Basic コードで XML を操作できます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-104">This enables you to use a familiar, convenient syntax for working with XML in your Visual Basic code.</span></span> <span data-ttu-id="5ee08-105">*XML リテラル*を使用すると、コードに XML を直接含めることができます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-105">*XML literals* enable you to include XML directly in your code.</span></span> <span data-ttu-id="5ee08-106">*XML 軸プロパティ*を使用すると、XML リテラルの子ノード、子孫ノード、および属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-106">*XML axis properties* enable you to access child nodes, descendant nodes, and attributes of an XML literal.</span></span> <span data-ttu-id="5ee08-107">詳細については、「[XML リテラルの概要](xml-literals-overview.md)」と「[Visual Basic での XML へのアクセス](accessing-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ee08-107">For more information, see [XML Literals Overview](xml-literals-overview.md) and [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="5ee08-108">は、統合言語クエリ (LINQ) を利用するために設計された、メモリ内の XML プログラミング API です。</span><span class="sxs-lookup"><span data-stu-id="5ee08-108">is an in-memory XML programming API designed specifically to take advantage of Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="5ee08-109">LINQ API は直接呼び出すことができますが、XML リテラルを宣言して XML 軸プロパティに直接アクセスできるのは、Visual Basic だけです。</span><span class="sxs-lookup"><span data-stu-id="5ee08-109">Although you can call the LINQ APIs directly, only Visual Basic enables you to declare XML literals and directly access XML axis properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ee08-110">XML リテラルおよび XML 軸プロパティは、ASP.NET ページの宣言型コードではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="5ee08-110">XML literals and XML axis properties are not supported in declarative code in an ASP.NET page.</span></span> <span data-ttu-id="5ee08-111">Visual Basic の XML 機能を使用するには、ASP.NET アプリケーションの分離コード ページにコードを配置します。</span><span class="sxs-lookup"><span data-stu-id="5ee08-111">To use Visual Basic XML features, put your code in a code-behind page in your ASP.NET application.</span></span>  
  
 <span data-ttu-id="5ee08-112">[再生ボタン](./media/overview-of-linq-to-xml/play-video-icon-example.gif) 関連するビデオ デモについては、「[LINQ to XML を使ってみる](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml)」と「[LINQ to XML を使用して Excel スプレッドシートを作成する](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ee08-112">[Play button](./media/overview-of-linq-to-xml/play-video-icon-example.gif) For related video demonstrations, see [How Do I Get Started with LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-get-started-with-linq-to-xml) and [How Do I Create Excel Spreadsheets using LINQ to XML?](/aspnet/web-forms/videos/data-access/linq-videos-from-the-vb-team/how-do-i-create-excel-spreadsheets-using-linq-to-xml).</span></span>
  
## <a name="creating-xml"></a><span data-ttu-id="5ee08-113">XML の作成</span><span class="sxs-lookup"><span data-stu-id="5ee08-113">Creating XML</span></span>  

 <span data-ttu-id="5ee08-114">Visual Basic で XML ツリーを作成する方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="5ee08-114">There are two ways to create XML trees in Visual Basic.</span></span> <span data-ttu-id="5ee08-115">XML リテラルをコード内に直接宣言するか、LINQ API を使用してツリーを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-115">You can declare an XML literal directly in code, or you can use the LINQ APIs to create the tree.</span></span> <span data-ttu-id="5ee08-116">どちらのプロセスでも、XML ツリーの最終的な構造をコードに反映させることができます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-116">Both processes enable the code to reflect the final structure of the XML tree.</span></span> <span data-ttu-id="5ee08-117">たとえば、次のコード例では、XML 要素を作成しています。</span><span class="sxs-lookup"><span data-stu-id="5ee08-117">For example, the following code example creates an XML element:</span></span>  
  
 [!code-vb[VbXmlSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 <span data-ttu-id="5ee08-118">詳細については、「[Visual Basicでの XML の作成](creating-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ee08-118">For more information, see [Creating XML in Visual Basic](creating-xml.md).</span></span>  
  
## <a name="accessing-and-navigating-xml"></a><span data-ttu-id="5ee08-119">XML へのアクセスおよび移動</span><span class="sxs-lookup"><span data-stu-id="5ee08-119">Accessing and Navigating XML</span></span>  

 <span data-ttu-id="5ee08-120">Visual Basic には、XML 構造体にアクセスして移動するための XML 軸プロパティが用意されています。</span><span class="sxs-lookup"><span data-stu-id="5ee08-120">Visual Basic provides XML axis properties for accessing and navigating XML structures.</span></span> <span data-ttu-id="5ee08-121">これらのプロパティを使用すると、XML の子要素名を指定することによって、XML の要素と属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-121">These properties enable you to access XML elements and attributes by specifying the XML child element names.</span></span> <span data-ttu-id="5ee08-122">または、LINQ メソッドを明示的に呼び出して、要素と属性の移動や検索を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-122">Alternatively, you can explicitly call the LINQ methods for navigating and locating elements and attributes.</span></span> <span data-ttu-id="5ee08-123">たとえば、次のコード例では、XML 要素の属性と子要素を参照するために XML 軸プロパティを使用しています。</span><span class="sxs-lookup"><span data-stu-id="5ee08-123">For example, the following code example uses XML axis properties to refer to the attributes and child elements of an XML element.</span></span> <span data-ttu-id="5ee08-124">このコード例では、LINQ クエリを使用して子要素を取得し、それらを XML 要素として出力し、変換を効果的に実行しています。</span><span class="sxs-lookup"><span data-stu-id="5ee08-124">The code example uses a LINQ query to retrieve child elements and output them as XML elements, effectively performing a transform.</span></span>  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 <span data-ttu-id="5ee08-125">詳細については、「[Visual Basicでの XML へのアクセス](accessing-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ee08-125">For more information, see [Accessing XML in Visual Basic](accessing-xml.md).</span></span>  
  
## <a name="xml-namespaces"></a><span data-ttu-id="5ee08-126">XML 名前空間</span><span class="sxs-lookup"><span data-stu-id="5ee08-126">XML Namespaces</span></span>  

 <span data-ttu-id="5ee08-127">Visual Basic を使用すると、`Imports` ステートメントを使用して、グローバルな XML 名前空間の別名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-127">Visual Basic enables you to specify an alias to a global XML namespace by using the `Imports` statement.</span></span> <span data-ttu-id="5ee08-128">次の例は、`Imports` ステートメントを使用して XML 名前空間をインポートする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5ee08-128">The following example shows how to use the `Imports` statement to import an XML namespace:</span></span>  
  
 [!code-vb[VbXMLSamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#1)]  
  
 <span data-ttu-id="5ee08-129">XML 名前空間の別名は、XML 軸プロパティにアクセスする場合や、XML ドキュメントおよび XML 要素の XML リテラルを宣言する場合に使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-129">You can use an XML namespace alias when you access XML axis properties and declare XML literals for XML documents and elements.</span></span>  
  
 <span data-ttu-id="5ee08-130">[GetXmlNamespace 演算子](../../../language-reference/operators/getxmlnamespace-operator.md)を使用すると、特定の名前空間プレフィックスの <xref:System.Xml.Linq.XNamespace> オブジェクトを取得できます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-130">You can retrieve an <xref:System.Xml.Linq.XNamespace> object for a particular namespace prefix by using the [GetXmlNamespace Operator](../../../language-reference/operators/getxmlnamespace-operator.md).</span></span>  
  
 <span data-ttu-id="5ee08-131">詳細については、「[Imports ステートメント (XML 名前空間)](../../../language-reference/statements/imports-statement-xml-namespace.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5ee08-131">For more information, see [Imports Statement (XML Namespace)](../../../language-reference/statements/imports-statement-xml-namespace.md).</span></span>  
  
### <a name="using-xml-namespaces-in-xml-literals"></a><span data-ttu-id="5ee08-132">XML リテラルでの XML 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="5ee08-132">Using XML Namespaces in XML Literals</span></span>  

 <span data-ttu-id="5ee08-133">次の例は、グローバルな名前空間 `ns` を使用する <xref:System.Xml.Linq.XElement> オブジェクトを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5ee08-133">The following example shows how to create an <xref:System.Xml.Linq.XElement> object that uses the global namespace `ns`:</span></span>  
  
 [!code-vb[VbXMLSamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#2)]  
  
 <span data-ttu-id="5ee08-134">Visual Basic コンパイラは、XML 名前空間の別名を含む XML リテラルを同等のコードに変換します。このコードは、`xmlns` 属性に XML 名前空間を使用するために XML 表記を使用します。</span><span class="sxs-lookup"><span data-stu-id="5ee08-134">The Visual Basic compiler translates XML literals that contain XML namespace aliases into equivalent code that uses the XML notation for using XML namespaces, with the `xmlns` attribute.</span></span> <span data-ttu-id="5ee08-135">前のセクションの例のコードをコンパイルすると、次の例と基本的に同じ実行可能コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-135">When compiled, the code in the previous section's example produces essentially the same executable code as the following example:</span></span>  
  
 [!code-vb[VbXMLSamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#3)]  
  
### <a name="using-xml-namespaces-in-xml-axis-properties"></a><span data-ttu-id="5ee08-136">XML 軸プロパティでの XML 名前空間の使用</span><span class="sxs-lookup"><span data-stu-id="5ee08-136">Using XML Namespaces in XML Axis Properties</span></span>  

 <span data-ttu-id="5ee08-137">XML リテラルで宣言された XML 名前空間を XML 軸プロパティで使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5ee08-137">XML namespaces declared in XML literals are not available for use in XML axis properties.</span></span> <span data-ttu-id="5ee08-138">ただし、XML 軸プロパティではグローバルな名前空間を使用できます。</span><span class="sxs-lookup"><span data-stu-id="5ee08-138">However, global namespaces can be used with the XML axis properties.</span></span> <span data-ttu-id="5ee08-139">XML 名前空間プレフィックスとローカルな要素名を区切るには、コロンを使用します。</span><span class="sxs-lookup"><span data-stu-id="5ee08-139">Use a colon to separate the XML namespace prefix from the local element name.</span></span> <span data-ttu-id="5ee08-140">例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="5ee08-140">Following is an example:</span></span>  
  
 [!code-vb[VbXMLSamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5ee08-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ee08-141">See also</span></span>

- [<span data-ttu-id="5ee08-142">XML</span><span class="sxs-lookup"><span data-stu-id="5ee08-142">XML</span></span>](index.md)
- [<span data-ttu-id="5ee08-143">Visual Basic での XML の作成</span><span class="sxs-lookup"><span data-stu-id="5ee08-143">Creating XML in Visual Basic</span></span>](creating-xml.md)
- [<span data-ttu-id="5ee08-144">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="5ee08-144">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="5ee08-145">Visual Basic での XML の操作</span><span class="sxs-lookup"><span data-stu-id="5ee08-145">Manipulating XML in Visual Basic</span></span>](manipulating-xml.md)
