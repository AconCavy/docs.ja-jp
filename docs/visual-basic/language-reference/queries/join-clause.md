---
title: Join 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: b0baca9f897a00b3c6c67699629477ff385d6ef7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353265"
---
# <a name="join-clause-visual-basic"></a><span data-ttu-id="664f0-102">Join 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="664f0-102">Join Clause (Visual Basic)</span></span>

<span data-ttu-id="664f0-103">2 つのコレクションを単一のコレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="664f0-103">Combines two collections into a single collection.</span></span> <span data-ttu-id="664f0-104">結合操作は、一致するキーに基づき、`Equals` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="664f0-104">The join operation is based on matching keys and uses the `Equals` operator.</span></span>

## <a name="syntax"></a><span data-ttu-id="664f0-105">構文</span><span class="sxs-lookup"><span data-stu-id="664f0-105">Syntax</span></span>

```vb
Join element In collection _
  [ joinClause _ ]
  [ groupJoinClause ... _ ]
On key1 Equals key2 [ And key3 Equals key4 [... ]
```

## <a name="parts"></a><span data-ttu-id="664f0-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="664f0-106">Parts</span></span>

<span data-ttu-id="664f0-107">`element` 必須。</span><span class="sxs-lookup"><span data-stu-id="664f0-107">`element` Required.</span></span> <span data-ttu-id="664f0-108">結合されるコレクションの制御変数。</span><span class="sxs-lookup"><span data-stu-id="664f0-108">The control variable for the collection being joined.</span></span>

`collection`  
<span data-ttu-id="664f0-109">必須です。</span><span class="sxs-lookup"><span data-stu-id="664f0-109">Required.</span></span> <span data-ttu-id="664f0-110">`Join` 演算子の左側に指定されているコレクションと結合するコレクション。</span><span class="sxs-lookup"><span data-stu-id="664f0-110">The collection to combine with the collection identified on the left side of the `Join` operator.</span></span> <span data-ttu-id="664f0-111">`Join` 句は、別の `Join` 句、または `Group Join` 句で入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="664f0-111">A `Join` clause can be nested in another `Join` clause, or in a `Group Join` clause.</span></span>

`joinClause`  
<span data-ttu-id="664f0-112">任意。</span><span class="sxs-lookup"><span data-stu-id="664f0-112">Optional.</span></span> <span data-ttu-id="664f0-113">クエリをさらに絞り込むための 1 つ以上の追加の `Join` 句。</span><span class="sxs-lookup"><span data-stu-id="664f0-113">One or more additional `Join` clauses to further refine the query.</span></span>

`groupJoinClause`  
<span data-ttu-id="664f0-114">任意。</span><span class="sxs-lookup"><span data-stu-id="664f0-114">Optional.</span></span> <span data-ttu-id="664f0-115">クエリをさらに絞り込むための 1 つ以上の追加の `Group Join` 句。</span><span class="sxs-lookup"><span data-stu-id="664f0-115">One or more additional `Group Join` clauses to further refine the query.</span></span>

<span data-ttu-id="664f0-116">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="664f0-116">`key1` `Equals` `key2`</span></span>  
<span data-ttu-id="664f0-117">必須です。</span><span class="sxs-lookup"><span data-stu-id="664f0-117">Required.</span></span> <span data-ttu-id="664f0-118">結合されるコレクションのキーを識別します。</span><span class="sxs-lookup"><span data-stu-id="664f0-118">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="664f0-119">`Equals` 演算子を使用して、結合されるコレクションのキーを比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="664f0-119">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="664f0-120">結合条件を組み合わせるには、複数のキーを識別するために、`And` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="664f0-120">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="664f0-121">`key1` は、`Join` 演算子の左側にあるコレクションのものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="664f0-121">`key1` must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="664f0-122">`key2` は、`Join` 演算子の右側にあるコレクションのものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="664f0-122">`key2` must be from the collection on the right side of the `Join` operator.</span></span>

<span data-ttu-id="664f0-123">結合条件で使用されるキーは、コレクションからの複数の項目を含む式にすることができます。</span><span class="sxs-lookup"><span data-stu-id="664f0-123">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="664f0-124">ただし、各キー式には、それぞれのコレクションの項目のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="664f0-124">However, each key expression can contain only items from its respective collection.</span></span>

## <a name="remarks"></a><span data-ttu-id="664f0-125">Remarks</span><span class="sxs-lookup"><span data-stu-id="664f0-125">Remarks</span></span>

