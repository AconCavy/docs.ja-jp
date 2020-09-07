---
ms.openlocfilehash: c3114277445daaae988b41782721c443c1e780d1
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497891"
---
### <a name="wpf-spawns-a-wisptisexe-process-which-can-freeze-the-mouse"></a><span data-ttu-id="4f265-101">WPF が wisptis.exe プロセスを生成し、マウスがフリーズする可能性がある</span><span class="sxs-lookup"><span data-stu-id="4f265-101">WPF spawns a wisptis.exe process which can freeze the mouse</span></span>

#### <a name="details"></a><span data-ttu-id="4f265-102">説明</span><span class="sxs-lookup"><span data-stu-id="4f265-102">Details</span></span>

<span data-ttu-id="4f265-103">この問題は 4.5.2 から発生するようになり、<code>wisptis.exe</code> が生成され、マウス入力がフリーズする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="4f265-103">An issue was introduced in 4.5.2 that causes <code>wisptis.exe</code> to be spawned that can freeze mouse input.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4f265-104">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="4f265-104">Suggestion</span></span>

<span data-ttu-id="4f265-105">この問題はサービス リリースの .NET Framework 4.5.2 (修正プログラム ロールアップ 3026376) で、あるいは .NET Framework 4.6 にアップグレードすることで解決できます。</span><span class="sxs-lookup"><span data-stu-id="4f265-105">A fix for this issue is available in a servicing release of the .NET Framework 4.5.2 (hotfix rollup 3026376), or by upgrading to the .NET Framework 4.6</span></span>

| <span data-ttu-id="4f265-106">名前</span><span class="sxs-lookup"><span data-stu-id="4f265-106">Name</span></span>    | <span data-ttu-id="4f265-107">[値]</span><span class="sxs-lookup"><span data-stu-id="4f265-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4f265-108">スコープ</span><span class="sxs-lookup"><span data-stu-id="4f265-108">Scope</span></span>   |<span data-ttu-id="4f265-109">Major</span><span class="sxs-lookup"><span data-stu-id="4f265-109">Major</span></span>|
|<span data-ttu-id="4f265-110">バージョン</span><span class="sxs-lookup"><span data-stu-id="4f265-110">Version</span></span>|<span data-ttu-id="4f265-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="4f265-111">4.5.2</span></span>|
|<span data-ttu-id="4f265-112">種類</span><span class="sxs-lookup"><span data-stu-id="4f265-112">Type</span></span>|<span data-ttu-id="4f265-113">ランタイム</span><span class="sxs-lookup"><span data-stu-id="4f265-113">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4f265-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="4f265-114">Affected APIs</span></span>

<span data-ttu-id="4f265-115">API 分析では検出できません。</span><span class="sxs-lookup"><span data-stu-id="4f265-115">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
