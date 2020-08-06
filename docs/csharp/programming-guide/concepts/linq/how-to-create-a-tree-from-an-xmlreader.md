---
title: XmlReader からツリーを作成する方法 (C#)
description: XmlReader から直接 XML ツリーを作成する方法について説明します。 T:System.Xml.XmlReader オブジェクトを作成する方法を示す例をご覧ください。
ms.date: 07/20/2015
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
ms.openlocfilehash: 3801177e664d142652d38748d44eaf3f274239dd
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302660"
---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a><span data-ttu-id="aeb7c-104">XmlReader からツリーを作成する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="aeb7c-104">How to create a tree from an XmlReader (C#)</span></span>
<span data-ttu-id="aeb7c-105">このトピックでは、<xref:System.Xml.XmlReader> から直接 XML ツリーを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-105">This topic shows how to create an XML tree directly from an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="aeb7c-106"><xref:System.Xml.Linq.XElement> から <xref:System.Xml.XmlReader> を作成するには、<xref:System.Xml.XmlReader> を要素ノードに配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-106">To create an <xref:System.Xml.Linq.XElement> from an <xref:System.Xml.XmlReader>, you must position the <xref:System.Xml.XmlReader> on an element node.</span></span> <span data-ttu-id="aeb7c-107"><xref:System.Xml.XmlReader> はコメントや処理命令をスキップしますが、<xref:System.Xml.XmlReader> がテキスト ノードに配置されている場合はエラーがスローされます。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-107">The <xref:System.Xml.XmlReader> will skip comments and processing instructions, but if the <xref:System.Xml.XmlReader> is positioned on a text node, an error will be thrown.</span></span> <span data-ttu-id="aeb7c-108">このようなエラーを回避するため、<xref:System.Xml.XmlReader> から XML ツリーを作成する前に、必ず <xref:System.Xml.XmlReader> を要素に配置してください。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-108">To avoid such errors, always position the <xref:System.Xml.XmlReader> on an element before you create an XML tree from the <xref:System.Xml.XmlReader>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb7c-109">例</span><span class="sxs-lookup"><span data-stu-id="aeb7c-109">Example</span></span>  
 <span data-ttu-id="aeb7c-110">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:書籍 (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md)」。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-110">This example uses the following XML document: [Sample XML File: Books (LINQ to XML)](./sample-xml-file-books-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="aeb7c-111">次のコードでは、`T:System.Xml.XmlReader` オブジェクトを作成し、最初の要素ノードが見つかるまでノードを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-111">The following code creates an `T:System.Xml.XmlReader` object, and then reads nodes until it finds the first element node.</span></span> <span data-ttu-id="aeb7c-112">次に <xref:System.Xml.Linq.XElement> オブジェクトを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-112">It then loads the <xref:System.Xml.Linq.XElement> object.</span></span>  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
```  
  
 <span data-ttu-id="aeb7c-113">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="aeb7c-113">This example produces the following output:</span></span>  
  
```xml  
<Catalog>  
   <Book id="bk101">  
      <Author>Garghentini, Davide</Author>  
      <Title>XML Developer's Guide</Title>  
      <Genre>Computer</Genre>  
      <Price>44.95</Price>  
      <PublishDate>2000-10-01</PublishDate>  
      <Description>An in-depth look at creating applications
      with XML.</Description>  
   </Book>  
   <Book id="bk102">  
      <Author>Garcia, Debra</Author>  
      <Title>Midnight Rain</Title>  
      <Genre>Fantasy</Genre>  
      <Price>5.95</Price>  
      <PublishDate>2000-12-16</PublishDate>  
      <Description>A former architect battles corporate zombies,
      an evil sorceress, and her own childhood to become queen
      of the world.</Description>  
   </Book>  
</Catalog>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aeb7c-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="aeb7c-114">See also</span></span>

- [<span data-ttu-id="aeb7c-115">XML の解析 (C#)</span><span class="sxs-lookup"><span data-stu-id="aeb7c-115">Parsing XML (C#)</span></span>](how-to-parse-a-string.md)
