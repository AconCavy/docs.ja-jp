---
title: タイマー
description: マルチスレッド環境で使用する .NET タイマーについて説明します。
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.openlocfilehash: d7d1fa13b02fe7425fa9b4cb81ba20297a23fe4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128948"
---
# <a name="timers"></a><span data-ttu-id="b3af9-103">タイマー</span><span class="sxs-lookup"><span data-stu-id="b3af9-103">Timers</span></span>

<span data-ttu-id="b3af9-104">.NET には、マルチスレッド環境で使用するタイマーが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="b3af9-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="b3af9-105"><xref:System.Threading.Timer?displayProperty=nameWithType> は <xref:System.Threading.ThreadPool> スレッドで決まった間隔を空けながら呼び出しメソッドを 1 つ実行します。</span><span class="sxs-lookup"><span data-stu-id="b3af9-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="b3af9-106"><xref:System.Timers.Timer?displayProperty=nameWithType> は既定では、<xref:System.Threading.ThreadPool> スレッドで決まった間隔を空けながらイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="b3af9-107">一部の .NET 実装には追加タイマーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b3af9-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="b3af9-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: 一定の間隔でイベントを発生させる Windows フォーム コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="b3af9-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="b3af9-109">このコンポーネントにはユーザー インターフェイスがなく、シングルスレッド環境で使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="b3af9-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="b3af9-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: 非同期または同期の Web ページのポストバックを一定の間隔で実行する ASP.NET コンポーネント。</span><span class="sxs-lookup"><span data-stu-id="b3af9-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="b3af9-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: 指定の間隔と指定の優先順位で処理される <xref:System.Windows.Threading.Dispatcher> キューに統合されるタイマー。</span><span class="sxs-lookup"><span data-stu-id="b3af9-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="b3af9-112">System.Threading.Timer クラス</span><span class="sxs-lookup"><span data-stu-id="b3af9-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="b3af9-113"><xref:System.Threading.Timer?displayProperty=nameWithType> クラスによって、指定の間隔でデリゲートを連続的に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="b3af9-114">このクラスを使用し、指定の間隔でデリゲートの呼び出しを 1 つスケジュールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="b3af9-115">デリゲートは <xref:System.Threading.ThreadPool> スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="b3af9-116"><xref:System.Threading.Timer?displayProperty=nameWithType> オブジェクトを作成するとき、呼び出しメソッドを定義する <xref:System.Threading.TimerCallback> デリゲート、呼び出しに渡される任意の状態オブジェクト、最初の呼び出しまで遅らせる時間、呼び出し間隔を指定します。</span><span class="sxs-lookup"><span data-stu-id="b3af9-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="b3af9-117">保留中のタイマーを取り消すには、<xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="b3af9-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="b3af9-118">次の例では、1 秒 (1000 ミリ秒) 後に最初の指定デリゲートを呼び出し、その後、2 秒おきに呼び出すタイマーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="b3af9-119">この例の状態オブジェクトは、デリゲートを呼び出す回数を数えるために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="b3af9-120">デリゲートが少なくとも 10 回呼び出されると、タイマーが停止します。</span><span class="sxs-lookup"><span data-stu-id="b3af9-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="b3af9-121">使用例を含む詳細については、「<xref:System.Threading.Timer?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3af9-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="b3af9-122">System.Timers.Timer クラス</span><span class="sxs-lookup"><span data-stu-id="b3af9-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="b3af9-123">マルチスレッド環境で使用できる別のタイマーが <xref:System.Timers.Timer?displayProperty=nameWithType> です。このタイマーは既定で、<xref:System.Threading.ThreadPool> スレッドでイベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="b3af9-124"><xref:System.Timers.Timer?displayProperty=nameWithType> オブジェクトを作成するとき、<xref:System.Timers.Timer.Elapsed> イベントを発生させる間隔を指定できます。</span><span class="sxs-lookup"><span data-stu-id="b3af9-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="b3af9-125"><xref:System.Timers.Timer.Enabled%2A> プロパティを使用し、タイマーが <xref:System.Timers.Timer.Elapsed> イベントを発生させるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b3af9-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="b3af9-126">指定間隔の経過後、1 回だけ <xref:System.Timers.Timer.Elapsed> イベントを発生させる必要がある場合、<xref:System.Timers.Timer.AutoReset%2A> を `false` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b3af9-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="b3af9-127"><xref:System.Timers.Timer.AutoReset%2A> プロパティの既定値は `true` です。<xref:System.Timers.Timer.Elapsed> プロパティで定義される間隔で <xref:System.Timers.Timer.Interval%2A> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="b3af9-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="b3af9-128">使用例を含む詳細については、「<xref:System.Timers.Timer?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3af9-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b3af9-129">参照</span><span class="sxs-lookup"><span data-stu-id="b3af9-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="b3af9-130">スレッド処理オブジェクトと機能</span><span class="sxs-lookup"><span data-stu-id="b3af9-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
