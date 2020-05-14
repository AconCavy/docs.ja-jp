---
title: XML の純粋関数型変換
ms.date: 07/20/2015
ms.assetid: 5e19b74a-7773-4b58-b110-953ffd364c55
ms.openlocfilehash: cccc1321d934dca5563a1e9e52af9352231bd558
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346599"
---
# <a name="pure-functional-transformations-of-xml-visual-basic"></a><span data-ttu-id="982ac-102">XML の純粋関数型変換 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ac-102">Pure Functional Transformations of XML (Visual Basic)</span></span>
<span data-ttu-id="982ac-103">ここでは、XML の関数型変換に関するチュートリアルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="982ac-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="982ac-104">このチュートリアルには、関数型変換を使用する場合に理解しておく必要がある主な概念や言語構造についての説明と、関数型変換を使用して XML ドキュメントを操作する例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="982ac-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="982ac-105">このチュートリアルでは、LINQ to XML のコード例が示されますが、基本的概念はすべて他の LINQ テクノロジにも適用されます。</span><span class="sxs-lookup"><span data-stu-id="982ac-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="982ac-106">「[チュートリアル:WordprocessingML ドキュメント内のコンテンツの操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)」チュートリアルは、それぞれ直前の例を基に構築されています。</span><span class="sxs-lookup"><span data-stu-id="982ac-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="982ac-107">これらの例では、純粋関数型変換を使用して XML を操作する方法を説明する複数の例が示されています。</span><span class="sxs-lookup"><span data-stu-id="982ac-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="982ac-108">このチュートリアルでは、Visual Basic に関する実践的な知識を前提としています。</span><span class="sxs-lookup"><span data-stu-id="982ac-108">This tutorial assumes a working knowledge of Visual Basic.</span></span> <span data-ttu-id="982ac-109">このチュートリアルでは言語構造の詳細なセマンティクスについては説明しませんが、必要に応じて言語ドキュメントへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="982ac-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="982ac-110">コンピューター科学の基本概念と、XML 名前空間など XML に関する実践的な知識も前提としています。</span><span class="sxs-lookup"><span data-stu-id="982ac-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="982ac-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="982ac-111">In This Section</span></span>  
  
|<span data-ttu-id="982ac-112">トピック</span><span class="sxs-lookup"><span data-stu-id="982ac-112">Topic</span></span>|<span data-ttu-id="982ac-113">説明</span><span class="sxs-lookup"><span data-stu-id="982ac-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="982ac-114">純粋関数型変換の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ac-114">Introduction to Pure Functional Transformations (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="982ac-115">関数型変換について説明し、関連する用語を定義します。</span><span class="sxs-lookup"><span data-stu-id="982ac-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="982ac-116">チュートリアル: 遅延実行 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ac-116">Tutorial: Deferred Execution (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)|<span data-ttu-id="982ac-117">レイジー評価と遅延実行について詳細に説明します。</span><span class="sxs-lookup"><span data-stu-id="982ac-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="982ac-118">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ac-118">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="982ac-119">関数型変換について例を使用して説明するチュートリアルです。</span><span class="sxs-lookup"><span data-stu-id="982ac-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="982ac-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="982ac-120">See also</span></span>

- [<span data-ttu-id="982ac-121">XML ツリーのクエリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="982ac-121">Querying XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)
