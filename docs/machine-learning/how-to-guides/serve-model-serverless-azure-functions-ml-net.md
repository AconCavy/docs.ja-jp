---
title: Azure Functions にモデルをデプロイする
description: Azure Functions を使用して、インターネット経由で予測用の ML.NET 感情分析機械学習モデルを提供します
ms.date: 11/07/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc, how-to
ms.openlocfilehash: 5ef6331950845b2900e33b2c51c308644ba17fd6
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733354"
---
# <a name="deploy-a-model-to-azure-functions"></a><span data-ttu-id="13055-103">Azure Functions にモデルをデプロイする</span><span class="sxs-lookup"><span data-stu-id="13055-103">Deploy a model to Azure Functions</span></span>

<span data-ttu-id="13055-104">Azure Functions のサーバーレス環境を介して、HTTP 経由での予測のために、事前トレーニング済みの ML.NET 機械学習モデルをデプロイする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="13055-104">Learn how to deploy a pre-trained ML.NET machine learning model for predictions over HTTP through an Azure Functions serverless environment.</span></span>

> [!NOTE]
> <span data-ttu-id="13055-105">このサンプルでは、`PredictionEnginePool` サービスのプレビュー バージョンを実行します。</span><span class="sxs-lookup"><span data-stu-id="13055-105">This sample runs a preview version of the `PredictionEnginePool` service.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="13055-106">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="13055-106">Prerequisites</span></span>

