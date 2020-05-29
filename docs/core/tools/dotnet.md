---
title: dotnet コマンド
description: dotnet コマンド (.NET Core CLI の汎用ドライバー) とその使用方法について説明します。
ms.date: 02/13/2020
ms.openlocfilehash: 88e92b3ff5e8f68b980015a817434dd2d67df93a
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378839"
---
# <a name="dotnet-command"></a><span data-ttu-id="9e87a-103">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-103">dotnet command</span></span>

<span data-ttu-id="9e87a-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="9e87a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9e87a-105">名前</span><span class="sxs-lookup"><span data-stu-id="9e87a-105">Name</span></span>

<span data-ttu-id="9e87a-106">`dotnet` - .NET Core CLI の汎用ドライバー。</span><span class="sxs-lookup"><span data-stu-id="9e87a-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9e87a-107">構文</span><span class="sxs-lookup"><span data-stu-id="9e87a-107">Synopsis</span></span>

<span data-ttu-id="9e87a-108">利用できるコマンドと環境に関する情報を取得するには:</span><span class="sxs-lookup"><span data-stu-id="9e87a-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="9e87a-109">コマンドを実行するには (SDK のインストールが必要):</span><span class="sxs-lookup"><span data-stu-id="9e87a-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="9e87a-110">アプリケーションを実行するには:</span><span class="sxs-lookup"><span data-stu-id="9e87a-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="9e87a-111">`--roll-forward` は、.NET Core 3.x 以降で利用できます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="9e87a-112">.NET Core 2.x には `--roll-forward-on-no-candidate-fx` を使用します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="9e87a-113">説明</span><span class="sxs-lookup"><span data-stu-id="9e87a-113">Description</span></span>

<span data-ttu-id="9e87a-114">`dotnet` コマンドには、次の 2 つの機能があります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="9e87a-115">.NET Core プロジェクトを操作するためのコマンドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="9e87a-116">たとえば、[`dotnet build`](dotnet-build.md) を使うと、プロジェクトをビルドできます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="9e87a-117">各コマンドには独自のオプションと引数が定義されています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="9e87a-118">すべてのコマンドは、コマンドの使用方法に関する簡単なドキュメントを出力するための `--help` オプションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="9e87a-119">.NET Core アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="9e87a-120">アプリケーションを実行するには、アプリケーション `.dll` ファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="9e87a-121">アプリケーションを実行するということは、エントリ ポイントを見つけて実行することを意味します。コンソール アプリの場合、これは `Main` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="9e87a-122">たとえば、`dotnet myapp.dll` を使うと、`myapp` アプリケーションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="9e87a-123">展開オプションについては、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="9e87a-124">オプション</span><span class="sxs-lookup"><span data-stu-id="9e87a-124">Options</span></span>

<span data-ttu-id="9e87a-125">`dotnet` 単独、コマンドの実行、アプリケーションの実行にはさまざまなオプションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="9e87a-126">dotnet 単独のオプション</span><span class="sxs-lookup"><span data-stu-id="9e87a-126">Options for dotnet by itself</span></span>

<span data-ttu-id="9e87a-127">次のオプションは、`dotnet` 単独のものです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="9e87a-128">たとえば、`dotnet --info` のようにします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="9e87a-129">環境に関する情報が出力されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="9e87a-130">現在のオペレーティング システムや .NET Core バージョンのコミット SHA など、.NET Core インストールとコンピューター環境に関する詳細を出力します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="9e87a-131">使用中の .NET Core SDK のバージョンを印刷します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="9e87a-132">インストールされている .NET Core ランタイムの一覧が出力されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="9e87a-133">x86 バージョンの SDK には x86 ランタイムのみが登録され、x64 バージョンの SDK には x64 ランタイムのみが登録されています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="9e87a-134">インストールされている .NET Core SDK の一覧が出力されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9e87a-135">使用できるコマンドの一覧が出力されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="9e87a-136">コマンドを実行するための SDK のオプション</span><span class="sxs-lookup"><span data-stu-id="9e87a-136">SDK options for running a command</span></span>

