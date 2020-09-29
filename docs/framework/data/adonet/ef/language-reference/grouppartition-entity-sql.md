---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 11abebeac682fed9e3a007986bb2f5c7bdb80f16
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204477"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="01bac-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="01bac-102">GROUPPARTITION (Entity SQL)</span></span>

<span data-ttu-id="01bac-103">引数値のコレクションを返します。この値は、集計が関連する現在のグループ パーティションから投影されたものです。</span><span class="sxs-lookup"><span data-stu-id="01bac-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="01bac-104">`GroupPartition` 集計は、グループベースの集計であり、コレクションベースの形式ではありません。</span><span class="sxs-lookup"><span data-stu-id="01bac-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01bac-105">構文</span><span class="sxs-lookup"><span data-stu-id="01bac-105">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="01bac-106">引数</span><span class="sxs-lookup"><span data-stu-id="01bac-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="01bac-107">任意のブール型 ( [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ) の式を指定します。</span><span class="sxs-lookup"><span data-stu-id="01bac-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01bac-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="01bac-108">Remarks</span></span>  

 <span data-ttu-id="01bac-109">次のクエリでは、製品の一覧と、製品ごとの注文明細の数量のコレクションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="01bac-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="01bac-110">次の 2 つのクエリは、同じ意味を持っています。</span><span class="sxs-lookup"><span data-stu-id="01bac-110">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="01bac-111">`GROUPPARTITION` 演算子は、ユーザー定義の集計関数と組み合わせて使用できます。</span><span class="sxs-lookup"><span data-stu-id="01bac-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="01bac-112">`GROUPPARTITION` は、グループ化された入力セットへの参照を格納する特殊な集計演算子です。</span><span class="sxs-lookup"><span data-stu-id="01bac-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="01bac-113">この参照は、GROUP BY がスコープに含まれているクエリ内の任意の位置で使用できます。</span><span class="sxs-lookup"><span data-stu-id="01bac-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="01bac-114">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="01bac-114">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="01bac-115">通常の `GROUP BY` では、グループ化の結果は非表示です。</span><span class="sxs-lookup"><span data-stu-id="01bac-115">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="01bac-116">結果は集計関数でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="01bac-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="01bac-117">グループ化の結果を表示するには、サブクエリを使用してグループ化の結果と、入力セットを相関させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="01bac-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="01bac-118">次の 2 つのクエリは等価です。</span><span class="sxs-lookup"><span data-stu-id="01bac-118">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="01bac-119">例からわかるように、GROUPPARTITION 集計演算子を使用すると、グループ化後の入力セットへの参照を容易に取得できます。</span><span class="sxs-lookup"><span data-stu-id="01bac-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="01bac-120">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] パラメーターを使用すると、GROUPPARTITION 演算子では、演算子入力内の任意の `expression` 式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="01bac-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="01bac-121">たとえば、グループ パーティションへの次の入力式はすべて有効です。</span><span class="sxs-lookup"><span data-stu-id="01bac-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="01bac-122">例</span><span class="sxs-lookup"><span data-stu-id="01bac-122">Example</span></span>  

 <span data-ttu-id="01bac-123">次の例では、GROUPPARTITION 句を GROUP BY 句と共に使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="01bac-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="01bac-124">GROUP BY 句は `SalesOrderHeader` によって `Contact`エンティティをグループ化します。</span><span class="sxs-lookup"><span data-stu-id="01bac-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="01bac-125">続いて GROUPPARTITION 句は、各グループの `TotalDue` プロパティを投影し、その結果、10 進数のコレクションが生成されます。</span><span class="sxs-lookup"><span data-stu-id="01bac-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
