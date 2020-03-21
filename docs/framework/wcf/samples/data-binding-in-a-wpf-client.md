---
title: Windows Presentation Foundation クライアントでのデータ バインディング
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 7bc389056872841905336dcf658a07223906bf82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183821"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="d227b-102">Windows Presentation Foundation クライアントでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="d227b-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="d227b-103">このサンプルでは、Windows Presentation Foundation (WPF) クライアントでのデータ バインディングの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d227b-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="d227b-104">このサンプルでは、クライアントに返すアルバムの配列をランダムに生成する Windows コミュニケーション ファンデーション (WCF) サービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="d227b-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="d227b-105">各アルバムには、名前、価格、およびアルバム トラックの一覧が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d227b-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="d227b-106">アルバム トラックには、名前と継続時間が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d227b-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="d227b-107">サービスによって返される情報は、Windows プレゼンテーション ファンデーション (WPF) クライアントによって提供されるユーザー インターフェイス (UI) に自動的にバインドされます。</span><span class="sxs-lookup"><span data-stu-id="d227b-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d227b-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d227b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d227b-109">データ バインディングでは、データ ソースを自動的に UI にバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="d227b-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="d227b-110">これによってプログラミング モデルが簡素化されます。プログラムを使って、各 UI 要素をデータ オブジェクトまたはデータ オブジェクトの配列からのデータで更新する必要がないためです。</span><span class="sxs-lookup"><span data-stu-id="d227b-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="d227b-111">単一の UI 要素にオブジェクトをバインドしたり、複数の入力情報を取得する `ListBox` などのコントロールに配列をバインドしたりできます。</span><span class="sxs-lookup"><span data-stu-id="d227b-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="d227b-112">データを UI 要素の `DataContext` にバインドする方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="d227b-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="d227b-113">前のサンプルでは、`DataContext` という `grid` レイアウト要素の `myPanel` が、`GetAlbumList` メソッドによって返されるデータに設定されます。</span><span class="sxs-lookup"><span data-stu-id="d227b-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="d227b-114">`DataContext` では、バインディングに使用されるデータ ソースやその他のバインディング特性 (パスなど) に関する情報を、要素が親要素から継承できます。</span><span class="sxs-lookup"><span data-stu-id="d227b-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="d227b-115">このコード行は、サーバー上のデータが更新されるたびに実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d227b-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="d227b-116">たとえば、ウィンドウが初期化されたり新しいアルバムが追加されたりするときに実行します。</span><span class="sxs-lookup"><span data-stu-id="d227b-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="d227b-117">次の XAML サンプル コードでは、`ListBox` に `ItemsSource="{Binding }"` を指定します。</span><span class="sxs-lookup"><span data-stu-id="d227b-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="d227b-118">これは、最上位の UI 要素にバインドされるデータは、このコントロール (アルバムの配列) にもバインドされることを示します。</span><span class="sxs-lookup"><span data-stu-id="d227b-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="d227b-119">また、`ItemTemplate="{StaticResource AlbumStyle}"` では、データ テンプレートが `ListBox` の各項目で使用されるように指定されます。</span><span class="sxs-lookup"><span data-stu-id="d227b-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="d227b-120">データの書式設定方法を指定するデータ テンプレートを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="d227b-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="d227b-121">こうしたデータ テンプレートは、アプリケーション内の他の UI 要素で再使用できます。この利点は、データ テンプレートを 1 つの場所で定義および維持できることです。</span><span class="sxs-lookup"><span data-stu-id="d227b-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="d227b-122">`AlbumStyle` データ テンプレートでは、2 つの並列の `TextBlock` を伴ってグリッドが配置されます。</span><span class="sxs-lookup"><span data-stu-id="d227b-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="d227b-123">このうちの 1 つはアルバムの名前を指定し、もう 1 つはアルバムのトラック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="d227b-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="d227b-124">2 つ目の `ListBox` を作成する XAML コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d227b-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="d227b-125">このコードは、`ItemsSource` のパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d227b-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="d227b-126">これは、このコントロールにバインドされるデータは最上位のデータではなく、`Tracks` という最上位データのプロパティであることを示します。</span><span class="sxs-lookup"><span data-stu-id="d227b-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="d227b-127">このプロパティは、アルバムに含まれるトラックの配列を表します。</span><span class="sxs-lookup"><span data-stu-id="d227b-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="d227b-128">さらに、`DataTemplate` という別の `TrackStyle` が指定されています。</span><span class="sxs-lookup"><span data-stu-id="d227b-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="d227b-129">`TrackStyle` テンプレートのレイアウトは `AlbumStyle` テンプレートのレイアウトに似ていますが、`TextBlock` は別々のプロパティにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="d227b-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="d227b-130">これは、2 つのテンプレートが異なるデータ オブジェクトで使用されるためです。</span><span class="sxs-lookup"><span data-stu-id="d227b-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d227b-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="d227b-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="d227b-132">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d227b-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="d227b-133">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="d227b-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="d227b-134">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="d227b-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d227b-135">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d227b-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d227b-136">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d227b-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d227b-137">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="d227b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d227b-138">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d227b-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
