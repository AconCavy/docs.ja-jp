---
title: ソースから .NET Core をビルドする
description: ソース コードから .NET Core と .NET Core CLI をビルドする方法を説明します。
author: bleroy
ms.date: 06/28/2017
ms.openlocfilehash: fe5431667d861d830c2ec56252e6e3e2ca08a866
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740916"
---
# <a name="build-net-core-from-source"></a><span data-ttu-id="127a4-103">ソースから .NET Core をビルドする</span><span class="sxs-lookup"><span data-stu-id="127a4-103">Build .NET Core from source</span></span>

<span data-ttu-id="127a4-104">ソース コードから .NET Core をビルドできることは、複数の方法において重要なことです。 .NET Core を新しいプラットフォームに簡単に移植でき、製品に対するコントリビューションと修正を有効にすることができ、また、.NET のカスタム バージョンを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="127a4-104">The ability to build .NET Core from its source code is important in multiple ways: it makes it easier to port .NET Core to new platforms, it enables contributions and fixes to the product, and it enables the creation of custom versions of .NET.</span></span>
<span data-ttu-id="127a4-105">この記事では、独自のバージョンの .NET Core をビルドして配布する開発者向けのガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="127a4-105">This article gives guidance to developers who want to build and distribute their own versions of .NET Core.</span></span>

## <a name="build-the-clr-from-source"></a><span data-ttu-id="127a4-106">ソースから CLR をビルドする</span><span class="sxs-lookup"><span data-stu-id="127a4-106">Build the CLR from source</span></span>

