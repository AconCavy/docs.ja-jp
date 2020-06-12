---
title: ガベージ コレクションの通知
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: 389e851782edb82578c216951be440070b92723c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286003"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="92d25-102">ガベージ コレクションの通知</span><span class="sxs-lookup"><span data-stu-id="92d25-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="92d25-103">共通言語ランタイムによるフル ガベージ コレクション (つまり、ジェネレーション 2 のコレクション) がパフォーマンスに悪影響を及ぼす場合があります。</span><span class="sxs-lookup"><span data-stu-id="92d25-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="92d25-104">これは、特に要求を大量に処理するサーバーで問題となることがあります。この例では、長時間のガベージ コレクションによって、要求のタイムアウトが発生します。重要な期間にフル ガベージ コレクションが発生しないようにするには、フル ガベージ コレクションが近づいていることの通知を受けたら、ワークロードを別のサーバー インスタンスにリダイレクトするアクションを取ります。</span><span class="sxs-lookup"><span data-stu-id="92d25-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="92d25-105">現在のサーバー インスタンスで要求を処理する必要がない場合、自分でコレクションを強制実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="92d25-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="92d25-106">ランタイムがフル ガーベッジ コレクションが近づいていることを検出すると、<xref:System.GC.RegisterForFullGCNotification%2A> メソッドによって通知の発生が登録されます。</span><span class="sxs-lookup"><span data-stu-id="92d25-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="92d25-107">この通知には、フル ガベージ コレクションが近づいている場合と、フル ガベージ コレクションが完了した場合の 2 つがあります。</span><span class="sxs-lookup"><span data-stu-id="92d25-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="92d25-108">通知は、ガベージ コレクションをブロックすることによってのみ発生します。</span><span class="sxs-lookup"><span data-stu-id="92d25-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="92d25-109">[\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) 構成要素が有効になっている場合、バックグラウンドのガベージ コレクションによって通知が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="92d25-109">When the [\<gcConcurrent>](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="92d25-110">通知が発生したことを判断するには、<xref:System.GC.WaitForFullGCApproach%2A> と <xref:System.GC.WaitForFullGCComplete%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="92d25-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="92d25-111">通常、これらのメソッドは、通知の状態を示す <xref:System.GCNotificationStatus> 列挙体を継続的に取得する `while` ループで使用します。</span><span class="sxs-lookup"><span data-stu-id="92d25-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="92d25-112">その値が <xref:System.GCNotificationStatus.Succeeded> の場合、次を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="92d25-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="92d25-113"><xref:System.GC.WaitForFullGCApproach%2A> メソッドで取得した通知を受け、作業負荷をリダイレクトします。ガベージ コレクションを手動で強制的に実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="92d25-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="92d25-114"><xref:System.GC.WaitForFullGCComplete%2A> メソッドで取得した通知を受け、現在のサーバー インスタンスで再度要求を処理できるようにします。</span><span class="sxs-lookup"><span data-stu-id="92d25-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="92d25-115">情報を収集することもできます。</span><span class="sxs-lookup"><span data-stu-id="92d25-115">You can also gather information.</span></span> <span data-ttu-id="92d25-116">たとえば、<xref:System.GC.CollectionCount%2A> メソッドを使用して、コレクションの数を記録することもできます。</span><span class="sxs-lookup"><span data-stu-id="92d25-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="92d25-117"><xref:System.GC.WaitForFullGCApproach%2A> と <xref:System.GC.WaitForFullGCComplete%2A> メソッドは、連携して動作するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="92d25-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="92d25-118">片方のみを使用する場合、結果が不正確になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="92d25-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="92d25-119">フル ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="92d25-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="92d25-120">ランタイムでは、次のいずれかのシナリオに当てはまる場合にフル ガベージ コレクションを実行します。</span><span class="sxs-lookup"><span data-stu-id="92d25-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="92d25-121">十分なメモリがジェネレーション 2 に昇格し、次のジェネレーション 2 のガベージ コレクションが発生する場合。</span><span class="sxs-lookup"><span data-stu-id="92d25-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="92d25-122">十分なメモリが、大きいオブジェクトのヒープに昇格し、次のジェネレーション 2 のガベージ コレクションが発生する場合。</span><span class="sxs-lookup"><span data-stu-id="92d25-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="92d25-123">その他の要因により、ジェネレーション 1 のガベージ コレクションがジェネレーション 2 のガベージ コレクションにエスカレートする場合。</span><span class="sxs-lookup"><span data-stu-id="92d25-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="92d25-124"><xref:System.GC.RegisterForFullGCNotification%2A> メソッドに指定したしきい値は、最初の 2 つのシナリオに該当します。</span><span class="sxs-lookup"><span data-stu-id="92d25-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="92d25-125">ただし、最初のシナリオでは、以下の 2 つの理由から、指定したしきい値に比例したタイミングで常に通知を受け取るとは限りません。</span><span class="sxs-lookup"><span data-stu-id="92d25-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="92d25-126">ランタイムは、パフォーマンス上の理由から、小さなオブジェクトの割り当てをチェックしません。</span><span class="sxs-lookup"><span data-stu-id="92d25-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="92d25-127">メモリがジェネレーション 2 に移動されるのは、ジェネレーション 1 のガベージ コレクションが実行された場合だけです。</span><span class="sxs-lookup"><span data-stu-id="92d25-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="92d25-128">3 番目のシナリオによっても、通知がいつあるかが不確実になります。</span><span class="sxs-lookup"><span data-stu-id="92d25-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="92d25-129">保証されるわけではないものの、この間要求をリダイレクトしたり、都合の良いときに自分でガベージ コレクションを強制的に実行したりして、タイミングの悪いフル ガベージ コレクションの影響を緩和することは有効な方法です。</span><span class="sxs-lookup"><span data-stu-id="92d25-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="92d25-130">通知しきい値パラメーター</span><span class="sxs-lookup"><span data-stu-id="92d25-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="92d25-131"><xref:System.GC.RegisterForFullGCNotification%2A> メソッドには、ジェネレーション 2 のオブジェクトと大きなオブジェクトのヒープのしきい値を指定するパラメーターが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="92d25-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="92d25-132">これらの値を超えると、ガベージ コレクションの通知が発行されます。</span><span class="sxs-lookup"><span data-stu-id="92d25-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="92d25-133">次の表で、これらのパラメーターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="92d25-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="92d25-134">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92d25-134">Parameter</span></span>|<span data-ttu-id="92d25-135">説明</span><span class="sxs-lookup"><span data-stu-id="92d25-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="92d25-136">ジェネレーション 2 に昇格したオブジェクト数に基づいて通知を発行するタイミングを指定する、1 ～ 99 の数値。</span><span class="sxs-lookup"><span data-stu-id="92d25-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="92d25-137">大きなオブジェクトのヒープに割り当てられたオブジェクト数に基づいて通知を発行するタイミングを指定する、1 ～ 99 の数値。</span><span class="sxs-lookup"><span data-stu-id="92d25-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="92d25-138">指定した値が高すぎる場合、通知を受け取る可能性は高くなりますが、ランタイムでコレクションが発生するまでに、長い時間がかかりります。</span><span class="sxs-lookup"><span data-stu-id="92d25-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="92d25-139">コレクションを自分で強制実行する場合、ランタイムによってコレクションが解放されるときよりも、より多くのオブジェクトを回収できます。</span><span class="sxs-lookup"><span data-stu-id="92d25-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="92d25-140">指定した値が小さすぎる場合、通知を受け取るのに十分な時間がない前に、ランタイムによってコレクションが実行されるおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="92d25-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92d25-141">例</span><span class="sxs-lookup"><span data-stu-id="92d25-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="92d25-142">説明</span><span class="sxs-lookup"><span data-stu-id="92d25-142">Description</span></span>  
 <span data-ttu-id="92d25-143">次の例では、サーバーのグループが受信した Web 要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="92d25-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="92d25-144">要求を処理するワークロードのシミュレートのため、バイト配列が <xref:System.Collections.Generic.List%601> コレクションに追加されています。</span><span class="sxs-lookup"><span data-stu-id="92d25-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="92d25-145">各サーバーはガベージ コレクションの通知を登録し、`WaitForFullGCProc`ユーザー メソッドでスレッドを開始して、<xref:System.GC.WaitForFullGCApproach%2A> メソッドと <xref:System.GC.WaitForFullGCComplete%2A> メソッドで返される <xref:System.GCNotificationStatus> 列挙型を継続的に監視します。</span><span class="sxs-lookup"><span data-stu-id="92d25-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="92d25-146">通知が発生すると、<xref:System.GC.WaitForFullGCApproach%2A> および <xref:System.GC.WaitForFullGCComplete%2A> メソッドによって、それぞれのイベント処理ユーザー メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="92d25-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="92d25-147">このメソッドはユーザー メソッド `RedirectRequests`を呼び出し、要求をキューに格納するサーバーに対して、このサーバーへの要求の送信を一時停止するよう指示します。</span><span class="sxs-lookup"><span data-stu-id="92d25-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="92d25-148">これは、これ以上オブジェクトが割り当てられないように、クラスレベルの変数 `bAllocate` を `false` に設定することによってシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="92d25-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="92d25-149">次に、`FinishExistingRequests` ユーザー メソッドが呼び出され、保留中のサーバー要求の処理が完了します。</span><span class="sxs-lookup"><span data-stu-id="92d25-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="92d25-150">これは、<xref:System.Collections.Generic.List%601> コレクションをクリアすることによってシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="92d25-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="92d25-151">最後に、作業負荷が軽いため、ガベージ コレクションが強制的に実行されます。</span><span class="sxs-lookup"><span data-stu-id="92d25-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="92d25-152">サーバーがフル ガベージ コレクションの影響を受ける可能性が低くなったため、ユーザー メソッド `AcceptRequests` を呼び出し、要求の受付を再開します。</span><span class="sxs-lookup"><span data-stu-id="92d25-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="92d25-153">このアクションは、オブジェクトが <xref:System.Collections.Generic.List%601> コレクションに追加開始されるよう `bAllocate` 変数を `true` に設定することによってシミュレートできます。</span><span class="sxs-lookup"><span data-stu-id="92d25-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="92d25-154">次のコードには、この例の `Main` メソッドを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="92d25-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="92d25-155">次のコードは、ユーザー メソッド `WaitForFullGCProc` のコードであり、ガベージ コレクションの通知を継続的にチェックする while ループが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92d25-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="92d25-156">次のコードには、次から呼び出される `OnFullGCApproachNotify` メソッドを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="92d25-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="92d25-157">`WaitForFullGCProc` メソッド</span><span class="sxs-lookup"><span data-stu-id="92d25-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="92d25-158">次のコードには、次から呼び出される `OnFullGCApproachComplete` メソッドを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="92d25-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="92d25-159">`WaitForFullGCProc` メソッド</span><span class="sxs-lookup"><span data-stu-id="92d25-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="92d25-160">次のコードには、`OnFullGCApproachNotify` および `OnFullGCCompleteNotify` メソッドから呼び出されるユーザー メソッドを含んでいます。</span><span class="sxs-lookup"><span data-stu-id="92d25-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="92d25-161">このユーザー メソッドは、要求のリダイレクト、既存の要求の終了、フル ガベージ コレクションの実行後の要求の受け付け再開を実行します。</span><span class="sxs-lookup"><span data-stu-id="92d25-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="92d25-162">コード全体のサンプルは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="92d25-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="92d25-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="92d25-163">See also</span></span>

- [<span data-ttu-id="92d25-164">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="92d25-164">Garbage Collection</span></span>](index.md)
