---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901797"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a><span data-ttu-id="358ff-101">ホスティング:AspNetCoreModule V1 が Windows ホスティング バンドルから削除されました</span><span class="sxs-lookup"><span data-stu-id="358ff-101">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>

<span data-ttu-id="358ff-102">ASP.NET Core 3.0 以降では、Windows ホスティング バンドルに AspNetCoreModule (ANCM) V1 が含まれません。</span><span class="sxs-lookup"><span data-stu-id="358ff-102">Starting with ASP.NET Core 3.0, the Windows Hosting Bundle won't contain AspNetCoreModule (ANCM) V1.</span></span>

<span data-ttu-id="358ff-103">ANCM V2 は、ANCM OutOfProcess との下位互換性があり、ASP.NET Core 3.0 アプリでの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="358ff-103">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="358ff-104">ディスカッションについては、[dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="358ff-104">For discussion, see [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="358ff-105">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="358ff-105">Version introduced</span></span>

<span data-ttu-id="358ff-106">3.0</span><span class="sxs-lookup"><span data-stu-id="358ff-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="358ff-107">以前の動作</span><span class="sxs-lookup"><span data-stu-id="358ff-107">Old behavior</span></span>

<span data-ttu-id="358ff-108">Windows ホスティング バンドルに ANCM V1 が含まれています。</span><span class="sxs-lookup"><span data-stu-id="358ff-108">ANCM V1 is included in the Windows Hosting Bundle.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="358ff-109">新しい動作</span><span class="sxs-lookup"><span data-stu-id="358ff-109">New behavior</span></span>

<span data-ttu-id="358ff-110">Windows ホスティング バンドルに ANCM V1 が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="358ff-110">ANCM V1 isn't included in the Windows Hosting Bundle.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="358ff-111">変更理由</span><span class="sxs-lookup"><span data-stu-id="358ff-111">Reason for change</span></span>

<span data-ttu-id="358ff-112">ANCM V2 は、ANCM OutOfProcess との下位互換性があり、ASP.NET Core 3.0 アプリでの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="358ff-112">ANCM V2 is backwards compatible with ANCM OutOfProcess and is recommended for use with ASP.NET Core 3.0 apps.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="358ff-113">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="358ff-113">Recommended action</span></span>

<span data-ttu-id="358ff-114">ASP.NET Core 3.0 アプリでお使いの ANCM V2 を使用します。</span><span class="sxs-lookup"><span data-stu-id="358ff-114">Use ANCM V2 with ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="358ff-115">ANCM V1 が必要な場合は、ASP.NET Core 2.1 または 2.2 の Windows ホスティング バンドルを使用してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="358ff-115">If ANCM V1 is required, it can be installed using the ASP.NET Core 2.1 or 2.2 Windows Hosting Bundle.</span></span>

<span data-ttu-id="358ff-116">この変更によって、次のような ASP.NET Core 3.0 アプリが中断されます。</span><span class="sxs-lookup"><span data-stu-id="358ff-116">This change will break ASP.NET Core 3.0 apps that:</span></span>

- <span data-ttu-id="358ff-117">`<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>` での ANCM V1 の使用が明示的に選択されている。</span><span class="sxs-lookup"><span data-stu-id="358ff-117">Explicitly opted into using ANCM V1 with `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.</span></span>
- <span data-ttu-id="358ff-118">カスタム *web.config* ファイルに `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />` が設定されている。</span><span class="sxs-lookup"><span data-stu-id="358ff-118">Have a custom *web.config* file with `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.</span></span>

#### <a name="category"></a><span data-ttu-id="358ff-119">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="358ff-119">Category</span></span>

<span data-ttu-id="358ff-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="358ff-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="358ff-121">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="358ff-121">Affected APIs</span></span>

<span data-ttu-id="358ff-122">None</span><span class="sxs-lookup"><span data-stu-id="358ff-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
