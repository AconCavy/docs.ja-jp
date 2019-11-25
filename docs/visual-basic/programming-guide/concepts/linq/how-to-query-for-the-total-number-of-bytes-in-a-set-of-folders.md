---
title: '方法 : 一連のフォルダーの合計バイト数を問い合わせる (LINQ)'
ms.date: 07/20/2015
ms.assetid: bfe85ed2-44dc-4ef1-aac7-241622b80a69
ms.openlocfilehash: b926a3e0ed973f449718ca5883aeabc0bfcf7b91
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347642"
---
# <a name="how-to-query-for-the-total-number-of-bytes-in-a-set-of-folders-linq-visual-basic"></a><span data-ttu-id="81e38-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81e38-102">How to: Query for the Total Number of Bytes in a Set of Folders (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="81e38-103">この例では、指定したフォルダーとそのすべてのサブフォルダーに格納されている全ファイルの合計バイト数を取得する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="81e38-103">This example shows how to retrieve the total number of bytes used by all the files in a specified folder and all its subfolders.</span></span>  
  
## <a name="example"></a><span data-ttu-id="81e38-104">例</span><span class="sxs-lookup"><span data-stu-id="81e38-104">Example</span></span>  
 <span data-ttu-id="81e38-105"><xref:System.Linq.Enumerable.Sum%2A> は、`select` 句で選択されたすべての項目の値を加算するメソッドです。</span><span class="sxs-lookup"><span data-stu-id="81e38-105">The <xref:System.Linq.Enumerable.Sum%2A> method adds the values of all the items selected in the `select` clause.</span></span> <span data-ttu-id="81e38-106">このクエリに少し変更を加え、<xref:System.Linq.Enumerable.Sum%2A> の代わりに <xref:System.Linq.Enumerable.Min%2A> メソッドまたは <xref:System.Linq.Enumerable.Max%2A> メソッドを呼び出せば、指定したディレクトリ ツリーの最大ファイルまたは最小ファイルを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="81e38-106">You can easily modify this query to retrieve the biggest or smallest file in the specified directory tree by calling the <xref:System.Linq.Enumerable.Min%2A> or <xref:System.Linq.Enumerable.Max%2A> method instead of <xref:System.Linq.Enumerable.Sum%2A>.</span></span>  
  
```vb  
Module QueryTotalBytes  
    Sub Main()  
  
        ' Change the drive\path if necessary.  
        Dim root As String = "C:\Program Files\Microsoft Visual Studio 9.0\VB"  
  
        'Take a snapshot of the folder contents.  
        ' This method assumes that the application has discovery permissions  
        ' for all folders under the specified path.  
        Dim fileList = My.Computer.FileSystem.GetFiles _  
                  (root, FileIO.SearchOption.SearchAllSubDirectories, "*.*")  
  
        Dim fileQuery = From file In fileList _  
                        Select GetFileLength(file)  
  
        ' Force execution and cache the results to avoid multiple trips to the file system.  
        Dim fileLengths = fileQuery.ToArray()  
  
        ' Find the largest file  
        Dim maxSize = Aggregate aFile In fileLengths Into Max()  
  
        ' Find the total number of bytes  
        Dim totalBytes = Aggregate aFile In fileLengths Into Sum()  
  
        Console.WriteLine("The largest file is " & maxSize & " bytes")  
        Console.WriteLine("There are " & totalBytes & " total bytes in " & _  
                          fileList.Count & " files under " & root)  
  
        ' Keep the console window open in debug mode  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
  
    ' This method is used to catch the possible exception  
    ' that can be raised when accessing the FileInfo.Length property.  
    Function GetFileLength(ByVal filename As String) As Long  
        Dim retval As Long  
        Try  
            Dim fi As New System.IO.FileInfo(filename)  
            retval = fi.Length  
        Catch ex As System.IO.FileNotFoundException  
            ' If a file is no longer present,  
            ' just return zero bytes.   
            retval = 0  
        End Try  
  
        Return retval  
    End Function  
End Module  
```  
  
 <span data-ttu-id="81e38-107">指定したディレクトリ ツリー内のバイト数をカウントするだけならば、LINQ クエリを作成せずに行う方が効率的です。LINQ クエリでは、データ ソースとしてリスト コレクションを作成する際のオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="81e38-107">If you only have to count the number of bytes in a specified directory tree, you can do this more efficiently without creating a LINQ query, which incurs the overhead of creating the list collection as a data source.</span></span> <span data-ttu-id="81e38-108">LINQ を使ったアプローチは、クエリが複雑化するか、同じデータ ソースに対して複数のクエリを実行する必要があるときに利便性が増します。</span><span class="sxs-lookup"><span data-stu-id="81e38-108">The usefulness of the LINQ approach increases as the query becomes more complex, or when you have to run multiple queries against the same data source.</span></span>  
  
 <span data-ttu-id="81e38-109">このクエリは、ファイルの長さを取得するために別のメソッドを呼び出しています。</span><span class="sxs-lookup"><span data-stu-id="81e38-109">The query calls out to a separate method to obtain the file length.</span></span> <span data-ttu-id="81e38-110">その理由は、`GetFiles` の呼び出しで <xref:System.IO.FileInfo> オブジェクトが作成された後に別のスレッドでファイルが削除された場合に発生する可能性のある例外を処理するためです。</span><span class="sxs-lookup"><span data-stu-id="81e38-110">It does this in order to consume the possible exception that will be raised if the file was deleted on another thread after the <xref:System.IO.FileInfo> object was created in the call to `GetFiles`.</span></span> <span data-ttu-id="81e38-111"><xref:System.IO.FileInfo> オブジェクトの作成後であっても、例外は発生する可能性があります。<xref:System.IO.FileInfo> オブジェクトは、<xref:System.IO.FileInfo.Length%2A> プロパティが最初にアクセスされたときに最新の長さに基づいてそのプロパティを更新しようと試みるためです。</span><span class="sxs-lookup"><span data-stu-id="81e38-111">Even though the <xref:System.IO.FileInfo> object has already been created, the exception can occur because a <xref:System.IO.FileInfo> object will try to refresh its <xref:System.IO.FileInfo.Length%2A> property with the most current length the first time the property is accessed.</span></span> <span data-ttu-id="81e38-112">この操作をクエリの外側の try-catch ブロックに置くことで、"副作用の原因となりうるような操作はクエリ内では行わない" という原則に従っているのです。</span><span class="sxs-lookup"><span data-stu-id="81e38-112">By putting this operation in a try-catch block outside the query, the code follows the rule of avoiding operations in queries that can cause side-effects.</span></span> <span data-ttu-id="81e38-113">一般に、アプリケーションが不明な状態に陥ることのないよう、例外を処理する際には十分な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="81e38-113">In general, great care must be taken when you consume exceptions to make sure that an application is not left in an unknown state.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="81e38-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="81e38-114">Compiling the Code</span></span>  
<span data-ttu-id="81e38-115">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span><span class="sxs-lookup"><span data-stu-id="81e38-115">Create a VB.NET console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="81e38-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="81e38-116">See also</span></span>

- [<span data-ttu-id="81e38-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81e38-117">LINQ to Objects (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)
- [<span data-ttu-id="81e38-118">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81e38-118">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
