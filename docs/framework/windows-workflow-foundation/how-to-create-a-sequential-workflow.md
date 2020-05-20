---
title: '方法: シーケンシャル ワークフローを作成する'
description: この記事では、Sequence アクティビティなどの組み込みアクティビティとカスタムアクティビティの両方を使用するワークフローを作成します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5280e816-ae17-48c4-8de0-a1e6895dd8f0
ms.openlocfilehash: f80ac471fdcc425504b11b5fb17effa888aa9590
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419695"
---
# <a name="how-to-create-a-sequential-workflow"></a><span data-ttu-id="79448-103">方法: シーケンシャル ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="79448-103">How to: Create a Sequential Workflow</span></span>

<span data-ttu-id="79448-104">ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。</span><span class="sxs-lookup"><span data-stu-id="79448-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="79448-105">このトピックでは、アクティビティなどの組み込みのアクティビティ <xref:System.Activities.Statements.Sequence> と、前の「 [How To: Create a activity](how-to-create-an-activity.md) 」のカスタムアクティビティの両方を使用するワークフローを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="79448-105">This topic steps through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Sequence> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="79448-106">このワークフローは、数値推測ゲームをモデル化しています。</span><span class="sxs-lookup"><span data-stu-id="79448-106">The workflow models a number guessing game.</span></span>

> [!NOTE]
> <span data-ttu-id="79448-107">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="79448-107">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="79448-108">このトピックを完了するには、まず「[方法: アクティビティを作成](how-to-create-an-activity.md)する」を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="79448-108">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>

