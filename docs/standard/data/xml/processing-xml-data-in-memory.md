---
title: メモリ内の XML データの処理
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1bbb4d05-ead7-4bda-8ece-f86d35c57ad4
ms.openlocfilehash: 038bcfcb9d40ee6087efa3487b6f27f252393f2c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710428"
---
# <a name="processing-xml-data-in-memory"></a><span data-ttu-id="8c21e-102">メモリ内の XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8c21e-102">Processing XML Data In-Memory</span></span>
<span data-ttu-id="8c21e-103">Microsoft .NET Framework には、XML データを処理するための 3 つのモデルである <xref:System.Xml.XmlDocument> クラス、<xref:System.Xml.XPath.XPathDocument> クラス、および [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) と [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8c21e-103">The Microsoft .NET Framework includes three models for processing XML data: the <xref:System.Xml.XmlDocument> class, the <xref:System.Xml.XPath.XPathDocument> class, and [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="8c21e-104"><xref:System.Xml.XmlDocument> クラスは、W3C ドキュメント オブジェクト モデル (DOM) 勧告の DOM Level 1 Core および DOM Level 2 Core を実装しています。</span><span class="sxs-lookup"><span data-stu-id="8c21e-104">The <xref:System.Xml.XmlDocument> class implements the W3C document object model (DOM) level 1 core and the core DOM level 2 recommendations.</span></span> <span data-ttu-id="8c21e-105">DOM は XML ドキュメントのメモリ内 (キャッシュ) ツリー表現です。</span><span class="sxs-lookup"><span data-stu-id="8c21e-105">The DOM is an in-memory (cache) tree representation of an XML document.</span></span> <span data-ttu-id="8c21e-106"><xref:System.Xml.XmlDocument> およびその関連クラスを使用すると、XML ドキュメントの作成、データの読み込みとアクセス、データの変更、および変更の保存が可能です。</span><span class="sxs-lookup"><span data-stu-id="8c21e-106">With the <xref:System.Xml.XmlDocument> and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
 <span data-ttu-id="8c21e-107"><xref:System.Xml.XPath.XPathDocument> クラスは、XPath データ モデルに基づく、読み取り専用のメモリ内データ ストアです。</span><span class="sxs-lookup"><span data-stu-id="8c21e-107">The <xref:System.Xml.XPath.XPathDocument> class is a read-only, in-memory data store that is based on the XPath data model.</span></span> <span data-ttu-id="8c21e-108"><xref:System.Xml.XPath.XPathNavigator> クラスは、読み取り専用の <xref:System.Xml.XPath.XPathDocument> クラスと <xref:System.Xml.XmlDocument> クラス内の XML ドキュメント全体にカーソル モデルを使用して、いくつかの編集オプションとナビゲーション機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="8c21e-108">The <xref:System.Xml.XPath.XPathNavigator> class offers several editing options and navigation capabilities using a cursor model over XML documents contained in the read-only <xref:System.Xml.XPath.XPathDocument> class as well as the <xref:System.Xml.XmlDocument> class.</span></span>  
  
 <span data-ttu-id="8c21e-109">[LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) は、XML データの処理を目的として .NET Framework バージョン 3.5 で導入されたモデルです。</span><span class="sxs-lookup"><span data-stu-id="8c21e-109">[LINQ to XML](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) is a model introduced in the .NET Framework version 3.5 for processing XML data.</span></span> <span data-ttu-id="8c21e-110">[統合言語クエリ (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md) を活用するメモリ内モデルです。</span><span class="sxs-lookup"><span data-stu-id="8c21e-110">It's an in-memory model that leverages [Language-Integrated Query (LINQ)](../../../csharp/programming-guide/concepts/linq/index.md).</span></span> <span data-ttu-id="8c21e-111">LINQ では C# および Visual Basic の言語構文を拡張することで、新しいクエリ機能を実現しています。</span><span class="sxs-lookup"><span data-stu-id="8c21e-111">LINQ extends the language syntax of C# and Visual Basic to provide new query capabilities.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c21e-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8c21e-112">In This Section</span></span>  
 [<span data-ttu-id="8c21e-113">DOM モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8c21e-113">Process XML Data Using the DOM Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-dom-model.md)  
 <span data-ttu-id="8c21e-114"><xref:System.Xml.XmlDocument> とその関連クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c21e-114">Discusses using the <xref:System.Xml.XmlDocument>, and its related classes to process XML data.</span></span>  
  
 [<span data-ttu-id="8c21e-115">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8c21e-115">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="8c21e-116"><xref:System.Xml.XPath.XPathDocument>、<xref:System.Xml.XmlDocument>、および <xref:System.Xml.XPath.XPathNavigator> クラスを使用した XML データの処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="8c21e-116">Discusses using the <xref:System.Xml.XPath.XPathDocument>, <xref:System.Xml.XmlDocument>, and <xref:System.Xml.XPath.XPathNavigator> classes to process XML data.</span></span>  
  
 [<span data-ttu-id="8c21e-117">LINQ to XML を使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="8c21e-117">Process XML Data Using LINQ to XML</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-linq-to-xml.md)  
 <span data-ttu-id="8c21e-118">LINQ to XML の概要を簡単に説明し、LINQ to XML に関する参照先のリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="8c21e-118">Provides a brief overview of LINQ to XML and provides links to the LINQ to XML documentation.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8c21e-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c21e-119">Related Sections</span></span>  
 [<span data-ttu-id="8c21e-120">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="8c21e-120">XML Documents and Data</span></span>](../../../../docs/standard/data/xml/index.md)
