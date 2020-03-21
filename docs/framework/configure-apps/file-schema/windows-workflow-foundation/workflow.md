---
title: <workflow>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 560aa9b6-9cf3-460e-b798-f87d14b1d2de
ms.openlocfilehash: e2df5d83375b2daa2e39ba1ee990c47a6a04f6fb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151859"
---
# <a name="workflow"></a><span data-ttu-id="58fa0-101">\<ワークフロー></span><span class="sxs-lookup"><span data-stu-id="58fa0-101">\<workflow></span></span>
<span data-ttu-id="58fa0-102"><xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。</span><span class="sxs-lookup"><span data-stu-id="58fa0-102">A configuration element that contains all queries for a specific workflow identified by the <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="58fa0-103">ワークフロー追跡とその構成の詳細については、「[ワークフロー追跡および追跡および追跡](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)[プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58fa0-103">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
<span data-ttu-id="58fa0-104">[**\<構成>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="58fa0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="58fa0-105">&nbsp;&nbsp;[**\<システム。サービスモデル>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="58fa0-105">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="58fa0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<追跡>**](tracking.md)</span><span class="sxs-lookup"><span data-stu-id="58fa0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<tracking>**](tracking.md)</span></span>\
<span data-ttu-id="58fa0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<追跡プロファイル>**](trackingprofile.md)</span><span class="sxs-lookup"><span data-stu-id="58fa0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<trackingProfile>**](trackingprofile.md)</span></span>\
<span data-ttu-id="58fa0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ワークフロー>**</span><span class="sxs-lookup"><span data-stu-id="58fa0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58fa0-109">構文</span><span class="sxs-lookup"><span data-stu-id="58fa0-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <tracking>
    <profiles>
      <participants>
        <add name="String"
             profileName="String"
             type="String" />
      </participants>
      <trackingProfile name="String">
        <workflow activityDefinitionId="String">
          <activityScheduledQueries>
            <activityScheduledQuery activityName="String"
                                    childActivityName="String"/>
          </activityScheduledQueries>
          <activityStateQueries>
            <activityStateQuery activityName="String" />
            <arguments>
              <argument name="String" />
            </arguments>
            <states>
              <state name="String"  />
            </states>
            <variables>
              <variable name="String" />
            </variables>
          </activityStateQueries>
          <bookmarkResumptionQueries>
            <bookmarkResumptionQuery name="String" />
          </bookmarkResumptionQueries>
          <cancelRequestQueries>
            <cancelRequestQuery activityName="String"
                                childActivityName="String"/>
          </cancelRequestQueries>
          <customTrackingQueries>
            <customTrackingQuery activityName="String"
                                 name="String"/>
          </customTrackingQueries>
          <faultPropagationQueries>
            <faultPropagationQuery activityName="String"
                                   faultHandlerActivityName="String" />
          </faultPropagationQueries>
          <workflowInstanceQueries>
            <workflowInstanceQuery>
              <states>
                <state name="String" />
              </states>
            </workflowInstanceQuery>
          </workflowInstanceQueries>
        </workflow>
      </trackingProfile>
    </profiles>
  </tracking>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58fa0-110">属性および要素</span><span class="sxs-lookup"><span data-stu-id="58fa0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="58fa0-111">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58fa0-112">属性</span><span class="sxs-lookup"><span data-stu-id="58fa0-112">Attributes</span></span>  
  
|<span data-ttu-id="58fa0-113">属性</span><span class="sxs-lookup"><span data-stu-id="58fa0-113">Attribute</span></span>|<span data-ttu-id="58fa0-114">説明</span><span class="sxs-lookup"><span data-stu-id="58fa0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58fa0-115">activityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="58fa0-115">activityDefinitionId</span></span>|<span data-ttu-id="58fa0-116">追跡対象のワークフローのアクティビティ定義 ID を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="58fa0-116">A string that specifies the activity definition ID of the workflow being tracked.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58fa0-117">子要素</span><span class="sxs-lookup"><span data-stu-id="58fa0-117">Child Elements</span></span>  
  
