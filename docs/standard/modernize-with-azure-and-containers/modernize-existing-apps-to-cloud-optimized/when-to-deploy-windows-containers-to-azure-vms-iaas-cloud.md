---
title: Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング
ms.date: 04/28/2018
ms.openlocfilehash: e9a2903662306b607977a7751018e24161ab80ab
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638994"
---
# <a name="when-to-deploy-windows-containers-to-azure-vms-iaas-cloud"></a>Azure Vm (IaaS クラウド) に Windows コンテナーを展開するタイミング

Windows コンテナーを使用する場合でも、組織は、Azure Vm を使用して、IaaS の取り扱いをまだしています。 負荷分散のインフラストラクチャで複数の Vm にデプロイする必要があるときに拡張性の高いアプリケーションのインフラストラクチャの操作、VM の OS 修正プログラム、およびインフラストラクチャの複雑さを処理するを意味します。 Azure VM で Windows コンテナーを使用する主なシナリオは次のとおりです。

- **開発/テスト環境**:クラウド内の VM では、開発とテストをクラウドに最適です。 迅速に作成または、環境のニーズに応じて停止できます。

- **小規模および中規模のスケーラビリティが必要な**:必要になるいくつかの Vm を運用環境のシナリオで Vm の数が少ないを管理する場合があります手頃な価格までオーケストレーターなどのより高度な PaaS 環境に移動することができます。

- **既存の展開ツールを使用して実稼働環境**:これには、Vm またはベア メタル サーバー (Puppet のようなツールなど) に複雑なデプロイを行うためのツールに投資して、オンプレミス環境から移動する可能性があります。 運用環境の展開手順の最小限の変更で、クラウドに移動するには、これらのツールを使用して Azure Vm にデプロイする続ける可能性があります。 ただし、配置の 1 単位として展開エクスペリエンスを向上させるために Windows コンテナーを使用するがします。

>[!div class="step-by-step"]
>[前へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
>[次へ](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
