---
title: ファイル アクセスにおける非同期の使用 (C#)
description: C# で非同期機能を使用してファイルにアクセスする方法について説明します。 コールバックを使用したり、複数のメソッドでコードを分割したりせずに、非同期メソッドを呼び出すことができます。
ms.date: 07/20/2015
ms.assetid: bb018fea-5313-4c80-ab3f-7c24b2145bd9
ms.openlocfilehash: eb67bd408fe37b99e6c5ffdc2550e8f95110d7eb
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925125"
---
# <a name="using-async-for-file-access-c"></a><span data-ttu-id="0fde0-104">ファイル アクセスにおける非同期の使用 (C#)</span><span class="sxs-lookup"><span data-stu-id="0fde0-104">Using Async for File Access (C#)</span></span>
<span data-ttu-id="0fde0-105">ファイルにアクセスする際に非同期機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-105">You can use the async feature to access files.</span></span> <span data-ttu-id="0fde0-106">非同期機能を使用すると、コールバックの使用や複数のメソッドまたはラムダ式へのコードの分割を行わずに、非同期メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-106">By using the async feature, you can call into asynchronous methods without using callbacks or splitting your code across multiple methods or lambda expressions.</span></span> <span data-ttu-id="0fde0-107">同期コードを非同期コードにするには、同期メソッドの代わりに非同期メソッドを呼び出して、コードにいくつかのキーワードを追加するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-107">To make synchronous code asynchronous, you just call an asynchronous method instead of a synchronous method and add a few keywords to the code.</span></span>  
  
 <span data-ttu-id="0fde0-108">ファイル アクセスの呼び出しに非同期性を適用する利点には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-108">You might consider the following reasons for adding asynchrony to file access calls:</span></span>  
  
- <span data-ttu-id="0fde0-109">非同期性により、UI アプリケーションの応答性が向上します。非同期処理を開始した UI スレッドが他の処理を実行できるためです。</span><span class="sxs-lookup"><span data-stu-id="0fde0-109">Asynchrony makes UI applications more responsive because the UI thread that launches the operation can perform other work.</span></span> <span data-ttu-id="0fde0-110">UI スレッドが、時間のかかるコード、たとえば 50 ミリ秒を超えるコードを実行する必要がある場合、I/O が完了して、UI スレッドがキーボードやマウス入力などのイベントを再度処理できるようになるまで、UI が停止することがあります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-110">If the UI thread must execute code that takes a long time (for example, more than 50 milliseconds), the UI may freeze until the I/O is complete and the UI thread can again process keyboard and mouse input and other events.</span></span>  
  
- <span data-ttu-id="0fde0-111">非同期性を適用すると、スレッドの必要性が軽減され、ASP.NET などのサーバー ベースのアプリケーションのスケーラビリティが向上します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-111">Asynchrony improves the scalability of ASP.NET and other server-based applications by reducing the need for threads.</span></span> <span data-ttu-id="0fde0-112">アプリケーションが応答ごとに専用スレッドを使用している場合、1,000 個の要求を同時に処理するには、1,000 個のスレッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="0fde0-112">If the application uses a dedicated thread per response and a thousand requests are being handled simultaneously, a thousand threads are needed.</span></span> <span data-ttu-id="0fde0-113">非同期処理では、待機中にスレッドを使用する必要がほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="0fde0-113">Asynchronous operations often don’t need to use a thread during the wait.</span></span> <span data-ttu-id="0fde0-114">既存の I/O 完了スレッドが最後に少しだけ使用されます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-114">They use the existing I/O completion thread briefly at the end.</span></span>  
  
- <span data-ttu-id="0fde0-115">現状ではファイル アクセス操作の待機時間が非常に短くても、将来に大幅に長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-115">The latency of a file access operation might be very low under current conditions, but the latency may greatly increase in the future.</span></span> <span data-ttu-id="0fde0-116">たとえば、地球の裏側にあるサーバーにファイルが移動される場合があります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-116">For example, a file may be moved to a server that's across the world.</span></span>  
  
- <span data-ttu-id="0fde0-117">非同期機能の使用に伴うオーバーヘッドはわずかです。</span><span class="sxs-lookup"><span data-stu-id="0fde0-117">The added overhead of using the Async feature is small.</span></span>  
  
- <span data-ttu-id="0fde0-118">非同期タスクは簡単に並列実行できます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-118">Asynchronous tasks can easily be run in parallel.</span></span>  
  
## <a name="running-the-examples"></a><span data-ttu-id="0fde0-119">例の実行</span><span class="sxs-lookup"><span data-stu-id="0fde0-119">Running the Examples</span></span>  
 <span data-ttu-id="0fde0-120">このトピックの例を実行するには、**WPF アプリケーション**または **Windows フォーム アプリケーション**を作成し、**ボタン**を追加します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-120">To run the examples in this topic, you can create a **WPF Application** or a **Windows Forms Application** and then add a **Button**.</span></span> <span data-ttu-id="0fde0-121">ボタンの `Click` イベントに、それぞれの例で最初のメソッドの呼び出しを追加してください。</span><span class="sxs-lookup"><span data-stu-id="0fde0-121">In the button's `Click` event, add a call to the first method in each example.</span></span>  
  
 <span data-ttu-id="0fde0-122">以降の例には、次の `using` ディレクティブを含めてください。</span><span class="sxs-lookup"><span data-stu-id="0fde0-122">In the following examples, include the following `using` directives.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Diagnostics;  
using System.IO;  
using System.Text;  
using System.Threading.Tasks;  
```  
  
## <a name="use-of-the-filestream-class"></a><span data-ttu-id="0fde0-123">FileStream クラスの使用</span><span class="sxs-lookup"><span data-stu-id="0fde0-123">Use of the FileStream Class</span></span>  
 <span data-ttu-id="0fde0-124">このトピックの例では、<xref:System.IO.FileStream> クラスを使用します。このクラスには、非同期 I/O をオペレーティング システム レベルで発生させるオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="0fde0-124">The examples in this topic use the <xref:System.IO.FileStream> class, which has an option that causes asynchronous I/O to occur at the operating system level.</span></span> <span data-ttu-id="0fde0-125">このオプションを使用すると、多くのケースで ThreadPool スレッドがブロックされるのを回避できます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-125">By using this option, you can avoid blocking a ThreadPool thread in many cases.</span></span> <span data-ttu-id="0fde0-126">このオプションを有効にするには、コンストラクター呼び出しで `useAsync=true` または `options=FileOptions.Asynchronous` 引数を指定します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-126">To enable this option, you specify the `useAsync=true` or `options=FileOptions.Asynchronous` argument in the constructor call.</span></span>  
  
 <span data-ttu-id="0fde0-127">ファイル パスを指定して <xref:System.IO.StreamReader> と <xref:System.IO.StreamWriter> を直接開いた場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="0fde0-127">You can’t use this option with <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> if you open them directly by specifying a file path.</span></span> <span data-ttu-id="0fde0-128">一方、<xref:System.IO.FileStream> クラスによって開かれた <xref:System.IO.Stream> を使用する場合は、このオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-128">However, you can use this option if you provide them a <xref:System.IO.Stream> that the <xref:System.IO.FileStream> class opened.</span></span> <span data-ttu-id="0fde0-129">UI アプリでは、ThreadPool スレッドがブロックされた場合でも、非同期呼び出しのほうが高速です。これは、UI スレッドは待機中にブロックされないためです。</span><span class="sxs-lookup"><span data-stu-id="0fde0-129">Note that asynchronous calls are faster in UI apps even if a ThreadPool thread is blocked, because the UI thread isn’t blocked during the wait.</span></span>  
  
## <a name="writing-text"></a><span data-ttu-id="0fde0-130">テキストの書き込み</span><span class="sxs-lookup"><span data-stu-id="0fde0-130">Writing Text</span></span>  
 <span data-ttu-id="0fde0-131">次の例では、ファイルにテキストを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-131">The following example writes text to a file.</span></span> <span data-ttu-id="0fde0-132">各 await ステートメントに達すると、メソッドは直ちに終了します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-132">At each await statement, the method immediately exits.</span></span> <span data-ttu-id="0fde0-133">ファイル I/O が完了すると、メソッドは await ステートメントの後のステートメントから再開します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-133">When the file I/O is complete, the method resumes at the statement that follows the await statement.</span></span> <span data-ttu-id="0fde0-134">await ステートメントを使用するメソッドの定義に async 修飾子が含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0fde0-134">Note that the async modifier is in the definition of methods that use the await statement.</span></span>  
  
```csharp  
public async Task ProcessWriteAsync()  
{  
    string filePath = @"temp2.txt";  
    string text = "Hello World\r\n";  
  
    await WriteTextAsync(filePath, text);  
}  
  
private async Task WriteTextAsync(string filePath, string text)  
{  
    byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Append, FileAccess.Write, FileShare.None,  
        bufferSize: 4096, useAsync: true))  
    {  
        await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
    };  
}  
```  
  
 <span data-ttu-id="0fde0-135">元の例には `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);` ステートメントがあります。これは、次の 2 つのステートメントの省略形です。</span><span class="sxs-lookup"><span data-stu-id="0fde0-135">The original example has the statement `await sourceStream.WriteAsync(encodedText, 0, encodedText.Length);`, which is a contraction of the following two statements:</span></span>  
  
```csharp  
Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
await theTask;  
```  
  
 <span data-ttu-id="0fde0-136">最初のステートメントはタスクを返し、ファイル処理を開始します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-136">The first statement returns a task and causes file processing to start.</span></span> <span data-ttu-id="0fde0-137">await が含まれた 2 番目のステートメントによって、メソッドが直ちに終了し、別のタスクを返します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-137">The second statement with the await causes the method to immediately exit and return a different task.</span></span> <span data-ttu-id="0fde0-138">ファイル処理が完了すると、await の後のステートメントに実行が戻ります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-138">When the file processing later completes, execution returns to the statement that follows the await.</span></span> <span data-ttu-id="0fde0-139">詳細については、「[非同期プログラムにおける制御フロー (C#)](./control-flow-in-async-programs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fde0-139">For more information, see  [Control Flow in Async Programs (C#)](./control-flow-in-async-programs.md).</span></span>  
  
## <a name="reading-text"></a><span data-ttu-id="0fde0-140">テキストの読み取り</span><span class="sxs-lookup"><span data-stu-id="0fde0-140">Reading Text</span></span>  
 <span data-ttu-id="0fde0-141">次の例では、ファイルからテキストを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-141">The following example reads text from a file.</span></span> <span data-ttu-id="0fde0-142">テキストはバッファーに格納されます。この例では <xref:System.Text.StringBuilder> に配置されます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-142">The text is buffered and, in this case, placed into a <xref:System.Text.StringBuilder>.</span></span> <span data-ttu-id="0fde0-143">前の例と異なり、await の評価で値が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-143">Unlike in the previous example, the evaluation of the await produces a value.</span></span> <span data-ttu-id="0fde0-144"><xref:System.IO.Stream.ReadAsync%2A> メソッドによって <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>> が返されます。処理の完了後、await の評価によって `Int32` 値 (`numRead`) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-144">The <xref:System.IO.Stream.ReadAsync%2A> method returns a <xref:System.Threading.Tasks.Task>\<<xref:System.Int32>>, so the evaluation of the await produces an `Int32` value (`numRead`) after the operation completes.</span></span> <span data-ttu-id="0fde0-145">詳しくは、「[非同期の戻り値の型 (C#)](./async-return-types.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0fde0-145">For more information, see [Async Return Types (C#)](./async-return-types.md).</span></span>  
  
```csharp  
public async Task ProcessReadAsync()  
{  
    string filePath = @"temp2.txt";  
  
    if (File.Exists(filePath) == false)  
    {  
        Debug.WriteLine("file not found: " + filePath);  
    }  
    else  
    {  
        try  
        {  
            string text = await ReadTextAsync(filePath);  
            Debug.WriteLine(text);  
        }  
        catch (Exception ex)  
        {  
            Debug.WriteLine(ex.Message);  
        }  
    }  
}  
  
