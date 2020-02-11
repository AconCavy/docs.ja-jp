---
title: 'チュートリアル: TensorFlow モデルを使用してレビューのセンチメントを分析する'
description: このチュートリアルでは、事前トレーニング済みの TensorFlow モデルを使用して、Web サイトのセンチメントを分類する方法について示します。 センチメントの 2 項分類子は、Visual Studio を使用して開発された C# コンソール アプリケーションです。
ms.date: 11/15/2019
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 7a6043f56a2ecaca633ba5545170f27a85a22efc
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092396"
---
# <a name="tutorial-analyze-sentiment-of-movie-reviews-using-a-pre-trained-tensorflow-model-in-mlnet"></a><span data-ttu-id="52e9c-104">チュートリアル: ML.NET で事前トレーニング済みの TensorFlow モデルを使用して映画レビューのセンチメントを分析する</span><span class="sxs-lookup"><span data-stu-id="52e9c-104">Tutorial: Analyze sentiment of movie reviews using a pre-trained TensorFlow model in ML.NET</span></span>

<span data-ttu-id="52e9c-105">このチュートリアルでは、事前トレーニング済みの TensorFlow モデルを使用して、Web サイトのセンチメントを分類する方法について示します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-105">This tutorial shows you how to use a pre-trained TensorFlow model to classify sentiment in website comments.</span></span> <span data-ttu-id="52e9c-106">センチメントの 2 項分類子は、Visual Studio を使用して開発された C# コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-106">The binary sentiment classifier is a C# console application developed using Visual Studio.</span></span>

<span data-ttu-id="52e9c-107">このチュートリアルで使用される TensorFlow モデルは、IMDB データベースの映画レビューを使用してトレーニングされました。</span><span class="sxs-lookup"><span data-stu-id="52e9c-107">The TensorFlow model used in this tutorial was trained using movie reviews from the IMDB database.</span></span> <span data-ttu-id="52e9c-108">アプリケーションの開発が完了すると、映画レビューのテキストを入力できるようになり、レビューに肯定的または否定的なセンチメントが含まれるかどうかがアプリケーションによって通知されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-108">Once you have finished developing the application, you will be able to supply movie review text and the application will tell you whether the review has positive or negative sentiment.</span></span>

<span data-ttu-id="52e9c-109">このチュートリアルでは、次の作業を行う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-109">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="52e9c-110">事前トレーニング済みの TensorFlow モデルを読み込む</span><span class="sxs-lookup"><span data-stu-id="52e9c-110">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="52e9c-111">Web サイトのコメント テキストをモデルに適したフィーチャーに変換する</span><span class="sxs-lookup"><span data-stu-id="52e9c-111">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="52e9c-112">モデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="52e9c-112">Use the model to make a prediction</span></span>

<span data-ttu-id="52e9c-113">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-113">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52e9c-114">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="52e9c-114">Prerequisites</span></span>

