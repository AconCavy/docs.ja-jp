---
title: Protected Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351315"
---
# <a name="protected-friend-visual-basic"></a><span data-ttu-id="0f652-102">Protected Friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f652-102">Protected Friend (Visual Basic)</span></span>

<span data-ttu-id="0f652-103">キーワード組み合わせ `Protected Friend` はメンバー アクセス修飾子です。</span><span class="sxs-lookup"><span data-stu-id="0f652-103">The `Protected Friend` keyword combination is a member access modifier.</span></span> <span data-ttu-id="0f652-104">このクラスは、宣言された要素に対して [Friend](friend.md) アクセスと [Protected](protected.md) アクセスの両方を実行するため、同じアセンブリ内の任意の場所、独自のクラス、および派生クラスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="0f652-104">It confers both [Friend](friend.md) access and [Protected](protected.md) access on the declared elements, so they are accessible from anywhere in the same assembly, from their own class, and from derived classes.</span></span> <span data-ttu-id="0f652-105">`Protected Friend` は、クラスのメンバーに対してのみ指定できます。構造体のメンバーに `Protected Friend` を適用することはできません。構造体を継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="0f652-105">You can specify `Protected Friend` only on members of classes; you cannot apply `Protected Friend` to members of a structure because structures cannot be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="0f652-106">Visual Studio では、`protected friend` で F1 ヘルプを選択すると、 [protected](protected.md) または [friend](friend.md) のヘルプが表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f652-106">In Visual Studio, selecting F1 help on `protected friend` provides help for either [protected](protected.md) or [friend](friend.md).</span></span> <span data-ttu-id="0f652-107">IDE は、複合単語ではなくカーソルの下にある1つのトークンを選択します。</span><span class="sxs-lookup"><span data-stu-id="0f652-107">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="0f652-108">ルール</span><span class="sxs-lookup"><span data-stu-id="0f652-108">Rules</span></span>

<span data-ttu-id="0f652-109">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="0f652-109">**Declaration Context.**</span></span> <span data-ttu-id="0f652-110">`Protected Friend` はクラスレベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0f652-110">You can use `Protected Friend` only at the class level.</span></span> <span data-ttu-id="0f652-111">つまり、`Protected` 要素の宣言コンテキストはクラスである必要があり、ソースファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="0f652-111">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="0f652-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f652-112">See also</span></span>

- [<span data-ttu-id="0f652-113">Public</span><span class="sxs-lookup"><span data-stu-id="0f652-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="0f652-114">Protected</span><span class="sxs-lookup"><span data-stu-id="0f652-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)
- [<span data-ttu-id="0f652-115">Friend</span><span class="sxs-lookup"><span data-stu-id="0f652-115">Friend</span></span>](friend.md)
- [<span data-ttu-id="0f652-116">Private</span><span class="sxs-lookup"><span data-stu-id="0f652-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="0f652-117">Private Protected</span><span class="sxs-lookup"><span data-stu-id="0f652-117">Private Protected</span></span>](./private-protected.md)
- [<span data-ttu-id="0f652-118">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="0f652-118">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="0f652-119">Visual Basic におけるプロシージャ</span><span class="sxs-lookup"><span data-stu-id="0f652-119">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="0f652-120">構造体</span><span class="sxs-lookup"><span data-stu-id="0f652-120">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0f652-121">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="0f652-121">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
