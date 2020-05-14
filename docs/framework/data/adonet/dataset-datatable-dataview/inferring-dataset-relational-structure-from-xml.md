---
title: XML からの DataSet リレーショナル構造の推論
ms.date: 03/30/2017
ms.assetid: cd2f41c6-6785-420e-aa43-3ceb0bdccdce
ms.openlocfilehash: 1c8325d7ed52fea7397a7b5aa8744bdfa90b2c6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785318"
---
# <a name="inferring-dataset-relational-structure-from-xml"></a><span data-ttu-id="94984-102">XML からの DataSet リレーショナル構造の推論</span><span class="sxs-lookup"><span data-stu-id="94984-102">Inferring DataSet Relational Structure from XML</span></span>
<span data-ttu-id="94984-103"><xref:System.Data.DataSet> のリレーショナル構造 (スキーマ) は、テーブル、列、制約、およびリレーションで構成されます。</span><span class="sxs-lookup"><span data-stu-id="94984-103">The relational structure, or schema, of a <xref:System.Data.DataSet> is made up of tables, columns, constraints, and relations.</span></span> <span data-ttu-id="94984-104">XML から <xref:System.Data.DataSet> を読み込むときには、事前定義されたスキーマを使用するか、または読み込む対象の XML から明示的にまたは推論によってスキーマを作成できます。</span><span class="sxs-lookup"><span data-stu-id="94984-104">When loading a <xref:System.Data.DataSet> from XML, the schema can be predefined, or it can be created, either explicitly or through inference, from the XML being loaded.</span></span> <span data-ttu-id="94984-105">XML から <xref:System.Data.DataSet> のスキーマおよび内容を読み込む方法の詳細については、「[XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)」および「[XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="94984-105">For more information about loading the schema and contents of a <xref:System.Data.DataSet> from XML, see [Loading a DataSet from XML](loading-a-dataset-from-xml.md) and [Loading DataSet Schema Information from XML](loading-dataset-schema-information-from-xml.md).</span></span>  
  
 <span data-ttu-id="94984-106"><xref:System.Data.DataSet> のスキーマを XML から作成する場合は、XML スキーマ定義言語 (「[XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照) または XDR (XML-Data Reduced) を使用して、スキーマを明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="94984-106">If the schema of a <xref:System.Data.DataSet> is being created from XML, the preferred method is to explicitly specify the schema using either the XML Schema definition language (XSD) (as described in [Deriving DataSet Relational Structure from XML Schema (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md)) or the XML-Data Reduced (XDR).</span></span> <span data-ttu-id="94984-107">XML で利用できる XML スキーマまたは XDR スキーマがない場合は、XML の要素および属性の構造から <xref:System.Data.DataSet> のスキーマを推論できます。</span><span class="sxs-lookup"><span data-stu-id="94984-107">If no XML Schema or XDR schema is available in the XML, the schema of the <xref:System.Data.DataSet> can be inferred from the structure of the XML elements and attributes.</span></span>  
  
 <span data-ttu-id="94984-108">ここでは、XML の要素と属性およびその構造を示し、<xref:System.Data.DataSet> スキーマの推論に関する規則について説明します。また、その規則に基づいて推論した <xref:System.Data.DataSet> スキーマも示します。</span><span class="sxs-lookup"><span data-stu-id="94984-108">This section describes the rules for <xref:System.Data.DataSet> schema inference by showing XML elements and attributes and their structure, and the resulting inferred <xref:System.Data.DataSet> schema.</span></span>  
  
 <span data-ttu-id="94984-109">XML ドキュメント内のすべての属性を推論プロセスの対象には含めないでください。</span><span class="sxs-lookup"><span data-stu-id="94984-109">Not all attributes present in an XML document should be included in the inference process.</span></span> <span data-ttu-id="94984-110">名前空間で修飾された属性には、XML ドキュメントにとっては重要ですが、<xref:System.Data.DataSet> スキーマにとっては不要なメタデータが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="94984-110">Namespace-qualified attributes can include metadata that is important for the XML document but not for the <xref:System.Data.DataSet> schema.</span></span> <span data-ttu-id="94984-111"><xref:System.Data.DataSet.InferXmlSchema%2A> を使用して、推論プロセスの間に無視する特定の名前空間を指定できます。</span><span class="sxs-lookup"><span data-stu-id="94984-111">Using <xref:System.Data.DataSet.InferXmlSchema%2A>, you can specify namespaces to be ignored during the inference process.</span></span> <span data-ttu-id="94984-112">詳しくは、「[XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="94984-112">For more information, see [Loading DataSet Schema Information from XML](loading-dataset-schema-information-from-xml.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94984-113">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="94984-113">In This Section</span></span>  
 [<span data-ttu-id="94984-114">DataSet スキーマの推論プロセスの概要</span><span class="sxs-lookup"><span data-stu-id="94984-114">Summary of the DataSet Schema Inference Process</span></span>](summary-of-the-dataset-schema-inference-process.md)  
 <span data-ttu-id="94984-115">XML から <xref:System.Data.DataSet> のスキーマを推論するときの規則について概要を示します。</span><span class="sxs-lookup"><span data-stu-id="94984-115">Provides a high-level summary of the rules for inferring the schema of a <xref:System.Data.DataSet> from XML.</span></span>  
  
 [<span data-ttu-id="94984-116">テーブルの推論</span><span class="sxs-lookup"><span data-stu-id="94984-116">Inferring Tables</span></span>](inferring-tables.md)  
 <span data-ttu-id="94984-117"><xref:System.Data.DataSet> のテーブルとして推論される XML の要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-117">Describes the XML elements that are inferred as tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="94984-118">列の推論</span><span class="sxs-lookup"><span data-stu-id="94984-118">Inferring Columns</span></span>](inferring-columns.md)  
 <span data-ttu-id="94984-119">テーブルの列として推論される XML の要素と属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-119">Describes the XML elements and attributes that are inferred as table columns.</span></span>  
  
 [<span data-ttu-id="94984-120">リレーションシップの推論</span><span class="sxs-lookup"><span data-stu-id="94984-120">Inferring Relationships</span></span>](inferring-relationships.md)  
 <span data-ttu-id="94984-121">推論された入れ子状のテーブルに対して作成される <xref:System.Data.DataRelation> オブジェクトおよび <xref:System.Data.ForeignKeyConstraint> オブジェクトについて説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-121">Describes the <xref:System.Data.DataRelation> and <xref:System.Data.ForeignKeyConstraint> objects created for nested, inferred tables.</span></span>  
  
 [<span data-ttu-id="94984-122">要素のテキストの推論</span><span class="sxs-lookup"><span data-stu-id="94984-122">Inferring Element Text</span></span>](inferring-element-text.md)  
 <span data-ttu-id="94984-123">XML 要素のテキストに対して作成される列について、および XML 要素のテキストが無視される場合について説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-123">Describes the columns that are created for text in XML elements, and explains when text in XML elements is ignored.</span></span>  
  
 [<span data-ttu-id="94984-124">推論の制限事項</span><span class="sxs-lookup"><span data-stu-id="94984-124">Inference Limitations</span></span>](inference-limitations.md)  
 <span data-ttu-id="94984-125">スキーマ推論の制限事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-125">Discusses the limitations of schema inference.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="94984-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="94984-126">Related Sections</span></span>  
 [<span data-ttu-id="94984-127">DataSet での XML の使用</span><span class="sxs-lookup"><span data-stu-id="94984-127">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="94984-128"><xref:System.Data.DataSet> オブジェクトと XML データとの対話について説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-128">Describes how the <xref:System.Data.DataSet> object interacts with XML data.</span></span>  
  
 [<span data-ttu-id="94984-129">XML スキーマ (XSD) からの DataSet リレーショナル構造の派生</span><span class="sxs-lookup"><span data-stu-id="94984-129">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="94984-130">XML スキーマ定義言語 (XSD) スキーマから作成された <xref:System.Data.DataSet> のリレーショナル構造 (スキーマ) について説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-130">Describes the relational structure, or schema, of a <xref:System.Data.DataSet> that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="94984-131">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="94984-131">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="94984-132">ADO.NET のアーキテクチャとコンポーネントについて、また ADO.NET を使用して既存のデータ ソースにアクセスしたり、アプリケーション データを管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="94984-132">Describes the ADO.NET architecture and components and how to use them to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94984-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="94984-133">See also</span></span>

- [<span data-ttu-id="94984-134">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="94984-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
