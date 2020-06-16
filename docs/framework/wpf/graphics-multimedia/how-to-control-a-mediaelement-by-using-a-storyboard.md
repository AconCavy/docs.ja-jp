---
title: '方法: ストーリーボードを使用して MediaElement を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
ms.openlocfilehash: ae785e11b1da0f2c408b24021ad46ab071419378
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032233"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a><span data-ttu-id="2b7b9-102">方法: ストーリーボードを使用して MediaElement を制御する</span><span class="sxs-lookup"><span data-stu-id="2b7b9-102">How to: Control a MediaElement by Using a Storyboard</span></span>
<span data-ttu-id="2b7b9-103">この例では、<xref:System.Windows.Media.Animation.Storyboard> で <xref:System.Windows.Media.MediaTimeline> を使用し、<xref:System.Windows.Controls.MediaElement> を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-103">This example shows how to control a <xref:System.Windows.Controls.MediaElement> by using a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b7b9-104">例</span><span class="sxs-lookup"><span data-stu-id="2b7b9-104">Example</span></span>  
 <span data-ttu-id="2b7b9-105"><xref:System.Windows.Media.Animation.Storyboard> で <xref:System.Windows.Media.MediaTimeline> を使用して <xref:System.Windows.Controls.MediaElement> のタイミングを制御するとき、機能は、アニメーションなど、他の <xref:System.Windows.Media.Animation.Timeline> オブジェクトの機能と同じになります。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-105">When you use a <xref:System.Windows.Media.MediaTimeline> in a <xref:System.Windows.Media.Animation.Storyboard> to control the timing of a <xref:System.Windows.Controls.MediaElement>, the functionality is identical to the functionality of other <xref:System.Windows.Media.Animation.Timeline> objects, such as animations.</span></span> <span data-ttu-id="2b7b9-106">たとえば、<xref:System.Windows.Media.MediaTimeline> では、<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> プロパティなどの <xref:System.Windows.Media.Animation.Timeline> プロパティを使用し、<xref:System.Windows.Controls.MediaElement> を起動するタイミングを指定します (メディア再生開始)。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-106">For example, a <xref:System.Windows.Media.MediaTimeline> uses <xref:System.Windows.Media.Animation.Timeline> properties like the <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> property to specify when to start a <xref:System.Windows.Controls.MediaElement> (start media playback).</span></span> <span data-ttu-id="2b7b9-107">また、<xref:System.Windows.Media.Animation.Timeline.Duration%2A> プロパティを使用し、<xref:System.Windows.Controls.MediaElement> がアクティブになる時間を指定します (メディア再生時間)。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-107">It also uses the <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property to specify how long the <xref:System.Windows.Controls.MediaElement> is active (duration of media playback).</span></span> <span data-ttu-id="2b7b9-108"><xref:System.Windows.Media.Animation.Storyboard> で <xref:System.Windows.Media.Animation.Timeline> オブジェクトを使用する方法の詳細については、「[ストーリーボードの概要](storyboards-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-108">For more information about using <xref:System.Windows.Media.Animation.Timeline> objects with a <xref:System.Windows.Media.Animation.Storyboard>, see [Storyboards Overview](storyboards-overview.md).</span></span>  
  
 <span data-ttu-id="2b7b9-109">この例では、<xref:System.Windows.Media.MediaTimeline> を使用して再生を制御する単純なメディア プレーヤーを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-109">This example shows how to create a simple media player that uses a <xref:System.Windows.Media.MediaTimeline> to control playback.</span></span> <span data-ttu-id="2b7b9-110">メディア プレーヤーには、再生、一時停止、再開、停止のボタンがあります。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-110">The media player includes play, pause, resume, and stop buttons.</span></span> <span data-ttu-id="2b7b9-111">プレーヤーにはまた、進行状況バーとして機能する <xref:System.Windows.Controls.Slider> コントロールがあります。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-111">The player also has a <xref:System.Windows.Controls.Slider> control that acts as a progress bar.</span></span>  
  
 <span data-ttu-id="2b7b9-112">次の例では、メディア プレーヤーの [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-112">The following example creates the [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] for the media player.</span></span>  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 <span data-ttu-id="2b7b9-113">次の例では、進行状況バーの機能が作成されます。</span><span class="sxs-lookup"><span data-stu-id="2b7b9-113">The following example creates the functionality for the progress bar.</span></span>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="2b7b9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2b7b9-114">See also</span></span>

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [<span data-ttu-id="2b7b9-115">MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する</span><span class="sxs-lookup"><span data-stu-id="2b7b9-115">Control a MediaElement (Play, Pause, Stop, Volume, and Speed)</span></span>](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [<span data-ttu-id="2b7b9-116">ストーリーボードの概要</span><span class="sxs-lookup"><span data-stu-id="2b7b9-116">Storyboards Overview</span></span>](storyboards-overview.md)
- [<span data-ttu-id="2b7b9-117">キー フレーム アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="2b7b9-117">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="2b7b9-118">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="2b7b9-118">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2b7b9-119">方法トピック</span><span class="sxs-lookup"><span data-stu-id="2b7b9-119">How-to Topics</span></span>](audio-and-video-how-to-topics.md)
- [<span data-ttu-id="2b7b9-120">グラフィックスとマルチメディア</span><span class="sxs-lookup"><span data-stu-id="2b7b9-120">Graphics and Multimedia</span></span>](index.md)
