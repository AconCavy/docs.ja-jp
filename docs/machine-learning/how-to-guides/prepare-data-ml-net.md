---
title: モデル構築用のデータを準備する
description: ML.NET での変換を利用して、追加処理やモデルのビルドのためにデータを操作して準備する方法について説明します。
author: luisquintanilla
ms.author: luquinta
ms.date: 01/29/2020
ms.custom: mvc, how-to, title-hack-0625
ms.openlocfilehash: 12f933253af9ea519d711c20227fe075fed003de
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452988"
---
# <a name="prepare-data-for-building-a-model"></a><span data-ttu-id="a8283-103">モデル構築用のデータを準備する</span><span class="sxs-lookup"><span data-stu-id="a8283-103">Prepare data for building a model</span></span>

<span data-ttu-id="a8283-104">ML.NET を利用して、追加処理やモデルのビルドのためのデータを準備する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a8283-104">Learn how to use ML.NET to prepare data for additional processing or building a model.</span></span>

<span data-ttu-id="a8283-105">多くの場合、データは未整理であり、分散しています。</span><span class="sxs-lookup"><span data-stu-id="a8283-105">Data is often unclean and sparse.</span></span> <span data-ttu-id="a8283-106">ML.NET 機械学習アルゴリズムでは、入力値などの特性が単一の数値ベクターになっていることを想定しています。</span><span class="sxs-lookup"><span data-stu-id="a8283-106">ML.NET machine learning algorithms expect input or features to be in a single numerical vector.</span></span> <span data-ttu-id="a8283-107">同様に、予測する値 (ラベル) は、カテゴリ データの場合は特に、エンコードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8283-107">Similarly, the value to predict (label), especially when it's categorical data, has to be encoded.</span></span> <span data-ttu-id="a8283-108">したがって、データ準備の目標の 1 つは、データを ML.NET アルゴリズムから期待されている形式にすることです。</span><span class="sxs-lookup"><span data-stu-id="a8283-108">Therefore one of the goals of data preparation is to get the data into the format expected by ML.NET algorithms.</span></span>

## <a name="filter-data"></a><span data-ttu-id="a8283-109">データのフィルター処理</span><span class="sxs-lookup"><span data-stu-id="a8283-109">Filter data</span></span>

