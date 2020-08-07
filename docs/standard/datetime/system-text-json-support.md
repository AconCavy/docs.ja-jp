---
title: TimeOffset support in での DateTime と DateTimeOffset のサポート
description: System.Text.Jsのライブラリでの DateTime 型と DateTimeOffset 型のサポートの概要について説明します。
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
ms.openlocfilehash: 1c573712f458d3e22cd59112b9e79e85391270c1
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854894"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="e3d23-103">TimeOffset support in での DateTime と DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="e3d23-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="e3d23-104">ライブラリの System.Text.Jsは、 <xref:System.DateTime> <xref:System.DateTimeOffset> ISO 8601:-2019 拡張プロファイルに従って、との値を解析して書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="e3d23-105">[コンバーター](xref:System.Text.Json.Serialization.JsonConverter%601)は、を使用したシリアル化と逆シリアル化のためのカスタムサポートを提供 <xref:System.Text.Json.JsonSerializer> します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-105">[Converters](xref:System.Text.Json.Serialization.JsonConverter%601) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>
<span data-ttu-id="e3d23-106">およびを使用する場合は、カスタムサポートを実装することもでき <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-106">Custom support can also be implemented when using <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="e3d23-107">ISO 8601-1:2019 形式のサポート</span><span class="sxs-lookup"><span data-stu-id="e3d23-107">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="e3d23-108">、、、およびの各型は、 <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonReader> <xref:System.Text.Json.Utf8JsonWriter> <xref:System.Text.Json.JsonElement> <xref:System.DateTime> <xref:System.DateTimeOffset> ISO 8601-1:2019 形式の拡張プロファイルに従って、解析および書き込みとテキスト表現を行います。たとえば、2019-07-26t16:59:57-05:00 のようになります。</span><span class="sxs-lookup"><span data-stu-id="e3d23-108">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="e3d23-109"><xref:System.DateTime>および <xref:System.DateTimeOffset> データは、次の方法でシリアル化でき <xref:System.Text.Json.JsonSerializer> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-109"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

<span data-ttu-id="e3d23-110">また、次のようにして逆シリアル化することもでき <xref:System.Text.Json.JsonSerializer> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-110">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

<span data-ttu-id="e3d23-111">既定のオプションでは、入力 <xref:System.DateTime> および <xref:System.DateTimeOffset> テキスト表現は拡張 ISO 8601-1:2019 プロファイルに準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3d23-111">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="e3d23-112">プロファイルに準拠していない表現を逆シリアル化しようとすると、がスローされ <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-112">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<span data-ttu-id="e3d23-113">は、 <xref:System.Text.Json.JsonDocument> JSON ペイロードの内容 (や表現を含む) への構造化されたアクセスを提供し <xref:System.DateTime> <xref:System.DateTimeOffset> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-113">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="e3d23-114">次の例では、温度のコレクションを指定した場合に、月曜日の平均温度を計算できる方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e3d23-114">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

<span data-ttu-id="e3d23-115">準拠していない形式のペイロードで平均温度を計算しようとすると、がを <xref:System.DateTime> <xref:System.Text.Json.JsonDocument> スローし <xref:System.FormatException> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-115">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

<span data-ttu-id="e3d23-116">下位レベルの <xref:System.Text.Json.Utf8JsonWriter> 書き込み <xref:System.DateTime> と <xref:System.DateTimeOffset> データ:</span><span class="sxs-lookup"><span data-stu-id="e3d23-116">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<span data-ttu-id="e3d23-117"><xref:System.Text.Json.Utf8JsonReader><xref:System.DateTime>とデータを解析し <xref:System.DateTimeOffset> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-117"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

