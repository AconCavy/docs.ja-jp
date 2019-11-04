---
title: '方法: XML からテキスト ファイルを生成する (C#)'
ms.date: 07/20/2015
ms.assetid: 9ad283f7-7cac-42ff-bf32-92aa866e6883
ms.openlocfilehash: 8e36bbda60bea207707dcf869afc059e645ec8ad
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418305"
---
# <a name="how-to-generate-text-files-from-xml-c"></a>方法: XML からテキスト ファイルを生成する (C#)
この例では、XML ファイルからコンマ区切り (CSV) ファイルを生成する方法について説明します。  
  
## <a name="example"></a>例  
 この例の C# バージョンでは、メソッド構文と `Aggregate` 演算子を使用して、1 つの式で XML ドキュメントから CSV ファイルを生成します。 詳細については、「[LINQ でのクエリ構文とメソッド構文](./query-syntax-and-method-syntax-in-linq.md)」を参照してください。  
  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:顧客と注文 (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)」。  
  
```csharp  
XElement custOrd = XElement.Load("CustomersOrders.xml");  
string csv =  
    (from el in custOrd.Element("Customers").Elements("Customer")  
    select  
        String.Format("{0},{1},{2},{3},{4},{5},{6},{7},{8},{9}{10}",  
            (string)el.Attribute("CustomerID"),  
            (string)el.Element("CompanyName"),  
            (string)el.Element("ContactName"),  
            (string)el.Element("ContactTitle"),  
            (string)el.Element("Phone"),  
            (string)el.Element("FullAddress").Element("Address"),  
            (string)el.Element("FullAddress").Element("City"),  
            (string)el.Element("FullAddress").Element("Region"),  
            (string)el.Element("FullAddress").Element("PostalCode"),  
            (string)el.Element("FullAddress").Element("Country"),  
            Environment.NewLine  
        )  
    )  
    .Aggregate(  
        new StringBuilder(),  
        (sb, s) => sb.Append(s),  
        sb => sb.ToString()  
    );  
Console.WriteLine(csv);  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```output  
GREAL,Great Lakes Food Market,Howard Snyder,Marketing Manager,(503) 555-7555,2732 Baker Blvd.,Eugene,OR,97403,USA  
HUNGC,Hungry Coyote Import Store,Yoshi Latimer,Sales Representative,(503) 555-6874,City Center Plaza 516 Main St.,Elgin,OR,97827,USA  
LAZYK,Lazy K Kountry Store,John Steel,Marketing Manager,(509) 555-7969,12 Orchestra Terrace,Walla Walla,WA,99362,USA  
LETSS,Let's Stop N Shop,Jaime Yorres,Owner,(415) 555-5938,87 Polk St. Suite 5,San Francisco,CA,94117,USA  
```  
  
## <a name="see-also"></a>関連項目

- [プロジェクションと変換 (LINQ to XML) (C#)](how-to-work-with-dictionaries-using-linq-to-xml.md)
