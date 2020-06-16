---
title: 'パフォーマンスの最適化: レイアウトとデザイン'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- layout [WPF], optimizing performance
- design considerations [WPF]
- layout pass [WPF]
ms.assetid: 005f4cda-a849-448b-916b-38d14d9a96fe
ms.openlocfilehash: a18cc364d625cc98f77e63b0f361980ef574e8a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611891"
---
# <a name="optimizing-performance-layout-and-design"></a><span data-ttu-id="5cf8c-102">パフォーマンスの最適化: レイアウトとデザイン</span><span class="sxs-lookup"><span data-stu-id="5cf8c-102">Optimizing Performance: Layout and Design</span></span>
<span data-ttu-id="5cf8c-103">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの設計によっては、レイアウトの計算やオブジェクト参照の検証で不要なオーバーヘッドが発生して、パフォーマンスに影響が及ぶことがあります。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-103">The design of your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application can impact its performance by creating unnecessary overhead in calculating layout and validating object references.</span></span> <span data-ttu-id="5cf8c-104">オブジェクトの作成 (特に実行時の作成) はアプリケーションのパフォーマンス特性に影響する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-104">The construction of objects, particularly at run time, can affect the performance characteristics of your application.</span></span>  
  
 <span data-ttu-id="5cf8c-105">このトピックでは、このようなパフォーマンスに関する推奨事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-105">This topic provides performance recommendations in these areas.</span></span>  
  
## <a name="layout"></a><span data-ttu-id="5cf8c-106">レイアウト</span><span class="sxs-lookup"><span data-stu-id="5cf8c-106">Layout</span></span>  
 <span data-ttu-id="5cf8c-107">"レイアウト パス" という用語は、<xref:System.Windows.Controls.Panel> 派生オブジェクトの子のコレクションのメンバーを測定および配置して、それらを画面上に描画するプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-107">The term "layout pass" describes the process of measuring and arranging the members of a <xref:System.Windows.Controls.Panel>-derived object's collection of children, and then drawing them onscreen.</span></span> <span data-ttu-id="5cf8c-108">レイアウト パスは数学的に増大するプロセスで、コレクション内の子の数が多くなれば、必要な計算の数も多くなります。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-108">The layout pass is a mathematically-intensive process—the larger the number of children in the collection, the greater the number of calculations required.</span></span> <span data-ttu-id="5cf8c-109">たとえば、コレクション内の子 <xref:System.Windows.UIElement> オブジェクトがその位置を変更するたびに、レイアウト システムによる新しいパスがトリガーされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-109">For example, each time a child <xref:System.Windows.UIElement> object in the collection changes its position, it has the potential to trigger a new pass by the layout system.</span></span> <span data-ttu-id="5cf8c-110">オブジェクトの特性とレイアウトの動作の間には密接な関係があるため、レイアウト システムを呼び出すことができるイベントの種類を把握することが重要です。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-110">Because of the close relationship between object characteristics and layout behavior, it's important to understand the type of events that can invoke the layout system.</span></span> <span data-ttu-id="5cf8c-111">レイアウト パスの不要な呼び出しをできるだけ減らすことで、アプリケーションのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-111">Your application will perform better by reducing as much as possible any unnecessary invocations of the layout pass.</span></span>  
  
 <span data-ttu-id="5cf8c-112">レイアウト システムは、コレクションの子メンバーごとに、測定パスと配置パスという 2 つのパスを実行します。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-112">The layout system completes two passes for each child member in a collection: a measure pass, and an arrange pass.</span></span> <span data-ttu-id="5cf8c-113">それぞれの子オブジェクトでは、独自のレイアウト動作を提供するために、<xref:System.Windows.UIElement.Measure%2A> および <xref:System.Windows.UIElement.Arrange%2A> メソッドの独自のオーバーライドされた実装が提供されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-113">Each child object provides its own overridden implementation of the <xref:System.Windows.UIElement.Measure%2A> and <xref:System.Windows.UIElement.Arrange%2A> methods in order to provide its own specific layout behavior.</span></span> <span data-ttu-id="5cf8c-114">簡単に言うと、レイアウトは、要素のサイズ測定、配置、画面上への描画を繰り返す再帰的なシステムです。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-114">At its simplest, layout is a recursive system that leads to an element being sized, positioned, and drawn onscreen.</span></span>  
  
