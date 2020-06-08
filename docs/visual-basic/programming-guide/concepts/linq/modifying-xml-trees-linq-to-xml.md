---
title: XML ツリーの変更 (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 4ae511a5-4fc9-4178-9c8e-761357deae3f
ms.openlocfilehash: 3402188c4e34ef81bad41ed49f9236b4fb7c47ef
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406886"
---
# <a name="modifying-xml-trees-linq-to-xml-visual-basic"></a><span data-ttu-id="d3cd8-102">XML ツリーの変更 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-102">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="d3cd8-103">は、XML ツリーのメモリ内ストアです。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-103">is an in-memory store for an XML tree.</span></span> <span data-ttu-id="d3cd8-104">ソースから XML ツリーを読み込んだり解析したりした後に、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] を使用してツリーを直接変更することができます。その後、ツリーをシリアル化して、ファイルに保存したり、リモート サーバーに送信したりできます。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-104">After you load or parse an XML tree from a source, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] lets you modify that tree in place, and then serialize the tree, perhaps saving it to a file or sending it to a remote server.</span></span>  
  
 <span data-ttu-id="d3cd8-105">ツリーを直接変更する際には、<xref:System.Xml.Linq.XContainer.Add%2A> などの特定のメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-105">When you modify a tree in place, you use certain methods, such as <xref:System.Xml.Linq.XContainer.Add%2A>.</span></span>  
  
 <span data-ttu-id="d3cd8-106">ただし、これには別の方法もあります。それは、関数型構築を使用して、別の新しいツリーを生成する方法です。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-106">However, there is another approach, which is to use functional construction to generate a new tree with a different shape.</span></span> <span data-ttu-id="d3cd8-107">XML ツリーに対する変更の種類やツリーのサイズによっては、この方法の方が堅牢で、開発も容易になります。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-107">Depending on the types of changes that you need to make to your XML tree, and depending on the size of the tree, this approach can be more robust and easier to develop.</span></span> <span data-ttu-id="d3cd8-108">このセクションの最初のトピックでは、この 2 つの方法を比較します。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-108">The first topic in this section compares these two approaches.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3cd8-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d3cd8-109">In This Section</span></span>  
  
|<span data-ttu-id="d3cd8-110">トピック</span><span class="sxs-lookup"><span data-stu-id="d3cd8-110">Topic</span></span>|<span data-ttu-id="d3cd8-111">説明</span><span class="sxs-lookup"><span data-stu-id="d3cd8-111">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="d3cd8-112">メモリ内の XML ツリーの変更と関数型構築 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-112">In-Memory XML Tree Modification vs. Functional Construction (LINQ to XML) (Visual Basic)</span></span>](in-memory-xml-tree-modification-vs-functional-construction.md)|<span data-ttu-id="d3cd8-113">XML ツリーのメモリ内での変更と関数型構築とを比較します。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-113">Compares modifying an XML tree in memory to functional construction.</span></span>|  
|[<span data-ttu-id="d3cd8-114">XML ツリーへの要素、属性、およびノードの追加 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-114">Adding Elements, Attributes, and Nodes to an XML Tree (Visual Basic)</span></span>](adding-elements-attributes-and-nodes-to-an-xml-tree.md)|<span data-ttu-id="d3cd8-115">XML ツリーへの要素、属性、またはノードの追加に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-115">Provides information about adding elements, attributes, or nodes to an XML tree.</span></span>|  
|[<span data-ttu-id="d3cd8-116">XML ツリー内の要素、属性、およびノードの変更</span><span class="sxs-lookup"><span data-stu-id="d3cd8-116">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>](modifying-elements-attributes-and-nodes-in-an-xml-tree.md)|<span data-ttu-id="d3cd8-117">既存の要素、属性、またはノードの変更に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-117">Provides information about modifying existing elements, attributes, or nodes.</span></span>|  
|[<span data-ttu-id="d3cd8-118">XML ツリーからの要素、属性、およびノードの削除 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-118">Removing Elements, Attributes, and Nodes from an XML Tree (Visual Basic)</span></span>](removing-elements-attributes-and-nodes-from-an-xml-tree.md)|<span data-ttu-id="d3cd8-119">XML ツリーからの要素、属性、またはノードの削除に関する情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-119">Provides information about removing elements, attributes, or nodes from the XML tree.</span></span>|  
|[<span data-ttu-id="d3cd8-120">名前と値のペアの保持 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-120">Maintaining Name/Value Pairs (Visual Basic)</span></span>](maintaining-name-value-pairs.md)|<span data-ttu-id="d3cd8-121">アプリケーションの情報を名前/値のペアとして保持する方法について説明します。このような情報には、構成情報やグローバル設定があります。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-121">Describes how to maintain application information that is best kept as name/value pairs, such as configuration information or global settings.</span></span>|  
|[<span data-ttu-id="d3cd8-122">方法: XML ツリー全体の名前空間を変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-122">How to: Change the Namespace for an Entire XML Tree (Visual Basic)</span></span>](how-to-change-the-namespace-for-an-entire-xml-tree.md)|<span data-ttu-id="d3cd8-123">XML ツリーを名前空間の間で移動する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3cd8-123">Shows how to move an XML tree from one namespace into another.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3cd8-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3cd8-124">See also</span></span>

- [<span data-ttu-id="d3cd8-125">プログラミング ガイド (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d3cd8-125">Programming Guide (LINQ to XML) (Visual Basic)</span></span>](programming-guide-linq-to-xml.md)
