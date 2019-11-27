---
title: 拡張メソッドを使用したリファクタリング
ms.date: 07/20/2015
ms.assetid: d87ae99a-cfa9-4a31-a5e4-9d6437be6810
ms.openlocfilehash: 1045a649907f877bddd0ec2d8c0e5dfa2a5d0830
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346504"
---
# <a name="refactoring-using-an-extension-method-visual-basic"></a><span data-ttu-id="29ac7-102">拡張メソッドを使用したリファクタリング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29ac7-102">Refactoring Using an Extension Method (Visual Basic)</span></span>
<span data-ttu-id="29ac7-103">この例は、拡張メソッドとして実装されている純粋関数を使用して文字列の連結をリファクタリングすることによって、[段落のテキスト (Visual Basic) を取得](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md)する前の例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="29ac7-103">This example builds on the previous example, [Retrieving the Text of the Paragraphs (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/retrieving-the-text-of-the-paragraphs.md), by refactoring the concatenation of strings using a pure function that is implemented as an extension method.</span></span>  
  
 <span data-ttu-id="29ac7-104">前の例では、<xref:System.Linq.Enumerable.Aggregate%2A> 標準クエリ演算子を使用して、複数の文字列が 1 つの文字列に連結されていました。</span><span class="sxs-lookup"><span data-stu-id="29ac7-104">The previous example used the <xref:System.Linq.Enumerable.Aggregate%2A> standard query operator to concatenate multiple strings into one string.</span></span> <span data-ttu-id="29ac7-105">ただし、拡張メソッドでこの処理を記述した方が、結果のクエリが小さく簡単になるので便利です。</span><span class="sxs-lookup"><span data-stu-id="29ac7-105">However, it is more convenient to write an extension method to do this, because the resulting query smaller and more simple.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29ac7-106">例</span><span class="sxs-lookup"><span data-stu-id="29ac7-106">Example</span></span>  
 <span data-ttu-id="29ac7-107">この例では、WordprocessingML ドキュメントを処理して、段落、各段落のスタイル、および各段落のテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="29ac7-107">This example processes a WordprocessingML document, retrieving the paragraphs, the style of each paragraph, and the text of each paragraph.</span></span> <span data-ttu-id="29ac7-108">この例は、このチュートリアルのこれまでの例に基づいています。</span><span class="sxs-lookup"><span data-stu-id="29ac7-108">This example builds on the previous examples in this tutorial.</span></span>  
  
 <span data-ttu-id="29ac7-109">この例には、`StringConcatenate` メソッドの複数のオーバーロードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="29ac7-109">The example contains multiple overloads of the `StringConcatenate` method.</span></span>  
  
 <span data-ttu-id="29ac7-110">この例のソースドキュメントを作成する手順については[、「ソースとなる Office OPEN XML ドキュメントを作成する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29ac7-110">You can find instructions for creating the source document for this example in [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="29ac7-111">この例では、WindowsBase アセンブリのクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="29ac7-111">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="29ac7-112">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="29ac7-112">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each s As String In source  
        sb.Append(s)  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal func As Func(Of T, String)) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each item As T In source  
        sb.Append(func(item))  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal separator As String) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each s As T In source  
        sb.Append(s).Append(separator)  
    Next  
    Return sb.ToString()  
End Function  
  
<System.Runtime.CompilerServices.Extension()> _  
Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
ByVal func As Func(Of T, String), ByVal separator As String) As String  
    Dim sb As StringBuilder = New StringBuilder()  
    For Each item As T In source  
        sb.Append(func(item)).Append(separator)  
    Next  
    Return sb.ToString()  
