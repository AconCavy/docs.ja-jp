---
title: XML ドキュメントと XML データ
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: e695047f-3c0f-4045-8708-5baea91cc380
ms.openlocfilehash: e0c3f3e99b06b65caf79d87a7831369f6fb33b08
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710792"
---
# <a name="xml-documents-and-data"></a><span data-ttu-id="f7c68-102">XML ドキュメントと XML データ</span><span class="sxs-lookup"><span data-stu-id="f7c68-102">XML Documents and Data</span></span>

<span data-ttu-id="f7c68-103">.NET Framework には、XML 対応アプリを容易に構築するための、包括的で統合された一連のクラスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="f7c68-103">The .NET Framework provides a comprehensive and integrated set of classes that enable you to build XML-aware apps easily.</span></span> <span data-ttu-id="f7c68-104">次の名前空間のクラスでは、XML の解析と書き込み、メモリ内での XML データの編集、データの検証、および XSLT 変換がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-104">The classes in the following namespaces support parsing and writing XML, editing XML data in memory, data validation, and XSLT transformation.</span></span>

- <xref:System.Xml>

- <xref:System.Xml.XPath>

- <xref:System.Xml.Xsl>

- <xref:System.Xml.Schema>

- <xref:System.Xml.Linq>

<span data-ttu-id="f7c68-105">完全な一覧で、[.NET API ブラウザー](https://docs.microsoft.com/dotnet/api/?term=system.xml)で "System.Xml" を検索、ます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-105">For a full list, search for "System.Xml" on the [.NET API browser](https://docs.microsoft.com/dotnet/api/?term=system.xml).</span></span>

<span data-ttu-id="f7c68-106">次の名前空間のクラスでは、World Wide Web Consortium (W3C) 勧告がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-106">The classes in these namespaces support World Wide Web Consortium (W3C) recommendations.</span></span> <span data-ttu-id="f7c68-107">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-107">For example:</span></span>

- <span data-ttu-id="f7c68-108"><xref:System.Xml.XmlDocument?displayProperty=nameWithType> クラスは、[W3C ドキュメント オブジェクト モデル (DOM) 勧告の DOM Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) および [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) を実装しています。</span><span class="sxs-lookup"><span data-stu-id="f7c68-108">The <xref:System.Xml.XmlDocument?displayProperty=nameWithType> class implements the [W3C Document Object Model (DOM) Level 1 Core](https://www.w3.org/TR/REC-DOM-Level-1/) and [DOM Level 2 Core](https://www.w3.org/TR/DOM-Level-2-Core/) recommendations.</span></span>

- <span data-ttu-id="f7c68-109"><xref:System.Xml.XmlReader?displayProperty=nameWithType> クラスと <xref:System.Xml.XmlWriter?displayProperty=nameWithType> クラスは、W3C 勧告『[XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/)』および『[Namespaces in XML](https://www.w3.org/TR/REC-xml-names/)』をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f7c68-109">The <xref:System.Xml.XmlReader?displayProperty=nameWithType> and <xref:System.Xml.XmlWriter?displayProperty=nameWithType> classes support the [W3C XML 1.0](https://www.w3.org/TR/2006/REC-xml-20060816/) and the [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/) recommendations.</span></span>

- <span data-ttu-id="f7c68-110"><xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> クラスのスキーマが以下をサポートします: 「[W3C XML Schema Part 1:Structures](https://www.w3.org/TR/xmlschema-1/)」 (XML スキーマ パート 1: 構造体) および「[XML Schema Part 2:Datatypes](https://www.w3.org/TR/xmlschema-2/)」 (XML スキーマ パート 2: データ型) の推奨事項。</span><span class="sxs-lookup"><span data-stu-id="f7c68-110">Schemas in the <xref:System.Xml.Schema.XmlSchemaSet?displayProperty=nameWithType> class support the [W3C XML Schema Part 1: Structures](https://www.w3.org/TR/xmlschema-1/) and [XML Schema Part 2: Datatypes](https://www.w3.org/TR/xmlschema-2/) recommendations.</span></span>

- <span data-ttu-id="f7c68-111"><xref:System.Xml.Xsl?displayProperty=nameWithType> 名前空間のクラスは、W3C 勧告『[XSLT version 1.0](https://www.w3.org/TR/xslt)』に準拠する XSLT 変換をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f7c68-111">Classes in the <xref:System.Xml.Xsl?displayProperty=nameWithType> namespace support XSLT transformations that conform to the [W3C XSLT 1.0](https://www.w3.org/TR/xslt) recommendation.</span></span>

<span data-ttu-id="f7c68-112">.NET Framework の XML クラスの利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-112">The XML classes in the .NET Framework provide these benefits:</span></span>

- <span data-ttu-id="f7c68-113">**生産性**</span><span class="sxs-lookup"><span data-stu-id="f7c68-113">**Productivity.**</span></span> <span data-ttu-id="f7c68-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) および [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) により XML でのプログラミングがさらに容易になるほか、SQL と同じようにクエリを利用できます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-114">[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) makes it easier to program with XML and provides a query experience that is similar to SQL.</span></span>

- <span data-ttu-id="f7c68-115">**拡張性**</span><span class="sxs-lookup"><span data-stu-id="f7c68-115">**Extensibility.**</span></span> <span data-ttu-id="f7c68-116">.NET Framework の XML クラスは、抽象基本クラスと仮想メソッドを使用することによって拡張できます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-116">The XML classes in the .NET Framework are extensible through the use of abstract base classes and virtual methods.</span></span> <span data-ttu-id="f7c68-117">たとえば、キャッシュ ストリームをローカルのディスクに格納する <xref:System.Xml.XmlUrlResolver> クラスの派生クラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-117">For example, you can create a derived class of the <xref:System.Xml.XmlUrlResolver> class that stores the cache stream to the local disk.</span></span>

- <span data-ttu-id="f7c68-118">**プラグ可能なアーキテクチャ。**</span><span class="sxs-lookup"><span data-stu-id="f7c68-118">**Pluggable architecture.**</span></span> <span data-ttu-id="f7c68-119">.NET Framework が提供するアーキテクチャでは、コンポーネントが相互に利用できます。また、コンポーネント間でデータをストリーム転送できます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-119">The .NET Framework provides an architecture in which components can utilize one another, and data can be streamed between components.</span></span> <span data-ttu-id="f7c68-120">たとえば、<xref:System.Xml.XPath.XPathDocument> オブジェクト、<xref:System.Xml.XmlDocument> オブジェクトなどのデータ ストアは、<xref:System.Xml.Xsl.XslCompiledTransform> クラスを使って変換でき、その出力は、別のストアにストリーム転送することも、Web サービスからのストリームとして返すこともできます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-120">For example, a data store, such as an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object, can be transformed with the <xref:System.Xml.Xsl.XslCompiledTransform> class, and the output can then be streamed either into another store or returned as a stream from a web service.</span></span>

- <span data-ttu-id="f7c68-121">**パフォーマンス。**</span><span class="sxs-lookup"><span data-stu-id="f7c68-121">**Performance.**</span></span> <span data-ttu-id="f7c68-122">アプリのパフォーマンスを高めるために、.NET Framework の一部の XML クラスはストリーム ベースのモデルをサポートし、次の特性を備えています。</span><span class="sxs-lookup"><span data-stu-id="f7c68-122">For better app performance, some of the XML classes in the .NET Framework support a streaming-based model with the following characteristics:</span></span>

  - <span data-ttu-id="f7c68-123">キャッシング処理を最小限に抑える前方参照専用のプル モデル解析 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="f7c68-123">Minimal caching for forward-only, pull-model parsing (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="f7c68-124">前方参照専用の検証 (<xref:System.Xml.XmlReader>)。</span><span class="sxs-lookup"><span data-stu-id="f7c68-124">Forward-only validation (<xref:System.Xml.XmlReader>).</span></span>

  - <span data-ttu-id="f7c68-125">作成するノードを単一の仮想ノードに抑えながら、ドキュメントへのランダム アクセスを可能にする、カーソル スタイルのナビゲーション (<xref:System.Xml.XPath.XPathNavigator>)。</span><span class="sxs-lookup"><span data-stu-id="f7c68-125">Cursor style navigation that minimizes node creation to a single virtual node while providing random access to the document (<xref:System.Xml.XPath.XPathNavigator>).</span></span>

  <span data-ttu-id="f7c68-126">XSLT 処理が必要になるときのパフォーマンスを常に高めるために、<xref:System.Xml.XPath.XPathDocument> クラスを使用できます。このクラスは、<xref:System.Xml.Xsl.XslCompiledTransform> クラスと効率よく連携するように設計された、XPath クエリ用の最適化された読み取り専用ストアです。</span><span class="sxs-lookup"><span data-stu-id="f7c68-126">For better performance whenever XSLT processing is required, you can use the <xref:System.Xml.XPath.XPathDocument> class, which is an optimized, read-only store for XPath queries designed to work efficiently with the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span>

- <span data-ttu-id="f7c68-127">**ADO.NET との統合。**</span><span class="sxs-lookup"><span data-stu-id="f7c68-127">**Integration with ADO.NET.**</span></span> <span data-ttu-id="f7c68-128">XML クラスと [ADO.NET](../../../../docs/framework/data/adonet/index.md) が緊密に統合されることで、リレーショナル データと XML が結合されます。</span><span class="sxs-lookup"><span data-stu-id="f7c68-128">The XML classes and [ADO.NET](../../../../docs/framework/data/adonet/index.md) are tightly integrated to bring together relational data and XML.</span></span> <span data-ttu-id="f7c68-129"><xref:System.Data.DataSet> クラスは、データベースから取得されたデータのメモリ内キャッシュです。</span><span class="sxs-lookup"><span data-stu-id="f7c68-129">The <xref:System.Data.DataSet> class is an in-memory cache of data retrieved from a database.</span></span> <span data-ttu-id="f7c68-130"><xref:System.Data.DataSet> クラスは、<xref:System.Xml.XmlReader> クラスと <xref:System.Xml.XmlWriter> クラスを使用して XML を読み書きする機能、内部リレーショナル スキーマ構造を XML スキーマ (XSD) として永続化する機能、および XML ドキュメントからスキーマ構造を推論する機能を備えています。</span><span class="sxs-lookup"><span data-stu-id="f7c68-130">The <xref:System.Data.DataSet> class has the ability to read and write XML by using the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> classes, to persist its internal relational schema structure as XML schemas (XSD), and to infer the schema structure of an XML document.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f7c68-131">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f7c68-131">In This Section</span></span>

<span data-ttu-id="f7c68-132">[XML の処理オプション](../../../../docs/standard/data/xml/xml-processing-options.md) XML データの処理に関するオプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-132">[XML Processing Options](../../../../docs/standard/data/xml/xml-processing-options.md) Discusses options for processing XML data.</span></span>

<span data-ttu-id="f7c68-133">[メモリ内の XML データの処理](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) XML データをメモリ内で処理する 3 つの方法について説明します。[LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) および [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md)、<xref:System.Xml.XmlDocument> クラス (W3C ドキュメント オブジェクト モデルに基づく)、および <xref:System.Xml.XPath.XPathDocument> クラス (XPath データ モデルに基づく)。</span><span class="sxs-lookup"><span data-stu-id="f7c68-133">[Processing XML Data In-Memory](../../../../docs/standard/data/xml/processing-xml-data-in-memory.md) Discusses the three models for processing XML data in-memory: [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) and [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md), the <xref:System.Xml.XmlDocument> class (based on the W3C Document Object Model), and the <xref:System.Xml.XPath.XPathDocument> class (based on the XPath data model).</span></span>

<span data-ttu-id="f7c68-134">[XSLT 変換](../../../../docs/standard/data/xml/xslt-transformations.md)</span><span class="sxs-lookup"><span data-stu-id="f7c68-134">[XSLT Transformations](../../../../docs/standard/data/xml/xslt-transformations.md)</span></span>\
<span data-ttu-id="f7c68-135">XSLT プロセッサの使い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-135">Describes how to use the XSLT processor.</span></span>

<span data-ttu-id="f7c68-136">[XML スキーマ オブジェクト モデル (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span><span class="sxs-lookup"><span data-stu-id="f7c68-136">[XML Schema Object Model (SOM)](../../../../docs/standard/data/xml/xml-schema-object-model-som.md)</span></span>\
<span data-ttu-id="f7c68-137">スキーマの読み込みと編集のための <xref:System.Xml.Schema.XmlSchema> クラスを提供することで、XML スキーマ (XSD) の作成と操作に使用されるクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-137">Describes the classes used for building and manipulating XML Schemas (XSD) by providing an <xref:System.Xml.Schema.XmlSchema> class to load and edit a schema.</span></span>

<span data-ttu-id="f7c68-138">[XML とリレーショナル データおよび ADO.NET との統合](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)</span><span class="sxs-lookup"><span data-stu-id="f7c68-138">[XML Integration with Relational Data and ADO.NET](../../../../docs/standard/data/xml/xml-integration-with-relational-data-and-adonet.md)</span></span>\
<span data-ttu-id="f7c68-139">.NET Framework が <xref:System.Data.DataSet> オブジェクトと <xref:System.Xml.XmlDataDocument> オブジェクトを介して、データのリレーショナル表現および階層表現の両方に対するリアルタイムの同期アクセスを実現するしくみついて説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-139">Describes how the .NET Framework enables real-time, synchronous access to both the relational and hierarchical representations of data through the <xref:System.Data.DataSet> object and the <xref:System.Xml.XmlDataDocument> object.</span></span>

<span data-ttu-id="f7c68-140">[XML ドキュメントでの名前空間の管理](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span><span class="sxs-lookup"><span data-stu-id="f7c68-140">[Managing Namespaces in an XML Document](../../../../docs/standard/data/xml/managing-namespaces-in-an-xml-document.md)</span></span>\
<span data-ttu-id="f7c68-141"><xref:System.Xml.XmlNamespaceManager> クラスを使用して、名前空間情報を格納および保持する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-141">Describes how the <xref:System.Xml.XmlNamespaceManager> class is used to store and maintain namespace information.</span></span>

<span data-ttu-id="f7c68-142">[System.Xml クラスでの型のサポート](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span><span class="sxs-lookup"><span data-stu-id="f7c68-142">[Type Support in the System.Xml Classes](../../../../docs/standard/data/xml/type-support-in-the-system-xml-classes.md)</span></span>\
<span data-ttu-id="f7c68-143">XML データ型を CLR 型にマップする方法、XML データ型を変換する方法、および <xref:System.Xml> クラスのその他の型サポート機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-143">Describes how XML data types map to CLR types, how to convert XML data types, and other type support features in the <xref:System.Xml> classes.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f7c68-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7c68-144">Related Sections</span></span>

<span data-ttu-id="f7c68-145">[ADO.NET](../../../../docs/framework/data/adonet/index.md)</span><span class="sxs-lookup"><span data-stu-id="f7c68-145">[ADO.NET](../../../../docs/framework/data/adonet/index.md)</span></span>\
<span data-ttu-id="f7c68-146">ADO.NET を使用してデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-146">Provides information on how to access data using ADO.NET.</span></span>

<span data-ttu-id="f7c68-147">[セキュリティ](../../../../docs/standard/security/index.md)</span><span class="sxs-lookup"><span data-stu-id="f7c68-147">[Security](../../../../docs/standard/security/index.md)</span></span>\
<span data-ttu-id="f7c68-148">.NET Framework セキュリティ システムの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="f7c68-148">Provides an overview of the .NET Framework security system.</span></span>
