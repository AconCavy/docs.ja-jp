---
title: '方法: 拡張子別にファイルをグループ化する (LINQ)'
ms.date: 07/20/2015
ms.assetid: 904dc6d7-7162-4655-a7f4-5785d669bc5a
ms.openlocfilehash: 67c48cd735b51009835cbc8df3101ea3cb212a87
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396546"
---
# <a name="how-to-group-files-by-extension-linq-visual-basic"></a><span data-ttu-id="5b1ef-102">方法: 拡張機能でファイルをグループ化する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b1ef-102">How to: Group Files by Extension (LINQ) (Visual Basic)</span></span>
<span data-ttu-id="5b1ef-103">この例では、LINQ を使用して、ファイルまたはフォルダーの一覧に対して、高度なグループ化および並べ替えを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-103">This example shows how LINQ can be used to perform advanced grouping and sorting operations on lists of files or folders.</span></span> <span data-ttu-id="5b1ef-104">また、<xref:System.Linq.Enumerable.Skip%2A> メソッドと <xref:System.Linq.Enumerable.Take%2A> メソッドを使用して、出力をページごとにコンソール ウィンドウに表示する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-104">It also shows how to page output in the console window by using the <xref:System.Linq.Enumerable.Skip%2A> and <xref:System.Linq.Enumerable.Take%2A> methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b1ef-105">例</span><span class="sxs-lookup"><span data-stu-id="5b1ef-105">Example</span></span>  
 <span data-ttu-id="5b1ef-106">次のクエリは、指定されたディレクトリ ツリーの内容を、ファイル名の拡張子別にグループ化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-106">The following query shows how to group the contents of a specified directory tree by the file name extension.</span></span>  
  
```vb  
Module GroupByExtension  
    Public Sub Main()  
  
        ' Root folder to query, along with all subfolders.  
        Dim startFolder As String = "C:\program files\Microsoft Visual Studio 9.0\VB\"  
  
        ' Used in WriteLine() to skip over startfolder in output lines.  
        Dim rootLength As Integer = startFolder.Length  
  
        'Take a snapshot of the folder contents  
        Dim dir As New System.IO.DirectoryInfo(startFolder)  
        Dim fileList = dir.GetFiles("*.*", System.IO.SearchOption.AllDirectories)  
  
        ' Create the query.  
        Dim queryGroupByExt = From file In fileList _  
                          Group By file.Extension.ToLower() Into fileGroup = Group _  
                          Order By ToLower _  
                          Select fileGroup  
  
        ' Execute the query. By storing the result we can  
        ' page the display with good performance.  
        Dim groupByExtList = queryGroupByExt.ToList()  
  
        ' Display one group at a time. If the number of
        ' entries is greater than the number of lines  
        ' in the console window, then page the output.  
        Dim trimLength = startFolder.Length  
        PageOutput(groupByExtList, trimLength)  
  
    End Sub  
  
    ' Pages console display for large query results. No more than one group per page.  
    ' This sub specifically works with group queries of FileInfo objects  
    ' but can be modified for any type.  
    Sub PageOutput(ByVal groupQuery, ByVal charsToSkip)  
  
        ' "3" = 1 line for extension key + 1 for "Press any key" + 1 for input cursor.  
        Dim numLines As Integer = Console.WindowHeight - 3  
        ' Flag to indicate whether there are more results to display  
        Dim goAgain As Boolean = True  
  
        For Each fg As IEnumerable(Of System.IO.FileInfo) In groupQuery  
            ' Start a new extension at the top of a page.  
            Dim currentLine As Integer = 0  
  
            Do While (currentLine < fg.Count())  
                Console.Clear()  
                Console.WriteLine(fg(0).Extension)  
  
                ' Get the next page of results  
                ' No more than one filename per page  
                Dim resultPage = From file In fg _  
                                Skip currentLine Take numLines  
  
                ' Execute the query. Trim the display output.  
                For Each line In resultPage  
                    Console.WriteLine(vbTab & line.FullName.Substring(charsToSkip))  
                Next  
  
                ' Advance the current position  
                currentLine = numLines + currentLine  
  
                ' Give the user a chance to break out of the loop  
                Console.WriteLine("Press any key for next page or the 'End' key to exit.")  
                Dim key As ConsoleKey = Console.ReadKey().Key  
                If key = ConsoleKey.End Then  
                    goAgain = False  
                    Exit For  
                End If  
            Loop  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="5b1ef-107">このプログラムの出力は、ローカル ファイル システムの詳細と `startFolder` の設定内容に応じて長くなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-107">The output from this program can be long, depending on the details of the local file system and what the `startFolder` is set to.</span></span> <span data-ttu-id="5b1ef-108">すべての結果を確認できるように、次の例では、結果をページごとに出力する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-108">To enable viewing of all results, this example shows how to page through results.</span></span> <span data-ttu-id="5b1ef-109">同じ手法を Windows アプリケーションや Web アプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-109">The same techniques can be applied to Windows and Web applications.</span></span> <span data-ttu-id="5b1ef-110">このコードでは、グループ内の項目をページごとに処理するため、`For Each` ループを入れ子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-110">Notice that because the code pages the items in a group, a nested `For Each` loop is required.</span></span> <span data-ttu-id="5b1ef-111">また、一覧内での現在位置を計算し、ユーザーがページングを停止してプログラムを終了できるようにするロジックも追加されています。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-111">There is also some additional logic to compute the current position in the list, and to enable the user to stop paging and exit the program.</span></span> <span data-ttu-id="5b1ef-112">この場合、ページング クエリは、元のクエリからキャッシュされた結果に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-112">In this particular case, the paging query is run against the cached results from the original query.</span></span> <span data-ttu-id="5b1ef-113">LINQ to SQL などの他のコンテキストでは、このようなキャッシュは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-113">In other contexts, such as LINQ to SQL, such caching is not required.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="5b1ef-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5b1ef-114">Compile the code</span></span>  
<span data-ttu-id="5b1ef-115">System.Linq 名前空間の `Imports` ステートメントを使用して、Visual Basic コンソール アプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="5b1ef-115">Create a Visual Basic console application project, with an `Imports` statement for the System.Linq namespace.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5b1ef-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b1ef-116">See also</span></span>

- [<span data-ttu-id="5b1ef-117">LINQ to Objects (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b1ef-117">LINQ to Objects (Visual Basic)</span></span>](linq-to-objects.md)
- [<span data-ttu-id="5b1ef-118">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b1ef-118">LINQ and File Directories (Visual Basic)</span></span>](linq-and-file-directories.md)
