---
title: カスタム アクティビティの設計と実装
description: この記事では、複合アクティビティを作成するか、新しいアクティビティの種類を作成することによって、Workflow Foundation でカスタムアクティビティを作成するためのリソースを提供します。
ms.date: 03/30/2017
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
ms.openlocfilehash: 9c184bff9518bb5581f3bf4cd408db224736192b
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419994"
---
# <a name="designing-and-implementing-custom-activities"></a><span data-ttu-id="ad533-103">カスタム アクティビティの設計と実装</span><span class="sxs-lookup"><span data-stu-id="ad533-103">Designing and Implementing Custom Activities</span></span>
<span data-ttu-id="ad533-104">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] のカスタム アクティビティを作成するには、システム標準アクティビティを複合アクティビティにアセンブルするか、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、または <xref:System.Activities.NativeActivity> から派生する新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="ad533-104">Custom activities in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] are created by either assembling system-provided activities into composite activities or by creating new types that derive from <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, or <xref:System.Activities.NativeActivity>.</span></span> <span data-ttu-id="ad533-105">ここでは、いずれかのメソッドを使用してカスタム アクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-105">This section describes how to create custom activities with either method.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ad533-106">既定では、カスタム アクティビティは、ワークフロー デザイナー内で、アクティビティ名を含む単純な四角形として表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad533-106">Custom activities by default display within the workflow designer as a simple rectangle with the activity’s name.</span></span> <span data-ttu-id="ad533-107">ワーク フロー デザイナーでアクティビティのカスタム ビジュアル表現を指定するには、カスタム デザイナーを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ad533-107">To provide a custom visual representation of your activity in the workflow designer you must also create a custom designer.</span></span> <span data-ttu-id="ad533-108">詳細については、「[カスタムアクティビティデザイナーおよびテンプレートの使用](using-custom-activity-designers-and-templates.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad533-108">For more information, see [Using Custom Activity Designers and Templates](using-custom-activity-designers-and-templates.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad533-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ad533-109">In This Section</span></span>  
 [<span data-ttu-id="ad533-110">アクティビティ作成オプション</span><span class="sxs-lookup"><span data-stu-id="ad533-110">Activity Authoring Options</span></span>](activity-authoring-options-in-wf.md)  
 <span data-ttu-id="ad533-111">[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] で使用できる作成スタイルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-111">Discusses the authoring styles available in [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)].</span></span>  
  
 [<span data-ttu-id="ad533-112">カスタム アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="ad533-112">Using a custom activity</span></span>](using-a-custom-activity.md)  
 <span data-ttu-id="ad533-113">ワークフロー プロジェクトにカスタム アクティビティを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-113">Describes how to add a custom activity to a workflow project.</span></span>  
  
  [<span data-ttu-id="ad533-114">非同期アクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="ad533-114">Creating Asynchronous Activities</span></span>](creating-asynchronous-activities-in-wf.md)  
 <span data-ttu-id="ad533-115">非同期アクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-115">Describes how to create asynchronous activities.</span></span>  
  
 [<span data-ttu-id="ad533-116">アクティビティ検証の構成</span><span class="sxs-lookup"><span data-stu-id="ad533-116">Configuring Activity Validation</span></span>](configuring-activity-validation.md)  
 <span data-ttu-id="ad533-117">アクティビティの検証を使用して、アクティビティを実行する前にその構成エラーを特定および報告する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-117">Describes how activity validation can be used to identify and report errors in an activity’s configuration prior to its execution.</span></span>  
  
 [<span data-ttu-id="ad533-118">実行時におけるアクティビティの作成</span><span class="sxs-lookup"><span data-stu-id="ad533-118">Creating an Activity at Runtime</span></span>](creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <span data-ttu-id="ad533-119"><xref:System.Activities.DynamicActivity> を使用して実行時にアクティビティを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-119">Discusses how to create activities at runtime using <xref:System.Activities.DynamicActivity>.</span></span>  
  
 [<span data-ttu-id="ad533-120">ワークフロー実行プロパティ</span><span class="sxs-lookup"><span data-stu-id="ad533-120">Workflow Execution Properties</span></span>](workflow-execution-properties.md)  
 <span data-ttu-id="ad533-121">ワークフロー実行プロパティを使用して、アクティビティの環境にコンテキスト固有のプロパティを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-121">Describes how to use workflow execution properties to add context specific properties to an activity’s environment</span></span>  
  
 [<span data-ttu-id="ad533-122">アクティビティ デリゲートの使用</span><span class="sxs-lookup"><span data-stu-id="ad533-122">Using Activity Delegates</span></span>](using-activity-delegates.md)  
 <span data-ttu-id="ad533-123">アクティビティ デリゲートを含むアクティビティを作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-123">Discusses how to author and use activities that contain activity delegates.</span></span>
  
 [<span data-ttu-id="ad533-124">アクティビティ拡張機能の使用</span><span class="sxs-lookup"><span data-stu-id="ad533-124">Using Activity Extensions</span></span>](using-activity-extensions.md)  
 <span data-ttu-id="ad533-125">アクティビティ拡張機能を作成および使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-125">Describes how to author and use activity extensions.</span></span>  
  
 [<span data-ttu-id="ad533-126">ワークフローからの OData フィードの利用</span><span class="sxs-lookup"><span data-stu-id="ad533-126">Consuming OData Feeds from a Workflow</span></span>](consuming-odata-feeds-from-a-workflow.md)  
 <span data-ttu-id="ad533-127">ワークフローから WCF Data Service を呼び出すためのいくつかの方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-127">Describes several methods for calling a WCF Data Service from a workflow.</span></span>  
  
 [<span data-ttu-id="ad533-128">アクティビティ定義のスコープ設定と表示</span><span class="sxs-lookup"><span data-stu-id="ad533-128">Activity Definition Scoping and Visibility</span></span>](activity-definition-scoping-and-visibility.md)  
 <span data-ttu-id="ad533-129">アクティビティのデータのスコープとメンバーの参照範囲を定義するためのオプションおよび規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad533-129">Describes the options and rules for defining data scoping and member visibility for activities.</span></span>
