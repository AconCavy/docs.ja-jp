---
title: '方法: カスタム アクティビティ デザイナーを作成する'
description: この記事では、任意のアクティビティを配置できるドロップゾーンを持つ Workflow Foundation カスタムアクティビティデザイナーを作成する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 2f3aade6-facc-44ef-9657-a407ef8b9b31
ms.openlocfilehash: 015efd1e482e2b531d28b9caec411c76116c9653
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419786"
---
# <a name="how-to-create-a-custom-activity-designer"></a><span data-ttu-id="8527d-103">方法: カスタム アクティビティ デザイナーを作成する</span><span class="sxs-lookup"><span data-stu-id="8527d-103">How to: Create a Custom Activity Designer</span></span>

<span data-ttu-id="8527d-104">カスタム アクティビティ デザイナーは、通常、関連付けられたアクティビティを他のアクティビティと組み合わせることができるように実装されます。他のアクティビティのデザイナーは、アクティビティと一緒にデザイン サーフェイスにドロップできます。</span><span class="sxs-lookup"><span data-stu-id="8527d-104">Custom activity designers are typically implemented so that their associated activities are composable with other activities whose designers can be dropped on to the design surface with them.</span></span> <span data-ttu-id="8527d-105">この機能を使用するには、カスタムアクティビティデザイナーが、任意のアクティビティを配置できる "ドロップゾーン" を提供する必要があります。また、デザインサーフェイスで結果として生成される要素のコレクションを管理する手段も必要です。</span><span class="sxs-lookup"><span data-stu-id="8527d-105">This functionality requires that a custom activity designer provide a "drop zone" where an arbitrary activity can be placed and also the means to manage the resulting collection of elements on the design surface.</span></span> <span data-ttu-id="8527d-106">ここでは、そのようなドロップ ゾーンを含むカスタム アクティビティ デザイナーを作成する方法と、デザイナー要素のコレクションを管理するために必要な編集機能を提供するカスタム アクティビティ デザイナーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8527d-106">This topic describes how to create a custom activity designer that contains such a drop zone and how to create a custom activity designer that provides that editing functionality needed to manage the collection of designer elements.</span></span>

<span data-ttu-id="8527d-107">カスタム アクティビティ デザイナーは、通常、<xref:System.Activities.Presentation.ActivityDesigner> を継承します。これは、特定のデザイナーを持たないアクティビティの既定の基本アクティビティ デザイナー型です。</span><span class="sxs-lookup"><span data-stu-id="8527d-107">Custom activity designers typically inherit from <xref:System.Activities.Presentation.ActivityDesigner> which is the default base activity designer type for any activities without a specific designer.</span></span> <span data-ttu-id="8527d-108">この型には、プロパティ グリッドと対話し、色やアイコンの管理などの基本的な側面を構成するデザイン時の機能があります。</span><span class="sxs-lookup"><span data-stu-id="8527d-108">This type provides the design-time experience of interacting with the property grid and configuring basic aspects such as managing colors and icons.</span></span>

<span data-ttu-id="8527d-109"><xref:System.Activities.Presentation.ActivityDesigner> では、カスタム アクティビティ デザイナーを開発しやすくする 2 つのヘルパー コントロール <xref:System.Activities.Presentation.WorkflowItemPresenter> と <xref:System.Activities.Presentation.WorkflowItemsPresenter> を使用します。</span><span class="sxs-lookup"><span data-stu-id="8527d-109"><xref:System.Activities.Presentation.ActivityDesigner> uses two helper controls, <xref:System.Activities.Presentation.WorkflowItemPresenter> and <xref:System.Activities.Presentation.WorkflowItemsPresenter> to make it easier to develop custom activity designers.</span></span> <span data-ttu-id="8527d-110">これらは、子要素のドラッグ アンド ドロップ、その子要素の削除、選択、追加などの一般的な機能を処理します。</span><span class="sxs-lookup"><span data-stu-id="8527d-110">They handle common functionality like dragging and dropping of child elements, deletion, selection, and addition of those child elements.</span></span> <span data-ttu-id="8527d-111">では、 <xref:System.Activities.Presentation.WorkflowItemPresenter> "ドロップゾーン" を提供する内の単一の子 UI 要素を使用できます。また、では、 <xref:System.Activities.Presentation.WorkflowItemsPresenter> 子要素の順序付け、移動、削除、追加などの追加機能を含む複数の ui 要素をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="8527d-111">The <xref:System.Activities.Presentation.WorkflowItemPresenter> allows a single child UI element inside, providing the "drop zone", it while the <xref:System.Activities.Presentation.WorkflowItemsPresenter> can provide support multiple UI elements, including additional functionality like the ordering, moving, deleting, and adding of child elements.</span></span>