> [!NOTE]
> <span data-ttu-id="79448-109">チュートリアルの完成版をダウンロードするには、「 [Windows Workflow Foundation (WF45) - Getting Started Tutorial (Windows Workflow Foundation (WF45) - チュートリアル入門)](https://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79448-109">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>

## <a name="to-create-the-workflow"></a><span data-ttu-id="79448-110">ワークフローを作成するには</span><span class="sxs-lookup"><span data-stu-id="79448-110">To create the workflow</span></span>

1. <span data-ttu-id="79448-111">**ソリューションエクスプローラー**で [ **NumberGuessWorkflowActivities** ] を右クリックし、[**追加**]、[**新しい項目**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="79448-111">Right-click **NumberGuessWorkflowActivities** in **Solution Explorer** and select **Add**, **New Item**.</span></span>

2. <span data-ttu-id="79448-112">[**インストール済み**] の [**共通項目**] ノードで、[**ワークフロー**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="79448-112">In the **Installed**, **Common Items** node, select **Workflow**.</span></span> <span data-ttu-id="79448-113">[**ワークフロー**] 一覧から [**アクティビティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="79448-113">Select **Activity** from the **Workflow** list.</span></span>

3. <span data-ttu-id="79448-114">`SequentialNumberGuessWorkflow`[**名前**] ボックスに「」と入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79448-114">Type `SequentialNumberGuessWorkflow` into the **Name** box and click **Add**.</span></span>

4. <span data-ttu-id="79448-115">[**ツールボックス**] の [**制御フロー** ] セクションから**Sequence**アクティビティをドラッグし、ワークフローデザインサーフェイスの [**ここにアクティビティをドロップ**] ラベルの上にドロップします。</span><span class="sxs-lookup"><span data-stu-id="79448-115">Drag a **Sequence** activity from the **Control Flow** section of the **Toolbox** and drop it onto the **Drop activity here** label on the workflow design surface.</span></span>

## <a name="to-create-the-workflow-variables-and-arguments"></a><span data-ttu-id="79448-116">ワークフロー変数および引数を作成するには</span><span class="sxs-lookup"><span data-stu-id="79448-116">To create the workflow variables and arguments</span></span>

1. <span data-ttu-id="79448-117">**ソリューションエクスプローラー**で**sequentialnumberguessworkflow.xaml**をダブルクリックして、ワークフローをデザイナーに表示します (まだ表示されていない場合)。</span><span class="sxs-lookup"><span data-stu-id="79448-117">Double-click **SequentialNumberGuessWorkflow.xaml** in **Solution Explorer** to display the workflow in the designer, if it is not already displayed.</span></span>

2. <span data-ttu-id="79448-118">ワークフローデザイナーの左下にある [**引数**] をクリックして、[**引数**] ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="79448-118">Click **Arguments** in the lower-left side of the workflow designer to display the **Arguments** pane.</span></span>

3. <span data-ttu-id="79448-119">[**Create Argument**] (引数の作成) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79448-119">Click **Create Argument**.</span></span>

4. <span data-ttu-id="79448-120">[名前] ボックスに「」と入力し、[ `MaxNumber` **方向**] ドロップダウンリストから [ **In** ] を選択します。次に、[**引数の型**] ドロップダウンリストから [ **Int32** ] を選択し、enter キーを押して引数を保存します。 **Name**</span><span class="sxs-lookup"><span data-stu-id="79448-120">Type `MaxNumber` into the **Name** box, select **In** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER to save the argument.</span></span>

5. <span data-ttu-id="79448-121">[**Create Argument**] (引数の作成) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79448-121">Click **Create Argument**.</span></span>

6. <span data-ttu-id="79448-122">`Turns`新しく追加された引数の下にある [**名前**] ボックスに「」と入力し、 `MaxNumber` [**方向**] ドロップダウンリストから [ **Out** ] を選択します。次に、[**引数の型**] ドロップダウンリストから [ **Int32** ] を選択し、enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="79448-122">Type `Turns` into the **Name** box that is below the newly added `MaxNumber` argument, select **Out** from the **Direction** drop-down list, select **Int32** from the **Argument type** drop-down list, and then press ENTER.</span></span>

7. <span data-ttu-id="79448-123">アクティビティ デザイナーの左下にある [**引数**] をクリックして、[**引数**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="79448-123">Click **Arguments** in the lower-left side of the activity designer to close the **Arguments** pane.</span></span>

8. <span data-ttu-id="79448-124">ワークフローデザイナーの左下にある [**変数**] をクリックして、[**変数**] ペインを表示します。</span><span class="sxs-lookup"><span data-stu-id="79448-124">Click **Variables** in the lower-left side of the workflow designer to display the **Variables** pane.</span></span>

9. <span data-ttu-id="79448-125">[**変数の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79448-125">Click **Create Variable**.</span></span>

    > [!TIP]
    > <span data-ttu-id="79448-126">[**変数の作成**] ボックスが表示されない場合は、ワークフローデザイナー画面で**Sequence**アクティビティをクリックして選択します。</span><span class="sxs-lookup"><span data-stu-id="79448-126">If no **Create Variable** box is displayed, click the **Sequence** activity on the workflow designer surface to select it.</span></span>

10. <span data-ttu-id="79448-127">[ `Guess` **名前**] ボックスに「」と入力し、[**変数の型**] ドロップダウンリストから [ **Int32** ] を選択します。次に、enter キーを押して変数を保存します。</span><span class="sxs-lookup"><span data-stu-id="79448-127">Type `Guess` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

11. <span data-ttu-id="79448-128">[**変数の作成**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79448-128">Click **Create Variable**.</span></span>

12. <span data-ttu-id="79448-129">[ `Target` **名前**] ボックスに「」と入力し、[**変数の型**] ドロップダウンリストから [ **Int32** ] を選択します。次に、enter キーを押して変数を保存します。</span><span class="sxs-lookup"><span data-stu-id="79448-129">Type `Target` into the **Name** box, select **Int32** from the **Variable type** drop-down list, and then press ENTER to save the variable.</span></span>

13. <span data-ttu-id="79448-130">アクティビティ デザイナーの左下にある [**変数**] をクリックして、[**変数**] ウィンドウを閉じます。</span><span class="sxs-lookup"><span data-stu-id="79448-130">Click **Variables** in the lower-left side of the activity designer to close the **Variables** pane.</span></span>

## <a name="to-add-the-workflow-activities"></a><span data-ttu-id="79448-131">ワークフロー アクティビティを追加するには</span><span class="sxs-lookup"><span data-stu-id="79448-131">To add the workflow activities</span></span>

1. <span data-ttu-id="79448-132">**ツールボックス**の [**プリミティブ**] セクションから**Assign**アクティビティをドラッグし、 **Sequence**アクティビティにドロップします。</span><span class="sxs-lookup"><span data-stu-id="79448-132">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it onto the **Sequence** activity.</span></span> <span data-ttu-id="79448-133">[ `Target` **To** ] ボックスに「」と入力し、[ **C# の式を入力**するか、VB の式を**入力**してください] ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-133">Type `Target` into the **To** box and the following expression into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

    ```vb
    New System.Random().Next(1, MaxNumber + 1)
    ```

    ```csharp
    new System.Random().Next(1, MaxNumber + 1)
    ```

    > [!TIP]
    > <span data-ttu-id="79448-134">[**ツールパレット**] ウィンドウが表示されていない場合は、[**表示**] メニューから [**ツールパレット**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="79448-134">If the **Toolbox** window is not displayed, select **Toolbox** from the **View** menu.</span></span>

2. <span data-ttu-id="79448-135">**ツールボックス**の [**制御フロー** ] セクションから**dowhile**アクティビティをドラッグし、 **Assign**アクティビティの下になるようにワークフローにドロップします。</span><span class="sxs-lookup"><span data-stu-id="79448-135">Drag a **DoWhile** activity from the **Control Flow** section of the **Toolbox** and drop it on the workflow so that it is below the **Assign** activity.</span></span>

3. <span data-ttu-id="79448-136">**Dowhile**アクティビティの [ **Condition** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-136">Type the following expression into the **DoWhile** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

     <span data-ttu-id="79448-137"><xref:System.Activities.Statements.DoWhile> アクティビティはその子アクティビティを実行し、その <xref:System.Activities.Statements.DoWhile.Condition%2A> を評価します。</span><span class="sxs-lookup"><span data-stu-id="79448-137">A <xref:System.Activities.Statements.DoWhile> activity executes its child activities and then evaluates its <xref:System.Activities.Statements.DoWhile.Condition%2A>.</span></span> <span data-ttu-id="79448-138"><xref:System.Activities.Statements.DoWhile.Condition%2A> が `True` と評価される場合、<xref:System.Activities.Statements.DoWhile> 内のアクティビティが再度実行されます。</span><span class="sxs-lookup"><span data-stu-id="79448-138">If the <xref:System.Activities.Statements.DoWhile.Condition%2A> evaluates to `True`, then the activities in the <xref:System.Activities.Statements.DoWhile> execute again.</span></span> <span data-ttu-id="79448-139">この例では、ユーザーの推定値が評価され、推定値が正しいと判断されるまで <xref:System.Activities.Statements.DoWhile> が続行されます。</span><span class="sxs-lookup"><span data-stu-id="79448-139">In this example, the user’s guess is evaluated and the <xref:System.Activities.Statements.DoWhile> continues until the guess is correct.</span></span>

4. <span data-ttu-id="79448-140">[**ツールボックス**] の [ **NumberGuessWorkflowActivities** ] セクションから**Prompt**アクティビティをドラッグし、前の手順の**dowhile**アクティビティにドロップします。</span><span class="sxs-lookup"><span data-stu-id="79448-140">Drag a **Prompt** activity from the **NumberGuessWorkflowActivities** section of the **Toolbox** and drop it in the **DoWhile** activity from the previous step.</span></span>

5. <span data-ttu-id="79448-141">[**プロパティ] ウィンドウ**で、 `"EnterGuess"` **Prompt**アクティビティの [ **BookmarkName** ] プロパティ値ボックスに引用符を含めて「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-141">In the **Properties Window**, type `"EnterGuess"` including the quotes into the **BookmarkName** property value box for the **Prompt** activity.</span></span> <span data-ttu-id="79448-142">`Guess`[ **Result** ] プロパティ値ボックスに「」と入力し、[ **Text** ] プロパティボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-142">Type `Guess` into the **Result** property value box, and type the following expression into the **Text** property box.</span></span>

    ```vb
    "Please enter a number between 1 and " & MaxNumber
    ```

    ```csharp
    "Please enter a number between 1 and " + MaxNumber
    ```

    > [!TIP]
    > <span data-ttu-id="79448-143">[**プロパティ] ウィンドウ**が表示されていない場合は、[**表示**] メニューの [**プロパティウィンドウ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="79448-143">If the **Properties Window** is not displayed, select **Properties Window** from the **View** menu.</span></span>

6. <span data-ttu-id="79448-144">**ツールボックス**の [**プリミティブ**] セクションから**Assign**アクティビティをドラッグして、 **Prompt**アクティビティに続くように**dowhile**アクティビティにドロップします。</span><span class="sxs-lookup"><span data-stu-id="79448-144">Drag an **Assign** activity from the **Primitives** section of the **Toolbox** and drop it in the **DoWhile** activity so that it follows the **Prompt** activity.</span></span>

    > [!NOTE]
    > <span data-ttu-id="79448-145">**Assign**アクティビティを削除すると、ワークフローデザイナーが、 **Prompt**アクティビティと新しく追加された**Assign**アクティビティの両方を含む**Sequence**アクティビティを自動的に追加することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="79448-145">When you drop the **Assign** activity, note how the workflow designer automatically adds a **Sequence** activity to contain both the **Prompt** activity and the newly added **Assign** activity.</span></span>

7. <span data-ttu-id="79448-146">[ `Turns` **To** ] ボックスに「」と入力し、[C# の式を入力するか、VB の式を入力してください `Turns + 1` ] ボックスに入力します**Enter a C# expression** 。 **Enter a VB expression**</span><span class="sxs-lookup"><span data-stu-id="79448-146">Type `Turns` into the **To** box and `Turns + 1` into the **Enter a C# expression** or **Enter a VB expression** box.</span></span>

8. <span data-ttu-id="79448-147">[**ツールボックス**] の [**制御フロー** ] セクションから**If**アクティビティをドラッグし、新しく追加した**Assign**アクティビティの後になるように**Sequence**アクティビティにドロップします。</span><span class="sxs-lookup"><span data-stu-id="79448-147">Drag an **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Sequence** activity so that it follows the newly added **Assign** activity.</span></span>

9. <span data-ttu-id="79448-148">**If**アクティビティの [ **Condition** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-148">Type the following expression into the **If** activity’s **Condition** property value box.</span></span>

    ```vb
    Guess <> Target
    ```

    ```csharp
    Guess != Target
    ```

10. <span data-ttu-id="79448-149">**ツールボックス**の [**制御フロー** ] セクションから別の**if**アクティビティをドラッグし、最初の**if**アクティビティの**Then**セクションにドロップします。</span><span class="sxs-lookup"><span data-stu-id="79448-149">Drag another **If** activity from the **Control Flow** section of the **Toolbox** and drop it in the **Then** section of the first **If** activity.</span></span>

11. <span data-ttu-id="79448-150">新しく追加された**If**アクティビティの [ **Condition** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-150">Type the following expression into the newly added **If** activity’s **Condition** property value box.</span></span>

    ```text
    Guess < Target
    ```

12. <span data-ttu-id="79448-151">**ツールボックス**の [**プリミティブ**] セクションから2つの**WriteLine**アクティビティをドラッグしてドロップします。1つは、新しく追加した**If**アクティビティの**Then**セクションにあり、もう1つは**Else**セクションにあります。</span><span class="sxs-lookup"><span data-stu-id="79448-151">Drag two **WriteLine** activities from the **Primitives** section of the **Toolbox** and drop them so that one is in the **Then** section of the newly added **If** activity, and one is in the **Else** section.</span></span>

13. <span data-ttu-id="79448-152">**[Then** ] セクションで [ **WriteLine** ] アクティビティをクリックして選択し、[ **Text** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-152">Click the **WriteLine** activity in the **Then** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too low."
    ```

14. <span data-ttu-id="79448-153">[ **Else** ] セクションの**WriteLine**アクティビティをクリックして選択し、[ **Text** ] プロパティ値ボックスに次の式を入力します。</span><span class="sxs-lookup"><span data-stu-id="79448-153">Click the **WriteLine** activity in the **Else** section to select it, and type the following expression into the **Text** property value box.</span></span>

    ```text
    "Your guess is too high."
    ```

     <span data-ttu-id="79448-154">完成したワークフローの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="79448-154">The following example illustrates the completed workflow:</span></span>

     ![完成したシーケンシャルワークフローを示すスクリーンショット。](./media/how-to-create-a-sequential-workflow/complete-sequential-workflow.jpg)

## <a name="to-build-the-workflow"></a><span data-ttu-id="79448-156">ワークフローをビルドするには</span><span class="sxs-lookup"><span data-stu-id="79448-156">To build the workflow</span></span>

1. <span data-ttu-id="79448-157">Ctrl + Shift + B キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="79448-157">Press CTRL+SHIFT+B to build the solution.</span></span>

     <span data-ttu-id="79448-158">ワークフローを実行する方法については、次のトピック「[方法: ワークフローを実行](how-to-run-a-workflow.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79448-158">For instructions on how to run the workflow, please see the next topic, [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span> <span data-ttu-id="79448-159">[「方法:](how-to-run-a-workflow.md)ワークフローステップを別のスタイルのワークフローで実行し、この手順のシーケンシャルワークフローを使用して実行する場合は、「 [How to: run a workflow](how-to-run-a-workflow.md)」の「[アプリケーションをビルドして実行するに](how-to-run-a-workflow.md#BKMK_ToRunTheApplication)は」に進んでください。</span><span class="sxs-lookup"><span data-stu-id="79448-159">If you have already completed the [How to: Run a Workflow](how-to-run-a-workflow.md) step with a different style of workflow and wish to run it using the sequential workflow from this step, skip ahead to the [To build and run the application](how-to-run-a-workflow.md#BKMK_ToRunTheApplication) section of [How to: Run a Workflow](how-to-run-a-workflow.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="79448-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="79448-160">See also</span></span>

- <xref:System.Activities.Statements.Flowchart>
- <xref:System.Activities.Statements.FlowDecision>
- [<span data-ttu-id="79448-161">Windows Workflow Foundation プログラミングの新機能</span><span class="sxs-lookup"><span data-stu-id="79448-161">Windows Workflow Foundation Programming</span></span>](programming.md)
- [<span data-ttu-id="79448-162">ワークフローの設計</span><span class="sxs-lookup"><span data-stu-id="79448-162">Designing Workflows</span></span>](designing-workflows.md)
- [<span data-ttu-id="79448-163">はじめにチュートリアル</span><span class="sxs-lookup"><span data-stu-id="79448-163">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
- [<span data-ttu-id="79448-164">方法: アクティビティを作成する</span><span class="sxs-lookup"><span data-stu-id="79448-164">How to: Create an Activity</span></span>](how-to-create-an-activity.md)
- [<span data-ttu-id="79448-165">方法: ワークフローを実行する</span><span class="sxs-lookup"><span data-stu-id="79448-165">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)
