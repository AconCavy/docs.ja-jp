---
title: ProgressBar のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 6551701e86dd6abcd42f143f146c7bdadfeabbcf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283447"
---
# <a name="progressbar-styles-and-templates"></a><span data-ttu-id="db9a3-102">ProgressBar のスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="db9a3-102">ProgressBar Styles and Templates</span></span>
<span data-ttu-id="db9a3-103">このトピックでは、<xref:System.Windows.Controls.ProgressBar> コントロールのスタイルとテンプレートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="db9a3-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.ProgressBar> control.</span></span> <span data-ttu-id="db9a3-104"><xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。</span><span class="sxs-lookup"><span data-stu-id="db9a3-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="db9a3-105">詳細については、「[コントロールのためにテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="db9a3-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="progressbar-parts"></a><span data-ttu-id="db9a3-106">ProgressBar のパーツ</span><span class="sxs-lookup"><span data-stu-id="db9a3-106">ProgressBar Parts</span></span>  
 <span data-ttu-id="db9a3-107">次の表は、<xref:System.Windows.Controls.ProgressBar> コントロールの名前付きパーツの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="db9a3-107">The following table lists the named parts for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="db9a3-108">パーツ</span><span class="sxs-lookup"><span data-stu-id="db9a3-108">Part</span></span>|<span data-ttu-id="db9a3-109">種類</span><span class="sxs-lookup"><span data-stu-id="db9a3-109">Type</span></span>|<span data-ttu-id="db9a3-110">説明</span><span class="sxs-lookup"><span data-stu-id="db9a3-110">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="db9a3-111">PART_Indicator</span><span class="sxs-lookup"><span data-stu-id="db9a3-111">PART_Indicator</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="db9a3-112">進行状況を示すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="db9a3-112">The object that indicates progress.</span></span>|  
|<span data-ttu-id="db9a3-113">PART_Track</span><span class="sxs-lookup"><span data-stu-id="db9a3-113">PART_Track</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="db9a3-114">進行状況インジケーターのパスを定義するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="db9a3-114">The object that defines the path of the progress indicator.</span></span>|  
|<span data-ttu-id="db9a3-115">PART_GlowRect</span><span class="sxs-lookup"><span data-stu-id="db9a3-115">PART_GlowRect</span></span>|<xref:System.Windows.FrameworkElement>|<span data-ttu-id="db9a3-116">進行状況バーを装飾するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="db9a3-116">An object that embellishes the progress bar.</span></span>|  
  
## <a name="progressbar-states"></a><span data-ttu-id="db9a3-117">ProgressBar の状態</span><span class="sxs-lookup"><span data-stu-id="db9a3-117">ProgressBar States</span></span>  
 <span data-ttu-id="db9a3-118">次の表は、<xref:System.Windows.Controls.ProgressBar> コントロールの表示状態の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="db9a3-118">The following table lists the visual states for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
|<span data-ttu-id="db9a3-119">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="db9a3-119">VisualState Name</span></span>|<span data-ttu-id="db9a3-120">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="db9a3-120">VisualStateGroup Name</span></span>|<span data-ttu-id="db9a3-121">説明</span><span class="sxs-lookup"><span data-stu-id="db9a3-121">Description</span></span>|  
|----------------------|---------------------------|-----------------|  
|<span data-ttu-id="db9a3-122">Determinate</span><span class="sxs-lookup"><span data-stu-id="db9a3-122">Determinate</span></span>|<span data-ttu-id="db9a3-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="db9a3-123">CommonStates</span></span>|<span data-ttu-id="db9a3-124"><xref:System.Windows.Controls.ProgressBar> で、進行状況を <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> プロパティに基づいて報告します。</span><span class="sxs-lookup"><span data-stu-id="db9a3-124"><xref:System.Windows.Controls.ProgressBar> reports progress based on the <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property.</span></span>|  
|<span data-ttu-id="db9a3-125">Indeterminate</span><span class="sxs-lookup"><span data-stu-id="db9a3-125">Indeterminate</span></span>|<span data-ttu-id="db9a3-126">CommonStates</span><span class="sxs-lookup"><span data-stu-id="db9a3-126">CommonStates</span></span>|<span data-ttu-id="db9a3-127"><xref:System.Windows.Controls.ProgressBar> 繰り返しパターンを使用して一般的な進行状況を報告します。</span><span class="sxs-lookup"><span data-stu-id="db9a3-127"><xref:System.Windows.Controls.ProgressBar> reports generic progress with a repeating pattern.</span></span>|  
|<span data-ttu-id="db9a3-128">有効</span><span class="sxs-lookup"><span data-stu-id="db9a3-128">Valid</span></span>|<span data-ttu-id="db9a3-129">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="db9a3-129">ValidationStates</span></span>|<span data-ttu-id="db9a3-130">このコントロールで <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `false` です。</span><span class="sxs-lookup"><span data-stu-id="db9a3-130">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="db9a3-131">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="db9a3-131">InvalidFocused</span></span>|<span data-ttu-id="db9a3-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="db9a3-132">ValidationStates</span></span>|<span data-ttu-id="db9a3-133"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがある `true` です。</span><span class="sxs-lookup"><span data-stu-id="db9a3-133">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control has focus.</span></span>|  
|<span data-ttu-id="db9a3-134">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="db9a3-134">InvalidUnfocused</span></span>|<span data-ttu-id="db9a3-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="db9a3-135">ValidationStates</span></span>|<span data-ttu-id="db9a3-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがない `true` です。</span><span class="sxs-lookup"><span data-stu-id="db9a3-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` has the control does not have focus.</span></span>|  
  
## <a name="progressbar-controltemplate-example"></a><span data-ttu-id="db9a3-137">ProgressBar の ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="db9a3-137">ProgressBar ControlTemplate Example</span></span>  
 <span data-ttu-id="db9a3-138">次の例は、<xref:System.Windows.Controls.ProgressBar> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="db9a3-138">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.ProgressBar> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
 <span data-ttu-id="db9a3-139">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="db9a3-139">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="db9a3-140">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="db9a3-140">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db9a3-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="db9a3-141">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="db9a3-142">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="db9a3-142">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="db9a3-143">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="db9a3-143">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="db9a3-144">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="db9a3-144">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="db9a3-145">コントロールのためのテンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="db9a3-145">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
