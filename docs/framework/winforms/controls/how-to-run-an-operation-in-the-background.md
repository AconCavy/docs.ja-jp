---
title: '方法: バックグラウンドで操作を実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 5b56e2aa-dc05-444f-930c-2d7b23f9ad5b
ms.openlocfilehash: 77f75a7eb1d7cc536df7110ef55727fbdf789f23
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591604"
---
# <a name="how-to-run-an-operation-in-the-background"></a>方法: バックグラウンドで操作を実行する
完了に長い時間がかかる操作を実行しており、ユーザー インターフェイスで遅延が発生しないようにするには<xref:System.ComponentModel.BackgroundWorker> クラスを使用して別のスレッドで操作を実行できます。  
  
 次のコード例は、バック グラウンドで時間のかかる操作を実行する方法を示します。 フォームには、**[開始]** ボタンと **[キャンセル]** ボタンがあります。 非同期操作を実行するには、**[開始]** ボタンをクリックします。 実行中の非同期操作を停止するには、**[キャンセル]** ボタンをクリックします。 各操作の結果は、<xref:System.Windows.Forms.MessageBox> に表示されます。  
  
 Visual Studio では、このタスクに対する広範なサポートが用意されています。  
  
 [チュートリアル: バック グラウンドで操作を実行する](walkthrough-running-an-operation-in-the-background.md)します。  
  
## <a name="example"></a>例  
 [!code-csharp[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.Example#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- System、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [方法: バックグラウンド操作を使用するフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)
- [BackgroundWorker コンポーネント](backgroundworker-component.md)
