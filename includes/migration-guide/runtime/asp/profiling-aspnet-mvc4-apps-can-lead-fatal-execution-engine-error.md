---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622034"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="947f2-101">ASP.Net MVC4 アプリのプロファイリングにより、致命的な実行エンジン エラーが発生する可能性がある</span><span class="sxs-lookup"><span data-stu-id="947f2-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="947f2-102">説明</span><span class="sxs-lookup"><span data-stu-id="947f2-102">Details</span></span>

<span data-ttu-id="947f2-103">NGEN/プロファイル アセンブリを使用するプロファイラーにより、起動時にプロファイルされた ASP.NET MVC4 アプリケーションがクラッシュし、"致命的な実行エンジン例外" が示される場合があります。</span><span class="sxs-lookup"><span data-stu-id="947f2-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="947f2-104">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="947f2-104">Suggestion</span></span>

<span data-ttu-id="947f2-105">この問題は、.NET Framework 4.5.2 で修正されます。</span><span class="sxs-lookup"><span data-stu-id="947f2-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="947f2-106">プロファイラーは、イベント マスクで <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> を指定することで、この問題を回避することもできます。</span><span class="sxs-lookup"><span data-stu-id="947f2-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="947f2-107">名前</span><span class="sxs-lookup"><span data-stu-id="947f2-107">Name</span></span>    | <span data-ttu-id="947f2-108">[値]</span><span class="sxs-lookup"><span data-stu-id="947f2-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="947f2-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="947f2-109">Scope</span></span>   |<span data-ttu-id="947f2-110">エッジ</span><span class="sxs-lookup"><span data-stu-id="947f2-110">Edge</span></span>|
|<span data-ttu-id="947f2-111">バージョン</span><span class="sxs-lookup"><span data-stu-id="947f2-111">Version</span></span>|<span data-ttu-id="947f2-112">4.5</span><span class="sxs-lookup"><span data-stu-id="947f2-112">4.5</span></span>|
|<span data-ttu-id="947f2-113">種類</span><span class="sxs-lookup"><span data-stu-id="947f2-113">Type</span></span>|<span data-ttu-id="947f2-114">ランタイム</span><span class="sxs-lookup"><span data-stu-id="947f2-114">Runtime</span></span>|
