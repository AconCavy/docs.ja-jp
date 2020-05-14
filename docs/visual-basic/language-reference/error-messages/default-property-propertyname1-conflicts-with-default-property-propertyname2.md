---
title: 既定プロパティ '<propertyname1>' は、'<propertyname2>' の既定プロパティ '<classname>' と競合しているため、'Shadows' と宣言できません。
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: c964003217e7b96cf25288e2ae6ae6a2fb07a6c3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651386"
---
# <a name="default-property-propertyname1-conflicts-with-default-property-propertyname2-in-classname-and-so-should-be-declared-shadows"></a><span data-ttu-id="6b1f4-102">既定のプロパティ '\<propertyname1>' は、'\<classname>' の既定のプロパティ '\<propertyname2>' と競合しているため、'Shadows' と宣言する必要があります</span><span class="sxs-lookup"><span data-stu-id="6b1f4-102">Default property '\<propertyname1>' conflicts with default property '\<propertyname2>' in '\<classname>' and so should be declared 'Shadows'</span></span>
<span data-ttu-id="6b1f4-103">プロパティが、基底クラスで定義されたプロパティと同じ名前で宣言されています。</span><span class="sxs-lookup"><span data-stu-id="6b1f4-103">A property is declared with the same name as a property defined in the base class.</span></span> <span data-ttu-id="6b1f4-104">この場合、このクラスのプロパティは、基底クラス プロパティをシャドウする必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b1f4-104">In this situation, the property in this class should shadow the base class property.</span></span>  
  
 <span data-ttu-id="6b1f4-105">このメッセージは警告です。</span><span class="sxs-lookup"><span data-stu-id="6b1f4-105">This message is a warning.</span></span> <span data-ttu-id="6b1f4-106">`Shadows` は、既定で指定されていると見なされます。</span><span class="sxs-lookup"><span data-stu-id="6b1f4-106">`Shadows` is assumed by default.</span></span> <span data-ttu-id="6b1f4-107">警告を非表示にする方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6b1f4-107">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="6b1f4-108">**エラー ID:** BC40007</span><span class="sxs-lookup"><span data-stu-id="6b1f4-108">**Error ID:** BC40007</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b1f4-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6b1f4-109">To correct this error</span></span>  
  
- <span data-ttu-id="6b1f4-110">`Shadows` キーワードを宣言に追加するか、宣言されるプロパティの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="6b1f4-110">Add the `Shadows` keyword to the declaration, or change the name of the property being declared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b1f4-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b1f4-111">See also</span></span>

- [<span data-ttu-id="6b1f4-112">Shadows</span><span class="sxs-lookup"><span data-stu-id="6b1f4-112">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="6b1f4-113">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="6b1f4-113">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
