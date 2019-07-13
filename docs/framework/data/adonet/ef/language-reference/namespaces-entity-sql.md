---
title: 名前空間 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7bcd7a72df8afbd598a15ccd9a259ed11b5b9ef7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583813"
---
# <a name="namespaces-entity-sql"></a>名前空間 (Entity SQL)
型名、エンティティ セット、関数など、グローバル識別子の名前の競合を防ぐために、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] には名前空間が採用されています。 名前空間のサポートで[!INCLUDE[esql](../../../../../../includes/esql-md.md)]は .NET framework 名前空間のサポートに似ています。  
  
 次の例のように、[!INCLUDE[esql](../../../../../../includes/esql-md.md)] では、2 とおりの形式で USING 句を指定できます。1 つは略称的な別名を指定する修飾名前空間、もう 1 つは別名を指定しない非修飾名前空間です。  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a>名前解決ルール  
 識別子は、ローカルのスコープで解決できない場合[!INCLUDE[esql](../../../../../../includes/esql-md.md)]グローバル スコープ (名前空間) での名前を検索しようとしています。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] は、まず識別子 (プレフィックス) と修飾名前空間の 1 つを照合します。 場合は、一致がある[!INCLUDE[esql](../../../../../../includes/esql-md.md)]指定した名前空間識別子の残りの部分を解決しようと試みます。 一致が見つからなかった場合は、例外がスローされます。  
  
 次に、[!INCLUDE[esql](../../../../../../includes/esql-md.md)]すべて非修飾の名前空間 (プロローグで指定)、識別子を検索しようとしています。 その識別子が属している名前空間を一意に特定できた場合は、その場所が返されます。 同じ識別子に対して複数の名前空間が見つかった場合は、例外がスローされます。 場合は、識別子の名前空間が識別されない[!INCLUDE[esql](../../../../../../includes/esql-md.md)][次へ] の外側のスコープに名前を渡します (、<xref:System.Data.Common.DbCommand>または<xref:System.Data.Common.DbConnection>オブジェクト)、次の例に示すように。  
  
```  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a>.NET Framework との違い  
 .NET Framework では、部分的に修飾名前空間を使用できます。 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] では使用できません。  
  
## <a name="adonet-usage"></a>ADO.NET の使用法  
 クエリは、ADO.NET の <xref:System.Data.Common.DbCommand> オブジェクトを使用して表されます。 <xref:System.Data.Common.DbCommand> オブジェクトは、<xref:System.Data.Common.DbConnection> オブジェクトに対して構築できます。 名前空間を <xref:System.Data.Common.DbCommand> オブジェクトや <xref:System.Data.Common.DbConnection> オブジェクトの一部として指定することもできます。 場合[!INCLUDE[esql](../../../../../../includes/esql-md.md)]識別子を解決できないクエリ自体内で、外部の名前空間が、(同様のルールに基づいて) が調査します。  
  
## <a name="see-also"></a>関連項目

- [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