<span data-ttu-id="e3d23-118">に準拠していない形式を読み取ろうとすると <xref:System.Text.Json.Utf8JsonReader> 、がスローされ <xref:System.FormatException> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-118">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a><span data-ttu-id="e3d23-119">およびのカスタムサポート <xref:System.DateTime><xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="e3d23-119">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset></span></span>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="e3d23-120">使用する場合<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="e3d23-120">When using <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="e3d23-121">シリアライザーでカスタムの解析または書式設定を実行する場合は、[カスタムコンバーター](xref:System.Text.Json.Serialization.JsonConverter%601)を実装できます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-121">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](xref:System.Text.Json.Serialization.JsonConverter%601).</span></span>
<span data-ttu-id="e3d23-122">次に例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-122">Here are a few examples:</span></span>

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="e3d23-123">およびを使用する `DateTime(Offset).Parse``DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="e3d23-123">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="e3d23-124">入力またはテキスト表現の形式を特定できない場合は <xref:System.DateTime> <xref:System.DateTimeOffset> 、 `DateTime(Offset).Parse` コンバーターの読み取りロジックでメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-124">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="e3d23-125">これにより、を使用できるようになります。さまざまな <xref:System.DateTime> 形式とテキスト形式のサポート <xref:System.DateTimeOffset> (iso 8601 以外の文字列や iso 8601 形式の拡張 iso 8601-1:2019 プロファイルに準拠していないなど) のサポート。</span><span class="sxs-lookup"><span data-stu-id="e3d23-125">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="e3d23-126">この方法では、シリアライザーのネイティブ実装よりもパフォーマンスが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-126">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="e3d23-127">シリアル化の場合は、 `DateTime(Offset).ToString` コンバーターの書き込みロジックでメソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-127">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="e3d23-128">これにより、 <xref:System.DateTime> 標準の <xref:System.DateTimeOffset> [日付と時刻の形式](../base-types/standard-date-and-time-format-strings.md)、および[カスタムの日付と時刻](../base-types/custom-date-and-time-format-strings.md)の書式を使用して、との値を書き込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-128">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](../base-types/standard-date-and-time-format-strings.md), and the [custom date and time formats](../base-types/custom-date-and-time-format-strings.md).</span></span>
<span data-ttu-id="e3d23-129">これは、シリアライザーのネイティブ実装を使用する場合よりも、パフォーマンスが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-129">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="e3d23-130">を実装するとき、およびがの場合、 <xref:System.Text.Json.Serialization.JsonConverter%601> `T` パラメーターは <xref:System.DateTime> `typeToConvert` 常にになり `typeof(DateTime)` ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-130">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="e3d23-131">パラメーターは、ポリモーフィックなケースを処理する場合や、ジェネリックを使用してパフォーマンスの高い方法を実現する場合に便利です `typeof(T)` 。</span><span class="sxs-lookup"><span data-stu-id="e3d23-131">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="e3d23-132">およびを使用する <xref:System.Buffers.Text.Utf8Parser><xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="e3d23-132">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="e3d23-133">入力 <xref:System.DateTime> または <xref:System.DateTimeOffset> テキスト表現が "R"、"l"、"O"、"G" のいずれかの[日付/時刻書式指定文字列](../base-types/standard-date-and-time-format-strings.md)に準拠している場合、またはこれらの形式のいずれかに従って記述する場合は、コンバーターロジックで utf-8 ベースの高速な解析および書式指定メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-133">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format strings](../base-types/standard-date-and-time-format-strings.md), or you want to write according to one of these formats.</span></span> <span data-ttu-id="e3d23-134">これは、およびを使用するよりもはるかに高速です `DateTime(Offset).Parse` `DateTime(Offset).ToString` 。</span><span class="sxs-lookup"><span data-stu-id="e3d23-134">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="e3d23-135">次の例は、 <xref:System.DateTime> ["R" 標準形式](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier)に従って値をシリアル化および逆シリアル化するカスタムコンバーターを示しています。</span><span class="sxs-lookup"><span data-stu-id="e3d23-135">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="e3d23-136">"R" 標準形式の長さは常に29文字です。</span><span class="sxs-lookup"><span data-stu-id="e3d23-136">The "R" standard format will always be 29 characters long.</span></span>
>
> <span data-ttu-id="e3d23-137">"L" (小文字の "L") 形式は、および型でのみサポートされているため、他の[標準の日時書式指定文字列](../base-types/standard-date-and-time-format-strings.md)には記載されていません `Utf8Parser` `Utf8Formatter` 。</span><span class="sxs-lookup"><span data-stu-id="e3d23-137">The "l" (lowercase "L") format is not documented with the other [standard date and time format strings](../base-types/standard-date-and-time-format-strings.md) because it is supported only by the `Utf8Parser` and `Utf8Formatter` types.</span></span> <span data-ttu-id="e3d23-138">形式は、小文字の RFC 1123 ("R" 形式の小文字バージョン) です。たとえば、"thu, 25 月 2019 06:36:07 gmt" のようになります。</span><span class="sxs-lookup"><span data-stu-id="e3d23-138">The format is lowercase RFC 1123 (a lowercase version of the "R" format), for example: "thu, 25 jul 2019 06:36:07 gmt".</span></span>

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="e3d23-139">`DateTime(Offset).Parse`シリアライザーのネイティブ解析へのフォールバックとしての使用</span><span class="sxs-lookup"><span data-stu-id="e3d23-139">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="e3d23-140">通常、入力 <xref:System.DateTime> またはデータが <xref:System.DateTimeOffset> 拡張 ISO 8601-1:2019 プロファイルに準拠していることが予想される場合は、シリアライザーのネイティブ解析ロジックを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-140">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="e3d23-141">また、場合によっては、フォールバックメカニズムを実装することもできます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-141">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="e3d23-142">この例では、を使用してテキスト表現の解析に失敗した後に、 <xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> コンバーターがを使用してデータを正常に解析することを示して <xref:System.DateTime.Parse(System.String)> います。</span><span class="sxs-lookup"><span data-stu-id="e3d23-142">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a><span data-ttu-id="e3d23-143">書き込み時に<xref:System.Text.Json.Utf8JsonWriter></span><span class="sxs-lookup"><span data-stu-id="e3d23-143">When writing with <xref:System.Text.Json.Utf8JsonWriter></span></span>

<span data-ttu-id="e3d23-144">でカスタムまたはテキスト表現を記述する場合は、 <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.Text.Json.Utf8JsonWriter> カスタム表現を <xref:System.String> 、、 `ReadOnlySpan<Byte>` 、またはに書式設定 `ReadOnlySpan<Char>` <xref:System.Text.Json.JsonEncodedText> し、それを対応するメソッドまたはメソッドに渡すことができ <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-144">If you want to write a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonWriter>, you can format your custom representation to a <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`, or <xref:System.Text.Json.JsonEncodedText>, then pass it to the corresponding <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> or <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="e3d23-145">次の例では、を使用してカスタム <xref:System.DateTime> 書式を作成 <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> し、メソッドを使用して記述する方法を示し <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-145">The following example shows how a custom <xref:System.DateTime> format can be created with <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>, then written with the <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> method:</span></span>

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a><span data-ttu-id="e3d23-146">読み取り時の<xref:System.Text.Json.Utf8JsonReader></span><span class="sxs-lookup"><span data-stu-id="e3d23-146">When reading with <xref:System.Text.Json.Utf8JsonReader></span></span>

