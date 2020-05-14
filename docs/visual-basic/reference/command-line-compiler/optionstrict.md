---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583076"
---
# <a name="-optionstrict"></a>-optionstrict

厳密な型のセマンティクスが強制され、暗黙的な型変換が制限されます。

## <a name="syntax"></a>構文

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>引数

`+` &#124; `-`  
任意。 `-optionstrict+` オプションは、暗黙的な型変換を制限します。 このオプションの既定値は `-optionstrict-` です。 `-optionstrict+` オプションは `-optionstrict` と同じです。 どちらも制限が少ない型のセマンティクスに使用できます。

`custom`  
必須です。 厳密な言語セマンティクスが守られていないときに警告します。

## <a name="remarks"></a>Remarks

`-optionstrict+` が有効な場合は、拡大型の変換のみを暗黙的に行うことができます。 整数型のオブジェクトへの `Decimal` 型オブジェクトの割り当てなど、暗黙的な縮小の型変換は、エラーとして報告されます。

暗黙的な縮小の型変換に関する警告を生成するには、`-optionstrict:custom` を使用します。 特定の警告を無視するには `-nowarn:numberlist` を使用し、特定の警告をエラーとして扱うには `-warnaserror:numberlist` を使用します。

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE で -optionstrict を設定するには

1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。

2. **[コンパイル]** タブをクリックします。

3. **[Option Strict]** ボックスで値を変更します。

### <a name="to-set--optionstrict-programmatically"></a>-optionstrict をプログラムで設定するには

「[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)」を参照してください。

## <a name="example"></a>例

次のコードでは、厳密な型のセマンティクスを使用して `Test.vb` がコンパイルされます。

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
