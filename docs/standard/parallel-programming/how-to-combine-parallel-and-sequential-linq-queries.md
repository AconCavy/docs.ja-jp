---
title: '方法: 並列および順次の LINQ クエリを連結する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel queries, combine parallel and sequential
ms.assetid: 1167cfe6-c8aa-4096-94ba-c66c3a4edf4c
ms.openlocfilehash: 4c04afb23a168a9cff60962bd5a75a65e3ebca4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134195"
---
# <a name="how-to-combine-parallel-and-sequential-linq-queries"></a><span data-ttu-id="64310-102">方法: 並列および順次の LINQ クエリを連結する</span><span class="sxs-lookup"><span data-stu-id="64310-102">How to: Combine Parallel and Sequential LINQ Queries</span></span>
<span data-ttu-id="64310-103">この例では、PLINQ にクエリ内の後続のすべての演算子を順次処理するように指示する <xref:System.Linq.ParallelEnumerable.AsSequential%2A> メソッドの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="64310-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.AsSequential%2A> method to instruct PLINQ to process all subsequent operators in the query sequentially.</span></span> <span data-ttu-id="64310-104">通常、順次処理は並列処理よりも遅いですが、正しい結果を出すためにこれが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="64310-104">Although sequential processing is generally slower than parallel, sometimes it is necessary to produce correct results.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="64310-105">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="64310-105">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="64310-106">高速化の詳細については、「[PLINQ での高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="64310-106">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="64310-107">例</span><span class="sxs-lookup"><span data-stu-id="64310-107">Example</span></span>  
 <span data-ttu-id="64310-108">次の例は、クエリの前の句で確立された順序を保持する <xref:System.Linq.ParallelEnumerable.AsSequential%2A> が必要な 1 つのシナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="64310-108">The following example shows one scenario in which <xref:System.Linq.ParallelEnumerable.AsSequential%2A> is required, namely to preserve the ordering that was established in a previous clause of the query.</span></span>  
  
 [!code-csharp[PLINQ#24](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#24)]
 [!code-vb[PLINQ#24](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#24)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="64310-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="64310-109">Compiling the Code</span></span>  
 <span data-ttu-id="64310-110">このコードをコンパイルして実行するには、これを [PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md) プロジェクトに貼り付けて、`Main` からメソッドを呼び出す行を追加し、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="64310-110">To compile and run this code, paste it into the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project, add a line to call the method from `Main`, and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64310-111">参照</span><span class="sxs-lookup"><span data-stu-id="64310-111">See also</span></span>

- [<span data-ttu-id="64310-112">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="64310-112">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
