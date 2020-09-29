---
title: 一連のフォルダーの合計バイト数を照会する方法 (LINQ) (C#)
description: C# で LINQ を使用して、指定したフォルダーとそのサブフォルダーに格納されている全ファイルの合計バイト数を確認する方法について説明します。
ms.date: 07/20/2015
ms.assetid: a01bd1d4-133c-4ca2-aa4e-e93e81d6076c
ms.openlocfilehash: 562fd32ad9e9040a5898322d840718f25b56e2cd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91159034"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-c"></a><span data-ttu-id="76453-103">一連のフォルダーの合計バイト数を照会する方法 (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="76453-103">How to query for the total number of bytes in a set of folders (LINQ) (C#)</span></span>

<span data-ttu-id="76453-104">この例では、指定したフォルダーとそのすべてのサブフォルダーに格納されている全ファイルの合計バイト数を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="76453-104">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="76453-105">例</span><span class="sxs-lookup"><span data-stu-id="76453-105">Example</span></span>  

 <span data-ttu-id="76453-106"><xref:System.Linq.Enumerable.Sum%2A> は、`select` 句で選択されたすべての項目の値を加算するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="76453-106">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="76453-107">このクエリに少し変更を加え、<xref:System.Linq.Enumerable.Sum%2A> の代わりに <xref:System.Linq.Enumerable.Min%2A> メソッドまたは <xref:System.Linq.Enumerable.Max%2A> メソッドを呼び出せば、指定したディレクトリ ツリーの最大ファイルまたは最小ファイルを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="76453-107">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```csharp  
class QuerySize  
{  
    public static void Main()  
    {  
        string startFolder = @"c:\program files\Microsoft Visual Studio 9.0\VC#";  
  
        // Take a snapshot of the file system.  
        // This method assumes that the application has discovery permissions  
        // for all folders under the specified path.  
        IEnumerable<string> fileList = System.IO.Directory.GetFiles(startFolder, "*.*", System.IO.SearchOption.AllDirectories);  
  
        var fileQuery = from file in fileList  
                        select GetFileLength(file);  
  
        // Cache the results to avoid multiple trips to the file system.  
        long[] fileLengths = fileQuery.ToArray();  
  
        // Return the size of the largest file  
        long largestFile = fileLengths.Max();  
  
        // Return the total number of bytes in all the files under the specified folder.  
        long totalBytes = fileLengths.Sum();  
  
        Console.WriteLine("There are {0} bytes in {1} files under {2}",  
            totalBytes, fileList.Count(), startFolder);  
        Console.WriteLine("The largest files is {0} bytes.", largestFile);  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit.");  
        Console.ReadKey();  
    }  
  
    // This method is used to swallow the possible exception  
    // that can be raised when accessing the System.IO.FileInfo.Length property.  
    static long GetFileLength(string filename)  
    {  
        long retval;  
        try  
        {  
            System.IO.FileInfo fi = new System.IO.FileInfo(filename);  
            retval = fi.Length;  
        }  
        catch (System.IO.FileNotFoundException)  
        {  
            // If a file is no longer present,  
            // just add zero bytes to the total.  
            retval = 0;  
        }  
        return retval;  
    }  
}  
```  
  
 <span data-ttu-id="76453-108">指定したディレクトリ ツリー内のバイト数をカウントするだけならば、LINQ クエリを作成せずに行う方が効率的です。LINQ クエリでは、データ ソースとしてリスト コレクションを作成する際のオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="76453-108">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="76453-109">LINQ を使ったアプローチは、クエリが複雑化するか、同じデータ ソースに対して複数のクエリを実行する必要があるときに利便性が増します。</span><span class="sxs-lookup"><span data-stu-id="76453-109">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="76453-110">このクエリは、ファイルの長さを取得するために別のメソッドを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="76453-110">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="76453-111">その理由は、`GetFiles` の呼び出しで <xref:System.IO.FileInfo> オブジェクトが作成された後に別のスレッドでファイルが削除された場合に発生する可能性のある例外を処理するためです。</span><span class="sxs-lookup"><span data-stu-id="76453-111">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="76453-112"><xref:System.IO.FileInfo> オブジェクトの作成後であっても、例外は発生する可能性があります。<xref:System.IO.FileInfo> オブジェクトは、<xref:System.IO.FileInfo.Length%2A> プロパティが最初にアクセスされたときに最新の長さに基づいてそのプロパティを更新しようと試みるためです。</span><span class="sxs-lookup"><span data-stu-id="76453-112">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="76453-113">この操作をクエリの外側の try-catch ブロックに置くことで、"副作用の原因となりうるような操作はクエリ内では行わない" という原則に従っているのです。</span><span class="sxs-lookup"><span data-stu-id="76453-113">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="76453-114">一般に、アプリケーションが不明な状態に陥ることのないよう、例外を処理する際には十分な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="76453-114">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="76453-115">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="76453-115">Compiling the Code</span></span>  

<span data-ttu-id="76453-116">System.Linq 名前空間と System.IO 名前空間に `using` ディレクティブを使用して、C# コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="76453-116">Create a C# console application project, with `using` directives for the System.Linq and System.IO namespaces.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="76453-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="76453-117">See also</span></span>

- [<span data-ttu-id="76453-118">LINQ to Objects (C#)</span><span class="sxs-lookup"><span data-stu-id="76453-118">LINQ to Objects (C#)</span></span>](./linq-to-objects.md)
- [<span data-ttu-id="76453-119">LINQ とファイル ディレクトリ (C#)</span><span class="sxs-lookup"><span data-stu-id="76453-119">LINQ and File Directories (C#)</span></span>](./linq-and-file-directories.md)
