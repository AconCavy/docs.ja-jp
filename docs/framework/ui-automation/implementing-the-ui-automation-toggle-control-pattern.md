---
title: UI オートメーション Toggle コントロール パターンの実装
description: UI オートメーションでトグルコントロールパターンを実装するためのガイドラインと規則を確認します。 IToggleProvider インターフェイスに必要なメンバーを確認します。
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: f9ae850a560101582b5f1a461de19f260ef59798
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168032"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a><span data-ttu-id="36a31-104">UI オートメーション Toggle コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="36a31-104">Implementing the UI Automation Toggle Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="36a31-105">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="36a31-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="36a31-106">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36a31-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="36a31-107">このトピックでは、メソッドおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IToggleProvider>の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="36a31-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>, including information about methods and properties.</span></span> <span data-ttu-id="36a31-108">その他のリファレンスへのリンクは、トピックの最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="36a31-108">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="36a31-109"><xref:System.Windows.Automation.TogglePattern> コントロール パターンは、一連の状態を順番に繰り返し、状態を一度設定したらそれを保持できるコントロールをサポートするために使用します。</span><span class="sxs-lookup"><span data-stu-id="36a31-109">The <xref:System.Windows.Automation.TogglePattern> control pattern is used to support controls that can cycle through a set of states and maintain a state once set.</span></span> <span data-ttu-id="36a31-110">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="36a31-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="36a31-111">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="36a31-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="36a31-112">Toggle コントロール パターンを実装する場合は、次のガイドラインと規則にご留意ください。</span><span class="sxs-lookup"><span data-stu-id="36a31-112">When implementing the Toggle control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="36a31-113">ボタン、ツール バー ボタン、ハイパーリンクなど、アクティブになったときに状態を保持しないコントロールは、代わりに <xref:System.Windows.Automation.Provider.IInvokeProvider> を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36a31-113">Controls that do not maintain state when activated, such as buttons, toolbar buttons, and hyperlinks, must implement <xref:System.Windows.Automation.Provider.IInvokeProvider> instead.</span></span>  
  
- <span data-ttu-id="36a31-114">コントロールは、 <xref:System.Windows.Automation.ToggleState> 、 <xref:System.Windows.Automation.ToggleState.On>、 <xref:System.Windows.Automation.ToggleState.Off> (サポートされている場合) の順にその <xref:System.Windows.Automation.ToggleState.Indeterminate>を繰り返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="36a31-114">A control must cycle through its <xref:System.Windows.Automation.ToggleState> in the following order: <xref:System.Windows.Automation.ToggleState.On>, <xref:System.Windows.Automation.ToggleState.Off> and, if supported, <xref:System.Windows.Automation.ToggleState.Indeterminate>.</span></span>  
  
- <span data-ttu-id="36a31-115"><xref:System.Windows.Automation.TogglePattern> は、SetState(newState) メソッドを提供しません。これは、適切な <xref:System.Windows.Automation.ToggleState> の順番の繰り返しをせずに、3 つの状態を持つ CheckBox を直接設定することに関連する問題のためです。</span><span class="sxs-lookup"><span data-stu-id="36a31-115"><xref:System.Windows.Automation.TogglePattern> does not provide a SetState(newState) method due to issues surrounding the direct setting of a tri-state CheckBox without cycling through its appropriate <xref:System.Windows.Automation.ToggleState> sequence.</span></span>  
  
- <span data-ttu-id="36a31-116">RadioButton コントロールは <xref:System.Windows.Automation.Provider.IToggleProvider>を実装しません。これは、その正しい状態を順番に繰り返す機能がないためです。</span><span class="sxs-lookup"><span data-stu-id="36a31-116">The RadioButton control does not implement <xref:System.Windows.Automation.Provider.IToggleProvider>, as it is not capable of cycling through its valid states.</span></span>  
  
<a name="Required_Members_for_IToggleProvider"></a>
## <a name="required-members-for-itoggleprovider"></a><span data-ttu-id="36a31-117">IToggleProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="36a31-117">Required Members for IToggleProvider</span></span>  
 <span data-ttu-id="36a31-118"><xref:System.Windows.Automation.Provider.IToggleProvider>の実装には、次のプロパティとメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="36a31-118">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IToggleProvider>.</span></span>  
  
|<span data-ttu-id="36a31-119">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="36a31-119">Required member</span></span>|<span data-ttu-id="36a31-120">メンバーの型</span><span class="sxs-lookup"><span data-stu-id="36a31-120">Member type</span></span>|<span data-ttu-id="36a31-121">メモ</span><span class="sxs-lookup"><span data-stu-id="36a31-121">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|<span data-ttu-id="36a31-122">メソッド</span><span class="sxs-lookup"><span data-stu-id="36a31-122">Method</span></span>|<span data-ttu-id="36a31-123">なし</span><span class="sxs-lookup"><span data-stu-id="36a31-123">None</span></span>|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|<span data-ttu-id="36a31-124">プロパティ</span><span class="sxs-lookup"><span data-stu-id="36a31-124">Property</span></span>|<span data-ttu-id="36a31-125">なし</span><span class="sxs-lookup"><span data-stu-id="36a31-125">None</span></span>|  
  
 <span data-ttu-id="36a31-126">このコントロール パターンには、関連するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="36a31-126">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="36a31-127">例外</span><span class="sxs-lookup"><span data-stu-id="36a31-127">Exceptions</span></span>  
 <span data-ttu-id="36a31-128">このコントロール パターンに関連付けられた例外はありません。</span><span class="sxs-lookup"><span data-stu-id="36a31-128">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36a31-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="36a31-129">See also</span></span>

- [<span data-ttu-id="36a31-130">UI オートメーション コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="36a31-130">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="36a31-131">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="36a31-131">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="36a31-132">クライアントの UI オートメーション コントロール パターン</span><span class="sxs-lookup"><span data-stu-id="36a31-132">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="36a31-133">UI オートメーションを使用した、チェック ボックスのトグル状態の取得</span><span class="sxs-lookup"><span data-stu-id="36a31-133">Get the Toggle State of a Check Box Using UI Automation</span></span>](get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [<span data-ttu-id="36a31-134">UI オートメーション ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="36a31-134">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="36a31-135">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="36a31-135">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
