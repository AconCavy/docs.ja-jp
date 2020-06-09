---
title: '方法: WorkflowServiceHost を使用して追跡を構成する'
ms.date: 03/30/2017
ms.assetid: ed1485fe-7529-4351-bca3-8bb915260b17
ms.openlocfilehash: 54594a8f464e77062c658606db6bc941e319f71d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599101"
---
# <a name="how-to-configure-tracking-with-workflowservicehost"></a><span data-ttu-id="3ed26-102">方法: WorkflowServiceHost を使用して追跡を構成する</span><span class="sxs-lookup"><span data-stu-id="3ed26-102">How to: Configure Tracking with WorkflowServiceHost</span></span>
<span data-ttu-id="3ed26-103">このトピックでは、[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] でホストされている <xref:System.ServiceModel.Activities.WorkflowServiceHost> ワークフロー サービスの追跡を構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3ed26-103">This topic explains how to configure tracking for a [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="3ed26-104">これは、Web.config ファイルにサービスの動作を指定することによって指定します。</span><span class="sxs-lookup"><span data-stu-id="3ed26-104">It is configured through a Web.config file by specifying a service behavior.</span></span>  
  
### <a name="configure-tracking-in-configuration"></a><span data-ttu-id="3ed26-105">構成での追跡の構成</span><span class="sxs-lookup"><span data-stu-id="3ed26-105">Configure Tracking in Configuration</span></span>  
  
1. <span data-ttu-id="3ed26-106">次の <xref:System.Activities.Tracking.EtwTrackingParticipant> `behavior` 例に示すように、構成ファイルに <> 要素を使用してを追加します。</span><span class="sxs-lookup"><span data-stu-id="3ed26-106">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <`behavior`> element in a configuration file, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
         <behavior>  
           <etwTracking profileName="Sample Tracking Profile" />  
         </behavior>
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="3ed26-107">前の構成サンプルでは、簡略化された構成を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3ed26-107">The preceding configuration sample is using simplified configuration.</span></span> <span data-ttu-id="3ed26-108">詳細については、「簡略化された[構成](../simplified-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ed26-108">For more information, see [Simplified Configuration](../simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="3ed26-109">前の構成サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ed26-109">The preceding configuration sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="3ed26-110">追跡プロファイルは `trackingProfile` <> 要素内の <> 要素に作成され `tracking` ます。</span><span class="sxs-lookup"><span data-stu-id="3ed26-110">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element.</span></span> <span data-ttu-id="3ed26-111">追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="3ed26-111">The tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="3ed26-112">追跡プロファイルを作成する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="3ed26-112">The following example shows how to create a tracking profile.</span></span>  
  
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
  
     <span data-ttu-id="3ed26-113">追跡プロファイルの詳細については、「[追跡プロファイル](../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ed26-113">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="3ed26-114">一般的な追跡の詳細については、「[ワークフローの追跡とトレース](../../windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ed26-114">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
### <a name="configure-tracking-in-code"></a><span data-ttu-id="3ed26-115">コードでの追跡の構成</span><span class="sxs-lookup"><span data-stu-id="3ed26-115">Configure Tracking in Code</span></span>  
  
1. <span data-ttu-id="3ed26-116">次の例に示すように、コードで <xref:System.Activities.Tracking.EtwTrackingParticipant> を動作を使用して <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> を追加します。</span><span class="sxs-lookup"><span data-stu-id="3ed26-116">Add the <xref:System.Activities.Tracking.EtwTrackingParticipant> using the <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior> behavior in code, as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new EtwTrackingBehavior { ProfileName = "Sample Tracking Profile" });  
    ```  
  
     <span data-ttu-id="3ed26-117">前のコード サンプルでは、<xref:System.Activities.Tracking.EtwTrackingParticipant> を追加し、追跡プロファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="3ed26-117">The preceding code sample adds a <xref:System.Activities.Tracking.EtwTrackingParticipant> and specifies a tracking profile name.</span></span> <span data-ttu-id="3ed26-118">追跡プロファイルは、 `trackingProfile` `tracking` 前のセクションで示したように、<> 要素内の <> 要素に作成されます。</span><span class="sxs-lookup"><span data-stu-id="3ed26-118">Tracking profiles are created in a <`trackingProfile`> element within a <`tracking`> element as shown in the previous section.</span></span>  
  
     <span data-ttu-id="3ed26-119">追跡プロファイルの詳細については、「[追跡プロファイル](../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ed26-119">For more information about tracking profiles, see [Tracking Profiles](../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
     <span data-ttu-id="3ed26-120">一般的な追跡の詳細については、「[ワークフローの追跡とトレース](../../windows-workflow-foundation/workflow-tracking-and-tracing.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ed26-120">For more information about tracking in general, see [Workflow Tracking and Tracing](../../windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span> <span data-ttu-id="3ed26-121">プログラムによって追跡を構成する例については[、「ワークフローの追跡の構成](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3ed26-121">For an example of configuring tracking programmatically see [Configuring Tracking for a Workflow](../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ed26-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="3ed26-122">See also</span></span>

- [<span data-ttu-id="3ed26-123">WCF サービスの簡略化された構成</span><span class="sxs-lookup"><span data-stu-id="3ed26-123">Simplified Configuration for WCF Services</span></span>](../samples/simplified-configuration-for-wcf-services.md)
- [<span data-ttu-id="3ed26-124">ワークフロー サービス</span><span class="sxs-lookup"><span data-stu-id="3ed26-124">Workflow Services</span></span>](workflow-services.md)
- [<span data-ttu-id="3ed26-125">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="3ed26-125">Tracking Profiles</span></span>](../../windows-workflow-foundation/tracking-profiles.md)
