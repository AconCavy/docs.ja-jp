---
title: dotnet run コマンド
description: dotnet run コマンドは、ソース コードからアプリケーションを実行する便利なオプションを提供します。
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734102"
---
# <a name="dotnet-run"></a><span data-ttu-id="6d8fc-103">dotnet run</span><span class="sxs-lookup"><span data-stu-id="6d8fc-103">dotnet run</span></span>

<span data-ttu-id="6d8fc-104">**この記事の対象:** ✔️ .NET Core 1.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="6d8fc-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="6d8fc-105">名前</span><span class="sxs-lookup"><span data-stu-id="6d8fc-105">Name</span></span>

<span data-ttu-id="6d8fc-106">`dotnet run` -- 明示的なコンパイルや起動コマンドなしで、ソース コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-106">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6d8fc-107">構文</span><span class="sxs-lookup"><span data-stu-id="6d8fc-107">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="6d8fc-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6d8fc-108">.NET Core 3.0</span></span>](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6d8fc-109">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6d8fc-109">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6d8fc-110">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6d8fc-110">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d8fc-111">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d8fc-111">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="6d8fc-112">説明</span><span class="sxs-lookup"><span data-stu-id="6d8fc-112">Description</span></span>

<span data-ttu-id="6d8fc-113">`dotnet run` コマンドは、1 つのコマンドを使用して、ソース コードからアプリケーションを実行する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-113">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="6d8fc-114">コマンド ラインからの短期間の反復開発に便利です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-114">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="6d8fc-115">このコマンドは [`dotnet build`](dotnet-build.md) コマンドに依存し、コードをビルドします。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-115">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="6d8fc-116">そのため、プロジェクトを最初に復元する必要があるなど、ビルドに要件があれば、それが `dotnet run` にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-116">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span>

<span data-ttu-id="6d8fc-117">出力ファイルは既定の場所である `bin/<configuration>/<target>` に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-117">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="6d8fc-118">たとえば、`netcoreapp2.1` というアプリケーションがあり、`dotnet run` を実行する場合、`bin/Debug/netcoreapp2.1` に出力されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-118">For example if you have a `netcoreapp2.1` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp2.1`.</span></span> <span data-ttu-id="6d8fc-119">必要に応じて、ファイルは上書きされます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-119">Files are overwritten as needed.</span></span> <span data-ttu-id="6d8fc-120">一時ファイルは `obj` ディレクトリに置かれます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-120">Temporary files are placed in the `obj` directory.</span></span>

<span data-ttu-id="6d8fc-121">フレームワークを複数指定するプロジェクトの場合、`-f|--framework <FRAMEWORK>` オプションを使用してフレームワークを指定しない限り、`dotnet run` を実行するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-121">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="6d8fc-122">`dotnet run` コマンドは、ビルド済みのアセンブリではなく、プロジェクトのコンテキストで使用されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-122">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="6d8fc-123">代わりにフレームワークに依存するアプリケーション DLL の実行を試みる場合は、コマンドなしで [dotnet](dotnet.md) を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-123">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="6d8fc-124">たとえば、`myapp.dll` を実行する場合は、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-124">For example, to run `myapp.dll`, use:</span></span>

```dotnetcli
dotnet myapp.dll
```

<span data-ttu-id="6d8fc-125">`dotnet` ドライバーの詳細については、[.NET Core コマンド ライン ツール (CLI)](index.md) に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-125">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="6d8fc-126">アプリケーションを実行するため、`dotnet run` コマンドは、NuGet キャッシュから共有ランタイムの外にあるアプリケーションの依存関係を解決します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-126">To run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="6d8fc-127">このコマンドではキャッシュされた依存関係を使用するため、`dotnet run` を使用してアプリケーションを実稼働環境で実行することは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-127">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="6d8fc-128">代わりに、[`dotnet publish`](dotnet-publish.md) コマンドを使用して[展開を作成](../deploying/index.md)し、発行された出力を展開します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-128">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a><span data-ttu-id="6d8fc-129">オプション</span><span class="sxs-lookup"><span data-stu-id="6d8fc-129">Options</span></span>

# <a name="net-core-30tabnetcore30"></a>[<span data-ttu-id="6d8fc-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6d8fc-130">.NET Core 3.0</span></span>](#tab/netcore30)

`--`

<span data-ttu-id="6d8fc-131">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-131">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="6d8fc-132">この区切り記号の後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-132">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d8fc-133">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-133">Defines the build configuration.</span></span> <span data-ttu-id="6d8fc-134">ほとんどのプロジェクトの既定値は、`Debug` です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-134">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d8fc-135">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-135">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6d8fc-136">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-136">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="6d8fc-137">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6d8fc-138">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-138">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="6d8fc-139">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-139">Prints out a short help for the command.</span></span>

`--interactive`

<span data-ttu-id="6d8fc-140">コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-140">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="6d8fc-141">アプリケーションを起動する場合に使用する起動プロファイル (存在する場合) の名前です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-141">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="6d8fc-142">起動プロファイルは *launchSettings.json* ファイル内に定義されており、通常は、`Development`、`Staging`、`Production` と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-142">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="6d8fc-143">詳細については、[「Working with multiple environments」](/aspnet/core/fundamentals/environments) (複数の環境での使用) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-143">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="6d8fc-144">実行前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-144">Doesn't build the project before running.</span></span> <span data-ttu-id="6d8fc-145">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-145">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="6d8fc-146">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-146">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="6d8fc-147">アプリケーションを構成するための *launchSettings.json* の使用を試みません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-147">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="6d8fc-148">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-148">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="6d8fc-149">実行するプロジェクト ファイルのパスを指定します (フォルダー名または完全なパス)。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-149">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="6d8fc-150">指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-150">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6d8fc-151">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="6d8fc-152">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6d8fc-153">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6d8fc-154">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6d8fc-155">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6d8fc-155">.NET Core 2.1</span></span>](#tab/netcore21)

`--`

<span data-ttu-id="6d8fc-156">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-156">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="6d8fc-157">この区切り記号の後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-157">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d8fc-158">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-158">Defines the build configuration.</span></span> <span data-ttu-id="6d8fc-159">ほとんどのプロジェクトの既定値は、`Debug` です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-159">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d8fc-160">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-160">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6d8fc-161">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-161">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="6d8fc-162">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-162">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6d8fc-163">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-163">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="6d8fc-164">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-164">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="6d8fc-165">アプリケーションを起動する場合に使用する起動プロファイル (存在する場合) の名前です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-165">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="6d8fc-166">起動プロファイルは *launchSettings.json* ファイル内に定義されており、通常は、`Development`、`Staging`、`Production` と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-166">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="6d8fc-167">詳細については、[「Working with multiple environments」](/aspnet/core/fundamentals/environments) (複数の環境での使用) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-167">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="6d8fc-168">実行前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-168">Doesn't build the project before running.</span></span> <span data-ttu-id="6d8fc-169">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-169">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="6d8fc-170">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-170">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="6d8fc-171">アプリケーションを構成するための *launchSettings.json* の使用を試みません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-171">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="6d8fc-172">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-172">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="6d8fc-173">実行するプロジェクト ファイルのパスを指定します (フォルダー名または完全なパス)。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-173">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="6d8fc-174">指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-174">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6d8fc-175">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-175">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="6d8fc-176">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-176">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6d8fc-177">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-177">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6d8fc-178">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-178">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6d8fc-179">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="6d8fc-179">.NET Core 2.0</span></span>](#tab/netcore20)

`--`

<span data-ttu-id="6d8fc-180">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-180">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="6d8fc-181">この区切り記号の後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-181">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d8fc-182">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-182">Defines the build configuration.</span></span> <span data-ttu-id="6d8fc-183">ほとんどのプロジェクトの既定値は、`Debug` です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-183">The default for most projects value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d8fc-184">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-184">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6d8fc-185">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-185">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="6d8fc-186">最後の復元が成功した場合でも、すべての依存関係が強制的に解決されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-186">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="6d8fc-187">このフラグを指定することは、*project.assets.json* ファイルを削除することと同じです。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-187">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="6d8fc-188">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-188">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="6d8fc-189">アプリケーションを起動する場合に使用する起動プロファイル (存在する場合) の名前です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-189">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="6d8fc-190">起動プロファイルは *launchSettings.json* ファイル内に定義されており、通常は、`Development`、`Staging`、`Production` と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-190">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging`, and `Production`.</span></span> <span data-ttu-id="6d8fc-191">詳細については、[「Working with multiple environments」](/aspnet/core/fundamentals/environments) (複数の環境での使用) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-191">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="6d8fc-192">実行前にプロジェクトをビルドしません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-192">Doesn't build the project before running.</span></span> <span data-ttu-id="6d8fc-193">また、`--no-restore` フラグが暗黙的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-193">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="6d8fc-194">プロジェクト間 (P2P) 参照を含むプロジェクトを復元する場合は、参照ではなく、ルート プロジェクトを復元します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-194">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="6d8fc-195">アプリケーションを構成するための *launchSettings.json* の使用を試みません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-195">Doesn't try to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="6d8fc-196">コマンドを実行するときに、暗黙的な復元を実行しません。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-196">Doesn't execute an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="6d8fc-197">実行するプロジェクト ファイルのパスを指定します (フォルダー名または完全なパス)。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-197">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="6d8fc-198">指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-198">If not specified, it defaults to the current directory.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="6d8fc-199">パッケージを復元するターゲット ランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-199">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="6d8fc-200">ランタイム ID (RID) の一覧については、[RID カタログ](../rid-catalog.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-200">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6d8fc-201">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="6d8fc-201">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="6d8fc-202">実行中のアプリケーションの引数と `dotnet run` の引数を区切ります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-202">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="6d8fc-203">この区切り記号の後の引数はすべて実行中のアプリケーションに渡されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-203">All arguments after this delimiter are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="6d8fc-204">ビルド構成を定義します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-204">Defines the build configuration.</span></span> <span data-ttu-id="6d8fc-205">ほとんどのプロジェクトの既定値は、`Debug` です。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-205">The default value for most projects is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="6d8fc-206">指定された[フレームワーク](../../standard/frameworks.md)を使用してアプリをビルドし、実行します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-206">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="6d8fc-207">フレームワークはプロジェクト ファイルに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-207">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="6d8fc-208">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-208">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="6d8fc-209">プロジェクト ファイルのパスと名前を指定します</span><span class="sxs-lookup"><span data-stu-id="6d8fc-209">Specifies the path and name of the project file.</span></span> <span data-ttu-id="6d8fc-210">(注を参照)。指定しない場合は、既定で現在のディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-210">(See the NOTE.) If not specified, it defaults to the current directory.</span></span>

> [!NOTE]
> <span data-ttu-id="6d8fc-211">`-p|--project` オプションでプロジェクト ファイルのパスと名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-211">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="6d8fc-212">CLI の回帰により、.NET Core SDK 1.x でフォルダー パスを指定できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-212">A regression in the CLI prevents providing a folder path with .NET Core SDK 1.x.</span></span> <span data-ttu-id="6d8fc-213">この問題の詳細については、[「dotnet run -p, can not start a project (dotnet/cli #5992)」](https://github.com/dotnet/cli/issues/5992) (dotnet run -p でプロジェクトを開始できない (dotnet/cli #5992)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-213">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="6d8fc-214">使用例</span><span class="sxs-lookup"><span data-stu-id="6d8fc-214">Examples</span></span>

<span data-ttu-id="6d8fc-215">現在のディレクトリのプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-215">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="6d8fc-216">指定されたプロジェクトを実行します。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-216">Run the specified project:</span></span>

`dotnet run --project ./projects/proj1/proj1.csproj`

<span data-ttu-id="6d8fc-217">現在のディレクトリのプロジェクトを実行します (この例では、空の `--` オプションが使用されているため、`--help` 引数がアプリケーションに渡されます)。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-217">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the blank `--` option is used):</span></span>

`dotnet run --configuration Release -- --help`

<span data-ttu-id="6d8fc-218">現在のディレクトリでプロジェクトの依存関係とツールを復元し、最小限の出力のみを表示して、プロジェクトを実行します (.NET Core SDK 2.0 以降のバージョン)。</span><span class="sxs-lookup"><span data-stu-id="6d8fc-218">Restore dependencies and tools for the project in the current directory only showing minimal output and then run the project: (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet run --verbosity m`
