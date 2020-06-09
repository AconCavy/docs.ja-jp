---
title: ワークフロー サービスのホストの概要
ms.date: 03/30/2017
ms.assetid: 19f3704f-06bf-4eeb-8724-5224e02d7ead
ms.openlocfilehash: 10ea35fc1988e1b3e6ceb44aca098e63bfc7d7e4
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597294"
---
# <a name="hosting-workflow-services-overview"></a><span data-ttu-id="d3671-102">ワークフロー サービスのホストの概要</span><span class="sxs-lookup"><span data-stu-id="d3671-102">Hosting Workflow Services Overview</span></span>
<span data-ttu-id="d3671-103">ワークフロー サービスを実行するには、ホストされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3671-103">Workflow services must be hosted to execute.</span></span> <span data-ttu-id="d3671-104"><xref:System.ServiceModel.WorkflowServiceHost> は、複数のインスタンス、構成、および WCF メッセージングをサポートする標準ワークフロー ホストです (ワークフローはホストされるためにメッセージングを使用する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="d3671-104">The <xref:System.ServiceModel.WorkflowServiceHost> is the out-of-the-box workflow host that supports multiple instances, configuration, and WCF messaging (although the workflows aren’t required to use messaging in order to be hosted).</span></span>  <span data-ttu-id="d3671-105">また、一連のサービス動作を介して永続性、追跡、およびインスタンス コントロールを統合します。</span><span class="sxs-lookup"><span data-stu-id="d3671-105">It also integrates with persistence, tracking, and instance control through a set of service behaviors.</span></span>  <span data-ttu-id="d3671-106">WCF の <xref:System.ServiceModel.ServiceHost> と同様に、<xref:System.ServiceModel.WorkflowServiceHost> は任意のマネージド .NET アプリケーションでの自己ホスト、または IIS/WAS での Web ホスト (.xamlx ファイルとして) が可能です。</span><span class="sxs-lookup"><span data-stu-id="d3671-106">Just like WCF’s <xref:System.ServiceModel.ServiceHost>, the <xref:System.ServiceModel.WorkflowServiceHost> can be self-hosted in any managed .NET application, or web-hosted (as a .xamlx file) in IIS / WAS.</span></span>  <span data-ttu-id="d3671-107">このセクションのトピックでは、ワークフロー サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3671-107">Topics in this section describe how to host a workflow service.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3671-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d3671-108">In This Section</span></span>  
 [<span data-ttu-id="d3671-109">ワークフロー サービスのホスティング</span><span class="sxs-lookup"><span data-stu-id="d3671-109">Hosting Workflow Services</span></span>](hosting-workflow-services.md)  
 <span data-ttu-id="d3671-110">ワークフロー サービスのホスティングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d3671-110">Describes hosting workflow services.</span></span>  
  
 [<span data-ttu-id="d3671-111">ワークフロー サービス ホストの内部</span><span class="sxs-lookup"><span data-stu-id="d3671-111">Workflow Service Host Internals</span></span>](workflow-service-host-internals.md)  
 <span data-ttu-id="d3671-112"><xref:System.ServiceModel.WorkflowServiceHost> がどのように受信メッセージを処理するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d3671-112">Describes how <xref:System.ServiceModel.WorkflowServiceHost> processes incoming messages.</span></span>  
  
 [<span data-ttu-id="d3671-113">ワークフロー サービス ホストの拡張機能</span><span class="sxs-lookup"><span data-stu-id="d3671-113">Workflow Service Host Extensibility</span></span>](workflow-service-host-extensibility.md)  
 <span data-ttu-id="d3671-114">ワークフロー サービス ホストの機能を拡張する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3671-114">Describes how to extend the functionality of the workflow service host.</span></span>  
  
 [<span data-ttu-id="d3671-115">ワークフロー コントロール エンドポイント</span><span class="sxs-lookup"><span data-stu-id="d3671-115">Workflow Control Endpoint</span></span>](workflow-control-endpoint.md)  
 <span data-ttu-id="d3671-116">ワークフロー インスタンスを作成できるエンドポイントを定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3671-116">Describes how to define an endpoint that allows you to create workflow instances.</span></span>
  
 [<span data-ttu-id="d3671-117">方法: Windows Server AppFabric を使用してワークフロー サービスをホストする</span><span class="sxs-lookup"><span data-stu-id="d3671-117">How to: Host a Workflow Service with Windows Server App Fabric</span></span>](how-to-host-a-workflow-service-with-windows-server-app-fabric.md)  
 <span data-ttu-id="d3671-118">Windows Server AppFabric の既存のワークフロー サービスをホストする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d3671-118">Demonstrates how to host an existing workflow service in Windows Server App Fabric.</span></span>  
  
 [<span data-ttu-id="d3671-119">WorkflowServiceHost の構成</span><span class="sxs-lookup"><span data-stu-id="d3671-119">Configuring WorkflowServiceHost</span></span>](configuring-workflowservicehost.md)  
 <span data-ttu-id="d3671-120">永続性、追跡、アイドル状態、および未処理の例外動作を制御する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d3671-120">Describes how to control persistence, tracking, idle, and unhandled exception behavior.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d3671-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3671-121">Reference</span></span>  
 <xref:System.ServiceModel.Activities.WorkflowServiceHost>  
  
 <xref:System.ServiceModel.Activities.WorkflowService>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactory>  
  
 <xref:System.ServiceModel.Activation.ServiceHostFactoryBase>  
  
 <xref:System.ServiceModel.Activation.WorkflowServiceHostFactory>  
  
## <a name="related-sections"></a><span data-ttu-id="d3671-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="d3671-122">Related Sections</span></span>  
 [<span data-ttu-id="d3671-123">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="d3671-123">Workflow Services</span></span>](workflow-services.md)
