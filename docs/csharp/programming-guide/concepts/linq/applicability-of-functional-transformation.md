---
title: 関数型変換の適用範囲 (C#)
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: bc2678354bb45f1ed0a4076f278f52d0ee7d350e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594875"
---
# <a name="applicability-of-functional-transformation-c"></a><span data-ttu-id="2d8da-102">関数型変換の適用範囲 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d8da-102">Applicability of Functional Transformation (C#)</span></span>
<span data-ttu-id="2d8da-103">純粋関数型変換は、さまざまな状況で適用できます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-103">Pure functional transformations are applicable in a wide variety of situations.</span></span>  
  
 <span data-ttu-id="2d8da-104">関数型変換の方法は、構造化されたデータのクエリと操作に適しているため、LINQ テクノロジに適切に対応できます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-104">The functional transformation approach is ideally suited for querying and manipulating structured data; therefore it fits well with LINQ technologies.</span></span> <span data-ttu-id="2d8da-105">ただし、関数型変換の適用範囲は、LINQ で使用する場合に比べてはるかに広範です。</span><span class="sxs-lookup"><span data-stu-id="2d8da-105">However, functional transformation has a much wider applicability than use with LINQ.</span></span> <span data-ttu-id="2d8da-106">データ形式の変換を中心とする処理はすべて、関数型変換の適用対象と考えることができます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-106">Any process where the main focus is on transforming data from one form to another should probably be considered as a candidate for functional transformation.</span></span>  
  
 <span data-ttu-id="2d8da-107">この方法は、一見して適用対象とは思われない数多くの問題に適用できます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-107">This approach is applicable to many problems that might not appear at first glance to be a candidate.</span></span> <span data-ttu-id="2d8da-108">次に示す適用対象では、関数型変換を LINQ と組み合わせて、または切り離して使用することを検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d8da-108">Used in conjunction with or separately from LINQ, functional transformation should be considered for the following areas:</span></span>  
  
- <span data-ttu-id="2d8da-109">XML ベースのドキュメント。</span><span class="sxs-lookup"><span data-stu-id="2d8da-109">XML-based documents.</span></span> <span data-ttu-id="2d8da-110">XML 言語の整形式データは、関数型変換を通じて容易に操作できます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-110">Well-formed data of any XML dialect can be easily manipulated through functional transformation.</span></span> <span data-ttu-id="2d8da-111">詳細については、「[XML の関数型変換 (C#)](./functional-transformation-of-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d8da-111">For more information, see [Functional Transformation of XML (C#)](./functional-transformation-of-xml.md).</span></span>  
  
- <span data-ttu-id="2d8da-112">その他の構造化されたファイル形式。</span><span class="sxs-lookup"><span data-stu-id="2d8da-112">Other structured file formats.</span></span> <span data-ttu-id="2d8da-113">Windows.ini ファイルからプレーンテキストのドキュメントに至るほとんどのファイルは、分析や変換に適した構造を備えています。</span><span class="sxs-lookup"><span data-stu-id="2d8da-113">From Windows.ini files to plain text documents, most files have some structure that lends itself to analysis and transformation.</span></span>  
  
- <span data-ttu-id="2d8da-114">データ ストリーミング プロトコル。</span><span class="sxs-lookup"><span data-stu-id="2d8da-114">Data streaming protocols.</span></span> <span data-ttu-id="2d8da-115">通信プロトコルへのデータのエンコードおよび通信プロトコルからのデータのデコードは、単純な関数型変換で表せる場合がほとんどです。</span><span class="sxs-lookup"><span data-stu-id="2d8da-115">Encoding data into and decoding data from communication protocols can often be represented by a simple functional transform.</span></span>  
  
- <span data-ttu-id="2d8da-116">RDBMS データと OODBMS データ。</span><span class="sxs-lookup"><span data-stu-id="2d8da-116">RDBMS and OODBMS data.</span></span> <span data-ttu-id="2d8da-117">リレーショナル データベースおよびオブジェクト指向データベースは、構造化されたデータ ソースとして XML と同様に広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="2d8da-117">Relational and object-oriented databases, just like XML, are widely-used structured data sources.</span></span>  
  
- <span data-ttu-id="2d8da-118">数学的、統計的、および科学的なソリューション。</span><span class="sxs-lookup"><span data-stu-id="2d8da-118">Mathematic, statistic, and science solutions.</span></span> <span data-ttu-id="2d8da-119">これらの分野では、視覚化、予測、重要な問題の解決などを支援する際に、大きなデータ セットが操作される傾向があります。</span><span class="sxs-lookup"><span data-stu-id="2d8da-119">These fields tend to manipulate large data sets to assist the user in visualizing, estimating, or actually solving non-trivial problems.</span></span>  
  
 <span data-ttu-id="2d8da-120">「[純粋関数へのリファクタリング (C#)](./refactoring-into-pure-functions.md)」で説明しているように、純粋関数の使用は関数型プログラミングの一例です。</span><span class="sxs-lookup"><span data-stu-id="2d8da-120">As described in [Refactoring Into Pure Functions (C#)](./refactoring-into-pure-functions.md), using pure functions is an example of functional programming.</span></span> <span data-ttu-id="2d8da-121">純粋関数は、その直接的な利点に加えて、関数型変換の観点から問題について考える場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-121">In additional to their immediate benefits, using pure functions provides valuable experience in thinking about problems from a functional transformation perspective.</span></span> <span data-ttu-id="2d8da-122">この方法は、プログラムおよびクラスの設計にも大きな影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-122">This approach can also have major impact on program and class design.</span></span> <span data-ttu-id="2d8da-123">上に示したように、問題がデータ変換ソリューションに関連している場合は、特に影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="2d8da-123">This is especially true when a problem lends itself to a data transformation solution as described above.</span></span>  
  
 <span data-ttu-id="2d8da-124">このチュートリアルでは扱いませんが、関数型変換の観点から影響を受ける設計は、アクターとしてオブジェクトよりもプロセスに重点を置く傾向があり、その結果であるソリューションは、個別のオブジェクト状態変更ではなく一連の大規模な変換として実装される傾向にあります。</span><span class="sxs-lookup"><span data-stu-id="2d8da-124">Although they are beyond the scope of this tutorial, designs that are influenced by the functional transformation perspective tend to center on processes more than on objects as actors, and the resulting solution tends to be implemented as series of large-scale transformations, rather than individual object state changes.</span></span>  
  
 <span data-ttu-id="2d8da-125">繰り返しになりますが、C# は命令型の方法と関数型の方法の両方をサポートしているため、両方の要素を組み込むことがアプリケーションにとって最善の設計であることを覚えておいてください。</span><span class="sxs-lookup"><span data-stu-id="2d8da-125">Again, remember that C# supports both imperative and functional approaches, so the best design for your application might incorporate elements of both.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8da-126">参照</span><span class="sxs-lookup"><span data-stu-id="2d8da-126">See also</span></span>

- [<span data-ttu-id="2d8da-127">純粋関数型変換の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d8da-127">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="2d8da-128">XML の関数型変換 (C#)</span><span class="sxs-lookup"><span data-stu-id="2d8da-128">Functional Transformation of XML (C#)</span></span>](./functional-transformation-of-xml.md)
- [<span data-ttu-id="2d8da-129">純粋関数へのリファクタリング (C#)</span><span class="sxs-lookup"><span data-stu-id="2d8da-129">Refactoring Into Pure Functions (C#)</span></span>](./refactoring-into-pure-functions.md)
