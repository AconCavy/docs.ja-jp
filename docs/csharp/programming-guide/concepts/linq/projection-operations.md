---
title: 射影操作 (C#)
description: 射影操作について説明します。 これらの操作では、オブジェクトが新しい形式に変換されます。多くの場合、それは後ほど使用するプロパティのみで構成されます。
ms.date: 07/20/2015
ms.assetid: 98df573a-aad9-4b8c-9a71-844be2c4fb41
ms.openlocfilehash: 6128b1bb2e7ba3dbb1b428d475acc307ba931013
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186004"
---
# <a name="projection-operations-c"></a><span data-ttu-id="d045c-104">射影操作 (C#)</span><span class="sxs-lookup"><span data-stu-id="d045c-104">Projection Operations (C#)</span></span>

<span data-ttu-id="d045c-105">射影とは、オブジェクトを、必要なプロパティだけで構成された別の形式に変換する操作のことをいいます。</span><span class="sxs-lookup"><span data-stu-id="d045c-105">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="d045c-106">射影を使用することにより、個々のオブジェクトから構築された新しい型を作成できます。</span><span class="sxs-lookup"><span data-stu-id="d045c-106">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="d045c-107">プロパティを投影し、それに対して数値演算関数を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d045c-107">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="d045c-108">また、元のオブジェクトを変更せずに射影することもできます。</span><span class="sxs-lookup"><span data-stu-id="d045c-108">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="d045c-109">次のセクションでは、射影を実行する標準クエリ演算子メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="d045c-109">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d045c-110">メソッド</span><span class="sxs-lookup"><span data-stu-id="d045c-110">Methods</span></span>  
  
|<span data-ttu-id="d045c-111">メソッド名</span><span class="sxs-lookup"><span data-stu-id="d045c-111">Method Name</span></span>|<span data-ttu-id="d045c-112">説明</span><span class="sxs-lookup"><span data-stu-id="d045c-112">Description</span></span>|<span data-ttu-id="d045c-113">C# のクエリ式の構文</span><span class="sxs-lookup"><span data-stu-id="d045c-113">C# Query Expression Syntax</span></span>|<span data-ttu-id="d045c-114">説明</span><span class="sxs-lookup"><span data-stu-id="d045c-114">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="d045c-115">選択</span><span class="sxs-lookup"><span data-stu-id="d045c-115">Select</span></span>|<span data-ttu-id="d045c-116">変換関数に基づいて値を射影します。</span><span class="sxs-lookup"><span data-stu-id="d045c-116">Projects values that are based on a transform function.</span></span>|`select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="d045c-117">SelectMany</span><span class="sxs-lookup"><span data-stu-id="d045c-117">SelectMany</span></span>|<span data-ttu-id="d045c-118">変換関数に基づいて値のシーケンスを射影し、それを 1 つのシーケンスに平坦化します。</span><span class="sxs-lookup"><span data-stu-id="d045c-118">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="d045c-119">複数の `from` 句を使用</span><span class="sxs-lookup"><span data-stu-id="d045c-119">Use multiple `from` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="d045c-120">クエリ式の構文例</span><span class="sxs-lookup"><span data-stu-id="d045c-120">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="d045c-121">選択</span><span class="sxs-lookup"><span data-stu-id="d045c-121">Select</span></span>  

 <span data-ttu-id="d045c-122">次の例では、`select` 句を使って、文字列リストにある各文字列の最初の文字を射影します。</span><span class="sxs-lookup"><span data-stu-id="d045c-122">The following example uses the `select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```csharp  
List<string> words = new List<string>() { "an", "apple", "a", "day" };  
  
var query = from word in words  
            select word.Substring(0, 1);  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    a  
    a  
    a  
    d  
*/  
```  
  
### <a name="selectmany"></a><span data-ttu-id="d045c-123">SelectMany</span><span class="sxs-lookup"><span data-stu-id="d045c-123">SelectMany</span></span>  

 <span data-ttu-id="d045c-124">次の例では、`from` 句を複数使用して、文字列リストにある各文字列の各単語を射影します。</span><span class="sxs-lookup"><span data-stu-id="d045c-124">The following example uses multiple `from` clauses  to project each word from each string in a list of strings.</span></span>  
  
```csharp  
List<string> phrases = new List<string>() { "an apple a day", "the quick brown fox" };  
  
var query = from phrase in phrases  
            from word in phrase.Split(' ')  
            select word;  
  
foreach (string s in query)  
    Console.WriteLine(s);  
  
/* This code produces the following output:  
  
    an  
    apple  
    a  
    day  
    the  
    quick  
    brown  
    fox  
*/  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="d045c-125">Select と SelectMany の比較</span><span class="sxs-lookup"><span data-stu-id="d045c-125">Select versus SelectMany</span></span>  

 <span data-ttu-id="d045c-126">`Select()` と `SelectMany()` の機能はどちらも、ソース値から結果値 (複数も可) を生成することです。</span><span class="sxs-lookup"><span data-stu-id="d045c-126">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="d045c-127">`Select()` は、ソース値ごとに結果値を 1 つ生成します。</span><span class="sxs-lookup"><span data-stu-id="d045c-127">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="d045c-128">そのため、結果全体は、ソース コレクションと同じ数の要素を持つ 1 つのコレクションになります。</span><span class="sxs-lookup"><span data-stu-id="d045c-128">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="d045c-129">これに対し、`SelectMany()` は、各ソース値から、連結されたサブコレクションを含む 1 つの総合的な結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="d045c-129">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="d045c-130">`SelectMany()` に引数として渡される変換関数は、ソース値ごとに列挙可能な値のシーケンスを返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d045c-130">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="d045c-131">この列挙可能なシーケンスは `SelectMany()` によって連結されて、1 つの大きなシーケンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="d045c-131">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="d045c-132">これら 2 つのメソッドのアクションの概念的な違いを次の 2 つの図に示します。</span><span class="sxs-lookup"><span data-stu-id="d045c-132">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="d045c-133">どちらも、セレクター (変換) 関数が各ソース値から花の配列を選択することを想定しています。</span><span class="sxs-lookup"><span data-stu-id="d045c-133">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="d045c-134">次の図は、`Select()` がソース コレクションと同じ数の要素を持つコレクションを返すしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="d045c-134">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Select&#40;&#41; のアクションを示すグラフィック。](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="d045c-136">次の図は、`SelectMany()` が中間配列シーケンスを、各中間配列の値を含む最終的な結果値に連結するしくみを示しています。</span><span class="sxs-lookup"><span data-stu-id="d045c-136">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![SelectMany&#40;&#41; のアクションを示すグラフィック。](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="d045c-138">コード例</span><span class="sxs-lookup"><span data-stu-id="d045c-138">Code Example</span></span>  

 <span data-ttu-id="d045c-139">次の例は、`Select()` と `SelectMany()` の動作を比較しています。</span><span class="sxs-lookup"><span data-stu-id="d045c-139">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="d045c-140">コードは、ソース コレクションの花の名前の各リストから最初の 2 つの項目を取って "花束" を作成します。</span><span class="sxs-lookup"><span data-stu-id="d045c-140">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="d045c-141">この例では、変換関数 <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> が使用する "単一の値" 自体が値のコレクションになっています。</span><span class="sxs-lookup"><span data-stu-id="d045c-141">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="d045c-142">各サブ シーケンスで各文字列を列挙するために追加の `foreach` ループを使用しています。</span><span class="sxs-lookup"><span data-stu-id="d045c-142">This requires the extra `foreach` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```csharp  
class Bouquet  
{  
    public List<string> Flowers { get; set; }  
}  
  
static void SelectVsSelectMany()  
{  
    List<Bouquet> bouquets = new List<Bouquet>() {  
        new Bouquet { Flowers = new List<string> { "sunflower", "daisy", "daffodil", "larkspur" }},  
        new Bouquet{ Flowers = new List<string> { "tulip", "rose", "orchid" }},  
        new Bouquet{ Flowers = new List<string> { "gladiolis", "lily", "snapdragon", "aster", "protea" }},  
        new Bouquet{ Flowers = new List<string> { "larkspur", "lilac", "iris", "dahlia" }}  
    };  
  
    // *********** Select ***********
    IEnumerable<List<string>> query1 = bouquets.Select(bq => bq.Flowers);  
  
    // ********* SelectMany *********  
    IEnumerable<string> query2 = bouquets.SelectMany(bq => bq.Flowers);  
  
    Console.WriteLine("Results by using Select():");  
    // Note the extra foreach loop here.  
    foreach (IEnumerable<String> collection in query1)  
        foreach (string item in collection)  
            Console.WriteLine(item);  
  
    Console.WriteLine("\nResults by using SelectMany():");  
    foreach (string item in query2)  
        Console.WriteLine(item);  
  
    /* This code produces the following output:  
  
       Results by using Select():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
  
       Results by using SelectMany():  
        sunflower  
        daisy  
        daffodil  
        larkspur  
        tulip  
        rose  
        orchid  
        gladiolis  
        lily  
        snapdragon  
        aster  
        protea  
        larkspur  
        lilac  
        iris  
        dahlia  
    */  
  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d045c-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="d045c-143">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="d045c-144">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="d045c-144">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="d045c-145">select 句</span><span class="sxs-lookup"><span data-stu-id="d045c-145">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
- [<span data-ttu-id="d045c-146">複数のソースからオブジェクト コレクションにデータを設定する方法 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d045c-146">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="d045c-147">グループを使用して 1 つのファイルを複数のファイルに分割する方法 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="d045c-147">How to split a file into many files by using groups (LINQ) (C#)</span></span>](./how-to-split-a-file-into-many-files-by-using-groups-linq.md)
