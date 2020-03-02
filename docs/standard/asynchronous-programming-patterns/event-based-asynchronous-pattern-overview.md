---
title: イベントベースの非同期パターンの概要
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 792aa8da-918b-458e-b154-9836b97735f3
ms.openlocfilehash: cce01a7c87f6f20b5e6c46881b8c863bb5a72a88
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160068"
---
# <a name="event-based-asynchronous-pattern-overview"></a><span data-ttu-id="f4aff-102">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="f4aff-102">Event-based Asynchronous Pattern Overview</span></span>
<span data-ttu-id="f4aff-103">多数のタスクを同時に実行しながら、ユーザーの操作にも応答するアプリケーションには、通常、複数のスレッドを使用するデザインが必要です。</span><span class="sxs-lookup"><span data-stu-id="f4aff-103">Applications that perform many tasks simultaneously, yet remain responsive to user interaction, often require a design that uses multiple threads.</span></span> <span data-ttu-id="f4aff-104"><xref:System.Threading> 名前空間は、高性能なマルチスレッド アプリケーションを作成するのに必要なすべてのツールを提供します。ただし、これらのツールを効果的に使用するには、マルチスレッド ソフトウェア エンジニアリングの豊富な経験が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4aff-104">The <xref:System.Threading> namespace provides all the tools necessary to create high-performance multithreaded applications, but using these tools effectively requires significant experience with multithreaded software engineering.</span></span> <span data-ttu-id="f4aff-105">比較的単純なマルチスレッド アプリケーションの場合は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントが簡単なソリューションを提供します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-105">For relatively simple multithreaded applications, the <xref:System.ComponentModel.BackgroundWorker> component provides a straightforward solution.</span></span> <span data-ttu-id="f4aff-106">より高度な非同期アプリケーションの場合は、イベント ベースの非同期パターンに準拠したクラスの実装を検討してください。</span><span class="sxs-lookup"><span data-stu-id="f4aff-106">For more sophisticated asynchronous applications, consider implementing a class that adheres to the Event-based Asynchronous Pattern.</span></span>  
  
 <span data-ttu-id="f4aff-107">イベント ベースの非同期パターンを使用すると、マルチスレッド デザイン固有の多くの複雑な問題を気にせずに、マルチスレッド アプリケーションの利点を活用できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-107">The Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span> <span data-ttu-id="f4aff-108">このパターンをサポートするクラスを使用すると、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-108">Using a class that supports this pattern can allow you to:</span></span>  
  
- <span data-ttu-id="f4aff-109">ダウンロードやデータベース操作などの時間がかかるタスクを、アプリケーションを中断せずに、"バックグラウンド" で行うことができます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-109">Perform time-consuming tasks, such as downloads and database operations, "in the background," without interrupting your application.</span></span>  
  
- <span data-ttu-id="f4aff-110">複数の操作を同時に実行し、それぞれの操作が完了するたびに通知を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-110">Execute multiple operations simultaneously, receiving notifications when each completes.</span></span>  
  
- <span data-ttu-id="f4aff-111">アプリケーションを停止 ("ブロック") せずに、リソースが使用可能な状態になるまで待機できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-111">Wait for resources to become available without stopping ("blocking") your application.</span></span>  
  
