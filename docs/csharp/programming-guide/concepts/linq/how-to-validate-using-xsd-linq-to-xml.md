---
title: XSD を使用して検証する方法 (LINQ to XML) (C#)
description: XML スキーマ定義言語 (XSD) ファイルを基準として XML ツリーを検証する方法について説明します。 コード例を参照し、追加リソースを確認してください。
ms.date: 07/20/2015
ms.assetid: 6a7f83a9-2d74-4c2b-8417-0a8595879516
ms.openlocfilehash: 3b4d2137d511efbe20e4d31ad27e4975d5444ec9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302634"
---
# <a name="how-to-validate-using-xsd-linq-to-xml-c"></a><span data-ttu-id="a9d1a-104">XSD を使用して検証する方法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="a9d1a-104">How to validate using XSD (LINQ to XML) (C#)</span></span>
<span data-ttu-id="a9d1a-105"><xref:System.Xml.Schema> 名前空間には、XML スキーマ定義言語 (XSD) ファイルに対して XML ツリーを簡単に検証できる拡張メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-105">The <xref:System.Xml.Schema> namespace contains extension methods that make it easy to validate an XML tree against an XML Schema Definition Language (XSD) file.</span></span> <span data-ttu-id="a9d1a-106">詳細については、<xref:System.Xml.Schema.Extensions.Validate%2A> メソッドのドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-106">For more information, see the <xref:System.Xml.Schema.Extensions.Validate%2A> method documentation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9d1a-107">例</span><span class="sxs-lookup"><span data-stu-id="a9d1a-107">Example</span></span>  
 <span data-ttu-id="a9d1a-108">次の例では、<xref:System.Xml.Schema.XmlSchemaSet> を作成し、このスキーマ セットに対して 2 つの <xref:System.Xml.Linq.XDocument> オブジェクトを検証します。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-108">The following example creates an <xref:System.Xml.Schema.XmlSchemaSet>, then validates two <xref:System.Xml.Linq.XDocument> objects against the schema set.</span></span> <span data-ttu-id="a9d1a-109">ドキュメントの 1 つは有効ですが、その他のドキュメントは無効です。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-109">One of the documents is valid, the other is not.</span></span>  
  
```csharp  
string xsdMarkup =  
    @"<xsd:schema xmlns:xsd='http://www.w3.org/2001/XMLSchema'>  
       <xsd:element name='Root'>  
        <xsd:complexType>  
         <xsd:sequence>  
          <xsd:element name='Child1' minOccurs='1' maxOccurs='1'/>  
          <xsd:element name='Child2' minOccurs='1' maxOccurs='1'/>  
         </xsd:sequence>  
        </xsd:complexType>  
       </xsd:element>  
      </xsd:schema>";  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", XmlReader.Create(new StringReader(xsdMarkup)));  
  
XDocument doc1 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child2", "content1")  
    )  
);  
  
XDocument doc2 = new XDocument(  
    new XElement("Root",  
        new XElement("Child1", "content1"),  
        new XElement("Child3", "content1")  
    )  
);  
  
Console.WriteLine("Validating doc1");  
bool errors = false;  
doc1.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc1 {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
Console.WriteLine("Validating doc2");  
errors = false;  
doc2.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("doc2 {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="a9d1a-110">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-110">This example produces the following output:</span></span>  
  
```output  
Validating doc1  
doc1 validated  
  
Validating doc2  
The element 'Root' has invalid child element 'Child3'. List of possible elements expected: 'Child2'.  
doc2 did not validate  
```  
  
## <a name="example"></a><span data-ttu-id="a9d1a-111">例</span><span class="sxs-lookup"><span data-stu-id="a9d1a-111">Example</span></span>  
 <span data-ttu-id="a9d1a-112">次の例では、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」の XML ドキュメントが「[サンプル XSD ファイル: 顧客と注文](./sample-xsd-file-customers-and-orders1.md)」のスキーマに従った有効なものであるかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-112">The following example validates that the XML document from [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) is valid per the schema from [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="a9d1a-113">次に、ソース XML ドキュメントを変更します。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-113">It then modifies the source XML document.</span></span> <span data-ttu-id="a9d1a-114">変更するのは最初の顧客の `CustomerID` 属性です。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-114">It changes the `CustomerID` attribute on the first customer.</span></span> <span data-ttu-id="a9d1a-115">変更が完了すると、存在しない顧客を注文が参照するようになります。したがって、この XML ドキュメントは有効ではなくなります。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-115">After the change, orders will then refer to a customer that does not exist, so the XML document will no longer validate.</span></span>  
  
 <span data-ttu-id="a9d1a-116">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-116">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
 <span data-ttu-id="a9d1a-117">この例では、XSD スキーマ、[サンプル XSD ファイル: 顧客と注文](./sample-xsd-file-customers-and-orders1.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-117">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>  
  
```csharp  
XmlSchemaSet schemas = new XmlSchemaSet();  
schemas.Add("", "CustomersOrders.xsd");  
  
Console.WriteLine("Attempting to validate");  
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");  
bool errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
  
Console.WriteLine();  
// Modify the source document so that it will not validate.  
custOrdDoc.Root.Element("Orders").Element("Order").Element("CustomerID").Value = "AAAAA";  
Console.WriteLine("Attempting to validate after modification");  
errors = false;  
custOrdDoc.Validate(schemas, (o, e) =>  
                     {  
                         Console.WriteLine("{0}", e.Message);  
                         errors = true;  
                     });  
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");  
```  
  
 <span data-ttu-id="a9d1a-118">この例を実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a9d1a-118">This example produces the following output:</span></span>  
  
```output  
Attempting to validate  
custOrdDoc validated  
  
Attempting to validate after modification  
The key sequence 'AAAAA' in Keyref fails to refer to some key.  
custOrdDoc did not validate  
```  
  
## <a name="see-also"></a><span data-ttu-id="a9d1a-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9d1a-119">See also</span></span>

- <xref:System.Xml.Schema.Extensions.Validate%2A>
- [<span data-ttu-id="a9d1a-120">XML ツリーの作成 (C#)</span><span class="sxs-lookup"><span data-stu-id="a9d1a-120">Creating XML Trees (C#)</span></span>](creating-xml-trees-linq-to-xml-2.md)
