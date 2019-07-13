---
title: この配列は固定か、または一時的にロックされています。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID10
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
ms.openlocfilehash: c7b5372b6046e25aad87131ba141cb71c580e12c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625937"
---
# <a name="this-array-is-fixed-or-temporarily-locked-visual-basic"></a>この配列は固定か、または一時的にロックされています。(Visual Basic)
このエラーは、次の考えられる原因があります。  
  
- 使用して`ReDim`固定サイズの配列の要素の数を変更します。  
  
- 1 つの要素に渡された引数としてプロシージャをモジュール レベル動的配列の次元。 防ぐために、配列がロックされている要素が渡された場合、プロシージャ内での参照パラメーターのメモリの割り当てを解除します。  
  
- 値を代入しようとして、`Variant`配列を含む変数が、`Variant`現在ロックされています。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. 元の配列を作成してで宣言することで修正するのではなく動的`ReDim`(配列が宣言されているプロシージャ内で)、または (この場合、配列は、モジュール レベルで宣言されます要素の数を指定せずに宣言。  
  
2. 実際に、モジュール内のすべてのプロシージャ内で参照可能であるため、要素を渡す必要があるかどうかを決定します。  
  
3. 何がロックを判断、`Variant`およびそれを解決します。  
  
## <a name="see-also"></a>関連項目

- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
