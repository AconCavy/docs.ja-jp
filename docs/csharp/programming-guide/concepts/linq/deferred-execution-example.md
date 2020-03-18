---
title: 遅延実行の例 (C#)
ms.date: 07/20/2015
ms.assetid: 50f4fbac-81fe-4f26-aedf-506e21419b19
ms.openlocfilehash: 0816594ad016f19af4c97198160b4bafb9b4b8b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204134"
---
# <a name="deferred-execution-example-c"></a><span data-ttu-id="99e2a-102">遅延実行の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="99e2a-102">Deferred Execution Example (C#)</span></span>
<span data-ttu-id="99e2a-103">このトピックでは、遅延実行とレイジー評価が LINQ to XML クエリの実行にどのように影響するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="99e2a-103">This topic shows how deferred execution and lazy evaluation affect the execution of your LINQ to XML queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99e2a-104">例</span><span class="sxs-lookup"><span data-stu-id="99e2a-104">Example</span></span>  
 <span data-ttu-id="99e2a-105">遅延実行を利用する拡張メソッドの使用時における実行順序の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="99e2a-105">The following example shows the order of execution when using an extension method that uses deferred execution.</span></span> <span data-ttu-id="99e2a-106">この例では、3 つの文字列の配列を宣言します。</span><span class="sxs-lookup"><span data-stu-id="99e2a-106">The example declares an array of three strings.</span></span> <span data-ttu-id="99e2a-107">次に、`ConvertCollectionToUpperCase` によって返されるコレクションを反復処理します。</span><span class="sxs-lookup"><span data-stu-id="99e2a-107">It then iterates through the collection returned by `ConvertCollectionToUpperCase`.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static IEnumerable<string>  
      ConvertCollectionToUpperCase(this IEnumerable<string> source)  
    {  
        foreach (string str in source)  
        {  
            Console.WriteLine("ToUpper: source {0}", str);  
            yield return str.ToUpper();  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        string[] stringArray = { "abc", "def", "ghi" };  
  
        var q = from str in stringArray.ConvertCollectionToUpperCase()  
                select str;  
  
        foreach (string str in q)  
            Console.WriteLine("Main: str {0}", str);  
    }  
}  
```  
  
 <span data-ttu-id="99e2a-108">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="99e2a-108">This example produces the following output:</span></span>  
  
```output  
ToUpper: source abc  
Main: str ABC  
ToUpper: source def  
Main: str DEF  
ToUpper: source ghi  
Main: str GHI  
```  
  
 <span data-ttu-id="99e2a-109">`ConvertCollectionToUpperCase` によって返されるコレクションの反復処理時、各アイテムはソース文字列の配列から取得され、次のアイテムがソース文字列の配列から取得される前に大文字に変換されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="99e2a-109">Notice that when iterating through the collection returned by `ConvertCollectionToUpperCase`, each item is retrieved from the source string array and converted to uppercase before the next item is retrieved from the source string array.</span></span>  
  
 <span data-ttu-id="99e2a-110">返されるコレクションの各アイテムが `foreach` の `Main` ループで処理されるまで、文字列の配列全体は大文字に変換されないことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="99e2a-110">You can see that the entire array of strings is not converted to uppercase before each item in the returned collection is processed in the `foreach` loop in `Main`.</span></span>  
  
 <span data-ttu-id="99e2a-111">このチュートリアルの次のトピックでは、クエリの連結について説明します。</span><span class="sxs-lookup"><span data-stu-id="99e2a-111">The next topic in this tutorial illustrates chaining queries together:</span></span>  
  
- [<span data-ttu-id="99e2a-112">クエリの連結の例 (C#)</span><span class="sxs-lookup"><span data-stu-id="99e2a-112">Chaining Queries Example (C#)</span></span>](./chaining-queries-example.md)  
  
## <a name="see-also"></a><span data-ttu-id="99e2a-113">参照</span><span class="sxs-lookup"><span data-stu-id="99e2a-113">See also</span></span>

- [<span data-ttu-id="99e2a-114">チュートリアル: クエリの連結 (C#)</span><span class="sxs-lookup"><span data-stu-id="99e2a-114">Tutorial: Chaining Queries Together (C#)</span></span>](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
