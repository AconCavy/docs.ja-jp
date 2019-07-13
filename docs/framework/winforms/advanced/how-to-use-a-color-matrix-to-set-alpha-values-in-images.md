---
title: '方法: カラー行列を使用してイメージのアルファ値を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using color matrices for semi-transparent
- transparency [Windows Forms], color matrices
- matrices [Windows Forms], alpha values
- bitmaps [Windows Forms], using color matrices for semi-transparent
ms.assetid: a27121e6-f7e9-4c09-84e2-f05aa9d2a1bb
ms.openlocfilehash: fd63380e04eeb4b7ec7ed7d59032309ea7446507
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593168"
---
# <a name="how-to-use-a-color-matrix-to-set-alpha-values-in-images"></a>方法: カラー行列を使用してイメージのアルファ値を設定する
<xref:System.Drawing.Bitmap>クラス (から継承する、<xref:System.Drawing.Image>クラス) と<xref:System.Drawing.Imaging.ImageAttributes>クラスが取得およびピクセル値を設定するための機能を提供します。 使用することができます、<xref:System.Drawing.Imaging.ImageAttributes>アルファを変更するクラスは、イメージ全体の値または呼び出すことができます、<xref:System.Drawing.Bitmap.SetPixel%2A>のメソッド、<xref:System.Drawing.Bitmap>個々 のピクセル値を変更するクラス。  
  
## <a name="example"></a>例  
 <xref:System.Drawing.Imaging.ImageAttributes>クラスの表示中にイメージの変更に使用できる多くのプロパティがあります。 次の例では、<xref:System.Drawing.Imaging.ImageAttributes>だったの 80% にすべてのアルファ値を設定するオブジェクトを使用します。 これは、カラー行列を初期化し、アルファ 0.8 をマトリックス内の値をスケーリングを設定します。 カラー行列のアドレスが渡される、<xref:System.Drawing.Imaging.ImageAttributes.SetColorMatrix%2A>のメソッド、<xref:System.Drawing.Imaging.ImageAttributes>オブジェクト、および<xref:System.Drawing.Imaging.ImageAttributes>にオブジェクトが渡される、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>オブジェクト。  
  
 レンダリング中には、ビットマップのアルファ値は、元の 80% に変換されます。 これは、結果、画像の背景とブレンドされます。 ビットマップ イメージが透明は次の図では、黒い実線を確認できます。  
  
 ![行列を使用してアルファ ブレンド](./media/image2.png "イメージ 2")  
  
 イメージは、バック グラウンドの白い部分には、イメージを白にブレンドされています。 イメージは、イメージが黒の線と交差する位置黒い色とブレンドされます。  
  
 [!code-csharp[System.Drawing.AlphaBlending#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.AlphaBlending#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
- [アルファ ブレンドの直線と塗りつぶし](alpha-blending-lines-and-fills.md)
