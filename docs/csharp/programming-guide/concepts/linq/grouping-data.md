---
title: データのグループ化 (C#)
ms.date: 07/20/2015
ms.assetid: e414e9e4-343a-4e6e-858f-4a30c5e64492
ms.openlocfilehash: e7f10b121a7a1c599d88731a806fe784eb1a7e66
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423419"
---
# <a name="grouping-data-c"></a><span data-ttu-id="187e1-102">データのグループ化 (C#)</span><span class="sxs-lookup"><span data-stu-id="187e1-102">Grouping Data (C#)</span></span>
<span data-ttu-id="187e1-103">グループ化とは、各グループの要素が共通の属性を持つようにデータをグループに分ける操作を指します。</span><span class="sxs-lookup"><span data-stu-id="187e1-103">Grouping refers to the operation of putting data into groups so that the elements in each group share a common attribute.</span></span>  
  
 <span data-ttu-id="187e1-104">次の図は、文字のシーケンスをグループ化した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="187e1-104">The following illustration shows the results of grouping a sequence of characters.</span></span> <span data-ttu-id="187e1-105">各グループのキーは文字です。</span><span class="sxs-lookup"><span data-stu-id="187e1-105">The key for each group is the character.</span></span>  
  
 ![LINQ グループ化操作を示す図。](./media/grouping-data/linq-group-operation.png)  
  
 <span data-ttu-id="187e1-107">次のセクションでは、データ要素をグループ化する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="187e1-107">The standard query operator methods that group data elements are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="187e1-108">メソッド</span><span class="sxs-lookup"><span data-stu-id="187e1-108">Methods</span></span>  
  
|<span data-ttu-id="187e1-109">メソッド名</span><span class="sxs-lookup"><span data-stu-id="187e1-109">Method Name</span></span>|<span data-ttu-id="187e1-110">説明</span><span class="sxs-lookup"><span data-stu-id="187e1-110">Description</span></span>|<span data-ttu-id="187e1-111">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="187e1-111">C# Query Expression Syntax</span></span>|<span data-ttu-id="187e1-112">説明</span><span class="sxs-lookup"><span data-stu-id="187e1-112">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="187e1-113">GroupBy</span><span class="sxs-lookup"><span data-stu-id="187e1-113">GroupBy</span></span>|<span data-ttu-id="187e1-114">共通の属性を共有する要素をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="187e1-114">Groups elements that share a common attribute.</span></span> <span data-ttu-id="187e1-115">各グループは <xref:System.Linq.IGrouping%602> オブジェクトによって表されます。</span><span class="sxs-lookup"><span data-stu-id="187e1-115">Each group is represented by an <xref:System.Linq.IGrouping%602> object.</span></span>|`group … by`<br /><br /> <span data-ttu-id="187e1-116">または</span><span class="sxs-lookup"><span data-stu-id="187e1-116">-or-</span></span><br /><br /> `group … by … into …`|<xref:System.Linq.Enumerable.GroupBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="187e1-117">ToLookup</span><span class="sxs-lookup"><span data-stu-id="187e1-117">ToLookup</span></span>|<span data-ttu-id="187e1-118">キー セレクター関数に基づいて、<xref:System.Linq.Lookup%602> (一対多の辞書) に要素を挿入します。</span><span class="sxs-lookup"><span data-stu-id="187e1-118">Inserts elements into a <xref:System.Linq.Lookup%602> (a one-to-many dictionary) based on a key selector function.</span></span>|<span data-ttu-id="187e1-119">該当なし。</span><span class="sxs-lookup"><span data-stu-id="187e1-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.ToLookup%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="187e1-120">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="187e1-120">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="187e1-121">次のコード例では、`group by` 句を使用して、偶数か奇数かによってリスト内の整数をグループ化します。</span><span class="sxs-lookup"><span data-stu-id="187e1-121">The following code example uses the `group by` clause to group integers in a list according to whether they are even or odd.</span></span>  
  
```csharp  
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };  
  
IEnumerable<IGrouping<int, int>> query = from number in numbers  
                                         group number by number % 2;  
  
foreach (var group in query)  
{  
    Console.WriteLine(group.Key == 0 ? "\nEven numbers:" : "\nOdd numbers:");  
    foreach (int i in group)  
        Console.WriteLine(i);  
}  
  
/* This code produces the following output:  
  
    Odd numbers:  
    35  
    3987  
    199  
    329  
  
    Even numbers:  
    44  
    200  
    84  
    4  
    446  
    208  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="187e1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="187e1-122">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="187e1-123">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="187e1-123">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="187e1-124">group 句</span><span class="sxs-lookup"><span data-stu-id="187e1-124">group clause</span></span>](../../../language-reference/keywords/group-clause.md)
- [<span data-ttu-id="187e1-125">方法: 入れ子になったグループの作成</span><span class="sxs-lookup"><span data-stu-id="187e1-125">How to: Create a Nested Group</span></span>](../../../linq/create-a-nested-group.md)
- [<span data-ttu-id="187e1-126">方法: 拡張子別にファイルをグループ化する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="187e1-126">How to: Group Files by Extension (LINQ) (C#)</span></span>](./how-to-group-files-by-extension-linq.md)
- [<span data-ttu-id="187e1-127">方法: クエリ結果のグループ化</span><span class="sxs-lookup"><span data-stu-id="187e1-127">How to: Group Query Results</span></span>](../../../linq/group-query-results.md)
- [<span data-ttu-id="187e1-128">方法: グループ化操作でのサブクエリの実行</span><span class="sxs-lookup"><span data-stu-id="187e1-128">How to: Perform a Subquery on a Grouping Operation</span></span>](../../../linq/perform-a-subquery-on-a-grouping-operation.md)
- [<span data-ttu-id="187e1-129">方法: グループを使用して 1 つのファイルを複数のファイルに分割する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="187e1-129">How to: Split a File Into Many Files by Using Groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
