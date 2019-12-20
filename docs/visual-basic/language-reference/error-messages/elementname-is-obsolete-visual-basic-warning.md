---
title: "'<elementname>' は古い形式です (Visual Basic 警告)"
ms.date: 07/20/2015
f1_keywords:
- vbc40008
- bc40008
helpviewer_keywords:
- BC40008
ms.assetid: 729e3eb5-76ac-4c55-9fdd-78350e0de55e
ms.openlocfilehash: d7d3d86f89ef3b76e958707dd0be2dce8a3e9bf2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64659813"
---
# <a name="elementname-is-obsolete-visual-basic-warning"></a><span data-ttu-id="4c93b-102">'\<elementname >' は廃止されています (Visual Basic 警告)</span><span class="sxs-lookup"><span data-stu-id="4c93b-102">'\<elementname>' is obsolete (Visual Basic Warning)</span></span>
<span data-ttu-id="4c93b-103">ステートメントが、<xref:System.ObsoleteAttribute> 属性でマーク付けされているプログラミング要素にアクセスしています。また、ディレクティブがそれを警告として扱うように設定されています。</span><span class="sxs-lookup"><span data-stu-id="4c93b-103">A statement attempts to access a programming element which has been marked with the <xref:System.ObsoleteAttribute> attribute and the directive to treat it as a warning.</span></span>  
  
 <span data-ttu-id="4c93b-104"><xref:System.ObsoleteAttribute> を適用することで、任意のプログラミング要素を使用しない要素としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="4c93b-104">You can mark any programming element as being no longer in use by applying <xref:System.ObsoleteAttribute> to it.</span></span> <span data-ttu-id="4c93b-105">これを行う場合は、属性の<xref:System.ObsoleteAttribute.IsError%2A> プロパティを `True` または `False`に設定できます。</span><span class="sxs-lookup"><span data-stu-id="4c93b-105">If you do this, you can set the attribute's <xref:System.ObsoleteAttribute.IsError%2A> property to either `True` or `False`.</span></span> <span data-ttu-id="4c93b-106">`True`に設定した場合、コンパイラは要素を使用する試みをエラーとして扱います。</span><span class="sxs-lookup"><span data-stu-id="4c93b-106">If you set it to `True`, the compiler treats an attempt to use the element as an error.</span></span> <span data-ttu-id="4c93b-107">`False`に設定した場合、または既定値の `False`を使用した場合、コンパイラはこの要素の使用が試行されると、警告を発行します。</span><span class="sxs-lookup"><span data-stu-id="4c93b-107">If you set it to `False`, or let it default to `False`, the compiler issues a warning if there is an attempt to use the element.</span></span>  
  
 <span data-ttu-id="4c93b-108">既定では、 <xref:System.ObsoleteAttribute.IsError%2A> の <xref:System.ObsoleteAttribute> プロパティが `False`であるため、このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="4c93b-108">By default, this message is a warning, because the <xref:System.ObsoleteAttribute.IsError%2A> property of <xref:System.ObsoleteAttribute> is `False`.</span></span> <span data-ttu-id="4c93b-109">警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4c93b-109">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="4c93b-110">**エラー ID:** BC40008</span><span class="sxs-lookup"><span data-stu-id="4c93b-110">**Error ID:** BC40008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4c93b-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4c93b-111">To correct this error</span></span>  
  
- <span data-ttu-id="4c93b-112">ソース コード参照の要素名のスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="4c93b-112">Ensure that the source-code reference is spelling the element name correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c93b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c93b-113">See also</span></span>

- [<span data-ttu-id="4c93b-114">属性の概要</span><span class="sxs-lookup"><span data-stu-id="4c93b-114">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
