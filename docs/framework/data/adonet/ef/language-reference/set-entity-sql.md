---
title: SET (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 28b4deac-c7e4-4f09-b428-4d352ef2dc94
ms.openlocfilehash: 4e2a387cf400a881dfd91c61b36ee3ce0f5a4431
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797775"
---
# <a name="set-entity-sql"></a>SET (Entity SQL)
SET 式は、重複する要素をすべて除外した新しいコレクションを生成することによって、オブジェクトのコレクションを 1 つの集合に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
SET ( expression )  
```  
  
## <a name="arguments"></a>引数  
 `expression`  
 コレクションを返す任意の有効なクエリ式。  
  
## <a name="remarks"></a>Remarks  
 集合式 `SET(c)` は、論理上、次の select ステートメントと等価です。  
  
```  
SELECT VALUE DISTINCT c FROM c  
```  
  
 `SET` は、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] の集合演算子の 1 つです。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] のすべての集合演算子は左から右に評価されます。 参照してください[EXCEPT](../../../../../../docs/framework/data/adonet/ef/language-reference/except-entity-sql.md)の優先順位は、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]演算子を設定します。  
  
## <a name="example"></a>例  
 次の Entity SQL クエリでは、SET 式を使用して、オブジェクトのコレクションを 1 つの集合に変換します。 このクエリは、AdventureWorks Sales Model に基づいています。 このクエリをコンパイルして実行するには、次の手順を実行します。  
  
1. 」の手順に従って[方法。PrimitiveType 結果を返すクエリを実行](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)します。  
  
2. 次のクエリを引数として `ExecutePrimitiveTypeQuery` メソッドに渡します。  
  
 [!code-csharp[DP EntityServices Concepts 2#SET](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#set)]  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
