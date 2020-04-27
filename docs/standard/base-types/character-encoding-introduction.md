---
title: .NET での文字エンコードの概要
description: .NET での文字エンコーディング/デコーディングについて説明します。
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 086430a720e6dc7f39d459a4b99d5bbdb1cfcac3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141307"
---
# <a name="character-encoding-in-net"></a><span data-ttu-id="cc797-103">.NET での文字エンコード</span><span class="sxs-lookup"><span data-stu-id="cc797-103">Character encoding in .NET</span></span>

<span data-ttu-id="cc797-104">この記事では、.NET で使用される文字エンコード システムの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="cc797-104">This article provides an introduction to character encoding systems that are used by .NET.</span></span> <span data-ttu-id="cc797-105">この記事では、<xref:System.String>、<xref:System.Char>、<xref:System.Text.Rune>、および <xref:System.Globalization.StringInfo> 型が Unicode、UTF-16、および UTF-8 でどのように動作するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cc797-105">The article explains how the <xref:System.String>, <xref:System.Char>, <xref:System.Text.Rune>, and <xref:System.Globalization.StringInfo> types work with Unicode, UTF-16, and UTF-8.</span></span>

<span data-ttu-id="cc797-106">ここでは、"*文字*" という用語が "*読者が 1 つの表示要素として認識するもの*" という全般的な意味で使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-106">The term *character* is used here in the general sense of *what a reader perceives as a single display element*.</span></span> <span data-ttu-id="cc797-107">一般的な例としては、文字 "a"、記号 "@"、絵文字 "🐂" などがあります。</span><span class="sxs-lookup"><span data-stu-id="cc797-107">Common examples are the letter "a", the symbol "@", and the emoji "🐂".</span></span> <span data-ttu-id="cc797-108">場合によっては、1 つの文字に見えるものが、[書記素クラスター](#grapheme-clusters)に関するセクションで説明しているように、実際には複数の独立した表示要素で構成されていることがあります。</span><span class="sxs-lookup"><span data-stu-id="cc797-108">Sometimes what looks like one character is actually composed of multiple independent display elements, as the section on [grapheme clusters](#grapheme-clusters) explains.</span></span>

## <a name="the-string-and-char-types"></a><span data-ttu-id="cc797-109">string 型と char 型</span><span class="sxs-lookup"><span data-stu-id="cc797-109">The string and char types</span></span>

<span data-ttu-id="cc797-110">[string](xref:System.String) クラスのインスタンスは、あるテキストを表します。</span><span class="sxs-lookup"><span data-stu-id="cc797-110">An instance of the [string](xref:System.String) class represents some text.</span></span> <span data-ttu-id="cc797-111">`string` は、論理的には 16 ビット値のシーケンスであり、そのそれぞれが [char](xref:System.Char) 構造体のインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="cc797-111">A `string` is logically a sequence of 16-bit values, each of which is an instance of the [char](xref:System.Char) struct.</span></span> <span data-ttu-id="cc797-112">[string.Length](xref:System.String.Length) プロパティでは、`string` インスタンスに含まれる `char` インスタンスの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-112">The [string.Length](xref:System.String.Length) property returns the number of `char` instances in the `string` instance.</span></span>

<span data-ttu-id="cc797-113">次のサンプル関数では、`string` に含まれるすべての `char` インスタンスの 16 進表記の値が出力されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-113">The following sample function prints out the values in hexadecimal notation of all the `char` instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

<span data-ttu-id="cc797-114">この関数に文字列 "Hello" を渡すと、次の出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="cc797-114">Pass the string "Hello" to this function, and you get the following output:</span></span>

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

<span data-ttu-id="cc797-115">各文字は、1 つの `char` 値で表されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-115">Each character is represented by a single `char` value.</span></span> <span data-ttu-id="cc797-116">このパターンは、世界のほとんどの言語に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="cc797-116">That pattern holds true for most of the world's languages.</span></span> <span data-ttu-id="cc797-117">たとえば、*nǐ hǎo* のように発音し "*こんにちは*" を意味する中国語の 2 文字に対する出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-117">For example, here's the output for two Chinese characters that sound like *nǐ hǎo* and mean *Hello*:</span></span>

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

<span data-ttu-id="cc797-118">ただし、一部の言語および一部の記号と絵文字については、1 つの文字を表すために 2 つの `char` インスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="cc797-118">However, for some languages and for some symbols and emoji, it takes two `char` instances to represent a single character.</span></span> <span data-ttu-id="cc797-119">たとえば、オセージ語で "*オセージ*" を表す単語に含まれる文字と `char` インスタンスを比較してください。</span><span class="sxs-lookup"><span data-stu-id="cc797-119">For example, compare the characters and `char` instances in the word that means *Osage* in the Osage language:</span></span>

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

<span data-ttu-id="cc797-120">前の例では、空白を除く各文字が 2 つの `char` インスタンスによって表されています。</span><span class="sxs-lookup"><span data-stu-id="cc797-120">In the preceding example, each character except the space is represented by two `char` instances.</span></span>

<span data-ttu-id="cc797-121">また、雄牛の絵文字を表す次の例で示すように、1 つの Unicode 絵文字も 2 つの `char` によって表されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-121">A single Unicode emoji is also represented by two `char`s, as seen in the following example showing an ox emoji:</span></span>

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

<span data-ttu-id="cc797-122">これらの例では、`char` インスタンスの数を示す `string.Length` の値が、必ずしも表示される文字数を示していないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="cc797-122">These examples show that the value of `string.Length`, which indicates the number of `char` instances, doesn't necessarily indicate the number of displayed characters.</span></span> <span data-ttu-id="cc797-123">1 つの `char` インスタンスは、必ずしもそれ自体で 1 文字を表すとは限りません。</span><span class="sxs-lookup"><span data-stu-id="cc797-123">A single `char` instance by itself doesn't necessarily represent a character.</span></span>

<span data-ttu-id="cc797-124">1 つの文字にマップされる `char` のペアは、"*サロゲート ペア*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cc797-124">The `char` pairs that map to a single character are called *surrogate pairs*.</span></span> <span data-ttu-id="cc797-125">それらがどのように動作するかを理解するには、Unicode と UTF-16 のエンコードについて理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-125">To understand how they work, you need to understand Unicode and UTF-16 encoding.</span></span>

## <a name="unicode-code-points"></a><span data-ttu-id="cc797-126">Unicode コード ポイント</span><span class="sxs-lookup"><span data-stu-id="cc797-126">Unicode code points</span></span>

