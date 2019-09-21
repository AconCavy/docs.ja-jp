---
title: '方法: 式ツリーの実行 (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 135c295070ea591f3b494734f9d236e36b9c3c5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916502"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>方法: 式ツリーの実行 (Visual Basic)
このトピックでは、式ツリーを実行する方法について説明します。 式ツリーを実行すると値が返される場合がありますが、メソッドの呼び出しなどの処理が実行されるだけの場合もあります。  
  
 実行できるのは、ラムダ式を表す式ツリーのみです。 ラムダ式を表す式ツリーの型は、<xref:System.Linq.Expressions.LambdaExpression> または <xref:System.Linq.Expressions.Expression%601> です。 このような式ツリーを実行するには、<xref:System.Linq.Expressions.LambdaExpression.Compile%2A> メソッドを呼び出して実行可能なデリゲートを作成した後、そのデリゲートを呼び出します。  
  
> [!NOTE]
> デリゲートの型が不明な場合、つまり、ラムダ式が <xref:System.Linq.Expressions.LambdaExpression> 型であり <xref:System.Linq.Expressions.Expression%601> 型ではない場合には、デリゲートを直接呼び出さずに、デリゲートに対して <xref:System.Delegate.DynamicInvoke%2A> メソッドを呼び出す必要があります。  
  
 式ツリーがラムダ式を表さない場合、<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> メソッドを呼び出すことで、元の式ツリーを本体に含む新しいラムダ式を作成できます。 その後、このセクションの説明のとおりにラムダ式を実行できます。  
  
## <a name="example"></a>例  
 次のコード例は、ラムダ式を作成して実行することで数値の累乗を表す式ツリーの実行方法を示しています。 このコードを実行すると、累乗された数値を表す結果が表示されます。  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- System.Linq.Expressions 名前空間をインクルードします。  
  
## <a name="see-also"></a>関連項目

- [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [方法: 式ツリーの変更 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
