---
title: "'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます"
ms.date: 07/20/2015
f1_keywords:
- bc36550
- vbc36550
helpviewer_keywords:
- BC36550
ms.assetid: 4387a51f-733c-45d7-abdb-eb64d4f51078
ms.openlocfilehash: 2ed3a10cdf941bb8d1d7c00379736e04e8cad4d7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583179"
---
# <a name="extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations"></a>'Extension' 属性は 'Module'、'Sub'、または 'Function' の各宣言にのみ適用できます

Visual Basic でデータ型を拡張する唯一の方法は、標準モジュール内で拡張メソッドを定義することです。 拡張メソッドになるのは、`Sub` プロシージャまたは `Function` プロシージャです。 すべての拡張メソッドは、<xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 名前空間の拡張属性 `<Extension()>` でマークする必要があります。 必要に応じて、拡張メソッドを含むモジュールを同じ方法でマークすることもできます。 その他の拡張属性の使用は有効ではありません。

**エラー ID:** BC36550

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 拡張属性を削除します。

- それを囲むモジュールに定義されているメソッドとして拡張機能を再設計します。

## <a name="example"></a>例

`String` データ型の `Print` メソッドを定義する例を次に示します。

```vb
Imports StringUtility
Imports System.Runtime.CompilerServices
Namespace StringUtility
    <Extension()>
    Module StringExtensions
        <Extension()>
        Public Sub Print (ByVal str As String)
            Console.WriteLine(str)
        End Sub
    End Module
End Namespace
```

## <a name="see-also"></a>関連項目

- [属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)
- [Module ステートメント](../../../visual-basic/language-reference/statements/module-statement.md)
