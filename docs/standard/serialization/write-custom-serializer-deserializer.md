---
title: System.Text.Json でカスタム シリアライザーと逆シリアライザーを作成する方法
description: System.Text.Json 名前空間を使用して、JSON のカスタム シリアライザーと逆シリアライザーを作成する方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: a01d3c8dd18c114ea1c3aabc402bc841a6025ffe
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439804"
---
# <a name="how-to-write-custom-serializers-and-deserializers-with-no-locsystemtextjson"></a><span data-ttu-id="9c345-103">System.Text.Json でカスタム シリアライザーと逆シリアライザーを作成する方法</span><span class="sxs-lookup"><span data-stu-id="9c345-103">How to write custom serializers and deserializers with System.Text.Json</span></span>

<span data-ttu-id="9c345-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> は、UTF-8 でエンコードされた JSON テキスト用の、ハイパフォーマンス、低割り当て、順方向専用のリーダーです。`ReadOnlySpan<byte>` または `ReadOnlySequence<byte>` から読み取られます。</span><span class="sxs-lookup"><span data-stu-id="9c345-104"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="9c345-105">`Utf8JsonReader` は低レベルの型であり、カスタム パーサーとデシリアライザーを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c345-105">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="9c345-106"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonReader` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-106">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="9c345-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> は、`String`、`Int32`、`DateTime` のような一般的な .NET 型から UTF-8 でエンコードされた JSON テキストを書き込むための、ハイパフォーマンスな方法です。</span><span class="sxs-lookup"><span data-stu-id="9c345-107"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="9c345-108">ライターは低レベルの型であり、カスタム シリアライザーを構築するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c345-108">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="9c345-109"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドでは、内部で `Utf8JsonWriter` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-109">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="9c345-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> では、`Utf8JsonReader` を使用して、読み取り専用のドキュメント オブジェクト モデル (DOM) を構築する機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-110"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="9c345-111">DOM では、JSON ペイロード内のデータへのランダム アクセスが提供されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-111">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="9c345-112">ペイロードを構成する JSON 要素には、<xref:System.Text.Json.JsonElement> 型を使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9c345-112">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="9c345-113">`JsonElement` 型では、配列とオブジェクト列挙子と共に、JSON テキストを一般的な .NET 型に変換する API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-113">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="9c345-114">`JsonDocument` では <xref:System.Text.Json.JsonDocument.RootElement> プロパティが公開されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-114">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="9c345-115">以下のセクションでは、これらのツールを使用して JSON の読み取りと書き込みを行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9c345-115">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="9c345-116">JsonDocument を使用してデータにアクセスする</span><span class="sxs-lookup"><span data-stu-id="9c345-116">Use JsonDocument for access to data</span></span>

<span data-ttu-id="9c345-117">次の例は、<xref:System.Text.Json.JsonDocument> クラスを使用して JSON 文字列内のデータにランダム アクセスする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c345-117">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades1":::

<span data-ttu-id="9c345-118">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="9c345-118">The preceding code:</span></span>

* <span data-ttu-id="9c345-119">分析する JSON が `jsonString` という名前の文字列に含まれていると想定します。</span><span class="sxs-lookup"><span data-stu-id="9c345-119">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="9c345-120">`Grade` プロパティを持つ `Students` 配列内のオブジェクトの平均グレードを計算します。</span><span class="sxs-lookup"><span data-stu-id="9c345-120">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="9c345-121">グレードのない学生には既定のグレード 70 を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="9c345-121">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="9c345-122">反復するたびに `count` 変数をインクリメントして学生をカウントします。</span><span class="sxs-lookup"><span data-stu-id="9c345-122">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="9c345-123">別の方法として、次の例に示すように <xref:System.Text.Json.JsonElement.GetArrayLength%2A> を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="9c345-123">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  :::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs" id="AverageGrades2":::

<span data-ttu-id="9c345-124">このコードで処理される JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c345-124">Here's an example of the JSON that this code processes:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="9c345-125">JsonDocument を使用して JSON を書き込む</span><span class="sxs-lookup"><span data-stu-id="9c345-125">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="9c345-126">次の例では、<xref:System.Text.Json.JsonDocument> から JSON を書き込む方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9c345-126">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs" id="Serialize":::

<span data-ttu-id="9c345-127">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="9c345-127">The preceding code:</span></span>

* <span data-ttu-id="9c345-128">JSON ファイルを読み取り、データを `JsonDocument` に読み込み、書式設定された (整形された) JSON をファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="9c345-128">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="9c345-129"><xref:System.Text.Json.JsonDocumentOptions> を使用して、入力 JSON 内でコメントは許可されるが無視されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c345-129">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="9c345-130">完了したら、ライターに対して <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="9c345-130">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="9c345-131">別の方法として、破棄されたときにライターを自動フラッシュすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9c345-131">An alternative is to let the writer auto-flush when it's disposed.</span></span>

<span data-ttu-id="9c345-132">コード例によって処理される JSON 入力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c345-132">Here's an example of JSON input to be processed by the example code:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Grades.json":::

<span data-ttu-id="9c345-133">その結果は、次のような整形された JSON 出力になります。</span><span class="sxs-lookup"><span data-stu-id="9c345-133">The result is the following pretty-printed JSON output:</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json":::

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="9c345-134">Utf8JsonWriter を使用する</span><span class="sxs-lookup"><span data-stu-id="9c345-134">Use Utf8JsonWriter</span></span>

<span data-ttu-id="9c345-135"><xref:System.Text.Json.Utf8JsonWriter> クラスを使用する方法を示す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c345-135">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs" id="Serialize":::

## <a name="use-utf8jsonreader"></a><span data-ttu-id="9c345-136">Utf8JsonReader を使用する</span><span class="sxs-lookup"><span data-stu-id="9c345-136">Use Utf8JsonReader</span></span>

<span data-ttu-id="9c345-137"><xref:System.Text.Json.Utf8JsonReader> クラスを使用する方法を示す例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c345-137">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs" id="Deserialize":::

<span data-ttu-id="9c345-138">上記のコードでは、`jsonUtf8` 変数が、UTF-8 としてエンコードされた有効な JSON を含むバイト配列であることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="9c345-138">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="9c345-139">Utf8JsonReader を使用してデータをフィルター処理する</span><span class="sxs-lookup"><span data-stu-id="9c345-139">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="9c345-140">次の例は、同期的にファイルを読み取り、値を検索する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c345-140">The following example shows how to synchronously read a file, and search for a value.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs":::

<span data-ttu-id="9c345-141">この例の非同期バージョンについては、[.NET サンプル JSON プロジェクト](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c345-141">For an asynchronous version of this example, see [.NET samples JSON project](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs).</span></span>

<span data-ttu-id="9c345-142">上記のコードでは次の操作が行われます。</span><span class="sxs-lookup"><span data-stu-id="9c345-142">The preceding code:</span></span>

* <span data-ttu-id="9c345-143">JSON にオブジェクトの配列が含まれ、各オブジェクトに文字列型の "name" プロパティが含まれている可能性があると想定します。</span><span class="sxs-lookup"><span data-stu-id="9c345-143">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="9c345-144">オブジェクトと "University" で終わる "name" プロパティ値をカウントします。</span><span class="sxs-lookup"><span data-stu-id="9c345-144">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="9c345-145">ファイルが UTF-16 としてエンコードされ、UTF-8 にトランスコードされるものと想定します。</span><span class="sxs-lookup"><span data-stu-id="9c345-145">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="9c345-146">UTF-8 としてエンコードされたファイルは、次のコードを使用して、`ReadOnlySpan<byte>` に直接読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="9c345-146">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="9c345-147">リーダーではテキストが想定されるため、ファイルに UTF-8 バイト オーダー マーク (BOM) が含まれている場合は、バイトを `Utf8JsonReader` に渡す前にそれを削除します。</span><span class="sxs-lookup"><span data-stu-id="9c345-147">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="9c345-148">そうしないと、BOM は無効な JSON と見なされ、リーダーによって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9c345-148">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="9c345-149">上記のコードで読み取ることができる JSON のサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9c345-149">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="9c345-150">結果として生成される概要メッセージは、"2 out of 4 have names that end with 'University'" です。</span><span class="sxs-lookup"><span data-stu-id="9c345-150">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

:::code language="json" source="snippets/system-text-json-how-to/csharp/Universities.json":::

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="9c345-151">Utf8JsonReader を使用してストリームから読み取る</span><span class="sxs-lookup"><span data-stu-id="9c345-151">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="9c345-152">大きなファイル (ギガバイト以上のサイズなど) を読み取る場合、一度にファイル全体をメモリに読み込む必要を回避することができます。</span><span class="sxs-lookup"><span data-stu-id="9c345-152">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="9c345-153">このシナリオでは、<xref:System.IO.FileStream> を使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c345-153">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="9c345-154">`Utf8JsonReader` を使用してストリームから読み取る場合、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-154">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="9c345-155">部分的な JSON ペイロードが格納されるバッファーは、リーダーが処理を進めることができるように、少なくともその中で最大の JSON トークンと同じ大きさにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c345-155">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="9c345-156">バッファーは、少なくとも JSON 内の空白の最大シーケンスと同じ大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c345-156">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="9c345-157">リーダーでは、JSON ペイロード内の次の <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> が完全に読み取られるまで、読み取られたデータが追跡されません。</span><span class="sxs-lookup"><span data-stu-id="9c345-157">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="9c345-158">そのため、バッファー内にバイトが残っている場合は、再びリーダーに渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c345-158">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="9c345-159"><xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> を使用して、残っているバイト数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9c345-159">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="9c345-160">次のコードは、ストリームから読み取る方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c345-160">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="9c345-161">この例は、<xref:System.IO.MemoryStream> を示しています。</span><span class="sxs-lookup"><span data-stu-id="9c345-161">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="9c345-162">同様のコードが <xref:System.IO.FileStream> で機能しますが、開始時に UTF-8 BOM が `FileStream` に含まれている場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="9c345-162">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="9c345-163">その場合は、残りのバイトを `Utf8JsonReader` に渡す前に、バッファーからこれらの 3 バイトを取り除く必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c345-163">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="9c345-164">そうしないと、BOM は JSON の有効な部分と見なされないため、リーダーによって例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="9c345-164">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="9c345-165">このサンプル コードでは、4 KB のバッファーから開始し、サイズが完全な JSON トークンに対応するのに十分な大きさではないことが判明するたびにバッファー サイズを 2 倍にします。これは、リーダーが JSON ペイロードの処理を進めるために必要です。</span><span class="sxs-lookup"><span data-stu-id="9c345-165">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="9c345-166">スニペットに用意されている JSON サンプルでは、非常に小さい初期バッファー サイズ (たとえば、10 バイト) を設定した場合にのみ、バッファー サイズが増加します。</span><span class="sxs-lookup"><span data-stu-id="9c345-166">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="9c345-167">初期バッファー サイズを 10 に設定すると、`Console.WriteLine` ステートメントによって、バッファー サイズの増加の原因と影響が示されます。</span><span class="sxs-lookup"><span data-stu-id="9c345-167">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="9c345-168">4 KB の初期バッファー サイズで、サンプルの JSON 全体が各 `Console.WriteLine` によって表示され、バッファー サイズを増やす必要はありません。</span><span class="sxs-lookup"><span data-stu-id="9c345-168">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs":::

<span data-ttu-id="9c345-169">前の例では、バッファーを拡大できる最大の大きさを無制限に設定しています。</span><span class="sxs-lookup"><span data-stu-id="9c345-169">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="9c345-170">トークン サイズが大きすぎる場合、コードは <xref:System.OutOfMemoryException> 例外で失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9c345-170">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="9c345-171">これは、JSON にサイズが約 1 GB 以上のトークンが含まれている場合に発生する可能性があります。1 GB のサイズを 2 倍にすると、サイズが大きすぎて `int32` バッファーに入り切らないためです。</span><span class="sxs-lookup"><span data-stu-id="9c345-171">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c345-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c345-172">See also</span></span>

* [<span data-ttu-id="9c345-173">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="9c345-173">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="9c345-174">文字エンコードをカスタマイズする方法</span><span class="sxs-lookup"><span data-stu-id="9c345-174">How to customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="9c345-175">JSON シリアル化のためのカスタム コンバーターを作成する方法</span><span class="sxs-lookup"><span data-stu-id="9c345-175">How to write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="9c345-176">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="9c345-176">[System.Text.Json API reference](xref:System.Text.Json)</span></span>