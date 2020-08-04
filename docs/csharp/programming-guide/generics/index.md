---
title: ジェネリック - C# プログラミング ガイド
description: ジェネリックについて説明します。 ジェネリック型では、コードの再利用、タイプ セーフ、およびパフォーマンスを最大化でき、コレクション クラスの作成によく使用されます。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: beef9c20e3ac62505bc7a4584b404637935de1dc
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299397"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="a0cd6-104">ジェネリック (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="a0cd6-104">Generics (C# Programming Guide)</span></span>

<span data-ttu-id="a0cd6-105">ジェネリックにより、.NET に型パラメーターという概念が導入されます。これを使用すると、クラスやメソッドがクライアント コードによって宣言され、インスタンス化されるまで、1 つ以上の型の指定を遅延させるクラスやメソッドを設計することができます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-105">Generics introduce the concept of type parameters to .NET, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="a0cd6-106">たとえば、ジェネリック型パラメーター `T` を使用すると、次に示すように、ランタイム キャストやボックス化操作を使うコストやリスクを発生させることなく他のクライアント コードで使用できる、単一のクラスを記述できます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-106">For example, by using a generic type parameter `T`, you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

<span data-ttu-id="a0cd6-107">ジェネリックのクラスとメソッドにより、非ジェネリックの場合には不可能な方法で、再利用性、タイプ セーフ、効率性が同時に実現されます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-107">Generic classes and methods combine reusability, type safety, and efficiency in a way that their non-generic counterparts cannot.</span></span> <span data-ttu-id="a0cd6-108">ジェネリックは、コレクションとそれを操作するメソッドとともに使用されるのが通常です。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-108">Generics are most frequently used with collections and the methods that operate on them.</span></span> <span data-ttu-id="a0cd6-109"><xref:System.Collections.Generic> 名前空間には、ジェネリック ベースのコレクション クラスがいくつか含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-109">The <xref:System.Collections.Generic> namespace contains several generic-based collection classes.</span></span> <span data-ttu-id="a0cd6-110"><xref:System.Collections.ArrayList> などの非ジェネリック コレクションは推奨されません。これらは互換性のために保持されています。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-110">The non-generic collections, such as <xref:System.Collections.ArrayList> are not recommended and are maintained for compatibility purposes.</span></span> <span data-ttu-id="a0cd6-111">詳細については、「[.NET のジェネリック](../../../standard/generics/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-111">For more information, see [Generics in .NET](../../../standard/generics/index.md).</span></span>

<span data-ttu-id="a0cd6-112">もちろん、カスタムのジェネリック型やジェネリック メソッドを作成して、タイプ セーフで効率的な独自の汎用ソリューションや設計パターンを実現することもできます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-112">Of course, you can also create custom generic types and methods to provide your own generalized solutions and design patterns that are type-safe and efficient.</span></span> <span data-ttu-id="a0cd6-113">次のコード例では、デモンストレーション用の簡単なジェネリックのリンク リスト クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-113">The following code example shows a simple generic linked-list class for demonstration purposes.</span></span> <span data-ttu-id="a0cd6-114">(通常は、独自のクラスを作成するのではなく、.NET で用意されている <xref:System.Collections.Generic.List%601> クラスを使用してください。)この例では、通常、具体的な型を使用して、リストに格納する項目の型を示す場面で、型パラメーター `T` を使用しています。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-114">(In most cases, you should use the <xref:System.Collections.Generic.List%601> class provided by .NET instead of creating your own.) The type parameter `T` is used in several locations where a concrete type would ordinarily be used to indicate the type of the item stored in the list.</span></span> <span data-ttu-id="a0cd6-115">このパラメーターは、次のように使用されています。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-115">It is used in the following ways:</span></span>

- <span data-ttu-id="a0cd6-116">`AddHead` メソッドのメソッド パラメーターの型として使用。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-116">As the type of a method parameter in the `AddHead` method.</span></span>
- <span data-ttu-id="a0cd6-117">入れ子になった `Node` クラスの `Data` プロパティの戻り値の型として使用。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-117">As the return type of the `Data` property in the nested `Node` class.</span></span>
- <span data-ttu-id="a0cd6-118">入れ子になったクラスのプライベート メンバー `data` の型として使用。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-118">As the type of the private member `data` in the nested class.</span></span>

 <span data-ttu-id="a0cd6-119">入れ子になった `Node` クラスで `T` を使用できることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-119">Note that `T` is available to the nested `Node` class.</span></span> <span data-ttu-id="a0cd6-120">`GenericList<T>` が `GenericList<int>` のような具象型でインスタンス化されると、`T` の部分はそれぞれ `int` に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-120">When `GenericList<T>` is instantiated with a concrete type, for example as a `GenericList<int>`, each occurrence of `T` will be replaced with `int`.</span></span>

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

<span data-ttu-id="a0cd6-121">次のコード例では、クライアント コードでジェネリックの `GenericList<T>` クラスを使用して、整数のリストを作成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-121">The following code example shows how client code uses the generic `GenericList<T>` class to create a list of integers.</span></span> <span data-ttu-id="a0cd6-122">このコードの型引数を変更するだけで、文字列やその他の任意のカスタム型のリストを作成するように簡単に修正できます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-122">Simply by changing the type argument, the following code could easily be modified to create lists of strings or any other custom type:</span></span>

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a><span data-ttu-id="a0cd6-123">ジェネリックの概要</span><span class="sxs-lookup"><span data-stu-id="a0cd6-123">Generics overview</span></span>

- <span data-ttu-id="a0cd6-124">ジェネリック型は、コードの再利用、タイプ セーフ、およびパフォーマンスを最大化するために使用します。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-124">Use generic types to maximize code reuse, type safety, and performance.</span></span>
- <span data-ttu-id="a0cd6-125">ジェネリックの最も一般的な用途は、コレクション クラスの作成です。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-125">The most common use of generics is to create collection classes.</span></span>
- <span data-ttu-id="a0cd6-126">.NET クラス ライブラリには、複数のジェネリック コレクション クラスが <xref:System.Collections.Generic> 名前空間に含まれています。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-126">The .NET class library contains several generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="a0cd6-127"><xref:System.Collections> 名前空間の <xref:System.Collections.ArrayList> などのクラスの代わりとして、できる限りこれらを使用してください。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-127">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>
- <span data-ttu-id="a0cd6-128">独自のジェネリック インターフェイス、クラス、メソッド、イベント、およびデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-128">You can create your own generic interfaces, classes, methods, events, and delegates.</span></span>
- <span data-ttu-id="a0cd6-129">ジェネリック クラスは、特定のデータ型のメソッドへのアクセスを有効にするように制限できます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-129">Generic classes may be constrained to enable access to methods on particular data types.</span></span>
- <span data-ttu-id="a0cd6-130">ジェネリック データ型で使用される型に関する情報は、実行時にリフレクションを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-130">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>

## <a name="related-sections"></a><span data-ttu-id="a0cd6-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0cd6-131">Related sections</span></span>

- [<span data-ttu-id="a0cd6-132">ジェネリック型パラメーター</span><span class="sxs-lookup"><span data-stu-id="a0cd6-132">Generic Type Parameters</span></span>](generic-type-parameters.md)
- [<span data-ttu-id="a0cd6-133">型パラメーターの制約</span><span class="sxs-lookup"><span data-stu-id="a0cd6-133">Constraints on Type Parameters</span></span>](constraints-on-type-parameters.md)
- [<span data-ttu-id="a0cd6-134">ジェネリック クラス</span><span class="sxs-lookup"><span data-stu-id="a0cd6-134">Generic Classes</span></span>](generic-classes.md)
- [<span data-ttu-id="a0cd6-135">ジェネリック インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a0cd6-135">Generic Interfaces</span></span>](generic-interfaces.md)
- [<span data-ttu-id="a0cd6-136">ジェネリック メソッド</span><span class="sxs-lookup"><span data-stu-id="a0cd6-136">Generic Methods</span></span>](generic-methods.md)
- [<span data-ttu-id="a0cd6-137">汎用デリゲート</span><span class="sxs-lookup"><span data-stu-id="a0cd6-137">Generic Delegates</span></span>](generic-delegates.md)
- [<span data-ttu-id="a0cd6-138">C++ テンプレートと C# ジェネリックの違い</span><span class="sxs-lookup"><span data-stu-id="a0cd6-138">Differences Between C++ Templates and C# Generics</span></span>](differences-between-cpp-templates-and-csharp-generics.md)
- [<span data-ttu-id="a0cd6-139">ジェネリックとリフレクション</span><span class="sxs-lookup"><span data-stu-id="a0cd6-139">Generics and Reflection</span></span>](generics-and-reflection.md)
- [<span data-ttu-id="a0cd6-140">ランタイムのジェネリック</span><span class="sxs-lookup"><span data-stu-id="a0cd6-140">Generics in the Run Time</span></span>](generics-in-the-run-time.md)

## <a name="c-language-specification"></a><span data-ttu-id="a0cd6-141">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="a0cd6-141">C# language specification</span></span>

<span data-ttu-id="a0cd6-142">詳細については、「[C# 言語の仕様](~/_csharplang/spec/types.md#constructed-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a0cd6-142">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="a0cd6-143">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0cd6-143">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="a0cd6-144">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a0cd6-144">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a0cd6-145">型</span><span class="sxs-lookup"><span data-stu-id="a0cd6-145">Types</span></span>](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [<span data-ttu-id="a0cd6-146">.NET のジェネリック</span><span class="sxs-lookup"><span data-stu-id="a0cd6-146">Generics in .NET</span></span>](../../../standard/generics/index.md)
