---
title: try-catch - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
ms.openlocfilehash: 3d4315a09869b77b4ae8cbb43646f9a96280b678
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173472"
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="d027c-102">try-catch (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="d027c-102">try-catch (C# Reference)</span></span>

<span data-ttu-id="d027c-103">try-catch ステートメントは、`try` ブロックと、それに続く 1 つ以上の `catch` 句で構成されます。この句にはさまざまな例外のハンドラーを指定します。</span><span class="sxs-lookup"><span data-stu-id="d027c-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>

<span data-ttu-id="d027c-104">例外がスローされると、共通言語ランタイム (CLR) によって、この例外を処理する `catch` ステートメントが検索されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-104">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="d027c-105">現在実行されているメソッドにそのような `catch` ブロックが含まれていない場合、CLR は現在のメソッドを呼び出したメソッドを検索し、呼び出し履歴の上位を検索していきます。</span><span class="sxs-lookup"><span data-stu-id="d027c-105">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="d027c-106">`catch` ブロックが見つからない場合、CLR はハンドルされていない例外のメッセージをユーザーに表示し、プログラムの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="d027c-106">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>

<span data-ttu-id="d027c-107">`try` ブロックには、例外を発生させる可能性がある保護されたコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d027c-107">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="d027c-108">このブロックは、例外がスローされるか、ブロックが正常に終了するまで実行されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-108">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="d027c-109">たとえば、次の例では `null` オブジェクトをキャストしようとすると、<xref:System.NullReferenceException> 例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="d027c-109">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>

```csharp
object o2 = null;
try
{
    int i2 = (int)o2;   // Error
}
```

<span data-ttu-id="d027c-110">`catch` 句は、引数なしで使用してすべての種類の例外をキャッチできますが、この使用方法はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="d027c-110">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="d027c-111">通常は、回復方法が判明している例外のみキャッチします。</span><span class="sxs-lookup"><span data-stu-id="d027c-111">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="d027c-112">したがって、<xref:System.Exception?displayProperty=nameWithType> から派生したオブジェクト引数を必ず指定します。以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d027c-112">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>

```csharp
catch (InvalidCastException e)
{
}
```

<span data-ttu-id="d027c-113">同一の try-catch ステートメントで、特定の `catch` 句を複数回使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="d027c-113">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="d027c-114">この場合、`catch` 句は順序どおりにチェックされるため、`catch` 句の順序が重要になります。</span><span class="sxs-lookup"><span data-stu-id="d027c-114">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="d027c-115">例外は、特殊性の高い順にキャッチしてください。</span><span class="sxs-lookup"><span data-stu-id="d027c-115">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="d027c-116">後のブロックに到達しないような順序で catch ブロックを並べた場合、コンパイラでエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d027c-116">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>

<span data-ttu-id="d027c-117">処理対象の例外をフィルター処理する方法の 1 つに、`catch` 引数の使用があります。</span><span class="sxs-lookup"><span data-stu-id="d027c-117">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="d027c-118">また、例外フィルターを使用して例外を確認し、それを処理するかどうかを決定することもできます。</span><span class="sxs-lookup"><span data-stu-id="d027c-118">You can also use an exception filter that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="d027c-119">例外フィルターが false を返す場合、ハンドラーの検索が続行されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-119">If the exception filter returns false, then the search for a handler continues.</span></span>

```csharp
catch (ArgumentException e) when (e.ParamName == "…")
{
}
```

<span data-ttu-id="d027c-120">スタックはフィルターの影響を受けないため、キャッチと再スロー (以下で説明します) には例外フィルターが適しています。</span><span class="sxs-lookup"><span data-stu-id="d027c-120">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="d027c-121">後のハンドラーでスタックをダンプすると、再スローされた最後の場所だけではなく、例外が最初に発生した場所がわかります。</span><span class="sxs-lookup"><span data-stu-id="d027c-121">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="d027c-122">例外のフィルター式の一般的な用途の 1 つにログの記録があります。</span><span class="sxs-lookup"><span data-stu-id="d027c-122">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="d027c-123">常に false を返しログも出力するフィルターを作成すれば、処理や再スローの必要なしにそのままの状態で例外をログに記録することができます。</span><span class="sxs-lookup"><span data-stu-id="d027c-123">You can create a filter that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>

<span data-ttu-id="d027c-124">[ ステートメントでキャッチされた例外を再びスローするには、](throw.md) ブロックで `catch`throw`catch` ステートメントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d027c-124">A [throw](throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="d027c-125">次の例では、<xref:System.IO.IOException> 例外からソース情報を抽出した後、親メソッドに例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="d027c-125">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>

```csharp
catch (FileNotFoundException e)
{
    // FileNotFoundExceptions are handled here.
}
catch (IOException e)
{
    // Extract some information from this exception, and then
    // throw it to the parent method.
    if (e.Source != null)
        Console.WriteLine("IOException source: {0}", e.Source);
    throw;
}
```

<span data-ttu-id="d027c-126">例外をキャッチして、別の例外をスローできます。</span><span class="sxs-lookup"><span data-stu-id="d027c-126">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="d027c-127">これを行うには、次の例に示すように、キャッチする例外を内部例外として指定します。</span><span class="sxs-lookup"><span data-stu-id="d027c-127">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    // Perform some action here, and then throw a new exception.
    throw new YourCustomException("Put your error message here.", e);
}
```

<span data-ttu-id="d027c-128">次の例に示すように、指定した条件が true の場合に例外を再スローすることもできます。</span><span class="sxs-lookup"><span data-stu-id="d027c-128">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>

```csharp
catch (InvalidCastException e)
{
    if (e.Data == null)
    {
        throw;
    }
    else
    {
        // Take some action.
    }
}
```

> [!NOTE]
> <span data-ttu-id="d027c-129">また、例外フィルターを使用すると、多くの場合、よりクリーンな方法で同様の結果を得ることができます (このドキュメントで前述したような、スタックの変更もありません)。</span><span class="sxs-lookup"><span data-stu-id="d027c-129">It is also possible to use an exception filter to get a similar result in an often cleaner fashion (as well as not modifying the stack, as explained earlier in this document).</span></span> <span data-ttu-id="d027c-130">次の例では、呼び出し元に対して前の例と同様の動作をします。</span><span class="sxs-lookup"><span data-stu-id="d027c-130">The following example has a similar behavior for callers as the previous example.</span></span> <span data-ttu-id="d027c-131">この関数は、`InvalidCastException` が `e.Data` の場合に、`null` を呼び出し元にスローして戻します。</span><span class="sxs-lookup"><span data-stu-id="d027c-131">The function throws the `InvalidCastException` back to the caller when `e.Data` is `null`.</span></span>
>
> ```csharp
> catch (InvalidCastException e) when (e.Data != null)
> {
>     // Take some action.
> }
> ```

<span data-ttu-id="d027c-132">`try` ブロック内では、そのブロックで宣言されている変数のみを初期化します。</span><span class="sxs-lookup"><span data-stu-id="d027c-132">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="d027c-133">そうしないと、ブロックの実行が完了する前に例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d027c-133">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="d027c-134">たとえば、次のコードでは、変数 `n` が `try` ブロック内で初期化されています。</span><span class="sxs-lookup"><span data-stu-id="d027c-134">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="d027c-135">この変数を `try` ブロックの外側にある `Write(n)` ステートメントで使おうとすると、コンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="d027c-135">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>

```csharp
static void Main()
{
    int n;
    try
    {
        // Do not initialize this variable here.
        n = 123;
    }
    catch
    {
    }
    // Error: Use of unassigned local variable 'n'.
    Console.Write(n);
}
```

<span data-ttu-id="d027c-136">catch の詳細については、「[try-catch-finally](try-catch-finally.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d027c-136">For more information about catch, see [try-catch-finally](try-catch-finally.md).</span></span>

## <a name="exceptions-in-async-methods"></a><span data-ttu-id="d027c-137">非同期メソッドの例外</span><span class="sxs-lookup"><span data-stu-id="d027c-137">Exceptions in async methods</span></span>

<span data-ttu-id="d027c-138">非同期メソッドは [async](async.md) 修飾子でマークされ、通常は 1 つ以上の await 式またはステートメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="d027c-138">An async method is marked  by an  [async](async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="d027c-139">await 式では、[await](../operators/await.md) 演算子が <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-139">An await expression applies the [await](../operators/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="d027c-140">コントロールが非同期メソッドの `await` に到達すると、メソッドの進行状況は、待機中のタスクが完了するまで中断されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-140">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="d027c-141">タスクが完了すると、メソッドで実行を再開できます。</span><span class="sxs-lookup"><span data-stu-id="d027c-141">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="d027c-142">詳細については、「[Async および Await を使用した非同期プログラミング](../../programming-guide/concepts/async/index.md)」と「[非同期プログラムにおける制御フロー](../../programming-guide/concepts/async/control-flow-in-async-programs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d027c-142">For more information, see [Asynchronous Programming with async and await](../../programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>

<span data-ttu-id="d027c-143">`await` が適用される完了したタスクは、タスクを返すメソッドでハンドルされない例外が発生したことが原因で、違反状態になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="d027c-143">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="d027c-144">タスクを待機すると例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d027c-144">Awaiting the task throws an exception.</span></span> <span data-ttu-id="d027c-145">タスクを返す非同期処理が取り消された場合に、取り消された状態でタスクを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="d027c-145">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="d027c-146">取り消されたタスクを待機すると、`OperationCanceledException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d027c-146">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="d027c-147">非同期処理を取り消す方法の詳細については、「[非同期アプリケーションの微調整](../../programming-guide/concepts/async/fine-tuning-your-async-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d027c-147">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="d027c-148">例外をキャッチするには、`try` ブロックでタスクを待機し、関連付けられている `catch` ブロックで例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="d027c-148">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="d027c-149">例については、[async メソッドの例](#async-method-example)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d027c-149">For an example, see the [Async method example](#async-method-example) section.</span></span>

<span data-ttu-id="d027c-150">待機中の非同期メソッドで複数の例外が発生したことが原因で、タスクが違反状態になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d027c-150">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="d027c-151">たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> の呼び出しの結果になることがあります。</span><span class="sxs-lookup"><span data-stu-id="d027c-151">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d027c-152">このようなタスクを待機すると、1 つの例外のみがキャッチされます。どの例外がキャッチされるかは予測できません。</span><span class="sxs-lookup"><span data-stu-id="d027c-152">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="d027c-153">例については、[Task.WhenAll の例](#taskwhenall-example)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d027c-153">For an example, see the [Task.WhenAll example](#taskwhenall-example) section.</span></span>

## <a name="example"></a><span data-ttu-id="d027c-154">例</span><span class="sxs-lookup"><span data-stu-id="d027c-154">Example</span></span>

<span data-ttu-id="d027c-155">例外が発生する可能性がある `try` メソッドへの呼び出しを含む `ProcessString` ブロックの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d027c-155">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="d027c-156">`catch` 句には、メッセージを画面に表示するだけの例外ハンドラーがあります。</span><span class="sxs-lookup"><span data-stu-id="d027c-156">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="d027c-157">`throw` ステートメントが `MyMethod` の内側から呼び出されると、システムによって `catch` ステートメントが検索され、メッセージ `Exception caught` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-157">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>

[!code-csharp[csrefKeywordsExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#2)]

## <a name="two-catch-blocks-example"></a><span data-ttu-id="d027c-158">2 つの catch ブロックの例</span><span class="sxs-lookup"><span data-stu-id="d027c-158">Two catch blocks example</span></span>

<span data-ttu-id="d027c-159">次の例では、2 種類の catch ブロックが使用され、特殊性が最も高い最初の例外がキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="d027c-159">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>

<span data-ttu-id="d027c-160">特殊性が最も低い例外をキャッチするには、`ProcessString` の throw ステートメントを `throw new Exception()` と置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="d027c-160">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>

<span data-ttu-id="d027c-161">この例で特殊性が最も低い catch ブロックを最初に配置すると、"`A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`" というエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-161">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>

[!code-csharp[csrefKeywordsExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#3)]

## <a name="async-method-example"></a><span data-ttu-id="d027c-162">非同期メソッドの例</span><span class="sxs-lookup"><span data-stu-id="d027c-162">Async method example</span></span>

<span data-ttu-id="d027c-163">次の例では、非同期メソッドの例外処理を示します。</span><span class="sxs-lookup"><span data-stu-id="d027c-163">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="d027c-164">非同期タスクからスローされる例外をキャッチするには、`await` ブロックに `try` 式を配置し、`catch` ブロックで例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="d027c-164">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>

<span data-ttu-id="d027c-165">例外処理を示すために、この例の `throw new Exception` 行のコメントを解除します。</span><span class="sxs-lookup"><span data-stu-id="d027c-165">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="d027c-166">タスクの `IsFaulted` プロパティが `True` に設定され、タスクの `Exception.InnerException` プロパティが例外に設定され、例外が `catch` ブロックでキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="d027c-166">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>

<span data-ttu-id="d027c-167">`throw new OperationCanceledException` 行のコメントを解除して、非同期処理を取り消したときに何が起こるかを示します。</span><span class="sxs-lookup"><span data-stu-id="d027c-167">Uncomment the `throw new OperationCanceledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="d027c-168">タスクの `IsCanceled` プロパティが `true` に設定され、例外が `catch` ブロックでキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="d027c-168">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="d027c-169">この例に該当しない一部の条件では、タスクの `IsFaulted` プロパティが `true` に設定され、`IsCanceled` が `false` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d027c-169">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>

[!code-csharp[csAsyncExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#2)]  

## <a name="taskwhenall-example"></a><span data-ttu-id="d027c-170">Task.WhenAll の例</span><span class="sxs-lookup"><span data-stu-id="d027c-170">Task.WhenAll example</span></span>

<span data-ttu-id="d027c-171">次の例では、複数のタスクで複数の例外が発生する可能性がある例外処理について説明します。</span><span class="sxs-lookup"><span data-stu-id="d027c-171">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="d027c-172">`try` ブロックは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> の呼び出しで返されるタスクを待機します。</span><span class="sxs-lookup"><span data-stu-id="d027c-172">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d027c-173">WhenAll が適用される 3 つのタスクが完了すると、このタスクは完了します。</span><span class="sxs-lookup"><span data-stu-id="d027c-173">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>

<span data-ttu-id="d027c-174">3 つのタスクでそれぞれ例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="d027c-174">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="d027c-175">`catch` ブロックは例外を反復処理します。この例外は、`Exception.InnerExceptions` で返されたタスクの <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> プロパティで見つかります。</span><span class="sxs-lookup"><span data-stu-id="d027c-175">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>

[!code-csharp[csAsyncExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncexceptions/cs/class1.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="d027c-176">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="d027c-176">C# language specification</span></span>

<span data-ttu-id="d027c-177">詳細については、「[C# 言語仕様](~/_csharplang/spec/statements.md#the-try-statement)」の「[try ステートメント](~/_csharplang/spec/introduction.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d027c-177">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d027c-178">参照</span><span class="sxs-lookup"><span data-stu-id="d027c-178">See also</span></span>

- [<span data-ttu-id="d027c-179">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="d027c-179">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d027c-180">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="d027c-180">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d027c-181">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="d027c-181">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d027c-182">try、throw、catch ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="d027c-182">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="d027c-183">throw</span><span class="sxs-lookup"><span data-stu-id="d027c-183">throw</span></span>](throw.md)
- [<span data-ttu-id="d027c-184">try-finally</span><span class="sxs-lookup"><span data-stu-id="d027c-184">try-finally</span></span>](try-finally.md)
- [<span data-ttu-id="d027c-185">方法: 例外を明示的にスローする</span><span class="sxs-lookup"><span data-stu-id="d027c-185">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
