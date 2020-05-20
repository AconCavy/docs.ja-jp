---
title: '方法: Parallel.For または ForEach ループを取り消す'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 67f1f91f235cc88deaa97d412f368819ae0a8cda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134242"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a><span data-ttu-id="5418d-102">方法: Parallel.For または ForEach ループを取り消す</span><span class="sxs-lookup"><span data-stu-id="5418d-102">How to: Cancel a Parallel.For or ForEach Loop</span></span>
<span data-ttu-id="5418d-103"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> および <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> メソッドでは、キャンセル トークンを使用した取り消し処理がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="5418d-103">The <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> methods support cancellation through the use of cancellation tokens.</span></span> <span data-ttu-id="5418d-104">一般的な取り消し処理の詳細については、「[キャンセル](../../../docs/standard/threading/cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5418d-104">For more information about cancellation in general, see [Cancellation](../../../docs/standard/threading/cancellation-in-managed-threads.md).</span></span> <span data-ttu-id="5418d-105">並列ループでは、<xref:System.Threading.Tasks.ParallelOptions> パラメーターのメソッドに <xref:System.Threading.CancellationToken> を指定してから、try-catch ブロックで並列呼び出しを囲みます。</span><span class="sxs-lookup"><span data-stu-id="5418d-105">In a parallel loop, you supply the <xref:System.Threading.CancellationToken> to the method in the <xref:System.Threading.Tasks.ParallelOptions> parameter and then enclose the parallel call in a try-catch block.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5418d-106">例</span><span class="sxs-lookup"><span data-stu-id="5418d-106">Example</span></span>  
 <span data-ttu-id="5418d-107">次の例は、<xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> の呼び出しを取り消す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5418d-107">The following example shows how to cancel a call to <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5418d-108"><xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> 呼び出しに同じ方法を適用できます。</span><span class="sxs-lookup"><span data-stu-id="5418d-108">You can apply the same approach to a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> call.</span></span>  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 <span data-ttu-id="5418d-109">取り消しを通知するトークンが <xref:System.Threading.Tasks.ParallelOptions> インスタンスで指定されているのと同じトークンである場合、並列ループは取り消し時に単一の <xref:System.OperationCanceledException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="5418d-109">If the token that signals the cancellation is the same token that is specified in the <xref:System.Threading.Tasks.ParallelOptions> instance, then the parallel loop will throw a single <xref:System.OperationCanceledException> on cancellation.</span></span> <span data-ttu-id="5418d-110">その他のいくつかのトークンによって取り消しが行われた場合、ループは InnerException として <xref:System.OperationCanceledException> と共に <xref:System.AggregateException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="5418d-110">If some other token causes cancellation, the loop will throw an <xref:System.AggregateException> with an <xref:System.OperationCanceledException> as an InnerException.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5418d-111">参照</span><span class="sxs-lookup"><span data-stu-id="5418d-111">See also</span></span>

- [<span data-ttu-id="5418d-112">データの並列化</span><span class="sxs-lookup"><span data-stu-id="5418d-112">Data Parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="5418d-113">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="5418d-113">Lambda Expressions in PLINQ and TPL</span></span>](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
