---
ms.openlocfilehash: b521f4163bf5bf4a369d0eec12dae503703a976e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614648"
---
### <a name="throttle-concurrent-requests-per-session"></a><span data-ttu-id="3bf97-101">セッションあたりの同時実行される要求のスロットル</span><span class="sxs-lookup"><span data-stu-id="3bf97-101">Throttle concurrent requests per session</span></span>

#### <a name="details"></a><span data-ttu-id="3bf97-102">説明</span><span class="sxs-lookup"><span data-stu-id="3bf97-102">Details</span></span>

<span data-ttu-id="3bf97-103">.NET Framework 4.6.2 以前の場合、ASP.NET は同じ Sessionid の要求を順番に実行します。ASP.NET は既定で常にクッキーを経由して Sessionid を発行します。</span><span class="sxs-lookup"><span data-stu-id="3bf97-103">In the .NET Framework 4.6.2 and earlier, ASP.NET executes requests with the same Sessionid sequentially, and ASP.NET always issues the Sessionid through cookies by default.</span></span> <span data-ttu-id="3bf97-104">ページの応答に長い時間がかかる場合、ブラウザーの <kbd>F5</kbd> を押すだけで、サーバーのパフォーマンスが大幅に低下します。</span><span class="sxs-lookup"><span data-stu-id="3bf97-104">If a page takes a long time to respond, it will significantly degrade server performance just by pressing <kbd>F5</kbd> on the browser.</span></span> <span data-ttu-id="3bf97-105">この修正プログラムでは、キューに置かれた要求を追跡し、特定の制限を超えたときに要求を終了するためのカウンターを追加しました。</span><span class="sxs-lookup"><span data-stu-id="3bf97-105">In the fix, we added a counter to track the queued requests and terminate the requests when they exceed a specified limit.</span></span> <span data-ttu-id="3bf97-106">既定値は 50 です。</span><span class="sxs-lookup"><span data-stu-id="3bf97-106">The default value is 50.</span></span> <span data-ttu-id="3bf97-107">制限に達すると、警告がイベント ログに記録され、HTTP 500 応答は IIS ログに記録される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3bf97-107">If the limit is reached, a warning will be logged in the event log, and an HTTP 500 response may be recorded in the IIS log.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3bf97-108">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="3bf97-108">Suggestion</span></span>

<span data-ttu-id="3bf97-109">以前の動作を復元するには、次の設定を web.config ファイルに追加して、新しい動作を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="3bf97-109">To restore the old behavior, you can add the following setting to your web.config file to opt out of the new behavior.</span></span>

```xml
<appSettings>
    <add key="aspnet:RequestQueueLimitPerSession" value="2147483647"/>
</appSettings>
```

| <span data-ttu-id="3bf97-110">名前</span><span class="sxs-lookup"><span data-stu-id="3bf97-110">Name</span></span>    | <span data-ttu-id="3bf97-111">[値]</span><span class="sxs-lookup"><span data-stu-id="3bf97-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3bf97-112">スコープ</span><span class="sxs-lookup"><span data-stu-id="3bf97-112">Scope</span></span>   | <span data-ttu-id="3bf97-113">エッジ</span><span class="sxs-lookup"><span data-stu-id="3bf97-113">Edge</span></span>        |
| <span data-ttu-id="3bf97-114">バージョン</span><span class="sxs-lookup"><span data-stu-id="3bf97-114">Version</span></span> | <span data-ttu-id="3bf97-115">4.7</span><span class="sxs-lookup"><span data-stu-id="3bf97-115">4.7</span></span>         |
| <span data-ttu-id="3bf97-116">種類</span><span class="sxs-lookup"><span data-stu-id="3bf97-116">Type</span></span>    | <span data-ttu-id="3bf97-117">再ターゲット中</span><span class="sxs-lookup"><span data-stu-id="3bf97-117">Retargeting</span></span> |
