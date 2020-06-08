---
title: スタイルを含む WordprocessingML ドキュメント 2
ms.date: 07/20/2015
ms.assetid: a9136e4d-c368-4661-8049-7d45c679a236
ms.openlocfilehash: caf80014077bf57dc1ffb8eaeac6390cf4258015
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403551"
---
# <a name="wordprocessingml-document-with-styles"></a><span data-ttu-id="8ad82-102">スタイルを含む WordprocessingML ドキュメント</span><span class="sxs-lookup"><span data-stu-id="8ad82-102">WordprocessingML Document with Styles</span></span>
<span data-ttu-id="8ad82-103">複雑な WordprocessingML ドキュメントには、スタイルを使用して書式設定された段落が含まれています。</span><span class="sxs-lookup"><span data-stu-id="8ad82-103">More complicated WordprocessingML documents have paragraphs that are formatted with styles.</span></span>  
  
 <span data-ttu-id="8ad82-104">WordprocessingML ドキュメントを構成する場合に役立つ情報をいくつか説明します。</span><span class="sxs-lookup"><span data-stu-id="8ad82-104">A few notes about the makeup of WordprocessingML documents are helpful.</span></span> <span data-ttu-id="8ad82-105">WordprocessingML ドキュメントはパッケージに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8ad82-105">WordprocessingML documents are stored in packages.</span></span> <span data-ttu-id="8ad82-106">パッケージには複数のパーツがあります (パーツは、パッケージのコンテキストで使用する場合は明示的な意味を持っています。基本的には、パーツとはパッケージを構成するためにまとめて圧縮されたファイルです)。</span><span class="sxs-lookup"><span data-stu-id="8ad82-106">Packages have multiple parts (parts have an explicit meaning when used in the context of packages; essentially, parts are files that are zipped together to comprise a package).</span></span> <span data-ttu-id="8ad82-107">スタイルを使用して書式設定された段落がドキュメントに含まれている場合、スタイルが適用されている段落を含むドキュメント パーツがあります。</span><span class="sxs-lookup"><span data-stu-id="8ad82-107">If a document contains paragraphs that are formatted with styles, there will be a document part that contains paragraphs that have styles applied to them.</span></span> <span data-ttu-id="8ad82-108">ドキュメントによって参照されるスタイルを含むスタイル パーツもあります。</span><span class="sxs-lookup"><span data-stu-id="8ad82-108">There will also be a style part that contains the styles that are referred to by the document.</span></span>  
  
 <span data-ttu-id="8ad82-109">パッケージにアクセスする場合、任意のパスを使用してではなく、パーツ間のリレーションシップを通じてアクセスすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="8ad82-109">When accessing packages, it is important that you do so through the relationships between parts, rather than using an arbitrary path.</span></span> <span data-ttu-id="8ad82-110">この問題は「WordprocessingML ドキュメント内のコンテンツの操作」のチュートリアルでは扱いませんが、このチュートリアルに用意されているプログラム例では正しい方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8ad82-110">This issue is beyond the scope of the Manipulating Content in a WordprocessingML Document tutorial, but the example programs that are included in this tutorial demonstrate the correct approach.</span></span>  
  
