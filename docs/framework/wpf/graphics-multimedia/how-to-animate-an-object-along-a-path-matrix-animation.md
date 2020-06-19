---
title: '方法: パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452910"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="4b103-102">方法: パスに沿ってオブジェクトをアニメーション化する (行列アニメーション)</span><span class="sxs-lookup"><span data-stu-id="4b103-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="4b103-103">この例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> クラスを使用して、<xref:System.Windows.Media.PathGeometry> で定義したパスに沿ってオブジェクトをアニメーション化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4b103-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b103-104">例</span><span class="sxs-lookup"><span data-stu-id="4b103-104">Example</span></span>  
 <span data-ttu-id="4b103-105">次の例では、以下の処理を実行し、パスに沿ってオブジェクトをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="4b103-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="4b103-106">オブジェクトを移動するために、そのオブジェクトに <xref:System.Windows.Media.MatrixTransform> を適用します。</span><span class="sxs-lookup"><span data-stu-id="4b103-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="4b103-107"><xref:System.Windows.Media.PathGeometry> を使用してパスを定義します。</span><span class="sxs-lookup"><span data-stu-id="4b103-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="4b103-108"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> を作成し、それを使用して <xref:System.Windows.Media.MatrixTransform> の <xref:System.Windows.Media.Matrix> プロパティをアニメーション化します。</span><span class="sxs-lookup"><span data-stu-id="4b103-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="4b103-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> は <xref:System.Windows.Media.PathGeometry> を取得し、それを使用して <xref:System.Windows.Media.Matrix> 値を生成します。</span><span class="sxs-lookup"><span data-stu-id="4b103-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="4b103-110">サンプル全体については、「[パス アニメーションのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b103-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="4b103-111">ジオメトリック パスの詳細については、「[ジオメトリの概要](geometry-overview.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4b103-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b103-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b103-112">See also</span></span>

- [<span data-ttu-id="4b103-113">アニメーションの概要</span><span class="sxs-lookup"><span data-stu-id="4b103-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="4b103-114">パス アニメーションのサンプル</span><span class="sxs-lookup"><span data-stu-id="4b103-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="4b103-115">パス アニメーションに関する「方法」トピック</span><span class="sxs-lookup"><span data-stu-id="4b103-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
