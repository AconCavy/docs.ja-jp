---
title: クロス検証を使って機械学習モデルをトレーニングする
description: ML.NET で、クロス検証を使用してより堅牢な機械学習モデルを構築する方法について説明します。 クロス検証は、データをいくつかのパーティションに分割し、それらのパーティション上で複数のアルゴリズムをトレーニングするトレーニングおよびモデル評価手法です。
ms.date: 08/29/2019
author: luisquintanilla
ms.author: luquinta
ms.custom: mvc,how-to,title-hack-0625
ms.openlocfilehash: 87eae789478752423f3e682d4db6cead0391aa6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73976925"
---
# <a name="train-a-machine-learning-model-using-cross-validation"></a><span data-ttu-id="72252-104">クロス検証を使って機械学習モデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="72252-104">Train a machine learning model using cross validation</span></span>

<span data-ttu-id="72252-105">ML.NET で、クロス検証を使用してより堅牢な機械学習モデルをトレーニングする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="72252-105">Learn how to use cross validation to train more robust machine learning models in ML.NET.</span></span>

<span data-ttu-id="72252-106">クロス検証は、データをいくつかのパーティションに分割し、それらのパーティション上で複数のアルゴリズムをトレーニングするトレーニングおよびモデル評価手法です。</span><span class="sxs-lookup"><span data-stu-id="72252-106">Cross-validation is a training and model evaluation technique that splits the data into several partitions and trains multiple algorithms on these partitions.</span></span> <span data-ttu-id="72252-107">この手法は、トレーニング プロセスのデータを提供することでモデルの堅牢性を改善します。</span><span class="sxs-lookup"><span data-stu-id="72252-107">This technique improves the robustness of the model by holding out data from the training process.</span></span> <span data-ttu-id="72252-108">データに制約のある環境では、目に見えない観測のパフォーマンス向上に加え、小規模のデータセットでモデルをトレーニングする場合の効果的なツールになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="72252-108">In addition to improving performance on unseen observations, in data-constrained environments it can be an effective tool for training models with a smaller dataset.</span></span>

## <a name="the-data-and-data-model"></a><span data-ttu-id="72252-109">データとデータ モデル</span><span class="sxs-lookup"><span data-stu-id="72252-109">The data and data model</span></span>

<span data-ttu-id="72252-110">次の形式を持つファイルのデータがあるとします。</span><span class="sxs-lookup"><span data-stu-id="72252-110">Given data from a file that has the following format:</span></span>

```text
Size (Sq. ft.), HistoricalPrice1 ($), HistoricalPrice2 ($), HistoricalPrice3 ($), Current Price ($)
620.00, 148330.32, 140913.81, 136686.39, 146105.37
550.00, 557033.46, 529181.78, 513306.33, 548677.95
1127.00, 479320.99, 455354.94, 441694.30, 472131.18
1120.00, 47504.98, 45129.73, 43775.84, 46792.41
```

<span data-ttu-id="72252-111">データは `HousingData` のようなクラスでモデル化し、[`IDataView`](xref:Microsoft.ML.IDataView) にロードできます。</span><span class="sxs-lookup"><span data-stu-id="72252-111">The data can be modeled by a class like `HousingData` and loaded into an [`IDataView`](xref:Microsoft.ML.IDataView).</span></span>

```csharp
public class HousingData
{
    [LoadColumn(0)]
    public float Size { get; set; }

    [LoadColumn(1, 3)]
    [VectorType(3)]
    public float[] HistoricalPrices { get; set; }

    [LoadColumn(4)]
    [ColumnName("Label")]
    public float CurrentPrice { get; set; }
}
```

## <a name="prepare-the-data"></a><span data-ttu-id="72252-112">データを準備する</span><span class="sxs-lookup"><span data-stu-id="72252-112">Prepare the data</span></span>

