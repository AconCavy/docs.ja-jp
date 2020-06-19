---
title: ボタンのスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Button
- parts [WPF], Button
- styles [WPF], Button
- Button [WPF], styles and templates
- templates [WPF], Button
- ControlTemplate [WPF], Button
ms.assetid: e223c759-f8c4-4717-acfb-b1e40bdf5f3b
ms.openlocfilehash: ef9f85848ebdda9dc4ae15d0f54847eacd46e24d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283578"
---
# <a name="button-styles-and-templates"></a><span data-ttu-id="2c35c-102">ボタンのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="2c35c-102">Button Styles and Templates</span></span>
<span data-ttu-id="2c35c-103">このトピックでは、<xref:System.Windows.Controls.Button> コントロールのスタイルとテンプレートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2c35c-103">This topic describes the styles and templates for the <xref:System.Windows.Controls.Button> control.</span></span> <span data-ttu-id="2c35c-104"><xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。</span><span class="sxs-lookup"><span data-stu-id="2c35c-104">You can modify the default <xref:System.Windows.Controls.ControlTemplate> to give the control a unique appearance.</span></span> <span data-ttu-id="2c35c-105">詳細については、「[コントロールのためにテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2c35c-105">For more information, see [Create a template for a control](../../../desktop-wpf/themes/how-to-create-apply-template.md).</span></span>  
  
## <a name="button-parts"></a><span data-ttu-id="2c35c-106">Button のパーツ</span><span class="sxs-lookup"><span data-stu-id="2c35c-106">Button Parts</span></span>  
 <span data-ttu-id="2c35c-107"><xref:System.Windows.Controls.Button> コントロールに名前付きパーツはありません。</span><span class="sxs-lookup"><span data-stu-id="2c35c-107">The <xref:System.Windows.Controls.Button> control does not have any named parts.</span></span>  
  
## <a name="button-states"></a><span data-ttu-id="2c35c-108">Button の状態</span><span class="sxs-lookup"><span data-stu-id="2c35c-108">Button States</span></span>  
 <span data-ttu-id="2c35c-109">次の表は、<xref:System.Windows.Controls.Button> コントロールの表示状態の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="2c35c-109">The following table lists the visual states for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
