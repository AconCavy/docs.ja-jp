---
title: Mod 演算子
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: b7552550d4b0496d6ad7ee76a7327054d544b874
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350915"
---
# <a name="mod-operator-visual-basic"></a><span data-ttu-id="08e7b-102">Mod 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08e7b-102">Mod operator (Visual Basic)</span></span>

<span data-ttu-id="08e7b-103">2 つの数値を除算して剰余のみを返します。</span><span class="sxs-lookup"><span data-stu-id="08e7b-103">Divides two numbers and returns only the remainder.</span></span>

## <a name="syntax"></a><span data-ttu-id="08e7b-104">構文</span><span class="sxs-lookup"><span data-stu-id="08e7b-104">Syntax</span></span>

```vb
result = number1 Mod number2
```

## <a name="parts"></a><span data-ttu-id="08e7b-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="08e7b-105">Parts</span></span>

`result` \
<span data-ttu-id="08e7b-106">必須です。</span><span class="sxs-lookup"><span data-stu-id="08e7b-106">Required.</span></span> <span data-ttu-id="08e7b-107">任意の数値変数またはプロパティ。</span><span class="sxs-lookup"><span data-stu-id="08e7b-107">Any numeric variable or property.</span></span>

`number1` \
<span data-ttu-id="08e7b-108">必須です。</span><span class="sxs-lookup"><span data-stu-id="08e7b-108">Required.</span></span> <span data-ttu-id="08e7b-109">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="08e7b-109">Any numeric expression.</span></span>

`number2` \
<span data-ttu-id="08e7b-110">必須です。</span><span class="sxs-lookup"><span data-stu-id="08e7b-110">Required.</span></span> <span data-ttu-id="08e7b-111">任意の数式。</span><span class="sxs-lookup"><span data-stu-id="08e7b-111">Any numeric expression.</span></span>

## <a name="supported-types"></a><span data-ttu-id="08e7b-112">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="08e7b-112">Supported types</span></span>

<span data-ttu-id="08e7b-113">すべての数値型。</span><span class="sxs-lookup"><span data-stu-id="08e7b-113">All numeric types.</span></span> <span data-ttu-id="08e7b-114">これには、符号なしおよび浮動小数点の型と `Decimal` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-114">This includes the unsigned and floating-point types and `Decimal`.</span></span>

## <a name="result"></a><span data-ttu-id="08e7b-115">結果</span><span class="sxs-lookup"><span data-stu-id="08e7b-115">Result</span></span>

<span data-ttu-id="08e7b-116">結果は、`number1` が `number2` で除算された後の剰余になります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-116">The result is the remainder after `number1` is divided by `number2`.</span></span> <span data-ttu-id="08e7b-117">たとえば、式 `14 Mod 4` は 2 に評価されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-117">For example, the expression `14 Mod 4` evaluates to 2.</span></span>

