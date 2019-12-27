---
title: 比較演算子
ms.date: 07/20/2015
f1_keywords:
- vb.<>
- vb.>=
- vb.<=
- vb.>
- vb.<
helpviewer_keywords:
- greater than or equal to operator [Visual Basic]
- '>= operator [Visual Basic]'
- = operator [Visual Basic]
- < operator [Visual Basic]
- less than operator [Visual Basic]
- relational operators [Visual Basic], syntax
- Like operator [Visual Basic]
- <> operator [Visual Basic]
- '> operator [Visual Basic]'
- equal operator [Visual Basic]
- less than or equal to operator [Visual Basic]
- symbols, operators
- greater than operator [Visual Basic]
- comparing values [Visual Basic]
- operators [Visual Basic], relational
- string comparison [Visual Basic]
- not equal to comparison operator [Visual Basic]
- <= operator [Visual Basic]
- operators [Visual Basic], comparison
- Is operator [Visual Basic]
- comparison operators [Visual Basic], Visual Basic
ms.assetid: d6cb12a8-e52e-46a7-8aaf-f804d634a825
ms.openlocfilehash: ea7604626ede66da818e4bc22fe4922bc752dc2c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336079"
---
# <a name="comparison-operators-visual-basic"></a><span data-ttu-id="36588-102">比較演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="36588-102">Comparison Operators (Visual Basic)</span></span>
<span data-ttu-id="36588-103">Visual Basic で定義されている比較演算子を次に示します。</span><span class="sxs-lookup"><span data-stu-id="36588-103">The following are the comparison operators defined in Visual Basic.</span></span>

 <span data-ttu-id="36588-104">`<` 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-104">`<` operator</span></span>

 <span data-ttu-id="36588-105">`<=` 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-105">`<=` operator</span></span>

 <span data-ttu-id="36588-106">`>` 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-106">`>` operator</span></span>

 <span data-ttu-id="36588-107">`>=` 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-107">`>=` operator</span></span>

 <span data-ttu-id="36588-108">`=` 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-108">`=` operator</span></span>

 <span data-ttu-id="36588-109">`<>` 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-109">`<>` operator</span></span>

 [<span data-ttu-id="36588-110">Is 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-110">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)

 [<span data-ttu-id="36588-111">IsNot 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-111">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)

 [<span data-ttu-id="36588-112">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-112">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)

 <span data-ttu-id="36588-113">これらの演算子は、2つの式を比較して、両者が等しいかどうかを判断します。存在しない場合は、両者がどのように異なるかを判断します。</span><span class="sxs-lookup"><span data-stu-id="36588-113">These operators compare two expressions to determine whether or not they are equal, and if not, how they differ.</span></span> <span data-ttu-id="36588-114">`Is`、`IsNot`、および `Like` の詳細については、個別のヘルプページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="36588-114">`Is`, `IsNot`, and `Like` are discussed in detail on separate Help pages.</span></span> <span data-ttu-id="36588-115">このページでは、関係比較演算子について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="36588-115">The relational comparison operators are discussed in detail on this page.</span></span>

## <a name="syntax"></a><span data-ttu-id="36588-116">構文</span><span class="sxs-lookup"><span data-stu-id="36588-116">Syntax</span></span>
  
```vb
result = expression1 comparisonoperator expression2  
result = object1 [Is | IsNot] object2  
result = string Like pattern  
```  
  
## <a name="parts"></a><span data-ttu-id="36588-117">指定項目</span><span class="sxs-lookup"><span data-stu-id="36588-117">Parts</span></span>
 `result`  
 <span data-ttu-id="36588-118">必須。</span><span class="sxs-lookup"><span data-stu-id="36588-118">Required.</span></span> <span data-ttu-id="36588-119">比較の結果を表す `Boolean` 値。</span><span class="sxs-lookup"><span data-stu-id="36588-119">A `Boolean` value representing the result of the comparison.</span></span>

 <span data-ttu-id="36588-120">`expression1`, `expression2`</span><span class="sxs-lookup"><span data-stu-id="36588-120">`expression1`, `expression2`</span></span>  
 <span data-ttu-id="36588-121">必須。</span><span class="sxs-lookup"><span data-stu-id="36588-121">Required.</span></span> <span data-ttu-id="36588-122">任意の式。</span><span class="sxs-lookup"><span data-stu-id="36588-122">Any expression.</span></span>

 `comparisonoperator`  
 <span data-ttu-id="36588-123">必須。</span><span class="sxs-lookup"><span data-stu-id="36588-123">Required.</span></span> <span data-ttu-id="36588-124">任意の関係比較演算子。</span><span class="sxs-lookup"><span data-stu-id="36588-124">Any relational comparison operator.</span></span>

 <span data-ttu-id="36588-125">`object1`, `object2`</span><span class="sxs-lookup"><span data-stu-id="36588-125">`object1`, `object2`</span></span>  
 <span data-ttu-id="36588-126">必須。</span><span class="sxs-lookup"><span data-stu-id="36588-126">Required.</span></span> <span data-ttu-id="36588-127">参照オブジェクトの名前。</span><span class="sxs-lookup"><span data-stu-id="36588-127">Any reference object names.</span></span>

 `string`  
 <span data-ttu-id="36588-128">必須。</span><span class="sxs-lookup"><span data-stu-id="36588-128">Required.</span></span> <span data-ttu-id="36588-129">任意のブール型 ( `String` ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="36588-129">Any `String` expression.</span></span>

 `pattern`  
 <span data-ttu-id="36588-130">必須。</span><span class="sxs-lookup"><span data-stu-id="36588-130">Required.</span></span> <span data-ttu-id="36588-131">任意の `String` 式または文字の範囲。</span><span class="sxs-lookup"><span data-stu-id="36588-131">Any `String` expression or range of characters.</span></span>

## <a name="remarks"></a><span data-ttu-id="36588-132">コメント</span><span class="sxs-lookup"><span data-stu-id="36588-132">Remarks</span></span>
 <span data-ttu-id="36588-133">次の表に、関係比較演算子と、`result` が `True` か `False`かを決定する条件の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="36588-133">The following table contains a list of the relational comparison operators and the conditions that determine whether `result` is `True` or `False`.</span></span>

|<span data-ttu-id="36588-134">演算子</span><span class="sxs-lookup"><span data-stu-id="36588-134">Operator</span></span>|<span data-ttu-id="36588-135">`True`:</span><span class="sxs-lookup"><span data-stu-id="36588-135">`True` if</span></span>|<span data-ttu-id="36588-136">`False`:</span><span class="sxs-lookup"><span data-stu-id="36588-136">`False` if</span></span>|
|--------------|---------------|----------------|
|<span data-ttu-id="36588-137">`<` (より小さい)</span><span class="sxs-lookup"><span data-stu-id="36588-137">`<` (Less than)</span></span>|`expression1` < `expression2`|`expression1` >= `expression2`|
|<span data-ttu-id="36588-138">`<=` (以下)</span><span class="sxs-lookup"><span data-stu-id="36588-138">`<=` (Less than or equal to)</span></span>|`expression1` <= `expression2`|`expression1` > `expression2`|
|<span data-ttu-id="36588-139">`>` (より大きい)</span><span class="sxs-lookup"><span data-stu-id="36588-139">`>` (Greater than)</span></span>|`expression1` > `expression2`|`expression1` <= `expression2`|
|<span data-ttu-id="36588-140">`>=` (以上)</span><span class="sxs-lookup"><span data-stu-id="36588-140">`>=` (Greater than or equal to)</span></span>|`expression1` >= `expression2`|`expression1` < `expression2`|
|<span data-ttu-id="36588-141">`=` (等しい)</span><span class="sxs-lookup"><span data-stu-id="36588-141">`=` (Equal to)</span></span>|`expression1` = `expression2`|`expression1` <> `expression2`|
|<span data-ttu-id="36588-142">`<>` (等しくない)</span><span class="sxs-lookup"><span data-stu-id="36588-142">`<>` (Not equal to)</span></span>|`expression1` <> `expression2`|`expression1` = `expression2`|

> [!NOTE]
> <span data-ttu-id="36588-143">[= 演算子](../../../visual-basic/language-reference/operators/assignment-operator.md)は、代入演算子としても使用されます。</span><span class="sxs-lookup"><span data-stu-id="36588-143">The [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) is also used as an assignment operator.</span></span>

 <span data-ttu-id="36588-144">`Is` 演算子、`IsNot` 演算子、および `Like` 演算子には、前の表の演算子とは異なる特定の比較機能があります。</span><span class="sxs-lookup"><span data-stu-id="36588-144">The `Is` operator, the `IsNot` operator, and the `Like` operator have specific comparison functionalities that differ from the operators in the preceding table.</span></span>

## <a name="comparing-numbers"></a><span data-ttu-id="36588-145">数値の比較</span><span class="sxs-lookup"><span data-stu-id="36588-145">Comparing Numbers</span></span>
 <span data-ttu-id="36588-146">`Single` 型の式を `Double`型の1つと比較すると、`Single` 式が `Double`に変換されます。</span><span class="sxs-lookup"><span data-stu-id="36588-146">When you compare an expression of type `Single` to one of type `Double`, the `Single` expression is converted to `Double`.</span></span> <span data-ttu-id="36588-147">この動作は Visual Basic 6 とは逆の動作です。</span><span class="sxs-lookup"><span data-stu-id="36588-147">This behavior is opposite to the behavior found in Visual Basic 6.</span></span>

 <span data-ttu-id="36588-148">同様に、`Decimal` 型の式を `Single` または `Double`型の式と比較すると、`Decimal` 式は `Single` または `Double`に変換されます。</span><span class="sxs-lookup"><span data-stu-id="36588-148">Similarly, when you compare an expression of type `Decimal` to an expression of type `Single` or `Double`, the `Decimal` expression is converted to `Single` or `Double`.</span></span> <span data-ttu-id="36588-149">`Decimal` 式の場合、1E-28 未満の小数値は失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="36588-149">For `Decimal` expressions, any fractional value less than 1E-28 might be lost.</span></span> <span data-ttu-id="36588-150">このような小数値の損失によって、2つの値が等しくない場合に等しいと見なされることがあります。</span><span class="sxs-lookup"><span data-stu-id="36588-150">Such fractional value loss may cause two values to compare as equal when they are not.</span></span> <span data-ttu-id="36588-151">このため、等値 (`=`) を使用して2つの浮動小数点変数を比較する場合は注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="36588-151">For this reason, you should take care when using equality (`=`) to compare two floating-point variables.</span></span> <span data-ttu-id="36588-152">2つの数値の差の絶対値が許容範囲の最小値より小さいかどうかをテストする方が安全です。</span><span class="sxs-lookup"><span data-stu-id="36588-152">It is safer to test whether the absolute value of the difference between the two numbers is less than a small acceptable tolerance.</span></span>

### <a name="floating-point-imprecision"></a><span data-ttu-id="36588-153">浮動小数点おける誤差</span><span class="sxs-lookup"><span data-stu-id="36588-153">Floating-point Imprecision</span></span>
 <span data-ttu-id="36588-154">浮動小数点数を使用する場合は、メモリ内に常に正確な表現がないという点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="36588-154">When you work with floating-point numbers, keep in mind that they do not always have a precise representation in memory.</span></span> <span data-ttu-id="36588-155">これにより、値の比較や[Mod 演算子](../../../visual-basic/language-reference/operators/mod-operator.md)など、特定の操作によって予期しない結果が生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="36588-155">This could lead to unexpected results from certain operations, such as value comparison and the [Mod Operator](../../../visual-basic/language-reference/operators/mod-operator.md).</span></span> <span data-ttu-id="36588-156">詳細については、「[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36588-156">For more information, see [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>

## <a name="comparing-strings"></a><span data-ttu-id="36588-157">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="36588-157">Comparing Strings</span></span>
 <span data-ttu-id="36588-158">文字列を比較すると、文字列式はアルファベット順の並べ替え順に基づいて評価されます。これは、`Option Compare` の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="36588-158">When you compare strings, the string expressions are evaluated based on their alphabetical sort order, which depends on the `Option Compare` setting.</span></span>

 <span data-ttu-id="36588-159">`Option Compare Binary` は、文字の内部バイナリ表現から派生した並べ替え順に基づいて文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="36588-159">`Option Compare Binary` bases string comparisons on a sort order derived from the internal binary representations of the characters.</span></span> <span data-ttu-id="36588-160">並べ替え順序は、コードページによって決まります。</span><span class="sxs-lookup"><span data-stu-id="36588-160">The sort order is determined by the code page.</span></span> <span data-ttu-id="36588-161">次の例は、一般的なバイナリ並べ替え順序を示しています。</span><span class="sxs-lookup"><span data-stu-id="36588-161">The following example shows a typical binary sort order.</span></span>

 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

 <span data-ttu-id="36588-162">`Option Compare Text` は、アプリケーションのロケールによって決定される、大文字と小文字を区別しないテキストの並べ替え順に基づいて文字列を比較します。</span><span class="sxs-lookup"><span data-stu-id="36588-162">`Option Compare Text` bases string comparisons on a case-insensitive, textual sort order determined by your application's locale.</span></span> <span data-ttu-id="36588-163">前の例で `Option Compare Text` を設定して文字を並べ替えると、次のテキストの並べ替え順序が適用されます。</span><span class="sxs-lookup"><span data-stu-id="36588-163">When you set `Option Compare Text` and sort the characters in the preceding example, the following text sort order applies:</span></span>

 `(A=a) < (À= à) < (B=b) < (E=e) < (Ê= ê) < (Ø = ø) < (Z=z)`

### <a name="locale-dependence"></a><span data-ttu-id="36588-164">ロケールの依存関係</span><span class="sxs-lookup"><span data-stu-id="36588-164">Locale Dependence</span></span>
 <span data-ttu-id="36588-165">`Option Compare Text`を設定すると、文字列比較の結果は、アプリケーションが実行されているロケールによって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="36588-165">When you set `Option Compare Text`, the result of a string comparison can depend on the locale in which the application is running.</span></span> <span data-ttu-id="36588-166">2文字は、1つのロケールでは等しいものの、別のロケールでは比較されない場合があります。</span><span class="sxs-lookup"><span data-stu-id="36588-166">Two characters might compare as equal in one locale but not in another.</span></span> <span data-ttu-id="36588-167">ログオン試行を受け入れるかどうかなど、重要な決定を行うために文字列比較を使用している場合は、ロケールの区別に関する警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36588-167">If you are using a string comparison to make important decisions, such as whether to accept an attempt to log on, you should be alert to locale sensitivity.</span></span> <span data-ttu-id="36588-168">ロケールを考慮して、`Option Compare Binary` を設定するか、<xref:Microsoft.VisualBasic.Strings.StrComp%2A>を呼び出すことを検討してください。</span><span class="sxs-lookup"><span data-stu-id="36588-168">Consider either setting `Option Compare Binary` or calling the <xref:Microsoft.VisualBasic.Strings.StrComp%2A>, which takes the locale into account.</span></span>

## <a name="typeless-programming-with-relational-comparison-operators"></a><span data-ttu-id="36588-169">関係比較演算子を使用したタイプレスプログラミング</span><span class="sxs-lookup"><span data-stu-id="36588-169">Typeless Programming with Relational Comparison Operators</span></span>
 <span data-ttu-id="36588-170">`Object` 式での関係比較演算子の使用は、`Option Strict On`では許可されていません。</span><span class="sxs-lookup"><span data-stu-id="36588-170">The use of relational comparison operators with `Object` expressions is not allowed under `Option Strict On`.</span></span> <span data-ttu-id="36588-171">`Option Strict` が `Off`、`expression1` または `expression2` が `Object` 式の場合、実行時の型によって比較方法が決まります。</span><span class="sxs-lookup"><span data-stu-id="36588-171">When `Option Strict` is `Off`, and either `expression1` or `expression2` is an `Object` expression, the run-time types determine how they are compared.</span></span> <span data-ttu-id="36588-172">次の表に、オペランドのランタイム型に応じて、式と比較した結果を示します。</span><span class="sxs-lookup"><span data-stu-id="36588-172">The following table shows how the expressions are compared and the result from the comparison, depending on the runtime type of the operands.</span></span>

|<span data-ttu-id="36588-173">オペランドがの場合</span><span class="sxs-lookup"><span data-stu-id="36588-173">If operands are</span></span>|<span data-ttu-id="36588-174">比較</span><span class="sxs-lookup"><span data-stu-id="36588-174">Comparison is</span></span>|
|---------------------|-------------------|
|<span data-ttu-id="36588-175">両方の `String`</span><span class="sxs-lookup"><span data-stu-id="36588-175">Both `String`</span></span>|<span data-ttu-id="36588-176">文字列の並べ替え特性に基づいて並べ替えの比較を行います。</span><span class="sxs-lookup"><span data-stu-id="36588-176">Sort comparison based on string sorting characteristics.</span></span>|
|<span data-ttu-id="36588-177">両方の数値</span><span class="sxs-lookup"><span data-stu-id="36588-177">Both numeric</span></span>|<span data-ttu-id="36588-178">`Double`に変換されたオブジェクト。数値比較。</span><span class="sxs-lookup"><span data-stu-id="36588-178">Objects converted to `Double`, numeric comparison.</span></span>|
|<span data-ttu-id="36588-179">1つの数値と1つの `String`</span><span class="sxs-lookup"><span data-stu-id="36588-179">One numeric and one `String`</span></span>|<span data-ttu-id="36588-180">`String` は `Double` に変換され、数値比較が実行されます。</span><span class="sxs-lookup"><span data-stu-id="36588-180">The `String` is converted to a `Double` and numeric comparison is performed.</span></span> <span data-ttu-id="36588-181">`String` を `Double`に変換できない場合は、<xref:System.InvalidCastException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="36588-181">If the `String` cannot be converted to `Double`, an <xref:System.InvalidCastException> is thrown.</span></span>|
|<span data-ttu-id="36588-182">またはのいずれかまたは両方が `String` 以外の参照型です</span><span class="sxs-lookup"><span data-stu-id="36588-182">Either or both are reference types other than `String`</span></span>|<span data-ttu-id="36588-183"><xref:System.InvalidCastException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="36588-183">An <xref:System.InvalidCastException> is thrown.</span></span>|

 <span data-ttu-id="36588-184">数値比較では、`Nothing` を0として扱います。</span><span class="sxs-lookup"><span data-stu-id="36588-184">Numeric comparisons treat `Nothing` as 0.</span></span> <span data-ttu-id="36588-185">文字列比較では、`Nothing` を `""` (空の文字列) として扱います。</span><span class="sxs-lookup"><span data-stu-id="36588-185">String comparisons treat `Nothing` as `""` (an empty string).</span></span>

## <a name="overloading"></a><span data-ttu-id="36588-186">オーバーロード</span><span class="sxs-lookup"><span data-stu-id="36588-186">Overloading</span></span>
 <span data-ttu-id="36588-187">関係比較演算子 (`<`。</span><span class="sxs-lookup"><span data-stu-id="36588-187">The relational comparison operators (`<`.</span></span> <span data-ttu-id="36588-188">`<=`、`>`、`>=`、`=`、`<>`) は*オーバーロード*できます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体で動作を再定義できます。</span><span class="sxs-lookup"><span data-stu-id="36588-188">`<=`, `>`, `>=`, `=`, `<>`) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="36588-189">このようなクラスまたは構造体でこれらの演算子のいずれかを使用するコードの場合は、再定義された動作を理解していることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="36588-189">If your code uses any of these operators on such a class or structure, be sure you understand the redefined behavior.</span></span> <span data-ttu-id="36588-190">詳細については、「[演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36588-190">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

 <span data-ttu-id="36588-191">[= 演算子](../../../visual-basic/language-reference/operators/assignment-operator.md)は、代入演算子としてではなく、関係比較演算子としてのみオーバーロードできることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="36588-191">Notice that the [= Operator](../../../visual-basic/language-reference/operators/assignment-operator.md) can be overloaded only as a relational comparison operator, not as an assignment operator.</span></span>

## <a name="example"></a><span data-ttu-id="36588-192">例</span><span class="sxs-lookup"><span data-stu-id="36588-192">Example</span></span>
 <span data-ttu-id="36588-193">次の例では、式を比較するために使用する関係比較演算子のさまざまな用途を示します。</span><span class="sxs-lookup"><span data-stu-id="36588-193">The following example shows various uses of relational comparison operators, which you use to compare expressions.</span></span> <span data-ttu-id="36588-194">関係比較演算子は、記述された式が `True`に評価されるかどうかを表す `Boolean` の結果を返します。</span><span class="sxs-lookup"><span data-stu-id="36588-194">Relational comparison operators return a `Boolean` result that represents whether or not the stated expression evaluates to `True`.</span></span> <span data-ttu-id="36588-195">文字列に `>` 演算子と `<` 演算子を適用すると、文字列の通常のアルファベット順の並べ替え順序を使用して比較が行われます。</span><span class="sxs-lookup"><span data-stu-id="36588-195">When you apply the `>` and `<` operators to strings, the comparison is made using the normal alphabetical sorting order of the strings.</span></span> <span data-ttu-id="36588-196">この順序は、ロケールの設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="36588-196">This order can be dependent on your locale setting.</span></span> <span data-ttu-id="36588-197">並べ替えで大文字と小文字を区別するかどうかは、[オプションの比較](../../../visual-basic/language-reference/statements/option-compare-statement.md)の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="36588-197">Whether the sort is case-sensitive or not depends on the [Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) setting.</span></span>

 [!code-vb[VbVbalrOperators#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#1)]

 <span data-ttu-id="36588-198">前の例では、最初の比較によって `False` が返され、残りの比較では `True`が返されます。</span><span class="sxs-lookup"><span data-stu-id="36588-198">In the preceding example, the first comparison returns `False` and the remaining comparisons return `True`.</span></span>

## <a name="see-also"></a><span data-ttu-id="36588-199">参照</span><span class="sxs-lookup"><span data-stu-id="36588-199">See also</span></span>

- <xref:System.InvalidCastException>
- [<span data-ttu-id="36588-200">= 演算子</span><span class="sxs-lookup"><span data-stu-id="36588-200">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="36588-201">Visual Basic における演算子の優先順位</span><span class="sxs-lookup"><span data-stu-id="36588-201">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="36588-202">機能別の演算子一覧</span><span class="sxs-lookup"><span data-stu-id="36588-202">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="36588-203">トラブルシューティング (データ型)</span><span class="sxs-lookup"><span data-stu-id="36588-203">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="36588-204">Visual Basic の比較演算子</span><span class="sxs-lookup"><span data-stu-id="36588-204">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
