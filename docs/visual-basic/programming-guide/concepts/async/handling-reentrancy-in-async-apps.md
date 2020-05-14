---
title: 非同期アプリにおける再入の処理
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 110298a2ca937dbf39c94cfe9df29afb2e76a91c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021499"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="9d2fa-102">非同期アプリにおける再入の処理 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d2fa-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>

<span data-ttu-id="9d2fa-103">非同期コードをアプリに含める場合は、再入を考慮し、場合によっては回避することをお勧めします。これは、完了前に非同期操作の再入力を参照します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="9d2fa-104">再入の可能性を特定して処理しないと、予期しない結果が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>

> [!NOTE]
> <span data-ttu-id="9d2fa-105">この例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-105">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

> [!NOTE]
> <span data-ttu-id="9d2fa-106">現在、アプリ開発で使用する最小バージョンは、トランスポート層セキュリティ (TLS) バージョン 1.2 です。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-106">Transport Layer Security (TLS) version 1.2 is now the minimum version to use in your app development.</span></span> <span data-ttu-id="9d2fa-107">ご利用のアプリがバージョン 4.7 より前の .NET Framework を対象としている場合は、「[.NET Framework でのトランスポート層セキュリティ (TLS) のベスト プラクティス](../../../../framework/network-programming/tls.md)」の記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-107">If your app targets a .NET Framework version earlier than 4.7, refer to the following article for [Transport Layer Security (TLS) best practices with the .NET Framework](../../../../framework/network-programming/tls.md).</span></span>

## <a name="recognizing-reentrancy"></a><a name="BKMK_RecognizingReentrancy"></a><span data-ttu-id="9d2fa-108">再入を認識する</span><span class="sxs-lookup"><span data-stu-id="9d2fa-108">Recognizing Reentrancy</span></span>

<span data-ttu-id="9d2fa-109">このトピックの例では、ユーザーが **[Start]** をクリックして非同期アプリを開始します。このアプリは、一連の Web サイトをダウンロードし、ダウンロードされた合計バイト数を計算します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-109">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="9d2fa-110">同期バージョンの例では、ユーザーが何回ボタンをクリックしても同じように応答します。2 回目以降はアプリが実行を完了するまで、UI スレッドはこれらのイベントを無視するからです。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-110">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="9d2fa-111">ただし、非同期アプリでは、UI スレッドは応答し続けるので、完了前に非同期操作を再入力することがあります。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-111">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>

<span data-ttu-id="9d2fa-112">次の例は、ユーザーが 1 度だけ **[Start]** をクリックした場合の出力を示しています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-112">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="9d2fa-113">ダウンロードされた Web サイトの一覧には、各サイトのサイズがバイト単位で表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-113">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="9d2fa-114">合計バイト数は最後に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-114">The total number of bytes appears at the end.</span></span>

```console
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

<span data-ttu-id="9d2fa-115">ただし、ユーザーがボタンを複数回クリックすると、イベント ハンドラーは繰り返し呼び出され、ダウンロード プロセスはそのたびに再入力されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-115">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="9d2fa-116">その結果、複数の非同期操作が同時に実行され、出力は結果をインターリーブするので、合計バイト数がややこしくなります。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-116">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>

```console
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

<span data-ttu-id="9d2fa-117">このトピックの最後にスクロールすると、この出力を生成するコードをレビューできます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-117">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="9d2fa-118">コードを試してみるには、ソリューションをローカル コンピューターにダウンロードにし、WebsiteDownload プロジェクトを実行するか、このトピックの最後にあるコードを使用して独自のプロジェクトを作成します。詳細と手順については、「[例のアプリをレビューして実行する](#BKMD_SettingUpTheExample)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-118">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>

## <a name="handling-reentrancy"></a><a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="9d2fa-119">再入を処理する</span><span class="sxs-lookup"><span data-stu-id="9d2fa-119">Handling Reentrancy</span></span>

<span data-ttu-id="9d2fa-120">再入の処理は、アプリで何を行うかに応じてさまざまな方法で実行できます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-120">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="9d2fa-121">このトピックでは、次の例を紹介します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-121">This topic presents the following examples:</span></span>

