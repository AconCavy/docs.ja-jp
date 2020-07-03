---
title: '方法: 文字列から無効な文字を取り除く'
description: 静的 Regex.Replace メソッドを使用して、文字列から害を及ぼす可能性のある文字を取り除く方法を示す例について確認します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, examples
- cleaning input
- user input, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- Regex.Replace method
- stripping invalid characters
- Replace method
- validating user input
ms.assetid: b4319c8a-9032-4129-a9d5-6f6fc28e7f32
ms.openlocfilehash: f9d671587d174a1eb2bb6a5dac24bdd0220be3dd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600829"
---
# <a name="how-to-strip-invalid-characters-from-a-string"></a><span data-ttu-id="c6f4b-103">方法: 文字列から無効な文字を取り除く</span><span class="sxs-lookup"><span data-stu-id="c6f4b-103">How to: Strip Invalid Characters from a String</span></span>
<span data-ttu-id="c6f4b-104">次の例では、静的 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> メソッドを使用して、文字列から無効な文字を取り除いています。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-104">The following example uses the static <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> method to strip invalid characters from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6f4b-105">例</span><span class="sxs-lookup"><span data-stu-id="c6f4b-105">Example</span></span>  
 <span data-ttu-id="c6f4b-106">この例で定義されている `CleanInput` メソッドを使用して、ユーザー入力を受け付けるテキスト フィールドに入力された、問題を引き起こす可能性がある文字を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-106">You can use the `CleanInput` method defined in this example to strip potentially harmful characters that have been entered into a text field that accepts user input.</span></span> <span data-ttu-id="c6f4b-107">この場合、`CleanInput` は、ピリオド (.)、アット記号 (@)、ハイフン (-) を除く英数字以外のすべての文字を取り除き、残りの文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-107">In this case, `CleanInput` strips out all nonalphanumeric characters except periods (.), at symbols (@), and hyphens (-), and returns the remaining string.</span></span> <span data-ttu-id="c6f4b-108">ただし、正規表現パターンを変更して、入力文字列に含めない任意の文字を取り除くこともできます。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-108">However, you can modify the regular expression pattern so that it strips out any characters that should not be included in an input string.</span></span>  
  
 [!code-csharp[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.StripChars#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.StripChars/vb/Example.vb#1)]  
  
 <span data-ttu-id="c6f4b-109">正規表現パターン `[^\w\.@-]` は、単語に使用される文字、ピリオド、@ 記号、またはハイフンではないすべての文字に一致します。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-109">The regular expression pattern `[^\w\.@-]` matches any character that is not a word character, a period, an @ symbol, or a hyphen.</span></span> <span data-ttu-id="c6f4b-110">単語に使用される文字とは、すべての英字、数字、または区切りのコネクタ文字 (アンダースコアなど) です。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-110">A word character is any letter, decimal digit, or punctuation connector such as an underscore.</span></span> <span data-ttu-id="c6f4b-111">このパターンに一致するすべての文字は、置換パターンで定義されている <xref:System.String.Empty?displayProperty=nameWithType> で置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-111">Any character that matches this pattern is replaced by <xref:System.String.Empty?displayProperty=nameWithType>, which is the string defined by the replacement pattern.</span></span> <span data-ttu-id="c6f4b-112">ユーザー入力で他の文字も許可するには、正規表現パターンの文字クラスにその文字を追加します。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-112">To allow additional characters in user input, add those characters to the character class in the regular expression pattern.</span></span> <span data-ttu-id="c6f4b-113">たとえば、正規表現パターン `[^\w\.@-\\%]` は、入力文字列にパーセント記号とバックスラッシュも許可しています。</span><span class="sxs-lookup"><span data-stu-id="c6f4b-113">For example, the regular expression pattern `[^\w\.@-\\%]` also allows a percentage symbol and a backslash in an input string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6f4b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6f4b-114">See also</span></span>

- [<span data-ttu-id="c6f4b-115">.NET の正規表現</span><span class="sxs-lookup"><span data-stu-id="c6f4b-115">.NET Regular Expressions</span></span>](regular-expressions.md)