- <span data-ttu-id="f4aff-112">使い慣れたイベントおよびデリゲートのモデルを使用して、保留中の非同期操作と通信できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-112">Communicate with pending asynchronous operations using the familiar events-and-delegates model.</span></span> <span data-ttu-id="f4aff-113">イベント ハンドラーおよびデリゲートの使い方の詳細については、[イベント](../../../docs/standard/events/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4aff-113">For more information on using event handlers and delegates, see [Events](../../../docs/standard/events/index.md).</span></span>  
  
 <span data-ttu-id="f4aff-114">イベント ベースの非同期パターンをサポートするクラスには、1 つまたは複数の _MethodName_**Async** という名前のメソッドが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-114">A class that supports the Event-based Asynchronous Pattern will have one or more methods named _MethodName_**Async**.</span></span> <span data-ttu-id="f4aff-115">これらのメソッドは、同期バージョンに対応するもので、現在のスレッドで同じ操作を行います。</span><span class="sxs-lookup"><span data-stu-id="f4aff-115">These methods may mirror synchronous versions, which perform the same operation on the current thread.</span></span> <span data-ttu-id="f4aff-116">クラスには、_MethodName_**Completed** イベントや _MethodName_**AsyncCancel** (または単に **CancelAsync**) メソッドが含まれる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-116">The class may also have a _MethodName_**Completed** event and it may have a _MethodName_**AsyncCancel** (or simply **CancelAsync**) method.</span></span>  
  
 <span data-ttu-id="f4aff-117"><xref:System.Windows.Forms.PictureBox> は、イベント ベースの非同期パターンをサポートする一般的なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="f4aff-117"><xref:System.Windows.Forms.PictureBox> is a typical component that supports the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="f4aff-118">イメージを同期的にダウンロードするには、その <xref:System.Windows.Forms.PictureBox.Load%2A>メソッドを呼び出します。ただし、イメージのサイズが大きい場合や、ネットワークの接続速度が遅い場合は、ダウンロード操作が完了して <xref:System.Windows.Forms.PictureBox.Load%2A> の呼び出しが返されるまで、アプリケーションが応答を停止します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-118">You can download an image synchronously by calling its <xref:System.Windows.Forms.PictureBox.Load%2A> method, but if the image is large, or if the network connection is slow, your application will stop responding until the download operation is completed and the call to <xref:System.Windows.Forms.PictureBox.Load%2A> returns.</span></span>  
  
 <span data-ttu-id="f4aff-119">イメージの読み込み中にもアプリケーションを実行し続けるには、<xref:System.Windows.Forms.PictureBox.LoadAsync%2A> メソッドを呼び出して、他のイベントを処理する場合と同様に、<xref:System.Windows.Forms.PictureBox.LoadCompleted> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-119">If you want your application to keep running while the image is loading, you can call the <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> method and handle the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event, just as you would handle any other event.</span></span> <span data-ttu-id="f4aff-120"><xref:System.Windows.Forms.PictureBox.LoadAsync%2A> メソッドを呼び出すと、ダウンロードを別のスレッドで ("バックグラウンド" で) 続行しながら、アプリケーションを実行し続けることができます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-120">When you call the <xref:System.Windows.Forms.PictureBox.LoadAsync%2A> method, your application will continue to run while the download proceeds on a separate thread ("in the background").</span></span> <span data-ttu-id="f4aff-121">イメージの読み込み操作が完了すると、イベント ハンドラーが呼び出されます。イベント ハンドラーは、<xref:System.ComponentModel.AsyncCompletedEventArgs> パラメーターを調べて、ダウンロードが正常に完了したかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-121">Your event handler will be called when the image-loading operation is complete, and your event handler can examine the <xref:System.ComponentModel.AsyncCompletedEventArgs> parameter to determine if the download completed successfully.</span></span>  
  
 <span data-ttu-id="f4aff-122">イベント ベースの非同期パターンでは、非同期操作をキャンセルできる必要があります。<xref:System.Windows.Forms.PictureBox> コントロールでは、その <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> メソッドでこの要件をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f4aff-122">The Event-based Asynchronous Pattern requires that an asynchronous operation can be canceled, and the <xref:System.Windows.Forms.PictureBox> control supports this requirement with its <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> method.</span></span> <span data-ttu-id="f4aff-123"><xref:System.Windows.Forms.PictureBox.CancelAsync%2A> を呼び出すと、保留中のダウンロードを停止する要求が送信されます。タスクがキャンセルされると、<xref:System.Windows.Forms.PictureBox.LoadCompleted> イベントが発生します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-123">Calling <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> submits a request to stop the pending download, and when the task is canceled, the <xref:System.Windows.Forms.PictureBox.LoadCompleted> event is raised.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="f4aff-124"><xref:System.Windows.Forms.PictureBox.CancelAsync%2A> 要求が作成されると同時に、ダウンロードが終了する可能性もあります。このような場合、<xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> にはキャンセルの要求が反映されません。</span><span class="sxs-lookup"><span data-stu-id="f4aff-124">It is possible that the download will finish just as the <xref:System.Windows.Forms.PictureBox.CancelAsync%2A> request is made, so <xref:System.ComponentModel.AsyncCompletedEventArgs.Cancelled%2A> may not reflect the request to cancel.</span></span> <span data-ttu-id="f4aff-125">これは*競合状態*と呼ばれる、マルチスレッド プログラミングの一般的な問題です。</span><span class="sxs-lookup"><span data-stu-id="f4aff-125">This is called a *race condition* and is a common issue in multithreaded programming.</span></span> <span data-ttu-id="f4aff-126">マルチスレッド プログラミングの問題の詳細については、「[マネージド スレッド処理のベスト プラクティス](../../../docs/standard/threading/managed-threading-best-practices.md)」 (管理されたスレッドのベスト プラクティス) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4aff-126">For more information on issues in multithreaded programming, see [Managed Threading Best Practices](../../../docs/standard/threading/managed-threading-best-practices.md).</span></span>  
  
