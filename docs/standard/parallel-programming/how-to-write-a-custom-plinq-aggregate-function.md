---
title: '方法: カスタムの PLINQ 集約関数を記述する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
ms.openlocfilehash: 8168c89a6edecd5f7e33a710c9a89c92a6f82005
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588230"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a><span data-ttu-id="d87ac-102">方法: カスタムの PLINQ 集約関数を記述する</span><span class="sxs-lookup"><span data-stu-id="d87ac-102">How to: Write a Custom PLINQ Aggregate Function</span></span>
<span data-ttu-id="d87ac-103">この例は、<xref:System.Linq.ParallelEnumerable.Aggregate%2A> メソッドを使用して、カスタム集計関数をソース シーケンスに適用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d87ac-103">This example shows how to use the <xref:System.Linq.ParallelEnumerable.Aggregate%2A> method to apply a custom aggregation function to a source sequence.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d87ac-104">この例は、使用方法を示すことを意図したものであるため、同等の順次的な LINQ to Objects クエリほど高速ではない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d87ac-104">This example is intended to demonstrate usage, and might not run faster than the equivalent sequential LINQ to Objects query.</span></span> <span data-ttu-id="d87ac-105">高速化の詳細については、「[PLINQ での高速化について](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d87ac-105">For more information about speedup, see [Understanding Speedup in PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d87ac-106">例</span><span class="sxs-lookup"><span data-stu-id="d87ac-106">Example</span></span>  
 <span data-ttu-id="d87ac-107">次の例では、整数シーケンスの標準偏差を計算します。</span><span class="sxs-lookup"><span data-stu-id="d87ac-107">The following example calculates the standard deviation of a sequence of integers.</span></span>  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 <span data-ttu-id="d87ac-108">この例では、PLINQ に固有の Aggregate 標準クエリ演算子のオーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="d87ac-108">This example uses an overload of the Aggregate standard query operator that is unique to PLINQ.</span></span> <span data-ttu-id="d87ac-109">このオーバーロードでは、3 番目の入力パラメーターとして、追加の <xref:System.Func%603?displayProperty=nameWithType> を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="d87ac-109">This overload takes an extra <xref:System.Func%603?displayProperty=nameWithType> as the third input parameter.</span></span> <span data-ttu-id="d87ac-110">このデリゲートは、集計結果で最終計算を実行する前に、すべてのスレッドからの結果を結合します。</span><span class="sxs-lookup"><span data-stu-id="d87ac-110">This delegate combines the results from all threads before it performs the final calculation on the aggregated results.</span></span> <span data-ttu-id="d87ac-111">この例では、すべてのスレッドからの合計をまとめます。</span><span class="sxs-lookup"><span data-stu-id="d87ac-111">In this example we add together the sums from all the threads.</span></span>  
  
 <span data-ttu-id="d87ac-112">ラムダ式の本体が単一の式で構成されている場合、<xref:System.Func%602?displayProperty=nameWithType> デリゲートの戻り値は式の値になることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d87ac-112">Note that when a lambda expression body consists of a single expression, the return value of the <xref:System.Func%602?displayProperty=nameWithType> delegate is the value of the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d87ac-113">参照</span><span class="sxs-lookup"><span data-stu-id="d87ac-113">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="d87ac-114">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="d87ac-114">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
