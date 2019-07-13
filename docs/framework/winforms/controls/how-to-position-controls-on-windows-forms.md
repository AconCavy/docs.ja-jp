---
title: '方法: Windows フォーム上のコントロールを位置設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 241edbe60c327493c9123c6cf7bdc19b7ba2b724
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211649"
---
# <a name="how-to-position-controls-on-windows-forms"></a>方法: Windows フォーム上のコントロールを位置設定する

コントロールの位置、Visual Studio で、Windows フォーム デザイナーを使用するかを指定する、<xref:System.Windows.Forms.Control.Location%2A>プロパティ。

## <a name="position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Windows フォーム デザイナーのデザイン サーフェイス上のコントロールを配置します。

Visual Studio では、マウスを使用して適切な場所にコントロールをドラッグします。

> [!NOTE]
> コントロールを選択しより正確に配置する矢印の付いたがキーに移動します。 また、*スナップ*コントロールをフォームに正確に配置できます。 詳細については、「[チュートリアル:フォームのスナップ線を使用して Windows 上のコントロール](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)します。

## <a name="position-a-control-using-the-properties-window"></a>[プロパティ] ウィンドウを使用して、コントロールを位置します。

1. Visual Studio に移動するコントロールをクリックします。

2. **プロパティ**ウィンドウで、値を入力、<xref:System.Windows.Forms.Control.Location%2A>プロパティ、コントロール コンテナー内の位置をコンマで区切って指定します。

     最初の数値 (X) は、コンテナーの左端からの距離2 番目の数字 (Y) は、ピクセル単位で、コンテナーの領域の上端からの距離です。

    > [!NOTE]
    > 展開することができます、<xref:System.Windows.Forms.Control.Location%2A>プロパティを入力、 **X**と**Y**個別の値します。

## <a name="position-a-control-programmatically"></a>プログラムでコントロールを位置します。

1. 設定、<xref:System.Windows.Forms.Control.Location%2A>するコントロールのプロパティを<xref:System.Drawing.Point>します。

    ```vb
    Button1.Location = New Point(100, 100)
    ```

    ```csharp
    button1.Location = new Point(100, 100);
    ```

    ```cpp
    button1->Location = Point(100, 100);
    ```

2. 変更するコントロールの位置の X 座標を使用して、<xref:System.Windows.Forms.Control.Left%2A>サブプロパティ。

    ```vb
    Button1.Left = 300
    ```

    ```csharp
    button1.Left = 300;
    ```

    ```cpp
    button1->Left = 300;
    ```

## <a name="increment-a-controls-location-programmatically"></a>コントロールの位置をプログラムでインクリメントします。

設定、<xref:System.Windows.Forms.Control.Left%2A>サブプロパティをコントロールの X 座標をインクリメントします。

```vb
Button1.Left += 200
```

```csharp
button1.Left += 200;
```

```cpp
button1->Left += 200;
```

> [!NOTE]
> 使用して、<xref:System.Windows.Forms.Control.Location%2A>コントロールの X と Y を設定するプロパティを同時に配置します。 位置を個別に設定するには、コントロールを使用して、 <xref:System.Windows.Forms.Control.Left%2A> (**X**) または<xref:System.Windows.Forms.Control.Top%2A>(**Y**) サブプロパティ。 座標 X と Y 座標を暗黙的に設定しないで、<xref:System.Drawing.Point>この構造体には、ボタンの座標のコピーが含まれているため、ボタンの場所を表す構造体です。

## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [チュートリアル: スナップ線を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [チュートリアル: TableLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [チュートリアル: FlowLayoutPanel を使用して Windows フォーム コントロールの配置](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
- [方法: Windows フォームの画面位置を設定します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/52aha046(v=vs.100))
