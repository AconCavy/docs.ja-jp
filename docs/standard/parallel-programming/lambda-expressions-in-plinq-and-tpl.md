---
title: PLINQ および TPL のラムダ式
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
ms.openlocfilehash: d1b716e977702d03db176da70be00a1e5c789a4b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129024"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a><span data-ttu-id="e7d13-102">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="e7d13-102">Lambda Expressions in PLINQ and TPL</span></span>

<span data-ttu-id="e7d13-103">タスク並列ライブラリ (TPL) には、入力パラメーターとしてデリゲートの <xref:System.Func%601?displayProperty=nameWithType> または <xref:System.Action?displayProperty=nameWithType> ファミリのいずれかを受け取る多くのメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="e7d13-103">The Task Parallel Library (TPL) contains many methods that take one of the <xref:System.Func%601?displayProperty=nameWithType> or <xref:System.Action?displayProperty=nameWithType> family of delegates as input parameters.</span></span> <span data-ttu-id="e7d13-104">これらのデリゲートを使用して、並列ループ、タスク、またはクエリにカスタムのプログラム ロジックを渡します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-104">You use these delegates to pass in your custom program logic to the parallel loop, task or query.</span></span> <span data-ttu-id="e7d13-105">TPL と PLINQ のコード例では、ラムダ式を使用して、インライン コード ブロックとしてこれらのデリゲートのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-105">The code examples for TPL as well as PLINQ use lambda expressions to create instances of those delegates as inline code blocks.</span></span> <span data-ttu-id="e7d13-106">このトピックでは、Func および Action について簡単に紹介し、タスク並列ライブラリと PLINQ でラムダ式を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-106">This topic provides a brief introduction to Func and Action and shows you how to use lambda expressions in the Task Parallel Library and PLINQ.</span></span>

> [!NOTE]
> <span data-ttu-id="e7d13-107">一般的なデリゲートの詳細については、「[デリゲート](../../csharp/programming-guide/delegates/index.md)」と「[デリゲート](../../visual-basic/programming-guide/language-features/delegates/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7d13-107">For more information about delegates in general, see [Delegates](../../csharp/programming-guide/delegates/index.md) and [Delegates](../../visual-basic/programming-guide/language-features/delegates/index.md).</span></span> <span data-ttu-id="e7d13-108">C# と Visual Basic のラムダ式の詳細については、それぞれ「[ラムダ式](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」と「[ラムダ式](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7d13-108">For more information about lambda expressions in C# and Visual Basic, see [Lambda Expressions](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) and [Lambda Expressions](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="func-delegate"></a><span data-ttu-id="e7d13-109">Func デリゲート</span><span class="sxs-lookup"><span data-stu-id="e7d13-109">Func Delegate</span></span>

<span data-ttu-id="e7d13-110">`Func` デリゲートは、値を返すメソッドをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-110">A `Func` delegate encapsulates a method that returns a value.</span></span> <span data-ttu-id="e7d13-111">Func シグネチャでは、末尾または最も右の型パラメーターが常に戻り値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-111">In a Func signature, the last or rightmost type parameter always specifies the return type.</span></span> <span data-ttu-id="e7d13-112">コンパイラ エラーの一般的な原因の 1 つは、2 つの入力パラメーターを <xref:System.Func%602?displayProperty=nameWithType> に渡そうとしていることです。この型は、実際には 1 つの入力パラメーターのみを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="e7d13-112">One common cause of compiler errors is to attempt to pass in two input parameters to a <xref:System.Func%602?displayProperty=nameWithType>; in fact this type takes only one input parameter.</span></span> <span data-ttu-id="e7d13-113">Framework クラス ライブラリでは、<xref:System.Func%601?displayProperty=nameWithType>、<xref:System.Func%602?displayProperty=nameWithType>、<xref:System.Func%603?displayProperty=nameWithType> から <xref:System.Func%6017?displayProperty=nameWithType> までの 17 バージョンの `Func` を定義します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-113">The Framework Class Library defines 17 versions of `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, and so on up through <xref:System.Func%6017?displayProperty=nameWithType>.</span></span>

## <a name="action-delegate"></a><span data-ttu-id="e7d13-114">Action デリゲート</span><span class="sxs-lookup"><span data-stu-id="e7d13-114">Action Delegate</span></span>

<span data-ttu-id="e7d13-115"><xref:System.Action?displayProperty=nameWithType> デリゲートは、値を返さない、または [void](../../csharp/language-reference/keywords/void.md) を返すメソッド (Visual Basic では Sub) をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-115">A <xref:System.Action?displayProperty=nameWithType> delegate encapsulates a method (Sub in Visual Basic) that does not return a value, or returns [void](../../csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="e7d13-116">Action 型シグネチャでは、型パラメーターは、入力パラメーターのみを表します。</span><span class="sxs-lookup"><span data-stu-id="e7d13-116">In an Action type signature, the type parameters represent only input parameters.</span></span> <span data-ttu-id="e7d13-117">Func のように、Framework クラス ライブラリでは、型パラメーターを持たないバージョンから 16 の型パラメーターを持つバージョンまでの、17 バージョンの Action が定義されています。</span><span class="sxs-lookup"><span data-stu-id="e7d13-117">Like Func, the Framework Class Library defines 17 versions of Action, from a version that has no type parameters up through a version that has 16 type parameters.</span></span>

## <a name="example"></a><span data-ttu-id="e7d13-118">例</span><span class="sxs-lookup"><span data-stu-id="e7d13-118">Example</span></span>

<span data-ttu-id="e7d13-119"><xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> メソッドの次の例は、ラムダ式を使用して、Func および Action の両方のデリゲートを表す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e7d13-119">The following example for the <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> method shows how to express both Func and Action delegates by using lambda expressions.</span></span>

[!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
[!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]

## <a name="see-also"></a><span data-ttu-id="e7d13-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7d13-120">See also</span></span>

- [<span data-ttu-id="e7d13-121">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="e7d13-121">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)
