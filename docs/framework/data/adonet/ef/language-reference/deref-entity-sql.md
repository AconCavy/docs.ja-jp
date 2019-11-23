---
title: DEREF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4c78e833-b260-453d-9bf4-eb39857dd0fa
ms.openlocfilehash: 27fc23a2be47ea00eff20aa8d2f559af5ae90387
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2019
ms.locfileid: "71833905"
---
# <a name="deref-entity-sql"></a><span data-ttu-id="7f976-102">DEREF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7f976-102">DEREF (Entity SQL)</span></span>
<span data-ttu-id="7f976-103">参照値を逆参照し、その逆参照の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="7f976-103">Dereferences a reference value and produces the result of that dereference.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f976-104">構文</span><span class="sxs-lookup"><span data-stu-id="7f976-104">Syntax</span></span>  
  
```sql  
SELECT DEREF ( o.expression ) FROM Table AS o;
```  
  
## <a name="arguments"></a><span data-ttu-id="7f976-105">引数</span><span class="sxs-lookup"><span data-stu-id="7f976-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7f976-106">コレクションを返す任意の有効なクエリ式。</span><span class="sxs-lookup"><span data-stu-id="7f976-106">Any valid query expression that returns a collection.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f976-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="7f976-107">Return Value</span></span>  
 <span data-ttu-id="7f976-108">参照されるエンティティの値。</span><span class="sxs-lookup"><span data-stu-id="7f976-108">The value of the entity that is referenced.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f976-109">コメント</span><span class="sxs-lookup"><span data-stu-id="7f976-109">Remarks</span></span>  
 <span data-ttu-id="7f976-110">DEREF 演算子は参照値を逆参照し、その逆参照の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="7f976-110">The DEREF operator dereferences a reference value and produces the result of that dereference.</span></span> <span data-ttu-id="7f976-111">たとえば、`r` が ref\<T > 型の参照である場合、`Deref(r)` は `T` によって参照されるエンティティを生成する型の式です。`r`</span><span class="sxs-lookup"><span data-stu-id="7f976-111">For example, if `r` is a reference of type ref\<T>, `Deref(r)` is an expression of type `T` that yields the entity referenced by `r`.</span></span> <span data-ttu-id="7f976-112">参照値が null または未解決 (つまり、参照先が存在しない) の場合、DEREF 演算子の結果は null になります。</span><span class="sxs-lookup"><span data-stu-id="7f976-112">If the reference value is null, or is dangling (that is, the target of the reference does not exist), the result of the DEREF operator is null.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f976-113">例</span><span class="sxs-lookup"><span data-stu-id="7f976-113">Example</span></span>  
 <span data-ttu-id="7f976-114">次の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、DEREF 演算子を使用して参照値を逆参照し、その逆参照の結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="7f976-114">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the DEREF operator to dereference a reference value and produce the result of that dereference.</span></span> <span data-ttu-id="7f976-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="7f976-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7f976-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="7f976-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7f976-117">[「方法: PrimitiveType の結果を返すクエリを実行](../how-to-execute-a-query-that-returns-primitivetype-results.md)する」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7f976-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="7f976-118">次のクエリを引数として ExecutePrimitiveTypeQuery メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="7f976-118">Pass the following query as an argument to the ExecutePrimitiveTypeQuery method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DEREF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#deref)]  
  
## <a name="see-also"></a><span data-ttu-id="7f976-119">参照</span><span class="sxs-lookup"><span data-stu-id="7f976-119">See also</span></span>

- [<span data-ttu-id="7f976-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="7f976-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="7f976-121">REF</span><span class="sxs-lookup"><span data-stu-id="7f976-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="7f976-122">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="7f976-122">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="7f976-123">KEY</span><span class="sxs-lookup"><span data-stu-id="7f976-123">KEY</span></span>](key-entity-sql.md)
- [<span data-ttu-id="7f976-124">NULL 値が許容される構造化型</span><span class="sxs-lookup"><span data-stu-id="7f976-124">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
