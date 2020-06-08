---
title: 量指定子 (正規表現)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, quantifiers
- metacharacters, quantifiers
- minimal matching quantifiers
- quantifiers in regular expressions
- .NET Framework regular expressions, quantifiers
- quantifiers
- lazy quantifiers
ms.assetid: 36b81212-6511-49ed-a8f1-ff080415312f
ms.openlocfilehash: dbfe4422b89b6223988ec9c6034d4b91b6ec8b5d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276149"
---
# <a name="quantifiers-in-regular-expressions"></a><span data-ttu-id="97d9d-102">量指定子 (正規表現)</span><span class="sxs-lookup"><span data-stu-id="97d9d-102">Quantifiers in Regular Expressions</span></span>
<span data-ttu-id="97d9d-103">量指定子は、一致と見なされるために入力中に存在する必要がある文字、グループ、または文字クラスの出現数を指定します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-103">Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found.</span></span>  <span data-ttu-id="97d9d-104">次の表に、.NET でサポートされている量指定子の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-104">The following table lists the quantifiers supported by .NET.</span></span>  
  
|<span data-ttu-id="97d9d-105">最長一致の量指定子</span><span class="sxs-lookup"><span data-stu-id="97d9d-105">Greedy quantifier</span></span>|<span data-ttu-id="97d9d-106">最短一致の量指定子</span><span class="sxs-lookup"><span data-stu-id="97d9d-106">Lazy quantifier</span></span>|<span data-ttu-id="97d9d-107">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-107">Description</span></span>|  
|-----------------------|---------------------|-----------------|  
|`*`|`*?`|<span data-ttu-id="97d9d-108">0 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-108">Match zero or more times.</span></span>|  
|`+`|`+?`|<span data-ttu-id="97d9d-109">1 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-109">Match one or more times.</span></span>|  
|`?`|`??`|<span data-ttu-id="97d9d-110">0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-110">Match zero or one time.</span></span>|  
|<span data-ttu-id="97d9d-111">`{` *n* `}`</span><span class="sxs-lookup"><span data-stu-id="97d9d-111">`{` *n* `}`</span></span>|<span data-ttu-id="97d9d-112">`{` *n* `}?`</span><span class="sxs-lookup"><span data-stu-id="97d9d-112">`{` *n* `}?`</span></span>|<span data-ttu-id="97d9d-113">*n* 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-113">Match exactly *n* times.</span></span>|  
|<span data-ttu-id="97d9d-114">`{` *n* `,}`</span><span class="sxs-lookup"><span data-stu-id="97d9d-114">`{` *n* `,}`</span></span>|<span data-ttu-id="97d9d-115">`{` *n* `,}?`</span><span class="sxs-lookup"><span data-stu-id="97d9d-115">`{` *n* `,}?`</span></span>|<span data-ttu-id="97d9d-116">*n* 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-116">Match at least *n* times.</span></span>|  
|<span data-ttu-id="97d9d-117">`{` *n* `,` *m* `}`</span><span class="sxs-lookup"><span data-stu-id="97d9d-117">`{` *n* `,` *m* `}`</span></span>|<span data-ttu-id="97d9d-118">`{` *n* `,` *m* `}?`</span><span class="sxs-lookup"><span data-stu-id="97d9d-118">`{` *n* `,` *m* `}?`</span></span>|<span data-ttu-id="97d9d-119">*n* 回から *m* 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-119">Match from *n* to *m* times.</span></span>|  
  
 <span data-ttu-id="97d9d-120">量 `n` および `m` は整数の定数です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-120">The quantities `n` and `m` are integer constants.</span></span> <span data-ttu-id="97d9d-121">通常、量指定子は最長一致です。最長一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ多くなるように照合が行われます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-121">Ordinarily, quantifiers are greedy; they cause the regular expression engine to match as many occurrences of particular patterns as possible.</span></span> <span data-ttu-id="97d9d-122">量指定子に `?` 文字を付けると最短一致になります。最短一致の場合、正規表現エンジンでは、特定のパターンの繰り返しができるだけ少なくなるように照合が行われます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-122">Appending the `?` character to a quantifier makes it lazy; it causes the regular expression engine to match as few occurrences as possible.</span></span> <span data-ttu-id="97d9d-123">最長一致と最短一致の量指定子の違いの詳細については、このトピックの「[最長一致と最短一致の量指定子](#Greedy)」のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="97d9d-123">For a complete description of the difference between greedy and lazy quantifiers, see the section [Greedy and Lazy Quantifiers](#Greedy) later in this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="97d9d-124">量指定子を入れ子にすると (たとえば、正規表現パターン `(a*)*` など)、入力文字列の文字数に応じて指数関数的に、正規表現エンジンで実行する必要がある比較の回数が増加する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="97d9d-124">Nesting quantifiers (for example, as the regular expression pattern `(a*)*` does) can increase the number of comparisons that the regular expression engine must perform, as an exponential function of the number of characters in the input string.</span></span> <span data-ttu-id="97d9d-125">この動作と回避方法の詳細については、[バックトラッキング](backtracking-in-regular-expressions.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="97d9d-125">For more information about this behavior and its workarounds, see [Backtracking](backtracking-in-regular-expressions.md).</span></span>  
  
