---
title: System.Text.Json でプロパティの名前と値をカスタマイズする方法
description: .NET で System.Text.Json を使用してシリアル化するときに、プロパティの名前と値をカスタマイズする方法について説明します。
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 4b88509313e719ea993e00d889bc6145f4976a2d
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008904"
---
# <a name="how-to-customize-property-names-and-values-with-no-locsystemtextjson"></a><span data-ttu-id="ab9c2-103">System.Text.Json でプロパティの名前と値をカスタマイズする方法</span><span class="sxs-lookup"><span data-stu-id="ab9c2-103">How to customize property names and values with System.Text.Json</span></span>

<span data-ttu-id="ab9c2-104">既定では、プロパティ名とディクショナリ キーは、大文字と小文字の区別を含め、JSON の出力では変更されません。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-104">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="ab9c2-105">列挙型の値は数値として表されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-105">Enum values are represented as numbers.</span></span> <span data-ttu-id="ab9c2-106">この記事では、次の方法について学習します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-106">In this article, you'll learn how to:</span></span>

> [!NOTE]
> <span data-ttu-id="ab9c2-107">[Web の既定値](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)はキャメル ケースです。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-107">The [web default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions) is camel case.</span></span>

* [<span data-ttu-id="ab9c2-108">個々のプロパティ名をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ab9c2-108">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="ab9c2-109">すべてのプロパティ名をキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-109">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="ab9c2-110">カスタム プロパティの名前付けポリシーを実装する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-110">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="ab9c2-111">ディクショナリ キーをキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-111">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="ab9c2-112">列挙型を文字列およびキャメル ケースに変換する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-112">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="ab9c2-113">JSON プロパティの名前と値の特別な処理を必要とするその他のシナリオでは、[カスタム コンバーターを実装](system-text-json-converters-how-to.md)することができます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-113">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

## <a name="customize-individual-property-names"></a><span data-ttu-id="ab9c2-114">個々のプロパティ名をカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ab9c2-114">Customize individual property names</span></span>

<span data-ttu-id="ab9c2-115">個々のプロパティの名前を設定するには、[[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-115">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="ab9c2-116">シリアル化する型と、結果として得られる JSON の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-116">Here's an example type to serialize and resulting JSON:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="ab9c2-117">この属性によって設定されるプロパティ名は:</span><span class="sxs-lookup"><span data-stu-id="ab9c2-117">The property name set by this attribute:</span></span>

* <span data-ttu-id="ab9c2-118">シリアル化と逆シリアル化の両方の方向に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-118">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="ab9c2-119">プロパティの名前付けポリシーよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-119">Takes precedence over property naming policies.</span></span>

## <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="ab9c2-120">すべての JSON プロパティ名にキャメル ケースを使用する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-120">Use camel case for all JSON property names</span></span>

<span data-ttu-id="ab9c2-121">すべての JSON プロパティ名にキャメル ケースを使用するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> を `JsonNamingPolicy.CamelCase` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-121">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs" id="Serialize":::

<span data-ttu-id="ab9c2-122">シリアル化するクラスと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-122">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="ab9c2-123">キャメル ケースのプロパティの名前付けポリシーは:</span><span class="sxs-lookup"><span data-stu-id="ab9c2-123">The camel case property naming policy:</span></span>

* <span data-ttu-id="ab9c2-124">シリアル化と逆シリアル化に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-124">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="ab9c2-125">`[JsonPropertyName]` 属性によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-125">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="ab9c2-126">このため、この例の JSON プロパティ名 `Wind` はキャメル ケースではありません。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-126">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

## <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="ab9c2-127">カスタム JSON プロパティの名前付けポリシーを使用する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-127">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="ab9c2-128">カスタム JSON プロパティの名前付けポリシーを使用するには、次の例に示すように、<xref:System.Text.Json.JsonNamingPolicy> から派生するクラスを作成し、<xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-128">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs":::

<span data-ttu-id="ab9c2-129">次に、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> プロパティを名前付けポリシー クラスのインスタンスに設定します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-129">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs" id="Serialize":::

<span data-ttu-id="ab9c2-130">シリアル化するクラスと JSON 出力の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-130">Here's an example class to serialize and JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPropertyNameAttribute":::

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="ab9c2-131">JSON プロパティの名前付けポリシーは:</span><span class="sxs-lookup"><span data-stu-id="ab9c2-131">The JSON property naming policy:</span></span>

* <span data-ttu-id="ab9c2-132">シリアル化と逆シリアル化に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-132">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="ab9c2-133">`[JsonPropertyName]` 属性によってオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-133">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="ab9c2-134">このため、この例の JSON プロパティ名 `Wind` は大文字ではありません。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-134">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

## <a name="camel-case-dictionary-keys"></a><span data-ttu-id="ab9c2-135">キャメル ケースのディクショナリ キー</span><span class="sxs-lookup"><span data-stu-id="ab9c2-135">Camel case dictionary keys</span></span>

<span data-ttu-id="ab9c2-136">シリアル化するオブジェクトのプロパティが `Dictionary<string,TValue>` 型である場合は、`string` キーをキャメル ケースに変換できます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-136">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="ab9c2-137">これを行うには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> を `JsonNamingPolicy.CamelCase` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-137">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs" id="Serialize":::

<span data-ttu-id="ab9c2-138">キーと値のペア `"ColdMinTemp", 20` および `"HotMinTemp", 40` を持つ `TemperatureRanges` という名前のディクショナリを使用してオブジェクトをシリアル化すると、次の例のような JSON 出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-138">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="ab9c2-139">ディクショナリ キーに対するキャメル ケースの名前付けポリシーは、シリアル化にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-139">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="ab9c2-140">ディクショナリを逆シリアル化すると、`DictionaryKeyPolicy` に `JsonNamingPolicy.CamelCase` を指定した場合でも、キーが JSON ファイルと一致します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-140">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

## <a name="enums-as-strings"></a><span data-ttu-id="ab9c2-141">文字列としての列挙型</span><span class="sxs-lookup"><span data-stu-id="ab9c2-141">Enums as strings</span></span>

<span data-ttu-id="ab9c2-142">既定では、列挙型は数値としてシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-142">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="ab9c2-143">列挙型名を文字列としてシリアル化するには、<xref:System.Text.Json.Serialization.JsonStringEnumConverter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-143">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="ab9c2-144">たとえば、列挙型を持つ次のクラスをシリアル化する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-144">For example, suppose you need to serialize the following class that has an enum:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnum":::

<span data-ttu-id="ab9c2-145">Summary が `Hot` の場合、既定では、シリアル化された JSON には数値 3 があります。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-145">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="ab9c2-146">次のサンプル コードでは、数値ではなく列挙型名をシリアル化し、名前をキャメル ケースに変換します。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-146">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Serialize":::

<span data-ttu-id="ab9c2-147">結果として生成される JSON は、次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-147">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="ab9c2-148">列挙型の文字列名も、次の例に示すように逆シリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="ab9c2-148">Enum string names can be deserialized as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs" id="Deserialize":::

## <a name="see-also"></a><span data-ttu-id="ab9c2-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="ab9c2-149">See also</span></span>

* [<span data-ttu-id="ab9c2-150">System.Text.Json の概要</span><span class="sxs-lookup"><span data-stu-id="ab9c2-150">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="ab9c2-151">JSON をシリアル化および逆シリアル化する方法</span><span class="sxs-lookup"><span data-stu-id="ab9c2-151">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="ab9c2-152">JsonSerializerOptions インスタンスのインスタンスを作成する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-152">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="ab9c2-153">大文字と小文字を区別しない一致を有効にする</span><span class="sxs-lookup"><span data-stu-id="ab9c2-153">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="ab9c2-154">プロパティを無視する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-154">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="ab9c2-155">無効な JSON を許可する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-155">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="ab9c2-156">オーバーフロー JSON の処理</span><span class="sxs-lookup"><span data-stu-id="ab9c2-156">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="ab9c2-157">参照を保持する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-157">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="ab9c2-158">変更できない型と非パブリック アクセサー</span><span class="sxs-lookup"><span data-stu-id="ab9c2-158">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="ab9c2-159">ポリモーフィックなシリアル化</span><span class="sxs-lookup"><span data-stu-id="ab9c2-159">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="ab9c2-160">Newtonsoft.Json から System.Text.Json に移行する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-160">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="ab9c2-161">文字エンコードをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="ab9c2-161">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="ab9c2-162">カスタム シリアライザーと逆シリアライザーを作成する</span><span class="sxs-lookup"><span data-stu-id="ab9c2-162">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="ab9c2-163">JSON シリアル化のためのカスタム コンバーターの作成</span><span class="sxs-lookup"><span data-stu-id="ab9c2-163">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="ab9c2-164">DateTime および DateTimeOffset のサポート</span><span class="sxs-lookup"><span data-stu-id="ab9c2-164">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="ab9c2-165">[System.Text.Json API リファレンス](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="ab9c2-165">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="ab9c2-166">[System.Text.Json.Serialization API リファレンス](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="ab9c2-166">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>