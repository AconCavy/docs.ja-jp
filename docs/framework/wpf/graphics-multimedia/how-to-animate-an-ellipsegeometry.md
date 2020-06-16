---
title: '方法: EllipseGeometry をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], EllipseGeometry objects [WPF]
- EllipseGeometry objects [WPF], animating
- graphics [WPF], animation
ms.assetid: 767b9b6e-9cb7-482e-b6c2-fee7750c3995
ms.openlocfilehash: 0f8174a2144435c9ad65904ee587355e8b38e935
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760923"
---
# <a name="how-to-animate-an-ellipsegeometry"></a><span data-ttu-id="18a5b-102">方法: EllipseGeometry をアニメーション化する</span><span class="sxs-lookup"><span data-stu-id="18a5b-102">How to: Animate an EllipseGeometry</span></span>
<span data-ttu-id="18a5b-103">この例では、<xref:System.Windows.Shapes.Path> 要素内で <xref:System.Windows.Media.Geometry> をアニメーション化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="18a5b-103">This example shows how to animate a <xref:System.Windows.Media.Geometry> within a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="18a5b-104">次の例では、<xref:System.Windows.Media.Animation.PointAnimation> は <xref:System.Windows.Media.EllipseGeometry> の <xref:System.Windows.Media.EllipseGeometry.Center%2A> をアニメーション化するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="18a5b-104">In the following example, a <xref:System.Windows.Media.Animation.PointAnimation> is used to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> of an <xref:System.Windows.Media.EllipseGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a5b-105">例</span><span class="sxs-lookup"><span data-stu-id="18a5b-105">Example</span></span>  
 [!code-xaml[animatepath_snip_XAML#1](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip_XAML/CS/EllipseGeometryExample.xaml#1)]  
  
 [!code-csharp[animatepath_snip#101](~/samples/snippets/csharp/VS_Snippets_Wpf/animatepath_snip/CSharp/EllipseGeometryExample.cs#101)]  
  
 [!code-vb[animatepath_snip#201](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animatepath_snip/VisualBasic/EllipseGeometryExample.vb#201)]  
  
## <a name="see-also"></a><span data-ttu-id="18a5b-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="18a5b-106">See also</span></span>

- [<span data-ttu-id="18a5b-107">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="18a5b-107">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="18a5b-108">ジオメトリの概要</span><span class="sxs-lookup"><span data-stu-id="18a5b-108">Geometry Overview</span></span>](geometry-overview.md)
