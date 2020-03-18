---
title: 高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する
description: Azure Kubernetes Service を使用して、アプリケーションをデプロイする方法について説明します。
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "71182370"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="7213f-103">Azure Kubernetes Service (AKS) へのデプロイ</span><span class="sxs-lookup"><span data-stu-id="7213f-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="7213f-104">推奨されるクライアント オペレーティング システムを使用して AKS とやりとりできます。ここでは、Microsoft Windows と Windows での Ubuntu Linux の埋め込みバージョンで、Bash コマンドを使用してそれを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7213f-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="7213f-105">AKS を使用前に準備しておく前提条件は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="7213f-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="7213f-106">Linux または Mac の開発用コンピューター</span><span class="sxs-lookup"><span data-stu-id="7213f-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="7213f-107">Windows の開発用コンピューター</span><span class="sxs-lookup"><span data-stu-id="7213f-107">Windows development machine</span></span>
  - <span data-ttu-id="7213f-108">Windows で開発者モードが有効にされている</span><span class="sxs-lookup"><span data-stu-id="7213f-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="7213f-109">Windows Subsystem for Linux</span><span class="sxs-lookup"><span data-stu-id="7213f-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="7213f-110">[Windows、Mac、または Linux](https://docs.microsoft.com/cli/azure/install-azure-cli) に Azure CLI がインストールされている</span><span class="sxs-lookup"><span data-stu-id="7213f-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)</span></span>

> [!NOTE]
> <span data-ttu-id="7213f-111">次に関する完全な情報を検索するには:</span><span class="sxs-lookup"><span data-stu-id="7213f-111">To find complete information about:</span></span>
>
> <span data-ttu-id="7213f-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span><span class="sxs-lookup"><span data-stu-id="7213f-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index></span></span>
>
> <span data-ttu-id="7213f-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="7213f-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="7213f-114">Azure で AKS 環境を作成する</span><span class="sxs-lookup"><span data-stu-id="7213f-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="7213f-115">AKS 環境を作成するにはいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="7213f-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="7213f-116">これを行うには、Azure CLI コマンドを使用するか、または Azure portal を使用します。</span><span class="sxs-lookup"><span data-stu-id="7213f-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="7213f-117">ここでは、Azure CLI を使用して、クラスターを作成し、Azure portal を使用して結果を確認するいくつかの例を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="7213f-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="7213f-118">また、開発用コンピューターに、Kubectl と Docker も備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="7213f-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="7213f-119">AKS クラスターを作成する</span><span class="sxs-lookup"><span data-stu-id="7213f-119">Create the AKS cluster</span></span>

<span data-ttu-id="7213f-120">次のコマンドを使用して、AKS クラスターを作成します。</span><span class="sxs-lookup"><span data-stu-id="7213f-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="7213f-121">作成ジョブが完了したら、Azure portal で作成した AKS を確認できます。</span><span class="sxs-lookup"><span data-stu-id="7213f-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="7213f-122">リソース グループ:</span><span class="sxs-lookup"><span data-stu-id="7213f-122">The resource group:</span></span>

![Azure AKS リソース グループのブラウザー ビュー。](media/aks-resource-group-view.png)

<span data-ttu-id="7213f-124">**図 4-17**.</span><span class="sxs-lookup"><span data-stu-id="7213f-124">**Figure 4-17**.</span></span> <span data-ttu-id="7213f-125">Azure からの AKS リソース グループ ビュー。</span><span class="sxs-lookup"><span data-stu-id="7213f-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="7213f-126">AKS クラスター:</span><span class="sxs-lookup"><span data-stu-id="7213f-126">The AKS cluster:</span></span>

![AKS リソース グループのブラウザー ビュー。](media/aks-cluster-view.png)

<span data-ttu-id="7213f-128">**図 4-18**.</span><span class="sxs-lookup"><span data-stu-id="7213f-128">**Figure 4-18**.</span></span> <span data-ttu-id="7213f-129">Azure からの AKS ビュー。</span><span class="sxs-lookup"><span data-stu-id="7213f-129">AKS view from Azure.</span></span>

<span data-ttu-id="7213f-130">`Azure-CLI` と `Kubectl` を使用して作成したノードを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="7213f-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="7213f-131">最初に、資格情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="7213f-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![上記のコマンドからのコンソール出力:root/.kube/config 内に "MsSampleK8Cluster" が現在のコンテキストとしてマージされました。](media/get-credentials-command-result.png)

<span data-ttu-id="7213f-133">**図 4-19**</span><span class="sxs-lookup"><span data-stu-id="7213f-133">**Figure 4-19**.</span></span> <span data-ttu-id="7213f-134">`aks get-credentials` コマンド結果。</span><span class="sxs-lookup"><span data-stu-id="7213f-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="7213f-135">次に、Kubectl からノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="7213f-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![上記のコマンドからのコンソール出力:状態、経過時間 (実行時間)、およびバージョンを含むノードの一覧](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="7213f-137">**図 4-20**</span><span class="sxs-lookup"><span data-stu-id="7213f-137">**Figure 4-20**.</span></span> <span data-ttu-id="7213f-138">`kubectl get nodes` コマンド結果。</span><span class="sxs-lookup"><span data-stu-id="7213f-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7213f-139">[前へ](orchestrate-high-scalability-availability.md)
>[次へ](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="7213f-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
