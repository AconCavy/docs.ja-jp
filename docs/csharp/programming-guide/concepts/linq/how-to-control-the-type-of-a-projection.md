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
# <a name="how-to-control-the-type-of-a-projection-c"></a>プロジェクションの型を制御する方法 (C#)
射影は、1 つのデータのセットを取得し、フィルター処理し、その形式を変更し、その型も変更するプロセスです。 ほとんどのクエリ式は射影を実行します。 このセクション内のクエリ式は、ほとんどが <xref:System.Collections.Generic.IEnumerable%601> の <xref:System.Xml.Linq.XElement> に評価されますが、射影の型を制御して別の型のコレクションを作成することができます。 このトピックでは、その方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、`Customer` という新しい型を定義します。 次に、クエリ式の `Customer` 句で新しい `Select` オブジェクトをインスタンス化します。 これによって、クエリ式の型が <xref:System.Collections.Generic.IEnumerable%601> の `Customer` になります。  
  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」。  
  
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
  
 このコードを実行すると、次の出力が生成されます。  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Linq.Enumerable.Select%2A>