<span data-ttu-id="72252-113">機械学習モデルの構築に使用する前に、データを前処理します。</span><span class="sxs-lookup"><span data-stu-id="72252-113">Pre-process the data before using it to build the machine learning model.</span></span> <span data-ttu-id="72252-114">このサンプルでは、`Size` 列と `HistoricalPrices` 列が 1 つの特徴ベクターに結合されます。これは、[`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) メソッドを使用して `Features` という新しい列に出力されます。</span><span class="sxs-lookup"><span data-stu-id="72252-114">In this sample, the `Size` and `HistoricalPrices` columns are combined into a single feature vector,  which is output to a new column called `Features` using the [`Concatenate`](xref:Microsoft.ML.TransformExtensionsCatalog.Concatenate*) method.</span></span> <span data-ttu-id="72252-115">データを ML.NET アルゴリズムで想定されている形式にすることに加え、列を連結すると、個別の列ではなく、連結した列に対して 1 回操作を適用されるので、パイプライン内の後続の操作が最適化されます。</span><span class="sxs-lookup"><span data-stu-id="72252-115">In addition to getting the data into the format expected by ML.NET algorithms, concatenating columns optimizes subsequent operations in the pipeline by applying the operation once for the concatenated column instead of each of the separate columns.</span></span>

<span data-ttu-id="72252-116">列が 1 つのベクターに結合されると、[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) が `Features` 列に適用され、0 - 1 という同じ範囲の `Size` と `HistoricalPrices` が得られます。</span><span class="sxs-lookup"><span data-stu-id="72252-116">Once the columns are combined into a single vector, [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax*) is applied to the `Features` column to get `Size` and `HistoricalPrices` in the same range between 0-1.</span></span>

```csharp
// Define data prep estimator
IEstimator<ITransformer> dataPrepEstimator =
    mlContext.Transforms.Concatenate("Features", new string[] { "Size", "HistoricalPrices" })
        .Append(mlContext.Transforms.NormalizeMinMax("Features"));

// Create data prep transformer
ITransformer dataPrepTransformer = dataPrepEstimator.Fit(data);

// Transform data
IDataView transformedData = dataPrepTransformer.Transform(data);
```

## <a name="train-model-with-cross-validation"></a><span data-ttu-id="72252-117">クロス検証を使用してモデルをトレーニングする</span><span class="sxs-lookup"><span data-stu-id="72252-117">Train model with cross validation</span></span>

<span data-ttu-id="72252-118">データの前処理が完了したら、次はモデルのトレーニングです。</span><span class="sxs-lookup"><span data-stu-id="72252-118">Once the data has been pre-processed, it's time to train the model.</span></span> <span data-ttu-id="72252-119">まず、実行する機械学習タスクと最も密接に連携するアルゴリズムを選択します。</span><span class="sxs-lookup"><span data-stu-id="72252-119">First, select the algorithm that most closely aligns with the machine learning task to be performed.</span></span> <span data-ttu-id="72252-120">予測値は数値的に連続した値なので、このタスクは回帰です。</span><span class="sxs-lookup"><span data-stu-id="72252-120">Because the predicted value is a numerically continuous value, the task is regression.</span></span> <span data-ttu-id="72252-121">ML.NET で実装されている回帰アルゴリズムの 1 つは [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) アルゴリズムです。</span><span class="sxs-lookup"><span data-stu-id="72252-121">One of the regression algorithms implemented by ML.NET is the [`StochasticDualCoordinateAscentCoordinator`](xref:Microsoft.ML.Trainers.SdcaRegressionTrainer) algorithm.</span></span> <span data-ttu-id="72252-122">クロス検証を使用してモデルをトレーニングするには、[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="72252-122">To train the model with cross-validation use the [`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) method.</span></span>

> [!NOTE]
> <span data-ttu-id="72252-123">このサンプルでは線形回帰モデルを使用しますが、CrossValidate は、異常検出を除く ML.NET の他のすべての機械学習タスクに適用できます。</span><span class="sxs-lookup"><span data-stu-id="72252-123">Although this sample uses a linear regression model, CrossValidate is applicable to all other machine learning tasks in ML.NET except Anomaly Detection.</span></span>

```csharp
// Define StochasticDualCoordinateAscent algorithm estimator
IEstimator<ITransformer> sdcaEstimator = mlContext.Regression.Trainers.Sdca();

// Apply 5-fold cross validation
var cvResults = mlContext.Regression.CrossValidate(transformedData, sdcaEstimator, numberOfFolds: 5);
```

<span data-ttu-id="72252-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) によって次の操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="72252-124">[`CrossValidate`](xref:Microsoft.ML.RegressionCatalog.CrossValidate*) performs the following operations:</span></span>