> [!NOTE]
> <span data-ttu-id="08e7b-118">数学的には "*剰余 (remainder)* " と "*法 (modulus)* " には違いがあり、負数の場合の結果が異なります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-118">There is a difference between *remainder* and *modulus* in mathematics, with different results for negative numbers.</span></span> <span data-ttu-id="08e7b-119">Visual Basic の `Mod` 演算子、.NET Framework の `op_Modulus` 演算子、基礎になる [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 命令ではすべて、剰余演算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-119">The `Mod` operator in Visual Basic, the .NET Framework `op_Modulus` operator, and the underlying [rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL instruction all perform a remainder operation.</span></span>

<span data-ttu-id="08e7b-120">`Mod` 演算の結果には被除数の符号 (`number1`) が保持されるため、結果は正または負になります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-120">The result of a `Mod` operation retains the sign of the dividend, `number1`, and so it may be positive or negative.</span></span> <span data-ttu-id="08e7b-121">結果は常に (-`number2`, `number2`) の範囲 (境界値は除外) になります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-121">The result is always in the range (-`number2`, `number2`), exclusive.</span></span> <span data-ttu-id="08e7b-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="08e7b-122">For example:</span></span>

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a><span data-ttu-id="08e7b-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="08e7b-123">Remarks</span></span>

<span data-ttu-id="08e7b-124">`number1` または `number2` のいずれかが浮動小数点値の場合、除算の浮動小数点の剰余が返されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-124">If either `number1` or `number2` is a floating-point value, the floating-point remainder of the division is returned.</span></span> <span data-ttu-id="08e7b-125">結果のデータ型は、`number1` と `number2` のデータ型による除算によって得られる可能性のあるすべての値を保持できる最小のデータ型です。</span><span class="sxs-lookup"><span data-stu-id="08e7b-125">The data type of the result is the smallest data type that can hold all possible values that result from division with the data types of `number1` and `number2`.</span></span>

<span data-ttu-id="08e7b-126">`number1` または `number2` が [Nothing](../../../visual-basic/language-reference/nothing.md) に評価された場合は、0 として扱われます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-126">If `number1` or `number2` evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>

<span data-ttu-id="08e7b-127">関連する演算子には、次のものがあります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-127">Related operators include the following:</span></span>

- <span data-ttu-id="08e7b-128">[\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) では、除算の整数の商が返されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-128">The [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md) returns the integer quotient of a division.</span></span> <span data-ttu-id="08e7b-129">たとえば、式 `14 \ 4` は 3 に評価されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-129">For example, the expression `14 \ 4` evaluates to 3.</span></span>

- <span data-ttu-id="08e7b-130">[/ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) では、剰余を含めた完全な商が浮動小数点数として返されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-130">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) returns the full quotient, including the remainder, as a floating-point number.</span></span> <span data-ttu-id="08e7b-131">たとえば、式 `14 / 4` は 3.5 に評価されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-131">For example, the expression `14 / 4` evaluates to 3.5.</span></span>

## <a name="attempted-division-by-zero"></a><span data-ttu-id="08e7b-132">0 除算を試行した場合</span><span class="sxs-lookup"><span data-stu-id="08e7b-132">Attempted division by zero</span></span>

<span data-ttu-id="08e7b-133">`number2` がゼロに評価された場合、`Mod` 演算子の動作は、オペランドのデータ型によって異なります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-133">If `number2` evaluates to zero, the behavior of the `Mod` operator depends on the data type of the operands:</span></span>

- <span data-ttu-id="08e7b-134">整数除算では、コンパイル時に `number2` を特定できない場合は <xref:System.DivideByZeroException> 例外がスローされ、コンパイル時に `number2` がゼロに評価された場合、コンパイル時エラー `BC30542 Division by zero occurred while evaluating this expression` が生成されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-134">An integral division throws a <xref:System.DivideByZeroException> exception if `number2` cannot be determined in compile-time and generates a compile-time error `BC30542 Division by zero occurred while evaluating this expression` if `number2` is evaluated to zero at compile-time.</span></span>
- <span data-ttu-id="08e7b-135">浮動小数点の除算では <xref:System.Double.NaN?displayProperty=nameWithType> が返されます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-135">A floating-point division returns <xref:System.Double.NaN?displayProperty=nameWithType>.</span></span>

## <a name="equivalent-formula"></a><span data-ttu-id="08e7b-136">同等の式</span><span class="sxs-lookup"><span data-stu-id="08e7b-136">Equivalent formula</span></span>

<span data-ttu-id="08e7b-137">式 `a Mod b` は、次のいずれかの式と同等です。</span><span class="sxs-lookup"><span data-stu-id="08e7b-137">The expression `a Mod b` is equivalent to either of the following formulas:</span></span>

`a - (b * (a \ b))`

`a - (b * Fix(a / b))`

## <a name="floating-point-imprecision"></a><span data-ttu-id="08e7b-138">浮動小数点の誤差</span><span class="sxs-lookup"><span data-stu-id="08e7b-138">Floating-point imprecision</span></span>

<span data-ttu-id="08e7b-139">浮動小数点数を操作する場合、メモリ内で常に正確な 10 進数表現が使用されるとは限らないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="08e7b-139">When you work with floating-point numbers, remember that they do not always have a precise decimal representation in memory.</span></span> <span data-ttu-id="08e7b-140">これにより、値の比較や `Mod` 演算子など、特定の演算によって、予期しない結果につながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-140">This can lead to unexpected results from certain operations, such as value comparison and the `Mod` operator.</span></span> <span data-ttu-id="08e7b-141">詳細については、「[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08e7b-141">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="overloading"></a><span data-ttu-id="08e7b-142">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="08e7b-142">Overloading</span></span>

<span data-ttu-id="08e7b-143">`Mod` 演算子は "*オーバーロード*" できます。つまり、クラスまたは構造体がその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-143">The `Mod` operator can be *overloaded*, which means that a class or structure can redefine its behavior.</span></span> <span data-ttu-id="08e7b-144">コードによって、そのようなオーバーロードを含むクラスまたは構造体のインスタンスに `Mod` を適用する場合は、その再定義された動作を確実に理解しておいてください。</span><span class="sxs-lookup"><span data-stu-id="08e7b-144">If your code applies `Mod` to an instance of a class or structure that includes such an overload, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="08e7b-145">詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08e7b-145">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="example"></a><span data-ttu-id="08e7b-146">例</span><span class="sxs-lookup"><span data-stu-id="08e7b-146">Example</span></span>

<span data-ttu-id="08e7b-147">次の例では、`Mod` 演算子を使用して 2 つの数値を除算し、剰余だけを返します。</span><span class="sxs-lookup"><span data-stu-id="08e7b-147">The following example uses the `Mod` operator to divide two numbers and return only the remainder.</span></span> <span data-ttu-id="08e7b-148">どちらかの数値が浮動小数点数の場合、結果は剰余を表す浮動小数点数になります。</span><span class="sxs-lookup"><span data-stu-id="08e7b-148">If either number is a floating-point number, the result is a floating-point number that represents the remainder.</span></span>

[!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]

## <a name="example"></a><span data-ttu-id="08e7b-149">例</span><span class="sxs-lookup"><span data-stu-id="08e7b-149">Example</span></span>

<span data-ttu-id="08e7b-150">次の例は、浮動小数点オペランドにおける誤差の可能性を示しています。</span><span class="sxs-lookup"><span data-stu-id="08e7b-150">The following example demonstrates the potential imprecision of floating-point operands.</span></span> <span data-ttu-id="08e7b-151">最初のステートメントでは、オペランドは `Double` であり、0.2 は、格納された値 0.20000000000000001 での無限に繰り返される 2 進小数です。</span><span class="sxs-lookup"><span data-stu-id="08e7b-151">In the first statement, the operands are `Double`, and 0.2 is an infinitely repeating binary fraction with a stored value of 0.20000000000000001.</span></span> <span data-ttu-id="08e7b-152">2 番目のステートメントでは、リテラル型の文字 `D` によって両方のオペランドが強制的に `Decimal` になり、0.2 には正確な表現が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08e7b-152">In the second statement, the literal type character `D` forces both operands to `Decimal`, and 0.2 has a precise representation.</span></span>

[!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]

## <a name="see-also"></a><span data-ttu-id="08e7b-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="08e7b-153">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [<span data-ttu-id="08e7b-154">算術演算子</span><span class="sxs-lookup"><span data-stu-id="08e7b-154">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="08e7b-155">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="08e7b-155">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="08e7b-156">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="08e7b-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="08e7b-157">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="08e7b-157">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="08e7b-158">Visual Basic における算術演算子</span><span class="sxs-lookup"><span data-stu-id="08e7b-158">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="08e7b-159">\ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08e7b-159">\ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/integer-division-operator.md)
