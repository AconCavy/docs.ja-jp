---
title: dotnet nuget locals コマンド
description: dotnet nuget locals コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 3fdd7d946b08b4c18cfaeb65013de259b927a7fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503684"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="6de38-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="6de38-103">dotnet nuget locals</span></span>

<span data-ttu-id="6de38-104">**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="6de38-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6de38-105">name</span><span class="sxs-lookup"><span data-stu-id="6de38-105">Name</span></span>

<span data-ttu-id="6de38-106">`dotnet nuget locals` - ローカル NuGet リソースをクリアまたはリストします。</span><span class="sxs-lookup"><span data-stu-id="6de38-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6de38-107">構文</span><span class="sxs-lookup"><span data-stu-id="6de38-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="6de38-108">[説明]</span><span class="sxs-lookup"><span data-stu-id="6de38-108">Description</span></span>

<span data-ttu-id="6de38-109">`dotnet nuget locals` コマンドは、HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーのローカルの NuGet リソースをクリアまたは一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="6de38-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="6de38-110">引数</span><span class="sxs-lookup"><span data-stu-id="6de38-110">Arguments</span></span>

- **`CACHE_LOCATION`**

  <span data-ttu-id="6de38-111">一覧表示またはクリアするキャッシュの場所。</span><span class="sxs-lookup"><span data-stu-id="6de38-111">The cache location to list or clear.</span></span> <span data-ttu-id="6de38-112">次のいずれかの値を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="6de38-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="6de38-113">`all` - 指定された操作をすべてのキャッシュの種類 (HTTP 要求キャッシュ、グローバル パッケージ キャッシュ、一時的なキャッシュ) に適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6de38-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="6de38-114">`http-cache` - 指定した操作を HTTP 要求キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6de38-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="6de38-115">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="6de38-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="6de38-116">`global-packages` - 指定した操作をグローバル パッケージ キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6de38-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="6de38-117">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="6de38-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="6de38-118">`temp` - 指定した操作を一時キャッシュのみに適用することを指定します。</span><span class="sxs-lookup"><span data-stu-id="6de38-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="6de38-119">その他のキャッシュの場所には影響しません。</span><span class="sxs-lookup"><span data-stu-id="6de38-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="6de38-120">オプション</span><span class="sxs-lookup"><span data-stu-id="6de38-120">Options</span></span>

- **`--force-english-output`**

  <span data-ttu-id="6de38-121">インバリアントの英語ベースのカルチャを使用して、アプリケーションの実行を強制します。</span><span class="sxs-lookup"><span data-stu-id="6de38-121">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6de38-122">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="6de38-122">Prints out a short help for the command.</span></span>

- **`-c|--clear`**

  <span data-ttu-id="6de38-123">クリア オプションは、指定されたキャッシュの種類でクリア操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="6de38-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="6de38-124">キャッシュ ディレクトリの内容は、再帰的に削除されます。</span><span class="sxs-lookup"><span data-stu-id="6de38-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="6de38-125">実行中のユーザー/グループには、キャッシュ ディレクトリ内のファイルへのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="6de38-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="6de38-126">アクセス許可がない場合は、ファイル/フォルダーがクリアされなかったことを示すエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="6de38-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

- **`-l|--list`**

  <span data-ttu-id="6de38-127">一覧表示オプションは、指定されたキャッシュの種類の場所を表示するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="6de38-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="6de38-128">例</span><span class="sxs-lookup"><span data-stu-id="6de38-128">Examples</span></span>

- <span data-ttu-id="6de38-129">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) のパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="6de38-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- <span data-ttu-id="6de38-130">ローカルの HTTP キャッシュ ディレクトリのパスを表示します。</span><span class="sxs-lookup"><span data-stu-id="6de38-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- <span data-ttu-id="6de38-131">すべてのローカルのキャッシュ ディレクトリ (HTTP キャッシュ ディレクトリ、グローバル パッケージ キャッシュ ディレクトリ、および一時的なキャッシュ ディレクトリ) からすべてのファイルをクリアします。</span><span class="sxs-lookup"><span data-stu-id="6de38-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- <span data-ttu-id="6de38-132">ローカルのグローバル キャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="6de38-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- <span data-ttu-id="6de38-133">ローカルの一時的なキャッシュ ディレクトリのファイルをすべてクリアします。</span><span class="sxs-lookup"><span data-stu-id="6de38-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="6de38-134">トラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="6de38-134">Troubleshooting</span></span>

<span data-ttu-id="6de38-135">`dotnet nuget locals` コマンドを使うときの一般的な問題やエラーについては、「[Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache)」 (NuGet キャッシュを管理する) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6de38-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
