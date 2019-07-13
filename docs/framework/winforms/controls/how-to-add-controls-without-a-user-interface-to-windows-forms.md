---
title: '方法: ユーザー インターフェイスを持たないコントロールを Windows フォームに追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- NonVisualSelection
helpviewer_keywords:
- invisible controls [Windows Forms]
- Windows Forms controls, adding to form
- controls [Windows Forms], nonvisual
- Windows Forms controls, nonvisual
- nonvisual controls [Windows Forms]
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
ms.openlocfilehash: 49bf927085d29b60c1d9cf5d61df3894495349db
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210413"
---
# <a name="how-to-add-controls-without-a-user-interface-to-windows-forms"></a>方法: ユーザー インターフェイスを持たないコントロールを Windows フォームに追加する

非ビジュアル コントロール (またはコンポーネント) は、アプリケーションに機能を提供します。 他のコントロールとは異なり、コンポーネントは、ユーザーにユーザー インターフェイスを提供しないし、ので、Windows フォーム デザイナー画面に表示する必要はありません。 コンポーネントはフォームに追加するときに、Windows フォーム デザイナーはすべてのコンポーネントが表示されるフォームの下部にあるサイズ変更可能なトレイを表示します。 コントロールがコンポーネント トレイに追加されたら、コンポーネントを選択し、フォーム上の他のコントロールと同様に、そのプロパティを設定することができます。

## <a name="add-a-component-to-a-windows-form"></a>Windows フォームにコンポーネントを追加します。

1. Visual Studio で、フォームを開きます。 詳細については、「[方法: デザイナーで Windows フォームを表示](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w5yd62ts(v=vs.100))します。

2. **ツールボックス**コンポーネントをクリックし、フォームにドラッグします。

     コンポーネントがコンポーネント トレイに表示されます。

さらに、コンポーネントは、実行時にフォームに追加できます。 これは、コンポーネントにはユーザー インターフェイスを持つコントロールとは異なり、ビジュアルの式があるないため、特に一般的なシナリオです。 次の例で、<xref:System.Windows.Forms.Timer>実行時にコンポーネントを追加します。 (Visual Studio には、別のタイマーの数値が含まれています。 この場合は、Windows フォームを使用して、<xref:System.Windows.Forms.Timer>コンポーネント。 Visual Studio の別のタイマーの詳細については、次を参照してください[サーバー ベースのタイマーの概要](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90))。)。

> [!CAUTION]
> コンポーネントには、効果的に機能するコンポーネントに設定する必要がありますコントロールに固有のプロパティが多くの場合があります。 場合、<xref:System.Windows.Forms.Timer>設定する次のコンポーネント、`Interval`プロパティ。 プロジェクトにあるプロパティを設定する、そのコンポーネントに必要なコンポーネントを追加するときにしてください。

## <a name="add-a-component-to-a-windows-form-programmatically"></a>Windows フォームにコンポーネントをプログラムで追加します。

1. インスタンスを作成、<xref:System.Windows.Forms.Timer>コード内のクラス。

2. 設定、`Interval`タイマーのティック間の時間を決定するプロパティ。

3. コンポーネントに必要なその他のプロパティを構成します。

     次のコードの作成を示しています、<xref:System.Windows.Forms.Timer>でその`Interval`プロパティ セット。

    ```vb
    Public Sub CreateTimer()
       Dim timerKeepTrack As New System.Windows.Forms.Timer
       timerKeepTrack.Interval = 1000
    End Sub
    ```

    ```csharp
    public void createTimer()
    {
       System.Windows.Forms.Timer timerKeepTrack = new
           System.Windows.Forms.Timer();
       timerKeepTrack.Interval = 1000;
    }
    ```

    ```cpp
    public:
       void createTimer()
       {
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew
             System::Windows::Forms::Timer();
          timerKeepTrack->Interval = 1000;
       }
    ```

    > [!IMPORTANT]
    > 悪意のあるユーザー コントロールを参照することで、ローカル コンピューターがネットワーク経由のセキュリティ リスクを公開する可能性があります。 誤ってそれをプロジェクトに追加した後に、有害なカスタム コントロールを作成する悪意のあるユーザーの場合の問題のみなります。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [方法: Windows フォームにコントロールを追加します。](how-to-add-controls-to-windows-forms.md)
- [方法: Windows フォームに ActiveX コントロールを追加します。](how-to-add-activex-controls-to-windows-forms.md)
- [方法: Windows フォーム間でコントロールをコピーします。](how-to-copy-controls-between-windows-forms.md)
- [Windows フォームへのコントロールの追加](putting-controls-on-windows-forms.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
