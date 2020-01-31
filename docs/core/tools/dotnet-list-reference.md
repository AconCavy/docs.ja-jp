---
title: dotnet list reference コマンド
description: dotnet list 参照コマンドは、プロジェクト間参照を列挙する便利なオプションを提供します。
ms.date: 06/26/2019
ms.openlocfilehash: 496cbcd8fa4d921e30b363904ad0273bd5ebacd5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733223"
---
# <a name="dotnet-list-reference"></a><span data-ttu-id="05a98-103">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="05a98-103">dotnet list reference</span></span>

<span data-ttu-id="05a98-104">**この記事の対象:** ✔️ .NET Core 1.x SDK 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="05a98-104">**This article applies to:** ✔️ .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="05a98-105">名前</span><span class="sxs-lookup"><span data-stu-id="05a98-105">Name</span></span>

<span data-ttu-id="05a98-106">`dotnet list reference` - プロジェクト間参照を列挙します。</span><span class="sxs-lookup"><span data-stu-id="05a98-106">`dotnet list reference` - Lists project-to-project references.</span></span>

## <a name="synopsis"></a><span data-ttu-id="05a98-107">構文</span><span class="sxs-lookup"><span data-stu-id="05a98-107">Synopsis</span></span>

`dotnet list [<PROJECT>|<SOLUTION>] reference [-h|--help]`

## <a name="description"></a><span data-ttu-id="05a98-108">説明</span><span class="sxs-lookup"><span data-stu-id="05a98-108">Description</span></span>

<span data-ttu-id="05a98-109">`dotnet list reference` コマンドは、特定のプロジェクトまたはソリューションのプロジェクト参照を列挙する便利なオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="05a98-109">The `dotnet list reference` command provides a convenient option to list project references for a given project or solution.</span></span>

## <a name="arguments"></a><span data-ttu-id="05a98-110">引数</span><span class="sxs-lookup"><span data-stu-id="05a98-110">Arguments</span></span>

* **`PROJECT | SOLUTION`**

  <span data-ttu-id="05a98-111">参照の一覧取得に使うプロジェクトまたはソリューション ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="05a98-111">Specifies the project or solution file to use for listing references.</span></span> <span data-ttu-id="05a98-112">指定されていない場合、コマンドではプロジェクト ファイルを現在のディレクトリで検索します。</span><span class="sxs-lookup"><span data-stu-id="05a98-112">If not specified, the command searches the current directory for a project file.</span></span>

## <a name="options"></a><span data-ttu-id="05a98-113">オプション</span><span class="sxs-lookup"><span data-stu-id="05a98-113">Options</span></span>

* **`-h|--help`**

  <span data-ttu-id="05a98-114">コマンドの短いヘルプを印刷します。</span><span class="sxs-lookup"><span data-stu-id="05a98-114">Prints out a short help for the command.</span></span>

## <a name="examples"></a><span data-ttu-id="05a98-115">使用例</span><span class="sxs-lookup"><span data-stu-id="05a98-115">Examples</span></span>

* <span data-ttu-id="05a98-116">指定したプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="05a98-116">List the project references for the specified project:</span></span>

  ```dotnetcli
  dotnet list app/app.csproj reference
  ```

* <span data-ttu-id="05a98-117">現在のディレクトリ内のプロジェクトのプロジェクト参照を列挙する:</span><span class="sxs-lookup"><span data-stu-id="05a98-117">List the project references for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet list reference
  ```
