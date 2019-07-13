---
title: '方法: Windows フォーム TreeView コントロールのアイコンを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: c7c801242c7d5958cce9826a5f60d13a0b257add
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348055"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>方法: Windows フォーム TreeView コントロールのアイコンを設定する
Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールは、各ノードの横にアイコンを表示できます。 アイコンは、ノードのテキストのすぐ左に配置されます。 これらのアイコンを表示するには、ツリー ビューを関連付ける必要があります、<xref:System.Windows.Forms.ImageList>コントロール。 イメージ リストの詳細については、次を参照してください。 [ImageList コンポーネント](imagelist-component-windows-forms.md)と[方法。追加または削除のイメージで、Windows フォームの ImageList コンポーネント](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)します。  
  
> [!NOTE]
>  Microsoft .NET Framework version 1.1 でのバグが表示されないイメージを防止<xref:System.Windows.Forms.TreeView>ノード アプリケーションが呼び出す<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>します。 このバグを回避するには、呼び出す<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>で、`Main`メソッドをすぐに呼び出して<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>します。 このバグは、.NET Framework 2.0 で修正されます。  
  
### <a name="to-display-images-in-a-tree-view"></a>ツリー ビューでイメージを表示するには  
  
1. 設定、<xref:System.Windows.Forms.TreeView>コントロールの<xref:System.Windows.Forms.TreeView.ImageList%2A>プロパティを既存の<xref:System.Windows.Forms.ImageList>を使用するコントロール。  
  
     デザイナーの [プロパティ] ウィンドウまたはコードでは、これらのプロパティを設定できます。  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. ノードの設定<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>と<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>プロパティ。 <xref:System.Windows.Forms.TreeNode.ImageIndex%2A>プロパティは、ノードの標準的な展開の状態に表示されるイメージを決定します。 および<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>プロパティ ノードの選択された状態に表示されるイメージを決定します。  
  
     コードでは、または、TreeNode エディター内で、これらのプロパティを設定できます。 TreeNode エディターを開くには、省略記号ボタンをクリックします。 ( ![。 Visual Studio の [プロパティ] ウィンドウで、省略記号ボタン (…)](./media/visual-studio-ellipsis-button.png)) 横に、 <xref:System.Windows.Forms.TreeView.Nodes%2A> [プロパティ] ウィンドウのプロパティ。  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a>関連項目

- [TreeView コントロールの概要](treeview-control-overview-windows-forms.md)
- [方法: 追加して、Windows フォーム TreeView コントロールでノードを削除](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理します。](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [方法: クリックしてされた TreeView ノードを決定します。](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加します。](add-custom-information-to-a-treeview-or-listview-control-wf.md)
