---
title: C# 演算子 - C# リファレンス
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 0cd0a06dc919ecf11f1a3d343fe8ff023a5f8524
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609913"
---
# <a name="c-operators-c-reference"></a>C# 演算子 (C# リファレンス)

C# は組み込み型でサポートされている定義済みの演算子を多数提供します。 たとえば、[算術演算子](arithmetic-operators.md)は組み込み数値型のオペランドの算術演算を実行し、[ブール論理演算子](boolean-logical-operators.md)は [bool](../keywords/bool.md) オペランドの論理演算を実行します。

ユーザー定義型は、その型のオペランドに対応する動作を定義する特定の演算子をオーバーロードできます。 詳細については、「[演算子のオーバーロード](operator-overloading.md)」を参照してください。

次のセクションは、C# の演算子を優先順位の高い順に示しています。 各セクションの演算子の優先順位は同じです。

## <a name="primary-operators"></a>主な演算子

優先順位が最も高い演算子です。

[x.y](member-access-operators.md#member-access-operator-) – メンバー アクセス。

[x?.y](member-access-operators.md#null-conditional-operators--and-) – null 条件付きのメンバー アクセス。 左側のオペランドが `null` に評価される場合に `null` を返します。

[x?[y]](member-access-operators.md#null-conditional-operators--and-) - null 条件付き配列要素または型インデクサーのアクセス。 左側のオペランドが `null` に評価される場合に `null` を返します。

[f(x)](member-access-operators.md#invocation-operator-) – メソッドの呼び出しまたはデリゲートの呼び出し。

[a&#91;x&#93;](member-access-operators.md#indexer-operator-) – 配列要素または型インデクサーのアクセス。

[x++](arithmetic-operators.md#increment-operator-) – 後置インクリメント。 x の値を返した後、1 大きくなった (通常は整数 1 が加算された) x の値で格納場所を更新します。

[x--](arithmetic-operators.md#decrement-operator---) – 後置デクリメント。 x の値を返した後、1 小さくなった (通常は整数 1 が減算された) x の値で格納場所を更新します。

[new](new-operator.md) – 型のインスタンス化。

[typeof](type-testing-and-conversion-operators.md#typeof-operator) – オペランドを表す <xref:System.Type> オブジェクトを返します。

[checked](../keywords/checked.md) – 整数演算のオーバーフロー チェックを有効にします。

[unchecked](../keywords/unchecked.md) – 整数演算のオーバーフロー チェックを無効にします。 これがコンパイラの既定の動作です。

[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – 型 T の既定の値を生成します。

[nameof](../keywords/nameof.md) – 変数、型、またはメンバーの単純な (修飾されていない) 名前を定数文字列として取得します。

[Delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – delegate インスタンスを宣言して返します。

[sizeof](../keywords/sizeof.md) – 型オペランドのサイズをバイト単位で返します。

[stackalloc](stackalloc.md) – スタックにメモリ ブロックを割り当てます。

[->](pointer-related-operators.md#pointer-member-access-operator--) – メンバー アクセスと組み合わせてポインターを間接参照します。

## <a name="unary-operators"></a>単項演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[+x](addition-operator.md) – x の値を返します。

[-x](subtraction-operator.md) – 数値の否定。

[\!x](boolean-logical-operators.md#logical-negation-operator-) – 論理否定。

[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – ビットごとの補数。

[++x](arithmetic-operators.md#increment-operator-) – 前置インクリメント。 1 大きくなった (通常は整数 1 が加算された) x の値で格納場所を更新した後に x の値を返します。

[--x](arithmetic-operators.md#decrement-operator---) – 前置デクリメント。 1 小さくなった (通常は整数 1 が減算された) x の値で格納場所を更新した後に x の値を返します。

[(T)x](type-testing-and-conversion-operators.md#cast-operator-) – 型キャスト。

[await](../keywords/await.md) – `Task` を待機します。

[&x](pointer-related-operators.md#address-of-operator-) – 変数のアドレス。

[* x](pointer-related-operators.md#pointer-indirection-operator-) – ポインターの間接参照、または逆参照。

[true 演算子](true-false-operators.md) - オペランドが確実に true であることを示す[ブール](../keywords/bool.md)値 `true` を返します。

[false 演算子](true-false-operators.md) - オペランドが確実に false であることを示す[ブール](../keywords/bool.md)値 `true` を返します。

## <a name="multiplicative-operators"></a>乗算演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x * y](arithmetic-operators.md#multiplication-operator-) – 乗算。

[x / y](arithmetic-operators.md#division-operator-) – 除算。 オペランドが整数の場合、結果は 0 に近い整数になるように切り捨てられます (例: `-7 / 2 is -3`)。

[x % y](arithmetic-operators.md#remainder-operator-) – 剰余。 オペランドが整数の場合、x を y で除算した剰余を返します。  `q = x / y` で `r = x % y` の場合、`x = q * y + r` になります。

## <a name="additive-operators"></a>加法演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x + y](arithmetic-operators.md#addition-operator-) – 加算。

[x – y](arithmetic-operators.md#subtraction-operator--) – 減算。

## <a name="shift-operators"></a>シフト演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – ビットを左へシフトし、右側には 0 を格納します。

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – ビットを右へシフトします。 左側のオペランドが `int` または `long` の場合、左側のビットには符号ビットが格納されます。 左側のオペランドが `uint` または `ulong` の場合、左側のビットには 0 が格納されます。

## <a name="relational-and-type-testing-operators"></a>関係演算子と型検査演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x \< y](comparison-operators.md#less-than-operator-) – より小さい (x が y より小さい場合は true)。

[x > y](comparison-operators.md#greater-than-operator-) – より大きい (x が y より大きい場合は true)。

[x \<= y](comparison-operators.md#less-than-or-equal-operator-) – 以下。

[x >= y](comparison-operators.md#greater-than-or-equal-operator-) – 以上。

[is](type-testing-and-conversion-operators.md#is-operator) – 型の互換性。 評価される左側のオペランドを右側のオペランドで指定された型にキャストできる場合は、`true` を返します。

[as](type-testing-and-conversion-operators.md#as-operator) – 型変換。 左側のオペランドを右側のオペランドで指定された型にキャストして返します。ただし、`(T)x` が例外をスローした場合、`as` は `null` を返します。

## <a name="equality-operators"></a>等値演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x == y](equality-operators.md#equality-operator-) – 等価比較。 既定では、`string` 以外の参照型の場合、参照の等価性を返します (等価テスト)。 ただし、型は `==` をオーバーロードできるため、同一性のテストが目的の場合は `object` で `ReferenceEquals` メソッドを使用することをお勧めします。

[x != y](equality-operators.md#inequality-operator-) – 等しくない。 `==` のコメントを参照してください。 型が `==` をオーバーロードする場合は、`!=` をオーバーロードする必要があります。

## <a name="logical-and-operator"></a>論理 AND 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

`x & y` – `bool` オペランドの場合は[論理 AND](boolean-logical-operators.md#logical-and-operator-)、整数型のオペランドの場合は[ビットごとの論理 AND](bitwise-and-shift-operators.md#logical-and-operator-)。

## <a name="logical-xor-operator"></a>論理 XOR 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

`x ^ y` – `bool` オペランドの場合は[論理 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-)、整数型のオペランドの場合は[ビットごとの論理 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)。

## <a name="logical-or-operator"></a>論理演算子 OR

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

`x | y` – `bool` オペランドの場合は[論理 OR](boolean-logical-operators.md#logical-or-operator-)、整数型のオペランドの場合は[ビットごとの論理 OR](bitwise-and-shift-operators.md#logical-or-operator-)。

## <a name="conditional-and-operator"></a>条件 AND 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – 論理 AND。 `x` が `false` に評価される場合、`y` は評価されません。

## <a name="conditional-or-operator"></a>条件 OR 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – 論理 OR。 `x` が `true` に評価される場合、`y` は評価されません。

## <a name="null-coalescing-operator"></a>Null 合体演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x ?? y](null-coalescing-operator.md) – `x` が `null` 以外の場合は x を返します。null の場合は `y` を返します。

## <a name="conditional-operator"></a>条件演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[t ? x : y](conditional-operator.md) – テスト `t` が true に評価される場合は `x` を評価して返します。それ以外の場合は `y` を評価して返します。

## <a name="assignment-and-lambda-operators"></a>代入演算子とラムダ演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x = y](assignment-operator.md) – 代入。

[x += y](arithmetic-operators.md#compound-assignment) – インクリメント。 `y` の値を `x` の値に加算した結果を `x` に格納し、新しい値を返します。 `x` が[イベント](../keywords/event.md)を指定した場合、`y` は、C# によってイベント ハンドラーとして追加される適切なメソッドである必要があります。

[x -= y](arithmetic-operators.md#compound-assignment) – デクリメント。 `y` の値を `x` の値から減算した結果を `x` に格納し、新しい値を返します。 `x` で[イベント](../keywords/event.md)を指定する場合、`y` は C# によってイベント ハンドラーとして削除される適切なメソッドである必要があります。

[x *= y](arithmetic-operators.md#compound-assignment) – 乗算代入。 `y` の値を `x` の値に乗算した結果を `x` に格納し、新しい値を返します。

[x /= y](arithmetic-operators.md#compound-assignment) – 除算代入。 `x` の値を `y` の値で除算した結果を `x` に格納し、新しい値を返します。

[x %= y](arithmetic-operators.md#compound-assignment) – 剰余代入。 `x` の値を `y` の値で除算した剰余を `x` に格納し、新しい値を返します。

[x &= y](boolean-logical-operators.md#compound-assignment) – AND 代入。 `y` の値と `x` の値の AND 演算を行った結果を `x` に格納し、新しい値を返します。

[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR 代入。 `y` の値と `x` の値の OR 演算を行った結果を `x` に格納し、新しい値を返します。

[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR 代入。 `y` の値と `x` の値の XOR 演算を行った結果を `x` に格納し、新しい値を返します。

[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – 左シフト代入。 `x` の値を `y` で指定した分だけ左へシフトした結果を `x` に格納し、新しい値を返します。

[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – 右シフト代入。 `x` の値を `y` で指定した分だけ右へシフトした結果を `x` に格納し、新しい値を返します。

[=>](lambda-operator.md) – ラムダ宣言。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [演算子](../../programming-guide/statements-expressions-operators/operators.md)
