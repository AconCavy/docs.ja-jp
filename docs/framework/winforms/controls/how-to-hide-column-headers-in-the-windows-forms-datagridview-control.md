---
title: '方法: Windows フォーム DataGridView コントロールの列ヘッダーを非表示にする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: 888ff59d42f44db652d3188e016b9e10a9590139
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651669"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a>方法: Windows フォーム DataGridView コントロールの列ヘッダーを非表示にする
表示することもありますが、<xref:System.Windows.Forms.DataGridView>列ヘッダーのないです。 <xref:System.Windows.Forms.DataGridView>コントロール、<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>プロパティの値が列ヘッダーを表示するかどうかを判断します。  
  
### <a name="to-hide-the-column-headers"></a>列ヘッダーを非表示にするには  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> プロパティを `false` に設定します。  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- `dataGridView1` という名前の <xref:System.Windows.Forms.DataGridView> コントロール。  
  
- <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでの列、行、およびセルの基本機能](basic-column-row-and-cell-features-wf-datagridview-control.md)
