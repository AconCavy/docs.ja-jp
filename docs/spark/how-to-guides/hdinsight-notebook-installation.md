---
title: Azure HDInsight Spark クラスター上の Jupyter Notebook に .NET for Apache Spark をインストールする
description: Azure HDInsight の Jupyter Notebook に .NET for Apache Spark をインストールする方法について説明します。
ms.date: 06/25/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 14babf7a551192b286f309393e3bbff25d4745d5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617744"
---
# <a name="install-net-for-apache-spark-on-jupyter-notebooks-on-azure-hdinsight-spark-clusters"></a><span data-ttu-id="acecc-103">Azure HDInsight Spark クラスター上の Jupyter Notebook に .NET for Apache Spark をインストールする</span><span class="sxs-lookup"><span data-stu-id="acecc-103">Install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters</span></span>

<span data-ttu-id="acecc-104">この記事では、Azure HDInsight Spark クラスター上の Jupyter Notebook に .NET for Apache Spark をインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="acecc-104">This article teaches you how to install .NET for Apache Spark on Jupyter notebooks on Azure HDInsight Spark clusters.</span></span> <span data-ttu-id="acecc-105">コマンド ラインと Azure portal を組み合わせて、Azure HDInsight クラスターに .NET for Apache Spark をデプロイすることができます (詳しくは [Azure HDInsight に .NET for Apache Spark アプリケーションをデプロイする方法](../tutorials/hdinsight-deployment.md)に関する記事を参照)。ただし、ノートブックにはより対話的で反復的なエクスペリエンスが用意されています。</span><span class="sxs-lookup"><span data-stu-id="acecc-105">You can deploy .NET for Apache Spark on Azure HDInsight clusters through a combination of the command line and the Azure portal (for more information, see [how to deploy a .NET for Apache Spark application to Azure HDInsight](../tutorials/hdinsight-deployment.md)), but notebooks provide a more interactive and iterative experience.</span></span>

<span data-ttu-id="acecc-106">Azure HDInsight クラスターには既に Jupyter Notebook が付属しているため、.NET for Apache Spark を実行するように Jupyter Notebook を構成するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="acecc-106">Azure HDInsight clusters already come with Jupyter notebooks, so all you have to do is configure the Jupyter notebooks to run .NET for Apache Spark.</span></span> <span data-ttu-id="acecc-107">Jupyter Notebook で .NET for Apache Spark を使用する場合、C# コードを 1 行ずつ実行し、必要に応じて実行状態を維持するために、C# REPL が必要です。</span><span class="sxs-lookup"><span data-stu-id="acecc-107">To use .NET for Apache Spark in your Jupyter notebooks, a C# REPL is needed to execute your C# code line-by-line and to preserve execution state when necessary.</span></span> <span data-ttu-id="acecc-108">[Try .NET](https://github.com/dotnet/try) は、公式の .NET REPL として統合されています。</span><span class="sxs-lookup"><span data-stu-id="acecc-108">[Try .NET](https://github.com/dotnet/try) has been integrated as the official .NET REPL.</span></span>

<span data-ttu-id="acecc-109">Jupyter Notebook のエクスペリエンスを通じて .NET for Apache Spark を有効にするには、[Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) を使用したいくつかの手動の手順に従い、HDInsight Spark クラスターで[スクリプト アクション](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)を送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acecc-109">To enable .NET for Apache Spark through the Jupyter Notebooks experience, you need to follow a few manual steps through [Ambari](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-manage-ambari) and submit [script actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux) on the HDInsight Spark cluster.</span></span>

> [!NOTE]
> <span data-ttu-id="acecc-110">この機能は "*試験段階*" であり、HDInsight Spark チームではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="acecc-110">This feature is *experimental* and is not supported by the HDInsight Spark team.</span></span>

[!INCLUDE [spark-preview-note](../../../includes/spark-preview-note.md)]

## <a name="prerequisites"></a><span data-ttu-id="acecc-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="acecc-111">Prerequisites</span></span>