<span data-ttu-id="664f0-126">`Join` 句は、結合されるコレクションからの一致するキー値に基づいて、2 つのコレクションを組み合わせます。</span><span class="sxs-lookup"><span data-stu-id="664f0-126">The `Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="664f0-127">結果のコレクションには、`Join` 演算子の左側に指定されたコレクションと、`Join` 句で指定されたコレクションからの値の任意の組み合わせが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="664f0-127">The resulting collection can contain any combination of values from the collection identified on the left side of the `Join` operator and the collection identified in the `Join` clause.</span></span> <span data-ttu-id="664f0-128">クエリから返されるのは、`Equals` 演算子によって指定された条件を満たした結果だけです。</span><span class="sxs-lookup"><span data-stu-id="664f0-128">The query will return only results for which the condition specified by the `Equals` operator is met.</span></span> <span data-ttu-id="664f0-129">これは、SQL の `INNER JOIN` と同じです。</span><span class="sxs-lookup"><span data-stu-id="664f0-129">This is equivalent to an `INNER JOIN` in SQL.</span></span>

<span data-ttu-id="664f0-130">クエリで複数の `Join` 句を使用して、複数のコレクションを 1 つのコレクションに結合できます。</span><span class="sxs-lookup"><span data-stu-id="664f0-130">You can use multiple `Join` clauses in a query to join two or more collections into a single collection.</span></span>

<span data-ttu-id="664f0-131">暗黙的結合を実行して、`Join` 句を使用せずにコレクションを結合することができます。</span><span class="sxs-lookup"><span data-stu-id="664f0-131">You can perform an implicit join to combine collections without the `Join` clause.</span></span> <span data-ttu-id="664f0-132">これを行うには、`From` 句に複数の `In` 句を含め、結合に使用するキーを識別する `Where` 句を指定します。</span><span class="sxs-lookup"><span data-stu-id="664f0-132">To do this, include multiple `In` clauses in your `From` clause and specify a `Where` clause that identifies the keys that you want to use for the join.</span></span>

<span data-ttu-id="664f0-133">`Group Join` 句を使用して、コレクションを、単一の階層コレクションに結合することができます。</span><span class="sxs-lookup"><span data-stu-id="664f0-133">You can use the `Group Join` clause to combine collections into a single hierarchical collection.</span></span> <span data-ttu-id="664f0-134">これは、SQL の `LEFT OUTER JOIN` に似ています。</span><span class="sxs-lookup"><span data-stu-id="664f0-134">This is like a `LEFT OUTER JOIN` in SQL.</span></span>

## <a name="example"></a><span data-ttu-id="664f0-135">例</span><span class="sxs-lookup"><span data-stu-id="664f0-135">Example</span></span>

<span data-ttu-id="664f0-136">次のコード例では、暗黙的結合を実行して、顧客のリストと注文を結合しています。</span><span class="sxs-lookup"><span data-stu-id="664f0-136">The following code example performs an implicit join to combine a list of customers with their orders.</span></span>

[!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]

## <a name="example"></a><span data-ttu-id="664f0-137">例</span><span class="sxs-lookup"><span data-stu-id="664f0-137">Example</span></span>

<span data-ttu-id="664f0-138">次のコード例では、`Join` 句を使用して 2 つのコレクションを結合しています。</span><span class="sxs-lookup"><span data-stu-id="664f0-138">The following code example joins two collections by using the `Join` clause.</span></span>

[!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]

<span data-ttu-id="664f0-139">この例では、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="664f0-139">This example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon`

`explorer (2424), File Explorer`

`cmd (5136), Command Window`

## <a name="example"></a><span data-ttu-id="664f0-140">例</span><span class="sxs-lookup"><span data-stu-id="664f0-140">Example</span></span>

<span data-ttu-id="664f0-141">次のコード例では、2 つのキー列で `Join` 句を使用して、2 つのコレクションを結合しています。</span><span class="sxs-lookup"><span data-stu-id="664f0-141">The following code example joins two collections by using the `Join` clause with two key columns.</span></span>

[!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]

<span data-ttu-id="664f0-142">この例では、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="664f0-142">The example will produce output similar to the following:</span></span>

`winlogon (968), Windows Logon, Priority = 13`

`cmd (700), Command Window, Priority = 8`

`explorer (2424), File Explorer, Priority = 8`

## <a name="see-also"></a><span data-ttu-id="664f0-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="664f0-143">See also</span></span>

- [<span data-ttu-id="664f0-144">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="664f0-144">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="664f0-145">クエリ</span><span class="sxs-lookup"><span data-stu-id="664f0-145">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="664f0-146">Select 句</span><span class="sxs-lookup"><span data-stu-id="664f0-146">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="664f0-147">From 句</span><span class="sxs-lookup"><span data-stu-id="664f0-147">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="664f0-148">Group Join 句</span><span class="sxs-lookup"><span data-stu-id="664f0-148">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [<span data-ttu-id="664f0-149">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="664f0-149">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