- <span data-ttu-id="13055-107">[Visual Studio 2017 バージョン 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)が ".NET Core クロスプラット フォーム開発" ワークロードおよび "Azure 開発" とともにインストールされていること。</span><span class="sxs-lookup"><span data-stu-id="13055-107">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) with the ".NET Core cross-platform development" workload and "Azure development" installed.</span></span>
- [<span data-ttu-id="13055-108">Azure Functions ツール</span><span class="sxs-lookup"><span data-stu-id="13055-108">Azure Functions Tools</span></span>](/azure/azure-functions/functions-develop-vs#check-your-tools-version)
- <span data-ttu-id="13055-109">PowerShell</span><span class="sxs-lookup"><span data-stu-id="13055-109">Powershell</span></span>
- <span data-ttu-id="13055-110">事前トレーニング済みのモデル。</span><span class="sxs-lookup"><span data-stu-id="13055-110">Pre-trained model.</span></span> <span data-ttu-id="13055-111">[ML.NET Sentiment Analysis のチュートリアル](../tutorials/sentiment-analysis.md)を使用して独自のモデルを構築するか、こちらの[事前トレーニング済みの感情分析の機械学習モデル](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)をダウンロードすること。</span><span class="sxs-lookup"><span data-stu-id="13055-111">Use the [ML.NET Sentiment Analysis tutorial](../tutorials/sentiment-analysis.md) to build your own model or download this [pre-trained sentiment analysis machine learning model](https://github.com/dotnet/samples/blob/master/machine-learning/models/sentimentanalysis/sentiment_model.zip)</span></span>

## <a name="azure-functions-sample-overview"></a><span data-ttu-id="13055-112">Azure Functions サンプルの概要</span><span class="sxs-lookup"><span data-stu-id="13055-112">Azure Functions sample overview</span></span>

<span data-ttu-id="13055-113">このサンプルは、事前トレーニング済みの二項分類モデルを使用してテキストのセンチメントを正または負として分類する、**C# HTTP トリガー Azure Functions アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="13055-113">This sample is a **C# HTTP Trigger Azure Functions application** that uses a pretrained binary classification model to categorize the sentiment of text as positive or negative.</span></span> <span data-ttu-id="13055-114">Azure Functions では、クラウド内の管理されたサーバーレス環境で小規模なコードを大規模に実行する簡単な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="13055-114">Azure Functions provides an easy way to run small pieces of code at scale on a managed serverless environment in the cloud.</span></span> <span data-ttu-id="13055-115">このサンプルのコードについては、GitHub の [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) リポジトリで見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="13055-115">The code for this sample can be found on the [dotnet/machinelearning-samples](https://github.com/dotnet/machinelearning-samples/tree/master/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction) repository on GitHub.</span></span>

## <a name="create-azure-functions-project"></a><span data-ttu-id="13055-116">Azure Functions プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="13055-116">Create Azure Functions project</span></span>

1. <span data-ttu-id="13055-117">Visual Studio 2017 を開きます。</span><span class="sxs-lookup"><span data-stu-id="13055-117">Open Visual Studio 2017.</span></span> <span data-ttu-id="13055-118">**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** をメニュー バーから選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-118">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="13055-119">**[新しいプロジェクト]** ダイアログで、 **[Visual C#]** ノードを選択し、 **[クラウド]** ノードを選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-119">In the **New Project** dialog, select the **Visual C#** node followed by the **Cloud** node.</span></span> <span data-ttu-id="13055-120">次に、**Azure Functions** プロジェクト テンプレートを選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-120">Then select the **Azure Functions** project template.</span></span> <span data-ttu-id="13055-121">**[名前]** テキスト ボックスに「SentimentAnalysisFunctionsApp」と入力し、 **[OK]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-121">In the **Name** text box, type "SentimentAnalysisFunctionsApp" and then select the **OK** button.</span></span>
1. <span data-ttu-id="13055-122">**[新しいプロジェクト]** ダイアログで、プロジェクト オプションの上のドロップダウンを開き、 **[Azure Functions v2 (.NET Core)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-122">In the **New Project** dialog, open the dropdown above the project options and select **Azure Functions v2 (.NET Core)**.</span></span> <span data-ttu-id="13055-123">次に、 **[Http トリガー]** プロジェクトを選択し、 **[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-123">Then, select the **Http trigger** project and then select the **OK** button.</span></span>
1. <span data-ttu-id="13055-124">モデルを保存するための *MLModels* という名前のディレクトリをプロジェクト内に作成します。</span><span class="sxs-lookup"><span data-stu-id="13055-124">Create a directory named *MLModels* in your project to save your model:</span></span>

    <span data-ttu-id="13055-125">**ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しいフォルダー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-125">In **Solution Explorer**, right-click on your project and select **Add** > **New Folder**.</span></span> <span data-ttu-id="13055-126">「MLModels」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="13055-126">Type "MLModels" and hit Enter.</span></span>

1. <span data-ttu-id="13055-127">**Microsoft.ML NuGet パッケージ** バージョン **1.3.1** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="13055-127">Install the **Microsoft.ML NuGet Package** version **1.3.1**:</span></span>

    <span data-ttu-id="13055-128">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-128">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="13055-129">[パッケージ ソース] として "nuget.org" を選択し、[参照] タブを選択して「**Microsoft.ML**」を検索します。一覧からそのパッケージを選択し、 **[インストール]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-129">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="13055-130">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-130">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="13055-131">**Microsoft.Azure.Functions.Extensions NuGet パッケージ**をインストールします。</span><span class="sxs-lookup"><span data-stu-id="13055-131">Install the **Microsoft.Azure.Functions.Extensions NuGet Package**:</span></span>

    <span data-ttu-id="13055-132">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-132">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="13055-133">パッケージ ソースとして "nuget.org" を選択します。[参照] タブを選択し、「**Microsoft.Azure.Functions.Extensions**」を検索します。一覧からそのパッケージを選択し、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-133">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Azure.Functions.Extensions**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="13055-134">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-134">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="13055-135">**Microsoft.Extensions.ML NuGet パッケージ** バージョン **0.15.1** をインストールします。</span><span class="sxs-lookup"><span data-stu-id="13055-135">Install the **Microsoft.Extensions.ML NuGet Package** version **0.15.1**:</span></span>

    <span data-ttu-id="13055-136">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-136">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="13055-137">パッケージ ソースとして "nuget.org" を選択します。[参照] タブを選択し、「**Microsoft.Extensions.ML**」を検索します。一覧からそのパッケージを選択して、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-137">Choose "nuget.org" as the Package source, select the Browse tab, search for **Microsoft.Extensions.ML**, select that package in the list, and select the **Install** button.</span></span> <span data-ttu-id="13055-138">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-138">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

1. <span data-ttu-id="13055-139">**Microsoft.NET.Sdk.Functions NuGet パッケージ** バージョン **1.0.28 以降**をインストールします。</span><span class="sxs-lookup"><span data-stu-id="13055-139">Install the **Microsoft.NET.Sdk.Functions NuGet Package** version **1.0.28+**:</span></span>

    <span data-ttu-id="13055-140">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-140">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="13055-141">パッケージ ソースとして "nuget.org" を選択します。[インストール済み] タブを選択し、「**Microsoft.NET.Sdk.Functions**」を検索します。一覧からそのパッケージを選択し、[バージョン] ドロップダウンから **1.0.28 以降**を選択し、 **[更新]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-141">Choose "nuget.org" as the Package source, select the Installed tab, search for **Microsoft.NET.Sdk.Functions**, select that package in the list, select **1.0.28 or later** from the Version dropdown, and select the **Update** button.</span></span> <span data-ttu-id="13055-142">**[変更のプレビュー]** ダイアログの **[OK]** を選択します。表示されているパッケージのライセンス条項に同意する場合は、 **[ライセンスの同意]** ダイアログの **[同意する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-142">Select the **OK** button on the **Preview Changes** dialog and then select the **I Accept** button on the **License Acceptance** dialog if you agree with the license terms for the packages listed.</span></span>

## <a name="add-pre-trained-model-to-project"></a><span data-ttu-id="13055-143">事前トレーニング済みモデルをプロジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="13055-143">Add pre-trained model to project</span></span>

1. <span data-ttu-id="13055-144">構築済みのモデルを *MLModels* フォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="13055-144">Copy your pre-built model to the *MLModels* folder.</span></span>
1. <span data-ttu-id="13055-145">ソリューション エクスプローラーで、構築済みのモデルのファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-145">In Solution Explorer, right-click your pre-built model file and select **Properties**.</span></span> <span data-ttu-id="13055-146">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="13055-146">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

## <a name="create-azure-function-to-analyze-sentiment"></a><span data-ttu-id="13055-147">Azure 関数を作成してセンチメントを分析する</span><span class="sxs-lookup"><span data-stu-id="13055-147">Create Azure Function to analyze sentiment</span></span>

<span data-ttu-id="13055-148">センチメントを予測するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="13055-148">Create a class to predict sentiment.</span></span> <span data-ttu-id="13055-149">プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-149">Add a new class to your project:</span></span>

1. <span data-ttu-id="13055-150">**ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-150">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>

1. <span data-ttu-id="13055-151">**[新しい項目の追加]** ダイアログ ボックスで、 **[Azure 関数]** を選択し、 **[名前]** フィールドを *SentimentData.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="13055-151">In the **Add New Item** dialog box, select **Azure Function** and change the **Name** field to *AnalyzeSentiment.cs*.</span></span> <span data-ttu-id="13055-152">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-152">Then, select the **Add** button.</span></span>

1. <span data-ttu-id="13055-153">**[新しい Azure 関数]** ダイアログ ボックスで、 **[Http トリガー]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-153">In the **New Azure Function** dialog box, select **Http Trigger**.</span></span> <span data-ttu-id="13055-154">次に、 **[OK]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-154">Then, select the **OK** button.</span></span>

    <span data-ttu-id="13055-155">コード エディターに *AnalyzeSentiment.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="13055-155">The *AnalyzeSentiment.cs* file opens in the code editor.</span></span> <span data-ttu-id="13055-156">*AnalyzeSentiment.cs* の先頭に次の `using` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-156">Add the following `using` statement to the top of *AnalyzeSentiment.cs*:</span></span>

    [!code-csharp [AnalyzeUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L1-L11)]

    <span data-ttu-id="13055-157">既定では、`AnalyzeSentiment` クラスは `static`です。</span><span class="sxs-lookup"><span data-stu-id="13055-157">By default, the `AnalyzeSentiment` class is `static`.</span></span> <span data-ttu-id="13055-158">クラス定義から `static` キーワードを必ず削除します。</span><span class="sxs-lookup"><span data-stu-id="13055-158">Make sure to remove the `static` keyword from the class definition.</span></span>

    ```csharp
    public class AnalyzeSentiment
    {

    }
    ```

## <a name="create-data-models"></a><span data-ttu-id="13055-159">データ モデルを作成する</span><span class="sxs-lookup"><span data-stu-id="13055-159">Create data models</span></span>

<span data-ttu-id="13055-160">入力データと予測のために、いくつかのクラスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13055-160">You need to create some classes for your input data and predictions.</span></span> <span data-ttu-id="13055-161">プロジェクトに新しいクラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-161">Add a new class to your project:</span></span>

1. <span data-ttu-id="13055-162">データ モデルを保存するための *DataModels* という名前のディレクトリをプロジェクト内に作成します。ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[追加]、[新しいフォルダー]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-162">Create a directory named *DataModels* in your project to save your data models: In Solution Explorer, right-click on your project and select **Add > New Folder**.</span></span> <span data-ttu-id="13055-163">「DataModels」と入力し、Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="13055-163">Type "DataModels" and hit Enter.</span></span>
2. <span data-ttu-id="13055-164">ソリューション エクスプローラーで、*DataModels* ディレクトリを右クリックし、 **[追加]、[新しいアイテム]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-164">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
3. <span data-ttu-id="13055-165">**[新しい項目の追加]** ダイアログボックスで **[クラス]** を選択し、 **[名前]** フィールドを *SentimentData.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="13055-165">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentData.cs*.</span></span> <span data-ttu-id="13055-166">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-166">Then, select the **Add** button.</span></span>

    <span data-ttu-id="13055-167">コードエディターで *SentimentData.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="13055-167">The *SentimentData.cs* file opens in the code editor.</span></span> <span data-ttu-id="13055-168">*SentimentData.cs* の先頭に次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-168">Add the following using statement to the top of *SentimentData.cs*:</span></span>

    [!code-csharp [SentimentDataUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L1)]

    <span data-ttu-id="13055-169">既存のクラス定義を削除し、次のコードを *SentimentData.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-169">Remove the existing class definition and add the following code to the *SentimentData.cs* file:</span></span>

    [!code-csharp [SentimentData](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentData.cs#L5-L13)]

4. <span data-ttu-id="13055-170">ソリューションエクスプローラーで、*DataModels* ディレクトリを右クリックし、 **[追加] > [新しいアイテム]** の順に選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-170">In Solution Explorer, right-click the *DataModels* directory, and then select **Add > New Item**.</span></span>
5. <span data-ttu-id="13055-171">**[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを *SentimentPrediction.cs* に変更します。</span><span class="sxs-lookup"><span data-stu-id="13055-171">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *SentimentPrediction.cs*.</span></span> <span data-ttu-id="13055-172">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-172">Then, select the **Add** button.</span></span> <span data-ttu-id="13055-173">コード エディターに *SentimentPrediction.cs* ファイルが開きます。</span><span class="sxs-lookup"><span data-stu-id="13055-173">The *SentimentPrediction.cs* file opens in the code editor.</span></span> <span data-ttu-id="13055-174">*SentimentPrediction.cs* の先頭に次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-174">Add the following using statement to the top of *SentimentPrediction.cs*:</span></span>

    [!code-csharp [SentimentPredictionUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L1)]

    <span data-ttu-id="13055-175">既存のクラス定義を削除し、次のコードを *SentimentPrediction.cs* ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-175">Remove the existing class definition and add the following code to the *SentimentPrediction.cs* file:</span></span>

    [!code-csharp [SentimentPrediction](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/DataModels/SentimentPrediction.cs#L5-L14)]

    <span data-ttu-id="13055-176">`SentimentPrediction` は `SentimentData` を継承し、モデルによって生成された出力だけでなく `SentimentText` プロパティで元のデータへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="13055-176">`SentimentPrediction` inherits from `SentimentData` which provides access to the original data in the `SentimentText` property as well as the output generated by the model.</span></span>

## <a name="register-predictionenginepool-service"></a><span data-ttu-id="13055-177">PredictionEnginePool サービスを登録する</span><span class="sxs-lookup"><span data-stu-id="13055-177">Register PredictionEnginePool service</span></span>

<span data-ttu-id="13055-178">1 つの予測を作成するには、[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13055-178">To make a single prediction, you have to create a [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602).</span></span> <span data-ttu-id="13055-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="13055-179">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="13055-180">さらに、アプリケーション内で必要なすべての場所にそのインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13055-180">Additionally, you have to create an instance of it everywhere it is needed within your application.</span></span> <span data-ttu-id="13055-181">アプリケーションの規模が拡大すると、このプロセスが管理不能になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13055-181">As your application grows, this process can become unmanageable.</span></span> <span data-ttu-id="13055-182">パフォーマンスとスレッド セーフを向上させるには、依存性の挿入と `PredictionEnginePool` サービスを組み合わせて使用します。これにより、アプリケーション全体で使用する [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="13055-182">For improved performance and thread safety, use a combination of dependency injection and the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span>

<span data-ttu-id="13055-183">依存関係の注入の詳細については、[こちらのリンク](https://en.wikipedia.org/wiki/Dependency_injection)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="13055-183">The following link provides more information if you want to learn more about [dependency injection](https://en.wikipedia.org/wiki/Dependency_injection).</span></span>

1. <span data-ttu-id="13055-184">**ソリューション エクスプローラー**で、プロジェクトを右クリックし、 **[追加]**  >  **[新しい項目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-184">In **Solution Explorer**, right-click the project, and then select **Add** > **New Item**.</span></span>
1. <span data-ttu-id="13055-185">**[新しい項目の追加]** ダイアログ ボックスで、 **[クラス]** を選択し、 **[名前]** フィールドを「*Startup.cs*」に変更します。</span><span class="sxs-lookup"><span data-stu-id="13055-185">In the **Add New Item** dialog box, select **Class** and change the **Name** field to *Startup.cs*.</span></span> <span data-ttu-id="13055-186">次に **[追加]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="13055-186">Then, select the **Add** button.</span></span>
1. <span data-ttu-id="13055-187">*Startup.cs* の先頭に次の using ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-187">Add the following using statements to the top of *Startup.cs*:</span></span>

    [!code-csharp [StartupUsings](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L1-L6)]

1. <span data-ttu-id="13055-188">using ステートメントの下にある既存のコードを削除し、次のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="13055-188">Remove the existing code below the using statements and add the following code:</span></span>

    ```csharp
    [assembly: FunctionsStartup(typeof(Startup))]
    namespace SentimentAnalysisFunctionsApp
    {
        public class Startup : FunctionsStartup
        {

        }
    }
    ```

1. <span data-ttu-id="13055-189">アプリが実行されている環境と `Startup` クラス内でモデルが配置されるファイル パスを格納する変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="13055-189">Define variables to store the environment the app is running in and the file path where the model is located inside the `Startup` class</span></span>

    [!code-csharp [DefineStartupVars](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L13-L14)]

1. <span data-ttu-id="13055-190">その下で、コンストラクターを作成して、`_environment` 変数と `_modelPath` 変数の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="13055-190">Below that, create a constructor to set the values of the `_environment` and `_modelPath` variables.</span></span> <span data-ttu-id="13055-191">アプリケーションがローカルで実行されている場合、既定の環境は *Development* になります。</span><span class="sxs-lookup"><span data-stu-id="13055-191">When the application is running locally, the default environment is *Development*.</span></span>

    [!code-csharp [StartupCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L16-L29)]

1. <span data-ttu-id="13055-192">次に、`Configure` という名前の新しいメソッドを追加して、`PredictionEnginePool` サービスをコンストラクターの下に登録します。</span><span class="sxs-lookup"><span data-stu-id="13055-192">Then, add a new method called `Configure` to register the `PredictionEnginePool` service below the constructor.</span></span>

    [!code-csharp [ConfigureServices](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/Startup.cs#L31-L35)]

<span data-ttu-id="13055-193">大まかに言えば、オブジェクトとサービスがアプリケーションによって要求されたときに、このコードでは、後で使用できるように手動ではなく自動的に初期化が実行されます。</span><span class="sxs-lookup"><span data-stu-id="13055-193">At a high level, this code initializes the objects and services automatically for later use when requested by the application instead of having to manually do it.</span></span>

<span data-ttu-id="13055-194">機械学習モデルは静的ではありません。</span><span class="sxs-lookup"><span data-stu-id="13055-194">Machine learning models are not static.</span></span> <span data-ttu-id="13055-195">新しいトレーニング データが使用可能になると、モデルの再トレーニングと再展開が行われます。</span><span class="sxs-lookup"><span data-stu-id="13055-195">As new training data becomes available, the model is retrained and redeployed.</span></span> <span data-ttu-id="13055-196">アプリケーションに最新バージョンのモデルを取り込む方法の 1 つは、アプリケーション全体を再展開することです。</span><span class="sxs-lookup"><span data-stu-id="13055-196">One way to get the latest version of the model into your application is to redeploy the entire application.</span></span> <span data-ttu-id="13055-197">ただし、これによってアプリケーションのダウンタイムが発生します。</span><span class="sxs-lookup"><span data-stu-id="13055-197">However, this introduces application downtime.</span></span> <span data-ttu-id="13055-198">`PredictionEnginePool` サービスには、アプリケーションを停止することなく、更新されたモデルを再度読み込むメカニズムが用意されています。</span><span class="sxs-lookup"><span data-stu-id="13055-198">The `PredictionEnginePool` service provides a mechanism to reload an updated model without taking your application down.</span></span>

<span data-ttu-id="13055-199">`watchForChanges` パラメーターを `true` に設定すると、`PredictionEnginePool` では、ファイル システムの変更通知をリッスンし、ファイルに変更があったときにイベントを発生させる [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) が開始されます。</span><span class="sxs-lookup"><span data-stu-id="13055-199">Set the `watchForChanges` parameter to `true`, and the `PredictionEnginePool` starts a [`FileSystemWatcher`](xref:System.IO.FileSystemWatcher) that listens to the file system change notifications and raises events when there is a change to the file.</span></span> <span data-ttu-id="13055-200">これにより、モデルを自動的に再度読み込む `PredictionEnginePool` のプロンプトが表示されます。</span><span class="sxs-lookup"><span data-stu-id="13055-200">This prompts the `PredictionEnginePool` to automatically reload the model.</span></span>

<span data-ttu-id="13055-201">モデルは `modelName` パラメーターによって識別されるため、変更時にアプリケーションごとに複数のモデルを再度読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="13055-201">The model is identified by the `modelName` parameter so that more than one model per application can be reloaded upon change.</span></span>

> [!TIP]
> <span data-ttu-id="13055-202">また、リモートに格納されているモデルを操作するときは `FromUri` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="13055-202">Alternatively, you can use the `FromUri` method when working with models stored remotely.</span></span> <span data-ttu-id="13055-203">`FromUri` では、ファイルの変更イベントを監視するのではなく、リモートの場所の変更をポーリングします。</span><span class="sxs-lookup"><span data-stu-id="13055-203">Rather than watching for file changed events, `FromUri` polls the remote location for changes.</span></span> <span data-ttu-id="13055-204">ポーリング間隔は既定で 5 分に設定されています。</span><span class="sxs-lookup"><span data-stu-id="13055-204">The polling interval defaults to 5 minutes.</span></span> <span data-ttu-id="13055-205">アプリケーションの要件に基づいてポーリング間隔を増減することができます。</span><span class="sxs-lookup"><span data-stu-id="13055-205">You can increase or decrease the polling interval based on your application's requirements.</span></span> <span data-ttu-id="13055-206">次のコード サンプルでは、`PredictionEnginePool` は、指定された URI に格納されているモデルを 1 分ごとにポーリングします。</span><span class="sxs-lookup"><span data-stu-id="13055-206">In the code sample below, the `PredictionEnginePool` polls the model stored at the specified URI every minute.</span></span>
>
>```csharp
>builder.Services.AddPredictionEnginePool<SentimentData, SentimentPrediction>()
>   .FromUri(
>       modelName: "SentimentAnalysisModel",
>       uri:"https://github.com/dotnet/samples/raw/master/machine-learning/models/sentimentanalysis/sentiment_model.zip",
>       period: TimeSpan.FromMinutes(1));
>```

## <a name="load-the-model-into-the-function"></a><span data-ttu-id="13055-207">関数にモデルを読み込む</span><span class="sxs-lookup"><span data-stu-id="13055-207">Load the model into the function</span></span>

<span data-ttu-id="13055-208">次のコードを *AnalyzeSentiment* クラス内に挿入します。</span><span class="sxs-lookup"><span data-stu-id="13055-208">Insert the following code inside the *AnalyzeSentiment* class:</span></span>

[!code-csharp [AnalyzeCtor](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L18-L24)]

<span data-ttu-id="13055-209">このコードでは、依存関係の挿入を通して取得する関数のコンストラクターに渡すことで、`PredictionEnginePool` を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="13055-209">This code assigns the `PredictionEnginePool` by passing it to the function's constructor which you get via dependency injection.</span></span>

## <a name="use-the-model-to-make-predictions"></a><span data-ttu-id="13055-210">モデルを使用して予測を行う</span><span class="sxs-lookup"><span data-stu-id="13055-210">Use the model to make predictions</span></span>

<span data-ttu-id="13055-211">*AnalyzeSentiment* クラスの *Run* メソッドの既存の実装を、次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="13055-211">Replace the existing implementation of *Run* method in *AnalyzeSentiment* class with the following code:</span></span>

[!code-csharp [AnalyzeRunMethod](~/machinelearning-samples/samples/csharp/end-to-end-apps/ScalableMLModelOnAzureFunction/SentimentAnalysisFunctionsApp/AnalyzeSentiment.cs#L26-L45)]

<span data-ttu-id="13055-212">`Run` メソッドが実行されると、HTTP 要求からの受信データが逆シリアル化されて、`PredictionEnginePool` への入力として使用されます。</span><span class="sxs-lookup"><span data-stu-id="13055-212">When the `Run` method executes, the incoming data from the HTTP request is deserialized and used as input for the `PredictionEnginePool`.</span></span> <span data-ttu-id="13055-213">次に、`Predict` メソッドが呼び出され、`Startup` クラスに登録されている `SentimentAnalysisModel` を使用して予測が行われ、成功した場合に結果がユーザーに返されます。</span><span class="sxs-lookup"><span data-stu-id="13055-213">The `Predict` method is then called to make predictions using the `SentimentAnalysisModel` registered in the `Startup` class and returns the results back to the user if successful.</span></span>

## <a name="test-locally"></a><span data-ttu-id="13055-214">ローカルでテストする</span><span class="sxs-lookup"><span data-stu-id="13055-214">Test locally</span></span>

<span data-ttu-id="13055-215">すべてが設定されたので、アプリケーションをテストします。</span><span class="sxs-lookup"><span data-stu-id="13055-215">Now that everything is set up, it's time to test the application:</span></span>

1. <span data-ttu-id="13055-216">アプリケーションの実行</span><span class="sxs-lookup"><span data-stu-id="13055-216">Run the application</span></span>
1. <span data-ttu-id="13055-217">PowerShell を開き、プロンプトにコードを入力します。PORT は、アプリケーションが実行されているポートです。</span><span class="sxs-lookup"><span data-stu-id="13055-217">Open PowerShell and enter the code into the prompt where PORT is the port your application is running on.</span></span> <span data-ttu-id="13055-218">通常、このポートは 7071 です。</span><span class="sxs-lookup"><span data-stu-id="13055-218">Typically the port is 7071.</span></span>

    ```powershell
    Invoke-RestMethod "http://localhost:<PORT>/api/AnalyzeSentiment" -Method Post -Body (@{SentimentText="This is a very bad steak"} | ConvertTo-Json) -ContentType "application/json"
    ```

    <span data-ttu-id="13055-219">成功した場合、出力は次のテキストのようになります。</span><span class="sxs-lookup"><span data-stu-id="13055-219">If successful, the output should look similar to the text below:</span></span>

    ```powershell
    Negative
    ```

<span data-ttu-id="13055-220">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="13055-220">Congratulations!</span></span> <span data-ttu-id="13055-221">Azure 関数を使用したインターネット経由での予測の実行に対して、モデルを正常に提供できました。</span><span class="sxs-lookup"><span data-stu-id="13055-221">You have successfully served your model to make predictions over the internet using an Azure Function.</span></span>

## <a name="next-steps"></a><span data-ttu-id="13055-222">次の手順</span><span class="sxs-lookup"><span data-stu-id="13055-222">Next Steps</span></span>

- [<span data-ttu-id="13055-223">Azure に配置する</span><span class="sxs-lookup"><span data-stu-id="13055-223">Deploy to Azure</span></span>](/azure/azure-functions/functions-develop-vs#publish-to-azure)