## <a name="characteristics-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="f4aff-127">イベント ベースの非同期パターンの特性</span><span class="sxs-lookup"><span data-stu-id="f4aff-127">Characteristics of the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="f4aff-128">イベント ベースの非同期パターンには、特定のクラスでサポートされている操作の複雑さに応じて、複数の形式があります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-128">The Event-based Asynchronous Pattern may take several forms, depending on the complexity of the operations supported by a particular class.</span></span> <span data-ttu-id="f4aff-129">最もシンプルなクラスには、単一の _MethodName_**Async** メソッドと、このメソッドに対応する _MethodName_**Completed** イベントが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-129">The simplest classes may have a single _MethodName_**Async** method and a corresponding _MethodName_**Completed** event.</span></span> <span data-ttu-id="f4aff-130">より複雑なクラスには、複数の _MethodName_**Async** メソッドと、それぞれに対応する _MethodName_**Completed** イベント、およびこれらのメソッドの同期バージョンが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-130">More complex classes may have several _MethodName_**Async** methods, each with a corresponding _MethodName_**Completed** event, as well as synchronous versions of these methods.</span></span> <span data-ttu-id="f4aff-131">クラスでは、各非同期メソッドの、キャンセル、進行状況のレポート、およびインクリメンタル結果をオプションでサポートできます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-131">Classes can optionally support cancellation, progress reporting, and incremental results for each asynchronous method.</span></span>  
  
 <span data-ttu-id="f4aff-132">また、非同期メソッドでは複数の保留中の呼び出し (複数の同時呼び出し) をサポートして、他の保留中の操作が完了するまで、コードを何度も呼び出せるようにできます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-132">An asynchronous method may also support multiple pending calls (multiple concurrent invocations), allowing your code to call it any number of times before it completes other pending operations.</span></span> <span data-ttu-id="f4aff-133">このような状況を適切に処理するには、アプリケーションで各操作の完了を追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-133">Correctly handling this situation may require your application to track the completion of each operation.</span></span>  
  
### <a name="examples-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="f4aff-134">イベント ベースの非同期パターンの例</span><span class="sxs-lookup"><span data-stu-id="f4aff-134">Examples of the Event-based Asynchronous Pattern</span></span>  
 <span data-ttu-id="f4aff-135"><xref:System.Media.SoundPlayer> および <xref:System.Windows.Forms.PictureBox> コンポーネントは、イベント ベースの非同期パターンのシンプルな実装です。</span><span class="sxs-lookup"><span data-stu-id="f4aff-135">The <xref:System.Media.SoundPlayer> and <xref:System.Windows.Forms.PictureBox> components represent simple implementations of the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="f4aff-136"><xref:System.Net.WebClient> および <xref:System.ComponentModel.BackgroundWorker> コンポーネントは、イベント ベースの非同期パターンのより複雑な実装です。</span><span class="sxs-lookup"><span data-stu-id="f4aff-136">The <xref:System.Net.WebClient> and <xref:System.ComponentModel.BackgroundWorker> components represent more complex implementations of the Event-based Asynchronous Pattern.</span></span>  
  
 <span data-ttu-id="f4aff-137">パターンに準拠したクラス宣言の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-137">Below is an example class declaration that conforms to the pattern:</span></span>  
  
