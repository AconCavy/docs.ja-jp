---
title: 0 から始まる文字列アクセスとVisual Basic における文字列の 1 から始まるアクセス
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591749"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a>0 から始まる文字列アクセスとVisual Basic における文字列の 1 から始まるアクセス
このトピックでは、Visual Basic と .NET Framework の文字列の文字へのアクセスを提供する方法を比較します。 .NET Framework は、Visual Basic では、関数によって、0 から始まると 1 つベースのアクセスは常に、文字列の文字に 0 から始まるへのアクセスを提供します。  
  
## <a name="one-based"></a>1 から始まる  
 1 から始まる Visual Basic の関数の例は、検討してください、`Mid`関数。 これは、位置 1 から始まる、部分文字列を開始する文字位置を示す引数を受け取ります。 .NET Framework<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッドは位置の 0 から始まるの部分文字列を開始するには、文字列内の文字のインデックスを受け取ります。 したがって、"ABCDE"文字列がある場合、個々 の文字の番号付けは 1,2,3,4,5 で使用するため、`Mid`関数が 0,1,2,3,4 で使用するため、<xref:System.String.Substring%2A?displayProperty=nameWithType>メソッド。  
  
## <a name="zero-based"></a>0 から始まる  
 0 から始まる Visual Basic の関数の例は、検討してください、`Split`関数。 文字列を分割し、これらの部分文字列を含む配列を返します。 .NET Framework<xref:System.String.Split%2A?displayProperty=nameWithType>もメソッドは文字列を分割し、部分文字列を含む配列を返します。 `Split`関数と<xref:System.String.Split%2A>メソッドは、.NET Framework の配列を返す、0 から始まる必要があります。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
