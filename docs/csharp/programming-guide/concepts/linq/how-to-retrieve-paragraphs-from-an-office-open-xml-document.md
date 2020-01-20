---
title: Office Open XML ドキュメントから段落を取得する方法 (C#)
ms.date: 07/20/2015
ms.assetid: cc2687cf-d648-451e-88ac-3847c6c967c8
ms.openlocfilehash: 241bacc730f205bf501c1ab1ab47f6fda4c15d64
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347456"
---
# <a name="how-to-retrieve-paragraphs-from-an-office-open-xml-document-c"></a><span data-ttu-id="bfd8f-102">Office Open XML ドキュメントから段落を取得する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="bfd8f-102">How to retrieve paragraphs from an Office Open XML document (C#)</span></span>
<span data-ttu-id="bfd8f-103">このトピックでは、Office Open XML ドキュメントを開き、そのドキュメント内のすべての段落のコレクションを取得する例について説明します。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-103">This topic presents an example that opens an Office Open XML document, and retrieves a collection of all of the paragraphs in the document.</span></span>  
  
 <span data-ttu-id="bfd8f-104">Office Open XML の詳細については、[Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) と [www.ericwhite.com](http://ericwhite.com/) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-104">For more information on Office Open XML, see [Open XML SDK](https://github.com/OfficeDev/Open-XML-SDK) and [www.ericwhite.com](http://ericwhite.com/).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfd8f-105">例</span><span class="sxs-lookup"><span data-stu-id="bfd8f-105">Example</span></span>  
 <span data-ttu-id="bfd8f-106">この例では、Office Open XML パッケージを開き、Open XML パッケージ内のリレーションシップを使用してドキュメントとスタイル パーツを検索します。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-106">This example opens an Office Open XML package, uses the relationships within the Open XML package to find the document and the style parts.</span></span> <span data-ttu-id="bfd8f-107">次に、ドキュメントに対してクエリを実行して、段落 <xref:System.Xml.Linq.XElement> ノード、各段落のスタイル名、および各段落のテキストを含む匿名型のコレクションを射影します。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-107">It then queries the document, projecting a collection of an anonymous type that contains the paragraph <xref:System.Xml.Linq.XElement> node, the style name of each paragraph, and the text of each paragraph.</span></span>  
  
 <span data-ttu-id="bfd8f-108">この例では、例の中でも提供される `StringConcatenate` という名前の拡張メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-108">The example uses an extension method named `StringConcatenate`, which is also supplied in the example.</span></span>  
  
 <span data-ttu-id="bfd8f-109">この例の処理を説明した詳細なチュートリアルについては、「[XML の純粋関数型変換 (C#)](./introduction-to-pure-functional-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-109">For a detailed tutorial that explains how this example works, see [Pure Functional Transformations of XML (C#)](./introduction-to-pure-functional-transformations.md).</span></span>  
  
 <span data-ttu-id="bfd8f-110">この例では、WindowsBase アセンブリに含まれるクラスを使用します。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-110">This example uses classes found in the WindowsBase assembly.</span></span> <span data-ttu-id="bfd8f-111">また、<xref:System.IO.Packaging?displayProperty=nameWithType> 名前空間内の型を使用します。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-111">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```csharp  
public static class LocalExtensions  
{  
    public static string StringConcatenate(this IEnumerable<string> source)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item));  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate(this IEnumerable<string> source, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (string s in source)  
            sb.Append(s).Append(separator);  
        return sb.ToString();  
    }  
  
    public static string StringConcatenate<T>(this IEnumerable<T> source,  
        Func<T, string> func, string separator)  
    {  
        StringBuilder sb = new StringBuilder();  
        foreach (T item in source)  
            sb.Append(func(item)).Append(separator);  
        return sb.ToString();  
    }  
}  
  
class Program  
{  
    public static string ParagraphText(XElement e)  
    {  
        XNamespace w = e.Name.Namespace;  
        return e  
               .Elements(w + "r")  
               .Elements(w + "t")  
               .StringConcatenate(element => (string)element);  
    }  
  
    static void Main(string[] args)  
    {  
        const string fileName = "SampleDoc.docx";  
  
        const string documentRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument";  
        const string stylesRelationshipType =  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles";  
        const string wordmlNamespace =  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main";  
        XNamespace w = wordmlNamespace;  
  
        XDocument xDoc = null;  
        XDocument styleDoc = null;  
  
        using (Package wdPackage = Package.Open(fileName, FileMode.Open, FileAccess.Read))  
        {  
            PackageRelationship docPackageRelationship =  
              wdPackage  
              .GetRelationshipsByType(documentRelationshipType)  
              .FirstOrDefault();  
            if (docPackageRelationship != null)  
            {  
                Uri documentUri =  
                    PackUriHelper  
                    .ResolvePartUri(  
                       new Uri("/", UriKind.Relative),  
                             docPackageRelationship.TargetUri);  
                PackagePart documentPart =  
                    wdPackage.GetPart(documentUri);  
  
                //  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()));  
  
                //  Find the styles part. There will only be one.  
                PackageRelationship styleRelation =  
                  documentPart.GetRelationshipsByType(stylesRelationshipType)  
                  .FirstOrDefault();  
                if (styleRelation != null)  
                {  
                    Uri styleUri = PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri);  
                    PackagePart stylePart = wdPackage.GetPart(styleUri);  
  
                    //  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()));  
                }  
            }  
        }  
  
        string defaultStyle =  
            (string)(  
                from style in styleDoc.Root.Elements(w + "style")  
                where (string)style.Attribute(w + "type") == "paragraph" &&  
                      (string)style.Attribute(w + "default") == "1"  
                select style  
            ).First().Attribute(w + "styleId");  
  
        // Find all paragraphs in the document.  
        var paragraphs =  
            from para in xDoc  
                         .Root  
                         .Element(w + "body")  
                         .Descendants(w + "p")  
            let styleNode = para  
                            .Elements(w + "pPr")  
                            .Elements(w + "pStyle")  
                            .FirstOrDefault()  
            select new  
            {  
                ParagraphNode = para,  
                StyleName = styleNode != null ?  
                    (string)styleNode.Attribute(w + "val") :  
                    defaultStyle  
            };  
  
        // Retrieve the text of each paragraph.  
        var paraWithText =  
            from para in paragraphs  
            select new  
            {  
                ParagraphNode = para.ParagraphNode,  
                StyleName = para.StyleName,  
                Text = ParagraphText(para.ParagraphNode)  
            };  
  
        foreach (var p in paraWithText)  
            Console.WriteLine("StyleName:{0} >{1}<", p.StyleName, p.Text);  
    }  
}  
```  
  
 <span data-ttu-id="bfd8f-112">この例で「[ソースとなる Office Open XML ドキュメントの作成 (C#)](./creating-the-source-office-open-xml-document.md)」に記載されているサンプルの Open XML ドキュメントを使用して実行すると、次のように出力されます。</span><span class="sxs-lookup"><span data-stu-id="bfd8f-112">When run with the sample Open XML document described in [Creating the Source Office Open XML Document (C#)](./creating-the-source-office-open-xml-document.md), this example produces the following output:</span></span>  
  
```output  
StyleName:Heading1 >Parsing WordprocessingML with LINQ to XML<  
StyleName:Normal ><  
StyleName:Normal >The following example prints to the console.<  
StyleName:Normal ><  
StyleName:Code >using System;<  
StyleName:Code ><  
StyleName:Code >class Program {<  
StyleName:Code >    public static void (string[] args) {<  
StyleName:Code >        Console.WriteLine("Hello World");<  
StyleName:Code >    }<  
StyleName:Code >}<  
StyleName:Normal ><  
StyleName:Normal >This example produces the following output:<  
StyleName:Normal ><  
StyleName:Code >Hello World<  
```  
