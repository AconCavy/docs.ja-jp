---
ms.openlocfilehash: da1ec7908b3082fc61313cb805773aa600bc1b5d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394417"
---
### <a name="localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete"></a><span data-ttu-id="aee90-101">ローカリゼーション:ResourceManagerWithCultureStringLocalizer と WithCulture を古い形式としてマーク</span><span class="sxs-lookup"><span data-stu-id="aee90-101">Localization: ResourceManagerWithCultureStringLocalizer and WithCulture marked obsolete</span></span>

<span data-ttu-id="aee90-102">[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) クラスと [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) インターフェイス メンバーは、特に、ユーザーが独自の `IStringLocalizer` 実装を作成するときに、ローカライズでユーザーの混乱の原因になることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="aee90-102">The [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) class and [WithCulture](https://github.com/aspnet/Localization/blob/master/src/Microsoft.Extensions.Localization/ResourceManagerStringLocalizer.cs#L154-L170) interface member are often sources of confusion for users of localization, especially when creating their own `IStringLocalizer` implementation.</span></span> <span data-ttu-id="aee90-103">これらの項目は、`IStringLocalizer` インスタンスが "言語ごとで、リソースごと" であるという印象をユーザーに与えています。</span><span class="sxs-lookup"><span data-stu-id="aee90-103">These items give the user the impression that an `IStringLocalizer` instance is "per-language, per-resource".</span></span> <span data-ttu-id="aee90-104">実際には、インスタンスは "リソースごと" のみである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aee90-104">In reality, the instances should only be "per-resource".</span></span> <span data-ttu-id="aee90-105">検索対象の言語は、実行時に `CultureInfo.CurrentUICulture` によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="aee90-105">The language searched for is determined by the `CultureInfo.CurrentUICulture` at execution time.</span></span> <span data-ttu-id="aee90-106">混乱の原因を排除するために、ASP.NET Core 3.0 Preview 3 では、API が古い形式としてマークされました。</span><span class="sxs-lookup"><span data-stu-id="aee90-106">To eliminate the source of confusion, the APIs were marked as obsolete in ASP.NET Core 3.0 Preview 3.</span></span> <span data-ttu-id="aee90-107">これらの API は、将来のリリースで削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="aee90-107">The APIs will be removed in a future release.</span></span>

<span data-ttu-id="aee90-108">コンテキストについては、[aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aee90-108">For context, see [aspnet/AspNetCore#3324](https://github.com/aspnet/AspNetCore/issues/3324).</span></span> <span data-ttu-id="aee90-109">ディスカッションについては、[aspnet/aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aee90-109">For discussion, see [aspnet/AspNetCore#7756](https://github.com/aspnet/AspNetCore/issues/7756).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aee90-110">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="aee90-110">Version introduced</span></span>

<span data-ttu-id="aee90-111">3.0</span><span class="sxs-lookup"><span data-stu-id="aee90-111">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="aee90-112">以前の動作</span><span class="sxs-lookup"><span data-stu-id="aee90-112">Old behavior</span></span>

<span data-ttu-id="aee90-113">メソッドは `Obsolete` としてマークされていませんでした。</span><span class="sxs-lookup"><span data-stu-id="aee90-113">Methods weren't marked as `Obsolete`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="aee90-114">新しい動作</span><span class="sxs-lookup"><span data-stu-id="aee90-114">New behavior</span></span>

<span data-ttu-id="aee90-115">メソッドは `Obsolete` としてマークされています。</span><span class="sxs-lookup"><span data-stu-id="aee90-115">Methods are marked `Obsolete`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="aee90-116">変更理由</span><span class="sxs-lookup"><span data-stu-id="aee90-116">Reason for change</span></span>

<span data-ttu-id="aee90-117">API が、推奨されていないユース ケースを表していました。</span><span class="sxs-lookup"><span data-stu-id="aee90-117">The APIs represented a use case that isn't recommended.</span></span> <span data-ttu-id="aee90-118">ローカライズの設計について混乱が生じていました。</span><span class="sxs-lookup"><span data-stu-id="aee90-118">There was confusion about the design of localization.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aee90-119">推奨される操作</span><span class="sxs-lookup"><span data-stu-id="aee90-119">Recommended action</span></span>

<span data-ttu-id="aee90-120">代わりに `ResourceManagerStringLocalizer` を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="aee90-120">The recommendation is to use `ResourceManagerStringLocalizer` instead.</span></span> <span data-ttu-id="aee90-121">カルチャは `CurrentCulture` によって設定できます。</span><span class="sxs-lookup"><span data-stu-id="aee90-121">Let the culture be set by the `CurrentCulture`.</span></span> <span data-ttu-id="aee90-122">これが適切でない場合は、[ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18) のコピーを作成して使用してください。</span><span class="sxs-lookup"><span data-stu-id="aee90-122">If that isn't an option, create and use a copy of [ResourceManagerWithCultureStringLocalizer](https://github.com/aspnet/Localization/blob/43b974482c7b703c92085c6f68b3b23d8fe32720/src/Microsoft.Extensions.Localization/ResourceManagerWithCultureStringLocalizer.cs#L18).</span></span>

#### <a name="category"></a><span data-ttu-id="aee90-123">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="aee90-123">Category</span></span>

<span data-ttu-id="aee90-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aee90-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aee90-125">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="aee90-125">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer>
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.ResourceManagerWithCultureStringLocalizer`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.WithCulture`

-->