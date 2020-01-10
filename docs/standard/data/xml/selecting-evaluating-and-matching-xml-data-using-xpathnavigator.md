---
title: XPathNavigator を使用した XML データの選択、評価、および照合
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 46e059f8-4dc8-4185-9236-784be95228ed
ms.openlocfilehash: 1a76edf22483c0df8871badcb5e162dd3e66001f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710142"
---
# <a name="selecting-evaluating-and-matching-xml-data-using-xpathnavigator"></a><span data-ttu-id="7b1d8-102">XPathNavigator を使用した XML データの選択、評価、および照合</span><span class="sxs-lookup"><span data-stu-id="7b1d8-102">Selecting, Evaluating and Matching XML Data using XPathNavigator</span></span>
<span data-ttu-id="7b1d8-103"><xref:System.Xml.XPath.XPathNavigator> クラスは、XPath クエリによる <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のノードの選択、XPath 式の結果の評価と検査、および <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のノードが指定された XPath 式に一致するかどうかの判定のためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-103">The <xref:System.Xml.XPath.XPathNavigator> class provides methods to select nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath query, evaluate and examine the results of an XPath expression, and determine if a node in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object matches a given XPath expression.</span></span> <span data-ttu-id="7b1d8-104">以下のトピックでは、これらの概念および <xref:System.Xml.XPath.XPathDocument> または <xref:System.Xml.XmlDocument> オブジェクト内のノードの選択、評価、および照合に関連する他の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-104">These and other concepts that relate to selecting, evaluating and matching nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object are described in the following topics.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b1d8-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="7b1d8-105">In This Section</span></span>  
 [<span data-ttu-id="7b1d8-106">XPathNavigator を使用した XML データの選択</span><span class="sxs-lookup"><span data-stu-id="7b1d8-106">Select XML Data Using XPathNavigator</span></span>](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 <span data-ttu-id="7b1d8-107"><xref:System.Xml.XPath.XPathNavigator> オブジェクトまたは <xref:System.Xml.XPath.XPathDocument> オブジェクト内で XPath 式を使用してノード セットを選択するために使用される <xref:System.Xml.XmlDocument> クラスの一連のメソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-107">Describes the set of <xref:System.Xml.XPath.XPathNavigator> class methods used to select a set of nodes in an <xref:System.Xml.XPath.XPathDocument> or <xref:System.Xml.XmlDocument> object using an XPath expression.</span></span>  
  
 [<span data-ttu-id="7b1d8-108">XPathNavigator による XPath 式の評価</span><span class="sxs-lookup"><span data-stu-id="7b1d8-108">Evaluate XPath Expressions using XPathNavigator</span></span>](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 <span data-ttu-id="7b1d8-109">XPath 式の評価に使用される <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-109">Describes the <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to evaluate an XPath expression.</span></span>  
  
 [<span data-ttu-id="7b1d8-110">XPathNavigator によるノードの一致</span><span class="sxs-lookup"><span data-stu-id="7b1d8-110">Matching Nodes using XPathNavigator</span></span>](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 <span data-ttu-id="7b1d8-111">ノードが XPath 式に一致するかどうかを判定するために使用される <xref:System.Xml.XPath.XPathNavigator.Matches%2A> クラスの <xref:System.Xml.XPath.XPathNavigator> メソッドについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-111">Describes the <xref:System.Xml.XPath.XPathNavigator.Matches%2A> method of the <xref:System.Xml.XPath.XPathNavigator> class used to determine if a node matches an XPath expression.</span></span>  
  
 [<span data-ttu-id="7b1d8-112">XPath クエリで認識されるノード型</span><span class="sxs-lookup"><span data-stu-id="7b1d8-112">Node Types Recognized with XPath Queries</span></span>](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 <span data-ttu-id="7b1d8-113">XPath クエリで認識されるノードの型について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-113">Describes the types of nodes recognized in an XPath query.</span></span>  
  
 [<span data-ttu-id="7b1d8-114">XPath クエリおよび名前空間</span><span class="sxs-lookup"><span data-stu-id="7b1d8-114">XPath Queries and Namespaces</span></span>](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 <span data-ttu-id="7b1d8-115">XPath クエリでの名前空間の使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-115">Describes the use of namespaces in an XPath query.</span></span>  
  
 [<span data-ttu-id="7b1d8-116">コンパイルされた XPath 式</span><span class="sxs-lookup"><span data-stu-id="7b1d8-116">Compiled XPath Expressions</span></span>](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)  
 <span data-ttu-id="7b1d8-117">コンパイル済みの XPath クエリを表す <xref:System.Xml.XPath.XPathExpression> クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="7b1d8-117">Describes the <xref:System.Xml.XPath.XPathExpression> class that represents a compiled XPath query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1d8-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b1d8-118">See also</span></span>

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [<span data-ttu-id="7b1d8-119">XPath データ モデルを使用した XML データの処理</span><span class="sxs-lookup"><span data-stu-id="7b1d8-119">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [<span data-ttu-id="7b1d8-120">XPathDocument および XmlDocument を使用した XML データの読み取り</span><span class="sxs-lookup"><span data-stu-id="7b1d8-120">Reading XML Data using XPathDocument and XmlDocument</span></span>](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md)
- [<span data-ttu-id="7b1d8-121">XPathNavigator による XML データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="7b1d8-121">Accessing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/accessing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="7b1d8-122">XPathNavigator による XML データの編集</span><span class="sxs-lookup"><span data-stu-id="7b1d8-122">Editing XML Data using XPathNavigator</span></span>](../../../../docs/standard/data/xml/editing-xml-data-using-xpathnavigator.md)
- [<span data-ttu-id="7b1d8-123">XPathNavigator を使用したスキーマ検証</span><span class="sxs-lookup"><span data-stu-id="7b1d8-123">Schema Validation using XPathNavigator</span></span>](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md)
