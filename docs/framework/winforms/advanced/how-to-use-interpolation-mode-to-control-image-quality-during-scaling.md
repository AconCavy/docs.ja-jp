---
title: '方法: 補間モードを使用してスケーリング時の画質を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: ab0ff93b3ee26467c0de448efd31b698167f95c2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505715"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>方法: 補間モードを使用してスケーリング時の画質を制御する
補間モードを<xref:System.Drawing.Graphics>オブジェクトの方法で構成される GDI + 拡張 (拡大および縮小) イメージに影響を与えます。 <xref:System.Drawing.Drawing2D.InterpolationMode>列挙型は、次のリストに表示される一部のいくつかの補間モードを定義します。  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 イメージを拡大するには、元のイメージ内の各ピクセルは大きいイメージのピクセルのグループにマップする必要があります。 イメージを縮小するには、小さいイメージの 1 つのピクセルに、元のイメージのピクセルのグループをマップする必要があります。 これらのマッピングを実行するアルゴリズムの効果は、スケーリングされたイメージの品質を決定します。 高品質な拡大縮小されたイメージを生成するアルゴリズムは、処理時間を必要とする傾向があります。 上記の一覧で<xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>最低の品質のモードと<xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>は最高品質のモードです。  
  
 補間モードを設定するには、メンバーのいずれかを割り当てる、<xref:System.Drawing.Drawing2D.InterpolationMode>列挙体を<xref:System.Drawing.Graphics.InterpolationMode%2A>のプロパティを<xref:System.Drawing.Graphics>オブジェクト。  
  
## <a name="example"></a>例  
 次の例では、イメージを描画し、3 つの異なる補間モードを使用してイメージが圧縮されます。  
  
 次の図は、元のイメージと 3 つの小さいイメージを示します。  
  
 ![さまざまな補間設定を使用してイメージを示すスクリーン ショット。](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。  
  
## <a name="see-also"></a>関連項目

- [イメージ、ビットマップ、メタファイル](images-bitmaps-and-metafiles.md)
- [イメージ、ビットマップ、アイコン、およびメタファイルの操作](working-with-images-bitmaps-icons-and-metafiles.md)
