---
title: ソース リンクと .NET ライブラリ
description: ソース リンクを使用して .NET ライブラリのデバッグ機能を改善するためのベスト プラクティス推奨事項。
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 89f9e3b1fd70003c528465f29a143b157468d539
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089287"
---
# <a name="source-link"></a><span data-ttu-id="b92b5-103">ソース リンク</span><span class="sxs-lookup"><span data-stu-id="b92b5-103">Source Link</span></span>

<span data-ttu-id="b92b5-104">ソース リンクは NuGet からの .NET アセンブリのソース コードを開発者がデバッグすることを可能にするテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="b92b5-104">Source Link is a technology that enables source code debugging of .NET assemblies from NuGet by developers.</span></span> <span data-ttu-id="b92b5-105">ソース リンクは NuGet パッケージの作成時に実行され、ソース コントロール メタデータをアセンブリとパッケージの内部に埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-105">Source Link executes when creating the NuGet package and embeds source control metadata inside assemblies and the package.</span></span> <span data-ttu-id="b92b5-106">パッケージをダウンロードし、Visual Studio でソース リンクを有効にした開発者は、そのソース コードにステップ インできます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-106">Developers who download the package and have Source Link enabled in Visual Studio can step into its source code.</span></span> <span data-ttu-id="b92b5-107">ソース リンクからは、効率的なデバッグを可能にするソース コントロール メタデータが提供されます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-107">Source Link provides source control metadata to create a great debugging experience.</span></span>

## <a name="source-link-demo"></a><span data-ttu-id="b92b5-108">ソース リンクのデモ</span><span class="sxs-lookup"><span data-stu-id="b92b5-108">Source Link demo</span></span>

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a><span data-ttu-id="b92b5-109">ソース リンクを使用する</span><span class="sxs-lookup"><span data-stu-id="b92b5-109">Using Source Link</span></span>

<span data-ttu-id="b92b5-110">ソース リンクの使用方法は、[dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="b92b5-110">Instructions for using Source Link can be found on the [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md) GitHub repository.</span></span>

<span data-ttu-id="b92b5-111">[NuGet パッケージ エクスプローラー](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer)を使用すれば、ソース リンク メタデータがパッケージに正常に埋め込まれたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-111">You can use [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) to confirm that the Source Link metadata has been successfully embedded in the package.</span></span> <span data-ttu-id="b92b5-112">`Repository` メタデータがコミット ID と共に存在すること、各ターゲットの .dll と共に .pdb ファイルが見つかることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b92b5-112">Check the `Repository` metadata is present with a commit identifier and that .pdb files are located with each target's .dll.</span></span>

<span data-ttu-id="b92b5-113">![NuGet パッケージ エクスプローラーのソース リンク](./media/sourcelink/nuget-package-explorer-sourcelink.png "NuGet パッケージ エクスプローラーのソース リンク")</span><span class="sxs-lookup"><span data-stu-id="b92b5-113">![Source Link in NuGet Package Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Source Link in NuGet Package Explorer")</span></span>

<span data-ttu-id="b92b5-114">**✔️ 検討** ソース リンクを使用して、お使いのアセンブリと NuGet パッケージにソース管理のメタデータを追加する。</span><span class="sxs-lookup"><span data-stu-id="b92b5-114">**✔️ CONSIDER** using Source Link to add source control metadata to your assemblies and NuGet packages.</span></span>

> [!TIP]
> <span data-ttu-id="b92b5-115">デバッガー属性を型に追加することで開発者のデバッグ機能をさらに強化できます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-115">You can further enhance a developer's debugging experience by adding debugger attributes to your types.</span></span>
>
> * <span data-ttu-id="b92b5-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> では、デバッガーの変数ウィンドウでクラスやフィールドを表示する方法をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-116"><xref:System.Diagnostics.DebuggerDisplayAttribute> can customize how a class or field is displayed in the debugger variable windows.</span></span>
> * <span data-ttu-id="b92b5-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> では、デバッガーに対してコードのステップ インではなくステップ実行が指示されます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-117"><xref:System.Diagnostics.DebuggerStepThroughAttribute> instructs the debugger to step through the code instead of stepping into the code.</span></span>
> * <span data-ttu-id="b92b5-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> では、デバッガー変数ウィンドウにメンバーを表示するかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="b92b5-118"><xref:System.Diagnostics.DebuggerBrowsableAttribute> controls whether a member is displayed in the debugger variable windows.</span></span>

<span data-ttu-id="b92b5-119">**✔️ 検討** シンボル ファイルを発行する (`*.pdb`)。</span><span class="sxs-lookup"><span data-stu-id="b92b5-119">**✔️ CONSIDER** publishing symbol files (`*.pdb`).</span></span>

> <span data-ttu-id="b92b5-120">デバッグのエクスペリエンスを最善にするには、ライブラリ上でシンボル ファイルを発行してソース リンクを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b92b5-120">For the best debugging experience your library should publish symbol files as well as use Source Link.</span></span> <span data-ttu-id="b92b5-121">シンボル ファイルとシンボル パッケージの詳細については、「[シンボル パッケージ](./nuget.md#symbol-packages)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b92b5-121">For more information about symbol files and symbol packages, see [Symbol packages](./nuget.md#symbol-packages).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b92b5-122">[前へ](dependencies.md)
>[次へ](publish-nuget-package.md)</span><span class="sxs-lookup"><span data-stu-id="b92b5-122">[Previous](dependencies.md)
[Next](publish-nuget-package.md)</span></span>
