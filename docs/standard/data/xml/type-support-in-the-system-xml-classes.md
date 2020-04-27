---
title: System.Xml クラスでの型のサポート
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 63570538-06e3-4401-ad4d-ac50be90c7bf
ms.openlocfilehash: cec47d40a0353639bc17b880265f7c15f2f53ac4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710103"
---
# <a name="type-support-in-the-systemxml-classes"></a><span data-ttu-id="c53df-102">System.Xml クラスでの型のサポート</span><span class="sxs-lookup"><span data-stu-id="c53df-102">Type Support in the System.Xml Classes</span></span>
<span data-ttu-id="c53df-103">.NET Framework Version 2.0 では、コアの XML クラスが強化され、型サポート機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="c53df-103">In the .NET Framework version 2.0, the core XML classes have been enhanced to include type support features.</span></span> <span data-ttu-id="c53df-104"><xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスには、XML スキーマ型と共通言語ランタイム (CLR) 型の間の変換機能を含む型サポート機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c53df-104">The <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes include type support features including the ability to convert between XML Schema types and common language runtime (CLR) types.</span></span>  
  
 <span data-ttu-id="c53df-105">.NET Framework Version 2.0 では、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter>、および <xref:System.Xml.XPath.XPathNavigator> クラスが強化され、型サポート機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="c53df-105">In the .NET Framework version 2.0, the <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.XPath.XPathNavigator> classes have been enhanced to include type support features.</span></span>  
  
- <span data-ttu-id="c53df-106"><xref:System.Xml.XmlReader> および <xref:System.Xml.XPath.XPathNavigator> クラスにはそれぞれ、ノードのスキーマ情報を返す **SchemaInfo** プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="c53df-106">The <xref:System.Xml.XmlReader> and <xref:System.Xml.XPath.XPathNavigator> classes each include a **SchemaInfo** property that returns the schema information on a node.</span></span>  
  
- <span data-ttu-id="c53df-107"><xref:System.Xml.XmlReader> クラスの **ReadContentAs** と **ReadElementContentAs** メソッドは、1 回のメソッド呼び出しでテキスト値を読み取り、それを CLR 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="c53df-107">The **ReadContentAs** and **ReadElementContentAs** and methods on the <xref:System.Xml.XmlReader> class read a text value and convert it to a CLR value in a single method call.</span></span>  
  
- <span data-ttu-id="c53df-108"><xref:System.Xml.XmlWriter.WriteValue%2A> クラスの <xref:System.Xml.XmlWriter> メソッドは、XML の書き出し時に、CLR 型を XML スキーマ型に変換します。</span><span class="sxs-lookup"><span data-stu-id="c53df-108">The <xref:System.Xml.XmlWriter.WriteValue%2A> method on the <xref:System.Xml.XmlWriter> class converts a CLR type to an XML Schema type when writing out XML.</span></span>  
  
- <span data-ttu-id="c53df-109"><xref:System.Xml.XPath.XPathNavigator> クラスの **ValueAs** および <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> プロパティは、1 回のメソッド呼び出しでノード値を返し、それを CLR 値に変換します。</span><span class="sxs-lookup"><span data-stu-id="c53df-109">The **ValueAs** and <xref:System.Xml.XPath.XPathNavigator.TypedValue%2A> properties on the <xref:System.Xml.XPath.XPathNavigator> class return a node value and convert it to a CLR value in a single method call.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c53df-110">.NET Framework Version 1.0 では、XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスが必要でした。</span><span class="sxs-lookup"><span data-stu-id="c53df-110">In the .NET Framework version 1.0 the <xref:System.Xml.XmlConvert> class was needed to convert between XML Schema and CLR types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c53df-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="c53df-111">In This Section</span></span>  
 [<span data-ttu-id="c53df-112">XML データ型から CLR 型へのマッピング</span><span class="sxs-lookup"><span data-stu-id="c53df-112">Mapping XML Data Types to CLR Types</span></span>](../../../../docs/standard/data/xml/mapping-xml-data-types-to-clr-types.md)  
 <span data-ttu-id="c53df-113">XML データ型から CLR 型への既定のマッピングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c53df-113">Describes the default mappings of XML data types to CLR types.</span></span>  
  
 [<span data-ttu-id="c53df-114">XML 型サポートの実装に関するメモ</span><span class="sxs-lookup"><span data-stu-id="c53df-114">XML Type Support Implementation Notes</span></span>](../../../../docs/standard/data/xml/xml-type-support-implementation-notes.md)  
 <span data-ttu-id="c53df-115">型サポート実装の詳細のいくつかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="c53df-115">Discusses some of the type support implementation details.</span></span>  
  
 [<span data-ttu-id="c53df-116">XML データ型の変換</span><span class="sxs-lookup"><span data-stu-id="c53df-116">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 <span data-ttu-id="c53df-117">XML スキーマ型と CLR 型の間の変換に <xref:System.Xml.XmlConvert> クラスを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c53df-117">Describes how to use the <xref:System.Xml.XmlConvert> class to convert between XML Schema and CLR types.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c53df-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c53df-118">Related Sections</span></span>  
 [<span data-ttu-id="c53df-119">厳密に型指定された XML データへの XPathNavigator を使用したアクセス</span><span class="sxs-lookup"><span data-stu-id="c53df-119">Accessing Strongly Typed XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
