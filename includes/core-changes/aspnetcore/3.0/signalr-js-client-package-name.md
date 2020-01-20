---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901721"
---
### <a name="signalr-javascript-client-package-name-changed"></a><span data-ttu-id="13b1c-101">SignalR:JavaScript クライアント パッケージ名が変更されました</span><span class="sxs-lookup"><span data-stu-id="13b1c-101">SignalR: JavaScript client package name changed</span></span>

<span data-ttu-id="13b1c-102">ASP.NET Core 3.0 Preview 7 で、SignalR JavaScript クライアント パッケージの名前が `@aspnet/signalr` から `@microsoft/signalr` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="13b1c-102">In ASP.NET Core 3.0 Preview 7, the SignalR JavaScript client package name changed from `@aspnet/signalr` to `@microsoft/signalr`.</span></span> <span data-ttu-id="13b1c-103">この名前変更は、Azure SignalR Service のおかげで、ASP.NET Core アプリ以外でも SignalR が便利になっている事実を反映しています。</span><span class="sxs-lookup"><span data-stu-id="13b1c-103">The name change reflects the fact that SignalR is useful in more than just ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

<span data-ttu-id="13b1c-104">この変更に合わせるため、*package.json* ファイル、`require` ステートメント、ECMAScript `import` ステートメントで参照を変更してください。</span><span class="sxs-lookup"><span data-stu-id="13b1c-104">To react to this change, change references in your *package.json* files, `require` statements, and ECMAScript `import` statements.</span></span> <span data-ttu-id="13b1c-105">この名前変更の一環として API が変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="13b1c-105">No API will change as part of this rename.</span></span>

<span data-ttu-id="13b1c-106">ディスカッションについては、[dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13b1c-106">For discussion, see [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="13b1c-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="13b1c-107">Version introduced</span></span>

<span data-ttu-id="13b1c-108">3.0</span><span class="sxs-lookup"><span data-stu-id="13b1c-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="13b1c-109">以前の動作</span><span class="sxs-lookup"><span data-stu-id="13b1c-109">Old behavior</span></span>

<span data-ttu-id="13b1c-110">クライアント パッケージの名前は `@aspnet/signalr` でした。</span><span class="sxs-lookup"><span data-stu-id="13b1c-110">The client package was named `@aspnet/signalr`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="13b1c-111">新しい動作</span><span class="sxs-lookup"><span data-stu-id="13b1c-111">New behavior</span></span>

<span data-ttu-id="13b1c-112">クライアント パッケージの名前は `@microsoft/signalr` です。</span><span class="sxs-lookup"><span data-stu-id="13b1c-112">The client package is named `@microsoft/signalr`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="13b1c-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="13b1c-113">Reason for change</span></span>

<span data-ttu-id="13b1c-114">この名前変更は、Azure SignalR Service のおかげで、ASP.NET Core アプリ以外でも SignalR が便利になっていることを表わしています。</span><span class="sxs-lookup"><span data-stu-id="13b1c-114">The name change clarifies that SignalR is useful beyond ASP.NET Core apps, thanks to the Azure SignalR Service.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="13b1c-115">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="13b1c-115">Recommended action</span></span>

<span data-ttu-id="13b1c-116">新しいパッケージ `@microsoft/signalr` に切り替えます。</span><span class="sxs-lookup"><span data-stu-id="13b1c-116">Switch to the new package `@microsoft/signalr`.</span></span>

#### <a name="category"></a><span data-ttu-id="13b1c-117">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="13b1c-117">Category</span></span>

<span data-ttu-id="13b1c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="13b1c-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="13b1c-119">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="13b1c-119">Affected APIs</span></span>

<span data-ttu-id="13b1c-120">None</span><span class="sxs-lookup"><span data-stu-id="13b1c-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
