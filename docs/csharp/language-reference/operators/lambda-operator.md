---
title: => 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971232"
---
# <a name="-operator-c-reference"></a>=> 演算子 (C# リファレンス)

`=>` トークンは、ラムダ演算子、および式本体の定義におけるメンバー名とメンバー実装の区切り記号という 2 つの形式でサポートされています。

## <a name="lambda-operator"></a>ラムダ演算子

[ラムダ式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)では、ラムダ演算子 `=>` により、左側の入力変数と右側のラムダ本体とが分けられます。

次の例は、メソッド構文で [LINQ](../../programming-guide/concepts/linq/index.md) 機能を使用して、ラムダ式の使用法を示しています。

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

ラムダ式の入力変数は、コンパイル時に厳密に型指定されます。 前の例のように、コンパイラが入力変数の型を推論できる場合は、省型宣言を略できます。 入力変数の型を指定する必要がある場合は、次の例に示すように、変数ごとに指定する必要があります。

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

次の例は、入力変数を含まないラムダ式を定義する方法を示しています。

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

詳細については、「[ラムダ式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。

## <a name="expression-body-definition"></a>式本体の定義

式本体の定義には、次の一般的な構文があります。

```csharp
member => expression;
```

ここで、`expression` には有効な式を指定します。 `expression` の戻り値の型は、メンバーの戻り値の型に暗黙的に変換可能である必要があります。 メンバーの戻り値の型が `void` の場合や、メンバーがコンストラクター、ファイナライザー、またはプロパティ `set` のアクセサーの場合、`expression` は ["*ステートメント式*"](~/_csharplang/spec/statements.md#expression-statements) である必要があります。この場合は任意の型を指定できます。

次の例は、`Person.ToString` メソッドの式本体の定義を示しています。

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

これは、次のメソッド定義の短縮形バージョンです。

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

メソッドおよび読み取り専用プロパティの式本体の定義は、C# 6 以降でサポートされています。 コンストラクター、ファイナライザー、プロパティ アクセサー、およびインデクサーの式本体の定義は、C# 7.0 以降でサポートされています。

詳細については、「[式形式のメンバー](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)」を参照してください。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

`=>` 演算子はオーバーロードできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の[無名関数の式](~/_csharplang/spec/expressions.md#anonymous-function-expressions)に関するセクションを参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# 演算子](index.md)
- [ラムダ式](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [式形式のメンバー](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