## <a name="regular-expression-quantifiers"></a><span data-ttu-id="97d9d-126">正規表現の量指定子</span><span class="sxs-lookup"><span data-stu-id="97d9d-126">Regular Expression Quantifiers</span></span>  
 <span data-ttu-id="97d9d-127">以降のセクションでは、.NET の正規表現でサポートされている量指定子について説明します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-127">The following sections list the quantifiers supported by .NET regular expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97d9d-128">正規表現エンジンでは、正規表現パターンで \*、+、?、{、および } の各文字を検出すると、[文字クラス](character-classes-in-regular-expressions.md)に含まれているもの以外は量指定子または量指定子コンストラクトの一部として解釈します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-128">If the \*, +, ?, {, and } characters are encountered in a regular expression pattern, the regular expression engine interprets them as quantifiers or part of quantifier constructs unless they are included in a [character class](character-classes-in-regular-expressions.md).</span></span> <span data-ttu-id="97d9d-129">文字クラスの外側でこれらをリテラル文字として解釈するには、文字の前に円記号を付けてエスケープする必要があります。</span><span class="sxs-lookup"><span data-stu-id="97d9d-129">To interpret these as literal characters outside a character class, you must escape them by preceding them with a backslash.</span></span> <span data-ttu-id="97d9d-130">たとえば、正規表現パターン内の `\*` という文字列は、リテラルのアスタリスク ("\*") 文字と解釈されます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-130">For example, the string `\*` in a regular expression pattern is interpreted as a literal asterisk ("\*") character.</span></span>  
  
### <a name="match-zero-or-more-times-"></a><span data-ttu-id="97d9d-131">0 回以上の繰り返しに一致: \*</span><span class="sxs-lookup"><span data-stu-id="97d9d-131">Match Zero or More Times: \*</span></span>  
 <span data-ttu-id="97d9d-132">`*` 量指定子は、直前の要素の 0 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-132">The `*` quantifier matches the preceding element zero or more times.</span></span> <span data-ttu-id="97d9d-133">これは `{0,}` 量指定子と同じです。</span><span class="sxs-lookup"><span data-stu-id="97d9d-133">It is equivalent to the `{0,}` quantifier.</span></span> <span data-ttu-id="97d9d-134">`*` は最長一致の量指定子であり、最短一致でこれに対応するのは `*?` です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-134">`*` is a greedy quantifier whose lazy equivalent is `*?`.</span></span>  
  
 <span data-ttu-id="97d9d-135">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-135">The following example illustrates this regular expression.</span></span> <span data-ttu-id="97d9d-136">入力文字列の 9 個の数字のうち、5 個がパターンに一致し、4 個 (`95`、`929`、`9219`、および `9919`) が一致しません。</span><span class="sxs-lookup"><span data-stu-id="97d9d-136">Of the nine digits in the input string, five match the pattern and four (`95`, `929`, `9219`, and `9919`) do not.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#1)]  
  
 <span data-ttu-id="97d9d-137">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-137">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-138">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-138">Pattern</span></span>|<span data-ttu-id="97d9d-139">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-139">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-140">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-140">Start at a word boundary.</span></span>|  
|`91*`|<span data-ttu-id="97d9d-141">"9" の後に文字 "1" が 0 個以上続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-141">Match a "9" followed by zero or more "1" characters.</span></span>|  
|`9*`|<span data-ttu-id="97d9d-142">0 個以上の文字 "9" に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-142">Match zero or more "9" characters.</span></span>|  
|`\b`|<span data-ttu-id="97d9d-143">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-143">End at a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-"></a><span data-ttu-id="97d9d-144">1 回以上の繰り返しに一致: +</span><span class="sxs-lookup"><span data-stu-id="97d9d-144">Match One or More Times: +</span></span>  
 <span data-ttu-id="97d9d-145">`+` 量指定子は、直前の要素の 1 回以上の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-145">The `+` quantifier matches the preceding element one or more times.</span></span> <span data-ttu-id="97d9d-146">これは `{1,}` と同じです。</span><span class="sxs-lookup"><span data-stu-id="97d9d-146">It is equivalent to `{1,}`.</span></span> <span data-ttu-id="97d9d-147">`+` は最長一致の量指定子であり、最短一致でこれに対応するのは `+?` です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-147">`+` is a greedy quantifier whose lazy equivalent is `+?`.</span></span>  
  
 <span data-ttu-id="97d9d-148">たとえば、正規表現 `\ban+\w*?\b` は、文字 `a` で始まり、文字 `n` が 1 回以上繰り返されるすべての単語に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-148">For example, the regular expression `\ban+\w*?\b` tries to match entire words that begin with the letter `a` followed by one or more instances of the letter `n`.</span></span> <span data-ttu-id="97d9d-149">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-149">The following example illustrates this regular expression.</span></span> <span data-ttu-id="97d9d-150">この正規表現は、単語 `an`、`annual`、`announcement`、および `antique` に一致し、`autumn` と `all` では不一致となります。</span><span class="sxs-lookup"><span data-stu-id="97d9d-150">The regular expression matches the words `an`, `annual`, `announcement`, and `antique`, and correctly fails to match `autumn` and `all`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#2)]  
  
 <span data-ttu-id="97d9d-151">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-151">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-152">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-152">Pattern</span></span>|<span data-ttu-id="97d9d-153">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-153">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-154">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-154">Start at a word boundary.</span></span>|  
