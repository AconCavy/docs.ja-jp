---
title: '方法: 複合モードを使用してアルファ ブレンドを制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- alpha blending [Windows Forms], compositing
- colors [Windows Forms], blending
- colors [Windows Forms], controlling transparency
ms.assetid: f331df2d-b395-4b0a-95be-24fec8c9bbb5
ms.openlocfilehash: 6863e59efa25323f80933bf8ab595316b430ef53
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590142"
---
# <a name="how-to-use-compositing-mode-to-control-alpha-blending"></a>方法: 複合モードを使用してアルファ ブレンドを制御する
次の特性を持つオフスクリーン ビットマップを作成する場合がある可能性があります。  
  
- 色のアルファ値 255 未満であるがあります。  
  
- 色はいないアルファ ビットマップを作成すると、相互のブレンドです。  
  
- 完成したビットマップを表示する場合、ビットマップの色は、アルファ ブレンドされるディスプレイ デバイスの背景色になります。  
  
 このようなビットマップを作成するには空白を構築<xref:System.Drawing.Bitmap>オブジェクト、および構築し、<xref:System.Drawing.Graphics>オブジェクトに基づくビットマップ。 複合モードの設定、<xref:System.Drawing.Graphics>オブジェクトを<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy?displayProperty=nameWithType>します。  
  
## <a name="example"></a>例  
 次の例では、作成、<xref:System.Drawing.Graphics>オブジェクトに基づいて、<xref:System.Drawing.Bitmap>オブジェクト。 コードを使用して、<xref:System.Drawing.Graphics>と共に半透明ブラシを 2 つのオブジェクト (アルファ = 160) にビットマップを描画します。 コードでは、赤い楕円および半透明ブラシを使用して、緑の楕円を塗りつぶします。 緑色の楕円が赤い楕円、重なっているが、ため、赤、緑がブレンドしないの複合モード、<xref:System.Drawing.Graphics>にオブジェクトが設定されている<xref:System.Drawing.Drawing2D.CompositingMode.SourceCopy>します。  
  
 コードは、ビットマップを描画、画面に 2 回: 白の背景に 1 回と 1 回マルチカラーの背景色。 2 つの楕円の一部であるビットマップのピクセルはあるので、省略記号は、画面の背景色とブレンドされた、160、アルファ コンポーネントです。  
  
 次の図は、コード例の出力を示します。 省略記号がバック グラウンドとブレンドされたが、相互ブレンドしないことに注意してください。  
  
 ![ダイアグラムが表示された楕円はない他のバック グラウンドとブレンドされます。](./media/how-to-use-compositing-mode-to-control-alpha-blending/ellipses-blended-background.png)  
  
 コード例には、このステートメントが含まれています。  
  
 [!code-csharp[System.Drawing.AlphaBlending#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.AlphaBlending#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#41)]  
  
 およびバック グラウンドでブレンドする省略記号を設定する場合は、そのステートメントを次のように変更します。  
  
 [!code-csharp[System.Drawing.AlphaBlending#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#42)]
 [!code-vb[System.Drawing.AlphaBlending#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#42)]  
  
 次の図は、変更後のコードの出力を示します。  
  
 ![省略記号を示す図は、バック グラウンドを使用してまとめてブレンドされます。](./media/how-to-use-compositing-mode-to-control-alpha-blending/blend-ellipses-background.png)  
  
 [!code-csharp[System.Drawing.AlphaBlending#43](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#43)]
 [!code-vb[System.Drawing.AlphaBlending#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#43)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Color.FromArgb%2A>
- [アルファ ブレンドの直線と塗りつぶし](alpha-blending-lines-and-fills.md)
