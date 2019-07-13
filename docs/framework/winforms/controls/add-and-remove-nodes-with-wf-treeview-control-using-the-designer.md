---
title: '方法: デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: 71ada3235343aa7e014e12ebf5b367ec744b00d3
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959663"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>方法: デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する

Windows フォームため<xref:System.Windows.Forms.TreeView>コントロールでは、親ノードに注意する必要がありますノードを追加するときに、階層的な方法でノードを表示します。

次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.TreeView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。

> [!NOTE]
> 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。

### <a name="to-add-or-remove-nodes-in-the-designer"></a>追加またはデザイナーでのノードを削除するには

1. <xref:System.Windows.Forms.TreeView> コントロールを選択します。

2. **プロパティ**ウィンドウで、をクリックして、**省略記号**(![. Visual Studio の [プロパティ] ウィンドウで、省略記号ボタン (…)](./media/visual-studio-ellipsis-button.png)) ボタンの横に、<xref:System.Windows.Forms.TreeView.Nodes%2A>プロパティ.

     **TreeNode エディター**が表示されます。

3. ノードを追加するには、ルート ノードが存在する必要があります。最初にクリックして、ルートを追加する必要がありますいずれかが存在しない場合、**ルートの追加**ボタンをクリックします。 ルートまたは他の任意のノードを選択しをクリックすると子ノードを追加することができますし、**子の追加**ボタンをクリックします。

4. ノードを削除するを削除し、をクリックし、ノードを選択します。、**削除**ボタンをクリックします。

## <a name="see-also"></a>関連項目

- [TreeView コントロール](treeview-control-windows-forms.md)
- [TreeView コントロールの概要](treeview-control-overview-windows-forms.md)
- [方法: Windows フォーム TreeView コントロールのアイコンを設定します。](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理します。](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [方法: クリックしてされた TreeView ノードを決定します。](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加します。](add-custom-information-to-a-treeview-or-listview-control-wf.md)
