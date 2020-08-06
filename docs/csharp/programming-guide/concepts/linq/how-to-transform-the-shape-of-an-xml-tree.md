---
title: XML ツリーの構造を変換する方法 (C#)
description: XML ツリーの構造を変換する方法について説明します。 XML ツリーの構造とは、その要素と属性の名前、およびその階層の特性を表すものです。
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 4fa3cc18f235d061ae1778c177c4ac9b626f4b71
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302647"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="3ece8-104">XML ツリーの構造を変換する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="3ece8-104">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="3ece8-105">XML ドキュメントの "*構造*" とは、XML ドキュメントの要素名、属性名、およびその階層の特性を表すものです。</span><span class="sxs-lookup"><span data-stu-id="3ece8-105">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="3ece8-106">XML ドキュメントの構造を変更しなければならない場合があります。</span><span class="sxs-lookup"><span data-stu-id="3ece8-106">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="3ece8-107">たとえば、既存の XML ドキュメントを、異なる要素名と属性名を必要とする別のシステムに送信するとします。</span><span class="sxs-lookup"><span data-stu-id="3ece8-107">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="3ece8-108">ドキュメント全体を調べ、必要に応じて要素の削除や要素名の変更を行うことも可能ですが、関数型構築を使用する方が、読みやすく保守しやすいコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="3ece8-108">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="3ece8-109">関数型構築の詳細については、「[関数型構築 (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="3ece8-109">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="3ece8-110">最初の例では、XML ドキュメントの編成を変更します。</span><span class="sxs-lookup"><span data-stu-id="3ece8-110">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="3ece8-111">ここでは、複合要素をツリー内で移動します。</span><span class="sxs-lookup"><span data-stu-id="3ece8-111">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="3ece8-112">このトピックの 2 番目の例では、ソース ドキュメントと異なる構造を持つ XML ドキュメントを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ece8-112">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="3ece8-113">要素名の大文字小文字の区別を変更し、一部の要素名を変更し、ソース ツリーの一部の要素を変換後のツリーに含めないようにします。</span><span class="sxs-lookup"><span data-stu-id="3ece8-113">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ece8-114">例</span><span class="sxs-lookup"><span data-stu-id="3ece8-114">Example</span></span>  
 <span data-ttu-id="3ece8-115">次のコードでは、組み込まれたクエリ式を使用して、XML ファイルの構造を変更します。</span><span class="sxs-lookup"><span data-stu-id="3ece8-115">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="3ece8-116">この例のソース XML ドキュメントでは、`Customers` 要素の下にある `Root` 要素に、すべての顧客が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ece8-116">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="3ece8-117">また、`Orders` 要素の下には `Root` 要素もあり、すべての注文が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ece8-117">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="3ece8-118">この例では、各顧客の注文が `Orders` 要素内の `Customer` 要素に含まれるような、新しい XML ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="3ece8-118">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="3ece8-119">元のドキュメントでは、`CustomerID` 要素内に `Order` 要素も含まれています。構造変更後のドキュメントからは、この要素が削除されます。</span><span class="sxs-lookup"><span data-stu-id="3ece8-119">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="3ece8-120">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」。</span><span class="sxs-lookup"><span data-stu-id="3ece8-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 <span data-ttu-id="3ece8-121">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ece8-121">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="3ece8-122">例</span><span class="sxs-lookup"><span data-stu-id="3ece8-122">Example</span></span>  
 <span data-ttu-id="3ece8-123">この例では、一部の要素の名前を変更し、一部の属性を要素に変換します。</span><span class="sxs-lookup"><span data-stu-id="3ece8-123">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="3ece8-124">コードで `ConvertAddress` を呼び出すと、<xref:System.Xml.Linq.XElement> オブジェクトの一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="3ece8-124">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="3ece8-125">メソッドの引数は、`Address` 属性の値が `Type` である `"Shipping"` 複合要素を特定するクエリです。</span><span class="sxs-lookup"><span data-stu-id="3ece8-125">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="3ece8-126">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:一般的な購買発注書 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) を使用します。</span><span class="sxs-lookup"><span data-stu-id="3ece8-126">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 <span data-ttu-id="3ece8-127">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="3ece8-127">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
