---
title: カスタム追跡参加要素を作成する方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: ea7a598a73f131d8ee33e285a39173fbf84a97f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182903"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="52093-102">カスタム追跡参加要素を作成する方法</span><span class="sxs-lookup"><span data-stu-id="52093-102">How to: Create a Custom Tracking Participant</span></span>
<span data-ttu-id="52093-103">ワークフロー追跡により、ワークフロー実行の状態が視覚的に示されます。</span><span class="sxs-lookup"><span data-stu-id="52093-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="52093-104">ワークフロー ランタイムによって、ワークフローのライフサイクル イベント、アクティビティのライフサイクル イベント、ブックマークの再開、およびエラーについて説明する追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="52093-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="52093-105">これらの追跡レコードは、追跡参加要素によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="52093-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="52093-106">Windows ワークフローファンデーション (WF) には、追跡レコードを Windows イベント トレース (ETW) イベントとして書き込む標準的な追跡参加要素が含まれています。</span><span class="sxs-lookup"><span data-stu-id="52093-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="52093-107">これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="52093-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="52093-108">チュートリアルのこの手順では、`WriteLine` アクティビティの出力をキャプチャするカスタム追跡参加要素と追跡プロファイルを作成して、ユーザーに表示できるようにする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52093-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="52093-109">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="52093-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="52093-110">このトピックを完了する前に、これまでのトピックを完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52093-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="52093-111">チュートリアルの完成版をダウンロードしたり、チュートリアルのビデオ チュートリアルを表示するには[、「Windows ワークフローファンデーション (WF45) - はじめにチュートリアル](https://go.microsoft.com/fwlink/?LinkID=248976)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52093-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="52093-112">カスタム追跡参加要素を作成するには</span><span class="sxs-lookup"><span data-stu-id="52093-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="52093-113">**ソリューション エクスプローラー**で **[NumberGuessWorkflowHost]** を右クリックし、[**追加**]、[**クラス**] の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="52093-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="52093-114">`StatusTrackingParticipant` **[名前**] ボックスに入力し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52093-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="52093-115">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="52093-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="52093-116">`StatusTrackingParticipant` クラスを変更して、`TrackingParticipant` から継承されるようにします。</span><span class="sxs-lookup"><span data-stu-id="52093-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. <span data-ttu-id="52093-117">次の `Track` メソッド オーバーライドを追加します。</span><span class="sxs-lookup"><span data-stu-id="52093-117">Add the following `Track` method override.</span></span> <span data-ttu-id="52093-118">追跡レコードには、いくつかの種類があります。</span><span class="sxs-lookup"><span data-stu-id="52093-118">There are several different types of tracking records.</span></span> <span data-ttu-id="52093-119">ここでは、アクティビティ追跡レコードに含まれる `WriteLine` アクティビティの出力に注目します。</span><span class="sxs-lookup"><span data-stu-id="52093-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="52093-120">`TrackingRecord` が `ActivityTrackingRecord` アクティビティの `WriteLine` である場合は、ワークフローの `Text` に基づいた名前の付いたファイルに `WriteLine` の `InstanceId` が追加されます。</span><span class="sxs-lookup"><span data-stu-id="52093-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="52093-121">このチュートリアルでは、ファイルはホスト アプリケーションの現在のフォルダーに保存されます。</span><span class="sxs-lookup"><span data-stu-id="52093-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="52093-122">追跡プロファイルを指定しない場合は、既定の追跡プロファイルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="52093-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="52093-123">既定の追跡プロファイルを使用する場合は、すべての `ActivityStates` に関する追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="52093-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="52093-124">ここでは、`WriteLine` アクティビティのライフサイクル中に 1 回だけテキストをキャプチャする必要があるため、`ActivityStates.Executing` 状態からテキストを抽出するだけです。</span><span class="sxs-lookup"><span data-stu-id="52093-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="52093-125">追跡[プロファイルを作成し、追跡参加要素を登録するには](#to-create-the-tracking-profile-and-register-the-tracking-participant)、追跡レコードのみを`WriteLine``ActivityStates.Executing`出力するように指定する追跡プロファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="52093-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="52093-126">追跡プロファイルを作成して追跡参加要素を登録するには</span><span class="sxs-lookup"><span data-stu-id="52093-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="52093-127">**ソリューション エクスプローラ**で **[WorkflowHostForm]** を右クリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52093-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="52093-128">次の `using` (または `Imports`) ステートメントを、他の `using` (または `Imports`) ステートメントを含むファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="52093-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="52093-129">ワークフロー拡張機能に `ConfigureWorkflowApplication` を追加するコードの直後で、ワークフロー ライフサイクル ハンドラーの前に、`StringWriter` に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="52093-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="52093-130">この追跡プロファイルでは、`WriteLine` 状態の `Executing` アクティビティのアクティビティ状態レコードのみがカスタム追跡参加要素に出力されるように指定します。</span><span class="sxs-lookup"><span data-stu-id="52093-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="52093-131">このコードを追加した後、`ConfigureWorkflowApplication` の先頭は次の例のようになります。</span><span class="sxs-lookup"><span data-stu-id="52093-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="52093-132">追跡情報を表示するには</span><span class="sxs-lookup"><span data-stu-id="52093-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="52093-133">**ソリューション エクスプローラ**で **[WorkflowHostForm]** を右クリックし、[**コードの表示**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="52093-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="52093-134">`InstanceId_SelectedIndexChanged` ハンドラーで、ステータス ウィンドウをクリアするコードの直後に次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="52093-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="52093-135">ワークフローの一覧で新しいワークフローを選択すると、そのワークフローの追跡レコードがステータス ウィンドウに読み込まれて表示されます。</span><span class="sxs-lookup"><span data-stu-id="52093-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="52093-136">完成した `InstanceId_SelectedIndexChanged` ハンドラーは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="52093-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="52093-137">アプリケーションをビルドして実行するには</span><span class="sxs-lookup"><span data-stu-id="52093-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="52093-138">Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="52093-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="52093-139">Ctrl キーを押しながら F5 キーを押してアプリケーションを起動します。</span><span class="sxs-lookup"><span data-stu-id="52093-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="52093-140">推測ゲームの範囲と開始するワークフローの種類を選択し、[**新しいゲーム**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52093-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="52093-141">**[推測**] ボックスに推測を入力し、[**移動**] をクリックして推測を送信します。</span><span class="sxs-lookup"><span data-stu-id="52093-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="52093-142">ワークフローの状態がステータス ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="52093-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="52093-143">この出力は、`WriteLine` アクティビティからキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="52093-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="52093-144">[**ワークフロー インスタンス ID]** コンボ ボックスからワークフローを選択して別のワークフローに切り替え、現在のワークフローの状態が削除されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="52093-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="52093-145">以前のワークフローに戻して、次の例のように、状態が復元されることを確認します。</span><span class="sxs-lookup"><span data-stu-id="52093-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="52093-146">追跡が有効になる前に開始されたワークフローに切り替えた場合、状態は表示されません。</span><span class="sxs-lookup"><span data-stu-id="52093-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="52093-147">ただし、推定値を追加すると、この時点では追跡が有効になっているため、その状態が保存されます。</span><span class="sxs-lookup"><span data-stu-id="52093-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > <span data-ttu-id="52093-148">この情報は、乱数の範囲を決定する場合に役立ちますが、これまでに作成された推定値に関する情報を含んでいません。</span><span class="sxs-lookup"><span data-stu-id="52093-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="52093-149">この情報は、次の手順「[方法: 複数のバージョンのワークフローを並べてホスト](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)する」にあります。</span><span class="sxs-lookup"><span data-stu-id="52093-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="52093-150">ワークフロー インスタンス ID を書き留め、ゲームを最後まで実行します。</span><span class="sxs-lookup"><span data-stu-id="52093-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="52093-151">エクスプローラを開き、プロジェクト設定に応じて **、番号ゲスワークフローホスト\ビン\デバッグ**フォルダ(または**ビン\リリース**)に移動します。</span><span class="sxs-lookup"><span data-stu-id="52093-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="52093-152">プロジェクトの実行可能ファイルに加え、GUID ファイル名が付いたファイルがあることに注意します。</span><span class="sxs-lookup"><span data-stu-id="52093-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="52093-153">前の手順で完了したワークフローのワークフロー インスタンス ID に対応するファイルを特定してメモ帳で開きます。</span><span class="sxs-lookup"><span data-stu-id="52093-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="52093-154">追跡情報は、次のような情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="52093-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="52093-155">この追跡データには、ユーザーの推定値だけでなく、ワークフローの最後の推定値に関する情報も含まれていません。</span><span class="sxs-lookup"><span data-stu-id="52093-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="52093-156">これは、追跡情報がワークフローからの `WriteLine` 出力のみで構成されており、表示される最後のメッセージがワークフロー完了後に `Completed` ハンドラーから表示されるためです。</span><span class="sxs-lookup"><span data-stu-id="52093-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="52093-157">チュートリアルの次のステップでは、[ワークフローの複数のバージョンを並べてホストする](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)、既存`WriteLine`のアクティビティは、ユーザーの推測を表示するように変更され、最終的な結果を表示する追加`WriteLine`のアクティビティが追加されます。</span><span class="sxs-lookup"><span data-stu-id="52093-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="52093-158">これらの変更が統合された後、[方法: 複数バージョンのワークフローを Side-by-side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)でホストする方法を示し、複数のバージョンのワークフローを同時にホストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="52093-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
