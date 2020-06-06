---
title: クエリにおける注釈の使用
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 50855b30-d5fe-49a9-89d3-3f1bfd670958
ms.openlocfilehash: 728408e744bc1eca62158fab1a7a17e985fe3b6c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "69947284"
---
# <a name="using-annotation-in-queries"></a><span data-ttu-id="64137-102">クエリにおける注釈の使用</span><span class="sxs-lookup"><span data-stu-id="64137-102">Using Annotation in Queries</span></span>
<span data-ttu-id="64137-103">注釈を使用すると、ビルド後に構成できる値を使用して、追跡レコードへのタグ付けを任意に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="64137-103">Annotations allow you to arbitrarily tag tracking records with a value that can be configured after build time.</span></span> <span data-ttu-id="64137-104">たとえば、複数のワークフローで複数の追跡レコードを "Mail Server" = = "Mail Server1" とタグ付けすることができます。</span><span class="sxs-lookup"><span data-stu-id="64137-104">For example, you might want several tracking records across several workflows to be tagged with "Mail Server" == "Mail Server1".</span></span> <span data-ttu-id="64137-105">こうすると、後で追跡レコードのクエリを実行するときに、このタグの付いたすべてのレコードを簡単に見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="64137-105">This makes it easy to find all records with this tag when querying tracking records later.</span></span>  
  
## <a name="adding-annotations"></a><span data-ttu-id="64137-106">注釈の追加</span><span class="sxs-lookup"><span data-stu-id="64137-106">Adding Annotations</span></span>  
 <span data-ttu-id="64137-107">次の例に示すように、追跡クエリに注釈を追加できます。</span><span class="sxs-lookup"><span data-stu-id="64137-107">An annotation can be added to a tracking query as shown in the following example.</span></span>  
  
```xml  
<activityStateQuery activityName="SendEmailActivity">  
  <states>  
    <state name="Closed"/>  
  </states>  
  <annotations>  
    <annotation name="MailServer" value="Mail Server1"/>  
  </annotations>  
</activityStateQuery>  
```  
  
> [!NOTE]
> <span data-ttu-id="64137-108">これらの追跡クエリ要素は、追跡プロファイルの作成に使用できます。</span><span class="sxs-lookup"><span data-stu-id="64137-108">These tracking query elements can be used to create a tracking profile.</span></span> <span data-ttu-id="64137-109">追跡プロファイルは構成またはコードで作成できます。</span><span class="sxs-lookup"><span data-stu-id="64137-109">A tracking profile can be created either in configuration or using code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64137-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="64137-110">See also</span></span>

- <xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement>
- <xref:System.Activities.Tracking.TrackingProfile>
- [\<participants>](participants.md)
- [<span data-ttu-id="64137-111">ワークフロー追跡とトレース</span><span class="sxs-lookup"><span data-stu-id="64137-111">Workflow Tracking and Tracing</span></span>](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [<span data-ttu-id="64137-112">追跡プロファイル</span><span class="sxs-lookup"><span data-stu-id="64137-112">Tracking Profiles</span></span>](../../../windows-workflow-foundation/tracking-profiles.md)