<span data-ttu-id="127a4-107">.NET CoreCLR のソース コードは、GitHub の [dotnet/runtime](https://github.com/dotnet/runtime/) リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="127a4-107">The source code for the .NET CoreCLR can be found in the [dotnet/runtime](https://github.com/dotnet/runtime/) repository on GitHub.</span></span>

<span data-ttu-id="127a4-108">ビルドは、現在、次の前提条件に依存しています。</span><span class="sxs-lookup"><span data-stu-id="127a4-108">The build currently depends on the following prerequisites:</span></span>

- [<span data-ttu-id="127a4-109">Git</span><span class="sxs-lookup"><span data-stu-id="127a4-109">Git</span></span>](https://git-scm.com/)
- [<span data-ttu-id="127a4-110">CMake</span><span class="sxs-lookup"><span data-stu-id="127a4-110">CMake</span></span>](https://cmake.org/)
- [<span data-ttu-id="127a4-111">Python</span><span class="sxs-lookup"><span data-stu-id="127a4-111">Python</span></span>](https://www.python.org/)
- <span data-ttu-id="127a4-112">C++ コンパイラ。</span><span class="sxs-lookup"><span data-stu-id="127a4-112">a C++ compiler.</span></span>

<span data-ttu-id="127a4-113">これらの前提条件をインストールしたら、[dotnet/runtime](https://github.com/dotnet/runtime/) リポジトリの下部にあるビルド スクリプト (Windows の場合は `build.cmd`、Linux と macOS の場合は `build.sh`) を呼び出して、CLR をビルドできます。</span><span class="sxs-lookup"><span data-stu-id="127a4-113">After you've installed these prerequisites, you can build the CLR by invoking the build script (`build.cmd` on Windows, or `build.sh` on Linux and macOS) at the base of the [dotnet/runtime](https://github.com/dotnet/runtime/) repository.</span></span>

<span data-ttu-id="127a4-114">コンポーネントのインストールは、オペレーティング システム (OS) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="127a4-114">Installing the components differ depending on the operating system (OS).</span></span> <span data-ttu-id="127a4-115">以下の特定の OS のビルド手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="127a4-115">See the build instructions for your specific OS:</span></span>

- [<span data-ttu-id="127a4-116">Windows</span><span class="sxs-lookup"><span data-stu-id="127a4-116">Windows</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [<span data-ttu-id="127a4-117">Linux</span><span class="sxs-lookup"><span data-stu-id="127a4-117">Linux</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [<span data-ttu-id="127a4-118">macOS</span><span class="sxs-lookup"><span data-stu-id="127a4-118">macOS</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [<span data-ttu-id="127a4-119">FreeBSD</span><span class="sxs-lookup"><span data-stu-id="127a4-119">FreeBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [<span data-ttu-id="127a4-120">NetBSD</span><span class="sxs-lookup"><span data-stu-id="127a4-120">NetBSD</span></span>](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

<span data-ttu-id="127a4-121">OS 間でのクロス ビルドはありません (X64 にビルドされる ARM の場合のみ)。</span><span class="sxs-lookup"><span data-stu-id="127a4-121">There is no cross-building across OS (only for ARM, which is built on X64).</span></span>  
<span data-ttu-id="127a4-122">特定のプラットフォームのビルドは、そのプラットフォームで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-122">You have to be on the particular platform to build that platform.</span></span>  

<span data-ttu-id="127a4-123">ビルドには、次の主な 2 つの `buildTypes` があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-123">The build has two main `buildTypes`:</span></span>

- <span data-ttu-id="127a4-124">デバッグ (既定) - 最小限の最適化と追加のランタイム チェック (アサート) を実行してランタイムをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="127a4-124">Debug (default)- Compiles the runtime with minimal optimizations and additional runtime checks (asserts).</span></span> <span data-ttu-id="127a4-125">最適化レベルを抑えるとともに追加のチェックを行うため、ランタイム実行の速度は低下しますが、デバッグには有用です。</span><span class="sxs-lookup"><span data-stu-id="127a4-125">This reduction in optimization level and the additional checks slow runtime execution but are valuable for debugging.</span></span> <span data-ttu-id="127a4-126">この設定は、開発環境およびテスト環境で推奨されます。</span><span class="sxs-lookup"><span data-stu-id="127a4-126">This is the recommended setting for development and testing environments.</span></span>
- <span data-ttu-id="127a4-127">リリース - 追加のランタイム チェックは実行せず、完全な最適化を行いランタイムをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="127a4-127">Release - Compiles the runtime with full optimizations and without the additional runtime checks.</span></span> <span data-ttu-id="127a4-128">これにより、実行時のパフォーマンスが大幅に向上しますが、ビルドにかかる時間が少し長くなり、デバッグが困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-128">This will yield much faster run-time performance, but it can take a bit longer to build and can be difficult to debug.</span></span> <span data-ttu-id="127a4-129">このビルドの種類を選択するには、`release` をビルド スクリプトに渡します。</span><span class="sxs-lookup"><span data-stu-id="127a4-129">Pass `release` to the build script to select this build type.</span></span>

<span data-ttu-id="127a4-130">さらに、既定では、ビルドでランタイムの実行可能ファイルの作成だけでなく、すべてのテストのビルドも行われます。</span><span class="sxs-lookup"><span data-stu-id="127a4-130">In addition, by default the build not only creates the runtime executables, but it also builds all the tests.</span></span>
<span data-ttu-id="127a4-131">かなり多くのテストがあり、単に変更を試みる場合には必要のない非常に長い時間を要します。</span><span class="sxs-lookup"><span data-stu-id="127a4-131">There are quite a few tests, taking a significant amount of time that isn't necessary if you just want to experiment with changes.</span></span>
<span data-ttu-id="127a4-132">次の例のように、ビルド スクリプトに `skiptests` 引数を追加することで、これらのテスト ビルドをスキップできます (Unix コンピューターでは `.\build` を `./build.sh` に置き換えます)。</span><span class="sxs-lookup"><span data-stu-id="127a4-132">You can skip the tests builds by adding the `skiptests` argument to the build script, like in the following example (replace `.\build` with `./build.sh` on Unix machines):</span></span>

```bat
    .\build skiptests
```

<span data-ttu-id="127a4-133">前の例では、開発時のチェック (アサート) を有効にし、最適化を無効にして `Debug` フレーバーをビルドする方法について説明しました。</span><span class="sxs-lookup"><span data-stu-id="127a4-133">The previous example showed how to build the `Debug` flavor, which has development time checks (asserts) enabled and optimizations disabled.</span></span> <span data-ttu-id="127a4-134">リリース (フル スピード) フレーバーをビルドするには、次のようにします。</span><span class="sxs-lookup"><span data-stu-id="127a4-134">To build the release (full speed) flavor, do the following:</span></span>

```bat
    .\build release skiptests
```

<span data-ttu-id="127a4-135">-? または -help 修飾子を使用すれば、他のビルド オプションを</span><span class="sxs-lookup"><span data-stu-id="127a4-135">You can find more build options with build by using the -?</span></span> <span data-ttu-id="127a4-136">見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="127a4-136">or -help qualifier.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="127a4-137">ビルドの使用</span><span class="sxs-lookup"><span data-stu-id="127a4-137">Using Your Build</span></span>

<span data-ttu-id="127a4-138">ビルドでは、リポジトリの下部の `bin` ディレクトリに生成されたすべてのファイルが配置されます。</span><span class="sxs-lookup"><span data-stu-id="127a4-138">The build places all of its generated files under the `bin` directory at the base of the repository.</span></span>
<span data-ttu-id="127a4-139">*bin\Log* ディレクトリには、ビルド時に生成されるログ ファイル (ビルドに失敗した場合に最も役立つ) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="127a4-139">There is a *bin\Log* directory that contains log files generated during the build (Most useful when the build fails).</span></span>
<span data-ttu-id="127a4-140">実際の出力は、*bin\Product\Windows_NT.x64.Release* などの *bin\Product\[platform].[CPU architecture].[build type]* ディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="127a4-140">The actual output is placed in a *bin\Product\[platform].[CPU architecture].[build type]* directory, such as *bin\Product\Windows_NT.x64.Release*.</span></span>

<span data-ttu-id="127a4-141">ビルドの "生" 出力が役立つ場合もありますが、通常は、前の出力ディレクトリの `.nuget\pkg` サブディレクトリに配置される、NuGet パッケージのみを使用します。</span><span class="sxs-lookup"><span data-stu-id="127a4-141">While the 'raw' output of the build is sometimes useful, normally you're only interested in the NuGet packages, which are placed in the `.nuget\pkg` subdirectory of the previous output directory.</span></span>

<span data-ttu-id="127a4-142">新しいランタイムを使用する場合、次の 2 つの基本的な方法があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-142">There are two basic techniques for using your new runtime:</span></span>

 1. <span data-ttu-id="127a4-143">**dotnet.exe と NuGet を使用して、アプリケーションを作成します**。</span><span class="sxs-lookup"><span data-stu-id="127a4-143">**Use dotnet.exe and NuGet to compose an application**.</span></span>
    <span data-ttu-id="127a4-144">作成した NuGet パッケージと 'dotnet' コマンド ライン インターフェイス (CLI) を使用して、新しいランタイムを使用するプログラムを作成する手順については、「[ビルドの使用](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="127a4-144">See [Using Your Build](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-your-build.md) for instructions on creating a program that uses your new runtime by using the NuGet packages you just created and the 'dotnet' command-line interface (CLI).</span></span> <span data-ttu-id="127a4-145">この方法では、ランタイム開発者以外が新しいランタイムを使用する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-145">This technique is the expected way non-runtime developers are likely to consume your new runtime.</span></span>

 2. <span data-ttu-id="127a4-146">**corerun.exe を使用し、解凍した DLL を使用してアプリケーションを実行します**。</span><span class="sxs-lookup"><span data-stu-id="127a4-146">**Use corerun.exe to run an application using unpackaged DLLs**.</span></span>
    <span data-ttu-id="127a4-147">このリポジトリでは、NuGet に依存しない corerun.exe という単純なホストの定義も行います。</span><span class="sxs-lookup"><span data-stu-id="127a4-147">This repository also defines a simple host called corerun.exe that does NOT take any dependency on NuGet.</span></span>
    <span data-ttu-id="127a4-148">実際に使用する必要な DLL を取得する場所をホストに指示する必要があり、これらの DLL は手動で収集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-148">You need to tell the host where to get the required DLLs you actually use, and you have to manually gather them together.</span></span>
    <span data-ttu-id="127a4-149">この手法は、[dotnet/runtime](https://github.com/dotnet/runtime) リポジトリ内のすべてのテストで使用されており、ローカルでの簡単な "編集-コンパイル-デバッグ" ループに便利です (予備の単体テストなど)。</span><span class="sxs-lookup"><span data-stu-id="127a4-149">This technique is used by all the tests in the [dotnet/runtime](https://github.com/dotnet/runtime) repo, and is useful for quick local 'edit-compile-debug' loop such as preliminary unit testing.</span></span>
    <span data-ttu-id="127a4-150">この方法の使用の詳細については、「[Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md)」 (CoreRun.exe を使用する .NET Core アプリの実行) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="127a4-150">See [Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/runtime/blob/master/docs/workflow/testing/using-corerun.md) for details on using this technique.</span></span>

## <a name="build-the-cli-from-source"></a><span data-ttu-id="127a4-151">ソースから CLI をビルドする</span><span class="sxs-lookup"><span data-stu-id="127a4-151">Build the CLI from source</span></span>

<span data-ttu-id="127a4-152">.NET Core CLI のソース コードは、GitHub の [dotnet/cli](https://github.com/dotnet/cli/) リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="127a4-152">The source code for the .NET Core CLI can be found in the [dotnet/cli](https://github.com/dotnet/cli/) repository on GitHub.</span></span>

<span data-ttu-id="127a4-153">.NET Core CLI をビルドするには、コンピューターに以下をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-153">In order to build the .NET Core CLI, you need the following installed on your machine.</span></span>

- <span data-ttu-id="127a4-154">Windows および Linux:</span><span class="sxs-lookup"><span data-stu-id="127a4-154">Windows & Linux:</span></span>
  - <span data-ttu-id="127a4-155">パスの git</span><span class="sxs-lookup"><span data-stu-id="127a4-155">git on the PATH</span></span>
- <span data-ttu-id="127a4-156">macOS:</span><span class="sxs-lookup"><span data-stu-id="127a4-156">macOS:</span></span>
  - <span data-ttu-id="127a4-157">パスの git</span><span class="sxs-lookup"><span data-stu-id="127a4-157">git on the PATH</span></span>
  - <span data-ttu-id="127a4-158">Xcode</span><span class="sxs-lookup"><span data-stu-id="127a4-158">Xcode</span></span>
  - <span data-ttu-id="127a4-159">Openssl</span><span class="sxs-lookup"><span data-stu-id="127a4-159">OpenSSL</span></span>

<span data-ttu-id="127a4-160">ビルドするには、Windows の場合は `build.cmd` を、Linux と macOS の場合は `build.sh` をルートから実行します。</span><span class="sxs-lookup"><span data-stu-id="127a4-160">In order to build, run `build.cmd` on Windows, or `build.sh` on Linux and macOS from the root.</span></span> <span data-ttu-id="127a4-161">テストを実行しない場合は、`build.cmd -t:Compile` または `./build.sh -t:Compile` を実行します。</span><span class="sxs-lookup"><span data-stu-id="127a4-161">If you don't want to execute tests, run `build.cmd -t:Compile` or `./build.sh -t:Compile`.</span></span> <span data-ttu-id="127a4-162">macOS Sierra で CLI をビルドするには、`export DOTNET_RUNTIME_ID=osx.10.11-x64` を実行して、DOTNET_RUNTIME_ID 環境変数を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="127a4-162">To build the CLI in macOS Sierra, you need to set the DOTNET_RUNTIME_ID environment variable by running `export DOTNET_RUNTIME_ID=osx.10.11-x64`.</span></span>

### <a name="using-your-build"></a><span data-ttu-id="127a4-163">ビルドの使用</span><span class="sxs-lookup"><span data-stu-id="127a4-163">Using your build</span></span>

<span data-ttu-id="127a4-164">*artifacts/{os}-{arch}/stage2* の `dotnet` 実行可能ファイルを使用して、新しくビルドされた CLI を試します。</span><span class="sxs-lookup"><span data-stu-id="127a4-164">Use the `dotnet` executable from *artifacts/{os}-{arch}/stage2* to try out the newly built CLI.</span></span> <span data-ttu-id="127a4-165">現在のコンソールから `dotnet` を呼び出す際にビルド出力を使用する場合は、*artifacts/{os}-{arch}/stage2* をパスに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="127a4-165">If you want to use the build output when invoking `dotnet` from the current console, you can also add *artifacts/{os}-{arch}/stage2* to the PATH.</span></span>

## <a name="see-also"></a><span data-ttu-id="127a4-166">関連項目</span><span class="sxs-lookup"><span data-stu-id="127a4-166">See also</span></span>

- [<span data-ttu-id="127a4-167">.NET ランタイム</span><span class="sxs-lookup"><span data-stu-id="127a4-167">.NET Runtime</span></span>](https://github.com/dotnet/runtime/blob/master/README.md)
- [<span data-ttu-id="127a4-168">.NET Core CLI 開発者ガイド</span><span class="sxs-lookup"><span data-stu-id="127a4-168">.NET Core CLI Developer Guide</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [<span data-ttu-id="127a4-169">.NET Core の配布パッケージ</span><span class="sxs-lookup"><span data-stu-id="127a4-169">.NET Core distribution packaging</span></span>](./distribution-packaging.md)
