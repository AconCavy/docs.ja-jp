---
title: = 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: ad74e3ebc947af4f36022be838b69df6ce24997a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608276"
---
# <a name="-operator-visual-basic"></a>= 演算子 (Visual Basic)
変数またはプロパティに値を割り当てます。  
  
## <a name="syntax"></a>構文  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>指定項目  
 `variableorproperty`  
 任意の書き込み可能な変数または任意のプロパティ。  
  
 `value`  
 任意のリテラル、定数、または式。  
  
## <a name="remarks"></a>Remarks  
 等号の左側にある要素 (`=`) は、単純なスカラー変数、プロパティ、または配列の要素。 変数またはプロパティにすることはできません[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)します。 `=`演算子は、変数に、右側の値またはプロパティの左側に代入します。  
  
> [!NOTE]
>  `=`演算子、比較演算子としても使用します。 詳細については、次を参照してください。[比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)します。  
  
## <a name="overloading"></a>オーバーロード  
 `=`関係比較演算子としてのみ、代入演算子としてではなく、演算子がオーバー ロードできます。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、代入演算子を示します。 右側の値は、左側の変数に割り当てられます。  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>関連項目

- [& = 演算子](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= 演算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= 演算子](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= 演算子](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