* <span data-ttu-id="52e9c-115">[Visual Studio 2017 バージョン 15.6 以降](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)が ".NET Core クロスプラットフォーム開発" ワークロードと共にインストールされている。</span><span class="sxs-lookup"><span data-stu-id="52e9c-115">[Visual Studio 2017 version 15.6 or later](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the ".NET Core cross-platform development" workload installed.</span></span>

## <a name="setup"></a><span data-ttu-id="52e9c-116">セットアップ</span><span class="sxs-lookup"><span data-stu-id="52e9c-116">Setup</span></span>

### <a name="create-the-application"></a><span data-ttu-id="52e9c-117">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="52e9c-117">Create the application</span></span>

1. <span data-ttu-id="52e9c-118">"TextClassificationTF" という名前の **.NET Core コンソール アプリケーション**を作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-118">Create a **.NET Core Console Application** called "TextClassificationTF".</span></span>

2. <span data-ttu-id="52e9c-119">データ セット ファイルを保存するために、プロジェクトに *Data* という名前のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-119">Create a directory named *Data* in your project to save your data set files.</span></span>

3. <span data-ttu-id="52e9c-120">**Microsoft.ML NuGet パッケージ**をインストールします。</span><span class="sxs-lookup"><span data-stu-id="52e9c-120">Install the **Microsoft.ML NuGet Package**:</span></span>

    <span data-ttu-id="52e9c-121">ソリューション エクスプローラーで、プロジェクトを右クリックし、 **[NuGet パッケージの管理]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-121">In Solution Explorer, right-click on your project and select **Manage NuGet Packages**.</span></span> <span data-ttu-id="52e9c-122">パッケージ ソースとして "nuget.org" を選択してから、 **[参照]** タブを選択します。**Microsoft.ML** を検索し、目的のパッケージを選択して、 **[インストール]** ボタンを選択します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-122">Choose "nuget.org" as the package source, and then select the **Browse** tab. Search for **Microsoft.ML**, select the package you want, and then select the **Install** button.</span></span> <span data-ttu-id="52e9c-123">選択したパッケージのライセンス条項に同意してインストールを続行します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-123">Proceed with the installation by agreeing to the license terms for the package you choose.</span></span> <span data-ttu-id="52e9c-124">**Microsoft.ML.TensorFlow** と **SciSharp.TensorFlow.Redist** にこれらの手順を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-124">Repeat these steps for **Microsoft.ML.TensorFlow** and **SciSharp.TensorFlow.Redist**.</span></span>

### <a name="add-the-tensorflow-model-to-the-project"></a><span data-ttu-id="52e9c-125">TensorFlow モデルをプロジェクトに追加する</span><span class="sxs-lookup"><span data-stu-id="52e9c-125">Add the TensorFlow model to the project</span></span>

> [!NOTE]
> <span data-ttu-id="52e9c-126">このチュートリアルのモデルは、[dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub リポジトリにあります。</span><span class="sxs-lookup"><span data-stu-id="52e9c-126">The model for this tutorial is from the [dotnet/machinelearning-testdata](https://github.com/dotnet/machinelearning-testdata/tree/master/Microsoft.ML.TensorFlow.TestModels/sentiment_model) GitHub repo.</span></span> <span data-ttu-id="52e9c-127">このモデルは TensorFlow SavedModel 形式です。</span><span class="sxs-lookup"><span data-stu-id="52e9c-127">The model is in TensorFlow SavedModel format.</span></span>

1. <span data-ttu-id="52e9c-128">[sentiment_model ZIP ファイル](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true)をダウンロードして解凍します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-128">Download the [sentiment_model zip file](https://github.com/dotnet/samples/blob/master/machine-learning/models/textclassificationtf/sentiment_model.zip?raw=true), and unzip.</span></span>

    <span data-ttu-id="52e9c-129">ZIP ファイルには次のものが含まれています。</span><span class="sxs-lookup"><span data-stu-id="52e9c-129">The zip file contains:</span></span>

    * <span data-ttu-id="52e9c-130">`saved_model.pb`: TensorFlow モデルそのもの。</span><span class="sxs-lookup"><span data-stu-id="52e9c-130">`saved_model.pb`: the TensorFlow model itself.</span></span> <span data-ttu-id="52e9c-131">このモデルは、IMDB レビューの文字列内のテキストを表すフィーチャーの固定長 (サイズ 600) の整数配列を受け取り、合計が 1 になる 2 つの確率を出力します。これは、入力レビューに肯定的センチメントが含まれる確率と、入力レビューに否定的センチメントが含まれる確率です。</span><span class="sxs-lookup"><span data-stu-id="52e9c-131">The model takes a fixed length (size 600) integer array of features representing the text in an IMDB review string, and outputs two probabilities which sum to 1: the probability that the input review has positive sentiment, and the probability that the input review has negative sentiment.</span></span>
    * <span data-ttu-id="52e9c-132">`imdb_word_index.csv`: 個々の単語から整数値へのマッピング。</span><span class="sxs-lookup"><span data-stu-id="52e9c-132">`imdb_word_index.csv`: a mapping from individual words to an integer value.</span></span> <span data-ttu-id="52e9c-133">マッピングは、TensorFlow モデル用に入力機能を作成するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-133">The mapping is used to generate the input features for the TensorFlow model.</span></span>

2. <span data-ttu-id="52e9c-134">最深部の `sentiment_model` ディレクトリの内容を *TextClassificationTF* プロジェクトの `sentiment_model` ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="52e9c-134">Copy the contents of the innermost `sentiment_model` directory into your *TextClassificationTF* project `sentiment_model` directory.</span></span> <span data-ttu-id="52e9c-135">次の画像に示すように、このディレクトリには、このチュートリアルに必要なモデルと追加のサポート ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="52e9c-135">This directory contains the model and additional support files needed for this tutorial, as shown in the following image:</span></span>

   ![sentiment_model ディレクトリ コンテンツ](./media/text-classification-tf/sentiment-model-files.png)

3. <span data-ttu-id="52e9c-137">ソリューション エクスプローラーで、`sentiment_model` ディレクトリとサブディレクトリ内の各ファイルを右クリックし、 **[プロパティ]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-137">In Solution Explorer, right-click each of the files in the `sentiment_model` directory and subdirectory and select **Properties**.</span></span> <span data-ttu-id="52e9c-138">**[詳細設定]** で、 **[出力ディレクトリにコピー]** の値を **[新しい場合はコピーする]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-138">Under **Advanced**, change the value of **Copy to Output Directory** to **Copy if newer**.</span></span>

### <a name="add-using-statements-and-global-variables"></a><span data-ttu-id="52e9c-139">using ステートメントとグローバル変数を追加する</span><span class="sxs-lookup"><span data-stu-id="52e9c-139">Add using statements and global variables</span></span>

1. <span data-ttu-id="52e9c-140">次に示す追加の `using` ステートメントを *Program.cs* ファイルの先頭に追加します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-140">Add the following additional `using` statements to the top of the *Program.cs* file:</span></span>

   [!code-csharp[AddUsings](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#AddUsings "Add necessary usings")]

1. <span data-ttu-id="52e9c-141">保存したモデルのファイル パスとフィーチャーのベクターの長さを保持するために、`Main` メソッドの真上にグローバル変数を 2 つ作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-141">Create two global variables right above the `Main` method to hold the saved model file path, and the feature vector length.</span></span>

   [!code-csharp[DeclareGlobalVariables](../../../samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DeclareGlobalVariables "Declare global variables")]

    * <span data-ttu-id="52e9c-142">`_modelPath` は、トレーニング済みモデルのファイル パスです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-142">`_modelPath` is the file path of the trained model.</span></span>
    * <span data-ttu-id="52e9c-143">`FeatureLength` は、モデルで想定している整数フィーチャー配列の長さです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-143">`FeatureLength` is the length of the integer feature array that the model is expecting.</span></span>

### <a name="model-the-data"></a><span data-ttu-id="52e9c-144">データのモデル化</span><span class="sxs-lookup"><span data-stu-id="52e9c-144">Model the data</span></span>

<span data-ttu-id="52e9c-145">映画レビューは自由形式のテキストです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-145">Movie reviews are free form text.</span></span> <span data-ttu-id="52e9c-146">アプリケーションでは、テキストがさまざまな個別のステージでモデルによって想定される入力形式に変換されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-146">Your application converts the text into the input format expected by the model in a number of discrete stages.</span></span>

<span data-ttu-id="52e9c-147">最初にテキストを別々の単語に分割し、指定されたマッピング ファイルを使用して各単語を整数のエンコードにマップします。</span><span class="sxs-lookup"><span data-stu-id="52e9c-147">The first is to split the text into separate words and use the provided mapping file to map each word onto an integer encoding.</span></span> <span data-ttu-id="52e9c-148">この変換の結果、文章内の単語数に応じた長さの可変長の整数配列になります。</span><span class="sxs-lookup"><span data-stu-id="52e9c-148">The result of this transformation is a variable length integer array with a length corresponding to the number of words in the sentence.</span></span>

|<span data-ttu-id="52e9c-149">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52e9c-149">Property</span></span>| <span data-ttu-id="52e9c-150">[値]</span><span class="sxs-lookup"><span data-stu-id="52e9c-150">Value</span></span>|<span data-ttu-id="52e9c-151">種類</span><span class="sxs-lookup"><span data-stu-id="52e9c-151">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="52e9c-152">ReviewText</span><span class="sxs-lookup"><span data-stu-id="52e9c-152">ReviewText</span></span>|<span data-ttu-id="52e9c-153">この映画は本当に良い</span><span class="sxs-lookup"><span data-stu-id="52e9c-153">this film is really good</span></span>|<span data-ttu-id="52e9c-154">string</span><span class="sxs-lookup"><span data-stu-id="52e9c-154">string</span></span>|
|<span data-ttu-id="52e9c-155">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="52e9c-155">VariableLengthFeatures</span></span>|<span data-ttu-id="52e9c-156">14、22、9、66、78、...</span><span class="sxs-lookup"><span data-stu-id="52e9c-156">14,22,9,66,78,...</span></span> |<span data-ttu-id="52e9c-157">int[]</span><span class="sxs-lookup"><span data-stu-id="52e9c-157">int[]</span></span>|

<span data-ttu-id="52e9c-158">可変長フィーチャーの配列は、固定長が 600 に変更されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-158">The variable length feature array is then resized to a fixed length of 600.</span></span> <span data-ttu-id="52e9c-159">これは、TensorFlow モデルで想定される長さです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-159">This is the length that the TensorFlow model expects.</span></span>

|<span data-ttu-id="52e9c-160">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52e9c-160">Property</span></span>| <span data-ttu-id="52e9c-161">[値]</span><span class="sxs-lookup"><span data-stu-id="52e9c-161">Value</span></span>|<span data-ttu-id="52e9c-162">種類</span><span class="sxs-lookup"><span data-stu-id="52e9c-162">Type</span></span>|
|-------------|-----------------------|------|
|<span data-ttu-id="52e9c-163">ReviewText</span><span class="sxs-lookup"><span data-stu-id="52e9c-163">ReviewText</span></span>|<span data-ttu-id="52e9c-164">この映画は本当に良い</span><span class="sxs-lookup"><span data-stu-id="52e9c-164">this film is really good</span></span>|<span data-ttu-id="52e9c-165">string</span><span class="sxs-lookup"><span data-stu-id="52e9c-165">string</span></span>|
|<span data-ttu-id="52e9c-166">VariableLengthFeatures</span><span class="sxs-lookup"><span data-stu-id="52e9c-166">VariableLengthFeatures</span></span>|<span data-ttu-id="52e9c-167">14、22、9、66、78、...</span><span class="sxs-lookup"><span data-stu-id="52e9c-167">14,22,9,66,78,...</span></span> |<span data-ttu-id="52e9c-168">int[]</span><span class="sxs-lookup"><span data-stu-id="52e9c-168">int[]</span></span>|
|<span data-ttu-id="52e9c-169">フィーチャー</span><span class="sxs-lookup"><span data-stu-id="52e9c-169">Features</span></span>|<span data-ttu-id="52e9c-170">14、22、9、66、78、...</span><span class="sxs-lookup"><span data-stu-id="52e9c-170">14,22,9,66,78,...</span></span> |<span data-ttu-id="52e9c-171">int[600]</span><span class="sxs-lookup"><span data-stu-id="52e9c-171">int[600]</span></span>|

1. <span data-ttu-id="52e9c-172">`Main` メソッドの後に、入力データ用のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-172">Create a class for your input data, after the `Main` method:</span></span>

    [!code-csharp[MovieReviewClass](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MovieReviewClass "Declare movie review type")]

    <span data-ttu-id="52e9c-173">入力データ クラス (`MovieReview`) には、ユーザー コメント (`ReviewText`) 用の `string` があります。</span><span class="sxs-lookup"><span data-stu-id="52e9c-173">The input data class, `MovieReview`, has a `string` for user comments (`ReviewText`).</span></span>

1. <span data-ttu-id="52e9c-174">次の `Main` メソッドの後に、可変長フィーチャー用のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-174">Create a class for the variable length features, after the `Main` method:</span></span>

    [!code-csharp[VariableLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#VariableLengthFeatures "Declare variable length features type")]

    <span data-ttu-id="52e9c-175">`VariableLengthFeatures` プロパティには、ベクターとして指定する [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-175">The `VariableLengthFeatures` property has a [VectorType](xref:Microsoft.ML.Data.VectorTypeAttribute.%23ctor%2A) attribute to designate it as a vector.</span></span>  <span data-ttu-id="52e9c-176">ベクター要素はすべて同じ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="52e9c-176">All of the vector elements must be the same type.</span></span> <span data-ttu-id="52e9c-177">列が多いデータ セットでは、複数の列を 1 つのベクターとして読み込むことで、データ変換を適用するときのデータ パスの数が減少します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-177">In data sets with a large number of columns, loading multiple columns as a single vector reduces the number of data passes when you apply data transformations.</span></span>

    <span data-ttu-id="52e9c-178">このクラスは、`ResizeFeatures` アクションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-178">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="52e9c-179">プロパティの名前 (この場合は 1 つのみ) を使用して、カスタム マッピング アクションへの_入力_として使用できる DataView 内の列を示します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-179">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _input_ to the custom mapping action.</span></span>

1. <span data-ttu-id="52e9c-180">次の `Main` メソッドの後に、固定長フィーチャー用のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-180">Create a class for the fixed length features, after the `Main` method:</span></span>

    [!code-csharp[FixedLengthFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#FixedLengthFeatures)]

    <span data-ttu-id="52e9c-181">このクラスは、`ResizeFeatures` アクションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-181">This class is used in the `ResizeFeatures` action.</span></span> <span data-ttu-id="52e9c-182">プロパティの名前 (この場合は 1 つのみ) を使用して、カスタム マッピング アクションへの_出力_として使用できる DataView 内の列を示します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-182">The names of its properties (in this case only one) are used to indicate which columns in the DataView can be used as the _output_ of the custom mapping action.</span></span>

    <span data-ttu-id="52e9c-183">プロパティ `Features` の名前は、TensorFlow モデルによって決定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="52e9c-183">Note that the name of the property `Features` is determined by the TensorFlow model.</span></span> <span data-ttu-id="52e9c-184">このプロパティ名は変更できません。</span><span class="sxs-lookup"><span data-stu-id="52e9c-184">You cannot change this property name.</span></span>

1. <span data-ttu-id="52e9c-185">次の `Main` メソッドの後に、予測用のクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-185">Create a class for the prediction after the `Main` method:</span></span>

    [!code-csharp[Prediction](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Prediction "Declare prediction class")]

    <span data-ttu-id="52e9c-186">`MovieReviewSentimentPrediction` はモデルのトレーニング後に使用される予測クラスです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-186">`MovieReviewSentimentPrediction` is the prediction class used after the model training.</span></span> <span data-ttu-id="52e9c-187">`MovieReviewSentimentPrediction` には、1 つの `float` 配列 (`Prediction`) と `VectorType` 属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-187">`MovieReviewSentimentPrediction` has a single `float` array (`Prediction`) and a `VectorType` attribute.</span></span>

### <a name="create-the-mlcontext-lookup-dictionary-and-action-to-resize-features"></a><span data-ttu-id="52e9c-188">MLContext、検索ディクショナリ、フィーチャーのサイズを変更するアクションを作成する</span><span class="sxs-lookup"><span data-stu-id="52e9c-188">Create the MLContext, lookup dictionary, and action to resize features</span></span>

<span data-ttu-id="52e9c-189">[MLContext クラス](xref:Microsoft.ML.MLContext)は、すべての ML.NET 操作の始点です。</span><span class="sxs-lookup"><span data-stu-id="52e9c-189">The [MLContext class](xref:Microsoft.ML.MLContext) is a starting point for all ML.NET operations.</span></span> <span data-ttu-id="52e9c-190">`mlContext` を初期化することで、モデル作成ワークフローのオブジェクト間で共有できる新しい ML.NET 環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-190">Initializing `mlContext` creates a new ML.NET environment that can be shared across the model creation workflow objects.</span></span> <span data-ttu-id="52e9c-191">これは Entity Framework における `DBContext` と概念的には同じです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-191">It's similar, conceptually, to `DBContext` in Entity Framework.</span></span>

1. <span data-ttu-id="52e9c-192">`Main` メソッドの `Console.WriteLine("Hello World!")` の行は、mlContext 変数を宣言して初期化する次のコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-192">Replace the `Console.WriteLine("Hello World!")` line in the `Main` method with the following code to declare and initialize the mlContext variable:</span></span>

   [!code-csharp[CreateMLContext](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateMLContext "Create the ML Context")]

1. <span data-ttu-id="52e9c-193">次の表に示すように、[`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) メソッドを使用して単語を整数としてエンコードするディクショナリを作成し、ファイルからマッピング データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-193">Create a dictionary to encode words as integers by using the [`LoadFromTextFile`](xref:Microsoft.ML.TextLoaderSaverCatalog.LoadFromTextFile%2A) method to load mapping data from a file, as seen in the following table:</span></span>

    |<span data-ttu-id="52e9c-194">単語</span><span class="sxs-lookup"><span data-stu-id="52e9c-194">Word</span></span>     |<span data-ttu-id="52e9c-195">インデックス</span><span class="sxs-lookup"><span data-stu-id="52e9c-195">Index</span></span>    |
    |---------|---------|
    |<span data-ttu-id="52e9c-196">子供向け</span><span class="sxs-lookup"><span data-stu-id="52e9c-196">kids</span></span>     |  <span data-ttu-id="52e9c-197">362</span><span class="sxs-lookup"><span data-stu-id="52e9c-197">362</span></span>    |
    |<span data-ttu-id="52e9c-198">必要</span><span class="sxs-lookup"><span data-stu-id="52e9c-198">want</span></span>     |  <span data-ttu-id="52e9c-199">181</span><span class="sxs-lookup"><span data-stu-id="52e9c-199">181</span></span>    |
    |<span data-ttu-id="52e9c-200">不適切</span><span class="sxs-lookup"><span data-stu-id="52e9c-200">wrong</span></span>    |  <span data-ttu-id="52e9c-201">355</span><span class="sxs-lookup"><span data-stu-id="52e9c-201">355</span></span>    |
    |<span data-ttu-id="52e9c-202">効果</span><span class="sxs-lookup"><span data-stu-id="52e9c-202">effects</span></span>  |  <span data-ttu-id="52e9c-203">302</span><span class="sxs-lookup"><span data-stu-id="52e9c-203">302</span></span>    |
    |<span data-ttu-id="52e9c-204">感覚</span><span class="sxs-lookup"><span data-stu-id="52e9c-204">feeling</span></span>  |  <span data-ttu-id="52e9c-205">547</span><span class="sxs-lookup"><span data-stu-id="52e9c-205">547</span></span>    |

    <span data-ttu-id="52e9c-206">次のコードを追加して、検索マップを作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-206">Add the code below to create the lookup map:</span></span>

    [!code-csharp[CreateLookupMap](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateLookupMap)]

1. <span data-ttu-id="52e9c-207">`Action` を追加して、可変長単語の整数配列のサイズを固定サイズの整数配列に変更します。次のコード行を使用します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-207">Add an `Action` to resize the variable length word integer array to an integer array of fixed size, with the next lines of code:</span></span>

   [!code-csharp[ResizeFeatures](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ResizeFeatures)]

## <a name="load-the-pre-trained-tensorflow-model"></a><span data-ttu-id="52e9c-208">事前トレーニング済みの TensorFlow モデルを読み込む</span><span class="sxs-lookup"><span data-stu-id="52e9c-208">Load the pre-trained TensorFlow model</span></span>

1. <span data-ttu-id="52e9c-209">TensorFlow モデルを読み込むためのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-209">Add code to load the TensorFlow model:</span></span>

    [!code-csharp[LoadTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#LoadTensorFlowModel)]

    <span data-ttu-id="52e9c-210">モデルが読み込まれたら、その入力および出力スキーマを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-210">Once the model is loaded, you can extract its input and output schema.</span></span> <span data-ttu-id="52e9c-211">スキーマは、参考および学習の目的のためにのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-211">The schemas are displayed for interest and learning only.</span></span> <span data-ttu-id="52e9c-212">最終的なアプリケーションを機能させるためには、このコードは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="52e9c-212">You do not need this code for the final application to function:</span></span>

    [!code-csharp[GetModelSchema](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#GetModelSchema)]

    <span data-ttu-id="52e9c-213">入力スキーマは、整数でエンコードされた単語の固定長配列です。</span><span class="sxs-lookup"><span data-stu-id="52e9c-213">The input schema is the fixed-length array of integer encoded words.</span></span> <span data-ttu-id="52e9c-214">出力スキーマは、レビューのセンチメントが否定的であるか、肯定的であるかを示す、確率の float 型配列です。</span><span class="sxs-lookup"><span data-stu-id="52e9c-214">The output schema is a float array of probabilities indicating whether a review's sentiment is negative, or positive .</span></span> <span data-ttu-id="52e9c-215">肯定的な確率は否定的なセンチメントの確率の補数であるため、これらの値の合計は 1 になります。</span><span class="sxs-lookup"><span data-stu-id="52e9c-215">These values sum to 1, as the probability of being positive is the complement of the probability of the sentiment being negative.</span></span>

## <a name="create-the-mlnet-pipeline"></a><span data-ttu-id="52e9c-216">ML.NET パイプラインを作成する</span><span class="sxs-lookup"><span data-stu-id="52e9c-216">Create the ML.NET pipeline</span></span>

1. <span data-ttu-id="52e9c-217">パイプラインを作成し、[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) 変換を使用して入力テキストを単語に分割し、次のコード行としてテキストを単語に分割します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-217">Create the pipeline and split the input text into words using [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform to break the text into words as the next line of code:</span></span>

   [!code-csharp[TokenizeIntoWords](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#TokenizeIntoWords)]

   <span data-ttu-id="52e9c-218">[TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) 変換では、スペースを使用してテキストまたは文字列を単語に解析します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-218">The [TokenizeIntoWords](xref:Microsoft.ML.TextCatalog.TokenizeIntoWords%2A) transform uses spaces to parse the text/string into words.</span></span> <span data-ttu-id="52e9c-219">これにより、新しい列が作成され、ユーザー定義の区切り記号に基づいて各入力文字列を部分文字列のベクターに分割します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-219">It creates a new column and splits each input string to a vector of substrings based on the user-defined separator.</span></span>

1. <span data-ttu-id="52e9c-220">上記で宣言した参照テーブルを使用して、単語を整数エンコードにマップします。</span><span class="sxs-lookup"><span data-stu-id="52e9c-220">Map the words onto their integer encoding using the lookup table that you declared above:</span></span>

    [!code-csharp[MapValue](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#MapValue)]

1. <span data-ttu-id="52e9c-221">可変長の整数エンコーディングのサイズを、モデルで必要とされる固定長に変更します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-221">Resize the variable length integer encodings to the fixed-length one required by the model:</span></span>

    [!code-csharp[CustomMapping](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CustomMapping)]

1. <span data-ttu-id="52e9c-222">読み込まれた TensorFlow モデルで入力を分類します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-222">Classify the input with the loaded TensorFlow model:</span></span>

    [!code-csharp[ScoreTensorFlowModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#ScoreTensorFlowModel)]

    <span data-ttu-id="52e9c-223">TensorFlow モデルの出力は `Prediction/Softmax` と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-223">The TensorFlow model output is called `Prediction/Softmax`.</span></span> <span data-ttu-id="52e9c-224">この名前 `Prediction/Softmax` は、TensorFlow モデルによって決定されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="52e9c-224">Note that the name `Prediction/Softmax` is determined by the TensorFlow model.</span></span> <span data-ttu-id="52e9c-225">この名前は変更できません。</span><span class="sxs-lookup"><span data-stu-id="52e9c-225">You cannot change this name.</span></span>

1. <span data-ttu-id="52e9c-226">出力予測用に新しい列を作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-226">Create a new column for the output prediction:</span></span>

    [!code-csharp[SnippetCopyColumns](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCopyColumns)]

    <span data-ttu-id="52e9c-227">`Prediction/Softmax` 列を C# クラス `Prediction` のプロパティとして使用できる名前を持つ列にコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="52e9c-227">You need to copy the `Prediction/Softmax` column into one with a name that can be used as a property in a C# class: `Prediction`.</span></span> <span data-ttu-id="52e9c-228">`/` 文字は、C# プロパティ名では使用できません。</span><span class="sxs-lookup"><span data-stu-id="52e9c-228">The `/` character is not allowed in a C# property name.</span></span>

## <a name="create-the-mlnet-model-from-the-pipeline"></a><span data-ttu-id="52e9c-229">パイプラインから ML.NET モデルを作成する</span><span class="sxs-lookup"><span data-stu-id="52e9c-229">Create the ML.NET model from the pipeline</span></span>

1. <span data-ttu-id="52e9c-230">パイプラインからモデルを作成するためのコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-230">Add the code to create the model from the pipeline:</span></span>

    [!code-csharp[SnippetCreateModel](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#SnippetCreateModel)]

    <span data-ttu-id="52e9c-231">ML.NET モデルは、`Fit` メソッドを呼び出すことによって、パイプラインのエスティメーターのチェーンから作成されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-231">An ML.NET model is created from the chain of estimators in the pipeline by calling the `Fit` method.</span></span> <span data-ttu-id="52e9c-232">この場合、TensorFlow モデルは既に以前トレーニングされているため、モデルを作成するためのデータを調整することはありません。</span><span class="sxs-lookup"><span data-stu-id="52e9c-232">In this case, we are not fitting any data to create the model, as the TensorFlow model has already been previously trained.</span></span> <span data-ttu-id="52e9c-233">`Fit` メソッドの要件を満たすために、空のデータ ビュー オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-233">We supply an empty data view object to satisfy the requirements of the `Fit` method.</span></span>

## <a name="use-the-model-to-make-a-prediction"></a><span data-ttu-id="52e9c-234">モデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="52e9c-234">Use the model to make a prediction</span></span>

1. <span data-ttu-id="52e9c-235">`PredictSentiment` メソッドを `Main` メソッドの下に追加します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-235">Add the `PredictSentiment` method below the `Main` method:</span></span>

    ```csharp
    public static void PredictSentiment(MLContext mlContext, ITransformer model)
    {

    }
    ```

1. <span data-ttu-id="52e9c-236">次のコードを追加して、`PredictionEngine` を `PredictSentiment()` メソッドの 1 行目として作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-236">Add the following code to create the `PredictionEngine` as the first line in the `PredictSentiment()` method:</span></span>

    [!code-csharp[CreatePredictionEngine](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreatePredictionEngine)]

    <span data-ttu-id="52e9c-237">[PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) は、データの 1 つのインスタンスに対して予測を実行できる便利な API です。</span><span class="sxs-lookup"><span data-stu-id="52e9c-237">The [PredictionEngine](xref:Microsoft.ML.PredictionEngine%602) is a convenience API, which allows you to perform a prediction on a single instance of data.</span></span> <span data-ttu-id="52e9c-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) はスレッド セーフではありません。</span><span class="sxs-lookup"><span data-stu-id="52e9c-238">[`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) is not thread-safe.</span></span> <span data-ttu-id="52e9c-239">シングル スレッド環境またはプロトタイプ環境で使用できます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-239">It's acceptable to use in single-threaded or prototype environments.</span></span> <span data-ttu-id="52e9c-240">運用環境でパフォーマンスとスレッド セーフを向上させるには、`PredictionEnginePool` サービスを使用します。これにより、アプリケーション全体で使用するできる [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) オブジェクトの [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-240">For improved performance and thread safety in production environments, use the `PredictionEnginePool` service, which creates an [`ObjectPool`](xref:Microsoft.Extensions.ObjectPool.ObjectPool%601) of [`PredictionEngine`](xref:Microsoft.ML.PredictionEngine%602) objects for use throughout your application.</span></span> <span data-ttu-id="52e9c-241">[ASP.NET Core Web API で `PredictionEnginePool` を使用する](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application)方法については、こちらのガイドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="52e9c-241">See this guide on how to [use `PredictionEnginePool` in an ASP.NET Core Web API](../how-to-guides/serve-model-web-api-ml-net.md#register-predictionenginepool-for-use-in-the-application).</span></span>

    > [!NOTE]
    > <span data-ttu-id="52e9c-242">`PredictionEnginePool` サービスの拡張機能は、現在プレビュー段階です。</span><span class="sxs-lookup"><span data-stu-id="52e9c-242">`PredictionEnginePool` service extension is currently in preview.</span></span>

1. <span data-ttu-id="52e9c-243">コメントを追加して、`Predict()` メソッドでトレーニングされたモデルの予測をテストします。これには `MovieReview` のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-243">Add a comment to test the trained model's prediction in the `Predict()` method by creating an instance of `MovieReview`:</span></span>

    [!code-csharp[CreateTestData](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CreateTestData)]

1. <span data-ttu-id="52e9c-244">`PredictSentiment()` メソッドに次のコード行を追加することで、テスト コメント データを `Prediction Engine` に渡します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-244">Pass the test comment data to the `Prediction Engine` by adding the next lines of code in the `PredictSentiment()` method:</span></span>

    [!code-csharp[Predict](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#Predict)]

1. <span data-ttu-id="52e9c-245">[Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) 関数では、データの単一行に対して予測を行います。</span><span class="sxs-lookup"><span data-stu-id="52e9c-245">The [Predict()](xref:Microsoft.ML.PredictionEngine%602.Predict%2A) function makes a prediction on a single row of data:</span></span>

    |<span data-ttu-id="52e9c-246">プロパティ</span><span class="sxs-lookup"><span data-stu-id="52e9c-246">Property</span></span>| <span data-ttu-id="52e9c-247">[値]</span><span class="sxs-lookup"><span data-stu-id="52e9c-247">Value</span></span>|<span data-ttu-id="52e9c-248">種類</span><span class="sxs-lookup"><span data-stu-id="52e9c-248">Type</span></span>|
    |-------------|-----------------------|------|
    |<span data-ttu-id="52e9c-249">予測</span><span class="sxs-lookup"><span data-stu-id="52e9c-249">Prediction</span></span>|<span data-ttu-id="52e9c-250">[0.5459937, 0.454006255]</span><span class="sxs-lookup"><span data-stu-id="52e9c-250">[0.5459937, 0.454006255]</span></span>|<span data-ttu-id="52e9c-251">float[]</span><span class="sxs-lookup"><span data-stu-id="52e9c-251">float[]</span></span>|

1. <span data-ttu-id="52e9c-252">次のコードを使用して、センチメント予測を表示します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-252">Display sentiment prediction using the following code:</span></span>

    [!code-csharp[DisplayPredictions](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#DisplayPredictions)]

1. <span data-ttu-id="52e9c-253">`Main` メソッドの末尾に、`PredictSentiment` に対する呼び出しを追加します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-253">Add a call to `PredictSentiment` at the end of the `Main` method:</span></span>

    [!code-csharp[CallPredictSentiment](~/samples/machine-learning/tutorials/TextClassificationTF/Program.cs#CallPredictSentiment)]

## <a name="results"></a><span data-ttu-id="52e9c-254">結果</span><span class="sxs-lookup"><span data-stu-id="52e9c-254">Results</span></span>

<span data-ttu-id="52e9c-255">アプリケーションをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="52e9c-255">Build and run your application.</span></span>

<span data-ttu-id="52e9c-256">結果は以下のようになるはずです。</span><span class="sxs-lookup"><span data-stu-id="52e9c-256">Your results should be similar to the following.</span></span> <span data-ttu-id="52e9c-257">処理中にメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-257">During processing, messages are displayed.</span></span> <span data-ttu-id="52e9c-258">警告または処理メッセージが表示されることがありますが、</span><span class="sxs-lookup"><span data-stu-id="52e9c-258">You may see warnings, or processing messages.</span></span> <span data-ttu-id="52e9c-259">わかりやすくするために、これらのメッセージは次の結果から削除してあります。</span><span class="sxs-lookup"><span data-stu-id="52e9c-259">These messages have been removed from the following results for clarity.</span></span>

```console
Number of classes: 2
Is sentiment/review positive ? Yes
```

<span data-ttu-id="52e9c-260">おめでとうございます!</span><span class="sxs-lookup"><span data-stu-id="52e9c-260">Congratulations!</span></span> <span data-ttu-id="52e9c-261">これで、ML.NET で事前トレーニング済みの `TensorFlow` モデルを再利用することにより、メッセージのセンチメントを分類および予測するための機械学習モデルをビルドできました。</span><span class="sxs-lookup"><span data-stu-id="52e9c-261">You've now successfully built a machine learning model for classifying and predicting messages sentiment by reusing a pre-trained `TensorFlow` model in ML.NET.</span></span>

<span data-ttu-id="52e9c-262">このチュートリアルのソース コードは [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) リポジトリで確認できます。</span><span class="sxs-lookup"><span data-stu-id="52e9c-262">You can find the source code for this tutorial at the [dotnet/samples](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/TextClassificationTF) repository.</span></span>

<span data-ttu-id="52e9c-263">このチュートリアルでは、次の作業を行う方法を学びました。</span><span class="sxs-lookup"><span data-stu-id="52e9c-263">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> * <span data-ttu-id="52e9c-264">事前トレーニング済みの TensorFlow モデルを読み込む</span><span class="sxs-lookup"><span data-stu-id="52e9c-264">Load a pre-trained TensorFlow model</span></span>
> * <span data-ttu-id="52e9c-265">Web サイトのコメント テキストをモデルに適したフィーチャーに変換する</span><span class="sxs-lookup"><span data-stu-id="52e9c-265">Transform website comment text into features suitable for the model</span></span>
> * <span data-ttu-id="52e9c-266">モデルを使用して予測する</span><span class="sxs-lookup"><span data-stu-id="52e9c-266">Use the model to make a prediction</span></span>
