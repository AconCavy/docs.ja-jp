---
title: 更新された .NET Core イベント パターン
description: .NET Core イベント パターンによって旧バージョンとの互換性を提供する柔軟性を実現する方法と、非同期サブスクライバーによる安全なイベント処理を実装する方法について説明します。
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 9aa627c3-3222-4094-9ca8-7e88e1071e06
ms.openlocfilehash: a916a09b622f8df9bf99fafe52f35c706220f484
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039784"
---
# <a name="the-updated-net-core-event-pattern"></a><span data-ttu-id="bb600-103">更新された .NET Core イベント パターン</span><span class="sxs-lookup"><span data-stu-id="bb600-103">The Updated .NET Core Event Pattern</span></span>

[<span data-ttu-id="bb600-104">前へ</span><span class="sxs-lookup"><span data-stu-id="bb600-104">Previous</span></span>](event-pattern.md)

<span data-ttu-id="bb600-105">前回の記事では、最も一般的なイベント パターンについて説明しました。</span><span class="sxs-lookup"><span data-stu-id="bb600-105">The previous article discussed the most common event patterns.</span></span> <span data-ttu-id="bb600-106">.NET Core には、もっと柔軟なパターンがあります。</span><span class="sxs-lookup"><span data-stu-id="bb600-106">.NET Core has a more relaxed pattern.</span></span> <span data-ttu-id="bb600-107">このバージョンでは、`EventHandler<TEventArgs>` 定義に、`TEventArgs` は `System.EventArgs` から派生したクラスでなければならないという制約がなくなりました。</span><span class="sxs-lookup"><span data-stu-id="bb600-107">In this version, the `EventHandler<TEventArgs>` definition no longer has the constraint that `TEventArgs` must be a class derived from `System.EventArgs`.</span></span>

<span data-ttu-id="bb600-108">これにより、柔軟性が向上し、旧バージョンとの互換性が与えられます。</span><span class="sxs-lookup"><span data-stu-id="bb600-108">This increases flexibility for you, and is backwards compatible.</span></span> <span data-ttu-id="bb600-109">柔軟性から始めましょう。</span><span class="sxs-lookup"><span data-stu-id="bb600-109">Let's start with the flexibility.</span></span> <span data-ttu-id="bb600-110">クラス System.EventArgs で `MemberwiseClone()` というメソッドが導入されました。これはオブジェクトの簡易コピーを作成するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="bb600-110">The class System.EventArgs introduces one method: `MemberwiseClone()`, which creates a shallow copy of the object.</span></span>
<span data-ttu-id="bb600-111">そのメソッドでは、`EventArgs` から派生したあらゆるクラスのための機能を実装する目的で、リフレクションを利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb600-111">That method must use reflection in order to implement its functionality for any class derived from `EventArgs`.</span></span> <span data-ttu-id="bb600-112">その機能では、特定の派生クラスでの作成が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="bb600-112">That functionality is easier to create in a specific derived class.</span></span> <span data-ttu-id="bb600-113">つまり、System.EventArgs からの派生は設計を制限する制約ですが、他に利点はありません。</span><span class="sxs-lookup"><span data-stu-id="bb600-113">That effectively means that deriving from System.EventArgs is a constraint that limits your designs, but does not provide any additional benefit.</span></span>
<span data-ttu-id="bb600-114">実際、`EventArgs` から派生しないように `FileFoundArgs` と `SearchDirectoryArgs` の定義を変更できます。</span><span class="sxs-lookup"><span data-stu-id="bb600-114">In fact, you can change the definitions of `FileFoundArgs` and `SearchDirectoryArgs` so that they do not derive from `EventArgs`.</span></span>
<span data-ttu-id="bb600-115">このプログラムはまったく同じように機能します。</span><span class="sxs-lookup"><span data-stu-id="bb600-115">The program will work exactly the same.</span></span>

<span data-ttu-id="bb600-116">さらに 1 つ変更するのであれば、`SearchDirectoryArgs` を構造体に変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="bb600-116">You could also change the `SearchDirectoryArgs` to a struct, if you make one more change:</span></span>

```csharp
internal struct SearchDirectoryArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs) : this()
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
```

<span data-ttu-id="bb600-117">追加の変更は、すべてのフィールドを初期化するコンストラクターに入る前にパラメータ―なしのコンストラクターを呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="bb600-117">The additional change is to call the parameterless constructor before entering the constructor that initializes all the fields.</span></span> <span data-ttu-id="bb600-118">その追加がなければ、C# のルールは、割り当てられる前にプロパティがアクセスされていると報告するでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb600-118">Without that addition, the rules of C# would report that the properties are being accessed before they have been assigned.</span></span>

