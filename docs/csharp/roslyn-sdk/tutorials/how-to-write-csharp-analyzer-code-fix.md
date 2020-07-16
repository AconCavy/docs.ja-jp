---
title: 'チュートリアル: 最初のアナライザーとコード修正を作成する'
description: このチュートリアルでは、.NET Compiler SDK (Roslyn API) を使用してアナライザーとコード修正を作成する手順を詳しく説明します。
ms.date: 08/01/2018
ms.custom: mvc
ms.openlocfilehash: c70fcacc6cb30969e5c69ffd0954ac52e637a915
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100939"
---
# <a name="tutorial-write-your-first-analyzer-and-code-fix"></a><span data-ttu-id="112b5-103">チュートリアル: 最初のアナライザーとコード修正を作成する</span><span class="sxs-lookup"><span data-stu-id="112b5-103">Tutorial: Write your first analyzer and code fix</span></span>

<span data-ttu-id="112b5-104">.NET Compiler Platform SDK には、C# または Visual Basic コードをターゲットとするカスタム警告を作成するために必要なツールが用意されています。</span><span class="sxs-lookup"><span data-stu-id="112b5-104">The .NET Compiler Platform SDK provides the tools you need to create custom warnings that target C# or Visual Basic code.</span></span> <span data-ttu-id="112b5-105">**アナライザー**には、規則違反を認識するコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="112b5-105">Your **analyzer** contains code that recognizes violations of your rule.</span></span> <span data-ttu-id="112b5-106">**コード修正**には、違反を修正するコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="112b5-106">Your **code fix** contains the code that fixes the violation.</span></span> <span data-ttu-id="112b5-107">実装する規則には、コード構造から、コーディング スタイル、名前付け規則などがあります。</span><span class="sxs-lookup"><span data-stu-id="112b5-107">The rules you implement can be anything from code structure to coding style to naming conventions and more.</span></span> <span data-ttu-id="112b5-108">.NET Compiler Platform には、開発者がコードを作成するときに分析を実行するためのフレームワークと、コードを修正するためのすべての Visual Studio UI 機能が用意されています。具体的には、エディターに波線を表示する、Visual Studio のエラー一覧を表示する、"電球" の提案を作成する、推奨される修正の豊富なプレビューを表示するなどの機能です。</span><span class="sxs-lookup"><span data-stu-id="112b5-108">The .NET Compiler Platform provides the framework for running analysis as developers are writing code, and all the Visual Studio UI features for fixing code: showing squiggles in the editor, populating the Visual Studio Error List, creating the "light bulb" suggestions and showing the rich preview of the suggested fixes.</span></span>

<span data-ttu-id="112b5-109">このチュートリアルでは、Roslyn API を使用して**アナライザー**とそれに付随する**コード修正**の作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="112b5-109">In this tutorial, you'll explore the creation of an **analyzer** and an accompanying **code fix** using the Roslyn APIs.</span></span> <span data-ttu-id="112b5-110">アナライザーは、ソース コードの分析を実行し、問題をユーザーに報告する方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="112b5-110">An analyzer is a way to perform source code analysis and report a problem to the user.</span></span> <span data-ttu-id="112b5-111">必要に応じて、アナライザーは、ユーザーのソース コードに対する変更を表すコード修正を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="112b5-111">Optionally, an analyzer can also provide a code fix that represents a modification to the user's source code.</span></span> <span data-ttu-id="112b5-112">このチュートリアルでは、`const` 修飾子を使用して宣言できますが、実際は宣言されていないローカル変数宣言を検出するアナライザーを作成します。</span><span class="sxs-lookup"><span data-stu-id="112b5-112">This tutorial creates an analyzer that finds local variable declarations that could be declared using the `const` modifier but are not.</span></span> <span data-ttu-id="112b5-113">付随するコード修正は、それらの宣言を修正して `const` 修飾子を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-113">The accompanying code fix modifies those declarations to add the `const` modifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="112b5-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="112b5-114">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="112b5-115">現行の Visual Studio **コード修正付きアナライザー (.NET Standard)** テンプレートには既知のバグが含まれていますが、Visual Studio 2019 バージョン 16.7 で修正されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-115">The current Visual Studio **Analyzer with code fix (.NET Standard)** template has a known bug in it and should be fixed in Visual Studio 2019 version 16.7.</span></span> <span data-ttu-id="112b5-116">テンプレートのプロジェクトは、次の変更が行われない限り、コンパイルされません。</span><span class="sxs-lookup"><span data-stu-id="112b5-116">The projects in the template will not compile unless the following changes are made:</span></span>
>
> 1. <span data-ttu-id="112b5-117">**[ツール]** 、 **[オプション]** 、 **[NuGet パッケージ マネージャー]** 、 **[パッケージ ソース]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="112b5-117">Select **Tools** > **Options** > **NuGet Package Manager** > **Package Sources**</span></span>
>    - <span data-ttu-id="112b5-118">プラス記号ボタンを選択すると、新しいソースが追加されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-118">Select the plus button, to add a new source:</span></span>
>    - <span data-ttu-id="112b5-119">**[ソース]** を `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` に設定し、 **[更新]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="112b5-119">Set the **Source** to `https://dotnet.myget.org/F/roslyn-analyzers/api/v3/index.json` and select **Update**</span></span>
> 1. <span data-ttu-id="112b5-120">**[ソリューション エクスプローラー]** で **[MakeConst.Vsix]** プロジェクトを右クリックし、 **[プロジェクト ファイルの編集]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="112b5-120">From the **Solution Explorer**, right-click on the **MakeConst.Vsix** project, and select **Edit Project File**</span></span>
>    - <span data-ttu-id="112b5-121">`<AssemblyName>` ノードを更新し、`.Visx` サフィックスを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-121">Update the `<AssemblyName>` node to add the `.Visx` suffix:</span></span>
>      - `<AssemblyName>MakeConst.Vsix</AssemblyName>`
>    - <span data-ttu-id="112b5-122">41 行目の `<ProjectReference>` ノードを更新し、`TargetFramework` の値を変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-122">Update the `<ProjectReference>` node on line 41 to alter the `TargetFramework` value:</span></span>
>      - `<ProjectReference Update="@(ProjectReference)" AdditionalProperties="TargetFramework=netstandard2.0" />`
> 1. <span data-ttu-id="112b5-123">*[MakeConst.Test]* プロジェクトで *MakeConstUnitTests.cs* ファイルを更新します。</span><span class="sxs-lookup"><span data-stu-id="112b5-123">Update the *MakeConstUnitTests.cs* file, in the *MakeConst.Test* project:</span></span>
>    - <span data-ttu-id="112b5-124">9 行目を次のように変更します。名前空間の変更に注目してください。</span><span class="sxs-lookup"><span data-stu-id="112b5-124">Change line 9 to the following, notice namespace alteration:</span></span>
>      - `using Verify = Microsoft.CodeAnalysis.CSharp.Testing.MSTest.CodeFixVerifier<`
>    - <span data-ttu-id="112b5-125">24 行目を次のメソッドに変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-125">Change line 24 to the following method:</span></span>
>      - `await Verify.VerifyAnalyzerAsync(test);`
>    - <span data-ttu-id="112b5-126">62 行目を次のメソッドに変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-126">Change line 62 to the following method:</span></span>
>      - `await Verify.VerifyCodeFixAsync(test, expected, fixtest);`

