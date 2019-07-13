---
title: '方法: 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins
- controls [Windows Forms], Margin property
- padding [Windows Forms], Windows Forms
- controls [Windows Forms], Padding property
- controls [Windows Forms], outlining
- Padding property [Windows Forms]
- margins [Windows Forms], Windows Forms
- Margin property [Windows Forms]
ms.assetid: bac7ed4d-a163-4259-98bd-155a36345890
ms.openlocfilehash: e3bbf43dbe45e675df172a6c3e1db16a3ba9caa8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746875"
---
# <a name="how-to-create-a-border-around-a-windows-forms-control-using-padding"></a>方法: 埋め込みを使用して Windows フォーム コントロールの周囲に境界線を作成する
次のコード例に境界線を作成またはに関する概要を説明する方法を示します、<xref:System.Windows.Forms.RichTextBox>コントロール。 例では、設定の値を<xref:System.Windows.Forms.Panel>コントロールの<xref:System.Windows.Forms.Padding>プロパティを 5 に設定、<xref:System.Windows.Forms.Control.Dock%2A>子のプロパティ<xref:System.Windows.Forms.RichTextBox>に制御を<xref:System.Windows.Forms.DockStyle.Fill>します。 <xref:System.Windows.Forms.Control.BackColor%2A>の<xref:System.Windows.Forms.Panel>に設定されているコントロール<xref:System.Drawing.Color.Blue%2A>、青い境界線を作成する<xref:System.Windows.Forms.RichTextBox>コントロール。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.Padding#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Padding/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.Padding#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Padding/VB/Form1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Padding>
- [Windows フォーム コントロールでのマージンと埋め込み](margin-and-padding-in-windows-forms-controls.md)
