---
ms.openlocfilehash: e77312605ee367c159171e305d8f69429f9ac58b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539598"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="4e41d-101">ID:AddDefaultUI メソッド オーバーロードが削除されました</span><span class="sxs-lookup"><span data-stu-id="4e41d-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="4e41d-102">ASP.NET Core 3.0 以降では、[IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) メソッド オーバーロードはなくなりました。</span><span class="sxs-lookup"><span data-stu-id="4e41d-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4e41d-103">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="4e41d-103">Version introduced</span></span>

<span data-ttu-id="4e41d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="4e41d-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="4e41d-105">変更理由</span><span class="sxs-lookup"><span data-stu-id="4e41d-105">Reason for change</span></span>

<span data-ttu-id="4e41d-106">この変更は、静的 Web アセット機能が導入された結果でした。</span><span class="sxs-lookup"><span data-stu-id="4e41d-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4e41d-107">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="4e41d-107">Recommended action</span></span>

<span data-ttu-id="4e41d-108">2 つの引数を取るオーバーロードの代わりに <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4e41d-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="4e41d-109">ブートストラップ 3 を使用している場合、プロジェクト ファイルの `<PropertyGroup>` 要素に次の行も追加します。</span><span class="sxs-lookup"><span data-stu-id="4e41d-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="4e41d-110">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="4e41d-110">Category</span></span>

<span data-ttu-id="4e41d-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4e41d-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="4e41d-112">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="4e41d-112">Affected APIs</span></span>

[<span data-ttu-id="4e41d-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="4e41d-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
