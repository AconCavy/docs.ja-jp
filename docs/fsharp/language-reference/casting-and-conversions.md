---
title: キャストと変換
description: さまざまなプリミティブF#型間の算術変換のための変換演算子をプログラミング言語がどのように提供するかについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630432"
---
# <a name="casting-and-conversions-f"></a>キャストと変換 (F#)

このトピックでは、F# の型変換のサポートについて説明します。

## <a name="arithmetic-types"></a>算術型

F#整数型と浮動小数点型の間など、さまざまなプリミティブ型間の算術変換のための変換演算子を提供します。 整数および文字の変換演算子は、チェックされたフォームと unchecked 形式を持っています。浮動小数点演算子と`enum`変換演算子では実行されません。 チェックを行わないフォームは`Microsoft.FSharp.Core.Operators`で定義され、チェックさ`Microsoft.FSharp.Core.Operators.Checked`れたフォームはで定義されます。 結果の値が対象の型の制限を超えた場合に、チェックされたフォームがオーバーフローをチェックし、ランタイム例外を生成します。

これらの各演算子には、変換先の型の名前と同じ名前が付けられています。 たとえば、次のコードでは、型に明示的に注釈`byte`が付けられているので、2つの異なる意味を持つが表示されます。 最初の出現は型で、2番目は変換演算子です。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

次の表では、F# で定義された変換演算子を示します。

|演算子|説明|
|--------|-----------|
|`byte`|8ビットの符号なしの型である byte に変換します。|
|`sbyte`|符号付きバイトに変換します。|
|`int16`|16ビット符号付き整数に変換します。|
|`uint16`|16ビット符号なし整数に変換します。|
|`int32, int`|32ビット符号付き整数に変換します。|
|`uint32`|32ビット符号なし整数に変換します。|
|`int64`|64ビット符号付き整数に変換します。|
|`uint64`|64ビット符号なし整数に変換します。|
|`nativeint`|ネイティブの整数に変換します。|
|`unativeint`|符号なしのネイティブ整数に変換します。|
|`float, double`|64ビットの倍精度 IEEE 浮動小数点数に変換します。|
|`float32, single`|32ビットの単精度 IEEE 浮動小数点数に変換します。|
|`decimal`|をに`System.Decimal`変換します。|
|`char`|Unicode 文字`System.Char`に変換します。|
|`enum`|列挙型に変換します。|

組み込みのプリミティブ型に加えて、適切なシグネチャを持つメソッドまたは`op_Explicit` `op_Implicit`メソッドを実装する型でこれらの演算子を使用できます。 たとえば、変換演算子`int`は、型をパラメーターとして受け取り、を`op_Explicit`返す`int`静的メソッドを提供する任意の型で動作します。 メソッドが戻り値の型によってオーバーロードできないことを示す一般的な規則の特別な例外`op_Explicit`と`op_Implicit`して、およびに対してこれを行うことができます。

## <a name="enumerated-types"></a>列挙型

演算子は、変換先の型を表す1つ`enum`の型パラメーターを受け取る汎用演算子です。 `enum` 列挙型に変換すると、型推論は、 `enum`変換先のの型を決定しようとします。 次の例では、変数`col1`に明示的に注釈が付けられていませんが、その型は後の等値テストから推論されます。 したがって、コンパイラは、 `Color`列挙型に変換していることを推測できます。 または、次の例のよう`col2`に、型の注釈を指定することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

次のコードのように、ターゲットの列挙型を明示的に型パラメーターとして指定することもできます。

```fsharp
let col3 = enum<Color> 3
```

列挙キャストは、列挙型の基になる型が変換される型と互換性がある場合にのみ機能します。 次のコードでは、と`int32` `uint32`の間に不一致があるため、変換に失敗します。

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

詳細については、「[列挙型](enumerations.md)」を参照してください。

## <a name="casting-object-types"></a>キャスト (オブジェクト型を)

オブジェクト階層内の型間の変換は、オブジェクト指向プログラミングの基本となります。 変換には、キャスト (キャスト) とキャストダウン (ダウンキャスト) の2つの基本的な種類があります。 階層をキャストすることは、派生オブジェクト参照からベースオブジェクト参照へのキャストを意味します。 このようなキャストは、基底クラスが派生クラスの継承階層内にある限り、確実に動作します。 基底オブジェクト参照から派生オブジェクト参照への階層のキャストは、オブジェクトが実際には正しい宛先 (派生) 型のインスタンスであるか、または変換先の型から派生した型である場合にのみ成功します。

F#は、これらの種類の変換のための演算子を提供します。 演算子`:>`は階層をキャストし、演算子は`:?>`階層を下位にキャストします。

### <a name="upcasting"></a>キャスト

多くのオブジェクト指向言語でキャストは暗黙の型です。F# では、規則が若干異なります。 キャストは、オブジェクト型のメソッドに引数を渡すときに自動的に適用されます。 ただし、モジュール内の let バインド関数の場合、パラメーターの型が柔軟な型として宣言されていない限り、キャストは自動ではありません。 詳細については、「[柔軟な型](flexible-Types.md)」を参照してください。

演算子`:>`は静的なキャストを実行します。これは、キャストの成功がコンパイル時に決定されることを意味します。 を使用`:>`するキャストが正常にコンパイルされた場合、それは有効なキャストであり、実行時にエラーが発生する可能性はありません。

このような変換を`upcast`実行するために演算子を使用することもできます。 次の式では、階層の上位変換が指定されています。

```fsharp
upcast expression
```

アップキャスト演算子を使用すると、コンパイラはコンテキストから変換先の型を推論しようとします。 コンパイラがターゲットの型を判断できない場合、コンパイラはエラーを報告します。

### <a name="downcasting"></a>ダウンキャスト

演算子`:?>`は動的キャストを実行します。これは、キャストの成功が実行時に決定されることを意味します。 `:?>`演算子を使用するキャストはコンパイル時にはチェックされませんが、実行時には指定された型にキャストしようとしました。 オブジェクトがターゲット型と互換性がある場合、キャストは成功します。 オブジェクトがターゲット型と互換性がない場合、ランタイムはを`InvalidCastException`発生させます。

また、演算子を使用`downcast`して、動的な型変換を実行することもできます。 次の式は、階層の下位への変換を、プログラムコンテキストから推論される型に指定します。

```fsharp
downcast expression
```

`upcast`演算子の場合と同様に、コンパイラがコンテキストから特定のターゲット型を推論できない場合は、エラーが報告されます。

次のコードは、演算子`:>`と`:?>`演算子の使用方法を示しています。 このコードは、変換`:?>`が成功したことがわかっている場合に、変換が失敗`InvalidCastException`した場合にスローされるため、演算子が最適に使用されることを示しています。 変換が成功したことがわからない場合は、例外を生成するオーバーヘッド`match`が回避されるため、式を使用する型テストの方が適しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

ジェネリック演算子`downcast`とは`upcast`型の推定に依存して引数と戻り値の型を決定するため、上記のコードでは、

```fsharp
let base1 = d1 :> Base1
```

代入

```fsharp
let base1 = upcast d1
```

前のコードでは、引数の型と戻り値`Derived1`の`Base1`型はそれぞれとになります。

型テストの詳細については、「 [Match 式](match-Expressions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)