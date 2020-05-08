---
title: ISNULL (Entity SQL)
ms.date: 03/30/2017
ms.assetid: dc7a0173-3664-4c90-a57b-5cbb0a8ed7ee
ms.openlocfilehash: b3fc2484e80b637ed5841375985f7bae476bbbf7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150201"
---
# <a name="isnull-entity-sql"></a><span data-ttu-id="73b04-102">ISNULL (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="73b04-102">ISNULL (Entity SQL)</span></span>
<span data-ttu-id="73b04-103">クエリ式が NULL かどうかを調べます。</span><span class="sxs-lookup"><span data-stu-id="73b04-103">Determines if a query expression is null.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b04-104">構文</span><span class="sxs-lookup"><span data-stu-id="73b04-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] NULL  
```  
  
## <a name="arguments"></a><span data-ttu-id="73b04-105">引数</span><span class="sxs-lookup"><span data-stu-id="73b04-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="73b04-106">任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="73b04-106">Any valid query expression.</span></span> <span data-ttu-id="73b04-107">コレクションにすることはできません。また、コレクション メンバーや、コレクション型のプロパティを持つレコード型を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="73b04-107">Cannot be a collection, have collection members, or a record type with collection type properties.</span></span>  
  
 <span data-ttu-id="73b04-108">NOT</span><span class="sxs-lookup"><span data-stu-id="73b04-108">NOT</span></span>  
 <span data-ttu-id="73b04-109">IS NULL の EDM.Boolean の結果を否定します。</span><span class="sxs-lookup"><span data-stu-id="73b04-109">Negates the EDM.Boolean result of IS NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73b04-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="73b04-110">Return Value</span></span>  
 <span data-ttu-id="73b04-111">`true` によって NULL が返される場合は `expression`、それ以外の場合は `false` です。</span><span class="sxs-lookup"><span data-stu-id="73b04-111">`true` if `expression` returns null; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73b04-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="73b04-112">Remarks</span></span>  
 <span data-ttu-id="73b04-113">外部結合の要素が NULL かどうかを確認するには、`IS NULL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="73b04-113">Use `IS NULL` to determine if the element of an outer join is null:</span></span>  
  
```sql  
select c
      from LOB.Customers as c left outer join LOB.Orders as o
                              on c.ID = o.CustomerID
      where o is not null and o.OrderQuantity = @x  
```  
  
 <span data-ttu-id="73b04-114">メンバーに実際の値が含まれているかどうかを確認するには、`IS NULL` を使用します。</span><span class="sxs-lookup"><span data-stu-id="73b04-114">Use `IS NULL` to determine if a member has an actual value:</span></span>  
  
```sql  
select c from LOB.Customer as c where c.DOB is not null  
```  
  
 <span data-ttu-id="73b04-115">次の表は、いくつかのパターンにおける `IS NULL` の動作を示しています。</span><span class="sxs-lookup"><span data-stu-id="73b04-115">The following table shows the behavior of `IS NULL` over some patterns.</span></span> <span data-ttu-id="73b04-116">すべての例外はクライアント側にスローされてから、プロバイダーが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="73b04-116">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="73b04-117">パターン</span><span class="sxs-lookup"><span data-stu-id="73b04-117">Pattern</span></span>|<span data-ttu-id="73b04-118">動作</span><span class="sxs-lookup"><span data-stu-id="73b04-118">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="73b04-119">null IS NULL</span><span class="sxs-lookup"><span data-stu-id="73b04-119">null IS NULL</span></span>|<span data-ttu-id="73b04-120">`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="73b04-120">Returns `true`.</span></span>|  
|<span data-ttu-id="73b04-121">TREAT (null AS EntityType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="73b04-121">TREAT (null AS EntityType) IS NULL</span></span>|<span data-ttu-id="73b04-122">`true` を返します。</span><span class="sxs-lookup"><span data-stu-id="73b04-122">Returns `true`.</span></span>|  
|<span data-ttu-id="73b04-123">TREAT (null AS ComplexType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="73b04-123">TREAT (null AS ComplexType) IS NULL</span></span>|<span data-ttu-id="73b04-124">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="73b04-124">Throws an error.</span></span>|  
|<span data-ttu-id="73b04-125">TREAT (null AS RowType) IS NULL</span><span class="sxs-lookup"><span data-stu-id="73b04-125">TREAT (null AS RowType) IS NULL</span></span>|<span data-ttu-id="73b04-126">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="73b04-126">Throws an error.</span></span>|  
|<span data-ttu-id="73b04-127">EntityType IS NULL</span><span class="sxs-lookup"><span data-stu-id="73b04-127">EntityType IS NULL</span></span>|<span data-ttu-id="73b04-128">`true` または `false`を返します。</span><span class="sxs-lookup"><span data-stu-id="73b04-128">Returns `true` or `false`.</span></span>|  
|<span data-ttu-id="73b04-129">ComplexType IS NULL</span><span class="sxs-lookup"><span data-stu-id="73b04-129">ComplexType IS NULL</span></span>|<span data-ttu-id="73b04-130">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="73b04-130">Throws an error.</span></span>|  
|<span data-ttu-id="73b04-131">RowType IS NULL</span><span class="sxs-lookup"><span data-stu-id="73b04-131">RowType IS NULL</span></span>|<span data-ttu-id="73b04-132">エラーをスローします。</span><span class="sxs-lookup"><span data-stu-id="73b04-132">Throws an error.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="73b04-133">例</span><span class="sxs-lookup"><span data-stu-id="73b04-133">Example</span></span>  
 <span data-ttu-id="73b04-134">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、IS NOT NULL 演算子を使用して、クエリ式が NULL でないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="73b04-134">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS NOT NULL operator to determine if a query expression is not null.</span></span> <span data-ttu-id="73b04-135">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="73b04-135">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="73b04-136">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="73b04-136">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="73b04-137">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="73b04-137">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="73b04-138">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="73b04-138">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ISNULL](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#isnull)]  
  
## <a name="see-also"></a><span data-ttu-id="73b04-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="73b04-139">See also</span></span>

- [<span data-ttu-id="73b04-140">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="73b04-140">Entity SQL Reference</span></span>](entity-sql-reference.md)
