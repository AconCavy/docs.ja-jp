---
title: XDocument クラスの概要 (C#)
ms.date: 07/20/2015
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: de49dc071d22dd77dddea29ca114663261e3edda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "69590845"
---
# <a name="xdocument-class-overview-c"></a><span data-ttu-id="56236-102">XDocument クラスの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="56236-102">XDocument Class Overview (C#)</span></span>
<span data-ttu-id="56236-103">このトピックでは、<xref:System.Xml.Linq.XDocument> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="56236-103">This topic introduces the <xref:System.Xml.Linq.XDocument> class.</span></span>  
  
## <a name="overview-of-the-xdocument-class"></a><span data-ttu-id="56236-104">XDocument クラスの概要</span><span class="sxs-lookup"><span data-stu-id="56236-104">Overview of the XDocument class</span></span>  
 <span data-ttu-id="56236-105"><xref:System.Xml.Linq.XDocument> クラスには、有効な XML ドキュメントに必要な情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="56236-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document.</span></span> <span data-ttu-id="56236-106">これには、XML 宣言、処理命令、コメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="56236-106">This includes an XML declaration, processing instructions, and comments.</span></span>  
  
 <span data-ttu-id="56236-107"><xref:System.Xml.Linq.XDocument> クラスが提供する特定の機能が必要な場合は、<xref:System.Xml.Linq.XDocument> オブジェクトを作成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="56236-107">Note that you only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="56236-108">多くの場合、<xref:System.Xml.Linq.XElement> を直接操作できます。</span><span class="sxs-lookup"><span data-stu-id="56236-108">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="56236-109"><xref:System.Xml.Linq.XElement> を直接操作するのは、比較的単純なプログラミング モデルです。</span><span class="sxs-lookup"><span data-stu-id="56236-109">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>  
  
 <span data-ttu-id="56236-110"><xref:System.Xml.Linq.XDocument> は <xref:System.Xml.Linq.XContainer> から派生しています。</span><span class="sxs-lookup"><span data-stu-id="56236-110"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>.</span></span> <span data-ttu-id="56236-111">したがって子ノードを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="56236-111">Therefore, it can contain child nodes.</span></span> <span data-ttu-id="56236-112">ただし、<xref:System.Xml.Linq.XDocument> オブジェクトに格納できる子 <xref:System.Xml.Linq.XElement> ノードは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="56236-112">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="56236-113">これは、XML ドキュメントにルート要素を 1 つしか持てないという XML 標準を反映しています。</span><span class="sxs-lookup"><span data-stu-id="56236-113">This reflects the XML standard that there can be only one root element in an XML document.</span></span>  
  
## <a name="components-of-xdocument"></a><span data-ttu-id="56236-114">XDocument のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="56236-114">Components of XDocument</span></span>  
 <span data-ttu-id="56236-115"><xref:System.Xml.Linq.XDocument> には、次の要素を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="56236-115">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>  
  
- <span data-ttu-id="56236-116">1 つの <xref:System.Xml.Linq.XDeclaration> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="56236-116">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="56236-117"><xref:System.Xml.Linq.XDeclaration> では、XML 宣言の関連部分である XML バージョン、ドキュメントのエンコード、および XML ドキュメントがスタンドアロンかどうかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="56236-117"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is stand-alone.</span></span>  
  
- <span data-ttu-id="56236-118">1 つの <xref:System.Xml.Linq.XElement> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="56236-118">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="56236-119">これは XML ドキュメントのルート ノードです。</span><span class="sxs-lookup"><span data-stu-id="56236-119">This is the root node of the XML document.</span></span>  
  
- <span data-ttu-id="56236-120">任意の数の <xref:System.Xml.Linq.XProcessingInstruction> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="56236-120">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="56236-121">処理命令は、XML を処理するアプリケーションに情報を伝達します。</span><span class="sxs-lookup"><span data-stu-id="56236-121">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
- <span data-ttu-id="56236-122">任意の数の <xref:System.Xml.Linq.XComment> オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="56236-122">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="56236-123">コメントは、ルート要素の兄弟になります。</span><span class="sxs-lookup"><span data-stu-id="56236-123">The comments will be siblings to the root element.</span></span> <span data-ttu-id="56236-124">XML ドキュメントをコメントで始めることは無効であるため、<xref:System.Xml.Linq.XComment> オブジェクトをリストの最初の引数にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="56236-124">The <xref:System.Xml.Linq.XComment> object cannot be the first argument in the list, because it is not valid for an XML document to start with a comment.</span></span>  
  
- <span data-ttu-id="56236-125">DTD 用の 1 つの <xref:System.Xml.Linq.XDocumentType>。</span><span class="sxs-lookup"><span data-stu-id="56236-125">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>  
  
 <span data-ttu-id="56236-126"><xref:System.Xml.Linq.XDocument> をシリアル化すると、`XDocument.Declaration` が `null` である場合でも、作成者が `Writer.Settings.OmitXmlDeclaration` を `false` (既定値) に設定していれば、出力には XML 宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="56236-126">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>  
  
 <span data-ttu-id="56236-127">既定では、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] によってバージョンが "1.0" に、エンコードが "utf-8" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="56236-127">By default, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sets the version to "1.0", and sets the encoding to "utf-8".</span></span>  
  
