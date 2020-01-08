---
title: カスタム複合デザイナー - Workflow Items Presenter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 70055c4b-1173-47a3-be80-b5bce6f59e9a
ms.openlocfilehash: 081dce85946fab85cff474508c46770c762b9e76
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75338721"
---
# <a name="custom-composite-designers---workflow-items-presenter"></a><span data-ttu-id="a4636-102">カスタム複合デザイナー - Workflow Items Presenter</span><span class="sxs-lookup"><span data-stu-id="a4636-102">Custom Composite Designers - Workflow Items Presenter</span></span>

<span data-ttu-id="a4636-103"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> は、格納されている要素のコレクションを編集できる、WF デザイナー プログラミング モデル内の主要な型です。</span><span class="sxs-lookup"><span data-stu-id="a4636-103">The <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> is a key type in the WF designer programming model that allows for the editing of a collection of contained elements.</span></span> <span data-ttu-id="a4636-104">このサンプルでは、このような編集可能なコレクションを表示するアクティビティ デザイナーの構築方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a4636-104">This sample shows how to build an activity designer that surfaces such an editable collection.</span></span>

<span data-ttu-id="a4636-105">このサンプルでは、次の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a4636-105">This sample demonstrates:</span></span>

- <span data-ttu-id="a4636-106"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> を使用したカスタム アクティビティ デザイナーの作成</span><span class="sxs-lookup"><span data-stu-id="a4636-106">Creating a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="a4636-107">"折りたたまれた" ビューと "展開済み" ビューを使用してアクティビティデザイナーを作成する。</span><span class="sxs-lookup"><span data-stu-id="a4636-107">Creating an activity designer with a "collapsed" and "expanded" view.</span></span>

- <span data-ttu-id="a4636-108">再ホストされたアプリケーションでの既定のデザイナーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="a4636-108">Overriding a default designer in a rehosted application.</span></span>

## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="a4636-109">サンプルをセットアップ、ビルド、および実行する</span><span class="sxs-lookup"><span data-stu-id="a4636-109">Set up, build, and run the sample</span></span>

1. <span data-ttu-id="a4636-110">または Visual Studio 2010 の Visual Basic 用の UsingWorkflowItemsPresenter サンプルソリューションを開きます。 C#</span><span class="sxs-lookup"><span data-stu-id="a4636-110">Open the **UsingWorkflowItemsPresenter.sln** sample solution for C# or for Visual Basic in Visual Studio 2010.</span></span>

2. <span data-ttu-id="a4636-111">ソリューションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="a4636-111">Build and run the solution.</span></span>

   <span data-ttu-id="a4636-112">再ホストされたワークフローデザイナーアプリケーションが開き、キャンバスにアクティビティをドラッグできるようになります。</span><span class="sxs-lookup"><span data-stu-id="a4636-112">A rehosted workflow designer application opens, and you can drag activities onto the canvas.</span></span>

## <a name="sample-highlights"></a><span data-ttu-id="a4636-113">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="a4636-113">Sample Highlights</span></span>

<span data-ttu-id="a4636-114">このサンプルのコードには、次の内容が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a4636-114">The code for this sample shows the following:</span></span>

- <span data-ttu-id="a4636-115">デザイナーをビルドするアクティビティは `Parallel` です。</span><span class="sxs-lookup"><span data-stu-id="a4636-115">The activity a designer is built for:  `Parallel`</span></span>

- <span data-ttu-id="a4636-116"><xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType> を使用してカスタム アクティビティ デザイナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4636-116">The creation of a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a4636-117">次の点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a4636-117">A few things to point out:</span></span>

  - <span data-ttu-id="a4636-118">`ModelItem.Branches` にバインドする WPF のデータ バインディングの使用に注意してください。</span><span class="sxs-lookup"><span data-stu-id="a4636-118">Note the use of WPF data binding to bind to `ModelItem.Branches`.</span></span> <span data-ttu-id="a4636-119">`ModelItem` は、デザイナーが使用されている、基になるオブジェクト (この例では `WorkflowElementDesigner`) を参照する `Parallel` のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a4636-119">`ModelItem` is the property on `WorkflowElementDesigner` that refers to the underlying object the designer is being used for, in this case, our `Parallel`.</span></span>

  - <span data-ttu-id="a4636-120"><xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> は、コレクション内の個々の項目間にビジュアル表示を配置するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4636-120">The <xref:System.Activities.Presentation.WorkflowItemsPresenter.SpacerTemplate?displayProperty=nameWithType> can be used to put a visual to display between the individual items in the collection.</span></span>

  - <span data-ttu-id="a4636-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> は、コレクション内の項目のレイアウトを決定するために提供できるテンプレートです。</span><span class="sxs-lookup"><span data-stu-id="a4636-121"><xref:System.Activities.Presentation.WorkflowItemsPresenter.ItemsPanel?displayProperty=nameWithType> is a template that can be provided to determine the layout of the items in the collection.</span></span> <span data-ttu-id="a4636-122">この例では、水平方向のスタック パネルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4636-122">In this case, a horizontal stack panel is used.</span></span>

  <span data-ttu-id="a4636-123">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a4636-123">This following example code shows this.</span></span>

  ```xaml
  <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                Items="{Binding Path=ModelItem.Branches}">
      <sad:WorkflowItemsPresenter.SpacerTemplate>
        <DataTemplate>
          <Ellipse Width="10" Height="10" Fill="Black"/>
        </DataTemplate>
      </sad:WorkflowItemsPresenter.SpacerTemplate>
      <sad:WorkflowItemsPresenter.ItemsPanel>
        <ItemsPanelTemplate>
          <StackPanel Orientation="Horizontal"/>
        </ItemsPanelTemplate>
      </sad:WorkflowItemsPresenter.ItemsPanel>
    </sad:WorkflowItemsPresenter>
  ```

