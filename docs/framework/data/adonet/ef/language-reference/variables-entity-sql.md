---
title: 変数 (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
ms.openlocfilehash: 88ee41bc08711cf84b8b2e273c9ac0f4267d1d34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149818"
---
# <a name="variables-entity-sql"></a><span data-ttu-id="c6ae7-102">変数 (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c6ae7-102">Variables (Entity SQL)</span></span>
## <a name="variable"></a><span data-ttu-id="c6ae7-103">変数</span><span class="sxs-lookup"><span data-stu-id="c6ae7-103">Variable</span></span>  
 <span data-ttu-id="c6ae7-104">変数式は、現在のスコープで定義されている名前付きの式への参照です。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-104">A variable expression is a reference to a named expression defined in the current scope.</span></span> <span data-ttu-id="c6ae7-105">変数参照は、[識別子](identifiers-entity-sql.md)で定義された有効な [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-105">A variable reference must be a valid [!INCLUDE[esql](../../../../../../includes/esql-md.md)] identifier, as defined in [Identifiers](identifiers-entity-sql.md).</span></span>  
  
 <span data-ttu-id="c6ae7-106">次の例は、式における変数の使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-106">The following example shows the use of a variable in the expression.</span></span> <span data-ttu-id="c6ae7-107">FROM 句の `c` は変数の定義です。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-107">The `c` in the FROM clause is the definition of the variable.</span></span> <span data-ttu-id="c6ae7-108">SELECT 句内で使用された `c` は、変数参照を表します。</span><span class="sxs-lookup"><span data-stu-id="c6ae7-108">The use of `c` in the SELECT clause represents the variable reference.</span></span>  
  
```sql  
select c
from LOB.customers as c  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6ae7-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="c6ae7-109">See also</span></span>

- [<span data-ttu-id="c6ae7-110">識別子</span><span class="sxs-lookup"><span data-stu-id="c6ae7-110">Identifiers</span></span>](identifiers-entity-sql.md)
- [<span data-ttu-id="c6ae7-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c6ae7-111">Parameters</span></span>](parameters-entity-sql.md)
- [<span data-ttu-id="c6ae7-112">Entity SQL の概要</span><span class="sxs-lookup"><span data-stu-id="c6ae7-112">Entity SQL Overview</span></span>](entity-sql-overview.md)
