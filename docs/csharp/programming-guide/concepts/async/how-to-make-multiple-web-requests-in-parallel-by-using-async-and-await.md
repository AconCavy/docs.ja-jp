---
title: async と await を使用して複数の Web 要求を並列実行する方法 (C#)
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: a6eef947e8f657cff574ffdf3afcd8943c665b8d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969945"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="35c3b-102">async と await を使用して複数の Web 要求を並列実行する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="35c3b-102">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="35c3b-103">非同期メソッドでは、タスクは作成されると開始されます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="35c3b-104">[await](../../../language-reference/operators/await.md) 演算子は、メソッド内でタスクが終了するまで処理が続行できなくなった時点で、タスクに適用されます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-104">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="35c3b-105">次の例に示すように、タスクは多くの場合、作成されるとすぐに待機します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="35c3b-106">ただし、プログラムにタスクの完了に依存せずに実行する別の処理がある場合、タスクの作成とタスクの待機を分けることもできます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="35c3b-107">タスクを開始して待機する間に、他のタスクを開始できます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="35c3b-108">追加のタスクは暗黙的に並列で実行されますが、追加のスレッドは作成されません。</span><span class="sxs-lookup"><span data-stu-id="35c3b-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="35c3b-109">次のプログラムは 3 つの非同期的な Web ダウンロードを開始し、次に呼び出した順にそれを待機します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="35c3b-110">プログラムを実行する場合、タスクは必ずしも作成して待機した順には終了しないことに注意します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="35c3b-111">タスクは作成されると実行され、メソッドが await 式に到達する前に 1 つまたは複数のタスクが終了する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="35c3b-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35c3b-112">このプロジェクトを完成させるには、Visual Studio 2012 以降および .NET Framework 4.5 以降がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="35c3b-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="35c3b-113">複数のタスクを同時に開始する別の例については、「[Task.WhenAll を使用して AsyncWalkthrough を拡張する方法 (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35c3b-113">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="35c3b-114">この例のコードは、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)のページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="35c3b-115">プロジェクトを設定するには</span><span class="sxs-lookup"><span data-stu-id="35c3b-115">To set up the project</span></span>  
  
1. <span data-ttu-id="35c3b-116">WPF アプリケーションを設定するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="35c3b-117">これらの手順の詳細については、「[チュートリアル: Async と Await を使用した Web へのアクセス (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="35c3b-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="35c3b-118">テキスト ボックスとボタンを含む WPF アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="35c3b-119">ボタンに `startButton` という名前を付け、テキスト ボックスに `resultsTextBox` という名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="35c3b-120"><xref:System.Net.Http> への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="35c3b-121">MainWindow.xaml.cs ファイルで、`System.Net.Http` に `using` ディレクティブを追加します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-121">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="35c3b-122">コードを追加するには</span><span class="sxs-lookup"><span data-stu-id="35c3b-122">To add the code</span></span>  
  
1. <span data-ttu-id="35c3b-123">デザイン ウィンドウの MainWindow.xaml で、ボタンをダブルクリックして、MainWindow.xaml.cs に `startButton_Click` イベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="35c3b-124">次のコードをコピーし、MainWindow.xaml.cs の `startButton_Click` の本体に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="35c3b-125">このコードは、アプリケーションを呼び出す非同期メソッドである `CreateMultipleTasksAsync` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="35c3b-126">プロジェクトに次のサポート メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-126">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="35c3b-127">`ProcessURLAsync` は <xref:System.Net.Http.HttpClient> メソッドを使用して、Web サイトのコンテンツをバイト配列としてダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="35c3b-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="35c3b-128">次に `ProcessURLAsync` サポート メソッドは、配列の長さを表示して返します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="35c3b-129">`DisplayResults` は各 URL のバイト配列内のバイトの数を表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="35c3b-130">この表示は、各タスクがいつダウンロードを完了したかを示します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="35c3b-131">次のメソッドをコピーし、MainWindow.xaml.cs の `startButton_Click` イベント ハンドラーの後に貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
  
    private void DisplayResults(string url, byte[] content)  
    {  
        // Display the length of each website. The string format   
        // is designed to be used with a monospaced font, such as  
        // Lucida Console or Global Monospace.  
        var bytes = content.Length;  
        // Strip off the "https://".  
        var displayURL = url.Replace("https://", "");  
        resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
    }  
    ```  
  
4. <span data-ttu-id="35c3b-132">最後に、次の手順を実行するメソッド `CreateMultipleTasksAsync` を定義します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="35c3b-133">このメソッドは、`HttpClient` の <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> メソッドにアクセスするために必要な `ProcessURLAsync` オブジェクトを宣言します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="35c3b-134">このメソッドは <xref:System.Threading.Tasks.Task%601> が整数である `TResult` 型の 3 つのタスクを作成して開始します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="35c3b-135">各タスクが終了すると、`DisplayResults` はタスクの URL とダウンロードしたコンテンツの長さを表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="35c3b-136">タスクは非同期的に実行されるため、結果が表示される順序は、宣言された順序と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="35c3b-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="35c3b-137">メソッドは、各タスクの完了を待機します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="35c3b-138">各 `await` 演算子は、待機したタスクが終了するまで `CreateMultipleTasksAsync` の実行を中断します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-138">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="35c3b-139">さらに演算子は、完了した各タスクから `ProcessURLAsync` への呼び出しからの戻り値を取得します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="35c3b-140">タスクが完了して整数値が取得されると、メソッドは Web サイトの長さの合計し、その結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="35c3b-141">次のメソッドをコピーしてソリューションに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="35c3b-141">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults   
        // displays its length.  
        Task<int> download1 =   
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =   
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="35c3b-142">F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="35c3b-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="35c3b-143">プログラムを複数回実行して、3 つのタスクが必ずしも同じ順序では完了しないこと、また完了の順序は必ずしも作成され待機した順序と同じではないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35c3b-144">例</span><span class="sxs-lookup"><span data-stu-id="35c3b-144">Example</span></span>  
 <span data-ttu-id="35c3b-145">ここまでの例をすべて含んだコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="35c3b-145">The following code contains the full example.</span></span>  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults   
            // displays its length.  
            Task<int> download1 =   
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =   
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="35c3b-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="35c3b-146">See also</span></span>

- [<span data-ttu-id="35c3b-147">チュートリアル: Async と Await を使用した Web へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="35c3b-147">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="35c3b-148">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="35c3b-148">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="35c3b-149">Task.WhenAll を使用して AsyncWalkthrough を拡張する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="35c3b-149">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
