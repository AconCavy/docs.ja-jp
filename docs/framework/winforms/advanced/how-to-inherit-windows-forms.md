---
title: '方法: Windows フォームを継承する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 0d8799359a12b9bb64331d83df2500bede8c0ff2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61722967"
---
# <a name="how-to-inherit-windows-forms"></a>方法: Windows フォームを継承する
新規の Windows フォームは、基本フォームから継承して簡単に複製できます。フォームが必要になるたびに、最初から作成し直す必要はありません。  
  
 使用してデザイン時にフォームの継承の詳細については、**継承ピッカー**継承されるコントロールのダイアログ ボックスとのセキュリティ レベルを視覚的に区別する方法は、「[方法。継承ピッカー ダイアログ ボックスを使用してフォームを継承する](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)します。  
  
 **メモ** フォームを継承するには、そのフォームを含むファイルまたは名前空間が実行可能ファイルまたは DLL に組み込まれている必要があります。 プロジェクトをビルドするには、**[ビルド]** メニューの **[ビルド]** を選択します。 また、フォームの継承先となるクラスに、名前空間への参照を追加する必要があります。 実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-inherit-a-form-programmatically"></a>プログラムによってフォームを継承するには  
  
1. クラスに、継承元のフォームを含む名前空間への参照を追加します。  
  
2. クラス定義に、継承元のフォームへの参照を追加します。 参照では、フォームを含んでいる名前空間を指定し、その後にピリオド、続いて基本フォーム自体の名前を指定します。  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 フォームを継承する場合は、イベント ハンドラーが 2 回呼び出されることで問題が発生する可能性があることに注意してください。これは、各イベントが基底クラスと継承クラスの両方によって処理されるためです。 この問題を回避する方法の詳細については、「[Visual Basic で継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Inherits ステートメント](~/docs/visual-basic/language-reference/statements/inherits-statement.md)
- [Imports ステートメント (.NET 名前空間および型)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [using](~/docs/csharp/language-reference/keywords/using.md)
- [基本フォームの外観を変更した場合の影響](effects-of-modifying-base-form-appearance.md)
- [Windows フォームのビジュアルの継承](windows-forms-visual-inheritance.md)
