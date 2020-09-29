---
title: 量指定子操作 (C#)
description: 量指定子操作について説明します。 これらの操作では、シーケンス内の要素の一部またはすべてが条件を満たしているかどうかを示すブール値が返されます。
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ffefe1715fd8a074692967e825e0f55673bb2b27
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202540"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="feb7b-104">量指定子操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="feb7b-104">Quantifier Operations (C#)</span></span>

<span data-ttu-id="feb7b-105">量指定子操作は、シーケンス内の要素の一部またはすべてが条件を満たしているかどうかを示す <xref:System.Boolean> 値を返します。</span><span class="sxs-lookup"><span data-stu-id="feb7b-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="feb7b-106">次の図は、2 つの異なるソース シーケンスに対する、2 つの異なる量指定子操作を示しています。</span><span class="sxs-lookup"><span data-stu-id="feb7b-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="feb7b-107">最初の操作では、1 つ以上の要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="feb7b-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="feb7b-108">2 番目の操作では、すべての要素が文字 'A' であるかどうかを尋ねていて、その結果は `true` です。</span><span class="sxs-lookup"><span data-stu-id="feb7b-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![LINQ 量指定子操作](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="feb7b-110">次のセクションでは、量指定子操作を実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="feb7b-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="feb7b-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="feb7b-111">Methods</span></span>  
  
|<span data-ttu-id="feb7b-112">メソッド名</span><span class="sxs-lookup"><span data-stu-id="feb7b-112">Method Name</span></span>|<span data-ttu-id="feb7b-113">説明</span><span class="sxs-lookup"><span data-stu-id="feb7b-113">Description</span></span>|<span data-ttu-id="feb7b-114">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="feb7b-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="feb7b-115">説明</span><span class="sxs-lookup"><span data-stu-id="feb7b-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="feb7b-116">すべて</span><span class="sxs-lookup"><span data-stu-id="feb7b-116">All</span></span>|<span data-ttu-id="feb7b-117">シーケンス内のすべての要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="feb7b-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="feb7b-118">該当なし。</span><span class="sxs-lookup"><span data-stu-id="feb7b-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="feb7b-119">どれでも可</span><span class="sxs-lookup"><span data-stu-id="feb7b-119">Any</span></span>|<span data-ttu-id="feb7b-120">シーケンス内のいずれかの要素が条件を満たしているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="feb7b-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="feb7b-121">該当なし。</span><span class="sxs-lookup"><span data-stu-id="feb7b-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="feb7b-122">内容</span><span class="sxs-lookup"><span data-stu-id="feb7b-122">Contains</span></span>|<span data-ttu-id="feb7b-123">指定した要素がシーケンスに格納されているかどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="feb7b-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="feb7b-124">該当なし。</span><span class="sxs-lookup"><span data-stu-id="feb7b-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="feb7b-125">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="feb7b-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="feb7b-126">すべて</span><span class="sxs-lookup"><span data-stu-id="feb7b-126">All</span></span>  

<span data-ttu-id="feb7b-127">次の例では、`All` を使用して、すべての文字列が特定の長さであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="feb7b-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="feb7b-128">どれでも可</span><span class="sxs-lookup"><span data-stu-id="feb7b-128">Any</span></span>  

<span data-ttu-id="feb7b-129">次の例では、`Any` を使用して、任意の文字列が "o" で開始されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="feb7b-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="feb7b-130">内容</span><span class="sxs-lookup"><span data-stu-id="feb7b-130">Contains</span></span>  

<span data-ttu-id="feb7b-131">次の例では、`Contains` を使用して、配列に特定の要素が含まれることを確認します。</span><span class="sxs-lookup"><span data-stu-id="feb7b-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="feb7b-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="feb7b-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="feb7b-133">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="feb7b-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="feb7b-134">実行時における述語フィルターの動的指定</span><span class="sxs-lookup"><span data-stu-id="feb7b-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="feb7b-135">指定されたワードのセットを含む文章を照会する方法 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="feb7b-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
