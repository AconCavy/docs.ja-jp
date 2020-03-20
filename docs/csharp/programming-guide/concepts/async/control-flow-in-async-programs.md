---
title: 非同期プログラムにおける制御フロー (C#)
ms.date: 07/20/2015
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
ms.openlocfilehash: 99f80a86f14179c5f270064a9f96e35f8611ef13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204446"
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="ae95a-102">非同期プログラムにおける制御フロー (C#)</span><span class="sxs-lookup"><span data-stu-id="ae95a-102">Control flow in async programs (C#)</span></span>

<span data-ttu-id="ae95a-103">`async` キーワードと `await` キーワードを使用すると、非同期のプログラムの作成と保守をより簡単に行えます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="ae95a-104">ただし、プログラムがどのように動作するかを理解しないと、その結果は予想に反するものになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ae95a-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="ae95a-105">このトピックでは、簡単な非同期プログラムによる制御フローをトレースして、制御があるメソッドから別のメソッドに移るタイミングと、その都度転送される情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>

<span data-ttu-id="ae95a-106">一般に、[async (C#)](../../../language-reference/keywords/async.md) 修飾子を使用した非同期コードを含むメソッドをマークします。</span><span class="sxs-lookup"><span data-stu-id="ae95a-106">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="ae95a-107">async 修飾子でマークされたメソッドでは、[await (C#)](../../../language-reference/operators/await.md) 演算子を使用して、呼び出される非同期処理の終了をメソッドが待機する場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-107">In a method that's marked with an async modifier, you can use an [await (C#)](../../../language-reference/operators/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="ae95a-108">詳細については、「[Async および Await を使用した非同期プログラミング (C#)](./index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae95a-108">For more information, see [Asynchronous Programming with async and await (C#)](./index.md).</span></span>

<span data-ttu-id="ae95a-109">次の例では、非同期メソッドを使用して、指定した Web サイトのコンテンツを文字列としてダウンロードし、その文字列の長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-109">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="ae95a-110">この例には、次の 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-110">The example contains the following two methods.</span></span>

- <span data-ttu-id="ae95a-111">`startButton_Click` を呼び出して結果を表示する `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="ae95a-111">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>

- <span data-ttu-id="ae95a-112">Web サイトのコンテンツを文字列としてダウンロードして、その文字列の長さを返す `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="ae95a-112">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="ae95a-113">`AccessTheWebAsync` は、非同期 <xref:System.Net.Http.HttpClient> メソッドである <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> を使用してコンテンツをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="ae95a-113">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>

<span data-ttu-id="ae95a-114">番号付き表示行はプログラム全体で重要なポイントを示し、プログラムがどのように実行され、マークされている各ポイントで何が発生するかを理解するために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-114">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="ae95a-115">表示行には「1」から「6」までのラベルが付けられています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-115">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="ae95a-116">このラベルは、プログラムがこれらのコード行に到達する順序を表します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-116">The labels represent the order in which the program reaches these lines of code.</span></span>

<span data-ttu-id="ae95a-117">次のコードは、プログラムの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-117">The following code shows an outline of the program.</span></span>

```csharp
public partial class MainWindow : Window
{
    // . . .
    private async void startButton_Click(object sender, RoutedEventArgs e)
    {
        // ONE
        Task<int> getLengthTask = AccessTheWebAsync();

        // FOUR
        int contentLength = await getLengthTask;

        // SIX
        resultsTextBox.Text +=
            $"\r\nLength of the downloaded string: {contentLength}.\r\n";
    }

    async Task<int> AccessTheWebAsync()
    {
        // TWO
        HttpClient client = new HttpClient();
        Task<string> getStringTask =
            client.GetStringAsync("https://msdn.microsoft.com");

        // THREE
        string urlContents = await getStringTask;

        // FIVE
        return urlContents.Length;
    }
}
```

<span data-ttu-id="ae95a-118">「1」から「6」までのそれぞれのラベルの位置は、プログラムの現在の状態に関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-118">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="ae95a-119">次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-119">The following output is produced:</span></span>

```output
ONE:   Entering startButton_Click.
           Calling AccessTheWebAsync.

TWO:   Entering AccessTheWebAsync.
           Calling HttpClient.GetStringAsync.

THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.

FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.

FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.

SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.

Length of the downloaded string: 33946.
```

## <a name="set-up-the-program"></a><span data-ttu-id="ae95a-120">プログラムをセットアップする</span><span class="sxs-lookup"><span data-stu-id="ae95a-120">Set up the program</span></span>

<span data-ttu-id="ae95a-121">このトピックで使用するコードは、MSDN からダウンロードするか、または自分でビルドできます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-121">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>

> [!NOTE]
> <span data-ttu-id="ae95a-122">この例を実行するには、Visual Studio 2012 以降と .NET Framework 4.5 以降が、コンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae95a-122">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

### <a name="download-the-program"></a><span data-ttu-id="ae95a-123">プログラムをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="ae95a-123">Download the program</span></span>

<span data-ttu-id="ae95a-124">このトピックのアプリケーションは、「[非同期のサンプル:非同期プログラムにおける制御フロー](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)」からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-124">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="ae95a-125">次の手順でプログラムを開いて実行します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-125">The following steps open and run the program.</span></span>

1. <span data-ttu-id="ae95a-126">ダウンロードしたファイルを解凍し、Visual Studio を開始します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-126">Unzip the downloaded file, and then start Visual Studio.</span></span>

2. <span data-ttu-id="ae95a-127">メニュー バーで、 **[ファイル]**  >  **[開く]**  >  **[プロジェクト/ソリューション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-127">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3. <span data-ttu-id="ae95a-128">解凍したサンプル コードが含まれるフォルダーに移動し、ソリューション (.sln) ファイルを開き、**F5** キーを押してプロジェクトをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-128">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the **F5** key to build and run the project.</span></span>

### <a name="create-the-program-yourself"></a><span data-ttu-id="ae95a-129">プログラムを自分で作成する</span><span class="sxs-lookup"><span data-stu-id="ae95a-129">Create the program Yourself</span></span>

<span data-ttu-id="ae95a-130">次の Windows Presentation Foundation (WPF) プロジェクトには、このトピックのコード例が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-130">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>

<span data-ttu-id="ae95a-131">このプロジェクトを実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-131">To run the project, perform the following steps:</span></span>

1. <span data-ttu-id="ae95a-132">Visual Studio を起動します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-132">Start Visual Studio.</span></span>

2. <span data-ttu-id="ae95a-133">メニュー バーで、 **[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-133">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="ae95a-134">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-134">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="ae95a-135">**[インストール済み]**  >  **[Visual C#]**  >  **[Windows Desktop]** カテゴリを選択し、プロジェクト テンプレートの一覧から **[WPF アプリ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-135">Choose the **Installed** > **Visual C#** > **Windows Desktop** category, and then choose **WPF App** from the list of project templates.</span></span>

4. <span data-ttu-id="ae95a-136">プロジェクトの名前として「`AsyncTracer`」と入力し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae95a-136">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>

     <span data-ttu-id="ae95a-137">**ソリューション エクスプローラー**に新しいプロジェクトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-137">The new project appears in **Solution Explorer**.</span></span>

5. <span data-ttu-id="ae95a-138">Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="ae95a-138">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

     <span data-ttu-id="ae95a-139">タブが表示されない場合は、**ソリューション エクスプローラー**で MainWindow.xaml のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-139">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>

6. <span data-ttu-id="ae95a-140">MainWindow.xaml の **XAML** ビューで、コードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-140">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>

    ```csharp
    <Window
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"
            Title="Control Flow Trace" Height="350" Width="592">
        <Grid>
            <Button x:Name="startButton" Content="Start
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>
        </Grid>
    </Window>
    ```

     <span data-ttu-id="ae95a-141">テキスト ボックスとボタンを含む簡単なウィンドウが、MainWindow.xaml の**デザイン** ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-141">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>

7. <span data-ttu-id="ae95a-142"><xref:System.Net.Http> への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-142">Add a reference for <xref:System.Net.Http>.</span></span>

8. <span data-ttu-id="ae95a-143">**ソリューション エクスプローラー**で MainWindow.xaml.cs のショートカット メニューを開き、 **[コードの表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-143">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

9. <span data-ttu-id="ae95a-144">MainWindow.xaml.cs のコードを次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-144">In MainWindow.xaml.cs, replace the code with the following code.</span></span>

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

    // Add a using directive and a reference for System.Net.Http;
    using System.Net.Http;

    namespace AsyncTracer
    {
        public partial class MainWindow : Window
        {
            public MainWindow()
            {
                InitializeComponent();
            }

            private async void startButton_Click(object sender, RoutedEventArgs e)
            {
                // The display lines in the example lead you through the control shifts.
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +
                    "           Calling AccessTheWebAsync.\r\n";

                Task<int> getLengthTask = AccessTheWebAsync();

                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is started.\r\n" +
                    "           About to await getLengthTask -- no caller to return to.\r\n";

                int contentLength = await getLengthTask;

                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +
                    "           Task getLengthTask is finished.\r\n" +
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +
                    "           About to display contentLength and exit.\r\n";

                resultsTextBox.Text +=
                    $"\r\nLength of the downloaded string: {contentLength}.\r\n";
            }

            async Task<int> AccessTheWebAsync()
            {
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";

                // Declare an HttpClient object.
                HttpClient client = new HttpClient();

                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";

                // GetStringAsync returns a Task<string>.
                Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");

                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +
                    "           Task getStringTask is started.";

                // AccessTheWebAsync can continue to work until getStringTask is awaited.

                resultsTextBox.Text +=
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";

                // Retrieve the website contents when task is complete.
                string urlContents = await getStringTask;

                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +
                    "\r\n           Task getStringTask is complete." +
                    "\r\n           Processing the return statement." +
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";

                return urlContents.Length;
            }
        }
    }
    ```

10. <span data-ttu-id="ae95a-145">**F5** キーを押してプログラムを実行し、 **[スタート]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="ae95a-145">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="ae95a-146">次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-146">The following output appears:</span></span>

    ```output
    ONE:   Entering startButton_Click.
               Calling AccessTheWebAsync.

    TWO:   Entering AccessTheWebAsync.
               Calling HttpClient.GetStringAsync.

    THREE: Back in AccessTheWebAsync.
               Task getStringTask is started.
               About to await getStringTask & return a Task<int> to startButton_Click.

    FOUR:  Back in startButton_Click.
               Task getLengthTask is started.
               About to await getLengthTask -- no caller to return to.

    FIVE:  Back in AccessTheWebAsync.
               Task getStringTask is complete.
               Processing the return statement.
               Exiting from AccessTheWebAsync.

    SIX:   Back in startButton_Click.
               Task getLengthTask is finished.
               Result from AccessTheWebAsync is stored in contentLength.
               About to display contentLength and exit.

    Length of the downloaded string: 33946.
    ```

## <a name="trace-the-program"></a><span data-ttu-id="ae95a-147">プログラムをトレースする</span><span class="sxs-lookup"><span data-stu-id="ae95a-147">Trace the program</span></span>

### <a name="steps-one-and-two"></a><span data-ttu-id="ae95a-148">手順 1. および 2.</span><span class="sxs-lookup"><span data-stu-id="ae95a-148">Steps ONE and TWO</span></span>

<span data-ttu-id="ae95a-149">`startButton_Click` が `AccessTheWebAsync` を呼び出し、`AccessTheWebAsync` が非同期 <xref:System.Net.Http.HttpClient> メソッド <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> を呼び出すと、最初の 2 行の表示行がパスをトレースします。</span><span class="sxs-lookup"><span data-stu-id="ae95a-149">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="ae95a-150">次の図は、メソッドからメソッドへの呼び出しを示しています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-150">The following image outlines the calls from method to method.</span></span>

<span data-ttu-id="ae95a-151">![手順 1. および 2.](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="ae95a-151">![Steps ONE and TWO](./media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>

<span data-ttu-id="ae95a-152">`AccessTheWebAsync` と `client.GetStringAsync` の戻り値の型はどちらも <xref:System.Threading.Tasks.Task%601> です。</span><span class="sxs-lookup"><span data-stu-id="ae95a-152">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ae95a-153">`AccessTheWebAsync` では、TResult は整数です。</span><span class="sxs-lookup"><span data-stu-id="ae95a-153">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="ae95a-154">`GetStringAsync` では、TResult は文字列です。</span><span class="sxs-lookup"><span data-stu-id="ae95a-154">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="ae95a-155">非同期メソッドの戻り値の型について詳しくは、「[非同期の戻り値の型 (C#)](./async-return-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae95a-155">For more information about async method return types, see [Async Return Types (C#)](./async-return-types.md).</span></span>

<span data-ttu-id="ae95a-156">タスクを返す非同期のメソッドは、制御が呼び出し元に戻ると、タスク インスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-156">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="ae95a-157">`await` 演算子が呼び出されたメソッドで実行されるか、または呼び出されたメソッドが終了すると、非同期メソッドから呼び出し元に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="ae95a-157">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="ae95a-158">「3」から「6」のラベルの付いた表示行はこのプロセスの部分をトレースします。</span><span class="sxs-lookup"><span data-stu-id="ae95a-158">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>

### <a name="step-three"></a><span data-ttu-id="ae95a-159">手順 3.</span><span class="sxs-lookup"><span data-stu-id="ae95a-159">Step THREE</span></span>

<span data-ttu-id="ae95a-160">`AccessTheWebAsync` で非同期メソッド <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> が呼び出され、ターゲットの Web ページのコンテンツがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-160">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="ae95a-161">`client.GetStringAsync` が制御を返すと、`AccessTheWebAsync` から `client.GetStringAsync` に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="ae95a-161">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>

 <span data-ttu-id="ae95a-162">`client.GetStringAsync` メソッドは、`getStringTask` の `AccessTheWebAsync` 変数に割り当てる文字列のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-162">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ae95a-163">プログラム例の次の行は、`client.GetStringAsync` の呼び出しと割り当てを示しています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-163">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>

```csharp
Task<string> getStringTask = client.GetStringAsync("https://msdn.microsoft.com");
```

 <span data-ttu-id="ae95a-164">このタスクは `client.GetStringAsync` により実際の文字列が最終的に生成される約束と見なすことができます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-164">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="ae95a-165">`AccessTheWebAsync` には `client.GetStringAsync` から約束された文字列に依存しない処理がある場合、その処理は `client.GetStringAsync` を待機している間は、続行できます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-165">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="ae95a-166">この例では、"THREE" のラベルの付いた行の出力は、独立した処理を行う機会を表します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-166">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>

```output
THREE: Back in AccessTheWebAsync.
           Task getStringTask is started.
           About to await getStringTask & return a Task<int> to startButton_Click.
```

 <span data-ttu-id="ae95a-167">次のステートメントは `AccessTheWebAsync` が待機中の場合 `getStringTask` の進行を中断します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-167">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>

```csharp
string urlContents = await getStringTask;
```

 <span data-ttu-id="ae95a-168">次の図は `client.GetStringAsync` から `getStringTask` への割り当てへの制御フロー、および `getStringTask` の作成から await 演算子のアプリケーションへの制御フローを示しています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-168">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>

 <span data-ttu-id="ae95a-169">![手順 3.](./media/asynctrace-three.png "AsyncTrace-Three")</span><span class="sxs-lookup"><span data-stu-id="ae95a-169">![Step THREE](./media/asynctrace-three.png "AsyncTrace-Three")</span></span>

 <span data-ttu-id="ae95a-170">await 式は `AccessTheWebAsync` が制御を返すまで `client.GetStringAsync` を中断します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-170">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="ae95a-171">その間、コントロールは `AccessTheWebAsync` の呼び出し元である `startButton_Click` に戻されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-171">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>

> [!NOTE]
> <span data-ttu-id="ae95a-172">通常、直ちに非同期メソッドへの呼び出しの待機状態となります。</span><span class="sxs-lookup"><span data-stu-id="ae95a-172">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="ae95a-173">たとえば、次の割り当てで、`getStringTask` を作成してそれを待機する前のコードを置き換えることができます: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="ae95a-173">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("https://msdn.microsoft.com");`</span></span>
>
> <span data-ttu-id="ae95a-174">このトピックでは、await 演算子が後で適用され、プログラムでの制御フローを示す出力行を格納します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-174">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>

### <a name="step-four"></a><span data-ttu-id="ae95a-175">手順 4.</span><span class="sxs-lookup"><span data-stu-id="ae95a-175">Step FOUR</span></span>

<span data-ttu-id="ae95a-176">`AccessTheWebAsync` の宣言された戻り値の型は、`Task<int>` です。</span><span class="sxs-lookup"><span data-stu-id="ae95a-176">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="ae95a-177">したがって、`AccessTheWebAsync` が中断されると、`startButton_Click` に整数のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-177">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="ae95a-178">返されたタスクは `getStringTask` ではないことに注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ae95a-178">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="ae95a-179">返されたタスクは、中断されたメソッド `AccessTheWebAsync` での未処理を表す、整数の新しいタスクです。</span><span class="sxs-lookup"><span data-stu-id="ae95a-179">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="ae95a-180">これにより、タスクが完了したときに `AccessTheWebAsync` が整数を生成することが保証されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-180">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>

<span data-ttu-id="ae95a-181">次のステートメントはこのタスクを `getLengthTask` 変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-181">The following statement assigns this task to the `getLengthTask` variable.</span></span>

```csharp
Task<int> getLengthTask = AccessTheWebAsync();
```

 <span data-ttu-id="ae95a-182">`AccessTheWebAsync` と同様に、`startButton_Click` は、非同期タスク (`getLengthTask`) の結果に依存しない処理を、タスクが待機するまで続行できます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-182">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="ae95a-183">次の出力行はその処理を表します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-183">The following output lines represent that work.</span></span>

```output
FOUR:  Back in startButton_Click.
           Task getLengthTask is started.
           About to await getLengthTask -- no caller to return to.
```

 <span data-ttu-id="ae95a-184">`startButton_Click` が待機すると、`getLengthTask` の進行は中断します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-184">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="ae95a-185">次の代入ステートメントは、`startButton_Click` が完了するまで `AccessTheWebAsync` を中断します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-185">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="ae95a-186">次の図で、矢印は `AccessTheWebAsync` の await 式から `getLengthTask` への値の割り当てへの制御のフロー、および `startButton_Click` が待機するまでの `getLengthTask` の通常の処理を示しています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-186">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>

 <span data-ttu-id="ae95a-187">![手順 4.](./media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="ae95a-187">![Step FOUR](./media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>

### <a name="step-five"></a><span data-ttu-id="ae95a-188">手順 5.</span><span class="sxs-lookup"><span data-stu-id="ae95a-188">Step FIVE</span></span>

<span data-ttu-id="ae95a-189">`client.GetStringAsync` が終了を通知すると、`AccessTheWebAsync` の処理は中断から解放され、await ステートメントを越えて続行できます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-189">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="ae95a-190">次の出力行は、処理の再開を表します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-190">The following lines of output represent the resumption of processing.</span></span>

```output
FIVE:  Back in AccessTheWebAsync.
           Task getStringTask is complete.
           Processing the return statement.
           Exiting from AccessTheWebAsync.
```

 <span data-ttu-id="ae95a-191">return ステートメントのオペランド `urlContents.Length` は `AccessTheWebAsync` が返すタスクに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-191">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="ae95a-192">await 式はその値を `getLengthTask` の `startButton_Click` から取得します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-192">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>

 <span data-ttu-id="ae95a-193">次の図は、`client.GetStringAsync` (および `getStringTask`) が完了した後の制御の移動を示します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-193">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>

 <span data-ttu-id="ae95a-194">![手順 5.](./media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="ae95a-194">![Step FIVE](./media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>

 <span data-ttu-id="ae95a-195">`AccessTheWebAsync` は完了するまで実行され、完了を待機していた `startButton_Click` に制御が戻ります。</span><span class="sxs-lookup"><span data-stu-id="ae95a-195">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>

### <a name="step-six"></a><span data-ttu-id="ae95a-196">手順 6.</span><span class="sxs-lookup"><span data-stu-id="ae95a-196">Step SIX</span></span>

<span data-ttu-id="ae95a-197">`AccessTheWebAsync` が終了を通知すると、処理は `startButton_Async` の await ステートメントを越えて続行できます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-197">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="ae95a-198">実際、プログラムはそれ以上行うことがありません。</span><span class="sxs-lookup"><span data-stu-id="ae95a-198">In fact, the program has nothing more to do.</span></span>

<span data-ttu-id="ae95a-199">次の出力行は、`startButton_Async` の処理の再開を表します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-199">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>

```output
SIX:   Back in startButton_Click.
           Task getLengthTask is finished.
           Result from AccessTheWebAsync is stored in contentLength.
           About to display contentLength and exit.
```

 <span data-ttu-id="ae95a-200">await 式は `getLengthTask` から `AccessTheWebAsync` の return ステートメントのオペランドである整数値を取得します。</span><span class="sxs-lookup"><span data-stu-id="ae95a-200">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="ae95a-201">次のステートメントはその値を `contentLength` 変数に割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ae95a-201">The following statement assigns that value to the `contentLength` variable.</span></span>

```csharp
int contentLength = await getLengthTask;
```

 <span data-ttu-id="ae95a-202">次の図は `AccessTheWebAsync` から `startButton_Click` に制御が戻ることを示しています。</span><span class="sxs-lookup"><span data-stu-id="ae95a-202">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>

 <span data-ttu-id="ae95a-203">![手順 6.](./media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="ae95a-203">![Step SIX](./media/asynctrace-six.png "AsyncTrace-SIX")</span></span>

## <a name="see-also"></a><span data-ttu-id="ae95a-204">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae95a-204">See also</span></span>

- [<span data-ttu-id="ae95a-205">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="ae95a-205">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="ae95a-206">非同期の戻り値の型 (C#)</span><span class="sxs-lookup"><span data-stu-id="ae95a-206">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="ae95a-207">チュートリアル: Async と Await を使用した Web へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="ae95a-207">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="ae95a-208">Async Sample:非同期プログラムにおける制御フロー (C# および Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae95a-208">Async Sample: Control Flow in Async Programs (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)
