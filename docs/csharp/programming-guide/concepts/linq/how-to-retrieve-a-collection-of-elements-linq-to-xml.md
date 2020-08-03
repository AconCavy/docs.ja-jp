---
title: 要素のコレクションを取得する方法 (LINQ to XML) (C#)
description: この C# の Elements メソッドによって、要素の子要素のコレクションが取得されます。 この LINQ to XML の例では、要素の子要素を反復処理します。
ms.date: 07/20/2015
ms.assetid: b849668c-7976-4974-b8e1-1cd587d34258
ms.openlocfilehash: 4f9b6ae4713af9ce1a4eeb5257f57cd9724f68b2
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103351"
---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-c"></a>要素のコレクションを取得する方法 (LINQ to XML) (C#)
このトピックでは、<xref:System.Xml.Linq.XContainer.Elements%2A> メソッドについて説明します。 このメソッドは、要素の子要素のコレクションを取得します。  
  
## <a name="example"></a>例  
 この例では、`purchaseOrder` 要素の子要素を反復処理します。  
  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:一般的な購買発注書 (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md) を使用します。  
  
```csharp  
XElement po = XElement.Load("PurchaseOrder.xml");  
IEnumerable<XElement> childElements =  
    from el in po.Elements()  
    select el;  
foreach (XElement el in childElements)  
    Console.WriteLine("Name: " + el.Name);  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```output  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>関連項目

- [LINQ to XML 軸 (C#)](./linq-to-xml-axes-overview.md)
