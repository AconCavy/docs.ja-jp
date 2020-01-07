---
title: 段落のテキストの取得
ms.date: 07/20/2015
ms.assetid: 095fa0d9-7b1b-4cbb-9c13-e2c9d8923d31
ms.openlocfilehash: 0f53eec44e0b11a6c23c7afb4892e4d5d876d6d6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341601"
---
# <a name="retrieving-the-text-of-the-paragraphs-visual-basic"></a><span data-ttu-id="8ca65-102">段落のテキストを取得する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ca65-102">Retrieving the Text of the Paragraphs (Visual Basic)</span></span>
<span data-ttu-id="8ca65-103">この例は、前の例に基づいて[おり、段落とそのスタイル (Visual Basic) を取得](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md)しています。</span><span class="sxs-lookup"><span data-stu-id="8ca65-103">This example builds on the previous example, [Retrieving the Paragraphs and Their Styles (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-paragraphs-and-their-styles.md).</span></span> <span data-ttu-id="8ca65-104">この新しい例では、各段落のテキストを文字列として取得します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-104">This new example retrieves the text of each paragraph as a string.</span></span>  
  
 <span data-ttu-id="8ca65-105">テキストを取得するため、この例で追加するクエリでは、匿名型のコレクションを反復処理し、新しいメンバー `Text` を追加して匿名型の新しいコレクションを射影します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-105">To retrieve the text, this example adds an additional query that iterates through the collection of anonymous types and projects a new collection of an anonymous type with the addition of a new member, `Text`.</span></span> <span data-ttu-id="8ca65-106">また、<xref:System.Linq.Enumerable.Aggregate%2A> 標準クエリ演算子を使用して、複数の文字列を 1 つの文字列に連結します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-106">It uses the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span>  
  
 <span data-ttu-id="8ca65-107">この手法 (まず匿名型のコレクションに射影した後、このコレクションを使用して匿名型の新しいコレクションに射影する) は、一般的で便利な表現形式です。</span><span class="sxs-lookup"><span data-stu-id="8ca65-107">This technique (that is, first projecting to a collection of an anonymous type, then using this collection to project to a new collection of an anonymous type) is a common and useful idiom.</span></span> <span data-ttu-id="8ca65-108">最初の匿名型に射影せずに、このクエリを記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="8ca65-108">This query could have been written without projecting to the first anonymous type.</span></span> <span data-ttu-id="8ca65-109">また、レイジー評価のため、その射影を行うことによって追加使用される処理能力は大きくありません。</span><span class="sxs-lookup"><span data-stu-id="8ca65-109">However, because of lazy evaluation, doing so does not use much additional processing power.</span></span> <span data-ttu-id="8ca65-110">この表現形式を使用すると、ヒープ上に作成される存続期間の短いオブジェクトが増加しますが、それによってパフォーマンスが大幅に低下することはありません。</span><span class="sxs-lookup"><span data-stu-id="8ca65-110">The idiom creates more short lived objects on the heap, but this does not substantially degrade performance.</span></span>  
  
 <span data-ttu-id="8ca65-111">もちろん、段落、各段落のスタイル、および各段落のテキストを取得する機能を持つ 1 つのクエリを記述することも可能です。</span><span class="sxs-lookup"><span data-stu-id="8ca65-111">Of course, it would be possible to write a single query that contains the functionality to retrieve the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="8ca65-112">しかし、多くの場合、比較的複雑なクエリは複数のクエリに分割した方が便利です。コードのモジュール性が高まり、保守が簡単になるためです。</span><span class="sxs-lookup"><span data-stu-id="8ca65-112">However, it often is useful to break up a more complicated query into multiple queries because the resulting code is more modular and easier to maintain.</span></span> <span data-ttu-id="8ca65-113">また、クエリの一部を再利用する必要がある場合、クエリを分割して記述すると、リファクタリングが容易になります。</span><span class="sxs-lookup"><span data-stu-id="8ca65-113">Furthermore, if you need to reuse a portion of the query, it is easier to refactor if the queries are written in this manner.</span></span>  
  
 <span data-ttu-id="8ca65-114">これらのクエリは連結されており、「[チュートリアル: 遅延実行 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)」で詳しく調査されている処理モデルを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-114">These queries, which are chained together, use the processing model that is examined in detail in the topic [Tutorial: Deferred Execution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ca65-115">使用例</span><span class="sxs-lookup"><span data-stu-id="8ca65-115">Example</span></span>  
 <span data-ttu-id="8ca65-116">この例では、WordprocessingML ドキュメントを処理して、要素ノード、スタイル名、および各段落のテキストを特定します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-116">This example processes a WordprocessingML document, determining the element node, the style name, and the text of each paragraph.</span></span> <span data-ttu-id="8ca65-117">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8ca65-117">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="8ca65-118">新しいクエリについては、以下のコード内にあるコメントで説明が示されています。</span><span class="sxs-lookup"><span data-stu-id="8ca65-118">The new query is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="8ca65-119">この例のソースドキュメントを作成する手順については、「[ソースとなる Office OPEN XML ドキュメントを作成する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ca65-119">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="8ca65-120">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-120">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="8ca65-121">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-121">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    ' Following function is required because Visual Basic does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Following is the new query that retrieves the text of  
        ' each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t> _  
                    .Aggregate(New StringBuilder(), _  
                               Function(s As StringBuilder, i As String) s.Append(CStr(i)), _  
                               Function(s As StringBuilder) s.ToString) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="8ca65-122">この例では、「ソースとなる[Office OPEN XML ドキュメントの作成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」で説明されているドキュメントに適用すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="8ca65-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
```console  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >Imports System<  
StyleName:Code ><  
StyleName:Code >Class Program<  
StyleName:Code >    Public Shared  Sub Main(ByVal args() As String)<  
StyleName:Code >        Console.WriteLine("Hello World")<  
StyleName:Code >   End Sub<  
StyleName:Code >End Class<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
  
## <a name="next-steps"></a><span data-ttu-id="8ca65-123">次のステップ</span><span class="sxs-lookup"><span data-stu-id="8ca65-123">Next Steps</span></span>  
 <span data-ttu-id="8ca65-124">次の例では、<xref:System.Linq.Enumerable.Aggregate%2A> の代わりに拡張メソッドを使用して、複数の文字列を 1 つの文字列に連結する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8ca65-124">The next example shows how to use an extension method, instead of <xref:System.Linq.Enumerable.Aggregate%2A>, to concatenate multiple strings into a single string.</span></span>  
  
- [<span data-ttu-id="8ca65-125">拡張メソッドを使用したリファクタリング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ca65-125">Refactoring Using an Extension Method (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-an-extension-method.md)  
  
## <a name="see-also"></a><span data-ttu-id="8ca65-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ca65-126">See also</span></span>

- [<span data-ttu-id="8ca65-127">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ca65-127">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="8ca65-128">LINQ to XML での遅延実行とレイジー評価 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ca65-128">Deferred Execution and Lazy Evaluation in LINQ to XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)
