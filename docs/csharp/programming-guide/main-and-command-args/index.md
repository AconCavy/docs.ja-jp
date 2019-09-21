---
title: Main() とコマンドライン引数 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: db4464cdd3d98103bbc61b824081b59cb1e01cb9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588908"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() とコマンドライン引数 (C# プログラミング ガイド)

`Main` メソッドは、C# アプリケーションのエントリ ポイントです (ライブラリおよびサービスでは、エントリ ポイントとしての `Main` メソッドは必要ありません)。アプリケーションを起動すると、最初に `Main` メソッドが呼び出されます。

 C# プログラムのエントリ ポイントは 1 つのみです。 `Main` メソッドを持つクラスが 2 つ以上ある場合、プログラムをコンパイルする際に **/main** コンパイラ オプションを使用して、どの `Main` メソッドをエントリ ポイントとして使用するかを指定する必要があります。 詳細については、「[/main (C# コンパイラ オプション)](../../language-reference/compiler-options/main-compiler-option.md)」を参照してください。

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>概要

- `Main` メソッドは実行可能プログラムのエントリ ポイントであり、ここでプログラムの制御を開始および終了します。
- `Main` は、クラスまたは構造体の内部で宣言されます。 `Main` は [static](../../language-reference/keywords/static.md) である必要がありますが、[public](../../language-reference/keywords/public.md) である必要はありません (先ほどの例では、既定の [private](../../language-reference/keywords/private.md) のアクセスを受け取ります)。外側のクラスまたは構造体は、static である必要はありません。
- `Main` の戻り値の型は、`void` または `int` のいずれかになります。C# 7.1 以降では `Task` または `Task<int>` になる場合もあります。
- `Main` で `Task` または `Task<int>` が返される場合に限り、`Main` の宣言に [`async`](../../language-reference/keywords/async.md) 修飾子を含めることができます。 この条件により、`async void Main` メソッドが明確に除外されることに注意してください。
- `Main` メソッドを宣言する際、コマンドライン引数を含む `string[]` パラメーターは指定してもしなくてもかまいません。 Visual Studio を使用して Windows アプリケーションを作成する場合、このパラメーターを手動で追加するか <xref:System.Environment> クラスを使用して、コマンドライン引数を取得できます。 パラメーターは、インデックス 0 のコマンドライン引数として読み取られます。 C や C++ とは異なり、プログラムの名前が最初のコマンドライン引数として扱われることはありません。

コンソール アプリケーションの `Main` で `await` を使用して非同期操作を開始する必要がある場合、戻り値の型 `async`、`Task`、`Task<int>` を追加することでプログラム コードを簡略化できます。

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [csc.exe を使用したコマンド ラインからのビルド](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# プログラミング ガイド](../index.md)
- [メソッド](../classes-and-structs/methods.md)
- [インサイド C# プログラム](../inside-a-program/index.md)
