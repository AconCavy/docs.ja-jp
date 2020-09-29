---
title: '- (除算) (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: ef48c368-f3ed-4275-8ada-4e9649781262
ms.openlocfilehash: d7d25d8c5b91850b21e36ba8f6f668af7a7d0045
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148162"
---
# <a name="-divide-entity-sql"></a><span data-ttu-id="9b4dd-102">/ (除算) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="9b4dd-102">/ (Divide) (Entity SQL)</span></span>

<span data-ttu-id="9b4dd-103">1 つの値を別の値で除算します。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-103">Divides one number by another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b4dd-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b4dd-104">Syntax</span></span>  
  
```sql  
dividend / divisor  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b4dd-105">引数</span><span class="sxs-lookup"><span data-stu-id="9b4dd-105">Arguments</span></span>  

 `dividend`  
 <span data-ttu-id="9b4dd-106">除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-106">The numeric expression to divide.</span></span> <span data-ttu-id="9b4dd-107">`dividend` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-107">`dividend` is any valid expression of any one of the numeric data types.</span></span>  
  
 `divisor`  
 <span data-ttu-id="9b4dd-108">被除数を除算する数値式。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-108">The numeric expression to divide the dividend by.</span></span> <span data-ttu-id="9b4dd-109">`divisor` は、任意の数値データ型の有効な式です。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-109">`divisor` is any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9b4dd-110">戻り値の型</span><span class="sxs-lookup"><span data-stu-id="9b4dd-110">Result Types</span></span>  

 <span data-ttu-id="9b4dd-111">2 つの引数の暗黙の型の昇格の結果であるデータ型。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-111">The data type that results from the implicit type promotion of the two arguments.</span></span> <span data-ttu-id="9b4dd-112">暗黙の型の昇格について詳しくは、「[型システム](type-system-entity-sql.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-112">For more information about implicit type promotion, see [Type System](type-system-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b4dd-113">例</span><span class="sxs-lookup"><span data-stu-id="9b4dd-113">Example</span></span>  

 <span data-ttu-id="9b4dd-114">次の Entity SQL クエリでは、/ 算術演算子を使用して 2 つの数値の間で除算をします。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-114">The following Entity SQL query uses the / arithmetic operator to divide one number by another.</span></span> <span data-ttu-id="9b4dd-115">このクエリは、AdventureWorks Sales Model に基づいています。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="9b4dd-116">このクエリをコンパイルして実行するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="9b4dd-117">「[方法: StructuralType 結果を返すクエリを実行する](../how-to-execute-a-query-that-returns-structuraltype-results.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-117">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="9b4dd-118">次のクエリを引数として `ExecuteStructuralTypeQuery` メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="9b4dd-118">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#DIVIDE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#divide)]  
  
## <a name="see-also"></a><span data-ttu-id="9b4dd-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="9b4dd-119">See also</span></span>

- [<span data-ttu-id="9b4dd-120">Entity SQL リファレンス</span><span class="sxs-lookup"><span data-stu-id="9b4dd-120">Entity SQL Reference</span></span>](entity-sql-reference.md)
