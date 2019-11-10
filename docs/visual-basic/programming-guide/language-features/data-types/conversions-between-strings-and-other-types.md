---
title: 文字列とその他の型との変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 06dabbb5d5dfbfb545f01afb157fd532ca0551df
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197337"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>文字列とその他の型との変換 (Visual Basic)
数値、`Boolean`、または日付/時刻の値を `String` に変換することができます。 文字列の内容が変換先のデータ型の有効な値として解釈される場合は、逆方向 (文字列値から数値、`Boolean`、または `Date`) に変換することもできます。 失敗した場合は、実行時エラーが発生します。  
  
 これらのすべての代入の変換は、どちらの方向でも縮小変換です。 型変換のキーワード (`CBool`、`CByte`、`CDate`、`CDbl`、`CDec`、`CInt`、`CLng`、`CSByte`、`CShort`、`CSng`、0、1 を使用する必要があり 2、3、4)。 <xref:Microsoft.VisualBasic.Strings.Format%2A> 関数と <xref:Microsoft.VisualBasic.Conversion.Val%2A> 関数を使用すると、文字列と数値の間の変換をさらに制御できます。  
  
 クラスまたは構造体を定義している場合は、`String` とクラスまたは構造体の型との間で型変換演算子を定義できます。 詳細については、「 [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)」を参照してください。  
  
## <a name="conversion-of-numbers-to-strings"></a>数値から文字列への変換  
 `Format` 関数を使用すると、数値を書式設定された文字列に変換できます。これには、適切な数字だけでなく、通貨記号 (`$`など)、桁区切り記号、*桁区切り記号*(など) を書式設定することもできます。`,`) と小数点の区切り記号 (`.`など)。 `Format` は、Windows の**コントロールパネル**で指定されている**地域のオプション**の設定に従って、適切なシンボルを自動的に使用します。  
  
 連結 (`&`) 演算子は、次の例に示すように、数値を文字列に暗黙的に変換できることに注意してください。  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>文字列から数値への変換  
 `Val` 関数を使用すると、文字列の数字を数値に明示的に変換できます。 `Val` は、数字、スペース、タブ、ラインフィード、またはピリオド以外の文字が見つかるまで文字列を読み取ります。 シーケンス "& O" と "& H" は、数値システムのベースを変更し、スキャンを終了します。 `Val` の読み取りを停止するまで、適切なすべての文字が数値に変換されます。 たとえば、次のステートメントは `141.825` 値を返します。  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic が文字列を数値に変換する場合、Windows の**コントロールパネル**で指定されている**地域のオプション**の設定を使用して、桁区切り記号、小数点の区切り記号、および通貨記号を解釈します。 つまり、変換は1つの設定では成功しますが、別の設定では成功しない可能性があります。 たとえば、`"$14.20"` は英語 (米国) のロケールでは許容されますが、フランス語のロケールでは使用できません。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic での型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [方法: Visual Basic でオブジェクトを別の型に変換する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [グローバル化およびローカライズされたアプリの開発](/visualstudio/ide/globalizing-and-localizing-applications)
