---
title: Pick アクティビティの使用
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 7ca4527cc1d5bc90ed1ec4df3eef6cf2d8b93b4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142616"
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="cc78f-102">Pick アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="cc78f-102">Using the Pick Activity</span></span>
<span data-ttu-id="cc78f-103">このサンプルでは、<xref:System.Activities.Statements.Pick> アクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cc78f-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>

 <span data-ttu-id="cc78f-104"><xref:System.Activities.Statements.Pick> アクティビティでは、イベント ベースの制御モデリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="cc78f-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="cc78f-105">このアクティビティの動作は C# の `switch` ステートメントに似ています。`switch` ステートメントでは、その分岐のうち 1 つだけが実行されます。</span><span class="sxs-lookup"><span data-stu-id="cc78f-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="cc78f-106">ただし、値に基づいて分岐が実行される `switch` ステートメントと異なり、<xref:System.Activities.Statements.Pick> アクティビティでは、アクティビティの完了の状態に基づいて分岐を実行します。</span><span class="sxs-lookup"><span data-stu-id="cc78f-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>

 <span data-ttu-id="cc78f-107">このサンプルでは、指定した時間内にコンソールでユーザー名を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="cc78f-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="cc78f-108">このサンプルの <xref:System.Activities.Statements.Pick> アクティビティには、ユーザーが 5 秒以内にユーザー名を入力したかどうかに基づいて実行される 2 つの分岐があります。</span><span class="sxs-lookup"><span data-stu-id="cc78f-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="cc78f-109">ユーザーが 5 秒以内にユーザー名を入力した場合は、カスタムの `ReadLine` アクティビティを含む最初の分岐が実行されます。それ以外の場合は、<xref:System.Activities.Statements.Delay> アクティビティを含むもう 1 つの分岐が実行されます。</span><span class="sxs-lookup"><span data-stu-id="cc78f-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="cc78f-110">コンソールでユーザー名を入力すると、そのユーザー名がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="cc78f-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="cc78f-111">5 秒以内に入力しないと、操作はタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="cc78f-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="cc78f-112">対象</span><span class="sxs-lookup"><span data-stu-id="cc78f-112">Demonstrates</span></span>
 <span data-ttu-id="cc78f-113"><xref:System.Activities.Statements.Pick> アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="cc78f-113"><xref:System.Activities.Statements.Pick> activity.</span></span>

## <a name="discussion"></a><span data-ttu-id="cc78f-114">ディスカッション</span><span class="sxs-lookup"><span data-stu-id="cc78f-114">Discussion</span></span>
 <span data-ttu-id="cc78f-115">このサンプルには、デザイナー ワークフローとコード化されたワークフローがあります。</span><span class="sxs-lookup"><span data-stu-id="cc78f-115">The sample includes a Designer workflow and coded workflow.</span></span>

 <span data-ttu-id="cc78f-116">デザイナー ワークフロー デザイナー バージョンのサンプルは、デザイナーでワークフローを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cc78f-116">Designer Workflow The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="cc78f-117">次のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="cc78f-117">The following files are included:</span></span>

- <span data-ttu-id="cc78f-118">Program.cs: サンプル ワークフローを実行する `Main` 関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc78f-118">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="cc78f-119">ReadString.cs: コンソールからの入力を読み取るカスタム アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="cc78f-119">ReadString.cs: A custom activity that reads some input from the console.</span></span>

- <span data-ttu-id="cc78f-120">Sequence1.xaml: Pick を使用する、デザイナーで作成されたワークフローです。</span><span class="sxs-lookup"><span data-stu-id="cc78f-120">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>

 <span data-ttu-id="cc78f-121">コード化されたワークフロー コード化されたバージョンのサンプルは、デザイナーでワークフローを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="cc78f-121">Coded Workflow The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="cc78f-122">次のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="cc78f-122">The following files are included:</span></span>

- <span data-ttu-id="cc78f-123">Program.cs: サンプル ワークフローを実行する `Main` 関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="cc78f-123">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>

- <span data-ttu-id="cc78f-124">ReadString.cs: コンソールからの入力を読み取るカスタム アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="cc78f-124">ReadString.cs: A custom activity that reads some input from the console.</span></span>

#### <a name="to-use-this-sample"></a><span data-ttu-id="cc78f-125">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="cc78f-125">To use this sample</span></span>

1. <span data-ttu-id="cc78f-126">Visual Studio 2010 を使用して、Pick.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="cc78f-126">Using Visual Studio 2010, open the Pick.sln solution file.</span></span>

2. <span data-ttu-id="cc78f-127">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="cc78f-127">To build the solution, press CTRL+SHIFT+B.</span></span>

3. <span data-ttu-id="cc78f-128">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="cc78f-128">To run the solution, press F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cc78f-129">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="cc78f-129">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cc78f-130">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cc78f-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="cc78f-131">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="cc78f-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cc78f-132">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cc78f-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`
