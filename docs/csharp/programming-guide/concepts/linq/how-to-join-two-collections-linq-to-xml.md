---
title: 2 つのコレクションを結合する方法 (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 7b817ede-911a-4cff-9dd3-639c3fc228c9
ms.openlocfilehash: a5044778bbfd9529faf5fe63c72076f6a973c815
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345857"
---
# <a name="how-to-join-two-collections-linq-to-xml-c"></a><span data-ttu-id="50ce6-102">2 つのコレクションを結合する方法 (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="50ce6-102">How to join two collections (LINQ to XML) (C#)</span></span>

<span data-ttu-id="50ce6-103">XML ドキュメント内の要素または属性は、別の要素または属性を参照することがあります。</span><span class="sxs-lookup"><span data-stu-id="50ce6-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="50ce6-104">たとえば、「[サンプル XML ファイル: 顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」の XML ドキュメントには、顧客の一覧と注文の一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="50ce6-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="50ce6-105">各 `Customer` 要素には、`CustomerID` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="50ce6-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="50ce6-106">各 `Order` 要素には、`CustomerID` 要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="50ce6-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="50ce6-107">各注文の `CustomerID` 要素は、顧客の `CustomerID` 属性を参照します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>

<span data-ttu-id="50ce6-108">「[サンプル XSD ファイル: 顧客と注文](./sample-xsd-file-customers-and-orders1.md)」のトピックには、このドキュメントの検証に使用できる XSD が含まれています。</span><span class="sxs-lookup"><span data-stu-id="50ce6-108">The topic [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="50ce6-109">この XSD は、XSD の `xs:key` 機能と `xs:keyref` 機能を使用して、`CustomerID` 要素の `Customer` 属性がキーであることを確立し、各 `CustomerID` 要素の `Order` 要素と各 `CustomerID` 要素の `Customer` 属性の間にリレーションシップを確立します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>

<span data-ttu-id="50ce6-110">[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] では、`join` 句を使用することで、このリレーションシップを利用できます。</span><span class="sxs-lookup"><span data-stu-id="50ce6-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `join` clause.</span></span>

<span data-ttu-id="50ce6-111">使用できるインデックスがないため、このような結合では実行時のパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-111">Because there is no index available, such joining will have poor run-time performance.</span></span>

<span data-ttu-id="50ce6-112">`join` の詳細については、「[結合演算](./join-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50ce6-112">For more detailed information about `join`, see [Join Operations (C#)](./join-operations.md).</span></span>

## <a name="example"></a><span data-ttu-id="50ce6-113">例</span><span class="sxs-lookup"><span data-stu-id="50ce6-113">Example</span></span>

<span data-ttu-id="50ce6-114">次の例では、`Customer` 要素を `Order` 要素に結合し、注文に `CompanyName` 要素が含まれている新しい XML ドキュメントを生成します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>

<span data-ttu-id="50ce6-115">クエリを実行する前に、この例では、ドキュメントが「[サンプル XSD ファイル: 顧客と注文](./sample-xsd-file-customers-and-orders1.md)」のスキーマに準拠しているかどうかを検証します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span> <span data-ttu-id="50ce6-116">これにより、結合句が常に機能するようになります。</span><span class="sxs-lookup"><span data-stu-id="50ce6-116">This ensures that the join clause will always work.</span></span>

<span data-ttu-id="50ce6-117">このクエリでは、まずすべての `Customer` 要素を取得し、次にそれらを `Order` 要素に結合します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="50ce6-118">クエリでは、"K" より大きい `CustomerID` を持つ顧客の注文のみを選択します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="50ce6-119">次に、各注文内に顧客情報を含む新しい `Order` 要素を射影します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>

<span data-ttu-id="50ce6-120">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」。</span><span class="sxs-lookup"><span data-stu-id="50ce6-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>

<span data-ttu-id="50ce6-121">この例では、XSD スキーマ、[サンプル XSD ファイル: 顧客と注文](./sample-xsd-file-customers-and-orders1.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](./sample-xsd-file-customers-and-orders1.md).</span></span>

<span data-ttu-id="50ce6-122">この方式の結合ではパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="50ce6-122">Joining in this fashion will not perform well.</span></span> <span data-ttu-id="50ce6-123">結合は線形探索によって実行されます。</span><span class="sxs-lookup"><span data-stu-id="50ce6-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="50ce6-124">パフォーマンスを向上させるハッシュ テーブルまたはインデックスはありません。</span><span class="sxs-lookup"><span data-stu-id="50ce6-124">There are no hash tables or indexes to help with performance.</span></span>

```csharp
XmlSchemaSet schemas = new XmlSchemaSet();
schemas.Add("", "CustomersOrders.xsd");

Console.Write("Attempting to validate, ");
XDocument custOrdDoc = XDocument.Load("CustomersOrders.xml");

bool errors = false;
custOrdDoc.Validate(schemas, (o, e) =>
                     {
                         Console.WriteLine("{0}", e.Message);
                         errors = true;
                     });
Console.WriteLine("custOrdDoc {0}", errors ? "did not validate" : "validated");

if (!errors)
{
    // Join customers and orders, and create a new XML document with
    // a different shape.

    // The new document contains orders only for customers with a
    // CustomerID > 'K'
    XElement custOrd = custOrdDoc.Element("Root");
    XElement newCustOrd = new XElement("Root",
        from c in custOrd.Element("Customers").Elements("Customer")
        join o in custOrd.Element("Orders").Elements("Order")
                   on (string)c.Attribute("CustomerID") equals
                      (string)o.Element("CustomerID")
        where ((string)c.Attribute("CustomerID")).CompareTo("K") > 0
        select new XElement("Order",
            new XElement("CustomerID", (string)c.Attribute("CustomerID")),
            new XElement("CompanyName", (string)c.Element("CompanyName")),
            new XElement("ContactName", (string)c.Element("ContactName")),
            new XElement("EmployeeID", (string)o.Element("EmployeeID")),
            new XElement("OrderDate", (DateTime)o.Element("OrderDate"))
        )
    );
    Console.WriteLine(newCustOrd);
}
```

<span data-ttu-id="50ce6-125">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="50ce6-125">This code produces the following output:</span></span>

```output
Attempting to validate, custOrdDoc validated
<Root>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-03-21T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LAZYK</CustomerID>
    <CompanyName>Lazy K Kountry Store</CompanyName>
    <ContactName>John Steel</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-05-22T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>1</EmployeeID>
    <OrderDate>1997-06-25T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>8</EmployeeID>
    <OrderDate>1997-10-27T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>6</EmployeeID>
    <OrderDate>1997-11-10T00:00:00</OrderDate>
  </Order>
  <Order>
    <CustomerID>LETSS</CustomerID>
    <CompanyName>Let's Stop N Shop</CompanyName>
    <ContactName>Jaime Yorres</ContactName>
    <EmployeeID>4</EmployeeID>
    <OrderDate>1998-02-12T00:00:00</OrderDate>
  </Order>
</Root>
```