<span data-ttu-id="8527d-112">カスタムアクティビティデザイナーの実装で強調表示する必要があるストーリーのもう1つの重要な部分は、WPF のデータバインディングを使用してビジュアルの編集をバインドする方法に関するもので、デザイナーでの編集内容のメモリに格納されているインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="8527d-112">The other key part of the story that needs highlighting in the implementation of a custom activity designer concerns the way in which the visual edits are bound using WPF data binding to the instance stored in memory of what we are editing in the designer.</span></span> <span data-ttu-id="8527d-113">これは、モデル アイテム ツリーによって実現されます。モデル アイテム ツリーは、変更通知やイベント (状態の変化など) の追跡を実現するためにも使用されます。</span><span class="sxs-lookup"><span data-stu-id="8527d-113">This is accomplished by the Model Item tree, which is also responsible for enabling change notification and the tracking of events like changes in states.</span></span>

<span data-ttu-id="8527d-114">ここでは、次の 2 つの手順の概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="8527d-114">This topic outlines two procedures.</span></span>

1. <span data-ttu-id="8527d-115">1 つ目の手順では、他のアクティビティを受け取るドロップ ゾーンを提供する <xref:System.Activities.Presentation.WorkflowItemPresenter> を使用してカスタム アクティビティ デザイナーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8527d-115">The first procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemPresenter> that provides the drop zone that receives other activities.</span></span> <span data-ttu-id="8527d-116">この手順は、「[カスタム複合デザイナー-Workflow Item プレゼンター](./samples/custom-composite-designers-workflow-item-presenter.md) sample」に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8527d-116">This procedure is based on the [Custom Composite Designers - Workflow Item Presenter](./samples/custom-composite-designers-workflow-item-presenter.md) sample.</span></span>

2. <span data-ttu-id="8527d-117">2 つ目の手順では、含まれている要素のコレクションを編集するために必要な機能を提供する <xref:System.Activities.Presentation.WorkflowItemsPresenter> を使用してカスタム アクティビティ デザイナーを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="8527d-117">The second procedure describes how to create a custom activity designer with a <xref:System.Activities.Presentation.WorkflowItemsPresenter> that provides the functionality needed to edit of a collection of contained elements.</span></span> <span data-ttu-id="8527d-118">この手順は、「[カスタム複合デザイナー-Workflow Items プレゼンター](./samples/custom-composite-designers-workflow-items-presenter.md) sample」に基づいています。</span><span class="sxs-lookup"><span data-stu-id="8527d-118">This procedure is based on the [Custom Composite Designers - Workflow Items Presenter](./samples/custom-composite-designers-workflow-items-presenter.md) sample.</span></span>

## <a name="to-create-a-custom-activity-designer-with-a-drop-zone-using-workflowitempresenter"></a><span data-ttu-id="8527d-119">WorkflowItemPresenter を使用してドロップ ゾーンを含むカスタム アクティビティ デザイナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="8527d-119">To create a custom activity designer with a drop zone using WorkflowItemPresenter</span></span>

