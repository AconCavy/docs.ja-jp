---
title: データの並べ替え (C#)
ms.date: 07/20/2015
ms.assetid: d93fa055-2f19-46d2-9898-e2aed628f1c9
ms.openlocfilehash: 78b263c384895b736b11cc524befa42b4a896380
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418189"
---
# <a name="sorting-data-c"></a><span data-ttu-id="6a9b0-102">データの並べ替え (C#)</span><span class="sxs-lookup"><span data-stu-id="6a9b0-102">Sorting Data (C#)</span></span>
<span data-ttu-id="6a9b0-103">並べ替え操作では、1 つ以上の属性に基づいてシーケンスの要素を並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-103">A sorting operation orders the elements of a sequence based on one or more attributes.</span></span> <span data-ttu-id="6a9b0-104">並べ替えの第 1 条件で、要素に対して一回目の並べ替えが実行されます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-104">The first sort criterion performs a primary sort on the elements.</span></span> <span data-ttu-id="6a9b0-105">第 2 条件を指定すると、第 1 条件で並べ替えられた各グループ内の要素を並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-105">By specifying a second sort criterion, you can sort the elements within each primary sort group.</span></span>  
  
 <span data-ttu-id="6a9b0-106">次の図は、文字のシーケンスに対してアルファベット順の並べ替え操作を実行した結果を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-106">The following illustration shows the results of an alphabetical sort operation on a sequence of characters:</span></span> 
  
 ![アルファベット順の並べ替え操作を示している図。](./media/sorting-data/alphabetical-sort-operation.png)  
  
 <span data-ttu-id="6a9b0-108">次のセクションでは、データの並べ替えを実行する標準クエリ演算子のメソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-108">The standard query operator methods that sort data are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a9b0-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="6a9b0-109">Methods</span></span>  
  
|<span data-ttu-id="6a9b0-110">メソッド名</span><span class="sxs-lookup"><span data-stu-id="6a9b0-110">Method Name</span></span>|<span data-ttu-id="6a9b0-111">説明</span><span class="sxs-lookup"><span data-stu-id="6a9b0-111">Description</span></span>|<span data-ttu-id="6a9b0-112">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="6a9b0-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="6a9b0-113">説明</span><span class="sxs-lookup"><span data-stu-id="6a9b0-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="6a9b0-114">OrderBy</span><span class="sxs-lookup"><span data-stu-id="6a9b0-114">OrderBy</span></span>|<span data-ttu-id="6a9b0-115">値を昇順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-115">Sorts values in ascending order.</span></span>|`orderby`|<xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6a9b0-116">OrderByDescending</span><span class="sxs-lookup"><span data-stu-id="6a9b0-116">OrderByDescending</span></span>|<span data-ttu-id="6a9b0-117">値を降順に並べ替えます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-117">Sorts values in descending order.</span></span>|`orderby … descending`|<xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OrderByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6a9b0-118">ThenBy</span><span class="sxs-lookup"><span data-stu-id="6a9b0-118">ThenBy</span></span>|<span data-ttu-id="6a9b0-119">2 番目の並べ替えを昇順で実行します。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-119">Performs a secondary sort in ascending order.</span></span>|`orderby …, …`|<xref:System.Linq.Enumerable.ThenBy%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenBy%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6a9b0-120">ThenByDescending</span><span class="sxs-lookup"><span data-stu-id="6a9b0-120">ThenByDescending</span></span>|<span data-ttu-id="6a9b0-121">2 番目の並べ替えを降順で実行します。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-121">Performs a secondary sort in descending order.</span></span>|`orderby …, … descending`|<xref:System.Linq.Enumerable.ThenByDescending%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.ThenByDescending%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="6a9b0-122">Reverse</span><span class="sxs-lookup"><span data-stu-id="6a9b0-122">Reverse</span></span>|<span data-ttu-id="6a9b0-123">コレクションの要素の順序を反転させます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-123">Reverses the order of the elements in a collection.</span></span>|<span data-ttu-id="6a9b0-124">該当なし。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Reverse%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Reverse%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="6a9b0-125">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="6a9b0-125">Query Expression Syntax Examples</span></span>  
  
### <a name="primary-sort-examples"></a><span data-ttu-id="6a9b0-126">1 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="6a9b0-126">Primary Sort Examples</span></span>  
  
#### <a name="primary-ascending-sort"></a><span data-ttu-id="6a9b0-127">1 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="6a9b0-127">Primary Ascending Sort</span></span>  
 <span data-ttu-id="6a9b0-128">次の例は、LINQ クエリで `orderby` 句を使用して、配列内の文字列を文字列長に従って昇順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-128">The following example demonstrates how to use the `orderby` clause in a LINQ query to sort the strings in an array by string length, in ascending order.</span></span>  
  
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
  
#### <a name="primary-descending-sort"></a><span data-ttu-id="6a9b0-129">1 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="6a9b0-129">Primary Descending Sort</span></span>  
 <span data-ttu-id="6a9b0-130">次の例は、LINQ クエリで `orderby descending` 句を使用して、文字列を最初の文字に従って降順に並べ替える方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-130">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to sort the strings by their first letter, in descending order.</span></span>  
  
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
  
### <a name="secondary-sort-examples"></a><span data-ttu-id="6a9b0-131">2 番目の並べ替えの例</span><span class="sxs-lookup"><span data-stu-id="6a9b0-131">Secondary Sort Examples</span></span>  
  
#### <a name="secondary-ascending-sort"></a><span data-ttu-id="6a9b0-132">2 番目の並べ替え (昇順)</span><span class="sxs-lookup"><span data-stu-id="6a9b0-132">Secondary Ascending Sort</span></span>  
 <span data-ttu-id="6a9b0-133">次の例は、LINQ クエリで `orderby` 句を使用して、配列内の文字列に対して 1 番目および 2 番目の並べ替えを実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-133">The following example demonstrates how to use the `orderby` clause in a LINQ query to perform a primary and secondary sort of the strings in an array.</span></span> <span data-ttu-id="6a9b0-134">文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として、どちらも昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-134">The strings are sorted primarily by length and secondarily by the first letter of the string, both in ascending order.</span></span>  
  
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
  
#### <a name="secondary-descending-sort"></a><span data-ttu-id="6a9b0-135">2 番目の並べ替え (降順)</span><span class="sxs-lookup"><span data-stu-id="6a9b0-135">Secondary Descending Sort</span></span>  
 <span data-ttu-id="6a9b0-136">次の例は、LINQ クエリで `orderby descending` 句を使用して、1 番目の並べ替えを昇順で実行し、2 番目の並べ替えを降順で実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-136">The next example demonstrates how to use the `orderby descending` clause in a LINQ query to perform a primary sort, in ascending order, and a secondary sort, in descending order.</span></span> <span data-ttu-id="6a9b0-137">各文字列は、最初に文字列長を基準として、次に文字列の最初の文字を基準として並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="6a9b0-137">The strings are sorted primarily by length and secondarily by the first letter of the string.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6a9b0-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="6a9b0-138">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="6a9b0-139">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="6a9b0-139">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="6a9b0-140">orderby 句</span><span class="sxs-lookup"><span data-stu-id="6a9b0-140">orderby clause</span></span>](../../../language-reference/keywords/orderby-clause.md)
- [<span data-ttu-id="6a9b0-141">方法: Join 句の結果の順序指定</span><span class="sxs-lookup"><span data-stu-id="6a9b0-141">How to: Order the Results of a Join Clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="6a9b0-142">方法: 任意の単語またはフィールドを基準にテキスト データの並べ替えまたはフィルター処理を実行する (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="6a9b0-142">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (C#)</span></span>](./how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
