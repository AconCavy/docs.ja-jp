---
title: AndAlso 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: a52f598c8a7c7a79b0f2436f1add7b3eb5d5261b
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2019
ms.locfileid: "71835226"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="dc61d-102">AndAlso 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc61d-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="dc61d-103">2つの式の短絡論理積を実行します。</span><span class="sxs-lookup"><span data-stu-id="dc61d-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc61d-104">構文</span><span class="sxs-lookup"><span data-stu-id="dc61d-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="dc61d-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="dc61d-105">Parts</span></span>  
  
|<span data-ttu-id="dc61d-106">用語</span><span class="sxs-lookup"><span data-stu-id="dc61d-106">Term</span></span>|<span data-ttu-id="dc61d-107">Definition</span><span class="sxs-lookup"><span data-stu-id="dc61d-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="dc61d-108">必須。</span><span class="sxs-lookup"><span data-stu-id="dc61d-108">Required.</span></span> <span data-ttu-id="dc61d-109">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc61d-109">Any `Boolean` expression.</span></span> <span data-ttu-id="dc61d-110">結果は、2つの式を比較した結果 `Boolean` になります。</span><span class="sxs-lookup"><span data-stu-id="dc61d-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="dc61d-111">必須。</span><span class="sxs-lookup"><span data-stu-id="dc61d-111">Required.</span></span> <span data-ttu-id="dc61d-112">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc61d-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="dc61d-113">必須。</span><span class="sxs-lookup"><span data-stu-id="dc61d-113">Required.</span></span> <span data-ttu-id="dc61d-114">任意のブール型 ( `Boolean` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="dc61d-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc61d-115">コメント</span><span class="sxs-lookup"><span data-stu-id="dc61d-115">Remarks</span></span>  
 <span data-ttu-id="dc61d-116">コンパイルされたコードが別の式の結果に応じて1つの式の評価をバイパスできる場合、論理操作は*ショートサーキット*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="dc61d-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="dc61d-117">最初に評価された式の結果が演算の最終結果を決定した場合、最終的な結果を変更できないため、2番目の式を評価する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="dc61d-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="dc61d-118">ショートサーキットは、バイパスされた式が複雑な場合や、プロシージャ呼び出しが関係している場合に、パフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="dc61d-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="dc61d-119">両方の式が `True`に評価される場合、`result` は `True`ます。</span><span class="sxs-lookup"><span data-stu-id="dc61d-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="dc61d-120">次の表は、`result` がどのように決定されるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="dc61d-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="dc61d-121">`expression1` の場合</span><span class="sxs-lookup"><span data-stu-id="dc61d-121">If `expression1` is</span></span>|<span data-ttu-id="dc61d-122">`expression2`</span><span class="sxs-lookup"><span data-stu-id="dc61d-122">And `expression2` is</span></span>|<span data-ttu-id="dc61d-123">`result` の値はです。</span><span class="sxs-lookup"><span data-stu-id="dc61d-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="dc61d-124">(評価なし)</span><span class="sxs-lookup"><span data-stu-id="dc61d-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="dc61d-125">データの種類</span><span class="sxs-lookup"><span data-stu-id="dc61d-125">Data Types</span></span>  
 <span data-ttu-id="dc61d-126">`AndAlso` 演算子は、[ブールデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)に対してのみ定義されます。</span><span class="sxs-lookup"><span data-stu-id="dc61d-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="dc61d-127">Visual Basic は、式を評価する前に、必要に応じて各オペランドを `Boolean` に変換します。</span><span class="sxs-lookup"><span data-stu-id="dc61d-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="dc61d-128">結果を数値型に代入すると、Visual Basic によって `Boolean` からその型に変換され、`False` が `0` になり、`True` が `-1`になります。</span><span class="sxs-lookup"><span data-stu-id="dc61d-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="dc61d-129">詳細については、「[ブール型変換](../data-types/boolean-data-type.md#type-conversions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc61d-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="dc61d-130">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="dc61d-130">Overloading</span></span>  
 <span data-ttu-id="dc61d-131">[And 演算子](../../../visual-basic/language-reference/operators/and-operator.md)と[IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)は*オーバーロード*することができます。つまり、クラスまたは構造体が、そのクラスまたは構造体の型を持つ場合に、その動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="dc61d-131">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="dc61d-132">`And` 演算子と `IsFalse` 演算子のオーバーロードは、`AndAlso` 演算子の動作に影響します。</span><span class="sxs-lookup"><span data-stu-id="dc61d-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="dc61d-133">コードで `And` と `IsFalse`をオーバーロードするクラスまたは構造体の `AndAlso` を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="dc61d-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="dc61d-134">詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dc61d-134">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc61d-135">例</span><span class="sxs-lookup"><span data-stu-id="dc61d-135">Example</span></span>  
 <span data-ttu-id="dc61d-136">次の例では、`AndAlso` 演算子を使用して、2つの式の論理積を実行します。</span><span class="sxs-lookup"><span data-stu-id="dc61d-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="dc61d-137">結果は、conjoined 式全体が true であるかどうかを示す `Boolean` 値です。</span><span class="sxs-lookup"><span data-stu-id="dc61d-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="dc61d-138">最初の式が `False`場合、2番目の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="dc61d-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="dc61d-139">前の例では、`True`、`False`、および `False`の結果がそれぞれ生成されます。</span><span class="sxs-lookup"><span data-stu-id="dc61d-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="dc61d-140">`secondCheck`の計算では、最初の式が既に `False`ているため、2番目の式は評価されません。</span><span class="sxs-lookup"><span data-stu-id="dc61d-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="dc61d-141">ただし、2番目の式は `thirdCheck`の計算で評価されます。</span><span class="sxs-lookup"><span data-stu-id="dc61d-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc61d-142">例</span><span class="sxs-lookup"><span data-stu-id="dc61d-142">Example</span></span>  
 <span data-ttu-id="dc61d-143">次の例は、配列の要素の中から特定の値を検索する `Function` プロシージャを示しています。</span><span class="sxs-lookup"><span data-stu-id="dc61d-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="dc61d-144">配列が空の場合、または配列の長さを超えた場合、`While` のステートメントでは、検索値に対して配列要素がテストされません。</span><span class="sxs-lookup"><span data-stu-id="dc61d-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="dc61d-145">参照</span><span class="sxs-lookup"><span data-stu-id="dc61d-145">See also</span></span>

- [<span data-ttu-id="dc61d-146">論理/ビット演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc61d-146">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="dc61d-147">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="dc61d-147">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="dc61d-148">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="dc61d-148">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="dc61d-149">And 演算子</span><span class="sxs-lookup"><span data-stu-id="dc61d-149">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="dc61d-150">IsFalse 演算子</span><span class="sxs-lookup"><span data-stu-id="dc61d-150">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="dc61d-151">Visual Basic の論理演算子とビット処理演算子</span><span class="sxs-lookup"><span data-stu-id="dc61d-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
