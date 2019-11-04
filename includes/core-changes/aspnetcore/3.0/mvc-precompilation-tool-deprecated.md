---
ms.openlocfilehash: 3f702febc78488b9413ec9303ded211493650f02
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198490"
---
### <a name="mvc-precompilation-tool-deprecated"></a><span data-ttu-id="8d2be-101">MVC:プリコンパイル ツールは非推奨です</span><span class="sxs-lookup"><span data-stu-id="8d2be-101">MVC: Precompilation tool deprecated</span></span>

<span data-ttu-id="8d2be-102">ASP.NET Core 1.1 では、`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC プリコンパイル ツール) パッケージが導入され、Razor ファイル ( *.cshtml* ファイル) の発行時のコンパイルのサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="8d2be-102">In ASP.NET Core 1.1, the `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC precompilation tool) package was introduced to add support for publish-time compilation of Razor files (*.cshtml* files).</span></span> <span data-ttu-id="8d2be-103">ASP.NET Core 2.1 では、プリコンパイル ツールの機能を拡張するために [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) が導入されました。</span><span class="sxs-lookup"><span data-stu-id="8d2be-103">In ASP.NET Core 2.1, the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) was introduced to expand upon features of the precompilation tool.</span></span> <span data-ttu-id="8d2be-104">Razor SDK では、Razor ファイルのビルドおよび発行時のコンパイルのサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="8d2be-104">The Razor SDK added support for build- and publish-time compilation of Razor files.</span></span> <span data-ttu-id="8d2be-105">SDK では、アプリの起動時間を改善しながら、ビルド時に *の* ファイルの正確性を確認します。</span><span class="sxs-lookup"><span data-stu-id="8d2be-105">The SDK verifies the correctness of *.cshtml* files at build time while improving on app startup time.</span></span> <span data-ttu-id="8d2be-106">Razor SDK は既定でオンになっており、その使用を開始するためにジェスチャは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="8d2be-106">The Razor SDK is on by default, and no gesture is required to start using it.</span></span>

<span data-ttu-id="8d2be-107">ASP.NET Core 3.0 では、ASP.NET Core 1.1 世代の MVC のプリコンパイル ツールが削除されました。</span><span class="sxs-lookup"><span data-stu-id="8d2be-107">In ASP.NET Core 3.0, the ASP.NET Core 1.1-era MVC precompilation tool was removed.</span></span> <span data-ttu-id="8d2be-108">以前のバージョンのパッケージでは、修正プログラムのリリースで重要なバグおよびセキュリティ修正プログラムを引き続き受け取ります。</span><span class="sxs-lookup"><span data-stu-id="8d2be-108">Earlier package versions will continue receiving important bug and security fixes in the patch release.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8d2be-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="8d2be-109">Version introduced</span></span>

<span data-ttu-id="8d2be-110">3.0</span><span class="sxs-lookup"><span data-stu-id="8d2be-110">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8d2be-111">以前の動作</span><span class="sxs-lookup"><span data-stu-id="8d2be-111">Old behavior</span></span>

<span data-ttu-id="8d2be-112">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` パッケージは、MVC Razor ビューをプリコンパイルするために使用されました。</span><span class="sxs-lookup"><span data-stu-id="8d2be-112">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package was used to pre-compile MVC Razor views.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8d2be-113">新しい動作</span><span class="sxs-lookup"><span data-stu-id="8d2be-113">New behavior</span></span>

<span data-ttu-id="8d2be-114">Razor SDK では、この機能がネイティブでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="8d2be-114">The Razor SDK natively supports this functionality.</span></span> <span data-ttu-id="8d2be-115">`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` パッケージが更新されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="8d2be-115">The `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` package is no longer updated.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8d2be-116">変更理由</span><span class="sxs-lookup"><span data-stu-id="8d2be-116">Reason for change</span></span>

<span data-ttu-id="8d2be-117">Razor SDK によって、より多くの機能が提供され、ビルド時に *.cshtml* ファイルの正確性が確認されます。</span><span class="sxs-lookup"><span data-stu-id="8d2be-117">The Razor SDK provides more functionality and verifies the correctness of *.cshtml* files at build time.</span></span> <span data-ttu-id="8d2be-118">また、SDK によってアプリの起動時間が改善されます。</span><span class="sxs-lookup"><span data-stu-id="8d2be-118">The SDK also improves app startup time.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8d2be-119">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="8d2be-119">Recommended action</span></span>

<span data-ttu-id="8d2be-120">ASP.NET Core 2.1 以降のユーザーの場合は、[Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0) でのプリコンパイルのネイティブ サポートを使用するように更新します。</span><span class="sxs-lookup"><span data-stu-id="8d2be-120">For users of ASP.NET Core 2.1 or later, update to use the native support for precompilation in the [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0).</span></span> <span data-ttu-id="8d2be-121">バグまたは不足している機能によって Razor SDK への移行が妨げられる場合は、[aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues) で問題を開きます。</span><span class="sxs-lookup"><span data-stu-id="8d2be-121">If bugs or missing features prevent migration to the Razor SDK, open an issue at [aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues).</span></span>

#### <a name="category"></a><span data-ttu-id="8d2be-122">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="8d2be-122">Category</span></span>

<span data-ttu-id="8d2be-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d2be-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8d2be-124">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="8d2be-124">Affected APIs</span></span>

<span data-ttu-id="8d2be-125">なし</span><span class="sxs-lookup"><span data-stu-id="8d2be-125">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis

-->
