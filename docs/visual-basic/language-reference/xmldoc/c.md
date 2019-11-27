---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348511"
---
# <a name="c-visual-basic"></a><span data-ttu-id="663d1-101">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="663d1-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="663d1-102">説明内のテキストがコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="663d1-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="663d1-103">構文</span><span class="sxs-lookup"><span data-stu-id="663d1-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="663d1-104">パラメーター</span><span class="sxs-lookup"><span data-stu-id="663d1-104">Parameters</span></span>  
  
|<span data-ttu-id="663d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="663d1-105">Parameter</span></span>|<span data-ttu-id="663d1-106">説明</span><span class="sxs-lookup"><span data-stu-id="663d1-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="663d1-107">コードとして指定するテキストです。</span><span class="sxs-lookup"><span data-stu-id="663d1-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="663d1-108">コメント</span><span class="sxs-lookup"><span data-stu-id="663d1-108">Remarks</span></span>  
 <span data-ttu-id="663d1-109">`<c>` タグを使用すると、説明内のテキストをコードとしてマークする必要があることを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="663d1-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="663d1-110">複数行をコードとして指定する場合は、[\<code>](../../../visual-basic/language-reference/xmldoc/code.md) タグを使用します。</span><span class="sxs-lookup"><span data-stu-id="663d1-110">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="663d1-111">コンパイル時に [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) を指定して、ドキュメント コメントをファイルに出力します。</span><span class="sxs-lookup"><span data-stu-id="663d1-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="663d1-112">例</span><span class="sxs-lookup"><span data-stu-id="663d1-112">Example</span></span>  
 <span data-ttu-id="663d1-113">この例では、summary セクションの `<c>` タグを使用して、`Counter` がコードであることを示します。</span><span class="sxs-lookup"><span data-stu-id="663d1-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="663d1-114">参照</span><span class="sxs-lookup"><span data-stu-id="663d1-114">See also</span></span>

- [<span data-ttu-id="663d1-115">XML のコメント用タグ</span><span class="sxs-lookup"><span data-stu-id="663d1-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
