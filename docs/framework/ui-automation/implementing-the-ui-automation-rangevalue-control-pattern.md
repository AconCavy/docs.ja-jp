---
title: UI オートメーション RangeValue コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
ms.openlocfilehash: 04db9f97ccea10cf8c65df0f0117c272a5e868dd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435108"
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a><span data-ttu-id="030b9-102">UI オートメーション RangeValue コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="030b9-102">Implementing the UI Automation RangeValue Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="030b9-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="030b9-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="030b9-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="030b9-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="030b9-105">このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IRangeValueProvider>の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="030b9-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IRangeValueProvider>, including information about events and properties.</span></span> <span data-ttu-id="030b9-106">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="030b9-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="030b9-107"><xref:System.Windows.Automation.RangeValuePattern> コントロール パターンは、一定の範囲内の値に設定できるコントロールをサポートするために使用します。</span><span class="sxs-lookup"><span data-stu-id="030b9-107">The <xref:System.Windows.Automation.RangeValuePattern> control pattern is used to support controls that can be set to a value within a range.</span></span> <span data-ttu-id="030b9-108">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="030b9-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="030b9-109">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="030b9-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="030b9-110">Range Value コントロール パターンを実装する場合は、次のガイドラインと規則に留意してください。</span><span class="sxs-lookup"><span data-stu-id="030b9-110">When implementing the Range Value control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="030b9-111">コントロールでは、ロケールまたはユーザー設定に基づいてサポートされているプロパティを再調整できます。</span><span class="sxs-lookup"><span data-stu-id="030b9-111">Controls allow recalibration of their supported properties based upon locale or user preference.</span></span> <span data-ttu-id="030b9-112">たとえば、温度計コントロールを、華氏または摂氏で温度を表示するように設定できます。</span><span class="sxs-lookup"><span data-stu-id="030b9-112">An example of this is a thermometer control that can be set to display the temperature in Fahrenheit or Celsius.</span></span>  
  
- <span data-ttu-id="030b9-113">進行状況バーやスライダーなどのあいまいな範囲の値を持つコントロールでは、それらの値を正規化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="030b9-113">Controls that have ambiguous range values, such as progress bars or sliders, should have those values normalized.</span></span>  
  
 <span data-ttu-id="030b9-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span><span class="sxs-lookup"><span data-stu-id="030b9-114">![Progress bar.](./media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")</span></span>  
<span data-ttu-id="030b9-115">値が整数型で、最小値と最大値のプロパティ値がそれぞれ 0 と 100 に正規化された進行状況バーの例</span><span class="sxs-lookup"><span data-stu-id="030b9-115">Example of a Progress Bar Where Value Is of Type Integer and Minimum and Maximum Property Values Are Normalized to 0 and 100, Respectively</span></span>  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a><span data-ttu-id="030b9-116">IRangeValueProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="030b9-116">Required Members for IRangeValueProvider</span></span>  
  
|<span data-ttu-id="030b9-117">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="030b9-117">Required member</span></span>|<span data-ttu-id="030b9-118">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="030b9-118">Member type</span></span>|<span data-ttu-id="030b9-119">ノート</span><span class="sxs-lookup"><span data-stu-id="030b9-119">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|<span data-ttu-id="030b9-120">property</span><span class="sxs-lookup"><span data-stu-id="030b9-120">Property</span></span>|<span data-ttu-id="030b9-121">None</span><span class="sxs-lookup"><span data-stu-id="030b9-121">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|<span data-ttu-id="030b9-122">property</span><span class="sxs-lookup"><span data-stu-id="030b9-122">Property</span></span>|<span data-ttu-id="030b9-123">None</span><span class="sxs-lookup"><span data-stu-id="030b9-123">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|<span data-ttu-id="030b9-124">property</span><span class="sxs-lookup"><span data-stu-id="030b9-124">Property</span></span>|<span data-ttu-id="030b9-125">None</span><span class="sxs-lookup"><span data-stu-id="030b9-125">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|<span data-ttu-id="030b9-126">property</span><span class="sxs-lookup"><span data-stu-id="030b9-126">Property</span></span>|<span data-ttu-id="030b9-127">None</span><span class="sxs-lookup"><span data-stu-id="030b9-127">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|<span data-ttu-id="030b9-128">property</span><span class="sxs-lookup"><span data-stu-id="030b9-128">Property</span></span>|<span data-ttu-id="030b9-129">None</span><span class="sxs-lookup"><span data-stu-id="030b9-129">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|<span data-ttu-id="030b9-130">property</span><span class="sxs-lookup"><span data-stu-id="030b9-130">Property</span></span>|<span data-ttu-id="030b9-131">None</span><span class="sxs-lookup"><span data-stu-id="030b9-131">None</span></span>|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|<span data-ttu-id="030b9-132">メソッド</span><span class="sxs-lookup"><span data-stu-id="030b9-132">Methods</span></span>|<span data-ttu-id="030b9-133">None</span><span class="sxs-lookup"><span data-stu-id="030b9-133">None</span></span>|  
  
 <span data-ttu-id="030b9-134">このコントロール パターンには、関連するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="030b9-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="030b9-135">例外</span><span class="sxs-lookup"><span data-stu-id="030b9-135">Exceptions</span></span>  
 <span data-ttu-id="030b9-136">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="030b9-136">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="030b9-137">例外の種類</span><span class="sxs-lookup"><span data-stu-id="030b9-137">Exception type</span></span>|<span data-ttu-id="030b9-138">条件</span><span class="sxs-lookup"><span data-stu-id="030b9-138">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<span data-ttu-id="030b9-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> は、 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> より大きい値または <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>より小さい値で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="030b9-139"><xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> is called with a value that is either greater than <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> or less than <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="030b9-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="030b9-140">See also</span></span>

- [<span data-ttu-id="030b9-141">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="030b9-141">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="030b9-142">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="030b9-142">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="030b9-143">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="030b9-143">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="030b9-144">UI Automation ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="030b9-144">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="030b9-145">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="030b9-145">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
