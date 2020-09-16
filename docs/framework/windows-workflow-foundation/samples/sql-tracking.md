---
title: SQL 追跡
ms.date: 03/30/2017
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
ms.openlocfilehash: 916c04b03dee296b7e6f5c792f0c4e50fb4203c0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559351"
---
# <a name="sql-tracking"></a><span data-ttu-id="0791d-102">SQL 追跡</span><span class="sxs-lookup"><span data-stu-id="0791d-102">SQL tracking</span></span>

<span data-ttu-id="0791d-103">このサンプルでは、SQL データベースに追跡レコードを書き込むカスタム SQL 追跡参加要素を記述する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0791d-103">This sample demonstrates how to write a custom SQL tracking participant that writes tracking records to a SQL database.</span></span> <span data-ttu-id="0791d-104">Windows Workflow Foundation (WF) は、ワークフローインスタンスの実行の可視性を得るためのワークフロー追跡機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="0791d-104">Windows Workflow Foundation (WF) provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="0791d-105">追跡ランタイムでは、ワークフローの実行中にワークフロー追跡レコードが出力されます。</span><span class="sxs-lookup"><span data-stu-id="0791d-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> <span data-ttu-id="0791d-106">ワークフロー追跡の詳細については、「 [ワークフローの追跡とトレース](../workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0791d-106">For more information about workflow tracking, see [Workflow Tracking and Tracing](../workflow-tracking-and-tracing.md).</span></span>

## <a name="use-the-sample"></a><span data-ttu-id="0791d-107">サンプルを使用する</span><span class="sxs-lookup"><span data-stu-id="0791d-107">Use the sample</span></span>

1. <span data-ttu-id="0791d-108">SQL Server 2008、SQL Server 2008 Express、またはそれ以降のバージョンがインストールされていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="0791d-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="0791d-109">サンプルと共にパッケージ化されているスクリプトは、SQL Express インスタンスをローカル コンピューターで使用していることが前提になります。</span><span class="sxs-lookup"><span data-stu-id="0791d-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="0791d-110">別のインスタンスがある場合は、データベース関連のスクリプトを変更してからサンプルを実行してください。</span><span class="sxs-lookup"><span data-stu-id="0791d-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>

2. <span data-ttu-id="0791d-111">Scripts ディレクトリ (\WF\Basic\Tracking\SqlTracking\CS\Scripts) 内で Trackingsetup.cmd を実行して SQL Server 追跡データベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="0791d-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="0791d-112">これによって、TrackingSample という名前のデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0791d-112">This creates a database called TrackingSample.</span></span>

   > [!NOTE]
   > <span data-ttu-id="0791d-113">このスクリプトでは、SQL Express の既定のインスタンスにデータベースが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0791d-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="0791d-114">別のデータベース インスタンスにインストールする場合は、Trackingsetup.cmd スクリプトを編集してください。</span><span class="sxs-lookup"><span data-stu-id="0791d-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>

3. <span data-ttu-id="0791d-115">Visual Studio 2010 で SqlTrackingSample .sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="0791d-115">Open SqlTrackingSample.sln in Visual Studio 2010.</span></span>

4. <span data-ttu-id="0791d-116">**Ctrl** + **Shift** + **B**キーを押して、ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="0791d-116">Press **Ctrl**+**Shift**+**B** to build the solution.</span></span>

5. <span data-ttu-id="0791d-117">**F5** キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="0791d-117">Press **F5** to run the application.</span></span>

   <span data-ttu-id="0791d-118">ブラウザー ウィンドウが開き、アプリケーションのディレクトリの一覧が示されます。</span><span class="sxs-lookup"><span data-stu-id="0791d-118">The browser window opens and shows the directory listing for the application.</span></span>

6. <span data-ttu-id="0791d-119">ブラウザーで、StockPriceService.xamlx をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0791d-119">In the browser, click StockPriceService.xamlx.</span></span>

7. <span data-ttu-id="0791d-120">ブラウザーに、[StockPriceService] ページが表示され、ローカル サービスの WSDL アドレスが示されます。</span><span class="sxs-lookup"><span data-stu-id="0791d-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="0791d-121">このアドレスをコピーします。</span><span class="sxs-lookup"><span data-stu-id="0791d-121">Copy this address.</span></span>

   <span data-ttu-id="0791d-122">ローカルサービスの WSDL アドレスの例は、 `http://localhost:65193/StockPriceService.xamlx?wsdl` です。</span><span class="sxs-lookup"><span data-stu-id="0791d-122">An example of the local service WSDL address is `http://localhost:65193/StockPriceService.xamlx?wsdl`.</span></span>

8. <span data-ttu-id="0791d-123">エクスプローラーを使用して、WCF テストクライアント (WcfTestClient.exe) を実行します。</span><span class="sxs-lookup"><span data-stu-id="0791d-123">Using File Explorer, run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="0791d-124">これは、 *Microsoft Visual Studio 10.0 \ Common7\IDE ディレクトリ*にあります。</span><span class="sxs-lookup"><span data-stu-id="0791d-124">It's located in the *Microsoft Visual Studio 10.0\Common7\IDE directory*.</span></span>

9. <span data-ttu-id="0791d-125">WCF テストクライアントで、[ **ファイル** ] メニューをクリックし、[ **サービスの追加**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="0791d-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="0791d-126">テキスト ボックスにローカル サービスのアドレスを貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="0791d-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="0791d-127">[**OK**] をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0791d-127">Click **OK** to close the dialog.</span></span>

10. <span data-ttu-id="0791d-128">WCF テストクライアントで、[ **Getstockprice**] をダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="0791d-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="0791d-129">これにより、 `GetStockPrice` 1 つのパラメーターを受け取る操作が開き、値を入力 `Contoso` して、[ **呼び出し**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0791d-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>

11. <span data-ttu-id="0791d-130">出力された追跡レコードが SQL データベースに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="0791d-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="0791d-131">追跡レコードを表示するには、SQL Management Studio で TrackingSample データベースを開き、テーブルに移動します。</span><span class="sxs-lookup"><span data-stu-id="0791d-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> <span data-ttu-id="0791d-132">テーブルで選択クエリを実行すると、それぞれのテーブルに格納されている追跡レコード内のデータが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0791d-132">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>

   <span data-ttu-id="0791d-133">SQL Server Management Studio の詳細については、「 [SQL Server Management Studio の概要](/sql/ssms/sql-server-management-studio-ssms)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0791d-133">For more information about SQL Server Management Studio, see [Introducing SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms).</span></span> <span data-ttu-id="0791d-134">SQL Server Management Studio [こちら](https://aka.ms/ssmsfullsetup)からダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="0791d-134">Download SQL Server Management Studio [here](https://aka.ms/ssmsfullsetup).</span></span>

## <a name="uninstall-the-sample"></a><span data-ttu-id="0791d-135">サンプルをアンインストールする</span><span class="sxs-lookup"><span data-stu-id="0791d-135">Uninstall the sample</span></span>

1. <span data-ttu-id="0791d-136">サンプル*ディレクトリ (-*----------/) で、スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="0791d-136">Run theTrackingcleanup.cmd script in the sample directory (*\WF\Basic\Tracking\SqlTracking*).</span></span>

    > [!NOTE]
    > <span data-ttu-id="0791d-137">Trackingcleanup.cmd は、ローカル コンピューターの SQL Express 内にあるデータベースを削除しようとします。</span><span class="sxs-lookup"><span data-stu-id="0791d-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="0791d-138">別の SQL Server インスタンスを使用している場合は、Trackingcleanup.cmd を編集します。</span><span class="sxs-lookup"><span data-stu-id="0791d-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0791d-139">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0791d-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="0791d-140">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0791d-140">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="0791d-141">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="0791d-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0791d-142">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0791d-142">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`

## <a name="see-also"></a><span data-ttu-id="0791d-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="0791d-143">See also</span></span>

- <span data-ttu-id="0791d-144">[AppFabric の監視のサンプル](/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="0791d-144">[AppFabric Monitoring Samples](/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
