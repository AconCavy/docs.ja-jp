---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 9be9f9e96fc1b79ea97d54c54352da63b93ef264
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938594"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)
説明内のテキストがコードであることを示します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>パラメーター  
  
|パラメーター|説明|  
|---|---|  
|`text`|コードとして指定するテキストです。|  
  
## <a name="remarks"></a>コメント  
 `<c>`タグを使用する方法を示す説明内のテキストをコードとしてマークする必要があります。 複数行をコードとして指定する場合は、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグを使用します。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<c>`ことを示す [概要] セクションでタグ`Counter`コードに示します。  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
