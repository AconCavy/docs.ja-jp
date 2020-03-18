---
title: in (ジェネリック修飾子) - C# リファレンス
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713483"
---
# <a name="in-generic-modifier-c-reference"></a><span data-ttu-id="7e9ae-102">in (ジェネリック修飾子) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="7e9ae-102">in (Generic Modifier) (C# Reference)</span></span>

<span data-ttu-id="7e9ae-103">ジェネリック型パラメーターの `in` キーワードは、型パラメーターが反変であることを指定します。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-103">For generic type parameters, the `in` keyword specifies that the type parameter is contravariant.</span></span> <span data-ttu-id="7e9ae-104">`in` キーワードは、ジェネリック インターフェイスとデリゲートで使用できます。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-104">You can use the `in` keyword in generic interfaces and delegates.</span></span>

<span data-ttu-id="7e9ae-105">反変性は、ジェネリック パラメーターによって指定された型よりも弱い派生型を使用できるようにする機能です。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-105">Contravariance enables you to use a less derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="7e9ae-106">これにより、反変性のインターフェイスを実装するクラスの暗黙の型変換とデリゲート型の暗黙の型変換が可能となります。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-106">This allows for implicit conversion of classes that implement contravariant interfaces and implicit conversion of delegate types.</span></span> <span data-ttu-id="7e9ae-107">ジェネリック型パラメーターの共変性および反変性は参照型ではサポートされますが、値型ではサポートされません。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-107">Covariance and contravariance in generic type parameters are supported for reference types, but they are not supported for value types.</span></span>

<span data-ttu-id="7e9ae-108">型をジェネリック インターフェイスまたはデリゲートで反変として宣言できるのは、メソッドの戻り値の型ではなく、メソッドのパラメーターの型を定義する場合のみです。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-108">A type can be declared contravariant in a generic interface or delegate only if it defines the type of a method's parameters and not of a method's return type.</span></span> <span data-ttu-id="7e9ae-109">`In`、`ref`、`out` パラメーターはインバリアントである必要があります。これは、これらのパラメーターが共変でも反変でもないことを意味します。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-109">`In`, `ref`, and `out` parameters must be invariant, meaning they are neither covariant or contravariant.</span></span>

<span data-ttu-id="7e9ae-110">反変の型パラメーターを持つインターフェイスを使用すると、そのインターフェイスのメソッドは、インターフェイス型パラメーターによって指定された型よりも弱い派生型の引数を受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-110">An interface that has a contravariant type parameter allows its methods to accept arguments of less derived types than those specified by the interface type parameter.</span></span> <span data-ttu-id="7e9ae-111">たとえば、<xref:System.Collections.Generic.IComparer%601> インターフェイスでは、T 型が反変なので、`IComparer<Person>` が `IComparer<Employee>` を継承する場合、特別な変換メソッドを使用しなくても `Employee` 型のオブジェクトを `Person` 型のオブジェクトに割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-111">For example, in the <xref:System.Collections.Generic.IComparer%601> interface, type T is contravariant, you can assign an object of the `IComparer<Person>` type to an object of the `IComparer<Employee>` type without using any special conversion methods if `Employee` inherits `Person`.</span></span>

<span data-ttu-id="7e9ae-112">反変のデリゲートには、型は同じでありながらより弱い派生ジェネリック型パラメーターを持つ別のデリゲートを割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-112">A contravariant delegate can be assigned another delegate of the same type, but with a less derived generic type parameter.</span></span>

<span data-ttu-id="7e9ae-113">詳細については、「[共変性と反変性](../../programming-guide/concepts/covariance-contravariance/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-113">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>

## <a name="contravariant-generic-interface"></a><span data-ttu-id="7e9ae-114">反変のジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7e9ae-114">Contravariant generic interface</span></span>

<span data-ttu-id="7e9ae-115">次の例では、反変のジェネリック インターフェイスを宣言、拡張、および実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-115">The following example shows how to declare, extend, and implement a contravariant generic interface.</span></span> <span data-ttu-id="7e9ae-116">また、このインターフェイスを実装するクラスの暗黙的な変換を使用する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-116">It also shows how you can use implicit conversion for classes that implement this interface.</span></span>

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a><span data-ttu-id="7e9ae-117">反変の汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="7e9ae-117">Contravariant generic delegate</span></span>

<span data-ttu-id="7e9ae-118">次の例では、反変の汎用デリゲートを宣言、インスタンス化、および呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-118">The following example shows how to declare, instantiate, and invoke a contravariant generic delegate.</span></span> <span data-ttu-id="7e9ae-119">また、デリゲート型を暗黙的に変換する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="7e9ae-119">It also shows how you can implicitly convert a delegate type.</span></span>

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="7e9ae-120">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="7e9ae-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7e9ae-121">参照</span><span class="sxs-lookup"><span data-stu-id="7e9ae-121">See also</span></span>

- [<span data-ttu-id="7e9ae-122">out</span><span class="sxs-lookup"><span data-stu-id="7e9ae-122">out</span></span>](out-generic-modifier.md)
- [<span data-ttu-id="7e9ae-123">共変性と反変性</span><span class="sxs-lookup"><span data-stu-id="7e9ae-123">Covariance and Contravariance</span></span>](../../programming-guide/concepts/covariance-contravariance/index.md)
- [<span data-ttu-id="7e9ae-124">修飾子</span><span class="sxs-lookup"><span data-stu-id="7e9ae-124">Modifiers</span></span>](index.md)
