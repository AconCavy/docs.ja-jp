---
title: + 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.+
helpviewer_keywords:
- arithmetic operators [Visual Basic], addition
- + operator
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
- sum operator [Visual Basic]
ms.assetid: 5694778f-0a2c-4539-8009-f66f318fb46d
ms.openlocfilehash: 12c14b3be0562a31470ddbd2d5489ccdbdf3b62b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350289"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b1387-102">+ 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1387-102">+ Operator (Visual Basic)</span></span>
<span data-ttu-id="b1387-103">2つの数値を加算するか、数値式の正の値を返します。</span><span class="sxs-lookup"><span data-stu-id="b1387-103">Adds two numbers or returns the positive value of a numeric expression.</span></span> <span data-ttu-id="b1387-104">は、2つの文字列式を連結するためにも使用できます。</span><span class="sxs-lookup"><span data-stu-id="b1387-104">Can also be used to concatenate two string expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1387-105">構文</span><span class="sxs-lookup"><span data-stu-id="b1387-105">Syntax</span></span>  
  
```vb
expression1 + expression2
```
  
<span data-ttu-id="b1387-106">または</span><span class="sxs-lookup"><span data-stu-id="b1387-106">or</span></span>

```vb  
+expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="b1387-107">指定項目</span><span class="sxs-lookup"><span data-stu-id="b1387-107">Parts</span></span>  
  
|<span data-ttu-id="b1387-108">用語</span><span class="sxs-lookup"><span data-stu-id="b1387-108">Term</span></span>|<span data-ttu-id="b1387-109">定義</span><span class="sxs-lookup"><span data-stu-id="b1387-109">Definition</span></span>|  
|---|---|  
|`expression1`|<span data-ttu-id="b1387-110">必須。</span><span class="sxs-lookup"><span data-stu-id="b1387-110">Required.</span></span> <span data-ttu-id="b1387-111">任意の数値または文字列式。</span><span class="sxs-lookup"><span data-stu-id="b1387-111">Any numeric or string expression.</span></span>|  
|`expression2`|<span data-ttu-id="b1387-112">`+` 演算子が負の値を計算する場合を除き、必須です。</span><span class="sxs-lookup"><span data-stu-id="b1387-112">Required unless the `+` operator is calculating a negative value.</span></span> <span data-ttu-id="b1387-113">任意の数値または文字列式。</span><span class="sxs-lookup"><span data-stu-id="b1387-113">Any numeric or string expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="b1387-114">結果</span><span class="sxs-lookup"><span data-stu-id="b1387-114">Result</span></span>  
 <span data-ttu-id="b1387-115">`expression1` と `expression2` が両方とも数値の場合、結果は算術和になります。</span><span class="sxs-lookup"><span data-stu-id="b1387-115">If `expression1` and `expression2` are both numeric, the result is their arithmetic sum.</span></span>  
  
 <span data-ttu-id="b1387-116">`expression2` が存在しない場合、`+` 演算子は、式の変更されていない値の*単項*id 演算子です。</span><span class="sxs-lookup"><span data-stu-id="b1387-116">If `expression2` is absent, the `+` operator is the *unary* identity operator for the unchanged value of an expression.</span></span> <span data-ttu-id="b1387-117">この意味では、操作は `expression1`の符号を保持することで構成されるため、`expression1` が負の場合、結果は負になります。</span><span class="sxs-lookup"><span data-stu-id="b1387-117">In this sense, the operation consists of retaining the sign of `expression1`, so the result is negative if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="b1387-118">`expression1` と `expression2` が両方とも文字列の場合、結果はその値を連結したものになります。</span><span class="sxs-lookup"><span data-stu-id="b1387-118">If `expression1` and `expression2` are both strings, the result is the concatenation of their values.</span></span>  
  
 <span data-ttu-id="b1387-119">`expression1` と `expression2` の型が混在している場合、実行される操作は、その型、内容、および[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b1387-119">If `expression1` and `expression2` are of mixed types, the action taken depends on their types, their contents, and the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="b1387-120">詳細については、「解説」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1387-120">For more information, see the tables in "Remarks."</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="b1387-121">サポートされている型</span><span class="sxs-lookup"><span data-stu-id="b1387-121">Supported Types</span></span>  
 <span data-ttu-id="b1387-122">符号なしおよび浮動小数点型および `Decimal`、`String`を含むすべての数値型。</span><span class="sxs-lookup"><span data-stu-id="b1387-122">All numeric types, including the unsigned and floating-point types and `Decimal`, and `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1387-123">コメント</span><span class="sxs-lookup"><span data-stu-id="b1387-123">Remarks</span></span>  
 <span data-ttu-id="b1387-124">一般に、`+` は可能な限り算術加算を実行し、両方の式が文字列である場合にのみ連結します。</span><span class="sxs-lookup"><span data-stu-id="b1387-124">In general, `+` performs arithmetic addition when possible, and concatenates only when both expressions are strings.</span></span>  
  
 <span data-ttu-id="b1387-125">どちらの式も `Object`でない場合、Visual Basic は次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="b1387-125">If neither expression is an `Object`, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="b1387-126">式のデータ型</span><span class="sxs-lookup"><span data-stu-id="b1387-126">Data types of expressions</span></span>|<span data-ttu-id="b1387-127">コンパイラによるアクション</span><span class="sxs-lookup"><span data-stu-id="b1387-127">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="b1387-128">両方の式は、数値データ型 (`SByte`、`Byte`、`Short`、`UShort`、`Integer`、`UInteger`、`Long`、`ULong`、`Decimal`、`Single`、または `Double`) です。</span><span class="sxs-lookup"><span data-stu-id="b1387-128">Both expressions are numeric data types (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, `ULong`, `Decimal`, `Single`, or `Double`)</span></span>|<span data-ttu-id="b1387-129">[追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1387-129">Add.</span></span> <span data-ttu-id="b1387-130">結果のデータ型は、`expression1` および `expression2`のデータ型に適した数値型です。</span><span class="sxs-lookup"><span data-stu-id="b1387-130">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="b1387-131">「[演算子の結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「整数演算」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1387-131">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="b1387-132">両方の式の型は `String`</span><span class="sxs-lookup"><span data-stu-id="b1387-132">Both expressions are of type `String`</span></span>|<span data-ttu-id="b1387-133">つなげ.</span><span class="sxs-lookup"><span data-stu-id="b1387-133">Concatenate.</span></span>|  
|<span data-ttu-id="b1387-134">一方の式は数値データ型で、もう一方は文字列です。</span><span class="sxs-lookup"><span data-stu-id="b1387-134">One expression is a numeric data type and the other is a string</span></span>|<span data-ttu-id="b1387-135">`Option Strict` が `On`場合は、コンパイラエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="b1387-135">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b1387-136">`Option Strict` が `Off`場合、`String` を `Double` に暗黙的に変換し、を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1387-136">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b1387-137">`String` を `Double`に変換できない場合は、<xref:System.InvalidCastException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b1387-137">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="b1387-138">1つの式は数値データ型であり、もう一方は[Nothing](../../../visual-basic/language-reference/nothing.md)です。</span><span class="sxs-lookup"><span data-stu-id="b1387-138">One expression is a numeric data type, and the other is [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>|<span data-ttu-id="b1387-139">を0として `Nothing` 値を加算します。</span><span class="sxs-lookup"><span data-stu-id="b1387-139">Add, with `Nothing` valued as zero.</span></span>|  
|<span data-ttu-id="b1387-140">一方の式は文字列で、もう一方は `Nothing`</span><span class="sxs-lookup"><span data-stu-id="b1387-140">One expression is a string, and the other is `Nothing`</span></span>|<span data-ttu-id="b1387-141">を連結して、値を "" と `Nothing` します。</span><span class="sxs-lookup"><span data-stu-id="b1387-141">Concatenate, with `Nothing` valued as "".</span></span>|  
  
 <span data-ttu-id="b1387-142">1つの式が `Object` 式の場合、Visual Basic は次のアクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="b1387-142">If one expression is an `Object` expression, Visual Basic takes the following actions.</span></span>  
  
|<span data-ttu-id="b1387-143">式のデータ型</span><span class="sxs-lookup"><span data-stu-id="b1387-143">Data types of expressions</span></span>|<span data-ttu-id="b1387-144">コンパイラによるアクション</span><span class="sxs-lookup"><span data-stu-id="b1387-144">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="b1387-145">`Object` 式は数値を保持し、もう一方は数値データ型です。</span><span class="sxs-lookup"><span data-stu-id="b1387-145">`Object` expression holds a numeric value and the other is a numeric data type</span></span>|<span data-ttu-id="b1387-146">`Option Strict` が `On`場合は、コンパイラエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="b1387-146">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b1387-147">`Option Strict` が `Off`場合は、を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1387-147">If `Option Strict` is `Off`, then add.</span></span>|  
|<span data-ttu-id="b1387-148">`Object` 式は数値を保持し、もう一方は型です `String`</span><span class="sxs-lookup"><span data-stu-id="b1387-148">`Object` expression holds a numeric value and the other is of type `String`</span></span>|<span data-ttu-id="b1387-149">`Option Strict` が `On`場合は、コンパイラエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="b1387-149">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b1387-150">`Option Strict` が `Off`場合、`String` を `Double` に暗黙的に変換し、を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1387-150">If `Option Strict` is `Off`, then implicitly convert the `String` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b1387-151">`String` を `Double`に変換できない場合は、<xref:System.InvalidCastException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b1387-151">If the `String` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="b1387-152">`Object` 式は文字列を保持し、もう1つは数値データ型です。</span><span class="sxs-lookup"><span data-stu-id="b1387-152">`Object` expression holds a string and the other is a numeric data type</span></span>|<span data-ttu-id="b1387-153">`Option Strict` が `On`場合は、コンパイラエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="b1387-153">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b1387-154">`Option Strict` が `Off`場合は、文字列 `Object` を `Double` に暗黙的に変換し、を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1387-154">If `Option Strict` is `Off`, then implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b1387-155">文字列 `Object` を `Double`に変換できない場合は、<xref:System.InvalidCastException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b1387-155">If the string `Object` cannot be converted to `Double`, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
|<span data-ttu-id="b1387-156">`Object` 式は文字列を保持し、もう一方は型です `String`</span><span class="sxs-lookup"><span data-stu-id="b1387-156">`Object` expression holds a string and the other is of type `String`</span></span>|<span data-ttu-id="b1387-157">`Option Strict` が `On`場合は、コンパイラエラーを生成します。</span><span class="sxs-lookup"><span data-stu-id="b1387-157">If `Option Strict` is `On`, then generate a compiler error.</span></span><br /><br /> <span data-ttu-id="b1387-158">`Option Strict` が `Off`場合は、`Object` を `String` に暗黙的に変換して連結します。</span><span class="sxs-lookup"><span data-stu-id="b1387-158">If `Option Strict` is `Off`, then implicitly convert `Object` to `String` and concatenate.</span></span>|  
  
 <span data-ttu-id="b1387-159">両方の式が `Object` 式の場合、Visual Basic は次の操作を実行します (`Option Strict Off` のみ)。</span><span class="sxs-lookup"><span data-stu-id="b1387-159">If both expressions are `Object` expressions, Visual Basic takes the following actions (`Option Strict Off` only).</span></span>  
  
|<span data-ttu-id="b1387-160">式のデータ型</span><span class="sxs-lookup"><span data-stu-id="b1387-160">Data types of expressions</span></span>|<span data-ttu-id="b1387-161">コンパイラによるアクション</span><span class="sxs-lookup"><span data-stu-id="b1387-161">Action by compiler</span></span>|  
|---|---|  
|<span data-ttu-id="b1387-162">数値を保持する `Object` 式の両方</span><span class="sxs-lookup"><span data-stu-id="b1387-162">Both `Object` expressions hold numeric values</span></span>|<span data-ttu-id="b1387-163">[追加] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b1387-163">Add.</span></span>|  
|<span data-ttu-id="b1387-164">どちらの `Object` 式も型 `String`</span><span class="sxs-lookup"><span data-stu-id="b1387-164">Both `Object` expressions are of type `String`</span></span>|<span data-ttu-id="b1387-165">つなげ.</span><span class="sxs-lookup"><span data-stu-id="b1387-165">Concatenate.</span></span>|  
|<span data-ttu-id="b1387-166">1つの `Object` 式は数値を保持し、もう一方は文字列を保持します。</span><span class="sxs-lookup"><span data-stu-id="b1387-166">One `Object` expression holds a numeric value and the other holds a string</span></span>|<span data-ttu-id="b1387-167">文字列 `Object` を `Double` に暗黙的に変換し、を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1387-167">Implicitly convert the string `Object` to `Double` and add.</span></span><br /><br /> <span data-ttu-id="b1387-168">文字列 `Object` を数値に変換できない場合は、<xref:System.InvalidCastException> 例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b1387-168">If the string `Object` cannot be converted to a numeric value, then throw an <xref:System.InvalidCastException> exception.</span></span>|  
  
 <span data-ttu-id="b1387-169">`Object` 式のいずれかが[Nothing](../../../visual-basic/language-reference/nothing.md)または <xref:System.DBNull>に評価される場合、`+` 演算子はその値を "" という値の `String` として扱います。</span><span class="sxs-lookup"><span data-stu-id="b1387-169">If either `Object` expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md) or <xref:System.DBNull>, the `+` operator treats it as a `String` with a value of "".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b1387-170">`+` 演算子を使用する場合、加算または文字列の連結が発生するかどうかを判断できないことがあります。</span><span class="sxs-lookup"><span data-stu-id="b1387-170">When you use the `+` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="b1387-171">`&` 演算子を連結に使用して、あいまいさをなくし、自己記述型のコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="b1387-171">Use the `&` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b1387-172">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="b1387-172">Overloading</span></span>  
 <span data-ttu-id="b1387-173">`+` 演算子は*オーバーロード*することができます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="b1387-173">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b1387-174">コードでこのようなクラスまたは構造体に対してこの演算子を使用する場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b1387-174">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b1387-175">詳細については、「[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b1387-175">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1387-176">例</span><span class="sxs-lookup"><span data-stu-id="b1387-176">Example</span></span>  
 <span data-ttu-id="b1387-177">次の例では、`+` 演算子を使用して数値を加算します。</span><span class="sxs-lookup"><span data-stu-id="b1387-177">The following example uses the `+` operator to add numbers.</span></span> <span data-ttu-id="b1387-178">オペランドが両方とも数値の場合、Visual Basic 演算結果が計算されます。</span><span class="sxs-lookup"><span data-stu-id="b1387-178">If the operands are both numeric, Visual Basic computes the arithmetic result.</span></span> <span data-ttu-id="b1387-179">算術結果は、2つのオペランドの合計を表します。</span><span class="sxs-lookup"><span data-stu-id="b1387-179">The arithmetic result represents the sum of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#6)]  
  
 <span data-ttu-id="b1387-180">`+` 演算子を使用して文字列を連結することもできます。</span><span class="sxs-lookup"><span data-stu-id="b1387-180">You can also use the `+` operator to concatenate strings.</span></span> <span data-ttu-id="b1387-181">オペランドが両方とも文字列の場合は、Visual Basic 連結します。</span><span class="sxs-lookup"><span data-stu-id="b1387-181">If the operands are both strings, Visual Basic concatenates them.</span></span> <span data-ttu-id="b1387-182">連結の結果は、2つのオペランドの内容で構成される1つの文字列を表します。</span><span class="sxs-lookup"><span data-stu-id="b1387-182">The concatenation result represents a single string consisting of the contents of the two operands one after the other.</span></span>  
  
 <span data-ttu-id="b1387-183">オペランドが混合型の場合、結果は[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="b1387-183">If the operands are of mixed types, the result depends on the setting of the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span> <span data-ttu-id="b1387-184">次の例は、`Option Strict` が `On`場合の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="b1387-184">The following example illustrates the result when `Option Strict` is `On`.</span></span>  
  
 [!code-vb[VbVbalrOperators#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class3.vb#53)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#51)]  
  
 <span data-ttu-id="b1387-185">次の例は、`Option Strict` が `Off`場合の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="b1387-185">The following example illustrates the result when `Option Strict` is `Off`.</span></span>  
  
 [!code-vb[VbVbalrOperators#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#54)]  
  
 [!code-vb[VbVbalrOperators#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#50)]  
[!code-vb[VbVbalrOperators#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class2.vb#52)]  
  
 <span data-ttu-id="b1387-186">あいまいさをなくすには、`+` の代わりに `&` 演算子を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1387-186">To eliminate ambiguity, you should use the `&` operator instead of `+` for concatenation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1387-187">関連項目</span><span class="sxs-lookup"><span data-stu-id="b1387-187">See also</span></span>

- [<span data-ttu-id="b1387-188">& 演算子</span><span class="sxs-lookup"><span data-stu-id="b1387-188">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="b1387-189">連結演算子</span><span class="sxs-lookup"><span data-stu-id="b1387-189">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="b1387-190">算術演算子</span><span class="sxs-lookup"><span data-stu-id="b1387-190">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="b1387-191">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="b1387-191">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b1387-192">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="b1387-192">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b1387-193">Visual Basic の算術演算子</span><span class="sxs-lookup"><span data-stu-id="b1387-193">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [<span data-ttu-id="b1387-194">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="b1387-194">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
