---
title: Task.WhenAll を使用して AsyncWalkthrough を拡張する方法 (C#)
description: C# で Task.WhenAll を使用して非同期ソリューションのパフォーマンスを向上させる方法について説明します。 このメソッドは、複数の非同期操作を非同期に待機します。
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 275f4aeca854f8938642dbea40bf7fd9dc5362d9
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925216"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="0be5c-104">Task.WhenAll を使用して AsyncWalkthrough を拡張する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="0be5c-104">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>

<span data-ttu-id="0be5c-105"><xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> メソッドを使用すると、「[チュートリアル: Async と Await を使用した Web へのアクセス (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)」の非同期ソリューションのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="0be5c-105">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0be5c-106">このメソッドは、タスクのコレクションとして表される、複数の非同期操作を非同期に待機します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-106">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>

<span data-ttu-id="0be5c-107">このチュートリアルでは、Web サイトが異なる速度でダウンロードされることに気付きます。</span><span class="sxs-lookup"><span data-stu-id="0be5c-107">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="0be5c-108">Web サイトの 1 つが非常に低速な場合があります。これは残りのすべてのダウンロードを遅延させます。</span><span class="sxs-lookup"><span data-stu-id="0be5c-108">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="0be5c-109">このチュートリアルで構築した非同期ソリューションを実行すると、プログラムを待たない場合には簡単に終了することができますが、よりよい方法は、すべてのダウンロードを同時に開始して、遅延したダウンロードを待たずに早いダウンロードが継続できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="0be5c-109">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>

<span data-ttu-id="0be5c-110">タスクのコレクションに `Task.WhenAll` メソッドを適用します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-110">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="0be5c-111">`WhenAll` を適用すると、コレクション内のすべてのタスクが完了するまで完了しない 1 つのタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-111">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="0be5c-112">タスクは並列で実行されるように見えますが、追加のスレッドは作成されません。</span><span class="sxs-lookup"><span data-stu-id="0be5c-112">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="0be5c-113">タスクは任意の順序で完了します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-113">The tasks can complete in any order.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0be5c-114">次の手順では、「[チュートリアル: Async と Await を使用した Web へのアクセス (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)」で開発した非同期アプリケーションの拡張機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-114">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="0be5c-115">チュートリアルを完了するか、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)からコードをダウンロードして、アプリケーションを開発できます。</span><span class="sxs-lookup"><span data-stu-id="0be5c-115">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>
>
> <span data-ttu-id="0be5c-116">例を実行するには、Visual Studio 2012 以降がコンピューターにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="0be5c-116">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>

### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="0be5c-117">GetURLContentsAsync ソリューションに Task.WhenAll を追加するには</span><span class="sxs-lookup"><span data-stu-id="0be5c-117">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>

1. <span data-ttu-id="0be5c-118">`ProcessURLAsync` メソッドを「[チュートリアル: Async と Await を使用した Web へのアクセス (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)」で開発した最初のアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-118">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="0be5c-119">コードを[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)からダウンロードした場合は、AsyncWalkthrough プロジェクトを開き、`ProcessURLAsync` を MainWindow.xaml.cs ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-119">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="0be5c-120">チュートリアルを実行してコードを開発する場合は、`ProcessURLAsync` メソッドを含むアプリケーションに `GetURLContentsAsync` を追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-120">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="0be5c-121">このアプリケーションの MainWindow.xaml.cs ファイルは、「チュートリアルの完全なコード例」のセクションにある 1 つ目の例です。</span><span class="sxs-lookup"><span data-stu-id="0be5c-121">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="0be5c-122">`ProcessURLAsync` メソッドは、元のチュートリアルの `SumPageSizesAsync` の `foreach` ループの本体にあるアクションを統合します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-122">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="0be5c-123">このメソッドは、指定した Web サイトのコンテンツをバイト配列として非同期的にダウンロードし、バイト配列の長さを表示して返します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-123">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    ```csharp
    private async Task<int> ProcessURLAsync(string url)
    {
        var byteArray = await GetURLContentsAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="0be5c-124">次のコードに示すように、`SumPageSizesAsync` の `foreach` ループをコメント アウトするか削除します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-124">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    byte[] urlContents = await GetURLContentsAsync(url);

    //    // The previous line abbreviates the following two assignment statements.
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //    //byte[] urlContents = await getContentsTask;

    //    DisplayResults(url, urlContents);

    //    // Update the total.
    //    total += urlContents.Length;
    //}
    ```

3. <span data-ttu-id="0be5c-125">タスクのコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-125">Create a collection of tasks.</span></span> <span data-ttu-id="0be5c-126">次のコードは、<xref:System.Linq.Enumerable.ToArray%2A> メソッドによって実行されるときに、各 Web サイトのコンテンツをダウンロードするタスクのコレクションを作成する[クエリ](../linq/index.md)を定義します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-126">The following code defines a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="0be5c-127">タスクは、クエリが評価されるときに開始されます。</span><span class="sxs-lookup"><span data-stu-id="0be5c-127">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="0be5c-128">`SumPageSizesAsync` の宣言の後の `urlList` メソッドに、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-128">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="0be5c-129">`Task.WhenAll` をタスクのコレクション `downloadTasks` に適用します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-129">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="0be5c-130">`Task.WhenAll` は、タスクのコレクションのすべてのタスクが完了すると完了する、単一のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-130">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="0be5c-131">次の例では、`await` 式は、`WhenAll` によって返される単一のタスクが完了するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-131">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="0be5c-132">式は、各整数がダウンロードされたサイトの長さである、整数の配列に評価します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-132">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="0be5c-133">`SumPageSizesAsync` の、前の手順で追加したコードの直後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-133">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="0be5c-134">最後に <xref:System.Linq.Enumerable.Sum%2A> メソッドを使って、すべての Web サイトの長さの合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-134">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="0be5c-135">`SumPageSizesAsync` に次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-135">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="0be5c-136">HttpClient.GetByteArrayAsync ソリューションに Task.WhenAll を追加するには</span><span class="sxs-lookup"><span data-stu-id="0be5c-136">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>

1. <span data-ttu-id="0be5c-137">`ProcessURLAsync` の次のバージョンを「[チュートリアル: Async と Await を使用した Web へのアクセス (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)」で開発した 2 番目のアプリケーションに追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-137">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>

    - <span data-ttu-id="0be5c-138">コードを[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)からダウンロードした場合は、AsyncWalkthrough_HttpClient プロジェクトを開き、`ProcessURLAsync` を MainWindow.xaml.cs ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-138">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>

    - <span data-ttu-id="0be5c-139">チュートリアルを実行してコードを開発する場合は、`ProcessURLAsync` メソッドを使うアプリケーションに `HttpClient.GetByteArrayAsync` を追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-139">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="0be5c-140">このアプリケーションの MainWindow.xaml.cs ファイルは、「チュートリアルの完全なコード例」のセクションにある 2 つ目の例です。</span><span class="sxs-lookup"><span data-stu-id="0be5c-140">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>

    <span data-ttu-id="0be5c-141">`ProcessURLAsync` メソッドは、元のチュートリアルの `SumPageSizesAsync` の `foreach` ループの本体にあるアクションを統合します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-141">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="0be5c-142">このメソッドは、指定した Web サイトのコンテンツをバイト配列として非同期的にダウンロードし、バイト配列の長さを表示して返します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-142">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>

    <span data-ttu-id="0be5c-143">前の手順の `ProcessURLAsync` メソッドとの唯一の違いは、<xref:System.Net.Http.HttpClient> インスタンス `client` の使用です。</span><span class="sxs-lookup"><span data-stu-id="0be5c-143">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>

    ```csharp
    async Task<int> ProcessURLAsync(string url, HttpClient client)
    {
        byte[] byteArray = await client.GetByteArrayAsync(url);
        DisplayResults(url, byteArray);
        return byteArray.Length;
    }
    ```

2. <span data-ttu-id="0be5c-144">次のコードに示すように、`For Each` の `foreach` または `SumPageSizesAsync` のループをコメント アウトするか削除します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-144">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>

    ```csharp
    //var total = 0;
    //foreach (var url in urlList)
    //{
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task
    //    // produces a byte array.
    //    byte[] urlContent = await client.GetByteArrayAsync(url);

    //    // The previous line abbreviates the following two assignment
    //    // statements.
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
    //    byte[] urlContent = await getContentTask;

    //    DisplayResults(url, urlContent);

    //    // Update the total.
    //    total += urlContent.Length;
    //}
    ```

3. <span data-ttu-id="0be5c-145"><xref:System.Linq.Enumerable.ToArray%2A> メソッドによって実行されるときに、各 Web サイトのコンテンツをダウンロードするタスクのコレクションを作成する[クエリ](../linq/index.md)を定義します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-145">Define a [query](../linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="0be5c-146">タスクは、クエリが評価されるときに開始されます。</span><span class="sxs-lookup"><span data-stu-id="0be5c-146">The tasks are started when the query is evaluated.</span></span>

    <span data-ttu-id="0be5c-147">`SumPageSizesAsync` および `client` の宣言の後の `urlList` メソッドに、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-147">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>

    ```csharp
    // Create a query.
    IEnumerable<Task<int>> downloadTasksQuery =
        from url in urlList select ProcessURLAsync(url, client);

    // Use ToArray to execute the query and start the download tasks.
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();
    ```

4. <span data-ttu-id="0be5c-148">次に、`Task.WhenAll` をタスクのコレクション `downloadTasks` に適用します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-148">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="0be5c-149">`Task.WhenAll` は、タスクのコレクションのすべてのタスクが完了すると完了する、単一のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-149">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>

    <span data-ttu-id="0be5c-150">次の例では、`await` 式は、`WhenAll` によって返される単一のタスクが完了するのを待機します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-150">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="0be5c-151">完了すると、`await` 式は、各整数がダウンロードされたサイトの長さである、整数の配列に評価します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-151">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="0be5c-152">`SumPageSizesAsync` の、前の手順で追加したコードの直後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-152">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>

    ```csharp
    // Await the completion of all the running tasks.
    int[] lengths = await Task.WhenAll(downloadTasks);

    //// The previous line is equivalent to the following two statements.
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
    //int[] lengths = await whenAllTask;
    ```

5. <span data-ttu-id="0be5c-153">最後に <xref:System.Linq.Enumerable.Sum%2A> メソッドを使って、すべての Web サイトの長さの合計を計算します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-153">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="0be5c-154">`SumPageSizesAsync` に次の行を追加します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-154">Add the following line to `SumPageSizesAsync`.</span></span>

    ```csharp
    int total = lengths.Sum();
    ```

### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="0be5c-155">Task.WhenAll ソリューションをテストするには</span><span class="sxs-lookup"><span data-stu-id="0be5c-155">To test the Task.WhenAll solutions</span></span>

- <span data-ttu-id="0be5c-156">各ソリューションで、F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。</span><span class="sxs-lookup"><span data-stu-id="0be5c-156">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="0be5c-157">出力は「[チュートリアル: Async と Await を使用した Web へのアクセス (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)」の非同期ソリューションからの出力に似たものになります。</span><span class="sxs-lookup"><span data-stu-id="0be5c-157">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="0be5c-158">ただし、Web サイトは毎回、異なる順序で表示されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0be5c-158">However, notice that the websites appear in a different order each time.</span></span>

## <a name="example"></a><span data-ttu-id="0be5c-159">例</span><span class="sxs-lookup"><span data-stu-id="0be5c-159">Example</span></span>

<span data-ttu-id="0be5c-160">次のコードは、`GetURLContentsAsync` メソッドを使用して Web からコンテンツをダウンロードするプロジェクトの拡張機能を示します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-160">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_WhenAll
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

            // Two-step async call.
            Task sumTask = SumPageSizesAsync();
            await sumTask;

            // One-step async call.
            //await SumPageSizesAsync();

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    byte[] urlContents = await GetURLContentsAsync(url);

            //    // The previous line abbreviates the following two assignment statements.
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
            //    //byte[] urlContents = await getContentsTask;

            //    DisplayResults(url, urlContents);

            //    // Update the total.
            //    total += urlContents.Length;
            //}

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        private async Task<int> ProcessURLAsync(string url)
        {
            var byteArray = await GetURLContentsAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    await responseStream.CopyToAsync(content);
                }
            }

            // Return the result as a byte array.
            return content.ToArray();

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

## <a name="example"></a><span data-ttu-id="0be5c-161">例</span><span class="sxs-lookup"><span data-stu-id="0be5c-161">Example</span></span>

<span data-ttu-id="0be5c-162">次のコードは、`HttpClient.GetByteArrayAsync` メソッドを使用して Web からコンテンツをダウンロードするプロジェクトの拡張機能を示します。</span><span class="sxs-lookup"><span data-stu-id="0be5c-162">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>

```csharp
// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF_HttpClient_WhenAll
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

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Create a query.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURLAsync(url, client);

            // Use ToArray to execute the query and start the download tasks.
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();

            // You can do other work here before awaiting.

            // Await the completion of all the running tasks.
            int[] lengths = await Task.WhenAll(downloadTasks);

            //// The previous line is equivalent to the following two statements.
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);
            //int[] lengths = await whenAllTask;

            int total = lengths.Sum();

            //var total = 0;
            //foreach (var url in urlList)
            //{
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task
            //    // produces a byte array.
            //    byte[] urlContent = await client.GetByteArrayAsync(url);

            //    // The previous line abbreviates the following two assignment
            //    // statements.
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);
            //    byte[] urlContent = await getContentTask;

            //    DisplayResults(url, urlContent);

            //    // Update the total.
            //    total += urlContent.Length;
            //}

            // Display the total count for all of the web addresses.
            resultsTextBox.Text +=
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        // The actions from the foreach loop are moved to this async method.
        async Task<int> ProcessURLAsync(string url, HttpClient client)
        {
            byte[] byteArray = await client.GetByteArrayAsync(url);
            DisplayResults(url, byteArray);
            return byteArray.Length;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each web site. The string format
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

## <a name="see-also"></a><span data-ttu-id="0be5c-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="0be5c-163">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0be5c-164">チュートリアル: Async と Await を使用した Web へのアクセス (C#)</span><span class="sxs-lookup"><span data-stu-id="0be5c-164">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
