---
title: TimeOffset support in での DateTime と DateTimeOffset のサポート
description: System.string ライブラリでの DateTime 型と DateTimeOffset 型のサポートの概要について説明します。
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 04e0e3c613b194ac85241d50d3bc5fd5dc0b6e54
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977325"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="35c39-103">TimeOffset support in での DateTime と DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="35c39-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="35c39-104">System.string ライブラリは、ISO 8601:-2019 拡張プロファイルに従って、<xref:System.DateTime> と <xref:System.DateTimeOffset> の値を解析して書き込みます。</span><span class="sxs-lookup"><span data-stu-id="35c39-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="35c39-105">[コンバーター](xref:System.Text.Json.Serialization.JsonConverter%601)は、<xref:System.Text.Json.JsonSerializer>によるシリアル化と逆シリアル化のためのカスタムサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="35c39-105">[Converters](xref:System.Text.Json.Serialization.JsonConverter%601) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>
<span data-ttu-id="35c39-106"><xref:System.Text.Json.Utf8JsonReader> と <xref:System.Text.Json.Utf8JsonWriter>を使用する場合は、カスタムサポートを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="35c39-106">Custom support can also be implemented when using <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="35c39-107">ISO 8601-1:2019 形式のサポート</span><span class="sxs-lookup"><span data-stu-id="35c39-107">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="35c39-108"><xref:System.Text.Json.JsonSerializer>、<xref:System.Text.Json.Utf8JsonReader>、<xref:System.Text.Json.Utf8JsonWriter>、および <xref:System.Text.Json.JsonElement> の種類では、ISO 8601-1:2019 形式の拡張プロファイルに従って、<xref:System.DateTime> と <xref:System.DateTimeOffset> のテキスト表現を解析して記述します。たとえば、2019-07-26T16:59:57-05:00 のようになります。</span><span class="sxs-lookup"><span data-stu-id="35c39-108">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="35c39-109"><xref:System.DateTime> と <xref:System.DateTimeOffset> のデータは <xref:System.Text.Json.JsonSerializer>でシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="35c39-109"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

<span data-ttu-id="35c39-110">また、<xref:System.Text.Json.JsonSerializer>で逆シリアル化することもできます。</span><span class="sxs-lookup"><span data-stu-id="35c39-110">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

<span data-ttu-id="35c39-111">既定のオプションでは、入力 <xref:System.DateTime> と <xref:System.DateTimeOffset> テキスト表現は、拡張 ISO 8601-1:2019 プロファイルに準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="35c39-111">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="35c39-112">プロファイルに準拠していない表現を逆シリアル化しようとすると、<xref:System.Text.Json.JsonSerializer> によって <xref:System.Text.Json.JsonException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35c39-112">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<span data-ttu-id="35c39-113"><xref:System.Text.Json.JsonDocument> は、<xref:System.DateTime> や <xref:System.DateTimeOffset> 表現など、JSON ペイロードのコンテンツへの構造化されたアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="35c39-113">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="35c39-114">次の例では、温度のコレクションを指定した場合に、月曜日の平均温度を計算できる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="35c39-114">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

<span data-ttu-id="35c39-115">準拠していない <xref:System.DateTime> 表現を持つペイロードで平均温度を計算しようとすると、<xref:System.Text.Json.JsonDocument> によって <xref:System.FormatException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35c39-115">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

<span data-ttu-id="35c39-116">下位レベルの <xref:System.Text.Json.Utf8JsonWriter> は、データ <xref:System.DateTime> と <xref:System.DateTimeOffset> を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="35c39-116">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<span data-ttu-id="35c39-117"><xref:System.Text.Json.Utf8JsonReader> は、<xref:System.DateTime> と <xref:System.DateTimeOffset> データを解析します。</span><span class="sxs-lookup"><span data-stu-id="35c39-117"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

