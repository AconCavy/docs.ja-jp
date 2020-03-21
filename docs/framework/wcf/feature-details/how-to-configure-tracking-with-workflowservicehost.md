---
title: '方法: WorkflowServiceHost を使用して追跡を構成する'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 962dfda9fc5780cc3ac7211464bb3a9be8b7fa90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185070"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="80ad1-102">方法: WorkflowServiceHost を使用して追跡を構成する</span><span class="sxs-lookup"><span data-stu-id="80ad1-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="80ad1-103">このトピックでは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] でホストされている <xref:System.ServiceModel.Activities.WorkflowServiceHost> ワークフロー サービスの追跡を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="80ad1-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="80ad1-104">これは、Web.config ファイルにサービスの動作を指定することによって指定します。</span><span class="sxs-lookup"><span data-stu-id="80ad1-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="80ad1-105">構成での追跡の構成</span><span class="sxs-lookup"><span data-stu-id="80ad1-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="80ad1-106">次の<xref:System.Activities.Tracking.EtwTrackingParticipant>例に示`behavior`すように、構成ファイルに <>要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="80ad1-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    <behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="80ad1-107">前の構成サンプルでは、簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="80ad1-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="80ad1-108">詳細については、「[簡略化された構成](../../../../docs/framework/wcf/simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80ad1-108">For more information, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="80ad1-109">前の構成サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="80ad1-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="80ad1-110">追跡プロファイルは、<>`trackingProfile``tracking`要素内の<>要素内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="80ad1-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="80ad1-111">追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="80ad1-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="80ad1-112">追跡プロファイルを作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="80ad1-112">The following example shows how to create a tracking profile.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <tracking>
         <trackingProfile name="Sample Tracking Profile">  
            <workflow activityDefinitionId="*">  
               <workflowInstanceQueries>  
                 <workflowInstanceQuery>  
                    <states>  
                       <state name="Started"/>  
                       <state name="Completed"/>  
                    </states>  
                </workflowInstanceQuery>  
             </workflowInstanceQueries>  
           </workflow>  
         </trackingProfile>
       </tracking>  
    </system.serviceModel>  
    ```  
  
     <span data-ttu-id="80ad1-113">追跡プロファイルの詳細については、「[追跡](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)プロファイル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80ad1-113">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="80ad1-114">追跡全般の詳細については、「[ワークフローの追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80ad1-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="80ad1-115">コードでの追跡の構成</span><span class="sxs-lookup"><span data-stu-id="80ad1-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="80ad1-116">次の例に示すように、コードで <xref:System.Activities.Tracking.EtwTrackingParticipant> を動作を使用して <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> を追加します。</span><span class="sxs-lookup"><span data-stu-id="80ad1-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="80ad1-117">前のコード サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="80ad1-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="80ad1-118">追跡プロファイルは、前のセクション`trackingProfile`で示したように、<>`tracking`要素内の<>要素内に作成されます。</span><span class="sxs-lookup"><span data-stu-id="80ad1-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="80ad1-119">追跡プロファイルの詳細については、「[追跡](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)プロファイル」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80ad1-119">For more information about tracking profiles, see [Tracking Profiles](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="80ad1-120">追跡全般の詳細については、「[ワークフローの追跡とトレース](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80ad1-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="80ad1-121">プログラムで追跡を構成する例については、「[ワークフローの追跡の構成](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80ad1-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../../../docs/framework/windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ad1-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="80ad1-122">See also</span></span>

- [<span data-ttu-id="80ad1-123">WCF サービスの簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="80ad1-123">Simplified Configuration for WCF Services</span></span>](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="80ad1-124">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="80ad1-124">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="80ad1-125">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="80ad1-125">Tracking Profiles</span></span>](../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
