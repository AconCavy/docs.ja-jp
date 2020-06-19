---
title: NavigationWindow のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
ms.openlocfilehash: 5cc504956ce036505ac9261ea1438c7881fa2790
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283491"
---
# <a name="navigationwindow-styles-and-templates"></a><span data-ttu-id="08f87-102">NavigationWindow のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="08f87-102">NavigationWindow Styles and Templates</span></span>
<span data-ttu-id="08f87-103">このトピックでは、<xref:System.Windows.Navigation.NavigationWindow> コントロールのスタイルとテンプレートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08f87-103">This topic describes the styles and templates for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span> <span data-ttu-id="08f87-104"><xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。</span><span class="sxs-lookup"><span data-stu-id="08f87-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="08f87-105">詳細については、「[コントロールのためにテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="08f87-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="navigationwindow-parts"></a><span data-ttu-id="08f87-106">NavigationWindow のパーツ</span><span class="sxs-lookup"><span data-stu-id="08f87-106">NavigationWindow Parts</span></span>  
 <span data-ttu-id="08f87-107">次の表は、<xref:System.Windows.Navigation.NavigationWindow> コントロールの名前付きパーツの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="08f87-107">The following table lists the named parts for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="08f87-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="08f87-108">Part</span></span>|<span data-ttu-id="08f87-109">種類</span><span class="sxs-lookup"><span data-stu-id="08f87-109">Type</span></span>|<span data-ttu-id="08f87-110">説明</span><span class="sxs-lookup"><span data-stu-id="08f87-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="08f87-111">PART_NavWinCP</span><span class="sxs-lookup"><span data-stu-id="08f87-111">PART_NavWinCP</span></span>|<xref:System.Windows.Controls.ContentPresenter>|<span data-ttu-id="08f87-112">コンテンツの領域。</span><span class="sxs-lookup"><span data-stu-id="08f87-112">The area for the content.</span></span>|  
  
## <a name="navigationwindow-states"></a><span data-ttu-id="08f87-113">NavigationWindow の状態</span><span class="sxs-lookup"><span data-stu-id="08f87-113">NavigationWindow States</span></span>  
 <span data-ttu-id="08f87-114">次の表は、<xref:System.Windows.Navigation.NavigationWindow> コントロールの表示状態の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="08f87-114">The following table lists the visual states for the <xref:System.Windows.Navigation.NavigationWindow> control.</span></span>  
  
|<span data-ttu-id="08f87-115">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="08f87-115">VisualState Name</span></span>|<span data-ttu-id="08f87-116">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="08f87-116">VisualStateGroup Name</span></span>|<span data-ttu-id="08f87-117">説明</span><span class="sxs-lookup"><span data-stu-id="08f87-117">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="08f87-118">有効</span><span class="sxs-lookup"><span data-stu-id="08f87-118">Valid</span></span>|<span data-ttu-id="08f87-119">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08f87-119">ValidationStates</span></span>|<span data-ttu-id="08f87-120">このコントロールで <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `false` です。</span><span class="sxs-lookup"><span data-stu-id="08f87-120">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="08f87-121">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="08f87-121">InvalidFocused</span></span>|<span data-ttu-id="08f87-122">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08f87-122">ValidationStates</span></span>|<span data-ttu-id="08f87-123"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがある `true` です。</span><span class="sxs-lookup"><span data-stu-id="08f87-123">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="08f87-124">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="08f87-124">InvalidUnfocused</span></span>|<span data-ttu-id="08f87-125">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="08f87-125">ValidationStates</span></span>|<span data-ttu-id="08f87-126"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがない `true` です。</span><span class="sxs-lookup"><span data-stu-id="08f87-126">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="navigationwindow-controltemplate-example"></a><span data-ttu-id="08f87-127">NavigationWindow の ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="08f87-127">NavigationWindow ControlTemplate Example</span></span>  
 <span data-ttu-id="08f87-128">この例には、<xref:System.Windows.Navigation.NavigationWindow> の <xref:System.Windows.Controls.ControlTemplate> に既定で定義されているすべての要素が含まれていますが、例として特定の値を考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="08f87-128">Although this example contains all of the elements that are defined in the <xref:System.Windows.Controls.ControlTemplate> of a <xref:System.Windows.Navigation.NavigationWindow> by default, the specific values should be thought of as examples.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 <span data-ttu-id="08f87-129">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="08f87-129">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="08f87-130">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08f87-130">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08f87-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="08f87-131">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="08f87-132">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="08f87-132">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="08f87-133">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="08f87-133">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="08f87-134">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="08f87-134">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="08f87-135">コントロールのためのテンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="08f87-135">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
