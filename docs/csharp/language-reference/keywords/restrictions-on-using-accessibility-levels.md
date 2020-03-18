---
title: アクセシビリティ レベルの使用に関する制限事項 - C# リファレンス
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#], accessibility level restrictions
ms.assetid: 987e2f22-46bf-4fea-80ee-270b9cd01045
ms.openlocfilehash: 48ab765db7c839ed0dd14df5e6b30f5bd6c0d29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173537"
---
# <a name="restrictions-on-using-accessibility-levels-c-reference"></a><span data-ttu-id="4dc71-102">アクセシビリティ レベルの使用に関する制限事項 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="4dc71-102">Restrictions on using accessibility levels (C# Reference)</span></span>

<span data-ttu-id="4dc71-103">宣言で型を指定する場合、その型のアクセシビリティ レベルがメンバーまたは他の型のアクセシビリティ レベルに依存するかどうかをチェックしてください。</span><span class="sxs-lookup"><span data-stu-id="4dc71-103">When you specify a type in a declaration, check whether the accessibility level of the type is dependent on the accessibility level of a member or of another type.</span></span> <span data-ttu-id="4dc71-104">たとえば、直接基底クラスは、少なくともその派生クラスと同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-104">For example, the direct base class must be at least as accessible as the derived class.</span></span> <span data-ttu-id="4dc71-105">次の宣言はコンパイラ エラーになりますが、それは基底クラス `BaseClass` のアクセシビリティが `MyClass` のアクセシビリティよりも低いためです。</span><span class="sxs-lookup"><span data-stu-id="4dc71-105">The following declarations cause a compiler error because the base class `BaseClass` is less accessible than `MyClass`:</span></span>

```csharp
class BaseClass {...}
public class MyClass: BaseClass {...} // Error
```

<span data-ttu-id="4dc71-106">宣言されたアクセシビリティ レベルの制限を次の表にまとめます。</span><span class="sxs-lookup"><span data-stu-id="4dc71-106">The following table summarizes the restrictions on declared accessibility levels.</span></span>

