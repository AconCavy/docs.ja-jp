---
title: プロジェクションの型を制御する方法 (C#)
description: C# の LINQ でプロジェクションの型を制御して、XElement の IEnumerable<T> 以外の型のコレクションを作成する方法について学習します。
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 32b019b5e1574e7160b4dce5fb0322caa3c1ca71
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103342"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="91013-103">プロジェクションの型を制御する方法 (C#)</span><span class="sxs-lookup"><span data-stu-id="91013-103">How to control the type of a projection (C#)</span></span>
<span data-ttu-id="91013-104">射影は、1 つのデータのセットを取得し、フィルター処理し、その形式を変更し、その型も変更するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="91013-104">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="91013-105">ほとんどのクエリ式は射影を実行します。</span><span class="sxs-lookup"><span data-stu-id="91013-105">Most query expressions perform projections.</span></span> <span data-ttu-id="91013-106">このセクション内のクエリ式は、ほとんどが <xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> に評価されますが、射影の型を制御して別の型のコレクションを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="91013-106">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="91013-107">このトピックでは、その方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="91013-107">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91013-108">例</span><span class="sxs-lookup"><span data-stu-id="91013-108">Example</span></span>  
 <span data-ttu-id="91013-109">次の例では、`Customer` という新しい型を定義します。</span><span class="sxs-lookup"><span data-stu-id="91013-109">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="91013-110">次に、クエリ式の `Customer` 句で新しい `Select` オブジェクトをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="91013-110">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="91013-111">これによって、クエリ式の型が <xref:System.Collections.Generic.IEnumerable%601> の `Customer` になります。</span><span class="sxs-lookup"><span data-stu-id="91013-111">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="91013-112">この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」。</span><span class="sxs-lookup"><span data-stu-id="91013-112">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 <span data-ttu-id="91013-113">このコードを実行すると、次の出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="91013-113">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="91013-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="91013-114">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
