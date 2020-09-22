---
title: dotnet add package コマンド
description: "'dotnet add package' コマンドは、NuGet パッケージ参照をプロジェクトに追加する便利なオプションを提供します。"
ms.date: 02/14/2020
ms.openlocfilehash: 1bdda241c1301b926ba2fd322f969407038b7b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538069"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="37c20-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="37c20-103">dotnet add package</span></span>

<span data-ttu-id="37c20-104">**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="37c20-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="37c20-105">名前</span><span class="sxs-lookup"><span data-stu-id="37c20-105">Name</span></span>

<span data-ttu-id="37c20-106">`dotnet add package` - プロジェクト ファイルにパッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="37c20-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37c20-107">構文</span><span class="sxs-lookup"><span data-stu-id="37c20-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="37c20-108">説明</span><span class="sxs-lookup"><span data-stu-id="37c20-108">Description</span></span>

<span data-ttu-id="37c20-109">`dotnet add package` コマンドは、プロジェクト ファイルにパッケージ参照を追加する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="37c20-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="37c20-110">このコマンドの実行後に、パッケージがプロジェクト内のフレームワークと互換性があることを確認する互換性チェックがあります。</span><span class="sxs-lookup"><span data-stu-id="37c20-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="37c20-111">互換性チェックに合格すると、`<PackageReference>` 要素がプロジェクト ファイルに追加されて、[dotnet restore](dotnet-restore.md) が実行されます。</span><span class="sxs-lookup"><span data-stu-id="37c20-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="37c20-112">たとえば、`Newtonsoft.Json` を *ToDo.csproj* に追加すると、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="37c20-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="37c20-113">この *ToDo.csproj* ファイルには、参照されるパッケージの [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="37c20-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="37c20-114">暗黙的な復元</span><span class="sxs-lookup"><span data-stu-id="37c20-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="37c20-115">引数</span><span class="sxs-lookup"><span data-stu-id="37c20-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="37c20-116">プロジェクト ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="37c20-116">Specifies the project file.</span></span> <span data-ttu-id="37c20-117">指定されていない場合、現在のディレクトリで検索されます。</span><span class="sxs-lookup"><span data-stu-id="37c20-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="37c20-118">追加するパッケージ参照。</span><span class="sxs-lookup"><span data-stu-id="37c20-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="37c20-119">オプション</span><span class="sxs-lookup"><span data-stu-id="37c20-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="37c20-120">特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、パッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="37c20-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="37c20-121">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="37c20-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="37c20-122">コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。</span><span class="sxs-lookup"><span data-stu-id="37c20-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="37c20-123">.NET Core 2.1 SDK バージョン 2.1.400 以降で使用可能です。</span><span class="sxs-lookup"><span data-stu-id="37c20-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="37c20-124">復元のプレビューと互換性チェックを実行せずにパッケージ参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="37c20-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="37c20-125">パッケージの復元先となるディレクトリ。</span><span class="sxs-lookup"><span data-stu-id="37c20-125">The directory where to restore the packages.</span></span> <span data-ttu-id="37c20-126">既定のパッケージ復元場所は、Windows の場合は `%userprofile%\.nuget\packages`、macOS と Linux の場合は `~/.nuget/packages` です。</span><span class="sxs-lookup"><span data-stu-id="37c20-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="37c20-127">詳細については、[NuGet でのグローバル パッケージ、キャッシュ、および一時フォルダーの管理](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37c20-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="37c20-128">復元操作時に使用する NuGet パッケージ ソースの URI。</span><span class="sxs-lookup"><span data-stu-id="37c20-128">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="37c20-129">パッケージのバージョン。</span><span class="sxs-lookup"><span data-stu-id="37c20-129">Version of the package.</span></span> <span data-ttu-id="37c20-130">[NuGet パッケージのバージョン管理](/nuget/reference/package-versioning)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="37c20-130">See [NuGet package versioning](/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="37c20-131">使用例</span><span class="sxs-lookup"><span data-stu-id="37c20-131">Examples</span></span>

- <span data-ttu-id="37c20-132">`Newtonsoft.Json` NuGet パッケージをプロジェクトに追加する:</span><span class="sxs-lookup"><span data-stu-id="37c20-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="37c20-133">特定バージョンのパッケージをプロジェクトに追加する:</span><span class="sxs-lookup"><span data-stu-id="37c20-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="37c20-134">特定の NuGet ソースを使用してパッケージを追加する:</span><span class="sxs-lookup"><span data-stu-id="37c20-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="37c20-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="37c20-135">See also</span></span>

- [<span data-ttu-id="37c20-136">NuGet でグローバル パッケージ、キャッシュ、および一時フォルダーを管理する</span><span class="sxs-lookup"><span data-stu-id="37c20-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="37c20-137">NuGet パッケージのバージョン管理</span><span class="sxs-lookup"><span data-stu-id="37c20-137">NuGet package versioning</span></span>](/nuget/reference/package-versioning)
