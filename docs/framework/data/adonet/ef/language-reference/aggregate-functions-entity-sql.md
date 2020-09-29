---
title: 集計関数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: acfd3149-f519-4c6e-8fe1-b21d243a0e58
ms.openlocfilehash: 308670f04b9a04b1fff77ece08deb39c8c4081d1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198081"
---
# <a name="aggregate-functions-entity-sql"></a><span data-ttu-id="1bc4c-102">集計関数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1bc4c-102">Aggregate Functions (Entity SQL)</span></span>

<span data-ttu-id="1bc4c-103">集計は、コレクションをグループ操作の一部としてスカラーに圧縮する言語構成要素です。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-103">An aggregate is a language construct that condenses a collection into a scalar as a part of a group operation.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1bc4c-104">集計には次の 2 つの形式があります。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-104">aggregates come in two forms:</span></span>  
  
- <span data-ttu-id="1bc4c-105">式内のあらゆる位置で使用できる [!INCLUDE[esql](../../../../../../includes/esql-md.md)] コレクション関数。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-105">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] collection functions that may be used anywhere in an expression.</span></span> <span data-ttu-id="1bc4c-106">これには、コレクションに対して作用するプロジェクションおよび述語での集計関数の使用が含まれます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-106">This includes using aggregate functions in projections and predicates that act on collections.</span></span> <span data-ttu-id="1bc4c-107">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] で集計を指定するには、コレクション関数を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-107">Collection functions are the preferred mode of specifying aggregates in [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span>  
  
- <span data-ttu-id="1bc4c-108">GROUP BY 句を含むクエリ式内のグループ集計。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-108">Group aggregates in query expressions that have a GROUP BY clause.</span></span> <span data-ttu-id="1bc4c-109">Transact-SQL と同様に、グループ集計では集計の入力に対する修飾子として DISTINCT と ALL を受け入れます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-109">As in Transact-SQL, group aggregates accept DISTINCT and ALL as modifiers to the aggregate input.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1bc4c-110">は、まず式をコレクション関数として解釈しようとしますが、SELECT 式のコンテキストにある式はグループ集計として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-110">first tries to interpret an expression as a collection function and if the expression is in the context of a SELECT expression it interprets it as a group aggregate.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1bc4c-111">では、[GROUPPARTITION](grouppartition-entity-sql.md) という特殊な集計演算子が定義されます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-111">defines a special aggregate operator called [GROUPPARTITION](grouppartition-entity-sql.md).</span></span> <span data-ttu-id="1bc4c-112">この演算子を使用すると、グループ化された入力セットへの参照を取得できます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-112">This operator enables you to get a reference to the grouped input set.</span></span> <span data-ttu-id="1bc4c-113">これにより、GROUP BY 句の結果をグループ集計関数やコレクション関数以外の場所で使用できる高度なグループ化クエリが可能になります。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-113">This allows more advanced grouping queries, where the results of the GROUP BY clause can be used in places other than group aggregate or collection functions.</span></span>  
  
## <a name="collection-functions"></a><span data-ttu-id="1bc4c-114">コレクション関数</span><span class="sxs-lookup"><span data-stu-id="1bc4c-114">Collection Functions</span></span>  

 <span data-ttu-id="1bc4c-115">コレクション関数はコレクションに対して実行され、スカラー値を返します。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-115">Collection functions operate on collections and return a scalar value.</span></span> <span data-ttu-id="1bc4c-116">たとえば、`orders` がすべての `orders` のコレクションである場合、次の式を使用して、最も早い出荷日を計算できます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-116">For example, if `orders` is a collection of all `orders`, you can calculate the earliest ship date with the following expression:</span></span>  
  
 `min(select value o.ShipDate from LOB.Orders as o)`  
  
## <a name="group-aggregates"></a><span data-ttu-id="1bc4c-117">グループ集計</span><span class="sxs-lookup"><span data-stu-id="1bc4c-117">Group Aggregates</span></span>  

 <span data-ttu-id="1bc4c-118">グループ集計では、GROUP BY 句によって定義されたグループ結果ごとに計算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-118">Group aggregates are calculated over a group result as defined by the GROUP BY clause.</span></span> <span data-ttu-id="1bc4c-119">GROUP BY 句により、データがグループに分けられます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-119">The GROUP BY clause partitions data  into groups.</span></span> <span data-ttu-id="1bc4c-120">分けられた各グループに集計関数が適用され、それぞれのグループ内の要素を集計計算の入力として使用して、各集計が計算されます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-120">For each group in the result, the aggregate function is applied and a separate aggregate is calculated by using the elements in each group as inputs to the aggregate calculation.</span></span> <span data-ttu-id="1bc4c-121">SELECT 式で GROUP BY 句を使用した場合、プロジェクション、HAVING、または ORDER BY 句で使用できるのは、グループ化式の名前、集計式、または定数式だけです。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-121">When a GROUP BY clause is used in a SELECT expression, only grouping expression names, aggregates, or constant expressions may be present in the projection, HAVING, or ORDER BY clause.</span></span>  
  
 <span data-ttu-id="1bc4c-122">次の例では、製品ごとの平均発注数量を計算しています。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-122">The following example calculates the average quantity ordered for each product.</span></span>  
  
 `select p, avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `group by ol.Product as p`  
  
 <span data-ttu-id="1bc4c-123">SELECT 式に明示的な GROUP BY 句を指定せずに、グループ集計を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-123">It is possible to have a group aggregate without an explicit GROUP BY clause in the SELECT expression.</span></span> <span data-ttu-id="1bc4c-124">すべての要素が 1 つのグループとして処理されます。これは定数に基づくグループ化を指定する場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-124">All elements will be treated as a single group, equivalent to the case of specifying a grouping based on a constant.</span></span>  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol`  
  
 `select avg(ol.Quantity) from LOB.OrderLines as ol group by 1`  
  
 <span data-ttu-id="1bc4c-125">GROUP BY 句で使用される式は、WHERE 句式から参照できる同じ名前解決スコープを使用して評価されます。</span><span class="sxs-lookup"><span data-stu-id="1bc4c-125">Expressions used in the GROUP BY clause are evaluated by using the same name-resolution scope that would be visible to the WHERE clause expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc4c-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bc4c-126">See also</span></span>

- [<span data-ttu-id="1bc4c-127">関数</span><span class="sxs-lookup"><span data-stu-id="1bc4c-127">Functions</span></span>](functions-entity-sql.md)
