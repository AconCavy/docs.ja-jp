---
title: 特定の子要素を持つ要素を検索する方法 (C#)
description: 特定の子要素を持つ要素を検索する方法について説明します。 コード例と追加リソースを確認してください。
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 1d02f3d3af0a3711a5361941727e2e0b6c8bbdc9
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301711"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>特定の子要素を持つ要素を検索する方法 (C#)
このトピックでは、特定の値を含む子要素を持つ特定の要素を検索する方法について説明します。  
  
## <a name="example"></a>例  
 この例では、"Examp2.EXE" の値を含む `Test` 子要素を持つ `CommandLine` 要素を検索します。  
  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル:テスト構成 (LINQ to XML)](./sample-xml-file-test-configuration-linq-to-xml.md)」。  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```output  
0002  
0006  
```  
  
## <a name="example"></a>例  
 次の例は名前空間に含まれている XML 用のクエリです。これらのクエリは上の例と同じ機能を表しています。 詳細については、「[名前空間の概要 (LINQ to XML)](namespaces-overview-linq-to-xml.md)」を参照してください。  
  
 この例では、次の XML ドキュメントを使用します: 「[サンプル XML ファイル: 名前空間内のテスト構成](./sample-xml-file-test-configuration-in-a-namespace1.md)」。  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```output  
0002  
0006  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [標準クエリ演算子の概要 (C#)](./standard-query-operators-overview.md)
- [射影操作 (C#)](./projection-operations.md)
