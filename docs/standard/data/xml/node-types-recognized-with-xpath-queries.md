---
title: XPath クエリで認識されるノード型
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 1d33e22d-18e5-43f8-a466-2e3d0a8dd094
ms.openlocfilehash: cc1aa668ccf6fc7f210f48a28cf76b364459c784
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710545"
---
# <a name="node-types-recognized-with-xpath-queries"></a><span data-ttu-id="da5a6-102">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="da5a6-102">Node Types Recognized with XPath Queries</span></span>
<span data-ttu-id="da5a6-103">XPath クエリで認識されるノードの型は、ドキュメント オブジェクト モデル (DOM) のノード型と同じではありません。</span><span class="sxs-lookup"><span data-stu-id="da5a6-103">The types of nodes recognized in an XPath query are not the same node types found in the Document Object Model (DOM).</span></span>  
  
## <a name="w3c-xpath-node-types"></a><span data-ttu-id="da5a6-104">W3C XPath のノード型</span><span class="sxs-lookup"><span data-stu-id="da5a6-104">W3C XPath Node Types</span></span>  
 <span data-ttu-id="da5a6-105">XPath クエリで認識されるノードの型は、ドキュメント オブジェクト モデル (DOM) のノード型ではありません。</span><span class="sxs-lookup"><span data-stu-id="da5a6-105">The types of nodes recognized in an XPath query are not the types of nodes found in the Document Object Model (DOM).</span></span> <span data-ttu-id="da5a6-106">以下は、<xref:System.Xml.XPath.XPathNodeType> 列挙体によって表される XPath のノード型です。</span><span class="sxs-lookup"><span data-stu-id="da5a6-106">The following are the XPath node types represented by the <xref:System.Xml.XPath.XPathNodeType> enumeration.</span></span>  
  
- <xref:System.Xml.XPath.XPathNodeType.All>  
  
- <xref:System.Xml.XPath.XPathNodeType.Attribute>  
  
- <xref:System.Xml.XPath.XPathNodeType.Comment>  
  
- <xref:System.Xml.XPath.XPathNodeType.Element>  
  
- <xref:System.Xml.XPath.XPathNodeType.Namespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>  
  
- <xref:System.Xml.XPath.XPathNodeType.Root>  
  
- <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace>  
  
- <xref:System.Xml.XPath.XPathNodeType.Text>  
  
- <xref:System.Xml.XPath.XPathNodeType.Whitespace>  
  
 <span data-ttu-id="da5a6-107">これらのノード型は、XPath データ モデルに基づいており、ノードは XML 情報セットから派生しています。</span><span class="sxs-lookup"><span data-stu-id="da5a6-107">These node types are based on the XPath data model, where the nodes are derived from the XML Information Set.</span></span> <span data-ttu-id="da5a6-108"><xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> および <xref:System.Xml.XPath.XPathNodeType.Whitespace> ノード型は、XPath データ モデルに記載されている基本のノード型に対する Microsoft .NET Framework の拡張です。</span><span class="sxs-lookup"><span data-stu-id="da5a6-108">The <xref:System.Xml.XPath.XPathNodeType.SignificantWhitespace> and <xref:System.Xml.XPath.XPathNodeType.Whitespace> node types are Microsoft .NET Framework extensions to the base node types described in the XPath data model.</span></span>  
  
 <span data-ttu-id="da5a6-109">XPath における属性ノード型の使用法は DOM と異なります。</span><span class="sxs-lookup"><span data-stu-id="da5a6-109">The attribute node type is used differently in the XPath data model than it is in the DOM.</span></span> <span data-ttu-id="da5a6-110">XPath データ モデルでは、要素ノードには関連する属性ノードのセットがあり、要素ノードはそれぞれの属性ノードの親になっています。</span><span class="sxs-lookup"><span data-stu-id="da5a6-110">In the XPath data model, the element node has a set of attribute nodes related to it and the element node is the parent of each attribute node.</span></span> <span data-ttu-id="da5a6-111">しかし、DOM では要素ノードは所有者であり、親ではありません。</span><span class="sxs-lookup"><span data-stu-id="da5a6-111">However, in the DOM, the element node is the owner and not the parent.</span></span> <span data-ttu-id="da5a6-112">いずれのモデルにおいても、属性ノードと名前空間ノードは要素ノードの子ノードとは見なされません。</span><span class="sxs-lookup"><span data-stu-id="da5a6-112">In both models, attribute and namespace nodes are not considered child nodes of the element node.</span></span>  
  
 <span data-ttu-id="da5a6-113">名前空間ノード型は XPath データ モデルに追加されたノード型であり、DOM で認識されるノード型ではありません。</span><span class="sxs-lookup"><span data-stu-id="da5a6-113">The namespace node type is an addition to the XPath data model and is not a recognized DOM node type.</span></span>  
  
 <span data-ttu-id="da5a6-114">要素ノード、属性ノード、名前空間ノードをナビゲートする方法については、「[XPathNavigator を使用するノード セットのナビゲーション](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)」と「[XPathNavigator を使用する属性と名前空間のナビゲーション](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="da5a6-114">For more information about navigating element, attribute, and namespace nodes, see the [Node Set Navigation Using XPathNavigator](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md) and [Attribute and Namespace Node Navigation Using XPathNavigator](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md) topics.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da5a6-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="da5a6-115">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="da5a6-116">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="da5a6-116">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="da5a6-117">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="da5a6-117">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="da5a6-118">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="da5a6-118">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [<span data-ttu-id="da5a6-119">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="da5a6-119">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [<span data-ttu-id="da5a6-120">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="da5a6-120">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [<span data-ttu-id="da5a6-121">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="da5a6-121">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
