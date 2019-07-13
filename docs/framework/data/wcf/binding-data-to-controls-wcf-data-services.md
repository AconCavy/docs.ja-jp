---
title: コントロールへのデータのバインド (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
ms.openlocfilehash: 99ad0db9f0adc54d57c5e9a7ed9a5aef3f0a3131
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652255"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>コントロールへのデータのバインド (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、`ComboBox` や `ListView` などのコントロールを <xref:System.Data.Services.Client.DataServiceCollection%601> クラスのインスタンスにバインドすることができます。 このコレクションは <xref:System.Collections.ObjectModel.ObservableCollection%601> クラスから継承され、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] フィードのデータが含まれます。 このクラスは、項目が追加または削除されたときに通知を行う動的なデータ コレクションを表します。 インスタンスを使用すると<xref:System.Data.Services.Client.DataServiceCollection%601>、データ バインディングの[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クライアント ライブラリによって追跡されるオブジェクトにこれらのイベントを処理する、<xref:System.Data.Services.Client.DataServiceContext>バインドされている UI 要素のデータの同期を維持します。  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> クラスは、<xref:System.Collections.Specialized.INotifyCollectionChanged> インターフェイスを (間接的に) 実装して、コレクションに対してオブジェクトが追加または削除されたときのコンテキストを警告します。 <xref:System.Data.Services.Client.DataServiceCollection%601> と使用するデータ サービス型オブジェクトは、<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスも実装して、バインディング コレクション内のオブジェクトのプロパティが変更されたときに <xref:System.Data.Services.Client.DataServiceCollection%601> に警告する必要があります。  
  
> [!NOTE]
>  使用すると、**サービス参照の追加**ダイアログまたは[DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)ツールを`/dataservicecollection`クライアント データ サービス クラスを生成するオプションは、生成されたデータ クラスの実装、 <xref:System.ComponentModel.INotifyPropertyChanged>インターフェイス。 詳細については、「[方法 :クライアント データ サービス クラスを手動で生成](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)します。  
  
## <a name="creating-the-binding-collection"></a>バインディング コレクションの作成  
 指定した <xref:System.Data.Services.Client.DataServiceCollection%601> インスタンスでクラス コンストラクター メソッドの 1 つを呼び出し、オプションで <xref:System.Data.Services.Client.DataServiceContext> または実行時に <xref:System.Data.Services.Client.DataServiceQuery%601> インスタンスを返す LINQ クエリを呼び出して <xref:System.Collections.Generic.IEnumerable%601> クラスの新しいインスタンスを作成します。 これは、<xref:System.Collections.Generic.IEnumerable%601>から具体化されるバインディング コレクションのオブジェクトのソースを提供する[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]フィードします。 詳細については、次を参照してください。[オブジェクトの具体化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)します。 既定では、バインドされたオブジェクトおよびコレクションに挿入された項目に対する変更は、<xref:System.Data.Services.Client.DataServiceContext> によって自動的に追跡されます。 手動でこれらの変更を追跡する必要がある場合を受け取るコンス トラクター メソッドの 1 つを呼び出して、`trackingMode`パラメーターの値を指定して<xref:System.Data.Services.Client.TrackingMode.None>します。  
  
 次の例は、指定された <xref:System.Data.Services.Client.DataServiceCollection%601> と、すべての顧客と関連する注文を返す <xref:System.Data.Services.Client.DataServiceContext> に基づいて、<xref:System.Data.Services.Client.DataServiceQuery%601> のインスタンスを作成する方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Windows Presentation Foundation 要素へのデータのバインド  
 <xref:System.Data.Services.Client.DataServiceCollection%601> クラスは <xref:System.Collections.ObjectModel.ObservableCollection%601> クラスを継承しているため、バインディングに <xref:System.Collections.ObjectModel.ObservableCollection%601> クラスを使用する場合と同様に、オブジェクトを Windows Presentation Foundation (WPF) アプリケーション内の要素 (またはコントロール) にバインドできます。 詳細については、次を参照してください。[データ バインド (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md)します。 データ サービスのデータを WPF コントロールにバインドする 1 つの方法は、要素の `DataContext` プロパティをクエリ結果を含む <xref:System.Data.Services.Client.DataServiceCollection%601> クラスのインスタンスに設定することです。 この場合、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティを使用して、コントロールのオブジェクト ソースを設定します。 <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> プロパティを使用して、バインドされたオブジェクトのどのプロパティを表示するかを指定します。 ナビゲーション プロパティから返される関連オブジェクトに要素をバインドする場合は、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティに対して定義されているバインドにパスを含めます。 このパスは、親コントロールの <xref:System.Windows.FrameworkElement.DataContext%2A> プロパティで設定されたルート オブジェクトを基準とした相対パスになります。 次の例では、<xref:System.Windows.FrameworkElement.DataContext%2A> 要素の <xref:System.Windows.Controls.StackPanel> プロパティを設定して、親コントロールをカスタム オブジェクトの <xref:System.Data.Services.Client.DataServiceCollection%601> にバインドします。  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 次の例は、子である <xref:System.Windows.Controls.DataGrid> コントロールと <xref:System.Windows.Controls.ComboBox> コントロールの XAML バインド定義を示しています。  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 詳細については、「[方法 :Windows Presentation Foundation 要素にデータをバインド](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)します。  
  
 一対多または多対多のリレーションシップのエンティティの場合は、リレーションシップのナビゲーション プロパティは関連するオブジェクトのコレクションを返します。 使用すると、**サービス参照の追加** ダイアログ ボックスまたは DataSvcUtil.exe ツールをクライアント データ サービス クラスを生成する、ナビゲーション プロパティがのインスタンスを返します<xref:System.Data.Services.Client.DataServiceCollection%601>します。 そのため、関連するオブジェクトをコントロールにバインドして、関連エンティティのマスター/詳細バインド パターンなど、一般的な WPF バインディング シナリオをサポートできます。 前の XAML の例では、XAML コードはマスター <xref:System.Data.Services.Client.DataServiceCollection%601> をルート データ要素にバインドします。 注文 <xref:System.Windows.Controls.DataGrid> が、選択した Customer オブジェクトから返される Orders <xref:System.Data.Services.Client.DataServiceCollection%601> にバインドされ、<xref:System.Windows.Window> のルート データ要素にバインドされます。  
  
## <a name="binding-data-to-windows-forms-controls"></a>Windows フォーム コントロールへのデータのバインド  
 オブジェクトを Windows フォーム コントロールにバインドするには、コントロールの `DataSource` プロパティをクエリ結果を含む <xref:System.Data.Services.Client.DataServiceCollection%601> クラスのインスタンスに設定します。  
  
> [!NOTE]
>  データ バインディングは、<xref:System.Collections.Specialized.INotifyCollectionChanged> インターフェイスおよび <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装することで変更イベントをリッスンしているコントロールでのみサポートされます。 コントロールがこの種類の変更通知をサポートしていない場合、基になる <xref:System.Data.Services.Client.DataServiceCollection%601> に対する変更はバインドされたコントロールに反映されません。  
  
 次の例では、<xref:System.Data.Services.Client.DataServiceCollection%601> を <xref:System.Windows.Forms.ComboBox> コントロールにバインドします。  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 使用すると、**サービス参照の追加**クライアント データ サービス クラス、データ ソースも作成されているプロジェクトを生成するためのダイアログは、生成されたに基づく<xref:System.Data.Services.Client.DataServiceContext>します。 このデータ ソースと UI 要素またはから項目をドラッグするだけで、データ サービスからデータを表示するコントロールを作成することができます、**データソース**デザイナーにウィンドウ。 これらの項目は、データ ソースにバインドされるアプリケーション UI の要素になります。 詳細については、「[方法 :プロジェクトのデータ ソースを使用してデータをバインド](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md)します。  
  
## <a name="binding-paged-data"></a>ページングされたデータのバインド  
 データ サービスは、1 つの応答メッセージで返されるクエリ データの量を制限するよう構成できます。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)します。 データ サービスによって応答データのページングが行われる場合、各応答には、結果の次のページを返すためのリンクが含まれます。 詳細については、次を参照してください。[遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)します。 この場合、次の例に示すように、<xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> プロパティから取得した URI を渡すことによって <xref:System.Data.Services.Client.DataServiceCollection%601> で <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> メソッドを呼び出してページを明示的に読み込む必要があります。  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 関連するオブジェクトは同様の方法で読み込まれます。 詳細については、「[方法 :Windows Presentation Foundation 要素にデータをバインド](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)します。  
  
## <a name="customizing-data-binding-behaviors"></a>データ バインディングの動作のカスタマイズ  
 <xref:System.Data.Services.Client.DataServiceCollection%601> クラスを使用すると、コレクションへの変更が行われたとき (オブジェクトが追加または削除されたときなど)、およびコレクション内のオブジェクトのプロパティに対して変更が行われたときに発生するイベントを先に取得できます。 データ バインディング イベントを変更して、次の制約を含む既定の動作をオーバーライドできます。  
  
- デリゲート内では検証は実行されません。  
  
- エンティティを追加すると関連エンティティが自動的に追加されます。  
  
- エンティティを削除しても関連エンティティは削除されません。  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> の新しいインスタンスを作成するとき、次のパラメーターを指定して、バインドされたオブジェクトが変更されたときに発生するイベントを処理するメソッドに対してデリゲートを定義できます。  
  
- `entityChanged` - バインドされたオブジェクトのプロパティが変更されたときに呼び出されるメソッド。 この <xref:System.Func%602> デリゲートは、<xref:System.Data.Services.Client.EntityChangedParams> オブジェクトを受け入れ、<xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> で <xref:System.Data.Services.Client.DataServiceContext> を呼び出す既定の動作を引き続き発生させるかどうかを示すブール値を返します。  
  
- `entityCollectionChanged` - バインディング コレクションに対してオブジェクトの追加または削除が行われたときに呼び出されるメソッド。 この <xref:System.Func%602> デリゲートは、<xref:System.Data.Services.Client.EntityCollectionChangedParams> オブジェクトを受け入れ、既定の動作 (<xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> での <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> アクションの <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> または <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> アクションの <xref:System.Data.Services.Client.DataServiceContext> 呼び出し) を引き続き発生させるかどうかを示すブール値を返します。  
  
> [!NOTE]
>  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、これらのデリゲートで実装したカスタムの動作を検証しません。  
  
 次の例では、<xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> アクションがカスタマイズされ、<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> および <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> メソッドが呼び出されて、削除された `Orders_Details` エンティティに属する `Orders` エンティティが削除されます。 親エンティティを削除しても依存エンティティは自動的に削除されないので、このカスタム アクションが実行されます。  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 詳細については、「[方法 :データ バインディングの動作をカスタマイズ](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md)します。  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> メソッドを使用して <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> からオブジェクトが削除されたときの既定の動作では、オブジェクトは <xref:System.Data.Services.Client.DataServiceContext> でも Deleted とマークされます。 この動作を変更するには、`entityCollectionChanged` イベントが発生すると呼び出される <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> パラメーター内のメソッドに対してデリゲートを指定できます。  
  
## <a name="data-binding-with-custom-client-data-classes"></a>カスタム クライアント データ クラスでのデータ バインディング  
 オブジェクトを <xref:System.Data.Services.Client.DataServiceCollection%601> に読み込むには、オブジェクト自身が <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを実装する必要があります。 データ サービスを使用するときに生成されるクライアント クラス、**サービス参照の追加** ダイアログ ボックスまたは[DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md)ツールは、このインターフェイスを実装します。 独自のクライアント データ クラスを提供する場合、データ バインディングに別の種類のコレクションを使用する必要があります。 オブジェクトが変更されると、データ バインド コントロール内のイベントを処理して、<xref:System.Data.Services.Client.DataServiceContext> クラスの次のメソッドを呼び出す必要があります。  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> - 新しいオブジェクトがコレクションに追加されたとき。  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> - オブジェクトがコレクションから削除されたとき。  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> - コレクション内のオブジェクトでプロパティが変更されたとき。  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> - オブジェクトが関連オブジェクトのコレクションに追加されたとき。  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> - オブジェクトが関連オブジェクトのコレクションに追加されたとき。  
  
 詳細については、次を参照してください。[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)します。  
  
## <a name="see-also"></a>関連項目

- [方法: クライアント データ サービス クラスを手動で生成します。](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [方法: データ サービス参照を追加します。](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