private async Task<string> ReadTextAsync(string filePath)  
{  
    using (FileStream sourceStream = new FileStream(filePath,  
        FileMode.Open, FileAccess.Read, FileShare.Read,  
        bufferSize: 4096, useAsync: true))  
    {  
        StringBuilder sb = new StringBuilder();  
  
        byte[] buffer = new byte[0x1000];  
        int numRead;  
        while ((numRead = await sourceStream.ReadAsync(buffer, 0, buffer.Length)) != 0)  
        {  
            string text = Encoding.Unicode.GetString(buffer, 0, numRead);  
            sb.Append(text);  
        }  
  
        return sb.ToString();  
    }  
}  
```  
  
## <a name="parallel-asynchronous-io"></a><span data-ttu-id="0fde0-146">並列非同期 I/O</span><span class="sxs-lookup"><span data-stu-id="0fde0-146">Parallel Asynchronous I/O</span></span>  
 <span data-ttu-id="0fde0-147">次の例では、10 個のテキスト ファイルを記述する並列処理を示します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-147">The following example demonstrates parallel processing by writing 10 text files.</span></span> <span data-ttu-id="0fde0-148"><xref:System.IO.Stream.WriteAsync%2A> メソッドは、ファイルごとにタスクを返します。タスクはタスクの一覧に追加されます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-148">For each file, the <xref:System.IO.Stream.WriteAsync%2A> method returns a task that is then added to a list of tasks.</span></span> <span data-ttu-id="0fde0-149">`await Task.WhenAll(tasks);` ステートメントはメソッドを終了し、すべてのタスクのファイル処理が完了すると、メソッド内で再開します。</span><span class="sxs-lookup"><span data-stu-id="0fde0-149">The `await Task.WhenAll(tasks);` statement exits the method and resumes within the method when file processing is complete for all of the tasks.</span></span>  
  
 <span data-ttu-id="0fde0-150">この例では、タスクの完了後、`finally` ブロックのすべての <xref:System.IO.FileStream> インスタンスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-150">The example closes all <xref:System.IO.FileStream> instances in a `finally` block after the tasks are complete.</span></span> <span data-ttu-id="0fde0-151">`using` ステートメントで `FileStream` が作成された場合は、タスクが完了する前に `FileStream` が破棄されることがあります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-151">If each `FileStream` was instead created in a `using` statement, the `FileStream` might be disposed of before the task was complete.</span></span>  
  
 <span data-ttu-id="0fde0-152">パフォーマンスの向上のほとんどが、非同期処理ではなく並列処理によって実現していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0fde0-152">Note that any performance boost is almost entirely from the parallel processing and not the asynchronous processing.</span></span> <span data-ttu-id="0fde0-153">非同期性の利点は、複数のスレッドやユーザー インターフェイス スレッドが拘束されなくなる点にあります。</span><span class="sxs-lookup"><span data-stu-id="0fde0-153">The advantages of asynchrony are that it doesn’t tie up multiple threads, and that it doesn’t tie up the user interface thread.</span></span>  
  
```csharp  
public async Task ProcessWriteMultAsync()  
{  
    string folder = @"tempfolder\";  
    List<Task> tasks = new List<Task>();  
    List<FileStream> sourceStreams = new List<FileStream>();  
  
    try  
    {  
        for (int index = 1; index <= 10; index++)  
        {  
            string text = "In file " + index.ToString() + "\r\n";  
  
            string fileName = "thefile" + index.ToString("00") + ".txt";  
            string filePath = folder + fileName;  
  
            byte[] encodedText = Encoding.Unicode.GetBytes(text);  
  
            FileStream sourceStream = new FileStream(filePath,  
                FileMode.Append, FileAccess.Write, FileShare.None,  
                bufferSize: 4096, useAsync: true);  
  
            Task theTask = sourceStream.WriteAsync(encodedText, 0, encodedText.Length);  
            sourceStreams.Add(sourceStream);  
  
            tasks.Add(theTask);  
        }  
  
        await Task.WhenAll(tasks);  
    }  
  
    finally  
    {  
        foreach (FileStream sourceStream in sourceStreams)  
        {  
            sourceStream.Close();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="0fde0-154"><xref:System.IO.Stream.WriteAsync%2A> メソッドと <xref:System.IO.Stream.ReadAsync%2A> メソッドを使用すると、<xref:System.Threading.CancellationToken> を指定して、途中で処理をキャンセルすることができます。</span><span class="sxs-lookup"><span data-stu-id="0fde0-154">When using the <xref:System.IO.Stream.WriteAsync%2A> and <xref:System.IO.Stream.ReadAsync%2A> methods, you can specify a <xref:System.Threading.CancellationToken>, which you can use to cancel the operation mid-stream.</span></span> <span data-ttu-id="0fde0-155">詳細については、「[非同期アプリケーションの微調整 (C#)](./fine-tuning-your-async-application.md)」および「[マネージド スレッドのキャンセル](../../../../standard/threading/cancellation-in-managed-threads.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fde0-155">For more information, see [Fine-Tuning Your Async Application (C#)](./fine-tuning-your-async-application.md) and [Cancellation in Managed Threads](../../../../standard/threading/cancellation-in-managed-threads.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fde0-156">関連項目</span><span class="sxs-lookup"><span data-stu-id="0fde0-156">See also</span></span>

- [<span data-ttu-id="0fde0-157">Async および Await を使用した非同期プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="0fde0-157">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="0fde0-158">非同期の戻り値の型 (C#)</span><span class="sxs-lookup"><span data-stu-id="0fde0-158">Async Return Types (C#)</span></span>](./async-return-types.md)
- [<span data-ttu-id="0fde0-159">非同期プログラムにおける制御フロー (C#)</span><span class="sxs-lookup"><span data-stu-id="0fde0-159">Control Flow in Async Programs (C#)</span></span>](./control-flow-in-async-programs.md)
