---
title: 文字列での単語の出現回数をカウントする方法 (LINQ) (C#)
description: この例では、C# で LINQ クエリを使用して、指定された単語が文字列内に出現する回数をカウントします。 Split メソッドを使用して単語の配列が作成されます。
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 1621e776510e366aa779f1d45468be34b3dec373
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103367"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a><span data-ttu-id="4ec41-104">文字列での単語の出現回数をカウントする方法 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="4ec41-104">How to count occurrences of a word in a string (LINQ) (C#)</span></span>
<span data-ttu-id="4ec41-105">この例では、LINQ クエリを使用して、指定された単語が文字列内に出現する回数をカウントする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4ec41-105">This example shows how to use a LINQ query to count the occurrences of a specified word in a string.</span></span> <span data-ttu-id="4ec41-106">カウントを実行するには、まず <xref:System.String.Split%2A> メソッドを呼び出して単語の配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="4ec41-106">Note that to perform the count, first the <xref:System.String.Split%2A> method is called to create an array of words.</span></span> <span data-ttu-id="4ec41-107"><xref:System.String.Split%2A> メソッドを呼び出すと、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="4ec41-107">There is a performance cost to the <xref:System.String.Split%2A> method.</span></span> <span data-ttu-id="4ec41-108">文字列に対する操作が単語のカウントのみである場合は、<xref:System.Text.RegularExpressions.Regex.Matches%2A> または <xref:System.String.IndexOf%2A> メソッドの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="4ec41-108">If the only operation on the string is to count the words, you should consider using the <xref:System.Text.RegularExpressions.Regex.Matches%2A> or <xref:System.String.IndexOf%2A> methods instead.</span></span> <span data-ttu-id="4ec41-109">ただし、パフォーマンスが重要でない場合や、他の種類のクエリを実行する目的で事前に文章を分割している場合は、LINQ を使用して単語や語句をカウントすることにも意味があります。</span><span class="sxs-lookup"><span data-stu-id="4ec41-109">However, if performance is not a critical issue, or you have already split the sentence in order to perform other types of queries over it, then it makes sense to use LINQ to count the words or phrases as well.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ec41-110">例</span><span class="sxs-lookup"><span data-stu-id="4ec41-110">Example</span></span>  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET Framework APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4ec41-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="4ec41-111">Compiling the Code</span></span>  
 <span data-ttu-id="4ec41-112">System.Linq 名前空間と System.IO 名前空間に `using` ディレクティブを使用して、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="4ec41-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec41-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ec41-113">See also</span></span>

- [<span data-ttu-id="4ec41-114">LINQ と文字列 (C#)</span><span class="sxs-lookup"><span data-stu-id="4ec41-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
