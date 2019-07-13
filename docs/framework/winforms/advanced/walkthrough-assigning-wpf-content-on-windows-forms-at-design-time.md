---
title: 'チュートリアル: デザイン時の Windows フォームでの WPF コンテンツの割り当て'
ms.date: 03/30/2017
helpviewer_keywords:
- WPF content [Windows Forms], assigning at design time
- ElementHost control [Windows Forms], assigning WPF content at design time
- interoperability [WPF]
- Windows Forms, content assignments
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: b3e9ef93-7e0f-4a2f-8f1e-3437609a1eb7
ms.openlocfilehash: 09427bfc836f40ca9c7aa76f4904bfe7083bf8dc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211237"
---
# <a name="walkthrough-assign-wpf-content-on-windows-forms-at-design-time"></a>チュートリアル: デザイン時に Windows フォームでの WPF コンテンツを割り当てる

このチュートリアルでは、フォームに表示する Windows Presentation Foundation (WPF) コントロール型を選択する方法について説明します。 プロジェクトに含まれている WPF コントロール型であれば、どれでも選択できます。

このチュートリアルでは次のタスクを実行します。

- プロジェクトを作成する。

- WPF コントロール型を作成する。

- WPF コントロールを選択する。

## <a name="prerequisites"></a>必須コンポーネント

このチュートリアルを完了するには Visual Studio が必要です。

## <a name="create-the-project"></a>プロジェクトの作成

Visual Studio を開き、Visual Basic または Visual で新しい Windows フォーム アプリケーション プロジェクトを作成C#という`SelectingWpfContent`します。

> [!NOTE]
> WPF コンテンツをホストする場合は、C# プロジェクトと Visual Basic プロジェクトのみがサポートされます。

## <a name="create-the-wpf-control-types"></a>WPF コントロール型を作成します。

プロジェクトに追加した WPF コントロール型は、さまざまな <xref:System.Windows.Forms.Integration.ElementHost> コントロール内でホストできます。

## <a name="create-wpf-control-types"></a>WPF コントロール型を作成します。

1. 新しい WPF <xref:System.Windows.Controls.UserControl> プロジェクトをソリューションに追加します。 コントロール型の既定の名前である `UserControl1.xaml` を使用します。 詳細については、「[チュートリアル:デザイン時に Windows フォームで新しい WPF コンテンツを作成する](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)します。

2. デザイン ビューで `UserControl1` が選択されていることを確認します。 詳細については、「[方法 :選択し、デザイン サーフェイス上の要素の移動](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/bb514527(v=vs.100))します。

3. **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`します。

4. 追加、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>への制御、<xref:System.Windows.Controls.UserControl>の値を設定し、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**ホストするコンテンツの**します。

5. WPF <xref:System.Windows.Controls.UserControl> をプロジェクトにもう 1 つ追加します。 コントロール型の既定の名前である `UserControl2.xaml` を使用します。

6. **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティ`200`します。

7. 追加、<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType>への制御、<xref:System.Windows.Controls.UserControl>の値を設定し、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティを**Hosted Content 2**します。

 **注**一般より高度な WPF コンテンツをホストする必要があります。 ここでは、説明する目的でのみ <xref:System.Windows.Controls.TextBox?displayProperty=nameWithType> コントロールを使用しています。

1. プロジェクトをビルドします。

## <a name="select-wpf-controls"></a>WPF コントロールを選択

既にコンテンツをホストしている <xref:System.Windows.Forms.Integration.ElementHost> コントロールに異なる WPF コンテンツを割り当てることができます。

1. Windows フォーム デザイナーで `Form1` を開きます。

2. **ツールボックス**、 をダブルクリックします`UserControl1`のインスタンスを作成する`UserControl1`形式にします。

     
  `UserControl1` のインスタンスは、`elementHost1` という名前の新しい <xref:System.Windows.Forms.Integration.ElementHost> コントロールでホストされます。

3. スマート タグ パネルで`elementHost1`、オープン、**ホストされているコンテンツの選択**ドロップダウン リスト。

4. 選択 **[usercontrol2]** ドロップダウン リスト ボックスから。

     これで、`elementHost1` コントロールが `UserControl2` 型のインスタンスをホストするようになりました。

5. **プロパティ**ウィンドウで、いることを確認、<xref:System.Windows.Forms.Integration.ElementHost.Child%2A>プロパティに設定されて **[usercontrol2]** します。

6. **ツールボックス**の**WPF 相互運用性**グループで、ドラッグ、<xref:System.Windows.Forms.Integration.ElementHost>コントロールをフォームにします。

     新しい名前として、このコントロールの既定である `elementHost2` を使用します。

7. スマート タグ パネルで`elementHost2`、オープン、**ホストされているコンテンツの選択**ドロップダウン リスト。

8. 選択**UserControl1**ドロップダウン リストから。

9. これで、`elementHost2` コントロールが `UserControl1` 型のインスタンスをホストするようになりました。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [移行と相互運用性](../../wpf/advanced/migration-and-interoperability.md)
- [WPF コントロールの使用](using-wpf-controls.md)
- [Visual Studio で XAML をデザインする](/visualstudio/designers/designing-xaml-in-visual-studio)
