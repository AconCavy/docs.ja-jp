---
ms.openlocfilehash: f955e270f709ddf6eea2e44bbcf386e372b9f6e3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621315"
---
### <a name="targetframeworkname-for-default-app-domain-no-longer-defaults-to-null-if-not-set"></a><span data-ttu-id="21579-101">既定のアプリケーション ドメインの TargetFrameworkName は、設定されなかった場合、既定で null に設定されなくなった</span><span class="sxs-lookup"><span data-stu-id="21579-101">TargetFrameworkName for default app domain no longer defaults to null if not set</span></span>

#### <a name="details"></a><span data-ttu-id="21579-102">説明</span><span class="sxs-lookup"><span data-stu-id="21579-102">Details</span></span>

<span data-ttu-id="21579-103"><xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> は、以前は、明示的に設定されない限り、既定のアプリケーション ドメインでは null でした。</span><span class="sxs-lookup"><span data-stu-id="21579-103">The <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> was previously null in the default app domain, unless it was explicitly set.</span></span> <span data-ttu-id="21579-104">4\.6 以降では、既定のアプリケーション ドメインの <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> プロパティは、TargetFrameworkAttribute (ある場合) から派生された既定値を持ちます。</span><span class="sxs-lookup"><span data-stu-id="21579-104">Beginning in 4.6, the <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> property for the default app domain will have a default value derived from the TargetFrameworkAttribute (if one is present).</span></span> <span data-ttu-id="21579-105">既定以外のアプリケーション ドメインは、明示的にオーバーライドされない限り、既定のアプリケーション ドメイン (4.6 では既定で null に設定されない) から <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> を継承し続けます。</span><span class="sxs-lookup"><span data-stu-id="21579-105">Non-default app domains will continue to inherit their <xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=fullName> from the default app domain (which will not default to null in 4.6) unless it is explicitly overridden.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="21579-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="21579-106">Suggestion</span></span>

<span data-ttu-id="21579-107"><xref:System.AppDomainSetup.TargetFrameworkName> が既定で null に設定されることに依然しないように、コードを更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21579-107">Code should be updated to not depend on <xref:System.AppDomainSetup.TargetFrameworkName> defaulting to null.</span></span> <span data-ttu-id="21579-108">このプロパティが引き続き null として評価される必要がある場合、明示的にその値に設定できます。</span><span class="sxs-lookup"><span data-stu-id="21579-108">If it is required that this property continue to evaluate to null, it can be explicitly set to that value.</span></span>

| <span data-ttu-id="21579-109">名前</span><span class="sxs-lookup"><span data-stu-id="21579-109">Name</span></span>    | <span data-ttu-id="21579-110">値</span><span class="sxs-lookup"><span data-stu-id="21579-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="21579-111">スコープ</span><span class="sxs-lookup"><span data-stu-id="21579-111">Scope</span></span>   |<span data-ttu-id="21579-112">エッジ</span><span class="sxs-lookup"><span data-stu-id="21579-112">Edge</span></span>|
|<span data-ttu-id="21579-113">バージョン</span><span class="sxs-lookup"><span data-stu-id="21579-113">Version</span></span>|<span data-ttu-id="21579-114">4.6</span><span class="sxs-lookup"><span data-stu-id="21579-114">4.6</span></span>|
|<span data-ttu-id="21579-115">種類</span><span class="sxs-lookup"><span data-stu-id="21579-115">Type</span></span>|<span data-ttu-id="21579-116">ランタイム</span><span class="sxs-lookup"><span data-stu-id="21579-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="21579-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="21579-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.TargetFrameworkName?displayProperty=nameWithType></li></ul>|
