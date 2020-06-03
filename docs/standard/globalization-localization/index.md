---
title: .NET アプリケーションのグローバライズとローカライズ
ms.date: 06/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- international applications [.NET]
- globalization [.NET], encoding
- global applications
- internationalization
- world-ready applications
- application development [.NET], globalization
- multilingual application development
ms.assetid: 9a59696b-d89b-45bd-946d-c75da4732d02
ms.openlocfilehash: 10d07a02a7ff744a87b920fd97df24b076c22cc3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288291"
---
# <a name="globalizing-and-localizing-net-applications"></a><span data-ttu-id="a1fbb-102">.NET アプリケーションのグローバライズとローカライズ</span><span class="sxs-lookup"><span data-stu-id="a1fbb-102">Globalizing and localizing .NET applications</span></span>

<span data-ttu-id="a1fbb-103">1 つ以上の言語にローカライズされるアプリケーションなど、国際対応アプリケーションを開発するには、グローバリゼーション、ローカライズ対象の確認、およびローカリゼーションの 3 つの手順が必要です。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-103">Developing a world-ready application, including an application that can be localized into one or more languages, involves three steps: globalization, localizability review, and localization.</span></span>

[<span data-ttu-id="a1fbb-104">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="a1fbb-104">Globalization</span></span>](globalization.md)

<span data-ttu-id="a1fbb-105">これは、特定のカルチャや言語に依存せず、すべてのユーザーに対して、ローカライズされたユーザー インターフェイスと、その地域に合ったデータをサポートするような、アプリケーションの設計と開発を行う手順です。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-105">This step involves designing and coding an application that is culture-neutral and language-neutral, and that supports localized user interfaces and regional data for all users.</span></span> <span data-ttu-id="a1fbb-106">これはカルチャ固有の前提に基づかない決定によって設計とプログラミングを行うことです。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-106">It involves making design and programming decisions that are not based on culture-specific assumptions.</span></span> <span data-ttu-id="a1fbb-107">グローバライズされたアプリケーションは、ローカライズされていなくても、後から比較的容易に 1 つ以上の言語にローカライズできるように設計開発されています。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-107">While a globalized application is not localized, it nevertheless is designed and written so that it can be subsequently localized into one or more languages with relative ease.</span></span>

