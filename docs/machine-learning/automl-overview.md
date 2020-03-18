---
title: ML.NET による自動機械学習
description: 自動モデル選択およびトレーニングの概要
ms.date: 05/01/2019
ms.topic: overview
ms.custom: mvc, mlnet-tooling
ms.openlocfilehash: acd6cae71d2d5d79209a77d34175e7f1b3c1ee35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "78849355"
---
# <a name="automated-machine-learning-with-mlnet"></a><span data-ttu-id="8952c-103">ML.NET による自動機械学習</span><span class="sxs-lookup"><span data-stu-id="8952c-103">Automated machine learning with ML.NET</span></span>

<span data-ttu-id="8952c-104">自動機械学習は、自動モデル選択およびトレーニングを実行する ML.NET の機能です。</span><span class="sxs-lookup"><span data-stu-id="8952c-104">Automated machine learning is a feature of ML.NET that performs automatic model selection and training.</span></span> <span data-ttu-id="8952c-105">機械学習タスクを指定し、データセットを指定すると、自動 ML によって最適なメトリックのモデルが選択されます。</span><span class="sxs-lookup"><span data-stu-id="8952c-105">You specify the machine learning task and supply a dataset, and automated ML chooses the model with the best metrics.</span></span> <span data-ttu-id="8952c-106">出力内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="8952c-106">It outputs:</span></span>

- <span data-ttu-id="8952c-107">予測アプリケーションに読み込むことができるモデル ファイル</span><span class="sxs-lookup"><span data-stu-id="8952c-107">a model file that can be loaded into your prediction application</span></span>
- <span data-ttu-id="8952c-108">予測を行うアプリケーション コード</span><span class="sxs-lookup"><span data-stu-id="8952c-108">application code to make predictions</span></span>
- <span data-ttu-id="8952c-109">(モデルを理解するために) 特徴の選択とモデルのトレーニングに使用されるソース コード</span><span class="sxs-lookup"><span data-stu-id="8952c-109">the source code used for feature selection and model training (to understand the model)</span></span>

> [!NOTE]
> <span data-ttu-id="8952c-110">この機能は現在プレビュー段階であり、資料は変更される場合があります。</span><span class="sxs-lookup"><span data-stu-id="8952c-110">This feature is currently in Preview, and material may be subject to change.</span></span>

<span data-ttu-id="8952c-111">現在、自動 ML は二項分類、多クラス分類、回帰の機械学習[タスク](resources/tasks.md)に限定されています。</span><span class="sxs-lookup"><span data-stu-id="8952c-111">Automated ML is currently limited to the machine learning [tasks](resources/tasks.md) of binary classification, multiclass classification, and regression.</span></span> <span data-ttu-id="8952c-112">他の機械学習タスクが今後のリリースでサポートされる予定です。</span><span class="sxs-lookup"><span data-stu-id="8952c-112">The other machine learning tasks will be supported in future releases.</span></span>

<span data-ttu-id="8952c-113">自動 ML を使用する方法は 3 つあります。</span><span class="sxs-lookup"><span data-stu-id="8952c-113">There are three ways to use automated ML:</span></span>

1. <span data-ttu-id="8952c-114">[ML.NET モデル ビルダー](automate-training-with-model-builder.md) でグラフィカル ユーザー インターフェイスを使用する</span><span class="sxs-lookup"><span data-stu-id="8952c-114">With a graphical user interface, with the [ML.NET Model Builder](automate-training-with-model-builder.md)</span></span>
1. <span data-ttu-id="8952c-115">コマンド ライン上で [ML.NET CLI](automate-training-with-cli.md) を使用する</span><span class="sxs-lookup"><span data-stu-id="8952c-115">On the command line, with the [ML.NET CLI](automate-training-with-cli.md)</span></span>
1. <span data-ttu-id="8952c-116">アプリケーションを介して[自動 ML API](how-to-guides/how-to-use-the-automl-api.md) を使用する</span><span class="sxs-lookup"><span data-stu-id="8952c-116">Via an application, with the [automated ML API](how-to-guides/how-to-use-the-automl-api.md)</span></span>