1. <span data-ttu-id="8527d-120">Visual Studio 2010 を起動します。</span><span class="sxs-lookup"><span data-stu-id="8527d-120">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="8527d-121">[**ファイル**] メニューの [**新規作成**] をポイントし、[**プロジェクト**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8527d-121">On the **File** menu, point to **New**, and then select **Project…**.</span></span>

     <span data-ttu-id="8527d-122">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8527d-122">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="8527d-123">[**インストールされたテンプレート**] ペインで、任意の言語カテゴリから [ **Windows** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-123">In the **Installed Templates** pane, select **Windows** from your preferred language category.</span></span>

4. <span data-ttu-id="8527d-124">[**テンプレート**] ペインで、[ **WPF アプリケーション**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-124">In the **Templates** pane, select **WPF Application**.</span></span>

5. <span data-ttu-id="8527d-125">[**名前**] ボックスに「」と入力し `UsingWorkflowItemPresenter` ます。</span><span class="sxs-lookup"><span data-stu-id="8527d-125">In the **Name** box, enter `UsingWorkflowItemPresenter`.</span></span>

6. <span data-ttu-id="8527d-126">[**場所**] ボックスに、プロジェクトを保存するディレクトリを入力するか、[**参照**] をクリックして移動します。</span><span class="sxs-lookup"><span data-stu-id="8527d-126">In the **Location** box, enter the directory in which you want to save your project, or click **Browse** to navigate to it.</span></span>

7. <span data-ttu-id="8527d-127">[**ソリューション**] ボックスで、既定値をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="8527d-127">In the **Solution** box, accept the default value.</span></span>

8. <span data-ttu-id="8527d-128">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8527d-128">Click **OK**.</span></span>

9. <span data-ttu-id="8527d-129">**ソリューションエクスプローラー**で*mainwindows .xaml*ファイルを右クリックし、[**削除**] を選択し、[ **Microsoft Visual Studio** ] ダイアログボックスで [ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8527d-129">Right-click the *MainWindows.xaml* file in the **Solution Explorer**, select **Delete** and confirm **OK** in the **Microsoft Visual Studio** dialog box.</span></span>

10. <span data-ttu-id="8527d-130">**ソリューションエクスプローラー**で [の Workflowitemプレゼンター] プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-130">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="8527d-131">[**新しい項目の追加**] ダイアログボックスを表示するには、左側の [**インストールされているテンプレート**] セクションで [ **WPF** ] カテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-131">to bring up the **Add New Item** dialog and select the **WPF** category from the **Installed Templates** section on the left.</span></span>

11. <span data-ttu-id="8527d-132">[**ウィンドウ (WPF)]** テンプレートを選択し、という名前 `RehostingWFDesigner` を指定して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8527d-132">Select the  **Window (WPF)** template, name it `RehostingWFDesigner`, and click **Add**.</span></span>

12. <span data-ttu-id="8527d-133">*Rehostingwfdesigner.xaml*ファイルを開き、次のコードを貼り付けて、アプリケーションの UI を定義します。</span><span class="sxs-lookup"><span data-stu-id="8527d-133">Open the *RehostingWFDesigner.xaml* file and paste the following code into it to define the UI for the application:</span></span>

    ```xaml
    <Window x:Class=" UsingWorkflowItemPresenter.RehostingWFDesigner"
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
            xmlns:sapt="clr-namespace:System.Activities.Presentation.Toolbox;assembly=System.Activities.Presentation"
            xmlns:sys="clr-namespace:System;assembly=mscorlib"
            Title="Window1" Height="600" Width="900">
        <Window.Resources>
            <sys:String x:Key="AssemblyName">System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35</sys:String>
        </Window.Resources>
        <Grid>
            <Grid.ColumnDefinitions>
                <ColumnDefinition Width="2*"/>
                <ColumnDefinition Width="7*"/>
                <ColumnDefinition Width="3*"/>
            </Grid.ColumnDefinitions>
            <Border Grid.Column="0">
                <sapt:ToolboxControl Name="Toolbox">
                    <sapt:ToolboxCategory CategoryName="Basic">
                        <sapt:ToolboxItemWrapper AssemblyName="{StaticResource AssemblyName}" >
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.Sequence
                            </sapt:ToolboxItemWrapper.ToolName>
                           </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.WriteLine
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.If
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                        <sapt:ToolboxItemWrapper  AssemblyName="{StaticResource AssemblyName}">
                            <sapt:ToolboxItemWrapper.ToolName>
                                System.Activities.Statements.While
                            </sapt:ToolboxItemWrapper.ToolName>

                        </sapt:ToolboxItemWrapper>
                    </sapt:ToolboxCategory>
                </sapt:ToolboxControl>
            </Border>
            <Border Grid.Column="1" Name="DesignerBorder"/>
            <Border Grid.Column="2" Name="PropertyBorder"/>
        </Grid>
    </Window>
    ```

13. <span data-ttu-id="8527d-134">アクティビティ デザイナーをアクティビティ タイプと関連付けるには、そのアクティビティ デザイナーをメタデータ ストアを使用して登録する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8527d-134">To associate an activity designer with an activity type, you must register that activity designer with the metadata store.</span></span> <span data-ttu-id="8527d-135">この操作を行うには、`RegisterMetadata` メソッドを `RehostingWFDesigner` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="8527d-135">To do this, add the `RegisterMetadata` method to the `RehostingWFDesigner` class.</span></span> <span data-ttu-id="8527d-136">`RegisterMetadata` メソッドのスコープで <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> オブジェクトを作成し、<xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> メソッドを呼び出して属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="8527d-136">Within the scope of the  `RegisterMetadata` method, create an <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder> object and call the <xref:System.Activities.Presentation.Metadata.AttributeTableBuilder.AddCustomAttributes%2A> method to add the attributes to it.</span></span> <span data-ttu-id="8527d-137"><xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> メソッドを呼び出して <xref:System.Activities.Presentation.Metadata.AttributeTable> をメタデータ ストアに追加します。</span><span class="sxs-lookup"><span data-stu-id="8527d-137">Call the <xref:System.Activities.Presentation.Metadata.MetadataStore.AddAttributeTable%2A> method to add the <xref:System.Activities.Presentation.Metadata.AttributeTable> to the metadata store.</span></span> <span data-ttu-id="8527d-138">次のコードには、デザイナーの再ホスト ロジックが含まれています </span><span class="sxs-lookup"><span data-stu-id="8527d-138">The following code contains the rehosting logic for the designer.</span></span> <span data-ttu-id="8527d-139">(メタデータの登録、`SimpleNativeActivity` のツールボックスへの追加、およびワークフローの作成)。</span><span class="sxs-lookup"><span data-stu-id="8527d-139">It registers the metadata, puts the `SimpleNativeActivity` into the toolbox, and creates the workflow.</span></span> <span data-ttu-id="8527d-140">このコードを*RehostingWFDesigner.xaml.cs*ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="8527d-140">Put this code into the *RehostingWFDesigner.xaml.cs* file.</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Presentation.Toolbox;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespace UsingWorkflowItemPresenter
    {
        // Interaction logic for RehostingWFDesigner.xaml
        public partial class RehostingWFDesigner
        {
            public RehostingWFDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();
                // Add custom activity to toolbox.
                Toolbox.Categories.Add(new ToolboxCategory("Custom activities"));
                Toolbox.Categories[1].Add(new ToolboxItemWrapper(typeof(SimpleNativeActivity)));

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(SimpleNativeActivity), new DesignerAttribute(typeof(SimpleNativeDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

14. <span data-ttu-id="8527d-141">ソリューションエクスプローラーで参照ディレクトリを右クリックし、[**参照の追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-141">Right-click the References directory in Solution Explorer and select **Add Reference …**</span></span> <span data-ttu-id="8527d-142">を選択すると、[**参照の追加**] ダイアログボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="8527d-142">to bring up the **Add Reference** dialog.</span></span>

15. <span data-ttu-id="8527d-143">[ **.Net** ] タブをクリックし、「system.string」と**いう名前の**アセンブリを見つけて選択し、[ **OK**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8527d-143">Click the **.NET** tab, locate the assembly named **System.Activities.Core.Presentation**, select it and click **OK**.</span></span>

16. <span data-ttu-id="8527d-144">同じ手順で次のアセンブリへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="8527d-144">Using the same procedure, add references to the following assemblies:</span></span>

    1. <span data-ttu-id="8527d-145">System.Data.DataSetExtensions.dll</span><span class="sxs-lookup"><span data-stu-id="8527d-145">System.Data.DataSetExtensions.dll</span></span>

    2. <span data-ttu-id="8527d-146">System.Activities.Presentation.dll</span><span class="sxs-lookup"><span data-stu-id="8527d-146">System.Activities.Presentation.dll</span></span>

    3. <span data-ttu-id="8527d-147">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="8527d-147">System.ServiceModel.Activities.dll</span></span>

17. <span data-ttu-id="8527d-148">*App.xaml*ファイルを開き、startupuri の値を "rehostingwfdesigner.xaml" に変更します。</span><span class="sxs-lookup"><span data-stu-id="8527d-148">Open the *App.xaml* file and change the value of the StartUpUri to "RehostingWFDesigner.xaml".</span></span>

18. <span data-ttu-id="8527d-149">**ソリューションエクスプローラー**で [の Workflowitemプレゼンター] プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-149">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="8527d-150">[**新しい項目の追加**] ダイアログを表示するには、左側の [**インストールされているテンプレート**] セクションで [**ワークフロー** ] カテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-150">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

19. <span data-ttu-id="8527d-151">**アクティビティデザイナー**テンプレートを選択し、という名前 `SimpleNativeDesigner` を指定して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8527d-151">Select the **Activity Designer** template, name it `SimpleNativeDesigner`, and click **Add**.</span></span>

20. <span data-ttu-id="8527d-152">*SimpleNativeDesigner*ファイルを開き、次のコードを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="8527d-152">Open the *SimpleNativeDesigner.xaml* file and paste the following code into it.</span></span> <span data-ttu-id="8527d-153">このコードは、<xref:System.Activities.Presentation.ActivityDesigner> をルート要素として使用し、子の型を複合アクティビティ デザイナーに表示できるように、バインディングを使用してデザイナーに <xref:System.Activities.Presentation.WorkflowItemPresenter> を統合する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="8527d-153">Note this code uses <xref:System.Activities.Presentation.ActivityDesigner> as your root element and shows how binding is used to integrate <xref:System.Activities.Presentation.WorkflowItemPresenter> into your designer so a child type can be displayed in your composite activity designer.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8527d-154"><xref:System.Activities.Presentation.ActivityDesigner> のスキーマでは、カスタム アクティビティ デザイナー定義に 1 つの子要素のみを追加できます。ただし、この要素は、`StackPanel`、`Grid` などの複合 UI 要素の可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8527d-154">The schema for <xref:System.Activities.Presentation.ActivityDesigner> allows the addition of only one child element to your custom activity designer definition; however, this element could be a `StackPanel`, `Grid`, or some other composite UI element.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemPresenter.SimpleNativeDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <StackPanel>
                    <TextBlock>This is the collapsed view</TextBlock>
                </StackPanel>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock>Custom Text</TextBlock>
                    <sap:WorkflowItemPresenter Item="{Binding Path=ModelItem.Body, Mode=TwoWay}"
                                            HintText="Please drop an activity here" />
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}" />
        </Grid>
    </sap:ActivityDesigner>
    ```

21. <span data-ttu-id="8527d-155">**ソリューションエクスプローラー**で [の Workflowitemプレゼンター] プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-155">Right-click the UsingWorkflowItemPresenter project in **Solution Explorer**, select **Add**, then **New Item…**</span></span> <span data-ttu-id="8527d-156">[**新しい項目の追加**] ダイアログを表示するには、左側の [**インストールされているテンプレート**] セクションで [**ワークフロー** ] カテゴリを選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-156">to bring up the **Add New Item** dialog and select the **Workflow** category form the **Installed Templates** section on the left.</span></span>

22. <span data-ttu-id="8527d-157">**Code アクティビティ**テンプレートを選択し、という名前 `SimpleNativeActivity` を指定して、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="8527d-157">Select the  **Code Activity** template, name it `SimpleNativeActivity`, and click **Add**.</span></span>

23. <span data-ttu-id="8527d-158">`SimpleNativeActivity` *SimpleNativeActivity.cs*ファイルに次のコードを入力して、クラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="8527d-158">Implement the `SimpleNativeActivity` class by entering the following code into the *SimpleNativeActivity.cs* file:</span></span>

    ```csharp
    using System.Activities;

    namespace UsingWorkflowItemPresenter
    {
        public sealed class SimpleNativeActivity : NativeActivity
        {
            // this property contains an activity that will be scheduled in the execute method
            // the WorkflowItemPresenter in the designer is bound to this to enable editing
            // of the value
            public Activity Body { get; set; }

            protected override void CacheMetadata(NativeActivityMetadata metadata)
            {
               metadata.AddChild(Body);
               base.CacheMetadata(metadata);

            }

            protected override void Execute(NativeActivityContext context)
            {
                context.ScheduleActivity(Body);
            }
        }
    }
    ```

24. <span data-ttu-id="8527d-159">[**ビルド**] メニューの [**ソリューションのビルド**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="8527d-159">Select **Build Solution** from the **Build** menu.</span></span>

25. <span data-ttu-id="8527d-160">[**デバッグ**] メニューの [**デバッグなしで開始**] をクリックして、再ホストされたカスタムデザインウィンドウを開きます。</span><span class="sxs-lookup"><span data-stu-id="8527d-160">Select **Start Without Debugging** from the **Debug** menu to open the rehosted custom design window.</span></span>

### <a name="to-create-a-custom-activity-designer-using-workflowitemspresenter"></a><span data-ttu-id="8527d-161">WorkflowItemsPresenter を使用してカスタム アクティビティ デザイナーを作成するには</span><span class="sxs-lookup"><span data-stu-id="8527d-161">To create a custom activity designer using WorkflowItemsPresenter</span></span>

1. <span data-ttu-id="8527d-162">2番目のカスタムアクティビティデザイナーの手順は、最初にいくつかの変更を加えたものです。最初に、2つ目のアプリケーションに名前を付け `UsingWorkflowItemsPresenter` ます。</span><span class="sxs-lookup"><span data-stu-id="8527d-162">The procedure for the second custom activity designer is the parallels the first with a few modifications, the first of which is to name the second application `UsingWorkflowItemsPresenter`.</span></span> <span data-ttu-id="8527d-163">また、このアプリケーションでは新しいカスタム アクティビティを定義しません。</span><span class="sxs-lookup"><span data-stu-id="8527d-163">Also this application does not define a new custom activity.</span></span>

2. <span data-ttu-id="8527d-164">キーの違いは、 *Customparalleldesigner .xaml*および*RehostingWFDesigner.xaml.cs*ファイルに含まれています。</span><span class="sxs-lookup"><span data-stu-id="8527d-164">Key differences are contained in the *CustomParallelDesigner.xaml* and *RehostingWFDesigner.xaml.cs* files.</span></span> <span data-ttu-id="8527d-165">次に、UI を定義する*Customparalleldesigner .xaml*ファイルのコードを示します。</span><span class="sxs-lookup"><span data-stu-id="8527d-165">Here is the code from the *CustomParallelDesigner.xaml* file that defines the UI:</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class=" UsingWorkflowItemsPresenter.CustomParallelDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">
        <sap:ActivityDesigner.Resources>
            <DataTemplate x:Key="Collapsed">
                <TextBlock>This is the Collapsed View</TextBlock>
            </DataTemplate>
            <DataTemplate x:Key="Expanded">
                <StackPanel>
                    <TextBlock HorizontalAlignment="Center">This is the</TextBlock>
                    <TextBlock HorizontalAlignment="Center">extended view</TextBlock>
                    <sap:WorkflowItemsPresenter HintText="Drop Activities Here"
                                        Items="{Binding Path=ModelItem.Branches}">
                        <sap:WorkflowItemsPresenter.SpacerTemplate>
                            <DataTemplate>
                                <Ellipse Width="10" Height="10" Fill="Black"/>
                            </DataTemplate>
                        </sap:WorkflowItemsPresenter.SpacerTemplate>
                        <sap:WorkflowItemsPresenter.ItemsPanel>
                            <ItemsPanelTemplate>
                                <StackPanel Orientation="Horizontal"/>
                            </ItemsPanelTemplate>
                        </sap:WorkflowItemsPresenter.ItemsPanel>
                    </sap:WorkflowItemsPresenter>
                </StackPanel>
            </DataTemplate>
            <Style x:Key="ExpandOrCollapsedStyle" TargetType="{x:Type ContentPresenter}">
                <Setter Property="ContentTemplate" Value="{DynamicResource Collapsed}"/>
                <Style.Triggers>
                    <DataTrigger Binding="{Binding Path=ShowExpanded}" Value="true">
                        <Setter Property="ContentTemplate" Value="{DynamicResource Expanded}"/>
                    </DataTrigger>
                </Style.Triggers>
            </Style>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ContentPresenter Style="{DynamicResource ExpandOrCollapsedStyle}" Content="{Binding}"/>
        </Grid>
    </sap:ActivityDesigner>
    ```

3. <span data-ttu-id="8527d-166">再ホストロジックを提供する*RehostingWFDesigner.xaml.cs*ファイルのコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="8527d-166">Here is the code from the *RehostingWFDesigner.xaml.cs* file that provides the rehosting logic:</span></span>

    ```csharp
    using System;
    using System.Activities.Core.Presentation;
    using System.Activities.Presentation;
    using System.Activities.Presentation.Metadata;
    using System.Activities.Statements;
    using System.ComponentModel;
    using System.Windows;

    namespaceUsingWorkflowItemsPresenter
    {
        public partial class RehostingWfDesigner : Window
        {
            public RehostingWfDesigner()
            {
                InitializeComponent();
            }

            protected override void OnInitialized(EventArgs e)
            {
                base.OnInitialized(e);
                // Register metadata.
                (new DesignerMetadata()).Register();
                RegisterCustomMetadata();

                // Create the workflow designer.
                var wd = new WorkflowDesigner();
                wd.Load(new Sequence());
                DesignerBorder.Child = wd.View;
                PropertyBorder.Child = wd.PropertyInspectorView;

            }

            void RegisterCustomMetadata()
            {
                var builder = new AttributeTableBuilder();
                builder.AddCustomAttributes(typeof(Parallel), new DesignerAttribute(typeof(CustomParallelDesigner)));
                MetadataStore.AddAttributeTable(builder.CreateTable());
            }
        }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="8527d-167">関連項目</span><span class="sxs-lookup"><span data-stu-id="8527d-167">See also</span></span>

- <xref:System.Activities.Presentation.ActivityDesigner>
- <xref:System.Activities.Presentation.WorkflowItemPresenter>
- <xref:System.Activities.Presentation.WorkflowItemsPresenter>
- <xref:System.Activities.Presentation.WorkflowViewElement>
- <xref:System.Activities.Presentation.Model.ModelItem>
- [<span data-ttu-id="8527d-168">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="8527d-168">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
