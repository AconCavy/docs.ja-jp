---
title: Short 型
ms.date: 01/31/2018
f1_keywords:
- vb.Short
helpviewer_keywords:
- numbers [Visual Basic], whole
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- data types [Visual Basic], integral
- S literal type character [Visual Basic]
- Short data type
- literal type characters [Visual Basic], S
ms.assetid: 65fcbcf3-a841-400e-885e-301497729a8b
ms.openlocfilehash: 8dfdfb56de32e4b3a96729b09ccf46a6fee9a424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401341"
---
# <a name="short-data-type-visual-basic"></a><span data-ttu-id="0c8cd-102">Short データ型 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c8cd-102">Short data type (Visual Basic)</span></span>

<span data-ttu-id="0c8cd-103">-32,768 から 32,767 までの符号付き 16 ビット (2 バイト) の整数を保持します。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-103">Holds signed 16-bit (2-byte) integers that range in value from -32,768 through 32,767.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c8cd-104">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c8cd-104">Remarks</span></span>  

 <span data-ttu-id="0c8cd-105">`Integer` の完全なデータ幅を必要としない整数値を格納するには、`Short` データ型を使用します。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-105">Use the `Short` data type to contain integer values that do not require the full data width of `Integer`.</span></span> <span data-ttu-id="0c8cd-106">場合によっては、共通言語ランタイムで `Short` 変数を緊密にパックし、メモリ消費を節約できます。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-106">In some cases, the common language runtime can pack your `Short` variables closely together and save memory consumption.</span></span>  
  
 <span data-ttu-id="0c8cd-107">`Short` の既定値は 0 です。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-107">The default value of `Short` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="0c8cd-108">リテラルの代入</span><span class="sxs-lookup"><span data-stu-id="0c8cd-108">Literal assignments</span></span>

<span data-ttu-id="0c8cd-109">`Short` 変数を宣言し、10 進リテラル、16 進リテラル、8 進リテラル、または (Visual Basic 2017 以降) バイナリ リテラルを代入することによって初期化できます。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-109">You can declare and initialize a `Short` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="0c8cd-110">整数リテラルが `Short` の範囲外にある場合 (つまり、<xref:System.Int16.MinValue?displayProperty=nameWithType> より小さいか、<xref:System.Int16.MaxValue?displayProperty=nameWithType> より大きい場合)、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-110">If the integer literal is outside the range of `Short` (that is, if it is less than <xref:System.Int16.MinValue?displayProperty=nameWithType> or greater than <xref:System.Int16.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="0c8cd-111">次の例では、整数 1,034 を 10 進リテラル、16 進リテラル、バイナリ リテラルで表したものが、[Integer](integer-data-type.md) から `Short` 値に暗黙的に変換されています。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-111">In the following example, integers equal to 1,034 that are represented as decimal, hexadecimal, and binary literals are implicitly converted from [Integer](integer-data-type.md) to `Short` values.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#Short)]

> [!NOTE]
> <span data-ttu-id="0c8cd-112">16 進リテラルを表すにはプレフィックス `&h` または `&H` を使い、バイナリ リテラルを表すにはプレフィックス `&b` または `&B` を使い、8 進リテラルを表すにはプレフィックス `&o` または `&O` を使います。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-112">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="0c8cd-113">10 進リテラルには、プレフィックスはありません。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-113">Decimal literals have no prefix.</span></span>

<span data-ttu-id="0c8cd-114">Visual Basic 2017 以降では、次の例に示すように、アンダースコア文字 `_` を桁区切り記号として使って読みやすくすることもできます。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-114">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[Short](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#ShortS)]

<span data-ttu-id="0c8cd-115">Visual Basic 15.5 以降では、プレフィックスと 16 進数、2 進数、または 8 進数の間に先頭の区切り記号としてアンダースコア文字 (`_`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-115">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="0c8cd-116">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-116">For example:</span></span>

```vb
Dim number As Short = &H_3264
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="0c8cd-117">数値リテラルには、次の例に示すように、`S` [型文字](../../programming-guide/language-features/data-types/type-characters.md)を含めて、`Short` データ型を表すこともできます。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-117">Numeric literals can also include the `S` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `Short` data type, as the following example shows.</span></span>

```vb
Dim number = &H_3264S
```

## <a name="programming-tips"></a><span data-ttu-id="0c8cd-118">プログラミングのヒント</span><span class="sxs-lookup"><span data-stu-id="0c8cd-118">Programming tips</span></span>

- <span data-ttu-id="0c8cd-119">**拡大変換。**</span><span class="sxs-lookup"><span data-stu-id="0c8cd-119">**Widening.**</span></span> <span data-ttu-id="0c8cd-120">`Short` データ型は、`Integer`、`Long`、`Decimal`、`Single`、または `Double` に拡大変換されます。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-120">The `Short` data type widens to `Integer`, `Long`, `Decimal`, `Single`, or `Double`.</span></span> <span data-ttu-id="0c8cd-121">これは、`Short` エラーを発生させることなく、これらの型のいずれかに <xref:System.OverflowException?displayProperty=nameWithType> を変換できることを意味します。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-121">This means you can convert `Short` to any one of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="0c8cd-122">**型文字。**</span><span class="sxs-lookup"><span data-stu-id="0c8cd-122">**Type Characters.**</span></span> <span data-ttu-id="0c8cd-123">あるリテラルにリテラルの型文字 `S` を付けると、そのリテラルは `Short` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-123">Appending the literal type character `S` to a literal forces it to the `Short` data type.</span></span> <span data-ttu-id="0c8cd-124">`Short` には識別子の型文字がありません。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-124">`Short` has no identifier type character.</span></span>  
  
- <span data-ttu-id="0c8cd-125">**Framework の型。**</span><span class="sxs-lookup"><span data-stu-id="0c8cd-125">**Framework Type.**</span></span> <span data-ttu-id="0c8cd-126">.NET Framework において対応する型は、<xref:System.Int16?displayProperty=nameWithType> 構造体です。</span><span class="sxs-lookup"><span data-stu-id="0c8cd-126">The corresponding type in the .NET Framework is the <xref:System.Int16?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c8cd-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c8cd-127">See also</span></span>

- <xref:System.Int16?displayProperty=nameWithType>
- [<span data-ttu-id="0c8cd-128">データの種類</span><span class="sxs-lookup"><span data-stu-id="0c8cd-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="0c8cd-129">データ型変換関数</span><span class="sxs-lookup"><span data-stu-id="0c8cd-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="0c8cd-130">変換の概要</span><span class="sxs-lookup"><span data-stu-id="0c8cd-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="0c8cd-131">Integer データ型</span><span class="sxs-lookup"><span data-stu-id="0c8cd-131">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="0c8cd-132">Long データ型</span><span class="sxs-lookup"><span data-stu-id="0c8cd-132">Long Data Type</span></span>](../../../visual-basic/language-reference/data-types/long-data-type.md)
- [<span data-ttu-id="0c8cd-133">データ型の有効な使用方法</span><span class="sxs-lookup"><span data-stu-id="0c8cd-133">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
