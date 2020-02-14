---
title: contextSwitchDeadlock MDA
ms.date: 03/30/2017
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
ms.openlocfilehash: e3fc4a2cb35cdcc713ba0ef362071083af08a27b
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217553"
---
# <a name="contextswitchdeadlock-mda"></a><span data-ttu-id="a4b44-102">contextSwitchDeadlock MDA</span><span class="sxs-lookup"><span data-stu-id="a4b44-102">contextSwitchDeadlock MDA</span></span>

<span data-ttu-id="a4b44-103">`contextSwitchDeadlock` マネージド デバッグ アシスタント (MDA) は、COM コンテキストの遷移の試行中にデッドロックが検出されるとアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="a4b44-103">The `contextSwitchDeadlock` managed debugging assistant (MDA) is activated when a deadlock is detected during an attempted COM context transition.</span></span>

## <a name="symptoms"></a><span data-ttu-id="a4b44-104">現象</span><span class="sxs-lookup"><span data-stu-id="a4b44-104">Symptoms</span></span>

<span data-ttu-id="a4b44-105">最も一般的な症状は、マネージド コードから実行されたアンマネージド COM コンポーネントの呼び出しから戻らないことです。</span><span class="sxs-lookup"><span data-stu-id="a4b44-105">The most common symptom is that a call on an unmanaged COM component from managed code does not return.</span></span>  <span data-ttu-id="a4b44-106">別の症状として、メモリの使用量が時間と共に増加する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a4b44-106">Another symptom is memory usage increasing over time.</span></span>

## <a name="cause"></a><span data-ttu-id="a4b44-107">原因</span><span class="sxs-lookup"><span data-stu-id="a4b44-107">Cause</span></span>

<span data-ttu-id="a4b44-108">最も考えられる原因として、シングルスレッド アパートメント (STA) スレッドがメッセージ ポンプを行っていないことがあります。</span><span class="sxs-lookup"><span data-stu-id="a4b44-108">The most probable cause is that a single-threaded apartment (STA) thread is not pumping messages.</span></span> <span data-ttu-id="a4b44-109">STA スレッドが、メッセージ ポンプを行わずに待機しているか、または時間のかかる操作を実行していて、メッセージ キューのポンプを許可していません。</span><span class="sxs-lookup"><span data-stu-id="a4b44-109">The STA thread is either waiting without pumping messages or is performing lengthy operations and is not allowing the message queue to pump.</span></span>

<span data-ttu-id="a4b44-110">メモリ使用量が時間の経過と共に増加する症状は、ファイナライザー スレッドがアンマネージ COM コンポーネント上の `Release` を呼び出そうとして、そのコンポーネントが戻らない場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="a4b44-110">Memory usage increasing over time is caused by the finalizer thread attempting to call `Release` on an unmanaged COM component and that component is not returning.</span></span>  <span data-ttu-id="a4b44-111">このため、ファイナライザーは他のオブジェクトを再利用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="a4b44-111">This prevents the finalizer from reclaiming other objects.</span></span>

<span data-ttu-id="a4b44-112">既定では、Visual Basic コンソール アプリケーションのメイン スレッドのスレッド処理モデルは STA です。</span><span class="sxs-lookup"><span data-stu-id="a4b44-112">By default, the threading model for the main thread of Visual Basic console applications is STA.</span></span> <span data-ttu-id="a4b44-113">STA スレッドが共通言語ランタイムまたはサードパーティ コントロールを通じて COM 相互運用性を直接または間接的に使用する場合、この MDA がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="a4b44-113">This MDA is activated if an STA thread uses COM interoperability either directly or indirectly through the common language runtime or a third-party control.</span></span>  <span data-ttu-id="a4b44-114">Visual Basic コンソール アプリケーションでこの MDA がアクティブ化されるのを防ぐには、メイン メソッドに <xref:System.MTAThreadAttribute> 属性を適用するか、またはメッセージをポンプするようにアプリケーションを変更します。</span><span class="sxs-lookup"><span data-stu-id="a4b44-114">To avoid activating this MDA in a Visual Basic console application, apply the <xref:System.MTAThreadAttribute> attribute to the main method or modify the application to pump messages.</span></span>

