---
ms.openlocfilehash: 08ad6fd4ccb6d5ddbbb4fa7ef1b325ce30689748
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621291"
---
### <a name="appdomainsetupdynamicbase-is-no-longer-randomized-by-userandomizedstringhashalgorithm"></a><span data-ttu-id="abbf6-101">AppDomainSetup.DynamicBase が UseRandomizedStringHashAlgorithm でランダム化されなくなった</span><span class="sxs-lookup"><span data-stu-id="abbf6-101">AppDomainSetup.DynamicBase is no longer randomized by UseRandomizedStringHashAlgorithm</span></span>

#### <a name="details"></a><span data-ttu-id="abbf6-102">説明</span><span class="sxs-lookup"><span data-stu-id="abbf6-102">Details</span></span>

<span data-ttu-id="abbf6-103">.NET Framework 4.6 より前では、UseRandomizedStringHashAlgorithm がアプリの構成ファイルで有効になっている場合、<xref:System.AppDomainSetup.DynamicBase> の値がアプリケーション ドメイン間、またはプロセス間でランダム化されます。</span><span class="sxs-lookup"><span data-stu-id="abbf6-103">Prior to the .NET Framework 4.6, the value of <xref:System.AppDomainSetup.DynamicBase> would be randomized between application domains, or between processes, if UseRandomizedStringHashAlgorithm was enabled in the app's config file.</span></span> <span data-ttu-id="abbf6-104">.NET Framework 4.6 以降では、<xref:System.AppDomainSetup.DynamicBase> は実行されているアプリの異なるインスタンス間、および異なるアプリ ドメイン間で安定した結果を返します。</span><span class="sxs-lookup"><span data-stu-id="abbf6-104">Beginning in the .NET Framework 4.6, <xref:System.AppDomainSetup.DynamicBase> will return a stable result between different instances of an app running, and between different app domains.</span></span> <span data-ttu-id="abbf6-105">それでも動的ベースはアプリによって異なります。この変更では、同じアプリの異なるインスタンスのランダムな名前付け要素のみが削除されます。</span><span class="sxs-lookup"><span data-stu-id="abbf6-105">Dynamic bases will still differ for different apps; this change only removes the random naming element for different instances of the same app.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="abbf6-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="abbf6-106">Suggestion</span></span>

<span data-ttu-id="abbf6-107"><code>UseRandomizedStringHashAlgorithm</code> を有効にすると、<xref:System.AppDomainSetup.DynamicBase> がランダム化されなくなることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="abbf6-107">Be aware that enabling <code>UseRandomizedStringHashAlgorithm</code> will not result in <xref:System.AppDomainSetup.DynamicBase> being randomized.</span></span> <span data-ttu-id="abbf6-108">ランダム ベースが必要な場合は、この API を使用するのではなく、アプリのコードで生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="abbf6-108">If a random base is needed, it must be produced in your app's code rather than via this API.</span></span>

| <span data-ttu-id="abbf6-109">名前</span><span class="sxs-lookup"><span data-stu-id="abbf6-109">Name</span></span>    | <span data-ttu-id="abbf6-110">値</span><span class="sxs-lookup"><span data-stu-id="abbf6-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="abbf6-111">スコープ</span><span class="sxs-lookup"><span data-stu-id="abbf6-111">Scope</span></span>   |<span data-ttu-id="abbf6-112">エッジ</span><span class="sxs-lookup"><span data-stu-id="abbf6-112">Edge</span></span>|
|<span data-ttu-id="abbf6-113">バージョン</span><span class="sxs-lookup"><span data-stu-id="abbf6-113">Version</span></span>|<span data-ttu-id="abbf6-114">4.6</span><span class="sxs-lookup"><span data-stu-id="abbf6-114">4.6</span></span>|
|<span data-ttu-id="abbf6-115">種類</span><span class="sxs-lookup"><span data-stu-id="abbf6-115">Type</span></span>|<span data-ttu-id="abbf6-116">ランタイム</span><span class="sxs-lookup"><span data-stu-id="abbf6-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="abbf6-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="abbf6-117">Affected APIs</span></span>

-<xref:System.AppDomainSetup.DynamicBase?displayProperty=nameWithType></li></ul>|
