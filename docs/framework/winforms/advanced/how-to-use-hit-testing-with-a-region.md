---
title: '方法: 領域でヒット テストを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [Windows Forms], using regions
- regions [Windows Forms], hit testing
ms.assetid: 3a4c07cb-a40a-4d14-ad35-008f531910a8
ms.openlocfilehash: 136f15f1364fb2aed791b4a61d0f11411b055967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778873"
---
# <a name="how-to-use-hit-testing-with-a-region"></a>方法: 領域でヒット テストを使用する
ヒット テストの目的では、アイコンやボタンなどの特定のオブジェクトの上にカーソルがかどうかを決定します。  
  
## <a name="example"></a>例  
 次の例では、2 つの四角形領域の和集合を形成して十字型の領域を作成します。 ある変数`point`最新のクリックの位置を保持します。 コードを調べますかどうか`point`十字型の領域にします。 ポイントは、リージョン (ヒット) では場合、は、非透過の赤いブラシで領域が入力されます。 それ以外の場合、領域は、半透明の赤いブラシで塗りつぶされます。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.MiscLegacyTopics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Region>
- [GDI+ での領域](regions-in-gdi.md)
- [方法: クリッピング領域を使用します。](how-to-use-clipping-with-a-region.md)
