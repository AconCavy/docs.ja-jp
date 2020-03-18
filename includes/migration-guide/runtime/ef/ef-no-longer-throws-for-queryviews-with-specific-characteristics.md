---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803214"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a><span data-ttu-id="0959d-101">EF で特定の特性を持つ QueryViews がスローされなくなった</span><span class="sxs-lookup"><span data-stu-id="0959d-101">EF no longer throws for QueryViews with specific characteristics</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0959d-102">説明</span><span class="sxs-lookup"><span data-stu-id="0959d-102">Details</span></span>|<span data-ttu-id="0959d-103">クエリの一部として関連エンティティを含めようとする 0..1 ナビゲーション プロパティを使用して QueryViews に関係するクエリをアプリが実行する場合、Entity Framework で <xref:System.StackOverflowException?displayProperty=name> 例外がスローされなくなりました。</span><span class="sxs-lookup"><span data-stu-id="0959d-103">Entity Framework no longer throws a <xref:System.StackOverflowException?displayProperty=name> exception when an app executes a query that involves a QueryView with a 0..1 navigation property that attempts to include the related entities as part of the query.</span></span> <span data-ttu-id="0959d-104">たとえば、<code>.Include(e =&gt; e.RelatedNavProp)</code> を呼び出す場合です。</span><span class="sxs-lookup"><span data-stu-id="0959d-104">For example, by calling <code>.Include(e =&gt; e.RelatedNavProp)</code>.</span></span>|
|<span data-ttu-id="0959d-105">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="0959d-105">Suggestion</span></span>|<span data-ttu-id="0959d-106">この変更は、.Include を呼び出すクエリの実行時に 1 - 0..1 の関係にある QueryViews を使用するコードにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="0959d-106">This change only affects code that uses QueryViews with 1-0..1 relationships when running queries that call .Include.</span></span> <span data-ttu-id="0959d-107">これにより信頼性が向上し、ほとんどすべてのアプリに対して透過的になります。</span><span class="sxs-lookup"><span data-stu-id="0959d-107">It improves reliability and should be transparent to almost all apps.</span></span> <span data-ttu-id="0959d-108">ただし、予期しない動作が発生する場合、次のエントリをアプリの構成ファイルの <code>&lt;appSettings&gt;</code> セクションに追加することにより、この変更を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="0959d-108">However, if it causes unexpected behavior, you can disable it by adding the following entry to the <code>&lt;appSettings&gt;</code> section of the app's configuration file:</span></span><pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="0959d-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="0959d-109">Scope</span></span>|<span data-ttu-id="0959d-110">エッジ</span><span class="sxs-lookup"><span data-stu-id="0959d-110">Edge</span></span>|
|<span data-ttu-id="0959d-111">バージョン</span><span class="sxs-lookup"><span data-stu-id="0959d-111">Version</span></span>|<span data-ttu-id="0959d-112">4.5.2</span><span class="sxs-lookup"><span data-stu-id="0959d-112">4.5.2</span></span>|
|<span data-ttu-id="0959d-113">[種類]</span><span class="sxs-lookup"><span data-stu-id="0959d-113">Type</span></span>|<span data-ttu-id="0959d-114">ランタイム</span><span class="sxs-lookup"><span data-stu-id="0959d-114">Runtime</span></span>|