- <span data-ttu-id="5cf8c-115">子 <xref:System.Windows.UIElement> オブジェクトでは、最初にそのコア プロパティが測定され、レイアウト プロセスが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-115">A child <xref:System.Windows.UIElement> object begins the layout process by first having its core properties measured.</span></span>  
  
- <span data-ttu-id="5cf8c-116"><xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.Margin%2A> など、サイズに関連するオブジェクトの <xref:System.Windows.FrameworkElement> のプロパティが評価されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-116">The object's <xref:System.Windows.FrameworkElement> properties that are related to size, such as <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, and <xref:System.Windows.FrameworkElement.Margin%2A>, are evaluated.</span></span>  
  
- <span data-ttu-id="5cf8c-117"><xref:System.Windows.Controls.Panel> 固有のロジックが適用されます。たとえば、<xref:System.Windows.Controls.DockPanel> の <xref:System.Windows.Controls.DockPanel.Dock%2A> プロパティや <xref:System.Windows.Controls.StackPanel> の <xref:System.Windows.Controls.StackPanel.Orientation%2A> プロパティなどです。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-117"><xref:System.Windows.Controls.Panel>-specific logic is applied, such as the <xref:System.Windows.Controls.DockPanel.Dock%2A> property of the <xref:System.Windows.Controls.DockPanel>, or the <xref:System.Windows.Controls.StackPanel.Orientation%2A> property of the <xref:System.Windows.Controls.StackPanel>.</span></span>  
  
- <span data-ttu-id="5cf8c-118">すべての子オブジェクトが測定された後、コンテンツが配置されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-118">Content is arranged, or positioned, after all child objects have been measured.</span></span>  
  
- <span data-ttu-id="5cf8c-119">子オブジェクトのコレクションが画面に描画されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-119">The collection of child objects is drawn to the screen.</span></span>  
  
 <span data-ttu-id="5cf8c-120">以下のアクションが発生すると、再びレイアウト パス プロセスが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-120">The layout pass process is invoked again if any of the following actions occur:</span></span>  
  
- <span data-ttu-id="5cf8c-121">子オブジェクトがコレクションに追加された場合。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-121">A child object is added to the collection.</span></span>  
  
- <span data-ttu-id="5cf8c-122">子オブジェクトに <xref:System.Windows.FrameworkElement.LayoutTransform%2A> が適用されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-122">A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> is applied to the child object.</span></span>  
  
- <span data-ttu-id="5cf8c-123">子オブジェクトに対して <xref:System.Windows.UIElement.UpdateLayout%2A> メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-123">The <xref:System.Windows.UIElement.UpdateLayout%2A> method is called for the child object.</span></span>  
  
- <span data-ttu-id="5cf8c-124">測定パスや配置パスに影響を与えるものとしてメタデータでマークされている依存関係プロパティの値が変更された場合。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-124">When a change occurs to the value of a dependency property that is marked with metadata affecting the measure or arrange passes.</span></span>  
  
