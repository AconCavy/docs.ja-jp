---
title: Windows フォームの Button コントロールを選択する方法
ms.date: 03/30/2017
helpviewer_keywords:
- Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
ms.openlocfilehash: e511b0d7bcac725ed477678ab4c865f5337e658d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584955"
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Windows フォームの Button コントロールを選択する方法
次の方法で Windows フォームのボタンを選択できます。  
  
- マウスを使用して、ボタンをクリックします。  
  
- 呼び出す、ボタンの<xref:System.Windows.Forms.Control.Click>コード内のイベント。  
  
- TAB キーを押し、ボタンにフォーカスを移動して、ボタンを選択し、space キーまたは ENTER キーを押して。  
  
- ボタンの (ALT + 下線付きの文字) のアクセス キーを押します。 アクセス キーの詳細については、次を参照してください。[方法。Windows フォーム コントロールのアクセス キーを作成](how-to-create-access-keys-for-windows-forms-controls.md)です。  
  
- ボタンがフォームの"accept"ボタンの場合は、ENTER キーを押してボタンを選択、別のコントロールにフォーカスがある場合でも、その他のコントロールが別のボタンや複数行テキスト ボックスでは、enter キーをトラップするカスタム コントロールの場合を除きます。  
  
- 別のコントロールにフォーカスがある場合でも、ESC キーを押してボタンがフォームの「キャンセル」ボタンの場合に、ボタンを選択します。  
  
- 呼び出す、<xref:System.Windows.Forms.Button.PerformClick%2A>メソッドをプログラムで、ボタンを選択します。  
  
## <a name="see-also"></a>関連項目

- [Button コントロールの概要](button-control-overview-windows-forms.md)
- [方法: Windows フォームのボタン クリックに応答するには](how-to-respond-to-windows-forms-button-clicks.md)
- [Button コントロール](button-control-windows-forms.md)
