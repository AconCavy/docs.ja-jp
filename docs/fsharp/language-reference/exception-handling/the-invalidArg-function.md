---
title: 例外:invalidArg 関数
description: "' Invalidarg F# ' 関数が引数の例外を生成する方法について説明します。"
ms.date: 05/16/2016
ms.openlocfilehash: 6b1c5fdb5a541da336977d3a67d471302edb36b6
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083011"
---
# <a name="exceptions-the-invalidarg-function"></a>例外:invalidArg 関数

関数`invalidArg`は、引数の例外を生成します。

## <a name="syntax"></a>構文

```fsharp
invalidArg parameter-name error-message-string
```

## <a name="remarks"></a>Remarks

前の構文のパラメーター名は、引数が無効であるパラメーターの名前を含む文字列です。 *エラーメッセージ文字列*は、リテラル文字列または型`string`の値です。 これは、 `Message` exception オブジェクトのプロパティになります。

によって`invalidArg`生成される`System.ArgumentException`例外は例外です。 次の`invalidArg`コードは、を使用して例外をスローする方法を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6101.fs)]

出力は次のようになり、その後にスタックトレース (表示されません) が続きます。

```console
December
January
System.ArgumentException: Month parameter out of range.
```

## <a name="see-also"></a>関連項目

- [例外処理](index.md)
- [例外の種類](exception-types.md)
- [例外: `try...with`式](the-try-with-expression.md)
- [例外: `try...finally`式](the-try-finally-expression.md)
- [例外: `raise` 関数](the-raise-function.md)
- [例外: `failwith`関数](the-failwith-function.md)
