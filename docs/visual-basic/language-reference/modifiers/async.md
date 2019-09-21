---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 6a3d9c8eb8e5929796683bd0bb50159ca0c69f1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959870"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)
修飾子は、変更するメソッドまたは[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)が非同期であることを示します。 `Async` このようなメソッドを*非同期メソッド*と呼びます。  
  
 非同期メソッドは、呼び出し元のスレッドをブロックすることなく、実行に時間のかかる可能性のある処理を行うことができる、便利な方法です。 非同期メソッドの呼び出し元は、非同期メソッドの完了を待たずに作業を再開できます。  
  
> [!NOTE]
> `Async` キーワードおよび `Await` キーワードは、Visual Studio 2012 で導入されました。 非同期プログラミングの概要については、「 [async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)」を参照してください。  
  
 次の例は、非同期メソッドの構造を示しています。 規則により、非同期メソッドの名前の末尾は "Async" になります。  
  
```vb  
Public Async Function ExampleMethodAsync() As Task(Of Integer)  
    ' . . .  
  
    ' At the Await expression, execution in this method is suspended and,  
    ' if AwaitedProcessAsync has not already finished, control returns  
    ' to the caller of ExampleMethodAsync. When the awaited task is   
    ' completed, this method resumes execution.   
    Dim exampleInt As Integer = Await AwaitedProcessAsync()  
  
    ' . . .  
  
    ' The return statement completes the task. Any method that is   
    ' awaiting ExampleMethodAsync can now get the integer result.  
    Return exampleInt  
End Function  
```  
  
 通常、 `Async`キーワードによって変更されたメソッドには、少なくとも1つの[Await](../../../visual-basic/language-reference/modifiers/async.md)式またはステートメントが含まれています。 メソッドは、最初の `Await` に到達するまで同期的に実行されますが、この時点で、待機していたタスクが完了するまで中断されます。 その間、コントロールはメソッドの呼び出し元に戻されます。 メソッドに `Await` 式またはステートメントが含まれていない場合、メソッドは中断されず、同期メソッドのように実行されます。 `Await` が含まれていない非同期メソッドが存在する場合は、その状態がエラーを示す可能性があるため、コンパイラによって警告が通知されます。 詳細については、「[コンパイラエラー](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md)」を参照してください。  
  
 `Async` キーワードは、予約されていないキーワードです。 メソッドまたはラムダ式を修飾する場合にキーワードとなります。 それ以外の場合は、識別子として解釈されます。  
  
## <a name="return-types"></a>戻り値の型  
 非同期メソッドは、[サブ](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)プロシージャ、または戻り値の型がまたは<xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>の[関数](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)プロシージャです。 メソッドで[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)パラメーターを宣言することはできません。  
  
 メソッドの`Task(Of TResult)` [return](../../../visual-basic/language-reference/statements/return-statement.md)ステートメントに TResult 型のオペランドが含まれている場合は、非同期メソッドの戻り値の型としてを指定します。 メソッドの完了時に意味のある値を返さない場合は、`Task` を使用します。 これにより、メソッドの呼び出しでは `Task` が返されますが、`Task` の完了時に、`Await` を待機している `Task` ステートメントは結果値を生成しません。  
  
 非同期サブルーチンは主として、`Sub` プロシージャが必要なイベント ハンドラーの定義に使用されます。 非同期サブルーチンの呼び出し元は、このサブルーチンを待機できず、このメソッドがスローする例外をキャッチできません。  
  
 使用例を含む詳細については、「[非同期の戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)」をご覧ください。  
  
## <a name="example"></a>例  
 次の例は、非同期のイベント ハンドラー、非同期ラムダ式、および非同期メソッドを示しています。 これらの要素を使用する完全な例に[ついては、「チュートリアル:Async と Await を使用した Web へのアクセス](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)」をご覧ください。 チュートリアル コードは、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)のページからダウンロードできます。  
  
```vb  
' An event handler must be a Sub procedure.  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
    textBox1.Clear()  
    ' SumPageSizesAsync is a method that returns a Task.  
    Await SumPageSizesAsync()  
    textBox1.Text = vbCrLf & "Control returned to button1_Click."  
End Sub  
  
' The following async lambda expression creates an equivalent anonymous  
' event handler.  
AddHandler button1.Click, Async Sub(sender, e)  
                              textBox1.Clear()  
                              ' SumPageSizesAsync is a method that returns a Task.  
                              Await SumPageSizesAsync()  
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."  
                          End Sub  
  
' The following async method returns a Task(Of T).  
' A typical call awaits the Byte array result:  
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")  
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
    ' The downloaded resource ends up in the variable named content.  
    Dim content = New MemoryStream()  
  
    ' Initialize an HttpWebRequest for the current URL.  
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
    ' Send the request to the Internet resource and wait for  
    ' the response.  
    Using response As WebResponse = Await webReq.GetResponseAsync()  
        ' Get the data stream that is associated with the specified URL.  
        Using responseStream As Stream = response.GetResponseStream()  
            ' Read the bytes in responseStream and copy them to content.    
            ' CopyToAsync returns a Task, not a Task<T>.  
            Await responseStream.CopyToAsync(content)  
        End Using  
    End Using  
  
    ' Return the result as a byte array.  
    Return content.ToArray()  
End Function  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Await 演算子](../../../visual-basic/language-reference/operators/await-operator.md)
- [Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)
- [チュートリアル: Async と Await を使用した Web へのアクセス](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
