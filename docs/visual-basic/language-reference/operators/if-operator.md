---
title: If 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249488"
---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="19ff1-102">If 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19ff1-102">If Operator (Visual Basic)</span></span>

<span data-ttu-id="19ff1-103">ショートサーキット評価を使用して、条件に応じて 2 つの値のいずれかを返します。</span><span class="sxs-lookup"><span data-stu-id="19ff1-103">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="19ff1-104">`If` 演算子は、3 つの引数または 2 つの引数を指定して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-104">The `If` operator can be called with three arguments or with two arguments.</span></span>

## <a name="syntax"></a><span data-ttu-id="19ff1-105">構文</span><span class="sxs-lookup"><span data-stu-id="19ff1-105">Syntax</span></span>

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="19ff1-106">3 つの引数を指定して If 演算子を呼び出す場合</span><span class="sxs-lookup"><span data-stu-id="19ff1-106">If operator called with three arguments</span></span>

<span data-ttu-id="19ff1-107">3 つの引数を使用して `If` を呼び出す場合、最初の引数は `Boolean` としてキャストできる値に評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="19ff1-107">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="19ff1-108">この `Boolean` 値によって、他の 2 つの引数のうち、どちらが評価されて返されるかが決まります。</span><span class="sxs-lookup"><span data-stu-id="19ff1-108">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="19ff1-109">次の一覧は、3 つの引数を使用して `If` 演算子を呼び出す場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-109">The following list applies only when the `If` operator is called by using three arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="19ff1-110">指定項目</span><span class="sxs-lookup"><span data-stu-id="19ff1-110">Parts</span></span>

