---
title: 集計正規関数
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 3f4bb84c45e503fc0018e7869f3b41ddab4581a6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251353"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="febef-102">集計正規関数</span><span class="sxs-lookup"><span data-stu-id="febef-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="febef-103">集計とは、一連の入力値をまとまった値 (単一の値など) に変換する式を指します。</span><span class="sxs-lookup"><span data-stu-id="febef-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="febef-104">集計は SELECT 式の GROUP BY 句と組み合わせて使用されるのが一般的であり、どこで使用できるかについては制約があります。</span><span class="sxs-lookup"><span data-stu-id="febef-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="febef-105">集計 Entity SQL 正規関数</span><span class="sxs-lookup"><span data-stu-id="febef-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="febef-106">集計 Entity SQL 正規関数を次に示します。</span><span class="sxs-lookup"><span data-stu-id="febef-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="febef-107">Avg(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-107">Avg(expression)</span></span>

<span data-ttu-id="febef-108">NULL 以外の値の平均を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="febef-109">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-109">**Arguments**</span></span>

<span data-ttu-id="febef-110">`Int32`、`Int64`、`Double`、および `Decimal`。</span><span class="sxs-lookup"><span data-stu-id="febef-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="febef-111">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-111">**Return Value**</span></span>

<span data-ttu-id="febef-112">`expression` の型、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="febef-113">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="febef-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-114">BigCount(expression)</span></span>

<span data-ttu-id="febef-115">NULL 値および重複値を含む集計のサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="febef-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="febef-116">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-116">**Arguments**</span></span>

<span data-ttu-id="febef-117">任意の型。</span><span class="sxs-lookup"><span data-stu-id="febef-117">Any type.</span></span>

<span data-ttu-id="febef-118">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-118">**Return Value**</span></span>

<span data-ttu-id="febef-119">`Int64`。</span><span class="sxs-lookup"><span data-stu-id="febef-119">An `Int64`.</span></span>

<span data-ttu-id="febef-120">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="febef-121">Count(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-121">Count(expression)</span></span>

<span data-ttu-id="febef-122">NULL 値および重複値を含む集計のサイズを返します。</span><span class="sxs-lookup"><span data-stu-id="febef-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="febef-123">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-123">**Arguments**</span></span>

<span data-ttu-id="febef-124">任意の型。</span><span class="sxs-lookup"><span data-stu-id="febef-124">Any type.</span></span>

<span data-ttu-id="febef-125">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-125">**Return Value**</span></span>

<span data-ttu-id="febef-126">`Int32`。</span><span class="sxs-lookup"><span data-stu-id="febef-126">An `Int32`.</span></span>

<span data-ttu-id="febef-127">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="febef-128">Max(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-128">Max(expression)</span></span>

<span data-ttu-id="febef-129">NULL 以外の値の最大値を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="febef-130">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-130">**Arguments**</span></span>

<span data-ttu-id="febef-131">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="febef-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="febef-132">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-132">**Return Value**</span></span>

<span data-ttu-id="febef-133">`expression` の型、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="febef-134">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="febef-135">Min(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-135">Min(expression)</span></span>

<span data-ttu-id="febef-136">NULL 以外の値の最小値を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="febef-137">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-137">**Arguments**</span></span>

<span data-ttu-id="febef-138">`Byte`、`Int16`、`Int32`、`Int64`、`Byte`、`Single`、`Double`、`Decimal`、`DateTime`、`DateTimeOffset`、`Time`、`String`、`Binary`。</span><span class="sxs-lookup"><span data-stu-id="febef-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="febef-139">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-139">**Return Value**</span></span>

<span data-ttu-id="febef-140">`expression` の型、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="febef-141">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="febef-142">StDev(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-142">StDev(expression)</span></span>

<span data-ttu-id="febef-143">NULL 以外の値の標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="febef-144">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-144">**Arguments**</span></span>

<span data-ttu-id="febef-145">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="febef-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="febef-146">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-146">**Return Value**</span></span>

<span data-ttu-id="febef-147">`Double`。</span><span class="sxs-lookup"><span data-stu-id="febef-147">A `Double`.</span></span> <span data-ttu-id="febef-148">すべての入力値が `Null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="febef-149">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="febef-150">StDevP(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-150">StDevP(expression)</span></span>

<span data-ttu-id="febef-151">すべての値の母集団の標準偏差を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="febef-152">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-152">**Arguments**</span></span>

<span data-ttu-id="febef-153">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="febef-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="febef-154">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-154">**Return Value**</span></span>

<span data-ttu-id="febef-155">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="febef-156">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="febef-157">Sum(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-157">Sum(expression)</span></span>

<span data-ttu-id="febef-158">NULL 以外の値の合計を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="febef-159">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-159">**Arguments**</span></span>

<span data-ttu-id="febef-160">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="febef-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="febef-161">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-161">**Return Value**</span></span>

<span data-ttu-id="febef-162">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="febef-163">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="febef-164">Var(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-164">Var(expression)</span></span>

<span data-ttu-id="febef-165">すべての null 以外の値の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="febef-166">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-166">**Arguments**</span></span>

<span data-ttu-id="febef-167">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="febef-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="febef-168">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-168">**Return Value**</span></span>

<span data-ttu-id="febef-169">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="febef-170">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="febef-171">VarP(expression)</span><span class="sxs-lookup"><span data-stu-id="febef-171">VarP(expression)</span></span>

<span data-ttu-id="febef-172">すべての null 以外の値の母集団の分散を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="febef-173">**引数**</span><span class="sxs-lookup"><span data-stu-id="febef-173">**Arguments**</span></span>

<span data-ttu-id="febef-174">`Int32`、`Int64`、`Double`、`Decimal`。</span><span class="sxs-lookup"><span data-stu-id="febef-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="febef-175">**戻り値**</span><span class="sxs-lookup"><span data-stu-id="febef-175">**Return Value**</span></span>

<span data-ttu-id="febef-176">`Double`、またはすべての入力値が `null` の場合は `null` です。</span><span class="sxs-lookup"><span data-stu-id="febef-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="febef-177">**例**</span><span class="sxs-lookup"><span data-stu-id="febef-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="febef-178">同等の機能は、Microsoft SQL クライアント マネージド プロバイダーでも利用できます。</span><span class="sxs-lookup"><span data-stu-id="febef-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="febef-179">詳細については、「[Entity Framework 用 SqlClient 関数](../sqlclient-for-ef-functions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="febef-179">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="febef-180">コレクションベースの集計</span><span class="sxs-lookup"><span data-stu-id="febef-180">Collection-based aggregates</span></span>

<span data-ttu-id="febef-181">コレクションベースの集計 (コレクション関数) は、コレクションに対して演算を実行して、値を返します。</span><span class="sxs-lookup"><span data-stu-id="febef-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="febef-182">たとえば、ORDERS がすべての注文のコレクションである場合、次の式を使って、最も早い出荷日を計算できます。</span><span class="sxs-lookup"><span data-stu-id="febef-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="febef-183">コレクションベースの集計では、現在の周囲の名前解決スコープ内で式が評価されます。</span><span class="sxs-lookup"><span data-stu-id="febef-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="febef-184">グループベースの集計</span><span class="sxs-lookup"><span data-stu-id="febef-184">Group-based aggregates</span></span>

<span data-ttu-id="febef-185">グループベースの集計では、GROUP BY 句によって定義されたグループごとに計算が実行されます。</span><span class="sxs-lookup"><span data-stu-id="febef-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="febef-186">その結果の各グループについて、それぞれのグループ内の要素を、集計計算の入力として使って別個の集計が計算されます。</span><span class="sxs-lookup"><span data-stu-id="febef-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="febef-187">select 式で group by 句を使用した場合、投影または order by 句で使用できるのは、グループ化式の名前、集計式、または定数式だけです。</span><span class="sxs-lookup"><span data-stu-id="febef-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="febef-188">次の例では、製品ごとの平均発注数量を計算しています。</span><span class="sxs-lookup"><span data-stu-id="febef-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="febef-189">SELECT 式に明示的な group by 句を指定せずに、グループベースの集計を行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="febef-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="febef-190">この場合、すべての要素が単一のグループとして扱われます。</span><span class="sxs-lookup"><span data-stu-id="febef-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="febef-191">これは、定数に基づくグループ化の指定と同等です。</span><span class="sxs-lookup"><span data-stu-id="febef-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="febef-192">たとえば、次のような式があったとします。</span><span class="sxs-lookup"><span data-stu-id="febef-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="febef-193">これは、次の指定と同じです。</span><span class="sxs-lookup"><span data-stu-id="febef-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="febef-194">グループベースの集計内の式は、WHERE 句式から可視である名前解決スコープ内で評価されます。</span><span class="sxs-lookup"><span data-stu-id="febef-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="febef-195">Transact-SQL の場合と同様、グループベースの集計には、ALL または DISTINCT の修飾子を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="febef-195">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="febef-196">DISTINCT 修飾子が指定された場合、集計を計算する前に、集計の入力コレクションから重複が除外されます。</span><span class="sxs-lookup"><span data-stu-id="febef-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="febef-197">ALL 修飾子が指定された場合 (または修飾子が指定されなかった場合)、重複は除外されません。</span><span class="sxs-lookup"><span data-stu-id="febef-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="febef-198">関連項目</span><span class="sxs-lookup"><span data-stu-id="febef-198">See also</span></span>

- [<span data-ttu-id="febef-199">正規関数</span><span class="sxs-lookup"><span data-stu-id="febef-199">Canonical Functions</span></span>](canonical-functions.md)