## <a name="using-xelement-without-xdocument"></a><span data-ttu-id="56236-128">XDocument なしでの XElement の使用</span><span class="sxs-lookup"><span data-stu-id="56236-128">Using XElement without XDocument</span></span>  
 <span data-ttu-id="56236-129">既に説明したように、<xref:System.Xml.Linq.XElement> クラスは [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] プログラミング インターフェイスのメイン クラスです。</span><span class="sxs-lookup"><span data-stu-id="56236-129">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programming interface.</span></span> <span data-ttu-id="56236-130">多くの場合、アプリケーションはドキュメントの作成を必要としません。</span><span class="sxs-lookup"><span data-stu-id="56236-130">In many cases, your application will not require that you create a document.</span></span> <span data-ttu-id="56236-131"><xref:System.Xml.Linq.XElement> クラスを使用することで、XML ツリーを作成し、そのツリーに他の XML ツリーを追加し、その XML ツリーを変更し、さらにそのツリーを保存できます。</span><span class="sxs-lookup"><span data-stu-id="56236-131">By using the <xref:System.Xml.Linq.XElement> class, you can create an XML tree, add other XML trees to it, modify the XML tree, and save it.</span></span>  
  
## <a name="using-xdocument"></a><span data-ttu-id="56236-132">XDocument の使用</span><span class="sxs-lookup"><span data-stu-id="56236-132">Using XDocument</span></span>  
 <span data-ttu-id="56236-133"><xref:System.Xml.Linq.XDocument> を構築するには、<xref:System.Xml.Linq.XElement> オブジェクトを構築する場合と同様に関数型構築を使用します。</span><span class="sxs-lookup"><span data-stu-id="56236-133">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>  
  
 <span data-ttu-id="56236-134">次のコードは、<xref:System.Xml.Linq.XDocument> オブジェクトおよび関連する格納されるオブジェクトを作成しています。</span><span class="sxs-lookup"><span data-stu-id="56236-134">The following code creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>  
  
```csharp  
XDocument d = new XDocument(  
    new XComment("This is a comment."),  
    new XProcessingInstruction("xml-stylesheet",  
        "href='mystyle.css' title='Compact' type='text/css'"),  
    new XElement("Pubs",  
        new XElement("Book",  
            new XElement("Title", "Artifacts of Roman Civilization"),  
            new XElement("Author", "Moreno, Jordao")  
        ),  
        new XElement("Book",  
            new XElement("Title", "Midieval Tools and Implements"),  
            new XElement("Author", "Gazit, Inbar")  
        )  
    ),  
    new XComment("This is another comment.")  
);  
d.Declaration = new XDeclaration("1.0", "utf-8", "true");  
Console.WriteLine(d);  
  
d.Save("test.xml");  
```  
  
 <span data-ttu-id="56236-135">ファイル test.xml を調べると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="56236-135">When you examine the file test.xml, you get the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<!--This is a comment.-->  
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>  
<Pubs>  
  <Book>  
    <Title>Artifacts of Roman Civilization</Title>  
    <Author>Moreno, Jordao</Author>  
  </Book>  
  <Book>  
    <Title>Midieval Tools and Implements</Title>  
    <Author>Gazit, Inbar</Author>  
  </Book>  
</Pubs>  
<!--This is another comment.-->  
```  
  
## <a name="see-also"></a><span data-ttu-id="56236-136">参照</span><span class="sxs-lookup"><span data-stu-id="56236-136">See also</span></span>

- [<span data-ttu-id="56236-137">LINQ to XML プログラミングの概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="56236-137">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
