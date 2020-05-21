---
title: .NET Core と .NET Standard の単体テスト
description: この記事では、.NET Core と .NET Standard プロジェクト用の単体テストの概要を簡単に説明します。
author: ardalis
ms.author: wiwagn
ms.date: 05/18/2020
zone_pivot_groups: unit-testing-framework-set-one
ms.openlocfilehash: e15f80b173389cdff86c6e62013e9c0f21171dd6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703105"
---
# <a name="unit-testing-in-net-core-and-net-standard"></a><span data-ttu-id="a818b-103">.NET Core と .NET Standard の単体テスト</span><span class="sxs-lookup"><span data-stu-id="a818b-103">Unit testing in .NET Core and .NET Standard</span></span>

<span data-ttu-id="a818b-104">.NET core では、簡単に単体テストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a818b-104">.NET Core makes it easy to create unit tests.</span></span> <span data-ttu-id="a818b-105">この記事では、単体テストについて紹介し、その他の種類のテストとの違いを示します。</span><span class="sxs-lookup"><span data-stu-id="a818b-105">This article introduces unit tests and illustrates how they differ from other kinds of tests.</span></span> <span data-ttu-id="a818b-106">ページの下部にあるリンクされたリソースは、テスト プロジェクトをソリューションに追加する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a818b-106">The linked resources near the bottom of the page show you how to add a test project to your solution.</span></span> <span data-ttu-id="a818b-107">テスト プロジェクトを設定した後は、コマンドラインまたは Visual Studio を使用して単体テストを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="a818b-107">After you set up your test project, you will be able to run your unit tests using the command line or Visual Studio.</span></span>

