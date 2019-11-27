---
title: Group Join 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 0546c86322663ce6c56a89e63311d0f02f88cfe4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346852"
---
# <a name="group-join-clause-visual-basic"></a><span data-ttu-id="abb4b-102">Group Join 句 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="abb4b-102">Group Join Clause (Visual Basic)</span></span>
<span data-ttu-id="abb4b-103">2 つのコレクションを、単一の階層コレクションに結合します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-103">Combines two collections into a single hierarchical collection.</span></span> <span data-ttu-id="abb4b-104">結合操作は、一致するキーに基づいています。</span><span class="sxs-lookup"><span data-stu-id="abb4b-104">The join operation is based on matching keys.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb4b-105">構文</span><span class="sxs-lookup"><span data-stu-id="abb4b-105">Syntax</span></span>  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a><span data-ttu-id="abb4b-106">指定項目</span><span class="sxs-lookup"><span data-stu-id="abb4b-106">Parts</span></span>  
  
|<span data-ttu-id="abb4b-107">用語</span><span class="sxs-lookup"><span data-stu-id="abb4b-107">Term</span></span>|<span data-ttu-id="abb4b-108">Definition</span><span class="sxs-lookup"><span data-stu-id="abb4b-108">Definition</span></span>|  
|---|---|  
|`element`|<span data-ttu-id="abb4b-109">必須。</span><span class="sxs-lookup"><span data-stu-id="abb4b-109">Required.</span></span> <span data-ttu-id="abb4b-110">結合されているコレクションのコントロール変数。</span><span class="sxs-lookup"><span data-stu-id="abb4b-110">The control variable for the collection being joined.</span></span>|  
|`type`|<span data-ttu-id="abb4b-111">省略可。</span><span class="sxs-lookup"><span data-stu-id="abb4b-111">Optional.</span></span> <span data-ttu-id="abb4b-112">`element` の型。</span><span class="sxs-lookup"><span data-stu-id="abb4b-112">The type of `element`.</span></span> <span data-ttu-id="abb4b-113">`type` が指定されていない場合、`element` の種類は `collection`から推論されます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-113">If no `type` is specified, the type of `element` is inferred from `collection`.</span></span>|  
|`collection`|<span data-ttu-id="abb4b-114">必須。</span><span class="sxs-lookup"><span data-stu-id="abb4b-114">Required.</span></span> <span data-ttu-id="abb4b-115">`Group Join` 演算子の左辺にあるコレクションと結合するコレクションです。</span><span class="sxs-lookup"><span data-stu-id="abb4b-115">The collection to combine with the collection that is on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="abb4b-116">`Group Join` 句は、`Join` の句または別の `Group Join` 句で入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-116">A `Group Join` clause can be nested in a `Join` clause or in another `Group Join` clause.</span></span>|  
|<span data-ttu-id="abb4b-117">`key1` `Equals` `key2`</span><span class="sxs-lookup"><span data-stu-id="abb4b-117">`key1` `Equals` `key2`</span></span>|<span data-ttu-id="abb4b-118">必須。</span><span class="sxs-lookup"><span data-stu-id="abb4b-118">Required.</span></span> <span data-ttu-id="abb4b-119">結合されているコレクションのキーを識別します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-119">Identifies keys for the collections being joined.</span></span> <span data-ttu-id="abb4b-120">`Equals` 演算子を使用して、結合されているコレクションのキーを比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abb4b-120">You must use the `Equals` operator to compare keys from the collections being joined.</span></span> <span data-ttu-id="abb4b-121">結合条件を結合するには、複数のキーを識別するために、`And` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-121">You can combine join conditions by using the `And` operator to identify multiple keys.</span></span> <span data-ttu-id="abb4b-122">`key1` パラメーターは、`Join` 演算子の左側のコレクションのものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="abb4b-122">The `key1` parameter must be from the collection on the left side of the `Join` operator.</span></span> <span data-ttu-id="abb4b-123">`key2` パラメーターは、`Join` 演算子の右側にあるコレクションのものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="abb4b-123">The `key2` parameter must be from the collection on the right side of the `Join` operator.</span></span><br /><br /> <span data-ttu-id="abb4b-124">結合条件で使用されるキーは、コレクションの複数の項目を含む式にすることができます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-124">The keys used in the join condition can be expressions that include more than one item from the collection.</span></span> <span data-ttu-id="abb4b-125">ただし、各キー式には、それぞれのコレクションの項目だけを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-125">However, each key expression can contain only items from its respective collection.</span></span>|  
|`expressionList`|<span data-ttu-id="abb4b-126">必須。</span><span class="sxs-lookup"><span data-stu-id="abb4b-126">Required.</span></span> <span data-ttu-id="abb4b-127">コレクションの要素のグループを集計する方法を識別する1つ以上の式。</span><span class="sxs-lookup"><span data-stu-id="abb4b-127">One or more expressions that identify how the groups of elements from the collection are aggregated.</span></span> <span data-ttu-id="abb4b-128">グループ化された結果のメンバー名を特定するには、`Group` キーワード (`<alias> = Group`) を使用します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-128">To identify a member name for the grouped results, use the `Group` keyword (`<alias> = Group`).</span></span> <span data-ttu-id="abb4b-129">グループに適用する集計関数を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-129">You can also include aggregate functions to apply to the group.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abb4b-130">コメント</span><span class="sxs-lookup"><span data-stu-id="abb4b-130">Remarks</span></span>  
 <span data-ttu-id="abb4b-131">`Group Join` 句は、結合されているコレクションのキー値の一致に基づいて2つのコレクションを結合します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-131">The `Group Join` clause combines two collections based on matching key values from the collections being joined.</span></span> <span data-ttu-id="abb4b-132">結果のコレクションには、最初のコレクションのキー値に一致する2番目のコレクションの要素のコレクションを参照するメンバーを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-132">The resulting collection can contain a member that references a collection of elements from the second collection that match the key value from the first collection.</span></span> <span data-ttu-id="abb4b-133">2番目のコレクションのグループ化された要素に適用する集計関数を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-133">You can also specify aggregate functions to apply to the grouped elements from the second collection.</span></span> <span data-ttu-id="abb4b-134">集計関数の詳細については、「 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abb4b-134">For information about aggregate functions, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="abb4b-135">たとえば、マネージャーのコレクションや従業員のコレクションなどを検討します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-135">Consider, for example, a collection of managers and a collection of employees.</span></span> <span data-ttu-id="abb4b-136">両方のコレクションの要素には、特定のマネージャーに報告する従業員を識別する ManagerID プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="abb4b-136">Elements from both collections have a ManagerID property that identifies the employees that report to a particular manager.</span></span> <span data-ttu-id="abb4b-137">結合操作の結果には、各マネージャーと、一致する ManagerID 値を持つ従業員の結果が含まれます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-137">The results from a join operation would contain a result for each manager and employee with a matching ManagerID value.</span></span> <span data-ttu-id="abb4b-138">`Group Join` 操作の結果には、マネージャーの完全な一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-138">The results from a `Group Join` operation would contain the complete list of managers.</span></span> <span data-ttu-id="abb4b-139">各マネージャーの結果には、特定のマネージャーに一致した従業員の一覧を参照するメンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-139">Each manager result would have a member that referenced the list of employees that were a match for the specific manager.</span></span>  
  
 <span data-ttu-id="abb4b-140">`Group Join` 操作によって生成されるコレクションには、`From` 句で指定されたコレクションの値と `Group Join` 句の `Into` 句で識別された式の任意の組み合わせを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-140">The collection resulting from a `Group Join` operation can contain any combination of values from the collection identified in the `From` clause and the expressions identified in the `Into` clause of the `Group Join` clause.</span></span> <span data-ttu-id="abb4b-141">`Into` 句の有効な式の詳細については、「 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abb4b-141">For more information about valid expressions for the `Into` clause, see [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).</span></span>  
  
 <span data-ttu-id="abb4b-142">`Group Join` 操作は、`Group Join` 演算子の左側で特定されたコレクションからすべての結果を返します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-142">A `Group Join` operation will return all results from the collection identified on the left side of the `Group Join` operator.</span></span> <span data-ttu-id="abb4b-143">これは、結合されているコレクションに一致するものがない場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="abb4b-143">This is true even if there are no matches in the collection being joined.</span></span> <span data-ttu-id="abb4b-144">これは、SQL の `LEFT OUTER JOIN` に似ています。</span><span class="sxs-lookup"><span data-stu-id="abb4b-144">This is like a `LEFT OUTER JOIN` in SQL.</span></span>  
  
 <span data-ttu-id="abb4b-145">`Join` 句を使用して、コレクションを1つのコレクションに結合できます。</span><span class="sxs-lookup"><span data-stu-id="abb4b-145">You can use the `Join` clause to combine collections into a single collection.</span></span> <span data-ttu-id="abb4b-146">これは、SQL の `INNER JOIN` に相当します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-146">This is equivalent to an `INNER JOIN` in SQL.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abb4b-147">例</span><span class="sxs-lookup"><span data-stu-id="abb4b-147">Example</span></span>  
 <span data-ttu-id="abb4b-148">次のコード例では、`Group Join` 句を使用して2つのコレクションを結合します。</span><span class="sxs-lookup"><span data-stu-id="abb4b-148">The following code example joins two collections by using the `Group Join` clause.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a><span data-ttu-id="abb4b-149">参照</span><span class="sxs-lookup"><span data-stu-id="abb4b-149">See also</span></span>

- [<span data-ttu-id="abb4b-150">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="abb4b-150">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="abb4b-151">クエリ</span><span class="sxs-lookup"><span data-stu-id="abb4b-151">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="abb4b-152">Select 句</span><span class="sxs-lookup"><span data-stu-id="abb4b-152">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="abb4b-153">From 句</span><span class="sxs-lookup"><span data-stu-id="abb4b-153">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="abb4b-154">Join 句</span><span class="sxs-lookup"><span data-stu-id="abb4b-154">Join Clause</span></span>](../../../visual-basic/language-reference/queries/join-clause.md)
- [<span data-ttu-id="abb4b-155">WHERE 句</span><span class="sxs-lookup"><span data-stu-id="abb4b-155">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="abb4b-156">Group By 句</span><span class="sxs-lookup"><span data-stu-id="abb4b-156">Group By Clause</span></span>](../../../visual-basic/language-reference/queries/group-by-clause.md)