<span data-ttu-id="e3d23-147">を使用してカスタムまたはテキスト表現を読み取る場合は、 <xref:System.DateTime> <xref:System.DateTimeOffset> 現在の <xref:System.Text.Json.Utf8JsonReader> JSON トークンの値をを使用して取得し <xref:System.String> 、その値を <xref:System.Text.Json.Utf8JsonReader.GetString> カスタムロジックを使用して解析することができます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-147">If you want to read a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonReader>, you can get the value of the current JSON token as a <xref:System.String> using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parse the value using custom logic.</span></span>

<span data-ttu-id="e3d23-148">次の例は、を使用してカスタム <xref:System.DateTimeOffset> テキスト表現を取得し <xref:System.Text.Json.Utf8JsonReader.GetString> 、を使用して解析する方法を示してい <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-148">The following example shows how a custom <xref:System.DateTimeOffset> text representation can be retrieved using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parsed using <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:</span></span>

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="e3d23-149">System.Text.Jsの拡張 ISO 8601-1:2019 プロファイル</span><span class="sxs-lookup"><span data-stu-id="e3d23-149">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="e3d23-150">日付と時刻のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="e3d23-150">Date and time components</span></span>

<span data-ttu-id="e3d23-151">で実装されている拡張 ISO 8601-1:2019 プロファイルは、 <xref:System.Text.Json> 日付と時刻の表現に関して次のコンポーネントを定義します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-151">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="e3d23-152">これらのコンポーネントは、解析と書式設定および表現の際にサポートされるさまざまな粒度レベルを定義するために使用され <xref:System.DateTime> <xref:System.DateTimeOffset> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-152">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="e3d23-153">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="e3d23-153">Component</span></span>       | <span data-ttu-id="e3d23-154">Format</span><span class="sxs-lookup"><span data-stu-id="e3d23-154">Format</span></span>                      | <span data-ttu-id="e3d23-155">説明</span><span class="sxs-lookup"><span data-stu-id="e3d23-155">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="e3d23-156">年</span><span class="sxs-lookup"><span data-stu-id="e3d23-156">Year</span></span>            | <span data-ttu-id="e3d23-157">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="e3d23-157">"yyyy"</span></span>                      | <span data-ttu-id="e3d23-158">0001-9999</span><span class="sxs-lookup"><span data-stu-id="e3d23-158">0001-9999</span></span>                                                                       |
| <span data-ttu-id="e3d23-159">Month</span><span class="sxs-lookup"><span data-stu-id="e3d23-159">Month</span></span>           | <span data-ttu-id="e3d23-160">"MM"</span><span class="sxs-lookup"><span data-stu-id="e3d23-160">"MM"</span></span>                        | <span data-ttu-id="e3d23-161">01-12</span><span class="sxs-lookup"><span data-stu-id="e3d23-161">01-12</span></span>                                                                           |
| <span data-ttu-id="e3d23-162">日間</span><span class="sxs-lookup"><span data-stu-id="e3d23-162">Day</span></span>             | <span data-ttu-id="e3d23-163">"dd"</span><span class="sxs-lookup"><span data-stu-id="e3d23-163">"dd"</span></span>                        | <span data-ttu-id="e3d23-164">01-28、01-29、01-30、01-31 (月/年)</span><span class="sxs-lookup"><span data-stu-id="e3d23-164">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="e3d23-165">時間</span><span class="sxs-lookup"><span data-stu-id="e3d23-165">Hour</span></span>            | <span data-ttu-id="e3d23-166">"HH"</span><span class="sxs-lookup"><span data-stu-id="e3d23-166">"HH"</span></span>                        | <span data-ttu-id="e3d23-167">00-23</span><span class="sxs-lookup"><span data-stu-id="e3d23-167">00-23</span></span>                                                                           |
| <span data-ttu-id="e3d23-168">分</span><span class="sxs-lookup"><span data-stu-id="e3d23-168">Minute</span></span>          | <span data-ttu-id="e3d23-169">"mm"</span><span class="sxs-lookup"><span data-stu-id="e3d23-169">"mm"</span></span>                        | <span data-ttu-id="e3d23-170">00-59</span><span class="sxs-lookup"><span data-stu-id="e3d23-170">00-59</span></span>                                                                           |
| <span data-ttu-id="e3d23-171">秒</span><span class="sxs-lookup"><span data-stu-id="e3d23-171">Second</span></span>          | <span data-ttu-id="e3d23-172">"ss"</span><span class="sxs-lookup"><span data-stu-id="e3d23-172">"ss"</span></span>                        | <span data-ttu-id="e3d23-173">00-59</span><span class="sxs-lookup"><span data-stu-id="e3d23-173">00-59</span></span>                                                                           |
| <span data-ttu-id="e3d23-174">2番目の分数</span><span class="sxs-lookup"><span data-stu-id="e3d23-174">Second fraction</span></span> | <span data-ttu-id="e3d23-175">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="e3d23-175">"FFFFFFF"</span></span>                   | <span data-ttu-id="e3d23-176">最低1桁、最大16桁</span><span class="sxs-lookup"><span data-stu-id="e3d23-176">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="e3d23-177">時間のオフセット</span><span class="sxs-lookup"><span data-stu-id="e3d23-177">Time offset</span></span>     | <span data-ttu-id="e3d23-178">"K"</span><span class="sxs-lookup"><span data-stu-id="e3d23-178">"K"</span></span>                         | <span data-ttu-id="e3d23-179">"Z" または "(' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="e3d23-179">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="e3d23-180">部分的な時間</span><span class="sxs-lookup"><span data-stu-id="e3d23-180">Partial time</span></span>    | <span data-ttu-id="e3d23-181">"HH ': ' mm ': ' ss [FFFFFFF]"</span><span class="sxs-lookup"><span data-stu-id="e3d23-181">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="e3d23-182">UTC オフセット情報なしの時間</span><span class="sxs-lookup"><span data-stu-id="e3d23-182">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="e3d23-183">完全な日付</span><span class="sxs-lookup"><span data-stu-id="e3d23-183">Full date</span></span>       | <span data-ttu-id="e3d23-184">"yyyy'-'mm'-'dd't'hh-' MM'-' dd"</span><span class="sxs-lookup"><span data-stu-id="e3d23-184">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="e3d23-185">カレンダーの日付</span><span class="sxs-lookup"><span data-stu-id="e3d23-185">Calendar date</span></span>                                                                   |
| <span data-ttu-id="e3d23-186">フルタイム</span><span class="sxs-lookup"><span data-stu-id="e3d23-186">Full time</span></span>       | <span data-ttu-id="e3d23-187">"Partial time'K"</span><span class="sxs-lookup"><span data-stu-id="e3d23-187">"'Partial time'K"</span></span>           | <span data-ttu-id="e3d23-188">現地時刻と UTC の時差を使用した日の UTC または現地時刻</span><span class="sxs-lookup"><span data-stu-id="e3d23-188">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="e3d23-189">日時</span><span class="sxs-lookup"><span data-stu-id="e3d23-189">Date time</span></span>       | <span data-ttu-id="e3d23-190">"' 完全な日付 ' ' ' ' ' ' ' は完全な時刻 '" になります。</span><span class="sxs-lookup"><span data-stu-id="e3d23-190">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="e3d23-191">カレンダーの日付と時刻。例: 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="e3d23-191">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="e3d23-192">解析のサポート</span><span class="sxs-lookup"><span data-stu-id="e3d23-192">Support for parsing</span></span>

