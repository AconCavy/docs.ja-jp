---
title: Yield ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Yield
helpviewer_keywords:
- iterators, Yield statement [Visual Basic]
- iterators [Visual Basic]
- Yield statement [Visual Basic]
ms.assetid: f33126c5-d7c4-43e2-8e36-4ae3f0703d97
ms.openlocfilehash: 645b8c4908095bc8d38c47836658325c9b47a569
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615063"
---
# <a name="yield-statement-visual-basic"></a>Yield ステートメント (Visual Basic)
コレクションの次の要素を`For Each...Next`ステートメントに送信します。  
  
## <a name="syntax"></a>構文  
  
```  
Yield expression  
```  
  
## <a name="parameters"></a>パラメーター  
  
|用語|定義|  
|---|---|  
|`expression`|必須。 `Yield`ステートメントを含む反復子メソッドまたは`Get`アクセサーの型に、暗黙的に変換できる式。|  
  
## <a name="remarks"></a>Remarks  
 `Yield`ステートメントは、一度に 1 つのコレクションの要素を返します。 `Yield`ステートメントは、コレクションに対するカスタム イテレーションを実行する反復子メソッドまたは`Get`アクセサーに含まれます。  
  
 [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)または LINQ クエリを使用して、反復子メソッドを使用します。 `For Each`ループの繰り返しごとに反復子メソッドを呼び出します。 反復子メソッドが`Yield` ステートメントに達するときに、`expression`が返され、コードの現在位置が保持されます。 次回、反復子メソッドが呼び出されると、この位置から実行が再開されます。  
  
 `Yield`ステートメントの`expression`の型から、反復子の戻り値の型への、暗黙的な変換が存在する必要があります。  
  
 `Exit Function`または`Return`ステートメントを使用することで、反復を終了できます。  
  
 "Yield"は予約語ではなく、`Iterator`関数または`Get`アクセサー内で使用されている場合にのみ、特別な意味を持ちます。  
  
 反復子メソッドまたは`Get`アクセサーの詳細については、[反復子](../../programming-guide/concepts/iterators.md)を参照してください。  
  
## <a name="iterator-functions-and-get-accessors"></a>反復子関数と Get アクセサー  
 反復子関数の宣言または`Get`アクセサーは、次の要件を満たす必要があります。  
  
- 含める必要があります、[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)修飾子。  
  
- 戻り値の型は、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> であることが必要です。  
  
- いずれかを持つことはできません`ByRef`パラメーター。  
  
 反復子関数は、イベント、インスタンス コンス トラクター、静的コンス トラクターまたは静的デストラクターで発生することはできません。  
  
 反復子関数では、匿名関数を指定できます。 詳細については、「 [反復子](../../programming-guide/concepts/iterators.md)」を参照してください。  
  
## <a name="exception-handling"></a>例外処理  
 A`Yield`内でステートメントを使用できます、`Try`のブロックを[お試しください.キャッチしてください.Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)します。 A`Try`を持つブロックを`Yield`ステートメントを持つことができます`Catch`ブロック、および、持つことができます、`Finally`ブロックします。  
  
 A`Yield`内でステートメントを使用できない、`Catch`ブロックまたは`Finally`ブロックします。  
  
 場合、`For Each`本体 (関数の外側で、反復子)、例外がスロー、`Catch`反復子関数のブロックは実行されませんが、`Finally`反復子関数でのブロックが実行されます。 A`Catch`反復子関数の内側のブロックは、反復子関数内で発生する例外のみをキャッチします。  
  
## <a name="technical-implementation"></a>技術的な実装  
 次のコードを返します、`IEnumerable (Of String)`を反復子関数からの要素を反復処理し、`IEnumerable (Of String)`します。  
  
```vb  
Dim elements As IEnumerable(Of String) = MyIteratorFunction()  
    …  
For Each element As String In elements  
Next  
```  
  
 呼び出し`MyIteratorFunction`関数の本体は実行されません。 この呼び出しでは、`IEnumerable(Of String)` が `elements` 変数に返されます。  
  
 `For Each` ループの反復処理では、<xref:System.Collections.IEnumerator.MoveNext%2A> について `elements` メソッドが呼び出されます。 この呼び出しでは、次の `MyIteratorFunction` ステートメントに到達するまで、`Yield` の本体が実行されます。 `Yield`ステートメントだけでなくの値を決定する式を返します、`element`ループの本体で使用するための変数も、<xref:System.Collections.Generic.IEnumerator%601.Current%2A>これは、要素のプロパティ、`IEnumerable (Of String)`します。  
  
 `For Each` ループの以降の各反復処理では、反復子本体の実行が中断した場所から続行し、`Yield` ステートメントに到達したときに再度停止します。 `For Each`ループが完了するときに、反復子関数の末尾または`Return`または`Exit Function`ステートメントに達する。  
  
## <a name="example"></a>例  
 次の例は、[For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)ループ内に`Yield`ステートメントがあります。 `Main`の[For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md)ステートメント本体の繰り返しごとに、`Power` 反復子メソッドへの呼び出しを作成します。 反復子メソッドを呼び出すごとに、`Yield` ステートメントの次の実行に進みます。これは、`For…Next` ループの次の繰り返しで行われます。  
  
 反復子メソッドの戻り値の型は、反復子インターフェイス型の<xref:System.Collections.Generic.IEnumerable%601>です。 反復子メソッドが呼び出されると、数値の累乗を含む列挙可能なオブジェクトが返されます。  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a>例  
 次の例は、反復子である `Get` アクセサーを示しています。 プロパティ宣言が含まれる、`Iterator`修飾子。  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 その他の例では、次を参照してください。[反復子](../../programming-guide/concepts/iterators.md)します。  
  
## <a name="see-also"></a>関連項目

- [ステートメント](../../../visual-basic/language-reference/statements/index.md)