<span data-ttu-id="acecc-112">まだお持ちでない場合は、[Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) クラスターを作成します。</span><span class="sxs-lookup"><span data-stu-id="acecc-112">If you don't already have one, create an [Azure HDInsight Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-jupyter-spark-sql-use-portal#create-an-apache-spark-cluster-in-hdinsight) cluster.</span></span>

1. <span data-ttu-id="acecc-113">[Azure portal](https://portal.azure.com) にアクセスし、 **[+ リソースの作成]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-113">Visit the [Azure portal](https://portal.azure.com) and select **+ Create a Resource**.</span></span>

1. <span data-ttu-id="acecc-114">新しい Azure HDInsight クラスターのリソースを作成します。</span><span class="sxs-lookup"><span data-stu-id="acecc-114">Create a new Azure HDInsight cluster resource.</span></span> <span data-ttu-id="acecc-115">クラスターの作成中に、**Spark 2.4** と **HDI 4.0** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-115">Select **Spark 2.4** and **HDI 4.0** during cluster creation.</span></span>

## <a name="install-net-for-apache-spark"></a><span data-ttu-id="acecc-116">.NET for Apache Spark のインストール</span><span class="sxs-lookup"><span data-stu-id="acecc-116">Install .NET for Apache Spark</span></span>

<span data-ttu-id="acecc-117">Azure portal で、前の手順で作成した **HDInsight Spark クラスター**を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-117">In the Azure portal, select the **HDInsight Spark cluster** you created in the previous step.</span></span>

### <a name="stop-the-livy-server"></a><span data-ttu-id="acecc-118">Livy サーバーを停止する</span><span class="sxs-lookup"><span data-stu-id="acecc-118">Stop the Livy server</span></span>

1. <span data-ttu-id="acecc-119">ポータルで **[概要]** を選択した後、 **[Ambari ホーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-119">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="acecc-120">入力を求められたら、クラスターのログイン資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="acecc-120">If prompted, enter the login credentials for the cluster.</span></span>

   ![Livy サーバーを停止する](./media/hdinsight-notebook-installation/select-ambari.png)

2. <span data-ttu-id="acecc-122">左側のナビゲーション メニューから **[Spark2]** を選択し、 **[LIVY FOR SPARK2 SERVER]\(Spark2 の Livy サーバー\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-122">Select **Spark2** from the left navigation menu, and select **LIVY FOR SPARK2 SERVER**.</span></span>

   ![Livy サーバーを停止する](./media/hdinsight-notebook-installation/select-livyserver.png)

3. <span data-ttu-id="acecc-124">**hn0 で始まるホスト**を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-124">Select **hn0... host**.</span></span>

   ![Livy サーバーを停止する](./media/hdinsight-notebook-installation/select-host.png)

4. <span data-ttu-id="acecc-126">**[Livy for Spark2 Server]\(Spark2 の Livy サーバー\)** の横にある省略記号を選択し、 **[停止]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-126">Select the ellipsis next to **Livy for Spark2 Server** and select **Stop**.</span></span> <span data-ttu-id="acecc-127">メッセージが表示されたら、 **[OK]** を選択して続行します。</span><span class="sxs-lookup"><span data-stu-id="acecc-127">When prompted, select **OK** to proceed.</span></span>

   <span data-ttu-id="acecc-128">Spark2 の Livy サーバーを停止します。</span><span class="sxs-lookup"><span data-stu-id="acecc-128">Stop Livy for Spark2 Server.</span></span>
   <span data-ttu-id="acecc-129">![Livy サーバーを停止する](./media/hdinsight-notebook-installation/stop-server.png)</span><span class="sxs-lookup"><span data-stu-id="acecc-129">![Stop Livy Server](./media/hdinsight-notebook-installation/stop-server.png)</span></span>

5. <span data-ttu-id="acecc-130">**hn1 で始まるホスト**に対して前の手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="acecc-130">Repeat the previous steps for **hn1... host**.</span></span>

### <a name="submit-an-hdinsight-script-action"></a><span data-ttu-id="acecc-131">HDInsight スクリプト アクションを送信する</span><span class="sxs-lookup"><span data-stu-id="acecc-131">Submit an HDInsight script action</span></span>

1. <span data-ttu-id="acecc-132">`install-interactive-notebook.sh` は、.NET for Apache Spark をインストールし、Apache Livy と sparkmagic に変更を加えるスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="acecc-132">The `install-interactive-notebook.sh` is a script that installs .NET for Apache Spark and makes changes to Apache Livy and sparkmagic.</span></span> <span data-ttu-id="acecc-133">スクリプト アクションを HDInsight に送信する前に、`install-interactive-notebook.sh` を作成してアップロードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="acecc-133">Before you submit a script action to HDInsight, you need to create and upload `install-interactive-notebook.sh`.</span></span>

   <span data-ttu-id="acecc-134">ご自分のローカル コンピューターに **install-interactive-notebook.sh** という名前の新しいファイルを作成し、[install-interactive-notebook.sh の内容](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh)を貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="acecc-134">Create a new file named **install-interactive-notebook.sh** in your local computer and paste the contents of [install-interactive-notebook.sh contents](https://raw.githubusercontent.com/dotnet/spark/master/deployment/HDI-Spark/Notebooks/install-interactive-notebook.sh).</span></span>

   <span data-ttu-id="acecc-135">このスクリプトを、HDInsight クラスターからアクセスできる [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) にアップロードします。</span><span class="sxs-lookup"><span data-stu-id="acecc-135">Upload the script to a [URI](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux#understand-script-actions) that's accessible from the HDInsight cluster.</span></span> <span data-ttu-id="acecc-136">たとえば、`https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh` のようにします。</span><span class="sxs-lookup"><span data-stu-id="acecc-136">For example, `https://<my storage account>.blob.core.windows.net/<my container>/<some dir>/install-interactive-notebook.sh`.</span></span>

2. <span data-ttu-id="acecc-137">[HDInsight スクリプト アクション](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux)を使用して、クラスターで `install-interactive-notebook.sh` を実行します。</span><span class="sxs-lookup"><span data-stu-id="acecc-137">Run `install-interactive-notebook.sh` on the cluster using [HDInsight Script Actions](https://docs.microsoft.com/azure/hdinsight/hdinsight-hadoop-customize-cluster-linux).</span></span>

   <span data-ttu-id="acecc-138">Azure portal で HDI クラスターに戻り、左側のオプションから **[スクリプト アクション]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-138">Return to your HDI cluster in the Azure portal, and select **Script actions** from the options on the left.</span></span> <span data-ttu-id="acecc-139">HDInsight Spark クラスターに .NET for Apache Spark の REPL をデプロイするためのスクリプト アクションを 1 つ送信します。</span><span class="sxs-lookup"><span data-stu-id="acecc-139">You submit one script action to deploy the .NET for Apache Spark REPL on your HDInsight Spark cluster.</span></span> <span data-ttu-id="acecc-140">次の設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="acecc-140">Use the following settings:</span></span>

   |<span data-ttu-id="acecc-141">プロパティ</span><span class="sxs-lookup"><span data-stu-id="acecc-141">Property</span></span>  |<span data-ttu-id="acecc-142">説明</span><span class="sxs-lookup"><span data-stu-id="acecc-142">Description</span></span>  |
   |---------|---------|
   | <span data-ttu-id="acecc-143">スクリプトの種類</span><span class="sxs-lookup"><span data-stu-id="acecc-143">Script type</span></span> | <span data-ttu-id="acecc-144">カスタム</span><span class="sxs-lookup"><span data-stu-id="acecc-144">Custom</span></span> |
   | <span data-ttu-id="acecc-145">名前</span><span class="sxs-lookup"><span data-stu-id="acecc-145">Name</span></span> | <span data-ttu-id="acecc-146">" *.NET for Apache Spark 対話型 Notebook エクスペリエンスをインストールする*"</span><span class="sxs-lookup"><span data-stu-id="acecc-146">*Install .NET for Apache Spark Interactive Notebook Experience*</span></span> |
   | <span data-ttu-id="acecc-147">Bash スクリプト URI</span><span class="sxs-lookup"><span data-stu-id="acecc-147">Bash script URI</span></span> | <span data-ttu-id="acecc-148">`install-interactive-notebook.sh` のアップロード先の URI。</span><span class="sxs-lookup"><span data-stu-id="acecc-148">The URI to which you uploaded `install-interactive-notebook.sh`.</span></span> |
   | <span data-ttu-id="acecc-149">ノードの種類</span><span class="sxs-lookup"><span data-stu-id="acecc-149">Node type(s)</span></span>| <span data-ttu-id="acecc-150">ヘッド、ワーカー</span><span class="sxs-lookup"><span data-stu-id="acecc-150">Head and Worker</span></span> |
   | <span data-ttu-id="acecc-151">パラメーター</span><span class="sxs-lookup"><span data-stu-id="acecc-151">Parameters</span></span> | <span data-ttu-id="acecc-152">.NET for Apache Spark のバージョン。</span><span class="sxs-lookup"><span data-stu-id="acecc-152">.NET for Apache Spark version.</span></span> <span data-ttu-id="acecc-153">[.NET for Apache Spark のリリース](https://github.com/dotnet/spark/releases)を確認できます。</span><span class="sxs-lookup"><span data-stu-id="acecc-153">You can check [.NET for Apache Spark releases](https://github.com/dotnet/spark/releases).</span></span> <span data-ttu-id="acecc-154">たとえば、Sparkdotnet バージョン 0.6.0 をインストールする場合は、`0.6.0` とします。</span><span class="sxs-lookup"><span data-stu-id="acecc-154">For example, if you want to install Sparkdotnet version 0.6.0 then it would be `0.6.0`.</span></span>

   <span data-ttu-id="acecc-155">スクリプト アクションの状態の横に緑色のチェックマークが表示されたら、次の手順に進みます。</span><span class="sxs-lookup"><span data-stu-id="acecc-155">Move to the next step when green checkmarks appear next to the status of the script action.</span></span>

### <a name="start-the-livy-server"></a><span data-ttu-id="acecc-156">Livy サーバーを起動する</span><span class="sxs-lookup"><span data-stu-id="acecc-156">Start the Livy server</span></span>

<span data-ttu-id="acecc-157">「[Livy サーバーを停止する](#stop-the-livy-server)」セクションの手順に従って、ホスト **hn0** と **hn1** に対して Spark2 の Livy サーバーを **[開始]** ( **[停止]** ではなく) します。</span><span class="sxs-lookup"><span data-stu-id="acecc-157">Follow the instructions in the [Stop Livy server](#stop-the-livy-server) section to **Start** (rather than **Stop**) the Livy for Spark2 Server for hosts **hn0** and **hn1**.</span></span>

### <a name="set-up-spark-default-configurations"></a><span data-ttu-id="acecc-158">Spark の既定の構成を設定する</span><span class="sxs-lookup"><span data-stu-id="acecc-158">Set up Spark default configurations</span></span>

1. <span data-ttu-id="acecc-159">ポータルで **[概要]** を選択した後、 **[Ambari ホーム]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-159">From the portal, select **Overview**, and then select **Ambari home**.</span></span> <span data-ttu-id="acecc-160">入力を求められたら、クラスターのログイン資格情報を入力します。</span><span class="sxs-lookup"><span data-stu-id="acecc-160">If prompted, enter the cluster login credentials for the cluster.</span></span>

2. <span data-ttu-id="acecc-161">**[Spark2]** 、 **[CONFIGS]\(構成\)** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-161">Select **Spark2** and **CONFIGS**.</span></span> <span data-ttu-id="acecc-162">次に、 **[Custom spark2-defaults]\(カスタム Spark2 既定値\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-162">Then, select **Custom spark2-defaults**.</span></span>

   ![構成の設定](./media/hdinsight-notebook-installation/spark-configs.png)

3. <span data-ttu-id="acecc-164">**[プロパティの追加...]** を選択して、Spark の既定の設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="acecc-164">Select **Add Property...** to add Spark default settings.</span></span>

   ![プロパティの追加](./media/hdinsight-notebook-installation/add-property.png)

   <span data-ttu-id="acecc-166">個別のプロパティが 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="acecc-166">There are three individual properties.</span></span> <span data-ttu-id="acecc-167">単一プロパティの追加モードで、**TEXT** プロパティの型を使用して、一度に 1 つずつ追加します。</span><span class="sxs-lookup"><span data-stu-id="acecc-167">Add them one at a time using the **TEXT** property type in Single property add mode.</span></span> <span data-ttu-id="acecc-168">いずれのキーまたは値の前後にも、余分なスペースがないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="acecc-168">Check that you don't have any extra spaces before or after any of the keys/values.</span></span>

   * <span data-ttu-id="acecc-169">**プロパティ 1**</span><span class="sxs-lookup"><span data-stu-id="acecc-169">**Property 1**</span></span>
       * <span data-ttu-id="acecc-170">キー: &ensp;&ensp;`spark.dotnet.shell.command`</span><span class="sxs-lookup"><span data-stu-id="acecc-170">Key:&ensp;&ensp;`spark.dotnet.shell.command`</span></span>
       * <span data-ttu-id="acecc-171">値: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span><span class="sxs-lookup"><span data-stu-id="acecc-171">Value: `/usr/share/dotnet-tools/dotnet-try,kernel-server,--default-kernel,csharp`</span></span>

   * <span data-ttu-id="acecc-172">**プロパティ 2** 前のスクリプト アクションに含めた .NET for Apache Spark のバージョンを使用してください。</span><span class="sxs-lookup"><span data-stu-id="acecc-172">**Property 2** Use the version of .NET for Apache Spark which you had included in the previous script action.</span></span>
       * <span data-ttu-id="acecc-173">キー: &ensp;&ensp;`spark.dotnet.packages`</span><span class="sxs-lookup"><span data-stu-id="acecc-173">Key:&ensp;&ensp;`spark.dotnet.packages`</span></span>
       * <span data-ttu-id="acecc-174">値: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span><span class="sxs-lookup"><span data-stu-id="acecc-174">Value: `["nuget: Microsoft.Spark, 0.6.0", "nuget: Microsoft.Spark.Extensions.Delta, 0.6.0"]`</span></span>

   * <span data-ttu-id="acecc-175">**プロパティ 3**</span><span class="sxs-lookup"><span data-stu-id="acecc-175">**Property 3**</span></span>
       * <span data-ttu-id="acecc-176">キー: &ensp;&ensp;`spark.dotnet.interpreter`</span><span class="sxs-lookup"><span data-stu-id="acecc-176">Key:&ensp;&ensp;`spark.dotnet.interpreter`</span></span>
       * <span data-ttu-id="acecc-177">値: `try`</span><span class="sxs-lookup"><span data-stu-id="acecc-177">Value: `try`</span></span>

   <span data-ttu-id="acecc-178">たとえば、次の画像は、プロパティ 1 を追加するための設定をキャプチャしたものです。</span><span class="sxs-lookup"><span data-stu-id="acecc-178">For example, the following image captures the setting for adding property 1:</span></span>

   ![構成の設定](./media/hdinsight-notebook-installation/add-sparkconfig.png)

   <span data-ttu-id="acecc-180">3 つのプロパティを追加したら、 **[保存]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-180">After adding the three properties, select **SAVE**.</span></span> <span data-ttu-id="acecc-181">構成の推奨事項に関する警告画面が表示された場合は、 **[PROCEED ANYWAY]\(警告を無視して続行\)** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-181">If you see a warning screen of config recommendations, select **PROCEED ANYWAY**.</span></span>

4. <span data-ttu-id="acecc-182">影響を受けたコンポーネントを再起動します。</span><span class="sxs-lookup"><span data-stu-id="acecc-182">Restart affected components.</span></span>

   <span data-ttu-id="acecc-183">新しいプロパティを追加したら、その変更の影響を受けたコンポーネントを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="acecc-183">After adding the new properties, you need to restart components that were affected by the changes.</span></span> <span data-ttu-id="acecc-184">上部にある **[再起動]** を選択して、ドロップダウンから **[影響を受けるものをすべて再起動する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="acecc-184">At the top, select **RESTART**, and then **Restart All Affected** from the drop-down.</span></span>

   ![構成の設定](./media/hdinsight-notebook-installation/restart-affected.png)

   <span data-ttu-id="acecc-186">メッセージが表示されたら、 **[CONFIRM RESTART ALL]\(すべて再起動\)** を選択して続行し、 **[OK]** をクリックして完了します。</span><span class="sxs-lookup"><span data-stu-id="acecc-186">When prompted, select **CONFIRM RESTART ALL** to continue, then click **OK** to finish.</span></span>

## <a name="submit-jobs-through-a-jupyter-notebook"></a><span data-ttu-id="acecc-187">Jupyter Notebook を使用してジョブを送信する</span><span class="sxs-lookup"><span data-stu-id="acecc-187">Submit jobs through a Jupyter notebook</span></span>

<span data-ttu-id="acecc-188">前の手順を完了したら、Jupyter Notebook を使用して .NET for Apache Spark ジョブを送信できるようになります。</span><span class="sxs-lookup"><span data-stu-id="acecc-188">After finishing the previous steps, you can now submit your .NET for Apache Spark jobs through Jupyter notebooks.</span></span>

1. <span data-ttu-id="acecc-189">新しい .NET for Apache Spark ノートブックを作成します。</span><span class="sxs-lookup"><span data-stu-id="acecc-189">Create a new .NET for Apache Spark notebook.</span></span> <span data-ttu-id="acecc-190">Azure portal で、HDI クラスターから Jupyter Notebook を起動します。</span><span class="sxs-lookup"><span data-stu-id="acecc-190">Launch a Jupyter notebook from your HDI cluster in the Azure portal.</span></span>

   ![Jupyter Notebook を起動する](./media/hdinsight-notebook-installation/launch-notebook.png)

   <span data-ttu-id="acecc-192">次に、 **[新規]**  >  **[.NET Spark (C#)]** の順に選択して、ノートブックを作成します。</span><span class="sxs-lookup"><span data-stu-id="acecc-192">Then, select **New** > **.NET Spark (C#)** to create a notebook.</span></span>

   ![Jupyter Notebook](./media/hdinsight-notebook-installation/create-sparkdotnet-notebook.png)

2. <span data-ttu-id="acecc-194">.NET for Apache Spark を使用してジョブを送信します。</span><span class="sxs-lookup"><span data-stu-id="acecc-194">Submit jobs using .NET for Apache Spark.</span></span>

   <span data-ttu-id="acecc-195">次のコード スニペットを使用して、データフレームを作成します。</span><span class="sxs-lookup"><span data-stu-id="acecc-195">Use the following code snippet to create a DataFrame:</span></span>

   ```csharp
   var df = spark.Range(0,5);
   df.Show();
   ```

   ![Spark ジョブを送信する](./media/hdinsight-notebook-installation/create-df.png)

   <span data-ttu-id="acecc-197">次のコード スニペットを使用して、ユーザー定義関数 (UDF) を登録し、データフレームを指定してその UDF を使用します。</span><span class="sxs-lookup"><span data-stu-id="acecc-197">Use the following code snippet to register a user-defined function (UDF) and use the UDF with DataFrames:</span></span>

   ```csharp
   var myawesomeudf = Udf<int, string>((id) => $"hello {id}");
   df.Select(myawesomeudf(df["id"])).Show();
   ```

   ![Spark ジョブを送信する](./media/hdinsight-notebook-installation/run-udf.png)

## <a name="next-steps"></a><span data-ttu-id="acecc-199">次の手順</span><span class="sxs-lookup"><span data-stu-id="acecc-199">Next steps</span></span>

* [<span data-ttu-id="acecc-200">.NET for Apache Spark アプリケーションを Azure HDInsight にデプロイする</span><span class="sxs-lookup"><span data-stu-id="acecc-200">Deploy a .NET for Apache Spark application to Azure HDInsight</span></span>](../tutorials/hdinsight-deployment.md)
* [<span data-ttu-id="acecc-201">HDInsight のドキュメント</span><span class="sxs-lookup"><span data-stu-id="acecc-201">HDInsight Documentation</span></span>](https://docs.microsoft.com/azure/hdinsight/)
