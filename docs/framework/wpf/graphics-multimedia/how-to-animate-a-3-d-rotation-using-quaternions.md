---
title: '方法: 四元数を使用して 3-D 回転をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: d994ac2ae67fd366f27f123d5bd15f14d5ac7abe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762125"
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a>方法: 四元数を使用して 3-D 回転をアニメーション化する
この例では、四元数を使用して 3-D オブジェクトの回転をアニメーション化する方法を示します。  
  
 次のコードを<xref:System.Windows.Media.Media3D.QuaternionRotation3D>の値として使用される、<xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A>のプロパティを<xref:System.Windows.Media.Media3D.RotateTransform3D>します。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 これは、<xref:System.Windows.Media.Media3D.QuaternionRotation3D>をアニメーション化は、<xref:System.Windows.Media.Animation.QuaternionAnimation>内で、<xref:System.Windows.Media.Animation.Storyboard>次のコードを使用して。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>例  
 次のコードでは、全体のサンプルを示します。  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [3-D シーンを作成する](how-to-create-a-3-d-scene.md)
- [3-D グラフィックスの概要](3-d-graphics-overview.md)
- [変換の概要](transforms-overview.md)
- [ストーリーボードを使用して 3-D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Rotation3DAnimation を使用して 3-D 回転をアニメーション化する](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
