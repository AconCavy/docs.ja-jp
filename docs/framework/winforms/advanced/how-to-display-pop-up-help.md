---
title: '方法: ポップアップ ヘルプを表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: bf3bcbff0cd6f3bbf71e96e748cb170d5ce68dfc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211401"
---
# <a name="how-to-display-pop-up-help"></a>方法: ポップアップ ヘルプを表示します。

Windows フォーム上のヘルプを表示する 1 つの方法は、使用、**ヘルプ**を通じてアクセス可能なタイトル バーの右側にあるボタンをクリック、<xref:System.Windows.Forms.Form.HelpButton%2A>プロパティ。 この種類のヘルプの表示は、ダイアログ ボックスでの使用に適しています。 モーダル形式で表示されるダイアログ ボックス (<xref:System.Windows.Forms.Form.ShowDialog%2A> メソッドを使用) は、別のウィンドウにフォーカスを移動するときはモーダル ダイアログ ボックスを閉じる必要があるため、外部のヘルプ システムを起動する場合は問題が発生します。 さらを使用して、**ヘルプ**ボタンがあることが必要ですありません**最小化**ボタンまたは**最大化**タイトル バーに表示されるボタンをクリックします。 フォームは、通常はあるが、これは、標準のダイアログ ボックスの規約では、**最小化**と**最大化**ボタン。

使用することも、<xref:System.Windows.Forms.HelpProvider>ポップアップ ヘルプを実装している場合でものヘルプ システムをファイルへのコントロールをリンクするコンポーネント。 詳細については、次を参照してください。 [Windows アプリケーションでヘルプを提供する](how-to-provide-help-in-a-windows-application.md)します。

## <a name="display-pop-up-help"></a>ポップアップ ヘルプを表示します。

1. Visual Studio で、ドラッグ、 [HelpProvider](../controls/helpprovider-component-windows-forms.md)コンポーネントをツールボックスからフォームにします。

   これは、Windows フォーム デザイナーの下部にあるトレイ内に配置されます。

2. [プロパティ] ウィンドウで、<xref:System.Windows.Forms.Form.HelpButton%2A> プロパティを `true` に設定します。 これで、フォームのタイトル バーの右側に疑問符の付いたボタンが表示されます。

3. <xref:System.Windows.Forms.Form.HelpButton%2A> が表示されるには、フォームの <xref:System.Windows.Forms.Form.MinimizeBox%2A> プロパティと <xref:System.Windows.Forms.Form.MaximizeBox%2A> プロパティを `false` に設定し、<xref:System.Windows.Forms.Form.ControlBox%2A> プロパティを `true` に設定し、<xref:System.Windows.Forms.Form.FormBorderStyle%2A> プロパティを<xref:System.Windows.Forms.FormBorderStyle.FixedSingle>、<xref:System.Windows.Forms.FormBorderStyle.Fixed3D>、<xref:System.Windows.Forms.FormBorderStyle.FixedDialog>、または <xref:System.Windows.Forms.FormBorderStyle.Sizable> のいずれかの値に設定する必要があります。

4. フォーム上のヘルプを表示し、[プロパティ] ウィンドウのヘルプの文字列を設定するコントロールを選択します。 これは、文字列のようなウィンドウに表示されるテキストを[ツールヒント](../controls/tooltip-component-windows-forms.md)します。

5. **F5**キーを押します。

6. キーを押して、**ヘルプ**タイトル バーにボタンをクリックし、ヘルプ文字列を設定するコントロールをクリックします。

## <a name="see-also"></a>関連項目

- [ツールヒントを使用したコントロールのヘルプ](control-help-using-tooltips.md)
- [Windows フォームでのヘルプの統合](integrating-user-help-in-windows-forms.md)
- [Windows フォーム](../index.md)
