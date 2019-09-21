---
title: クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |クラウドで CI/CD パイプラインと DevOps ツールを使用してアプリのライフサイクルを最新化する
ms.date: 04/30/2018
ms.openlocfilehash: 62b6c541780ed3bf82c55e576fa485f811b55b17
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374140"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>クラウドの CI/CD パイプラインや DevOps ツールでアプリのライフ サイクルを最新化する

今日の企業は、市場で競争力を高めるために、迅速にイノベーションを行う必要があります。 高品質で最新のアプリケーションを提供するには、このような革新的なイノベーションサイクルを実装するうえで不可欠な DevOps ツールとプロセスが必要です。 適切な DevOps ツールを使用すると、開発者は継続的なデプロイを効率化し、革新的なアプリケーションをより迅速にユーザーに渡すことができます。

継続的な統合とデプロイの方法は適切に確立されていますが、コンテナーの導入には、特に複数コンテナーアプリケーションを使用している場合に、新しい考慮事項が導入されています。

Azure DevOps Services は、公式の Azure DevOps Services 展開タスクを使用して、さまざまな環境への複数コンテナーアプリケーションの継続的インテグレーションと継続的なデプロイをサポートしています。

- [Azure Web App for Containers へのデプロイ](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [Azure Container Service へのデプロイ– Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

ただし、Azure DevOps Services スクリプトベースのタスクを使用して、 [Docker の群れ](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/)や DC/OS にデプロイすることもできます。

デプロイの機敏性を維持するために、これらのツールは、開発および CI/CD ソリューションを選択して、コンテナーのワークロードに対して優れた開発からテスト環境へのデプロイエクスペリエンスを提供します。

図4-12 は、Azure Container Service で Kubernetes クラスターにデプロイする継続的なデプロイパイプラインを示しています。

![Kubernetes クラスターにデプロイする継続的デプロイパイプラインの Azure DevOps Services](./media/image12.png)

**図 4-12.** Kubernetes クラスターにデプロイする継続的デプロイパイプラインの Azure DevOps Services

>[!div class="step-by-step"]
>[前へ](modernize-your-apps-with-monitoring-and-telemetry.md)
>[次へ](migrate-to-hybrid-cloud-scenarios.md)
