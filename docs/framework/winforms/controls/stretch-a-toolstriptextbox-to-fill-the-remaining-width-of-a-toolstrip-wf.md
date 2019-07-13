---
title: '方法: Toolstriptextbox (Windows フォーム) にあるコマンド バーの残りの幅を入力するには'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 7a9fd703206caadf2d9c63d92567f8b1c3b51e61
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751421"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>方法: Toolstriptextbox (Windows フォーム) にあるコマンド バーの残りの幅を入力するには
設定すると、<xref:System.Windows.Forms.ToolStrip.Stretch%2A>のプロパティを<xref:System.Windows.Forms.ToolStrip>に制御を`true`コントロールがエンド ツー エンドのコンテナーを入力し、そのコンテナーのサイズ変更時のサイズを変更します。 この構成ですることが有用かもしれませんなど、コントロールの項目を拡張する、<xref:System.Windows.Forms.ToolStripTextBox>空き領域の塗りつぶし、およびコントロールのサイズ変更時にサイズを変更します。 この引き伸ばし役に立ちます、たとえば、外観と Microsoft® Internet Explorer のアドレス バーに似た動作を実現する場合。  
  
## <a name="example"></a>例  
 次のコード例から派生したクラスを提供します。<xref:System.Windows.Forms.ToolStripTextBox>と呼ばれる`ToolStripSpringTextBox`します。 このクラスのオーバーライド、 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> 、親の使用可能な幅を計算するメソッド<xref:System.Windows.Forms.ToolStrip>の他のすべての項目の幅の合計を削除した後に制御します。 このコード例も用意されています。、<xref:System.Windows.Forms.Form>クラスと`Program`クラスの新しい動作を示します。  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [ToolStrip コントロールのアーキテクチャ](toolstrip-control-architecture.md)
- [方法: Statusstrip 内で Spring プロパティを対話的に使用します。](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