<span data-ttu-id="35c39-118"><xref:System.Text.Json.Utf8JsonReader> に準拠していない形式を読み取ろうとすると、<xref:System.FormatException>がスローされます。</span><span class="sxs-lookup"><span data-stu-id="35c39-118">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a><span data-ttu-id="35c39-119"><xref:System.DateTime> および <xref:System.DateTimeOffset> のカスタムサポート</span><span class="sxs-lookup"><span data-stu-id="35c39-119">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset></span></span>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="35c39-120"><xref:System.Text.Json.JsonSerializer> を使用する場合</span><span class="sxs-lookup"><span data-stu-id="35c39-120">When using <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="35c39-121">シリアライザーでカスタムの解析または書式設定を実行する場合は、[カスタムコンバーター](xref:System.Text.Json.Serialization.JsonConverter%601)を実装できます。</span><span class="sxs-lookup"><span data-stu-id="35c39-121">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](xref:System.Text.Json.Serialization.JsonConverter%601).</span></span>
<span data-ttu-id="35c39-122">いくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="35c39-122">Here are a few examples:</span></span>

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="35c39-123">`DateTime(Offset).Parse` と `DateTime(Offset).ToString` の使用</span><span class="sxs-lookup"><span data-stu-id="35c39-123">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="35c39-124">入力 <xref:System.DateTime> の形式や <xref:System.DateTimeOffset> テキスト表現を特定できない場合は、コンバーターの読み取りロジックで `DateTime(Offset).Parse` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35c39-124">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="35c39-125">これにより、を使用できるようになります。さまざまな <xref:System.DateTime> および <xref:System.DateTimeOffset> テキスト形式を解析するための広範なサポート (ISO 8601 以外の文字列や iso 8601 形式の拡張 ISO 8601-1:2019 プロファイルに準拠していない)。</span><span class="sxs-lookup"><span data-stu-id="35c39-125">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="35c39-126">この方法では、シリアライザーのネイティブ実装よりもパフォーマンスが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="35c39-126">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="35c39-127">シリアル化の場合は、コンバーター書き込みロジックで `DateTime(Offset).ToString` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35c39-127">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="35c39-128">これにより、[標準の日付と時刻の形式](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)、および[カスタムの日付と時刻](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)の形式を使用して、<xref:System.DateTime> と <xref:System.DateTimeOffset> の値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="35c39-128">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="35c39-129">これは、シリアライザーのネイティブ実装を使用する場合よりも、パフォーマンスが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="35c39-129">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="35c39-130"><xref:System.Text.Json.Serialization.JsonConverter%601>を実装し、`T` を <xref:System.DateTime>場合、`typeToConvert` パラメーターは常に `typeof(DateTime)`になります。</span><span class="sxs-lookup"><span data-stu-id="35c39-130">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="35c39-131">パラメーターは、ポリモーフィックなケースを処理する場合や、ジェネリックを使用してパフォーマンスの高い方法で `typeof(T)` を取得する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="35c39-131">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="35c39-132"><xref:System.Buffers.Text.Utf8Parser> と <xref:System.Buffers.Text.Utf8Formatter> の使用</span><span class="sxs-lookup"><span data-stu-id="35c39-132">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="35c39-133">入力 <xref:System.DateTime> または <xref:System.DateTimeOffset> テキスト表現が "R"、"l"、"O"、"G" のいずれかの[標準の日時書式指定文字列](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)に準拠している場合、またはこれらの形式のいずれかに従って記述する場合は、コンバーターロジックで utf-8 ベースの高速な解析および書式指定メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35c39-133">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="35c39-134">これは `DateTime(Offset).Parse` と `DateTime(Offset).ToString`を使用するよりもはるかに高速です。</span><span class="sxs-lookup"><span data-stu-id="35c39-134">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="35c39-135">次の例は、 ["R" 標準形式](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier)に従って <xref:System.DateTime> 値をシリアル化および逆シリアル化するカスタムコンバーターを示しています。</span><span class="sxs-lookup"><span data-stu-id="35c39-135">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="35c39-136">"R" 標準形式の長さは常に29文字です。</span><span class="sxs-lookup"><span data-stu-id="35c39-136">The "R" standard format will always be 29 characters long.</span></span>

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="35c39-137">シリアライザーのネイティブ解析へのフォールバックとしての `DateTime(Offset).Parse` の使用</span><span class="sxs-lookup"><span data-stu-id="35c39-137">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="35c39-138">入力 <xref:System.DateTime> または <xref:System.DateTimeOffset> データが拡張 ISO 8601-1:2019 プロファイルに準拠していると予想される場合は、シリアライザーのネイティブ解析ロジックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="35c39-138">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="35c39-139">また、場合によっては、フォールバックメカニズムを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="35c39-139">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="35c39-140">この例では、<xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>を使用して <xref:System.DateTime> テキスト表現の解析に失敗した後、コンバーターが <xref:System.DateTime.Parse(System.String)>を使用してデータを正常に解析することを示しています。</span><span class="sxs-lookup"><span data-stu-id="35c39-140">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a><span data-ttu-id="35c39-141"><xref:System.Text.Json.Utf8JsonWriter> を使用して書き込む場合</span><span class="sxs-lookup"><span data-stu-id="35c39-141">When writing with <xref:System.Text.Json.Utf8JsonWriter></span></span>