|`an+`|<span data-ttu-id="97d9d-155">"a" の後に文字 "n" が 1 個以上続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-155">Match an "a" followed by one or more "n" characters.</span></span>|  
|`\w*?`|<span data-ttu-id="97d9d-156">単語に含まれる文字の 0 回以上の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-156">Match a word character zero or more times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="97d9d-157">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-157">End at a word boundary.</span></span>|  
  
### <a name="match-zero-or-one-time-"></a><span data-ttu-id="97d9d-158">0 回または 1 回の繰り返しに一致: ?</span><span class="sxs-lookup"><span data-stu-id="97d9d-158">Match Zero or One Time: ?</span></span>  
 <span data-ttu-id="97d9d-159">`?` 量指定子は、直前の要素の 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-159">The `?` quantifier matches the preceding element zero or one time.</span></span> <span data-ttu-id="97d9d-160">これは `{0,1}` と同じです。</span><span class="sxs-lookup"><span data-stu-id="97d9d-160">It is equivalent to `{0,1}`.</span></span> <span data-ttu-id="97d9d-161">`?` は最長一致の量指定子であり、最短一致でこれに対応するのは `??` です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-161">`?` is a greedy quantifier whose lazy equivalent is `??`.</span></span>  
  
 <span data-ttu-id="97d9d-162">たとえば、正規表現 `\ban?\b` は、文字 `a` で始まり、文字 `n` が 0 回または 1 回繰り返されるすべての単語に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-162">For example, the regular expression `\ban?\b` tries to match entire words that begin with the letter `a` followed by zero or one instances of the letter `n`.</span></span> <span data-ttu-id="97d9d-163">つまり、単語 `a` と `an` に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-163">In other words, it tries to match the words `a` and `an`.</span></span> <span data-ttu-id="97d9d-164">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-164">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#3](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#3)]
 [!code-vb[RegularExpressions.Quantifiers#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#3)]  
  
 <span data-ttu-id="97d9d-165">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-165">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-166">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-166">Pattern</span></span>|<span data-ttu-id="97d9d-167">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-167">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-168">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-168">Start at a word boundary.</span></span>|  
|`an?`|<span data-ttu-id="97d9d-169">"a" の後に文字 "n" が 0 個または 1 個続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-169">Match an "a" followed by zero or one "n" character.</span></span>|  
|`\b`|<span data-ttu-id="97d9d-170">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-170">End at a word boundary.</span></span>|  
  
### <a name="match-exactly-n-times-n"></a><span data-ttu-id="97d9d-171">n 回の繰り返しに一致: {n}</span><span class="sxs-lookup"><span data-stu-id="97d9d-171">Match Exactly n Times: {n}</span></span>  
 <span data-ttu-id="97d9d-172">`{`*n*`}` 量指定子は、直前の要素の *n* 回の繰り返しに一致します。ここで、*n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-172">The `{`*n*`}` quantifier matches the preceding element exactly *n* times, where *n* is any integer.</span></span> <span data-ttu-id="97d9d-173">`{`*n*`}` は最長一致の量指定子であり、最短一致でこれに対応するのは `{`*n*`}?` です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-173">`{`*n*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`}?`.</span></span>  
  
 <span data-ttu-id="97d9d-174">たとえば、正規表現 `\b\d+\,\d{3}\b` は、ワード境界、1 個以上の 10 進数、3 個の 10 進数、ワード境界の順に続く文字に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-174">For example, the regular expression `\b\d+\,\d{3}\b` tries to match a word boundary followed by one or more decimal digits followed by three decimal digits followed by a word boundary.</span></span> <span data-ttu-id="97d9d-175">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-175">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#4](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#4)]
 [!code-vb[RegularExpressions.Quantifiers#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#4)]  
  
 <span data-ttu-id="97d9d-176">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-176">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-177">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-177">Pattern</span></span>|<span data-ttu-id="97d9d-178">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-178">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-179">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-179">Start at a word boundary.</span></span>|  
|`\d+`|<span data-ttu-id="97d9d-180">1 個以上の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-180">Match one or more decimal digits.</span></span>|  
|`\,`|<span data-ttu-id="97d9d-181">コンマ文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-181">Match a comma character.</span></span>|  
|`\d{3}`|<span data-ttu-id="97d9d-182">3 個の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-182">Match three decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="97d9d-183">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-183">End at a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-n"></a><span data-ttu-id="97d9d-184">n 回以上の繰り返しに一致: {n,}</span><span class="sxs-lookup"><span data-stu-id="97d9d-184">Match at Least n Times: {n,}</span></span>  
 <span data-ttu-id="97d9d-185">`{`*n*`,}` 量指定子は、直前の要素の *n* 回以上の繰り返しに一致します。ここで、*n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-185">The `{`*n*`,}` quantifier matches the preceding element at least *n* times, where *n* is any integer.</span></span> <span data-ttu-id="97d9d-186">`{`*n*`,}` は最長一致の量指定子であり、最短一致でこれに対応するのは `{`*n*`,}?` です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-186">`{`*n*`,}` is a greedy quantifier whose lazy equivalent is `{`*n*`,}?`.</span></span>  
  
 <span data-ttu-id="97d9d-187">たとえば、正規表現 `\b\d{2,}\b\D+` は、ワード境界、2 個以上の 10 進数、ワード境界、数字以外の文字の順に続く文字に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-187">For example, the regular expression `\b\d{2,}\b\D+` tries to match a word boundary followed by at least two digits followed by a word boundary and a non-digit character.</span></span> <span data-ttu-id="97d9d-188">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-188">The following example illustrates this regular expression.</span></span> <span data-ttu-id="97d9d-189">この正規表現は `"7 days"` という語句には一致しません。これは、10 進数が 1 個しか含まれていないためです。しかし、`"10 weeks and 300 years"` という語句には正常に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-189">The regular expression fails to match the phrase `"7 days"` because it contains just one decimal digit, but it successfully matches the phrases `"10 weeks and 300 years"`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#5)]
 [!code-vb[RegularExpressions.Quantifiers#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#5)]  
  
 <span data-ttu-id="97d9d-190">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-190">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-191">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-191">Pattern</span></span>|<span data-ttu-id="97d9d-192">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-192">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-193">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-193">Start at a word boundary.</span></span>|  
|`\d{2,}`|<span data-ttu-id="97d9d-194">2 個以上の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-194">Match at least two decimal digits.</span></span>|  
|`\b`|<span data-ttu-id="97d9d-195">ワード境界に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-195">Match a word boundary.</span></span>|  
|`\D+`|<span data-ttu-id="97d9d-196">1 個以上の 10 進数以外の数字と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-196">Match at least one non-decimal digit.</span></span>|  
  
### <a name="match-between-n-and-m-times-nm"></a><span data-ttu-id="97d9d-197">n 回から m 回までの繰り返しに一致: {n,m}</span><span class="sxs-lookup"><span data-stu-id="97d9d-197">Match Between n and m Times: {n,m}</span></span>  
 <span data-ttu-id="97d9d-198">`{`*n*`,`*m*`}` 量指定子は、直前の要素の *n* 回以上、*m* 回以下の繰り返しに一致します。ここで、*n* と *m* は整数です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-198">The `{`*n*`,`*m*`}` quantifier matches the preceding element at least *n* times, but no more than *m* times, where *n* and *m* are integers.</span></span> <span data-ttu-id="97d9d-199">`{`*n*`,`*m*`}` は最長一致の量指定子であり、最短一致でこれに対応するのは `{`*n*`,`*m*`}?` です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-199">`{`*n*`,`*m*`}` is a greedy quantifier whose lazy equivalent is `{`*n*`,`*m*`}?`.</span></span>  
  
 <span data-ttu-id="97d9d-200">次の例では、正規表現 `(00\s){2,4}` は、2 個の 0 と 1 個のスペースが、2 回以上 4 回以下だけ現れる文字列に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-200">In the following example, the regular expression `(00\s){2,4}` tries to match between two and four occurrences of two zero digits followed by a space.</span></span> <span data-ttu-id="97d9d-201">入力文字列の最後の部分には、このパターンが最大の 4 回ではなく 5 回含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="97d9d-201">Note that the final portion of the input string includes this pattern five times rather than the maximum of four.</span></span> <span data-ttu-id="97d9d-202">この部分文字列の最初の部分 (スペースと 5 つ目の 0 のペアまで) だけが正規表現パターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-202">However, only the initial portion of this substring (up to the space and the fifth pair of zeros) matches the regular expression pattern.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#6)]
 [!code-vb[RegularExpressions.Quantifiers#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#6)]  
  
### <a name="match-zero-or-more-times-lazy-match-"></a><span data-ttu-id="97d9d-203">0 回以上の繰り返しに一致 (最短一致): \*?</span><span class="sxs-lookup"><span data-stu-id="97d9d-203">Match Zero or More Times (Lazy Match): \*?</span></span>  
 <span data-ttu-id="97d9d-204">`*?` 量指定子は、直前の要素の 0 回以上の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-204">The `*?` quantifier matches the preceding element zero or more times, but as few times as possible.</span></span> <span data-ttu-id="97d9d-205">これは、最長一致の量指定子 `*` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-205">It is the lazy counterpart of the greedy quantifier `*`.</span></span>  
  
 <span data-ttu-id="97d9d-206">次の例では、正規表現 `\b\w*?oo\w*?\b` は、文字列 `oo` を含むすべての単語に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-206">In the following example, the regular expression `\b\w*?oo\w*?\b` matches all words that contain the string `oo`.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#7](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#7)]
 [!code-vb[RegularExpressions.Quantifiers#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#7)]  
  
 <span data-ttu-id="97d9d-207">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-207">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-208">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-208">Pattern</span></span>|<span data-ttu-id="97d9d-209">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-209">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-210">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-210">Start at a word boundary.</span></span>|  
|`\w*?`|<span data-ttu-id="97d9d-211">単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-211">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`oo`|<span data-ttu-id="97d9d-212">文字列 "oo" と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-212">Match the string "oo".</span></span>|  
|`\w*?`|<span data-ttu-id="97d9d-213">単語に含まれる 0 個以上の文字のうち、最も少ない文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-213">Match zero or more word characters, but as few characters as possible.</span></span>|  
|`\b`|<span data-ttu-id="97d9d-214">ワード境界で終了します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-214">End on a word boundary.</span></span>|  
  
### <a name="match-one-or-more-times-lazy-match-"></a><span data-ttu-id="97d9d-215">1 回以上の繰り返しに一致 (最短一致): +?</span><span class="sxs-lookup"><span data-stu-id="97d9d-215">Match One or More Times (Lazy Match): +?</span></span>  
 <span data-ttu-id="97d9d-216">`+?` 量指定子は、直前の要素の 1 回以上の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-216">The `+?` quantifier matches the preceding element one or more times, but as few times as possible.</span></span> <span data-ttu-id="97d9d-217">これは、最長一致の量指定子 `+` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-217">It is the lazy counterpart of the greedy quantifier `+`.</span></span>  
  
 <span data-ttu-id="97d9d-218">たとえば、正規表現 `\b\w+?\b` は、ワード境界で区切られた 1 つ以上の文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-218">For example, the regular expression `\b\w+?\b` matches one or more characters separated by word boundaries.</span></span> <span data-ttu-id="97d9d-219">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-219">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#8)]
 [!code-vb[RegularExpressions.Quantifiers#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#8)]  
  
### <a name="match-zero-or-one-time-lazy-match-"></a><span data-ttu-id="97d9d-220">0 回または 1 回の繰り返しに一致 (最短一致): ??</span><span class="sxs-lookup"><span data-stu-id="97d9d-220">Match Zero or One Time (Lazy Match): ??</span></span>  
 <span data-ttu-id="97d9d-221">`??` 量指定子は、直前の要素の 0 回または 1 回の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-221">The `??` quantifier matches the preceding element zero or one time, but as few times as possible.</span></span> <span data-ttu-id="97d9d-222">これは、最長一致の量指定子 `?` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-222">It is the lazy counterpart of the greedy quantifier `?`.</span></span>  
  
 <span data-ttu-id="97d9d-223">たとえば、正規表現 `^\s*(System.)??Console.Write(Line)??\(??` は、文字列 "Console.Write" または "Console.WriteLine" に一致を試みます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-223">For example, the regular expression `^\s*(System.)??Console.Write(Line)??\(??` attempts to match the strings "Console.Write" or "Console.WriteLine".</span></span> <span data-ttu-id="97d9d-224">文字列には、"Console" の前に</span><span class="sxs-lookup"><span data-stu-id="97d9d-224">The string can also include "System."</span></span> <span data-ttu-id="97d9d-225">"System." が含まれていてもよく、最後に左かっこがあってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="97d9d-225">before "Console", and it can be followed by an opening parenthesis.</span></span> <span data-ttu-id="97d9d-226">文字列は行の先頭にある必要がありますが、文字列の前に空白があってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="97d9d-226">The string must be at the beginning of a line, although it can be preceded by white space.</span></span> <span data-ttu-id="97d9d-227">次の例は、この正規表現を示しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-227">The following example illustrates this regular expression.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#9](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#9)]
 [!code-vb[RegularExpressions.Quantifiers#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#9)]  
  
 <span data-ttu-id="97d9d-228">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-228">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-229">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-229">Pattern</span></span>|<span data-ttu-id="97d9d-230">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-230">Description</span></span>|  
|-------------|-----------------|  
|`^`|<span data-ttu-id="97d9d-231">入力ストリームの先頭と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-231">Match the start of the input stream.</span></span>|  
|`\s*`|<span data-ttu-id="97d9d-232">0 個以上の空白文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-232">Match zero or more white-space characters.</span></span>|  
|`(System.)??`|<span data-ttu-id="97d9d-233">文字列 "System." の 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-233">Match zero or one occurrence of the string "System.".</span></span>|  
|`Console.Write`|<span data-ttu-id="97d9d-234">文字列 "Console.Write" と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-234">Match the string "Console.Write".</span></span>|  
|`(Line)??`|<span data-ttu-id="97d9d-235">文字列 "Line" の 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-235">Match zero or one occurrence of the string "Line".</span></span>|  
|`\(??`|<span data-ttu-id="97d9d-236">左かっこの 0 回または 1 回の繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-236">Match zero or one occurrence of the opening parenthesis.</span></span>|  
  
### <a name="match-exactly-n-times-lazy-match-n"></a><span data-ttu-id="97d9d-237">n 回の繰り返しに一致 (最短一致): {n}?</span><span class="sxs-lookup"><span data-stu-id="97d9d-237">Match Exactly n Times (Lazy Match): {n}?</span></span>  
 <span data-ttu-id="97d9d-238">`{`*n*`}?` 量指定子は、直前の要素の `n` 回の繰り返しに一致します。ここで、*n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-238">The `{`*n*`}?` quantifier matches the preceding element exactly `n` times, where *n* is any integer.</span></span> <span data-ttu-id="97d9d-239">これは、最長一致の量指定子 `{`*n*`}` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-239">It is the lazy counterpart of the greedy quantifier `{`*n*`}`.</span></span>  
  
 <span data-ttu-id="97d9d-240">次の例では、正規表現 `\b(\w{3,}?\.){2}?\w{3,}?\b` を使用して Web サイトのアドレスを識別します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-240">In the following example, the regular expression `\b(\w{3,}?\.){2}?\w{3,}?\b` is used to identify a Web site address.</span></span> <span data-ttu-id="97d9d-241">"www.microsoft.com" と "msdn.microsoft.com" には一致しますが、"mywebsite" や "mycompany.com" には一致しない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="97d9d-241">Note that it matches "www.microsoft.com" and "msdn.microsoft.com", but does not match "mywebsite" or "mycompany.com".</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#10](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#10)]
 [!code-vb[RegularExpressions.Quantifiers#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#10)]  
  
 <span data-ttu-id="97d9d-242">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-242">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-243">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-243">Pattern</span></span>|<span data-ttu-id="97d9d-244">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-244">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-245">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-245">Start at a word boundary.</span></span>|  
|`(\w{3,}?\.)`|<span data-ttu-id="97d9d-246">単語に含まれる 3 個以上の文字のうち、最も少ない文字の後に、ドット (ピリオド) 文字が続くパターンに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-246">Match at least 3 word characters, but as few characters as possible, followed by a dot or period character.</span></span> <span data-ttu-id="97d9d-247">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="97d9d-247">This is the first capturing group.</span></span>|  
|`(\w{3,}?\.){2}?`|<span data-ttu-id="97d9d-248">最初のグループのパターンの 2 回の繰り返しのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-248">Match the pattern in the first group two times, but as few times as possible.</span></span>|  
|`\b`|<span data-ttu-id="97d9d-249">ワード境界で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-249">End the match on a word boundary.</span></span>|  
  
### <a name="match-at-least-n-times-lazy-match-n"></a><span data-ttu-id="97d9d-250">n 回以上の繰り返しに一致 (最短一致): {n,}?</span><span class="sxs-lookup"><span data-stu-id="97d9d-250">Match at Least n Times (Lazy Match): {n,}?</span></span>  
 <span data-ttu-id="97d9d-251">`{`*n*`,}?` 量指定子は、直前の要素の `n` 回以上の繰り返しのうち、最も少ない繰り返しに一致します。ここで、*n* は任意の整数です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-251">The `{`*n*`,}?` quantifier matches the preceding element at least `n` times, where *n* is any integer, but as few times as possible.</span></span> <span data-ttu-id="97d9d-252">これは、最長一致の量指定子 `{`*n*`,}` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-252">It is the lazy counterpart of the greedy quantifier `{`*n*`,}`.</span></span>  
  
 <span data-ttu-id="97d9d-253">`{`*n*`}?` 量指定子の例については、前のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="97d9d-253">See the example for the `{`*n*`}?` quantifier in the previous section for an illustration.</span></span> <span data-ttu-id="97d9d-254">この例の正規表現は、3 文字以上の後にピリオドが続く文字列に一致させるために `{`*n*`,}` 量指定子を使用しています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-254">The regular expression in that example uses the `{`*n*`,}` quantifier to match a string that has at least three characters followed by a period.</span></span>  
  
### <a name="match-between-n-and-m-times-lazy-match-nm"></a><span data-ttu-id="97d9d-255">n 回から m 回までの繰り返しに一致 (最短一致): {n,m}?</span><span class="sxs-lookup"><span data-stu-id="97d9d-255">Match Between n and m Times (Lazy Match): {n,m}?</span></span>  
 <span data-ttu-id="97d9d-256">`{`*n*`,`*m*`}?` 量指定子は、直前の要素の `n` 回から `m` 回までの繰り返しのうち、最も少ない繰り返しに一致します。ここで、*n* と *m* は整数です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-256">The `{`*n*`,`*m*`}?` quantifier matches the preceding element between `n` and `m` times, where *n* and *m* are integers, but as few times as possible.</span></span> <span data-ttu-id="97d9d-257">これは、最長一致の量指定子 `{`*n*`,`*m*`}` に対応する、最短一致の量指定子です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-257">It is the lazy counterpart of the greedy quantifier `{`*n*`,`*m*`}`.</span></span>  
  
 <span data-ttu-id="97d9d-258">次の例では、正規表現 `\b[A-Z](\w*?\s*?){1,10}[.!?]` は、1 個以上 10 個以下の単語が含まれる文に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-258">In the following example, the regular expression `\b[A-Z](\w*?\s*?){1,10}[.!?]` matches sentences that contain between one and ten words.</span></span> <span data-ttu-id="97d9d-259">18 個の単語が含まれている 1 つの文を除き、入力文字列中のすべての文に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-259">It matches all the sentences in the input string except for one sentence that contains 18 words.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers#12](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers/cs/Quantifiers1.cs#12)]
 [!code-vb[RegularExpressions.Quantifiers#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers/vb/Quantifiers1.vb#12)]  
  
 <span data-ttu-id="97d9d-260">正規表現パターンは、次の表に示すように定義されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-260">The regular expression pattern is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-261">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-261">Pattern</span></span>|<span data-ttu-id="97d9d-262">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-262">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="97d9d-263">ワード境界から開始します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-263">Start at a word boundary.</span></span>|  
|`[A-Z]`|<span data-ttu-id="97d9d-264">A から Z の大文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-264">Match an uppercase character from A to Z.</span></span>|  
|`(\w*?\s*?)`|<span data-ttu-id="97d9d-265">0 個以上の単語文字の後に 1 個以上の空白文字続くパターンのうち、最も少ない繰り返しに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-265">Match zero or more word characters, followed by one or more white-space characters, but as few times as possible.</span></span> <span data-ttu-id="97d9d-266">これが最初のキャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="97d9d-266">This is the first capture group.</span></span>|  
|`{1,10}`|<span data-ttu-id="97d9d-267">前のパターンの 1 回以上 10 回以下に一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-267">Match the previous pattern between 1 and 10 times.</span></span>|  
|`[.!?]`|<span data-ttu-id="97d9d-268">区切り文字 "."、"!"、"?" のいずれか 1 文字と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-268">Match any one of the punctuation characters ".", "!", or "?".</span></span>|  
  
<a name="Greedy"></a>
## <a name="greedy-and-lazy-quantifiers"></a><span data-ttu-id="97d9d-269">最長一致と最短一致の量指定子</span><span class="sxs-lookup"><span data-stu-id="97d9d-269">Greedy and Lazy Quantifiers</span></span>  
 <span data-ttu-id="97d9d-270">いくつかの量指定子には次の 2 つのバージョンがあります。</span><span class="sxs-lookup"><span data-stu-id="97d9d-270">A number of the quantifiers have two versions:</span></span>  
  
- <span data-ttu-id="97d9d-271">最長一致バージョン。</span><span class="sxs-lookup"><span data-stu-id="97d9d-271">A greedy version.</span></span>  
  
     <span data-ttu-id="97d9d-272">最長一致の量指定子は、要素をできるだけ多く一致させようとします。</span><span class="sxs-lookup"><span data-stu-id="97d9d-272">A greedy quantifier tries to match an element as many times as possible.</span></span>  
  
- <span data-ttu-id="97d9d-273">最短一致バージョン。</span><span class="sxs-lookup"><span data-stu-id="97d9d-273">A non-greedy (or lazy) version.</span></span>  
  
     <span data-ttu-id="97d9d-274">最短一致の量指定子は、要素をできるだけ少なく一致させようとします。</span><span class="sxs-lookup"><span data-stu-id="97d9d-274">A non-greedy quantifier tries to match an element as few times as possible.</span></span> <span data-ttu-id="97d9d-275">最長一致の量指定子に `?` を追加するだけで最短一致の量指定子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-275">You can turn a greedy quantifier into a lazy quantifier by simply adding a `?`.</span></span>  
  
 <span data-ttu-id="97d9d-276">クレジット カード番号などの数値の列から最後の 4 桁の数字を取り出す、単純な正規表現について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-276">Consider a simple regular expression that is intended to extract the last four digits from a string of numbers such as a credit card number.</span></span> <span data-ttu-id="97d9d-277">最長一致の `*` 量指定子を使用するバージョンの正規表現は、`\b.*([0-9]{4})\b` です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-277">The version of the regular expression that uses the `*` greedy quantifier is `\b.*([0-9]{4})\b`.</span></span> <span data-ttu-id="97d9d-278">しかし、2 個の数値が含まれている文字列の場合、この正規表現は、次の例に示すように 2 番目の数値の最後の 4 桁の数字だけに一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-278">However, if a string contains two numbers, this regular expression matches the last four digits of the second number only, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#1)]  
  
 <span data-ttu-id="97d9d-279">この正規表現は最初の数値の一致に失敗します。`*` 量指定子では、直前の要素をできるだけ多く繰り返して文字列全体に一致させようとして、文字列の最後まで一致と見なされるためです。</span><span class="sxs-lookup"><span data-stu-id="97d9d-279">The regular expression fails to match the first number because the `*` quantifier tries to match the previous element as many times as possible in the entire string, and so it finds its match at the end of the string.</span></span>  
  
 <span data-ttu-id="97d9d-280">これは期待した動作ではありません。</span><span class="sxs-lookup"><span data-stu-id="97d9d-280">This is not the desired behavior.</span></span> <span data-ttu-id="97d9d-281">代わりに `*?` 最短一致の量指定子を使用すると、次の例のように両方の数値から数字を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-281">Instead, you can use the `*?`lazy quantifier to extract digits from both numbers, as the following example shows.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/cs/Greedy.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.Greedy#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Quantifiers.Greedy/vb/Greedy.vb#2)]  
  
 <span data-ttu-id="97d9d-282">多くの場合、最長一致と最短一致の量指定子を使用した正規表現は、同じ一致結果を返します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-282">In most cases, regular expressions with greedy and lazy quantifiers return the same matches.</span></span> <span data-ttu-id="97d9d-283">異なる結果を返すことが最も多いのは、任意の文字に一致するワイルドカード (`.`) のメタ文字を使用した場合です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-283">They most commonly return different results when they are used with the wildcard (`.`) metacharacter, which matches any character.</span></span>  
  
## <a name="quantifiers-and-empty-matches"></a><span data-ttu-id="97d9d-284">量指定子と空一致</span><span class="sxs-lookup"><span data-stu-id="97d9d-284">Quantifiers and Empty Matches</span></span>  
 <span data-ttu-id="97d9d-285">量指定子 `*`、`+`、および `{`*n*`,`*m*`}` と、これらに対応する最短一致の量指定子は、最小回数のキャプチャが見つかった場合、空一致の後には繰り返されません。</span><span class="sxs-lookup"><span data-stu-id="97d9d-285">The quantifiers `*`, `+`, and `{`*n*`,`*m*`}` and their lazy counterparts never repeat after an empty match when the minimum number of captures has been found.</span></span> <span data-ttu-id="97d9d-286">この規則により、可能なグループ キャプチャの最大回数が無限またはほぼ無限のときに、量指定子が空の部分式一致の無限ループに入ることを回避できます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-286">This rule prevents quantifiers from entering infinite loops on empty subexpression matches when the maximum number of possible group captures is infinite or near infinite.</span></span>  
  
 <span data-ttu-id="97d9d-287">たとえば、次のコードは、0 個または 1 個の文字 "a" と 0 回以上一致する正規表現パターン `(a?)*` を指定して <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> メソッドを呼び出した結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-287">For example, the following code shows the result of a call to the <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> method with the regular expression pattern `(a?)*`, which matches zero or one "a" character zero or more times.</span></span> <span data-ttu-id="97d9d-288">単一のキャプチャ グループによって各 "a" と <xref:System.String.Empty?displayProperty=nameWithType> がキャプチャされますが、2 番目の空一致はないことに注意してください。これは、最初の空一致により量指定子が繰り返しを停止するためです。</span><span class="sxs-lookup"><span data-stu-id="97d9d-288">Note that the single capturing group captures each "a" as well as <xref:System.String.Empty?displayProperty=nameWithType>, but that there is no second empty match, because the first empty match causes the quantifier to stop repeating.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch1.cs#1)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch1.vb#1)]  
  
 <span data-ttu-id="97d9d-289">最小回数と最大回数のキャプチャを定義するキャプチャ グループと固定回数のキャプチャを定義するキャプチャ グループとの間の実際の違いを確認するために、正規表現パターンの `(a\1|(?(1)\1)){0,2}` と `(a\1|(?(1)\1)){2}` について検討します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-289">To see the practical difference between a capturing group that defines a minimum and a maximum number of captures and one that defines a fixed number of captures, consider the regular expression patterns `(a\1|(?(1)\1)){0,2}` and `(a\1|(?(1)\1)){2}`.</span></span> <span data-ttu-id="97d9d-290">どちらの正規表現も、次の表に示すように定義される単一のキャプチャ グループで構成されています。</span><span class="sxs-lookup"><span data-stu-id="97d9d-290">Both regular expressions consist of a single capturing group, which is defined as shown in the following table.</span></span>  
  
|<span data-ttu-id="97d9d-291">パターン</span><span class="sxs-lookup"><span data-stu-id="97d9d-291">Pattern</span></span>|<span data-ttu-id="97d9d-292">説明</span><span class="sxs-lookup"><span data-stu-id="97d9d-292">Description</span></span>|  
|-------------|-----------------|  
|`(a\1`|<span data-ttu-id="97d9d-293">"a" と最初のキャプチャ グループの値に一致します …</span><span class="sxs-lookup"><span data-stu-id="97d9d-293">Either match "a" along with the value of the first captured group …</span></span>|  
|<code>&#124;(?(1)</code>|<span data-ttu-id="97d9d-294">…</span><span class="sxs-lookup"><span data-stu-id="97d9d-294">…</span></span> <span data-ttu-id="97d9d-295">または、最初のキャプチャ グループが定義されているかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="97d9d-295">or test whether the first captured group has been defined.</span></span> <span data-ttu-id="97d9d-296">(`(?(1)` コンストラクトではキャプチャ グループは定義されないことに注意してください。)</span><span class="sxs-lookup"><span data-stu-id="97d9d-296">(Note that the `(?(1)` construct does not define a capturing group.)</span></span>|  
|`\1))`|<span data-ttu-id="97d9d-297">最初のキャプチャ グループが存在する場合、その値と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-297">If the first captured group exists, match its value.</span></span> <span data-ttu-id="97d9d-298">グループが存在しない場合、そのグループは <xref:System.String.Empty?displayProperty=nameWithType> と一致します。</span><span class="sxs-lookup"><span data-stu-id="97d9d-298">If the group does not exist, the group will match <xref:System.String.Empty?displayProperty=nameWithType>.</span></span>|  
  
 <span data-ttu-id="97d9d-299">最初の正規表現では 0 ～ 2 回、このパターンとの照合が行われます。2 番目の正規表現では、厳密に 2 回です。</span><span class="sxs-lookup"><span data-stu-id="97d9d-299">The first regular expression tries to match this pattern between zero and two times; the second, exactly two times.</span></span> <span data-ttu-id="97d9d-300">最初のパターンは <xref:System.String.Empty?displayProperty=nameWithType> の最初のキャプチャでキャプチャの最小回数に達するため、`a\1` との照合は繰り返されません。`{0,2}` 量指定子では、最後の繰り返しでの空一致だけが許可されます。</span><span class="sxs-lookup"><span data-stu-id="97d9d-300">Because the first pattern reaches its minimum number of captures with its first capture of <xref:System.String.Empty?displayProperty=nameWithType>, it never repeats to try to match `a\1`; the `{0,2}` quantifier allows only empty matches in the last iteration.</span></span> <span data-ttu-id="97d9d-301">一方、2 番目の正規表現では、2 回目の `a\1` が評価されるため、"a" に一致します。繰り返しの最小回数は 2 で、空一致の後でエンジンが繰り返さなければならない回数になります。</span><span class="sxs-lookup"><span data-stu-id="97d9d-301">In contrast, the second regular expression does match "a" because it evaluates `a\1` a second time; the minimum number of iterations, 2, forces the engine to repeat after an empty match.</span></span>  
  
 [!code-csharp[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/csharp/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/cs/emptymatch4.cs#2)]
 [!code-vb[RegularExpressions.Quantifiers.EmptyMatch#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/regularexpressions.quantifiers.emptymatch/vb/emptymatch4.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="97d9d-302">関連項目</span><span class="sxs-lookup"><span data-stu-id="97d9d-302">See also</span></span>

- [<span data-ttu-id="97d9d-303">正規表現言語 - クイック リファレンス</span><span class="sxs-lookup"><span data-stu-id="97d9d-303">Regular Expression Language - Quick Reference</span></span>](regular-expression-language-quick-reference.md)
- [<span data-ttu-id="97d9d-304">バックトラッキング</span><span class="sxs-lookup"><span data-stu-id="97d9d-304">Backtracking</span></span>](backtracking-in-regular-expressions.md)
