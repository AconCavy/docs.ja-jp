---
title: NotOverridable
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351444"
---
# <a name="notoverridable-visual-basic"></a><span data-ttu-id="f692f-102">NotOverridable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f692f-102">NotOverridable (Visual Basic)</span></span>
<span data-ttu-id="f692f-103">派生クラス内のプロパティまたはプロシージャをオーバーライドできないことを示します。</span><span class="sxs-lookup"><span data-stu-id="f692f-103">Specifies that a property or procedure cannot be overridden in a derived class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f692f-104">Remarks</span><span class="sxs-lookup"><span data-stu-id="f692f-104">Remarks</span></span>  
 <span data-ttu-id="f692f-105">`NotOverridable` 修飾子は、派生クラス内のプロパティまたはメソッドがオーバーライドされるのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="f692f-105">The `NotOverridable` modifier prevents a property or method from being overridden in a derived class.</span></span>  <span data-ttu-id="f692f-106">[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) 修飾子を使用すると、クラス内のプロパティまたはメソッドを派生クラスでオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="f692f-106">The [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifier allows a property or method in a class to be overridden in a derived class.</span></span> <span data-ttu-id="f692f-107">詳細については、「[継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f692f-107">For more information, see [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="f692f-108">`Overridable` または `NotOverridable` 修飾子が指定されていない場合、既定の設定は、プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドするかどうかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="f692f-108">If the `Overridable` or `NotOverridable` modifier is not specified, the default setting depends on whether the property or method overrides a base class property or method.</span></span> <span data-ttu-id="f692f-109">プロパティまたはメソッドが基底クラスのプロパティまたはメソッドをオーバーライドする場合、既定の設定は `Overridable` であり、そうでない場合は `NotOverridable` です。</span><span class="sxs-lookup"><span data-stu-id="f692f-109">If the property or method overrides a base class property or method, the default setting is `Overridable`; otherwise, it is `NotOverridable`.</span></span>  
  
 <span data-ttu-id="f692f-110">オーバーライドできない要素は、*シールド*要素と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="f692f-110">An element that cannot be overridden is sometimes called a *sealed* element.</span></span>  
  
 <span data-ttu-id="f692f-111">`NotOverridable` は、プロパティまたはプロシージャの宣言ステートメントでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="f692f-111">You can use `NotOverridable` only in a property or procedure declaration statement.</span></span> <span data-ttu-id="f692f-112">`NotOverridable` は、別のプロパティまたはプロシージャをオーバーライドするプロパティまたはプロシージャでのみ、つまり `Overrides` との組み合わせでのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="f692f-112">You can specify `NotOverridable` only on a property or procedure that overrides another property or procedure, that is, only in combination with `Overrides`.</span></span>  
  
## <a name="combined-modifiers"></a><span data-ttu-id="f692f-113">結合された修飾子</span><span class="sxs-lookup"><span data-stu-id="f692f-113">Combined Modifiers</span></span>  
 <span data-ttu-id="f692f-114">`Private` メソッドに `Overridable` または `NotOverridable` を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f692f-114">You cannot specify `Overridable` or `NotOverridable` for a `Private` method.</span></span>  
  
 <span data-ttu-id="f692f-115">同じ宣言内で `NotOverridable` を `MustOverride`、`Overridable`、または `Shared` と共に指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f692f-115">You cannot specify `NotOverridable` together with `MustOverride`, `Overridable`, or `Shared` in the same declaration.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="f692f-116">使用方法</span><span class="sxs-lookup"><span data-stu-id="f692f-116">Usage</span></span>  
 <span data-ttu-id="f692f-117">`NotOverridable` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="f692f-117">The `NotOverridable` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="f692f-118">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="f692f-118">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="f692f-119">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="f692f-119">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="f692f-120">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="f692f-120">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="f692f-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f692f-121">See also</span></span>

- [<span data-ttu-id="f692f-122">修飾子</span><span class="sxs-lookup"><span data-stu-id="f692f-122">Modifiers</span></span>](../../../visual-basic/language-reference/modifiers/index.md)
- [<span data-ttu-id="f692f-123">継承の基本</span><span class="sxs-lookup"><span data-stu-id="f692f-123">Inheritance Basics</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="f692f-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="f692f-124">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [<span data-ttu-id="f692f-125">Overridable</span><span class="sxs-lookup"><span data-stu-id="f692f-125">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)
- [<span data-ttu-id="f692f-126">Overrides</span><span class="sxs-lookup"><span data-stu-id="f692f-126">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)
- [<span data-ttu-id="f692f-127">キーワード</span><span class="sxs-lookup"><span data-stu-id="f692f-127">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
- [<span data-ttu-id="f692f-128">Visual Basic におけるシャドウ</span><span class="sxs-lookup"><span data-stu-id="f692f-128">Shadowing in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