<span data-ttu-id="35c39-142">カスタム <xref:System.DateTime> を作成する場合、または <xref:System.Text.Json.Utf8JsonWriter>でテキスト表現を <xref:System.DateTimeOffset> する場合は、カスタム表現を <xref:System.String>、`ReadOnlySpan<Byte>`、`ReadOnlySpan<Char>`、または <xref:System.Text.Json.JsonEncodedText>に書式設定し、それを対応する[Utf8JsonWriter](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0)または[WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0)メソッドに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="35c39-142">If you want to write a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonWriter>, you can format your custom representation to a <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`, or <xref:System.Text.Json.JsonEncodedText>, then pass it to the corresponding [Utf8JsonWriter.WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) or [Utf8JsonWriter.WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) method.</span></span>

<span data-ttu-id="35c39-143">次の例では、<xref:System.DateTime.ToString(System.String,System.IFormatProvider)>でカスタムの <xref:System.DateTime> 形式を作成し、<xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> メソッドを使用して記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35c39-143">The following example shows how a custom <xref:System.DateTime> format can be created with <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>, then written with the <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> method:</span></span>

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a><span data-ttu-id="35c39-144"><xref:System.Text.Json.Utf8JsonReader> を使用した読み取り時</span><span class="sxs-lookup"><span data-stu-id="35c39-144">When reading with <xref:System.Text.Json.Utf8JsonReader></span></span>

<span data-ttu-id="35c39-145">カスタム <xref:System.DateTime> を読み取る場合や、<xref:System.Text.Json.Utf8JsonReader>でテキスト表現を <xref:System.DateTimeOffset> する場合は、<xref:System.Text.Json.Utf8JsonReader.GetString>を使用して現在の JSON トークンの値を <xref:System.String> として取得し、その値をカスタムロジックを使用して解析することができます。</span><span class="sxs-lookup"><span data-stu-id="35c39-145">If you want to read a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonReader>, you can get the value of the current JSON token as a <xref:System.String> using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parse the value using custom logic.</span></span>

<span data-ttu-id="35c39-146">次の例では、<xref:System.Text.Json.Utf8JsonReader.GetString>を使用してカスタム <xref:System.DateTimeOffset> テキスト表現を取得し、<xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>を使用して解析する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="35c39-146">The following example shows how a custom <xref:System.DateTimeOffset> text representation can be retrieved using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parsed using <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:</span></span>

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="35c39-147">System.string の拡張された ISO 8601-1:2019 プロファイル</span><span class="sxs-lookup"><span data-stu-id="35c39-147">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="35c39-148">日付と時刻のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="35c39-148">Date and time components</span></span>

<span data-ttu-id="35c39-149"><xref:System.Text.Json> で実装されている拡張 ISO 8601-1:2019 プロファイルは、日付と時刻の表現に対して次のコンポーネントを定義します。</span><span class="sxs-lookup"><span data-stu-id="35c39-149">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="35c39-150">これらのコンポーネントは、<xref:System.DateTime> と <xref:System.DateTimeOffset> 表現を解析および書式設定するときにサポートされるさまざまな粒度レベルを定義するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="35c39-150">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="35c39-151">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="35c39-151">Component</span></span>       | <span data-ttu-id="35c39-152">形式</span><span class="sxs-lookup"><span data-stu-id="35c39-152">Format</span></span>                      | <span data-ttu-id="35c39-153">説明</span><span class="sxs-lookup"><span data-stu-id="35c39-153">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="35c39-154">Year</span><span class="sxs-lookup"><span data-stu-id="35c39-154">Year</span></span>            | <span data-ttu-id="35c39-155">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="35c39-155">"yyyy"</span></span>                      | <span data-ttu-id="35c39-156">0001-9999</span><span class="sxs-lookup"><span data-stu-id="35c39-156">0001-9999</span></span>                                                                       |
| <span data-ttu-id="35c39-157">月</span><span class="sxs-lookup"><span data-stu-id="35c39-157">Month</span></span>           | <span data-ttu-id="35c39-158">"MM"</span><span class="sxs-lookup"><span data-stu-id="35c39-158">"MM"</span></span>                        | <span data-ttu-id="35c39-159">01-12</span><span class="sxs-lookup"><span data-stu-id="35c39-159">01-12</span></span>                                                                           |
| <span data-ttu-id="35c39-160">Day</span><span class="sxs-lookup"><span data-stu-id="35c39-160">Day</span></span>             | <span data-ttu-id="35c39-161">"dd"</span><span class="sxs-lookup"><span data-stu-id="35c39-161">"dd"</span></span>                        | <span data-ttu-id="35c39-162">01-28、01-29、01-30、01-31 (月/年)</span><span class="sxs-lookup"><span data-stu-id="35c39-162">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="35c39-163">Hour</span><span class="sxs-lookup"><span data-stu-id="35c39-163">Hour</span></span>            | <span data-ttu-id="35c39-164">"HH"</span><span class="sxs-lookup"><span data-stu-id="35c39-164">"HH"</span></span>                        | <span data-ttu-id="35c39-165">00-23</span><span class="sxs-lookup"><span data-stu-id="35c39-165">00-23</span></span>                                                                           |
| <span data-ttu-id="35c39-166">Minute</span><span class="sxs-lookup"><span data-stu-id="35c39-166">Minute</span></span>          | <span data-ttu-id="35c39-167">"mm"</span><span class="sxs-lookup"><span data-stu-id="35c39-167">"mm"</span></span>                        | <span data-ttu-id="35c39-168">00-59</span><span class="sxs-lookup"><span data-stu-id="35c39-168">00-59</span></span>                                                                           |
| <span data-ttu-id="35c39-169">Second</span><span class="sxs-lookup"><span data-stu-id="35c39-169">Second</span></span>          | <span data-ttu-id="35c39-170">"ss"</span><span class="sxs-lookup"><span data-stu-id="35c39-170">"ss"</span></span>                        | <span data-ttu-id="35c39-171">00-59</span><span class="sxs-lookup"><span data-stu-id="35c39-171">00-59</span></span>                                                                           |
| <span data-ttu-id="35c39-172">2番目の分数</span><span class="sxs-lookup"><span data-stu-id="35c39-172">Second fraction</span></span> | <span data-ttu-id="35c39-173">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="35c39-173">"FFFFFFF"</span></span>                   | <span data-ttu-id="35c39-174">最低1桁、最大16桁</span><span class="sxs-lookup"><span data-stu-id="35c39-174">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="35c39-175">時間のオフセット</span><span class="sxs-lookup"><span data-stu-id="35c39-175">Time offset</span></span>     | <span data-ttu-id="35c39-176">"K"</span><span class="sxs-lookup"><span data-stu-id="35c39-176">"K"</span></span>                         | <span data-ttu-id="35c39-177">"Z" または "(' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="35c39-177">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="35c39-178">部分的な時間</span><span class="sxs-lookup"><span data-stu-id="35c39-178">Partial time</span></span>    | <span data-ttu-id="35c39-179">"HH ': ' mm ': ' ss [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="35c39-179">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="35c39-180">UTC オフセット情報なしの時間</span><span class="sxs-lookup"><span data-stu-id="35c39-180">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="35c39-181">完全な日付</span><span class="sxs-lookup"><span data-stu-id="35c39-181">Full date</span></span>       | <span data-ttu-id="35c39-182">"yyyy'-'mm'-'dd't'hh-' MM'-' dd"</span><span class="sxs-lookup"><span data-stu-id="35c39-182">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="35c39-183">カレンダーの日付</span><span class="sxs-lookup"><span data-stu-id="35c39-183">Calendar date</span></span>                                                                   |
| <span data-ttu-id="35c39-184">フルタイム</span><span class="sxs-lookup"><span data-stu-id="35c39-184">Full time</span></span>       | <span data-ttu-id="35c39-185">"Partial time'K"</span><span class="sxs-lookup"><span data-stu-id="35c39-185">"'Partial time'K"</span></span>           | <span data-ttu-id="35c39-186">現地時刻と UTC の時差を使用した日の UTC または現地時刻</span><span class="sxs-lookup"><span data-stu-id="35c39-186">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="35c39-187">日付/時刻</span><span class="sxs-lookup"><span data-stu-id="35c39-187">Date time</span></span>       | <span data-ttu-id="35c39-188">"' 完全な日付 ' ' ' ' ' ' ' は完全な時刻 '" になります。</span><span class="sxs-lookup"><span data-stu-id="35c39-188">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="35c39-189">カレンダーの日付と時刻。例: 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="35c39-189">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="35c39-190">解析のサポート</span><span class="sxs-lookup"><span data-stu-id="35c39-190">Support for parsing</span></span>

<span data-ttu-id="35c39-191">解析のために次の粒度のレベルが定義されています。</span><span class="sxs-lookup"><span data-stu-id="35c39-191">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="35c39-192">' 完全な日付 '</span><span class="sxs-lookup"><span data-stu-id="35c39-192">'Full date'</span></span>
    1. <span data-ttu-id="35c39-193">"yyyy'-'mm'-'dd't'hh-' MM'-' dd"</span><span class="sxs-lookup"><span data-stu-id="35c39-193">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="35c39-194">"' Full date ' ' ' Hour ' ': ' ' Minute '"</span><span class="sxs-lookup"><span data-stu-id="35c39-194">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="35c39-195">"yyyy'-'mm'-'dd't'hh-' MM'-' + ': ' MM '</span><span class="sxs-lookup"><span data-stu-id="35c39-195">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="35c39-196">"' 完全な日付 ' t ' ' Partial time '"</span><span class="sxs-lookup"><span data-stu-id="35c39-196">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="35c39-197">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="35c39-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="35c39-198">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="35c39-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="35c39-199">"' Full date ' ' ' Time Time ' ': ' ' Minute ' ' Time offset '"</span><span class="sxs-lookup"><span data-stu-id="35c39-199">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="35c39-200">"yyyy'-'mm'-'dd't'hh-" MM'-' Dd' T' HH ': ' mmZ "</span><span class="sxs-lookup"><span data-stu-id="35c39-200">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="35c39-201">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' Hh ': ' mm (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="35c39-201">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="35c39-202">' 日時 '</span><span class="sxs-lookup"><span data-stu-id="35c39-202">'Date time'</span></span>
    1. <span data-ttu-id="35c39-203">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="35c39-203">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="35c39-204">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "</span><span class="sxs-lookup"><span data-stu-id="35c39-204">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="35c39-205">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="35c39-205">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="35c39-206">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="35c39-206">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="35c39-207">秒の小数部がある場合は、少なくとも1つの数字が必要です。`2019-07-26T00:00:00.` は許可されていません。</span><span class="sxs-lookup"><span data-stu-id="35c39-207">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="35c39-208">最大16桁の小数部を使用できますが、最初の7だけが解析されます。</span><span class="sxs-lookup"><span data-stu-id="35c39-208">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="35c39-209">それを超えるものはゼロと見なされます。</span><span class="sxs-lookup"><span data-stu-id="35c39-209">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="35c39-210">たとえば、`2019-07-26T00:00:00.1234567890` は `2019-07-26T00:00:00.1234567`であるかのように解析されます。</span><span class="sxs-lookup"><span data-stu-id="35c39-210">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="35c39-211">これは、この解決に限定される <xref:System.DateTime> の実装との互換性を維持するためのものです。</span><span class="sxs-lookup"><span data-stu-id="35c39-211">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="35c39-212">うるう秒はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="35c39-212">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="35c39-213">書式設定のサポート</span><span class="sxs-lookup"><span data-stu-id="35c39-213">Support for formatting</span></span>

<span data-ttu-id="35c39-214">次の粒度レベルは、書式設定のために定義されています。</span><span class="sxs-lookup"><span data-stu-id="35c39-214">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="35c39-215">"' 完全な日付 ' t ' ' Partial time '"</span><span class="sxs-lookup"><span data-stu-id="35c39-215">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="35c39-216">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="35c39-216">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="35c39-217">秒の小数部を含まない <xref:System.DateTime> の書式を設定し、オフセット情報を使用しないようにします。</span><span class="sxs-lookup"><span data-stu-id="35c39-217">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="35c39-218">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="35c39-218">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="35c39-219">秒の小数部のオフセット情報を含まない <xref:System.DateTime> の書式を設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="35c39-219">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="35c39-220">' 日時 '</span><span class="sxs-lookup"><span data-stu-id="35c39-220">'Date time'</span></span>
    1. <span data-ttu-id="35c39-221">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="35c39-221">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="35c39-222">秒の小数部を除いて、UTC オフセットを使用して <xref:System.DateTime> を書式設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="35c39-222">Used to format a <xref:System.DateTime> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="35c39-223">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "</span><span class="sxs-lookup"><span data-stu-id="35c39-223">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="35c39-224">秒の小数部と UTC オフセットを使用して <xref:System.DateTime> の書式を設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="35c39-224">Used to format a <xref:System.DateTime> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="35c39-225">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="35c39-225">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="35c39-226">秒の小数部を除いて、ローカルオフセットを使用して、<xref:System.DateTime> または <xref:System.DateTimeOffset> を書式設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="35c39-226">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="35c39-227">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="35c39-227">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="35c39-228">秒の小数部とローカルオフセットを使用して、<xref:System.DateTime> または <xref:System.DateTimeOffset> の書式を設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="35c39-228">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>

<span data-ttu-id="35c39-229">存在する場合は、最大7桁の小数部が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="35c39-229">If present, a maximum of 7 fractional digits are written.</span></span> <span data-ttu-id="35c39-230">これは、この解決に限定される <xref:System.DateTime> の実装と一致します。</span><span class="sxs-lookup"><span data-stu-id="35c39-230">This aligns with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>
