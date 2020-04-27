---
ms.openlocfilehash: 2afe5ae80c2d7feca89737b767a6335950d04416
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021677"
---
### <a name="jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument"></a><span data-ttu-id="9fb71-101">JsonEncodedText.Encode メソッドに JavaScriptEncoder 引数を追加</span><span class="sxs-lookup"><span data-stu-id="9fb71-101">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>

<span data-ttu-id="9fb71-102">.NET Core 3.0 Preview 8 以降、<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> メソッドには、オプションの <xref:System.Text.Encodings.Web.JavaScriptEncoder> 引数が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9fb71-102">Starting with .NET Core 3.0 Preview 8, the <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> methods contain an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> argument.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9fb71-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="9fb71-103">Change description</span></span>

<span data-ttu-id="9fb71-104">.NET Core 3.0 には、新しい型 xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9fb71-104">.NET Core 3.0 includes a new type, xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9fb71-105">.NET Core 3.0 Preview 8 以降では、<xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> メソッドのすべてのオーバーロードのシグネチャにオプションの <xref:System.Text.Encodings.Web.JavaScriptEncoder> パラメーターを含むように変更されました。</span><span class="sxs-lookup"><span data-stu-id="9fb71-105">Starting with .NET Core 3.0 Preview 8, the signature of all <xref:System.Text.Json.JsonEncodedText.Encode%2A?displayProperty=nameWithType> method overloads has changed to include an optional <xref:System.Text.Encodings.Web.JavaScriptEncoder> parameter.</span></span> <span data-ttu-id="9fb71-106">この変更により、別のエンコーダーまたはカスタムのエンコーダーを使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9fb71-106">This change was made to allow for a different or custom encoder.</span></span>

<span data-ttu-id="9fb71-107">.NET Core 3.0 Preview 7 の `Encode` メソッドのシグネチャは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9fb71-107">The signature of the `Encode` methods in .NET Core 3.0 Preview 7 is:</span></span>

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value);
        public static JsonEncodedText Encode(string value);
    }
}
```

<span data-ttu-id="9fb71-108">.NET Core 3.0 Preview 8 以降のバージョンでは、同じ `Encode` メソッドのシグネチャが次のようになります。</span><span class="sxs-lookup"><span data-stu-id="9fb71-108">The signature of the same `Encode` methods in .NET Core 3.0 Preview 8 and later versions is:</span></span>

```csharp
namespace System.Text.Json
{
    public readonly struct JsonEncodedText
    {
        public static JsonEncodedText Encode(ReadOnlySpan<byte> utf8Value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(ReadOnlySpan<char> value, JavaScriptEncoder encoder = null);
        public static JsonEncodedText Encode(string value, JavaScriptEncoder encoder = null);
    }
}
```

#### <a name="version-introduced"></a><span data-ttu-id="9fb71-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9fb71-109">Version introduced</span></span>

<span data-ttu-id="9fb71-110">.NET Core 3.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="9fb71-110">.NET Core 3.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9fb71-111">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="9fb71-111">Recommended action</span></span>

<span data-ttu-id="9fb71-112">これはバイナリのみの破壊的変更です。 .NET Core 3.0 Preview 8 以降のバージョンに再コンパイルすると、実行時の問題はすべて修正されます。</span><span class="sxs-lookup"><span data-stu-id="9fb71-112">This is a binary breaking change only; a recompile against .NET Core 3.0 Preview 8 or a later version will fix any runtime issues.</span></span>

#### <a name="category"></a><span data-ttu-id="9fb71-113">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9fb71-113">Category</span></span>

<span data-ttu-id="9fb71-114">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="9fb71-114">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9fb71-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9fb71-115">Affected APIs</span></span>

- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Byte%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan%7BSystem.Char%7D,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>
- <xref:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Byte},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.ReadOnlySpan{System.Char},System.Text.Encodings.Web.JavaScriptEncoder)`
- `M:System.Text.Json.JsonEncodedText.Encode(System.String,System.Text.Encodings.Web.JavaScriptEncoder)`

-->
