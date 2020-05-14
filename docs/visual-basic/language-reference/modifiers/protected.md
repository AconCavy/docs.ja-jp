---
title: Protected
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: 740c998b8a6ccc6798bce37e9b08e408dac7c17d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351299"
---
# <a name="protected-visual-basic"></a><span data-ttu-id="17e9d-102">Protected (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="17e9d-102">Protected (Visual Basic)</span></span>

<span data-ttu-id="17e9d-103">1 つ以上の宣言されたプログラミング要素を指定するメンバー アクセス修飾子は、独自のクラス内から、または派生クラスからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-103">A member access modifier that specifies that one or more declared programming elements are accessible only from within their own class or from a derived class.</span></span>

## <a name="remarks"></a><span data-ttu-id="17e9d-104">Remarks</span><span class="sxs-lookup"><span data-stu-id="17e9d-104">Remarks</span></span>

<span data-ttu-id="17e9d-105">場合によっては、クラスで宣言されたプログラミング要素に機密データまたは制限コードが含まれていて、要素へのアクセスを制限する必要があります。</span><span class="sxs-lookup"><span data-stu-id="17e9d-105">Sometimes a programming element declared in a class contains sensitive data or restricted code, and you want to limit access to the element.</span></span> <span data-ttu-id="17e9d-106">ただし、クラスが継承可能であり、派生クラスの階層を想定している場合は、これらの派生クラスがデータまたはコードにアクセスする必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="17e9d-106">However, if the class is inheritable and you expect a hierarchy of derived classes, it might be necessary for these derived classes to access the data or code.</span></span> <span data-ttu-id="17e9d-107">このような場合は、基底クラスとすべての派生クラスの両方から要素にアクセスできるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="17e9d-107">In such a case, you want the element to be accessible both from the base class and from all derived classes.</span></span> <span data-ttu-id="17e9d-108">この方法で要素へのアクセスを制限するには、`Protected` を使用して宣言できます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-108">To limit access to an element in this manner, you can declare it with `Protected`.</span></span>

> [!NOTE]
> <span data-ttu-id="17e9d-109">`Protected` アクセス修飾子は、次の 2 つの修飾子と組み合わせることができます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-109">The `Protected` access modifier can be combined with two other modifiers:</span></span>
>
> - <span data-ttu-id="17e9d-110">[Protected Friend](protected-friend.md) 修飾子は、クラス メンバーに、クラス内、派生クラス、およびクラスが定義されている同じアセンブリからアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="17e9d-110">The [Protected Friend](protected-friend.md) modifier makes a class member accessible from within that class, from derived classes, and from the same assembly in which the class is defined.</span></span>
> - <span data-ttu-id="17e9d-111">[Private Protected](private-protected.md) 修飾子は、派生型によってクラス メンバーにアクセスできるようにしますが、その包含アセンブリ内に限られます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-111">The [Private Protected](private-protected.md) modifier makes a class member accessible by derived types, but only within its containing assembly.</span></span>

## <a name="rules"></a><span data-ttu-id="17e9d-112">ルール</span><span class="sxs-lookup"><span data-stu-id="17e9d-112">Rules</span></span>

<span data-ttu-id="17e9d-113">**宣言コンテキスト。**</span><span class="sxs-lookup"><span data-stu-id="17e9d-113">**Declaration Context.**</span></span> <span data-ttu-id="17e9d-114">`Protected` は、クラス レベルでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-114">You can use `Protected` only at the class level.</span></span> <span data-ttu-id="17e9d-115">つまり、`Protected` 要素の宣言コンテキストはクラスにする必要があり、ソース ファイル、名前空間、インターフェイス、モジュール、構造体、またはプロシージャにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="17e9d-115">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="17e9d-116">動作</span><span class="sxs-lookup"><span data-stu-id="17e9d-116">Behavior</span></span>

- <span data-ttu-id="17e9d-117">**アクセス レベル。**</span><span class="sxs-lookup"><span data-stu-id="17e9d-117">**Access Level.**</span></span> <span data-ttu-id="17e9d-118">クラス内のすべてのコードで、その要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-118">All code in a class can access its elements.</span></span> <span data-ttu-id="17e9d-119">基底クラスから派生するすべてのクラスのコードで、基底クラスのすべての `Protected` 要素にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-119">Code in any class that derives from a base class can access all the `Protected` elements of the base class.</span></span> <span data-ttu-id="17e9d-120">これは、派生のすべての世代に当てはまります。</span><span class="sxs-lookup"><span data-stu-id="17e9d-120">This is true for all generations of derivation.</span></span> <span data-ttu-id="17e9d-121">これは、クラスが基底クラスの基底クラスの `Protected` 要素にアクセスでき、以下同様に続くことを意味します。</span><span class="sxs-lookup"><span data-stu-id="17e9d-121">This means that a class can access `Protected` elements of the base class of the base class, and so on.</span></span>

     <span data-ttu-id="17e9d-122">保護されたアクセスは、フレンド アクセスのスーパーセットまたはサブセットではありません。</span><span class="sxs-lookup"><span data-stu-id="17e9d-122">Protected access is not a superset or subset of friend access.</span></span>

- <span data-ttu-id="17e9d-123">**アクセス修飾子。**</span><span class="sxs-lookup"><span data-stu-id="17e9d-123">**Access Modifiers.**</span></span> <span data-ttu-id="17e9d-124">アクセス レベルを指定するキーワードは、*アクセス修飾子*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-124">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="17e9d-125">アクセス修飾子の比較については、「[Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17e9d-125">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="17e9d-126">`Protected` 修飾子は、次のコンテキストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="17e9d-126">The `Protected` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="17e9d-127">Class ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-127">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)

- [<span data-ttu-id="17e9d-128">Const ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-128">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)

- [<span data-ttu-id="17e9d-129">Declare ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-129">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)

- [<span data-ttu-id="17e9d-130">Delegate ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-130">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [<span data-ttu-id="17e9d-131">Dim ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-131">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)

- [<span data-ttu-id="17e9d-132">Enum ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-132">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)

- [<span data-ttu-id="17e9d-133">Event ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-133">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)

- [<span data-ttu-id="17e9d-134">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-134">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)

- [<span data-ttu-id="17e9d-135">Interface ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-135">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)

- [<span data-ttu-id="17e9d-136">Property ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-136">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)

- [<span data-ttu-id="17e9d-137">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-137">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)

- [<span data-ttu-id="17e9d-138">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="17e9d-138">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="17e9d-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="17e9d-139">See also</span></span>

- [<span data-ttu-id="17e9d-140">Public</span><span class="sxs-lookup"><span data-stu-id="17e9d-140">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)
- [<span data-ttu-id="17e9d-141">Friend</span><span class="sxs-lookup"><span data-stu-id="17e9d-141">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)
- [<span data-ttu-id="17e9d-142">Private</span><span class="sxs-lookup"><span data-stu-id="17e9d-142">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
- [<span data-ttu-id="17e9d-143">Private Protected</span><span class="sxs-lookup"><span data-stu-id="17e9d-143">Private Protected</span></span>](private-protected.md)
- [<span data-ttu-id="17e9d-144">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="17e9d-144">Protected Friend</span></span>](protected-friend.md)
- [<span data-ttu-id="17e9d-145">Visual Basic でのアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="17e9d-145">Access levels in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="17e9d-146">手順</span><span class="sxs-lookup"><span data-stu-id="17e9d-146">Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="17e9d-147">構造体</span><span class="sxs-lookup"><span data-stu-id="17e9d-147">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="17e9d-148">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="17e9d-148">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
