---
title: '方法: SpinWait を使用して 2 フェーズ待機操作を実装する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137948"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="4ef2c-102">方法: SpinWait を使用して 2 フェーズ待機操作を実装する</span><span class="sxs-lookup"><span data-stu-id="4ef2c-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="4ef2c-103">次の例では、<xref:System.Threading.SpinWait?displayProperty=nameWithType> オブジェクトを使用して、2 フェーズ待機操作を実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="4ef2c-104">最初のフェーズでは、同期オブジェクトである `Latch` は、ロックが使用可能になったかどうかを確認しながら、数回のサイクルの間スピンします。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="4ef2c-105">2 番目のフェーズでは、ロックが使用可能になった場合に、`Wait` メソッドは待機を実行するために <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> を使用せずに制御を返します (それ以外の場合、`Wait` は待機を実行します)。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ef2c-106">例</span><span class="sxs-lookup"><span data-stu-id="4ef2c-106">Example</span></span>  
 <span data-ttu-id="4ef2c-107">この例では、ラッチ同期プリミティブの非常に基本的な実装を示します。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="4ef2c-108">待機時間が非常に短くなると予測される場合は、このデータ構造を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="4ef2c-109">この例は、デモンストレーション目的のみで提供されます。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="4ef2c-110">プログラムでラッチ型機能が必要な場合は、<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="4ef2c-111">ラッチでは <xref:System.Threading.SpinWait> オブジェクトを使用して、次の `SpinOnce` の呼び出しで <xref:System.Threading.SpinWait> がスレッドのタイム スライスを生成するまでの間のみ、スピンが発生するようにします。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="4ef2c-112">その時点で、<xref:System.Threading.ManualResetEvent> で <xref:System.Threading.WaitHandle.WaitOne%2A> を呼び出し、残りのタイムアウト値を渡すことで、ラッチにより独自のコンテキスト切り替えが発生します。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="4ef2c-113">ログ出力には、<xref:System.Threading.ManualResetEvent> を使用せずにロックを取得することで、ラッチでパフォーマンスを向上させることができた頻度が示されます。</span><span class="sxs-lookup"><span data-stu-id="4ef2c-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef2c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ef2c-114">See also</span></span>

- [<span data-ttu-id="4ef2c-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="4ef2c-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)
- [<span data-ttu-id="4ef2c-116">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="4ef2c-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