<span data-ttu-id="e3d23-193">解析のために次の粒度のレベルが定義されています。</span><span class="sxs-lookup"><span data-stu-id="e3d23-193">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="e3d23-194">' 完全な日付 '</span><span class="sxs-lookup"><span data-stu-id="e3d23-194">'Full date'</span></span>
    1. <span data-ttu-id="e3d23-195">"yyyy'-'mm'-'dd't'hh-' MM'-' dd"</span><span class="sxs-lookup"><span data-stu-id="e3d23-195">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="e3d23-196">"' Full date ' ' ' Hour ' ': ' ' Minute '"</span><span class="sxs-lookup"><span data-stu-id="e3d23-196">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="e3d23-197">"yyyy'-'mm'-'dd't'hh-' MM'-' + ': ' MM '</span><span class="sxs-lookup"><span data-stu-id="e3d23-197">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="e3d23-198">"' 完全な日付 ' t ' ' Partial time '"</span><span class="sxs-lookup"><span data-stu-id="e3d23-198">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="e3d23-199">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="e3d23-199">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="e3d23-200">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="e3d23-200">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="e3d23-201">"' Full date ' ' ' Time Time ' ': ' ' Minute ' ' Time offset '"</span><span class="sxs-lookup"><span data-stu-id="e3d23-201">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="e3d23-202">"yyyy'-'mm'-'dd't'hh-" MM'-' Dd' T' HH ': ' mmZ "</span><span class="sxs-lookup"><span data-stu-id="e3d23-202">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="e3d23-203">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' Hh ': ' mm (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="e3d23-203">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="e3d23-204">' 日時 '</span><span class="sxs-lookup"><span data-stu-id="e3d23-204">'Date time'</span></span>
    1. <span data-ttu-id="e3d23-205">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="e3d23-205">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="e3d23-206">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "</span><span class="sxs-lookup"><span data-stu-id="e3d23-206">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="e3d23-207">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="e3d23-207">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="e3d23-208">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="e3d23-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="e3d23-209">秒の小数部がある場合は、少なくとも1つの数字が必要です。`2019-07-26T00:00:00.`は使用できません。</span><span class="sxs-lookup"><span data-stu-id="e3d23-209">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="e3d23-210">最大16桁の小数部を使用できますが、最初の7だけが解析されます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-210">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="e3d23-211">それを超えるものはゼロと見なされます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-211">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="e3d23-212">たとえば、はの `2019-07-26T00:00:00.1234567890` ように解析され `2019-07-26T00:00:00.1234567` ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-212">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="e3d23-213">これは、 <xref:System.DateTime> この解決に限定された実装との互換性を維持するためのものです。</span><span class="sxs-lookup"><span data-stu-id="e3d23-213">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="e3d23-214">うるう秒はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e3d23-214">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="e3d23-215">書式設定のサポート</span><span class="sxs-lookup"><span data-stu-id="e3d23-215">Support for formatting</span></span>

