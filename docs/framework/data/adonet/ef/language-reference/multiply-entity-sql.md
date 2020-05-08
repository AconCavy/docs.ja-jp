---
title: '* (乗算) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 508ce246-4e86-47dd-a605-4af4bebb9891
ms.openlocfilehash: 7006f5143e8cc18156f748ae7664f3787c9ff5c9
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319613"
---
# <a name="-multiply-entity-sql"></a><span data-ttu-id="5ee49-102">\* (乗算) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="5ee49-102">\* (Multiply) (Entity SQL)</span></span>
<span data-ttu-id="5ee49-103">2 つの式を乗算します。</span><span class="sxs-lookup"><span data-stu-id="5ee49-103">Multiplies two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee49-104">構文</span><span class="sxs-lookup"><span data-stu-id="5ee49-104">Syntax</span></span>  
  
```sql  
expression * expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="5ee49-105">引数</span><span class="sxs-lookup"><span data-stu-id="5ee49-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="5ee49-106">任意の数値データ型の有効な式。</span><span class="sxs-lookup"><span data-stu-id="5ee49-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="5ee49-107">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="5ee49-107">Result Types</span></span>  
 <span data-ttu-id="5ee49-108">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="5ee49-108">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="5ee49-109">暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5ee49-109">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ee49-110">例</span><span class="sxs-lookup"><span data-stu-id="5ee49-110">Example</span></span>  
 <span data-ttu-id="5ee49-111">次の Entity SQL クエリでは、\* 算術演算子を使用して 2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="5ee49-111">The following Entity SQL query uses the \* arithmetic operator to multiply two numbers.</span></span> <span data-ttu-id="5ee49-112">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="5ee49-112">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="5ee49-113">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="5ee49-113">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="5ee49-114">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="5ee49-114">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="5ee49-115">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="5ee49-115">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#MULTIPLY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#multiply)]  
  
## <a name="see-also"></a><span data-ttu-id="5ee49-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5ee49-116">See also</span></span>

- [<span data-ttu-id="5ee49-117">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="5ee49-117">Entity SQL Reference</span></span>](entity-sql-reference.md)