[<span data-ttu-id="a1fbb-108">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="a1fbb-108">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="a1fbb-109">この手順により、アプリケーションのコードと設計をレビューして、ローカライズが容易になるようにし、ローカライズのための潜在的な問題点を識別し、アプリケーションの実行可能コードがリソースから分離されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-109">This step involves reviewing an application's code and design to ensure that it can be localized easily and to identify potential roadblocks for localization, and verifying that the application's executable code is separated from its resources.</span></span> <span data-ttu-id="a1fbb-110">グローバリゼーションの段階が効果的なものであれば、ローカリゼーション レビューはグローバリゼーションの過程で行われた設計とコーディングの決定を確認するものになります。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-110">If the globalization stage was effective, the localizability review will confirm the design and coding choices made during globalization.</span></span> <span data-ttu-id="a1fbb-111">ローカライズ対象の確認の段階では、ローカライズの段階でアプリケーションのソース コードを変更する必要がないように、残っている問題を特定します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-111">The localizability stage may also identify any remaining issues so that an application's source code doesn't have to be modified during the localization stage.</span></span>

[<span data-ttu-id="a1fbb-112">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="a1fbb-112">Localization</span></span>](localization.md)

<span data-ttu-id="a1fbb-113">この手順では、特定のカルチャまたは地域に合わせてアプリケーションをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-113">This step involves customizing an application for specific cultures or regions.</span></span> <span data-ttu-id="a1fbb-114">グローバリゼーションとローカライズ対象の確認を適切に行うと、ローカリゼーションでは主にユーザー インターフェイスの翻訳作業が行われます。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-114">If the globalization and localizability steps have been performed correctly, localization consists primarily of translating the user interface.</span></span>

<span data-ttu-id="a1fbb-115">この 3 つの手順に従うことにより、次の 2 つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-115">Following these three steps provides two advantages:</span></span>

- <span data-ttu-id="a1fbb-116">米国英語などのような 1 つのカルチャだけをサポートするアプリケーションを、他のカルチャもサポートするように変更する作業を行う必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-116">It frees you from having to retrofit an application that is designed to support a single culture, such as U.S. English, to support additional cultures.</span></span>

- <span data-ttu-id="a1fbb-117">ローカライズされたアプリケーションが、より安定してバグがより少ないものになります。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-117">It results in localized applications that are more stable and have fewer bugs.</span></span>

<span data-ttu-id="a1fbb-118">.NET には、国際対応アプリケーションやローカライズされたアプリケーションの開発の拡張サポートが備わっています。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-118">.NET provides extensive support for the development of world-ready and localized applications.</span></span> <span data-ttu-id="a1fbb-119">特に、.NET クラス ライブラリの多くの型メンバーは、現在のユーザーのカルチャまたは特定のカルチャの規則を表す値を返すことができ、グローバリゼーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-119">In particular, many type members in the .NET class library aid globalization by returning values that reflect the conventions of either the current user's culture or a specified culture.</span></span> <span data-ttu-id="a1fbb-120">また、.NET はサテライト アセンブリをサポートし、アプリケーションのローカライズ プロセスを容易にします。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-120">Also, .NET supports satellite assemblies, which facilitate the process of localizing an application.</span></span>

<span data-ttu-id="a1fbb-121">詳細については、[グローバリゼーションのドキュメント](/globalization/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-121">For additional information, see the [Globalization documentation](/globalization/).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a1fbb-122">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a1fbb-122">In this section</span></span>

[<span data-ttu-id="a1fbb-123">グローバリゼーション</span><span class="sxs-lookup"><span data-stu-id="a1fbb-123">Globalization</span></span>](globalization.md)

<span data-ttu-id="a1fbb-124">国際対応アプリケーションを作成するための最初の手順を説明します。カルチャや言語に依存しないアプリケーションの設計とコーディングを行います。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-124">Discusses the first stage of creating a world-ready application, which involves designing and coding an application that is culture-neutral and language-neutral.</span></span>

[<span data-ttu-id="a1fbb-125">.NET グローバリゼーションと ICU</span><span class="sxs-lookup"><span data-stu-id="a1fbb-125">.NET globalization and ICU</span></span>](globalization-icu.md)

<span data-ttu-id="a1fbb-126">.NET グローバリゼーションで [ICU (International Components for Unicode)](http://site.icu-project.org/home) がどのように使用されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-126">Describes how .NET globalization uses [International Components for Unicode (ICU)](http://site.icu-project.org/home).</span></span>

[<span data-ttu-id="a1fbb-127">ローカライズ化の確認</span><span class="sxs-lookup"><span data-stu-id="a1fbb-127">Localizability review</span></span>](localizability-review.md)

<span data-ttu-id="a1fbb-128">ローカライズされたアプリケーションを作成するための 2 つ目の手順を説明します。ローカライズのための潜在的な問題点を識別します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-128">Discusses the second stage of creating a localized application, which involves identifying potential roadblocks to localization.</span></span>

[<span data-ttu-id="a1fbb-129">ローカリゼーション</span><span class="sxs-lookup"><span data-stu-id="a1fbb-129">Localization</span></span>](localization.md)

<span data-ttu-id="a1fbb-130">ローカライズされたアプリケーションを作成するための最後の手順を説明します。特定の地域またはカルチャのために、アプリケーションのユーザー インターフェイスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-130">Discusses the final stage of creating a localized application, which involves customizing an application's user interface for specific regions or cultures.</span></span>

[<span data-ttu-id="a1fbb-131">カルチャを認識しない文字列操作</span><span class="sxs-lookup"><span data-stu-id="a1fbb-131">Culture-insensitive string operations</span></span>](culture-insensitive-string-operations.md)

<span data-ttu-id="a1fbb-132">既定ではカルチャが識別される .NET のメソッドやクラスを使用して、カルチャが識別されない結果を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-132">Describes how to use .NET methods and classes that are culture-sensitive by default to obtain culture-insensitive results.</span></span>

[<span data-ttu-id="a1fbb-133">推奨される国際対応アプリケーション開発手順</span><span class="sxs-lookup"><span data-stu-id="a1fbb-133">Best practices for developing world-ready applications</span></span>](best-practices-for-developing-world-ready-apps.md)

<span data-ttu-id="a1fbb-134">国際対応 ASP.NET アプリケーションのグローバリゼーション、ローカリゼーション、および開発の推奨手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-134">Describes the best practices to follow for globalization, localization, and developing world-ready ASP.NET applications.</span></span>

## <a name="reference"></a><span data-ttu-id="a1fbb-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1fbb-135">Reference</span></span>

- <span data-ttu-id="a1fbb-136"><xref:System.Globalization?displayProperty=nameWithType> 名前空間</span><span class="sxs-lookup"><span data-stu-id="a1fbb-136"><xref:System.Globalization?displayProperty=nameWithType> namespace</span></span>

   <span data-ttu-id="a1fbb-137">言語、国/地域、使用する暦、日付、通貨、通知の書式パターン、文字列の並べ替え順序など、カルチャ関連の情報を定義するクラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-137">Contains classes that define culture-related information, including the language, the country/region, the calendars in use, the format patterns for dates, currency, and numbers, and the sort order for strings.</span></span>

- <span data-ttu-id="a1fbb-138"><xref:System.Resources> 名前空間</span><span class="sxs-lookup"><span data-stu-id="a1fbb-138"><xref:System.Resources> namespace</span></span>

   <span data-ttu-id="a1fbb-139">リソースを作成、操作、および使用するためのクラスが格納されている名前空間です。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-139">Provides classes for creating, manipulating, and using resources.</span></span>

- <span data-ttu-id="a1fbb-140"><xref:System.Text> 名前空間</span><span class="sxs-lookup"><span data-stu-id="a1fbb-140"><xref:System.Text> namespace</span></span>

   <span data-ttu-id="a1fbb-141">ASCII、ANSI、Unicode、およびその他の文字エンコーディングを表すクラスが格納されている名前空間です。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-141">Contains classes representing ASCII, ANSI, Unicode, and other character encodings.</span></span>

- [<span data-ttu-id="a1fbb-142">Resgen.exe (リソース ファイル ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="a1fbb-142">Resgen.exe (Resource File Generator)</span></span>](../../framework/tools/resgen-exe-resource-file-generator.md)

   <span data-ttu-id="a1fbb-143">Resgen.exe を使用して .txt ファイルと XML ベース リソース フォーマット (.resx) ファイルを共通言語ランタイムのバイナリ .resources ファイルに変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-143">Describes how to use Resgen.exe to convert .txt files and XML-based resource format (.resx) files to common language runtime binary .resources files.</span></span>

- [<span data-ttu-id="a1fbb-144">Winres.exe (Windows フォーム リソース エディター)</span><span class="sxs-lookup"><span data-stu-id="a1fbb-144">Winres.exe (Windows Forms Resource Editor)</span></span>](../../framework/tools/winres-exe-windows-forms-resource-editor.md)

   <span data-ttu-id="a1fbb-145">Winres.exe を使用して Windows フォームのフォームをローカライズする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1fbb-145">Describes how to use Winres.exe to localize Windows Forms forms.</span></span>
