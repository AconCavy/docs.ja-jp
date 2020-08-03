---
title: クエリの連結の例 (C#)
description: この例では、2 つのクエリ (どちらのクエリも C# で遅延実行とレイジー評価を使用している) を連結した場合の結果について説明します。
ms.date: 07/20/2015
ms.assetid: abbca162-d95e-43af-b92c-e46e6aa2540e
ms.openlocfilehash: 0cfcfe1c8f537778fd1ef909277d95d83991af51
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105546"
---
# <a name="chaining-queries-example-c"></a><span data-ttu-id="d3120-103">クエリの連結の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="d3120-103">Chaining Queries Example (C#)</span></span>
<span data-ttu-id="d3120-104">この例は前の例に基づいており、2 つのクエリ (どちらのクエリも遅延実行とレイジー評価を使用している) を連結した場合の結果について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3120-104">This example builds on the previous example and shows what happens when you chain together two queries that both use deferred execution and lazy evaluation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3120-105">例</span><span class="sxs-lookup"><span data-stu-id="d3120-105">Example</span></span>  
 <span data-ttu-id="d3120-106">この例では、拡張メソッドをもう 1 つ導入します。この `AppendString` という拡張メソッドは、指定された文字列をソース コレクションのすべての文字列に追加して新しい文字列を生成します。</span><span class="sxs-lookup"><span data-stu-id="d3120-106">In this example, another extension method is introduced, `AppendString`, which appends a specified string onto every string in the source collection, and then yields the new strings.</span></span>  
  
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
  
 <span data-ttu-id="d3120-107">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="d3120-107">This example produces the following output:</span></span>  
  
```output  
ToUpper: source >abc<  
AppendString: source >ABC<  
Main: str >ABC!!!<  
  
ToUpper: source >def<  
AppendString: source >DEF<  
Main: str >DEF!!!<  
  
ToUpper: source >ghi<  
AppendString: source >GHI<  
Main: str >GHI!!!<  
```  
  
 <span data-ttu-id="d3120-108">この例では、各拡張メソッドがソース コレクションのアイテムごとに 1 つずつ実行されることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="d3120-108">In this example, you can see that each extension method operates one at a time for each item in the source collection.</span></span>  
  
 <span data-ttu-id="d3120-109">この例からわかることは、コレクションを生成するクエリを連結しても中間コレクションは具体化されないということです。</span><span class="sxs-lookup"><span data-stu-id="d3120-109">What should be clear from this example is that even though we have chained together queries that yield collections, no intermediate collections are materialized.</span></span> <span data-ttu-id="d3120-110">代わりに、各アイテムが一方のレイジー メソッドから次のメソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d3120-110">Instead, each item is passed from one lazy method to the next.</span></span> <span data-ttu-id="d3120-111">この場合のメモリ使用量は、まず文字列の 1 つの配列を取得し、次に大文字に変換した文字列の 2 つ目の配列を作成し、最後に各文字列に感嘆符を追加した文字列の 3 つ目の配列を作成する方法と比べると、はるかに少なくなります。</span><span class="sxs-lookup"><span data-stu-id="d3120-111">This results in a much smaller memory footprint than an approach that would first take one array of strings, then create a second array of strings that have been converted to uppercase, and finally create a third array of strings where each string has the exclamation points appended to it.</span></span>  
  
 <span data-ttu-id="d3120-112">このチュートリアルの次のトピックでは、中間結果の具体化について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3120-112">The next topic in this tutorial illustrates intermediate materialization:</span></span>  
  
- [<span data-ttu-id="d3120-113">中間結果の具体化 (C#)</span><span class="sxs-lookup"><span data-stu-id="d3120-113">Intermediate Materialization (C#)</span></span>](./intermediate-materialization.md)  
  
## <a name="see-also"></a><span data-ttu-id="d3120-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3120-114">See also</span></span>

- [<span data-ttu-id="d3120-115">チュートリアル: クエリの連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="d3120-115">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