- [<span data-ttu-id="112b5-127">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="112b5-127">Visual Studio 2017</span></span>](https://visualstudio.microsoft.com/vs/older-downloads/#visual-studio-2017-and-other-products)
- [<span data-ttu-id="112b5-128">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="112b5-128">Visual Studio 2019</span></span>](https://www.visualstudio.com/downloads)

<span data-ttu-id="112b5-129">Visual Studio インストーラーで **.NET Compiler Platform SDK** をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-129">You'll need to install the **.NET Compiler Platform SDK** via the Visual Studio Installer:</span></span>

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<span data-ttu-id="112b5-130">アナライザーの作成と検証にはいくつかの手順があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-130">There are several steps to creating and validating your analyzer:</span></span>

1. <span data-ttu-id="112b5-131">ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="112b5-131">Create the solution.</span></span>
1. <span data-ttu-id="112b5-132">アナライザーの名前と説明を登録します。</span><span class="sxs-lookup"><span data-stu-id="112b5-132">Register the analyzer name and description.</span></span>
1. <span data-ttu-id="112b5-133">アナライザーの警告と推奨事項を報告します。</span><span class="sxs-lookup"><span data-stu-id="112b5-133">Report analyzer warnings and recommendations.</span></span>
1. <span data-ttu-id="112b5-134">推奨事項を受け取るコード修正を実装します。</span><span class="sxs-lookup"><span data-stu-id="112b5-134">Implement the code fix to accept recommendations.</span></span>
1. <span data-ttu-id="112b5-135">単体テストで分析を改善します。</span><span class="sxs-lookup"><span data-stu-id="112b5-135">Improve the analysis through unit tests.</span></span>

## <a name="explore-the-analyzer-template"></a><span data-ttu-id="112b5-136">アナライザー テンプレートを調べる</span><span class="sxs-lookup"><span data-stu-id="112b5-136">Explore the analyzer template</span></span>

<span data-ttu-id="112b5-137">アナライザーは、ローカル定数に変換できるローカル変数宣言をユーザーに報告します。</span><span class="sxs-lookup"><span data-stu-id="112b5-137">Your analyzer reports to the user any local variable declarations that can be converted to local constants.</span></span> <span data-ttu-id="112b5-138">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="112b5-138">For example, consider the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="112b5-139">上記のコードでは、`x` には定数値が割り当てられており、変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="112b5-139">In the code above, `x` is assigned a constant value and is never modified.</span></span> <span data-ttu-id="112b5-140">これは `const` 修飾子を使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="112b5-140">It can be declared using the `const` modifier:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="112b5-141">変数を定数にすることができるかどうかを判断するために、構文解析、初期化子式の定数分析、および変数に書き込まれないというデータフロー分析が必要です。</span><span class="sxs-lookup"><span data-stu-id="112b5-141">The analysis to determine whether a variable can be made constant is involved, requiring syntactic analysis, constant analysis of the initializer expression and dataflow analysis to ensure that the variable is never written to.</span></span> <span data-ttu-id="112b5-142">.NET Compiler Platform には、この分析を簡単に実行できる API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="112b5-142">The .NET Compiler Platform provides APIs that make it easier to perform this analysis.</span></span> <span data-ttu-id="112b5-143">最初の手順は、新しい C# の**コード修正を含むアナライザー** プロジェクトを作成することです。</span><span class="sxs-lookup"><span data-stu-id="112b5-143">The first step is to create a new C# **Analyzer with code fix** project.</span></span>

- <span data-ttu-id="112b5-144">Visual Studio で、 **[ファイル] > [新規] > [プロジェクト]** の順に選択して、[新しいプロジェクト] ダイアログを表示します。</span><span class="sxs-lookup"><span data-stu-id="112b5-144">In Visual Studio, choose **File > New > Project...** to display the New Project dialog.</span></span>
- <span data-ttu-id="112b5-145">**[Visual C#] > [Extensibility]** で、 **[Analyzer with code fix (.NET Standard)]\(コード修正付きアナライザー (.NET Standard)\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="112b5-145">Under **Visual C# > Extensibility**, choose **Analyzer with code fix (.NET Standard)**.</span></span>
- <span data-ttu-id="112b5-146">プロジェクトに「**MakeConst**」という名前を付けて、[OK] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="112b5-146">Name your project "**MakeConst**" and click OK.</span></span>

<span data-ttu-id="112b5-147">コード修正テンプレート付きアナライザー テンプレートを使用すると、アナライザーとコード修正を含むプロジェクト、単体テスト プロジェクト、VSIX プロジェクトという 3 つのプロジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-147">The analyzer with code fix template creates three projects: one contains the analyzer and code fix, the second is a unit test project, and the third is the VSIX project.</span></span> <span data-ttu-id="112b5-148">既定のスタートアップ プロジェクトは VSIX プロジェクトです。</span><span class="sxs-lookup"><span data-stu-id="112b5-148">The default startup project is the VSIX project.</span></span> <span data-ttu-id="112b5-149"><kbd>F5</kbd> キーを押して、VSIX プロジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="112b5-149">Press <kbd>F5</kbd> to start the VSIX project.</span></span> <span data-ttu-id="112b5-150">これにより、新しいアナライザーが読み込まれた Visual Studio の 2 つ目のインスタンスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-150">This starts a second instance of Visual Studio that has loaded your new analyzer.</span></span>

> [!TIP]
> <span data-ttu-id="112b5-151">アナライザーを実行するときは、Visual Studio の 2 つ目のコピーを開始します。</span><span class="sxs-lookup"><span data-stu-id="112b5-151">When you run your analyzer, you start a second copy of Visual Studio.</span></span> <span data-ttu-id="112b5-152">この 2 つ目のコピーは、別のレジストリ ハイブを使用して設定を保存します。</span><span class="sxs-lookup"><span data-stu-id="112b5-152">This second copy uses a different registry hive to store settings.</span></span> <span data-ttu-id="112b5-153">これにより、Visual Studio の 2 つのコピーのビジュアル設定を区別することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-153">That enables you to differentiate the visual settings in the two copies of Visual Studio.</span></span> <span data-ttu-id="112b5-154">Visual Studio の実験的な実行のために、別のテーマを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-154">You can pick a different theme for the experimental run of Visual Studio.</span></span> <span data-ttu-id="112b5-155">また、設定のローミングや、Visual Studio アカウントへのログインには、Visual Studio の実験的な実行が使用されません。</span><span class="sxs-lookup"><span data-stu-id="112b5-155">In addition, don't roam your settings or login to your Visual Studio account using the experimental run of Visual Studio.</span></span> <span data-ttu-id="112b5-156">そのため、設定を分けておくことができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-156">That keeps the settings different.</span></span>

<span data-ttu-id="112b5-157">開始した 2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成します (.NET Core または .NET Framework プロジェクトが動作し、アナライザーはソース レベルで動作します)。波線の下線が表示されているトークンにマウス カーソルを移動すると、アナライザーに設定されている警告テキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-157">In the second Visual Studio instance that you just started, create a new C# Console Application project (either .NET Core or .NET Framework project will work -- analyzers work at the source level.) Hover over the token with a wavy underline, and the warning text provided by an analyzer appears.</span></span>

<span data-ttu-id="112b5-158">テンプレートを使用すると、次の図のように、型名が小文字の個々の型宣言に対して警告を報告するアナライザーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-158">The template creates an analyzer that reports a warning on each type declaration where the type name contains lowercase letters, as shown in the following figure:</span></span>

![警告を報告するアナライザー](media/how-to-write-csharp-analyzer-code-fix/report-warning.png)

<span data-ttu-id="112b5-160">また、テンプレートには、小文字を含むすべての型名をすべて大文字に変更するコード修正も用意されています。</span><span class="sxs-lookup"><span data-stu-id="112b5-160">The template also provides a code fix that changes any type name containing lower case characters to all upper case.</span></span> <span data-ttu-id="112b5-161">警告が表示された電球をクリックすると、推奨される変更が表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-161">You can click on the light bulb displayed with the warning to see the suggested changes.</span></span> <span data-ttu-id="112b5-162">推奨される変更を受け入れると、型の名前と、ソリューション内のその型に対するすべての参照が更新されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-162">Accepting the suggested changes updates the type name and all references to that type in the solution.</span></span> <span data-ttu-id="112b5-163">最初のアナライザーの動作を確認したら、2 つ目の Visual Studio インスタンスを閉じ、アナライザー プロジェクトに戻ります。</span><span class="sxs-lookup"><span data-stu-id="112b5-163">Now that you've seen the initial analyzer in action, close the second Visual Studio instance and return to your analyzer project.</span></span>

<span data-ttu-id="112b5-164">アナライザーのすべての変更をテストするために、Visual Studio の 2 つ目のコピーを開始して、新しいコードを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="112b5-164">You don't have to start a second copy of Visual Studio and create new code to test every change in your analyzer.</span></span> <span data-ttu-id="112b5-165">このテンプレートを使用すると、単体テスト プロジェクトも自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-165">The template also creates a unit test project for you.</span></span> <span data-ttu-id="112b5-166">このプロジェクトには 2 つのテストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="112b5-166">That project contains two tests.</span></span> <span data-ttu-id="112b5-167">`TestMethod1` では、診断をトリガーせずにコードを分析するテストの一般的な形式が表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-167">`TestMethod1` shows the typical format of a test that analyzes code without triggering a diagnostic.</span></span> <span data-ttu-id="112b5-168">`TestMethod2` では、診断をトリガーするテストの形式が表示され、推奨されたコード修正が適用されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-168">`TestMethod2` shows the format of a test that triggers a diagnostic, and then applies a suggested code fix.</span></span> <span data-ttu-id="112b5-169">アナライザーとコード修正をビルドするときに、異なるコード構造のテストを作成して作業を検証します。</span><span class="sxs-lookup"><span data-stu-id="112b5-169">As you build your analyzer and code fix, you'll write tests for different code structures to verify your work.</span></span> <span data-ttu-id="112b5-170">アナライザーの単体テストは、Visual Studio を使用して対話的にテストするよりもはるかに簡単です。</span><span class="sxs-lookup"><span data-stu-id="112b5-170">Unit tests for analyzers are much quicker than testing them interactively with Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="112b5-171">アナライザーの単体テストは、アナライザーをトリガーするべきコード構造とトリガーするべきではないコード構造を知りたいときに最適なツールです。</span><span class="sxs-lookup"><span data-stu-id="112b5-171">Analyzer unit tests are a great tool when you know what code constructs should and shouldn't trigger your analyzer.</span></span> <span data-ttu-id="112b5-172">Visual Studio のもう 1 つのコピーにアナライザーを読み込むことは、まだ検討していない可能性のあるコンストラクトを探索して見つけるために最適なツールです。</span><span class="sxs-lookup"><span data-stu-id="112b5-172">Loading your analyzer in another copy of Visual Studio is a great tool to explore and find constructs you may not have thought about yet.</span></span>

## <a name="create-analyzer-registrations"></a><span data-ttu-id="112b5-173">アナライザーの登録を作成する</span><span class="sxs-lookup"><span data-stu-id="112b5-173">Create analyzer registrations</span></span>

<span data-ttu-id="112b5-174">このテンプレートを使用すると、**MakeConstAnalyzer.cs** ファイルに初期の `DiagnosticAnalyzer` クラスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-174">The template creates the initial `DiagnosticAnalyzer` class, in the **MakeConstAnalyzer.cs** file.</span></span> <span data-ttu-id="112b5-175">この初期のアナライザーは、あらゆるアナライザーが持つ 2 つの重要な特性を示しています。</span><span class="sxs-lookup"><span data-stu-id="112b5-175">This initial analyzer shows two important properties of every analyzer.</span></span>

- <span data-ttu-id="112b5-176">すべての診断アナライザーは、動作する言語を記述する `[DiagnosticAnalyzer]` 属性を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-176">Every diagnostic analyzer must provide a `[DiagnosticAnalyzer]` attribute that describes the language it operates on.</span></span>
- <span data-ttu-id="112b5-177">すべての診断アナライザーは、<xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> クラスから派生する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-177">Every diagnostic analyzer must derive from the <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer> class.</span></span>

<span data-ttu-id="112b5-178">このテンプレートは、アナライザーの一部である基本機能も示しています。</span><span class="sxs-lookup"><span data-stu-id="112b5-178">The template also shows the basic features that are part of any analyzer:</span></span>

1. <span data-ttu-id="112b5-179">アクションを登録します。</span><span class="sxs-lookup"><span data-stu-id="112b5-179">Register actions.</span></span> <span data-ttu-id="112b5-180">アクションは、アナライザーをトリガーしてコード違反を調べるコードの変更を表します。</span><span class="sxs-lookup"><span data-stu-id="112b5-180">The actions represent code changes that should trigger your analyzer to examine code for violations.</span></span> <span data-ttu-id="112b5-181">Visual Studio で、登録済みのアクションと一致するコード編集が検出されると、アナライザーの登録済みメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-181">When Visual Studio detects code edits that match a registered action, it calls your analyzer's registered method.</span></span>
1. <span data-ttu-id="112b5-182">診断を作成します。</span><span class="sxs-lookup"><span data-stu-id="112b5-182">Create diagnostics.</span></span> <span data-ttu-id="112b5-183">アナライザーで違反を検出されると、違反をユーザーに通知するために Visual Studio で使用される診断オブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-183">When your analyzer detects a violation, it creates a diagnostic object that Visual Studio uses to notify the user of the violation.</span></span>

<span data-ttu-id="112b5-184"><xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> メソッドのオーバーライドでアクションを登録します。</span><span class="sxs-lookup"><span data-stu-id="112b5-184">You register actions in your override of <xref:Microsoft.CodeAnalysis.Diagnostics.DiagnosticAnalyzer.Initialize(Microsoft.CodeAnalysis.Diagnostics.AnalysisContext)?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="112b5-185">このチュートリアルでは、**構文ノード**にアクセスしてローカル宣言を探し、定数値を持つものを調べます。</span><span class="sxs-lookup"><span data-stu-id="112b5-185">In this tutorial, you'll visit **syntax nodes** looking for local declarations, and see which of those have constant values.</span></span> <span data-ttu-id="112b5-186">宣言が定数であれば、アナライザーによって診断が作成され、報告されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-186">If a declaration could be constant, your analyzer will create and report a diagnostic.</span></span>

<span data-ttu-id="112b5-187">最初の手順は、登録定数が "Make Const" アナライザーを示すように、登録定数と `Initialize` メソッドを更新することです。</span><span class="sxs-lookup"><span data-stu-id="112b5-187">The first step is to update the registration constants and `Initialize` method so these constants indicate your "Make Const" analyzer.</span></span> <span data-ttu-id="112b5-188">ほとんどの文字列定数は、文字列リソース ファイルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="112b5-188">Most of the string constants are defined in the string resource file.</span></span> <span data-ttu-id="112b5-189">ローカリゼーションを容易にするには、この手法に従うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="112b5-189">You should follow that practice for easier localization.</span></span> <span data-ttu-id="112b5-190">**MakeConst** アナライザー プロジェクト用に **Resources.resx** ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="112b5-190">Open the **Resources.resx** file for the **MakeConst** analyzer project.</span></span> <span data-ttu-id="112b5-191">これでリソース エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-191">This displays the resource editor.</span></span> <span data-ttu-id="112b5-192">文字列リソースを次のように更新します。</span><span class="sxs-lookup"><span data-stu-id="112b5-192">Update the string resources as follows:</span></span>

- <span data-ttu-id="112b5-193">`AnalyzerTitle` を "変数を定数に変更できる" に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-193">Change `AnalyzerTitle` to "Variable can be made constant".</span></span>
- <span data-ttu-id="112b5-194">`AnalyzerMessageFormat` を "定数に変更できる" に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-194">Change `AnalyzerMessageFormat` to "Can be made constant".</span></span>
- <span data-ttu-id="112b5-195">`AnalyzerDescription` を "定数にする" に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-195">Change `AnalyzerDescription` to "Make Constant".</span></span>

<span data-ttu-id="112b5-196">また、 **[アクセス修飾子]** ドロップダウンを `public` に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-196">Also, change the **Access Modifier** drop-down to `public`.</span></span> <span data-ttu-id="112b5-197">こうすることで、単体テストでこれらの定数を簡単に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="112b5-197">That makes it easier to use these constants in unit tests.</span></span> <span data-ttu-id="112b5-198">完了すると、次の図のようにリソース エディターが表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-198">When you have finished, the resource editor should appear as follow figure shows:</span></span>

![文字列リソースを更新する](media/how-to-write-csharp-analyzer-code-fix/update-string-resources.png)

<span data-ttu-id="112b5-200">残りの変更はアナライザー ファイル内にあります。</span><span class="sxs-lookup"><span data-stu-id="112b5-200">The remaining changes are in the analyzer file.</span></span> <span data-ttu-id="112b5-201">Visual Studio で **MakeConstAnalyzer.cs** を開きます。</span><span class="sxs-lookup"><span data-stu-id="112b5-201">Open **MakeConstAnalyzer.cs** in Visual Studio.</span></span> <span data-ttu-id="112b5-202">登録済みアクションを、シンボル対して動作するものから構文に対して動作するものに変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-202">Change the registered action from one that acts on symbols to one that acts on syntax.</span></span> <span data-ttu-id="112b5-203">`MakeConstAnalyzerAnalyzer.Initialize` メソッドで、シンボルにアクションを登録する行を見つけます。</span><span class="sxs-lookup"><span data-stu-id="112b5-203">In the `MakeConstAnalyzerAnalyzer.Initialize` method, find the line that registers the action on symbols:</span></span>

```csharp
context.RegisterSymbolAction(AnalyzeSymbol, SymbolKind.NamedType);
```

<span data-ttu-id="112b5-204">これを次の行で置き換えます。</span><span class="sxs-lookup"><span data-stu-id="112b5-204">Replace it with the following line:</span></span>

[!code-csharp[Register the node action](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstAnalyzer.cs#RegisterNodeAction "Register a node action")]

<span data-ttu-id="112b5-205">この変更後は、`AnalyzeSymbol` メソッドを削除できます。</span><span class="sxs-lookup"><span data-stu-id="112b5-205">After that change, you can delete the `AnalyzeSymbol` method.</span></span> <span data-ttu-id="112b5-206">このアナライザーでは、<xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> ステートメントではなく <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType> ステートメントが検査されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-206">This analyzer examines <xref:Microsoft.CodeAnalysis.CSharp.SyntaxKind.LocalDeclarationStatement?displayProperty=nameWithType>, not <xref:Microsoft.CodeAnalysis.SymbolKind.NamedType?displayProperty=nameWithType> statements.</span></span> <span data-ttu-id="112b5-207">`AnalyzeNode` に赤い波線が表示されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="112b5-207">Notice that `AnalyzeNode` has red squiggles under it.</span></span> <span data-ttu-id="112b5-208">追加したコードは、宣言されていない `AnalyzeNode` メソッドを参照しています。</span><span class="sxs-lookup"><span data-stu-id="112b5-208">The code you just added references an `AnalyzeNode` method that hasn't been declared.</span></span> <span data-ttu-id="112b5-209">次のコードを使用してそのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="112b5-209">Declare that method using the following code:</span></span>

```csharp
private void AnalyzeNode(SyntaxNodeAnalysisContext context)
{
}
```

<span data-ttu-id="112b5-210">次のコードに示すように、**MakeConstAnalyzer.cs**  の `Category` を "Usage" に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-210">Change the `Category` to "Usage" in **MakeConstAnalyzer.cs** as shown in the following code:</span></span>

```csharp
private const string Category = "Usage";
```

## <a name="find-local-declarations-that-could-be-const"></a><span data-ttu-id="112b5-211">定数の可能性があるローカル宣言を見つける</span><span class="sxs-lookup"><span data-stu-id="112b5-211">Find local declarations that could be const</span></span>

<span data-ttu-id="112b5-212">次は `AnalyzeNode` メソッドの最初のバージョンを作成してみましょう。</span><span class="sxs-lookup"><span data-stu-id="112b5-212">It's time to write the first version of the `AnalyzeNode` method.</span></span> <span data-ttu-id="112b5-213">次のコードのように、`const` の可能性がありますが実際はそうではない単一のローカル宣言を探します。</span><span class="sxs-lookup"><span data-stu-id="112b5-213">It should look for a single local declaration that could be `const` but is not, like the following code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="112b5-214">最初の手順は、ローカル宣言を見つけることです。</span><span class="sxs-lookup"><span data-stu-id="112b5-214">The first step is to find local declarations.</span></span> <span data-ttu-id="112b5-215">**MakeConstAnalyzer.cs** の `AnalyzeNode` に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-215">Add the following code to `AnalyzeNode` in **MakeConstAnalyzer.cs**:</span></span>

```csharp
var localDeclaration = (LocalDeclarationStatementSyntax)context.Node;
```

<span data-ttu-id="112b5-216">アナライザーにローカル宣言 (ローカル宣言のみ) の変更が登録されているため、このキャストは常に成功します。</span><span class="sxs-lookup"><span data-stu-id="112b5-216">This cast always succeeds because your analyzer registered for changes to local declarations, and only local declarations.</span></span> <span data-ttu-id="112b5-217">他のノードの種類では `AnalyzeNode` メソッドへの呼び出しがトリガーされません。</span><span class="sxs-lookup"><span data-stu-id="112b5-217">No other node type triggers a call to your `AnalyzeNode` method.</span></span> <span data-ttu-id="112b5-218">次に、`const` 修飾子の宣言を確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-218">Next, check the declaration for any `const` modifiers.</span></span> <span data-ttu-id="112b5-219">見つかったら、すぐに戻ります。</span><span class="sxs-lookup"><span data-stu-id="112b5-219">If you find them, return immediately.</span></span> <span data-ttu-id="112b5-220">次のコードでは、ローカル宣言の `const` 修飾子を探します。</span><span class="sxs-lookup"><span data-stu-id="112b5-220">The following code looks for any `const` modifiers on the local declaration:</span></span>

```csharp
// make sure the declaration isn't already const:
if (localDeclaration.Modifiers.Any(SyntaxKind.ConstKeyword))
{
    return;
}
```

<span data-ttu-id="112b5-221">最後に、変数を `const` にすることができることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-221">Finally, you need to check that the variable could be `const`.</span></span> <span data-ttu-id="112b5-222">つまり、初期化後に決して割り当てられないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-222">That means making sure it is never assigned after it is initialized.</span></span>

<span data-ttu-id="112b5-223"><xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext> を使用していくつかのセマンティック解析を実行します。</span><span class="sxs-lookup"><span data-stu-id="112b5-223">You'll perform some semantic analysis using the <xref:Microsoft.CodeAnalysis.Diagnostics.SyntaxNodeAnalysisContext>.</span></span> <span data-ttu-id="112b5-224">`context` 引数を使用して、ローカル変数の宣言を `const` にすることができるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="112b5-224">You use the `context` argument to determine whether the local variable declaration can be made `const`.</span></span> <span data-ttu-id="112b5-225"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> は、単一のソース ファイル内のすべてのセマンティック情報を表します。</span><span class="sxs-lookup"><span data-stu-id="112b5-225">A <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> represents all of semantic information in a single source file.</span></span> <span data-ttu-id="112b5-226">詳細については、[セマンティック モデル](../work-with-semantics.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="112b5-226">You can learn more in the article that covers [semantic models](../work-with-semantics.md).</span></span> <span data-ttu-id="112b5-227"><xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> を使用して、ローカル宣言ステートメントでデータ フロー分析を実行します。</span><span class="sxs-lookup"><span data-stu-id="112b5-227">You'll use the <xref:Microsoft.CodeAnalysis.SemanticModel?displayProperty=nameWithType> to perform data flow analysis on the local declaration statement.</span></span> <span data-ttu-id="112b5-228">次に、このデータ フロー分析の結果を使用して、ローカル変数が他の場所の新しい値で上書きされないようにします。</span><span class="sxs-lookup"><span data-stu-id="112b5-228">Then, you use the results of this data flow analysis to ensure that the local variable isn't written with a new value anywhere else.</span></span> <span data-ttu-id="112b5-229">変数の <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> 拡張メソッドを呼び出して変数の <xref:Microsoft.CodeAnalysis.ILocalSymbol> を取得し、データ フロー分析の <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> コレクションに含まれていないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-229">Call the <xref:Microsoft.CodeAnalysis.ModelExtensions.GetDeclaredSymbol%2A> extension method to retrieve the <xref:Microsoft.CodeAnalysis.ILocalSymbol> for the variable and check that it isn't contained with the <xref:Microsoft.CodeAnalysis.DataFlowAnalysis.WrittenOutside%2A?displayProperty=nameWithType> collection of the data flow analysis.</span></span> <span data-ttu-id="112b5-230">`AnalyzeNode` メソッドの末尾に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-230">Add the following code to the end of the `AnalyzeNode` method:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="112b5-231">この追加したコードで、変数は変更されなくなります。そのため、`const` にすることができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-231">The code just added ensures that the variable isn't modified, and can therefore be made `const`.</span></span> <span data-ttu-id="112b5-232">それでは診断を呼び出してみましょう。</span><span class="sxs-lookup"><span data-stu-id="112b5-232">It's time to raise the diagnostic.</span></span> <span data-ttu-id="112b5-233">`AnalyzeNode` の最後の行に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-233">Add the following code as the last line in `AnalyzeNode`:</span></span>

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, context.Node.GetLocation()));
```

<span data-ttu-id="112b5-234"><kbd>F5</kbd> キーを押してアナライザーを実行して、進行状況を確認できます。</span><span class="sxs-lookup"><span data-stu-id="112b5-234">You can check your progress by pressing <kbd>F5</kbd> to run your analyzer.</span></span> <span data-ttu-id="112b5-235">以前に作成したコンソール アプリケーションを読み込み、次のテスト コードを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-235">You can load the console application you created earlier and then add the following test code:</span></span>

```csharp
int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="112b5-236">電球が表示され、アナライザーから診断が報告されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-236">The light bulb should appear, and your analyzer should report a diagnostic.</span></span> <span data-ttu-id="112b5-237">ただし、電球には、テンプレートで生成されたコード修正が使用されているので、大文字にすることができることがわかります。</span><span class="sxs-lookup"><span data-stu-id="112b5-237">However, the light bulb still uses the template generated code fix, and tells you it can be made upper case.</span></span> <span data-ttu-id="112b5-238">次のセクションでは、コード修正の記述方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="112b5-238">The next section explains how to write the code fix.</span></span>

## <a name="write-the-code-fix"></a><span data-ttu-id="112b5-239">コード修正を記述する</span><span class="sxs-lookup"><span data-stu-id="112b5-239">Write the code fix</span></span>

<span data-ttu-id="112b5-240">アナライザーで、1 つまたは複数のコード修正が表示される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-240">An analyzer can provide one or more code fixes.</span></span> <span data-ttu-id="112b5-241">コード修正では、報告された問題を解決する編集が定義されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-241">A code fix defines an edit that addresses the reported issue.</span></span> <span data-ttu-id="112b5-242">作成したアナライザーに、const キーワードを挿入するコード修正を用意することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-242">For the analyzer that you created, you can provide a code fix that inserts the const keyword:</span></span>

```csharp
const int x = 0;
Console.WriteLine(x);
```

<span data-ttu-id="112b5-243">エディターの電球の UI からユーザーが選択すると、Visual Studio によってコードが変更されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-243">The user chooses it from the light bulb UI in the editor and Visual Studio changes the code.</span></span>

<span data-ttu-id="112b5-244">テンプレートによって追加された **MakeConstCodeFixProvider.cs** ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="112b5-244">Open the **MakeConstCodeFixProvider.cs** file added by the template.</span></span>  <span data-ttu-id="112b5-245">このコード修正は、診断アナライザーによって生成された診断 ID に既に関連付けられていますが、まだ適切なコード変換が実装されていません。</span><span class="sxs-lookup"><span data-stu-id="112b5-245">This code fix is already wired up to the Diagnostic ID produced by your diagnostic analyzer, but it doesn't yet implement the right code transform.</span></span> <span data-ttu-id="112b5-246">まず、テンプレート コードの一部を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-246">First you should remove some of the template code.</span></span> <span data-ttu-id="112b5-247">タイトルの文字列を "定数にする" に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-247">Change the title string to "Make constant":</span></span>

[!code-csharp[Update the CodeFix title](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CodeFixTitle "Update the CodeFix title")]

<span data-ttu-id="112b5-248">次に `MakeUppercaseAsync` メソッドを削除します</span><span class="sxs-lookup"><span data-stu-id="112b5-248">Next, delete the `MakeUppercaseAsync` method.</span></span> <span data-ttu-id="112b5-249">これで適用されなくなります。</span><span class="sxs-lookup"><span data-stu-id="112b5-249">It no longer applies.</span></span>

<span data-ttu-id="112b5-250">すべてのコード修正プロバイダーは <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider> から派生します。</span><span class="sxs-lookup"><span data-stu-id="112b5-250">All code fix providers derive from <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider>.</span></span> <span data-ttu-id="112b5-251">これらはすべて <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> をオーバーライドし、使用できるコード修正を報告します。</span><span class="sxs-lookup"><span data-stu-id="112b5-251">They all override <xref:Microsoft.CodeAnalysis.CodeFixes.CodeFixProvider.RegisterCodeFixesAsync(Microsoft.CodeAnalysis.CodeFixes.CodeFixContext)?displayProperty=nameWithType> to report available code fixes.</span></span> <span data-ttu-id="112b5-252">`RegisterCodeFixesAsync` で、診断に合わせて、次のように検索している先祖ノードの種類を <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-252">In `RegisterCodeFixesAsync`, change the ancestor node type you're searching for to a <xref:Microsoft.CodeAnalysis.CSharp.Syntax.LocalDeclarationStatementSyntax> to match the diagnostic:</span></span>

[!code-csharp[Find local declaration node](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FindDeclarationNode  "Find the local declaration node that raised the diagnostic")]

<span data-ttu-id="112b5-253">次に、最後の行を変更してコード修正を登録します。</span><span class="sxs-lookup"><span data-stu-id="112b5-253">Next, change the last line to register a code fix.</span></span> <span data-ttu-id="112b5-254">この修正で、既存の宣言に `const` 修飾子を追加した結果の新しいドキュメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-254">Your fix will create a new document that results from adding the `const` modifier to an existing declaration:</span></span>

[!code-csharp[Register the new code fix](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#RegisterCodeFix  "Register the new code fix")]

<span data-ttu-id="112b5-255">シンボル `MakeConstAsync` に追加したコードに、赤い波線が表示されている点に注目してください。</span><span class="sxs-lookup"><span data-stu-id="112b5-255">You'll notice red squiggles in the code you just added on the symbol `MakeConstAsync`.</span></span> <span data-ttu-id="112b5-256">次のコードのように、`MakeConstAsync` の宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-256">Add a declaration for `MakeConstAsync` like the following code:</span></span>

```csharp
private async Task<Document> MakeConstAsync(Document document,
   LocalDeclarationStatementSyntax localDeclaration,
   CancellationToken cancellationToken)
{
}
```

<span data-ttu-id="112b5-257">新しい `MakeConstAsync` メソッドによって、ユーザーのソース ファイルを表す <xref:Microsoft.CodeAnalysis.Document> は、`const` 宣言を含む新しい <xref:Microsoft.CodeAnalysis.Document> に変換されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-257">Your new `MakeConstAsync` method will transform the <xref:Microsoft.CodeAnalysis.Document> representing the user's source file into a new <xref:Microsoft.CodeAnalysis.Document> that now contains a `const` declaration.</span></span>

<span data-ttu-id="112b5-258">宣言ステートメントの前に挿入される新しい `const` キーワード トークンを作成します。</span><span class="sxs-lookup"><span data-stu-id="112b5-258">You create a new `const` keyword token to insert at the front of the declaration statement.</span></span> <span data-ttu-id="112b5-259">先頭に trivia があれば、まず宣言ステートメントの最初のトークンから削除し、それを `const` トークンにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="112b5-259">Be careful to first remove any leading trivia from the first token of the declaration statement and attach it to the `const` token.</span></span> <span data-ttu-id="112b5-260">`MakeConstAsync` メソッドに次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-260">Add the following code to the `MakeConstAsync` method:</span></span>

[!code-csharp[Create a new const keyword token](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#CreateConstToken  "Create the new const keyword token")]

<span data-ttu-id="112b5-261">次に、以下のコードを使用して宣言に `const` トークンを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-261">Next, add the `const` token to the declaration using the following code:</span></span>

```csharp
// Insert the const token into the modifiers list, creating a new modifiers list.
var newModifiers = trimmedLocal.Modifiers.Insert(0, constToken);
// Produce the new local declaration.
var newLocal = trimmedLocal
    .WithModifiers(newModifiers)
    .WithDeclaration(localDeclaration.Declaration);
```

<span data-ttu-id="112b5-262">次に、C# の書式設定規則に合わせて新しい宣言の書式を設定します。</span><span class="sxs-lookup"><span data-stu-id="112b5-262">Next, format the new declaration to match C# formatting rules.</span></span> <span data-ttu-id="112b5-263">既存のコードに合わせて変更の書式を設定すると、エクスペリエンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="112b5-263">Formatting your changes to match existing code creates a better experience.</span></span> <span data-ttu-id="112b5-264">既存のコードの直後に次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-264">Add the following statement immediately after the existing code:</span></span>

[!code-csharp[Format the new declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#FormatLocal  "Format the new declaration")]

<span data-ttu-id="112b5-265">このコード用に新しい名前空間が必要です。</span><span class="sxs-lookup"><span data-stu-id="112b5-265">A new namespace is required for this code.</span></span> <span data-ttu-id="112b5-266">次の `using` ディレクティブをファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-266">Add the following `using` directive to the top of the file:</span></span>

```csharp
using Microsoft.CodeAnalysis.Formatting;
```

<span data-ttu-id="112b5-267">最後の手順は編集です。</span><span class="sxs-lookup"><span data-stu-id="112b5-267">The final step is to make your edit.</span></span> <span data-ttu-id="112b5-268">このプロセスには 3 つの手順があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-268">There are three steps to this process:</span></span>

1. <span data-ttu-id="112b5-269">既存のドキュメントのハンドルを取得する。</span><span class="sxs-lookup"><span data-stu-id="112b5-269">Get a handle to the existing document.</span></span>
1. <span data-ttu-id="112b5-270">既存の宣言を新しい宣言で置き換えて、新しいドキュメントを作成する。</span><span class="sxs-lookup"><span data-stu-id="112b5-270">Create a new document by replacing the existing declaration with the new declaration.</span></span>
1. <span data-ttu-id="112b5-271">新しいドキュメントを返す。</span><span class="sxs-lookup"><span data-stu-id="112b5-271">Return the new document.</span></span>

<span data-ttu-id="112b5-272">`MakeConstAsync` メソッドの末尾に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-272">Add the following code to the end of the `MakeConstAsync` method:</span></span>

[!code-csharp[replace the declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceDocument  "Generate a new document by replacing the declaration")]

<span data-ttu-id="112b5-273">コード修正を試す準備が整いました。</span><span class="sxs-lookup"><span data-stu-id="112b5-273">Your code fix is ready to try.</span></span>  <span data-ttu-id="112b5-274"><kbd>F5</kbd> キーを押して、Visual Studio の 2 つ目のインスタンスでアナライザー プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="112b5-274">Press <kbd>F5</kbd> to run the analyzer project in a second instance of Visual Studio.</span></span> <span data-ttu-id="112b5-275">2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成し、定数値を使用して初期化されたローカル変数宣言をいくつか Main メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-275">In the second Visual Studio instance, create a new C# Console Application project and add a few local variable declarations initialized with constant values to the Main method.</span></span> <span data-ttu-id="112b5-276">次のように警告として報告されることがわかります。</span><span class="sxs-lookup"><span data-stu-id="112b5-276">You'll see that they are reported as warnings as below.</span></span>

![const 警告を生成できる](media/how-to-write-csharp-analyzer-code-fix/make-const-warning.png)

<span data-ttu-id="112b5-278">ここでは、さまざまな作業を行いました。</span><span class="sxs-lookup"><span data-stu-id="112b5-278">You've made a lot of progress.</span></span> <span data-ttu-id="112b5-279">`const` にすることができる宣言には、波線が表示されています。</span><span class="sxs-lookup"><span data-stu-id="112b5-279">There are squiggles under the declarations that can be made `const`.</span></span> <span data-ttu-id="112b5-280">ただし、まだするべきことがあります。</span><span class="sxs-lookup"><span data-stu-id="112b5-280">But there is still work to do.</span></span> <span data-ttu-id="112b5-281">これは、`i` で始まる宣言に `const` を追加し、次に `j` を追加し、最後に `k` を追加して改善することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-281">This works fine if you add `const` to the declarations starting with `i`, then `j` and finally `k`.</span></span> <span data-ttu-id="112b5-282">ただし、`k` で始まる `const` 修飾子を異なる順序で追加すると、アナライザーによってエラーが生成されます。`i` と `j` の両方が既に `const` でなければ、`k` を `const` と宣言できません。</span><span class="sxs-lookup"><span data-stu-id="112b5-282">But, if you add the `const` modifier in a different order, starting with `k`, your analyzer creates errors: `k` can't be declared `const`, unless `i` and `j` are both already `const`.</span></span> <span data-ttu-id="112b5-283">変数を宣言して初期化できるさまざまな方法を確実に処理できるように、さらに分析を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-283">You've got to do more analysis to ensure you handle the different ways variables can be declared and initialized.</span></span>

## <a name="build-data-driven-tests"></a><span data-ttu-id="112b5-284">データ駆動型テストをビルドする</span><span class="sxs-lookup"><span data-stu-id="112b5-284">Build data driven tests</span></span>

<span data-ttu-id="112b5-285">アナライザーとコード修正は、const にすることができる単一の宣言という単純なケースで動作します。</span><span class="sxs-lookup"><span data-stu-id="112b5-285">Your analyzer and code fix work on a simple case of a single declaration that can be made const.</span></span> <span data-ttu-id="112b5-286">この実装によって間違いが発生する可能性のある宣言ステートメントは数多くあります。</span><span class="sxs-lookup"><span data-stu-id="112b5-286">There are numerous possible declaration statements where this implementation makes mistakes.</span></span> <span data-ttu-id="112b5-287">このようなケースには、テンプレートによって作成される単体テスト ライブラリを使用して対処します。</span><span class="sxs-lookup"><span data-stu-id="112b5-287">You'll address these cases by working with the unit test library written by the template.</span></span> <span data-ttu-id="112b5-288">これは、Visual Studio の 2 つ目のコピーを繰り返し開くよりもはるかに高速です。</span><span class="sxs-lookup"><span data-stu-id="112b5-288">It's much faster than repeatedly opening a second copy of Visual Studio.</span></span>

<span data-ttu-id="112b5-289">単体テスト プロジェクトで **MakeConstUnitTests.cs** ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="112b5-289">Open the **MakeConstUnitTests.cs** file in the unit test project.</span></span> <span data-ttu-id="112b5-290">テンプレートによって、アナライザーとコード修正の単体テスト用に 2 つの共通パターンに従う 2 つのテストが作成されています。</span><span class="sxs-lookup"><span data-stu-id="112b5-290">The template created two tests that follow the two common patterns for an analyzer and code fix unit test.</span></span> <span data-ttu-id="112b5-291">`TestMethod1` は、診断を報告すべきではないときに、アナライザーから診断が報告されないようにするテストのパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="112b5-291">`TestMethod1` shows the pattern for a test that ensures the analyzer doesn't report a diagnostic when it shouldn't.</span></span> <span data-ttu-id="112b5-292">`TestMethod2` は、診断を報告し、コード修正を実行するためのパターンを示します。</span><span class="sxs-lookup"><span data-stu-id="112b5-292">`TestMethod2` shows the pattern for reporting a diagnostic and running the code fix.</span></span>

<span data-ttu-id="112b5-293">アナライザーのほぼすべてのテストのコードは、この 2 つのパターンのいずれかに従います。</span><span class="sxs-lookup"><span data-stu-id="112b5-293">The code for almost every test for your analyzer follows one of these two patterns.</span></span> <span data-ttu-id="112b5-294">1 つ目の手順では、これらのテストをデータ駆動型テストとして修正することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-294">For the first step, you can rework these tests as data driven tests.</span></span> <span data-ttu-id="112b5-295">次に、さまざまなテスト入力を表す新しい文字列定数を追加することで、新しいテストを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="112b5-295">Then, it will be easy to create new tests by adding new string constants to represent different test inputs.</span></span>

<span data-ttu-id="112b5-296">効率化するには、1 つ目の手順を 2 つのテストをデータ駆動型テストにリファクターします。</span><span class="sxs-lookup"><span data-stu-id="112b5-296">For efficiency, the first step is to refactor the two tests into data driven tests.</span></span> <span data-ttu-id="112b5-297">すると、必要な作業は、新しいテストのたびに、いくつかの文字列定数を定義するだけになります。</span><span class="sxs-lookup"><span data-stu-id="112b5-297">Then, you only need to define a couple string constants for each new test.</span></span> <span data-ttu-id="112b5-298">リファクター時に、両方のメソッドをわかりやすい名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="112b5-298">While you are refactoring, rename both methods to better names.</span></span> <span data-ttu-id="112b5-299">診断が呼び出されないように、`TestMethod1` をこのテストに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="112b5-299">Replace `TestMethod1` with this test that ensures no diagnostic is raised:</span></span>

```csharp
[DataTestMethod]
[DataRow("")]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
{
    VerifyCSharpDiagnostic(testCode);
}
```

<span data-ttu-id="112b5-300">診断で警告がトリガーされないようにするコード フラグメントすることで、このテスト用に新しいデータ行を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-300">You can create a new data row for this test by defining any code fragment that should not cause your diagnostic to trigger a warning.</span></span> <span data-ttu-id="112b5-301">ソース コード フラグメントに対してトリガーされる診断がない場合、`VerifyCSharpDiagnostic` のこのオーバーロードは成功します。</span><span class="sxs-lookup"><span data-stu-id="112b5-301">This overload of `VerifyCSharpDiagnostic` passes when there are no diagnostics triggered for the source code fragment.</span></span>

<span data-ttu-id="112b5-302">次に、`TestMethod2` をこのテストに置き換えて、診断を呼び出し、ソース コード フラグメントに対してコード修正を適用するようにします。</span><span class="sxs-lookup"><span data-stu-id="112b5-302">Next, replace `TestMethod2` with this test that ensures a diagnostic is raised and a code fix applied for the source code fragment:</span></span>

```csharp
[DataTestMethod]
[DataRow(LocalIntCouldBeConstant, LocalIntCouldBeConstantFixed, 10, 13)]
public void WhenDiagnosticIsRaisedFixUpdatesCode(
    string test,
    string fixTest,
    int line,
    int column)
{
    var expected = new DiagnosticResult
    {
        Id = MakeConstAnalyzer.DiagnosticId,
        Message = new LocalizableResourceString(nameof(MakeConst.Resources.AnalyzerMessageFormat), MakeConst.Resources.ResourceManager, typeof(MakeConst.Resources)).ToString(),
        Severity = DiagnosticSeverity.Warning,
        Locations =
            new[] {
                    new DiagnosticResultLocation("Test0.cs", line, column)
                }
    };

    VerifyCSharpDiagnostic(test, expected);

    VerifyCSharpFix(test, fixTest);
}
```

<span data-ttu-id="112b5-303">また、前のコードでは、想定される診断結果を構築する変更をいくつかコードに加えました。</span><span class="sxs-lookup"><span data-stu-id="112b5-303">The preceding code also made a couple changes to the code that builds the expected diagnostic result.</span></span> <span data-ttu-id="112b5-304">これには `MakeConst` アナライザーに登録されたパブリック定数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-304">It uses the public constants registered in the `MakeConst` analyzer.</span></span> <span data-ttu-id="112b5-305">さらに、入力ソースと修正済みソース用に 2 つの文字列定数が使用されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-305">In addition, it uses two string constants for the input and fixed source.</span></span> <span data-ttu-id="112b5-306">`UnitTest` クラスに次の文字列定数を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-306">Add the following string constants to the `UnitTest` class:</span></span>

[!code-csharp[string constants for fix test](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FirstFixTest "string constants for fix test")]

<span data-ttu-id="112b5-307">これらの 2 つのテストを実行して、合格することを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-307">Run these two tests to make sure they pass.</span></span> <span data-ttu-id="112b5-308">Visual Studio で、 **[テスト]**  >  **[Windows]**  >  **[テスト エクスプローラー]** の順に選択して、**テスト エクスプローラー**を開きます。</span><span class="sxs-lookup"><span data-stu-id="112b5-308">In Visual Studio, open the **Test Explorer** by selecting **Test** > **Windows** > **Test Explorer**.</span></span> <span data-ttu-id="112b5-309">次に、 **[すべて実行]** リンクを選択します。</span><span class="sxs-lookup"><span data-stu-id="112b5-309">Then select the **Run All** link.</span></span>

## <a name="create-tests-for-valid-declarations"></a><span data-ttu-id="112b5-310">有効な宣言のテストを作成する</span><span class="sxs-lookup"><span data-stu-id="112b5-310">Create tests for valid declarations</span></span>

<span data-ttu-id="112b5-311">一般的な規則として、アナライザーはできるだけ早く終了し、最低限の作業を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-311">As a general rule, analyzers should exit as quickly as possible, doing minimal work.</span></span> <span data-ttu-id="112b5-312">ユーザーがコードを編集すると、Visual Studio では登録済みのアナライザーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-312">Visual Studio calls registered analyzers as the user edits code.</span></span> <span data-ttu-id="112b5-313">応答性は重要な要件です。</span><span class="sxs-lookup"><span data-stu-id="112b5-313">Responsiveness is a key requirement.</span></span> <span data-ttu-id="112b5-314">診断を呼び出すべきではないコードのテストケースがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="112b5-314">There are several test cases for code that should not raise your diagnostic.</span></span> <span data-ttu-id="112b5-315">このアナライザーは、このようなテストのうち、初期化後に変数が割り当てられるケースのテストを既に処理しています。</span><span class="sxs-lookup"><span data-stu-id="112b5-315">Your analyzer already handles one of those tests, the case where a variable is assigned after being initialized.</span></span> <span data-ttu-id="112b5-316">そのケースを表すために、テストに次の文字列定数を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-316">Add the following string constant to your tests to represent that case:</span></span>

[!code-csharp[variable assigned](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VariableAssigned "a variable that is assigned after being initialized won't raise the diagnostic")]

<span data-ttu-id="112b5-317">次に、以下のスニペットに示すように、このテストのデータ行を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-317">Then, add a data row for this test as shown in the snippet below:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
 DataRow(VariableAssigned)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="112b5-318">このテストも合格します。</span><span class="sxs-lookup"><span data-stu-id="112b5-318">This test passes as well.</span></span> <span data-ttu-id="112b5-319">次に、まだ処理していない条件の定数を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-319">Next, add constants for conditions you haven't handled yet:</span></span>

- <span data-ttu-id="112b5-320">既に const なので、既に `const` である宣言:</span><span class="sxs-lookup"><span data-stu-id="112b5-320">Declarations that are already `const`, because they are already const:</span></span>

   [!code-csharp[already const declaration](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#AlreadyConst "a declaration that is already const should not raise the diagnostic")]

- <span data-ttu-id="112b5-321">使用する価値がないため、初期化子がない宣言:</span><span class="sxs-lookup"><span data-stu-id="112b5-321">Declarations that have no initializer, because there is no value to use:</span></span>

   [!code-csharp[declarations that have no initializer](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#NoInitializer "a declaration that has no initializer should not raise the diagnostic")]

- <span data-ttu-id="112b5-322">コンパイル時の定数にすることはできないため、初期化子が定数ではない宣言:</span><span class="sxs-lookup"><span data-stu-id="112b5-322">Declarations where the initializer is not a constant, because they can't be compile-time constants:</span></span>

   [!code-csharp[declarations where the initializer isn't const](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#InitializerNotConstant "a declaration where the initializer is not a compile-time constant should not raise the diagnostic")]

<span data-ttu-id="112b5-323">C# は複数の宣言を 1 つのステートメントとして許可するので、さらに複雑になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-323">It can be even more complicated because C# allows multiple declarations as one statement.</span></span> <span data-ttu-id="112b5-324">次のテスト ケース文字列定数を考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="112b5-324">Consider the following test case string constant:</span></span>

[!code-csharp[multiple initializers](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#MultipleInitializers "A declaration can be made constant only if all variables in that statement can be made constant")]

<span data-ttu-id="112b5-325">変数 `i` は定数にすることができますが、変数 `j` はできません。</span><span class="sxs-lookup"><span data-stu-id="112b5-325">The variable `i` can be made constant, but the variable `j` cannot.</span></span> <span data-ttu-id="112b5-326">そのため、このステートメントを const 宣言にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="112b5-326">Therefore, this statement cannot be made a const declaration.</span></span> <span data-ttu-id="112b5-327">これらすべてのテストについて `DataRow` 宣言を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-327">Add the `DataRow` declarations for all these tests:</span></span>

```csharp
[DataTestMethod]
[DataRow(""),
    DataRow(VariableAssigned),
    DataRow(AlreadyConst),
    DataRow(NoInitializer),
    DataRow(InitializerNotConstant),
    DataRow(MultipleInitializers)]
public void WhenTestCodeIsValidNoDiagnosticIsTriggered(string testCode)
```

<span data-ttu-id="112b5-328">テストをもう一度実行すると、これらの新しいテスト ケースが失敗することがわかります。</span><span class="sxs-lookup"><span data-stu-id="112b5-328">Run your tests again, and you'll see these new test cases fail.</span></span>

## <a name="update-your-analyzer-to-ignore-correct-declarations"></a><span data-ttu-id="112b5-329">正しい宣言を無視するようにアナライザーを更新する</span><span class="sxs-lookup"><span data-stu-id="112b5-329">Update your analyzer to ignore correct declarations</span></span>

<span data-ttu-id="112b5-330">アナライザーの `AnalyzeNode` メソッドにいくつか拡張を追加して、これらの条件に一致するコードをフィルター処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-330">You need some enhancements to your analyzer's `AnalyzeNode` method to filter out code that matches these conditions.</span></span> <span data-ttu-id="112b5-331">これらはすべて関連する条件なので、同様の変更でこれらすべての条件を修正します。</span><span class="sxs-lookup"><span data-stu-id="112b5-331">They are all related conditions, so similar changes will fix all these conditions.</span></span> <span data-ttu-id="112b5-332">`AnalyzeNode` に次の変更を加えます。</span><span class="sxs-lookup"><span data-stu-id="112b5-332">Make the following changes to `AnalyzeNode`:</span></span>

- <span data-ttu-id="112b5-333">セマンティック分析では、単一の変数宣言を調査しました。</span><span class="sxs-lookup"><span data-stu-id="112b5-333">Your semantic analysis examined a single variable declaration.</span></span> <span data-ttu-id="112b5-334">このコードは、同じステートメントで宣言されたすべての変数を調査する `foreach` ループ内に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-334">This code needs to be in a `foreach` loop that examines all the variables declared in the same statement.</span></span>
- <span data-ttu-id="112b5-335">宣言された各変数には初期化子が必要です。</span><span class="sxs-lookup"><span data-stu-id="112b5-335">Each declared variable needs to have an initializer.</span></span>
- <span data-ttu-id="112b5-336">宣言された各変数の初期化子は、コンパイル時定数にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-336">Each declared variable's initializer must be a compile-time constant.</span></span>

<span data-ttu-id="112b5-337">`AnalyzeNode` メソッドで、元のセマンティック分析を置き換えます。</span><span class="sxs-lookup"><span data-stu-id="112b5-337">In your `AnalyzeNode` method, replace the original semantic analysis:</span></span>

```csharp
// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

// Retrieve the local symbol for each variable in the local declaration
// and ensure that it is not written outside of the data flow analysis region.
var variable = localDeclaration.Declaration.Variables.Single();
var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
{
    return;
}
```

<span data-ttu-id="112b5-338">次のコード スニペットのようにします。</span><span class="sxs-lookup"><span data-stu-id="112b5-338">with the following code snippet:</span></span>

```csharp
// Ensure that all variables in the local declaration have initializers that
// are assigned with constant values.
foreach (var variable in localDeclaration.Declaration.Variables)
{
    var initializer = variable.Initializer;
    if (initializer == null)
    {
        return;
    }

    var constantValue = context.SemanticModel.GetConstantValue(initializer.Value);
    if (!constantValue.HasValue)
    {
        return;
    }
}

// Perform data flow analysis on the local declaration.
var dataFlowAnalysis = context.SemanticModel.AnalyzeDataFlow(localDeclaration);

foreach (var variable in localDeclaration.Declaration.Variables)
{
    // Retrieve the local symbol for each variable in the local declaration
    // and ensure that it is not written outside of the data flow analysis region.
    var variableSymbol = context.SemanticModel.GetDeclaredSymbol(variable);
    if (dataFlowAnalysis.WrittenOutside.Contains(variableSymbol))
    {
        return;
    }
}
```

<span data-ttu-id="112b5-339">最初の `foreach` ループで、構文解析を使用して各変数宣言を調査します。</span><span class="sxs-lookup"><span data-stu-id="112b5-339">The first `foreach` loop examines each variable declaration using syntactic analysis.</span></span> <span data-ttu-id="112b5-340">最初の検査で、変数に初期化子があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-340">The first check guarantees that the variable has an initializer.</span></span> <span data-ttu-id="112b5-341">2 つ目の検査で、初期化子が定数であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-341">The second check guarantees that the initializer is a constant.</span></span> <span data-ttu-id="112b5-342">2 つ目のループには、元のセマンティック分析があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-342">The second loop has the original semantic analysis.</span></span> <span data-ttu-id="112b5-343">セマンティック検査は、パフォーマンスに大きな影響があるため、別のループに配置されています。</span><span class="sxs-lookup"><span data-stu-id="112b5-343">The semantic checks are in a separate loop because it has a greater impact on performance.</span></span> <span data-ttu-id="112b5-344">テストをもう一度実行すると、すべてが合格になるはずです。</span><span class="sxs-lookup"><span data-stu-id="112b5-344">Run your tests again, and you should see them all pass.</span></span>

## <a name="add-the-final-polish"></a><span data-ttu-id="112b5-345">最後の仕上げを加える</span><span class="sxs-lookup"><span data-stu-id="112b5-345">Add the final polish</span></span>

<span data-ttu-id="112b5-346">完了までもう少しです。</span><span class="sxs-lookup"><span data-stu-id="112b5-346">You're almost done.</span></span> <span data-ttu-id="112b5-347">アナライザーが処理できる条件がまだいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="112b5-347">There are a few more conditions for your analyzer to handle.</span></span> <span data-ttu-id="112b5-348">Visual Studio では、ユーザーがコードを記述しているときにアナライザーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-348">Visual Studio calls analyzers while the user is writing code.</span></span> <span data-ttu-id="112b5-349">コンパイルされないコードに対してアナライザーが呼び出されることはよくあります。</span><span class="sxs-lookup"><span data-stu-id="112b5-349">It's often the case that your analyzer will be called for code that doesn't compile.</span></span> <span data-ttu-id="112b5-350">診断アナライザーの `AnalyzeNode` メソッドは、定数値を変数型に変換できるかどうかを検査しません。</span><span class="sxs-lookup"><span data-stu-id="112b5-350">The diagnostic analyzer's `AnalyzeNode` method does not check to see if the constant value is convertible to the variable type.</span></span> <span data-ttu-id="112b5-351">そのため、現在の実装では、int i = "abc" のような正しくない宣言でもそのままローカル定数に変換されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-351">So, the current implementation will happily convert an incorrect declaration such as int i = "abc"' to a local constant.</span></span> <span data-ttu-id="112b5-352">このような条件に対して次のソース文字列定数を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-352">Add a source string constant for that condition:</span></span>

[!code-csharp[Mismatched types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsInvalid "When the variable type and the constant type don't match, there's no diagnostic")]

<span data-ttu-id="112b5-353">また、参照型が正しく処理されません。</span><span class="sxs-lookup"><span data-stu-id="112b5-353">In addition, reference types are not handled properly.</span></span> <span data-ttu-id="112b5-354">参照型に使用できる唯一の定数値は、文字列リテラルを許可する <xref:System.String?displayProperty=nameWithType> の場合を除き、`null` です。</span><span class="sxs-lookup"><span data-stu-id="112b5-354">The only constant value allowed for a reference type is `null`, except in this case of <xref:System.String?displayProperty=nameWithType>, which allows string literals.</span></span> <span data-ttu-id="112b5-355">つまり、`const string s = "abc"` は有効ですが、`const object s = "abc"` は有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="112b5-355">In other words, `const string s = "abc"` is legal, but `const object s = "abc"` is not.</span></span> <span data-ttu-id="112b5-356">このコード スニペットで、次の条件を検証します。</span><span class="sxs-lookup"><span data-stu-id="112b5-356">This code snippet verifies that condition:</span></span>

[!code-csharp[Reference types don't raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#DeclarationIsntString "When the variable type is a reference type other than string, there's no diagnostic")]

<span data-ttu-id="112b5-357">さらに徹底するには、文字列の定数宣言を作成できるように別のテストを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-357">To be thorough, you need to add another test to make sure that you can create a constant declaration for a string.</span></span> <span data-ttu-id="112b5-358">次のスニペットでは、診断を呼び出すコードと、修正が適用された後のコードの両方を定義しています。</span><span class="sxs-lookup"><span data-stu-id="112b5-358">The following snippet defines both the code that raises the diagnostic, and the code after the fix has been applied:</span></span>

[!code-csharp[string reference types raise diagnostics](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#ConstantIsString "When the variable type is string, it can be constant")]

<span data-ttu-id="112b5-359">最後に、変数が `var` キーワードで宣言されている場合、コード修正で適切な処理が実行されず、C# 言語でサポートされていない `const var` 宣言が生成されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-359">Finally, if a variable is declared with the `var` keyword, the code fix does the wrong thing and generates a `const var` declaration, which is not supported by the C# language.</span></span> <span data-ttu-id="112b5-360">このバグを修正するには、コード修正で `var` キーワードを推定型の名前に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-360">To fix this bug, the code fix must replace the `var` keyword with the inferred type's name:</span></span>

[!code-csharp[var references need to use the inferred types](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#VarDeclarations "Declarations made using var must have the type replaced with the inferred type")]

<span data-ttu-id="112b5-361">これらの変更で、両方のテストのデータ行の宣言が更新されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-361">These changes update the data row declarations for both tests.</span></span> <span data-ttu-id="112b5-362">次のコードは、すべてのデータ行の属性を使用したこれらのテストを示しています。</span><span class="sxs-lookup"><span data-stu-id="112b5-362">The following code shows these tests with all data row attributes:</span></span>

[!code-csharp[The finished tests](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst.Test/MakeConstUnitTests.cs#FinishedTests "The finished tests for the make const analyzer")]

<span data-ttu-id="112b5-363">幸いにも、上記のすべてのバグは、ここで学んだテクニックを使って解決できます。</span><span class="sxs-lookup"><span data-stu-id="112b5-363">Fortunately, all of the above bugs can be addressed using the same techniques that you just learned.</span></span>

<span data-ttu-id="112b5-364">最初のバグを修正するには、まず **DiagnosticAnalyzer.cs** を開き、各ローカル宣言の初期化子が検査される foreach ループを見つけて、それらに定数値が割り当てられていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-364">To fix the first bug, first open **DiagnosticAnalyzer.cs** and locate the foreach loop where each of the local declaration's initializers are checked to ensure that they're assigned with constant values.</span></span> <span data-ttu-id="112b5-365">最初の foreach ループの_直前_に `context.SemanticModel.GetTypeInfo()` を呼び出し、宣言されたローカル宣言の型に関する詳細情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="112b5-365">Immediately _before_ the first foreach loop, call `context.SemanticModel.GetTypeInfo()` to retrieve detailed information about the declared type of the local declaration:</span></span>

```csharp
var variableTypeName = localDeclaration.Declaration.Type;
var variableType = context.SemanticModel.GetTypeInfo(variableTypeName).ConvertedType;
```

<span data-ttu-id="112b5-366">次に、`foreach` ループ内に、各初期化子が変数型に変換できることを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-366">Then, inside your `foreach` loop, check each initializer to make sure it's convertible to the variable type.</span></span> <span data-ttu-id="112b5-367">初期化子が定数であることを確認したら、次の検査を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-367">Add the following check after ensuring that the initializer is a constant:</span></span>

```csharp
// Ensure that the initializer value can be converted to the type of the
// local declaration without a user-defined conversion.
var conversion = context.SemanticModel.ClassifyConversion(initializer.Value, variableType);
if (!conversion.Exists || conversion.IsUserDefined)
{
    return;
}
```

<span data-ttu-id="112b5-368">次の変更は、最後の変更に基づいています。</span><span class="sxs-lookup"><span data-stu-id="112b5-368">The next change builds upon the last one.</span></span> <span data-ttu-id="112b5-369">最初の foreach ループの中かっこの前に、定数が文字列または null の場合にローカル宣言の型を検査する次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-369">Before the closing curly brace of the first foreach loop, add the following code to check the type of the local declaration when the constant is a string or null.</span></span>

```csharp
// Special cases:
//  * If the constant value is a string, the type of the local declaration
//    must be System.String.
//  * If the constant value is null, the type of the local declaration must
//    be a reference type.
if (constantValue.Value is string)
{
    if (variableType.SpecialType != SpecialType.System_String)
    {
        return;
    }
}
else if (variableType.IsReferenceType && constantValue.Value != null)
{
    return;
}
```

<span data-ttu-id="112b5-370">var' キーワードを正しい型名に置き換えるには、コード修正プロバイダーに少しコードを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-370">You must write a bit more code in your code fix provider to replace the var' keyword with the correct type name.</span></span> <span data-ttu-id="112b5-371">**CodeFixProvider.cs** に戻ります。</span><span class="sxs-lookup"><span data-stu-id="112b5-371">Return to **CodeFixProvider.cs**.</span></span> <span data-ttu-id="112b5-372">追加するコードで、次の手順が実行されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-372">The code you'll add does the following steps:</span></span>

- <span data-ttu-id="112b5-373">宣言が `var` 宣言かどうかを検査し、その場合は次の処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="112b5-373">Check if the declaration is a `var` declaration, and if it is:</span></span>
- <span data-ttu-id="112b5-374">推定型の新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="112b5-374">Create a new type for the inferred type.</span></span>
- <span data-ttu-id="112b5-375">型宣言がエイリアスでないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-375">Make sure the type declaration is not an alias.</span></span> <span data-ttu-id="112b5-376">その場合は、`const var` を宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-376">If so, it is legal to declare `const var`.</span></span>
- <span data-ttu-id="112b5-377">`var` がこのプログラムの型名でないことを確認します</span><span class="sxs-lookup"><span data-stu-id="112b5-377">Make sure that `var` isn't a type name in this program.</span></span> <span data-ttu-id="112b5-378">(その場合、`const var` は有効です)。</span><span class="sxs-lookup"><span data-stu-id="112b5-378">(If so, `const var` is legal).</span></span>
- <span data-ttu-id="112b5-379">完全な型名を簡略化する</span><span class="sxs-lookup"><span data-stu-id="112b5-379">Simplify the full type name</span></span>

<span data-ttu-id="112b5-380">多数のコードが必要なようですが、</span><span class="sxs-lookup"><span data-stu-id="112b5-380">That sounds like a lot of code.</span></span> <span data-ttu-id="112b5-381">そうではありません。</span><span class="sxs-lookup"><span data-stu-id="112b5-381">It's not.</span></span> <span data-ttu-id="112b5-382">`newLocal` を宣言し、初期化する行を次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="112b5-382">Replace the line that declares and initializes `newLocal` with the following code.</span></span> <span data-ttu-id="112b5-383">`newModifiers` の初期化直後に配置します。</span><span class="sxs-lookup"><span data-stu-id="112b5-383">It goes immediately after the initialization of `newModifiers`:</span></span>

[!code-csharp[Replace Var designations](~/samples/snippets/csharp/roslyn-sdk/Tutorials/MakeConst/MakeConst/MakeConstCodeFixProvider.cs#ReplaceVar "Replace a var designation with the explicit type")]

<span data-ttu-id="112b5-384"><xref:Microsoft.CodeAnalysis.Simplification.Simplifier> 型を使用するには、1 つの `using` ディレクティブを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="112b5-384">You'll need to add one `using` directive to use the <xref:Microsoft.CodeAnalysis.Simplification.Simplifier> type:</span></span>

```csharp
using Microsoft.CodeAnalysis.Simplification;
```

<span data-ttu-id="112b5-385">テストを実行します。テストはすべて合格するはずです。</span><span class="sxs-lookup"><span data-stu-id="112b5-385">Run your tests, and they should all pass.</span></span> <span data-ttu-id="112b5-386">完成したアナライザーを実行してみてください。</span><span class="sxs-lookup"><span data-stu-id="112b5-386">Congratulate yourself by running your finished analyzer.</span></span> <span data-ttu-id="112b5-387"><kbd>Ctrl + F5</kbd> キーを押して Roslyn Preview 拡張機能が読み込まれた Visual Studio の 2 つ目のインスタンスでアナライザー プロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="112b5-387">Press <kbd>Ctrl+F5</kbd> to run the analyzer project in a second instance of Visual Studio with the Roslyn Preview extension loaded.</span></span>

- <span data-ttu-id="112b5-388">2 つ目の Visual Studio インスタンスで、新しい C# コンソール アプリケーション プロジェクトを作成し、`int x = "abc";` を Main メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-388">In the second Visual Studio instance, create a new C# Console Application project and add `int x = "abc";` to the Main method.</span></span> <span data-ttu-id="112b5-389">最初のバグ修正のおかげで、このローカル変数宣言について警告は報告されません (ただし、想定どおりコンパイラ エラーが発生します)。</span><span class="sxs-lookup"><span data-stu-id="112b5-389">Thanks to the first bug fix, no warning should be reported for this local variable declaration (though there's a compiler error as expected).</span></span>
- <span data-ttu-id="112b5-390">次に、Main メソッドに `object s = "abc";` を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-390">Next, add `object s = "abc";` to the Main method.</span></span> <span data-ttu-id="112b5-391">2 つ目のバグ修正のおかげで、警告は報告されません。</span><span class="sxs-lookup"><span data-stu-id="112b5-391">Because of the second bug fix, no warning should be reported.</span></span>
- <span data-ttu-id="112b5-392">最後に、`var` キーワードを使用する別のローカル変数を追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-392">Finally, add another local variable that uses the `var` keyword.</span></span> <span data-ttu-id="112b5-393">警告が報告され、左側の下部に推奨が表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-393">You'll see that a warning is reported and a suggestion appears beneath to the left.</span></span>
- <span data-ttu-id="112b5-394">波線にエディターのカレットを移動し、<kbd>Ctrl +</kbd> キーを押します。</span><span class="sxs-lookup"><span data-stu-id="112b5-394">Move the editor caret over the squiggly underline and press <kbd>Ctrl+</kbd>.</span></span> <span data-ttu-id="112b5-395">推奨されたコード修正が表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-395">to display the suggested code fix.</span></span> <span data-ttu-id="112b5-396">コード修正を選択して、var' キーワードが正しく処理されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="112b5-396">Upon selecting your code fix, note that the var' keyword is now handled correctly.</span></span>

<span data-ttu-id="112b5-397">最後に、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="112b5-397">Finally, add the following code:</span></span>

```csharp
int i = 2;
int j = 32;
int k = i + j;
```

<span data-ttu-id="112b5-398">これらの変更の後は、最初の 2 つの変数にのみ赤い波線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="112b5-398">After these changes, you get red squiggles only on the first two variables.</span></span> <span data-ttu-id="112b5-399">`i` と `j` の両方に `const` を追加すると、`const` になる可能性があるので、`k` で新しい警告を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="112b5-399">Add `const` to both `i` and `j`, and you get a new warning on `k` because it can now be `const`.</span></span>

<span data-ttu-id="112b5-400">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="112b5-400">Congratulations!</span></span> <span data-ttu-id="112b5-401">ここでは最初の .NET Compiler Platform 拡張機能を作成しました。これは、その場でコード分析を実行し、問題を検出してそれを修正する簡単な修正案を提供する拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="112b5-401">You've created your first .NET Compiler Platform extension that performs on-the-fly code analysis to detect an issue and provides a quick fix to correct it.</span></span> <span data-ttu-id="112b5-402">この過程で、.NET Compiler Platform SDK (Roslyn API) に含まれる多くのコード API を学びました。</span><span class="sxs-lookup"><span data-stu-id="112b5-402">Along the way, you've learned many of the code APIs that are part of the .NET Compiler Platform SDK (Roslyn APIs).</span></span> <span data-ttu-id="112b5-403">サンプル GitHub リポジトリの[完成したサンプル](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst)に対して作業を検査することができます。</span><span class="sxs-lookup"><span data-stu-id="112b5-403">You can check your work against the [completed sample](https://github.com/dotnet/samples/tree/master/csharp/roslyn-sdk/Tutorials/MakeConst) in our samples GitHub repository.</span></span>

## <a name="other-resources"></a><span data-ttu-id="112b5-404">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="112b5-404">Other resources</span></span>

- [<span data-ttu-id="112b5-405">構文解析の概要</span><span class="sxs-lookup"><span data-stu-id="112b5-405">Get started with syntax analysis</span></span>](../get-started/syntax-analysis.md)
- [<span data-ttu-id="112b5-406">セマンティック解析の概要</span><span class="sxs-lookup"><span data-stu-id="112b5-406">Get started with semantic analysis</span></span>](../get-started/semantic-analysis.md)
