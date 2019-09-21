---
title: 'チュートリアル: COM オブジェクトを使用した継承の実装 (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 7cbf71d7a2bbd1e94864e785894fdea41d522486
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053332"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>チュートリアル: COM オブジェクトを使用した継承の実装 (Visual Basic)

Visual Basic クラスは、以前の`Public`バージョンの Visual Basic で作成されたものであっても、COM オブジェクトのクラスから派生できます。 COM オブジェクトから継承されたクラスのプロパティとメソッドは、他の基底クラスのプロパティおよびメソッドがオーバーライドまたはオーバーロードできるのと同様にオーバーライドまたはオーバーロードできます。 COM オブジェクトからの継承は、再コンパイルしたくない既存のクラスライブラリがある場合に便利です。

次の手順では、Visual Basic 6.0 を使用して、クラスを含む COM オブジェクトを作成し、それを基底クラスとして使用する方法を示します。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>このチュートリアルで使用する COM オブジェクトをビルドするには

1. Visual Basic 6.0 で、新しい ActiveX DLL プロジェクトを開きます。 という名前`Project1`のプロジェクトが作成されます。 このクラスには、 `Class1`という名前のクラスがあります。

2. **Project Explorer**で、 **[project1]** を右クリックし、 **[project1 のプロパティ]** をクリックします。 **[プロジェクトのプロパティ]** ダイアログボックスが表示されます。

3. **[プロジェクトのプロパティ]** ダイアログボックス`ComObject1`の **[全般**] タブで、プロジェクト **[名]** フィールドに「」と入力してプロジェクト名を変更します。

4. **プロジェクトエクスプローラー**で、を右クリック`Class1`し、 **[プロパティ]** をクリックします。 クラスの **[プロパティ]** ウィンドウが表示されます。

5. プロパティをに`MathFunctions`変更します。 `Name`

6. **プロジェクトエクスプローラー**で、を右クリック`MathFunctions`し、[コードの**表示**] をクリックします。 **コードエディター**が表示されます。

7. プロパティ値を保持するローカル変数を追加します。

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. プロパティ`Let`とプロパティ`Get`プロパティの追加プロシージャ:

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. 関数を追加します。

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. **[ファイル]** メニューの **[ComObject1]** の作成 をクリックして、COM オブジェクトを作成し、登録します。

    > [!NOTE]
    > Visual Basic で作成されたクラスを COM オブジェクトとして公開することもできますが、これは真の COM オブジェクトではなく、このチュートリアルでは使用できません。 詳細については、「 [.NET Framework アプリケーションでの COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)」を参照してください。

## <a name="interop-assemblies"></a>相互運用機能アセンブリ

次の手順では、アンマネージコード (COM オブジェクトなど) と Visual Studio で使用されるマネージコードの間のブリッジとして機能する相互運用機能アセンブリを作成します。 Visual Basic に*よって作成*された相互運用機能アセンブリは、com オブジェクトとの間で移動するときに、パラメーターと戻り値を同等のデータ型にパッケージ化するプロセスなど、com オブジェクトの操作の詳細の多くを処理します。 Visual Basic アプリケーション内の参照は、実際の COM オブジェクトではなく、相互運用機能アセンブリを指します。

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Visual Basic 2005 以降のバージョンで COM オブジェクトを使用するには

1. 新しい Visual Basic Windows アプリケーション プロジェクトを開きます。

2. **[プロジェクト]** メニューの **[参照の追加]** をクリックします。

     **[参照の追加]** ダイアログ ボックスが表示されます。

3. **[COM]** タブで、[ `ComObject1` **コンポーネント名**] ボックスの一覧をダブルクリックし、 **[OK]** をクリックします。

4. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。

     **[新しい項目の追加]** ダイアログ ボックスが表示されます。

5. **[テンプレート]** ペインで、 **[クラス]** をクリックします。

     既定のファイル名`Class1.vb`は、 **[名前]** フィールドに表示されます。 このフィールドを MathClass に変更し、 **[追加]** をクリックします。 これにより、と`MathClass`いう名前のクラスが作成され、そのコードが表示されます。

6. COM クラスを継承するために、 `MathClass`の先頭に次のコードを追加します。

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. に`MathClass`次のコードを追加して、基底クラスのパブリックメソッドをオーバーロードします。

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. に`MathClass`次のコードを追加して、継承されたクラスを拡張します。

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

新しいクラスは、COM オブジェクトの基底クラスのプロパティを継承し、メソッドをオーバーロードして、クラスを拡張する新しいメソッドを定義します。

### <a name="to-test-the-inherited-class"></a>継承されたクラスをテストするには

1. スタートアップフォームにボタンを追加し、それをダブルクリックしてコードを表示します。

2. ボタンの`Click`イベントハンドラープロシージャに次のコードを追加して、の`MathClass`インスタンスを作成し、オーバーロードされたメソッドを呼び出します。

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. F5 キーを押してプロジェクトを実行します。

フォーム`AddNumbers`のボタンをクリックすると、メソッドが最初にデータ型の`Short`数値で呼び出され、Visual Basic によって基本クラスから適切なメソッドが選択されます。 の2回目`AddNumbers`の呼び出しは、からの`MathClass`オーバーロードメソッドに送られます。 3番目の呼び出し`SubtractNumbers`は、クラスを拡張するメソッドを呼び出します。 基本クラスのプロパティが設定され、値が表示されます。

## <a name="next-steps"></a>次の手順

オーバーロード`AddNumbers`された関数は、COM オブジェクトの基底クラスから継承されたメソッドと同じデータ型を持つように見えるかもしれません。 これは、基底クラスのメソッドの引数とパラメーターが Visual Basic 6.0 では16ビット整数として定義されていますが、それ以降のバージョン`Short`の Visual Basic では型の16ビット整数として公開されるためです。 新しい関数は、32ビットの整数を受け取り、基底クラスの関数をオーバーロードします。

COM オブジェクトを使用する場合は、パラメーターのサイズとデータ型を必ず確認してください。 たとえば、引数として Visual Basic 6.0 collection オブジェクトを受け取る COM オブジェクトを使用している場合、Visual Basic の新しいバージョンのコレクションを指定することはできません。

COM クラスから継承されたプロパティとメソッドはオーバーライドできます。つまり、基本 COM クラスから継承されたプロパティまたはメソッドを置き換えるローカルプロパティまたはメソッドを宣言できます。 継承された COM プロパティをオーバーライドするための規則は、次の例外を除き、他のプロパティおよびメソッドをオーバーライドするための規則に似ています。

- COM クラスから継承されたプロパティまたはメソッドをオーバーライドする場合は、継承された他のすべてのプロパティとメソッドをオーバーライドする必要があります。

- パラメーターを使用`ByRef`するプロパティをオーバーライドすることはできません。

## <a name="see-also"></a>関連項目

- [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short データ型](../../../visual-basic/language-reference/data-types/short-data-type.md)
