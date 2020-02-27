---
title: 非同期アプリにおける再入の処理 (C#)
ms.date: 07/20/2015
ms.assetid: 47c5075e-c448-45ce-9155-ed4e7e98c677
ms.openlocfilehash: 67fbbd294ffe6219b58065f974543b2dd483a92c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451864"
---
# <a name="handling-reentrancy-in-async-apps-c"></a><span data-ttu-id="425f8-102">非同期アプリにおける再入の処理 (C#)</span><span class="sxs-lookup"><span data-stu-id="425f8-102">Handling Reentrancy in Async Apps (C#)</span></span>

<span data-ttu-id="425f8-103">非同期コードをアプリに含める場合は、再入を考慮し、場合によっては回避することをお勧めします。これは、完了前に非同期操作の再入力を参照します。</span><span class="sxs-lookup"><span data-stu-id="425f8-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="425f8-104">再入の可能性を特定して処理しないと、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="425f8-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

<span data-ttu-id="425f8-105">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="425f8-105">**In this topic**</span></span>

- [<span data-ttu-id="425f8-106">再入を認識する</span><span class="sxs-lookup"><span data-stu-id="425f8-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)

- [<span data-ttu-id="425f8-107">再入を処理する</span><span class="sxs-lookup"><span data-stu-id="425f8-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)

  - <span data-ttu-id="425f8-108">[[Start] ボタンを無効にする](#BKMK_DisableTheStartButton)</span><span class="sxs-lookup"><span data-stu-id="425f8-108">[Disable the Start Button](#BKMK_DisableTheStartButton)</span></span>

  - [<span data-ttu-id="425f8-109">操作を取り消して再開する</span><span class="sxs-lookup"><span data-stu-id="425f8-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  - [<span data-ttu-id="425f8-110">複数の操作を実行して出力をキューに登録する</span><span class="sxs-lookup"><span data-stu-id="425f8-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

- [<span data-ttu-id="425f8-111">例のアプリをレビューして実行する</span><span class="sxs-lookup"><span data-stu-id="425f8-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)

> [!NOTE]
> <span data-ttu-id="425f8-112">この例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="425f8-112">To run the example, you must have Visual Studio 2012 or newer and .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="425f8-113">現在、アプリ開発で使用する最小バージョンは、トランスポート層セキュリティ (TLS) バージョン 1.2 です。</span><span class="sxs-lookup"><span data-stu-id="425f8-113">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="425f8-114">ご利用のアプリがバージョン 4.7 より前の .NET Framework を対象としている場合は、「[.NET Framework でのトランスポート層セキュリティ (TLS) のベスト プラクティス](../../../../framework/network-programming/tls.md)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="425f8-114">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="425f8-115">再入を認識する</span><span class="sxs-lookup"><span data-stu-id="425f8-115">Recognizing Reentrancy</span></span>

<span data-ttu-id="425f8-116">このトピックの例では、ユーザーが **[Start]** をクリックして非同期アプリを開始します。このアプリは、一連の Web サイトをダウンロードし、ダウンロードされた合計バイト数を計算します。</span><span class="sxs-lookup"><span data-stu-id="425f8-116">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="425f8-117">同期バージョンの例では、ユーザーが何回ボタンをクリックしても同じように応答します。2 回目以降はアプリが実行を完了するまで、UI スレッドはこれらのイベントを無視するからです。</span><span class="sxs-lookup"><span data-stu-id="425f8-117">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="425f8-118">ただし、非同期アプリでは、UI スレッドは応答し続けるので、完了前に非同期操作を再入力することがあります。</span><span class="sxs-lookup"><span data-stu-id="425f8-118">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="425f8-119">次の例は、ユーザーが 1 度だけ **[Start]** をクリックした場合の出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="425f8-119">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="425f8-120">ダウンロードされた Web サイトの一覧には、各サイトのサイズがバイト単位で表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-120">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="425f8-121">合計バイト数は最後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-121">The total number of bytes appears at the end.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="425f8-122">ただし、ユーザーがボタンを複数回クリックすると、イベント ハンドラーは繰り返し呼び出され、ダウンロード プロセスはそのたびに再入力されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-122">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="425f8-123">その結果、複数の非同期操作が同時に実行され、出力は結果をインターリーブするので、合計バイト数がややこしくなります。</span><span class="sxs-lookup"><span data-stu-id="425f8-123">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
7. msdn.microsoft.com                                            42972
4. msdn.microsoft.com/library/hh290140.aspx               117152
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

5. msdn.microsoft.com/library/hh524395.aspx                68959
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
6. msdn.microsoft.com/library/ms404677.aspx               197325
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
7. msdn.microsoft.com                                            42972
5. msdn.microsoft.com/library/hh524395.aspx                68959
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591

6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="425f8-124">このトピックの最後にスクロールすると、この出力を生成するコードをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="425f8-124">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="425f8-125">コードを試してみるには、ソリューションをローカル コンピューターにダウンロードしてから WebsiteDownload プロジェクトを実行するか、このトピックの最後にあるコードを使用して独自のプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="425f8-125">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project.</span></span> <span data-ttu-id="425f8-126">詳細と手順については、「[例のアプリをレビューして実行する](#BKMD_SettingUpTheExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="425f8-126">For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="425f8-127">再入を処理する</span><span class="sxs-lookup"><span data-stu-id="425f8-127">Handling Reentrancy</span></span>

<span data-ttu-id="425f8-128">再入の処理は、アプリで何を行うかに応じてさまざまな方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="425f8-128">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="425f8-129">このトピックでは、次の例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="425f8-129">This topic presents the following examples:</span></span>

- <span data-ttu-id="425f8-130">[[Start] ボタンを無効にする](#BKMK_DisableTheStartButton)</span><span class="sxs-lookup"><span data-stu-id="425f8-130">[Disable the Start Button](#BKMK_DisableTheStartButton)</span></span>

  <span data-ttu-id="425f8-131">処理の実行中、ユーザーが中断できないように **[Start]** ボタンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="425f8-131">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="425f8-132">操作を取り消して再開する</span><span class="sxs-lookup"><span data-stu-id="425f8-132">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="425f8-133">ユーザーが **[Start]** を再度クリックしたときに実行されている処理を取り消し、最後に要求された処理を続行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="425f8-133">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="425f8-134">複数の操作を実行して出力をキューに登録する</span><span class="sxs-lookup"><span data-stu-id="425f8-134">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="425f8-135">要求されたすべての処理を非同期的に実行できるようにします。ただし、各処理の結果が順番にまとめて表示されるように出力を調整します。</span><span class="sxs-lookup"><span data-stu-id="425f8-135">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="425f8-136">[Start] ボタンを無効にする</span><span class="sxs-lookup"><span data-stu-id="425f8-136">Disable the Start Button</span></span>

<span data-ttu-id="425f8-137">処理の実行中に **[Start]** ボタンを利用できないようにするには、`StartButton_Click` イベント ハンドラーの上部にあるボタンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="425f8-137">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="425f8-138">処理が完了しユーザーが再度アプリを実行できるようになったら、`finally` ブロック内からこのボタンを再度有効にできます。</span><span class="sxs-lookup"><span data-stu-id="425f8-138">You can then reenable the button from within a  `finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="425f8-139">このシナリオを設定するには、「[例のアプリをレビューして実行する](#BKMD_SettingUpTheExample)」に用意されている基本コードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="425f8-139">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="425f8-140">また、完成したアプリを「[Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)」 (非同期の例: .NET デスクトップ アプリでの再入) からダウンロードすることもできます。</span><span class="sxs-lookup"><span data-stu-id="425f8-140">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="425f8-141">プロジェクトの名前は DisableStartButton です。</span><span class="sxs-lookup"><span data-stu-id="425f8-141">The name of the project is DisableStartButton.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Text = "";

    // ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = false;

    try
    {
        await AccessTheWebAsync();
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
    // ***Enable the Start button in case you want to run the program again.
    finally
    {
        StartButton.IsEnabled = true;
    }
}
```

<span data-ttu-id="425f8-142">変更の結果、`AccessTheWebAsync` が Web サイトをダウンロードしている間は、ボタンが応答しないので、プロセスを再入力できません。</span><span class="sxs-lookup"><span data-stu-id="425f8-142">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="BKMK_CancelAndRestart"></a><span data-ttu-id="425f8-143">操作を取り消して再開する</span><span class="sxs-lookup"><span data-stu-id="425f8-143">Cancel and Restart the Operation</span></span>

<span data-ttu-id="425f8-144">**[Start]** ボタンを無効にせず、有効の状態を保持できますが、ユーザーがボタンを再度クリックしたときに、実行中の処理を取り消し、最後に開始された処理を続行できます。</span><span class="sxs-lookup"><span data-stu-id="425f8-144">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="425f8-145">取り消しの詳細については、「[Fine Tuning Your Async Application (C#) (非同期アプリケーションの微調整 (C#))](./fine-tuning-your-async-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="425f8-145">For more information about cancellation, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="425f8-146">このシナリオを設定するには、「[例のアプリをレビューして実行する](#BKMD_SettingUpTheExample)」に用意されている基本コードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="425f8-146">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="425f8-147">また、完成したアプリを「[Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)」 (非同期の例: .NET デスクトップ アプリでの再入) からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="425f8-147">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="425f8-148">プロジェクトの名前は CancelAndRestart です。</span><span class="sxs-lookup"><span data-stu-id="425f8-148">The name of the project is CancelAndRestart.</span></span>

1. <span data-ttu-id="425f8-149">すべてのメソッドのスコープである <xref:System.Threading.CancellationTokenSource> 変数、`cts` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="425f8-149">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```csharp
    public partial class MainWindow : Window   // Or class MainPage
    {
        // *** Declare a System.Threading.CancellationTokenSource.
        CancellationTokenSource cts;
    ```

2. <span data-ttu-id="425f8-150">`StartButton_Click` で、処理が既に実行されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="425f8-150">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="425f8-151">`cts` の値が null の場合、アクティブな操作はまだありません。</span><span class="sxs-lookup"><span data-stu-id="425f8-151">If the value of `cts` is null, no operation is already active.</span></span> <span data-ttu-id="425f8-152">値が null 以外の場合は、実行中の処理が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-152">If the value isn't null, the operation that is already running is canceled.</span></span>

    ```csharp
    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }
    ```

3. <span data-ttu-id="425f8-153">`cts` に、現在のプロセスを表す別の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="425f8-153">Set `cts` to a different value that represents the current process.</span></span>

    ```csharp
    // *** Now set cts to a new value that you can use to cancel the current process
    // if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;
    ```

4. <span data-ttu-id="425f8-154">`StartButton_Click` の最後で現在のプロセスが完了します。したがって、`cts` の値を null に戻します。</span><span class="sxs-lookup"><span data-stu-id="425f8-154">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to null.</span></span>

    ```csharp
    // *** When the process is complete, signal that another process can begin.
    if (cts == newCTS)
        cts = null;
    ```

<span data-ttu-id="425f8-155">次のコードは、`StartButton_Click` のすべての変更を示しています。</span><span class="sxs-lookup"><span data-stu-id="425f8-155">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="425f8-156">追加部分はアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="425f8-156">The additions are marked with asterisks.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // This line is commented out to make the results clearer in the output.
    //ResultsTextBox.Clear();

    // *** If a download process is already underway, cancel it.
    if (cts != null)
    {
        cts.Cancel();
    }

    // *** Now set cts to cancel the current process if the button is chosen again.
    CancellationTokenSource newCTS = new CancellationTokenSource();
    cts = newCTS;

    try
    {
        // ***Send cts.Token to carry the message if there is a cancellation request.
        await AccessTheWebAsync(cts.Token);

    }
    // *** Catch cancellations separately.
    catch (OperationCanceledException)
    {
        ResultsTextBox.Text += "\r\nDownloads canceled.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.\r\n";
    }
    // *** When the process is complete, signal that another process can proceed.
    if (cts == newCTS)
        cts = null;
}
```

<span data-ttu-id="425f8-157">`AccessTheWebAsync` で、次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="425f8-157">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="425f8-158">`StartButton_Click` からキャンセル トークンを受け取るためのパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="425f8-158">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="425f8-159"><xref:System.Net.Http.HttpClient.GetAsync%2A> メソッドを使用して Web サイトをダウンロードします。これは `GetAsync` が <xref:System.Threading.CancellationToken> 引数を受け取るからです。</span><span class="sxs-lookup"><span data-stu-id="425f8-159">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="425f8-160">`DisplayResults` を呼び出してダウンロードした各 Web サイトの結果を表示する前に、`ct` で、現在の処理が取り消されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="425f8-160">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

<span data-ttu-id="425f8-161">次のコードはこの変更を示しています。変更の部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="425f8-161">The following code shows these changes, which are marked with asterisks.</span></span>

```csharp
// *** Provide a parameter for the CancellationToken from StartButton_Click.
async Task AccessTheWebAsync(CancellationToken ct)
{
    // Declare an HttpClient object.
    HttpClient client = new HttpClient();

    // Make a list of web addresses.
    List<string> urlList = SetUpURLList();

    var total = 0;
    var position = 0;

    foreach (var url in urlList)
    {
        // *** Use the HttpClient.GetAsync method because it accepts a
        // cancellation token.
        HttpResponseMessage response = await client.GetAsync(url, ct);

        // *** Retrieve the website contents from the HttpResponseMessage.
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

        // *** Check for cancellations before displaying information about the
        // latest site.
        ct.ThrowIfCancellationRequested();

        DisplayResults(url, urlContents, ++position);

        // Update the total.
        total += urlContents.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

<span data-ttu-id="425f8-162">このアプリの実行中に複数回 **[Start]** ボタンをクリックすると、次の出力のような結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-162">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>

```output
1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               122505
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
Download canceled.

1. msdn.microsoft.com/library/hh191443.aspx                83732
2. msdn.microsoft.com/library/aa578028.aspx               205273
3. msdn.microsoft.com/library/jj155761.aspx                29019
4. msdn.microsoft.com/library/hh290140.aspx               117152
5. msdn.microsoft.com/library/hh524395.aspx                68959
6. msdn.microsoft.com/library/ms404677.aspx               197325
7. msdn.microsoft.com                                            42972
8. msdn.microsoft.com/library/ff730837.aspx               146159

TOTAL bytes returned:  890591
```

<span data-ttu-id="425f8-163">部分的なリストを削除するには、`StartButton_Click` コードの先頭行のコメントを解除して、ユーザーが操作を再開するたびに、テキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="425f8-163">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="425f8-164">複数の操作を実行して出力をキューに登録する</span><span class="sxs-lookup"><span data-stu-id="425f8-164">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="425f8-165">この 3 番目の例は、ユーザーが **[Start]** ボタンをクリックするたびに非同期操作が開始され、すべての操作が完了まで実行されるという点で最も複雑です。</span><span class="sxs-lookup"><span data-stu-id="425f8-165">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="425f8-166">要求されたすべての操作によって Web サイトがリストから非同期的にダウンロードされますが、操作からの出力は順次表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-166">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="425f8-167">つまり、「[再入を認識する](#BKMK_RecognizingReentrancy)」の出力に示されているように、実際のダウンロード アクティビティはインターリーブされますが、各グループの結果のリストは個別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-167">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="425f8-168">操作は、表示プロセスのゲートキーパーとして機能するグローバル <xref:System.Threading.Tasks.Task>、`pendingWork` を共有します。</span><span class="sxs-lookup"><span data-stu-id="425f8-168">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="425f8-169">このシナリオを設定するには、「[例のアプリをレビューして実行する](#BKMD_SettingUpTheExample)」に用意されている基本コードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="425f8-169">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="425f8-170">また、完成したアプリを「[Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)」 (非同期の例: .NET デスクトップ アプリでの再入) からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="425f8-170">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="425f8-171">プロジェクトの名前は QueueResults です。</span><span class="sxs-lookup"><span data-stu-id="425f8-171">The name of the project is QueueResults.</span></span>

<span data-ttu-id="425f8-172">次の出力は、ユーザーが 1 度だけ **[Start]** ボタンをクリックした場合の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="425f8-172">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="425f8-173">文字ラベル A は、 **[Start]** ボタンが最初にクリックされた結果であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="425f8-173">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="425f8-174">数字は、ダウンロード対象の一覧における URL の順序を示しています。</span><span class="sxs-lookup"><span data-stu-id="425f8-174">The numbers show the order of the URLs in the list of download targets.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               209858
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71260
A-6. msdn.microsoft.com/library/ms404677.aspx               199186
A-7. msdn.microsoft.com                                            53266
A-8. msdn.microsoft.com/library/ff730837.aspx               148020

TOTAL bytes returned:  918876

#Group A is complete.
```

<span data-ttu-id="425f8-175">ユーザーが **[Start]** ボタンを 3 回クリックすると、アプリでは次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-175">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="425f8-176">先頭にシャープ記号 (#) が付いている情報行は、アプリケーションの進行状況を追跡します。</span><span class="sxs-lookup"><span data-stu-id="425f8-176">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

```output
#Starting group A.
#Task assigned for group A.

A-1. msdn.microsoft.com/library/hh191443.aspx                87389
A-2. msdn.microsoft.com/library/aa578028.aspx               207089
A-3. msdn.microsoft.com/library/jj155761.aspx                30870
A-4. msdn.microsoft.com/library/hh290140.aspx               119027
A-5. msdn.microsoft.com/library/hh524395.aspx                71259
A-6. msdn.microsoft.com/library/ms404677.aspx               199185

#Starting group B.
#Task assigned for group B.

A-7. msdn.microsoft.com                                            53266

#Starting group C.
#Task assigned for group C.

A-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916095

B-1. msdn.microsoft.com/library/hh191443.aspx                87389
B-2. msdn.microsoft.com/library/aa578028.aspx               207089
B-3. msdn.microsoft.com/library/jj155761.aspx                30870
B-4. msdn.microsoft.com/library/hh290140.aspx               119027
B-5. msdn.microsoft.com/library/hh524395.aspx                71260
B-6. msdn.microsoft.com/library/ms404677.aspx               199186

#Group A is complete.

B-7. msdn.microsoft.com                                            53266
B-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  916097

C-1. msdn.microsoft.com/library/hh191443.aspx                87389
C-2. msdn.microsoft.com/library/aa578028.aspx               207089

#Group B is complete.

C-3. msdn.microsoft.com/library/jj155761.aspx                30870
C-4. msdn.microsoft.com/library/hh290140.aspx               119027
C-5. msdn.microsoft.com/library/hh524395.aspx                72765
C-6. msdn.microsoft.com/library/ms404677.aspx               199186
C-7. msdn.microsoft.com                                            56190
C-8. msdn.microsoft.com/library/ff730837.aspx               148010

TOTAL bytes returned:  920526

#Group C is complete.
```

<span data-ttu-id="425f8-177">グループ B とグループ C は、グループ A が終了する前に開始します。ただし、各グループの出力は個別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-177">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="425f8-178">グループ A のすべての出力が最初に表示され、その後にグループ B のすべての出力が続き、さらにグループ C のすべての出力が表示されます。グループは必ず順番に表示され、グループごとに、個別の Web サイトに関する情報が URL 一覧の URL の順番で表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-178">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="425f8-179">ただし、ダウンロードが実際に行われる順序は予測できません。</span><span class="sxs-lookup"><span data-stu-id="425f8-179">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="425f8-180">複数のグループが開始されたら、そのグループが生成するダウンロード タスクはすべてのアクティブです。</span><span class="sxs-lookup"><span data-stu-id="425f8-180">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="425f8-181">B-1 の前に A-1 がダウンロードされる、また、A-2 の前に A-1 がダウンロードされると仮定することはできません。</span><span class="sxs-lookup"><span data-stu-id="425f8-181">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="425f8-182">グローバル定義</span><span class="sxs-lookup"><span data-stu-id="425f8-182">Global Definitions</span></span>

<span data-ttu-id="425f8-183">サンプル コードには、すべてのメソッドから参照できる次の 2 つのグローバル宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="425f8-183">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```csharp
public partial class MainWindow : Window  // Class MainPage in Windows Store app.
{
    // ***Declare the following variables where all methods can access them.
    private Task pendingWork = null;
    private char group = (char)('A' - 1);
```

<span data-ttu-id="425f8-184">`Task` 変数、`pendingWork` は、表示プロセスを監視し、あるグループが別のグループの表示操作を中断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="425f8-184">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="425f8-185">文字変数 `group` は、異なるグループからの出力にラベルを付け、予想された順序で結果が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="425f8-185">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="425f8-186">Click イベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="425f8-186">The Click Event Handler</span></span>

<span data-ttu-id="425f8-187">イベント ハンドラー `StartButton_Click` は、ユーザーが **[Start]** ボタンを選択するたびに、グループ文字をインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="425f8-187">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="425f8-188">ハンドラーは `AccessTheWebAsync` を呼び出して、ダウンロード操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="425f8-188">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```csharp
private async void StartButton_Click(object sender, RoutedEventArgs e)
{
    // ***Verify that each group's results are displayed together, and that
    // the groups display in order, by marking each group with a letter.
    group = (char)(group + 1);
    ResultsTextBox.Text += $"\r\n\r\n#Starting group {group}.";

    try
    {
        // *** Pass the group value to AccessTheWebAsync.
        char finishedGroup = await AccessTheWebAsync(group);

        // The following line verifies a successful return from the download and
        // display procedures.
        ResultsTextBox.Text += $"\r\n\r\n#Group {finishedGroup} is complete.\r\n";
    }
    catch (Exception)
    {
        ResultsTextBox.Text += "\r\nDownloads failed.";
    }
}
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="425f8-189">AccessTheWebAsync メソッド</span><span class="sxs-lookup"><span data-stu-id="425f8-189">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="425f8-190">この例では、`AccessTheWebAsync` を 2 つのメソッドに分割します。</span><span class="sxs-lookup"><span data-stu-id="425f8-190">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="425f8-191">最初のメソッド、`AccessTheWebAsync` は、グループのすべてのダウンロード タスクを開始し、`pendingWork` を設定して表示プロセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="425f8-191">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="425f8-192">このメソッドは、統合言語クエリ (LINQ クエリ) と <xref:System.Linq.Enumerable.ToArray%2A> を使用して、すべてのダウンロードを同時に開始します。</span><span class="sxs-lookup"><span data-stu-id="425f8-192">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="425f8-193">その後、`AccessTheWebAsync` は、`FinishOneGroupAsync` を呼び出して各ダウンロードが完了するまで待機し、その長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="425f8-193">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="425f8-194">`FinishOneGroupAsync` は、`pendingWork` の `AccessTheWebAsync` に割り当てられたタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="425f8-194">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="425f8-195">この値は、タスクが完了する前に、別の操作によって操作が中断されないようにします。</span><span class="sxs-lookup"><span data-stu-id="425f8-195">That value prevents interruption by another operation before the task is complete.</span></span>

```csharp
private async Task<char> AccessTheWebAsync(char grp)
{
    HttpClient client = new HttpClient();

    // Make a list of the web addresses to download.
    List<string> urlList = SetUpURLList();

    // ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Task<byte[]>[] getContentTasks = urlList.Select(url => client.GetByteArrayAsync(url)).ToArray();

    // ***Call the method that awaits the downloads and displays the results.
    // Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp);

    ResultsTextBox.Text += $"\r\n#Task assigned for group {grp}. Download tasks are active.\r\n";

    // ***This task is complete when a group has finished downloading and displaying.
    await pendingWork;

    // You can do other work here or just return.
    return grp;
}
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="425f8-196">FinishOneGroupAsync メソッド</span><span class="sxs-lookup"><span data-stu-id="425f8-196">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="425f8-197">このメソッドは、グループのダウンロード タスクを循環参照し、それぞれを待機してから、ダウンロードされた Web サイトの長さを表示して、その長さを合計に追加します。</span><span class="sxs-lookup"><span data-stu-id="425f8-197">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="425f8-198">`FinishOneGroupAsync` の最初のステートメントは、`pendingWork` を使用して、メソッドを入力することが、表示プロセスの操作または待機中の操作の妨げにならないようにします。</span><span class="sxs-lookup"><span data-stu-id="425f8-198">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="425f8-199">これらの操作が進行中の場合、入力操作は順番を待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="425f8-199">If such an operation is in progress, the entering operation must wait its turn.</span></span>

```csharp
private async Task FinishOneGroupAsync(List<string> urls, Task<byte[]>[] contentTasks, char grp)
{
    // ***Wait for the previous group to finish displaying results.
    if (pendingWork != null) await pendingWork;

    int total = 0;

    // contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    for (int i = 0; i < contentTasks.Length; i++)
    {
        // Await the download of a particular URL, and then display the URL and
        // its length.
        byte[] content = await contentTasks[i];
        DisplayResults(urls[i], content, i, grp);
        total += content.Length;
    }

    // Display the total count for all of the websites.
    ResultsTextBox.Text +=
        $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
}
```

#### <a name="points-of-interest"></a><span data-ttu-id="425f8-200">目的のポイント</span><span class="sxs-lookup"><span data-stu-id="425f8-200">Points of Interest</span></span>

<span data-ttu-id="425f8-201">出力で先頭にシャープ記号 (#) が付いている情報行は、この例の動作を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="425f8-201">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="425f8-202">出力のパターンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="425f8-202">The output shows the following patterns.</span></span>

- <span data-ttu-id="425f8-203">前のグループが出力を表示していても、グループを開始できます。その際、前のグループの出力の表示は中断されません。</span><span class="sxs-lookup"><span data-stu-id="425f8-203">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

    ```output
    #Starting group A.
    #Task assigned for group A. Download tasks are active.

    A-1. msdn.microsoft.com/library/hh191443.aspx                87389
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260

    #Starting group B.
    #Task assigned for group B. Download tasks are active.

    A-6. msdn.microsoft.com/library/ms404677.aspx               199186
    A-7. msdn.microsoft.com                                            53078
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915919

    B-1. msdn.microsoft.com/library/hh191443.aspx                87388
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870

    #Group A is complete.

    B-4. msdn.microsoft.com/library/hh290140.aspx               119027
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186
    B-7. msdn.microsoft.com                                            53078
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010

    TOTAL bytes returned:  915908
    ```

- <span data-ttu-id="425f8-204">最初に開始したグループ A についてのみ、`FinishOneGroupAsync` 開始時の、`pendingWork` タスクは null になります。</span><span class="sxs-lookup"><span data-stu-id="425f8-204">The `pendingWork` task is null  at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="425f8-205">`FinishOneGroupAsync` に達したとき、グループ A はまだ await 式を完了していません。</span><span class="sxs-lookup"><span data-stu-id="425f8-205">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="425f8-206">したがって、コントロールは `AccessTheWebAsync` に戻っておらず、`pendingWork` への最初の割り当ては発生していません。</span><span class="sxs-lookup"><span data-stu-id="425f8-206">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="425f8-207">次の 2 行は、出力に必ず同時に表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-207">The following two lines always appear together in the output.</span></span> <span data-ttu-id="425f8-208">`StartButton_Click` のグループ操作が開始してから、グループのタスクが `pendingWork` に割り当てられるまでの間、コードが中断されることは決してありません。</span><span class="sxs-lookup"><span data-stu-id="425f8-208">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

    ```output
    #Starting group B.
    #Task assigned for group B. Download tasks are active.
    ```

    <span data-ttu-id="425f8-209">グループが `StartButton_Click` に移行したら、`FinishOneGroupAsync` に移行するまでは、await 式は完了しません。</span><span class="sxs-lookup"><span data-stu-id="425f8-209">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="425f8-210">したがって、コード セグメントの途中で、他の操作がコントロールを得ることはありません。</span><span class="sxs-lookup"><span data-stu-id="425f8-210">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="425f8-211">例のアプリをレビューして実行する</span><span class="sxs-lookup"><span data-stu-id="425f8-211">Reviewing and Running the Example App</span></span>

<span data-ttu-id="425f8-212">サンプル アプリをさらに詳しく理解するには、そのアプリをダウンロードし、ご自身でビルドしてみてください。また、このトピックの最後にあるコードをレビューすることもできます。アプリを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="425f8-212">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="425f8-213">Windows Presentation Foundation (WPF) デスクトップ アプリとして例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="425f8-213">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="425f8-214">アプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="425f8-214">Downloading the App</span></span>

1. <span data-ttu-id="425f8-215">圧縮ファイルを「[Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)」 (非同期の例: .NET デスクトップ アプリでの再入) からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="425f8-215">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="425f8-216">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="425f8-216">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="425f8-217">メニュー バーで **[ファイル]** 、 **[開く]** 、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="425f8-217">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="425f8-218">圧縮解除したサンプル コードが含まれるフォルダーに移動し、ソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="425f8-218">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="425f8-219">**ソリューション エクスプローラー**で、実行するプロジェクトのショートカット メニューを開き、 **[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="425f8-219">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="425f8-220">Ctrl キーを押しながら F5 キーを押してプロジェクトをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="425f8-220">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="BKMK_BuildingTheApp"></a><span data-ttu-id="425f8-221">アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="425f8-221">Building the App</span></span>

<span data-ttu-id="425f8-222">次のセクションでは、WPF アプリとして例をビルドするコードを示します。</span><span class="sxs-lookup"><span data-stu-id="425f8-222">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="425f8-223">WPF アプリをビルドするには</span><span class="sxs-lookup"><span data-stu-id="425f8-223">To build a WPF app</span></span>

1. <span data-ttu-id="425f8-224">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="425f8-224">Start Visual Studio.</span></span>

2. <span data-ttu-id="425f8-225">メニュー バーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="425f8-225">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="425f8-226">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-226">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="425f8-227">**[インストールされたテンプレート]** ペインで、 **[Visual C#]** を展開し、 **[Windows]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="425f8-227">In the **Installed Templates** pane, expand **Visual C#**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="425f8-228">プロジェクトの種類の一覧の **[WPF アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="425f8-228">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="425f8-229">プロジェクトに `WebsiteDownloadWPF` という名前を指定し、4.6 以降の .NET Framework のバージョンを選択して、 **[OK]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="425f8-229">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="425f8-230">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-230">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="425f8-231">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="425f8-231">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="425f8-232">タブが表示されない場合は、**ソリューション エクスプローラー**で MainWindow.xaml のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="425f8-232">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="425f8-233">MainWindow.xaml の **XAML** ビューで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="425f8-233">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window x:Class="WebsiteDownloadWPF.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WebsiteDownloadWPF"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Width="517" Height="360">
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />
        </Grid>
    </Window>
    ```

     <span data-ttu-id="425f8-234">テキスト ボックスとボタンを含む簡単なウィンドウが、MainWindow.xaml の**デザイン** ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="425f8-234">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="425f8-235">**ソリューション エクスプローラー**で **[参照]** を右クリックし、 **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="425f8-235">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="425f8-236">まだ選択されていない場合は、<xref:System.Net.Http> の参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="425f8-236">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="425f8-237">**ソリューション エクスプローラー**で MainWindow.xaml.cs のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="425f8-237">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

10. <span data-ttu-id="425f8-238">MainWindow.xaml.cs のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="425f8-238">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    using System.Windows;
    using System.Windows.Controls;
    using System.Windows.Data;
    using System.Windows.Documents;
    using System.Windows.Input;
    using System.Windows.Media;
    using System.Windows.Media.Imaging;
    using System.Windows.Navigation;
    using System.Windows.Shapes;

    // Add the following using directives, and add a reference for System.Net.Http.
    using System.Net.Http;
    using System.Threading;

    namespace WebsiteDownloadWPF
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                System.Net.ServicePointManager.SecurityProtocol |= System.Net.SecurityProtocolType.Tls12;
                InitializeComponent();
            }

            private async void StartButton_Click(object sender, RoutedEventArgs e)
            {
                // This line is commented out to make the results clearer in the output.
                //ResultsTextBox.Text = "";

                try
                {
                    await AccessTheWebAsync();
                }
                catch (Exception)
                {
                    ResultsTextBox.Text += "\r\nDownloads failed.";
                }
            }

            private async Task AccessTheWebAsync()
            {
                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                // Make a list of web addresses.
                List<string> urlList = SetUpURLList();

                var total = 0;
                var position = 0;

                foreach (var url in urlList)
                {
                    // GetByteArrayAsync returns a task. At completion, the task
                    // produces a byte array.
                    byte[] urlContents = await client.GetByteArrayAsync(url);

                    DisplayResults(url, urlContents, ++position);

                    // Update the total.
                    total += urlContents.Length;
                }

                // Display the total count for all of the websites.
                ResultsTextBox.Text +=
                    $"\r\n\r\nTOTAL bytes returned:  {total}\r\n";
            }

            private List<string> SetUpURLList()
            {
                List<string> urls = new List<string>
                {
                    "https://msdn.microsoft.com/library/hh191443.aspx",
                    "https://msdn.microsoft.com/library/aa578028.aspx",
                    "https://msdn.microsoft.com/library/jj155761.aspx",
                    "https://msdn.microsoft.com/library/hh290140.aspx",
                    "https://msdn.microsoft.com/library/hh524395.aspx",
                    "https://msdn.microsoft.com/library/ms404677.aspx",
                    "https://msdn.microsoft.com",
                    "https://msdn.microsoft.com/library/ff730837.aspx"
                };
                return urls;
            }

            private void DisplayResults(string url, byte[] content, int pos)
            {
                // Display the length of each website. The string format is designed
                // to be used with a monospaced font, such as Lucida Console or
                // Global Monospace.

                // Strip off the "https://".
                var displayURL = url.Replace("https://", "");
                // Display position in the URL list, the URL, and the number of bytes.
                ResultsTextBox.Text += $"\n{pos}. {displayURL,-58} {content.Length,8}";
            }
        }
    }
    ```

11. <span data-ttu-id="425f8-239">Ctrl キーを押しながら F5 キーを押してプログラムを実行し、 **[Start]** ボタンを複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="425f8-239">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="425f8-240">「[[Start] ボタンを無効にする](#BKMK_DisableTheStartButton)」、「[操作を取り消して再開する](#BKMK_CancelAndRestart)」、または「[複数の操作を実行して出力をキューに登録する](#BKMK_RunMultipleOperations)」の変更を行って再入を処理します。</span><span class="sxs-lookup"><span data-stu-id="425f8-240">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="425f8-241">関連項目</span><span class="sxs-lookup"><span data-stu-id="425f8-241">See also</span></span>

- [<span data-ttu-id="425f8-242">チュートリアル: Async と Await を使用した Web へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="425f8-242">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="425f8-243">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="425f8-243">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
