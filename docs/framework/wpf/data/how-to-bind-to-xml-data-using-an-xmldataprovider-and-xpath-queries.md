---
title: '方法: XMLDataProvider と XPath クエリを使用して XML データにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- XmlDataProvider [WPF], binding to XML data
- data binding [WPF], binding to XML data using XmlDataProvider queries
- binding [WPF], to XML data using XmlDataProvider queries
ms.assetid: 7dcd018f-16aa-4870-8e47-c1b4ea31e574
ms.openlocfilehash: 4833e024fcd352094a2163f11df8572aa4c241f8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944650"
---
# <a name="how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries"></a>方法: XMLDataProvider と XPath クエリを使用して XML データにバインドする
この例では、 [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] <xref:System.Windows.Data.XmlDataProvider>を使用してデータにバインドする方法を示します。  
  
 を使用すると[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 、アプリケーションのデータバインディングを介してアクセスできる基になるデータは、ノードの任意のツリーにすることができます。<xref:System.Windows.Data.XmlDataProvider> つまり、は<xref:System.Windows.Data.XmlDataProvider> 、ノードの任意の[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]ツリーをバインディングソースとして使用する便利な方法を提供します。  
  
## <a name="example"></a>例  
 次の例では、データが[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] <xref:System.Windows.FrameworkElement.Resources%2A>セクション内に*データアイランド*として直接埋め込まれています。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データ アイランドは、`<x:XData>` タグ内にラップされていることと、常にルート ノードを 1 つだけ (この例では *Inventory*) 持つことが必要です。  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データのルート ノードには、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間を空の文字列に設定する **xmlns** 属性があります。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページ内にインラインで配置されるデータ アイランドに XPath クエリを適用する場合に必須です。 このインラインの場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、、、およびデータアイランドは、 <xref:System.Windows>名前空間を継承します。 このため、名前空間を空白に設定して、XPath クエリを<xref:System.Windows>名前空間で修飾しないようにする必要があります。これにより、クエリが誤って送信されます。  
  
 [!code-xaml[XMLDataSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource/CS/Window1.xaml#1)]  
  
 この例に示すように、同じバインディング宣言を属性構文で作成するには、特殊文字を適切にエスケープする必要があります。 詳しくは、「[XML Character Entities and XAML](../../xaml-services/xml-character-entities-and-xaml.md)」(XML 文字エンティティと XAML) をご覧ください。  
  
 この<xref:System.Windows.Controls.ListBox>例を実行すると、によって次の項目が表示されます。 これらは、*Books* の下のすべての要素のうち、*Stock* の値が "*out*" か、*Number* の値が 3 に等しいか 8 以上のものの *Title* です。 に設定されている<xref:System.Windows.Data.XmlDataProvider.XPath%2A> <xref:System.Windows.Data.XmlDataProvider>値によって、*書籍*の要素のみが公開される (基本的にフィルターを設定する) ことが示されるので、CD 項目は返されません。  
  
 ![4冊の書籍のタイトルを示す XPath の例のスクリーンショット。](./media/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries/xpath-example-listbox-details.png)  
  
 この例では<xref:System.Windows.Data.Binding.XPath%2A> 、の<xref:System.Windows.Controls.TextBlock>バインド<xref:System.Windows.DataTemplate>のが "*Title*" に設定されているため、書籍のタイトルが表示されます。 属性の値 ( *ISBN*など) を表示する場合は、その<xref:System.Windows.Data.Binding.XPath%2A>値を "`@ISBN`" に設定します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 内の **XPath** プロパティは、XmlNode.SelectNodes メソッドによって処理されます。 別の結果を得るために、**XPath** クエリを変更できます。 前の例のバインド<xref:System.Windows.Data.Binding.XPath%2A> <xref:System.Windows.Controls.ListBox>に対するクエリの例をいくつか次に示します。  
  
- `XPath="Book[1]"` は、最初の書籍要素 ("XML in Action") を返します。 **XPath** のインデックスが 0 ではなく 1 から開始することにご注意ください。  
  
- `XPath="Book[@*]"` は、任意の属性を持つすべての書籍要素を返します。  
  
- `XPath="Book[last()-1]"` は、最後から 2 番目の書籍要素 ("Introducing Microsoft .NET") を返します。  
  
- `XPath="*[position()>3]"` は、最初の 3 つを除くすべての書籍要素を返します。  
  
 **XPath**クエリを実行すると、 <xref:System.Xml.XmlNode>または XmlNodes のリストが返されます。 <xref:System.Xml.XmlNode>は共通言語ランタイム (clr) オブジェクトです。これは、 <xref:System.Windows.Data.Binding.Path%2A>プロパティを使用して共通言語ランタイム (clr) のプロパティにバインドできることを意味します。 前の例をもう一度考えてみます。 この例の残りの部分が変わらず、 <xref:System.Windows.Controls.TextBlock>バインドを次のように変更した場合は、 <xref:System.Windows.Controls.ListBox>返された XmlNodes の名前がに表示されます。 この場合、返されたノードの名前はすべて "*Book*" です。  
  
 [!code-xaml[XmlDataSourceVariation#XmlNodePath](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSourceVariation/CS/Page1.xaml#xmlnodepath)]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページのソースに [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] をデータ アイランドとして埋め込む方法では、コンパイル時に正確なデータ コンテンツが必要となるので、アプリケーションによっては不都合が生じます。 したがって、次の例のように、外部 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ファイルからのデータの取得もサポートされています。  
  
 [!code-xaml[XMLDataSource2#XmlFileExample](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlDataSource2/CS/Window1.xaml#xmlfileexample)]  
  
 データが[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]リモートファイルに存在する場合は、次のように<xref:System.Windows.Data.XmlDataProvider.Source%2A>属性に適切[!INCLUDE[TLA2#tla_url](../../../../includes/tla2sharptla-url-md.md)]なを割り当てることによって、データへのアクセスを定義します。  
  
```xml  
<XmlDataProvider x:Key="BookData" Source="http://MyUrl" XPath="Books"/>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.ObjectDataProvider>
- [XDocument、XElement、または LINQ for XML クエリの結果にバインドする](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md)
- [階層 XML データでマスター詳細パターンを使用する](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [バインディング ソースの概要](binding-sources-overview.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
