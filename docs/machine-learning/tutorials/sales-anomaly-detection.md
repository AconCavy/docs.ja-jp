---
title: 'チュートリアル: 製品売上の異常を検出する'
description: 製品売上データの異常検出アプリケーションを構築する方法について説明します。 このチュートリアルでは、Visual Studio 2019 の C# を使って .NET Core コンソール アプリケーションを作成します。
ms.date: 06/30/2020
ms.topic: tutorial
ms.custom: mvc, title-hack-0612
ms.openlocfilehash: cf61f197e4befebdbb1fbf2ca4cbcdc61c48780a
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281668"
---
# <a name="tutorial-detect-anomalies-in-product-sales-with-mlnet"></a><span data-ttu-id="a242f-104">チュートリアル: ML.NET で製品売上の異常を検出する</span><span class="sxs-lookup"><span data-stu-id="a242f-104">Tutorial: Detect anomalies in product sales with ML.NET</span></span>

<span data-ttu-id="a242f-105">製品売上データの異常検出アプリケーションを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a242f-105">Learn how to build an anomaly detection application for product sales data.</span></span> <span data-ttu-id="a242f-106">このチュートリアルでは、Visual Studio の C# を使って .NET Core コンソール アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-106">This tutorial creates a .NET Core console application using C# in Visual Studio.</span></span>

<span data-ttu-id="a242f-107">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a242f-107">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a242f-108">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="a242f-108">Load the data</span></span>
> * <span data-ttu-id="a242f-109">スパイクの異常検出のために変換を作成する</span><span class="sxs-lookup"><span data-stu-id="a242f-109">Create a transform for spike anomaly detection</span></span>
> * <span data-ttu-id="a242f-110">変換を使用してスパイクの異常を検出する</span><span class="sxs-lookup"><span data-stu-id="a242f-110">Detect spike anomalies with the transform</span></span>
> * <span data-ttu-id="a242f-111">変化点の異常検出のために変換を作成する</span><span class="sxs-lookup"><span data-stu-id="a242f-111">Create a transform for change point anomaly detection</span></span>
> * <span data-ttu-id="a242f-112">変換を使用して変化点の異常を検出する</span><span class="sxs-lookup"><span data-stu-id="a242f-112">Detect change point anomalies with the transform</span></span>

<span data-ttu-id="a242f-113">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="a242f-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a242f-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a242f-114">Prerequisites</span></span>

* <span data-ttu-id="a242f-115">[Visual Studio 2017 バージョン 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)が ".NET Core クロスプラットフォーム開発" ワークロードと共にインストールされている。</span><span class="sxs-lookup"><span data-stu-id="a242f-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

* [<span data-ttu-id="a242f-116">product-sales.csv データセット</span><span class="sxs-lookup"><span data-stu-id="a242f-116">The product-sales.csv dataset</span></span>](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv)

>[!NOTE]
> <span data-ttu-id="a242f-117">`product-sales.csv` のデータ形式は、DataMarket が出典であるデータセット "Shampoo Sales Over a Three Year Period" (過去 3 年間のシャンプーの売上) に基づいており、Rob Hyndman が作成した Time Series Data Library (TSDL) で提供されています。</span><span class="sxs-lookup"><span data-stu-id="a242f-117">The data format in `product-sales.csv` is based on the dataset “Shampoo Sales Over a Three Year Period” originally sourced from DataMarket and provided by Time Series Data Library (TSDL), created by Rob Hyndman.</span></span>
> <span data-ttu-id="a242f-118">"Shampoo Sales Over a Three Year Period" データセットは、DataMarket Default Open License の下でライセンスを受けています。</span><span class="sxs-lookup"><span data-stu-id="a242f-118">“Shampoo Sales Over a Three Year Period” Dataset Licensed Under the DataMarket Default Open License.</span></span>

## <a name="create-a-console-application"></a><span data-ttu-id="a242f-119">コンソール アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="a242f-119">Create a console application</span></span>

1. <span data-ttu-id="a242f-120">"ProductSalesAnomalyDetection" という **.NET Core コンソール アプリケーション**を作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-120">Create a **.NET Core Console Application** called "ProductSalesAnomalyDetection".</span></span>

2. <span data-ttu-id="a242f-121">データ セット ファイルを保存するために、プロジェクトに *Data* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-121">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="a242f-122">**Microsoft.ML NuGet パッケージ**をインストールします。</span><span class="sxs-lookup"><span data-stu-id="a242f-122">Install the **Microsoft.ML NuGet Package**:</span></span>

    [!INCLUDE [mlnet-current-nuget-version](../../../includes/mlnet-current-nuget-version.md)]

    <span data-ttu-id="a242f-123">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a242f-123">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="a242f-124">[パッケージ ソース] として [nuget.org] を選択します。[参照] タブを選択し、「**Microsoft.ML**」を検索し、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="a242f-124">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML** and select the **Install** button.</span></span> <span data-ttu-id="a242f-125">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a242f-125">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span> <span data-ttu-id="a242f-126">**Microsoft.ML.TimeSeries** についてもこれらの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a242f-126">Repeat these steps for **Microsoft.ML.TimeSeries**.</span></span>

