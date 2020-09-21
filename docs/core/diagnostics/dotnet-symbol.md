---
title: dotnet-symbol - .NET Core
description: dotnet-symbol コマンドライン ツールのインストールおよび使用。
ms.date: 08/26/2020
ms.openlocfilehash: 5a96306fc96525b00e57eda089a45b730a7e3e8c
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679189"
---
# <a name="symbol-downloader-dotnet-symbol"></a><span data-ttu-id="b1dd9-103">シンボル ダウンローダー (dotnet-symbol)</span><span class="sxs-lookup"><span data-stu-id="b1dd9-103">Symbol downloader (dotnet-symbol)</span></span>

<span data-ttu-id="b1dd9-104">**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="b1dd9-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-symbol"></a><span data-ttu-id="b1dd9-105">dotnet-symbol をインストールする</span><span class="sxs-lookup"><span data-stu-id="b1dd9-105">Install dotnet-symbol</span></span>

<span data-ttu-id="b1dd9-106">`dotnet-symbol` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-symbol)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-106">To install the latest release version of the `dotnet-symbol` [NuGet package](https://www.nuget.org/packages/dotnet-symbol), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-symbol
```

## <a name="synopsis"></a><span data-ttu-id="b1dd9-107">構文</span><span class="sxs-lookup"><span data-stu-id="b1dd9-107">Synopsis</span></span>

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a><span data-ttu-id="b1dd9-108">説明</span><span class="sxs-lookup"><span data-stu-id="b1dd9-108">Description</span></span>

<span data-ttu-id="b1dd9-109">`dotnet-symbol` グローバル ツールによって、コア ダンプとミニダンプのデバッグに必要なファイル (シンボル、DAC、モジュールなど) をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-109">The `dotnet-symbol` global tool downloads files (symbols, DAC, modules, etc.) needed for debugging core dumps and minidumps.</span></span> <span data-ttu-id="b1dd9-110">これは、別のコンピューターでキャプチャされたダンプをデバッグするときに便利です。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-110">This can be useful when debugging dumps captured on another machine.</span></span> <span data-ttu-id="b1dd9-111">`dotnet-symbol` を使用すると、ダンプを分析するために必要なモジュールとシンボルをダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-111">`dotnet-symbol` can download modules and symbols needed to analyze the dump.</span></span>

## <a name="options"></a><span data-ttu-id="b1dd9-112">オプション</span><span class="sxs-lookup"><span data-stu-id="b1dd9-112">Options</span></span>

- **`--microsoft-symbol-server`**

  <span data-ttu-id="b1dd9-113">'http://msdl.microsoft.com/download/symbols ' シンボル サーバー パス (既定) を追加します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-113">Add 'http://msdl.microsoft.com/download/symbols' symbol server path (default).</span></span>

- **`--server-path <symbol server path>`**

  <span data-ttu-id="b1dd9-114">サーバー パスにシンボル サーバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-114">Add a symbol server to the server path.</span></span>

- **`authenticated-server-path <pat> <server path>`**

  <span data-ttu-id="b1dd9-115">個人用アクセス トークン (PAT) を使用して、認証済みのシンボル サーバーをサーバー パスに追加します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-115">Add an authenticated symbol server to the server path using a personal access token (PAT).</span></span>

- **`--cache-directory <file cache directory>`**

  <span data-ttu-id="b1dd9-116">キャッシュ ディレクトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-116">Adds a cache directory.</span></span>

- **`--recurse-subdirectories`**

  <span data-ttu-id="b1dd9-117">すべてのサブディレクトリの入力ファイルを処理します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-117">Process input files in all subdirectories.</span></span>

- **`--host-only`**

  <span data-ttu-id="b1dd9-118">lldb でコア ダンプを読み込むために必要なホスト プログラム (つまり dotnet) のみをダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-118">Download only the host program (i.e. dotnet) that lldb needs for loading core dumps.</span></span>

- **`--symbols`**

  <span data-ttu-id="b1dd9-119">シンボル ファイル (.pdb、.dbg、.dwarf) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-119">Download symbol files (.pdb, .dbg, .dwarf).</span></span>

- **`--modules`**

  <span data-ttu-id="b1dd9-120">モジュール ファイル (.dll、.so、.dylib) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-120">Download the module files (.dll, .so, .dylib).</span></span>

- **`--debugging`**

  <span data-ttu-id="b1dd9-121">特別なデバッグ モジュール (DAC、DBI、SOS) をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-121">Download the special debugging modules (DAC, DBI, SOS).</span></span>

- **`--windows-pdbs`**

  <span data-ttu-id="b1dd9-122">ポータブル PDB も使用できる場合は、Windows PDB を強制的にダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-122">Force the downloading of the Windows PDBs when Portable PDBs are also available.</span></span>

- **`-o, --output <output directory>`**

  <span data-ttu-id="b1dd9-123">出力ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-123">Set the output directory.</span></span> <span data-ttu-id="b1dd9-124">それ以外の場合は、入力ファイルの次に書き込みます (既定)。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-124">Otherwise, write next to the input file (default).</span></span>

- **`-d, --diagnostics`**

  <span data-ttu-id="b1dd9-125">診断出力を有効にします。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-125">Enable diagnostic output.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b1dd9-126">コマンド ライン ヘルプを表示します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-126">Shows command-line help.</span></span>

## <a name="download-symbols"></a><span data-ttu-id="b1dd9-127">シンボルをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="b1dd9-127">Download symbols</span></span>

<span data-ttu-id="b1dd9-128">ダンプ ファイルに対して `dotnet-symbol` を実行すると、既定では、マネージド アセンブリを含むダンプのデバッグに必要なすべてのモジュール、シンボル、および DAC (または DBI) ファイルがダウンロードされます。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-128">Running `dotnet-symbol` against a dump file will, by default, download all the modules, symbols, and DAC/DBI files needed to debug the dump including the managed assemblies.</span></span> <span data-ttu-id="b1dd9-129">SOS で必要に応じてシンボルをダウンロードできるようになったため、ほとんどの Linux コア ダンプは、ホスト (dotnet) モジュールとデバッグ モジュールのみを含む lldb を使用して分析できます。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-129">Because SOS can now download symbols when needed, most Linux core dumps can be analyzed using lldb with only the host (dotnet) and debugging modules.</span></span> <span data-ttu-id="b1dd9-130">lldb を使用してコア ダンプを診断するために必要なこれらのファイルを取得するには、次のように実行します。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-130">To get these files necessary for diagnosing a core dump with lldb run:</span></span>

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a><span data-ttu-id="b1dd9-131">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b1dd9-131">Troubleshoot</span></span>

- <span data-ttu-id="b1dd9-132">シンボルのダウンロード中の 404 Not Found。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-132">404 Not Found while downloading symbols.</span></span>

   <span data-ttu-id="b1dd9-133">シンボルのダウンロードは、[公式 Web サイト](https://dotnet.microsoft.com/download/dotnet-core)などの公式チャネルを通じて取得された公式の .NET Core ランタイム バージョンと、[dotnet インストール スクリプト内の既定のソース](../tools/dotnet-install-script.md)でのみサポートされています。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-133">Symbol download is only supported for official .NET Core runtime versions acquired through official channels such as [the official web site](https://dotnet.microsoft.com/download/dotnet-core) and the [default sources in the dotnet installation scripts](../tools/dotnet-install-script.md).</span></span> <span data-ttu-id="b1dd9-134">デバッグ ファイルのダウンロード中に 404 エラーが発生した場合は、ダンプが別のソースの .NET Core ランタイムを使って作成されたことが示されている可能性があります。たとえば、ソースからローカルに構築されたものや、特定の Linux ディストリビューション用のもの、または archlinux のようなコミュニティ サイトから作成されたものです。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-134">A 404 error while downloading debugging files may indicate that the dump was created with a .NET Core runtime from another source, such as one built from source locally or for a particular Linux distro, or from community sites like archlinux.</span></span> <span data-ttu-id="b1dd9-135">このような場合は、デバッグに必要なファイル (dotnet、libcoreclr.so、libmscordaccore.so) を、それらのソースから、またはダンプ ファイルが作成された環境からコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b1dd9-135">In such cases, file necessary for debugging (dotnet, libcoreclr.so, and libmscordaccore.so) should be copied from those sources or from the environment the dump file was created in.</span></span>
