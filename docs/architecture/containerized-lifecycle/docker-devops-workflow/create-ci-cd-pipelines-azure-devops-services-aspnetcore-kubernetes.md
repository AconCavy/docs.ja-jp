---
title: コンテナーで .NET アプリケーション用の Azure DevOps Services で CI/CD パイプラインを作成し、Kubernetes クラスターにデプロイする
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
ms.date: 01/06/2021
ms.openlocfilehash: ef994f132716547ee402237016ee71013528d779
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970487"
---
# <a name="create-cicd-pipelines-in-azure-devops-services-for-a-net-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>コンテナーで .NET アプリケーション用の Azure DevOps Services で CI/CD パイプラインを作成し、Kubernetes クラスターにデプロイする

図 5-12 では、コード管理、コードのコンパイル、Docker イメージ ビルド、Docker レジストリへの Docker イメージのプッシュ、および最終的な Azure での Kubernetes クラスターへのデプロイを含むエンドツーエンドの DevOps シナリオを参照できます。

![ワークフロー:開発用コンピューターで開始します。 リポジトリへのプッシュにより、カスタム イメージを使用したビルド/CI タスクが開始され、カスタム イメージは Docker レジストリにプッシュされ、その後 CD/デプロイ タスクで使用され、最終的に AKS にプッシュされます。](media/docker-workflow-ci-cd-aks.png)

**図 5-12** Docker イメージを作成して、Azure で Kubernetes クラスターにデプロイする CI/CD シナリオ

ビルド/CI とリリース/CD の 2 つのパイプラインが Docker レジストリ (Docker Hub や Azure Container Registry など) によって、接続されていることを強調することが重要です。 Docker レジストリは、Docker を使用しない従来の CI/CD プロセスと比較して、主な相違点の 1 つです。

図 5-13 に示すように、最初のフェーズは、ビルド/CI パイプラインです。 Azure DevOps Services では、コードをコンパイルし、Docker イメージを作成して、それらを Docker Hub や Azure Container Registry などの Docker レジストリにプッシュするビルド/CI パイプラインを作成できます。

![Azure DevOps、ビルド プロセス タスク定義のブラウザー ビュー。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**図 5-13** Docker イメージをビルドし、Docker レジストリにイメージをプッシュする Azure DevOps のビルド/CI パイプライン

2 番目のフェーズは、デプロイ/リリース パイプラインの作成です。 Azure DevOps Services では、図 5-14 に示すように、Azure DevOps Services の Kubernetes タスクを使用して、Kubernetes クラスターを対象とするデプロイ パイプラインを簡単に作成できます。

![Kubernetes へのデプロイ タスク定義を示す、Azure DevOps のブラウザー ビュー。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**図 5-14** Kubernetes クラスターにデプロイする Azure DevOps Services のリリース/CD パイプライン

> [!Walkthrough] Kubernetes への eShopModernized のデプロイ:
>
> Kubernetes にデプロイする Azure DevOps CI/CD パイプラインの詳細なチュートリアルについては、この投稿を参照してください。\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[前へ](docker-application-outer-loop-devops-workflow.md)
>[次へ](../run-manage-monitor-docker-environments/index.md)
