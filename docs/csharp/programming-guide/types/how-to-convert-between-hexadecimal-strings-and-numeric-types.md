---
title: 16 進文字列と数値型の間で変換する方法 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 0e1f6ad2606b367d369c1c644c947831b2aa8289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698522"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="72093-102">16 進文字列と数値型の間で変換する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="72093-102">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>
<span data-ttu-id="72093-103">以下の例では、次のタスクを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72093-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="72093-104">[string](../../language-reference/builtin-types/reference-types.md) の各文字の 16 進値を取得する。</span><span class="sxs-lookup"><span data-stu-id="72093-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="72093-105">16 進文字列の各値に対応する [char](../../language-reference/builtin-types/char.md) を取得する。</span><span class="sxs-lookup"><span data-stu-id="72093-105">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="72093-106">16 進 `string` を [int](../../language-reference/builtin-types/integral-numeric-types.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="72093-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="72093-107">16 進 `string` を [float](../../language-reference/builtin-types/floating-point-numeric-types.md) に変換する。</span><span class="sxs-lookup"><span data-stu-id="72093-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="72093-108">[バイト](../../language-reference/builtin-types/integral-numeric-types.md)配列を 16 進 `string` に変換する。</span><span class="sxs-lookup"><span data-stu-id="72093-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72093-109">例</span><span class="sxs-lookup"><span data-stu-id="72093-109">Example</span></span>  
 <span data-ttu-id="72093-110">この例では、`string` の各文字の 16 進値を出力しています。</span><span class="sxs-lookup"><span data-stu-id="72093-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="72093-111">まず `string` を解析し、文字配列に変換します。</span><span class="sxs-lookup"><span data-stu-id="72093-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="72093-112">次いで、その数値を取得するために、各文字で <xref:System.Convert.ToInt32%28System.Char%29> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="72093-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="72093-113">最後に、その数を 16 進表現で `string` に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="72093-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="72093-114">例</span><span class="sxs-lookup"><span data-stu-id="72093-114">Example</span></span>  
 <span data-ttu-id="72093-115">この例は、16 進値の `string` を解析し、各 16 進値に対応する文字を出力しています。</span><span class="sxs-lookup"><span data-stu-id="72093-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="72093-116">まず、[Split(Char\[\])](xref:System.String.Split(System.Char[])) メソッドを呼び出して、各 16 進値を配列内の個別の `string` として取得します。</span><span class="sxs-lookup"><span data-stu-id="72093-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="72093-117">次いで <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> を呼び出し、16 進数値を [int](../../language-reference/builtin-types/integral-numeric-types.md) の 10 進数値に変換します。ここでは、その文字コードに対応する文字を取得するための 2 つの方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="72093-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="72093-118">1 つは、<xref:System.Char.ConvertFromUtf32%28System.Int32%29> を使用する方法です。これは、整数引数に対応する文字を `string` として返します。</span><span class="sxs-lookup"><span data-stu-id="72093-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="72093-119">もう 1 つは、`int` を明示的に [char](../../language-reference/builtin-types/char.md) にキャストする方法です。</span><span class="sxs-lookup"><span data-stu-id="72093-119">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="72093-120">例</span><span class="sxs-lookup"><span data-stu-id="72093-120">Example</span></span>  
 <span data-ttu-id="72093-121">この例では、<xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> メソッドを呼び出し、16 進数 `string` を整数に変換する、別の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72093-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="72093-122">例</span><span class="sxs-lookup"><span data-stu-id="72093-122">Example</span></span>  
 <span data-ttu-id="72093-123">次の例では、<xref:System.BitConverter?displayProperty=nameWithType> クラスおよび <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> メソッドを使用して、16 進数の `string` を [float](../../language-reference/builtin-types/floating-point-numeric-types.md) に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72093-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="72093-124">例</span><span class="sxs-lookup"><span data-stu-id="72093-124">Example</span></span>  
 <span data-ttu-id="72093-125">次の例は、<xref:System.BitConverter?displayProperty=nameWithType> クラスを使用して [byte](../../language-reference/builtin-types/integral-numeric-types.md) 配列を 16 進文字列に変換する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="72093-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="72093-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="72093-126">See also</span></span>

- [<span data-ttu-id="72093-127">標準の数値書式指定文字列</span><span class="sxs-lookup"><span data-stu-id="72093-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="72093-128">型</span><span class="sxs-lookup"><span data-stu-id="72093-128">Types</span></span>](./index.md)
- [<span data-ttu-id="72093-129">文字列が数値を表しているかどうかを確認する方法</span><span class="sxs-lookup"><span data-stu-id="72093-129">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
