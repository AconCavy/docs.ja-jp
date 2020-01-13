---
title: インターフェイス - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- interface_CSharpKeyword
helpviewer_keywords:
- interface keyword [C#]
ms.assetid: 7da38e81-4f99-4bc5-b07d-c986b687eeba
ms.openlocfilehash: 19ca4b8a490dc85de0d0e2be6d3ca8fa7982fc14
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713448"
---
# <a name="interface-c-reference"></a><span data-ttu-id="08a96-102">インターフェイス (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="08a96-102">interface (C# Reference)</span></span>

<span data-ttu-id="08a96-103">インターフェイスには、[メソッド](../../programming-guide/classes-and-structs/methods.md)、[プロパティ](../../programming-guide/classes-and-structs/properties.md)、[イベント](../../programming-guide/events/index.md)、[インデクサー](../../programming-guide/indexers/index.md)のシグネチャのみが含まれています。</span><span class="sxs-lookup"><span data-stu-id="08a96-103">An interface contains only the signatures of [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [events](../../programming-guide/events/index.md) or [indexers](../../programming-guide/indexers/index.md).</span></span> <span data-ttu-id="08a96-104">インターフェイスを実装するクラスまたは構造体は、インターフェイス定義で指定されているインターフェイスのメンバーを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08a96-104">A class or struct that implements the interface must implement the members of the interface that are specified in the interface definition.</span></span> <span data-ttu-id="08a96-105">次の例の `ImplementationClass` クラスは、`SampleMethod` を返す、パラメーターのない `void` メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="08a96-105">In the following example, class `ImplementationClass` must implement a method named `SampleMethod` that has no parameters and returns `void`.</span></span>

<span data-ttu-id="08a96-106">使用例を含む詳細については、「[インターフェイス](../../programming-guide/interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08a96-106">For more information and examples, see [Interfaces](../../programming-guide/interfaces/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="08a96-107">例</span><span class="sxs-lookup"><span data-stu-id="08a96-107">Example</span></span>

[!code-csharp[csrefKeywordsTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#14)]

<span data-ttu-id="08a96-108">インターフェイスは、名前空間またはクラスのメンバーであり、次のメンバーのシグネチャを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="08a96-108">An interface can be a member of a namespace or a class and can contain signatures of the following members:</span></span>

- [<span data-ttu-id="08a96-109">メソッド</span><span class="sxs-lookup"><span data-stu-id="08a96-109">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)

- [<span data-ttu-id="08a96-110">プロパティ</span><span class="sxs-lookup"><span data-stu-id="08a96-110">Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)

- [<span data-ttu-id="08a96-111">インデクサー</span><span class="sxs-lookup"><span data-stu-id="08a96-111">Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)

- [<span data-ttu-id="08a96-112">イベント</span><span class="sxs-lookup"><span data-stu-id="08a96-112">Events</span></span>](event.md)

<span data-ttu-id="08a96-113">インターフェイスは、1 つ以上の基底インターフェイスから継承できます。</span><span class="sxs-lookup"><span data-stu-id="08a96-113">An interface can inherit from one or more base interfaces.</span></span>

<span data-ttu-id="08a96-114">基本型のリストに基底クラスとインターフェイスが含まれる場合は、基底クラスがリストの最初に表示されます。</span><span class="sxs-lookup"><span data-stu-id="08a96-114">When a base type list contains a base class and interfaces, the base class must come first in the list.</span></span>

<span data-ttu-id="08a96-115">インターフェイスを実装するクラスは、そのインターフェイスのメンバーを明示的に実装できます。</span><span class="sxs-lookup"><span data-stu-id="08a96-115">A class that implements an interface can explicitly implement members of that interface.</span></span> <span data-ttu-id="08a96-116">明示的に実装されているメンバーには、クラス インスタンスではアクセスできません。インターフェイスのインスタンスを使用した場合にのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="08a96-116">An explicitly implemented member cannot be accessed through a class instance, but only through an instance of the interface.</span></span>

<span data-ttu-id="08a96-117">明示的なインターフェイスの実装の詳細とコード例については、「[明示的なインターフェイスの実装](../../programming-guide/interfaces/explicit-interface-implementation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="08a96-117">For more details and code examples on explicit interface implementation, see [Explicit Interface Implementation](../../programming-guide/interfaces/explicit-interface-implementation.md).</span></span>

## <a name="example"></a><span data-ttu-id="08a96-118">例</span><span class="sxs-lookup"><span data-stu-id="08a96-118">Example</span></span>

<span data-ttu-id="08a96-119">ここでは、インターフェイスの実装例を示します。</span><span class="sxs-lookup"><span data-stu-id="08a96-119">The following example demonstrates interface implementation.</span></span> <span data-ttu-id="08a96-120">この例では、インターフェイスにプロパティ宣言が含まれ、クラスに実装が含まれます。</span><span class="sxs-lookup"><span data-stu-id="08a96-120">In this example, the interface contains the property declaration and the class contains the implementation.</span></span> <span data-ttu-id="08a96-121">`IPoint` を実装するクラスのインスタンスには、整数プロパティ `x` および `y` が含まれています。</span><span class="sxs-lookup"><span data-stu-id="08a96-121">Any instance of a class that implements `IPoint` has integer properties `x` and `y`.</span></span>

[!code-csharp[csrefKeywordsTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#15)]

## <a name="c-language-specification"></a><span data-ttu-id="08a96-122">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="08a96-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="08a96-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="08a96-123">See also</span></span>

- [<span data-ttu-id="08a96-124">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="08a96-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="08a96-125">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="08a96-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="08a96-126">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="08a96-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="08a96-127">参照型</span><span class="sxs-lookup"><span data-stu-id="08a96-127">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="08a96-128">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08a96-128">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
- [<span data-ttu-id="08a96-129">プロパティの使用</span><span class="sxs-lookup"><span data-stu-id="08a96-129">Using Properties</span></span>](../../programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="08a96-130">インデクサーの使用</span><span class="sxs-lookup"><span data-stu-id="08a96-130">Using Indexers</span></span>](../../programming-guide/indexers/using-indexers.md)
- [<span data-ttu-id="08a96-131">class</span><span class="sxs-lookup"><span data-stu-id="08a96-131">class</span></span>](class.md)
- [<span data-ttu-id="08a96-132">struct</span><span class="sxs-lookup"><span data-stu-id="08a96-132">struct</span></span>](struct.md)
- [<span data-ttu-id="08a96-133">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="08a96-133">Interfaces</span></span>](../../programming-guide/interfaces/index.md)
