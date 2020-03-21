---
title: '方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112168"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>方法 : キー フレームを使用してカメラの位置および方向をアニメーション化する
次の例では、3D<xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames>シーンでの a の<xref:System.Windows.Media.Media3D.PerspectiveCamera>位置をアニメートするために使用します。 さらに、<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>カメラが 3D シーンで向いている方向をアニメートするために使用されます。 これらのアニメーションはどちらも、一連のアニメーション効果を作成するいくつかのキー フレームを使用します。  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>値<xref:System.Windows.Media.Animation.LinearVector3DKeyFrame>間の滑らかな直線補間を作成するために使用されます。  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>値<xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame>間に突然の「ジャンプ」を作成するために使用されます(補間なし)。  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>プロパティ<xref:System.Windows.Media.Animation.SplineVector3DKeyFrame>に応じて値間の変数遷移を<xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A>作成するために使用されます。 次の例では、アニメーションは低速から開始しますが、時間セグメントの終わりに向かって、指数関数的に高速化します。  
  
## <a name="example"></a>例  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [3D シーンでカメラの位置および方向をアニメーション化する](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [3D グラフィックスの概要](3-d-graphics-overview.md)
