---
title: '方法: ストーリーボードを使用せずにプロパティをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963020"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a><span data-ttu-id="bfaf1-102">方法: ストーリーボードを使用せずにプロパティをアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="bfaf1-102">How to: Animate a Property Without Using a Storyboard</span></span>
<span data-ttu-id="bfaf1-103">この例では、<xref:System.Windows.Media.Animation.Storyboard> を使用せずに、プロパティにアニメーションを適用する 1 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-103">This example shows one way to apply an animation to a property without using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bfaf1-104">この機能は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では使用できません。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-104">This functionality is not available in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="bfaf1-105">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でプロパティをアニメーション化する方法については、「[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-105">For information about animating a property in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="bfaf1-106">プロパティにローカル アニメーションを適用するには、<xref:System.Windows.UIElement.BeginAnimation%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-106">To apply a local animation to a property, use the <xref:System.Windows.UIElement.BeginAnimation%2A> method.</span></span> <span data-ttu-id="bfaf1-107">このメソッドは、2 つのパラメーターを受け取ります。アニメーション化するプロパティを指定する <xref:System.Windows.DependencyProperty> とプロパティに適用するアニメーションです。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-107">This method takes two parameters: a <xref:System.Windows.DependencyProperty> that specifies the property to animate, and the animation to apply to that property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfaf1-108">例</span><span class="sxs-lookup"><span data-stu-id="bfaf1-108">Example</span></span>  
 <span data-ttu-id="bfaf1-109">次の例は、<xref:System.Windows.Controls.Button> の幅と背景色をアニメーション化する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-109">The following example shows how to animate the width and background color of a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 <span data-ttu-id="bfaf1-110"><xref:System.Windows.Media.Animation> 名前空間には、さまざまな種類のプロパティをアニメーション化するための多様なアニメーション クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-110">A variety of animation classes in the <xref:System.Windows.Media.Animation> namespace exist for animating different types of properties.</span></span> <span data-ttu-id="bfaf1-111">プロパティのアニメーション化の詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-111">For more information about animating properties, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="bfaf1-112">依存関係プロパティ (これらの例に示されているプロパティの種類) とその機能の詳細については、「[依存関係プロパティの概要](../advanced/dependency-properties-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-112">For more information about dependency properties (the type of properties that are shown in these examples) and their features, see [Dependency Properties Overview](../advanced/dependency-properties-overview.md).</span></span>  
  
 <span data-ttu-id="bfaf1-113"><xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用せずにアニメーション化する方法は他にもあります。詳細については、「[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bfaf1-113">There are other ways to animate without using <xref:System.Windows.Media.Animation.Storyboard> objects; for more information, see [Property Animation Techniques Overview](property-animation-techniques-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfaf1-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="bfaf1-114">See also</span></span>

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="bfaf1-115">プロパティ アニメーションの手法の概要</span><span class="sxs-lookup"><span data-stu-id="bfaf1-115">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="bfaf1-116">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="bfaf1-116">Animation Overview</span></span>](animation-overview.md)
