---
title: '方法: ビジュアルからビットマップを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: a622d99f7c477f8654526ed399f1eb37288682fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910261"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a><span data-ttu-id="c2e4a-102">方法: ビジュアルからビットマップを作成する</span><span class="sxs-lookup"><span data-stu-id="c2e4a-102">How to: Create a Bitmap from a Visual</span></span>
<span data-ttu-id="c2e4a-103">この例では、<xref:System.Windows.Media.Visual> からビットマップを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c2e4a-103">This example shows how you can create a bitmap from a <xref:System.Windows.Media.Visual>.</span></span> <span data-ttu-id="c2e4a-104"><xref:System.Windows.Media.DrawingVisual> は <xref:System.Windows.Media.FormattedText> でレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="c2e4a-104">A <xref:System.Windows.Media.DrawingVisual> is rendered with <xref:System.Windows.Media.FormattedText>.</span></span> <span data-ttu-id="c2e4a-105">次に <xref:System.Windows.Media.Visual> は <xref:System.Windows.Media.Imaging.RenderTargetBitmap> にレンダリングされ、所与のテキストのビットマップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c2e4a-105">The <xref:System.Windows.Media.Visual> is then rendered to the <xref:System.Windows.Media.Imaging.RenderTargetBitmap> creating a bitmap of the given text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2e4a-106">例</span><span class="sxs-lookup"><span data-stu-id="c2e4a-106">Example</span></span>  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a><span data-ttu-id="c2e4a-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="c2e4a-107">See also</span></span>

- <xref:System.Windows.Media.DrawingContext>
- [<span data-ttu-id="c2e4a-108">イメージングの概要</span><span class="sxs-lookup"><span data-stu-id="c2e4a-108">Imaging Overview</span></span>](imaging-overview.md)
- [<span data-ttu-id="c2e4a-109">Drawing オブジェクトの概要</span><span class="sxs-lookup"><span data-stu-id="c2e4a-109">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="c2e4a-110">DrawingVisual オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="c2e4a-110">Using DrawingVisual Objects</span></span>](using-drawingvisual-objects.md)
