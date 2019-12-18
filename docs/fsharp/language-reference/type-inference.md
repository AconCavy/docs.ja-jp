---
title: 型の推定
description: コンパイラが値F# 、変数、パラメーター、および戻り値の型を推論する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 4b18c1a67a8b7ddadb4fb334ea4736e9fd29feb0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630188"
---
# <a name="type-inference"></a>型の推定

このトピックでは、F# コンパイラが値、変数、パラメーターおよび戻り値の型を推論する方法について説明します。

## <a name="type-inference-in-general"></a>一般的な型の推定

型の推論という考え方は、F# の構成要素と、コンパイラには、型が推測できません増やした以外の種類を指定する必要はありません。 F# は動的に型指定された言語に、F# での値が所有権が弱い型指定された、明示的な型情報を省略することは限りません。 F#は静的に型指定された言語です。つまり、コンパイラはコンパイル時に各コンストラクトに対して正確な型を推測します。 コンパイラが各コンストラクトの型を推測するのに十分な情報がない場合は、追加の型情報を指定する必要があります。通常は、コードのどこかに明示的な型の注釈を追加します。

## <a name="inference-of-parameter-and-return-types"></a>パラメーターと戻り値の型の推論

パラメーターリストでは、各パラメーターの型を指定する必要はありません。 さらに、 F#は静的に型指定された言語であるため、すべての値と式はコンパイル時に明確な型になります。 明示的に指定しない型については、コンパイラはコンテキストに基づいて型を推測します。 型が指定されていない場合は、ジェネリックであると推論されます。 コードで値が一貫して使用されていない場合、値のすべての使用を満たす1つの推論された型が存在しないようにすると、コンパイラはエラーを報告します。

関数の戻り値の型は、関数内の最後の式の型によって決まります。

たとえば、次のコードでは、 `a`リテラル`100`の型`int`が`b`で`int`あるため、パラメーターの型と戻り値の型はすべて、として推論されます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

リテラルを変更することで、型の推定に影響を与えることができます。 サフィックス`100` `a` `uint32` `b`を追加して`uint32`を作成した場合、、、およびの戻り値の型はと推論されます。 `u`

特定の型のみを使用する関数やメソッドなど、型に制限がある他の構造体を使用して型の推定に影響を与えることもできます。

また、次の例に示すように、関数またはメソッドのパラメーターまたは式の変数に明示的な型の注釈を適用することもできます。 異なる制約の間で競合が発生すると、エラーが発生します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

また、すべてのパラメーターの後に型の注釈を指定することで、関数の戻り値を明示的に指定することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

パラメーターで型の注釈が役立つ一般的なケースは、パラメーターがオブジェクト型で、メンバーを使用する場合です。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a>自動ジェネリック化

関数コードがパラメーターの型に依存していない場合、コンパイラはパラメーターをジェネリックと見なします。 これは*自動汎*化と呼ばれ、複雑さを増すことなく汎用コードを記述するための強力な機能となります。

たとえば、次の関数は、任意の型の2つのパラメーターを組に結合します。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

型は、として推論されます。

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a>追加情報

型の推定については、F# 言語仕様で詳しく説明します。

## <a name="see-also"></a>関連項目

- [自動ジェネリック化](./generics/automatic-generalization.md)