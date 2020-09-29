---
title: LINQ クエリと正規表現を組み合わせる方法 (C#)
description: この例では、C# で Regex クラスを使用して正規表現を作成し、テキスト文字列内の一致を取得します。
ms.date: 07/20/2015
ms.assetid: 6b003b65-20a4-4ca2-929e-2ee3f215aecc
ms.openlocfilehash: e423261961c25c6aae62483d332ce053d7b6f963
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157500"
---
# <a name="how-to-combine-linq-queries-with-regular-expressions-c"></a><span data-ttu-id="2c277-103">LINQ クエリと正規表現を組み合わせる方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="2c277-103">How to combine LINQ queries with regular expressions (C#)</span></span>

<span data-ttu-id="2c277-104">この例では、<xref:System.Text.RegularExpressions.Regex> クラスを使用して正規表現を作成し、テキスト文字列内の複雑な一致を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2c277-104">This example shows how to use the <xref:System.Text.RegularExpressions.Regex> class to create a regular expression for more complex matching in text strings.</span></span> <span data-ttu-id="2c277-105">LINQ クエリを使用すると、正規表現で検索する必要のあるファイルだけをフィルターで抽出したり、結果の形式を指定したりするのが簡単になります。</span><span class="sxs-lookup"><span data-stu-id="2c277-105">The LINQ query makes it easy to filter on exactly the files that you want to search with the regular expression, and to shape the results.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c277-106">例</span><span class="sxs-lookup"><span data-stu-id="2c277-106">Example</span></span>  
  
```csharp  
class QueryWithRegEx  
{  
    public static void Main()  
    {  
        // Modify this path as necessary so that it accesses your version of Visual Studio.  
        string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio 14.0\";  
        // One of the following paths may be more appropriate on your computer.  
        //string startFolder = @"C:\Program Files (x86)\Microsoft Visual Studio\2017\";  
  
        // Take a snapshot of the file system.  
        IEnumerable<System.IO.FileInfo> fileList = GetFiles(startFolder);  
  
        // Create the regular expression to find all things "Visual".  
        System.Text.RegularExpressions.Regex searchTerm =  
            new System.Text.RegularExpressions.Regex(@"Visual (Basic|C#|C\+\+|Studio)");  
  
        // Search the contents of each .htm file.  
        // Remove the where clause to find even more matchedValues!  
        // This query produces a list of files where a match  
        // was found, and a list of the matchedValues in that file.  
        // Note: Explicit typing of "Match" in select clause.  
        // This is required because MatchCollection is not a
        // generic IEnumerable collection.  
        var queryMatchingFiles =  
            from file in fileList  
            where file.Extension == ".htm"  
            let fileText = System.IO.File.ReadAllText(file.FullName)  
            let matches = searchTerm.Matches(fileText)  
            where matches.Count > 0  
            select new  
            {  
                name = file.FullName,  
                matchedValues = from System.Text.RegularExpressions.Match match in matches  
                                select match.Value  
            };  
  
        // Execute the query.  
        Console.WriteLine("The term \"{0}\" was found in:", searchTerm.ToString());  
  
        foreach (var v in queryMatchingFiles)  
        {  
            // Trim the path a bit, then write
            // the file name in which a match was found.  
            string s = v.name.Substring(startFolder.Length - 1);  
            Console.WriteLine(s);  
  
            // For this file, write out all the matching strings  
            foreach (var v2 in v.matchedValues)  
            {  
                Console.WriteLine("  " + v2);  
            }  
        }  
  
        // Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
  
    // This method assumes that the application has discovery
    // permissions for all folders under the specified path.  
    static IEnumerable<System.IO.FileInfo> GetFiles(string path)  
    {  
        if (!System.IO.Directory.Exists(path))  
            throw new System.IO.DirectoryNotFoundException();  
  
        string[] fileNames = null;  
        List<System.IO.FileInfo> files = new List<System.IO.FileInfo>();  
  
        fileNames = System.IO.Directory.GetFiles(path, "*.*", System.IO.SearchOption.AllDirectories);  
        foreach (string name in fileNames)  
        {  
            files.Add(new System.IO.FileInfo(name));  
        }  
        return files;  
    }  
}  
```  
  
 <span data-ttu-id="2c277-107">`RegEx` 検索で返された <xref:System.Text.RegularExpressions.MatchCollection> オブジェクトのクエリを実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="2c277-107">Note that you can also query the <xref:System.Text.RegularExpressions.MatchCollection> object that is returned by a `RegEx` search.</span></span> <span data-ttu-id="2c277-108">この例では、一致した各文字列の値のみが結果として生成されています。</span><span class="sxs-lookup"><span data-stu-id="2c277-108">In this example only the value of each match is produced in the results.</span></span> <span data-ttu-id="2c277-109">しかし、LINQ を使用して、各種のフィルター処理、並べ替え、グループ化をそのコレクションに対して実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="2c277-109">However, it is also possible to use LINQ to perform all kinds of filtering, sorting, and grouping on that collection.</span></span> <span data-ttu-id="2c277-110"><xref:System.Text.RegularExpressions.MatchCollection> が非ジェネリック <xref:System.Collections.IEnumerable> コレクションなので、クエリで範囲変数の型を明示的に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2c277-110">Because <xref:System.Text.RegularExpressions.MatchCollection> is a non-generic <xref:System.Collections.IEnumerable> collection, you have to explicitly state the type of the range variable in the query.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2c277-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="2c277-111">Compiling the Code</span></span>  

 <span data-ttu-id="2c277-112">System.Linq 名前空間と System.IO 名前空間に `using` ディレクティブを使用して、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="2c277-112">Create a C# console application project with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c277-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c277-113">See also</span></span>

- [<span data-ttu-id="2c277-114">LINQ と文字列 (C#)</span><span class="sxs-lookup"><span data-stu-id="2c277-114">LINQ and Strings (C#)</span></span>](./linq-and-strings.md)
- [<span data-ttu-id="2c277-115">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="2c277-115">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