<span data-ttu-id="9e87a-137">次のオプションは、コマンドを指定した `dotnet` 用です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="9e87a-138">たとえば、`dotnet build --help` のようにします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="9e87a-139">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9e87a-140">コマンドの詳細レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9e87a-141">指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9e87a-142">すべてのコマンドでサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="9e87a-142">Not supported in every command.</span></span> <span data-ttu-id="9e87a-143">このオプションを使用できるかどうかについては、そのコマンド ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9e87a-144">`dotnet build --help` など、特定のコマンドのドキュメントを出力します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="9e87a-145">各コマンドには、そのコマンドに固有のオプションが定義されています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="9e87a-146">使用できるオプションの一覧については、そのコマンドのページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="9e87a-147">ランタイム オプション</span><span class="sxs-lookup"><span data-stu-id="9e87a-147">Runtime options</span></span>

<span data-ttu-id="9e87a-148">次のオプションは、`dotnet` でアプリケーションを実行するときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="9e87a-149">たとえば、`dotnet myapp.dll --roll-forward Major` のようにします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="9e87a-150">プローブ ポリシーとプローブするアセンブリを含むパスです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="9e87a-151">追加の *.deps.json* ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="9e87a-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="9e87a-152">*deps.json* ファイルには、依存関係、コンパイル依存関係、アセンブリ競合に対処するためのバージョン情報の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="9e87a-153">詳細については、GitHub の「[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)」 (ランタイム構成ファイル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="9e87a-154">*deps.json* ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="9e87a-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="9e87a-155">*deps. json* ファイルは、アプリケーションの実行に必要な依存関係に関する情報を含む構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="9e87a-156">このファイルは、.NET Core SDK によって生成されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-156">This file is generated by the .NET Core SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="9e87a-157">*runtimeconfig.json* ファイルへのパス。</span><span class="sxs-lookup"><span data-stu-id="9e87a-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="9e87a-158">*runtimeconfig.json* ファイルは、ランタイム設定を含む構成ファイルです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="9e87a-159">詳細については、「[.NET Core ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-159">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="9e87a-160">**`--roll-forward <SETTING>`** **.NET Core SDK 3.0 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="9e87a-161">アプリにロール フォ ワードを適用する方法を制御します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="9e87a-162">`SETTING` には次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="9e87a-163">指定しない場合の既定は、`Minor` です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="9e87a-164">`LatestPatch` - 最新のパッチ バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="9e87a-165">これで、マイナー バージョンのロールフォワードが無効になります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="9e87a-166">`Minor` - 要求されたマイナー バージョンが見つからない場合は、それよりも高い最小マイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="9e87a-167">要求されたマイナー バージョンが存在する場合は、LatestPatch ポリシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="9e87a-168">`Major` - 要求されたメジャー バージョンが見つからない場合は、それよりも高い最小メジャー バージョンで最小マイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="9e87a-169">要求されたメジャー バージョンが存在する場合は、Minor ポリシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="9e87a-170">`LatestMinor` - 要求されたマイナー バージョンが存在する場合でも、最上位のマイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="9e87a-171">コンポーネント ホスティング シナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="9e87a-172">`LatestMajor` - 要求されたメジャーが存在する場合でも、最上位のメジャー バージョンで最上位のマイナー バージョンにロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="9e87a-173">コンポーネント ホスティング シナリオを対象としています。</span><span class="sxs-lookup"><span data-stu-id="9e87a-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="9e87a-174">`Disable` - ロール フォワードしません。</span><span class="sxs-lookup"><span data-stu-id="9e87a-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="9e87a-175">指定されたバージョンにのみバインドします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-175">Only bind to specified version.</span></span> <span data-ttu-id="9e87a-176">このポリシーは、最新のパッチにロールフォワードする機能が無効になるため、一般的な使用にはお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="9e87a-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="9e87a-177">この値はテスト用にのみ推奨されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="9e87a-178">`Disable` を除いて、すべての設定は使用できる最高のパッチ バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="9e87a-179">ロール フォワード動作は、プロジェクト ファイル プロパティ、ランタイム構成ファイル プロパティ、および環境変数でも構成できます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="9e87a-180">詳細については、「[メジャーバージョン ランタイムのロールフォワード](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="9e87a-181">**`--roll-forward-on-no-candidate-fx <N>`** **.NET Core 2.x SDK で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="9e87a-182">必要な共有フレームワークが利用できない場合の動作を定義します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="9e87a-183">`N` には以下があります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-183">`N` can be:</span></span>

  - <span data-ttu-id="9e87a-184">`0` - マイナー バージョンのロールフォワードでも無効にします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="9e87a-185">`1` - マイナー バージョンはロール フォワードしますが、メジャー バージョンはしません。</span><span class="sxs-lookup"><span data-stu-id="9e87a-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="9e87a-186">これが既定の動作です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-186">This is the default behavior.</span></span>
  - <span data-ttu-id="9e87a-187">`2` - マイナー バージョンとメジャー バージョンをロール フォワードします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="9e87a-188">詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="9e87a-189">.NET Core 3.0 以降では、このオプションは `--roll-forward` に置き換えられており、代わりにこのオプションを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="9e87a-190">アプリケーションを実行するために使用する .NET Core ランタイムのバージョン。</span><span class="sxs-lookup"><span data-stu-id="9e87a-190">Version of the .NET Core runtime to use to run the application.</span></span>

  <span data-ttu-id="9e87a-191">このオプションは、アプリケーションの `.runtimeconfig.json` ファイル内の最初のフレームワーク参照のバージョンをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="9e87a-192">つまり、予期したとおりに動作するのは、フレームワーク参照が 1 つの場合のみです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="9e87a-193">アプリケーションに複数のフレームワーク参照がある場合、このオプションを使用するとエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="9e87a-194">dotnet コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="9e87a-195">全般</span><span class="sxs-lookup"><span data-stu-id="9e87a-195">General</span></span>

| <span data-ttu-id="9e87a-196">コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-196">Command</span></span>                                       | <span data-ttu-id="9e87a-197">関数</span><span class="sxs-lookup"><span data-stu-id="9e87a-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="9e87a-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="9e87a-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="9e87a-199">.NET Core アプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-199">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="9e87a-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="9e87a-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="9e87a-201">ビルドによって起動されたサーバーとやり取りします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="9e87a-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="9e87a-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="9e87a-203">クリーン ビルド出力です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="9e87a-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="9e87a-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="9e87a-205">コマンドのより詳細なドキュメントをオンラインで表示します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="9e87a-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="9e87a-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="9e87a-207">有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="9e87a-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9e87a-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="9e87a-209">MSBuild コマンド ラインへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="9e87a-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9e87a-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="9e87a-211">指定されたテンプレートの C# または F# プロジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="9e87a-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="9e87a-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="9e87a-213">コードの NuGet パッケージを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="9e87a-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9e87a-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="9e87a-215">.NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="9e87a-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="9e87a-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="9e87a-217">指定されたアプリケーションの依存関係を復元します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="9e87a-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="9e87a-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="9e87a-219">ソースからアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="9e87a-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9e87a-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="9e87a-221">ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。</span><span class="sxs-lookup"><span data-stu-id="9e87a-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="9e87a-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="9e87a-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="9e87a-223">ランタイム パッケージ ストアにアセンブリを格納します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="9e87a-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="9e87a-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="9e87a-225">テスト ランナーを使用してテストを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="9e87a-226">プロジェクト参照</span><span class="sxs-lookup"><span data-stu-id="9e87a-226">Project references</span></span>

<span data-ttu-id="9e87a-227">コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-227">Command</span></span> | <span data-ttu-id="9e87a-228">関数</span><span class="sxs-lookup"><span data-stu-id="9e87a-228">Function</span></span>
--- | ---
[<span data-ttu-id="9e87a-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="9e87a-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="9e87a-230">プロジェクト参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-230">Adds a project reference.</span></span>
[<span data-ttu-id="9e87a-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="9e87a-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="9e87a-232">プロジェクト参照をリストします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-232">Lists project references.</span></span>
[<span data-ttu-id="9e87a-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="9e87a-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="9e87a-234">プロジェクト参照を削除します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="9e87a-235">NuGet パッケージ</span><span class="sxs-lookup"><span data-stu-id="9e87a-235">NuGet packages</span></span>

<span data-ttu-id="9e87a-236">コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-236">Command</span></span> | <span data-ttu-id="9e87a-237">関数</span><span class="sxs-lookup"><span data-stu-id="9e87a-237">Function</span></span>
--- | ---
[<span data-ttu-id="9e87a-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="9e87a-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="9e87a-239">NuGet パッケージを追加します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="9e87a-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="9e87a-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="9e87a-241">NuGet パッケージを削除します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="9e87a-242">NuGet コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-242">NuGet commands</span></span>

<span data-ttu-id="9e87a-243">コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-243">Command</span></span> | <span data-ttu-id="9e87a-244">関数</span><span class="sxs-lookup"><span data-stu-id="9e87a-244">Function</span></span>
--- | ---
[<span data-ttu-id="9e87a-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="9e87a-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="9e87a-246">サーバーからパッケージを削除または一覧から削除します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="9e87a-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="9e87a-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="9e87a-248">パッケージをサーバーにプッシュして発行します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="9e87a-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="9e87a-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="9e87a-250">HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="9e87a-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="9e87a-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="9e87a-252">NuGet ソースを追加します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="9e87a-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="9e87a-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="9e87a-254">NuGet ソースを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="9e87a-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="9e87a-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="9e87a-256">NuGet ソースを有効にします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="9e87a-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="9e87a-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="9e87a-258">構成されている NuGet ソースをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="9e87a-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="9e87a-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="9e87a-260">NuGet ソースを削除します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="9e87a-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="9e87a-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="9e87a-262">NuGet ソースを更新します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="9e87a-263">グローバル、ツールパス、およびローカル ツールのコマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="9e87a-264">ツールは、NuGet パッケージからインストールされ、コマンド プロンプトから呼び出されるコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="9e87a-265">ツールは自分で作成することも、サードパーティによって作成されたツールをインストールすることもできます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="9e87a-266">ツールは、グローバル ツール、ツールパス ツール、およびローカル ツールとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="9e87a-267">詳細については、[.NET Core ツールの概要](global-tools.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-267">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="9e87a-268">グローバル ツールとツールパス ツールは、.NET Core SDK 2.1 以降使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="9e87a-269">ローカル ツールは、.NET Core SDK 3.0 以降使用できます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="9e87a-270">コマンド</span><span class="sxs-lookup"><span data-stu-id="9e87a-270">Command</span></span> | <span data-ttu-id="9e87a-271">関数</span><span class="sxs-lookup"><span data-stu-id="9e87a-271">Function</span></span>
--- | ---
[<span data-ttu-id="9e87a-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="9e87a-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="9e87a-273">ツールをお使いのコンピューターにインストールします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="9e87a-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="9e87a-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="9e87a-275">コンピューターに現在インストールされているグローバル、ツールパス、またはローカル ツールをすべて一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="9e87a-276">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="9e87a-276">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="9e87a-277">ツールをお使いのコンピューターからアンインストールします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-277">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="9e87a-278">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="9e87a-278">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="9e87a-279">コンピューターにインストールされているツールを更新します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-279">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="9e87a-280">その他のツール</span><span class="sxs-lookup"><span data-stu-id="9e87a-280">Additional tools</span></span>

<span data-ttu-id="9e87a-281">.NET Core SDK 2.1.300 以降では、`DotnetCliToolReference` を使用してプロジェクト単位でのみ入手可能であった複数のツールを .NET Core SDK の一部として入手できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="9e87a-281">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="9e87a-282">これらのツールを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-282">These tools are listed in the following table:</span></span>

| <span data-ttu-id="9e87a-283">ツール</span><span class="sxs-lookup"><span data-stu-id="9e87a-283">Tool</span></span>                                              | <span data-ttu-id="9e87a-284">関数</span><span class="sxs-lookup"><span data-stu-id="9e87a-284">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="9e87a-285">dev-certs</span><span class="sxs-lookup"><span data-stu-id="9e87a-285">dev-certs</span></span>                                         | <span data-ttu-id="9e87a-286">開発証明書を作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-286">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="9e87a-287">ef</span><span class="sxs-lookup"><span data-stu-id="9e87a-287">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="9e87a-288">Entity Framework Core コマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-288">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="9e87a-289">sql-cache</span><span class="sxs-lookup"><span data-stu-id="9e87a-289">sql-cache</span></span>                                         | <span data-ttu-id="9e87a-290">SQL Server キャッシュ コマンドライン ツールです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-290">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="9e87a-291">user-secrets</span><span class="sxs-lookup"><span data-stu-id="9e87a-291">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="9e87a-292">開発ユーザーのシークレットを管理します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-292">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="9e87a-293">watch</span><span class="sxs-lookup"><span data-stu-id="9e87a-293">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="9e87a-294">ファイルが変化するとコマンドを実行するファイル ウォッチャーを起動します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-294">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="9e87a-295">各ツールの詳細については、`dotnet <tool-name> --help` と入力してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-295">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="9e87a-296">使用例</span><span class="sxs-lookup"><span data-stu-id="9e87a-296">Examples</span></span>

<span data-ttu-id="9e87a-297">新しい .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-297">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="9e87a-298">指定されたディレクトリにプロジェクトとその依存関係をビルドします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-298">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="9e87a-299">アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-299">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="9e87a-300">環境変数</span><span class="sxs-lookup"><span data-stu-id="9e87a-300">Environment variables</span></span>

- <span data-ttu-id="9e87a-301">`DOTNET_ROOT`、`DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="9e87a-301">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="9e87a-302">.NET Core ランタイムが既定の場所にインストールされていない場合、それらの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-302">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="9e87a-303">Windows 上の既定の場所は `C:\Program Files\dotnet` です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-303">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="9e87a-304">Linux と macOS 上の既定の場所は `/usr/share/dotnet` です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-304">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="9e87a-305">この環境変数は、生成された実行可能ファイル (apphosts) を介してアプリを実行する場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-305">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="9e87a-306">64 ビット OS 上で 32 ビット実行可能ファイルを実行する場合は、代わりに `DOTNET_ROOT(x86)` が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-306">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="9e87a-307">グローバル パッケージ フォルダー。</span><span class="sxs-lookup"><span data-stu-id="9e87a-307">The global packages folder.</span></span> <span data-ttu-id="9e87a-308">設定されていない場合は、既定で `~/.nuget/packages` (Unix の場合) または `%userprofile%\.nuget\packages` (Windows の場合) になります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-308">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="9e87a-309">ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-309">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="9e87a-310">最初の実行時に .NET Core のウェルカム メッセージとテレメトリ メッセージを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-310">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="9e87a-311">`true` に設定すると、これらのメッセージは表示されません (値 `true`、`1`、または `yes` が受け入れられます)。`false` に設定すると許可されます (値 `false`、`0`、または `no` が受け入れられます)。</span><span class="sxs-lookup"><span data-stu-id="9e87a-311">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="9e87a-312">設定しない場合、既定値は `false` であり、最初の実行時にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-312">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="9e87a-313">このフラグはテレメトリには影響しません (テレメトリの送信のオプトアウトについては `DOTNET_CLI_TELEMETRY_OPTOUT` を参照)。</span><span class="sxs-lookup"><span data-stu-id="9e87a-313">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="9e87a-314">.NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="9e87a-315">`true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。</span><span class="sxs-lookup"><span data-stu-id="9e87a-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="9e87a-316">それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。</span><span class="sxs-lookup"><span data-stu-id="9e87a-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="9e87a-317">設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="9e87a-318">.NET Core ランタイム、共有フレームワーク、または SDK がグローバルな場所から解決されるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="9e87a-319">設定されていない場合、既定値は 1 (論理 `true`) です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-319">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="9e87a-320">グローバルな場所から解決せず、.NET Core インストールを分離するには、0 (論理 `false`) に設定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-320">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="9e87a-321">複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="9e87a-322">`DOTNET_ROLL_FORWARD` **.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-322">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="9e87a-323">ロール フォワード動作を決定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-323">Determines roll forward behavior.</span></span> <span data-ttu-id="9e87a-324">詳細については、この記事で前述した `--roll-forward` オプションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-324">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="9e87a-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="9e87a-326">`1` (有効) に設定した場合は、リリース バージョンからプレリリース バージョンへのロール フォワードが有効になります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-326">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="9e87a-327">既定 (`0` - 無効) では、.NET Core ランタイムのリリース バージョンが要求されるとき、インストールされているリリース バージョンのみがロール フォワードによって考慮されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-327">By default (`0` - disabled), when a release version of .NET Core runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="9e87a-328">詳細については、「[Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)」(ロールフォワード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-328">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="9e87a-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **.NET Core 2.x で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="9e87a-330">`0` に設定されている場合、マイナー バージョンのロールフォワードを無効にします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-330">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="9e87a-331">詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-331">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="9e87a-332">この設定は、.NET Core 3.0 では、`DOTNET_ROLL_FORWARD` によって置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-332">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="9e87a-333">代わりに、新しい設定を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-333">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="9e87a-334">`en-us` などのロケール値を使用して、CLI UI の言語を設定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-334">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="9e87a-335">サポートされている値は、Visual Studio の場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-335">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="9e87a-336">詳細については、[Visual Studio のインストール ドキュメント](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)のインストーラーの言語を変更する方法に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-336">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="9e87a-337">.NET リソース マネージャーの規則が適用されるため、完全一致を選択する必要はありません。`CultureInfo` ツリーで子孫を選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-337">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="9e87a-338">たとえば、`fr-CA` に設定すると、CLI によって `fr` の翻訳が検索され、使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-338">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="9e87a-339">サポートされていない言語に設定すると、CLI は英語にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-339">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="9e87a-340">GUI 対応の生成された実行可能ファイルの場合、通常は特定のクラスのエラーに対して表示されるダイアログ ポップアップが無効になります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-340">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="9e87a-341">この場合、`stderr` にのみ書き込まれ、終了します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-341">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="9e87a-342">CLI オプション `--additional-deps` に相当します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-342">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="9e87a-343">検出された RID をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="9e87a-343">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="9e87a-344">アセンブリの解決がフォールバックする "共有ストア" の場所。</span><span class="sxs-lookup"><span data-stu-id="9e87a-344">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="9e87a-345">スタートアップ フックを読み込み、実行するアセンブリの一覧。</span><span class="sxs-lookup"><span data-stu-id="9e87a-345">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="9e87a-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="9e87a-347">単一ファイル アプリケーションが実行前に抽出されるディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-347">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="9e87a-348">詳細については、「[単一ファイルの実行可能ファイル](../whats-new/dotnet-core-3-0.md#single-file-executables)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9e87a-348">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="9e87a-349">`COREHOST_TRACE`、`COREHOST_TRACEFILE`、`COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="9e87a-349">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="9e87a-350">`dotnet.exe`、`hostfxr`、`hostpolicy` などのホスティング コンポーネントからの診断トレースを制御します。</span><span class="sxs-lookup"><span data-stu-id="9e87a-350">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="9e87a-351">`COREHOST_TRACE=[0/1]` - 既定値は `0` で、トレースは無効です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-351">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="9e87a-352">`1` に設定すると、診断トレースが有効になります。</span><span class="sxs-lookup"><span data-stu-id="9e87a-352">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="9e87a-353">`COREHOST_TRACEFILE=<file path>` - `COREHOST_TRACE=1` によってトレースが有効になっている場合のみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-353">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="9e87a-354">設定すると、指定したファイルにトレース情報が書き込まれます。それ以外の場合、トレース情報は `stderr` に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-354">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="9e87a-355">**.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-355">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="9e87a-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - 規定値は `4` です。</span><span class="sxs-lookup"><span data-stu-id="9e87a-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="9e87a-357">この設定は、`COREHOST_TRACE=1` によってトレースが有効になっている場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-357">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="9e87a-358">**.NET Core 3.x 以降で使用できます。**</span><span class="sxs-lookup"><span data-stu-id="9e87a-358">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="9e87a-359">`4` - すべてのトレース情報が書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-359">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="9e87a-360">`3` - 情報、警告、およびエラー メッセージのみが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-360">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="9e87a-361">`2` - 警告およびエラー メッセージのみが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-361">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="9e87a-362">`1` - エラー メッセージのみが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-362">`1` - only error messages are written</span></span>

  <span data-ttu-id="9e87a-363">アプリケーションの起動に関して詳しいトレース情報を取得する一般的な方法は、`COREHOST_TRACE=1` と `COREHOST_TRACEFILE=host_trace.txt` を設定してアプリケーションを実行することです。</span><span class="sxs-lookup"><span data-stu-id="9e87a-363">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="9e87a-364">詳細情報を含む新しいファイル `host_trace.txt` が現在のディレクトリに作成されます。</span><span class="sxs-lookup"><span data-stu-id="9e87a-364">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e87a-365">関連項目</span><span class="sxs-lookup"><span data-stu-id="9e87a-365">See also</span></span>

- [<span data-ttu-id="9e87a-366">ランタイム構成ファイル</span><span class="sxs-lookup"><span data-stu-id="9e87a-366">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="9e87a-367">.NET Core ランタイム構成設定</span><span class="sxs-lookup"><span data-stu-id="9e87a-367">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
