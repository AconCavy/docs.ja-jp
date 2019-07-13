---
title: XElement クラスの概要 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: d5ae3feae632c3bc3ce927a6d376e9ec4911e9fd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647394"
---
# <a name="xelement-class-overview-visual-basic"></a>XElement クラスの概要 (Visual Basic)
<xref:System.Xml.Linq.XElement> クラスは、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の基礎クラスの 1 つです。 これは XML 要素を表します。 このクラスを使用すると、要素の作成、要素のコンテンツの変更、子要素の追加、変更、削除、要素への属性の追加、および要素のコンテンツのテキスト形式へのシリアル化を行うことができます。 <xref:System.Xml?displayProperty=nameWithType>、<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> などの、<xref:System.Xml.Xsl.XslCompiledTransform> の他のクラスと相互運用することもできます。  
  
## <a name="xelement-functionality"></a>XElement の機能  
 このトピックでは、<xref:System.Xml.Linq.XElement> クラスによって提供される機能について説明します。  
  
### <a name="constructing-xml-trees"></a>XML ツリーの構築  
 次のようなさまざまな方法で XML ツリーを構築できます。  
  
- コードで XML ツリーを構築できます。 詳細については、次を参照してください。 [XML ツリーの作成 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)します。  
  
- <xref:System.IO.TextReader>、テキスト ファイル、Web アドレス (URL) など、さまざまなソースから XML を解析できます。 詳細については、次を参照してください。 [XML の解析 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)します。  
  
- <xref:System.Xml.XmlReader> を使用してツリーを設定できます。 詳細については、「 <xref:System.Xml.Linq.XNode.ReadFrom%2A> 」を参照してください。  
  
- <xref:System.Xml.XmlWriter> にコンテンツを書き込むことができるモジュールがある場合は、<xref:System.Xml.Linq.XContainer.CreateWriter%2A> メソッドを使用してライターを作成し、このライターをモジュールに渡し、<xref:System.Xml.XmlWriter> に書き込まれたコンテンツを使用して XML ツリーを設定できます。  
  
 しかし、XML ツリーを作成する最も一般的な方法は次のとおりです。  
  
```vb  
Dim contacts As XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone>206-555-0144</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 XML ツリーを作成するもう 1 つの一般的な方法では、次の例に示すように、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリの結果を使用して XML ツリーを設定します。  
  
```vb  
Dim srcTree As XElement = _  
    <Root>  
        <Element>1</Element>  
        <Element>2</Element>  
        <Element>3</Element>  
        <Element>4</Element>  
        <Element>5</Element>  
    </Root>  
Dim xmlTree As XElement = _  
    <Root>  
        <Child>1</Child>  
        <Child>2</Child>  
        <%= From el In srcTree.Elements() _  
            Where el.Value > 2 _  
            Select el %>  
    </Root>  
Console.WriteLine(xmlTree)  
```  
  
 この例を実行すると、次の出力が生成されます。  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a>XML ツリーのシリアル化  
 XML ツリーは、<xref:System.IO.File>、<xref:System.IO.TextWriter>、または <xref:System.Xml.XmlWriter> にシリアル化できます。  
  
 詳細については、次を参照してください。 [XML ツリーをシリアル化する」(Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)します。  
  
### <a name="retrieving-xml-data-via-axis-methods"></a>軸メソッドによる XML データの取得  
 軸メソッドを使用すると、属性、子要素、子孫要素、および祖先要素を取得できます。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリは、軸メソッドに対して機能し、XML ツリーを操作して処理するための、柔軟で強力な複数の機能を備えています。  
  
 詳細については、次を参照してください。 [LINQ to XML 軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)します。  
  
### <a name="querying-xml-trees"></a>XML ツリーのクエリ  
 XML ツリーからデータを抽出する [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリを記述できます。  
  
 詳細については、次を参照してください。 [XML ツリーのクエリ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)します。  
  
### <a name="modifying-xml-trees"></a>XML ツリーの変更  
 要素を変更するには、そのコンテンツや属性を変更するなど、さまざまな方法があります。 要素を親から削除することもできます。  
  
 詳細については、次を参照してください。 [XML ツリーの変更 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)します。  
  
## <a name="see-also"></a>関連項目

- [LINQ to XML プログラミングの概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
