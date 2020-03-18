---
title: Docker アプリケーションの外側のループ DevOps ワークフローの手順
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "68673779"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="29dfc-103">コンテナーで.NET Core 2.0 アプリケーション用の Azure DevOps Services で CI/CD パイプラインを作成し、Kubernetes クラスターにデプロイする</span><span class="sxs-lookup"><span data-stu-id="29dfc-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="29dfc-104">図 5-12 では、コード管理、コードのコンパイル、Docker イメージ ビルド、Docker レジストリへの Docker イメージのプッシュ、および最終的な Azure での Kubernetes クラスターへのデプロイを含むエンドツーエンドの DevOps シナリオを参照できます。</span><span class="sxs-lookup"><span data-stu-id="29dfc-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![ワークフロー:開発用コンピューターで開始します。](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="29dfc-107">**図 5-12**</span><span class="sxs-lookup"><span data-stu-id="29dfc-107">**Figure 5-12**.</span></span> <span data-ttu-id="29dfc-108">Docker イメージを作成して、Azure で Kubernetes クラスターにデプロイする CI/CD シナリオ</span><span class="sxs-lookup"><span data-stu-id="29dfc-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="29dfc-109">ビルド/CI とリリース/CD の 2 つのパイプラインが Docker レジストリ (Docker Hub や Azure Container Registry など) によって、接続されていることを強調することが重要です。</span><span class="sxs-lookup"><span data-stu-id="29dfc-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="29dfc-110">Docker レジストリは、Docker を使用しない従来の CI/CD プロセスと比較して、主な相違点の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="29dfc-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="29dfc-111">図 5-13 に示すように、最初のフェーズは、ビルド/CI パイプラインです。</span><span class="sxs-lookup"><span data-stu-id="29dfc-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="29dfc-112">Azure DevOps Services では、コードをコンパイルし、Docker イメージを作成して、それらを Docker Hub や Azure Container Registry などの Docker レジストリにプッシュするビルド/CI パイプラインを作成できます。</span><span class="sxs-lookup"><span data-stu-id="29dfc-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Azure DevOps、ビルド プロセス タスク定義のブラウザー ビュー。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="29dfc-114">**図 5-13**</span><span class="sxs-lookup"><span data-stu-id="29dfc-114">**Figure 5-13**.</span></span> <span data-ttu-id="29dfc-115">Docker イメージをビルドし、Docker レジストリにイメージをプッシュする Azure DevOps のビルド/CI パイプライン</span><span class="sxs-lookup"><span data-stu-id="29dfc-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="29dfc-116">2 番目のフェーズは、デプロイ/リリース パイプラインの作成です。</span><span class="sxs-lookup"><span data-stu-id="29dfc-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="29dfc-117">Azure DevOps Services では、図 5-14 に示すように、Azure DevOps Services の Kubernetes タスクを使用して、Kubernetes クラスターを対象とするデプロイ パイプラインを簡単に作成できます。</span><span class="sxs-lookup"><span data-stu-id="29dfc-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Kubernetes へのデプロイ タスク定義を示す、Azure DevOps のブラウザー ビュー。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="29dfc-119">**図 5-14**</span><span class="sxs-lookup"><span data-stu-id="29dfc-119">**Figure 5-14**.</span></span> <span data-ttu-id="29dfc-120">Kubernetes クラスターにデプロイする Azure DevOps Services のリリース/CD パイプライン</span><span class="sxs-lookup"><span data-stu-id="29dfc-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [!Walkthrough]<span data-ttu-id="29dfc-121"> Kubernetes への eShopModernized のデプロイ:</span><span class="sxs-lookup"><span data-stu-id="29dfc-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="29dfc-122">Kubernetes にデプロイする Azure DevOps CI/CD パイプラインの詳細なチュートリアルについては、この投稿を参照してください。</span><span class="sxs-lookup"><span data-stu-id="29dfc-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="29dfc-123">[前へ](docker-application-outer-loop-devops-workflow.md)
>[次へ](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="29dfc-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
