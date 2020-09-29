---
title: + (追加)
ms.date: 03/30/2017
ms.assetid: 51769b02-a8f7-4177-9e99-bbd10e77092c
ms.openlocfilehash: b86d273658362c3bb204d5220ff5e9db1f8de9fe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198055"
---
# <a name="-add"></a><span data-ttu-id="f7fc0-102">+ (加算)</span><span class="sxs-lookup"><span data-stu-id="f7fc0-102">+ (Add)</span></span>

<span data-ttu-id="f7fc0-103">2 つの値を加算します。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-103">Adds two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7fc0-104">構文</span><span class="sxs-lookup"><span data-stu-id="f7fc0-104">Syntax</span></span>  
  
```csharp  
expression + expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="f7fc0-105">引数</span><span class="sxs-lookup"><span data-stu-id="f7fc0-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="f7fc0-106">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f7fc0-107">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="f7fc0-107">Result Types</span></span>  

 <span data-ttu-id="f7fc0-108">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="f7fc0-109">暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7fc0-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="f7fc0-110">Remarks</span></span>  

 <span data-ttu-id="f7fc0-111">EDM.String 型の場合は、値が連結されます。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-111">For EDM.String types, addition is concatenation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7fc0-112">例</span><span class="sxs-lookup"><span data-stu-id="f7fc0-112">Example</span></span>  

 <span data-ttu-id="f7fc0-113">次の Entity SQL クエリでは、+ 算術演算子を使用して 2 つの数値を加算します。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-113">The following Entity SQL query uses the + arithmetic operator to add two numbers.</span></span> <span data-ttu-id="f7fc0-114">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f7fc0-115">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f7fc0-116">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f7fc0-117">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f7fc0-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ADD](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#add)]  
  
## <a name="see-also"></a><span data-ttu-id="f7fc0-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7fc0-118">See also</span></span>

- [<span data-ttu-id="f7fc0-119">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="f7fc0-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f7fc0-120">概念モデルの型 (CSDL)</span><span class="sxs-lookup"><span data-stu-id="f7fc0-120">Conceptual Model Types (CSDL)</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)