<span data-ttu-id="a8283-110">データセット内の全データが、分析に関係するわけではない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="a8283-110">Sometimes, not all data in a dataset is relevant for analysis.</span></span> <span data-ttu-id="a8283-111">関係のないデータを除去する方法が、フィルター処理です。</span><span class="sxs-lookup"><span data-stu-id="a8283-111">An approach to remove irrelevant data is filtering.</span></span> <span data-ttu-id="a8283-112">[`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) には、全データを含む [`IDataView`](xref:Microsoft.ML.IDataView) を取得して目的のデータだけを含む [IDataView](xref:Microsoft.ML.IDataView) を返す一連のフィルター操作が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a8283-112">The [`DataOperationsCatalog`](xref:Microsoft.ML.DataOperationsCatalog) contains a set of filter operations that take in an [`IDataView`](xref:Microsoft.ML.IDataView) containing all of the data and return an [IDataView](xref:Microsoft.ML.IDataView) containing only the data points of interest.</span></span> <span data-ttu-id="a8283-113">フィルター操作は、[`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog) にあるような [`IEstimator`](xref:Microsoft.ML.IEstimator%601) または [`ITransformer`](xref:Microsoft.ML.ITransformer) ではないため、[`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) または [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) データ準備パイプラインの一部に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="a8283-113">It's important to note that because filter operations are not an [`IEstimator`](xref:Microsoft.ML.IEstimator%601) or [`ITransformer`](xref:Microsoft.ML.ITransformer) like those in the [`TransformsCatalog`](xref:Microsoft.ML.TransformsCatalog), they cannot be included as part of an [`EstimatorChain`](xref:Microsoft.ML.Data.EstimatorChain%601) or [`TransformerChain`](xref:Microsoft.ML.Data.TransformerChain%601) data preparation pipeline.</span></span>

<span data-ttu-id="a8283-114">次の入力データを取得して、`data` と呼ばれる [`IDataView`](xref:Microsoft.ML.IDataView) に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a8283-114">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="a8283-115">列の値に基づいてデータをフィルター処理するには、[`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a8283-115">To filter data based on the value of a column, use the [`FilterRowsByColumn`](xref:Microsoft.ML.DataOperationsCatalog.FilterRowsByColumn%2A) method.</span></span>

```csharp
// Apply filter
IDataView filteredData = mlContext.Data.FilterRowsByColumn(data, "Price", lowerBound: 200000, upperBound: 1000000);
```

<span data-ttu-id="a8283-116">上記のサンプルでは、データセット内の価格が 200000 から 1000000 までの行を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8283-116">The sample above takes rows in the dataset with a price between 200000 and 1000000.</span></span> <span data-ttu-id="a8283-117">このフィルターを適用した結果として、データ内の最後の 2 行だけが返されます。最初の行は価格が 100000 になっており、指定された範囲外にあるために除外されます。</span><span class="sxs-lookup"><span data-stu-id="a8283-117">The result of applying this filter would return only the last two rows in the data and exclude the first row because its price is 100000 and not between the specified range.</span></span>

## <a name="replace-missing-values"></a><span data-ttu-id="a8283-118">欠損値を置き換える</span><span class="sxs-lookup"><span data-stu-id="a8283-118">Replace missing values</span></span>

<span data-ttu-id="a8283-119">欠損値は、データセット内でよく発生します。</span><span class="sxs-lookup"><span data-stu-id="a8283-119">Missing values are a common occurrence in datasets.</span></span> <span data-ttu-id="a8283-120">欠損値を処理する 1 つの方法は、指定された型の既定値があればその値に、またはそのデータの平均値などの意味のある別の値に置き換えることです。</span><span class="sxs-lookup"><span data-stu-id="a8283-120">One approach to dealing with missing values is to replace them with the default value for the given type if any or another meaningful value such as the mean value in the data.</span></span>

<span data-ttu-id="a8283-121">次の入力データを取得して、`data` と呼ばれる [`IDataView`](xref:Microsoft.ML.IDataView) に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a8283-121">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=float.NaN
    }
};
```

<span data-ttu-id="a8283-122">リスト内の最後の要素では、`Price` が欠損値になっていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a8283-122">Notice that the last element in our list has a missing value for `Price`.</span></span> <span data-ttu-id="a8283-123">`Price` 列内の欠損値を置き換えるには、[`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) メソッドを使用して該当の欠損値を入力します。</span><span class="sxs-lookup"><span data-stu-id="a8283-123">To replace the missing values in the `Price` column, use the [`ReplaceMissingValues`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) method to fill in that missing value.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a8283-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) は、数値データのみで機能します。</span><span class="sxs-lookup"><span data-stu-id="a8283-124">[`ReplaceMissingValue`](xref:Microsoft.ML.ExtensionsCatalog.ReplaceMissingValues%2A) only works with numerical data.</span></span>

```csharp
// Define replacement estimator
var replacementEstimator = mlContext.Transforms.ReplaceMissingValues("Price", replacementMode: MissingValueReplacingEstimator.ReplacementMode.Mean);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer replacementTransformer = replacementEstimator.Fit(data);

// Transform data
IDataView transformedData = replacementTransformer.Transform(data);
```

<span data-ttu-id="a8283-125">ML.NET では、さまざまな[置換モード](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode)をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a8283-125">ML.NET supports various [replacement modes](xref:Microsoft.ML.Transforms.MissingValueReplacingEstimator.ReplacementMode).</span></span> <span data-ttu-id="a8283-126">上記のサンプルでは、該当の列の平均値を使って欠損値が入力される `Mean` 置換モードが使用されています。</span><span class="sxs-lookup"><span data-stu-id="a8283-126">The sample above uses the `Mean` replacement mode, which fills in the missing value with that column's average value.</span></span> <span data-ttu-id="a8283-127">置換の結果、データ内の最後の要素である `Price` プロパティには、100,000 と 300,000 の平均として 200,000 が入力されます。</span><span class="sxs-lookup"><span data-stu-id="a8283-127">The replacement 's result fills in the `Price` property for the last element in our data with 200,000 since it's the average of 100,000 and 300,000.</span></span>

