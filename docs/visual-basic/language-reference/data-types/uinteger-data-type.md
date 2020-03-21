---
title: UInteger 型
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: ccff61608aed797734cb4f5ca0571d7ed73ba98b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401377"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="f5133-102">UInteger データ型</span><span class="sxs-lookup"><span data-stu-id="f5133-102">UInteger data type</span></span>

<span data-ttu-id="f5133-103">0 から 4,294,967,295 までの範囲の符号なし 32 ビット (4 バイト) 整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="f5133-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5133-104">解説</span><span class="sxs-lookup"><span data-stu-id="f5133-104">Remarks</span></span>

<span data-ttu-id="f5133-105">データ`UInteger`型は、最も効率的なデータ幅で最大の符号なし値を提供します。</span><span class="sxs-lookup"><span data-stu-id="f5133-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>

<span data-ttu-id="f5133-106">`UInteger` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="f5133-106">The default value of `UInteger` is 0.</span></span>

## <a name="literal-assignments"></a><span data-ttu-id="f5133-107">リテラル代入</span><span class="sxs-lookup"><span data-stu-id="f5133-107">Literal assignments</span></span>

<span data-ttu-id="f5133-108">変数を`UInteger`宣言して初期化するには、10 進リテラル、16 進リテラル、8 進数リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="f5133-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="f5133-109">整数リテラルが `UInteger` の範囲外にある場合 (つまり、<xref:System.UInt32.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.UInt32.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="f5133-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="f5133-110">次の例では、整数 3,000,000,000 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、`UInteger` 値に割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="f5133-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]

> [!NOTE]
> <span data-ttu-id="f5133-111">プレフィックス`&h`を使用`&H`するか、16 進リテラル、プレフィックス`&b`、または`&B`バイナリ リテラルを表す場合、およびプレフィックス`&o`を`&O`表すか、8 進数リテラルを表します。</span><span class="sxs-lookup"><span data-stu-id="f5133-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="f5133-112">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="f5133-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="f5133-113">Visual Basic 2017 以降では、`_`下線付きの文字を桁区切り記号として使用して読みやすさを向上させることもできます。</span><span class="sxs-lookup"><span data-stu-id="f5133-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]

<span data-ttu-id="f5133-114">Visual Basic 15.5 以降では、接頭辞と`_`16 進数、2 進数、または 8 進数の間の先頭の区切り記号としてアンダースコア文字 ( ) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f5133-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="f5133-115">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="f5133-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="f5133-116">次の例に示すように、`UI`数値`ui`リテラルには`UInteger`、データ型を示す[or 型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="f5133-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="f5133-117">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="f5133-117">Programming tips</span></span>

<span data-ttu-id="f5133-118">`Integer`および`UInteger`データ型は、使用するビット数が少なくても、より少ない整数型 (`UShort` `Short`、 `Byte`、 `SByte`、 、 ) が読み込み、格納、およびフェッチに時間がかかるため、32 ビット プロセッサで最適なパフォーマンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="f5133-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>

- <span data-ttu-id="f5133-119">**負の数。**</span><span class="sxs-lookup"><span data-stu-id="f5133-119">**Negative Numbers.**</span></span> <span data-ttu-id="f5133-120">符号`UInteger`なしの型であるため、負の数を表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="f5133-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="f5133-121">型`-``UInteger`と評価される式に単項マイナス ( ) 演算子を使用すると、その式が最初に`Long`変換されます。</span><span class="sxs-lookup"><span data-stu-id="f5133-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>

- <span data-ttu-id="f5133-122">**CLS コンプライアンス。**</span><span class="sxs-lookup"><span data-stu-id="f5133-122">**CLS Compliance.**</span></span> <span data-ttu-id="f5133-123">データ`UInteger`型は[共通言語仕様](https://www.ecma-international.org/publications/standards/Ecma-335.htm)(CLS) の一部ではないため、CLS 準拠のコードで使用するコンポーネントを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="f5133-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>

- <span data-ttu-id="f5133-124">**相互運用の考慮事項。**</span><span class="sxs-lookup"><span data-stu-id="f5133-124">**Interop Considerations.**</span></span> <span data-ttu-id="f5133-125">オートメーション オブジェクトや COM オブジェクトなど、.NET Framework 用に作成されていないコンポーネントとインターフェイスを使用している場合は、他`uint`の環境ではデータ幅 (16 ビット) が異なる型が使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5133-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="f5133-126">このようなコンポーネントに 16 ビットの引数を渡す場合は、マネージ`UShort`Visual `UInteger` Basic コードではなく、それを宣言します。</span><span class="sxs-lookup"><span data-stu-id="f5133-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>

- <span data-ttu-id="f5133-127">**拡大。**</span><span class="sxs-lookup"><span data-stu-id="f5133-127">**Widening.**</span></span> <span data-ttu-id="f5133-128">データ`UInteger`型は`Long`、 、 `ULong`、 `Decimal` `Single`、 `Double`、 、 、 にまで広がります。</span><span class="sxs-lookup"><span data-stu-id="f5133-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="f5133-129">つまり、<xref:System.OverflowException?displayProperty=nameWithType>エラーが発生`UInteger`することなく、これらの型に変換できます。</span><span class="sxs-lookup"><span data-stu-id="f5133-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>

- <span data-ttu-id="f5133-130">**文字を入力します。**</span><span class="sxs-lookup"><span data-stu-id="f5133-130">**Type Characters.**</span></span> <span data-ttu-id="f5133-131">リテラルにリテラルの型文字`UI`を追加すると、データ型に`UInteger`強制的に追加されます。</span><span class="sxs-lookup"><span data-stu-id="f5133-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="f5133-132">`UInteger`識別子の種類の文字がありません。</span><span class="sxs-lookup"><span data-stu-id="f5133-132">`UInteger` has no identifier type character.</span></span>

- <span data-ttu-id="f5133-133">**Framework のデータ型**</span><span class="sxs-lookup"><span data-stu-id="f5133-133">**Framework Type.**</span></span> <span data-ttu-id="f5133-134">.NET Framework において対応する型は、<xref:System.UInt32?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="f5133-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5133-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5133-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="f5133-136">データ型</span><span class="sxs-lookup"><span data-stu-id="f5133-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="f5133-137">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="f5133-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="f5133-138">変換の概要</span><span class="sxs-lookup"><span data-stu-id="f5133-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="f5133-139">方法 : 符号なしの型を使用する Windows の機能を呼び出す</span><span class="sxs-lookup"><span data-stu-id="f5133-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="f5133-140">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="f5133-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
