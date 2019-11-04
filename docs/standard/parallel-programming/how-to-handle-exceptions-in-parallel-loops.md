---
title: '方法: 並列ループの例外を処理する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
ms.openlocfilehash: ae2fadd68cb211285e31e4ee990b6fb288056091
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73091552"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a><span data-ttu-id="15bf3-102">方法: 並列ループの例外を処理する</span><span class="sxs-lookup"><span data-stu-id="15bf3-102">How to: Handle Exceptions in Parallel Loops</span></span>
<span data-ttu-id="15bf3-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> および <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> のオーバーロード には、スローされる可能性のある例外を処理する特別な仕組みはありません。</span><span class="sxs-lookup"><span data-stu-id="15bf3-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> overloads do not have any special mechanism to handle exceptions that might be thrown.</span></span> <span data-ttu-id="15bf3-104">この点では、標準の `for` ループおよび `foreach` ループ (Visual Basic では `For` と `For Each`) と似ており、処理されない例外でループはすぐに終了します。</span><span class="sxs-lookup"><span data-stu-id="15bf3-104">In this respect, they resemble regular `for` and `foreach` loops (`For` and `For Each` in Visual Basic); an unhandled exception causes the loop to terminate immediately.</span></span>  
  
 <span data-ttu-id="15bf3-105">独自の例外処理のロジックを並列ループに追加する場合は、同様の例外が複数のスレッドに同時にスローされるケース、および特定のスレッドにスローされる例外が、別のスレッドに別の例外をスローするケースを処理してください。</span><span class="sxs-lookup"><span data-stu-id="15bf3-105">When you add your own exception-handling logic to parallel loops, handle the case in which similar exceptions might be thrown on multiple threads concurrently, and the case in which an exception thrown on one thread causes another exception to be thrown on another thread.</span></span> <span data-ttu-id="15bf3-106"><xref:System.AggregateException?displayProperty=nameWithType>  のループからすべての例外をラップすることで、両方のケースを処理できます。</span><span class="sxs-lookup"><span data-stu-id="15bf3-106">You can handle both cases by wrapping all exceptions from the loop in a <xref:System.AggregateException?displayProperty=nameWithType>.</span></span> <span data-ttu-id="15bf3-107">考えられる方法の 1 つの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="15bf3-107">The following example shows one possible approach.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15bf3-108">[マイ コードのみ] が有効になっている場合、Visual Studio では、例外をスローする行で処理が中断され、"ユーザー コードで処理されない例外" に関するエラー メッセージが表示されることがあります。</span><span class="sxs-lookup"><span data-stu-id="15bf3-108">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="15bf3-109">このエラーは問題にはなりません。</span><span class="sxs-lookup"><span data-stu-id="15bf3-109">This error is benign.</span></span> <span data-ttu-id="15bf3-110">F5 キーを押して、処理が中断された箇所から続行し、以下の例に示す例外処理動作を確認できます。</span><span class="sxs-lookup"><span data-stu-id="15bf3-110">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the example below.</span></span> <span data-ttu-id="15bf3-111">Visual Studio による処理が最初のエラーで中断しないようにするには、 **[ツール] メニューの [オプション]、[デバッグ] 、[全般]** の順にクリックし、[マイ コードのみ] チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="15bf3-111">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15bf3-112">例</span><span class="sxs-lookup"><span data-stu-id="15bf3-112">Example</span></span>  
 <span data-ttu-id="15bf3-113">この例では、すべての例外がキャッチされた後に <xref:System.AggregateException?displayProperty=nameWithType> にラップされ、スローされます。</span><span class="sxs-lookup"><span data-stu-id="15bf3-113">In this example, all exceptions are caught and then wrapped in an <xref:System.AggregateException?displayProperty=nameWithType> which is thrown.</span></span> <span data-ttu-id="15bf3-114">呼び出し元は、どの例外を処理するかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="15bf3-114">The caller can decide which exceptions to handle.</span></span>  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a><span data-ttu-id="15bf3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="15bf3-115">See also</span></span>

- [<span data-ttu-id="15bf3-116">データの並列化</span><span class="sxs-lookup"><span data-stu-id="15bf3-116">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="15bf3-117">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="15bf3-117">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
