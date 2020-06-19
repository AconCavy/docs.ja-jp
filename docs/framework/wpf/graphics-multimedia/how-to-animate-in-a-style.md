---
title: スタイル内でアニメーション化する方法
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], properties [WPF], within styles
- styles [WPF], animating properties within
ms.assetid: 6a791f3d-6b1f-4972-a2f9-35880bcfd954
ms.openlocfilehash: 0b29648bf15f0046adcdee610f9565f7deb24972
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744879"
---
# <a name="how-to-animate-in-a-style"></a><span data-ttu-id="7ff32-102">スタイル内でアニメーション化する方法</span><span class="sxs-lookup"><span data-stu-id="7ff32-102">How to animate in a style</span></span>

<span data-ttu-id="7ff32-103">この例では、スタイル内でプロパティをアニメーション化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7ff32-103">This example shows how to animate properties within a style.</span></span> <span data-ttu-id="7ff32-104">スタイル内でアニメーション化する場合、スタイルが定義されているフレームワーク要素のみを直接ターゲットにできます。</span><span class="sxs-lookup"><span data-stu-id="7ff32-104">When animating within a style, only the framework element for which the style is defined can be targeted directly.</span></span> <span data-ttu-id="7ff32-105">Freezable オブジェクトをターゲットにするには、スタイルが設定されている要素のプロパティから "ドット ダウン" する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ff32-105">To target a freezable object, you must "dot down" from a property of the styled element.</span></span>

<span data-ttu-id="7ff32-106">次の例では、いくつかのアニメーションがスタイル内に定義されており、<xref:System.Windows.Controls.Button> に適用されています。</span><span class="sxs-lookup"><span data-stu-id="7ff32-106">In the following example, several animations are defined within a style and applied to a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="7ff32-107">ユーザーがボタンの上にマウスを移動すると、ボタンは不透明から部分的に半透明になって元に戻ることを繰り返します。</span><span class="sxs-lookup"><span data-stu-id="7ff32-107">When the user moves the mouse over the button, it fades from opaque to partially translucent and back again, repeatedly.</span></span> <span data-ttu-id="7ff32-108">ユーザーがマウスをボタンから移動すると、ボタンは完全に不透明になります。</span><span class="sxs-lookup"><span data-stu-id="7ff32-108">When the user moves the mouse off the button, it becomes completely opaque.</span></span> <span data-ttu-id="7ff32-109">ボタンをクリックすると、ボタンの背景色がオレンジから白に変わり、元に戻ります。</span><span class="sxs-lookup"><span data-stu-id="7ff32-109">When the button is clicked, its background color changes from orange to white and back again.</span></span> <span data-ttu-id="7ff32-110">ボタンの描画に使用される <xref:System.Windows.Media.SolidColorBrush> を直接ターゲットにすることはできないため、ボタンの <xref:System.Windows.Controls.Control.Background%2A> プロパティからドット ダウンしてアクセスします。</span><span class="sxs-lookup"><span data-stu-id="7ff32-110">Because the <xref:System.Windows.Media.SolidColorBrush> used to paint the button can't be targeted directly, it is accessed by dotting down from the button's <xref:System.Windows.Controls.Control.Background%2A> property.</span></span>

## <a name="example"></a><span data-ttu-id="7ff32-111">例</span><span class="sxs-lookup"><span data-stu-id="7ff32-111">Example</span></span>

[!code-xaml[timingbehaviors_snip#21](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StyleStoryboardsExample.xaml#21)]

<span data-ttu-id="7ff32-112">スタイル内でアニメーション化するときに、存在しないオブジェクトをターゲットにすることができる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="7ff32-112">Note that when animating within a style, it's possible to target objects that don't exist.</span></span> <span data-ttu-id="7ff32-113">たとえば、スタイルで <xref:System.Windows.Media.SolidColorBrush> を使用してボタンの背景プロパティを設定していたが、ある時点でそのスタイルがオーバーライドされて、<xref:System.Windows.Media.LinearGradientBrush> を使用してボタンの背景が設定されたとします。</span><span class="sxs-lookup"><span data-stu-id="7ff32-113">For example, suppose your style uses a <xref:System.Windows.Media.SolidColorBrush> to set a Button's background property, but at some point the style is overridden and the button's background is set with a <xref:System.Windows.Media.LinearGradientBrush>.</span></span>  <span data-ttu-id="7ff32-114"><xref:System.Windows.Media.SolidColorBrush> をアニメーション化しても例外はスローされません。アニメーションは、単に警告なしで失敗します。</span><span class="sxs-lookup"><span data-stu-id="7ff32-114">Trying to animate the <xref:System.Windows.Media.SolidColorBrush> won't throw an exception; the animation will simply fail silently.</span></span>

<span data-ttu-id="7ff32-115">ストーリーボードのターゲット設定構文の詳細については、「[ストーリーボードの概要](storyboards-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ff32-115">For more information about storyboard targeting syntax, see the [Storyboards Overview](storyboards-overview.md).</span></span> <span data-ttu-id="7ff32-116">アニメーション化の詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ff32-116">For more information about animation, see the [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="7ff32-117">スタイルの詳細については、「[スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ff32-117">For more information about styles, see the [Styling and Templating](../../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>
