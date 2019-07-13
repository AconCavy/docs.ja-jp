---
title: <permission> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <permission> XML tag
- permission XML tag
ms.assetid: 0edf0500-5cd7-49c0-9255-64c48f972b77
ms.openlocfilehash: 7333d4a4d051c157f6732224da0fffe4d7cd35ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940830"
---
# <a name="permission-visual-basic"></a>\<アクセス許可 > (Visual Basic)
メンバーの必要なアクセス許可を指定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<permission cref="member">description</permission>  
```  
  
## <a name="parameters"></a>パラメーター  
 `member`  
 現在のコンパイル環境からの呼び出しに利用できる、メンバーまたはフィールドへの参照。 コンパイラは、指定されたコード要素が存在し、出力の XML で `member` が正規要素名に変換されることを確認します。 囲む`member`引用符 ("")。  
  
 `description`  
 メンバーへのアクセスの説明です。  
  
## <a name="remarks"></a>Remarks  
 使用して、`<permission>`メンバーへのアクセスを文書化タグ。 使用して、<xref:System.Security.PermissionSet>クラス メンバーへのアクセスを指定します。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<permission>`を記述するタグ、<xref:System.Security.Permissions.FileIOPermission>に必要な`ReadFile`メソッド。  
  
 [!code-vb[VbVbcnXmlDocComments#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#7)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
