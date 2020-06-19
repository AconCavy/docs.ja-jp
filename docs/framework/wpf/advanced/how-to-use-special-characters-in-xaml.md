---
title: '方法: XAML で特殊文字を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- Unicode UTF-8 file format
- UTF-8 file format
- characters [WPF], special
- typography [WPF], special characters
- special characters [WPF]
ms.assetid: a57776d1-f353-4794-afa0-bfa3c712ed1c
ms.openlocfilehash: 59449637bb45f6b75462b6809c354af7972fc2e7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740834"
---
# <a name="how-to-use-special-characters-in-xaml"></a><span data-ttu-id="fda9f-102">方法: XAML で特殊文字を使用する</span><span class="sxs-lookup"><span data-stu-id="fda9f-102">How to: Use Special Characters in XAML</span></span>
<span data-ttu-id="fda9f-103">マークアップ ファイルを Visual Studio で作成すると、自動的に Unicode UTF-8 ファイル形式で保存されます。つまり、アクセント記号など、ほとんどの特殊文字が正しくエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="fda9f-103">Markup files that are created in Visual Studio are automatically saved in the Unicode UTF-8 file format, which means that most special characters, such as accent marks, are encoded correctly.</span></span> <span data-ttu-id="fda9f-104">ただし、一般的に使用される一連の特殊文字で、別の方法で処理されるものがあります。</span><span class="sxs-lookup"><span data-stu-id="fda9f-104">However, there is a set of commonly-used special characters that are handled differently.</span></span> <span data-ttu-id="fda9f-105">これらの特殊文字は、World Wide Web コンソーシアム (W3C) XML 標準に従ってエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="fda9f-105">These special characters follow the World Wide Web Consortium (W3C) XML standard for encoding.</span></span>  
  
 <span data-ttu-id="fda9f-106">この一連の特殊文字をエンコードするための構文を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="fda9f-106">The following table shows the syntax for encoding this set of special characters:</span></span>  
  
|<span data-ttu-id="fda9f-107">文字</span><span class="sxs-lookup"><span data-stu-id="fda9f-107">Character</span></span>|<span data-ttu-id="fda9f-108">構文</span><span class="sxs-lookup"><span data-stu-id="fda9f-108">Syntax</span></span>|<span data-ttu-id="fda9f-109">説明</span><span class="sxs-lookup"><span data-stu-id="fda9f-109">Description</span></span>|  
|---------------|------------|-----------------|  
|<|`&lt;`|<span data-ttu-id="fda9f-110">より小さい記号</span><span class="sxs-lookup"><span data-stu-id="fda9f-110">Less than symbol.</span></span>|  
|>|`&gt;`|<span data-ttu-id="fda9f-111">より大きい記号</span><span class="sxs-lookup"><span data-stu-id="fda9f-111">Greater than sign.</span></span>|  
|&|`&amp;`|<span data-ttu-id="fda9f-112">アンパサンド記号</span><span class="sxs-lookup"><span data-stu-id="fda9f-112">Ampersand symbol.</span></span>|  
|<span data-ttu-id="fda9f-113">"</span><span class="sxs-lookup"><span data-stu-id="fda9f-113">"</span></span>|`&quot;`|<span data-ttu-id="fda9f-114">二重引用符記号</span><span class="sxs-lookup"><span data-stu-id="fda9f-114">Double quote symbol.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="fda9f-115">Windows メモ帳などのテキスト エディターを使用してマークアップ ファイルを作成する場合は、エンコードされた特殊文字を保持するために、ファイルを Unicode UTF-8 ファイル形式で保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fda9f-115">If you create a markup file using a text editor, such as Windows Notepad, you must save the file in the Unicode UTF-8 file format in order to preserve any encoded special characters.</span></span>  
  
 <span data-ttu-id="fda9f-116">次の例では、マークアップを作成するときにテキストで特殊文字を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fda9f-116">The following example shows how you can use special characters in text when creating markup.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fda9f-117">例</span><span class="sxs-lookup"><span data-stu-id="fda9f-117">Example</span></span>  
 [!code-xaml[SpecialCharsSnippets#SpecialCharsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/SpecialCharsSnippets/CS/Window1.xaml#specialcharssnippet1)]
