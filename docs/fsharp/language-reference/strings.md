---
title: 文字列
description: "F # の ' string ' 型が Unicode 文字のシーケンスとして不変テキストを表す方法について説明します。"
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812212"
---
# <a name="strings"></a>文字列

この `string` 型は、変更できないテキストを Unicode 文字のシーケンスとして表します。 `string` は .NET の `System.String` の別名です。

## <a name="remarks"></a>注釈

文字列リテラルは引用符 (") で区切られます。 バックスラッシュ文字 ( \\ ) は、特定の特殊文字をエンコードするために使用されます。 円記号と次の文字は、 *エスケープシーケンス*と呼ばれます。 F # の文字列リテラルでサポートされているエスケープシーケンスを次の表に示します。

|文字|エスケープ シーケンス|
|---------|---------------|
|アラート:|`\a`|
|バックスペース|`\b`|
|フォーム フィード|`\f`|
|改行|`\n`|
|キャリッジ リターン|`\r`|
|タブ|`\t`|
|垂直タブ|`\v`|
|円記号|`\\`|
|引用符|`\"`|
|アポストロフィ|`\'`|
|Unicode 文字|`\DDD` (は `D` 10 進数字、000-255 の範囲、 `\231` = "ç" など)|
|Unicode 文字|`\xHH` (は `H` 16 進数の数字、00 ~ FF の範囲、 `\xE7` = "ç" など)|
|Unicode 文字|`\uHHHH` (UTF-16)(は `H` 16 進数の数字、0000 ~ FFFF の範囲を示します。 たとえば、 `\u00E7` = "ç")|
|Unicode 文字|`\U00HHHHHH` (UTF-32)( `H` は16進数字、範囲 000000-10FFFF を示します。 たとえば、 `\U0001F47D` = " 👽 ")|

> [!IMPORTANT]
> `\DDD`エスケープシーケンスは、他のほとんどの言語のような8進数表記ではなく、10進表記です。 したがって、桁数 `8` と `9` は有効であり、のシーケンスは `\032` 空白 (U + 0020) を表しますが、8進数表記では同じコードポイントが使用さ `\040` れます。

> [!NOTE]
> 0-255 (0xFF) の範囲に制限されている場合、とエスケープシーケンスは、実際には、 `\DDD` `\x` 最初の 256 Unicode コードポイントと一致するため、 [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) 文字セットになります。

## <a name="verbatim-strings"></a>逐語的文字列

前に @ 記号が付いている場合、リテラルは逐語的文字列になります。 これは、2つの引用符文字が1つの引用符文字として解釈される点を除いて、すべてのエスケープシーケンスが無視されることを意味します。

## <a name="triple-quoted-strings"></a>三重引用符で囲まれた文字列

さらに、文字列を三重引用符で囲むこともできます。 この場合、二重引用符文字を含め、すべてのエスケープシーケンスが無視されます。 引用符で囲まれた埋め込み文字列を含む文字列を指定するには、逐語的文字列または三重引用符で囲んだ文字列を使用します。 逐語的文字列を使用する場合は、単一引用符文字を示す2つの引用符文字を指定する必要があります。 三重引用符で囲まれた文字列を使用する場合は、文字列の末尾として解析することなく、単一引用符文字を使用できます。 この手法は、XML や、埋め込み引用符を含むその他の構造体を操作する場合に便利です。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

コードでは、改行文字を含む文字列は改行文字として解釈されますが、バックスラッシュ文字が改行前の最後の文字である場合は除きます。 円記号が使用されている場合、次の行の先頭の空白文字は無視されます。 次のコードでは、値を持つ文字列と値を持つ文字列が生成され `str1` `"abc\ndef"` `str2` `"abcdef"` ます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>文字列のインデックス作成とスライス

次のように、配列に似た構文を使用して、文字列内の個々の文字にアクセスできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

出力は `b` になります。

または、次のコードに示すように、配列スライス構文を使用して部分文字列を抽出することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

出力は次のとおりです。

```console
abc
def
```

符号なしバイトの配列 (型) によって ASCII 文字列を表すことができ `byte[]` ます。 文字列リテラルにサフィックスを追加し `B` て、ASCII 文字列であることを示します。 バイト配列で使用される ASCII 文字列リテラルでは、unicode エスケープシーケンスを除き、Unicode 文字列と同じエスケープシーケンスがサポートされます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>文字列演算子

演算子を使用して文字列を `+` 連結し、文字列処理機能 .NET Framework との互換性を維持することができます。 次の例は、文字列の連結を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String クラス

F # の文字列型は実際には .NET Framework 型であるため、 `System.String` すべての `System.String` メンバーを使用できます。 これには、文字列 `+` を連結するために使用される演算子、 `Length` プロパティ、および `Chars` Unicode 文字の配列として文字列を返すプロパティが含まれます。 文字列の詳細については、「」を参照してください `System.String` 。

のプロパティを使用すると、 `Chars` `System.String` 次のコードに示すように、インデックスを指定することにより、文字列内の個々の文字にアクセスできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>文字列モジュール

文字列処理の追加機能は、名前空間のモジュールに含まれてい `String` `FSharp.Core` ます。 詳細については、「 [文字列モジュール](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html)」を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
