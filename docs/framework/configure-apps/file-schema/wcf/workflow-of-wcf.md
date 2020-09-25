---
title: <workflow> WCF の
ms.date: 03/30/2017
ms.assetid: c0443eba-d3b4-4fae-886e-9878daf77691
ms.openlocfilehash: cada3fca028562312be0272cb2a6021dfd1cf9cb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194883"
---
# <a name="workflow-of-wcf"></a><span data-ttu-id="2a3ba-102">\<workflow> WCF の</span><span class="sxs-lookup"><span data-stu-id="2a3ba-102">\<workflow> of WCF</span></span>

<span data-ttu-id="2a3ba-103">ランタイムから直接出力される追跡レコードをリッスンし、追跡レコードの構成方法に従って処理を行う追跡参加要素を構成します。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-103">Configure a tracking participant that listens to the tracking records being emitted from the runtime directly and process them in whatever way it was configured.</span></span> <span data-ttu-id="2a3ba-104">これには、特定の出力 (ファイル、コンソール、ETW など) への書き込み、レコードの処理や集計、またはその他の必要な組み合わせが含まれます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-104">This includes writing to a specific output (e.g., file, Console, ETW), processing/aggregating the records, or any other combination that might be required.</span></span>  
  
 <span data-ttu-id="2a3ba-105">ワークフロー追跡と追跡参加要素の詳細については、「 [ワークフローの追跡とトレース](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 」と「 [追跡参加要素](../../../windows-workflow-foundation/tracking-participants.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-105">For more information in workflow tracking and tracking participants, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Tracking Participants](../../../windows-workflow-foundation/tracking-participants.md).</span></span>  
  
 \<system.serviceModel>  
\<tracking>  
\<participants>  
\<add>  
  
## <a name="syntax"></a><span data-ttu-id="2a3ba-106">構文</span><span class="sxs-lookup"><span data-stu-id="2a3ba-106">Syntax</span></span>  
  
```xml  
<tracking>
  <participants>
    <add name="String"
         profileName="String"
         type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a3ba-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="2a3ba-107">Attributes and Elements</span></span>  

 <span data-ttu-id="2a3ba-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a3ba-109">属性</span><span class="sxs-lookup"><span data-stu-id="2a3ba-109">Attributes</span></span>  
  
|<span data-ttu-id="2a3ba-110">要素</span><span class="sxs-lookup"><span data-stu-id="2a3ba-110">Element</span></span>|<span data-ttu-id="2a3ba-111">説明</span><span class="sxs-lookup"><span data-stu-id="2a3ba-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2a3ba-112">name</span><span class="sxs-lookup"><span data-stu-id="2a3ba-112">name</span></span>|<span data-ttu-id="2a3ba-113">追跡参加要素の名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-113">A string that specifies the name of a tracking participant.</span></span>|  
|<span data-ttu-id="2a3ba-114">profileName</span><span class="sxs-lookup"><span data-stu-id="2a3ba-114">profileName</span></span>|<span data-ttu-id="2a3ba-115">追跡参加要素が定期受信した追跡レコードを定義する、追跡プロファイルの名前を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-115">A string that specifies the name of the tracking profile which defines the tracking records the tracking participant has subscribed to.</span></span>|  
|<span data-ttu-id="2a3ba-116">type</span><span class="sxs-lookup"><span data-stu-id="2a3ba-116">type</span></span>|<span data-ttu-id="2a3ba-117">追跡参加要素の型を指定する文字列。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-117">A string that specifies the type of a tracking participant.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2a3ba-118">子要素</span><span class="sxs-lookup"><span data-stu-id="2a3ba-118">Child Elements</span></span>  

 <span data-ttu-id="2a3ba-119">なし。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2a3ba-120">親要素</span><span class="sxs-lookup"><span data-stu-id="2a3ba-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2a3ba-121">要素</span><span class="sxs-lookup"><span data-stu-id="2a3ba-121">Element</span></span>|<span data-ttu-id="2a3ba-122">説明</span><span class="sxs-lookup"><span data-stu-id="2a3ba-122">Description</span></span>|  
|-------------|-----------------|  
|[\<participants>](../windows-workflow-foundation/participants.md)|<span data-ttu-id="2a3ba-123">追跡参加要素の一覧</span><span class="sxs-lookup"><span data-stu-id="2a3ba-123">A list of tracking participants</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2a3ba-124">解説</span><span class="sxs-lookup"><span data-stu-id="2a3ba-124">Remarks</span></span>  

 <span data-ttu-id="2a3ba-125">追跡参加要素は、ワークフローから生成される追跡データを取得し、それを別のメディアに保存するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-125">Tracking participants are used to get the tracking data emitted from the workflow and store it into different mediums.</span></span> <span data-ttu-id="2a3ba-126">同様に、追跡レコードの後処理はすべて、追跡参加要素内でも実行できます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-126">Likewise, any post processing on the tracking Records can also be done within the tracking participant.</span></span>  
  
 <span data-ttu-id="2a3ba-127">複数の追跡参加要素が追跡イベントを同時に使用することができます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-127">Multiple tracking participants can consume the tracking events simultaneously.</span></span> <span data-ttu-id="2a3ba-128">各追跡参加要素は、それぞれ別の追跡プロファイルと関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-128">Each tracking participant can be associated with a different tracking profile.</span></span>  
  
 <span data-ttu-id="2a3ba-129">追跡レコードを ETW セッションに書き込む、標準の追跡参加要素が用意されています。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-129">A standard tracking participant is provided which writes the tracking records to an ETW session.</span></span> <span data-ttu-id="2a3ba-130">参加要素は、追跡固有の動作を構成ファイルに追加することによって、ワークフロー サービスで構成されます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-130">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="2a3ba-131">ETW 追跡参加要素を有効にすると、追跡レコードをイベント ビューアーで表示できます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-131">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="2a3ba-132">これで要件が満たされない場合は、カスタムの追跡参加要素を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-132">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a3ba-133">例</span><span class="sxs-lookup"><span data-stu-id="2a3ba-133">Example</span></span>  

 <span data-ttu-id="2a3ba-134">次の構成例は、Web.config ファイルで構成されている標準の ETW 追跡参加要素を示します。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-134">The following configuration example shows the standard ETW tracking participant being configured in the Web.config file.</span></span>  
  
 <span data-ttu-id="2a3ba-135">ETW 追跡参加要素が追跡レコードを ETW に書き込むために使用するプロバイダー ID は、`<diagnostics>` セクションで定義されます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-135">The Provider Id that the ETW Tracking Participant uses for writing the Tracking Records to ETW is defined in the `<diagnostics>` section.</span></span> <span data-ttu-id="2a3ba-136">追跡参加要素には、その要素が定期受信した追跡レコードを指定するためのプロファイルが関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-136">The tracking participant has a profile associated with it to specify the tracking records it has subscribed to.</span></span> <span data-ttu-id="2a3ba-137">これは、`profileName` 要素の `<add>` 属性で定義されます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-137">This is defined by the `profileName` attribute of the `<add>` element.</span></span> <span data-ttu-id="2a3ba-138">これらが定義されると、追跡参加要素は `<etwTracking>` サービス動作に追加されます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-138">Once these are defined, the Tracking Participant is added to the `<etwTracking>` service behavior.</span></span> <span data-ttu-id="2a3ba-139">これにより、選択した追跡参加要素がワークフロー インスタンスの拡張機能に追加され、追跡レコードの受信が開始されます。</span><span class="sxs-lookup"><span data-stu-id="2a3ba-139">This will add the selected Tracking Participants to the Workflow instance’s extensions, so that they begin to receive the Tracking Records.</span></span>  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0" />
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile" />
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="2a3ba-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="2a3ba-140">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [<span data-ttu-id="2a3ba-141">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="2a3ba-141">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="2a3ba-142">追跡参加要素</span><span class="sxs-lookup"><span data-stu-id="2a3ba-142">Tracking Participants</span></span>](../../../windows-workflow-foundation/tracking-participants.md)