|<span data-ttu-id="4dc71-107">コンテキスト</span><span class="sxs-lookup"><span data-stu-id="4dc71-107">Context</span></span>|<span data-ttu-id="4dc71-108">解説</span><span class="sxs-lookup"><span data-stu-id="4dc71-108">Remarks</span></span>|
|-------------|-------------|
|[<span data-ttu-id="4dc71-109">クラス</span><span class="sxs-lookup"><span data-stu-id="4dc71-109">Classes</span></span>](../../programming-guide/classes-and-structs/classes.md)|<span data-ttu-id="4dc71-110">クラスの型の直接基底クラスは、少なくとも、クラスの型自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-110">The direct base class of a class type must be at least as accessible as the class type itself.</span></span>|
|[<span data-ttu-id="4dc71-111">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4dc71-111">Interfaces</span></span>](../../programming-guide/interfaces/index.md)|<span data-ttu-id="4dc71-112">インターフェイスの型の明示的な基本インターフェイスは、少なくとも、インターフェイスの型自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-112">The explicit base interfaces of an interface type must be at least as accessible as the interface type itself.</span></span>|
|[<span data-ttu-id="4dc71-113">デリゲート</span><span class="sxs-lookup"><span data-stu-id="4dc71-113">Delegates</span></span>](../../programming-guide/delegates/index.md)|<span data-ttu-id="4dc71-114">デリゲート型の戻り値の型およびパラメーターの型は、少なくとも、デリゲート型自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-114">The return type and parameter types of a delegate type must be at least as accessible as the delegate type itself.</span></span>|
|[<span data-ttu-id="4dc71-115">定数</span><span class="sxs-lookup"><span data-stu-id="4dc71-115">Constants</span></span>](../../programming-guide/classes-and-structs/constants.md)|<span data-ttu-id="4dc71-116">定数の型は、少なくとも定数自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-116">The type of a constant must be at least as accessible as the constant itself.</span></span>|
|[<span data-ttu-id="4dc71-117">フィールド</span><span class="sxs-lookup"><span data-stu-id="4dc71-117">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)|<span data-ttu-id="4dc71-118">フィールドの型は、少なくともフィールド自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-118">The type of a field must be at least as accessible as the field itself.</span></span>|
|[<span data-ttu-id="4dc71-119">メソッド</span><span class="sxs-lookup"><span data-stu-id="4dc71-119">Methods</span></span>](../../programming-guide/classes-and-structs/methods.md)|<span data-ttu-id="4dc71-120">メソッドの戻り値の型およびパラメーターの型は、少なくとも、メソッド自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-120">The return type and parameter types of a method must be at least as accessible as the method itself.</span></span>|
|[<span data-ttu-id="4dc71-121">Properties</span><span class="sxs-lookup"><span data-stu-id="4dc71-121">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)|<span data-ttu-id="4dc71-122">プロパティの型は、少なくともプロパティ自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-122">The type of a property must be at least as accessible as the property itself.</span></span>|
|[<span data-ttu-id="4dc71-123">イベント</span><span class="sxs-lookup"><span data-stu-id="4dc71-123">Events</span></span>](../../programming-guide/events/index.md)|<span data-ttu-id="4dc71-124">イベントの型は、少なくともイベント自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-124">The type of an event must be at least as accessible as the event itself.</span></span>|
|[<span data-ttu-id="4dc71-125">インデクサー</span><span class="sxs-lookup"><span data-stu-id="4dc71-125">Indexers</span></span>](../../programming-guide/indexers/index.md)|<span data-ttu-id="4dc71-126">インデクサーの型とパラメーターの型は、少なくとも、インデクサー自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-126">The type and parameter types of an indexer must be at least as accessible as the indexer itself.</span></span>|
|[<span data-ttu-id="4dc71-127">オペレーター</span><span class="sxs-lookup"><span data-stu-id="4dc71-127">Operators</span></span>](../operators/index.md)|<span data-ttu-id="4dc71-128">演算子の戻り値の型とパラメーターの型は、少なくとも、演算子自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-128">The return type and parameter types of an operator must be at least as accessible as the operator itself.</span></span>|
|[<span data-ttu-id="4dc71-129">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="4dc71-129">Constructors</span></span>](../../programming-guide/classes-and-structs/constructors.md)|<span data-ttu-id="4dc71-130">コンストラクターのパラメーターの型は、少なくとも、コンストラクター自体と同程度にアクセス可能である必要があります。</span><span class="sxs-lookup"><span data-stu-id="4dc71-130">The parameter types of a constructor must be at least as accessible as the constructor itself.</span></span>|

## <a name="example"></a><span data-ttu-id="4dc71-131">例</span><span class="sxs-lookup"><span data-stu-id="4dc71-131">Example</span></span>

<span data-ttu-id="4dc71-132">さまざまな型の不適切な宣言の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="4dc71-132">The following example contains erroneous declarations of different types.</span></span> <span data-ttu-id="4dc71-133">各宣言の後のコメントは、予期されるコンパイラ エラーを示しています。</span><span class="sxs-lookup"><span data-stu-id="4dc71-133">The comment following each declaration indicates the expected compiler error.</span></span>

```csharp
// Restrictions on Using Accessibility Levels
// CS0052 expected as well as CS0053, CS0056, and CS0057
// To make the program work, change access level of both class B
// and MyPrivateMethod() to public.

using System;

// A delegate:
delegate int MyDelegate();

class B
{
    // A private method:
    static int MyPrivateMethod()
    {
        return 0;
    }
}

public class A
{
    // Error: The type B is less accessible than the field A.myField.
    public B myField = new B();

    // Error: The type B is less accessible
    // than the constant A.myConst.
    public readonly B myConst = new B();

    public B MyMethod()
    {
        // Error: The type B is less accessible
        // than the method A.MyMethod.
        return new B();
    }

    // Error: The type B is less accessible than the property A.MyProp
    public B MyProp
    {
        set
        {
        }
    }

    MyDelegate d = new MyDelegate(B.MyPrivateMethod);
    // Even when B is declared public, you still get the error:
    // "The parameter B.MyPrivateMethod is not accessible due to
    // protection level."

    public static B operator +(A m1, B m2)
    {
        // Error: The type B is less accessible
        // than the operator A.operator +(A,B)
        return new B();
    }

    static void Main()
    {
        Console.Write("Compiled successfully");
    }
}
```

## <a name="c-language-specification"></a><span data-ttu-id="4dc71-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4dc71-134">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="4dc71-135">参照</span><span class="sxs-lookup"><span data-stu-id="4dc71-135">See also</span></span>

- [<span data-ttu-id="4dc71-136">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="4dc71-136">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="4dc71-137">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="4dc71-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4dc71-138">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="4dc71-138">C# Keywords</span></span>](../../language-reference/keywords/index.md)
- [<span data-ttu-id="4dc71-139">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="4dc71-139">Access Modifiers</span></span>](../../language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="4dc71-140">アクセシビリティ ドメイン</span><span class="sxs-lookup"><span data-stu-id="4dc71-140">Accessibility Domain</span></span>](../../language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="4dc71-141">アクセシビリティ レベル</span><span class="sxs-lookup"><span data-stu-id="4dc71-141">Accessibility Levels</span></span>](../../language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="4dc71-142">アクセス修飾子</span><span class="sxs-lookup"><span data-stu-id="4dc71-142">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="4dc71-143">public</span><span class="sxs-lookup"><span data-stu-id="4dc71-143">public</span></span>](../../language-reference/keywords/public.md)
- [<span data-ttu-id="4dc71-144">private</span><span class="sxs-lookup"><span data-stu-id="4dc71-144">private</span></span>](../../language-reference/keywords/private.md)
- [<span data-ttu-id="4dc71-145">protected</span><span class="sxs-lookup"><span data-stu-id="4dc71-145">protected</span></span>](../../language-reference/keywords/protected.md)
- [<span data-ttu-id="4dc71-146">internal</span><span class="sxs-lookup"><span data-stu-id="4dc71-146">internal</span></span>](../../language-reference/keywords/internal.md)
