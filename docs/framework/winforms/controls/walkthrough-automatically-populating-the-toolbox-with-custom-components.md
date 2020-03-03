---
title: 'チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定'
ms.date: 03/30/2017
helpviewer_keywords:
- IToolboxService interface
- Toolbox [Windows Forms], populating
- custom components [Windows Forms], adding to Toolbox
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
ms.openlocfilehash: 876de650f9c182c0f82a02d1c5b356faa4f7f118
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211154"
---
# <a name="walkthrough-automatically-populating-the-toolbox-with-custom-components"></a>チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定

自動的に表示されます、コンポーネントは現在開いているソリューション内のプロジェクトで定義されている場合、**ツールボックス**操作は必要とします。 手動で設定することができます、**ツールボックス**を使用して、カスタム コンポーネントで、[選択ツールボックス項目 ダイアログ ボックス (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))が、**ツールボックス**を考慮に入れたソリューションの内の項目の次のすべての特性を持つ出力をビルドします。

- 実装<xref:System.ComponentModel.IComponent>;

- <xref:System.ComponentModel.ToolboxItemAttribute>設定`false`;

- <xref:System.ComponentModel.DesignTimeVisibleAttribute>設定`false`します。

> [!NOTE]
> **ツールボックス**ソリューションのプロジェクトで構築されていない項目が表示されないように、参照のチェーンに従わない。

このチュートリアルでは、カスタム コンポーネントを自動的にでの表示方法、**ツールボックス**したら、コンポーネントが構築されます。 このチュートリアルでは、以下のタスクを行います。

- Windows フォーム プロジェクトを作成します。

- カスタム コンポーネントを作成します。

- カスタム コンポーネントのインスタンスを作成します。

- アンロードして、カスタム コンポーネントを再読み込みします。

完了したらが表示されますが、**ツールボックス**は作成したコンポーネントが格納されます。

## <a name="create-the-project"></a>プロジェクトの作成

1. Visual Studio で、という名前の Windows ベースのアプリケーション プロジェクトを作成`ToolboxExample`(**ファイル** > **新規** > **プロジェクト** >  **Visual C#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォームアプリケーション**)。

2. 新しいコンポーネントをプロジェクトに追加します。 このプロジェクトに `DemoComponent`という名前を付けます。

     詳細については、「[方法 :新しいプロジェクト項目の追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w0572c5b(v=vs.100))します。

3. プロジェクトをビルドします。

4. **ツール** メニューのをクリックして、**オプション**項目。 をクリックして**全般**下、 **Windows フォーム デザイナー**いることを確認し、 **AutoToolboxPopulate**にオプションが設定されている**True**します。

## <a name="create-an-instance-of-a-custom-component"></a>カスタム コンポーネントのインスタンスを作成します。

次の手順では、フォームにカスタム コンポーネントのインスタンスを作成します。 **ツールボックス**を自動的に新しいコンポーネントのアカウントは、これは他のコンポーネントまたはコントロールの作成と同じくらい簡単です。

1. プロジェクトのフォームを開き、**フォーム デザイナー**します。

2. **ツールボックス**と呼ばれる新しいタブをクリックします。 **ToolboxExample コンポーネント**します。

     このタブをクリックすると表示されます**と**します。

    > [!NOTE]
    > パフォーマンス上の理由から、コンポーネントの自動設定 領域で、**ツールボックス**カスタムのビットマップを表示しないと、<xref:System.Drawing.ToolboxBitmapAttribute>はサポートされていません。 カスタムのコンポーネントのアイコンを表示する、**ツールボックス**を使用して、**ツールボックス アイテムの選択**コンポーネントの読み込み ダイアログ ボックス。

3. コンポーネントをフォームにドラッグします。

     コンポーネントのインスタンスが作成されに追加、**コンポーネント トレイ**します。

## <a name="unload-and-reload-a-custom-component"></a>アンロードし、カスタム コンポーネントを再読み込み

**ツールボックス**の各コンポーネントの実行アカウントには、プロジェクトが読み込まれ、プロジェクトが読み込まれると、プロジェクトのコンポーネントへの参照を削除します。

1. ソリューションからプロジェクトをアンロードします。

     プロジェクトのアンロードの詳細については、次を参照してください。[方法。アンロードし、プロジェクトの再読み込み](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/tt479x1t(v=vs.100))します。 保存するメッセージが表示されたら、選択**はい**します。

2. 新しい追加**Windows アプリケーション**プロジェクトがソリューションにします。 フォームを開いて、**デザイナー**します。

     **ToolboxExample コンポーネント**前のプロジェクトからのタブがここではなくなっています。

3. 再読み込み、`ToolboxExample`プロジェクト。

     **ToolboxExample コンポーネント** タブのようになりましたが再表示されます。

## <a name="next-steps"></a>次の手順

このチュートリアルで説明する、**ツールボックス**プロジェクトのコンポーネントを考慮に入れたが、**ツールボックス**コントロールになります。 追加と管理プロジェクトをソリューションから削除して、独自のカスタム コントロールを試します。

## <a name="see-also"></a>関連項目

- [一般に、Windows フォーム デザイナー オプション ダイアログ ボックス](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/5aazxs78(v=vs.100))
- [方法: [ツールボックス] タブを操作する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/66kwe227(v=vs.100))
- [[ツールボックス アイテムの選択] ダイアログ ボックス (Visual Studio)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dyca0t6t(v=vs.100))
- [Windows フォームへのコントロールの追加](putting-controls-on-windows-forms.md)