<span data-ttu-id="bb600-119">`FileFoundArgs` はクラス (参照型) から構造体 (値型) に変更しないでください。</span><span class="sxs-lookup"><span data-stu-id="bb600-119">You should not change the `FileFoundArgs` from a class (reference type) to a struct (value type).</span></span> <span data-ttu-id="bb600-120">キャンセルを処理するプロトコルで、イベント引数が参照で渡されることが要求されるためです。</span><span class="sxs-lookup"><span data-stu-id="bb600-120">That's because the protocol for handling cancel requires that the event arguments are passed by reference.</span></span> <span data-ttu-id="bb600-121">同じ変更をした場合、ファイル検索クラスは、イベント サブスクライバーが行った変更を観察できなくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bb600-121">If you made the same change, the file search class could never observe any changes made by any of the event subscribers.</span></span> <span data-ttu-id="bb600-122">サブスクライバーごとに構造体の新しいコピーが使用され、そのコピーは、ファイル検索オブジェクトで確認されるものとは別のコピーになるでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb600-122">A new copy of the structure would be used for each subscriber, and that copy would be a different copy than the one seen by the file search object.</span></span>

<span data-ttu-id="bb600-123">次に、この変更を下位互換可能にする方法について考えましょう。</span><span class="sxs-lookup"><span data-stu-id="bb600-123">Next, let's consider how this change can be backwards compatible.</span></span>
<span data-ttu-id="bb600-124">制約を削除しても、既存のコードには影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="bb600-124">The removal of the constraint does not affect any existing code.</span></span> <span data-ttu-id="bb600-125">既存のイベントの引数の型は引き続き `System.EventArgs` から派生します。</span><span class="sxs-lookup"><span data-stu-id="bb600-125">Any existing event argument types do still derive from `System.EventArgs`.</span></span>
<span data-ttu-id="bb600-126">`System.EventArgs` から引き続き派生する理由の 1 つが下位互換性です。</span><span class="sxs-lookup"><span data-stu-id="bb600-126">Backwards compatibility is one major reason why they will continue to derive from `System.EventArgs`.</span></span> <span data-ttu-id="bb600-127">既存のイベント サブスクライバーは、従来のパターンに従ったイベントのサブスクライバーになります。</span><span class="sxs-lookup"><span data-stu-id="bb600-127">Any existing event subscribers will be subscribers to an event that followed the classic pattern.</span></span>

<span data-ttu-id="bb600-128">同様の論理に従うと、今、イベントの引数の型を作成すると、それには既存のコードベースのサブスクライバーが与えられないでしょう。</span><span class="sxs-lookup"><span data-stu-id="bb600-128">Following similar logic, any event argument type created now would not have any subscribers in any existing codebases.</span></span> <span data-ttu-id="bb600-129">`System.EventArgs` から派生しない新しいイベントの型は、そのようなコードベースを壊しません。</span><span class="sxs-lookup"><span data-stu-id="bb600-129">New event types that do not derive from `System.EventArgs` will not break those codebases.</span></span>

## <a name="events-with-async-subscribers"></a><span data-ttu-id="bb600-130">非同期サブスクライバーのあるイベント</span><span class="sxs-lookup"><span data-stu-id="bb600-130">Events with Async subscribers</span></span>

<span data-ttu-id="bb600-131">学習する最後のパターンは、非同期コードを呼び出すイベント サブスクライバーを正しく記述する方法です。</span><span class="sxs-lookup"><span data-stu-id="bb600-131">You have one final pattern to learn: How to correctly write event subscribers that call async code.</span></span> <span data-ttu-id="bb600-132">この難題の説明は、[async と await](async.md) に関する記事にあります。</span><span class="sxs-lookup"><span data-stu-id="bb600-132">The challenge is described in the article on [async and await](async.md).</span></span> <span data-ttu-id="bb600-133">非同期メソッドには戻り値の型 void を指定できますが、指定しないことが推奨されます。</span><span class="sxs-lookup"><span data-stu-id="bb600-133">Async methods can have a void return type, but that is strongly discouraged.</span></span> <span data-ttu-id="bb600-134">イベント サブスクライバーのコードが非同期メソッドを呼び出すとき、`async void` メソッドを作成する以外の選択肢はありません。</span><span class="sxs-lookup"><span data-stu-id="bb600-134">When your event subscriber code calls an async method, you have no choice but to create an `async void` method.</span></span> <span data-ttu-id="bb600-135">イベント ハンドラー シグネチャでそれが要求されます。</span><span class="sxs-lookup"><span data-stu-id="bb600-135">The event handler signature requires it.</span></span>

