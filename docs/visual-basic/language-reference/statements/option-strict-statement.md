---
title: Option Strict ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: a8466cb0672ccf26717d012bdebb7363f31ebb08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912263"
---
# <a name="option-strict-statement"></a>Option Strict Statement
暗黙的なデータ型変換を拡大変換のみに制限し、遅延バインディングを許可しません。また`Object` 、型の結果となる暗黙的な型指定を許可しません。  
  
## <a name="syntax"></a>構文  
  
```  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`On`|任意。 チェック`Option Strict`を有効にします。|  
|`Off`|任意。 チェック`Option Strict`を無効にします。|  
  
## <a name="remarks"></a>Remarks  
 また`Option Strict On` は`Option Strict`がファイルに含まれている場合、次の条件によってコンパイル時エラーが発生します。  
  
- 暗黙的な縮小変換  
  
- 遅延バインディング  
  
- 結果が `Object` 型となる暗黙の型指定  
  
> [!NOTE]
> [[コンパイル] ページ (プロジェクトデザイナー)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)で設定できる警告構成 (Visual Basic) には、コンパイル時エラーの原因となる3つの条件に対応する3つの設定があります。 これらの設定の使用方法の詳細については、このトピックの「 [IDE で警告構成を設定するに](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions)は」を参照してください。  
  
 ステートメント`Option Strict Off`では、関連する IDE 設定でこれらのエラーまたは警告をオンにするように指定している場合でも、3つの条件すべてについてエラーおよび警告チェックがオフになります。 ステートメント`Option Strict On`は、関連する IDE 設定でこれらのエラーまたは警告をオフにするように指定している場合でも、3つの条件すべてについてエラーおよび警告チェックをオンにします。  
  
 この`Option Strict`ステートメントを使用する場合は、ファイル内の他のコードステートメントの前に記述する必要があります。  
  
 をに`Option Strict` `On`設定すると、Visual Basic によって、すべてのプログラミング要素にデータ型が指定されているかどうかがチェックされます。 データ型は、明示的に指定することも、ローカル型推論を使用して指定することもできます。 次の理由から、すべてのプログラミング要素にデータ型を指定することをお勧めします。  
  
- これにより、変数とパラメーターの IntelliSense サポートが有効になります。 これにより、コードを入力するときに、プロパティとその他のメンバーを表示できます。  
  
- これにより、コンパイラが型チェックを実行できるようになります。 型チェックを使用すると、型変換エラーのために実行時に失敗する可能性があるステートメントを見つけることができます。 また、これらのメソッドをサポートしていないオブジェクトに対するメソッドの呼び出しも識別します。  
  
- これにより、コードの実行速度が向上します。 その理由の1つは、プログラミング要素のデータ型を指定しない場合、Visual Basic コンパイラによって型が`Object`割り当てられることです。 コンパイルされたコードは、と他の`Object`データ型との間で変換を行う必要があるため、パフォーマンスが低下します。  
  
## <a name="implicit-narrowing-conversion-errors"></a>暗黙的な縮小変換エラー  
 縮小変換する暗黙的なデータ型変換がある場合は、暗黙的な縮小変換エラーが発生します。  
  
 Visual Basic は、さまざまなデータ型を他のデータ型に変換できます。 データが失われる可能性があるのは、あるデータ型の値が、精度が低いか、容量が小さいデータ型に変換されたときです。 このような縮小変換が失敗した場合、実行時エラーが発生します。 `Option Strict`これらの縮小変換のコンパイル時通知を使用して、それらを回避できるようにします。 詳細については、「[暗黙的な変換と明示的な変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)」および「拡大変換[と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
 エラーを発生させる可能性のある変換には、式で発生する暗黙的な変換が含まれます。 詳細については、次のトピックを参照してください。  
  
- [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 [& 演算子](../../../visual-basic/language-reference/operators/concatenation-operator.md)を使用して文字列を連結するときに、文字列への変換はすべて拡大変換と見なされます。 そのため、`Option Strict`がオンの場合でも、暗黙的な縮小変換エラーは生成されません。  
  
 対応するパラメーターと異なるデータ型を持つ引数を持つメソッドを呼び出すときに、`Option Strict`がオンの場合は縮小変換がコンパイル時エラーになります。 拡大変換または明示的な変換を使用することで、コンパイル時エラーを回避できます。  
  
 `For Each…Next`のコレクション内の要素からループ コントロール変数への変換では、コンパイル時に暗黙的な縮小変換エラーが抑制されます。 これは`Option Strict`がオンの場合も発生します。 詳細については、[For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)の"縮小変換"セクションを参照してください。  
  
## <a name="late-binding-errors"></a>遅延バインディングエラー  
 `Object` 型として宣言された変数のプロパティまたはメソッドにオブジェクトを代入する場合は、そのオブジェクトは遅延バインディングされます。 詳細については、「[事前バインディングと遅延バインディング](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)」を参照してください。  
  
## <a name="implicit-object-type-errors"></a>暗黙的なオブジェクト型のエラー  
 適切な型が宣言された変数を推論できない場合は暗黙的なオブジェクトの型エラーが発生するため、`Object` の型が推論されます。 これは主に、`As` 句を使用せず、`Option Infer` をオフにして、`Dim` ステートメントを使用して変数を宣言した場合に発生します。 詳細については、「[オプションの推定ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)」および「 [Visual Basic 言語の仕様](../../../visual-basic/reference/language-specification/index.md)」を参照してください。  
  
 メソッドパラメーターの場合、 `As`が off の場合`Option Strict` 、句は省略可能です。 ただし、1つのパラメーターで`As`句を使用する場合は、すべてのパラメーターで句を使用する必要があります。 が`Option Strict` on の場合`As` 、すべてのパラメーター定義に句が必要です。  
  
 `As`句を使用せずに変数を宣言し、に設定`Nothing`すると、 `Object`変数の型はになります。 この場合、が on であり、 `Option Strict` `Option Infer`がオンになっている場合、コンパイル時エラーは発生しません。 たとえば、の`Dim something = Nothing`ようになります。  
  
### <a name="default-data-types-and-values"></a>既定のデータ型と値  
 次の表では、 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)でデータ型と初期化子を指定するさまざまな組み合わせの結果について説明します。  
  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|---|---|---|---|  
|いいえ|いいえ|`Dim qty`|`Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|[はい]|`Dim qty = 5`|`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。 「[ローカル型の推定](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|[はい]|いいえ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 詳細については、「 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)」を参照してください。|  
|[はい]|[はい]|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>Option Strict ステートメントが存在しない場合  
 ソースコードに`Option Strict`ステートメントが含まれていない場合、[[コンパイル] ページ (プロジェクトデザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)の**Option strict**設定が使用されます。 [**コンパイル] ページ**には、エラーを生成する条件をさらに制御するための設定があります。  
  
 コマンドラインコンパイラを使用している場合は、 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラオプションを使用しての`Option Strict`設定を指定できます。  
  
### <a name="to-set-option-strict-in-the-ide"></a>IDE で Option Strict を設定するには  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. **[コンパイル]** タブで、 **[Option Strict]** ボックスの値を設定します。  
  
### <a name="conditions"></a>IDE で警告の構成を設定するには  
 `Option Strict`ステートメントの代わりに [[コンパイル] ページ (プロジェクトデザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用すると、エラーを生成する条件をさらに制御できます。 [**コンパイル] ページ**の [ `Option Strict`警告の**構成**] セクションには、がオンのときにコンパイル時にエラーが発生する3つの条件に対応する設定があります。 これらの設定を次に示します。  
  
- **暗黙的な変換**  
  
- **遅延バインディング、呼び出しが実行時に失敗する可能性があります**  
  
- **暗黙的な型、オブジェクトと見なされます**  
  
 **[Option Strict]** を **[オン]** に設定すると、これら 3 つの警告の構成設定のすべてが **[エラー]** に設定されます。 **[Option Strict]** を **[オフ]** に設定すると、3 つの設定すべてが **[なし]** に設定されます。  
  
 各警告の構成設定を個別に **[なし]** 、 **[警告]** 、または **[エラー]** に変更することができます。 3 つの警告の構成設定がすべて **[エラー]** に設定されている場合、`Option strict` ボックスに `On` が表示されます。 3 つすべてが **[なし]** に設定されている場合、このボックスには `Off` が表示されます。 これらの設定のその他の組み合わせに対しては、 **(カスタム)** が表示されます。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>新しいプロジェクトの Option Strict default 設定を設定するには  
 プロジェクトを作成すると、 **[コンパイル]** タブの**option strict**設定が、 **[オプション]** ダイアログボックスの **[strict]** 設定に設定されます。  
  
 このダイアログ`Option Strict`ボックスでを設定するには、 **[ツール]** メニューの **[オプション]** をクリックします。 **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。 既定では、 **VB**の既定の`Off`設定はです。  
  
### <a name="to-set-option-strict-on-the-command-line"></a>コマンドラインで Option Strict を設定するには  
 **Vbc.exe**コマンドに[/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)コンパイラオプションを含めます。  
  
## <a name="example"></a>例  
 次の例は、縮小変換である暗黙の型変換によって発生するコンパイル時のエラーを示しています。 このカテゴリのエラーは、[**コンパイル] ページ**の**暗黙の変換**条件に対応しています。  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>例  
 次の例は、遅延バインディングによって発生するコンパイル時のエラーを示しています。 このカテゴリのエラーは、遅延バインディングに対応しています。 **コンパイル ページ**の **実行時に呼び出しが失敗する可能性**があります。  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>例  
 次の例では、暗黙的な型`Object`を使用して宣言された変数に起因するエラーを示します。 このカテゴリのエラーは、暗黙的な型に対応しています **。オブジェクト**は、**コンパイルページ**で条件を想定しています。  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>関連項目

- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [方法: オブジェクトのメンバーにアクセスする](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Office ソリューションの遅延バインディング](/visualstudio/vsto/late-binding-in-office-solutions)
- [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
