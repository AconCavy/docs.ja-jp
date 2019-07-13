---
title: '方法: LINQ to XML (Visual Basic) を使用してディクショナリを使用します。'
ms.date: 07/20/2015
ms.assetid: 6cb3f969-1986-414a-b850-87418712edea
ms.openlocfilehash: def00fcd356472825ebc4b9f5c306cf3547991e1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61614146"
---
# <a name="how-to-work-with-dictionaries-using-linq-to-xml-visual-basic"></a>方法: LINQ to XML (Visual Basic) を使用してディクショナリを使用します。
さまざまなデータ構造と XML を相互に変換すると便利な場合がよくあります。 このトピックでは、<xref:System.Collections.Generic.Dictionary%602> と XML を相互に変換することによる、一般的な相互変換の実装について説明します。  
  
## <a name="example"></a>例  
 この例では、埋め込み式の中で XML リテラルと、クエリを使用します。 新しいクエリ プロジェクト<xref:System.Xml.Linq.XElement>用の新しいコンテンツになりますが、オブジェクト、 `Root` <xref:System.Xml.Linq.XElement>オブジェクト。  
  
```vb  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)()  
dict.Add("Child1", "Value1")  
dict.Add("Child2", "Value2")  
dict.Add("Child3", "Value3")  
dict.Add("Child4", "Value4")  
Dim root As XElement = _  
    <Root>  
        <%= From keyValue In dict _  
            Select New XElement(keyValue.Key, keyValue.Value) %>  
    </Root>  
Console.WriteLine(root)  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```xml  
          <Root>  
  <Child1>Value1</Child1>  
  <Child2>Value2</Child2>  
  <Child3>Value3</Child3>  
  <Child4>Value4</Child4>  
</Root>  
```  
  
## <a name="example"></a>例  
 次のコードは、XML からディクショナリを作成します。  
  
```vb  
Dim root As XElement = _  
        <Root>  
            <Child1>Value1</Child1>  
            <Child2>Value2</Child2>  
            <Child3>Value3</Child3>  
            <Child4>Value4</Child4>  
        </Root>  
  
Dim dict As Dictionary(Of String, String) = New Dictionary(Of String, String)  
For Each el As XElement In root.Elements  
    dict.Add(el.Name.LocalName, el.Value)  
Next  
For Each str As String In dict.Keys  
    Console.WriteLine("{0}:{1}", str, dict(str))  
Next  
```  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
Child1:Value1  
Child2:Value2  
Child3:Value3  
Child4:Value4  
```  
  
## <a name="see-also"></a>関連項目

- [射影と変換 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
