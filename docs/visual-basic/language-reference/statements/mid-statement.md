---
title: Mid ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.MidB
- vb.Mid
helpviewer_keywords:
- substrings [Visual Basic], Mid statement
- strings [Visual Basic], substrings
- Mid statement [Visual Basic]
- strings [Visual Basic], replacing
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
ms.openlocfilehash: ff3b908e2805f4d51463a82d90f2305efc9f1608
ms.sourcegitcommit: c4dfe37032c64a1fba2cc3d5947550d79f95e3b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/13/2019
ms.locfileid: "67041581"
---
# <a name="mid-statement"></a>Mid ステートメント
指定した文字数を置き換える、`String`別の文字列から文字を含む変数。  
  
## <a name="syntax"></a>構文  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## <a name="parts"></a>指定項目  
 `Target`  
 必須。 名前、`String`変数を変更します。  
  
 `Start`  
 必須。 `Integer` 式。 内の位置の文字`Target`テキストの置換を開始します。 `Start` 1 から始まるインデックスを使用します。  
  
 `Length`  
 省略可能です。 `Integer` 式。 置換する文字の数。 省略した場合、すべての`String`使用されます。  
  
 `StringExpression`  
 必須。 `String` 式の一部を置換する`Target`します。  
  
## <a name="exceptions"></a>例外  
  
|例外の種類|条件|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|`Start` < = 0 または`Length`< 0。|  
  
## <a name="remarks"></a>Remarks  
 置き換えられた文字の数は、文字数以下では常に`Target`します。  
  
 Visual Basic には、<xref:Microsoft.VisualBasic.Strings.Mid%2A>関数と`Mid`ステートメント。 これらの要素で指定された数、文字列内の文字の両方の動作が、`Mid`関数の中に文字を返します、`Mid`ステートメントには、文字が置き換えられます。 詳細については、「 <xref:Microsoft.VisualBasic.Strings.Mid%2A> 」を参照してください。  
  
> [!NOTE]
>  `MidB`以前のバージョンの Visual Basic のステートメントには、文字ではなく、(バイト単位) で部分文字列が置き換えられます。 2 バイト文字セット (DBCS) のアプリケーションで文字列に変換するためには、主に使用されます。 Visual Basic のすべての文字列が Unicode では、`MidB`現在サポートされていません。  
  
## <a name="example"></a>例  
 この例では、`Mid`ステートメントを指定した文字列変数内の文字数を別の文字列から文字に置き換えます。  
  
 [!code-vb[VbVbalrStrings#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class1.vb#5)]  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール:** `Strings`  
  
 **アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- [文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)
- [Visual Basic の文字列の概要](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