```vb  
Public Class AsyncExample  
    ' Synchronous methods.  
    Public Function Method1(ByVal param As String) As Integer
    Public Sub Method2(ByVal param As Double)
  
    ' Asynchronous methods.  
    Overloads Public Sub Method1Async(ByVal param As String)
    Overloads Public Sub Method1Async(ByVal param As String, ByVal userState As Object)
    Public Event Method1Completed As Method1CompletedEventHandler  
  
    Overloads Public Sub Method2Async(ByVal param As Double)
    Overloads Public Sub Method2Async(ByVal param As Double, ByVal userState As Object)
    Public Event Method2Completed As Method2CompletedEventHandler  
  
    Public Sub CancelAsync(ByVal userState As Object)
  
    Public ReadOnly Property IsBusy () As Boolean  
  
    ' Class implementation not shown.  
End Class  
```  
  
```csharp  
public class AsyncExample  
{  
    // Synchronous methods.  
    public int Method1(string param);  
    public void Method2(double param);  
  
    // Asynchronous methods.  
    public void Method1Async(string param);  
    public void Method1Async(string param, object userState);  
    public event Method1CompletedEventHandler Method1Completed;  
  
    public void Method2Async(double param);  
    public void Method2Async(double param, object userState);  
    public event Method2CompletedEventHandler Method2Completed;  
  
    public void CancelAsync(object userState);  
  
    public bool IsBusy { get; }  
  
    // Class implementation not shown.  
}  
```  
  
 <span data-ttu-id="f4aff-138">架空の `AsyncExample` クラスには 2 つのメソッドがあり、いずれも同期および非同期の呼び出しをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="f4aff-138">The fictitious `AsyncExample` class has two methods, both of which support synchronous and asynchronous invocations.</span></span> <span data-ttu-id="f4aff-139">同期のオーバーロードは、呼び出し元スレッドで操作を呼び出しおよび実行する任意のメソッドと同様に動作します。操作に時間がかかる場合は、呼び出しから戻るまでにかなりの遅延が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-139">The synchronous overloads behave like any method call and execute the operation on the calling thread; if the operation is time-consuming, there may be a noticeable delay before the call returns.</span></span> <span data-ttu-id="f4aff-140">非同期のオーバーロードは、別のスレッドで操作を開始して即座に戻ります。これにより、操作を "バックグラウンド" で実行しながら、呼び出し元スレッドを続行できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-140">The asynchronous overloads will start the operation on another thread and then return immediately, allowing the calling thread to continue while the operation executes "in the background."</span></span>  
  
### <a name="asynchronous-method-overloads"></a><span data-ttu-id="f4aff-141">非同期メソッドのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="f4aff-141">Asynchronous Method Overloads</span></span>  
 <span data-ttu-id="f4aff-142">非同期操作には、基本的に単一呼び出しと複数呼び出しの 2 つのオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-142">There are potentially two overloads for the asynchronous operations: single-invocation and multiple-invocation.</span></span> <span data-ttu-id="f4aff-143">これら 2 つの形式はそのメソッド シグネチャで区別できます。複数呼び出しの形式には、`userState` という名前の追加のパラメーターがあります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-143">You can distinguish these two forms by their method signatures: the multiple-invocation form has an extra parameter called `userState`.</span></span> <span data-ttu-id="f4aff-144">この形式を使用すると、保留中の非同期操作が完了するのを待たずに、コードで `Method1Async(string param, object userState)` を複数回呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-144">This form makes it possible for your code to call `Method1Async(string param, object userState)` multiple times without waiting for any pending asynchronous operations to finish.</span></span> <span data-ttu-id="f4aff-145">一方、直前の呼び出しが完了する前に `Method1Async(string param)` を呼び出そうとすると、メソッドにより <xref:System.InvalidOperationException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-145">If, on the other hand, you try to call `Method1Async(string param)` before a previous invocation has completed, the method raises an <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="f4aff-146">複数呼び出しのオーバーロードの `userState` パラメーターにより、非同期操作を区別できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-146">The `userState` parameter for the multiple-invocation overloads allows you to distinguish among asynchronous operations.</span></span> <span data-ttu-id="f4aff-147">`Method1Async(string param, object userState)` の各呼び出しに一意な値 (GUID やハッシュ コードなど) を指定すると、各操作が完了したときに、イベント ハンドラーは、どの操作のインスタンスが完了イベントを発生させたのかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-147">You provide a unique value (for example, a GUID or hash code) for each call to `Method1Async(string param, object userState)`, and when each operation is completed, your event handler can determine which instance of the operation raised the completion event.</span></span>  
  
