---
title: '正規表現の例: 日付形式の変更'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: 5fcc75a5-09d7-45ae-a4c0-9ad6085ac83d
ms.openlocfilehash: 4290bf0d6ee9deec8129c5f4f6092eedb08345f0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276180"
---
# <a name="regular-expression-example-changing-date-formats"></a><span data-ttu-id="fc4d4-102">正規表現の例: 日付形式の変更</span><span class="sxs-lookup"><span data-stu-id="fc4d4-102">Regular Expression Example: Changing Date Formats</span></span>
<span data-ttu-id="fc4d4-103">次のコード例では、<xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> メソッドを使用して、*mm*/*dd*/*yy* 形式の日付を *dd*-*mm*-*yy* 形式の日付に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-103">The following code example uses the <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to replace dates that have the form *mm*/*dd*/*yy* with dates that have the form *dd*-*mm*-*yy*.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc4d4-104">例</span><span class="sxs-lookup"><span data-stu-id="fc4d4-104">Example</span></span>  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#1)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#1)]  
  
 <span data-ttu-id="fc4d4-105">次のコードは、アプリケーションで `MDYToDMY` メソッドを呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-105">The following code shows how the `MDYToDMY` method can be called in an application.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/cs/Example_ChangeDateFormats1.cs#2)]
 [!code-vb[RegularExpressions.Examples.ChangeDateFormats#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.ChangeDateFormats/vb/Example_ChangeDateFormats1.vb#2)]  
  
## <a name="comments"></a><span data-ttu-id="fc4d4-106">コメント</span><span class="sxs-lookup"><span data-stu-id="fc4d4-106">Comments</span></span>  
 <span data-ttu-id="fc4d4-107">この正規表現パターン `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` の解釈を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-107">The regular expression pattern  `\b(?<month>\d{1,2})/(?<day>\d{1,2})/(?<year>\d{2,4})\b` is interpreted as shown in the following table.</span></span>  
  
|<span data-ttu-id="fc4d4-108">パターン</span><span class="sxs-lookup"><span data-stu-id="fc4d4-108">Pattern</span></span>|<span data-ttu-id="fc4d4-109">[説明]</span><span class="sxs-lookup"><span data-stu-id="fc4d4-109">Description</span></span>|  
|-------------|-----------------|  
|`\b`|<span data-ttu-id="fc4d4-110">ワード境界から照合を開始します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-110">Begin the match at a word boundary.</span></span>|  
|`(?<month>\d{1,2})`|<span data-ttu-id="fc4d4-111">1 桁または 2 桁の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-111">Match one or two decimal digits.</span></span> <span data-ttu-id="fc4d4-112">これは、`month` キャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-112">This is the `month` captured group.</span></span>|  
|`/`|<span data-ttu-id="fc4d4-113">スラッシュ マークと一致します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-113">Match the slash mark.</span></span>|  
|`(?<day>\d{1,2})`|<span data-ttu-id="fc4d4-114">1 桁または 2 桁の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-114">Match one or two decimal digits.</span></span> <span data-ttu-id="fc4d4-115">これは、`day` キャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-115">This is the `day` captured group.</span></span>|  
|`/`|<span data-ttu-id="fc4d4-116">スラッシュ マークと一致します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-116">Match the slash mark.</span></span>|  
|`(?<year>\d{2,4})`|<span data-ttu-id="fc4d4-117">2 ～ 4 の 10 進数と一致します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-117">Match from two to four decimal digits.</span></span> <span data-ttu-id="fc4d4-118">これは、`year` キャプチャ グループです。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-118">This is the `year` captured group.</span></span>|  
|`\b`|<span data-ttu-id="fc4d4-119">ワード境界で照合を終了します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-119">End the match at a word boundary.</span></span>|  
  
 <span data-ttu-id="fc4d4-120">パターン `${day}-${month}-${year}` は、次の表に示すように置換文字列を定義します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-120">The pattern `${day}-${month}-${year}` defines the replacement string as shown in the following table.</span></span>  
  
|<span data-ttu-id="fc4d4-121">パターン</span><span class="sxs-lookup"><span data-stu-id="fc4d4-121">Pattern</span></span>|<span data-ttu-id="fc4d4-122">[説明]</span><span class="sxs-lookup"><span data-stu-id="fc4d4-122">Description</span></span>|  
|-------------|-----------------|  
|`$(day)`|<span data-ttu-id="fc4d4-123">`day` キャプチャ グループによってキャプチャされた文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-123">Add the string captured by the `day` capturing group.</span></span>|  
|`-`|<span data-ttu-id="fc4d4-124">ハイフンを追加します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-124">Add a hyphen.</span></span>|  
|`$(month)`|<span data-ttu-id="fc4d4-125">`month` キャプチャ グループによってキャプチャされた文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-125">Add the string captured by the `month` capturing group.</span></span>|  
|`-`|<span data-ttu-id="fc4d4-126">ハイフンを追加します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-126">Add a hyphen.</span></span>|  
|`$(year)`|<span data-ttu-id="fc4d4-127">`year` キャプチャ グループによってキャプチャされた文字列を追加します。</span><span class="sxs-lookup"><span data-stu-id="fc4d4-127">Add the string captured by the `year` capturing group.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc4d4-128">参照</span><span class="sxs-lookup"><span data-stu-id="fc4d4-128">See also</span></span>

- [<span data-ttu-id="fc4d4-129">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="fc4d4-129">.NET Regular Expressions</span></span>](regular-expressions.md)
