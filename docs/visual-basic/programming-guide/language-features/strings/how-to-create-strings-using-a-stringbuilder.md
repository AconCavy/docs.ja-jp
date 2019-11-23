---
title: 'How to: create strings using a StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 9295b9d0cdcfdb05dfc75f75f48c16c2354b09b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344381"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a><span data-ttu-id="b281e-102">How to: create strings using a StringBuilder in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b281e-102">How to: create strings using a StringBuilder in Visual Basic</span></span>

<span data-ttu-id="b281e-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span><span class="sxs-lookup"><span data-stu-id="b281e-103">This example constructs a long string from many smaller strings using the <xref:System.Text.StringBuilder> class.</span></span> <span data-ttu-id="b281e-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span><span class="sxs-lookup"><span data-stu-id="b281e-104">The <xref:System.Text.StringBuilder> class is more efficient than the `&=` operator for concatenating many strings.</span></span>

## <a name="example"></a><span data-ttu-id="b281e-105">例</span><span class="sxs-lookup"><span data-stu-id="b281e-105">Example</span></span>

<span data-ttu-id="b281e-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span><span class="sxs-lookup"><span data-stu-id="b281e-106">The following example creates an instance of the <xref:System.Text.StringBuilder> class, appends 1,000 strings to that instance, and then returns its string representation:</span></span>

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a><span data-ttu-id="b281e-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="b281e-107">See also</span></span>

- [<span data-ttu-id="b281e-108">StringBuilder クラスの使用</span><span class="sxs-lookup"><span data-stu-id="b281e-108">Using the StringBuilder Class</span></span>](../../../../standard/base-types/stringbuilder.md)
- [<span data-ttu-id="b281e-109">& = 演算子</span><span class="sxs-lookup"><span data-stu-id="b281e-109">&= Operator</span></span>](../../../language-reference/operators/and-assignment-operator.md)
- [<span data-ttu-id="b281e-110">文字列</span><span class="sxs-lookup"><span data-stu-id="b281e-110">Strings</span></span>](index.md)
- [<span data-ttu-id="b281e-111">新しい文字列の作成</span><span class="sxs-lookup"><span data-stu-id="b281e-111">Creating New Strings</span></span>](../../../../standard/base-types/creating-new.md)
- [<span data-ttu-id="b281e-112">文字列の操作</span><span class="sxs-lookup"><span data-stu-id="b281e-112">Manipulating Strings</span></span>](../../../../standard/base-types/manipulating-strings.md)