4. <span data-ttu-id="a242f-127">*Program.cs* の先頭に次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-127">Add the following `using` statements at the top of your *Program.cs* file:</span></span>

    [!code-csharp[AddUsings](./snippets/sales-anomaly-detection/csharp/Program.cs#AddUsings "Add necessary usings")]

### <a name="download-your-data"></a><span data-ttu-id="a242f-128">データをダウンロードする</span><span class="sxs-lookup"><span data-stu-id="a242f-128">Download your data</span></span>

1. <span data-ttu-id="a242f-129">データセットをダウンロードし、以前に作成した *Data* フォルダーに保存します。</span><span class="sxs-lookup"><span data-stu-id="a242f-129">Download the dataset and save it to the *Data* folder you previously created:</span></span>

   * <span data-ttu-id="a242f-130">[*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) を右クリックし、[名前を付けてリンクを保存 (またはターゲット)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a242f-130">Right click on [*product-sales.csv*](https://raw.githubusercontent.com/dotnet/machinelearning-samples/master/samples/csharp/getting-started/AnomalyDetection_Sales/SpikeDetection/Data/product-sales.csv) and select "Save Link (or Target) As..."</span></span>

     <span data-ttu-id="a242f-131">\*.csv ファイルを *Data* フォルダーに保存したことを確認します。または他の場所に保存した後に、\*.csv ファイルを *Data* フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="a242f-131">Make sure you either save the \*.csv file to the *Data* folder, or after you save it elsewhere, move the \*.csv file to the *Data* folder.</span></span>

2. <span data-ttu-id="a242f-132">ソリューション エクスプローラーで、\*.csv ファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a242f-132">In Solution Explorer, right-click the \*.csv file and select **Properties**.</span></span> <span data-ttu-id="a242f-133">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="a242f-133">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

<span data-ttu-id="a242f-134">次の表は、\*.csv ファイルのデータのプレビューです。</span><span class="sxs-lookup"><span data-stu-id="a242f-134">The following table is a data preview from your \*.csv file:</span></span>

|<span data-ttu-id="a242f-135">月</span><span class="sxs-lookup"><span data-stu-id="a242f-135">Month</span></span>  |<span data-ttu-id="a242f-136">ProductSales</span><span class="sxs-lookup"><span data-stu-id="a242f-136">ProductSales</span></span> |
|-------|-------------|
|<span data-ttu-id="a242f-137">1-Jan</span><span class="sxs-lookup"><span data-stu-id="a242f-137">1-Jan</span></span>  |    <span data-ttu-id="a242f-138">271</span><span class="sxs-lookup"><span data-stu-id="a242f-138">271</span></span>      |
|<span data-ttu-id="a242f-139">2-Jan</span><span class="sxs-lookup"><span data-stu-id="a242f-139">2-Jan</span></span>  |    <span data-ttu-id="a242f-140">150.9</span><span class="sxs-lookup"><span data-stu-id="a242f-140">150.9</span></span>    |
|<span data-ttu-id="a242f-141">.....</span><span class="sxs-lookup"><span data-stu-id="a242f-141">.....</span></span>  |    <span data-ttu-id="a242f-142">.....</span><span class="sxs-lookup"><span data-stu-id="a242f-142">.....</span></span>    |
|<span data-ttu-id="a242f-143">1-Feb</span><span class="sxs-lookup"><span data-stu-id="a242f-143">1-Feb</span></span>  |    <span data-ttu-id="a242f-144">199.3</span><span class="sxs-lookup"><span data-stu-id="a242f-144">199.3</span></span>    |
|<span data-ttu-id="a242f-145">.....</span><span class="sxs-lookup"><span data-stu-id="a242f-145">.....</span></span>  |    <span data-ttu-id="a242f-146">.....</span><span class="sxs-lookup"><span data-stu-id="a242f-146">.....</span></span>    |

### <a name="create-classes-and-define-paths"></a><span data-ttu-id="a242f-147">クラスを作成してパスを定義する</span><span class="sxs-lookup"><span data-stu-id="a242f-147">Create classes and define paths</span></span>

<span data-ttu-id="a242f-148">次に、入力クラスと予測クラスのデータ構造を定義します。</span><span class="sxs-lookup"><span data-stu-id="a242f-148">Next, define your input and prediction class data structures.</span></span>

<span data-ttu-id="a242f-149">プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="a242f-150">**ソリューション エクスプローラー**で、プロジェクトを右クリックして、 **[追加]、[新しいアイテム]** の順に選びます。</span><span class="sxs-lookup"><span data-stu-id="a242f-150">In **Solution Explorer**, right-click the project, and then select **Add > New Item**.</span></span>

2. <span data-ttu-id="a242f-151">**[新しい項目の追加] ダイアログ ボックス**で、 **[クラス]** を選択し、 **[名前]** フィールドを「*ProductSalesData.cs*」に変更します。</span><span class="sxs-lookup"><span data-stu-id="a242f-151">In the **Add New Item dialog box**, select **Class** and change the **Name** field to *ProductSalesData.cs*.</span></span> <span data-ttu-id="a242f-152">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="a242f-152">Then, select the **Add** button.</span></span>

   <span data-ttu-id="a242f-153">コード エディターで *ProductSalesData.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="a242f-153">The *ProductSalesData.cs* file opens in the code editor.</span></span>

3. <span data-ttu-id="a242f-154">次の `using` ステートメントを *ProductSalesData.cs* の先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-154">Add the following `using` statement to the top of *ProductSalesData.cs*:</span></span>

   ```csharp
   using Microsoft.ML.Data;
   ```

4. <span data-ttu-id="a242f-155">既存のクラス定義を削除し、`ProductSalesData` と `ProductSalesPrediction` の 2 つのクラスを含む次のコードを *ProductSalesData.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-155">Remove the existing class definition and add the following code, which has two classes `ProductSalesData` and `ProductSalesPrediction`, to the *ProductSalesData.cs* file:</span></span>

    [!code-csharp[DeclareTypes](./snippets/sales-anomaly-detection/csharp/ProductSalesData.cs#DeclareTypes "Declare data record types")]

    <span data-ttu-id="a242f-156">`ProductSalesData` は入力データ クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a242f-156">`ProductSalesData` specifies an input data class.</span></span> <span data-ttu-id="a242f-157">[LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) 属性は、データセット内のどの列 (列インデックス) を読み込むかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a242f-157">The [LoadColumn](xref:Microsoft.ML.Data.LoadColumnAttribute.%23ctor%28System.Int32%29) attribute specifies which columns (by column index) in the dataset should be loaded.</span></span>

    <span data-ttu-id="a242f-158">`ProductSalesPrediction` では予測データ クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a242f-158">`ProductSalesPrediction` specifies the prediction data class.</span></span> <span data-ttu-id="a242f-159">異常検出の場合、予測は異常、生スコア、p 値があるかどうかを示すアラートで構成されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-159">For anomaly detection, the prediction consists of an alert to indicate whether there is an anomaly, a raw score, and p-value.</span></span> <span data-ttu-id="a242f-160">p 値が 0 に近いほど、異常が発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="a242f-160">The closer the p-value is to 0, the more likely an anomaly has occurred.</span></span>

5. <span data-ttu-id="a242f-161">最近ダウンロードしたデータセット ファイルのパスと保存したモデル ファイルのパスを保持するために、2 つのグローバル フィールドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-161">Create two global fields to hold the recently downloaded dataset file path and the saved model file path:</span></span>

    * <span data-ttu-id="a242f-162">`_dataPath` には、モデルのトレーニングに使用するデータ セットのパスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a242f-162">`_dataPath` has the path to the dataset used to train the model.</span></span>
    * <span data-ttu-id="a242f-163">`_docsize` はデータセット ファイル内のレコード数です。</span><span class="sxs-lookup"><span data-stu-id="a242f-163">`_docsize` has the number of records in dataset file.</span></span> <span data-ttu-id="a242f-164">`_docSize` を `pvalueHistoryLength` の計算に使用します。</span><span class="sxs-lookup"><span data-stu-id="a242f-164">You'll use `_docSize` to calculate `pvalueHistoryLength`.</span></span>

6. <span data-ttu-id="a242f-165">`Main` メソッドのすぐ上にある行に次のコードを追加して、それらのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a242f-165">Add the following code to the line right above the `Main` method to specify those paths:</span></span>

    [!code-csharp[Declare global variables](./snippets/sales-anomaly-detection/csharp/Program.cs#DeclareGlobalVariables "Declare global variables")]

### <a name="initialize-variables-in-main"></a><span data-ttu-id="a242f-166">Main で変数を初期化する</span><span class="sxs-lookup"><span data-stu-id="a242f-166">Initialize variables in Main</span></span>

1. <span data-ttu-id="a242f-167">`Main` メソッドの `Console.WriteLine("Hello World!")` の行は、`mlContext` 変数を宣言して初期化する次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="a242f-167">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the `mlContext` variable:</span></span>

    [!code-csharp[CreateMLContext](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateMLContext "Create the ML Context")]

    <span data-ttu-id="a242f-168">[MLContext クラス](xref:Microsoft.ML.MLContext)は、すべての ML.NET 操作の開始点で、`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-168">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations, and initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="a242f-169">これは Entity Framework における `DBContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="a242f-169">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

### <a name="load-the-data"></a><span data-ttu-id="a242f-170">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="a242f-170">Load the data</span></span>

<span data-ttu-id="a242f-171">ML.NET 内のデータは、[IDataView クラス](xref:Microsoft.ML.IDataView)として表されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-171">Data in ML.NET is represented as an [IDataView class](xref:Microsoft.ML.IDataView).</span></span> <span data-ttu-id="a242f-172">`IDataView` は、表形式のデータ (数値とテキスト) を表すための柔軟で効率的な方法です。</span><span class="sxs-lookup"><span data-stu-id="a242f-172">`IDataView` is a flexible, efficient way of describing tabular data (numeric and text).</span></span> <span data-ttu-id="a242f-173">データはテキスト ファイルから、または他のソース (SQL データベースやログ ファイルなど) から `IDataView` オブジェクトに読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="a242f-173">Data can be loaded from a text file or from other sources (for example, SQL database or log files) to an `IDataView` object.</span></span>

1. <span data-ttu-id="a242f-174">`Main()` メソッドの次の行として次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-174">Add the following code as the next line of the `Main()` method:</span></span>

    [!code-csharp[LoadData](./snippets/sales-anomaly-detection/csharp/Program.cs#LoadData "loading dataset")]

    <span data-ttu-id="a242f-175">[LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) は、データ スキーマを定義し、ファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="a242f-175">The [LoadFromTextFile()](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%60%601%28Microsoft.ML.DataOperationsCatalog,System.String,System.Char,System.Boolean,System.Boolean,System.Boolean,System.Boolean%29) defines the data schema and reads in the file.</span></span> <span data-ttu-id="a242f-176">データ パス変数を取得して、`IDataView` を返します。</span><span class="sxs-lookup"><span data-stu-id="a242f-176">It takes in the data path variables and returns an `IDataView`.</span></span>

## <a name="time-series-anomaly-detection"></a><span data-ttu-id="a242f-177">時系列の異常検出</span><span class="sxs-lookup"><span data-stu-id="a242f-177">Time series anomaly detection</span></span>

<span data-ttu-id="a242f-178">異常検出によって、予期しない、または通常とは異なるイベントや動作にフラグが立てられます。</span><span class="sxs-lookup"><span data-stu-id="a242f-178">Anomaly detection flags unexpected or unusual events or behaviors.</span></span> <span data-ttu-id="a242f-179">これは、問題を探す場所の手がかりとなり、"これはおかしいだろうか" という問いの答えを見つけるために役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a242f-179">It gives clues where to look for problems and helps you answer the question "Is this weird?".</span></span>

!["これはおかしいだろうか" 異常検出の例。](./media/sales-anomaly-detection/time-series-anomaly-detection.png)

<span data-ttu-id="a242f-181">異常検出は、時系列データの異常値 (指定された入力の時系列上で、動作が予期されたものではない点、つまり "おかしい" 点) を検出するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="a242f-181">Anomaly detection is the process of detecting time-series data outliers; points on a given input time-series where the behavior isn't what was expected, or "weird".</span></span>

<span data-ttu-id="a242f-182">異常検出は、さまざまな場面で役立ちます。</span><span class="sxs-lookup"><span data-stu-id="a242f-182">Anomaly detection can be useful in lots of ways.</span></span> <span data-ttu-id="a242f-183">たとえば、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a242f-183">For instance:</span></span>

<span data-ttu-id="a242f-184">車を持っている場合に知りたいこと:このオイル ゲージの表示値は正常か。それとも漏れがあるか。</span><span class="sxs-lookup"><span data-stu-id="a242f-184">If you have a car, you might want to know: Is this oil gauge reading normal, or do I have a leak?</span></span>
<span data-ttu-id="a242f-185">電力消費量を監視している場合に知りたいこと:停電はあるか。</span><span class="sxs-lookup"><span data-stu-id="a242f-185">If you're monitoring power consumption, you’d want to know: Is there an outage?</span></span>

<span data-ttu-id="a242f-186">検出できる時系列の異常には 2 つの種類があります。</span><span class="sxs-lookup"><span data-stu-id="a242f-186">There are two types of time series anomalies that can be detected:</span></span>

* <span data-ttu-id="a242f-187">**スパイク**は、システム内の異常動作の一時的なバーストを示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-187">**Spikes** indicate temporary bursts of anomalous behavior in the system.</span></span>

* <span data-ttu-id="a242f-188">**変化点**は、システム内での長期にわたる永続的な変化の始まりを示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-188">**Change points** indicate the beginning of persistent changes over time in the system.</span></span>

<span data-ttu-id="a242f-189">ML.NET では、[独立した同一分散のデータセット](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables)には IID Spike Detection (IID スパイク検出) アルゴリズムまたは IID Change point Detection (IID 変化点検出) アルゴリズムが適しています。</span><span class="sxs-lookup"><span data-stu-id="a242f-189">In ML.NET, The IID Spike Detection or IID Change point Detection algorithms are suited for [independent and identically distributed datasets](https://en.wikipedia.org/wiki/Independent_and_identically_distributed_random_variables).</span></span>

<span data-ttu-id="a242f-190">他のチュートリアルのモデルとは異なり、時系列の異常検出器の変換は入力データで直接操作されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-190">Unlike the models in the other tutorials, the time series anomaly detector transforms operate directly on input data.</span></span> <span data-ttu-id="a242f-191">`IEstimator.Fit()` メソッドでは、変換を生成するためにトレーニング データを必要としません。</span><span class="sxs-lookup"><span data-stu-id="a242f-191">The `IEstimator.Fit()` method does not need training data to produce the transform.</span></span> <span data-ttu-id="a242f-192">データ スキーマは必要ですが、`ProductSalesData` の空のリストから生成されたデータ ビューによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-192">It does need the data schema though, which is provided by a data view generated from an empty list of `ProductSalesData`.</span></span>

<span data-ttu-id="a242f-193">スパイクと変化点の検出には、同じ製品売上データを分析します。</span><span class="sxs-lookup"><span data-stu-id="a242f-193">You'll analyze the same product sales data to detect spikes and change points.</span></span> <span data-ttu-id="a242f-194">構築とトレーニング モデル プロセスは、スパイク検出と変化点検出で同じです。主な違いは、使用される具体的な検出アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="a242f-194">The building and training model process is the same for spike detection and change point detection; the main difference is the specific detection algorithm used.</span></span>

## <a name="spike-detection"></a><span data-ttu-id="a242f-195">スパイク検出</span><span class="sxs-lookup"><span data-stu-id="a242f-195">Spike detection</span></span>

<span data-ttu-id="a242f-196">スパイク検出の目的は、時系列データ値の大部分と大きく異なる突然の一時的なバーストを特定することです。</span><span class="sxs-lookup"><span data-stu-id="a242f-196">The goal of spike detection is to identify sudden yet temporary bursts that significantly differ from the majority of the time series data values.</span></span> <span data-ttu-id="a242f-197">このような疑わしいまれな項目、イベント、または観測値を適時に検出して最小限に抑えることが重要です。</span><span class="sxs-lookup"><span data-stu-id="a242f-197">It's important to detect these suspicious rare items, events, or observations in a timely manner to be minimized.</span></span> <span data-ttu-id="a242f-198">次のようなアプローチを利用すると、停電、サイバー攻撃、バイラル Web コンテンツなど、さまざまな異常を検出できます。</span><span class="sxs-lookup"><span data-stu-id="a242f-198">The following approach can be used to detect a variety of anomalies such as: outages, cyber-attacks, or viral web content.</span></span> <span data-ttu-id="a242f-199">次の図は、時系列データセットのスパイクの例です。</span><span class="sxs-lookup"><span data-stu-id="a242f-199">The following image is an example of spikes in a time series dataset:</span></span>

![2 つのスパイク検出を示すスクリーンショット。](./media/sales-anomaly-detection/two-spike-detections.png)

### <a name="add-the-createemptydataview-method"></a><span data-ttu-id="a242f-201">CreateEmptyDataView () メソッドを追加する</span><span class="sxs-lookup"><span data-stu-id="a242f-201">Add the CreateEmptyDataView() method</span></span>

<span data-ttu-id="a242f-202">次のメソッドを `Program.cs` に追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-202">Add the following method to `Program.cs`:</span></span>

[!code-csharp[CreateEmptyDataView](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEmptyDataView)]

<span data-ttu-id="a242f-203">`CreateEmptyDataView()` では、`IEstimator.Fit()` メソッドへの入力として使用される正しいスキーマで、空のデータ ビュー オブジェクトを生成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-203">The `CreateEmptyDataView()` produces an empty data view object with the correct schema to be used as input to the `IEstimator.Fit()` method.</span></span>

### <a name="create-the-detectspike-method"></a><span data-ttu-id="a242f-204">DetectSpike() メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-204">Create the DetectSpike() method</span></span>

<span data-ttu-id="a242f-205">`DetectSpike()` メソッド:</span><span class="sxs-lookup"><span data-stu-id="a242f-205">The `DetectSpike()` method:</span></span>

* <span data-ttu-id="a242f-206">エスティメーターから変換を作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-206">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="a242f-207">売上データ履歴に基づいてスパイクを検出します。</span><span class="sxs-lookup"><span data-stu-id="a242f-207">Detects spikes based on historical sales data.</span></span>
* <span data-ttu-id="a242f-208">結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-208">Displays the results.</span></span>

1. <span data-ttu-id="a242f-209">`Main()` メソッドの直後に、次のコードを使用して `DetectSpike()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-209">Create the `DetectSpike()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectSpike(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="a242f-210">スパイク検出のために、[IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) を使用してモデルをトレーニングします。</span><span class="sxs-lookup"><span data-stu-id="a242f-210">Use the [IidSpikeEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidSpikeEstimator) to train the model for spike detection.</span></span> <span data-ttu-id="a242f-211">それを次のコードを使用して `DetectSpike()` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-211">Add it to the `DetectSpike()` method with the following code:</span></span>

    [!code-csharp[AddSpikeTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddSpikeTrainer)]

1. <span data-ttu-id="a242f-212">`DetectSpike()` メソッドの次のコード行として以下を追加して、スパイク検出の変換を作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-212">Create the spike detection transform by adding the following as the next line of code in the `DetectSpike()` method:</span></span>

    [!code-csharp[TrainModel1](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel1)]

1. <span data-ttu-id="a242f-213">次のコード行を追加して、`productSales` データを `DetectSpike()` メソッドの次の行に変換します。</span><span class="sxs-lookup"><span data-stu-id="a242f-213">Add the following line of code to transform the `productSales` data as the next line in the `DetectSpike()` method:</span></span>

    [!code-csharp[TransformData1](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData1)]

    <span data-ttu-id="a242f-214">前のコードでは、[Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) メソッドを使用して、データセットの複数の入力行の予測を行います。</span><span class="sxs-lookup"><span data-stu-id="a242f-214">The previous code uses the [Transform()](xref:Microsoft.ML.ITransformer.Transform%2A) method to make predictions for multiple input rows of a dataset.</span></span>

1. <span data-ttu-id="a242f-215">表示を簡単にするために、次のコードを使用し、[CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) メソッドを使って `transformedData` を厳密に型指定された `IEnumerable` に変換します。</span><span class="sxs-lookup"><span data-stu-id="a242f-215">Convert your `transformedData` into a strongly typed `IEnumerable` for easier display using the [CreateEnumerable()](xref:Microsoft.ML.DataOperationsCatalog.CreateEnumerable%2A) method with the following code:</span></span>

    [!code-csharp[CreateEnumerable1](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable1)]

1. <span data-ttu-id="a242f-216">次の <xref:System.Console.WriteLine?displayProperty=nameWithType> コードを使用して表示ヘッダー行を作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-216">Create a display header line using the following <xref:System.Console.WriteLine?displayProperty=nameWithType> code:</span></span>

    [!code-csharp[DisplayHeader1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader1)]

    <span data-ttu-id="a242f-217">スパイクの検出結果には、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-217">You'll display the following information in your spike detection results:</span></span>

    * <span data-ttu-id="a242f-218">`Alert` は、特定のデータ ポイントに対するスパイク アラートを示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-218">`Alert` indicates a spike alert for a given data point.</span></span>
    * <span data-ttu-id="a242f-219">`Score`は、データセット内の特定のデータ ポイントに対する `ProductSales` 値です。</span><span class="sxs-lookup"><span data-stu-id="a242f-219">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="a242f-220">`P-Value` "P" は確率を表します。</span><span class="sxs-lookup"><span data-stu-id="a242f-220">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="a242f-221">p 値が 0 に近いほど、データ ポイントが異常になる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="a242f-221">The closer the p-value is to 0, the more likely the data point is an anomaly.</span></span>

1. <span data-ttu-id="a242f-222">次のコードを使用して `predictions` `IEnumerable` を反復処理し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-222">Use the following code to iterate through the `predictions` `IEnumerable` and display the results:</span></span>

    [!code-csharp[DisplayResults1](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults1)]

1. <span data-ttu-id="a242f-223">`DetectSpike()` メソッドに対する呼び出しを `Main()` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-223">Add the call to the `DetectSpike()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectSpike](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectSpike)]

## <a name="spike-detection-results"></a><span data-ttu-id="a242f-224">スパイクの検出結果</span><span class="sxs-lookup"><span data-stu-id="a242f-224">Spike detection results</span></span>

<span data-ttu-id="a242f-225">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="a242f-225">Your results should be similar to the following.</span></span> <span data-ttu-id="a242f-226">処理中にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-226">During processing, messages are displayed.</span></span> <span data-ttu-id="a242f-227">警告または処理メッセージが表示されることがありますが、</span><span class="sxs-lookup"><span data-stu-id="a242f-227">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a242f-228">わかりやすくするために、一部のメッセージは次の結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="a242f-228">Some of the messages have been removed from the following results for clarity.</span></span>

```console
Detect temporary changes in pattern
=============== Training the model ===============
=============== End of training process ===============
Alert   Score   P-Value
0       271.00  0.50
0       150.90  0.00
0       188.10  0.41
0       124.30  0.13
0       185.30  0.47
0       173.50  0.47
0       236.80  0.19
0       229.50  0.27
0       197.80  0.48
0       127.90  0.13
1       341.50  0.00 <-- Spike detected
0       190.90  0.48
0       199.30  0.48
0       154.50  0.24
0       215.10  0.42
0       278.30  0.19
0       196.40  0.43
0       292.00  0.17
0       231.00  0.45
0       308.60  0.18
0       294.90  0.19
1       426.60  0.00 <-- Spike detected
0       269.50  0.47
0       347.30  0.21
0       344.70  0.27
0       445.40  0.06
0       320.90  0.49
0       444.30  0.12
0       406.30  0.29
0       442.40  0.21
1       580.50  0.00 <-- Spike detected
0       412.60  0.45
1       687.00  0.01 <-- Spike detected
0       480.30  0.40
0       586.30  0.20
0       651.90  0.14
```

## <a name="change-point-detection"></a><span data-ttu-id="a242f-229">変化点検出</span><span class="sxs-lookup"><span data-stu-id="a242f-229">Change point detection</span></span>

<span data-ttu-id="a242f-230">`Change points` は、レベルの変化や傾向など、時系列のイベント ストリームの値分布の永続的な変化です。</span><span class="sxs-lookup"><span data-stu-id="a242f-230">`Change points` are persistent changes in a time series event stream distribution of values, like level changes and trends.</span></span> <span data-ttu-id="a242f-231">こうした永続的な変化は、`spikes` よりもはるかに長く続き、壊滅的なイベントを示している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a242f-231">These persistent changes last much longer than `spikes` and could indicate catastrophic event(s).</span></span> <span data-ttu-id="a242f-232">通常、`Change points` は目視ではわかりませんが、次のような方法を使用してデータから検出できます。</span><span class="sxs-lookup"><span data-stu-id="a242f-232">`Change points` are not usually visible to the naked eye, but can be detected in your data using approaches such as in the following method.</span></span>  <span data-ttu-id="a242f-233">次の図は、変化点検出の例です。</span><span class="sxs-lookup"><span data-stu-id="a242f-233">The following image is an example of a change point detection:</span></span>

![2 つの変更点検出を示すスクリーンショット。](./media/sales-anomaly-detection/change-point-detection.png)

### <a name="create-the-detectchangepoint-method"></a><span data-ttu-id="a242f-235">DetectChangepoint() メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-235">Create the DetectChangepoint() method</span></span>

<span data-ttu-id="a242f-236">`DetectChangepoint()` メソッドは次のタスクを実行します。</span><span class="sxs-lookup"><span data-stu-id="a242f-236">The `DetectChangepoint()` method executes the following tasks:</span></span>

* <span data-ttu-id="a242f-237">エスティメーターから変換を作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-237">Creates the transform from the estimator.</span></span>
* <span data-ttu-id="a242f-238">売上データ履歴に基づいて変更点を検出します。</span><span class="sxs-lookup"><span data-stu-id="a242f-238">Detects change points based on historical sales data.</span></span>
* <span data-ttu-id="a242f-239">結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-239">Displays the results.</span></span>

1. <span data-ttu-id="a242f-240">`Main()` メソッドの直後に、次のコードを使用して `DetectChangepoint()` メソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-240">Create the `DetectChangepoint()` method, just after the `Main()` method, using the following code:</span></span>

    ```csharp
    static void DetectChangepoint(MLContext mlContext, int docSize, IDataView productSales)
    {

    }
    ```

1. <span data-ttu-id="a242f-241">次のコードを使って `DetectChangepoint()` メソッドで [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) を作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-241">Create the [iidChangePointEstimator](xref:Microsoft.ML.Transforms.TimeSeries.IidChangePointEstimator) in the `DetectChangepoint()` method with the following code:</span></span>

    [!code-csharp[AddChangepointTrainer](./snippets/sales-anomaly-detection/csharp/Program.cs#AddChangepointTrainer)]

1. <span data-ttu-id="a242f-242">前に行ったように、`DetectChangePoint()` メソッドに次のコード行を追加して、エスティメーターから変換を作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-242">As you did previously, create the transform from the estimator by adding the following line of code in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[TrainModel2](./snippets/sales-anomaly-detection/csharp/Program.cs#TrainModel2)]

1. <span data-ttu-id="a242f-243">`Transform()` メソッドを使用して、次のコードを `DetectChangePoint()` に追加してデータを変換します。</span><span class="sxs-lookup"><span data-stu-id="a242f-243">Use the `Transform()` method to transform the data by adding the following code to `DetectChangePoint()`:</span></span>

    [!code-csharp[TransformData2](./snippets/sales-anomaly-detection/csharp/Program.cs#TransformData2)]

1. <span data-ttu-id="a242f-244">以前と同様に、表示を簡単にするために、次のコードを使用し、`CreateEnumerable()` メソッドを使って `transformedData` を厳密に型指定された `IEnumerable` に変換します。</span><span class="sxs-lookup"><span data-stu-id="a242f-244">As you did previously, convert your `transformedData` into a strongly typed `IEnumerable` for easier display using the `CreateEnumerable()`method with the following code:</span></span>

    [!code-csharp[CreateEnumerable2](./snippets/sales-anomaly-detection/csharp/Program.cs#CreateEnumerable2)]

1. <span data-ttu-id="a242f-245">`DetectChangePoint()` メソッドの次の行として次のコードを使用して、表示ヘッダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="a242f-245">Create a display header with the following code as the next line in the `DetectChangePoint()` method:</span></span>

    [!code-csharp[DisplayHeader2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayHeader2)]

    <span data-ttu-id="a242f-246">変化点の検出結果には、次の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-246">You'll display the following information in your change point detection results:</span></span>

    * <span data-ttu-id="a242f-247">`Alert` は、特定のデータ ポイントに対する変化点アラートを示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-247">`Alert` indicates a change point alert for a given data point.</span></span>
    * <span data-ttu-id="a242f-248">`Score`は、データセット内の特定のデータ ポイントに対する `ProductSales` 値です。</span><span class="sxs-lookup"><span data-stu-id="a242f-248">`Score` is the `ProductSales` value for a given data point in the dataset.</span></span>
    * <span data-ttu-id="a242f-249">`P-Value` "P" は確率を表します。</span><span class="sxs-lookup"><span data-stu-id="a242f-249">`P-Value` The "P" stands for probability.</span></span> <span data-ttu-id="a242f-250">P 値が 0 に近いほど、データ ポイントが異常になる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="a242f-250">The closer the P-value is to 0, the more likely the data point is an anomaly.</span></span>
    * <span data-ttu-id="a242f-251">`Martingale value` は、一連の P 値に基づいて、データ ポイントがどの程度 "おかしい" かを特定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-251">`Martingale value` is used to identify how "weird" a data point is, based on the sequence of P-values.</span></span>

1. <span data-ttu-id="a242f-252">次のコードを使用して `predictions` `IEnumerable` を反復処理し、結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="a242f-252">Iterate through the `predictions` `IEnumerable` and display the results with the following code:</span></span>

    [!code-csharp[DisplayResults2](./snippets/sales-anomaly-detection/csharp/Program.cs#DisplayResults2)]

1. <span data-ttu-id="a242f-253">次の `DetectChangepoint()` メソッドに対する呼び出しを `Main()` メソッドに追加します。</span><span class="sxs-lookup"><span data-stu-id="a242f-253">Add the following call to the `DetectChangepoint()`method in the `Main()` method:</span></span>

    [!code-csharp[CallDetectChangepoint](./snippets/sales-anomaly-detection/csharp/Program.cs#CallDetectChangepoint)]

## <a name="change-point-detection-results"></a><span data-ttu-id="a242f-254">変化点の検出結果</span><span class="sxs-lookup"><span data-stu-id="a242f-254">Change point detection results</span></span>

<span data-ttu-id="a242f-255">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="a242f-255">Your results should be similar to the following.</span></span> <span data-ttu-id="a242f-256">処理中にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a242f-256">During processing, messages are displayed.</span></span> <span data-ttu-id="a242f-257">警告または処理メッセージが表示されることがありますが、</span><span class="sxs-lookup"><span data-stu-id="a242f-257">You may see warnings, or processing messages.</span></span> <span data-ttu-id="a242f-258">わかりやすくするために、一部のメッセージは次の結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="a242f-258">Some messages have been removed from the following results for clarity.</span></span>

```console
Detect Persistent changes in pattern
=============== Training the model Using Change Point Detection Algorithm===============
=============== End of training process ===============
Alert   Score   P-Value Martingale value
0       271.00  0.50    0.00
0       150.90  0.00    2.33
0       188.10  0.41    2.80
0       124.30  0.13    9.16
0       185.30  0.47    9.77
0       173.50  0.47    10.41
0       236.80  0.19    24.46
0       229.50  0.27    42.38
1       197.80  0.48    44.23 <-- alert is on, predicted changepoint
0       127.90  0.13    145.25
0       341.50  0.00    0.01
0       190.90  0.48    0.01
0       199.30  0.48    0.00
0       154.50  0.24    0.00
0       215.10  0.42    0.00
0       278.30  0.19    0.00
0       196.40  0.43    0.00
0       292.00  0.17    0.01
0       231.00  0.45    0.00
0       308.60  0.18    0.00
0       294.90  0.19    0.00
0       426.60  0.00    0.00
0       269.50  0.47    0.00
0       347.30  0.21    0.00
0       344.70  0.27    0.00
0       445.40  0.06    0.02
0       320.90  0.49    0.01
0       444.30  0.12    0.02
0       406.30  0.29    0.01
0       442.40  0.21    0.01
0       580.50  0.00    0.01
0       412.60  0.45    0.01
0       687.00  0.01    0.12
0       480.30  0.40    0.08
0       586.30  0.20    0.03
0       651.90  0.14    0.09
```

<span data-ttu-id="a242f-259">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="a242f-259">Congratulations!</span></span> <span data-ttu-id="a242f-260">これで、売上データのスパイクや変化点の異常を検出するための機械学習モデルを適切に構築できました。</span><span class="sxs-lookup"><span data-stu-id="a242f-260">You've now successfully built machine learning models for detecting spikes and change point anomalies in sales data.</span></span>

<span data-ttu-id="a242f-261">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="a242f-261">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/ProductSalesAnomalyDetection) repository.</span></span>

<span data-ttu-id="a242f-262">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="a242f-262">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="a242f-263">データを読み込む</span><span class="sxs-lookup"><span data-stu-id="a242f-263">Load the data</span></span>
> * <span data-ttu-id="a242f-264">スパイクの異常検出のためにモデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="a242f-264">Train the model for spike anomaly detection</span></span>
> * <span data-ttu-id="a242f-265">トレーニング済みモデルを使用してスパイクの異常を検出する</span><span class="sxs-lookup"><span data-stu-id="a242f-265">Detect spike anomalies with the trained model</span></span>
> * <span data-ttu-id="a242f-266">変化点の異常検出のためにモデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="a242f-266">Train the model for change point anomaly detection</span></span>
> * <span data-ttu-id="a242f-267">トレーニング済みモデルを使用して変化点の異常を検出する</span><span class="sxs-lookup"><span data-stu-id="a242f-267">Detect change point anomalies with the trained mode</span></span>

## <a name="next-steps"></a><span data-ttu-id="a242f-268">次の手順</span><span class="sxs-lookup"><span data-stu-id="a242f-268">Next steps</span></span>

<span data-ttu-id="a242f-269">Machine Learning サンプルの GitHub リポジトリを確認し、Power Consumption Anomaly Detection サンプルを調べてください。</span><span class="sxs-lookup"><span data-stu-id="a242f-269">Check out the Machine Learning samples GitHub repository to explore a Power Consumption Anomaly Detection sample.</span></span>
> [!div class="nextstepaction"]
> [<span data-ttu-id="a242f-270">dotnet/machinelearning-samples GitHub リポジトリ</span><span class="sxs-lookup"><span data-stu-id="a242f-270">dotnet/machinelearning-samples GitHub repository</span></span>](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/getting-started/AnomalyDetection_PowerMeterReadings)
