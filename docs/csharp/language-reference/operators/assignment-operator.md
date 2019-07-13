---
title: = 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: ef9c9bab5c1cebb06edf934254507180e2197349
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306562"
---
# <a name="-operator-c-reference"></a>= 演算子 (C# リファレンス)

代入演算子 `=` は、右辺オペランドの値を、左辺オペランドに指定された変数、[プロパティ](../../programming-guide/classes-and-structs/properties.md)、または[インデクサー](../../../csharp/programming-guide/indexers/index.md)要素に割り当てます。 代入式の結果は、左辺のオペランドに割り当てられる値です。 右辺のオペランドの型は、左辺のオペランドの型と同じであるか、暗黙に変換できる必要があります。

代入演算子は右結合です。つまり、次の形式の式があるとします。

```csharp
a = b = c
```

これが次のように評価されます。

```csharp
a = (b = c)
```

次の例では、左側のオペランドとしてローカル変数、プロパティ、およびインデクサー要素を使用する代入演算子の使用方法を示します。

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>ref 代入演算子

C# 7.3 以降では、ref 代入演算子 `= ref` を使用して、[ref ローカル](../keywords/ref.md#ref-locals)変数または [ref 読み取り専用ローカル](../keywords/ref.md#ref-readonly-locals)変数を割り当てることができます。 次の例は、ref 代入演算子の使用方法を示しています。

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

ref 代入演算子の場合、その両方のオペランドの型が同じである必要があります。

詳しくは、[機能提案メモ](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)をご覧ください。

## <a name="compound-assignment"></a>複合代入。

2 項演算子 `op` の場合、フォームの複合代入式

```csharp
x op= y
```

上記の式は、次の式と同じです。

```csharp
x = x op y
```

ただし、`x` が評価されるのは 1 回だけです。

複合代入は、[算術](arithmetic-operators.md#compound-assignment)、[ブール論理](boolean-logical-operators.md#compound-assignment)、[ビット単位論理およびシフト](bitwise-and-shift-operators.md#compound-assignment)の各演算子でサポートされています。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

ユーザー定義型は、代入演算子をオーバー ロードできません。 ただし、ユーザー定義型は、別の型への暗黙的な変換を定義できます。 この方法により、ユーザー定義型の値を、別の型の変数、プロパティ、またはインデクサー要素に割り当てることができます。 詳しくは、[implicit](../keywords/implicit.md) キーワードに関する記事をご覧ください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](../language-specification/index.md)の「[Assignment operators (代入演算子)](~/_csharplang/spec/expressions.md#assignment-operators)」セクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# 演算子](index.md)
- [ref キーワード](../keywords/ref.md)