1. <span data-ttu-id="72252-125">`numberOfFolds` パラメーターに指定された値と等しい数のパーティションにデータを分割します。</span><span class="sxs-lookup"><span data-stu-id="72252-125">Partitions the data into a number of partitions equal to the value specified in the `numberOfFolds` parameter.</span></span> <span data-ttu-id="72252-126">各パーティションの結果は [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="72252-126">The result of each partition is a [`TrainTestData`](xref:Microsoft.ML.DataOperationsCatalog.TrainTestData) object.</span></span>
1. <span data-ttu-id="72252-127">各パーティションでは、トレーニング データ セットに対して指定した機械学習アルゴリズム エスティメーターを使用してモデルがトレーニングされます。</span><span class="sxs-lookup"><span data-stu-id="72252-127">A model is trained on each of the partitions using the specified machine learning algorithm estimator on the training data set.</span></span>
1. <span data-ttu-id="72252-128">各モデルのパフォーマンスは、テスト データ セットに対して [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) メソッドを使用して評価されます。</span><span class="sxs-lookup"><span data-stu-id="72252-128">Each model's performance is evaluated using the [`Evaluate`](xref:Microsoft.ML.RegressionCatalog.Evaluate*) method on the test data set.</span></span>
1. <span data-ttu-id="72252-129">各モデルについて、モデルとそのメトリックが返されます。</span><span class="sxs-lookup"><span data-stu-id="72252-129">The model along with its metrics are returned for each of the models.</span></span>

<span data-ttu-id="72252-130">`cvResults` に格納される結果は、[`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) オブジェクトのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="72252-130">The result stored in `cvResults` is a collection of [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) objects.</span></span> <span data-ttu-id="72252-131">このオブジェクトには、トレーニング済みモデルだけでなく、[`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) プロパティと [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) プロパティの両方からそれぞれアクセスできるメトリックが含まれています。</span><span class="sxs-lookup"><span data-stu-id="72252-131">This object includes the trained model as well as metrics which are both accessible form the [`Model`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Model) and [`Metrics`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601.Metrics) properties respectively.</span></span> <span data-ttu-id="72252-132">このサンプルでは、`Model` プロパティは [`ITransformer`](xref:Microsoft.ML.ITransformer) 型であり、`Metrics` プロパティは [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics) 型です。</span><span class="sxs-lookup"><span data-stu-id="72252-132">In this sample, the `Model` property is of type [`ITransformer`](xref:Microsoft.ML.ITransformer) and the `Metrics` property is of type [`RegressionMetrics`](xref:Microsoft.ML.Data.RegressionMetrics).</span></span>

## <a name="evaluate-the-model"></a><span data-ttu-id="72252-133">モデルを評価する</span><span class="sxs-lookup"><span data-stu-id="72252-133">Evaluate the model</span></span>

<span data-ttu-id="72252-134">個々の [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) オブジェクトの `Metrics` プロパティを介してさまざまなトレーニング済みモデルのメトリックにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="72252-134">Metrics for the different trained models can be accessed through the `Metrics` property of the individual [`CrossValidationResult`](xref:Microsoft.ML.TrainCatalogBase.CrossValidationResult%601) object.</span></span> <span data-ttu-id="72252-135">この場合は、[R-2 乗メトリック](https://en.wikipedia.org/wiki/Coefficient_of_determination)にアクセスし、変数 `rSquared` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="72252-135">In this case, the [R-Squared metric](https://en.wikipedia.org/wiki/Coefficient_of_determination) is accessed and stored in the variable `rSquared`.</span></span>

```csharp
IEnumerable<double> rSquared =
    cvResults
        .Select(fold => fold.Metrics.RSquared);
```

<span data-ttu-id="72252-136">`rSquared` 変数の内容を調べると、出力は 0 - 1 の範囲の 5 つの値になります (1 に近いほど適しています)。</span><span class="sxs-lookup"><span data-stu-id="72252-136">If you inspect the contents of the `rSquared` variable, the output should be five values ranging from 0-1 where closer to 1 means best.</span></span> <span data-ttu-id="72252-137">R-2 乗などのメトリックを使用して、最適なパフォーマンスから最低のパフォーマンスのモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="72252-137">Using metrics like R-Squared, select the models from best to worst performing.</span></span> <span data-ttu-id="72252-138">次に、最上位のモデルを選択して予測を行うか、追加の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="72252-138">Then, select the top model to make predictions or perform additional operations with.</span></span>

```csharp
// Select all models
ITransformer[] models =
    cvResults
        .OrderByDescending(fold => fold.Metrics.RSquared)
        .Select(fold => fold.Model)
        .ToArray();

// Get Top Model
ITransformer topModel = models[0];
```
