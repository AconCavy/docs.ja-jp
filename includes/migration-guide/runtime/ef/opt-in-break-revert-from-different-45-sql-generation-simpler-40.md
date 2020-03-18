---
ms.openlocfilehash: e5d81d791e1a2f1a2dbdafc787dec1227423883d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803269"
---
### <a name="opt-in-break-to-revert-from-different-45-sql-generation-to-simpler-40-sql-generation"></a><span data-ttu-id="ba43f-101">異なる 4.5 SQL 生成からより単純な 4.0 SQL 生成に戻す</span><span class="sxs-lookup"><span data-stu-id="ba43f-101">Opt-in break to revert from different 4.5 SQL generation to simpler 4.0 SQL generation</span></span>

|   |   |
|---|---|
|<span data-ttu-id="ba43f-102">説明</span><span class="sxs-lookup"><span data-stu-id="ba43f-102">Details</span></span>|<span data-ttu-id="ba43f-103">最初に OrderBy を使用せずに JOIN ステートメントを生成し、制限操作への呼び出しを含むクエリで、より単純な SQL が生成されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="ba43f-103">Queries that produce JOIN statements and contain a call to a limiting operation without first using OrderBy now produce simpler SQL.</span></span> <span data-ttu-id="ba43f-104">.NET Framework 4.5 へのアップグレード後、これらのクエリは以前のバージョンよりも複雑な SQL を生成しました。</span><span class="sxs-lookup"><span data-stu-id="ba43f-104">After upgrading to .NET Framework 4.5, these queries produced more complicated SQL than previous versions.</span></span>|
|<span data-ttu-id="ba43f-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="ba43f-105">Suggestion</span></span>|<span data-ttu-id="ba43f-106">既定では、この機能は無効です。</span><span class="sxs-lookup"><span data-stu-id="ba43f-106">This feature is disabled by default.</span></span> <span data-ttu-id="ba43f-107">Entity Framework がパフォーマンスを低下させる追加の JOIN ステートメントを生成する場合は、アプリケーション構成 (app.config) ファイルの <code>&lt;appSettings&gt;</code> セクションへ次のエントリを追加してこの機能を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="ba43f-107">If Entity Framework generates extra JOIN statements that cause performance degradation, you can enable this feature by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the application configuration (app.config) file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyLimitOperations&quot; value=&quot;true&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="ba43f-108">スコープ</span><span class="sxs-lookup"><span data-stu-id="ba43f-108">Scope</span></span>|<span data-ttu-id="ba43f-109">透過的</span><span class="sxs-lookup"><span data-stu-id="ba43f-109">Transparent</span></span>|
|<span data-ttu-id="ba43f-110">バージョン</span><span class="sxs-lookup"><span data-stu-id="ba43f-110">Version</span></span>|<span data-ttu-id="ba43f-111">4.5.2</span><span class="sxs-lookup"><span data-stu-id="ba43f-111">4.5.2</span></span>|
|<span data-ttu-id="ba43f-112">[種類]</span><span class="sxs-lookup"><span data-stu-id="ba43f-112">Type</span></span>|<span data-ttu-id="ba43f-113">ランタイム</span><span class="sxs-lookup"><span data-stu-id="ba43f-113">Runtime</span></span>|
