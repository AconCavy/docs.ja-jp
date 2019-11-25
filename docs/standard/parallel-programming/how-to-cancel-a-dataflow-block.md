---
title: '方法: データフロー ブロックをキャンセルする'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
ms.openlocfilehash: aa175d95f27fcbf28c3f3da3eaa7b8f7988681e1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140096"
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="b2546-102">方法: データフロー ブロックをキャンセルする</span><span class="sxs-lookup"><span data-stu-id="b2546-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="b2546-103">このドキュメントでは、アプリケーションでキャンセルを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b2546-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="b2546-104">この例では、Windows フォームを使用して、データフロー パイプラインで作業項目がアクティブである場所と、キャンセルの影響を示します。</span><span class="sxs-lookup"><span data-stu-id="b2546-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="b2546-105">Windows フォーム アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b2546-105">To Create the Windows Forms Application</span></span>  
  
1. <span data-ttu-id="b2546-106">C# または Visual Basic の **Windows フォーム アプリケーション** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2546-106">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="b2546-107">以降の手順では、プロジェクトの名前は `CancellationWinForms` とします。</span><span class="sxs-lookup"><span data-stu-id="b2546-107">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2. <span data-ttu-id="b2546-108">メイン フォーム Form1.cs (Visual Basic の Form1.vb) のフォーム デザイナーで、<xref:System.Windows.Forms.ToolStrip> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-108">On the form designer for the main form, Form1.cs (Form1.vb for Visual Basic), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3. <span data-ttu-id="b2546-109"><xref:System.Windows.Forms.ToolStrip> コントロールに <xref:System.Windows.Forms.ToolStripButton> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-109">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="b2546-110"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> プロパティを <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> に設定し、<xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを「**作業項目の追加**」に設定します。</span><span class="sxs-lookup"><span data-stu-id="b2546-110">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4. <span data-ttu-id="b2546-111"><xref:System.Windows.Forms.ToolStrip> コントロールに 2 つ目の <xref:System.Windows.Forms.ToolStripButton> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-111">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="b2546-112"><xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> プロパティを <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> に、<xref:System.Windows.Forms.ToolStripItem.Text%2A> プロパティを「**キャンセル**」に、<xref:System.Windows.Forms.ToolStripItem.Enabled%2A> プロパティを `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="b2546-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5. <span data-ttu-id="b2546-113">4 つの <xref:System.Windows.Forms.ToolStripProgressBar> コントロールを <xref:System.Windows.Forms.ToolStrip> コントロールに追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-113">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="b2546-114">データフロー パイプラインの作成</span><span class="sxs-lookup"><span data-stu-id="b2546-114">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="b2546-115">このセクションでは、作業項目を処理して進行状況バーを更新するデータフロー パイプラインを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b2546-115">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="b2546-116">データフロー パイプラインを作成するには</span><span class="sxs-lookup"><span data-stu-id="b2546-116">To Create the Dataflow Pipeline</span></span>  
  
1. <span data-ttu-id="b2546-117">プロジェクトで、System.Threading.Tasks.Dataflow.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-117">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2. <span data-ttu-id="b2546-118">Form1.cs (Visual Basic の Form1.vb) に次の `using` ステートメント (Visual Basic では `Imports`) が含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2546-118">Ensure that Form1.cs (Form1.vb for Visual Basic) contains the following `using` statements (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3. <span data-ttu-id="b2546-119">`Form1` クラスの内部の型として `WorkItem` クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-119">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4. <span data-ttu-id="b2546-120">`Form1` クラスに次のデータ メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-120">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5. <span data-ttu-id="b2546-121">次の `CreatePipeline` メソッドを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="b2546-121">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="b2546-122">`incrementProgress` と `decrementProgress` のデータフロー ブロックはユーザー インターフェイスで機能するので、これらの操作をユーザー インターフェイス スレッドで実行することが重要です。</span><span class="sxs-lookup"><span data-stu-id="b2546-122">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="b2546-123">これを実現するため、構築時にこれらのオブジェクトは <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> プロパティが <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> に設定された <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="b2546-123">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b2546-124"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2546-124">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="b2546-125">`Form1` コンストラクターはユーザー インターフェイス スレッドから呼び出されるので、`incrementProgress` および `decrementProgress` データフロー ブロックに対するアクションも、ユーザー インターフェイス スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="b2546-125">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="b2546-126">この例では、パイプラインのメンバーを構築するときに <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b2546-126">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="b2546-127"><xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> プロパティはデータフロー ブロックの実行を完全にキャンセルするので、ユーザーが操作をキャンセルした後にパイプラインにさらに作業項目を追加する場合は、すべてのパイプラインを作り直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2546-127">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="b2546-128">操作をキャンセルした後も他の作業を実行できるようにデータフロー ブロックをキャンセルする方法もあります。例については、「[チュートリアル:Windows フォーム アプリケーションでのデータフローの使用](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b2546-128">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="b2546-129">ユーザー インターフェイスへのデータフロー パイプラインの接続</span><span class="sxs-lookup"><span data-stu-id="b2546-129">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="b2546-130">このセクションでは、ユーザー インターフェイスにデータフロー パイプラインを接続する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="b2546-130">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="b2546-131">パイプラインの作成とパイプラインへの作業項目の追加は、どちらも **[作業項目の追加]** ボタンのインベント ハンドラーによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="b2546-131">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="b2546-132">キャンセルは **[キャンセル]** ボタンによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="b2546-132">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="b2546-133">ユーザーがこのいずれかのボタンをクリックすると、適切な操作が非同期的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="b2546-133">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="b2546-134">ユーザー インターフェイスにデータフロー パイプラインを接続するには</span><span class="sxs-lookup"><span data-stu-id="b2546-134">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1. <span data-ttu-id="b2546-135">メイン フォームのフォーム デザイナーで、 **[作業項目の追加]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントのイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2546-135">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2. <span data-ttu-id="b2546-136">**[作業項目の追加]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="b2546-136">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3. <span data-ttu-id="b2546-137">メイン フォームのフォーム デザイナーで、 **[キャンセル]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベント ハンドラーのイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="b2546-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4. <span data-ttu-id="b2546-138">**[キャンセル]** ボタンの <xref:System.Windows.Forms.ToolStripItem.Click> イベント ハンドラーを実装します。</span><span class="sxs-lookup"><span data-stu-id="b2546-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="b2546-139">例</span><span class="sxs-lookup"><span data-stu-id="b2546-139">Example</span></span>  
 <span data-ttu-id="b2546-140">次の例は、Form1.cs (Visual Basic の Form1.vb) のコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="b2546-140">The following example shows the complete code for Form1.cs (Form1.vb for Visual Basic).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="b2546-141">次の図は、実行中のアプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="b2546-141">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="b2546-142">![Windows フォーム アプリケーション](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="b2546-142">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  

## <a name="see-also"></a><span data-ttu-id="b2546-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="b2546-143">See also</span></span>

- [<span data-ttu-id="b2546-144">データフロー</span><span class="sxs-lookup"><span data-stu-id="b2546-144">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
