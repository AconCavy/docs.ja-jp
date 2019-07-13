---
title: '方法: デザイナーを使用して TreeNode にショートカット メニューを割り当てる'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: 9be633d14429bc2ceda1f0db2ff09252d55d5dd5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59337449"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>方法: デザイナーを使用して TreeNode にショートカット メニューを割り当てる
Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールは、ファイルと Windows オペレーティング システムで Windows エクスプ ローラーの機能の左側のウィンドウに表示されるフォルダーと同様に、ノードの階層を表示します。 設定して、<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>プロパティに提供できる状況依存の操作、ユーザーを右クリックすると、<xref:System.Windows.Forms.TreeView>コントロール。 関連付けることによって、<xref:System.Windows.Forms.ContextMenuStrip>個々 のコンポーネント<xref:System.Windows.Forms.TreeNode>項目のショートカット メニューの機能レベルをカスタマイズを追加することができます、<xref:System.Windows.Forms.TreeView>コントロール。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>デザイン時に TreeNode にショートカット メニューを関連付ける  
  
1. 追加、<xref:System.Windows.Forms.TreeView>をフォームに制御し、ノードを追加し、<xref:System.Windows.Forms.TreeView>に応じて。 詳細については、「[方法 :追加し、削除のノードで、Windows フォーム TreeView コントロール](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)します。  
  
2. 追加、<xref:System.Windows.Forms.ContextMenuStrip>コンポーネントをフォームにし、実行時に使用できるようにするノード レベルの操作を表すショートカット メニューにメニュー項目を追加します。 詳細については、「[方法 :メニュー項目を ContextMenuStrip に追加](how-to-add-menu-items-to-a-contextmenustrip.md)します。  
  
3. もう一度開きます、 **TreeNodeEditor**の ダイアログ ボックス、<xref:System.Windows.Forms.TreeView>制御で、編集、および設定するノードを選択します。 その<xref:System.Windows.Forms.ContextMenuStrip>プロパティを追加したショートカット メニューを。  
  
4. このプロパティが設定されている場合、ノードを右クリックすると、ショートカット メニューが表示されます。  
  
     さらに、処理するコードを記述するが、<xref:System.Windows.Forms.ToolStripItem.Click>これらのメニュー項目のイベント。  
  
## <a name="see-also"></a>関連項目

- [TreeView コントロール](treeview-control-windows-forms.md)
- [TreeView コントロールの概要](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip コントロール](contextmenustrip-control.md)