### <a name="use-the-most-efficient-panel-where-possible"></a><span data-ttu-id="5cf8c-125">可能な場合は最も効率的なパネルを使用する</span><span class="sxs-lookup"><span data-stu-id="5cf8c-125">Use the Most Efficient Panel where Possible</span></span>  
 <span data-ttu-id="5cf8c-126">使用する <xref:System.Windows.Controls.Panel> 派生要素のレイアウト動作は、レイアウト プロセスの複雑さに直接基づいています。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-126">The complexity of the layout process is directly based on the layout behavior of the <xref:System.Windows.Controls.Panel>-derived elements you use.</span></span> <span data-ttu-id="5cf8c-127">たとえば、<xref:System.Windows.Controls.Grid> または <xref:System.Windows.Controls.StackPanel> コントロールでは <xref:System.Windows.Controls.Canvas> コントロールよりもはるかに多くの機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-127">For example, a <xref:System.Windows.Controls.Grid> or <xref:System.Windows.Controls.StackPanel> control provides much more functionality than a <xref:System.Windows.Controls.Canvas> control.</span></span> <span data-ttu-id="5cf8c-128">はるかに多くの機能が用意されていますが、その代償として、パフォーマンスへの負荷も高くなります。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-128">The price for this greater increase in functionality is a greater increase in performance costs.</span></span> <span data-ttu-id="5cf8c-129">しかし、<xref:System.Windows.Controls.Grid> コントロールに用意されている機能が必要ない場合は、<xref:System.Windows.Controls.Canvas> やカスタム パネルなど、コストのかからない代替手段を使用してください。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-129">However, if you do not require the functionality that a <xref:System.Windows.Controls.Grid> control provides, you should use the less costly alternatives, such as a <xref:System.Windows.Controls.Canvas> or a custom panel.</span></span>  
  
 <span data-ttu-id="5cf8c-130">詳細については、「[Panels Overview](../controls/panels-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-130">For more information, see [Panels Overview](../controls/panels-overview.md).</span></span>  
  
### <a name="update-rather-than-replace-a-rendertransform"></a><span data-ttu-id="5cf8c-131">RenderTransform は置き換えずに更新する</span><span class="sxs-lookup"><span data-stu-id="5cf8c-131">Update Rather than Replace a RenderTransform</span></span>  
 <span data-ttu-id="5cf8c-132"><xref:System.Windows.Media.Transform> を <xref:System.Windows.UIElement.RenderTransform%2A> プロパティの値として置き換えずに、更新することができます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-132">You may be able to update a <xref:System.Windows.Media.Transform> rather than replacing it as the value of a <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span> <span data-ttu-id="5cf8c-133">アニメーションを含むシナリオでは特にこれが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-133">This is particularly true in scenarios that involve animation.</span></span> <span data-ttu-id="5cf8c-134">既存の <xref:System.Windows.Media.Transform> を更新すると、不要なレイアウト計算が開始されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-134">By updating an existing <xref:System.Windows.Media.Transform>, you avoid initiating an unnecessary layout calculation.</span></span>  
  
### <a name="build-your-tree-top-down"></a><span data-ttu-id="5cf8c-135">ツリーはトップダウンで作成する</span><span class="sxs-lookup"><span data-stu-id="5cf8c-135">Build Your Tree Top-Down</span></span>  
 <span data-ttu-id="5cf8c-136">論理ツリーのノードが追加または削除されると、ノードの親とそのすべての子でプロパティの無効化が行われます。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-136">When a node is added or removed from the logical tree, property invalidations are raised on the node's parent and all its children.</span></span> <span data-ttu-id="5cf8c-137">このため、常にトップダウンの作成パターンに従って、検証済みのノードで無駄に無効化が行われないようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-137">As a result, a top-down construction pattern should always be followed to avoid the cost of unnecessary invalidations on nodes that have already been validated.</span></span> <span data-ttu-id="5cf8c-138">次の表に、ツリーをトップダウンで作成した場合とボトムアップで作成した場合の実行速度の違いを示します。このツリーには 150 のレベルがあり、各レベルに <xref:System.Windows.Controls.TextBlock> と <xref:System.Windows.Controls.DockPanel> が 1 つずつ含まれています。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-138">The following table shows the difference in execution speed between building a tree top-down versus bottom-up, where the tree is 150 levels deep with a single <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Controls.DockPanel> at each level.</span></span>  
  
|<span data-ttu-id="5cf8c-139">**動作**</span><span class="sxs-lookup"><span data-stu-id="5cf8c-139">**Action**</span></span>|<span data-ttu-id="5cf8c-140">**ツリーの作成 (ミリ秒)**</span><span class="sxs-lookup"><span data-stu-id="5cf8c-140">**Tree building (in ms)**</span></span>|<span data-ttu-id="5cf8c-141">**レンダリング-ツリーの作成を含む (ミリ秒)**</span><span class="sxs-lookup"><span data-stu-id="5cf8c-141">**Render—includes tree building (in ms)**</span></span>|  
|----------------|---------------------------------|-------------------------------------------------|  
|<span data-ttu-id="5cf8c-142">ボトムアップ</span><span class="sxs-lookup"><span data-stu-id="5cf8c-142">Bottom-up</span></span>|<span data-ttu-id="5cf8c-143">366</span><span class="sxs-lookup"><span data-stu-id="5cf8c-143">366</span></span>|<span data-ttu-id="5cf8c-144">454</span><span class="sxs-lookup"><span data-stu-id="5cf8c-144">454</span></span>|  
|<span data-ttu-id="5cf8c-145">トップダウン</span><span class="sxs-lookup"><span data-stu-id="5cf8c-145">Top-down</span></span>|<span data-ttu-id="5cf8c-146">11</span><span class="sxs-lookup"><span data-stu-id="5cf8c-146">11</span></span>|<span data-ttu-id="5cf8c-147">96</span><span class="sxs-lookup"><span data-stu-id="5cf8c-147">96</span></span>|  
  
 <span data-ttu-id="5cf8c-148">ツリーをトップダウンで作成する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-148">The following code example demonstrates how to create a tree top down.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Window1.xaml.cs#performancesnippet1)]
 [!code-vb[Performance#PerformanceSnippet1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/window1.xaml.vb#performancesnippet1)]  
  
 <span data-ttu-id="5cf8c-149">論理ツリーについて詳しくは、「[WPF のツリー](trees-in-wpf.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="5cf8c-149">For more information on the logical tree, see [Trees in WPF](trees-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf8c-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="5cf8c-150">See also</span></span>

- [<span data-ttu-id="5cf8c-151">WPF アプリケーションのパフォーマンスの最適化</span><span class="sxs-lookup"><span data-stu-id="5cf8c-151">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="5cf8c-152">アプリケーション パフォーマンスの計画</span><span class="sxs-lookup"><span data-stu-id="5cf8c-152">Planning for Application Performance</span></span>](planning-for-application-performance.md)
- [<span data-ttu-id="5cf8c-153">ハードウェアの活用</span><span class="sxs-lookup"><span data-stu-id="5cf8c-153">Taking Advantage of Hardware</span></span>](optimizing-performance-taking-advantage-of-hardware.md)
- [<span data-ttu-id="5cf8c-154">2D グラフィックスとイメージング</span><span class="sxs-lookup"><span data-stu-id="5cf8c-154">2D Graphics and Imaging</span></span>](optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="5cf8c-155">オブジェクトの動作</span><span class="sxs-lookup"><span data-stu-id="5cf8c-155">Object Behavior</span></span>](optimizing-performance-object-behavior.md)
- [<span data-ttu-id="5cf8c-156">アプリケーション リソース</span><span class="sxs-lookup"><span data-stu-id="5cf8c-156">Application Resources</span></span>](optimizing-performance-application-resources.md)
- <span data-ttu-id="5cf8c-157">[[テキスト]](optimizing-performance-text.md)</span><span class="sxs-lookup"><span data-stu-id="5cf8c-157">[Text](optimizing-performance-text.md)</span></span>
- [<span data-ttu-id="5cf8c-158">データ バインディング</span><span class="sxs-lookup"><span data-stu-id="5cf8c-158">Data Binding</span></span>](optimizing-performance-data-binding.md)
- [<span data-ttu-id="5cf8c-159">パフォーマンスに関するその他の推奨事項</span><span class="sxs-lookup"><span data-stu-id="5cf8c-159">Other Performance Recommendations</span></span>](optimizing-performance-other-recommendations.md)
- [<span data-ttu-id="5cf8c-160">レイアウト</span><span class="sxs-lookup"><span data-stu-id="5cf8c-160">Layout</span></span>](layout.md)
