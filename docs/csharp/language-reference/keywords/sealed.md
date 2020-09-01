---
description: sealed 修飾子 - C# リファレンス
title: sealed 修飾子 - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: 5b945503c6f6546f571a2422ae77760da0363b08
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136968"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="f536e-103">sealed (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f536e-103">sealed (C# Reference)</span></span>

<span data-ttu-id="f536e-104">`sealed` 修飾子をクラスに適用すると、それ以外のクラスが、そのクラスから継承できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f536e-104">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="f536e-105">次の例では、`B` クラスは `A` クラスを継承しますが、`B` クラスからはどのクラスも継承できなくなります。</span><span class="sxs-lookup"><span data-stu-id="f536e-105">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="f536e-106">`sealed` 修飾子は、基底クラスの仮想メソッドまたは仮想プロパティをオーバーライドするメソッドやプロパティで使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="f536e-106">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="f536e-107">これにより、クラスの派生が行えるようになり、そのクラスが特定の仮想メソッドまたは仮想プロパティをオーバーライドできなくなります。</span><span class="sxs-lookup"><span data-stu-id="f536e-107">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="f536e-108">例</span><span class="sxs-lookup"><span data-stu-id="f536e-108">Example</span></span>

<span data-ttu-id="f536e-109">次の例では、`Z` は `Y` から継承しますが、`Z` は仮想関数 `F` をオーバーライドできません。この仮想関数は `X` で宣言されており、`Y` でシールされています。</span><span class="sxs-lookup"><span data-stu-id="f536e-109">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="f536e-110">新しいメソッドまたはプロパティをクラスで定義するときに、派生クラスによるオーバーライドを防ぐには、その派生クラスを [virtual](virtual.md) として宣言しないようにします。</span><span class="sxs-lookup"><span data-stu-id="f536e-110">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="f536e-111">[abstract](abstract.md) 修飾子をシール クラスで使用するとエラーになります。抽象メソッドまたは抽象プロパティを実装するクラスでは、抽象クラスを継承する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="f536e-111">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="f536e-112">`sealed` 修飾子は、メソッドまたはプロパティに適用するときは、常に [override](override.md) と一緒に使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f536e-112">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="f536e-113">構造体は暗黙的にシールされるため、継承できません。</span><span class="sxs-lookup"><span data-stu-id="f536e-113">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="f536e-114">詳細については、「[継承](../../programming-guide/classes-and-structs/inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f536e-114">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="f536e-115">上記以外の例については、「[抽象クラスとシール クラス、およびクラス メンバー](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f536e-115">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="f536e-116">例</span><span class="sxs-lookup"><span data-stu-id="f536e-116">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="f536e-117">前の例で、次のステートメントを使用して、シール クラスからの継承を試みたとします。</span><span class="sxs-lookup"><span data-stu-id="f536e-117">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="f536e-118">この場合、次のエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f536e-118">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="remarks"></a><span data-ttu-id="f536e-119">注釈</span><span class="sxs-lookup"><span data-stu-id="f536e-119">Remarks</span></span>

<span data-ttu-id="f536e-120">クラス、メソッド、またはプロパティをシールするかどうかを判断するには、通常、次の 2 つの点を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f536e-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="f536e-121">クラスをカスタマイズすることで、派生クラスにもたらされる可能性があるメリット。</span><span class="sxs-lookup"><span data-stu-id="f536e-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="f536e-122">派生クラスがクラスを変更することで、そのクラスが正常に、または期待どおりに機能しなくなる可能性。</span><span class="sxs-lookup"><span data-stu-id="f536e-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f536e-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="f536e-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f536e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="f536e-124">See also</span></span>

- [<span data-ttu-id="f536e-125">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="f536e-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f536e-126">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="f536e-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f536e-127">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="f536e-127">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f536e-128">静的クラスと静的クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="f536e-128">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="f536e-129">抽象クラスとシール クラス、およびクラス メンバー</span><span class="sxs-lookup"><span data-stu-id="f536e-129">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="f536e-130">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="f536e-130">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="f536e-131">修飾子</span><span class="sxs-lookup"><span data-stu-id="f536e-131">Modifiers</span></span>](index.md)
- [<span data-ttu-id="f536e-132">override</span><span class="sxs-lookup"><span data-stu-id="f536e-132">override</span></span>](override.md)
- [<span data-ttu-id="f536e-133">virtual</span><span class="sxs-lookup"><span data-stu-id="f536e-133">virtual</span></span>](virtual.md)