<span data-ttu-id="bb600-136">このような相反する指示と何とか折り合いを付け、</span><span class="sxs-lookup"><span data-stu-id="bb600-136">You need to reconcile this opposing guidance.</span></span> <span data-ttu-id="bb600-137">無難な `async void` メソッドを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb600-137">Somehow, you must create a safe `async void` method.</span></span> <span data-ttu-id="bb600-138">実装が必要なパターンの基本は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="bb600-138">The basics of the pattern you need to implement are below:</span></span>

```csharp
worker.StartWorking += async (sender, eventArgs) =>
{
    try 
    {
        await DoWorkAsync();
    }
    catch (Exception e)
    {
        //Some form of logging.
        Console.WriteLine($"Async task failure: {e.ToString()}");
        // Consider gracefully, and quickly exiting.
    }
};
```

<span data-ttu-id="bb600-139">最初に、ハンドラーが非同期ハンドラーとしてマークされていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="bb600-139">First, notice that the handler is marked as an async handler.</span></span> <span data-ttu-id="bb600-140">イベント ハンドラーのデリゲート型に割り当てられているため、戻り値の型 void が与えられます。</span><span class="sxs-lookup"><span data-stu-id="bb600-140">Because it is being assigned to an event handler delegate type, it will have a void return type.</span></span> <span data-ttu-id="bb600-141">つまり、ハンドラーに示されるパターンに従う必要があります。非同期ハンドラーのコンテキストから例外をスローすることを許可しません。</span><span class="sxs-lookup"><span data-stu-id="bb600-141">That means you must follow the pattern shown in the handler, and not allow any exceptions to be thrown out of the context of the async handler.</span></span> <span data-ttu-id="bb600-142">タスクを返さないため、エラーが発生してもタスクはそれを報告できません。</span><span class="sxs-lookup"><span data-stu-id="bb600-142">Because it does not return a task, there is no task that can report the error by entering the faulted state.</span></span> <span data-ttu-id="bb600-143">メソッドは非同期であるため、例外をスローできません。</span><span class="sxs-lookup"><span data-stu-id="bb600-143">Because the method is async, the method can't simply throw the exception.</span></span> <span data-ttu-id="bb600-144">(呼び出しメソッドは `async` であるため、実行を続行しています。)実際の実行時動作は、環境が異なれば各様に定義されます。</span><span class="sxs-lookup"><span data-stu-id="bb600-144">(The calling method has continued execution because it is `async`.) The actual runtime behavior will be defined differently for different environments.</span></span> <span data-ttu-id="bb600-145">スレッドまたはスレッドを所有するプロセスを終了させたり、またはプロセスを中間状態のままにする場合があります。</span><span class="sxs-lookup"><span data-stu-id="bb600-145">It may terminate the thread or the process that owns the thread, or leave the process in an indeterminate state.</span></span> <span data-ttu-id="bb600-146">これらの潜在的な結果はすべて、非常に望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="bb600-146">All of these potential outcomes are highly undesirable.</span></span>

<span data-ttu-id="bb600-147">そのため、独自の try ブロックに非同期タスクの await ステートメントをラップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="bb600-147">That's why you should wrap the await statement for the async Task in your own try block.</span></span> <span data-ttu-id="bb600-148">それでタスクにエラーが発生した場合、エラーをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="bb600-148">If it does cause a faulted task, you can log the error.</span></span> <span data-ttu-id="bb600-149">アプリケーションがエラーから復旧できない場合、プログラムを至急、正常に終了できます。</span><span class="sxs-lookup"><span data-stu-id="bb600-149">If it is an error from which your application cannot recover, you can exit the program quickly and gracefully</span></span>

<span data-ttu-id="bb600-150">以上が .NET イベント パターンの主要な更新でした。</span><span class="sxs-lookup"><span data-stu-id="bb600-150">Those are the major updates to the .NET event pattern.</span></span> <span data-ttu-id="bb600-151">使用するライブラリには以前のバージョンのサンプルがたくさんあります。</span><span class="sxs-lookup"><span data-stu-id="bb600-151">You will see many examples of the earlier versions in the libraries you work with.</span></span> <span data-ttu-id="bb600-152">しかしながら、最新のパターンも理解してください。</span><span class="sxs-lookup"><span data-stu-id="bb600-152">However, you should understand what the latest patterns are as well.</span></span>

<span data-ttu-id="bb600-153">このシリーズの次の記事では、設計における `delegates` と `events` の使い分けについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bb600-153">The next article in this series helps you distinguish between using `delegates` and `events` in your designs.</span></span> <span data-ttu-id="bb600-154">概念は似ており、最良のプログラムを作るための知識をその記事で得ることができます。</span><span class="sxs-lookup"><span data-stu-id="bb600-154">They are similar concepts, and that article will help you make the best decision for your programs.</span></span>

[<span data-ttu-id="bb600-155">次へ</span><span class="sxs-lookup"><span data-stu-id="bb600-155">Next</span></span>](distinguish-delegates-events.md)
