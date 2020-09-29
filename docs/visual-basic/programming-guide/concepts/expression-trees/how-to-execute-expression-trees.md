---
title: '方法: 式ツリーを実行する'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 703a2dc49ba905c81948267f6eec3ca7578fc308
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077333"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="1d1af-102">方法: 式ツリーを実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d1af-102">How to: Execute Expression Trees (Visual Basic)</span></span>

<span data-ttu-id="1d1af-103">このトピックでは、式ツリーを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1d1af-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="1d1af-104">式ツリーを実行すると値が返される場合がありますが、メソッドの呼び出しなどの処理が実行されるだけの場合もあります。</span><span class="sxs-lookup"><span data-stu-id="1d1af-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="1d1af-105">実行できるのは、ラムダ式を表す式ツリーのみです。</span><span class="sxs-lookup"><span data-stu-id="1d1af-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="1d1af-106">ラムダ式を表す式ツリーの型は、<xref:System.Linq.Expressions.LambdaExpression> または <xref:System.Linq.Expressions.Expression%601> です。</span><span class="sxs-lookup"><span data-stu-id="1d1af-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="1d1af-107">このような式ツリーを実行するには、<xref:System.Linq.Expressions.LambdaExpression.Compile%2A> メソッドを呼び出して実行可能なデリゲートを作成した後、そのデリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="1d1af-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1d1af-108">デリゲートの型が不明な場合、つまり、ラムダ式が <xref:System.Linq.Expressions.LambdaExpression> 型であり <xref:System.Linq.Expressions.Expression%601> 型ではない場合には、デリゲートを直接呼び出さずに、デリゲートに対して <xref:System.Delegate.DynamicInvoke%2A> メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="1d1af-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="1d1af-109">式ツリーがラムダ式を表さない場合、<xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> メソッドを呼び出すことで、元の式ツリーを本体に含む新しいラムダ式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="1d1af-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="1d1af-110">その後、このセクションの説明のとおりにラムダ式を実行できます。</span><span class="sxs-lookup"><span data-stu-id="1d1af-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d1af-111">例</span><span class="sxs-lookup"><span data-stu-id="1d1af-111">Example</span></span>  

 <span data-ttu-id="1d1af-112">次のコード例は、ラムダ式を作成して実行することで数値の累乗を表す式ツリーの実行方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="1d1af-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="1d1af-113">このコードを実行すると、累乗された数値を表す結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="1d1af-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compile-the-code"></a><span data-ttu-id="1d1af-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="1d1af-114">Compile the code</span></span>  
  
- <span data-ttu-id="1d1af-115">System.Linq.Expressions 名前空間をインクルードします。</span><span class="sxs-lookup"><span data-stu-id="1d1af-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1af-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d1af-116">See also</span></span>

- [<span data-ttu-id="1d1af-117">式ツリー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d1af-117">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="1d1af-118">方法: 式ツリーを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d1af-118">How to: Modify Expression Trees (Visual Basic)</span></span>](how-to-modify-expression-trees.md)