|<span data-ttu-id="19ff1-111">用語</span><span class="sxs-lookup"><span data-stu-id="19ff1-111">Term</span></span>|<span data-ttu-id="19ff1-112">定義</span><span class="sxs-lookup"><span data-stu-id="19ff1-112">Definition</span></span>|
|---|---|
|`argument1`|<span data-ttu-id="19ff1-113">必須です。</span><span class="sxs-lookup"><span data-stu-id="19ff1-113">Required.</span></span> <span data-ttu-id="19ff1-114">`Boolean`。</span><span class="sxs-lookup"><span data-stu-id="19ff1-114">`Boolean`.</span></span> <span data-ttu-id="19ff1-115">他のどの引数を評価して返すかを決定します。</span><span class="sxs-lookup"><span data-stu-id="19ff1-115">Determines which of the other arguments to evaluate and return.</span></span>|
|`argument2`|<span data-ttu-id="19ff1-116">必須です。</span><span class="sxs-lookup"><span data-stu-id="19ff1-116">Required.</span></span> <span data-ttu-id="19ff1-117">`Object`。</span><span class="sxs-lookup"><span data-stu-id="19ff1-117">`Object`.</span></span> <span data-ttu-id="19ff1-118">`argument1` が `True` に評価された場合に、評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-118">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|
|`argument3`|<span data-ttu-id="19ff1-119">必須です。</span><span class="sxs-lookup"><span data-stu-id="19ff1-119">Required.</span></span> <span data-ttu-id="19ff1-120">`Object`。</span><span class="sxs-lookup"><span data-stu-id="19ff1-120">`Object`.</span></span> <span data-ttu-id="19ff1-121">`argument1` が `False` に評価された場合、または `argument1` が [Nothing](../../../visual-basic/language-reference/nothing.md) に評価された [null 許容](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` 変数である場合に、評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-121">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>|

<span data-ttu-id="19ff1-122">3 つの引数を指定して呼び出される `If` 演算子は、ショートサーキット評価を使用する点を除き、`IIf` 関数と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="19ff1-122">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="19ff1-123">`IIf` 関数では常に、その 3 つの引数がすべて評価されます。それに対し、3 つの引数を持つ `If` 演算子では、そのうちの 2 つだけが評価されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-123">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="19ff1-124">最初の `If` 引数が評価され、結果が `Boolean` 値 (`True` または `False`) としてキャストされます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-124">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="19ff1-125">値が `True` の場合、`argument2` が評価され、その値が返されますが、`argument3` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="19ff1-125">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="19ff1-126">`Boolean` 式の値が `False` の場合、`argument3` が評価され、その値が返されますが、`argument2` は評価されません。</span><span class="sxs-lookup"><span data-stu-id="19ff1-126">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="19ff1-127">次の例では、3 つの引数が使用されている場合の `If` の使用法を示しています。</span><span class="sxs-lookup"><span data-stu-id="19ff1-127">The following examples illustrate the use of `If` when three arguments are used:</span></span>

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

<span data-ttu-id="19ff1-128">次の例は、ショートサーキット評価の値を示しています。</span><span class="sxs-lookup"><span data-stu-id="19ff1-128">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="19ff1-129">この例では、変数 `divisor` による変数 `number` の除算が 2 回試行されていることを示しています。これは `divisor` がゼロの場合以外に行われます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-129">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="19ff1-130">該当する場合は 0 が返されます。また、実行時エラーが発生するため、除算を実行しようとしないでください。</span><span class="sxs-lookup"><span data-stu-id="19ff1-130">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="19ff1-131">`If` 式ではショートサーキット評価が使用されるため、最初の引数の値に応じて、2 番目または 3 番目の引数のいずれかが評価されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-131">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="19ff1-132">最初の引数が true の場合、除数はゼロではなく、2 番目の引数を評価して除算を実行しても問題はありません。</span><span class="sxs-lookup"><span data-stu-id="19ff1-132">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="19ff1-133">最初の引数が false の場合、3 番目の引数のみが評価され、0 が返されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-133">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="19ff1-134">したがって、除数が 0 の場合、除算の実行は試みられず、エラーも発生しません。</span><span class="sxs-lookup"><span data-stu-id="19ff1-134">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="19ff1-135">ただし、`IIf` ではショートサーキット評価が使用されないため、最初の引数が false の場合でも 2 番目の引数が評価されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-135">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="19ff1-136">これにより、実行時の 0 除算エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="19ff1-136">This causes a run-time divide-by-zero error.</span></span>

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="19ff1-137">2 つの引数を指定して If 演算子を呼び出す場合</span><span class="sxs-lookup"><span data-stu-id="19ff1-137">If operator called with two arguments</span></span>

<span data-ttu-id="19ff1-138">`If` の最初の引数は省略できます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-138">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="19ff1-139">これにより、2 つの引数のみを使用してこの演算子を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-139">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="19ff1-140">次の一覧は、2 つの引数を使用して `If` 演算子を呼び出す場合にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-140">The following list applies only when the `If` operator is called with two arguments.</span></span>

### <a name="parts"></a><span data-ttu-id="19ff1-141">指定項目</span><span class="sxs-lookup"><span data-stu-id="19ff1-141">Parts</span></span>

|<span data-ttu-id="19ff1-142">用語</span><span class="sxs-lookup"><span data-stu-id="19ff1-142">Term</span></span>|<span data-ttu-id="19ff1-143">定義</span><span class="sxs-lookup"><span data-stu-id="19ff1-143">Definition</span></span>|
|---|---|
|`argument2`|<span data-ttu-id="19ff1-144">必須です。</span><span class="sxs-lookup"><span data-stu-id="19ff1-144">Required.</span></span> <span data-ttu-id="19ff1-145">`Object`。</span><span class="sxs-lookup"><span data-stu-id="19ff1-145">`Object`.</span></span> <span data-ttu-id="19ff1-146">参照または null 許容値型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="19ff1-146">Must be a reference or nullable value type.</span></span> <span data-ttu-id="19ff1-147">`Nothing` 以外に評価された場合に、評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-147">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|
|`argument3`|<span data-ttu-id="19ff1-148">必須です。</span><span class="sxs-lookup"><span data-stu-id="19ff1-148">Required.</span></span> <span data-ttu-id="19ff1-149">`Object`。</span><span class="sxs-lookup"><span data-stu-id="19ff1-149">`Object`.</span></span> <span data-ttu-id="19ff1-150">`argument2` が `Nothing` に評価された場合に、評価されて返されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-150">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|

<span data-ttu-id="19ff1-151">`Boolean` 引数が省略された場合、最初の引数は参照または null 許容値型でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="19ff1-151">When the `Boolean` argument is omitted, the first argument must be a reference or nullable value type.</span></span> <span data-ttu-id="19ff1-152">最初の引数が `Nothing` に評価された場合は、2 番目の引数の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-152">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="19ff1-153">その他すべての場合、最初の引数の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="19ff1-153">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="19ff1-154">次の例は、この評価のしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="19ff1-154">The following example illustrates how this evaluation works:</span></span>

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a><span data-ttu-id="19ff1-155">関連項目</span><span class="sxs-lookup"><span data-stu-id="19ff1-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [<span data-ttu-id="19ff1-156">null 許容値型</span><span class="sxs-lookup"><span data-stu-id="19ff1-156">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="19ff1-157">Nothing</span><span class="sxs-lookup"><span data-stu-id="19ff1-157">Nothing</span></span>](../nothing.md)