<span data-ttu-id="cc797-127">Unicode は、さまざまなプラットフォーム上で、さまざまな言語とスクリプトで使用するための国際エンコード標準です。</span><span class="sxs-lookup"><span data-stu-id="cc797-127">Unicode is an international encoding standard for use on various platforms and with various languages and scripts.</span></span>

<span data-ttu-id="cc797-128">Unicode 標準では、110 万個を超える[コード ポイント](https://www.unicode.org/glossary/#code_point)が定義されています。</span><span class="sxs-lookup"><span data-stu-id="cc797-128">The Unicode Standard defines over 1.1 million [code points](https://www.unicode.org/glossary/#code_point).</span></span> <span data-ttu-id="cc797-129">コード ポイントは、0 から `U+10FFFF` (10 進数の 1,114,111) までの範囲の整数値です。</span><span class="sxs-lookup"><span data-stu-id="cc797-129">A code point is an integer value that can range from 0 to `U+10FFFF` (decimal 1,114,111).</span></span> <span data-ttu-id="cc797-130">一部のコード ポイントは、文字、記号、または絵文字に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="cc797-130">Some code points are assigned to letters, symbols, or emoji.</span></span> <span data-ttu-id="cc797-131">その他は、新しい行に進むなど、テキストや文字の表示方法を制御するアクションに割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="cc797-131">Others are assigned to actions that control how text or characters are displayed, such as advance to a new line.</span></span> <span data-ttu-id="cc797-132">多くのコード ポイントはまだ割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="cc797-132">Many code points are not yet assigned.</span></span>

<span data-ttu-id="cc797-133">コード ポイントの割り当てのいくつかの例と、それらが記載されている Unicode 表へのリンクを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-133">Here are some examples of code point assignments, with links to Unicode charts in which they appear:</span></span>

|<span data-ttu-id="cc797-134">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="cc797-134">Decimal</span></span>|<span data-ttu-id="cc797-135">Hex</span><span class="sxs-lookup"><span data-stu-id="cc797-135">Hex</span></span>       |<span data-ttu-id="cc797-136">例</span><span class="sxs-lookup"><span data-stu-id="cc797-136">Example</span></span>|<span data-ttu-id="cc797-137">説明</span><span class="sxs-lookup"><span data-stu-id="cc797-137">Description</span></span>|
|------:|----------|-------|-----------|
|<span data-ttu-id="cc797-138">10</span><span class="sxs-lookup"><span data-stu-id="cc797-138">10</span></span>     | `U+000A` |<span data-ttu-id="cc797-139">N/A</span><span class="sxs-lookup"><span data-stu-id="cc797-139">N/A</span></span>| [<span data-ttu-id="cc797-140">改行</span><span class="sxs-lookup"><span data-stu-id="cc797-140">LINE FEED</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="cc797-141">65</span><span class="sxs-lookup"><span data-stu-id="cc797-141">65</span></span>     | `U+0061` | <span data-ttu-id="cc797-142">a</span><span class="sxs-lookup"><span data-stu-id="cc797-142">a</span></span> | [<span data-ttu-id="cc797-143">ラテン小文字 A</span><span class="sxs-lookup"><span data-stu-id="cc797-143">LATIN SMALL LETTER A</span></span>](https://www.unicode.org/charts/PDF/U0000.pdf) |
|<span data-ttu-id="cc797-144">562</span><span class="sxs-lookup"><span data-stu-id="cc797-144">562</span></span>    | `U+0232` | <span data-ttu-id="cc797-145">Ȳ</span><span class="sxs-lookup"><span data-stu-id="cc797-145">Ȳ</span></span> | [<span data-ttu-id="cc797-146">長音符号付きラテン大文字 Y</span><span class="sxs-lookup"><span data-stu-id="cc797-146">LATIN CAPITAL LETTER Y WITH MACRON</span></span>](https://www.unicode.org/charts/PDF/U0180.pdf) |
|<span data-ttu-id="cc797-147">68,675</span><span class="sxs-lookup"><span data-stu-id="cc797-147">68,675</span></span> | `U+10C43`| <span data-ttu-id="cc797-148">𐱃</span><span class="sxs-lookup"><span data-stu-id="cc797-148">𐱃</span></span> | [<span data-ttu-id="cc797-149">古テュルク語文字オルホン AT</span><span class="sxs-lookup"><span data-stu-id="cc797-149">OLD TURKIC LETTER ORKHON AT</span></span>](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|<span data-ttu-id="cc797-150">127,801</span><span class="sxs-lookup"><span data-stu-id="cc797-150">127,801</span></span>| `U+1F339`| <span data-ttu-id="cc797-151">🌹</span><span class="sxs-lookup"><span data-stu-id="cc797-151">🌹</span></span> | [<span data-ttu-id="cc797-152">バラの絵文字</span><span class="sxs-lookup"><span data-stu-id="cc797-152">ROSE emoji</span></span>](https://www.unicode.org/charts/PDF/U1F300.pdf) |

<span data-ttu-id="cc797-153">コード ポイントは、習慣的に、`U+xxxx` 構文を使用して参照されます。`xxxx` は 16 進エンコードの整数値です。</span><span class="sxs-lookup"><span data-stu-id="cc797-153">Code points are customarily referred to by using the syntax `U+xxxx`, where `xxxx` is the hex-encoded integer value.</span></span>

<span data-ttu-id="cc797-154">コード ポイントの全範囲内には、次の 2 つの部分範囲があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-154">Within the full range of code points there are two subranges:</span></span>

* <span data-ttu-id="cc797-155">`U+0000..U+FFFF` の範囲の**基本多言語面 (BMP)** 。</span><span class="sxs-lookup"><span data-stu-id="cc797-155">The **Basic Multilingual Plane (BMP)** in the range `U+0000..U+FFFF`.</span></span> <span data-ttu-id="cc797-156">この 16 ビットの範囲によって 65,536 個のコード ポイントが提供され、世界の書記体系の大部分を十分にカバーできます。</span><span class="sxs-lookup"><span data-stu-id="cc797-156">This 16-bit range provides 65,536 code points, enough to cover the majority of the world's writing systems.</span></span>
* <span data-ttu-id="cc797-157">`U+10000..U+10FFFF` の範囲の**補助コード ポイント**。</span><span class="sxs-lookup"><span data-stu-id="cc797-157">**Supplementary code points** in the range `U+10000..U+10FFFF`.</span></span> <span data-ttu-id="cc797-158">この 21 ビットの範囲によって、100 万個を超える追加のコード ポイントが提供されます。これは、あまり一般的ではない言語や、絵文字などのその他の目的のために使用できます。</span><span class="sxs-lookup"><span data-stu-id="cc797-158">This 21-bit range provides more than a million additional code points that can be used for less well-known languages and other purposes such as emojis.</span></span>

<span data-ttu-id="cc797-159">次の図は、BMP と補助コード ポイントの関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc797-159">The following diagram illustrates the relationship between the BMP and the supplementary code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP と補助コード ポイント":::

## <a name="utf-16-code-units"></a><span data-ttu-id="cc797-161">UTF-16 コード単位</span><span class="sxs-lookup"><span data-stu-id="cc797-161">UTF-16 code units</span></span>

<span data-ttu-id="cc797-162">16 ビット Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) は、16 ビットの "*コード単位*" を使用して Unicode コード ポイントを表す、文字エンコード システムです。</span><span class="sxs-lookup"><span data-stu-id="cc797-162">16-bit Unicode Transformation Format ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)) is a character encoding system that uses 16-bit *code units* to represent Unicode code points.</span></span> <span data-ttu-id="cc797-163">.NET では、`string` 内のテキストをエンコードするために UTF-16 が使用されています。</span><span class="sxs-lookup"><span data-stu-id="cc797-163">.NET uses UTF-16 to encode the text in a `string`.</span></span> <span data-ttu-id="cc797-164">`char` インスタンスは、16 ビットのコード単位を表します。</span><span class="sxs-lookup"><span data-stu-id="cc797-164">A `char` instance represents a 16-bit code unit.</span></span>

<span data-ttu-id="cc797-165">1 つの 16 ビット コード単位は、基本多言語面の 16 ビット範囲に含まれる任意のコード ポイントを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="cc797-165">A single 16-bit code unit can represent any code point in the 16-bit range of the Basic Multilingual Plane.</span></span> <span data-ttu-id="cc797-166">ただし、補助範囲内のコード ポイントについては、2 つの `char` インスタンスが必要です。</span><span class="sxs-lookup"><span data-stu-id="cc797-166">But for a code point in the supplementary range, two `char` instances are needed.</span></span>

## <a name="surrogate-pairs"></a><span data-ttu-id="cc797-167">サロゲート ペア</span><span class="sxs-lookup"><span data-stu-id="cc797-167">Surrogate pairs</span></span>

<span data-ttu-id="cc797-168">2 つの 16 ビット値から 1 つの 21 ビット値への変換は、`U+D800` から `U+DFFF` (10 進数の 55,296 から 57,343) まで (境界も含める) の、"*サロゲート コード ポイント*" と呼ばれる特殊な範囲を使用して行われます。</span><span class="sxs-lookup"><span data-stu-id="cc797-168">The translation of two 16-bit values to a single 21-bit value is facilitated by a special range called the *surrogate code points*, from `U+D800` to `U+DFFF` (decimal 55,296 to 57,343), inclusive.</span></span>

<span data-ttu-id="cc797-169">次の図は、BMP とサロゲート コード ポイントの関係を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc797-169">The following diagram illustrates the relationship between the BMP and the surrogate code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP とサロゲート コード ポイント":::

<span data-ttu-id="cc797-171">"*上位サロゲート*" コード ポイント (`U+D800..U+DBFF`) の直後に "*下位サロゲート*" コード ポイント (`U+DC00..U+DFFF`) が続く場合、そのペアは、次の数式を使用して補助コード ポイントとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-171">When a *high surrogate* code point (`U+D800..U+DBFF`) is immediately followed by a *low surrogate* code point (`U+DC00..U+DFFF`), the pair is interpreted as a supplementary code point by using the following formula:</span></span>

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

<span data-ttu-id="cc797-172">10 進表記を使用した同じ数式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-172">Here's the same formula using decimal notation:</span></span>

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

<span data-ttu-id="cc797-173">"*上位*" サロゲート コード ポイントには、"*下位*" サロゲート コード ポイントよりも大きい数値は含まれません。</span><span class="sxs-lookup"><span data-stu-id="cc797-173">A *high* surrogate code point doesn't have a higher number value than a *low* surrogate code point.</span></span> <span data-ttu-id="cc797-174">上位サロゲート コード ポイントが "上位" と呼ばれる理由は、完全な 21 ビットのコード ポイント範囲の上位 11 ビットを計算するために使用されるからです。</span><span class="sxs-lookup"><span data-stu-id="cc797-174">The high surrogate code point is called "high" because it's used to calculate the higher-order 11 bits of the full 21-bit code point range.</span></span> <span data-ttu-id="cc797-175">下位サロゲート コード ポイントは、下位 10 ビットを計算するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-175">The low surrogate code point is used to calculate the lower-order 10 bits.</span></span>

<span data-ttu-id="cc797-176">たとえば、サロゲート ペア `0xD83C` と `0xDF39` に対応する実際のコード ポイントは、次のように計算されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-176">For example, the actual code point that corresponds to the surrogate pair `0xD83C` and `0xDF39`  is computed as follows:</span></span>

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

<span data-ttu-id="cc797-177">10 進表記を使用した同じ計算を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-177">Here's the same calculation using decimal notation:</span></span>

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

<span data-ttu-id="cc797-178">前の例では、`"\ud83c\udf39"` が、前述の `U+1F339 ROSE ('🌹')` コード ポイントの UTF-16 エンコードであることが示されています。</span><span class="sxs-lookup"><span data-stu-id="cc797-178">The preceding example demonstrates that `"\ud83c\udf39"` is the UTF-16 encoding of the `U+1F339 ROSE ('🌹')` code point mentioned earlier.</span></span>

## <a name="unicode-scalar-values"></a><span data-ttu-id="cc797-179">Unicode スカラー値</span><span class="sxs-lookup"><span data-stu-id="cc797-179">Unicode scalar values</span></span>

<span data-ttu-id="cc797-180">[Unicode スカラー値](https://www.unicode.org/glossary/#unicode_scalar_value)という用語は、サロゲート コード ポイント以外のすべてのコード ポイントを指します。</span><span class="sxs-lookup"><span data-stu-id="cc797-180">The term [Unicode scalar value](https://www.unicode.org/glossary/#unicode_scalar_value) refers to all code points other than the surrogate code points.</span></span> <span data-ttu-id="cc797-181">つまり、スカラー値とは、文字が割り当てられているか、将来文字が割り当てられる可能性があるコード ポイントです。</span><span class="sxs-lookup"><span data-stu-id="cc797-181">In other words, a scalar value is any code point that is assigned a character or can be assigned a character in the future.</span></span> <span data-ttu-id="cc797-182">ここでの "文字" は、コード ポイントに割り当てることができるすべてのものを指します。これには、テキストや文字の表示方法を制御するアクションなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc797-182">"Character" here refers to anything that can be assigned to a code point, which includes such things as actions that control how text or characters are displayed.</span></span>

<span data-ttu-id="cc797-183">次の図は、スカラー値のコード ポイントを示しています。</span><span class="sxs-lookup"><span data-stu-id="cc797-183">The following diagram illustrates the scalar value code points.</span></span>

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="スカラー値":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a><span data-ttu-id="cc797-185">スカラー値としての Rune 型</span><span class="sxs-lookup"><span data-stu-id="cc797-185">The Rune type as a scalar value</span></span>

<span data-ttu-id="cc797-186">.NET Core 3.0 以降では、<xref:System.Text.Rune?displayProperty=fullName> 型によって Unicode スカラー値が表されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-186">Beginning with .NET Core 3.0, the <xref:System.Text.Rune?displayProperty=fullName> type represents a Unicode scalar value.</span></span> <span data-ttu-id="cc797-187">**`Rune` は、.NET Core 2.x または .NET Framework 4.x では使用できません。**</span><span class="sxs-lookup"><span data-stu-id="cc797-187">**`Rune` is not available in .NET Core 2.x or .NET Framework 4.x.**</span></span>

<span data-ttu-id="cc797-188">`Rune` コンストラクターでは、生成されるインスタンスが有効な Unicode スカラー値であることが検証されます。そうでない場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="cc797-188">The `Rune` constructors validate that the resulting instance is a valid Unicode scalar value, otherwise they throw an exception.</span></span> <span data-ttu-id="cc797-189">次の例は、`Rune` インスタンスのインスタンス化に成功するコードを示しています。入力が有効なスカラー値を表しているためです。</span><span class="sxs-lookup"><span data-stu-id="cc797-189">The following example shows code that successfully instantiates `Rune` instances because the input represents valid scalar values:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

<span data-ttu-id="cc797-190">次の例では、例外がスローされます。コード ポイントがサロゲートの範囲内にあり、サロゲート ペアの一部ではないためです。</span><span class="sxs-lookup"><span data-stu-id="cc797-190">The following example throws an exception because the code point is in the surrogate range and isn't part of a surrogate pair:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

<span data-ttu-id="cc797-191">次の例では、コード ポイントが補助範囲を超えているため、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="cc797-191">The following example throws an exception because the code point is beyond the supplementary range:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Rune<span data-ttu-id="cc797-192"> の使用例: 大文字と小文字の変更</span><span class="sxs-lookup"><span data-stu-id="cc797-192"> usage example: changing letter case</span></span>

<span data-ttu-id="cc797-193">`char` を受け取り、スカラー値であるコード ポイントを操作していると仮定する API は、その `char` がサロゲート ペアのものであった場合、正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="cc797-193">An API that takes a `char` and assumes it is working with a code point that is a scalar value doesn't work correctly if the `char` is from a surrogate pair.</span></span> <span data-ttu-id="cc797-194">たとえば、string に含まれる各 char に対して <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> を呼び出す、次のようなメソッドを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="cc797-194">For example, consider the following method that calls <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> on each char in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

<span data-ttu-id="cc797-195">`input` string に小文字のデザレット文字 `er` (`𐑉`) が含まれていた場合、このコードでは大文字 (`𐐡`) に変換することができません。</span><span class="sxs-lookup"><span data-stu-id="cc797-195">If the `input` string contains the lowercase Deseret letter `er` (`𐑉`), this code won't convert it to uppercase (`𐐡`).</span></span> <span data-ttu-id="cc797-196">このコードでは、`U+D801` と `U+DC49` の各サロゲート コード ポイントに対して、個別に `char.ToUpperInvariant` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-196">The code calls `char.ToUpperInvariant` separately on each surrogate code point, `U+D801` and `U+DC49`.</span></span> <span data-ttu-id="cc797-197">しかし、`U+D801` 自体には、それを小文字として識別するのに十分な情報が含まれていないため、`char.ToUpperInvariant` による変更は行われません。</span><span class="sxs-lookup"><span data-stu-id="cc797-197">But `U+D801` doesn't have enough information by itself to identify it as a lowercase letter, so `char.ToUpperInvariant` leaves it alone.</span></span> <span data-ttu-id="cc797-198">また、`U+DC49` も同じ方法で処理されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-198">And it handles `U+DC49` the same way.</span></span> <span data-ttu-id="cc797-199">その結果、`input` string に含まれる小文字の '𐑉' は、大文字の '𐐡' に変換されません。</span><span class="sxs-lookup"><span data-stu-id="cc797-199">The result is that lowercase '𐑉' in the `input` string doesn't get converted to uppercase '𐐡'.</span></span>

<span data-ttu-id="cc797-200">string を適切に大文字に変換するための 2 つのオプションを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-200">Here are two options for correctly converting a string to uppercase:</span></span>

* <span data-ttu-id="cc797-201">`char` から `char` へと反復処理するのではなく、入力 string に対して <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="cc797-201">Call <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> on the input string rather than iterating `char`-by-`char`.</span></span> <span data-ttu-id="cc797-202">`string.ToUpperInvariant` メソッドは各サロゲート ペアの両方の部分にアクセスできるため、すべての Unicode コード ポイントを正しく処理できます。</span><span class="sxs-lookup"><span data-stu-id="cc797-202">The `string.ToUpperInvariant` method has access to both parts of each surrogate pair, so it can handle all Unicode code points correctly.</span></span>
* <span data-ttu-id="cc797-203">次の例に示すように、`char` インスタンスではなく `Rune` インスタンスとして Unicode スカラー値を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="cc797-203">Iterate through the Unicode scalar values as `Rune` instances instead of `char` instances, as shown in the following example.</span></span> <span data-ttu-id="cc797-204">`Rune` インスタンスは有効な Unicode スカラー値であるため、スカラー値に対して動作することが想定されている API に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="cc797-204">Since a `Rune` instance is a valid Unicode scalar value, it can be passed to APIs that expect to operate on a scalar value.</span></span> <span data-ttu-id="cc797-205">たとえば、次の例に示すように <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> を呼び出すと、正しい結果が得られます。</span><span class="sxs-lookup"><span data-stu-id="cc797-205">For example, calling <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> as shown in the following example gives correct results:</span></span>

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a><span data-ttu-id="cc797-206">その他の Rune API</span><span class="sxs-lookup"><span data-stu-id="cc797-206">Other Rune APIs</span></span>

<span data-ttu-id="cc797-207">`Rune` 型では、多くの `char` API と類似した機能が公開されています。</span><span class="sxs-lookup"><span data-stu-id="cc797-207">The `Rune` type exposes analogs of many of the `char` APIs.</span></span> <span data-ttu-id="cc797-208">たとえば、以下のメソッドは、`char` 型の静的 API に対応しています。</span><span class="sxs-lookup"><span data-stu-id="cc797-208">For example, the following methods mirror static APIs on the `char` type:</span></span>

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

<span data-ttu-id="cc797-209">`Rune` インスタンスから生のスカラー値を取得するには、<xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="cc797-209">To get the raw scalar value from a `Rune` instance, use the <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> property.</span></span>

<span data-ttu-id="cc797-210">`Rune` インスタンスを再び `char` のシーケンスに変換するには、<xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> または <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="cc797-210">To convert a `Rune` instance back to a sequence of `char`s, use <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> or the <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cc797-211">すべての Unicode スカラー値は 1 つの `char` またはサロゲート ペアによって表すことができるため、あらゆる `Rune` インスタンスは多くても 2 つの `char` インスタンスによって表すことができます。</span><span class="sxs-lookup"><span data-stu-id="cc797-211">Since any Unicode scalar value is representable by a single `char` or by a surrogate pair, any `Rune` instance can be represented by at most 2 `char` instances.</span></span> <span data-ttu-id="cc797-212">`Rune` インスタンスを表すために必要な `char` インスタンスの数を確認するには、<xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> を使用します。</span><span class="sxs-lookup"><span data-stu-id="cc797-212">Use <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> to see how many `char` instances are required to represent a `Rune` instance.</span></span>

<span data-ttu-id="cc797-213">.NET の `Rune` 型の詳細については、[`Rune` API リファレンス](xref:System.Text.Rune)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc797-213">For more information about the .NET `Rune` type, see the [`Rune` API reference](xref:System.Text.Rune).</span></span>

## <a name="grapheme-clusters"></a><span data-ttu-id="cc797-214">書記素クラスター</span><span class="sxs-lookup"><span data-stu-id="cc797-214">Grapheme clusters</span></span>

<span data-ttu-id="cc797-215">1 つの文字に見えるものが、複数のコード ポイントの組み合わせから生成されている場合があります。このため、"文字" の代わりに使用されることが多い、[書記素クラスター](https://www.unicode.org/glossary/#grapheme_cluster)というよりわかりやすい用語があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-215">What looks like one character might result from a combination of multiple code points, so a more descriptive term that is often used in place of "character" is [grapheme cluster](https://www.unicode.org/glossary/#grapheme_cluster).</span></span> <span data-ttu-id="cc797-216">.NET における同等の用語は、[テキスト要素](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)です。</span><span class="sxs-lookup"><span data-stu-id="cc797-216">The equivalent term in .NET is [text element](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).</span></span>

<span data-ttu-id="cc797-217">次の `string` インスタンスについて考えてみましょう: "a"、"á"。</span><span class="sxs-lookup"><span data-stu-id="cc797-217">Consider the `string` instances "a", "á".</span></span> <span data-ttu-id="cc797-218">"á"、"`👩🏽‍🚒`"。</span><span class="sxs-lookup"><span data-stu-id="cc797-218">"á", and "`👩🏽‍🚒`".</span></span> <span data-ttu-id="cc797-219">お使いのオペレーティング システムによってこれらが Unicode 標準で指定されているとおりに処理される場合、これらの各 `string` インスタンスは、1 つのテキスト要素、または書記素クラスターとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-219">If your operating system handles them as specified by the Unicode standard, each of these `string` instances appears as a single text element or grapheme cluster.</span></span> <span data-ttu-id="cc797-220">ただし、最後の 2 つは、複数のスカラー値コード ポイントによって表されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-220">But the last two are represented by more than one scalar value code point.</span></span>

* <span data-ttu-id="cc797-221">string "a" は 1 つのスカラー値で表され、1 つの `char` インスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc797-221">The string "a" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+0061 LATIN SMALL LETTER A`

* <span data-ttu-id="cc797-222">string "á" は 1 つのスカラー値で表され、1 つの `char` インスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc797-222">The string "á" is represented by one scalar value and contains one `char` instance.</span></span>

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* <span data-ttu-id="cc797-223">string "á" は、"á" と同じように見えますが、2 つのスカラー値で表され、2 つの `char` インスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc797-223">The string "á" looks the same as "á" but is represented by two scalar values and contains two `char` instances.</span></span>

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* <span data-ttu-id="cc797-224">最後に、string "`👩🏽‍🚒`" は 4 つのスカラー値で表され、7 つの `char` インスタンスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="cc797-224">Finally, the string "`👩🏽‍🚒`" is represented by four scalar values and contains seven `char` instances.</span></span>

  * <span data-ttu-id="cc797-225">`U+1F469 WOMAN` (補助範囲、サロゲート ペアが必要)</span><span class="sxs-lookup"><span data-stu-id="cc797-225">`U+1F469 WOMAN` (supplementary range, requires a surrogate pair)</span></span>
  * <span data-ttu-id="cc797-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (補助範囲、サロゲート ペアが必要)</span><span class="sxs-lookup"><span data-stu-id="cc797-226">`U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (supplementary range, requires a surrogate pair)</span></span>
  * `U+200D ZERO WIDTH JOINER`
  * <span data-ttu-id="cc797-227">`U+1F692 FIRE ENGINE` (補助範囲、サロゲート ペアが必要)</span><span class="sxs-lookup"><span data-stu-id="cc797-227">`U+1F692 FIRE ENGINE` (supplementary range, requires a surrogate pair)</span></span>

<span data-ttu-id="cc797-228">前の例の一部 (結合アクセントの修飾子や肌の色の修飾子など) では、コード ポイントが画面にスタンドアロン要素として表示されません。</span><span class="sxs-lookup"><span data-stu-id="cc797-228">In some of the preceding examples - such as the combining accent modifier or the skin tone modifier - the code point does not display as a standalone element on the screen.</span></span> <span data-ttu-id="cc797-229">代わりに、それは、その前に現れるテキスト要素の外観を変更する役割を果たしています。</span><span class="sxs-lookup"><span data-stu-id="cc797-229">Rather, it serves to modify the appearance of a text element that came before it.</span></span> <span data-ttu-id="cc797-230">これらの例は、1 つの "文字" または "書記素クラスター" と見なされるものを構成するために、複数のスカラー値が必要になる場合があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="cc797-230">These examples show that it might take multiple scalar values to make up what we think of as a single "character," or "grapheme cluster."</span></span>

<span data-ttu-id="cc797-231">`string` の書記素クラスターを列挙するには、次の例に示すように <xref:System.Globalization.StringInfo> クラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="cc797-231">To enumerate the grapheme clusters of a `string`, use the <xref:System.Globalization.StringInfo> class as shown in the following example.</span></span> <span data-ttu-id="cc797-232">Swift に慣れている場合、.NET の `StringInfo` 型は、概念的に [Swift の `character` 型](https://developer.apple.com/documentation/swift/character)と似ています。</span><span class="sxs-lookup"><span data-stu-id="cc797-232">If you're familiar with Swift, the .NET `StringInfo` type is conceptually similar to [Swift's `character` type](https://developer.apple.com/documentation/swift/character).</span></span>

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a><span data-ttu-id="cc797-233">例: char、Rune、テキスト要素のインスタンス数を数える</span><span class="sxs-lookup"><span data-stu-id="cc797-233">Example: count char, Rune, and text element instances</span></span>

<span data-ttu-id="cc797-234">.NET API では、書記素クラスターは "*テキスト要素*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cc797-234">In .NET APIs, a grapheme cluster is called a *text element*.</span></span> <span data-ttu-id="cc797-235">次のメソッドは、`string` に含まれる `char`、`Rune`、およびテキスト要素のインスタンスの違いを示しています。</span><span class="sxs-lookup"><span data-stu-id="cc797-235">The following method demonstrates the differences between `char`, `Rune`, and text element instances in a `string`:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

<span data-ttu-id="cc797-236">.NET Framework または .NET Core 3.1 以前でこのコードを実行すると、絵文字のテキスト要素の数として `4` が表示されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-236">If you run this code in .NET Framework or .NET Core 3.1 or earlier, the text element count for the emoji shows `4`.</span></span> <span data-ttu-id="cc797-237">これは、.NET 5 で修正されている `StringInfo` クラスのバグが原因です。</span><span class="sxs-lookup"><span data-stu-id="cc797-237">That is due to a bug in the `StringInfo` class that is fixed in .NET 5.</span></span>

### <a name="example-splitting-opno-locstring-instances"></a><span data-ttu-id="cc797-238">例: string インスタンスの分割</span><span class="sxs-lookup"><span data-stu-id="cc797-238">Example: splitting string instances</span></span>

<span data-ttu-id="cc797-239">`string` インスタンスを分割する場合は、サロゲート ペアと書記素クラスターを分割しないようにします。</span><span class="sxs-lookup"><span data-stu-id="cc797-239">When splitting `string` instances, avoid splitting surrogate pairs and grapheme clusters.</span></span> <span data-ttu-id="cc797-240">不適切なコードを示す次の例について考えてみましょう。ここでは、string 内の 10 文字ごとに改行を挿入しようとしています。</span><span class="sxs-lookup"><span data-stu-id="cc797-240">Consider the following example of incorrect code, which intends to insert line breaks every 10 characters in a string:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

<span data-ttu-id="cc797-241">このコードでは `char` インスタンスが列挙されているため、10-`char` の境界にまたがるサロゲート ペアは分割され、それらの間に改行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-241">Because this code enumerates `char` instances, a surrogate pair that happens to straddle a 10-`char` boundary will be split and a newline injected between them.</span></span> <span data-ttu-id="cc797-242">サロゲート コード ポイントはペアとしてのみ意味があるので、この挿入によってデータの破損が発生します。</span><span class="sxs-lookup"><span data-stu-id="cc797-242">This insertion introduces data corruption, because surrogate code points are meaningful only as pairs.</span></span>

<span data-ttu-id="cc797-243">データの破損の可能性は、`char` インスタンスではなく `Rune` インスタンス (スカラー値) を列挙してもなくなりません。</span><span class="sxs-lookup"><span data-stu-id="cc797-243">The potential for data corruption isn't eliminated if you enumerate `Rune` instances (scalar values) instead of `char` instances.</span></span> <span data-ttu-id="cc797-244">`Rune` インスタンスのセットによって、10-`char` の境界にまたがる書記素クラスターが構成される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-244">A set of `Rune` instances might make up a grapheme cluster that straddles a 10-`char` boundary.</span></span> <span data-ttu-id="cc797-245">書記素クラスターのセットが分割された場合は、正しく解釈できません。</span><span class="sxs-lookup"><span data-stu-id="cc797-245">If the grapheme cluster set is split up, it can't be interpreted correctly.</span></span>

<span data-ttu-id="cc797-246">より適切なアプローチは、次の例のように、書記素クラスター (またはテキスト要素) をカウントすることによって string を分割することです。</span><span class="sxs-lookup"><span data-stu-id="cc797-246">A better approach is to break the string by counting grapheme clusters, or text elements, as in the following example:</span></span>

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

<span data-ttu-id="cc797-247">ただし、前述のように、.NET 5 以外の .NET の実装では、`StringInfo` クラスによって一部の書記素クラスターが不適切に処理される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-247">As noted earlier, however, in implementations of .NET other than .NET 5, the `StringInfo` class might handle some grapheme clusters incorrectly.</span></span>

## <a name="utf-8-and-utf-32"></a><span data-ttu-id="cc797-248">UTF-8 と UTF-32</span><span class="sxs-lookup"><span data-stu-id="cc797-248">UTF-8 and UTF-32</span></span>

<span data-ttu-id="cc797-249">前のセクションでは、UTF-16 に焦点を当てました。.NET では `string` インスタンスをエンコードするために UTF-16 が使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="cc797-249">The preceding sections focused on UTF-16 because that's what .NET uses to encode `string` instances.</span></span> <span data-ttu-id="cc797-250">Unicode には、他のエンコード システムもあります: [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) と [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32) です。</span><span class="sxs-lookup"><span data-stu-id="cc797-250">There are other encoding systems for Unicode - [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) and [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32).</span></span> <span data-ttu-id="cc797-251">これらのエンコードでは、8 ビットのコード単位と 32 ビットのコード単位がそれぞれ使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-251">These encodings use 8-bit code units and 32-bit code units, respectively.</span></span>

<span data-ttu-id="cc797-252">UTF-16 と同様に、UTF-8 では、一部の Unicode スカラー値を表すために複数のコード単位が必要になります。</span><span class="sxs-lookup"><span data-stu-id="cc797-252">Like UTF-16, UTF-8 requires multiple code units to represent some Unicode scalar values.</span></span> <span data-ttu-id="cc797-253">UTF-32 では、1 つの 32 ビット コード単位で任意のスカラー値を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="cc797-253">UTF-32 can represent any scalar value in a single 32-bit code unit.</span></span>

<span data-ttu-id="cc797-254">これら 3 つの各 Unicode エンコード システムで、同じ Unicode コード ポイントがどのように表されるかを示すいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-254">Here are some examples showing how the same Unicode code point is represented in each of these three Unicode encoding systems:</span></span>

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

<span data-ttu-id="cc797-255">前述のように、[サロゲート ペア](#surrogate-pairs)に由来する 1 つの UTF-16 コード単位は、単独では意味がありません。</span><span class="sxs-lookup"><span data-stu-id="cc797-255">As noted earlier, a single UTF-16 code unit from a [surrogate pair](#surrogate-pairs) is meaningless by itself.</span></span> <span data-ttu-id="cc797-256">同様に、1 つの UTF-8 コード単位が、スカラー値の計算に使用される 2 つ、3 つ、または 4 つのシーケンスに含まれている場合、それは単独では意味がありません。</span><span class="sxs-lookup"><span data-stu-id="cc797-256">In the same way, a single UTF-8 code unit is meaningless by itself if it's in a sequence of two, three, or four used to calculate a scalar value.</span></span>

### <a name="endianness"></a><span data-ttu-id="cc797-257">エンディアン</span><span class="sxs-lookup"><span data-stu-id="cc797-257">Endianness</span></span>

<span data-ttu-id="cc797-258">.NET では、string の UTF-16 コード単位は、16 ビット整数 (`char` インスタンス) のシーケンスとして連続したメモリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-258">In .NET, the UTF-16 code units of a string are stored in contiguous memory as a sequence of 16-bit integers (`char` instances).</span></span> <span data-ttu-id="cc797-259">個々のコード単位のビットは、現在のアーキテクチャの[エンディアン](https://en.wikipedia.org/wiki/Endianness)に従って並べられます。</span><span class="sxs-lookup"><span data-stu-id="cc797-259">The bits of individual code units are laid out according to the [endianness](https://en.wikipedia.org/wiki/Endianness) of the current architecture.</span></span>

<span data-ttu-id="cc797-260">リトル エンディアンのアーキテクチャでは、UTF-16 コード ポイント `[ D801 DCCC ]` で構成される string は、バイト `[ 0x01, 0xD8, 0xCC, 0xDC ]` としてメモリ内に並べられます。</span><span class="sxs-lookup"><span data-stu-id="cc797-260">On a little-endian architecture, the string consisting of the UTF-16 code points `[ D801 DCCC ]` would be laid out in memory as the bytes `[ 0x01, 0xD8, 0xCC, 0xDC ]`.</span></span> <span data-ttu-id="cc797-261">ビッグ エンディアンのアーキテクチャでは、同じ string がバイト `[ 0xD8, 0x01, 0xDC, 0xCC ]` としてメモリ内に並べられます。</span><span class="sxs-lookup"><span data-stu-id="cc797-261">On a big-endian architecture that same string would be laid out in memory as the bytes `[ 0xD8, 0x01, 0xDC, 0xCC ]`.</span></span>

<span data-ttu-id="cc797-262">相互に通信するコンピューター システムは、ネットワークを通過するデータの表現方法を一致させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-262">Computer systems that communicate with each other must agree on the representation of data crossing the wire.</span></span> <span data-ttu-id="cc797-263">ほとんどのネットワーク プロトコルでは、テキストの送信時に UTF-8 が標準として使用されます。その理由の一部は、ビッグ エンディアンのコンピューターがリトル エンディアンのコンピューターと通信する際に発生する可能性のある問題を回避するためです。</span><span class="sxs-lookup"><span data-stu-id="cc797-263">Most network protocols use UTF-8 as a standard when transmitting text, partly to avoid issues that might result from a big-endian machine communicating with a little-endian machine.</span></span> <span data-ttu-id="cc797-264">UTF-8 コード ポイント `[ F0 90 93 8C ]` で構成される string は、エンディアンに関係なく常にバイト `[ 0xF0, 0x90, 0x93, 0x8C ]` として表されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-264">The string consisting of the UTF-8 code points `[ F0 90 93 8C ]` will always be represented as the bytes `[ 0xF0, 0x90, 0x93, 0x8C ]` regardless of endianness.</span></span>

<span data-ttu-id="cc797-265">UTF-8 を使用してテキストを送信する場合、.NET アプリケーションでは、次の例のようなコードが使用されることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="cc797-265">To use UTF-8 for transmitting text, .NET applications often use code like the following example:</span></span>

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

<span data-ttu-id="cc797-266">前の例では、メソッド [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) によって UTF-16 の `string` が一連の Unicode スカラー値にデコードされ、そのスカラー値が UTF-8 に再エンコードされて、生成されたシーケンスが `byte` の配列に配置されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-266">In the preceding example, the method [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) decodes the UTF-16 `string` back into a series of Unicode scalar values, then it re-encodes those scalar values into UTF-8 and places the resulting sequence into a `byte` array.</span></span> <span data-ttu-id="cc797-267">メソッド [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) では反対の変換が実行されます。つまり、UTF-8 の `byte` 配列が UTF-16 の `string` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-267">The method [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) performs the opposite transformation, converting a UTF-8 `byte` array to a UTF-16 `string`.</span></span>

> [!WARNING]
> <span data-ttu-id="cc797-268">インターネット上では UTF-8 が一般的であるため、ネットワークから生バイトを読み取り、そのデータを UTF-8 であるかのように扱いたくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-268">Since UTF-8 is commonplace on the internet, it may be tempting to read raw bytes from the wire and to treat the data as if it were UTF-8.</span></span> <span data-ttu-id="cc797-269">しかし、それが本当に適切な形式であることを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-269">However, you should validate that it is indeed well-formed.</span></span> <span data-ttu-id="cc797-270">悪意のあるクライアントが、あなたのサービスに不適切な形式の UTF-8 を送信する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-270">A malicious client might submit ill-formed UTF-8 to your service.</span></span> <span data-ttu-id="cc797-271">そのデータが適切な形式であるかのように操作された場合、アプリケーションにエラーやセキュリティ ホールが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cc797-271">If you operate on that data as if it were well-formed, it could cause errors or security holes in your application.</span></span> <span data-ttu-id="cc797-272">UTF-8 のデータを検証するには、`Encoding.UTF8.GetString` のようなメソッドを使用できます。これは、受信データを `string` に変換するときに検証を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc797-272">To validate UTF-8 data, you can use a method like `Encoding.UTF8.GetString`, which will perform validation while converting the incoming data to a `string`.</span></span>

### <a name="well-formed-encoding"></a><span data-ttu-id="cc797-273">適切な形式のエンコード</span><span class="sxs-lookup"><span data-stu-id="cc797-273">Well-formed encoding</span></span>

<span data-ttu-id="cc797-274">適切な形式の Unicode エンコードとは、明確に、かつエラーなしで Unicode スカラー値のシーケンスにデコードできる、コード単位の string のことです。</span><span class="sxs-lookup"><span data-stu-id="cc797-274">A well-formed Unicode encoding is a string of code units that can be decoded unambiguously and without error into a sequence of Unicode scalar values.</span></span> <span data-ttu-id="cc797-275">適切な形式のデータは、UTF-8、UTF-16、および UTF-32 間で自由にトランスコードできます。</span><span class="sxs-lookup"><span data-stu-id="cc797-275">Well-formed data can be transcoded freely back and forth between UTF-8, UTF-16, and UTF-32.</span></span>

<span data-ttu-id="cc797-276">あるエンコード シーケンスが適切な形式であるかどうかは、コンピューターのアーキテクチャのエンディアンには関係ありません。</span><span class="sxs-lookup"><span data-stu-id="cc797-276">The question of whether an encoding sequence is well-formed or not is unrelated to the endianness of a machine's architecture.</span></span> <span data-ttu-id="cc797-277">不適切な形式の UTF-8 シーケンスは、ビッグ エンディアンのコンピューターでもリトル エンディアンのコンピューターでも、同じように不適切な形式になります。</span><span class="sxs-lookup"><span data-stu-id="cc797-277">An ill-formed UTF-8 sequence is ill-formed in the same way on both big-endian and little-endian machines.</span></span>

<span data-ttu-id="cc797-278">不適切な形式のエンコードの例を、次にいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-278">Here are some examples of ill-formed encodings:</span></span>

* <span data-ttu-id="cc797-279">UTF-8 では、シーケンス `[ 6C C2 61 ]` は不適切な形式です。`C2` の後に `61` を配置することはできないためです。</span><span class="sxs-lookup"><span data-stu-id="cc797-279">In UTF-8, the sequence `[ 6C C2 61 ]` is ill-formed because `C2` cannot be followed by `61`.</span></span>

* <span data-ttu-id="cc797-280">UTF-16 では、シーケンス `[ DC00 DD00 ]` (または、C# では、string `"\udc00\udd00"`) は不適切な形式です。下位サロゲート `DC00` の後に別の下位サロゲート `DD00` を配置することはできないためです。</span><span class="sxs-lookup"><span data-stu-id="cc797-280">In UTF-16, the sequence `[ DC00 DD00 ]` (or, in C#, the string `"\udc00\udd00"`) is ill-formed because the low surrogate `DC00` cannot be followed by another low surrogate `DD00`.</span></span>

* <span data-ttu-id="cc797-281">UTF-32 では、シーケンス `[ 0011ABCD ]` は不適切な形式です。`0011ABCD` が Unicode スカラー値の範囲外であるためです。</span><span class="sxs-lookup"><span data-stu-id="cc797-281">In UTF-32, the sequence `[ 0011ABCD ]` is ill-formed because `0011ABCD` is outside the range of Unicode scalar values.</span></span>

<span data-ttu-id="cc797-282">.NET では、`string` インスタンスにはほとんど常に適切な形式の UTF-16 データが含まれますが、保証されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="cc797-282">In .NET, `string` instances almost always contain well-formed UTF-16 data, but that isn't guaranteed.</span></span> <span data-ttu-id="cc797-283">`string` インスタンス内に不適切な形式の UTF-16 データを作成する有効な C# コードを、次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cc797-283">The following examples show valid C# code that creates ill-formed UTF-16 data in `string` instances.</span></span>

* <span data-ttu-id="cc797-284">不適切な形式のリテラル:</span><span class="sxs-lookup"><span data-stu-id="cc797-284">An ill-formed literal:</span></span>

  ```csharp
  const string s = "\ud800";
  ```

* <span data-ttu-id="cc797-285">サロゲート ペアを分割する部分文字列:</span><span class="sxs-lookup"><span data-stu-id="cc797-285">A substring that splits up a surrogate pair:</span></span>

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

<span data-ttu-id="cc797-286">[`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) のような API を使用する場合、不適切な形式の `string` インスタンスが返されることはありません。</span><span class="sxs-lookup"><span data-stu-id="cc797-286">APIs like [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) never return ill-formed `string` instances.</span></span> <span data-ttu-id="cc797-287">`Encoding.GetString` および `Encoding.GetBytes` メソッドでは、入力に含まれる不適切な形式のシーケンスが検出され、出力を生成する際に文字の置換が実行されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-287">`Encoding.GetString` and `Encoding.GetBytes` methods detect ill-formed sequences in the input and perform character substitution when generating the output.</span></span> <span data-ttu-id="cc797-288">たとえば、[`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) への入力に非 ASCII バイト (U+0000..U+007F の範囲外) が含まれていた場合、返される `string` インスタンスには '?' が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-288">For example, if [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) sees a non-ASCII byte in the input (outside the range U+0000..U+007F), it inserts a '?' into the returned `string` instance.</span></span> <span data-ttu-id="cc797-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) によって返される `string` インスタンスでは、不適切な形式の UTF-8 シーケンスが `U+FFFD REPLACEMENT CHARACTER ('�')` に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="cc797-289">[`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) replaces ill-formed UTF-8 sequences with `U+FFFD REPLACEMENT CHARACTER ('�')` in the returned `string` instance.</span></span> <span data-ttu-id="cc797-290">詳細については、[Unicode 標準](https://www.unicode.org/versions/latest/)の、セクション 5.22 および 3.9 を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cc797-290">For more information, see [the Unicode Standard](https://www.unicode.org/versions/latest/), Sections 5.22 and 3.9.</span></span>

<span data-ttu-id="cc797-291">組み込みの `Encoding` クラスは、不適切な形式のシーケンスが検出されたときに、文字の置換を実行するのではなく、例外をスローするように構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="cc797-291">The built-in `Encoding` classes can also be configured to throw an exception rather than perform character substitution when ill-formed sequences are seen.</span></span> <span data-ttu-id="cc797-292">この方法は、文字の置換が受け入れられない可能性がある、セキュリティに影響するアプリケーションでよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="cc797-292">This approach is often used in security-sensitive applications where character substitution might not be acceptable.</span></span>

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

<span data-ttu-id="cc797-293">組み込みの `Encoding` クラスの使用方法について詳しくは、「[.NET で文字エンコーディング クラスを使用する方法](character-encoding.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cc797-293">For information about how to use the built-in `Encoding` classes, see [How to use character encoding classes in .NET](character-encoding.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc797-294">関連項目</span><span class="sxs-lookup"><span data-stu-id="cc797-294">See also</span></span>

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [<span data-ttu-id="cc797-295">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="cc797-295">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
