---
title: '方法: フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: d143d7ec87a214a900264e069b329ea28a92c3e9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65590382"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a>方法: フォームとコントロールのダブル バッファリングを行うことによってグラフィックスのちらつきを軽減する
ダブル バッファリングでは、メモリ バッファーを使用して、複数の描画操作に関連するちらつきの問題に対処します。 ダブル バッファリングを有効にすると、すべての描画操作が画面上の描画サーフェイスではなく、最初にメモリ バッファーに描画されます。 描画操作がすべて完了すると、メモリ バッファーが、関連付けられている描画サーフェイスに直接コピーされます。 画面に 1 つだけのグラフィックス操作を実行するため、複雑な描画操作に関連付けられているイメージのちらつきがなくなります。ほとんどのアプリケーションで、既定のダブル バッファリング、.NET Framework によって提供される最良の結果が提供されます。 標準の Windows フォーム コントロールは、既定でバッファリング double です。 既定のダブル バッファリング、フォーム内で有効にすることができ、2 つの方法でコントロールを作成します。 設定するか、<xref:System.Windows.Forms.Control.DoubleBuffered%2A>プロパティを`true`、または呼び出すことができます、<xref:System.Windows.Forms.Control.SetStyle%2A>を設定するメソッド、<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>フラグを`true`します。 どちらの方法は、フォームまたはコントロールのダブル バッファリングを既定値を有効にして、グラフィックスのちらつきのないレンダリングを提供します。 呼び出す、<xref:System.Windows.Forms.Control.SetStyle%2A>メソッドがすべてのレンダリング コードを記述したカスタム コントロールに対してのみお勧めします。  
  
 アニメーションや高度なメモリ管理より高度なダブル バッファリングのシナリオには、独自のダブル バッファリング ロジックを実装できます。 詳細については、「[方法 :バッファリングされたグラフィックスを手動で管理](how-to-manually-manage-buffered-graphics.md)します。  
  
### <a name="to-reduce-flicker"></a>ちらつきを軽減するには  
  
- <xref:System.Windows.Forms.Control.DoubleBuffered%2A> プロパティを `true` に設定します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 \- または -  
  
- 呼び出す、<xref:System.Windows.Forms.Control.SetStyle%2A>を設定するメソッド、<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>フラグを`true`します。  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [ダブル バッファリングされたグラフィックス](double-buffered-graphics.md)
- [Windows フォームにおけるグラフィックスと描画](graphics-and-drawing-in-windows-forms.md)
