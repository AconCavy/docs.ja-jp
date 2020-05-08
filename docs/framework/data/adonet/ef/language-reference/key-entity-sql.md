---
title: KEY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: cbaa97a8-c89c-4460-8c74-00474695789f
ms.openlocfilehash: 894a9d41aa3a14ad66b537433aa315823a299f95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150170"
---
# <a name="key-entity-sql"></a><span data-ttu-id="6b46f-102">KEY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6b46f-102">KEY (Entity SQL)</span></span>
<span data-ttu-id="6b46f-103">参照またはエンティティ式のキーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="6b46f-103">Extracts the key of a reference or of an entity expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b46f-104">構文</span><span class="sxs-lookup"><span data-stu-id="6b46f-104">Syntax</span></span>  
  
```sql  
KEY(createref_expression)  
```  
  
## <a name="remarks"></a><span data-ttu-id="6b46f-105">Remarks</span><span class="sxs-lookup"><span data-stu-id="6b46f-105">Remarks</span></span>  
 <span data-ttu-id="6b46f-106">エンティティ キーには、指定されたエンティティまたはエンティティ参照の正しい順序でキー値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="6b46f-106">An entity key contains the key values in the correct order of the specified entity or entity reference.</span></span> <span data-ttu-id="6b46f-107">複数のエンティティ セットが同じ型に基づくことができるので、同じキーがそれぞれのエンティティ セットで使用される場合があります。</span><span class="sxs-lookup"><span data-stu-id="6b46f-107">Because multiple entity sets can be based on the same type, the same key might appear in each entity set.</span></span> <span data-ttu-id="6b46f-108">一意の参照を取得するには、 `REF`を使用します。</span><span class="sxs-lookup"><span data-stu-id="6b46f-108">To get a unique reference, use `REF`.</span></span> <span data-ttu-id="6b46f-109">KEY 演算子の戻り値の型は、同じ順序でエンティティの各キーの 1 つのフィールドを含む行型です。</span><span class="sxs-lookup"><span data-stu-id="6b46f-109">The return type of the KEY operator is a row type that includes one field for each key of the entity, in the same order.</span></span>  
  
 <span data-ttu-id="6b46f-110">次の例では、キー演算子は、BadOrder エンティティへの参照に渡され、その参照のキー部分を返します。</span><span class="sxs-lookup"><span data-stu-id="6b46f-110">In the following example, the key operator is passed a reference to the BadOrder entity, and returns the key portion of that reference.</span></span> <span data-ttu-id="6b46f-111">この場合、 `Id` プロパティに対応する 1 つだけのフィールドを持つレコード型です。</span><span class="sxs-lookup"><span data-stu-id="6b46f-111">In this case, a record type with exactly one field corresponding to the `Id` property.</span></span>  
  
```sql  
select Key( CreateRef(LOB.BadOrders, row(o.Id)) )
from LOB.Orders as o  
```  
  
## <a name="example"></a><span data-ttu-id="6b46f-112">例</span><span class="sxs-lookup"><span data-stu-id="6b46f-112">Example</span></span>  
 <span data-ttu-id="6b46f-113">次の Entity SQL クエリは、KEY 演算子を使用して、型参照を持つ式のキー部分を抽出します。</span><span class="sxs-lookup"><span data-stu-id="6b46f-113">The following Entity SQL query uses the KEY operator to extract the key portion of an expression with type reference.</span></span> <span data-ttu-id="6b46f-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6b46f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6b46f-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="6b46f-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6b46f-116">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="6b46f-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6b46f-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="6b46f-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#KEY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#key)]  
  
## <a name="see-also"></a><span data-ttu-id="6b46f-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b46f-118">See also</span></span>

- [<span data-ttu-id="6b46f-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="6b46f-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6b46f-120">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="6b46f-120">CREATEREF</span></span>](createref-entity-sql.md)
- [<span data-ttu-id="6b46f-121">REF</span><span class="sxs-lookup"><span data-stu-id="6b46f-121">REF</span></span>](ref-entity-sql.md)
- [<span data-ttu-id="6b46f-122">DEREF</span><span class="sxs-lookup"><span data-stu-id="6b46f-122">DEREF</span></span>](deref-entity-sql.md)
