---
title: デリゲート (Visual Basic) の変性の使用
ms.date: 07/20/2015
ms.assetid: 7b5c20f1-6416-46a3-94b6-f109c31c842c
ms.openlocfilehash: ebba7e862e1b4677d9438aa301ef2b713fba3712
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169065"
---
# <a name="using-variance-in-delegates-visual-basic"></a>デリゲート (Visual Basic) の変性の使用

メソッドをデリゲートに割り当てると、"*共変性*" と "*反変性*" により、デリゲート型をメソッドのシグネチャに柔軟に一致させることができます。 共変性により、メソッドの戻り値の型の派生を、デリゲートに定義されている型よりも強くできます。 また、反変性により、メソッドのパラメーター型の派生をデリゲート型よりも弱くできます。

## <a name="example-1-covariance"></a>例 1:共変性

### <a name="description"></a>説明

この例は、デリゲート シグネチャ内の戻り値の型から派生した戻り値の型を持つメソッドで、デリゲートをどのように使用できるかを示しています。 `DogsHandler` が返すデータ型は `Dogs` です。これは、デリゲートに定義された `Mammals` 型の派生型です。

### <a name="code"></a>コード

```vb
Class Mammals
End Class

Class Dogs
    Inherits Mammals
End Class
Class Test
    Public Delegate Function HandlerMethod() As Mammals
    Public Shared Function MammalsHandler() As Mammals
        Return Nothing
    End Function
    Public Shared Function DogsHandler() As Dogs
        Return Nothing
    End Function
    Sub Test()
        Dim handlerMammals As HandlerMethod = AddressOf MammalsHandler
        ' Covariance enables this assignment.
        Dim handlerDogs As HandlerMethod = AddressOf DogsHandler
    End Sub
End Class
```

## <a name="example-2-contravariance"></a>例 2:反変性

### <a name="description"></a>説明

この例では、型がデリゲートシグネチャパラメーター型の基本型であるパラメーターを持つメソッドで、デリゲートを使用する方法を示します。 反変性により、複数のハンドラーの代わりに単一のイベント ハンドラーを使用できます。 次の例では、2つのデリゲートを使用します。

- [ボタンの](xref:System.Windows.Forms.Control.KeyDown)署名を定義するデリゲート。KeyDown<xref:System.Windows.Forms.KeyEventHandler>イベント。 その署名は次のとおりです。

   ```vb
   Public Delegate Sub KeyEventHandler(sender As Object, e As KeyEventArgs)
   ```

- [MouseClick イベント](xref:System.Windows.Forms.Control.MouseDown)の署名を定義する<xref:System.Windows.Forms.MouseEventHandler>デリゲート。 その署名は次のとおりです。

   ```vb
   Public Delegate Sub MouseEventHandler(sender As Object, e As MouseEventArgs)
   ```

この例では、 <xref:System.EventArgs>パラメーターを使用してイベントハンドラーを定義し、それを使用してイベントと`Button.MouseClick`イベントの`Button.KeyDown`両方を処理します。 これは、が<xref:System.EventArgs> <xref:System.Windows.Forms.KeyEventArgs>と<xref:System.Windows.Forms.MouseEventArgs>の基本型であるためです。

### <a name="code"></a>コード

```vb
' Event handler that accepts a parameter of the EventArgs type.
Private Sub MultiHandler(ByVal sender As Object,
                         ByVal e As System.EventArgs)
    Label1.Text = DateTime.Now
End Sub

Private Sub Form1_Load(ByVal sender As System.Object,
    ByVal e As System.EventArgs) Handles MyBase.Load

    ' You can use a method that has an EventArgs parameter,
    ' although the event expects the KeyEventArgs parameter.
    AddHandler Button1.KeyDown, AddressOf MultiHandler

    ' You can use the same method
    ' for the event that expects the MouseEventArgs parameter.
    AddHandler Button1.MouseClick, AddressOf MultiHandler
End Sub
```

## <a name="see-also"></a>関連項目

- [デリゲートの変性 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
- [Func および Action 汎用デリゲートでの変性の使用 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
