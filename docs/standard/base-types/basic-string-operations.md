---
title: .NET の基本的な文字列操作
description: 文字列で実行できる基本的な操作について説明します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- strings [.NET Framework], basic string operations
- custom strings
ms.assetid: 8133d357-90b5-4b62-9927-43323d99b6b6
ms.custom: seadec18
ms.openlocfilehash: 05cdf399e104fc9e528c954adb19634a5c136664
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132909"
---
# <a name="basic-string-operations-in-net"></a><span data-ttu-id="617c0-103">.NET の基本的な文字列操作</span><span class="sxs-lookup"><span data-stu-id="617c0-103">Basic String Operations in .NET</span></span>
<span data-ttu-id="617c0-104">アプリケーションは、多くの場合、ユーザー入力に基づいてメッセージを構築することによってユーザーに応答します。</span><span class="sxs-lookup"><span data-stu-id="617c0-104">Applications often respond to users by constructing messages based on user input.</span></span> <span data-ttu-id="617c0-105">たとえば、Web サイトで、新たにログオンしたユーザーに対して、ユーザーの名前を含む特別なメッセージで応答することは珍しいことではありません。</span><span class="sxs-lookup"><span data-stu-id="617c0-105">For example, it is not uncommon for Web sites to respond to a newly logged-on user with a specialized greeting that includes the user's name.</span></span> <span data-ttu-id="617c0-106"><xref:System.String?displayProperty=nameWithType> クラスと <xref:System.Text.StringBuilder?displayProperty=nameWithType> クラスのいくつかのメソッドを使用すると、ユーザー インターフェイスに表示するカスタム文字列を動的に構築できます。</span><span class="sxs-lookup"><span data-stu-id="617c0-106">Several methods in the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes allow you to dynamically construct custom strings to display in your user interface.</span></span> <span data-ttu-id="617c0-107">これらのメソッドでは、バイト配列から新しい文字列を作成する、文字列の値を比較する、既存の文字列を変更するなどのいくつかの基本的な文字列操作を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="617c0-107">These methods also help you perform a number of basic string operations like creating new strings from arrays of bytes, comparing the values of strings, and modifying existing strings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="617c0-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="617c0-108">In This Section</span></span>  
 [<span data-ttu-id="617c0-109">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="617c0-109">Creating New Strings</span></span>](../../../docs/standard/base-types/creating-new.md)  
 <span data-ttu-id="617c0-110">オブジェクトを文字列に変換し、文字列を結合する基本的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-110">Describes basic ways to convert objects into strings and to combine strings.</span></span>  
  
 [<span data-ttu-id="617c0-111">文字のトリムと削除</span><span class="sxs-lookup"><span data-stu-id="617c0-111">Trimming and Removing Characters</span></span>](../../../docs/standard/base-types/trimming.md)  
 <span data-ttu-id="617c0-112">文字列内の文字をトリミングまたは削除する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-112">Describes how to trim or remove characters in a string.</span></span>  
  
 [<span data-ttu-id="617c0-113">文字列の埋め込み</span><span class="sxs-lookup"><span data-stu-id="617c0-113">Padding Strings</span></span>](../../../docs/standard/base-types/padding.md)  
 <span data-ttu-id="617c0-114">文字列に文字または空白を挿入する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-114">Describes how to insert characters or empty spaces into a string.</span></span>  
  
 [<span data-ttu-id="617c0-115">文字列の比較</span><span class="sxs-lookup"><span data-stu-id="617c0-115">Comparing Strings</span></span>](../../../docs/standard/base-types/comparing.md)  
 <span data-ttu-id="617c0-116">2 つ以上の文字列の内容を比較する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-116">Describes how to compare the contents of two or more strings.</span></span>  
  
 [<span data-ttu-id="617c0-117">大文字と小文字の変更</span><span class="sxs-lookup"><span data-stu-id="617c0-117">Changing Case</span></span>](../../../docs/standard/base-types/changing-case.md)  
 <span data-ttu-id="617c0-118">文字列内の文字の大文字と小文字を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-118">Describes how to change the case of characters within a string.</span></span>  
  
 [<span data-ttu-id="617c0-119">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="617c0-119">Using the StringBuilder Class</span></span>](../../../docs/standard/base-types/stringbuilder.md)  
 <span data-ttu-id="617c0-120"><xref:System.Text.StringBuilder> クラスの動的な文字列オブジェクトを作成および変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-120">Describes how to create and modify dynamic string objects with the <xref:System.Text.StringBuilder> class.</span></span>  
  
 [<span data-ttu-id="617c0-121">方法: 基本的な文字列操作を実行する</span><span class="sxs-lookup"><span data-stu-id="617c0-121">How to: Perform Basic String Manipulations</span></span>](../../../docs/standard/base-types/basic-manipulations.md)  
 <span data-ttu-id="617c0-122">基本的な文字列操作の使用を示します。</span><span class="sxs-lookup"><span data-stu-id="617c0-122">Demonstrates the use of basic string operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="617c0-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="617c0-123">Related Sections</span></span>  
 [<span data-ttu-id="617c0-124">.NET での型変換</span><span class="sxs-lookup"><span data-stu-id="617c0-124">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="617c0-125">型を変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-125">Describes how to convert one type into another type.</span></span>  
  
 [<span data-ttu-id="617c0-126">型の書式設定</span><span class="sxs-lookup"><span data-stu-id="617c0-126">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="617c0-127">書式指定子を使用して文字列の書式を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="617c0-127">Describes how to format strings using format specifiers.</span></span>
