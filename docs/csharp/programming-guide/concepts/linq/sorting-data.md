---
title: データの並べ替え (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 8db5ab2ead0e59b8d41d83704ff237d4493155c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346454"
---
# <a name="sorting-data-c"></a><span data-ttu-id="54410-102">データの並べ替え (C#)</span><span class="sxs-lookup"><span data-stu-id="54410-102">Sorting Data (C#)</span></span>
<span data-ttu-id="54410-103">並べ替え操作では、1 つ以上の属性に基づいてシーケンスの要素を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="54410-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="54410-104">並べ替えの第 1 条件で、要素に対して一回目の並べ替えが実行されます。</span><span class="sxs-lookup"><span data-stu-id="54410-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="54410-105">第 2 条件を指定すると、第 1 条件で並べ替えられた各グループ内の要素を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="54410-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="54410-106">次の図は、文字のシーケンスに対してアルファベット順の並べ替え操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="54410-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![アルファベット順の並べ替え操作を示している図。](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="54410-108">次のセクションでは、データの並べ替えを実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="54410-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54410-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="54410-109">Methods</span></span>  
  
|<span data-ttu-id="54410-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="54410-110">Method Name</span></span>|<span data-ttu-id="54410-111">説明</span><span class="sxs-lookup"><span data-stu-id="54410-111">Description</span></span>|<span data-ttu-id="54410-112">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="54410-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="54410-113">説明</span><span class="sxs-lookup"><span data-stu-id="54410-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="54410-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="54410-114">OrderBy</span></span>|<span data-ttu-id="54410-115">値を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="54410-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="54410-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="54410-116">OrderByDescending</span></span>|<span data-ttu-id="54410-117">値を降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="54410-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="54410-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="54410-118">ThenBy</span></span>|<span data-ttu-id="54410-119">2 番目の並べ替えを昇順で実行します。</span><span class="sxs-lookup"><span data-stu-id="54410-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="54410-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="54410-120">ThenByDescending</span></span>|<span data-ttu-id="54410-121">2 番目の並べ替えを降順で実行します。</span><span class="sxs-lookup"><span data-stu-id="54410-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="54410-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="54410-122">Reverse</span></span>|<span data-ttu-id="54410-123">コレクションの要素の順序を反転させます。</span><span class="sxs-lookup"><span data-stu-id="54410-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="54410-124">該当なし。</span><span class="sxs-lookup"><span data-stu-id="54410-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="54410-125">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="54410-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="54410-126">1 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="54410-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="54410-127">1 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="54410-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="54410-128">次の例は、LINQ クエリで `orderby` 句を使用して、配列内の文字列を文字列長に従って昇順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="54410-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    brown  
    jumps  
*/  
```  
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="54410-129">1 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="54410-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="54410-130">次の例は、LINQ クエリで `orderby descending` 句を使用して、文字列を最初の文字に従って降順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="54410-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    quick  
    jumps  
    fox  
    brown  
*/  
```  
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="54410-131">2 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="54410-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="54410-132">2 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="54410-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="54410-133">次の例は、LINQ クエリで `orderby` 句を使用して、配列内の文字列に対して 1 番目および 2 番目の並べ替えを実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="54410-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="54410-134">文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として、どちらも昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="54410-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1)  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    fox  
    the  
    brown  
    jumps  
    quick  
*/  
```  
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="54410-135">2 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="54410-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="54410-136">次の例は、LINQ クエリで `orderby descending` 句を使用して、1 番目の並べ替えを昇順で実行し、2 番目の並べ替えを降順で実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="54410-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="54410-137">各文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="54410-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
```csharp  
string[] words = { "the", "quick", "brown", "fox", "jumps" };  
  
IEnumerable<string> query = from word in words  
                            orderby word.Length, word.Substring(0, 1) descending  
                            select word;  
  
foreach (string str in query)  
    Console.WriteLine(str);  
  
/* This code produces the following output:  
  
    the  
    fox  
    quick  
    jumps  
    brown  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="54410-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="54410-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="54410-139">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="54410-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="54410-140">orderby 句</span><span class="sxs-lookup"><span data-stu-id="54410-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="54410-141">join 句の結果の順序指定</span><span class="sxs-lookup"><span data-stu-id="54410-141">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="54410-142">任意のワードまたはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する方法 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="54410-142">How to sort or filter text data by any word or field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