<span data-ttu-id="a818b-108">**ASP.NET Core** プロジェクトをテストしている場合は、「[ASP.NET Core の統合テスト](/aspnet/core/test/integration-tests#test-app-prerequisites)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a818b-108">If you're testing an **ASP.NET Core** project, see [Integration tests in ASP.NET Core](/aspnet/core/test/integration-tests#test-app-prerequisites).</span></span>

<span data-ttu-id="a818b-109">.NET Core 2.0 以降では [.NET Standard 2.0](../../standard/net-standard.md) がサポートされます。単体テストはそのライブラリを使用して説明します。</span><span class="sxs-lookup"><span data-stu-id="a818b-109">.NET Core 2.0 and later supports [.NET Standard 2.0](../../standard/net-standard.md), and we will use its libraries to demonstrate unit tests.</span></span>

<span data-ttu-id="a818b-110">C#、F#、Visual Basic 向けに組み込まれている .NET Core 2.0 以降の単体テスト プロジェクト テンプレートを個人プロジェクトの開始点として使用することができます。</span><span class="sxs-lookup"><span data-stu-id="a818b-110">You are able to use built-in .NET Core 2.0 and later unit test project templates for C#, F# and Visual Basic as a starting point for your personal project.</span></span>

## <a name="what-are-unit-tests"></a><span data-ttu-id="a818b-111">単体テストとは</span><span class="sxs-lookup"><span data-stu-id="a818b-111">What are unit tests?</span></span>

<span data-ttu-id="a818b-112">自動テストを備えることは、ソフトウェア アプリケーションを作成者の意図どおりに確実に動作させるための最良の方法です。</span><span class="sxs-lookup"><span data-stu-id="a818b-112">Having automated tests is a great way to ensure a software application does what its authors intend it to do.</span></span> <span data-ttu-id="a818b-113">ソフトウェア アプリケーションには複数の種類のテストがあります。</span><span class="sxs-lookup"><span data-stu-id="a818b-113">There are multiple types of tests for software applications.</span></span> <span data-ttu-id="a818b-114">統合テスト、Web テスト、ロード テストなどが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a818b-114">These include integration tests, web tests, load tests, and others.</span></span> <span data-ttu-id="a818b-115">**単体テスト**は、個々 のソフトウェア コンポーネントとメソッドをテストします。</span><span class="sxs-lookup"><span data-stu-id="a818b-115">**Unit tests** test individual software components and methods.</span></span> <span data-ttu-id="a818b-116">単体テストでは、開発者のコントロール内のコードのみがテストされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a818b-116">Unit tests should only test code within the developer’s control.</span></span> <span data-ttu-id="a818b-117">インフラストラクチャの懸念事項をテストすべきではありません。</span><span class="sxs-lookup"><span data-stu-id="a818b-117">They should not test infrastructure concerns.</span></span> <span data-ttu-id="a818b-118">インフラストラクチャの懸念事項には、データベース、ファイル システム、ネットワーク リソースが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a818b-118">Infrastructure concerns include databases, file systems, and network resources.</span></span>

<span data-ttu-id="a818b-119">テストを記述するためのベスト プラクティスもあります。</span><span class="sxs-lookup"><span data-stu-id="a818b-119">Also, keep in mind there are best practices for writing tests.</span></span> <span data-ttu-id="a818b-120">たとえば、[テスト駆動開発 (TDD)](https://deviq.com/test-driven-development/) では、チェックされるコードよりも前に単体テストが記述されます。</span><span class="sxs-lookup"><span data-stu-id="a818b-120">For example, [Test Driven Development (TDD)](https://deviq.com/test-driven-development/) is when a unit test is written before the code it is meant to check.</span></span> <span data-ttu-id="a818b-121">TDD は本を書く前にアウトラインを作成するのと似ています。</span><span class="sxs-lookup"><span data-stu-id="a818b-121">TDD is like creating an outline for a book before we write it.</span></span> <span data-ttu-id="a818b-122">開発者が簡潔で読みやすく、効率的なコードを記述できるように支援します。</span><span class="sxs-lookup"><span data-stu-id="a818b-122">It is meant to help developers write simpler, more readable, and efficient code.</span></span>

> [!NOTE]
> <span data-ttu-id="a818b-123">ASP.NET チームは[この規則](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests)に従って、開発者がテスト クラスとメソッドに適した名前を考えられるように支援します。</span><span class="sxs-lookup"><span data-stu-id="a818b-123">The ASP.NET team follows [these conventions](https://github.com/dotnet/aspnetcore/wiki/Engineering-guidelines#unit-tests-and-functional-tests) to help developers come up with good names for test classes and methods.</span></span>

<span data-ttu-id="a818b-124">単体テストを記述するときは、インフラストラクチャに対する依存関係を設けようとしないでください。</span><span class="sxs-lookup"><span data-stu-id="a818b-124">Try not to introduce dependencies on infrastructure when writing unit tests.</span></span> <span data-ttu-id="a818b-125">テストが低速で不安定になるため、これは統合テストで行います。</span><span class="sxs-lookup"><span data-stu-id="a818b-125">These make the tests slow and brittle, and should be reserved for integration tests.</span></span> <span data-ttu-id="a818b-126">アプリケーションでこれらの依存関係を回避するには、[明示的な依存関係の原則](https://deviq.com/explicit-dependencies-principle/)に従い、[依存関係の挿入](/aspnet/core/fundamentals/dependency-injection)を使用します。</span><span class="sxs-lookup"><span data-stu-id="a818b-126">You can avoid these dependencies in your application by following the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/) and using [Dependency Injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="a818b-127">個別のプロジェクトの単体テストを統合テストと区別することもできます。</span><span class="sxs-lookup"><span data-stu-id="a818b-127">You can also keep your unit tests in a separate project from your integration tests.</span></span> <span data-ttu-id="a818b-128">これにより、単体テスト プロジェクトとインフラストラクチャ パッケージの間に参照や依存関係がなくなります。</span><span class="sxs-lookup"><span data-stu-id="a818b-128">This ensures your unit test project doesn’t have references to or dependencies on infrastructure packages.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a818b-129">次の手順</span><span class="sxs-lookup"><span data-stu-id="a818b-129">Next steps</span></span>

<span data-ttu-id="a818b-130">.NET Core プロジェクトでの単体テストの詳細については、次を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a818b-130">More information on unit testing in .NET Core projects:</span></span>

<span data-ttu-id="a818b-131">次に対する .NET Core 単体テスト プロジェクトがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a818b-131">.NET Core unit test projects are supported for:</span></span>

- [<span data-ttu-id="a818b-132">C#</span><span class="sxs-lookup"><span data-stu-id="a818b-132">C#</span></span>](../../csharp/index.yml)
- [<span data-ttu-id="a818b-133">F#</span><span class="sxs-lookup"><span data-stu-id="a818b-133">F#</span></span>](../../fsharp/index.yml)
- [<span data-ttu-id="a818b-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a818b-134">Visual Basic</span></span>](../../visual-basic/index.yml)

<span data-ttu-id="a818b-135">複数の単体テスト フレームワークから選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="a818b-135">You can also choose between several unit test frameworks:</span></span>

- [<span data-ttu-id="a818b-136">xUnit</span><span class="sxs-lookup"><span data-stu-id="a818b-136">xUnit</span></span>](https://xunit.net/)
- [<span data-ttu-id="a818b-137">NUnit</span><span class="sxs-lookup"><span data-stu-id="a818b-137">NUnit</span></span>](https://nunit.org)
- [<span data-ttu-id="a818b-138">MSTest</span><span class="sxs-lookup"><span data-stu-id="a818b-138">MSTest</span></span>](https://github.com/Microsoft/testfx-docs)

<span data-ttu-id="a818b-139">次のチュートリアルでさらに詳しく学習できます。</span><span class="sxs-lookup"><span data-stu-id="a818b-139">You can learn more in the following walkthroughs:</span></span>

:::zone pivot="mstest"

- <span data-ttu-id="a818b-140">[*MSTest* と *C#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-with-mstest.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-140">Create unit tests using [*MSTest* and *C#* with the .NET Core CLI](unit-testing-with-mstest.md).</span></span>
- <span data-ttu-id="a818b-141">[*MSTest* と *F#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-fsharp-with-mstest.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-141">Create unit tests using [*MSTest* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-mstest.md).</span></span>
- <span data-ttu-id="a818b-142">[*MSTest* と *Visual Basic* を使用して .NET Core CLI で単体テストを作成する](unit-testing-visual-basic-with-mstest.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-142">Create unit tests using [*MSTest* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-mstest.md).</span></span>

:::zone-end
:::zone pivot="xunit"

- <span data-ttu-id="a818b-143">[*xUnit* と *C#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-with-dotnet-test.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-143">Create unit tests using [*xUnit* and *C#* with the .NET Core CLI](unit-testing-with-dotnet-test.md).</span></span>
- <span data-ttu-id="a818b-144">[*xUnit* と *F#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-fsharp-with-dotnet-test.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-144">Create unit tests using [*xUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-dotnet-test.md).</span></span>
- <span data-ttu-id="a818b-145">[*xUnit* と *Visual Basic* を使用して .NET Core CLI で単体テストを作成する](unit-testing-visual-basic-with-dotnet-test.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-145">Create unit tests using [*xUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-dotnet-test.md).</span></span>

:::zone-end
:::zone pivot="nunit"

- <span data-ttu-id="a818b-146">[*NUnit* と *C#* を使用して .NET Core CLI で単体テストを作成する](unit-testing-with-nunit.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-146">Create unit tests using [*NUnit* and *C#* with the .NET Core CLI](unit-testing-with-nunit.md).</span></span>
- <span data-ttu-id="a818b-147">[*NUnit* と *F#* を使用して .NET Core CLI](unit-testing-fsharp-with-nunit.md) で単体テストを作成する。</span><span class="sxs-lookup"><span data-stu-id="a818b-147">Create unit tests using [*NUnit* and *F#* with the .NET Core CLI](unit-testing-fsharp-with-nunit.md).</span></span>
- <span data-ttu-id="a818b-148">[*NUnit* と *Visual Basic* を使用して .NET Core CLI で単体テストを作成する](unit-testing-visual-basic-with-nunit.md)。</span><span class="sxs-lookup"><span data-stu-id="a818b-148">Create unit tests using [*NUnit* and *Visual Basic* with the .NET Core CLI](unit-testing-visual-basic-with-nunit.md).</span></span>

:::zone-end

<span data-ttu-id="a818b-149">次の記事でさらに詳しく学習できます。</span><span class="sxs-lookup"><span data-stu-id="a818b-149">You can learn more in the following articles:</span></span>

- <span data-ttu-id="a818b-150">Visual Studio Enterprise は、.NET Core の優れたテスト ツールを提供します。</span><span class="sxs-lookup"><span data-stu-id="a818b-150">Visual Studio Enterprise offers great testing tools for .NET Core.</span></span> <span data-ttu-id="a818b-151">[Live Unit Testing](/visualstudio/test/live-unit-testing) または[コード カバレッジ](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage)をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="a818b-151">Check out [Live Unit Testing](/visualstudio/test/live-unit-testing) or [code coverage](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage) to learn more.</span></span>
- <span data-ttu-id="a818b-152">選択的単体テストの実行方法に関する詳細については、「[選択的単体テストの実行](selective-unit-tests.md)」、または [Visual Studio を使用したテストの組み込みと除外](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)に関するトピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a818b-152">For more information on how to run selective unit tests, see [Running selective unit tests](selective-unit-tests.md), or [including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).</span></span>
- <span data-ttu-id="a818b-153">[.NET Core と Visual Studio で xUnit を使用する方法](https://xunit.github.io/docs/getting-started-dotnet-core.html)</span><span class="sxs-lookup"><span data-stu-id="a818b-153">[How to use xUnit with .NET Core and Visual Studio](https://xunit.github.io/docs/getting-started-dotnet-core.html).</span></span>
