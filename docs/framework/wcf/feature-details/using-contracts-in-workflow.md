---
title: ワークフロー内でのコントラクトの使用
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184274"
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="982e1-102">ワークフロー内でのコントラクトの使用</span><span class="sxs-lookup"><span data-stu-id="982e1-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="982e1-103">サービスを実装するときは、サービスおよびサービスが送受信するデータを説明する一連のコントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="982e1-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="982e1-104">データはデータ コントラクトとメッセージ コントラクトとして表されます。WCF とワークフロー の両方のサービスは、サービスの説明の一部としてデータ コントラクトとメッセージ コントラクトの定義を使用します。</span><span class="sxs-lookup"><span data-stu-id="982e1-104">The data is represented as data contracts and message contracts; both WCF and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="982e1-105">サービス自体は、(WSDL の形で) メタデータを公開して、サービスの操作を説明します。</span><span class="sxs-lookup"><span data-stu-id="982e1-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="982e1-106">WCF では、サービス コントラクトと操作コントラクトによって、サービス、およびサービスがサポートする操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="982e1-106">In WCF, service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="982e1-107">ただし、ワークフロー サービスでは、これらのコントラクトはビジネス プロセス自体の一部になり、コントラクト推論と呼ばれるプロセスによってメタデータとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="982e1-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="982e1-108">コントラクト推論</span><span class="sxs-lookup"><span data-stu-id="982e1-108">Contract Inference</span></span>  
 <span data-ttu-id="982e1-109">ワークフロー サービスが <xref:System.ServiceModel.Activities.WorkflowServiceHost> を使用してホストされている場合は、ワークフローで見つかった一連のメッセージ アクティビティに基づいて、ワークフロー定義が確認され、コントラクトが生成されます。</span><span class="sxs-lookup"><span data-stu-id="982e1-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="982e1-110">具体的には、次のアクティビティとプロパティが、コントラクトの生成に使用されます。</span><span class="sxs-lookup"><span data-stu-id="982e1-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="982e1-111"><xref:System.ServiceModel.Activities.Receive> の利用状況</span><span class="sxs-lookup"><span data-stu-id="982e1-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <span data-ttu-id="982e1-112"><xref:System.ServiceModel.Activities.SendReply> の利用状況</span><span class="sxs-lookup"><span data-stu-id="982e1-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="982e1-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> の利用状況</span><span class="sxs-lookup"><span data-stu-id="982e1-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="982e1-114">コントラクト推論の結果は、WCF サービスと操作コントラクトと同じデータ構造を使用するサービスの説明になります。</span><span class="sxs-lookup"><span data-stu-id="982e1-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="982e1-115">この情報を使用して、ワークフロー サービス用に WSDL が公開されます。</span><span class="sxs-lookup"><span data-stu-id="982e1-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982e1-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="982e1-116">See also</span></span>

- [<span data-ttu-id="982e1-117">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="982e1-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="982e1-118">メッセージング アクティビティ</span><span class="sxs-lookup"><span data-stu-id="982e1-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [<span data-ttu-id="982e1-119">方法: メッセージング アクティビティを使用してワークフロー サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="982e1-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [<span data-ttu-id="982e1-120">既存のサービス コントラクトを使用するワークフロー サービスを作成する方法</span><span class="sxs-lookup"><span data-stu-id="982e1-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