### <a name="tracking-pending-operations"></a><span data-ttu-id="f4aff-148">保留中の操作の追跡</span><span class="sxs-lookup"><span data-stu-id="f4aff-148">Tracking Pending Operations</span></span>  
 <span data-ttu-id="f4aff-149">複数呼び出しのオーバーロードを使用する場合は、保留中のタスクの `userState` オブジェクト (タスク ID) を追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-149">If you use the multiple-invocation overloads, your code will need to keep track of the `userState` objects (task IDs) for pending tasks.</span></span> <span data-ttu-id="f4aff-150">`Method1Async(string param, object userState)` の呼び出しごとに、通常は新しい一意な `userState` オブジェクトを生成し、それをコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-150">For each call to `Method1Async(string param, object userState)`, you will typically generate a new, unique `userState` object and add it to a collection.</span></span> <span data-ttu-id="f4aff-151">この `userState` オブジェクトに対応するタスクが完了イベントを発生させると、完了メソッドの実装は <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> を調べて、それをコレクションから削除します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-151">When the task corresponding to this `userState` object raises the completion event, your completion method implementation will examine <xref:System.ComponentModel.AsyncCompletedEventArgs.UserState%2A?displayProperty=nameWithType> and remove it from your collection.</span></span> <span data-ttu-id="f4aff-152">このように使用すると、`userState` パラメーターはタスク ID の役割を果たします。</span><span class="sxs-lookup"><span data-stu-id="f4aff-152">Used this way, the `userState` parameter takes the role of a task ID.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f4aff-153">複数呼び出しのオーバーロードの呼び出しでは、`userState` に一意な値を指定するように注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4aff-153">You must be careful to provide a unique value for `userState` in your calls to multiple-invocation overloads.</span></span> <span data-ttu-id="f4aff-154">タスク ID が一意でないと、非同期クラスが <xref:System.ArgumentException> をスローします。</span><span class="sxs-lookup"><span data-stu-id="f4aff-154">Non-unique task IDs will cause the asynchronous class throw an <xref:System.ArgumentException>.</span></span>  
  
### <a name="canceling-pending-operations"></a><span data-ttu-id="f4aff-155">保留中の操作のキャンセル</span><span class="sxs-lookup"><span data-stu-id="f4aff-155">Canceling Pending Operations</span></span>  
 <span data-ttu-id="f4aff-156">非同期操作を完了前にいつでもキャンセルできることは重要です。</span><span class="sxs-lookup"><span data-stu-id="f4aff-156">It is important to be able to cancel asynchronous operations at any time before their completion.</span></span> <span data-ttu-id="f4aff-157">イベント ベースの非同期パターンを実装するクラスには、`CancelAsync` メソッド (非同期メソッドが 1 つだけの場合) または _MethodName_**AsyncCancel** メソッド (複数の非同期メソッドがある場合) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-157">Classes that implement the Event-based Asynchronous Pattern will have a `CancelAsync` method (if there is only one asynchronous method) or a _MethodName_**AsyncCancel** method (if there are multiple asynchronous methods).</span></span>  
  
 <span data-ttu-id="f4aff-158">複数呼び出しを可能にするメソッドは `userState` パラメーターを受け取ります。これは、各タスクの有効期間を追跡するのに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-158">Methods that allow multiple invocations take a `userState` parameter, which can be used to track the lifetime of each task.</span></span> <span data-ttu-id="f4aff-159">`CancelAsync` は `userState` パラメーターを受け取ります。このパラメーターにより、特定の保留中のタスクを取り消すことができます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-159">`CancelAsync` takes a `userState` parameter, which allows you to cancel particular pending tasks.</span></span>  
  
 <span data-ttu-id="f4aff-160">保留中の操作を一度に 1 つだけサポートする `Method1Async(string param)` のようなメソッドは、キャンセルできません。</span><span class="sxs-lookup"><span data-stu-id="f4aff-160">Methods that support only a single pending operation at a time, like `Method1Async(string param)`, are not cancelable.</span></span>  
  
