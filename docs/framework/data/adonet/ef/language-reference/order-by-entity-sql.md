---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150070"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="ed523-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="ed523-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="ed523-103">SELECT ステートメントで返されるオブジェクトで使用される並べ替え順を指定します。</span><span class="sxs-lookup"><span data-stu-id="ed523-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed523-104">構文</span><span class="sxs-lookup"><span data-stu-id="ed523-104">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="ed523-105">引数</span><span class="sxs-lookup"><span data-stu-id="ed523-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="ed523-106">並べ替えるプロパティを指定する有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="ed523-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="ed523-107">並べ替えのキーとなる式を複数指定できます。</span><span class="sxs-lookup"><span data-stu-id="ed523-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="ed523-108">ORDER BY 句内に記述するキー式の並び順によって、並べ替えられた結果セットの構成が決まります。</span><span class="sxs-lookup"><span data-stu-id="ed523-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="ed523-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="ed523-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="ed523-110">ORDER BY 操作が `collation_name`で指定された照合順序に従って実行されることを指定します。</span><span class="sxs-lookup"><span data-stu-id="ed523-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="ed523-111">COLLATE は文字列式にのみ適用できます。</span><span class="sxs-lookup"><span data-stu-id="ed523-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="ed523-112">ASC</span><span class="sxs-lookup"><span data-stu-id="ed523-112">ASC</span></span>  
 <span data-ttu-id="ed523-113">指定したプロパティの値が昇順、つまり小さい値から大きい値へと並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="ed523-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="ed523-114">これは既定値です。</span><span class="sxs-lookup"><span data-stu-id="ed523-114">This is the default.</span></span>  
  
 <span data-ttu-id="ed523-115">DESC</span><span class="sxs-lookup"><span data-stu-id="ed523-115">DESC</span></span>  
 <span data-ttu-id="ed523-116">指定したプロパティの値が降順、つまり大きい値から小さい値へと並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="ed523-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="ed523-117">LIMIT `n`</span><span class="sxs-lookup"><span data-stu-id="ed523-117">LIMIT `n`</span></span>  
 <span data-ttu-id="ed523-118">最初の `n` 個の項目のみが選択されます。</span><span class="sxs-lookup"><span data-stu-id="ed523-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="ed523-119">SKIP `n`</span><span class="sxs-lookup"><span data-stu-id="ed523-119">SKIP `n`</span></span>  
 <span data-ttu-id="ed523-120">最初の `n` 個の項目をスキップします。</span><span class="sxs-lookup"><span data-stu-id="ed523-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed523-121">解説</span><span class="sxs-lookup"><span data-stu-id="ed523-121">Remarks</span></span>  
 <span data-ttu-id="ed523-122">ORDER BY 句は、SELECT 句の結果に論理的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="ed523-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="ed523-123">ORDER BY 句では、別名を使用して選択リストの項目を参照できます。</span><span class="sxs-lookup"><span data-stu-id="ed523-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="ed523-124">ORDER BY 句は、現在スコープ内にあるその他の変数も参照できます。</span><span class="sxs-lookup"><span data-stu-id="ed523-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="ed523-125">ただし、SELECT 句が DISTINCT 修飾子で指定されている場合は、ORDER BY 句は SELECT 句の別名のみを参照できます。</span><span class="sxs-lookup"><span data-stu-id="ed523-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="ed523-126">ORDER BY 句内の各式は、順序付けられた不等号 (より小さい、より大きいなど) について比較できる型として評価される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed523-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="ed523-127">通常、これらの型は数値、文字列、日付などのスカラー プリミティブです。</span><span class="sxs-lookup"><span data-stu-id="ed523-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="ed523-128">比較できる型の RowType は順序も比較できます。</span><span class="sxs-lookup"><span data-stu-id="ed523-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="ed523-129">順序付けされたセットで、最上位の投影を除きコードが反復処理を行う場合、出力でその順序が維持されることは保証されません。</span><span class="sxs-lookup"><span data-stu-id="ed523-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="ed523-130">次の例では、順序が保持されます。</span><span class="sxs-lookup"><span data-stu-id="ed523-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="ed523-131">次のクエリでは、入れ子になったクエリの順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ed523-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="ed523-132">UNION、UNION ALL、EXCEPT、または INTERSECT 操作を順序付けするには、次のパターンを使用してください。</span><span class="sxs-lookup"><span data-stu-id="ed523-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="ed523-133">制限付きのキーワード</span><span class="sxs-lookup"><span data-stu-id="ed523-133">Restricted keywords</span></span>  
 <span data-ttu-id="ed523-134">次のキーワードは `ORDER BY` 句で使用する場合には、引用符で囲む必要があります。</span><span class="sxs-lookup"><span data-stu-id="ed523-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="ed523-135">CROSS</span><span class="sxs-lookup"><span data-stu-id="ed523-135">CROSS</span></span>  
  
- <span data-ttu-id="ed523-136">FULL</span><span class="sxs-lookup"><span data-stu-id="ed523-136">FULL</span></span>  
  
- <span data-ttu-id="ed523-137">KEY</span><span class="sxs-lookup"><span data-stu-id="ed523-137">KEY</span></span>  
  
- <span data-ttu-id="ed523-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="ed523-138">LEFT</span></span>  
  
- <span data-ttu-id="ed523-139">ORDER</span><span class="sxs-lookup"><span data-stu-id="ed523-139">ORDER</span></span>  
  
- <span data-ttu-id="ed523-140">OUTER</span><span class="sxs-lookup"><span data-stu-id="ed523-140">OUTER</span></span>  
  
- <span data-ttu-id="ed523-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="ed523-141">RIGHT</span></span>  
  
- <span data-ttu-id="ed523-142">ROW</span><span class="sxs-lookup"><span data-stu-id="ed523-142">ROW</span></span>  
  
- <span data-ttu-id="ed523-143">値</span><span class="sxs-lookup"><span data-stu-id="ed523-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="ed523-144">入れ子になったクエリの順序</span><span class="sxs-lookup"><span data-stu-id="ed523-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="ed523-145">Entity Framework では、入れ子になった式をクエリ内の任意の場所に配置できるため、入れ子になったクエリの順序は維持されません。</span><span class="sxs-lookup"><span data-stu-id="ed523-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="ed523-146">次のクエリは、結果を姓順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="ed523-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="ed523-147">次のクエリでは、入れ子になったクエリの順序は無視されます。</span><span class="sxs-lookup"><span data-stu-id="ed523-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="ed523-148">例</span><span class="sxs-lookup"><span data-stu-id="ed523-148">Example</span></span>  
 <span data-ttu-id="ed523-149">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、SELECT ステートメントで返されたオブジェクトの並べ替え順序の指定に ORDER BY 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="ed523-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="ed523-150">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="ed523-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="ed523-151">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="ed523-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="ed523-152">「 [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ed523-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="ed523-153">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="ed523-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="ed523-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed523-154">See also</span></span>

- [<span data-ttu-id="ed523-155">クエリ式</span><span class="sxs-lookup"><span data-stu-id="ed523-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="ed523-156">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="ed523-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="ed523-157">スキップ</span><span class="sxs-lookup"><span data-stu-id="ed523-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="ed523-158">制限</span><span class="sxs-lookup"><span data-stu-id="ed523-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="ed523-159">ページのトップへ</span><span class="sxs-lookup"><span data-stu-id="ed523-159">TOP</span></span>](top-entity-sql.md)
