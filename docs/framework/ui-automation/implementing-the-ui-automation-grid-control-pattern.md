---
title: UI オートメーション Grid コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: f4b5f1763b655026b20f37605d4649606af7fea6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435373"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a><span data-ttu-id="657db-102">UI オートメーション Grid コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="657db-102">Implementing the UI Automation Grid Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="657db-103">このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="657db-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="657db-104">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="657db-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="657db-105">このトピックでは、プロパティ、メソッド、イベントに関する情報など、 <xref:System.Windows.Automation.Provider.IGridProvider>の実装のためのガイドラインと規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="657db-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IGridProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="657db-106">その他のリファレンスへのリンクは、概要の最後に記載します。</span><span class="sxs-lookup"><span data-stu-id="657db-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="657db-107"><xref:System.Windows.Automation.GridPattern> コントロール パターンは、子要素のコレクションのコンテナーとして機能するコントロールをサポートするために使用します。</span><span class="sxs-lookup"><span data-stu-id="657db-107">The <xref:System.Windows.Automation.GridPattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="657db-108">この要素の子には <xref:System.Windows.Automation.Provider.IGridItemProvider> を実装する必要があります。また、この要素の子は、行と列で表現できる 2 次元の論理座標システムで編成しなければなりません。</span><span class="sxs-lookup"><span data-stu-id="657db-108">The children of this element must implement <xref:System.Windows.Automation.Provider.IGridItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="657db-109">このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="657db-109">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="657db-110">実装のガイドラインと規則</span><span class="sxs-lookup"><span data-stu-id="657db-110">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="657db-111">Grid コントロール パターンを実装する場合は、次のガイドラインと規則に注意してください。</span><span class="sxs-lookup"><span data-stu-id="657db-111">When implementing the Grid control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="657db-112">グリッド座標は 0 から始まり、左上 (ロケールによっては右上) のセルの座標が (0,0) になります。</span><span class="sxs-lookup"><span data-stu-id="657db-112">Grid coordinates are zero-based with the upper left (or upper right cell depending on locale) having coordinates (0, 0).</span></span>  
  