### <a name="receiving-progress-updates-and-incremental-results"></a><span data-ttu-id="f4aff-161">進行状況の更新およびインクリメンタル結果の受信</span><span class="sxs-lookup"><span data-stu-id="f4aff-161">Receiving Progress Updates and Incremental Results</span></span>  
 <span data-ttu-id="f4aff-162">イベント ベースの非同期パターンに準拠するクラスは、進行状況およびインクリメンタル結果を追跡するイベントをオプションで提供します。</span><span class="sxs-lookup"><span data-stu-id="f4aff-162">A class that adheres to the Event-based Asynchronous Pattern may optionally provide an event for tracking progress and incremental results.</span></span> <span data-ttu-id="f4aff-163">通常、これは `ProgressChanged` または _MethodName_**ProgressChanged** という名前で、その対応するイベント ハンドラーは <xref:System.ComponentModel.ProgressChangedEventArgs> パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f4aff-163">This will typically be named `ProgressChanged` or _MethodName_**ProgressChanged**, and its corresponding event handler will take a <xref:System.ComponentModel.ProgressChangedEventArgs> parameter.</span></span>  
  
 <span data-ttu-id="f4aff-164">`ProgressChanged` イベントのイベント ハンドラーは、<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> プロパティを調べて、非同期タスクの何パーセントが完了したのかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-164">The event handler for the `ProgressChanged` event can examine the <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A?displayProperty=nameWithType> property to determine what percentage of an asynchronous task has been completed.</span></span> <span data-ttu-id="f4aff-165">このプロパティは 0 ～ 100 の範囲です。これを使用すると、<xref:System.Windows.Forms.ProgressBar.Value%2A>ar の <xref:System.Windows.Forms.ProgressBar> プロパティを更新できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-165">This property will range from 0 to 100, and it can be used to update the <xref:System.Windows.Forms.ProgressBar.Value%2A> property of a <xref:System.Windows.Forms.ProgressBar>.</span></span> <span data-ttu-id="f4aff-166">複数の非同期操作が保留中の場合は、<xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> プロパティを使用して、どの操作が進行状況をレポートしているのかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-166">If multiple asynchronous operations are pending, you can use the <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A?displayProperty=nameWithType> property to distinguish which operation is reporting progress.</span></span>  
  
 <span data-ttu-id="f4aff-167">一部のクラスは、非同期操作の進行に応じて、インクリメンタル結果をレポートします。</span><span class="sxs-lookup"><span data-stu-id="f4aff-167">Some classes may report incremental results as asynchronous operations proceed.</span></span> <span data-ttu-id="f4aff-168">これらの結果は <xref:System.ComponentModel.ProgressChangedEventArgs> から派生したクラス内に保存され、派生クラスのプロパティとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-168">These results will be stored in a class that derives from <xref:System.ComponentModel.ProgressChangedEventArgs> and they will appear as properties in the derived class.</span></span> <span data-ttu-id="f4aff-169">`ProgressChanged` イベントのイベント ハンドラーのこれらの結果へは、<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> プロパティにアクセスするのと同じようにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-169">You can access these results in the event handler for the `ProgressChanged` event, just as you would access the <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> property.</span></span> <span data-ttu-id="f4aff-170">複数の非同期操作が保留中の場合は、<xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> プロパティを使用して、どの操作がインクリメンタル結果をレポートしているのかを判別できます。</span><span class="sxs-lookup"><span data-stu-id="f4aff-170">If multiple asynchronous operations are pending, you can use the <xref:System.ComponentModel.ProgressChangedEventArgs.UserState%2A> property to distinguish which operation is reporting incremental results.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4aff-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4aff-171">See also</span></span>

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [<span data-ttu-id="f4aff-172">方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する</span><span class="sxs-lookup"><span data-stu-id="f4aff-172">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="f4aff-173">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="f4aff-173">How to: Run an Operation in the Background</span></span>](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [<span data-ttu-id="f4aff-174">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="f4aff-174">How to: Implement a Form That Uses a Background Operation</span></span>](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [<span data-ttu-id="f4aff-175">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="f4aff-175">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="f4aff-176">イベントベースの非同期パターンを実装するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="f4aff-176">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [<span data-ttu-id="f4aff-177">イベントベースの非同期パターンをいつ実装するかの決定</span><span class="sxs-lookup"><span data-stu-id="f4aff-177">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
