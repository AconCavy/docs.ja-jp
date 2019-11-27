---
title: 演算子および式
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: fa410a739be2da8802e76a35068448263ddec1fc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343608"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="d30f3-102">Visual Basic の演算子および式</span><span class="sxs-lookup"><span data-stu-id="d30f3-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="d30f3-103">*演算子*は、値が格納されている 1 つ以上のコード要素に対して演算を実行するコード要素です。</span><span class="sxs-lookup"><span data-stu-id="d30f3-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="d30f3-104">値要素は、変数、定数、リテラル、プロパティ、`Function` プロシージャおよび `Operator` プロシージャからの戻り値、式などです。</span><span class="sxs-lookup"><span data-stu-id="d30f3-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="d30f3-105">*式*は、演算子で結合され、新しい値を生成する一連の値要素です。</span><span class="sxs-lookup"><span data-stu-id="d30f3-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="d30f3-106">演算子は、値要素に対して、計算、比較、またはその他の演算を実行します。</span><span class="sxs-lookup"><span data-stu-id="d30f3-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="d30f3-107">演算子の種類</span><span class="sxs-lookup"><span data-stu-id="d30f3-107">Types of Operators</span></span>  
 <span data-ttu-id="d30f3-108">Visual Basic には、次の種類の演算子があります。</span><span class="sxs-lookup"><span data-stu-id="d30f3-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="d30f3-109">[算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)は、数値に対して一般的な計算を実行します (ビット パターンのシフトも含まれます)。</span><span class="sxs-lookup"><span data-stu-id="d30f3-109">[Arithmetic Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="d30f3-110">[比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)は、2 つの式を比較し、比較の結果を表す `Boolean` 値を返します。</span><span class="sxs-lookup"><span data-stu-id="d30f3-110">[Comparison Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="d30f3-111">[連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)は、複数の文字列を結合して 1 つの文字列にします。</span><span class="sxs-lookup"><span data-stu-id="d30f3-111">[Concatenation Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="d30f3-112">[Visual Basic の論理演算子およびビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)は、`Boolean` 値または数値を組み合わせて、同じデータ型の結果を値として返します。</span><span class="sxs-lookup"><span data-stu-id="d30f3-112">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="d30f3-113">演算子で結合される値要素は、演算子の*オペランド*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="d30f3-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="d30f3-114">演算子は値要素と結合されると*式*になります。ただし、代入演算子は例外で、これはステートメントになります。</span><span class="sxs-lookup"><span data-stu-id="d30f3-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="d30f3-115">詳細については、「[ステートメント](../../../../visual-basic/programming-guide/language-features/statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d30f3-115">For more information, see [Statements](../../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="d30f3-116">式の評価</span><span class="sxs-lookup"><span data-stu-id="d30f3-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="d30f3-117">式の最終的な結果は、通常、`Boolean`、`String`、または数値型などの一般的なデータ型で表されます。</span><span class="sxs-lookup"><span data-stu-id="d30f3-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="d30f3-118">次に式の例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="d30f3-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="d30f3-119">次の例のように、1 つの式またはステートメントで複数の演算子を使うこともできます。</span><span class="sxs-lookup"><span data-stu-id="d30f3-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="d30f3-120">前の例では、Visual Basic 代入演算子 (`=`) の右側にある式の演算を実行し、結果の値を左側の変数 `x` に代入します。</span><span class="sxs-lookup"><span data-stu-id="d30f3-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="d30f3-121">1 つの式で使用できる演算子の数には、事実上制限はありません。ただし、正しい結果を得るには、[Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d30f3-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="d30f3-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d30f3-122">See also</span></span>

- [<span data-ttu-id="d30f3-123">演算子</span><span class="sxs-lookup"><span data-stu-id="d30f3-123">Operators</span></span>](../../../../visual-basic/language-reference/operators/index.md)
- [<span data-ttu-id="d30f3-124">演算子の効率のよい組み合わせ</span><span class="sxs-lookup"><span data-stu-id="d30f3-124">Efficient Combination of Operators</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [<span data-ttu-id="d30f3-125">ステートメント</span><span class="sxs-lookup"><span data-stu-id="d30f3-125">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
