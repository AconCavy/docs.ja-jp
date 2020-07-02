---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620365"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="7afc9-101">MinFreeMemoryPercentageToActiveService が順守されるようになった</span><span class="sxs-lookup"><span data-stu-id="7afc9-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="7afc9-102">説明</span><span class="sxs-lookup"><span data-stu-id="7afc9-102">Details</span></span>

<span data-ttu-id="7afc9-103">この設定は、WCF サービスをアクティブにするためにサーバー上で使用できなければならない最小メモリを設定します。</span><span class="sxs-lookup"><span data-stu-id="7afc9-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="7afc9-104"><xref:System.OutOfMemoryException?displayProperty=fullName> 例外が発生しないようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="7afc9-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="7afc9-105">.NET Framework 4.5 では、この設定には効果はありません。</span><span class="sxs-lookup"><span data-stu-id="7afc9-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="7afc9-106">.NET Framework 4.5.1 では、この設定が守られます。</span><span class="sxs-lookup"><span data-stu-id="7afc9-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7afc9-107">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="7afc9-107">Suggestion</span></span>

<span data-ttu-id="7afc9-108">Web サーバーで使用できる空きメモリが構成設定によって定義されたパーセンテージよりも小さい場合、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="7afc9-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="7afc9-109">制約されたメモリ環境で正常に開始し、実行された WCF サービスが今度は失敗することがあります。</span><span class="sxs-lookup"><span data-stu-id="7afc9-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="7afc9-110">名前</span><span class="sxs-lookup"><span data-stu-id="7afc9-110">Name</span></span>    | <span data-ttu-id="7afc9-111">[値]</span><span class="sxs-lookup"><span data-stu-id="7afc9-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7afc9-112">スコープ</span><span class="sxs-lookup"><span data-stu-id="7afc9-112">Scope</span></span>   |<span data-ttu-id="7afc9-113">マイナー</span><span class="sxs-lookup"><span data-stu-id="7afc9-113">Minor</span></span>|
|<span data-ttu-id="7afc9-114">バージョン</span><span class="sxs-lookup"><span data-stu-id="7afc9-114">Version</span></span>|<span data-ttu-id="7afc9-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="7afc9-115">4.5.1</span></span>|
|<span data-ttu-id="7afc9-116">種類</span><span class="sxs-lookup"><span data-stu-id="7afc9-116">Type</span></span>|<span data-ttu-id="7afc9-117">ランタイム</span><span class="sxs-lookup"><span data-stu-id="7afc9-117">Runtime</span></span>|