|<span data-ttu-id="2c35c-110">VisualState 名</span><span class="sxs-lookup"><span data-stu-id="2c35c-110">VisualState Name</span></span>|<span data-ttu-id="2c35c-111">VisualStateGroup 名</span><span class="sxs-lookup"><span data-stu-id="2c35c-111">VisualStateGroup Name</span></span>|<span data-ttu-id="2c35c-112">説明</span><span class="sxs-lookup"><span data-stu-id="2c35c-112">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="2c35c-113">標準</span><span class="sxs-lookup"><span data-stu-id="2c35c-113">Normal</span></span>|<span data-ttu-id="2c35c-114">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-114">CommonStates</span></span>|<span data-ttu-id="2c35c-115">既定の状態です。</span><span class="sxs-lookup"><span data-stu-id="2c35c-115">The default state.</span></span>|  
|<span data-ttu-id="2c35c-116">MouseOver</span><span class="sxs-lookup"><span data-stu-id="2c35c-116">MouseOver</span></span>|<span data-ttu-id="2c35c-117">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-117">CommonStates</span></span>|<span data-ttu-id="2c35c-118">マウス ポインターがコントロール上に配置されています。</span><span class="sxs-lookup"><span data-stu-id="2c35c-118">The mouse pointer is positioned over the control.</span></span>|  
|<span data-ttu-id="2c35c-119">押されている</span><span class="sxs-lookup"><span data-stu-id="2c35c-119">Pressed</span></span>|<span data-ttu-id="2c35c-120">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-120">CommonStates</span></span>|<span data-ttu-id="2c35c-121">コントロールが押されています。</span><span class="sxs-lookup"><span data-stu-id="2c35c-121">The control is pressed.</span></span>|  
|<span data-ttu-id="2c35c-122">無効</span><span class="sxs-lookup"><span data-stu-id="2c35c-122">Disabled</span></span>|<span data-ttu-id="2c35c-123">CommonStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-123">CommonStates</span></span>|<span data-ttu-id="2c35c-124">コントロールが無効になっています。</span><span class="sxs-lookup"><span data-stu-id="2c35c-124">The control is disabled.</span></span>|  
|<span data-ttu-id="2c35c-125">フォーカスされている</span><span class="sxs-lookup"><span data-stu-id="2c35c-125">Focused</span></span>|<span data-ttu-id="2c35c-126">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-126">FocusStates</span></span>|<span data-ttu-id="2c35c-127">コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="2c35c-127">The control has focus.</span></span>|  
|<span data-ttu-id="2c35c-128">フォーカスされていない</span><span class="sxs-lookup"><span data-stu-id="2c35c-128">Unfocused</span></span>|<span data-ttu-id="2c35c-129">FocusStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-129">FocusStates</span></span>|<span data-ttu-id="2c35c-130">コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="2c35c-130">The control does not have focus.</span></span>|  
|<span data-ttu-id="2c35c-131">有効</span><span class="sxs-lookup"><span data-stu-id="2c35c-131">Valid</span></span>|<span data-ttu-id="2c35c-132">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-132">ValidationStates</span></span>|<span data-ttu-id="2c35c-133">このコントロールで <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `false` です。</span><span class="sxs-lookup"><span data-stu-id="2c35c-133">The control uses the <xref:System.Windows.Controls.Validation> class and the <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `false`.</span></span>|  
|<span data-ttu-id="2c35c-134">InvalidFocused</span><span class="sxs-lookup"><span data-stu-id="2c35c-134">InvalidFocused</span></span>|<span data-ttu-id="2c35c-135">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-135">ValidationStates</span></span>|<span data-ttu-id="2c35c-136"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `true` で、コントロールにフォーカスがあります。</span><span class="sxs-lookup"><span data-stu-id="2c35c-136">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control has focus.</span></span>|  
|<span data-ttu-id="2c35c-137">InvalidUnfocused</span><span class="sxs-lookup"><span data-stu-id="2c35c-137">InvalidUnfocused</span></span>|<span data-ttu-id="2c35c-138">ValidationStates</span><span class="sxs-lookup"><span data-stu-id="2c35c-138">ValidationStates</span></span>|<span data-ttu-id="2c35c-139"><xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `true` で、コントロールにフォーカスがありません。</span><span class="sxs-lookup"><span data-stu-id="2c35c-139">The <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> attached property is `true` and the control does not have focus.</span></span>|  
  
## <a name="button-controltemplate-example"></a><span data-ttu-id="2c35c-140">Button の ControlTemplate の例</span><span class="sxs-lookup"><span data-stu-id="2c35c-140">Button ControlTemplate Example</span></span>  
 <span data-ttu-id="2c35c-141">次の例は、<xref:System.Windows.Controls.Button> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="2c35c-141">The following example shows how to define a <xref:System.Windows.Controls.ControlTemplate> for the <xref:System.Windows.Controls.Button> control.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Button](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#button)]  
  
 <span data-ttu-id="2c35c-142">前の例では、次のリソースの 1 つ以上を使用します。</span><span class="sxs-lookup"><span data-stu-id="2c35c-142">The preceding example uses one or more of the following resources.</span></span>  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 <span data-ttu-id="2c35c-143">完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2c35c-143">For the complete sample, see [Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c35c-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="2c35c-144">See also</span></span>

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [<span data-ttu-id="2c35c-145">コントロールのスタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="2c35c-145">Control Styles and Templates</span></span>](control-styles-and-templates.md)
- [<span data-ttu-id="2c35c-146">コントロールのカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="2c35c-146">Control Customization</span></span>](control-customization.md)
- [<span data-ttu-id="2c35c-147">スタイルとテンプレート</span><span class="sxs-lookup"><span data-stu-id="2c35c-147">Styling and Templating</span></span>](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [<span data-ttu-id="2c35c-148">コントロールのためのテンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="2c35c-148">Create a template for a control</span></span>](../../../desktop-wpf/themes/how-to-create-apply-template.md)