## <a name="use-normalizers"></a><span data-ttu-id="a8283-128">ノーマライザーを使用する</span><span class="sxs-lookup"><span data-stu-id="a8283-128">Use normalizers</span></span>

<span data-ttu-id="a8283-129">[正規化](https://en.wikipedia.org/wiki/Feature_scaling)は、特徴を同じ範囲 (通常は 0 から 1 の範囲) になるようにスケーリングして、機械学習アルゴリズムによる処理をより正確に実行できるようにするために使用されるデータの事前処理手法です。</span><span class="sxs-lookup"><span data-stu-id="a8283-129">[Normalization](https://en.wikipedia.org/wiki/Feature_scaling) is a data pre-processing technique used to scale features to be in the same range, usually between 0 and 1, so that they can be more accurately processed by a machine learning algorithm.</span></span> <span data-ttu-id="a8283-130">たとえば、年齢と収入の値の範囲は、年齢は一般的に 0 から 100 の範囲で、収入は一般的に 0 から 1,000 単位の範囲で、大きく変化します。</span><span class="sxs-lookup"><span data-stu-id="a8283-130">For example, the ranges for age and income vary significantly with age generally being in the range of 0-100 and income generally being in the range of zero to thousands.</span></span> <span data-ttu-id="a8283-131">正規化変換のより詳細な一覧と説明については、[変換に関するページ](../resources/transforms.md)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8283-131">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of normalization transforms.</span></span>

### <a name="min-max-normalization"></a><span data-ttu-id="a8283-132">最小 - 最大の正規化</span><span class="sxs-lookup"><span data-stu-id="a8283-132">Min-Max normalization</span></span>

<span data-ttu-id="a8283-133">次の入力データを取得して、`data` と呼ばれる [`IDataView`](xref:Microsoft.ML.IDataView) に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a8283-133">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms = 2f,
        Price = 200000f
    },
    new HomeData
    {
        NumberOfBedrooms = 1f,
        Price = 100000f
    }
};
```

<span data-ttu-id="a8283-134">正規化は、1 つの数値およびベクターを含む列に適用できます。</span><span class="sxs-lookup"><span data-stu-id="a8283-134">Normalization can be applied to columns with single numerical values as well as vectors.</span></span> <span data-ttu-id="a8283-135">[`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) メソッドによる最小 - 最大の正規化を使って、`Price` 列のデータを正規化します。</span><span class="sxs-lookup"><span data-stu-id="a8283-135">Normalize the data in the `Price` column using min-max normalization with the [`NormalizeMinMax`](xref:Microsoft.ML.NormalizationCatalog.NormalizeMinMax%2A) method.</span></span>

```csharp
// Define min-max estimator
var minMaxEstimator = mlContext.Transforms.NormalizeMinMax("Price");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer minMaxTransformer = minMaxEstimator.Fit(data);

// Transform data
IDataView transformedData = minMaxTransformer.Transform(data);
```

<span data-ttu-id="a8283-136">0 から 1 の範囲で出力値を生成する `MinMax` 正規化の数式を使用して、元の価格値 `[200000,100000]` が `[ 1, 0.5 ]` に変換されます。</span><span class="sxs-lookup"><span data-stu-id="a8283-136">The original price values `[200000,100000]` are converted to `[ 1, 0.5 ]` using the `MinMax` normalization formula that generates output values in the range of 0-1.</span></span>

### <a name="binning"></a><span data-ttu-id="a8283-137">ビン分割</span><span class="sxs-lookup"><span data-stu-id="a8283-137">Binning</span></span>