<span data-ttu-id="a4b44-115">次のすべての条件が満たされる場合、この MDA が誤ってアクティブ化される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4b44-115">It is possible for this MDA to be falsely activated when all of the following conditions are met:</span></span>

- <span data-ttu-id="a4b44-116">アプリケーションがライブラリを通じて直接または間接的に STA スレッドから COM コンポーネントを作成する。</span><span class="sxs-lookup"><span data-stu-id="a4b44-116">An application creates COM components from STA threads either directly or indirectly through libraries.</span></span>

- <span data-ttu-id="a4b44-117">デバッガーでアプリケーションが中断され、ユーザーがアプリケーションを続行したか、またはステップ操作を実行した。</span><span class="sxs-lookup"><span data-stu-id="a4b44-117">The application was stopped in the debugger and the user either continued the application or performed a step operation.</span></span>

- <span data-ttu-id="a4b44-118">アンマネージ デバッグが有効になっていない。</span><span class="sxs-lookup"><span data-stu-id="a4b44-118">Unmanaged debugging is not enabled.</span></span>

<span data-ttu-id="a4b44-119">MDA が誤ってアクティブ化されたかどうかを判断するには、すべてのブレークポイントを無効にし、アプリケーションを再び実行して、中断なしで実行させます。</span><span class="sxs-lookup"><span data-stu-id="a4b44-119">To determine if the MDA is being falsely activated, disable all breakpoints, restart the application, and allow it to run without stopping.</span></span> <span data-ttu-id="a4b44-120">MDA がアクティブ化されない場合は、最初のアクティブ化は誤りだった可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4b44-120">If the MDA is not activated, it is likely the initial activation was false.</span></span> <span data-ttu-id="a4b44-121">その場合は、MDA を無効にして、デバッグ セッションとの干渉を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="a4b44-121">In this case, disable the MDA to avoid interference with the debugging session.</span></span>

> [!NOTE]
> <span data-ttu-id="a4b44-122">この MDA は、Visual Studio の既定のセットに含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4b44-122">This MDA is in the default set for Visual Studio.</span></span> <span data-ttu-id="a4b44-123">Mda を無効にする方法の詳細については、「[マネージデバッグアシスタントによるエラーの診断](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4b44-123">For information about how to disable MDAs, see [Diagnosing Errors with Managed Debugging Assistants](diagnosing-errors-with-managed-debugging-assistants.md#enable-and-disable-mdas).</span></span>

## <a name="resolution"></a><span data-ttu-id="a4b44-124">解決策</span><span class="sxs-lookup"><span data-stu-id="a4b44-124">Resolution</span></span>

<span data-ttu-id="a4b44-125">STA メッセージ ポンプに関する COM 規則に従います。</span><span class="sxs-lookup"><span data-stu-id="a4b44-125">Follow COM rules regarding STA message pumping.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="a4b44-126">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="a4b44-126">Effect on the Runtime</span></span>

<span data-ttu-id="a4b44-127">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="a4b44-127">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="a4b44-128">COM コンテキストに関するデータを報告するだけです。</span><span class="sxs-lookup"><span data-stu-id="a4b44-128">It only reports data about COM contexts.</span></span>

## <a name="output"></a><span data-ttu-id="a4b44-129">出力</span><span class="sxs-lookup"><span data-stu-id="a4b44-129">Output</span></span>

<span data-ttu-id="a4b44-130">現在のコンテキストおよびターゲット コンテキストを説明するメッセージです。</span><span class="sxs-lookup"><span data-stu-id="a4b44-130">A message describing the current context and the target context.</span></span>

## <a name="configuration"></a><span data-ttu-id="a4b44-131">構成</span><span class="sxs-lookup"><span data-stu-id="a4b44-131">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <contextSwitchDeadlock />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a><span data-ttu-id="a4b44-132">参照</span><span class="sxs-lookup"><span data-stu-id="a4b44-132">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="a4b44-133">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="a4b44-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="a4b44-134">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="a4b44-134">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
