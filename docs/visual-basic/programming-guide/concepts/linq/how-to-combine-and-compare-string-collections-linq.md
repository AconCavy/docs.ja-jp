---
title: '方法: 文字列コレクションを結合および比較する (LINQ)'
ms.date: 07/20/2015
ms.assetid: 243cfafc-9eaa-4354-a9df-d329f1d39913
ms.openlocfilehash: 2df5db16e51e8f9de8a8e3506eb1f7b737065a14
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337572"
---
# <a name="how-to-combine-and-compare-string-collections-linq-visual-basic"></a><span data-ttu-id="f5b46-102">方法: 文字列コレクションを結合および比較する (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5b46-102">How to: Combine and Compare String Collections (LINQ) (Visual Basic)</span></span>

<span data-ttu-id="f5b46-103">この例では、複数行のテキストが含まれるファイルをマージし、結果を並び替える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f5b46-103">This example shows how to merge files that contain lines of text and then sort the results.</span></span> <span data-ttu-id="f5b46-104">具体的には、複数のテキスト行からなる 2 つの集合の単純な連結、和集合、積集合を求める方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f5b46-104">Specifically, it shows how to perform a simple concatenation, a union, and an intersection on the two sets of text lines.</span></span>

## <a name="set-up-the-project-and-the-text-files"></a><span data-ttu-id="f5b46-105">プロジェクトとテキスト ファイルを設定する</span><span class="sxs-lookup"><span data-stu-id="f5b46-105">Set up the project and the text files</span></span>

1. <span data-ttu-id="f5b46-106">次の名前を names1.txt という名前のテキスト ファイルにコピーし、プロジェクト フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="f5b46-106">Copy these names into a text file that is named names1.txt and save it in your project folder:</span></span>

    ```text
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Potra, Cristina
    Noriega, Fabricio
    Aw, Kam Foo
    Beebe, Ann
    Toyoshima, Tim
    Guy, Wey Yuan
    Garcia, Debra
    ```

2. <span data-ttu-id="f5b46-107">次の名前を names2.txt という名前のテキスト ファイルにコピーし、プロジェクト フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="f5b46-107">Copy these names into a text file that is named names2.txt and save it in your project folder.</span></span> <span data-ttu-id="f5b46-108">2 つのファイルには、共通の名前がいくつか含まれていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f5b46-108">Note that the two files have some names in common.</span></span>

    ```text
    Liu, Jinghao
    Bankov, Peter
    Holm, Michael
    Garcia, Hugo
    Beebe, Ann
    Gilchrist, Beth
    Myrcha, Jacek
    Giakoumakis, Leo
    McLin, Nkenge
    El Yassir, Mehdi
    ```

## <a name="example"></a><span data-ttu-id="f5b46-109">例</span><span class="sxs-lookup"><span data-stu-id="f5b46-109">Example</span></span>

```vb
Class ConcatenateStrings
    Shared Sub Main()

        ' Create the IEnumerable data sources.
        Dim fileA As String() = System.IO.File.ReadAllLines("../../../names1.txt")
        Dim fileB As String() = System.IO.File.ReadAllLines("../../../names2.txt")

        ' Simple concatenation and sort.
        Dim concatQuery = fileA.Concat(fileB).OrderBy(Function(name) name)

        ' Pass the query variable to another function for execution
        OutputQueryResults(concatQuery, "Simple concatenation and sort. Duplicates are preserved:")

        ' New query. Concatenate files and remove duplicates
        Dim uniqueNamesQuery = fileA.Union(fileB).OrderBy(Function(name) name)
        OutputQueryResults(uniqueNamesQuery, "Union removes duplicate names:")

        ' New query. Find the names that occur in both files.
        Dim commonNamesQuery = fileA.Intersect(fileB)
        OutputQueryResults(commonNamesQuery, "Merge based on intersect: ")

        ' New query in three steps for better readability
        ' First filter each list separately

        Dim nameToSearch As String = "Garcia"
        Dim mergeQueryA As IEnumerable(Of String) = From name In fileA
                          Let n = name.Split(New Char() {","})
                          Where n(0) = nameToSearch
                          Select name

        Dim mergeQueryB = From name In fileB
                          Let n = name.Split(New Char() {","})
                          Where n(0) = nameToSearch
                          Select name

        ' Create a new query to concatenate and sort results. Duplicates are removed in Union.
        ' Note that none of the queries actually executed until the call to OutputQueryResults.
        Dim mergeSortQuery = mergeQueryA.Union(mergeQueryB).OrderBy(Function(str) str)

        ' Now execute mergeSortQuery
        OutputQueryResults(mergeSortQuery, "Concat based on partial name match """ & nameToSearch & """ from each list:")

        ' Keep console window open in debug mode.
        Console.WriteLine("Press any key to exit.")
        Console.ReadKey()

    End Sub

    Shared Sub OutputQueryResults(ByVal query As IEnumerable(Of String), ByVal message As String)

        Console.WriteLine(System.Environment.NewLine & message)
        For Each item As String In query
            Console.WriteLine(item)
        Next
        Console.WriteLine(query.Count & " total names in list")

    End Sub
End Class
' Output:

' Simple concatenation and sort. Duplicates are preserved:
' Aw, Kam Foo
' Bankov, Peter
' Bankov, Peter
' Beebe, Ann
' Beebe, Ann
' El Yassir, Mehdi
' Garcia, Debra
' Garcia, Hugo
' Garcia, Hugo
' Giakoumakis, Leo
' Gilchrist, Beth
' Guy, Wey Yuan
' Holm, Michael
' Holm, Michael
' Liu, Jinghao
' McLin, Nkenge
' Myrcha, Jacek
' Noriega, Fabricio
' Potra, Cristina
' Toyoshima, Tim
' 20 total names in list

' Union removes duplicate names:
' Aw, Kam Foo
' Bankov, Peter
' Beebe, Ann
' El Yassir, Mehdi
' Garcia, Debra
' Garcia, Hugo
' Giakoumakis, Leo
' Gilchrist, Beth
' Guy, Wey Yuan
' Holm, Michael
' Liu, Jinghao
' McLin, Nkenge
' Myrcha, Jacek
' Noriega, Fabricio
' Potra, Cristina
' Toyoshima, Tim
' 16 total names in list

' Merge based on intersect:
' Bankov, Peter
' Holm, Michael
' Garcia, Hugo
' Beebe, Ann
' 4 total names in list

' Concat based on partial name match "Garcia" from each list:
' Garcia, Debra
' Garcia, Hugo
' 2 total names in list
```

## <a name="compile-the-code"></a><span data-ttu-id="f5b46-110">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="f5b46-110">Compile the code</span></span>

<span data-ttu-id="f5b46-111">Visual Basic コンソール アプリケーションのプロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="f5b46-111">Create a Visual Basic console application project.</span></span> <span data-ttu-id="f5b46-112">System.Linq 名前空間の `Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="f5b46-112">Add an `Imports` statement for the System.Linq namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="f5b46-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5b46-113">See also</span></span>

- [<span data-ttu-id="f5b46-114">LINQ と文字列 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5b46-114">LINQ and Strings (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [<span data-ttu-id="f5b46-115">LINQ とファイル ディレクトリ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5b46-115">LINQ and File Directories (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-and-file-directories.md)
