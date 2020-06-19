---
title: '方法: ストーリーボードを開始後に制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboards [WPF], controlling after start
ms.assetid: 040f13f0-69f9-4ab5-be2b-079f4f80c7c0
ms.openlocfilehash: de30cfdb49df721cb4d6845dc67464e8a5b61f93
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855864"
---
# <a name="how-to-control-a-storyboard-after-it-starts"></a><span data-ttu-id="3b1ee-102">方法: ストーリーボードを開始後に制御する</span><span class="sxs-lookup"><span data-stu-id="3b1ee-102">How to: Control a Storyboard After It Starts</span></span>

<span data-ttu-id="3b1ee-103">この例では、コードを使用して、<xref:System.Windows.Media.Animation.Storyboard> を開始後に制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-103">This example shows how to use code to control a <xref:System.Windows.Media.Animation.Storyboard> after it has started.</span></span> <span data-ttu-id="3b1ee-104">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でストーリーボードを制御するには、<xref:System.Windows.Trigger> および <xref:System.Windows.TriggerAction> オブジェクトを使用します。例については、「[開始後のストーリーボードをイベント トリガーを使用して制御する](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-104">To control a storyboard in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], use <xref:System.Windows.Trigger> and <xref:System.Windows.TriggerAction> objects; for an example, see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

<span data-ttu-id="3b1ee-105">ストーリーボードを開始するには、その <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用します。これにより、ストーリーボードのアニメーションがアニメーション化するプロパティに配布され、ストーリーボードが開始されます。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-105">To start a storyboard, you use its <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method, which distributes the storyboard's animations to the properties they animate and starts the storyboard.</span></span>

<span data-ttu-id="3b1ee-106">ストーリーボードを制御できるようにするには、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用し、2 番目のパラメーターとして **true** を指定します。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-106">To make a storyboard controllable, you use the <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> method and specify **true** as the second parameter.</span></span> <span data-ttu-id="3b1ee-107">その後、ストーリーボードの対話型メソッドを使用して、ストーリーボードの一時停止、再開、シーク、停止、加速、または減速を行ったり、保留期間の最後に進めたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-107">You can then use the storyboard's interactive methods to pause, resume, seek, stop, speed up, or slow down the storyboard, or advance it to its fill period.</span></span> <span data-ttu-id="3b1ee-108">次に、ストーリーボードの対話型メソッドの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-108">The following is a list of the storyboard's interactive methods:</span></span>

- <span data-ttu-id="3b1ee-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>:ストーリーボードを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-109"><xref:System.Windows.Media.Animation.Storyboard.Pause%2A>: Pauses the storyboard.</span></span>

- <span data-ttu-id="3b1ee-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>:一時停止したストーリーボードを再開します。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-110"><xref:System.Windows.Media.Animation.Storyboard.Resume%2A>: Resumes a paused storyboard.</span></span>

- <span data-ttu-id="3b1ee-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>:ストーリーボードの対話速度を設定します。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-111"><xref:System.Windows.Media.Animation.Storyboard.SetSpeedRatio%2A>: Sets the storyboard's interactive speed.</span></span>

- <span data-ttu-id="3b1ee-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>:指定された位置にストーリーボードをシークします。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-112"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A>: Seeks the storyboard the specified location.</span></span>

- <span data-ttu-id="3b1ee-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>:指定された位置にストーリーボードをシークします。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-113"><xref:System.Windows.Media.Animation.Storyboard.SeekAlignedToLastTick%2A>: Seeks the storyboard to the specified location.</span></span> <span data-ttu-id="3b1ee-114"><xref:System.Windows.Media.Animation.Storyboard.Seek%2A> メソッドとは異なり、この操作は次のティックの前に処理されます。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-114">Unlike the <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> method, this operation is processed before the next tick.</span></span>

- <span data-ttu-id="3b1ee-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>:ストーリーボードをその保留期間 (ある場合) に進めます。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-115"><xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>: Advances the storyboard to its fill period, if it has one.</span></span>

- <span data-ttu-id="3b1ee-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>:ストーリーボードを停止します。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-116"><xref:System.Windows.Media.Animation.Storyboard.Stop%2A>: Stops the storyboard.</span></span>

<span data-ttu-id="3b1ee-117">次の例では、ストーリーボードを対話的に制御するために、いくつかのストーリーボード メソッドが使用されています。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-117">In the following example, several storyboard methods are used to interactively control a storyboard.</span></span>

> [!NOTE]
> <span data-ttu-id="3b1ee-118">[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でトリガーを使用してストーリーボードを制御する例については、「[開始後のストーリーボードをイベント トリガーを使用して制御する](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b1ee-118">To see an example of controlling a storyboard using triggers with [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], see [Use Event Triggers to Control a Storyboard After It Starts](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md).</span></span>

## <a name="example"></a><span data-ttu-id="3b1ee-119">例</span><span class="sxs-lookup"><span data-stu-id="3b1ee-119">Example</span></span>

[!code-csharp[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ControlStoryboardExample.cs#controlstoryboardexampleusingwholepage)]
[!code-vb[timingbehaviors_procedural_snip#ControlStoryboardExampleUsingWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/controlstoryboardexample.vb#controlstoryboardexampleusingwholepage)]

## <a name="see-also"></a><span data-ttu-id="3b1ee-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b1ee-120">See also</span></span>

- [<span data-ttu-id="3b1ee-121">開始後のストーリーボードをイベント トリガーを使用して制御する</span><span class="sxs-lookup"><span data-stu-id="3b1ee-121">Use Event Triggers to Control a Storyboard After It Starts</span></span>](how-to-use-event-triggers-to-control-a-storyboard-after-it-starts.md)