- <span data-ttu-id="657db-113">セルが空の場合でも、そのセルの <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> プロパティをサポートするために、UI オートメーション要素を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="657db-113">If a cell is empty, a UI Automation element must still be returned in order to support the <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> property for that cell.</span></span> <span data-ttu-id="657db-114">これが可能なのは、グリッド内の子要素のレイアウトが不調和配列に似ている場合です (次の例を参照)。</span><span class="sxs-lookup"><span data-stu-id="657db-114">This is possible when the layout of child elements in the grid is similar to a ragged array (see example below).</span></span>  
  
 <span data-ttu-id="657db-115">![不規則レイアウトを表示するエクスプローラービュー。](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span><span class="sxs-lookup"><span data-stu-id="657db-115">![Windows Explorer view showing ragged layout.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")</span></span>  
<span data-ttu-id="657db-116">空の座標を持つグリッド コントロールの例</span><span class="sxs-lookup"><span data-stu-id="657db-116">Example of a Grid Control with Empty Coordinates</span></span>  
  
- <span data-ttu-id="657db-117">項目が 1 つのグリッドでも、論理的にグリッドであると見なされる場合は、 <xref:System.Windows.Automation.Provider.IGridProvider> を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="657db-117">A grid with a single item is still required to implement <xref:System.Windows.Automation.Provider.IGridProvider> if it is logically considered to be a grid.</span></span> <span data-ttu-id="657db-118">グリッド内の子項目の数は問題ではありません。</span><span class="sxs-lookup"><span data-stu-id="657db-118">The number of child items in the grid is immaterial.</span></span>  
  
- <span data-ttu-id="657db-119">プロバイダーの実装によっては、非表示の行および列は [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーに読み込まれ、 <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> プロパティおよび <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> プロパティに反映されます。</span><span class="sxs-lookup"><span data-stu-id="657db-119">Hidden rows and columns, depending on the provider implementation, may be loaded in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree and therefore will be reflected in the <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> and <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> properties.</span></span> <span data-ttu-id="657db-120">読み込まれていない場合は、非表示の行および列はカウントされません。</span><span class="sxs-lookup"><span data-stu-id="657db-120">If the hidden rows and columns have not yet been loaded, they should not be counted.</span></span>  
  
- <span data-ttu-id="657db-121"><xref:System.Windows.Automation.Provider.IGridProvider> はグリッドのアクティブな操作を有効にしないため、 <xref:System.Windows.Automation.Provider.ITransformProvider> を実装してこの機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="657db-121"><xref:System.Windows.Automation.Provider.IGridProvider> does not enable active manipulation of a grid; <xref:System.Windows.Automation.Provider.ITransformProvider> must be implemented to enable this functionality.</span></span>  
  
- <span data-ttu-id="657db-122"><xref:System.Windows.Automation.StructureChangedEventHandler> を使用すると、追加、削除、マージされたセルなど、グリッドの構造またはレイアウトの変更をリッスンできます。</span><span class="sxs-lookup"><span data-stu-id="657db-122">Use a <xref:System.Windows.Automation.StructureChangedEventHandler> to listen for structural or layout changes to the grid such as cells that have been added, removed, or merged.</span></span>  
  
- <span data-ttu-id="657db-123"><xref:System.Windows.Automation.AutomationFocusChangedEventHandler> を使用すると、グリッドの項目またはセルの反復処理を追跡できます。</span><span class="sxs-lookup"><span data-stu-id="657db-123">Use a <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> to track traversal through the items or cells of a grid.</span></span>  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a><span data-ttu-id="657db-124">IGridProvider の必須メンバー</span><span class="sxs-lookup"><span data-stu-id="657db-124">Required Members for IGridProvider</span></span>  
 <span data-ttu-id="657db-125">IGridProvider インターフェイスの実装時には、次のプロパティとメソッドが必要です。</span><span class="sxs-lookup"><span data-stu-id="657db-125">The following properties and methods are required for implementing the IGridProvider interface.</span></span>  
  
|<span data-ttu-id="657db-126">必須メンバー</span><span class="sxs-lookup"><span data-stu-id="657db-126">Required members</span></span>|<span data-ttu-id="657db-127">種類</span><span class="sxs-lookup"><span data-stu-id="657db-127">Type</span></span>|<span data-ttu-id="657db-128">説明</span><span class="sxs-lookup"><span data-stu-id="657db-128">Notes</span></span>|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|<span data-ttu-id="657db-129">プロパティ</span><span class="sxs-lookup"><span data-stu-id="657db-129">Property</span></span>|<span data-ttu-id="657db-130">なし</span><span class="sxs-lookup"><span data-stu-id="657db-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|<span data-ttu-id="657db-131">プロパティ</span><span class="sxs-lookup"><span data-stu-id="657db-131">Property</span></span>|<span data-ttu-id="657db-132">なし</span><span class="sxs-lookup"><span data-stu-id="657db-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|<span data-ttu-id="657db-133">メソッド</span><span class="sxs-lookup"><span data-stu-id="657db-133">Method</span></span>|<span data-ttu-id="657db-134">なし</span><span class="sxs-lookup"><span data-stu-id="657db-134">None</span></span>|  
  
 <span data-ttu-id="657db-135">このコントロール パターンには、関連するイベントがありません。</span><span class="sxs-lookup"><span data-stu-id="657db-135">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="657db-136">例外</span><span class="sxs-lookup"><span data-stu-id="657db-136">Exceptions</span></span>  
 <span data-ttu-id="657db-137">プロバイダーは、次の例外をスローする必要があります。</span><span class="sxs-lookup"><span data-stu-id="657db-137">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="657db-138">例外の種類</span><span class="sxs-lookup"><span data-stu-id="657db-138">Exception type</span></span>|<span data-ttu-id="657db-139">条件</span><span class="sxs-lookup"><span data-stu-id="657db-139">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="657db-140">-要求された行座標が <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> より大きい場合、または列座標が <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>より大きい場合。</span><span class="sxs-lookup"><span data-stu-id="657db-140">-   If the requested row coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> or the column coordinate is larger than the <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> <span data-ttu-id="657db-141">-要求された行または列の座標のいずれかが0未満の場合。</span><span class="sxs-lookup"><span data-stu-id="657db-141">-   If either of the requested row or column coordinates is less than zero.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="657db-142">参照</span><span class="sxs-lookup"><span data-stu-id="657db-142">See also</span></span>

- [<span data-ttu-id="657db-143">UI Automation コントロール パターンの概要</span><span class="sxs-lookup"><span data-stu-id="657db-143">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="657db-144">UI オートメーション プロバイダーでのコントロール パターンのサポート</span><span class="sxs-lookup"><span data-stu-id="657db-144">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="657db-145">UI Automation Control Patterns for Clients</span><span class="sxs-lookup"><span data-stu-id="657db-145">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="657db-146">UI オートメーション GridItem コントロール パターンの実装</span><span class="sxs-lookup"><span data-stu-id="657db-146">Implementing the UI Automation GridItem Control Pattern</span></span>](implementing-the-ui-automation-griditem-control-pattern.md)
- [<span data-ttu-id="657db-147">UI Automation ツリーの概要</span><span class="sxs-lookup"><span data-stu-id="657db-147">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="657db-148">UI オートメーションにおけるキャッシュの使用</span><span class="sxs-lookup"><span data-stu-id="657db-148">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
