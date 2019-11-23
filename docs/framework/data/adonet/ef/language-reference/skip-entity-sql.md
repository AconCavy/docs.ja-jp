---
title: SKIP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: e2139412-8ea4-451b-8f10-91af18dfa3ec
ms.openlocfilehash: 75140384823588b8f6785de00b0ab3cd17314a3f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319341"
---
# <a name="skip-entity-sql"></a><span data-ttu-id="a92aa-102">SKIP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="a92aa-102">SKIP (Entity SQL)</span></span>

<span data-ttu-id="a92aa-103">物理的なページングは、ORDER BY 句の SKIP サブ句を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="a92aa-103">You can perform physical paging by using the SKIP sub-clause in the ORDER BY clause.</span></span> <span data-ttu-id="a92aa-104">SKIP を ORDER BY 句と切り離して使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a92aa-104">SKIP cannot be used separately from the ORDER BY clause.</span></span>

## <a name="syntax"></a><span data-ttu-id="a92aa-105">構文</span><span class="sxs-lookup"><span data-stu-id="a92aa-105">Syntax</span></span>

```sql
[ SKIP n ]
```

## <a name="arguments"></a><span data-ttu-id="a92aa-106">引数</span><span class="sxs-lookup"><span data-stu-id="a92aa-106">Arguments</span></span>

`n` \
<span data-ttu-id="a92aa-107">スキップするアイテムの数。</span><span class="sxs-lookup"><span data-stu-id="a92aa-107">The number of items to skip.</span></span>

## <a name="remarks"></a><span data-ttu-id="a92aa-108">コメント</span><span class="sxs-lookup"><span data-stu-id="a92aa-108">Remarks</span></span>

<span data-ttu-id="a92aa-109">SKIP 式のサブ句が ORDER BY 句に存在する場合、結果は並べ替え順序に従って並べ替えられ、結果セットには SKIP 式の直後の行から始まる行が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a92aa-109">If a SKIP expression sub-clause is present in an ORDER BY clause, the results will be sorted according the sort specification and the result set will include rows starting from the next row immediately after the SKIP expression.</span></span> <span data-ttu-id="a92aa-110">たとえば、SKIP 5 は、先頭の 5 行をスキップし、6 行目以降を返します。</span><span class="sxs-lookup"><span data-stu-id="a92aa-110">For example, SKIP 5 will skip the first five rows and return from the sixth row forward.</span></span>

> [!NOTE]
> <span data-ttu-id="a92aa-111">TOP 修飾子と SKIP サブ句が同じクエリ式内に存在する場合、 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリは無効です。</span><span class="sxs-lookup"><span data-stu-id="a92aa-111">An [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query is invalid if both the TOP modifier and the SKIP sub-clause are present in the same query expression.</span></span> <span data-ttu-id="a92aa-112">TOP 式を LIMIT 式に変更してクエリを記述し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a92aa-112">The query should be rewritten by changing the TOP expression to the LIMIT expression.</span></span>

> [!NOTE]
> <span data-ttu-id="a92aa-113">SQL Server 2000 では、キー以外の列で ORDER BY と共に SKIP を使用すると、正しくない結果が返される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a92aa-113">In SQL Server 2000, using SKIP with ORDER BY on non-key columns might return incorrect results.</span></span> <span data-ttu-id="a92aa-114">キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="a92aa-114">More than the specified number of rows might be skipped if the non-key column has duplicate data in it.</span></span> <span data-ttu-id="a92aa-115">これは、SQL Server 2000 に対する SKIP の変換方法によるものです。</span><span class="sxs-lookup"><span data-stu-id="a92aa-115">This is due to how SKIP is translated for SQL Server 2000.</span></span> <span data-ttu-id="a92aa-116">たとえば、次のコードでは、 `E.NonKeyColumn` に重複値が存在する場合、5 行を超える行はスキップされます。</span><span class="sxs-lookup"><span data-stu-id="a92aa-116">For example, in the following code more than five rows might be skipped if `E.NonKeyColumn` has duplicate values:</span></span>
>
> ```sql
> SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L
> ```

<span data-ttu-id="a92aa-117">「[方法: クエリ結果](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))を表示する」の [!INCLUDE[esql](../../../../../../includes/esql-md.md)] クエリでは、ORDER BY 演算子を SKIP と共に使用して、SELECT ステートメントで返されるオブジェクトで使用される並べ替え順序を指定します。</span><span class="sxs-lookup"><span data-stu-id="a92aa-117">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query in [How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100)) uses the ORDER BY operator with SKIP to specify the sort order used on objects returned in a SELECT statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="a92aa-118">参照</span><span class="sxs-lookup"><span data-stu-id="a92aa-118">See also</span></span>

- [<span data-ttu-id="a92aa-119">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="a92aa-119">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="a92aa-120">[方法: クエリ結果をページに表示する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a92aa-120">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="a92aa-121">ページング</span><span class="sxs-lookup"><span data-stu-id="a92aa-121">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="a92aa-122">TOP</span><span class="sxs-lookup"><span data-stu-id="a92aa-122">TOP</span></span>](top-entity-sql.md)