<span data-ttu-id="e3d23-216">次の粒度レベルは、書式設定のために定義されています。</span><span class="sxs-lookup"><span data-stu-id="e3d23-216">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="e3d23-217">"' 完全な日付 ' t ' ' Partial time '"</span><span class="sxs-lookup"><span data-stu-id="e3d23-217">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="e3d23-218">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="e3d23-218">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="e3d23-219"><xref:System.DateTime>秒の小数部を含まない、オフセット情報を使用せずに、を書式設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-219">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="e3d23-220">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="e3d23-220">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="e3d23-221"><xref:System.DateTime>秒の小数部のオフセット情報を使用せずに、を書式設定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-221">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="e3d23-222">' 日時 '</span><span class="sxs-lookup"><span data-stu-id="e3d23-222">'Date time'</span></span>
    1. <span data-ttu-id="e3d23-223">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="e3d23-223">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="e3d23-224">秒単位ではなく、UTC オフセットを使用して、を書式設定するために使用 <xref:System.DateTime> します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-224">Used to format a <xref:System.DateTime> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="e3d23-225">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "</span><span class="sxs-lookup"><span data-stu-id="e3d23-225">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="e3d23-226">秒の小数部を UTC オフセットで書式設定するために使用し <xref:System.DateTime> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-226">Used to format a <xref:System.DateTime> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="e3d23-227">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="e3d23-227">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="e3d23-228"><xref:System.DateTime>秒の小数部を含まない、またはローカルオフセットを使用して、またはの書式を設定するために使用 <xref:System.DateTimeOffset> します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-228">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="e3d23-229">"yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "</span><span class="sxs-lookup"><span data-stu-id="e3d23-229">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="e3d23-230"><xref:System.DateTime>秒の小数部とローカルオフセットを使用して、またはの書式を設定するために使用し <xref:System.DateTimeOffset> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-230">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>

