---
title: '方法: PLINQ クエリの順序を制御する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to control ordering
ms.assetid: c67eccc7-004d-4b2f-987e-919cbbd62ef7
ms.openlocfilehash: d38c039fa99433d9476d62c1e96dff7e306fd766
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123123"
---
# <a name="how-to-control-ordering-in-a-plinq-query"></a><span data-ttu-id="7ce35-102">方法: PLINQ クエリの順序を制御する</span><span class="sxs-lookup"><span data-stu-id="7ce35-102">How to: Control Ordering in a PLINQ Query</span></span>
<span data-ttu-id="7ce35-103">以下の例では、<xref:System.Linq.ParallelEnumerable.AsOrdered%2A> 拡張メソッドを使用して PLINQ クエリの順序を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ce35-103">These examples show how to control the ordering in a PLINQ query by using the <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> extension method.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="7ce35-104">これらの例は使用法を示すことを主な目的としており、同等の LINQ to Objects 順次クエリよりも実行速度が速い場合もあれば遅い場合もあります。</span><span class="sxs-lookup"><span data-stu-id="7ce35-104">These examples are primarily intended to demonstrate usage, and may or may not run faster than the equivalent sequential LINQ to Objects queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ce35-105">例</span><span class="sxs-lookup"><span data-stu-id="7ce35-105">Example</span></span>  
 <span data-ttu-id="7ce35-106">次の例では、ソース シーケンスの順序を維持します。</span><span class="sxs-lookup"><span data-stu-id="7ce35-106">The following example preserves the ordering of the source sequence.</span></span> <span data-ttu-id="7ce35-107">この操作が必要になるのは、たとえば、正確な結果を生成するためにクエリ演算子で順序ありのソース シーケンスが求められる場合です。</span><span class="sxs-lookup"><span data-stu-id="7ce35-107">This is sometimes necessary; for example some query operators require an ordered source sequence to produce correct results.</span></span>  
  
 [!code-csharp[PLINQ#12](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#12)]
 [!code-vb[PLINQ#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="7ce35-108">例</span><span class="sxs-lookup"><span data-stu-id="7ce35-108">Example</span></span>  
 <span data-ttu-id="7ce35-109">次の例は、ソース シーケンスで順序付けが求められるクエリ演算子を示しています。</span><span class="sxs-lookup"><span data-stu-id="7ce35-109">The following example shows some query operators whose source sequence is probably expected to be ordered.</span></span> <span data-ttu-id="7ce35-110">これらの演算子は、順序なしのシーケンスで動作しますが、予測できない結果を生成する場合があります。</span><span class="sxs-lookup"><span data-stu-id="7ce35-110">These operators will work on unordered sequences, but they might produce unexpected results.</span></span>  
  
 [!code-csharp[PLINQ#14](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#14)]
 [!code-vb[PLINQ#14](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#14)]  
  
 <span data-ttu-id="7ce35-111">このメソッドを実行するには、[PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md) プロジェクトの PLINQDataSample クラスに貼り付け、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7ce35-111">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ce35-112">例</span><span class="sxs-lookup"><span data-stu-id="7ce35-112">Example</span></span>  
 <span data-ttu-id="7ce35-113">次の例は、クエリの最初の部分で順序を維持した後に、join 句のパフォーマンスを向上させるために順序を削除し、最終的な結果に順序を再適用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7ce35-113">The following example shows how to preserve ordering for the first part of a query, then remove the ordering to increase the performance of a join clause, and then reapply ordering to the final result sequence.</span></span>  
  
 [!code-csharp[PLINQ#15](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#15)]
 [!code-vb[PLINQ#15](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#15)]  
  
 <span data-ttu-id="7ce35-114">このメソッドを実行するには、[PLINQ データのサンプル](../../../docs/standard/parallel-programming/plinq-data-sample.md) プロジェクトの PLINQDataSample クラスに貼り付け、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7ce35-114">To run this method, paste it into the PLINQDataSample class in the [PLINQ Data Sample](../../../docs/standard/parallel-programming/plinq-data-sample.md) project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce35-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ce35-115">See also</span></span>

- <xref:System.Linq.ParallelEnumerable>
- [<span data-ttu-id="7ce35-116">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="7ce35-116">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
