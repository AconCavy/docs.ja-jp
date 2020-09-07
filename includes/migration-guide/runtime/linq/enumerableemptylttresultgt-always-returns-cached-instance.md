---
ms.openlocfilehash: 05f60978f5380c406c43aa98ded0c812b1d50694
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497521"
---
### <a name="enumerableemptylttresultgt-always-returns-cached-instance"></a><span data-ttu-id="6158b-101">Enumerable.Empty&lt;TResult&gt; は、常にキャッシュされたインスタンスを返します</span><span class="sxs-lookup"><span data-stu-id="6158b-101">Enumerable.Empty&lt;TResult&gt; always returns cached instance</span></span>

#### <a name="details"></a><span data-ttu-id="6158b-102">説明</span><span class="sxs-lookup"><span data-stu-id="6158b-102">Details</span></span>

<span data-ttu-id="6158b-103">.NET Framework 4.5 以降では、<xref:System.Linq.Enumerable.Empty%60%601> は、常にキャッシュされた内部インスタンス <xref:System.Collections.Generic.IEnumerable%601> を返します。以前は、<xref:System.Linq.Enumerable.Empty%60%601> は、API が呼び出された時点で空の <xref:System.Collections.Generic.IEnumerable%601> をキャッシュしました。つまり、<xref:System.Linq.Enumerable.Empty%60%601> が迅速かつ同時に呼び出されるような条件では、API の別の呼び出しに対して、型の別のインスタンスが返される可能性がありました。</span><span class="sxs-lookup"><span data-stu-id="6158b-103">Beginning in .NET Framework 4.5, <xref:System.Linq.Enumerable.Empty%60%601> always returns a cached internal instance <xref:System.Collections.Generic.IEnumerable%601>.Previously, <xref:System.Linq.Enumerable.Empty%60%601> would cache an empty <xref:System.Collections.Generic.IEnumerable%601> at the time the API was called, meaning that in some conditions in which <xref:System.Linq.Enumerable.Empty%60%601> was called rapidly and concurrently, different instances of the type could be returned for different calls to the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6158b-104">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="6158b-104">Suggestion</span></span>

<span data-ttu-id="6158b-105">以前の動作は非確定的なため、コードがそれに依存している可能性は低いです。</span><span class="sxs-lookup"><span data-stu-id="6158b-105">Because the previous behavior was non-deterministic, code is unlikely to depend on it.</span></span> <span data-ttu-id="6158b-106">ただし、ありそうにないことですが、空の列挙が比較され、ときには等しくないことが予期されている場合には、<xref:System.Linq.Enumerable.Empty%60%601> を使用する代わりに、明示的に空の配列を作成する (<code>new T[0]</code>) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="6158b-106">However, in the unlikely case that empty enumerables are being compared and expected to sometimes be unequal, explicit empty arrays should be created (<code>new T[0]</code>) instead of using <xref:System.Linq.Enumerable.Empty%60%601>.</span></span>

| <span data-ttu-id="6158b-107">名前</span><span class="sxs-lookup"><span data-stu-id="6158b-107">Name</span></span>    | <span data-ttu-id="6158b-108">[値]</span><span class="sxs-lookup"><span data-stu-id="6158b-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6158b-109">スコープ</span><span class="sxs-lookup"><span data-stu-id="6158b-109">Scope</span></span>   |<span data-ttu-id="6158b-110">エッジ</span><span class="sxs-lookup"><span data-stu-id="6158b-110">Edge</span></span>|
|<span data-ttu-id="6158b-111">バージョン</span><span class="sxs-lookup"><span data-stu-id="6158b-111">Version</span></span>|<span data-ttu-id="6158b-112">4.5</span><span class="sxs-lookup"><span data-stu-id="6158b-112">4.5</span></span>|
|<span data-ttu-id="6158b-113">種類</span><span class="sxs-lookup"><span data-stu-id="6158b-113">Type</span></span>|<span data-ttu-id="6158b-114">ランタイム</span><span class="sxs-lookup"><span data-stu-id="6158b-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="6158b-115">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="6158b-115">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.Empty%60%601?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Linq.Enumerable.Empty``1``

-->
