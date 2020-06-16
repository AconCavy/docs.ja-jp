---
title: '方法: タイムラインの速度を変更せずにクロックの速度を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- speed of Clock [WPF], changing
- clocks [WPF], changing speed of
ms.assetid: 72f36dd0-f085-445d-8589-19a83fe74f5e
ms.openlocfilehash: 19e6874b9b472cb4a5f716677f99af03f2b73b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010190"
---
# <a name="how-to-change-the-speed-of-a-clock-without-changing-the-speed-of-its-timeline"></a><span data-ttu-id="4df9a-102">方法: タイムラインの速度を変更せずにクロックの速度を変更する</span><span class="sxs-lookup"><span data-stu-id="4df9a-102">How to: Change the Speed of a Clock Without Changing the Speed of Its Timeline</span></span>
<span data-ttu-id="4df9a-103"><xref:System.Windows.Media.Animation.ClockController> オブジェクトの <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> プロパティを使用すると、クロックの <xref:System.Windows.Media.Animation.Timeline> の <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> を変更することなく、<xref:System.Windows.Media.Animation.Clock> の速度を変更できます。</span><span class="sxs-lookup"><span data-stu-id="4df9a-103">A <xref:System.Windows.Media.Animation.ClockController> object's <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> property enables you to change the speed of a <xref:System.Windows.Media.Animation.Clock> without altering the <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> of the clock's <xref:System.Windows.Media.Animation.Timeline>.</span></span> <span data-ttu-id="4df9a-104">次の例では、<xref:System.Windows.Media.Animation.ClockController> を使用して、クロックの <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> を対話的に変更できます。</span><span class="sxs-lookup"><span data-stu-id="4df9a-104">In the following example, a <xref:System.Windows.Media.Animation.ClockController> is used to interactively modify the <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> of a clock.</span></span> <span data-ttu-id="4df9a-105"><xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> イベントとクロックの <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> プロパティを使用して、対話型 <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> が変更されるたびに、クロックの現在のグローバル速度を表示します。</span><span class="sxs-lookup"><span data-stu-id="4df9a-105">The <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeedInvalidated> event and the clock's <xref:System.Windows.Media.Animation.Clock.CurrentGlobalSpeed%2A> property are used to display the clock's current global speed each time its interactive <xref:System.Windows.Media.Animation.ClockController.SpeedRatio%2A> is changed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df9a-106">例</span><span class="sxs-lookup"><span data-stu-id="4df9a-106">Example</span></span>  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerSpeedRatioExample.cs#graphicsmmclockcontrollerspeedratioexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerSpeedRatioExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerspeedratioexample.vb#graphicsmmclockcontrollerspeedratioexample)]
