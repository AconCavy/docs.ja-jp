---
title: <paramref> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 3e2bf7990343a325bbecc56f6d3754a77f1e08e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940843"
---
# <a name="paramref-visual-basic"></a>\<paramref > (Visual Basic)
単語をパラメーターとして書式設定します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<paramref name="name"/>  
```  
  
## <a name="parameters"></a>パラメーター  
 `name`  
 参照されるパラメーターの名前です。 名前は二重引用符 (" ") で囲みます。  
  
## <a name="remarks"></a>Remarks  
 `<paramref>`タグを使用する単語がパラメーターであることを示します。 XML ファイルを処理することで、何らかの方法でこのパラメーターの書式を設定します。  
  
 コンパイル時に [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。  
  
## <a name="example"></a>例  
 この例では、`<paramref>`タグを参照する、`id`パラメーター。  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [XML のコメント用タグ](../../../visual-basic/language-reference/xmldoc/index.md)
