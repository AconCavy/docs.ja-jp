---
title: 高いスケーラビリティと可用性のためにマイクロサービスと複数のコンテナー アプリケーションを調整する
description: Azure Kubernetes Service を使用して、アプリケーションをデプロイする方法について説明します。
ms.date: 08/06/2020
ms.openlocfilehash: b4deb9906e0fece7fb611b6988df576e8b07fe46
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916112"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="e35fd-103">Azure Kubernetes Service (AKS) へのデプロイ</span><span class="sxs-lookup"><span data-stu-id="e35fd-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="e35fd-104">Azure コマンドライン インターフェイス (Azure CLI) がインストールされている任意のクライアント オペレーティング システム (Windows、macOS、または Linux) を使用して、AKS と対話することができます。</span><span class="sxs-lookup"><span data-stu-id="e35fd-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="e35fd-105">詳細については、使用可能な環境に関する [Azure CLI ドキュメント](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest)と[インストール ガイド](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e35fd-105">For more details, refer [Azure CLI documentation](https://docs.microsoft.com/cli/azure/?view=azure-cli-latest) and [Installation guide](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="e35fd-106">Azure で AKS 環境を作成する</span><span class="sxs-lookup"><span data-stu-id="e35fd-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="e35fd-107">AKS 環境を作成するにはいくつかの方法があります。</span><span class="sxs-lookup"><span data-stu-id="e35fd-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="e35fd-108">これを行うには、Azure CLI コマンドを使用するか、または Azure portal を使用します。</span><span class="sxs-lookup"><span data-stu-id="e35fd-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="e35fd-109">ここでは、クラスターを作成するための Azure CLI、および結果を確認するための Azure portal を使用して、例をいくつか調べることができます。</span><span class="sxs-lookup"><span data-stu-id="e35fd-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="e35fd-110">また、開発用コンピューターに、Kubectl と Docker も備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e35fd-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="e35fd-111">AKS クラスターを作成する</span><span class="sxs-lookup"><span data-stu-id="e35fd-111">Create the AKS cluster</span></span>

<span data-ttu-id="e35fd-112">次のコマンドを使用して、AKS クラスターを作成します (リソース グループが存在している必要があります)。</span><span class="sxs-lookup"><span data-stu-id="e35fd-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="e35fd-113">`--node-vm-size` パラメーターと `--node-count` パラメーターの値は、サンプルまたは開発アプリケーションに適しています。</span><span class="sxs-lookup"><span data-stu-id="e35fd-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="e35fd-114">作成ジョブが完了したら、次のことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="e35fd-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="e35fd-115">最初のリソース グループに作成された AKS クラスター。</span><span class="sxs-lookup"><span data-stu-id="e35fd-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="e35fd-116">次の図に示すような、AKS クラスターに関連するリソースが含まれる関連する新しいリソース グループ。</span><span class="sxs-lookup"><span data-stu-id="e35fd-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="e35fd-117">AKS クラスターが含まれる最初のリソース グループは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e35fd-117">The initial resource group, with the AKS cluster:</span></span>

![AKS リソース グループのブラウザー ビュー。](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="e35fd-119">**図 4-17**. </span><span class="sxs-lookup"><span data-stu-id="e35fd-119">**Figure 4-17**.</span></span> <span data-ttu-id="e35fd-120">Azure からの AKS リソース グループ ビュー。</span><span class="sxs-lookup"><span data-stu-id="e35fd-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="e35fd-121">AKS クラスター リソース グループは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="e35fd-121">The AKS cluster resource group:</span></span>

![Azure AKS リソース グループのブラウザー ビュー。](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="e35fd-123">**図 4-18**.</span><span class="sxs-lookup"><span data-stu-id="e35fd-123">**Figure 4-18**.</span></span> <span data-ttu-id="e35fd-124">Azure からの AKS ビュー。</span><span class="sxs-lookup"><span data-stu-id="e35fd-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e35fd-125">一般に、AKS クラスター リソース グループ内のリソースを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e35fd-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="e35fd-126">たとえば、AKS クラスターを削除すると、リソース グループが削除されます。</span><span class="sxs-lookup"><span data-stu-id="e35fd-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="e35fd-127">`Azure CLI` と `Kubectl` を使用して作成したノードを表示することもできます。</span><span class="sxs-lookup"><span data-stu-id="e35fd-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="e35fd-128">最初に、資格情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="e35fd-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![上記のコマンドからのコンソール出力:/home/miguel/.kube/config の現在のコンテキストとしてマージされた "explore-docker-aks"。](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="e35fd-130">**図 4-19**</span><span class="sxs-lookup"><span data-stu-id="e35fd-130">**Figure 4-19**.</span></span> <span data-ttu-id="e35fd-131">`aks get-credentials` コマンド結果。</span><span class="sxs-lookup"><span data-stu-id="e35fd-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="e35fd-132">次に、Kubectl からノードを取得します。</span><span class="sxs-lookup"><span data-stu-id="e35fd-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![上記のコマンドからのコンソール出力:状態、経過時間 (実行時間)、およびバージョンを含むノードの一覧](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="e35fd-134">**図 4-20**</span><span class="sxs-lookup"><span data-stu-id="e35fd-134">**Figure 4-20**.</span></span> <span data-ttu-id="e35fd-135">`kubectl get nodes` コマンド結果。</span><span class="sxs-lookup"><span data-stu-id="e35fd-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="e35fd-136">[前へ](orchestrate-high-scalability-availability.md)
> [次へ](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="e35fd-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