End Function  
```  
  
## <a name="example"></a><span data-ttu-id="29ac7-113">例</span><span class="sxs-lookup"><span data-stu-id="29ac7-113">Example</span></span>  
 <span data-ttu-id="29ac7-114">`StringConcatenate` メソッドには 4 つのオーバーロードがあります。</span><span class="sxs-lookup"><span data-stu-id="29ac7-114">There are four overloads of the `StringConcatenate` method.</span></span> <span data-ttu-id="29ac7-115">あるオーバーロードは、文字列のコレクションを受け取って 1 つの文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="29ac7-115">One overload simply takes a collection of strings and returns a single string.</span></span> <span data-ttu-id="29ac7-116">別のオーバーロードは、任意の型のコレクション、および単一のコレクションを文字列に射影するデリゲートを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="29ac7-116">Another overload can take a collection of any type, and a delegate that projects from a singleton of the collection to a string.</span></span> <span data-ttu-id="29ac7-117">残りの 2 つのオーバーロードでは、区切り文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="29ac7-117">There are two more overloads that allow you to specify a separator string.</span></span>  
  
 <span data-ttu-id="29ac7-118">次のコードでは、4 つのオーバーロードがすべて使用されています。</span><span class="sxs-lookup"><span data-stu-id="29ac7-118">The following code uses all four overloads.</span></span>  
  
```vb  
Dim numbers As String() = {"one", "two", "three"}  
  
Console.WriteLine("{0}", numbers.StringConcatenate())  
Console.WriteLine("{0}", numbers.StringConcatenate(":"))  
  
Dim intNumbers As Integer() = {1, 2, 3}  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString()))  
Console.WriteLine("{0}", intNumbers.StringConcatenate(Function(i) i.ToString(), ":"))  
```  
  
 <span data-ttu-id="29ac7-119">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="29ac7-119">This example produces the following output:</span></span>  
  
```console  
onetwothree  
one:two:three:  
123  
1:2:3:  
```  
  
## <a name="example"></a><span data-ttu-id="29ac7-120">例</span><span class="sxs-lookup"><span data-stu-id="29ac7-120">Example</span></span>  
 <span data-ttu-id="29ac7-121">ここで、新しい拡張メソッドを利用するように例を変更します。</span><span class="sxs-lookup"><span data-stu-id="29ac7-121">Now, the example can be modified to take advantage of the new extension method:</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
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
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = para.ParagraphNode.<w:r>.<w:t>.StringConcatenate(Function(e) CStr(e)) _  
            }  
  
        For Each p In paraWithText  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text)  
        Next  
  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="29ac7-122">この例では、「ソースとなる[Office OPEN XML ドキュメントの作成 (Visual Basic)](creating-the-source-office-open-xml-document.md)」で説明されているドキュメントに適用すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="29ac7-122">This example produces the following output when applied to the document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md).</span></span>
  
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
  
 <span data-ttu-id="29ac7-123">このリファクタリングは、純粋関数へのリファクタリングの変化形であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="29ac7-123">Note that this refactoring is a variant of refactoring into a pure function.</span></span> <span data-ttu-id="29ac7-124">次のトピックでは、純粋関数へのリファクタリングに関する考え方について詳しく紹介します。</span><span class="sxs-lookup"><span data-stu-id="29ac7-124">The next topic will introduce the idea of factoring into pure functions in more detail.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="29ac7-125">次の手順</span><span class="sxs-lookup"><span data-stu-id="29ac7-125">Next Steps</span></span>  
 <span data-ttu-id="29ac7-126">次の例は、純粋関数を使用してこのコードをリファクターする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="29ac7-126">The next example shows how to refactor this code in another way, by using pure functions:</span></span>  
  
- [<span data-ttu-id="29ac7-127">純粋関数によるリファクタリング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29ac7-127">Refactoring Using a Pure Function (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-using-a-pure-function.md)  
  
## <a name="see-also"></a><span data-ttu-id="29ac7-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="29ac7-128">See also</span></span>

- [<span data-ttu-id="29ac7-129">チュートリアル: WordprocessingML ドキュメント内のコンテンツの操作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29ac7-129">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)
- [<span data-ttu-id="29ac7-130">純粋関数へのリファクタリング (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29ac7-130">Refactoring Into Pure Functions (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)