## <a name="a-document-that-uses-styles"></a><span data-ttu-id="8ad82-111">スタイルを使用するドキュメント</span><span class="sxs-lookup"><span data-stu-id="8ad82-111">A Document that Uses Styles</span></span>  
 <span data-ttu-id="8ad82-112">「[WordprocessingML ドキュメントの構造 (Visual Basic)](shape-of-wordprocessingml-documents.md)」のトピックに示されている WordML の例は、とても簡単な例です。</span><span class="sxs-lookup"><span data-stu-id="8ad82-112">The WordML example presented in the [Shape of WordprocessingML Documents (Visual Basic)](shape-of-wordprocessingml-documents.md) topic is a very simple one.</span></span> <span data-ttu-id="8ad82-113">次のドキュメントはもっと複雑になっています。段落がスタイルで書式設定されています。</span><span class="sxs-lookup"><span data-stu-id="8ad82-113">The following document is more complicated: It has paragraphs that are formatted with styles.</span></span> <span data-ttu-id="8ad82-114">Office Open XML ドキュメントを構成する XML を確認するには、「[Office Open XML ドキュメント パーツを出力する例 (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md)」を実行するのが最も簡単です。</span><span class="sxs-lookup"><span data-stu-id="8ad82-114">The easiest way to see the XML that makes up an Office Open XML document is to run the [Example that Outputs Office Open XML Document Parts (Visual Basic)](example-that-outputs-office-open-xml-document-parts.md).</span></span>  
  
 <span data-ttu-id="8ad82-115">次のドキュメントでは、最初の段落にスタイル `Heading1` が設定されています。</span><span class="sxs-lookup"><span data-stu-id="8ad82-115">In the following document, the first paragraph has the style `Heading1`.</span></span> <span data-ttu-id="8ad82-116">既定のスタイルが設定されている段落が多数あります。</span><span class="sxs-lookup"><span data-stu-id="8ad82-116">There are a number of paragraphs that have the default style.</span></span> <span data-ttu-id="8ad82-117">スタイル `Code` が設定されている段落も多数あります。</span><span class="sxs-lookup"><span data-stu-id="8ad82-117">There are also a number of paragraphs that have the style `Code`.</span></span> <span data-ttu-id="8ad82-118">このドキュメントは比較的複雑であるため、LINQ to XML を使用した解析を行うのに適したドキュメントといえます。</span><span class="sxs-lookup"><span data-stu-id="8ad82-118">Because of this relative complexity, this is a more interesting document to parse with LINQ to XML.</span></span>  
  
 <span data-ttu-id="8ad82-119">既定以外のスタイルが設定されている段落では、段落要素に `w:pPr` という名前の子要素があり、この子要素には `w:pStyle` という子要素があります。</span><span class="sxs-lookup"><span data-stu-id="8ad82-119">In those paragraphs with non-default styles, the paragraph elements have a child element named `w:pPr`, which in turn has a child element `w:pStyle`.</span></span> <span data-ttu-id="8ad82-120">`w:val` 要素には、スタイル名を格納する  という属性があります。</span><span class="sxs-lookup"><span data-stu-id="8ad82-120">That element has an attribute, `w:val`, which contains the style name.</span></span> <span data-ttu-id="8ad82-121">段落に既定のスタイルが設定されている場合は、段落要素に `w:p.Pr` 子要素はありません。</span><span class="sxs-lookup"><span data-stu-id="8ad82-121">If the paragraph has the default style, it means that the paragraph element does not have a `w:p.Pr` child element.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<w:document  
    xmlns:ve="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:o="urn:schemas-microsoft-com:office:office"  
    xmlns:r="http://schemas.openxmlformats.org/officeDocument/2006/relationships"  
    xmlns:m="http://schemas.openxmlformats.org/officeDocument/2006/math"  
    xmlns:v="urn:schemas-microsoft-com:vml"  
    xmlns:wp="http://schemas.openxmlformats.org/drawingml/2006/wordprocessingDrawing"  
    xmlns:w10="urn:schemas-microsoft-com:office:word"  
    xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
    xmlns:wne="http://schemas.microsoft.com/office/word/2006/wordml">  
  <w:body>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Heading1" />  
      </w:pPr>  
      <w:r>  
        <w:t>Parsing WordprocessingML with LINQ to XML</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>The following example prints to the console.</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>using System;</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>class Program {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    public static void </w:t>  
      </w:r>  
      <w:smartTag w:uri="urn:schemas-microsoft-com:office:smarttags" w:element="place">  
        <w:r w:rsidRPr="00876F34">  
          <w:t>Main</w:t>  
        </w:r>  
      </w:smartTag>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>(string[] args) {</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">        Console.WriteLine("Hello World");</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t xml:space="preserve">    }</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRPr="00876F34" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r w:rsidRPr="00876F34">  
        <w:t>}</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0">  
      <w:r>  
        <w:t>This example produces the following output:</w:t>  
      </w:r>  
    </w:p>  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" />  
    <w:p w:rsidR="00A75AE0" w:rsidRDefault="00A75AE0" w:rsidP="006027C7">  
      <w:pPr>  
        <w:pStyle w:val="Code" />  
      </w:pPr>  
      <w:r>  
        <w:t>Hello World</w:t>  
      </w:r>  
    </w:p>  
    <w:sectPr w:rsidR="00A75AE0" w:rsidSect="00A75AE0">  
      <w:pgSz w:w="12240" w:h="15840" />  
      <w:pgMar w:top="1440" w:right="1800" w:bottom="1440" w:left="1800" w:header="720" w:footer="720" w:gutter="0" />  
      <w:cols w:space="720" />  
      <w:docGrid w:linePitch="360" />  
    </w:sectPr>  
  </w:body>  
</w:document>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8ad82-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ad82-122">See also</span></span>

- [<span data-ttu-id="8ad82-123">Office Open XML WordprocessingML ドキュメントの詳細 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ad82-123">Details of Office Open XML WordprocessingML Documents (Visual Basic)</span></span>](details-of-office-open-xml-wordprocessingml-documents.md)
