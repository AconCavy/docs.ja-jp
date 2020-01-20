---
title: ディレクトリ ツリーで重複するファイルを照会する方法 (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 1ff5562b-0d30-46d1-b426-a04e8f78c840
ms.openlocfilehash: 7c84dba3e87077077f28bc2e665ea3774cf44d3b
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347875"
---
# <a name="how-to-query-for-duplicate-files-in-a-directory-tree-linq-c"></a><span data-ttu-id="b9611-102">ディレクトリ ツリーで重複するファイルを照会する方法 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="b9611-102">How to query for duplicate files in a directory tree (LINQ) (C#)</span></span>
<span data-ttu-id="b9611-103">同じ名前のファイルが複数のフォルダーに存在することがあります。</span><span class="sxs-lookup"><span data-stu-id="b9611-103">Sometimes files that have the same name may be located in more than one folder.</span></span> <span data-ttu-id="b9611-104">たとえば、Visual Studio インストール フォルダーでは、複数のフォルダーに readme.htm ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b9611-104">For example, under the Visual Studio installation folder, several folders have a readme.htm file.</span></span> <span data-ttu-id="b9611-105">次の例は、指定したルート フォルダーの下で、このような重複したファイル名をクエリする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="b9611-105">This example shows how to query for such duplicate file names under a specified root folder.</span></span> <span data-ttu-id="b9611-106">また、2 番目の例では、名前のほかにサイズと LastWrite 時刻が一致するファイルをクエリする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b9611-106">The second example shows how to query for files whose size and LastWrite times also match.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9611-107">例</span><span class="sxs-lookup"><span data-stu-id="b9611-107">Example</span></span>  
  
```csharp  
class QueryDuplicateFileNames  
{  
    static void Main(string[] args)  
    {  
        // Uncomment QueryDuplicates2 to run that query.  
        QueryDuplicates();  
        // QueryDuplicates2();  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    static void QueryDuplicates()  
    {  
        // Change the root drive or folder if necessary  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\";  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // used in WriteLine to keep the lines shorter  
        int charsToSkip = startFolder.Length;  
  
        // var can be used for convenience with groups.  
        var queryDupNames =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by file.Name into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        // Pass the query to a method that will  
        // output one page at a time.  
        PageOutput<string, string>(queryDupNames);  
    }  
  
    // A Group key that can be passed to a separate method.  
    // Override Equals and GetHashCode to define equality for the key.  
    // Override ToString to provide a friendly name for Key.ToString()  
    class PortableKey  
    {  
        public string Name { get; set; }  
        public DateTime LastWriteTime { get; set; }  
        public long Length { get; set; }  
  
        public override bool Equals(object obj)  
        {  
            PortableKey other = (PortableKey)obj;  
            return other.LastWriteTime == this.LastWriteTime &&  
                   other.Length == this.Length &&  
                   other.Name == this.Name;  
        }  
  
        public override int GetHashCode()  
        {  
            string str = $"{this.LastWriteTime}{this.Length}{this.Name}";
            return str.GetHashCode();  
        }  
        public override string ToString()  
        {  
            return $"{this.Name} {this.Length} {this.LastWriteTime}";
        }  
    }  
    static void QueryDuplicates2()  
    {  
        // Change the root drive or folder if necessary.  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\Common7";  
  
        // Make the lines shorter for the console display  
        int charsToSkip = startFolder.Length;  
  
        // Take a snapshot of the file system.  
        System.IO.DirectoryInfo dir = new System.IO.DirectoryInfo(startFolder);  
        IEnumerable<System.IO.FileInfo> fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories);  
  
        // Note the use of a compound key. Files that match  
        // all three properties belong to the same group.  
        // A named type is used to enable the query to be  
        // passed to another method. Anonymous types can also be used  
        // for composite keys but cannot be passed across method boundaries  
        //   
        var queryDupFiles =  
            from file in fileList  
            group file.FullName.Substring(charsToSkip) by  
                new PortableKey { Name = file.Name, LastWriteTime = file.LastWriteTime, Length = file.Length } into fileGroup  
            where fileGroup.Count() > 1  
            select fileGroup;  
  
        var list = queryDupFiles.ToList();  
  
        int i = queryDupFiles.Count();  
  
        PageOutput<PortableKey, string>(queryDupFiles);  
    }  
  
    // A generic method to page the output of the QueryDuplications methods  
    // Here the type of the group must be specified explicitly. "var" cannot  
    // be used in method signatures. This method does not display more than one  
    // group per page.  
    private static void PageOutput<K, V>(IEnumerable<System.Linq.IGrouping<K, V>> groupByExtList)  
    {  
        // Flag to break out of paging loop.  
        bool goAgain = true;  
  
        // "3" = 1 line for extension + 1 for "Press any key" + 1 for input cursor.  
        int numLines = Console.WindowHeight - 3;  
  
        // Iterate through the outer collection of groups.  
        foreach (var filegroup in groupByExtList)  
        {  
            // Start a new extension at the top of a page.  
            int currentLine = 0;  
  
            // Output only as many lines of the current group as will fit in the window.  
            do  
            {  
                Console.Clear();  
                Console.WriteLine("Filename = {0}", filegroup.Key.ToString() == String.Empty ? "[none]" : filegroup.Key.ToString());  
  
                // Get 'numLines' number of items starting at number 'currentLine'.  
                var resultPage = filegroup.Skip(currentLine).Take(numLines);  
  
                //Execute the resultPage query  
                foreach (var fileName in resultPage)  
                {  
                    Console.WriteLine("\t{0}", fileName);  
                }  
  
                // Increment the line counter.  
                currentLine += numLines;  
  
                // Give the user a chance to escape.  
                Console.WriteLine("Press any key to continue or the 'End' key to break...");  
                ConsoleKey key = Console.ReadKey().Key;  
                if (key == ConsoleKey.End)  
                {  
                    goAgain = false;  
                    break;  
                }  
            } while (currentLine < filegroup.Count());  
  
            if (goAgain == false)  
                break;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="b9611-108">最初のクエリでは、単純なキーを使用して一致を判断します。これにより、同じ名前を持つファイルが検索されますが、この場合、各ファイルの内容が一致するとは限りません。</span><span class="sxs-lookup"><span data-stu-id="b9611-108">The first query uses a simple key to determine a match; this finds files that have the same name but whose contents might be different.</span></span> <span data-ttu-id="b9611-109">2 番目のクエリでは、複合キーを使用して、<xref:System.IO.FileInfo> オブジェクトの 3 つのプロパティと照合します。</span><span class="sxs-lookup"><span data-stu-id="b9611-109">The second query uses a compound key to match against three properties of the <xref:System.IO.FileInfo> object.</span></span> <span data-ttu-id="b9611-110">このクエリでは、名前が同じで、内容も類似または一致するファイルが検索される可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="b9611-110">This query is much more likely to find files that have the same name and similar or identical content.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9611-111">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b9611-111">Compiling the Code</span></span>  
 <span data-ttu-id="b9611-112">System.Linq 名前空間と System.IO 名前空間に `using` ディレクティブを使用して、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b9611-112">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9611-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9611-113">See also</span></span>

- [<span data-ttu-id="b9611-114">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="b9611-114">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="b9611-115">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="b9611-115">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
