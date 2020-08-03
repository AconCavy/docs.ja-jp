---
title: 標準クエリ演算子の連結 (C#)
description: この例では、C# で標準クエリ演算子を連結する方法を示します。 このクエリによって中間結果が具体化されることはありません。
ms.date: 07/20/2015
ms.assetid: 66f2b0a9-2c23-4735-988e-bbc9dfb55c7b
ms.openlocfilehash: 41a7e4c7910c783d07181fe16254b0cac6902794
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104065"
---
# <a name="chaining-standard-query-operators-together-c"></a><span data-ttu-id="69a95-104">標準クエリ演算子の連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="69a95-104">Chaining Standard Query Operators Together (C#)</span></span>
<span data-ttu-id="69a95-105">これは、「[チュートリアル:クエリの連結 (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)」の最後のトピックです。</span><span class="sxs-lookup"><span data-stu-id="69a95-105">This is the final topic in the [Tutorial: Chaining Queries Together (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md) tutorial.</span></span>  
  
 <span data-ttu-id="69a95-106">標準クエリ演算子も連結することができます。</span><span class="sxs-lookup"><span data-stu-id="69a95-106">The standard query operators can also be chained together.</span></span> <span data-ttu-id="69a95-107">たとえば、<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> 演算子を挿入することができます。また、この演算子はレイジー方式でも機能します。</span><span class="sxs-lookup"><span data-stu-id="69a95-107">For example, you can interject the <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> operator, and it also operates in a lazy fashion.</span></span> <span data-ttu-id="69a95-108">この演算子によって中間結果が具体化されることはありません。</span><span class="sxs-lookup"><span data-stu-id="69a95-108">No intermediate results are materialized by it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="69a95-109">例</span><span class="sxs-lookup"><span data-stu-id="69a95-109">Example</span></span>  
 <span data-ttu-id="69a95-110">この例では、<xref:System.Linq.Enumerable.Where%2A> の前に `ConvertCollectionToUpperCase` メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="69a95-110">In this example, the <xref:System.Linq.Enumerable.Where%2A> method is called before calling `ConvertCollectionToUpperCase`.</span></span> <span data-ttu-id="69a95-111"><xref:System.Linq.Enumerable.Where%2A> メソッドは、このチュートリアルの前の例で使用したレイジー メソッド (`ConvertCollectionToUpperCase` および `AppendString`) とほぼ同様に動作しますが、この例では異なる点もあります。</span><span class="sxs-lookup"><span data-stu-id="69a95-111">The <xref:System.Linq.Enumerable.Where%2A> method operates in almost exactly the same way as the lazy methods used in previous examples in this tutorial, `ConvertCollectionToUpperCase` and `AppendString`.</span></span>  
  
 <span data-ttu-id="69a95-112">異なる点とは、この場合の <xref:System.Linq.Enumerable.Where%2A> メソッドではソース コレクションを反復処理し、最初の項目を述語に渡さないことを決定してから、述語に渡す次の項目を取得します。</span><span class="sxs-lookup"><span data-stu-id="69a95-112">One difference is that in this case, the <xref:System.Linq.Enumerable.Where%2A> method iterates through its source collection, determines that the first item does not pass the predicate, and then gets the next item, which does pass.</span></span> <span data-ttu-id="69a95-113">その後、2 番目の項目を生成します。</span><span class="sxs-lookup"><span data-stu-id="69a95-113">It then yields the second item.</span></span>  
  
 <span data-ttu-id="69a95-114">ただし、基本的な考え方は同じです。つまり、中間コレクションは、必要がない限り具体化されません。</span><span class="sxs-lookup"><span data-stu-id="69a95-114">However, the basic idea is the same: Intermediate collections are not materialized unless they have to be.</span></span>  
  
 <span data-ttu-id="69a95-115">クエリ式が使用されている場合、そのクエリ式は標準クエリ演算子への呼び出しに変換され、同じ原則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="69a95-115">When query expressions are used, they are converted to calls to the standard query operators, and the same principles apply.</span></span>  
  
 <span data-ttu-id="69a95-116">Office Open XML ドキュメントに対してクエリを実行するこのセクションの例はすべて、同じ原則を使用します。</span><span class="sxs-lookup"><span data-stu-id="69a95-116">All of the examples in this section that are querying Office Open XML documents use the same principle.</span></span> <span data-ttu-id="69a95-117">遅延実行およびレイジー評価は、LINQ (および LINQ to XML) を効果的に使用するために理解しておく必要がある基本的概念です。</span><span class="sxs-lookup"><span data-stu-id="69a95-117">Deferred execution and lazy evaluation are some of the fundamental concepts that you must understand  to use LINQ (and LINQ to XML) effectively.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source >{0}<", str);  
            yield return str.ToUpper();  
        }  
    }  
  
    public static IEnumerable<string>  
      AppendString(this IEnumerable<string> source, string stringToAppend)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("AppendString: source >{0}<", str);  
            yield return str + stringToAppend;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        IEnumerable<string> q1 =  
            from s in stringArray.ConvertCollectionToUpperCase()  
            where s.CompareTo("D") >= 0  
            select s;  
  
        IEnumerable<string> q2 =  
            from s in q1.AppendString("!!!")  
            select s;  
  
        foreach (string str in q2)  
        {  
            Console.WriteLine("Main: str >{0}<", str);  
            Console.WriteLine();  
        }  
    }  
}  
```  
  
 <span data-ttu-id="69a95-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="69a95-118">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