|<span data-ttu-id="58fa0-118">要素</span><span class="sxs-lookup"><span data-stu-id="58fa0-118">Element</span></span>|<span data-ttu-id="58fa0-119">説明</span><span class="sxs-lookup"><span data-stu-id="58fa0-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58fa0-120">\<アクティビティスケジュールされたクエリ></span><span class="sxs-lookup"><span data-stu-id="58fa0-120">\<activityScheduledQueries></span></span>](activityscheduledqueries.md)|<span data-ttu-id="58fa0-121">親アクティビティによる実行がスケジュールされているアクティビティを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-121">Represents a collection of queries that are used to track an activity scheduled for execution by a parent activity.</span></span> <span data-ttu-id="58fa0-122">アクティビティがスケジュールされたレコードを追跡参加要素が定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="58fa0-122">The query is necessary for a tracking participant to subscribe to activity scheduled records.</span></span>|  
|[<span data-ttu-id="58fa0-123">\<アクティビティステートクエリ></span><span class="sxs-lookup"><span data-stu-id="58fa0-123">\<activityStateQueries></span></span>](activitystatequeries.md)|<span data-ttu-id="58fa0-124">ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-124">Represents a collection of queries that are used to track life cycle changes of the activities that make up a workflow instance.</span></span> <span data-ttu-id="58fa0-125">たとえば、ワークフロー インスタンス内で "電子メールの送信" アクティビティが完了するたびに追跡できます。</span><span class="sxs-lookup"><span data-stu-id="58fa0-125">For example, you may want to keep track of every time the "Send E-Mail" activity completes within a workflow instance.</span></span> <span data-ttu-id="58fa0-126">追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="58fa0-126">This query is necessary for a tracking participant to subscribe to activity state record objects.</span></span> <span data-ttu-id="58fa0-127">定期受信可能な状態は ActivityStates で指定します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-127">The available states to subscribe to are specified in ActivityStates.</span></span>|  
|[<span data-ttu-id="58fa0-128">\<ブックマーククエリ></span><span class="sxs-lookup"><span data-stu-id="58fa0-128">\<bookmarkResumptionQueries></span></span>](bookmarkresumptionqueries.md)|<span data-ttu-id="58fa0-129">ワークフロー インスタンス内のブックマークの再開を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-129">Represents a collection of queries that are used to track resumption of a bookmark within a workflow instance.</span></span> <span data-ttu-id="58fa0-130">追跡参加要素がブックマーク再開レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="58fa0-130">The query is necessary for a tracking participant to subscribe to bookmark resumption records.</span></span>|  
|[<span data-ttu-id="58fa0-131">\<>要求されたクエリをキャンセルします。</span><span class="sxs-lookup"><span data-stu-id="58fa0-131">\<cancelRequestedQueries></span></span>](cancelrequestedqueries.md)|<span data-ttu-id="58fa0-132">親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-132">Represents a collection of queries that are used to track requests to cancel a child activity by the parent activity.</span></span> <span data-ttu-id="58fa0-133">追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="58fa0-133">The query is necessary for a tracking participant to subscribe to cancel request record objects.</span></span>|  
|[<span data-ttu-id="58fa0-134">\<>を照会する</span><span class="sxs-lookup"><span data-stu-id="58fa0-134">\<customTrackingQueries></span></span>](customtrackingqueries.md)|<span data-ttu-id="58fa0-135">コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-135">Represents a collection of queries that are used to track events that you define in your code activities.</span></span> <span data-ttu-id="58fa0-136">追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="58fa0-136">The query is necessary for a tracking participant to subscribe to custom tracking records.</span></span>|  
|[<span data-ttu-id="58fa0-137">\<>クエリー</span><span class="sxs-lookup"><span data-stu-id="58fa0-137">\<faultPropagationQueries></span></span>](faultpropagationqueries.md)|<span data-ttu-id="58fa0-138">1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、クエリのコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-138">Represents a collection of queries that are used to track the handling of faults that occur within an activity.</span></span>  <span data-ttu-id="58fa0-139">このイベントは、FaultHandler がエラーを処理するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-139">This event occurs each time a FaultHandler processes a fault.</span></span> <span data-ttu-id="58fa0-140">1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。</span><span class="sxs-lookup"><span data-stu-id="58fa0-140">You should use such query to track the handling of faults that occur within an activity.</span></span> <span data-ttu-id="58fa0-141">追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。</span><span class="sxs-lookup"><span data-stu-id="58fa0-141">The query is necessary for a  tracking participant to subscribe to fault propagation records.</span></span>|  
|[<span data-ttu-id="58fa0-142">\<></span><span class="sxs-lookup"><span data-stu-id="58fa0-142">\<workflowInstanceQueries></span></span>](workflowinstancequeries.md)|<span data-ttu-id="58fa0-143">開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡する構成要素のコレクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-143">Represents a collection of configuration elements that track workflow instance life cycle changes such as a started or completed event.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58fa0-144">親要素</span><span class="sxs-lookup"><span data-stu-id="58fa0-144">Parent Elements</span></span>  
  
