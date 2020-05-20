---
title: カルチャを認識しない文字列操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
ms.openlocfilehash: 06c46033936e16355b8d2eb6650e8731a04af6e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141281"
---
# <a name="culture-insensitive-string-operations"></a><span data-ttu-id="2d836-102">カルチャを認識しない文字列操作</span><span class="sxs-lookup"><span data-stu-id="2d836-102">Culture-insensitive string operations</span></span>

<span data-ttu-id="2d836-103">カルチャを認識する文字列操作は、カルチャごとにユーザーに結果を表示するようデザインされたアプリケーションを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="2d836-103">Culture-sensitive string operations can be an advantage if you are creating applications designed to display results to users on a per-culture basis.</span></span> <span data-ttu-id="2d836-104">既定では、カルチャを認識するメソッドは、使用するカルチャを現在のスレッドの <xref:System.Globalization.CultureInfo.CurrentCulture%2A> プロパティから取得します。</span><span class="sxs-lookup"><span data-stu-id="2d836-104">By default, culture-sensitive methods obtain the culture to use from the <xref:System.Globalization.CultureInfo.CurrentCulture%2A> property for the current thread.</span></span>

<span data-ttu-id="2d836-105">ただし、カルチャを認識する文字列操作は、必ずしも望ましい動作ではありません。</span><span class="sxs-lookup"><span data-stu-id="2d836-105">Note that culture-sensitive string operations are not always the desired behavior.</span></span> <span data-ttu-id="2d836-106">結果をカルチャに依存させない場合に、カルチャを認識する操作を使用すると、カスタムの大文字と小文字の対応規則および並べ替え規則を使用するカルチャでのアプリケーション コードの実行が失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="2d836-106">Using culture-sensitive operations when results should be independent of culture can cause application code to fail on cultures with custom case mappings and sorting rules.</span></span> <span data-ttu-id="2d836-107">たとえば、「[.NET の文字列を使用するためのベスト プラクティス](../../../docs/standard/base-types/best-practices-strings.md)」の記事の「[現在のカルチャを使用する文字列比較](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d836-107">For an example, see the ["String Comparisons that Use the Current Culture"](../../../docs/standard/base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) section in the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article.</span></span>

<span data-ttu-id="2d836-108">文字列操作でカルチャに依存するかどうかは、アプリケーションで結果をどのように使用するかに基づいて決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d836-108">Whether string operations should be culture-sensitive or culture-insensitive depends on how your application uses the results.</span></span> <span data-ttu-id="2d836-109">ユーザーに結果を表示する場合は、通常、カルチャを認識する文字列操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d836-109">String operations that display results to the user should typically be culture-sensitive.</span></span> <span data-ttu-id="2d836-110">たとえば、アプリケーションがローカライズされた文字列を並べ替えてリスト ボックスに表示する場合は、カルチャを認識する並べ替えを実行します。</span><span class="sxs-lookup"><span data-stu-id="2d836-110">For example, if an application displays a sorted list of localized strings in a list box, the application should perform a culture-sensitive sort.</span></span>

<span data-ttu-id="2d836-111">内部的に使用される文字列に対する操作は、通常、カルチャを認識しないようにします。</span><span class="sxs-lookup"><span data-stu-id="2d836-111">Results of string operations that are used internally should typically be culture-insensitive.</span></span> <span data-ttu-id="2d836-112">一般的に、アプリケーションがファイル名、永続形式、エンド ユーザーに表示されないシンボル情報などの処理を実行する場合には、文字列操作の結果がカルチャごとに変わらないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d836-112">In general, if the application is working with file names, persistence formats, or symbolic information that is not displayed to the user, results of string operations should not vary by culture.</span></span> <span data-ttu-id="2d836-113">たとえば、XML タグとして認識されるかどうかを調べるために文字列を比較するアプリケーションでは、比較操作でカルチャを認識しないでください。</span><span class="sxs-lookup"><span data-stu-id="2d836-113">For example, if an application compares a string to determine whether it is a recognized XML tag, the comparison should not be culture-sensitive.</span></span> <span data-ttu-id="2d836-114">また、セキュリティに関する決定が文字列の比較操作や大文字と小文字の変更操作の結果に基づいて行われる場合は、この操作がカルチャを認識しないようにして、操作の結果が <xref:System.Globalization.CultureInfo.CurrentCulture%2A> の値に影響されないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d836-114">In addition, if a security decision is based on the result of a string comparison or case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of <xref:System.Globalization.CultureInfo.CurrentCulture%2A>.</span></span>

<span data-ttu-id="2d836-115">開発するアプリケーションにローカリゼーションとグローバリゼーションに対応するためのコードが含まれているかどうかに関係なく、.NET Framework のメソッドは既定ではカルチャを認識する結果を取得することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2d836-115">Whether or not you are developing an application that includes code to handle localization and globalization issues, you should be aware of the .NET Framework methods that retrieve culture-sensitive results by default.</span></span> <span data-ttu-id="2d836-116">このトピックの目的は、アプリケーションがこれらのメソッドを使用してカルチャを認識しない結果を取得するための正しい方法を示すことです。</span><span class="sxs-lookup"><span data-stu-id="2d836-116">The purpose of this topic is to illustrate the correct way for your applications to use these methods to obtain culture-insensitive results.</span></span>

## <a name="see-also"></a><span data-ttu-id="2d836-117">参照</span><span class="sxs-lookup"><span data-stu-id="2d836-117">See also</span></span>

- [<span data-ttu-id="2d836-118">グローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="2d836-118">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)