- <span data-ttu-id="9d2fa-122">[[Start] ボタンを無効にする](#BKMK_DisableTheStartButton)</span><span class="sxs-lookup"><span data-stu-id="9d2fa-122">[Disable the Start Button](#BKMK_DisableTheStartButton)</span></span>

  <span data-ttu-id="9d2fa-123">処理の実行中、ユーザーが中断できないように **[Start]** ボタンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-123">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>

- [<span data-ttu-id="9d2fa-124">操作を取り消して再開する</span><span class="sxs-lookup"><span data-stu-id="9d2fa-124">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)

  <span data-ttu-id="9d2fa-125">ユーザーが **[Start]** を再度クリックしたときに実行されている処理を取り消し、最後に要求された処理を続行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-125">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>

- [<span data-ttu-id="9d2fa-126">複数の操作を実行して出力をキューに登録する</span><span class="sxs-lookup"><span data-stu-id="9d2fa-126">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)

  <span data-ttu-id="9d2fa-127">要求されたすべての処理を非同期的に実行できるようにします。ただし、各処理の結果が順番にまとめて表示されるように出力を調整します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-127">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>

### <a name="disable-the-start-button"></a><a name="BKMK_DisableTheStartButton"></a><span data-ttu-id="9d2fa-128">[Start] ボタンを無効にする</span><span class="sxs-lookup"><span data-stu-id="9d2fa-128">Disable the Start Button</span></span>

<span data-ttu-id="9d2fa-129">処理の実行中に **[Start]** ボタンを利用できないようにするには、`StartButton_Click` イベント ハンドラーの上部にあるボタンを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-129">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="9d2fa-130">処理が完了しユーザーが再度アプリを実行できるようになったら、`Finally` ブロック内からこのボタンを再度有効にできます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-130">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>

<span data-ttu-id="9d2fa-131">次のコードはこの変更を示しています。変更の部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-131">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="9d2fa-132">この変更をこのトピックの最後にあるコードに追加できます。また、完成したアプリを「[Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)」 (非同期の例: .NET デスクトップ アプリでの再入) からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-132">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="9d2fa-133">プロジェクト名は DisableStartButton です。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-133">The project name is DisableStartButton.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' This line is commented out to make the results clearer in the output.
    'ResultsTextBox.Text = ""

    ' ***Disable the Start button until the downloads are complete.
    StartButton.IsEnabled = False

    Try
        Await AccessTheWebAsync()

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    ' ***Enable the Start button in case you want to run the program again.
    Finally
        StartButton.IsEnabled = True

    End Try
End Sub
```

<span data-ttu-id="9d2fa-134">変更の結果、`AccessTheWebAsync` が Web サイトをダウンロードしている間は、ボタンが応答しないので、プロセスを再入力できません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-134">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>

### <a name="cancel-and-restart-the-operation"></a><a name="BKMK_CancelAndRestart"></a><span data-ttu-id="9d2fa-135">操作を取り消して再開する</span><span class="sxs-lookup"><span data-stu-id="9d2fa-135">Cancel and Restart the Operation</span></span>

<span data-ttu-id="9d2fa-136">**[Start]** ボタンを無効にせず、有効の状態を保持できますが、ユーザーがボタンを再度クリックしたときに、実行中の処理を取り消し、最後に開始された処理を続行できます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-136">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>

<span data-ttu-id="9d2fa-137">取り消しの詳細については、「[非同期アプリケーションの微調整 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-137">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>

<span data-ttu-id="9d2fa-138">このシナリオを設定するには、「[例のアプリをレビューして実行する](#BKMD_SettingUpTheExample)」に用意されている基本コードを次のように変更します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-138">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="9d2fa-139">また、完成したアプリを「[Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)」 (非同期の例: .NET デスクトップ アプリでの再入) からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-139">You can also download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="9d2fa-140">このプロジェクトの名前は CancelAndRestart です。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-140">The name of this project is CancelAndRestart.</span></span>

1. <span data-ttu-id="9d2fa-141">すべてのメソッドのスコープである <xref:System.Threading.CancellationTokenSource> 変数、`cts` を宣言します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-141">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>

    ```vb
    Class MainWindow // Or Class MainPage

        ' *** Declare a System.Threading.CancellationTokenSource.
        Dim cts As CancellationTokenSource
    ```

2. <span data-ttu-id="9d2fa-142">`StartButton_Click` で、処理が既に実行されているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-142">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="9d2fa-143">`cts` の値が `Nothing` の場合、アクティブな操作はまだありません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-143">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="9d2fa-144">値が `Nothing` 以外の場合は、実行中の処理が取り消されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-144">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>

    ```vb
    ' *** If a download process is already underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If
    ```

3. <span data-ttu-id="9d2fa-145">`cts` に、現在のプロセスを表す別の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-145">Set `cts` to a different value that represents the current process.</span></span>

    ```vb
    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS
    ```

4. <span data-ttu-id="9d2fa-146">`StartButton_Click` の最後で現在のプロセスが完了します。したがって、`cts` の値を `Nothing` に戻します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-146">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>

    ```vb
    ' *** When the process completes, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
    ```

<span data-ttu-id="9d2fa-147">次のコードは、`StartButton_Click` のすべての変更を示しています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-147">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="9d2fa-148">追加部分はアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-148">The additions are marked with asterisks.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)

    ' This line is commented out to make the results clearer.
    'ResultsTextBox.Text = ""

    ' *** If a download process is underway, cancel it.
    If cts IsNot Nothing Then
        cts.Cancel()
    End If

    ' *** Now set cts to cancel the current process if the button is chosen again.
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()
    cts = newCTS

    Try
        ' *** Send a token to carry the message if the operation is canceled.
        Await AccessTheWebAsync(cts.Token)

    Catch ex As OperationCanceledException
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."
    End Try

    ' *** When the process is complete, signal that another process can proceed.
    If cts Is newCTS Then
        cts = Nothing
    End If
End Sub
```

<span data-ttu-id="9d2fa-149">`AccessTheWebAsync` で、次の変更を行います。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-149">In `AccessTheWebAsync`, make the following changes.</span></span>

- <span data-ttu-id="9d2fa-150">`StartButton_Click` からキャンセル トークンを受け取るためのパラメーターを追加します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-150">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>

- <span data-ttu-id="9d2fa-151"><xref:System.Net.Http.HttpClient.GetAsync%2A> メソッドを使用して Web サイトをダウンロードします。これは `GetAsync` が <xref:System.Threading.CancellationToken> 引数を受け取るからです。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-151">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>

- <span data-ttu-id="9d2fa-152">`DisplayResults` を呼び出してダウンロードした各 Web サイトの結果を表示する前に、`ct` で、現在の処理が取り消されていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-152">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>

 <span data-ttu-id="9d2fa-153">次のコードはこの変更を示しています。変更の部分にはアスタリスクが付いています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-153">The following code shows these changes, which are marked with asterisks.</span></span>

```vb
' *** Provide a parameter for the CancellationToken from StartButton_Click.
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task

    ' Declare an HttpClient object.
    Dim client = New HttpClient()

    ' Make a list of web addresses.
    Dim urlList As List(Of String) = SetUpURLList()

    Dim total = 0
    Dim position = 0

    For Each url In urlList
        ' *** Use the HttpClient.GetAsync method because it accepts a
        ' cancellation token.
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)

        ' *** Retrieve the website contents from the HttpResponseMessage.
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()

        ' *** Check for cancellations before displaying information about the
        ' latest site.
        ct.ThrowIfCancellationRequested()

        position += 1
        DisplayResults(url, urlContents, position)

        ' Update the total.
        total += urlContents.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

<span data-ttu-id="9d2fa-154">このアプリの実行中に複数回 **[Start]** ボタンをクリックすると、次の出力のような結果が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-154">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output:</span></span>

```console
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

<span data-ttu-id="9d2fa-155">部分的なリストを削除するには、`StartButton_Click` コードの先頭行のコメントを解除して、ユーザーが操作を再開するたびに、テキスト ボックスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-155">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>

### <a name="run-multiple-operations-and-queue-the-output"></a><a name="BKMK_RunMultipleOperations"></a><span data-ttu-id="9d2fa-156">複数の操作を実行して出力をキューに登録する</span><span class="sxs-lookup"><span data-stu-id="9d2fa-156">Run Multiple Operations and Queue the Output</span></span>

<span data-ttu-id="9d2fa-157">この 3 番目の例は、ユーザーが **[Start]** ボタンをクリックするたびに非同期操作が開始され、すべての操作が完了まで実行されるという点で最も複雑です。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-157">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="9d2fa-158">要求されたすべての操作によって Web サイトがリストから非同期的にダウンロードされますが、操作からの出力は順次表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-158">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="9d2fa-159">つまり、「[再入を認識する](#BKMK_RecognizingReentrancy)」の出力に示されているように、実際のダウンロード アクティビティはインターリーブされますが、各グループの結果のリストは個別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-159">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>

<span data-ttu-id="9d2fa-160">操作は、表示プロセスのゲートキーパーとして機能するグローバル <xref:System.Threading.Tasks.Task>、`pendingWork` を共有します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-160">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>

<span data-ttu-id="9d2fa-161">この例を実行するには、変更を「[アプリケーションをビルドする](#BKMK_BuildingTheApp)」のコードに貼り付けます。また、「[アプリをダウンロードする](#BKMK_DownloadingTheApp)」の手順に従って、サンプルをダウンロードし、QueueResults プロジェクトを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-161">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>

<span data-ttu-id="9d2fa-162">次の出力は、ユーザーが 1 度だけ **[Start]** ボタンをクリックした場合の結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-162">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="9d2fa-163">文字ラベル A は、 **[Start]** ボタンが最初にクリックされた結果であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-163">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="9d2fa-164">数字は、ダウンロード対象の一覧における URL の順序を示しています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-164">The numbers show the order of the URLs in the list of download targets.</span></span>

```console
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

<span data-ttu-id="9d2fa-165">ユーザーが **[Start]** ボタンを 3 回クリックすると、アプリでは次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-165">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="9d2fa-166">先頭にシャープ記号 (#) が付いている情報行は、アプリケーションの進行状況を追跡します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-166">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>

```console
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

<span data-ttu-id="9d2fa-167">グループ B とグループ C は、グループ A が終了する前に開始します。ただし、各グループの出力は個別に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-167">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="9d2fa-168">グループ A のすべての出力が最初に表示され、その後にグループ B のすべての出力が続き、さらにグループ C のすべての出力が表示されます。グループは必ず順番に表示され、グループごとに、個別の Web サイトに関する情報が URL 一覧の URL の順番で表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-168">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>

<span data-ttu-id="9d2fa-169">ただし、ダウンロードが実際に行われる順序は予測できません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-169">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="9d2fa-170">複数のグループが開始されたら、そのグループが生成するダウンロード タスクはすべてのアクティブです。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-170">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="9d2fa-171">B-1 の前に A-1 がダウンロードされる、また、A-2 の前に A-1 がダウンロードされると仮定することはできません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-171">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>

#### <a name="global-definitions"></a><span data-ttu-id="9d2fa-172">グローバル定義</span><span class="sxs-lookup"><span data-stu-id="9d2fa-172">Global Definitions</span></span>

<span data-ttu-id="9d2fa-173">サンプル コードには、すべてのメソッドから参照できる次の 2 つのグローバル宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-173">The sample code contains the following two global declarations that are visible from all methods.</span></span>

```vb
Class MainWindow    ' Class MainPage in Windows Store app.

    ' ***Declare the following variables where all methods can access them.
    Private pendingWork As Task = Nothing
    Private group As Char = ChrW(AscW("A") - 1)
```

<span data-ttu-id="9d2fa-174">`Task` 変数、`pendingWork` は、表示プロセスを監視し、あるグループが別のグループの表示操作を中断しないようにします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-174">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="9d2fa-175">文字変数 `group` は、異なるグループからの出力にラベルを付け、予想された順序で結果が表示されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-175">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>

#### <a name="the-click-event-handler"></a><span data-ttu-id="9d2fa-176">Click イベント ハンドラー</span><span class="sxs-lookup"><span data-stu-id="9d2fa-176">The Click Event Handler</span></span>

<span data-ttu-id="9d2fa-177">イベント ハンドラー `StartButton_Click` は、ユーザーが **[Start]** ボタンを選択するたびに、グループ文字をインクリメントします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-177">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="9d2fa-178">ハンドラーは `AccessTheWebAsync` を呼び出して、ダウンロード操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-178">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>

```vb
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
    ' ***Verify that each group's results are displayed together, and that
    ' the groups display in order, by marking each group with a letter.
    group = ChrW(AscW(group) + 1)
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)

    Try
        ' *** Pass the group value to AccessTheWebAsync.
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)

        ' The following line verifies a successful return from the download and
        ' display procedures.
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)

    Catch ex As Exception
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."

    End Try
End Sub
```

#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="9d2fa-179">AccessTheWebAsync メソッド</span><span class="sxs-lookup"><span data-stu-id="9d2fa-179">The AccessTheWebAsync Method</span></span>

<span data-ttu-id="9d2fa-180">この例では、`AccessTheWebAsync` を 2 つのメソッドに分割します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-180">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="9d2fa-181">最初のメソッド、`AccessTheWebAsync` は、グループのすべてのダウンロード タスクを開始し、`pendingWork` を設定して表示プロセスを制御します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-181">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="9d2fa-182">このメソッドは、統合言語クエリ (LINQ クエリ) と <xref:System.Linq.Enumerable.ToArray%2A> を使用して、すべてのダウンロードを同時に開始します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-182">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>

<span data-ttu-id="9d2fa-183">その後、`AccessTheWebAsync` は、`FinishOneGroupAsync` を呼び出して各ダウンロードが完了するまで待機し、その長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-183">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>

<span data-ttu-id="9d2fa-184">`FinishOneGroupAsync` は、`pendingWork` の `AccessTheWebAsync` に割り当てられたタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-184">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="9d2fa-185">この値は、タスクが完了する前に、別の操作によって操作が中断されないようにします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-185">That value prevents interruption by another operation before the task is complete.</span></span>

```vb
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)

    Dim client = New HttpClient()

    ' Make a list of the web addresses to download.
    Dim urlList As List(Of String) = SetUpURLList()

    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.
    Dim getContentTasks As Task(Of Byte())() =
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()

    ' ***Call the method that awaits the downloads and displays the results.
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)

    ResultsTextBox.Text &=
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)

    ' ***This task is complete when a group has finished downloading and displaying.
    Await pendingWork

    ' You can do other work here or just return.
    Return grp
End Function
```

#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="9d2fa-186">FinishOneGroupAsync メソッド</span><span class="sxs-lookup"><span data-stu-id="9d2fa-186">The FinishOneGroupAsync Method</span></span>

<span data-ttu-id="9d2fa-187">このメソッドは、グループのダウンロード タスクを循環参照し、それぞれを待機してから、ダウンロードされた Web サイトの長さを表示して、その長さを合計に追加します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-187">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>

<span data-ttu-id="9d2fa-188">`FinishOneGroupAsync` の最初のステートメントは、`pendingWork` を使用して、メソッドを入力することが、表示プロセスの操作または待機中の操作の妨げにならないようにします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-188">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="9d2fa-189">これらの操作が進行中の場合、入力操作は順番を待つ必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-189">If such an operation is in progress, the entering operation must wait its turn.</span></span>

```vb
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task

    ' Wait for the previous group to finish displaying results.
    If pendingWork IsNot Nothing Then
        Await pendingWork
    End If

    Dim total = 0

    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.
    For i As Integer = 0 To contentTasks.Length - 1
        ' Await the download of a particular URL, and then display the URL and
        ' its length.
        Dim content As Byte() = Await contentTasks(i)
        DisplayResults(urls(i), content, i, grp)
        total += content.Length
    Next

    ' Display the total count for all of the websites.
    ResultsTextBox.Text &=
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
End Function
```

<span data-ttu-id="9d2fa-190">この例を実行するには、変更を「[アプリケーションをビルドする](#BKMK_BuildingTheApp)」のコードに貼り付けます。また、「[アプリをダウンロードする](#BKMK_DownloadingTheApp)」の手順に従って、サンプルをダウンロードし、QueueResults プロジェクトを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-190">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>

#### <a name="points-of-interest"></a><span data-ttu-id="9d2fa-191">目的のポイント</span><span class="sxs-lookup"><span data-stu-id="9d2fa-191">Points of Interest</span></span>

<span data-ttu-id="9d2fa-192">出力で先頭にシャープ記号 (#) が付いている情報行は、この例の動作を明確に示しています。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-192">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>

<span data-ttu-id="9d2fa-193">出力のパターンを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-193">The output shows the following patterns.</span></span>

- <span data-ttu-id="9d2fa-194">前のグループが出力を表示していても、グループを開始できます。その際、前のグループの出力の表示は中断されません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-194">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>

  ```console
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

- <span data-ttu-id="9d2fa-195">最初に開始したグループ A についてのみ、`FinishOneGroupAsync` 開始時の、`pendingWork` タスクは `Nothing` になります。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-195">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="9d2fa-196">`FinishOneGroupAsync` に達したとき、グループ A はまだ await 式を完了していません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-196">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="9d2fa-197">したがって、コントロールは `AccessTheWebAsync` に戻っておらず、`pendingWork` への最初の割り当ては発生していません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-197">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>

- <span data-ttu-id="9d2fa-198">次の 2 行は、出力に必ず同時に表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-198">The following two lines always appear together in the output.</span></span> <span data-ttu-id="9d2fa-199">`StartButton_Click` のグループ操作が開始してから、グループのタスクが `pendingWork` に割り当てられるまでの間、コードが中断されることは決してありません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-199">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>

  ```console
  #Starting group B.
  #Task assigned for group B. Download tasks are active.
  ```

  <span data-ttu-id="9d2fa-200">グループが `StartButton_Click` に移行したら、`FinishOneGroupAsync` に移行するまでは、await 式は完了しません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-200">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="9d2fa-201">したがって、コード セグメントの途中で、他の操作がコントロールを得ることはありません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-201">Therefore, no other operation can gain control during that segment of code.</span></span>

## <a name="reviewing-and-running-the-example-app"></a><a name="BKMD_SettingUpTheExample"></a><span data-ttu-id="9d2fa-202">例のアプリをレビューして実行する</span><span class="sxs-lookup"><span data-stu-id="9d2fa-202">Reviewing and Running the Example App</span></span>

<span data-ttu-id="9d2fa-203">サンプル アプリをさらに詳しく理解するには、そのアプリをダウンロードし、ご自身でビルドしてみてください。また、このトピックの最後にあるコードをレビューすることもできます。アプリを実装する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-203">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>

> [!NOTE]
> <span data-ttu-id="9d2fa-204">Windows Presentation Foundation (WPF) デスクトップ アプリとして例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-204">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="downloading-the-app"></a><a name="BKMK_DownloadingTheApp"></a><span data-ttu-id="9d2fa-205">アプリをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="9d2fa-205">Downloading the App</span></span>

1. <span data-ttu-id="9d2fa-206">圧縮ファイルを「[Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)」 (非同期の例: .NET デスクトップ アプリでの再入) からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-206">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>

2. <span data-ttu-id="9d2fa-207">ダウンロードしたファイルを圧縮解除し、Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-207">Decompress the file that you downloaded, and then start Visual Studio.</span></span>

3. <span data-ttu-id="9d2fa-208">メニュー バーで **[ファイル]** 、 **[開く]** 、 **[プロジェクト/ソリューション]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-208">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>

4. <span data-ttu-id="9d2fa-209">圧縮解除したサンプル コードが含まれるフォルダーに移動し、ソリューション (.sln) ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-209">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>

5. <span data-ttu-id="9d2fa-210">**ソリューション エクスプローラー**で、実行するプロジェクトのショートカット メニューを開き、 **[スタートアップ プロジェクトに設定]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-210">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>

6. <span data-ttu-id="9d2fa-211">Ctrl キーを押しながら F5 キーを押してプロジェクトをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-211">Choose the CTRL+F5 keys to build and run the project.</span></span>

### <a name="building-the-app"></a><a name="BKMK_BuildingTheApp"></a><span data-ttu-id="9d2fa-212">アプリケーションをビルドする</span><span class="sxs-lookup"><span data-stu-id="9d2fa-212">Building the App</span></span>

<span data-ttu-id="9d2fa-213">次のセクションでは、WPF アプリとして例をビルドするコードを示します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-213">The following section provides the code to build the example as a WPF app.</span></span>

##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="9d2fa-214">WPF アプリをビルドするには</span><span class="sxs-lookup"><span data-stu-id="9d2fa-214">To build a WPF app</span></span>

1. <span data-ttu-id="9d2fa-215">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-215">Start Visual Studio.</span></span>

2. <span data-ttu-id="9d2fa-216">メニュー バーで、 **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-216">On the menu bar, choose **File**, **New**, **Project**.</span></span>

     <span data-ttu-id="9d2fa-217">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-217">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="9d2fa-218">**[インストールされたテンプレート]** ペインで、 **[Visual Basic]** を展開し、 **[Windows]** を展開します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-218">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>

4. <span data-ttu-id="9d2fa-219">プロジェクトの種類の一覧の **[WPF アプリケーション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-219">In the list of project types, choose **WPF Application**.</span></span>

5. <span data-ttu-id="9d2fa-220">プロジェクトに `WebsiteDownloadWPF` という名前を指定し、4.6 以降の .NET Framework のバージョンを選択して、 **[OK]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-220">Name the project `WebsiteDownloadWPF`, choose .NET Framework version of 4.6 or higher and then click the **OK** button.</span></span>

     <span data-ttu-id="9d2fa-221">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-221">The new project appears in **Solution Explorer**.</span></span>

6. <span data-ttu-id="9d2fa-222">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-222">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="9d2fa-223">タブが表示されない場合は、**ソリューション エクスプローラー**で MainWindow.xaml のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-223">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

7. <span data-ttu-id="9d2fa-224">MainWindow.xaml の **XAML** ビューで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-224">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```xaml
    <Window x:Class="MainWindow"
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

     <span data-ttu-id="9d2fa-225">テキスト ボックスとボタンを含む簡単なウィンドウが、MainWindow.xaml の**デザイン** ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-225">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

8. <span data-ttu-id="9d2fa-226">**ソリューション エクスプローラー**で **[参照]** を右クリックし、 **[参照の追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-226">In **Solution Explorer**, right-click on **References** and select **Add Reference**.</span></span>

     <span data-ttu-id="9d2fa-227">まだ選択されていない場合は、<xref:System.Net.Http> の参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-227">Add a reference for <xref:System.Net.Http>, if it is not selected already.</span></span>

9. <span data-ttu-id="9d2fa-228">**ソリューション エクスプローラー**で MainWindow.xaml.vb のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-228">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

10. <span data-ttu-id="9d2fa-229">MainWindow.xaml.vb のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-229">In MainWindow.xaml.vb , replace the code with the following code.</span></span>

    ```vb
    ' Add the following Imports statements, and add a reference for System.Net.Http.
    Imports System.Net.Http
    Imports System.Threading

    Class MainWindow

        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)
            System.Net.ServicePointManager.SecurityProtocol = System.Net.ServicePointManager.SecurityProtocol Or System.Net.SecurityProtocolType.Tls12

            ' This line is commented out to make the results clearer in the output.
            'ResultsTextBox.Text = ""

            Try
                Await AccessTheWebAsync()

            Catch ex As Exception
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."

            End Try
        End Sub

        Private Async Function AccessTheWebAsync() As Task

            ' Declare an HttpClient object.
            Dim client = New HttpClient()

            ' Make a list of web addresses.
            Dim urlList As List(Of String) = SetUpURLList()

            Dim total = 0
            Dim position = 0

            For Each url In urlList
                ' GetByteArrayAsync returns a task. At completion, the task
                ' produces a byte array.
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

                position += 1
                DisplayResults(url, urlContents, position)

                ' Update the total.
                total += urlContents.Length
            Next

            ' Display the total count for all of the websites.
            ResultsTextBox.Text &=
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)
        End Function

        Private Function SetUpURLList() As List(Of String)
            Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/hh191443.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/jj155761.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/hh524395.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
            Return urls
        End Function

        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)
            ' Display the length of each website. The string format is designed
            ' to be used with a monospaced font, such as Lucida Console or
            ' Global Monospace.

            ' Strip off the "http:'".
            Dim displayURL = url.Replace("https://", "")
            ' Display position in the URL list, the URL, and the number of bytes.
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)
        End Sub
    End Class
    ```

11. <span data-ttu-id="9d2fa-230">Ctrl キーを押しながら F5 キーを押してプログラムを実行し、 **[Start]** ボタンを複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-230">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>

12. <span data-ttu-id="9d2fa-231">「[[Start] ボタンを無効にする](#BKMK_DisableTheStartButton)」、「[操作を取り消して再開する](#BKMK_CancelAndRestart)」、または「[複数の操作を実行して出力をキューに登録する](#BKMK_RunMultipleOperations)」の変更を行って再入を処理します。</span><span class="sxs-lookup"><span data-stu-id="9d2fa-231">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d2fa-232">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d2fa-232">See also</span></span>

- [<span data-ttu-id="9d2fa-233">チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d2fa-233">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="9d2fa-234">Async および Await を使用した非同期プログラミング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d2fa-234">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