<span data-ttu-id="a8283-138">[ビン分割](https://en.wikipedia.org/wiki/Data_binning)では、連続する値を不連続な入力値表現に変換します。</span><span class="sxs-lookup"><span data-stu-id="a8283-138">[Binning](https://en.wikipedia.org/wiki/Data_binning) converts continuous values into a discrete representation of the input.</span></span> <span data-ttu-id="a8283-139">たとえば、特性の 1 つが年齢だとします。</span><span class="sxs-lookup"><span data-stu-id="a8283-139">For example, suppose one of your features is age.</span></span> <span data-ttu-id="a8283-140">実際の年齢値を使用する代わりに、ビン分割によってその値の範囲を作成します。</span><span class="sxs-lookup"><span data-stu-id="a8283-140">Instead of using the actual age value,  binning creates ranges for that value.</span></span> <span data-ttu-id="a8283-141">0 から 18 を 1 つのビン、19 から 35 をもう 1 つのビン、のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8283-141">0-18 could be one bin, another could be 19-35 and so on.</span></span>

<span data-ttu-id="a8283-142">次の入力データを取得して、`data` と呼ばれる [`IDataView`](xref:Microsoft.ML.IDataView) に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a8283-142">Take the following input data and load it into an [`IDataView`](xref:Microsoft.ML.IDataView) called `data`:</span></span>

```csharp
HomeData[] homeDataList = new HomeData[]
{
    new HomeData
    {
        NumberOfBedrooms=1f,
        Price=100000f
    },
    new HomeData
    {
        NumberOfBedrooms=2f,
        Price=300000f
    },
    new HomeData
    {
        NumberOfBedrooms=6f,
        Price=600000f
    }
};
```

<span data-ttu-id="a8283-143">[`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) メソッドを使用して、データをビンに正規化します。</span><span class="sxs-lookup"><span data-stu-id="a8283-143">Normalize the data into bins using the [`NormalizeBinning`](xref:Microsoft.ML.NormalizationCatalog.NormalizeBinning%2A) method.</span></span> <span data-ttu-id="a8283-144">`maximumBinCount` パラメータ―を使用すると、データを分類するために必要なビン数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a8283-144">The `maximumBinCount` parameter enables you to specify the number of bins needed to classify your data.</span></span> <span data-ttu-id="a8283-145">この例では、データは 2 つのビンに配置されます。</span><span class="sxs-lookup"><span data-stu-id="a8283-145">In this example, data will be put into two bins.</span></span>

```csharp
// Define binning estimator
var binningEstimator = mlContext.Transforms.NormalizeBinning("Price", maximumBinCount: 2);

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
var binningTransformer = binningEstimator.Fit(data);

// Transform Data
IDataView transformedData = binningTransformer.Transform(data);
```

<span data-ttu-id="a8283-146">ビン分割の結果、`[0,200000,Infinity]` のビン境界が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a8283-146">The result of binning creates bin bounds of `[0,200000,Infinity]`.</span></span> <span data-ttu-id="a8283-147">したがって、最初の測定範囲を 0 から 200000 まで、それ以外を 200000 より大きいが無限大より小さいとするため、結果として得られるビンは `[0,1,1]` となります。</span><span class="sxs-lookup"><span data-stu-id="a8283-147">Therefore the resulting bins are `[0,1,1]` because the first observation is between 0-200000 and the others are greater than 200000 but less than infinity.</span></span>

## <a name="work-with-categorical-data"></a><span data-ttu-id="a8283-148">カテゴリ別データを扱う</span><span class="sxs-lookup"><span data-stu-id="a8283-148">Work with categorical data</span></span>

<span data-ttu-id="a8283-149">最も一般的な種類のデータの 1 つは、カテゴリ別データです。</span><span class="sxs-lookup"><span data-stu-id="a8283-149">One of the most common types of data is categorical data.</span></span> <span data-ttu-id="a8283-150">カテゴリ別データには、有限個のカテゴリがあります。</span><span class="sxs-lookup"><span data-stu-id="a8283-150">Categorical data has a finite number of categories.</span></span> <span data-ttu-id="a8283-151">たとえば、米国の州や、一連の写真で見つかった動物の種類の一覧があります。</span><span class="sxs-lookup"><span data-stu-id="a8283-151">For example, the states of the USA, or a list of the types of animals found in a set of pictures.</span></span> <span data-ttu-id="a8283-152">カテゴリ別データが特徴であってもラベルであっても、機械学習モデルを生成するために使用できるように、数値にマップされる必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8283-152">Whether the categorical data are features or labels, they must be mapped onto a numerical value so they can be used to generate a machine learning model.</span></span> <span data-ttu-id="a8283-153">解決する問題に応じて、ML.NET でカテゴリ別データを操作する方法は多数あります。</span><span class="sxs-lookup"><span data-stu-id="a8283-153">There are a number of ways of working with categorical data in ML.NET, depending on the problem you are solving.</span></span>

### <a name="key-value-mapping"></a><span data-ttu-id="a8283-154">キー値のマッピング</span><span class="sxs-lookup"><span data-stu-id="a8283-154">Key value mapping</span></span>

<span data-ttu-id="a8283-155">ML.NET では、キーは、カテゴリを表す整数値です。</span><span class="sxs-lookup"><span data-stu-id="a8283-155">In ML.NET, a key is an integer value that represents a category.</span></span> <span data-ttu-id="a8283-156">キー値のマッピングが最もよく使用されるのは、文字列ラベルをトレーニング用の一意の整数値にマップし、モデルを使用して予測を行うときに文字列値に戻すためです。</span><span class="sxs-lookup"><span data-stu-id="a8283-156">Key value mapping is most often used to map string labels into unique integer values for training, then back to their string values when the model is used to make a prediction.</span></span>

<span data-ttu-id="a8283-157">キー値のマッピングを実行するために使用される変換は、[MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) と [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A) です。</span><span class="sxs-lookup"><span data-stu-id="a8283-157">The transforms used to perform key value mapping are [MapValueToKey](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapValueToKey%2A) and [MapKeyToValue](xref:Microsoft.ML.ConversionsExtensionsCatalog.MapKeyToValue%2A).</span></span>

<span data-ttu-id="a8283-158">`MapValueToKey` によってマッピングのディクショナリがモデルに追加されるため、予測時に `MapKeyToValue` によって逆変換を実行できます。</span><span class="sxs-lookup"><span data-stu-id="a8283-158">`MapValueToKey` adds a dictionary of mappings in the model, so that `MapKeyToValue` can perform the reverse transform when making a prediction.</span></span>

### <a name="one-hot-encoding"></a><span data-ttu-id="a8283-159">1 つのホット エンコード</span><span class="sxs-lookup"><span data-stu-id="a8283-159">One hot encoding</span></span>

<span data-ttu-id="a8283-160">1 つのホット エンコードでは、値の有限個のセットが取得され、バイナリ表現に文字列内の一意の位置の単一の `1` 値が含まれている整数にそれらがマップされます。</span><span class="sxs-lookup"><span data-stu-id="a8283-160">One hot encoding takes a finite set of values and maps them onto integers whose binary representation has a single `1` value in unique positions in the string.</span></span> <span data-ttu-id="a8283-161">カテゴリ別データの暗黙的な順序が存在しない場合は、1 つのホット エンコードが最適な選択肢になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8283-161">One hot encoding can be the best choice if there is no implicit ordering of the categorical data.</span></span> <span data-ttu-id="a8283-162">次の表に、郵便番号を生の値として使用する例を示します。</span><span class="sxs-lookup"><span data-stu-id="a8283-162">The following table shows an example with zip codes as raw values.</span></span>

|<span data-ttu-id="a8283-163">生の値</span><span class="sxs-lookup"><span data-stu-id="a8283-163">Raw value</span></span>|<span data-ttu-id="a8283-164">1 つのホット エンコード値</span><span class="sxs-lookup"><span data-stu-id="a8283-164">One hot encoded value</span></span>|
|---------|---------------------|
|<span data-ttu-id="a8283-165">98052</span><span class="sxs-lookup"><span data-stu-id="a8283-165">98052</span></span>|<span data-ttu-id="a8283-166">00...01</span><span class="sxs-lookup"><span data-stu-id="a8283-166">00...01</span></span>|
|<span data-ttu-id="a8283-167">98100</span><span class="sxs-lookup"><span data-stu-id="a8283-167">98100</span></span>|<span data-ttu-id="a8283-168">00...10</span><span class="sxs-lookup"><span data-stu-id="a8283-168">00...10</span></span>|
|<span data-ttu-id="a8283-169">...</span><span class="sxs-lookup"><span data-stu-id="a8283-169">...</span></span>|<span data-ttu-id="a8283-170">...</span><span class="sxs-lookup"><span data-stu-id="a8283-170">...</span></span>|
|<span data-ttu-id="a8283-171">98109</span><span class="sxs-lookup"><span data-stu-id="a8283-171">98109</span></span>|<span data-ttu-id="a8283-172">10...00</span><span class="sxs-lookup"><span data-stu-id="a8283-172">10...00</span></span>|

<span data-ttu-id="a8283-173">カテゴリ別データを 1 つのホット エンコード数値に変換する変換は [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A) です。</span><span class="sxs-lookup"><span data-stu-id="a8283-173">The transform to convert categorical data to one-hot encoded numbers is [`OneHotEncoding`](xref:Microsoft.ML.CategoricalCatalog.OneHotEncoding%2A).</span></span>

### <a name="hashing"></a><span data-ttu-id="a8283-174">ハッシュ</span><span class="sxs-lookup"><span data-stu-id="a8283-174">Hashing</span></span>

<span data-ttu-id="a8283-175">ハッシュは、カテゴリ別データを数値に変換する別の方法です。</span><span class="sxs-lookup"><span data-stu-id="a8283-175">Hashing is another way to convert categorical data to numbers.</span></span> <span data-ttu-id="a8283-176">ハッシュ関数では、任意のサイズのデータ (たとえばテキストの文字列) が固定範囲の数値にマップされます。</span><span class="sxs-lookup"><span data-stu-id="a8283-176">A hash function maps data of an arbitrary size (a string of text for example) onto a number with a fixed range.</span></span> <span data-ttu-id="a8283-177">ハッシュを行うと、特徴を高速かつ空間効率の良い方法でベクター化できる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a8283-177">Hashing can be a fast and space-efficient way of vectorizing features.</span></span> <span data-ttu-id="a8283-178">機械学習でのハッシュの典型例として、電子メールのスパム フィルターがあります。ここでは、既知の単語の辞書を保持する代わりに、電子メール内のすべての単語がハッシュ化され、大規模な特徴ベクターに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a8283-178">One notable example of hashing in machine learning is email spam filtering where, instead of maintaining a dictionary of known words, every word in the email is hashed and added to a large feature vector.</span></span> <span data-ttu-id="a8283-179">ハッシュをこの方法で使用することで、ディクショナリに含まれていない単語の使用による悪意のあるスパムのフィルター回避の問題を避けることができます。</span><span class="sxs-lookup"><span data-stu-id="a8283-179">Using hashing in this way avoids the problem of malicious spam filtering circumvention by the use of words that are not in the dictionary.</span></span>

<span data-ttu-id="a8283-180">ML.NET には、テキスト、日付、および数値データに対してハッシュを実行するための [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) 変換が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a8283-180">ML.NET provides [Hash](xref:Microsoft.ML.ConversionsExtensionsCatalog.Hash%2A) transform to perform hashing on text, dates, and numerical data.</span></span> <span data-ttu-id="a8283-181">キー値のマッピングと同様に、ハッシュ変換の出力はキーの種類になります。</span><span class="sxs-lookup"><span data-stu-id="a8283-181">Like value key mapping, the outputs of the hash transform are key types.</span></span>

## <a name="work-with-text-data"></a><span data-ttu-id="a8283-182">テキスト データを操作する</span><span class="sxs-lookup"><span data-stu-id="a8283-182">Work with text data</span></span>

<span data-ttu-id="a8283-183">カテゴリ別データと同様に、テキスト データも、機械学習モデルの構築に使用する前に、数値特徴に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a8283-183">Like categorical data, text data needs to be transformed into numerical features before using it to build a machine learning model.</span></span> <span data-ttu-id="a8283-184">テキスト変換のより詳細な一覧と説明については、[変換に関するページ](../resources/transforms.md)を確認してください。</span><span class="sxs-lookup"><span data-stu-id="a8283-184">Visit the [transforms page](../resources/transforms.md) for a more detailed list and description of text transforms.</span></span>

<span data-ttu-id="a8283-185">以下のようなデータを使用します。データは [`IDataView`](xref:Microsoft.ML.IDataView) に読み込まれています。</span><span class="sxs-lookup"><span data-stu-id="a8283-185">Using data like the data below that has been loaded into an [`IDataView`](xref:Microsoft.ML.IDataView):</span></span>

```csharp
ReviewData[] reviews = new ReviewData[]
{
    new ReviewData
    {
        Description="This is a good product",
        Rating=4.7f
    },
    new ReviewData
    {
        Description="This is a bad product",
        Rating=2.3f
    }
};
```

<span data-ttu-id="a8283-186">ML.NET には、テキストの文字列値を受け取り、一連の個別の変換を適用することでテキストから一連の特徴を作成する [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) 変換が用意されています。</span><span class="sxs-lookup"><span data-stu-id="a8283-186">ML.NET provides the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) transform that takes a text's string value and creates a set of features from the text, by applying a series of individual transforms.</span></span>

```csharp
// Define text transform estimator
var textEstimator  = mlContext.Transforms.Text.FeaturizeText("Description");

// Fit data to estimator
// Fitting generates a transformer that applies the operations of defined by estimator
ITransformer textTransformer = textEstimator.Fit(data);

// Transform data
IDataView transformedData = textTransformer.Transform(data);
```

<span data-ttu-id="a8283-187">変換の結果、`Description` 列内のテキスト値が、以下の出力のような数値ベクターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="a8283-187">The resulting transform converts the text values in the `Description` column to a numerical vector that looks similar to the output below:</span></span>

```text
[ 0.2041241, 0.2041241, 0.2041241, 0.4082483, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0.2041241, 0, 0, 0, 0, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0.4472136, 0 ]
```

<span data-ttu-id="a8283-188">特徴の生成をより細かく制御するために、`FeaturizeText` を構成する変換を個別に適用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a8283-188">The transforms that make up `FeaturizeText` can also be applied individually for finer grain control over feature generation.</span></span>

```csharp
// Define text transform estimator
var textEstimator = mlContext.Transforms.Text.NormalizeText("Description")
    .Append(mlContext.Transforms.Text.TokenizeIntoWords("Description"))
    .Append(mlContext.Transforms.Text.RemoveDefaultStopWords("Description"))
    .Append(mlContext.Transforms.Conversion.MapValueToKey("Description"))
    .Append(mlContext.Transforms.Text.ProduceNgrams("Description"))
    .Append(mlContext.Transforms.NormalizeLpNorm("Description"));
```

<span data-ttu-id="a8283-189">`textEstimator` には、[`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) メソッドによって実行される操作のサブセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="a8283-189">`textEstimator` contains a subset of operations performed by the [`FeaturizeText`](xref:Microsoft.ML.TextCatalog.FeaturizeText%2A) method.</span></span> <span data-ttu-id="a8283-190">より複雑なパイプラインの利点は、データに適用される変換に対する制御と可視性です。</span><span class="sxs-lookup"><span data-stu-id="a8283-190">The benefit of a more complex pipeline is control and visibility over the transformations applied to the data.</span></span>

<span data-ttu-id="a8283-191">最初の項目を例として使用した場合、`textEstimator` によって定義された変換手順で生成した結果を詳細に説明すると、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a8283-191">Using the first entry as an example, the following is a detailed description of the results produced by the transformation steps defined by `textEstimator`:</span></span>

<span data-ttu-id="a8283-192">**元のテキスト:This is a good product**</span><span class="sxs-lookup"><span data-stu-id="a8283-192">**Original Text: This is a good product**</span></span>

|<span data-ttu-id="a8283-193">変換</span><span class="sxs-lookup"><span data-stu-id="a8283-193">Transform</span></span> | <span data-ttu-id="a8283-194">説明</span><span class="sxs-lookup"><span data-stu-id="a8283-194">Description</span></span> | <span data-ttu-id="a8283-195">結果</span><span class="sxs-lookup"><span data-stu-id="a8283-195">Result</span></span>
|--|--|--|
|<span data-ttu-id="a8283-196">1.NormalizeText</span><span class="sxs-lookup"><span data-stu-id="a8283-196">1. NormalizeText</span></span> | <span data-ttu-id="a8283-197">既定ですべての文字を小文字に変換します</span><span class="sxs-lookup"><span data-stu-id="a8283-197">Converts all letters to lowercase by default</span></span> | <span data-ttu-id="a8283-198">this is a good product</span><span class="sxs-lookup"><span data-stu-id="a8283-198">this is a good product</span></span>
|<span data-ttu-id="a8283-199">2.TokenizeWords</span><span class="sxs-lookup"><span data-stu-id="a8283-199">2. TokenizeWords</span></span> | <span data-ttu-id="a8283-200">文字列を個々の単語に分割します</span><span class="sxs-lookup"><span data-stu-id="a8283-200">Splits string into individual words</span></span> | <span data-ttu-id="a8283-201">["this","is","a","good","product"]</span><span class="sxs-lookup"><span data-stu-id="a8283-201">["this","is","a","good","product"]</span></span>
|<span data-ttu-id="a8283-202">3.RemoveDefaultStopWords</span><span class="sxs-lookup"><span data-stu-id="a8283-202">3. RemoveDefaultStopWords</span></span> | <span data-ttu-id="a8283-203">*is* や *a* のようなストップワードを削除します。</span><span class="sxs-lookup"><span data-stu-id="a8283-203">Removes stopwords like *is* and *a*.</span></span> | <span data-ttu-id="a8283-204">["good","product"]</span><span class="sxs-lookup"><span data-stu-id="a8283-204">["good","product"]</span></span>
|<span data-ttu-id="a8283-205">4.MapValueToKey</span><span class="sxs-lookup"><span data-stu-id="a8283-205">4. MapValueToKey</span></span> | <span data-ttu-id="a8283-206">入力データに基づくキー (カテゴリ) に値をマップします</span><span class="sxs-lookup"><span data-stu-id="a8283-206">Maps the values to keys (categories) based on the input data</span></span> |  <span data-ttu-id="a8283-207">[1,2]</span><span class="sxs-lookup"><span data-stu-id="a8283-207">[1,2]</span></span>
|<span data-ttu-id="a8283-208">5.ProduceNGrams</span><span class="sxs-lookup"><span data-stu-id="a8283-208">5. ProduceNGrams</span></span> | <span data-ttu-id="a8283-209">テキストを連続する単語のシーケンスに変換します</span><span class="sxs-lookup"><span data-stu-id="a8283-209">Transforms text into sequence of consecutive words</span></span> | <span data-ttu-id="a8283-210">[1,1,1,0,0]</span><span class="sxs-lookup"><span data-stu-id="a8283-210">[1,1,1,0,0]</span></span>
|<span data-ttu-id="a8283-211">6.NormalizeLpNorm</span><span class="sxs-lookup"><span data-stu-id="a8283-211">6. NormalizeLpNorm</span></span> | <span data-ttu-id="a8283-212">lp 正則化によって入力値をスケーリングします</span><span class="sxs-lookup"><span data-stu-id="a8283-212">Scale inputs by their lp-norm</span></span> | <span data-ttu-id="a8283-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span><span class="sxs-lookup"><span data-stu-id="a8283-213">[ 0.577350529, 0.577350529, 0.577350529, 0, 0 ]</span></span>
