---
title: 文字型 (Char)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 1ed5b19a307d094fc1d5a6bb0251c57052dc9bc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344045"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="49266-102">文字型 (Char) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="49266-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="49266-103">0 から 65535 までの値の範囲の符号なし 16 ビット (2 バイト) のコード ポイントを保持します。</span><span class="sxs-lookup"><span data-stu-id="49266-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="49266-104">各*コード ポイント* (文字コード) は、1 つの Unicode 文字を表します。</span><span class="sxs-lookup"><span data-stu-id="49266-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="49266-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="49266-105">Remarks</span></span>

<span data-ttu-id="49266-106">1 文字だけを保持する必要があり、`String` のオーバーヘッドを必要としない場合に、`Char` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="49266-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="49266-107">場合によっては、複数の文字を保持するために、`Char` 要素の配列である `Char()` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="49266-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="49266-108">`Char` の既定値は、コード ポイントが 0 の文字です。</span><span class="sxs-lookup"><span data-stu-id="49266-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="49266-109">Unicode 文字</span><span class="sxs-lookup"><span data-stu-id="49266-109">Unicode Characters</span></span>

<span data-ttu-id="49266-110">Unicode の最初の 128 コード ポイント (0 ～ 127) は、標準の米国キーボードの文字と記号に対応しています。</span><span class="sxs-lookup"><span data-stu-id="49266-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="49266-111">これらの最初の 128 コード ポイントは、ASCII 文字セットで定義されているものと同じです。</span><span class="sxs-lookup"><span data-stu-id="49266-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="49266-112">2 番目の 128 コード ポイント (128 ～ 255) は、ラテン語に基づくアルファベット文字、アクセント、通貨記号、分数などの特殊文字を表します。</span><span class="sxs-lookup"><span data-stu-id="49266-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="49266-113">Unicode では、残りのコード ポイント (256-65535) を、世界全体のテキスト文字、分音記号、数学記号、技術記号などの多様な記号に使用しています。</span><span class="sxs-lookup"><span data-stu-id="49266-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="49266-114">`Char` 変数に対して <xref:System.Char.IsDigit%2A> や <xref:System.Char.IsPunctuation%2A> などのメソッドを使用して、その Unicode の分類を判断できます。</span><span class="sxs-lookup"><span data-stu-id="49266-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="49266-115">型変換</span><span class="sxs-lookup"><span data-stu-id="49266-115">Type Conversions</span></span>

<span data-ttu-id="49266-116">Visual Basic では、`Char` と数値型の間で直接に変換されません。</span><span class="sxs-lookup"><span data-stu-id="49266-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="49266-117"><xref:Microsoft.VisualBasic.Strings.Asc%2A> または <xref:Microsoft.VisualBasic.Strings.AscW%2A> 関数を使用して、`Char` 値をそのコード ポイントを表す `Integer` に変換できます。</span><span class="sxs-lookup"><span data-stu-id="49266-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="49266-118"><xref:Microsoft.VisualBasic.Strings.Chr%2A> または <xref:Microsoft.VisualBasic.Strings.ChrW%2A> 関数を使用して、`Integer` 値をそのコード ポイントを持つ `Char` に変換できます。</span><span class="sxs-lookup"><span data-stu-id="49266-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="49266-119">型チェック スイッチ ([Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)) がオンになっている場合、リテラル型の文字を 1 文字の文字列リテラルに追加して、`Char` データ型として識別する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49266-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="49266-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="49266-120">The following example illustrates this.</span></span> <span data-ttu-id="49266-121">`charVar` 変数への最初の代入では、`Option Strict` がオンになっているため、コンパイラ エラー [BC30512](../../misc/bc30512.md) が生成されます。</span><span class="sxs-lookup"><span data-stu-id="49266-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="49266-122">2 つ目は、リテラル型の文字 `c` によって、リテラルが `Char` 値として識別されるため、正常にコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="49266-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="49266-123">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="49266-123">Programming Tips</span></span>

- <span data-ttu-id="49266-124">**負の数値。**</span><span class="sxs-lookup"><span data-stu-id="49266-124">**Negative Numbers.**</span></span> <span data-ttu-id="49266-125">`Char` は符号なしの型であるため、負の値を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="49266-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="49266-126">いかなる場合でも、`Char` を使用して数値を保持しないでください。</span><span class="sxs-lookup"><span data-stu-id="49266-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="49266-127">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="49266-127">**Interop Considerations.**</span></span> <span data-ttu-id="49266-128">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとやり取りする場合、他の環境では文字型のデータ幅 (8 ビット) が異なることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="49266-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="49266-129">そのようなコンポーネントに 8 ビットの引数を渡す場合は、新しい Visual Basic のコードで、`Char` ではなく `Byte` として宣言します。</span><span class="sxs-lookup"><span data-stu-id="49266-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="49266-130">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="49266-130">**Widening.**</span></span> <span data-ttu-id="49266-131">`Char` データ型は、`String` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="49266-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="49266-132">つまり、`Char` を `String` に変換でき、<xref:System.OverflowException?displayProperty=nameWithType> は発生しません。</span><span class="sxs-lookup"><span data-stu-id="49266-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="49266-133">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="49266-133">**Type Characters.**</span></span> <span data-ttu-id="49266-134">1 文字の文字列リテラルにリテラルの型文字 `C` を付けると、それは `Char` データ型に変換されます。</span><span class="sxs-lookup"><span data-stu-id="49266-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="49266-135">`Char` には識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="49266-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="49266-136">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="49266-136">**Framework Type.**</span></span> <span data-ttu-id="49266-137">.NET Framework において対応する型は、<xref:System.Char?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="49266-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="49266-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="49266-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="49266-139">データの種類</span><span class="sxs-lookup"><span data-stu-id="49266-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="49266-140">String データ型</span><span class="sxs-lookup"><span data-stu-id="49266-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="49266-141">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="49266-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="49266-142">変換の概要</span><span class="sxs-lookup"><span data-stu-id="49266-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="49266-143">方法: 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="49266-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="49266-144">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="49266-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
