---
title: "'ReDim' では最も右にある次元のみ変更できます"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 584370f356180fe8b1710a9e145018be7f2d8a0f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592307"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a>'ReDim' では最も右にある次元のみ変更できます
`ReDim` ステートメントが `Preserve` キーワードを使用して、最後のディメンションではない配列のディメンションを変更しようとしました。 `Preserve`を使用すると、配列の最後のディメンションについてのみ、サイズを変更できます。 他のすべてのディメンションに対しては、既存の配列と同じサイズを指定する必要があります。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- `Preserve` キーワードを削除します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における配列](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [Visual Basic で配列の次元](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [ReDim ステートメント](../../visual-basic/language-reference/statements/redim-statement.md)
- [Dim ステートメント](../../visual-basic/language-reference/statements/dim-statement.md)