|<span data-ttu-id="58fa0-145">要素</span><span class="sxs-lookup"><span data-stu-id="58fa0-145">Element</span></span>|<span data-ttu-id="58fa0-146">説明</span><span class="sxs-lookup"><span data-stu-id="58fa0-146">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58fa0-147">\<追跡プロファイル></span><span class="sxs-lookup"><span data-stu-id="58fa0-147">\<trackingProfile></span></span>](trackingprofile.md)|<span data-ttu-id="58fa0-148">追跡参加要素内でワークフロー追跡レコードのサブスクリプションを作成するための、構成セクションを表します。</span><span class="sxs-lookup"><span data-stu-id="58fa0-148">Represents a configuration section for creating a subscription to workflow tracking records in a tracking participant.</span></span> <span data-ttu-id="58fa0-149">追跡プロファイルには、実行時にワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58fa0-149">A tracking profile contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a workflow instance changes at runtime.</span></span> <span data-ttu-id="58fa0-150">追跡プロファイル セクション内で定義されたクエリでは、サブスクリプションによって返されるイベントの種類が定義されます。</span><span class="sxs-lookup"><span data-stu-id="58fa0-150">The queries defined within the tracking profile section define the kinds of events that are returned by the subscription.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58fa0-151">解説</span><span class="sxs-lookup"><span data-stu-id="58fa0-151">Remarks</span></span>  
 <span data-ttu-id="58fa0-152">追跡プロファイルには、実行時に特定のワークフロー インスタンスの状態が変化したときに生成されるワークフロー イベントを追跡参加要素が定期受信できるようにする、追跡クエリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="58fa0-152">Tracking profiles contains tracking queries that permit a tracking participant to subscribe to workflow events that are emitted when the state of a particular workflow instance changes at runtime.</span></span> <span data-ttu-id="58fa0-153">この構成要素を使用して、追跡対象のワークフロー インスタンスが識別されます。</span><span class="sxs-lookup"><span data-stu-id="58fa0-153">The workflow instance being tracked is identified by this configuration element.</span></span>  
  
 <span data-ttu-id="58fa0-154">監視の要件に応じて、ワークフローの主な状態変化の少数のセットを定期受信する、大まかなプロファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="58fa0-154">Depending on your monitoring requirements you may write a profile that is very coarse, which subscribes to a small set of high-level state changes on a workflow.</span></span> <span data-ttu-id="58fa0-155">それとは反対に、結果として得られるイベントが、後で詳細な実行フローを十分に再構築できるほど豊富な、詳細なプロファイルを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="58fa0-155">Conversely, you may create a very specific profile whose resulting events are rich enough to reconstruct a detailed execution flow later.</span></span>  
  
 <span data-ttu-id="58fa0-156">追跡プロファイルは、特定の追跡レコードを対象としてワークフロー ランタイムを照会できる、追跡レコード用の宣言型のサブスクリプションとして構築されます。</span><span class="sxs-lookup"><span data-stu-id="58fa0-156">Tracking profiles are structured as declarative subscriptions for tracking records that allow you to query the workflow runtime for specific tracking records.</span></span> <span data-ttu-id="58fa0-157">クエリには複数の型があり、これらを使用して、追跡レコードのさまざまなクラスを定期受信できます。</span><span class="sxs-lookup"><span data-stu-id="58fa0-157">There are a handful of query types that allow you subscribe to different classes of tracking records.</span></span> <span data-ttu-id="58fa0-158">クエリの完全な一覧については、このトピックの子要素の一覧と[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58fa0-158">For a complete list of queries, see the child element list of this topic and [Tracking Profiles](../../../windows-workflow-foundation/tracking-profiles.md).</span></span>  
  
 <span data-ttu-id="58fa0-159">次の例は、追跡参加要素が`Started``Completed`および ワークフロー イベントをサブスクライブできるようにする構成ファイル内の追跡プロファイルを示しています。</span><span class="sxs-lookup"><span data-stu-id="58fa0-159">The following example shows a tracking profile in a configuration file that allows a tracking participant to subscribe to the `Started` and `Completed` workflow events.</span></span>  
  
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
   </profiles>  
  </tracking>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58fa0-160">関連項目</span><span class="sxs-lookup"><span data-stu-id="58fa0-160">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [<span data-ttu-id="58fa0-161">ワークフローの追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="58fa0-161">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="58fa0-162">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="58fa0-162">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
