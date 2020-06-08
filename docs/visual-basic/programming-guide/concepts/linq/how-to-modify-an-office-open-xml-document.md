---
title: '方法: Office Open XML ドキュメントを変更する'
ms.date: 07/20/2015
ms.assetid: 1cefd7f5-8e39-44c4-869c-f8021538a777
ms.openlocfilehash: 9fb046f43686405a3d84cb68b49cd6dcd34e0839
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398026"
---
# <a name="how-to-modify-an-office-open-xml-document-visual-basic"></a><span data-ttu-id="60f0d-102">方法: Office Open XML ドキュメントを変更する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60f0d-102">How to: Modify an Office Open XML Document (Visual Basic)</span></span>
<span data-ttu-id="60f0d-103">このトピックでは、Office Open XML ドキュメントを開き、それを変更して保存する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="60f0d-103">This topic presents an example that opens an Office Open XML document, modifies it, and saves it.</span></span>  
  
 <span data-ttu-id="60f0d-104">Office Open XML の詳細については、[Eric White のブログ](http://www.ericwhite.com)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="60f0d-104">For more information on Office Open XML, see [Eric White's Blog](http://www.ericwhite.com).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60f0d-105">例</span><span class="sxs-lookup"><span data-stu-id="60f0d-105">Example</span></span>  
 <span data-ttu-id="60f0d-106">この例では、ドキュメント内の最初の段落要素を検索します。</span><span class="sxs-lookup"><span data-stu-id="60f0d-106">This example finds the first paragraph element in the document.</span></span> <span data-ttu-id="60f0d-107">次に、段落からテキストを取得し、段落内のテキスト ランをすべて削除します。</span><span class="sxs-lookup"><span data-stu-id="60f0d-107">It retrieves the text from the paragraph, and then deletes all text runs in the paragraph.</span></span> <span data-ttu-id="60f0d-108">また、大文字に変換された最初の段落のテキストから構成される新しいテキスト ランを作成します。</span><span class="sxs-lookup"><span data-stu-id="60f0d-108">It creates a new text run that consists of the first paragraph text that has been converted to upper case.</span></span> <span data-ttu-id="60f0d-109">最後に、変更した XML を Open XML パッケージにシリアル化して閉じます。</span><span class="sxs-lookup"><span data-stu-id="60f0d-109">It then serializes the changed XML into the Open XML package and closes it.</span></span>  
  
 <span data-ttu-id="60f0d-110">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="60f0d-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="60f0d-111">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="60f0d-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
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
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
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
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.ReadWrite)  
            Dim docPackageRelationship As PackageRelationship = wdPackage _  
                    .GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", _  
                            UriKind.Relative), docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                Dim xDoc As XDocument = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = documentPart _  
                        .GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                Dim stylePart As PackagePart = Nothing  
                Dim styleDoc As XDocument = Nothing  
  
                If (styleRelation IsNot Nothing) Then  
                    Dim styleUri As Uri = PackUriHelper.ResolvePartUri( _  
                            documentUri, styleRelation.TargetUri)  
                    stylePart = wdPackage.GetPart(styleUri)  
  
                    ' Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
  
                Dim paraNode As XElement = xDoc.Root.<w:body>...<w:p>.FirstOrDefault()  
  
                Dim paraText As String = ParagraphText(paraNode)  
  
                ' Remove all text runs.  
                paraNode...<w:r>.Remove()  
  
                paraNode.Add(<w:r><w:t><%= paraText.ToUpper() %></w:t></w:r>)  
  
                ' Save the XML into the package.  
                Using xw As XmlWriter = _  
                  XmlWriter.Create(documentPart.GetStream(FileMode.Create, FileAccess.Write))  
                    xDoc.Save(xw)  
                End Using  
  
                Console.WriteLine("New first paragraph: >{0}<", paraText.ToUpper())  
            End If  
        End Using  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="60f0d-112">このプログラムを実行した後で `SampleDoc.docx` を開くと、このプログラムによってドキュメント内の最初の段落が大文字に変換されたかどうかを確認できます。</span><span class="sxs-lookup"><span data-stu-id="60f0d-112">If you open `SampleDoc.docx` after running this program, you can see that this program converted the first paragraph in the document to upper case.</span></span>  
  
 <span data-ttu-id="60f0d-113">この例で「[ソースとなる Office Open XML ドキュメントの作成 (Visual Basic)](creating-the-source-office-open-xml-document.md)」に記載されているサンプルの Open XML ドキュメントを使用して実行すると、次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="60f0d-113">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (Visual Basic)](creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```console  
New first paragraph: >PARSING WORDPROCESSINGML WITH LINQ TO XML<  
```  
  
## <a name="see-also"></a><span data-ttu-id="60f0d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="60f0d-114">See also</span></span>

- [<span data-ttu-id="60f0d-115">高度なクエリ手法 (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60f0d-115">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
