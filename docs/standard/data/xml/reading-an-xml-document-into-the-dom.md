---
title: XML ドキュメントの DOM への読み取り
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a4fb291f-5630-49ba-a49a-5b66c3b71e49
ms.openlocfilehash: 02338d72f51d3a7507c0dfa030383399b9e213f6
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282403"
---
# <a name="reading-an-xml-document-into-the-dom"></a><span data-ttu-id="e3658-102">XML ドキュメントの DOM への読み取り</span><span class="sxs-lookup"><span data-stu-id="e3658-102">Reading an XML Document into the DOM</span></span>
<span data-ttu-id="e3658-103">XML 情報は、さまざまな形式からメモリに読み取られます。</span><span class="sxs-lookup"><span data-stu-id="e3658-103">XML information is read into memory from different formats.</span></span> <span data-ttu-id="e3658-104">XML 情報は、文字列、ストリーム、URL、テキスト リーダー、および <xref:System.Xml.XmlReader> から派生したクラスから読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="e3658-104">It can be read from a string, stream, URL, text reader, or a class derived from the <xref:System.Xml.XmlReader>.</span></span>  
  
 <span data-ttu-id="e3658-105">ドキュメントをメモリに読み取る <xref:System.Xml.XmlDocument.Load%2A> メソッドには、オーバーロードされたメソッドが用意されており、異なる形式からデータを取得するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="e3658-105">The <xref:System.Xml.XmlDocument.Load%2A> method brings the document into memory and has overloaded methods available to take data from each of the different formats.</span></span> <span data-ttu-id="e3658-106">また、文字列から XML を読み取る <xref:System.Xml.XmlDocument.LoadXml%2A> メソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="e3658-106">There is also a <xref:System.Xml.XmlDocument.LoadXml%2A> method that reads XML from a string.</span></span>  
  
 <span data-ttu-id="e3658-107">各 <xref:System.Xml.XmlDocument.Load%2A> メソッドによって、XML ドキュメント オブジェクト モデル (DOM) が読み込まれるときに作成されるノードは異なります。</span><span class="sxs-lookup"><span data-stu-id="e3658-107">Different <xref:System.Xml.XmlDocument.Load%2A> methods affect which nodes are created when the XML Document Object Model (DOM) is loaded.</span></span> <span data-ttu-id="e3658-108">各種の <xref:System.Xml.XmlDocument.Load%2A> メソッド間の違いと、それについて説明しているトピックを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="e3658-108">The following table lists the differences between some of the <xref:System.Xml.XmlDocument.Load%2A> methods and topics that address them.</span></span>  
  
|<span data-ttu-id="e3658-109">Subject</span><span class="sxs-lookup"><span data-stu-id="e3658-109">Subject</span></span>|<span data-ttu-id="e3658-110">トピック</span><span class="sxs-lookup"><span data-stu-id="e3658-110">Topic</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="e3658-111">空白ノードの作成</span><span class="sxs-lookup"><span data-stu-id="e3658-111">Creation of white space nodes</span></span>|<span data-ttu-id="e3658-112">DOM を読み込むために使用したオブジェクトに応じて、DOM で生成される空白ノードと有意の空白ノードの処理が異なります。</span><span class="sxs-lookup"><span data-stu-id="e3658-112">The object used to load the DOM has an affect on the white space and significant white space nodes generated in the DOM.</span></span> <span data-ttu-id="e3658-113">詳細については、「[DOM を読み込むときの空白および有意の空白の処理](white-space-and-significant-white-space-handling-when-loading-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3658-113">For more information, see [White Space and Significant White Space Handling when Loading the DOM](white-space-and-significant-white-space-handling-when-loading-the-dom.md).</span></span>|  
|<span data-ttu-id="e3658-114">特定ノード以降の XML の読み込み、または XML ドキュメント全体の読み込み</span><span class="sxs-lookup"><span data-stu-id="e3658-114">Loading XML starting from a specific node or loading the entire XML document</span></span>|<span data-ttu-id="e3658-115"><xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> メソッドを使用して、データを特定のノードから DOM に読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="e3658-115">Using the <xref:System.Xml.XmlDocument.Load%2A?displayProperty=nameWithType> method data can be loaded from a specific node into the DOM.</span></span> <span data-ttu-id="e3658-116">詳細については、「[リーダーからのデータの読み込み](load-data-from-a-reader.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3658-116">For more information, see [Load Data from a Reader](load-data-from-a-reader.md).</span></span>|  
|<span data-ttu-id="e3658-117">XML の読み込み時の検証</span><span class="sxs-lookup"><span data-stu-id="e3658-117">Validating the XML as it is loaded</span></span>|<span data-ttu-id="e3658-118">DOM に読み込む XML データは、読み込みながら検証することができます。</span><span class="sxs-lookup"><span data-stu-id="e3658-118">The XML data loaded into the DOM can be validated as it is loaded.</span></span> <span data-ttu-id="e3658-119">これは検証型の <xref:System.Xml.XmlReader> を使用して行えます。</span><span class="sxs-lookup"><span data-stu-id="e3658-119">This is accomplished using a validating <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="e3658-120">読み込み時の XML の検証の詳細については、「[DOM における XML ドキュメントの検証](validating-an-xml-document-in-the-dom.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e3658-120">For more information about validating XML as it is loaded, see [Validating an XML Document in the DOM](validating-an-xml-document-in-the-dom.md).</span></span>|  
  
 <span data-ttu-id="e3658-121"><xref:System.Xml.XmlDocument.LoadXml%2A> メソッドによって XML を読み込む例を次に示します。読み込まれたデータは、`data.xml` というテキスト ファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="e3658-121">The following example shows XML being loaded with the <xref:System.Xml.XmlDocument.LoadXml%2A> method and the data subsequently saved to a text file called `data.xml`.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.LoadXml(("<book genre='novel' ISBN='1-861001-57-5'>" & _  
                    "<title>Pride And Prejudice</title>" & _  
                    "</book>"))  
        ' Save the document to a file.  
        doc.Save("data.xml")  
    End Sub 'Main  
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
    public static void Main()  
    {  
        // Create the XmlDocument.  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5'>" +  
                    "<title>Pride And Prejudice</title>" +  
                    "</book>");  
  
        // Save the document to a file.  
        doc.Save("data.xml");  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="e3658-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3658-122">See also</span></span>

- [<span data-ttu-id="e3658-123">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="e3658-123">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
