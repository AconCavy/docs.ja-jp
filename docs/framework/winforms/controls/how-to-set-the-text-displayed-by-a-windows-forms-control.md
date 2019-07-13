---
title: '方法: Windows フォーム コントロールによって表示されるテキストを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: 59570af89e6236e3c13866d45dc5361d52b84274
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013089"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>方法: Windows フォーム コントロールによって表示されるテキストを設定する
Windows フォーム コントロールは、通常、コントロールの主な機能に関連するいくつかのテキストを表示します。 たとえば、<xref:System.Windows.Forms.Button> コントロールは、通常、ボタンがクリックされたときにどのようなアクションを実行するかを示すキャプションを表示します。 すべてのコントロールに対して、<xref:System.Windows.Forms.Control.Text%2A> プロパティを使用してテキストを設定または返すことができます。 <xref:System.Windows.Forms.Control.Font%2A> プロパティを使用して、フォントを変更することができます。 また、デザイナーを使用してテキストを設定することもできます。  参照してください[方法。Windows フォーム デザイナーを使用してコントロールのアクセス キーを作成](how-to-create-access-keys-for-windows-forms-controls-using-the-designer.md)、[方法。によって表示されるテキストを設定、Windows フォーム デザイナーを使用してコントロール](how-to-set-the-text-displayed-by-a-windows-forms-control-using-the-designer.md)、[方法。によって表示されるイメージの設定を Windows フォーム デザイナーを使用してコントロール](how-to-set-the-image-displayed-by-a-windows-forms-control-using-the-designer.md)します。  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>コントロールによって表示されるテキストをプログラムで設定するには  
  
1. <xref:System.Windows.Forms.Control.Text%2A> プロパティを文字列に設定します。  
  
     下線付きのアクセス キーを作成するアンパサンドが含まれています (&) は、アクセス キーとなる文字の前にします。  
  
2. <xref:System.Windows.Forms.Control.Font%2A> プロパティを型 <xref:System.Drawing.Font> のオブジェクトに設定します。  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  エスケープ文字を使用すると、メニュー項目など、通常は別の解釈がなされるユーザー インターフェイス要素の特殊文字を表示できます。 たとえば、次のコード行は、メニュー項目のテキストを読み取るを設定します。"& Now For Something まったく異なる"。  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>
- [方法: Windows フォーム コントロールのアクセス キーを作成します。](how-to-create-access-keys-for-windows-forms-controls.md)
- [方法: Windows フォームのボタン クリックに応答するには](how-to-respond-to-windows-forms-button-clicks.md)
