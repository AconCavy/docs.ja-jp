---
title: 量指定子操作 (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5899af79799d5b8404e60027d7ba1b005c4b1b79
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423360"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="7ecec-102">量指定子操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="7ecec-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="7ecec-103">量指定子操作は、シーケンス内の要素の一部またはすべてが条件を満たしているかどうかを示す <xref:System.Boolean> 値を返します。</span><span class="sxs-lookup"><span data-stu-id="7ecec-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="7ecec-104">次の図は、2 つの異なるソース シーケンスに対する、2 つの異なる量指定子操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="7ecec-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="7ecec-105">最初の操作では、1 つ以上の要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="7ecec-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="7ecec-106">2 番目の操作では、すべての要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="7ecec-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 量指定子操作](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="7ecec-108">次のセクションでは、量指定子操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="7ecec-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ecec-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="7ecec-109">Methods</span></span>  
  
|<span data-ttu-id="7ecec-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="7ecec-110">Method Name</span></span>|<span data-ttu-id="7ecec-111">説明</span><span class="sxs-lookup"><span data-stu-id="7ecec-111">Description</span></span>|<span data-ttu-id="7ecec-112">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="7ecec-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="7ecec-113">説明</span><span class="sxs-lookup"><span data-stu-id="7ecec-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7ecec-114">すべて</span><span class="sxs-lookup"><span data-stu-id="7ecec-114">All</span></span>|<span data-ttu-id="7ecec-115">シーケンス内のすべての要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="7ecec-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7ecec-116">該当なし。</span><span class="sxs-lookup"><span data-stu-id="7ecec-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ecec-117">どれでも可</span><span class="sxs-lookup"><span data-stu-id="7ecec-117">Any</span></span>|<span data-ttu-id="7ecec-118">シーケンス内のいずれかの要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="7ecec-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7ecec-119">該当なし。</span><span class="sxs-lookup"><span data-stu-id="7ecec-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7ecec-120">内容</span><span class="sxs-lookup"><span data-stu-id="7ecec-120">Contains</span></span>|<span data-ttu-id="7ecec-121">指定した要素がシーケンスに格納されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="7ecec-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="7ecec-122">該当なし。</span><span class="sxs-lookup"><span data-stu-id="7ecec-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  
  
## <a name="see-also"></a><span data-ttu-id="7ecec-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ecec-123">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7ecec-124">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="7ecec-124">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="7ecec-125">方法: 実行時に述語フィルターを動的に指定する</span><span class="sxs-lookup"><span data-stu-id="7ecec-125">How to: Dynamically Specify Predicate Filters at Runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="7ecec-126">方法: 指定された単語のセットを含む文章を照会する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7ecec-126">How to: Query for Sentences that Contain a Specified Set of Words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
