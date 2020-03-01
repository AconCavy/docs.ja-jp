---
title: .NET Core にライブラリを移植する
description: ライブラリ プロジェクトを .NET Framework から .NET Core に移植する方法を説明します。
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: 68fe36e543d949dc76bdb0c19ef3482936ad9e79
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157532"
---
# <a name="port-net-framework-libraries-to-net-core"></a><span data-ttu-id="ad70c-103">.NET Framework ライブラリを .NET Core に移植する</span><span class="sxs-lookup"><span data-stu-id="ad70c-103">Port .NET Framework libraries to .NET Core</span></span>

<span data-ttu-id="ad70c-104">.NET Framework ライブラリ コードを .NET Core に移植し、そこでクロスプラットフォームを実行して、それを使用するアプリの範囲を広げる方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-104">Learn how to port .NET Framework library code to .NET Core, where it runs cross-platform and expands the reach of the apps that use it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad70c-105">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="ad70c-105">Prerequisites</span></span>

<span data-ttu-id="ad70c-106">この記事では、以下を前提とします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-106">This article assumes that you:</span></span>

- <span data-ttu-id="ad70c-107">Visual Studio 2017 以降を使用している。</span><span class="sxs-lookup"><span data-stu-id="ad70c-107">Are using Visual Studio 2017 or later.</span></span> <span data-ttu-id="ad70c-108">(それ以前のバージョンの Visual Studio では、.NET Core がサポートされていません。)</span><span class="sxs-lookup"><span data-stu-id="ad70c-108">(.NET Core isn't supported on earlier versions of Visual Studio.)</span></span>
- <span data-ttu-id="ad70c-109">[推奨の移植プロセス](index.md)を理解している。</span><span class="sxs-lookup"><span data-stu-id="ad70c-109">Understand the [recommended porting process](index.md).</span></span>
- <span data-ttu-id="ad70c-110">[サード パーティの依存関係](third-party-deps.md)の問題が解決されている。</span><span class="sxs-lookup"><span data-stu-id="ad70c-110">Have resolved any issues with [third-party dependencies](third-party-deps.md).</span></span>

<span data-ttu-id="ad70c-111">次の記事の内容を理解している必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-111">You should also become familiar with the content of the following articles:</span></span>

<span data-ttu-id="ad70c-112">[.NET Standard](../../standard/net-standard.md)</span><span class="sxs-lookup"><span data-stu-id="ad70c-112">[.NET Standard](../../standard/net-standard.md)</span></span>\
<span data-ttu-id="ad70c-113">この記事では、すべての .NET 実装で使用可能にすることを目的とした、.NET API の正式な仕様について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-113">This article describes the formal specification of .NET APIs that are intended to be available on all .NET implementations.</span></span>

<span data-ttu-id="ad70c-114">[パッケージ、メタパッケージ、フレームワーク](../packages.md)</span><span class="sxs-lookup"><span data-stu-id="ad70c-114">[Packages, Metapackages and Frameworks](../packages.md)</span></span>\
<span data-ttu-id="ad70c-115">この記事では、.NET Core でのパッケージの定義と使用について説明すると共に、複数の .NET 実装で実行されるコードがパッケージでどのようにサポートされるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-115">This article discusses how .NET Core defines and uses packages and how packages support code running on multiple .NET implementations.</span></span>

<span data-ttu-id="ad70c-116">[クロス プラットフォーム ツールによるライブラリの作成](../tutorials/libraries.md)</span><span class="sxs-lookup"><span data-stu-id="ad70c-116">[Developing Libraries with Cross Platform Tools](../tutorials/libraries.md)</span></span>\
<span data-ttu-id="ad70c-117">この記事では、.NET Core CLI を使用してライブラリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-117">This article explains how to write libraries using the .NET Core CLI.</span></span>

<span data-ttu-id="ad70c-118">[.NET Core の *csproj* 形式に追加されたもの](../tools/csproj.md)</span><span class="sxs-lookup"><span data-stu-id="ad70c-118">[Additions to the *csproj* format for .NET Core](../tools/csproj.md)</span></span>\
<span data-ttu-id="ad70c-119">この記事では、*csproj* および MSBuild への移行に伴ってプロジェクト ファイルに追加された変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-119">This article outlines the changes that were added to the project file as part of the move to *csproj* and MSBuild.</span></span>

<span data-ttu-id="ad70c-120">[.NET Core への移植 - サード パーティの依存関係の分析](third-party-deps.md)</span><span class="sxs-lookup"><span data-stu-id="ad70c-120">[Porting to .NET Core - Analyzing your Third-Party Party Dependencies](third-party-deps.md)</span></span>\
<span data-ttu-id="ad70c-121">この記事では、サード パーティの依存関係の移植性と、NuGet パッケージの依存関係が .NET Core で機能しない場合の対処方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-121">This article discusses the portability of third-party dependencies and what to do when a NuGet package dependency doesn't run on .NET Core.</span></span>

## <a name="retarget-to-net-framework-472"></a><span data-ttu-id="ad70c-122">.NET Framework 4.7.2 に再ターゲット設定する</span><span class="sxs-lookup"><span data-stu-id="ad70c-122">Retarget to .NET Framework 4.7.2</span></span>

<span data-ttu-id="ad70c-123">コードのターゲットが .NET Framework 4.7.2 でない場合、.NET Framework 4.7.2 に再ターゲット設定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-123">If your code isn't targeting .NET Framework 4.7.2, we recommended that you retarget to .NET Framework 4.7.2.</span></span> <span data-ttu-id="ad70c-124">ターゲット設定することで、.NET Standard が既存の API をサポートしていない場合に、最新の代替 API を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-124">This ensures the availability of the latest API alternatives for cases where the .NET Standard doesn't support existing APIs.</span></span>

<span data-ttu-id="ad70c-125">移植するプロジェクトごとに、Visual Studio で次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-125">For each of the projects you wish to port, do the following in Visual Studio:</span></span>

1. <span data-ttu-id="ad70c-126">プロジェクトを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-126">Right-click on the project and select **Properties**.</span></span>
1. <span data-ttu-id="ad70c-127">**[対象とする Framework]** ボックスの一覧で、 **[.NET Framework 4.7.2]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-127">In the **Target Framework** dropdown, select **.NET Framework 4.7.2**.</span></span>
1. <span data-ttu-id="ad70c-128">プロジェクトを再コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-128">Recompile the project.</span></span>

<span data-ttu-id="ad70c-129">プロジェクトのターゲットが .NET Framework 4.7.2 になったため、コード移植のベースとしてその .NET Framework を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-129">Because your projects now target .NET Framework 4.7.2, use that version of the .NET Framework as your base for porting code.</span></span>

## <a name="determine-portability"></a><span data-ttu-id="ad70c-130">移植性を判別する</span><span class="sxs-lookup"><span data-stu-id="ad70c-130">Determine portability</span></span>

<span data-ttu-id="ad70c-131">次の手順では、API Portability Analyzer (ApiPort) を実行して、分析用の移植性レポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-131">The next step is to run the API Portability Analyzer (ApiPort) to generate a portability report for analysis.</span></span>

<span data-ttu-id="ad70c-132">[API Portability Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) を理解し、.NET Core をターゲットとする移植性レポートを生成する方法を理解している必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-132">Make sure you understand the [API Portability Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) and how to generate portability reports for targeting .NET Core.</span></span> <span data-ttu-id="ad70c-133">その方法は、ニーズと個人の好みによって変わります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-133">How you do this likely varies based on your needs and personal tastes.</span></span> <span data-ttu-id="ad70c-134">以下のセクションでは、いくつかの異なるアプローチについて詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-134">The following sections detail a few different approaches.</span></span> <span data-ttu-id="ad70c-135">コードの構成内容によっては、これらのアプローチの手順を組み合わせて使用していることに気付くかもしれません。</span><span class="sxs-lookup"><span data-stu-id="ad70c-135">You may find yourself mixing steps of these approaches depending on how your code is structured.</span></span>

### <a name="deal-primarily-with-the-compiler"></a><span data-ttu-id="ad70c-136">主にコンパイラを使用して対処する</span><span class="sxs-lookup"><span data-stu-id="ad70c-136">Deal primarily with the compiler</span></span>

<span data-ttu-id="ad70c-137">このアプローチは、小さなプロジェクト、つまり多くの .NET Framework API を使用しないプロジェクトに適しています。</span><span class="sxs-lookup"><span data-stu-id="ad70c-137">This approach works well for small projects or projects that don't use many .NET Framework APIs.</span></span> <span data-ttu-id="ad70c-138">このアプローチは単純です。</span><span class="sxs-lookup"><span data-stu-id="ad70c-138">The approach is simple:</span></span>

1. <span data-ttu-id="ad70c-139">必要に応じてプロジェクトで ApiPort を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-139">Optionally, run ApiPort on your project.</span></span> <span data-ttu-id="ad70c-140">ApiPort を実行すると、レポートから対応が必要となる問題についての情報を得られます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-140">If you run ApiPort, gain knowledge from the report on issues you'll need to address.</span></span>
1. <span data-ttu-id="ad70c-141">すべてのコードを新しい .NET Core プロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-141">Copy all of your code over into a new .NET Core project.</span></span>
1. <span data-ttu-id="ad70c-142">移植性に関するレポート (生成されている場合) を参照しながら、プロジェクトが完全にコンパイルされるまでコンパイラ エラーを解決します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-142">While referring to the portability report (if generated), solve compiler errors until the project fully compiles.</span></span>

<span data-ttu-id="ad70c-143">このコード中心のアプローチは、構造化されていませんが、多くの場合に問題を迅速に解決します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-143">Although it is unstructured, this code-focused approach often resolves issues quickly.</span></span> <span data-ttu-id="ad70c-144">特に、データ モデルのみが含まれるプロジェクトにはこのアプローチが最適です。</span><span class="sxs-lookup"><span data-stu-id="ad70c-144">A project that contains only data models might be an ideal candidate for this approach.</span></span>

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a><span data-ttu-id="ad70c-145">移植性の問題が解決されるまで .NET Framework を使い続ける</span><span class="sxs-lookup"><span data-stu-id="ad70c-145">Stay on the .NET Framework until portability issues are resolved</span></span>

<span data-ttu-id="ad70c-146">このアプローチは、すべてのプロセスでコンパイルできるコードを作成したい場合にお勧めです。</span><span class="sxs-lookup"><span data-stu-id="ad70c-146">This approach might be the best if you prefer to have code that compiles during the entire process.</span></span> <span data-ttu-id="ad70c-147">アプローチは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ad70c-147">The approach is as follows:</span></span>

1. <span data-ttu-id="ad70c-148">プロジェクトで ApiPort を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-148">Run ApiPort on a project.</span></span>
1. <span data-ttu-id="ad70c-149">移植可能な別の API を使用して問題に対処します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-149">Address issues by using different APIs that are portable.</span></span>
1. <span data-ttu-id="ad70c-150">直接の代替方法を使用できない領域をすべて書き留めます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-150">Take note of any areas where you're prevented from using a direct alternative.</span></span>
1. <span data-ttu-id="ad70c-151">新しい .NET Core プロジェクトにコピーしても問題ないことが確認できるまで、移植するすべてのプロジェクトに対して前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-151">Repeat the prior steps for all projects you're porting until you're confident each is ready to be copied over into a new .NET Core project.</span></span>
1. <span data-ttu-id="ad70c-152">コードを新しい .NET Core プロジェクトにコピーします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-152">Copy the code into a new .NET Core project.</span></span>
1. <span data-ttu-id="ad70c-153">直接の代替手段がないと書き留めた問題に対処します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-153">Work out any issues where you noted that a direct alternative doesn't exist.</span></span>

<span data-ttu-id="ad70c-154">この慎重なアプローチは、コンパイラ エラーに対処するだけの方法よりも体系的ですが、それでも比較的コード中心であり、コンパイルできるコードが常にあるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-154">This careful approach is more structured than simply working out compiler errors, but it's still relatively code-focused and has the benefit of always having code that compiles.</span></span> <span data-ttu-id="ad70c-155">別の API を使用するだけでは解決できなかった問題を解決する方法は、大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-155">The way you resolve certain issues that couldn't be addressed by just using another API varies greatly.</span></span> <span data-ttu-id="ad70c-156">プロジェクトによっては、次のアプローチのように、より包括的な計画を開発する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-156">You may find that you need to develop a more comprehensive plan for certain projects, which is covered in the next approach.</span></span>

### <a name="develop-a-comprehensive-plan-of-attack"></a><span data-ttu-id="ad70c-157">包括的な計画を新たに作成する</span><span class="sxs-lookup"><span data-stu-id="ad70c-157">Develop a comprehensive plan of attack</span></span>

<span data-ttu-id="ad70c-158">このアプローチは、.NET Core をサポートするために、コードの再構築や特定範囲の完全な書き換えが必要になる可能性があるような、大規模で複雑なプロジェクトにお勧めです。</span><span class="sxs-lookup"><span data-stu-id="ad70c-158">This approach might be best for larger and more complex projects, where restructuring code or completely rewriting certain areas of code might be necessary to support .NET Core.</span></span> <span data-ttu-id="ad70c-159">アプローチは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ad70c-159">The approach is as follows:</span></span>

1. <span data-ttu-id="ad70c-160">プロジェクトで ApiPort を実行します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-160">Run ApiPort on a project.</span></span>
1. <span data-ttu-id="ad70c-161">移植できない性質のものが使用されている箇所と、それが移植性全体に与える影響を把握します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-161">Understand where each non-portable type is used and how that affects overall portability.</span></span>
   - <span data-ttu-id="ad70c-162">種類の性質を理解します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-162">Understand the nature of those types.</span></span> <span data-ttu-id="ad70c-163">数は少なくても使用頻度は高いですか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-163">Are they small in number but used frequently?</span></span> <span data-ttu-id="ad70c-164">数は多くても使用頻度は低いですか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-164">Are they large in number but used infrequently?</span></span> <span data-ttu-id="ad70c-165">コードで集中して使用されていますか、それともあちこちで使用されていますか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-165">Is their use concentrated, or is it spread throughout your code?</span></span>
   - <span data-ttu-id="ad70c-166">移植できないコードの分離は簡単で、効果的に処理できますか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-166">Is it easy to isolate code that isn't portable so that you can deal with it more effectively?</span></span>
   - <span data-ttu-id="ad70c-167">コードをリファクタリングする必要はありますか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-167">Do you need to refactor your code?</span></span>
   - <span data-ttu-id="ad70c-168">移植可能ではない種類の場合、同じ作業を実行できる代替 API はありますか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-168">For those types that aren't portable, are there alternative APIs that accomplish the same task?</span></span> <span data-ttu-id="ad70c-169">たとえば、<xref:System.Net.WebClient> クラスを使用している場合は、代わりに <xref:System.Net.Http.HttpClient> クラスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-169">For example, if you're using the <xref:System.Net.WebClient> class, you might be able to use the <xref:System.Net.Http.HttpClient> class instead.</span></span>
   - <span data-ttu-id="ad70c-170">一時的な置き換えでない場合でも、作業を完了させるのに使用できる、移植可能な API が別にありますか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-170">Are there different portable APIs available to accomplish a task, even if it's not a drop-in replacement?</span></span> <span data-ttu-id="ad70c-171">たとえば、<xref:System.Xml.Schema.XmlSchema> を使用して XML を解析しているが、XML スキーマ検出が不要な場合、<xref:System.Xml.Linq> API を使用して API に依存しない解析を独自に実装できます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-171">For example, if you're using <xref:System.Xml.Schema.XmlSchema> to parse XML but don't require XML schema discovery, you could use <xref:System.Xml.Linq> APIs and implement parsing yourself as opposed to relying on an API.</span></span>
1. <span data-ttu-id="ad70c-172">移植が困難なアセンブリがある場合、.NET Framework を今すぐ止める価値はあるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-172">If you have assemblies that are difficult to port, is it worth leaving them on .NET Framework for now?</span></span> <span data-ttu-id="ad70c-173">次の点を考慮することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-173">Here are some things to consider:</span></span>
   - <span data-ttu-id="ad70c-174">.NET Framework または Windows 固有の機能への依存度が高いために、.NET Core との互換性がない機能がライブラリにあるとします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-174">You may have some functionality in your library that's incompatible with .NET Core because it relies too heavily on .NET Framework or Windows-specific functionality.</span></span> <span data-ttu-id="ad70c-175">現時点ではその機能をあきらめ、機能を移植できるリソースが利用できるようになるまで、機能の少ない一時的な .NET Core バージョンのライブラリをリリースするのがよいでしょうか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-175">Is it worth leaving that functionality behind for now and releasing a temporary .NET Core version of your library with less features until resources are available to port the features?</span></span>
   - <span data-ttu-id="ad70c-176">リファクタリングが有効でしょうか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-176">Would a refactor help?</span></span>
1. <span data-ttu-id="ad70c-177">使用できない .NET Framework API の代わりになる実装を開発することは理にかなっていますか。</span><span class="sxs-lookup"><span data-stu-id="ad70c-177">Is it reasonable to write your own implementation of an unavailable .NET Framework API?</span></span>
   <span data-ttu-id="ad70c-178">[.NET Framework の参照ソース](https://github.com/Microsoft/referencesource)のコードのコピー、変更、および使用も検討できます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-178">You could consider copying, modifying, and using code from the [.NET Framework reference source](https://github.com/Microsoft/referencesource).</span></span> <span data-ttu-id="ad70c-179">この参照ソース コードは [MIT ライセンス](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt)の下で使用が許可されているため、このソースをコードの基盤として、かなり自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-179">The reference source code is licensed under the [MIT License](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), so you have significant freedom to use the source as a basis for your own code.</span></span> <span data-ttu-id="ad70c-180">ただし、コードには Microsoft への帰属を適切に示してください。</span><span class="sxs-lookup"><span data-stu-id="ad70c-180">Just be sure to properly attribute Microsoft in your code.</span></span>
1. <span data-ttu-id="ad70c-181">プロジェクトごとにこのプロセスを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-181">Repeat this process as needed for different projects.</span></span>

<span data-ttu-id="ad70c-182">コードベースのサイズによっては、分析フェーズに時間がかかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-182">The analysis phase could take some time depending on the size of your codebase.</span></span> <span data-ttu-id="ad70c-183">このフェーズに時間を割き、必要な変更の範囲を完全に把握してから計画を立てることで、長期的には多くの時間を節約できます。特に、コードベースが複雑な場合には有効です。</span><span class="sxs-lookup"><span data-stu-id="ad70c-183">Spending time in this phase to thoroughly understand the scope of changes needed and to develop a plan usually saves you time in the long run, particularly if you have a complex codebase.</span></span>

<span data-ttu-id="ad70c-184">コードベースの大幅な変更が必要な計画になる可能性がありますが、ターゲット設定は .NET Framework 4.7.2 です。そのため、これは前のアプローチよりも体系化されたバージョンです。</span><span class="sxs-lookup"><span data-stu-id="ad70c-184">Your plan could involve making significant changes to your codebase while still targeting .NET Framework 4.7.2, making this a more structured version of the previous approach.</span></span> <span data-ttu-id="ad70c-185">計画の実施方法は、コードベースによって異なります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-185">How you go about executing your plan is dependent on your codebase.</span></span>

### <a name="mixed-approach"></a><span data-ttu-id="ad70c-186">混合アプローチ</span><span class="sxs-lookup"><span data-stu-id="ad70c-186">Mixed approach</span></span>

<span data-ttu-id="ad70c-187">多くの場合は、プロジェクトごとに、前述のアプローチを混合して利用します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-187">It's likely that you'll mix the above approaches on a per-project basis.</span></span> <span data-ttu-id="ad70c-188">自分とコードベースにとって最も有用な処理を実行するようにします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-188">You should do what makes the most sense to you and for your codebase.</span></span>

## <a name="port-your-tests"></a><span data-ttu-id="ad70c-189">テストを移植する</span><span class="sxs-lookup"><span data-stu-id="ad70c-189">Port your tests</span></span>

<span data-ttu-id="ad70c-190">コードを移植したときにすべての機能が動作することを確認するには、コードを .NET Core に移植してテストすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-190">The best way to make sure everything works when you've ported your code is to test your code as you port it to .NET Core.</span></span> <span data-ttu-id="ad70c-191">このテストを行うには、.NET Core 用のテストを構築して実行するためのテスト フレームワークを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-191">To do this, you'll need to use a testing framework that builds and runs tests for .NET Core.</span></span> <span data-ttu-id="ad70c-192">現在のところ、次の 3 つの選択肢があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-192">Currently, you have three options:</span></span>

- [<span data-ttu-id="ad70c-193">xUnit</span><span class="sxs-lookup"><span data-stu-id="ad70c-193">xUnit</span></span>](https://xunit.github.io/)
  - [<span data-ttu-id="ad70c-194">はじめに</span><span class="sxs-lookup"><span data-stu-id="ad70c-194">Getting Started</span></span>](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [<span data-ttu-id="ad70c-195">MSTest プロジェクトを xUnit に変換するツール</span><span class="sxs-lookup"><span data-stu-id="ad70c-195">Tool to convert an MSTest project to xUnit</span></span>](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [<span data-ttu-id="ad70c-196">NUnit</span><span class="sxs-lookup"><span data-stu-id="ad70c-196">NUnit</span></span>](https://nunit.org/)
  - [<span data-ttu-id="ad70c-197">はじめに</span><span class="sxs-lookup"><span data-stu-id="ad70c-197">Getting Started</span></span>](https://github.com/nunit/docs/wiki/Installation)
  - [<span data-ttu-id="ad70c-198">MSTest から NUnit への移行に関するブログ投稿</span><span class="sxs-lookup"><span data-stu-id="ad70c-198">Blog post about migrating from MSTest to NUnit</span></span>](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [<span data-ttu-id="ad70c-199">MSTest</span><span class="sxs-lookup"><span data-stu-id="ad70c-199">MSTest</span></span>](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a><span data-ttu-id="ad70c-200">推奨されるアプローチ</span><span class="sxs-lookup"><span data-stu-id="ad70c-200">Recommended approach</span></span>

<span data-ttu-id="ad70c-201">最終的に、移植作業は .NET Framework コードの構成内容に大きく左右されます。</span><span class="sxs-lookup"><span data-stu-id="ad70c-201">Ultimately, the porting effort depends heavily on how your .NET Framework code is structured.</span></span> <span data-ttu-id="ad70c-202">コードを移植するのに良い方法は、コードの基本コンポーネントであるライブラリの "*ベース*" から始めることです。</span><span class="sxs-lookup"><span data-stu-id="ad70c-202">A good way to port your code is to begin with the *base* of your library, which is the foundational components of your code.</span></span> <span data-ttu-id="ad70c-203">ベースは、その他すべてが直接または間接的に使用するデータ モデル、または他の基本クラスやメソッドの場合があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-203">This might be data models or some other foundational classes and methods that everything else uses directly or indirectly.</span></span>

1. <span data-ttu-id="ad70c-204">移植対象のライブラリのレイヤーをテストするテスト プロジェクトを移植します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-204">Port the test project that tests the layer of your library that you're currently porting.</span></span>
1. <span data-ttu-id="ad70c-205">ライブラリのベースを新しい .NET Core プロジェクトにコピーし、サポートする .NET Standard のバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-205">Copy over the base of your library into a new .NET Core project and select the version of the .NET Standard you wish to support.</span></span>
1. <span data-ttu-id="ad70c-206">必要に応じてコードを変更し、コンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ad70c-206">Make any changes needed to get the code to compile.</span></span> <span data-ttu-id="ad70c-207">多くの場合、NuGet パッケージの依存関係を *csproj* ファイルに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-207">Much of this may require adding NuGet package dependencies to your *csproj* file.</span></span>
1. <span data-ttu-id="ad70c-208">テストを実行し、必要な調整を行います。</span><span class="sxs-lookup"><span data-stu-id="ad70c-208">Run the tests and make any needed adjustments.</span></span>
1. <span data-ttu-id="ad70c-209">次のコード レイヤーを選択して移植し、前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="ad70c-209">Pick the next layer of code to port over and repeat the prior steps.</span></span>

<span data-ttu-id="ad70c-210">ライブラリのベースから開始してベースから外側に向かい、必要に応じて各レイヤーをテストする場合、移植は、問題が一度でコードの 1 レイヤーに分離される体系的なプロセスになります。</span><span class="sxs-lookup"><span data-stu-id="ad70c-210">If you start with the base of your library and move outward from the base and test each layer as needed, porting is a systematic process where problems are isolated to one layer of code at a time.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad70c-211">次の手順</span><span class="sxs-lookup"><span data-stu-id="ad70c-211">Next steps</span></span>

>[!div class="nextstepaction"]
>[<span data-ttu-id="ad70c-212">.NET Core のプロジェクトを整理する</span><span class="sxs-lookup"><span data-stu-id="ad70c-212">Organize projects for .NET Core</span></span>](project-structure.md)