- <span data-ttu-id="a4636-124">`DesignerAttribute` の `Parallel` 型への関連付けを実行し、報告された属性を出力します。</span><span class="sxs-lookup"><span data-stu-id="a4636-124">Perform an association of the `DesignerAttribute` to the `Parallel` type and then output the attributes reported.</span></span>

  - <span data-ttu-id="a4636-125">最初に、すべての既定のデザイナーを登録します。</span><span class="sxs-lookup"><span data-stu-id="a4636-125">First, register all of the default designers.</span></span>

    <span data-ttu-id="a4636-126">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a4636-126">The following is the code example.</span></span>

    ```csharp
    // register metadata
    (new DesignerMetadata()).Register();
    RegisterCustomMetadata();
    ```

    ```vb
    ' register metadata
    Dim metadata = New DesignerMetadata()
    metadata.Register()
    ' register custom metadata
    RegisterCustomMetadata()
    ```

  - <span data-ttu-id="a4636-127">次に、`RegisterCustomMetadata` メソッドで parallel をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="a4636-127">Then, override the parallel in `RegisterCustomMetadata` method.</span></span>

    <span data-ttu-id="a4636-128">次に、C# と Visual Basic のコード例をそれぞれ示します。</span><span class="sxs-lookup"><span data-stu-id="a4636-128">The following code shows this in C# and Visual Basic.</span></span>

    ```csharp
    void RegisterCustomMetadata()
    {
          AttributeTableBuilder builder = new AttributeTableBuilder();
          builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
          MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

    ```vb
    Sub RegisterCustomMetadata()
       Dim builder As New AttributeTableBuilder()
       builder.AddCustomAttributes(GetType(Parallel), New DesignerAttribute(GetType(CustomParallelDesigner)))
       MetadataStore.AddAttributeTable(builder.CreateTable())
    End Sub
    ```

- <span data-ttu-id="a4636-129">最後に、さまざまなデータ テンプレートとトリガーを使用して、`IsRootDesigner` プロパティに基づいて適切なテンプレートを選択していることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="a4636-129">Finally, note the use of differing data templates and triggers to select the appropriate template based on the `IsRootDesigner` property.</span></span>

  <span data-ttu-id="a4636-130">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a4636-130">The following is the code example.</span></span>

  ```xaml
  <sad:ActivityDesigner x:Class="Microsoft.Samples.CustomParallelDesigner"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:sad="clr-namespace:System.Activities.Design;assembly=System.Activities.Design"
      xmlns:sadv="clr-namespace:System.Activities.Design.View;assembly=System.Activities.Design">
    <sad:ActivityDesigner.Resources>
      <DataTemplate x:Key="Expanded">
        <StackPanel>
          <TextBlock>This is the Expanded View</TextBlock>
          <sad:WorkflowItemsPresenter HintText="Drop Activities Here"
                                      Items="{Binding Path=ModelItem.Branches}">
            <sad:WorkflowItemsPresenter.SpacerTemplate>
              <DataTemplate>
                <Ellipse Width="10" Height="10" Fill="Black"/>
              </DataTemplate>
            </sad:WorkflowItemsPresenter.SpacerTemplate>
            <sad:WorkflowItemsPresenter.ItemsPanel>
              <ItemsPanelTemplate>
                <StackPanel Orientation="Horizontal"/>
              </ItemsPanelTemplate>
            </sad:WorkflowItemsPresenter.ItemsPanel>
          </sad:WorkflowItemsPresenter>
        </StackPanel>
      </DataTemplate>
      <DataTemplate x:Key="Collapsed">
        <TextBlock>This is the Collapsed View</TextBlock>
      </DataTemplate>
      <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
        <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
        <Style.Triggers>
          <DataTrigger Binding="{Binding Path=IsRootDesigner}" Value="true">
            <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
          </DataTrigger>
        </Style.Triggers>
      </Style>
    </sad: ActivityDesigner.Resources>
    <Grid>
      <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
    </Grid>
  </sad: ActivityDesigner>
  ```

> [!IMPORTANT]
> <span data-ttu-id="a4636-131">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a4636-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a4636-132">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a4636-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="a4636-133">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459)にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) と [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a4636-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a4636-134">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a4636-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\WorkflowItemsPresenter`

## <a name="see-also"></a><span data-ttu-id="a4636-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4636-135">See also</span></span>

- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- [<span data-ttu-id="a4636-136">ワークフロー デザイナーを使用したアプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="a4636-136">Developing Applications with the Workflow Designer</span></span>](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