<span data-ttu-id="e3d23-231">またはインスタンスの[ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表現の <xref:System.DateTime> <xref:System.DateTimeOffset> 秒の小数部に後続のゼロがある場合、 <xref:System.Text.Json.JsonSerializer> とは、末尾に0を <xref:System.Text.Json.Utf8JsonWriter> 付けずにインスタンスの表現を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-231">If the [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation of a <xref:System.DateTime> or <xref:System.DateTimeOffset> instance has trailing zeros in its fractional seconds, then <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter> will format a representation of the instance without trailing zeros.</span></span>
<span data-ttu-id="e3d23-232">たとえば、 <xref:System.DateTime> [ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表現がであるインスタンスは、 `2019-04-24T14:50:17.1010000Z` とによって書式設定され `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonWriter> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-232">For example, a <xref:System.DateTime> instance whose [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation is `2019-04-24T14:50:17.1010000Z`, will be formatted as `2019-04-24T14:50:17.101Z` by <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

<span data-ttu-id="e3d23-233">またはインスタンスの[ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表現で <xref:System.DateTime> 、 <xref:System.DateTimeOffset> 秒の小数部にゼロがすべて含まれている場合、 <xref:System.Text.Json.JsonSerializer> と <xref:System.Text.Json.Utf8JsonWriter> は秒の小数部なしでインスタンスの表現を書式設定します。</span><span class="sxs-lookup"><span data-stu-id="e3d23-233">If the [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation of a <xref:System.DateTime> or <xref:System.DateTimeOffset> instance has all zeros in its fractional seconds, then <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter> will format a representation of the instance without fractional seconds.</span></span>
<span data-ttu-id="e3d23-234">たとえば、 <xref:System.DateTime> [ラウンドトリップ形式](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier)表現がであるインスタンスは、 `2019-04-24T14:50:17.0000000+02:00` とによって書式設定され `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonWriter> ます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-234">For example, a <xref:System.DateTime> instance whose [round-trip format](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) representation is `2019-04-24T14:50:17.0000000+02:00`, will be formatted as `2019-04-24T14:50:17+02:00` by <xref:System.Text.Json.JsonSerializer> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

<span data-ttu-id="e3d23-235">秒の小数点以下桁数で0を切り捨てた場合、書き込まれるラウンドトリップに関する情報を保持するために必要な最小の出力が可能になります。</span><span class="sxs-lookup"><span data-stu-id="e3d23-235">Truncating zeros in fractional-second digits allows the smallest output needed to preserve information on a round trip to be written.</span></span>

<span data-ttu-id="e3d23-236">最大7桁の小数点以下桁数が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-236">A maximum of 7 fractional-second digits are written.</span></span> <span data-ttu-id="e3d23-237">これ <xref:System.DateTime> は、この解決に限定される実装に合わせて配置されます。</span><span class="sxs-lookup"><span data-stu-id="e3d23-237">This aligns with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>
