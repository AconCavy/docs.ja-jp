---
title: タプル型 - C# ガイド
description: C# の名前のないタプルと名前付きタプルについて
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 9ce9e1d4395d1a75f36004384ec215c615cd9802
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156910"
---
# <a name="c-tuple-types"></a><span data-ttu-id="cbfd3-103">C# のタプル型</span><span class="sxs-lookup"><span data-stu-id="cbfd3-103">C# tuple types</span></span>

<span data-ttu-id="cbfd3-104">C# のタプルは、軽量構文を使用して定義する型で、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-104">C# tuples are types that you define using a lightweight syntax.</span></span> <span data-ttu-id="cbfd3-105">構文がシンプルである、変換の規則が要素の数 ("カーディナリティ" と呼ばれます) と種類に基づく、コピー、等値テスト、および割り当ての規則が一貫している、などのメリットがあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-105">The advantages include a simpler syntax, rules for conversions based on number (referred to as cardinality) and types of elements, and consistent rules for copies, equality tests, and assignments.</span></span> <span data-ttu-id="cbfd3-106">そのトレードオフとして、タプルでは、継承に関連するオブジェクト指向の表現形式の一部がサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-106">As a tradeoff, tuples do not support some of the object-oriented idioms associated with inheritance.</span></span> <span data-ttu-id="cbfd3-107">概要については、[C# 7.0 の新機能のタプル](whats-new/csharp-7.md#tuples)に関する記事のセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-107">You can get an overview in the section on [tuples in the What's new in C# 7.0](whats-new/csharp-7.md#tuples) article.</span></span>

<span data-ttu-id="cbfd3-108">この記事では、C# 7.0 以降のバージョンでタプルに適用される言語の規則、タプルの使用方法、およびタプルを操作するための入門的ガイダンスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-108">In this article, you'll learn the language rules governing tuples in C# 7.0 and later versions, different ways to use them, and initial guidance on working with tuples.</span></span>

> [!NOTE]
> <span data-ttu-id="cbfd3-109">新しいタプル機能を使用するには、<xref:System.ValueTuple> 型が必要です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-109">The new tuples features require the <xref:System.ValueTuple> types.</span></span>
> <span data-ttu-id="cbfd3-110">型が含まれていないプラットフォームで使用する場合は、NuGet パッケージ [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-110">You must add the NuGet package [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) in order to use it on platforms that do not include the types.</span></span>
>
> <span data-ttu-id="cbfd3-111">これは、フレームワークで提供される型に依存するその他の言語機能に似ています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-111">This is similar to other language features that rely on types delivered in the framework.</span></span> <span data-ttu-id="cbfd3-112">たとえば、`async` インターフェイスに依存する `await` や `INotifyCompletion`、`IEnumerable<T>` に依存する LINQ などがあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-112">Examples include `async` and `await` relying on the `INotifyCompletion` interface, and LINQ relying on `IEnumerable<T>`.</span></span> <span data-ttu-id="cbfd3-113">ただし、.NET がプラットフォームにさらに依存しなくなりつつあるため、配信メカニズムもそれに応じて変わりつつあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-113">However, the delivery mechanism is changing as .NET is becoming more platform independent.</span></span> <span data-ttu-id="cbfd3-114">.NET Framework が、言語コンパイラと同じ周期で配布されるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-114">The .NET Framework may not always ship on the same cadence as the language compiler.</span></span> <span data-ttu-id="cbfd3-115">新しい言語機能が新しい型に依存する場合、それらの型は、言語機能の配布時に NuGet パッケージとして入手できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-115">When new language features rely on new types, those types will be available as NuGet packages when the language features ship.</span></span> <span data-ttu-id="cbfd3-116">これらの新しい型は .NET 標準 API に追加され、フレームワークの一部として配信されるため、NuGet パッケージは必要なくなります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-116">As these new types get added to the .NET Standard API and delivered as part of the framework, the NuGet package requirement will be removed.</span></span>

<span data-ttu-id="cbfd3-117">詳しく見ていく前に、新しいタプルのサポートを追加した理由について説明します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-117">Let's start with the reasons for adding new tuple support.</span></span> <span data-ttu-id="cbfd3-118">メソッドが返すのは 1 つのオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-118">Methods return a single object.</span></span> <span data-ttu-id="cbfd3-119">タプルを使用すると、その 1 つのオブジェクトに複数の値を簡単にパッケージできます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-119">Tuples enable you to package multiple values in that single object more easily.</span></span>

<span data-ttu-id="cbfd3-120">.NET Framework には `Tuple` ジェネリック クラスが既にありますが、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-120">The .NET Framework already has generic `Tuple` classes.</span></span> <span data-ttu-id="cbfd3-121">このクラスには 2 つの大きな制限がありました。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-121">These classes, however, had two major limitations.</span></span> <span data-ttu-id="cbfd3-122">1 つは、`Tuple` クラスのプロパティに `Item1`、`Item2` という名前が付けられるというものです。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-122">For one, the `Tuple` classes named their properties `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="cbfd3-123">その名前にはセマンティック情報が保持されていません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-123">Those names carry no semantic information.</span></span> <span data-ttu-id="cbfd3-124">つまり、この `Tuple` 型を使用しても、各プロパティの情報を伝達することはできません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-124">Using these `Tuple` types does not enable communicating the meaning of each of the properties.</span></span> <span data-ttu-id="cbfd3-125">新しい言語機能を使用すると、タプルの要素に意味的にわかりやすい名前を宣言して使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-125">The new language features enable you to declare and use semantically meaningful names for the elements in a tuple.</span></span>

<span data-ttu-id="cbfd3-126">`Tuple` クラスは参照型であるため、パフォーマンスの問題が発生しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-126">The `Tuple` classes cause more performance concerns because they are reference types.</span></span> <span data-ttu-id="cbfd3-127">`Tuple` 型を使用するには、オブジェクトを割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-127">Using one of the `Tuple` types means allocating objects.</span></span> <span data-ttu-id="cbfd3-128">ホット パスでは、多数の小さいオブジェクトの割り当てがアプリケーションのパフォーマンスに大きな影響を及ぼすことがあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-128">On hot paths, allocating many small objects can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="cbfd3-129">そのため、タプルの言語サポートでは、新しい `ValueTuple` 構造体を活用します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-129">Therefore, the language support for tuples leverages the new `ValueTuple` structs.</span></span>

<span data-ttu-id="cbfd3-130">`class` や `struct` を作成して複数の要素を伝達すれば、この弱点を回避できますが、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-130">To avoid those deficiencies, you could create a `class` or a `struct` to carry multiple elements.</span></span> <span data-ttu-id="cbfd3-131">その分、手間が増え、設計の意図がわかりにくくなります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-131">Unfortunately, that's more work for you, and it obscures your design intent.</span></span> <span data-ttu-id="cbfd3-132">`struct` や `class` を作成すると、データと動作の両方で型を定義しなければなりませんが、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-132">Making a `struct` or `class` implies that you are defining a type with both data and behavior.</span></span> <span data-ttu-id="cbfd3-133">1 つのオブジェクトに複数の値を格納したいだけという状況もよくあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-133">Many times, you simply want to store multiple values in a single object.</span></span>

<span data-ttu-id="cbfd3-134">これらの機能と `ValueTuple` ジェネリック構造体では、タプル型に動作 (メソッド) を追加できないという規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-134">The language features and the `ValueTuple` generic structs enforce the rule that you cannot add any behavior (methods) to these tuple types.</span></span>
<span data-ttu-id="cbfd3-135">すべての `ValueTuple` 型が "*mutable 構造体*" で、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-135">All the `ValueTuple` types are *mutable structs*.</span></span> <span data-ttu-id="cbfd3-136">各メンバー フィールドがパブリック フィールドであるため、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-136">Each member field is a public field.</span></span> <span data-ttu-id="cbfd3-137">非常に軽量です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-137">That makes them very lightweight.</span></span> <span data-ttu-id="cbfd3-138">ただし、不変性が重要な場合は、タプルを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-138">However, that means tuples should not be used where immutability is important.</span></span>

<span data-ttu-id="cbfd3-139">タプルは、`class` 型や `struct` 型に比べて、シンプルで柔軟なデータ コンテナーです。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-139">Tuples are both simpler and more flexible data containers than `class` and `struct` types.</span></span> <span data-ttu-id="cbfd3-140">両者の違いを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-140">Let's explore those differences.</span></span>

## <a name="named-and-unnamed-tuples"></a><span data-ttu-id="cbfd3-141">名前付きのタプルと名前がないタプル</span><span class="sxs-lookup"><span data-stu-id="cbfd3-141">Named and unnamed tuples</span></span>

<span data-ttu-id="cbfd3-142">既存の `ValueTuple` 型で定義されたプロパティと同様、`Item1` 構造体のフィールドには `Item2`、`Item3`、`Tuple` といった名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-142">The `ValueTuple` struct has fields named `Item1`, `Item2`, `Item3`, and so on, similar to the properties defined in the existing `Tuple` types.</span></span>
<span data-ttu-id="cbfd3-143">"*名前のないタプル*" には、この名前しか使用できません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-143">These names are the only names you can use for *unnamed tuples*.</span></span> <span data-ttu-id="cbfd3-144">タプルに代替フィールド名を付けなかった場合は、名前のないタプルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-144">When you do not provide any alternative field names to a tuple, you've created an unnamed tuple:</span></span>

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

<span data-ttu-id="cbfd3-145">前の例のタプルは、リテラル定数を使って初期化されており、C# 7.1 の*タプル フィールド名プロジェクション*を使って作成された要素名はありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-145">The tuple in the previous example was initialized using literal constants and won't have element names created using *tuple field name projections* in C# 7.1.</span></span>

<span data-ttu-id="cbfd3-146">タプルを初期化する際に、新しい機能を使用して、各フィールドにわかりやすい名前を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-146">However, when you initialize a tuple, you can use new language features that give better names to each field.</span></span> <span data-ttu-id="cbfd3-147">これによって、"*名前付きタプル*" が作成されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-147">Doing so creates a *named tuple*.</span></span>
<span data-ttu-id="cbfd3-148">名前付きタプルには `Item1`、`Item2`、`Item3` という名前の要素がまだ存在しますが、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-148">Named tuples still have elements named `Item1`, `Item2`, `Item3` and so on.</span></span>
<span data-ttu-id="cbfd3-149">名前を付けた要素に対してシノニムも設定されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-149">But they also have synonyms for any of those elements that you have named.</span></span>
<span data-ttu-id="cbfd3-150">名前付きタプルを作成するには、各要素の名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-150">You create a named tuple by specifying the names for each element.</span></span> <span data-ttu-id="cbfd3-151">たとえば、タプル初期化の一環として名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-151">One way is to specify the names as part of the tuple initialization:</span></span>

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

<span data-ttu-id="cbfd3-152">コンパイラと言語によってシノニムが処理されるため、名前付きタプルを効果的に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-152">These synonyms are handled by the compiler and the language so that you can use named tuples effectively.</span></span> <span data-ttu-id="cbfd3-153">IDE やエディターは Roslyn API を使用して、セマンティック名を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-153">IDEs and editors can read these semantic names using the Roslyn APIs.</span></span> <span data-ttu-id="cbfd3-154">これにより、同じアセンブリ内の任意の場所で、セマンティック名によって名前付きタプルの要素を参照できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-154">You can reference the elements of a named tuple by those semantic names anywhere in the same assembly.</span></span> <span data-ttu-id="cbfd3-155">定義した名前は、コンパイル済み出力が生成されるときに、対応する `Item*` に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-155">The compiler replaces the names you've defined with `Item*` equivalents when generating the compiled output.</span></span> <span data-ttu-id="cbfd3-156">これらの要素に設定した名前は、コンパイルされた Microsoft Intermediate Language (MSIL) には含まれません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-156">The compiled Microsoft Intermediate Language (MSIL) does not include the names you've given these elements.</span></span>

<span data-ttu-id="cbfd3-157">C# 7.1 以降、タプルのフィールド名は、タプルの初期化に使用した変数によって指定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-157">Beginning with C# 7.1, the field names for a tuple may be provided from the variables used to initialize the tuple.</span></span> <span data-ttu-id="cbfd3-158">これは、 **[タプル プロジェクション初期化子](#tuple-projection-initializers)** と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-158">This is referred to as **[tuple projection initializers](#tuple-projection-initializers)**.</span></span> <span data-ttu-id="cbfd3-159">次のコードでは、要素 `accumulation` (整数)、および `count` (倍精度浮動小数点型) で `sum` という名前のタプルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-159">The following code creates a tuple named `accumulation` with elements `count` (an integer), and `sum` (a double).</span></span>

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

<span data-ttu-id="cbfd3-160">コンパイラは、パブリック メソッドまたはプロパティから返されたタプルに指定されている名前を伝える必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-160">The compiler must communicate those names you created for tuples that are returned from public methods or properties.</span></span> <span data-ttu-id="cbfd3-161">このような場合、コンパイラはメソッドに <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> 属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-161">In those cases, the compiler adds a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> attribute on the method.</span></span> <span data-ttu-id="cbfd3-162">この属性には、タプルの各要素に付けられた名前が含まれた <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> リスト プロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-162">This attribute contains a <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> list property that contains the names given to each of the elements in the tuple.</span></span>

> [!NOTE]
> <span data-ttu-id="cbfd3-163">Visual Studio などの開発ツールも、そのメタデータを読み取り、メタデータ フィールド名を使用する IntelliSense などの機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-163">Development Tools, such as Visual Studio, also read that metadata, and provide IntelliSense and other features using the metadata field names.</span></span>

<span data-ttu-id="cbfd3-164">名前付きタプルを相互に割り当てるための規則を理解するには、新しいタプルと `ValueTuple` 型の基本を理解しておくことが重要です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-164">It is important to understand these underlying fundamentals of the new tuples and the `ValueTuple` type in order to understand the rules for assigning named tuples to each other.</span></span>

## <a name="tuple-projection-initializers"></a><span data-ttu-id="cbfd3-165">タプル プロジェクション初期化子</span><span class="sxs-lookup"><span data-stu-id="cbfd3-165">Tuple projection initializers</span></span>

<span data-ttu-id="cbfd3-166">一般に、タプル プロジェクション初期化子は、タプルの初期化ステートメントの右側にある変数またはフィールド名を使用して機能します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-166">In general, tuple projection initializers work by using the variable or field names from the right-hand side of a tuple initialization statement.</span></span>
<span data-ttu-id="cbfd3-167">明示的な名前が指定された場合は、射影された名前より優先されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-167">If an explicit name is given, that takes precedence over any projected name.</span></span> <span data-ttu-id="cbfd3-168">たとえば、次の初期化子では、要素は `explicitFieldOne` や `explicitFieldTwo` ではなく、`localVariableOne` と `localVariableTwo` になります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-168">For example, in the following initializer, the elements are `explicitFieldOne` and `explicitFieldTwo`, not `localVariableOne` and `localVariableTwo`:</span></span>

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

<span data-ttu-id="cbfd3-169">明示的な名前が指定されていないフィールドの場合、適用可能な暗黙的な名前が射影されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-169">For any field where an explicit name is not provided, an applicable implicit name is projected.</span></span> <span data-ttu-id="cbfd3-170">明示的または暗黙的のいずれかで、セマンティック名を指定するための要件はありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-170">There is no requirement to provide semantic names, either explicitly or implicitly.</span></span> <span data-ttu-id="cbfd3-171">次の初期化子には、フィールド名 `Item1` があり、その値は `42` と `stringContent` で、その値は "The answer to everything" です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-171">The following initializer has     field names `Item1`, whose value is `42` and `stringContent`, whose value is "The answer to everything":</span></span>

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

<span data-ttu-id="cbfd3-172">候補フィールド名がタプル フィールドに射影されない場合の条件は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-172">There are two conditions where candidate field names are not projected onto the tuple field:</span></span>

1. <span data-ttu-id="cbfd3-173">候補名が予約されているタプル名の場合。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-173">When the candidate name is a reserved tuple name.</span></span> <span data-ttu-id="cbfd3-174">例としては、`Item3`、`ToString` または `Rest` です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-174">Examples include `Item3`, `ToString`, or `Rest`.</span></span>
1. <span data-ttu-id="cbfd3-175">候補名が、別のタプル フィールド名 (明示的または暗黙的のいずれか) の複製である場合。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-175">When the candidate name is a duplicate of another tuple field name, either explicit or implicit.</span></span>

<span data-ttu-id="cbfd3-176">これらの条件によってあいまいさを回避します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-176">These conditions avoid ambiguity.</span></span> <span data-ttu-id="cbfd3-177">この名前がタプルのフィールドのフィールド名として使用される場合、あいまいさの原因となります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-177">These names would cause an ambiguity if they were used as the field names for a field in a tuple.</span></span> <span data-ttu-id="cbfd3-178">この条件はどちらも、コンパイル時エラーを発生させることはありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-178">Neither of these conditions cause compile-time errors.</span></span> <span data-ttu-id="cbfd3-179">代わりに、射影された名前のない要素には、射影されたセマンティック名がありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-179">Instead, the elements without projected names do not have semantic names projected for them.</span></span>  <span data-ttu-id="cbfd3-180">これらの条件の例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-180">The following examples demonstrate these conditions:</span></span>

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

<span data-ttu-id="cbfd3-181">これらの条件は、タプル フィールド名プロジェクションが利用できなかった場合、C# 7.0 で記述されたコードに対する重大な変更になるため、コンパイラ エラーが発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-181">These situations do not cause compiler errors because that would be a breaking change for code written with C# 7.0, when tuple field name projections were not available.</span></span>

## <a name="equality-and-tuples"></a><span data-ttu-id="cbfd3-182">等値とタプル</span><span class="sxs-lookup"><span data-stu-id="cbfd3-182">Equality and tuples</span></span>

<span data-ttu-id="cbfd3-183">C# 7.3 以降では、タプル型で `==` および `!=` 演算子がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-183">Beginning with C# 7.3, tuple types support the `==` and `!=` operators.</span></span> <span data-ttu-id="cbfd3-184">これらの演算子は、左の引数の各メンバーと右の引数の各メンバーを順番に比較することによって機能します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-184">These operators work by comparing each member of the left argument to each member of the right argument in order.</span></span> <span data-ttu-id="cbfd3-185">これらの比較はショートさせます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-185">These comparisons short-circuit.</span></span> <span data-ttu-id="cbfd3-186">これらは、ペアが等値でなくなるとすぐにメンバーの評価を停止します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-186">They will stop evaluating members as soon as one pair is not equal.</span></span> <span data-ttu-id="cbfd3-187">次のコード例では `==` を使用しますが、比較規則がすべて `!=` に適用されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-187">The following code examples use `==`, but the comparison rules all apply to `!=`.</span></span> <span data-ttu-id="cbfd3-188">次のコード例は、整数の 2 つのペアの等値比較を示しています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-188">The following code example shows an equality comparison for two pairs of integers:</span></span>

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

<span data-ttu-id="cbfd3-189">タプルの等値テストをより簡単にするルールがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-189">There are several rules that make tuple equality tests more convenient.</span></span> <span data-ttu-id="cbfd3-190">次のコードに示すように、いずれかのタプルが null 許容タプルの場合、タプルの等値性によって[リフト変換](~/_csharplang/spec/conversions.md#lifted-conversion-operators)が実行されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-190">Tuple equality performs [lifted conversions](~/_csharplang/spec/conversions.md#lifted-conversion-operators) if one of the tuples is a nullable tuple, as shown in the following code:</span></span>

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

<span data-ttu-id="cbfd3-191">タプルの等値性では、両方のタプルの各メンバーに対して暗黙の変換も実行されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-191">Tuple equality also performs implicit conversions on each member of both tuples.</span></span> <span data-ttu-id="cbfd3-192">これらには、リフト変換、拡大変換などの暗黙の型変換も含まれます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-192">These include lifted conversions, widening conversions, or other implicit conversions.</span></span> <span data-ttu-id="cbfd3-193">次の例は、整数から long 型への暗黙の型変換によって、整数の 2 つのタプルを long 型の 2 つのタプルと比較できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-193">The following examples show that an integer 2-tuple can be compared to a long 2-tuple because of the implicit conversion from integer to long:</span></span>

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

<span data-ttu-id="cbfd3-194">タプルのメンバーの名前は、等値性のテストに参加しません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-194">The names of the tuple members do not participate in tests for equality.</span></span> <span data-ttu-id="cbfd3-195">ただし、いずれかのオペランドが明示的な名前を持つタプル リテラルの場合、コンパイラは、この名前が他のオペランドの名前と一致しない場合、警告 CS8383 を生成します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-195">However, if one of the operands is a tuple literal with explicit names, the compiler generates warning CS8383 if those names do not match the names of the other operand.</span></span>
<span data-ttu-id="cbfd3-196">両方のオペランドがタプル リテラルである場合、警告は次の例に示すように右オペランドに含まれます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-196">In the case where both operands are tuple literals, the warning is on the right operand as shown in the following example:</span></span>

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

<span data-ttu-id="cbfd3-197">最後に、タプルに入れ子になったタプルが含まれることがあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-197">Finally, tuples may contain nested tuples.</span></span> <span data-ttu-id="cbfd3-198">タプルの等値性によって、次の例に示すように、入れ子になったタプルを通じて各オペランドの "シェイプ" が比較されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-198">Tuple equality compares the "shape" of each operand through nested tuples as shown in the following example:</span></span>

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

<span data-ttu-id="cbfd3-199">シェイプが異なる 2 つのタプルの等値性 (または非等値性) を比較すると、コンパイル時エラーになります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-199">It's a compile time error to compare two tuples for equality (or inequality) when they have different shapes.</span></span> <span data-ttu-id="cbfd3-200">コンパイラは、入れ子になったタプルを比較するためにその分解を試行することはありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-200">The compiler won't attempt any deconstruction of nested tuples in order to compare them.</span></span>

## <a name="assignment-and-tuples"></a><span data-ttu-id="cbfd3-201">割り当てとタプル</span><span class="sxs-lookup"><span data-stu-id="cbfd3-201">Assignment and tuples</span></span>

<span data-ttu-id="cbfd3-202">この言語では、要素の数が同じタプル型間での割り当てがサポートされています。ここでは、右側の各要素をそれに対応する左側の要素に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-202">The language supports assignment between tuple types that have the same number of elements, where each right-hand side element can be implicitly converted to its corresponding left-hand side element.</span></span> <span data-ttu-id="cbfd3-203">他の変換は、割り当てでは考慮されません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-203">Other conversions aren't considered for assignments.</span></span> <span data-ttu-id="cbfd3-204">あるタプルを、シェイプが異なる別のタプルに割り当てると、コンパイル時エラーになります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-204">It's a compile time error to assign one tuple to another when they have different shapes.</span></span> <span data-ttu-id="cbfd3-205">コンパイラは、入れ子になったタプルを割り当てるためにその分解を試行することはありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-205">The compiler won't attempt any deconstruction of nested tuples in order to assign them.</span></span>
<span data-ttu-id="cbfd3-206">タプル型間で許可されている割り当ての種類を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-206">Let's look at the kinds of assignments that are allowed between tuple types.</span></span>

<span data-ttu-id="cbfd3-207">以降の例で使用されている変数について考えます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-207">Consider these variables used in the following examples:</span></span>

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

<span data-ttu-id="cbfd3-208">最初の 2 つの変数 `unnamed` および `anonymous` では、要素にセマンティック名が割り当てられていません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-208">The first two variables, `unnamed` and `anonymous` do not have semantic names provided for the elements.</span></span> <span data-ttu-id="cbfd3-209">フィールド名は `Item1` と `Item2` になります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-209">The field names are `Item1` and `Item2`.</span></span>
<span data-ttu-id="cbfd3-210">最後の 2 つの変数 `named` および `differentName` では、要素にセマンティック名が付けられています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-210">The last two variables, `named` and `differentName` have semantic names given for the elements.</span></span> <span data-ttu-id="cbfd3-211">この 2 つのタプルでは、要素名が異なっています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-211">These two tuples have different names for the elements.</span></span>

<span data-ttu-id="cbfd3-212">この 4 つのタプルに含まれている要素の数 ("カーディナリティ" と呼ばれます) と要素の型は同じです。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-212">All four of these tuples have the same number of elements (referred to as 'cardinality') and the types of those elements are identical.</span></span> <span data-ttu-id="cbfd3-213">このため、これらの割り当てはすべて機能します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-213">Therefore, all of these assignments work:</span></span>

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

<span data-ttu-id="cbfd3-214">タプルの名前が割り当てられていないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-214">Notice that the names of the tuples are not assigned.</span></span> <span data-ttu-id="cbfd3-215">要素の値は、タプルの要素の順序に従って割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-215">The values of the elements are assigned following the order of the elements in the tuple.</span></span>

<span data-ttu-id="cbfd3-216">要素の型または数が異なるタプルを割り当てることはできません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-216">Tuples of different types or numbers of elements are not assignable:</span></span>

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="cbfd3-217">メソッドの戻り値としてのタプル</span><span class="sxs-lookup"><span data-stu-id="cbfd3-217">Tuples as method return values</span></span>

<span data-ttu-id="cbfd3-218">タプルはメソッドの戻り値として使用できます。これはタプルの一般的な使用方法の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-218">One of the most common uses for tuples is as a method return value.</span></span> <span data-ttu-id="cbfd3-219">その例を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-219">Let's walk through one example.</span></span> <span data-ttu-id="cbfd3-220">数値シーケンスの標準偏差を計算する次のメソッドについて考えます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-220">Consider this method that computes the standard deviation for a sequence of numbers:</span></span>

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> <span data-ttu-id="cbfd3-221">この例では、未修正のサンプル標準偏差を計算します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-221">These examples compute the uncorrected sample standard deviation.</span></span>
> <span data-ttu-id="cbfd3-222">修正後のサンプル標準偏差式は、`Average` 拡張メソッドで行われるのと同様に、平均値との差の二乗和を、N ではなく (N-1) で除算します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-222">The corrected sample standard deviation formula would divide the sum of the squared differences from the mean by (N-1) instead of N, as the `Average` extension method does.</span></span> <span data-ttu-id="cbfd3-223">標準偏差のこうした数式の間に生じる差の詳細については、統計値のテキストを参照してください。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-223">Consult a statistics text for more details on the differences between these formulas for standard deviation.</span></span>

<span data-ttu-id="cbfd3-224">上のコードは、標準偏差の教科書どおりの数式に従っています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-224">The preceding code follows the textbook formula for the standard deviation.</span></span> <span data-ttu-id="cbfd3-225">正しい答えが生成されますが、非効率的な実装です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-225">It produces the correct answer, but it's an inefficient implementation.</span></span> <span data-ttu-id="cbfd3-226">このメソッドは、シーケンスを 2 回列挙します。1 回は平均値を生成するため、もう 1 回は平均値との差を 2 乗して、その平均値を生成するためです</span><span class="sxs-lookup"><span data-stu-id="cbfd3-226">This method enumerates the sequence twice: Once to produce the average, and once to produce the average of the square of the difference of the average.</span></span>
<span data-ttu-id="cbfd3-227">(前述のとおり、LINQ クエリは遅延評価されるため、平均値との差と、その差の平均値の計算で生成される列挙は 1 つだけです)。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-227">(Remember that LINQ queries are evaluated lazily, so the computation of the differences from the mean and the average of those differences makes only one enumeration.)</span></span>

<span data-ttu-id="cbfd3-228">シーケンスの列挙を 1 つだけ使用して標準偏差を計算する、別の数式があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-228">There is an alternative formula that computes standard deviation using only one enumeration of the sequence.</span></span>  <span data-ttu-id="cbfd3-229">この計算では、シーケンスを列挙しながら、2 つの値が生成されます。1 つはシーケンス内のすべての項目の合計、もう 1 つは各値の二乗和です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-229">This computation produces two values as it enumerates the sequence: the sum of all items in the sequence, and the sum of the each value squared:</span></span>

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

<span data-ttu-id="cbfd3-230">このバージョンでは、シーケンスを 1 回だけ列挙しますが、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-230">This version enumerates the sequence exactly once.</span></span> <span data-ttu-id="cbfd3-231">再利用可能なコードとは言えません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-231">But it's not reusable code.</span></span> <span data-ttu-id="cbfd3-232">操作を続けていくと、さまざまな統計計算処理の多くが、シーケンス内の項目数、シーケンスの合計、およびシーケンスの二乗和を使用していることがわかります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-232">As you keep working, you'll find that many different statistical computations use the number of items in the sequence, the sum of the sequence, and the sum of the squares of the sequence.</span></span> <span data-ttu-id="cbfd3-233">このメソッドをリファクタリングし、その 3 つの値すべてを生成するユーティリティ メソッドを作成しましょう。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-233">Let's refactor this method and write a utility method that produces all three of those values.</span></span> <span data-ttu-id="cbfd3-234">3 つすべての値をタプルとして戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-234">All three values can be returned as a tuple.</span></span>

<span data-ttu-id="cbfd3-235">このメソッドを更新して、列挙中に計算された 3 つの値をタプルに格納しましょう。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-235">Let's update this method so the three values computed during the enumeration are stored in a tuple.</span></span> <span data-ttu-id="cbfd3-236">そうすると、次のバージョンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-236">That creates this version:</span></span>

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

<span data-ttu-id="cbfd3-237">Visual Studio のリファクタリング サポートにより、主要な統計情報の機能をプライベート メソッドに抽出できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-237">Visual Studio's Refactoring support makes it easy to extract the functionality for the core statistics into a private method.</span></span> <span data-ttu-id="cbfd3-238">これにより、3 つの値 `private static`、`Sum`、`SumOfSquares` を含むタプル型を返す `Count` メソッドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-238">That gives you a `private static` method that returns the tuple type with the three values of `Sum`, `SumOfSquares`, and `Count`:</span></span>

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]

<span data-ttu-id="cbfd3-239">編集を手動ですばやく行う必要がある場合は、使用できるオプションが他にもいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-239">The language enables a couple more options that you can use, if you want to make a few quick edits by hand.</span></span> <span data-ttu-id="cbfd3-240">まず、`var` 宣言を使用することで、`ComputeSumAndSumOfSquares` メソッド呼び出しのタプルの結果を初期化できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-240">First, you can use the `var` declaration to initialize the tuple result from the `ComputeSumAndSumOfSquares` method call.</span></span> <span data-ttu-id="cbfd3-241">`ComputeSumAndSumOfSquares` メソッド内に異なる 3 つの変数を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-241">You can also create three discrete variables inside the `ComputeSumAndSumOfSquares` method.</span></span> <span data-ttu-id="cbfd3-242">最終的なバージョンを次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-242">The final version is shown in the following code:</span></span>

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

<span data-ttu-id="cbfd3-243">この最終バージョンは、この 3 つの値を必要とするすべてのメソッド、またはそのサブセットで使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-243">This final version can be used for any method that needs those three values, or any subset of them.</span></span>

<span data-ttu-id="cbfd3-244">このようなタプルを返すメソッドで要素の名前を管理するオプションが他にもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-244">The language supports other options in managing the names of the elements in these tuple-returning methods.</span></span>

<span data-ttu-id="cbfd3-245">戻り値の宣言からフィールド名を削除して、名前のないタプルを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-245">You can remove the field names from the return value declaration and return an unnamed tuple:</span></span>

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

<span data-ttu-id="cbfd3-246">このタプルのフィールドは、`Item1`、`Item2`、および `Item3` という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-246">The fields of this tuple are named `Item1`, `Item2`, and `Item3`.</span></span>
<span data-ttu-id="cbfd3-247">メソッドから返されたタプルの要素には、セマンティック名を指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-247">It's recommended that you provide semantic names to the elements of tuples returned from methods.</span></span>

<span data-ttu-id="cbfd3-248">LINQ クエリを作成するときも、タプルが便利です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-248">Another idiom where tuples can be useful is when you are authoring LINQ queries.</span></span> <span data-ttu-id="cbfd3-249">最終的な予測される結果では、選択されているオブジェクトのプロパティのすべてではなく、一部が含まれる場合が一般的です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-249">The final projected result often contains some, but not all, of the properties of the objects being selected.</span></span>

<span data-ttu-id="cbfd3-250">従来、クエリの結果は、匿名型のオブジェクトのシーケンスに射影していましたが、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-250">You would traditionally project the results of the query into a sequence of objects that were an anonymous type.</span></span> <span data-ttu-id="cbfd3-251">この方法には多くの制限が伴いました。メソッドの戻り値の型では、匿名型に名前を付けるのが簡単ではなかったからです。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-251">That presented many limitations, primarily because anonymous types could not conveniently be named in the return type for a method.</span></span> <span data-ttu-id="cbfd3-252">代替手段として `object` や `dynamic` を結果の型に使用すると、パフォーマンス コストは大きくなります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-252">Alternatives using `object` or `dynamic` as the type of the result came with significant performance costs.</span></span>

<span data-ttu-id="cbfd3-253">タプル型のシーケンスを返すのは簡単です。要素の名前と型は、コンパイル時に IDE ツールで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-253">Returning a sequence of a tuple type is easy, and the names and types of the elements are available at compile time and through IDE tools.</span></span>
<span data-ttu-id="cbfd3-254">たとえば、次の ToDo アプリケーションを考えてみます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-254">For example, consider a ToDo application.</span></span> <span data-ttu-id="cbfd3-255">ToDo リストの 1 つのエントリを表すために、次のようなクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-255">You might define a class similar to the following to represent a single entry in the ToDo list:</span></span>

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

<span data-ttu-id="cbfd3-256">モバイル アプリケーションでサポートされるのは、タイトルしか表示されないコンパクト形式の現在の ToDo 項目です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-256">Your mobile applications may support a compact form of the current ToDo items that only displays the title.</span></span> <span data-ttu-id="cbfd3-257">その LINQ クエリでは、ID とタイトルのみが含まれるプロジェクションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-257">That LINQ query would make a projection that includes only the ID and the title.</span></span> <span data-ttu-id="cbfd3-258">タプルのシーケンスを返すメソッドは、その設計を適切に表現しています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-258">A method that returns a sequence of tuples expresses that design well:</span></span>

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> <span data-ttu-id="cbfd3-259">C# 7.1 では、タプル プロジェクションを使用して、匿名型で名前が付けられたプロパティと同様の方法で、要素を使用する名前付きタプルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-259">In C# 7.1, tuple projections enable you to create named tuples using elements, in a manner similar to the property naming in anonymous types.</span></span> <span data-ttu-id="cbfd3-260">上記のコードでは、クエリ プロジェクションの `select` ステートメントで、要素 `ID` と `Title` を含むタプルを作成します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-260">In the above code, the `select` statement in the query projection creates a tuple that has elements `ID` and `Title`.</span></span>

<span data-ttu-id="cbfd3-261">名前付きタプルは、署名に含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-261">The named tuple can be part of the signature.</span></span> <span data-ttu-id="cbfd3-262">これによって、コンパイラと IDE ツールは静的チェックを行い、結果が正しく使用されていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-262">It lets the compiler and IDE tools provide static checking that you are using the result correctly.</span></span> <span data-ttu-id="cbfd3-263">名前付きタプルには静的情報も含まれているため、リフレクション、動的バインドなど、コストのかかるランタイム機能を使用して結果を操作する必要がありません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-263">The named tuple also carries the static type information so there is no need to use expensive run time features like reflection or dynamic binding to work with the results.</span></span>

## <a name="deconstruction"></a><span data-ttu-id="cbfd3-264">分解</span><span class="sxs-lookup"><span data-stu-id="cbfd3-264">Deconstruction</span></span>

<span data-ttu-id="cbfd3-265">タプル内のすべての項目を展開するには、メソッドによって返されるタプルを*分解*します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-265">You can unpackage all the items in a tuple by *deconstructing* the tuple returned by a method.</span></span> <span data-ttu-id="cbfd3-266">タプルは 3 とおりの方法で分解できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-266">There are three different approaches to deconstructing tuples.</span></span>  <span data-ttu-id="cbfd3-267">まず、かっこの中で各フィールドの型を明示的に宣言して、タプルの要素ごとに個別の変数を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-267">First, you can explicitly declare the type of each field inside parentheses to create discrete variables for each of the elements in the tuple:</span></span>

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

<span data-ttu-id="cbfd3-268">また、かっこの外に `var` キーワードを使用して、タプルの各フィールドに対して暗黙的に型指定された変数を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-268">You can also declare implicitly typed variables for each field in a tuple by using the `var` keyword outside the parentheses:</span></span>

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

<span data-ttu-id="cbfd3-269">`var` キーワードは、かっこ内のいずれか 1 つの変数宣言に使用することも、すべての変数宣言に使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-269">It is also legal to use the `var` keyword with any, or all of the variable declarations inside the parentheses.</span></span>

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

<span data-ttu-id="cbfd3-270">タプル内のフィールドすべての型が同じでも、かっこ外では使用できない型があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-270">You cannot use a specific type outside the parentheses, even if every field in the tuple has the same type.</span></span>

<span data-ttu-id="cbfd3-271">既存の宣言を使用してタプルを分解することもできます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-271">You can deconstruct tuples with existing declarations as well:</span></span>

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> <span data-ttu-id="cbfd3-272">既存の宣言をかっこ内の宣言と混在させることはできません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-272">You cannot mix existing declarations with declarations inside the parentheses.</span></span> <span data-ttu-id="cbfd3-273">たとえば、`(var x, y) = MyMethod();` は許可されません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-273">For instance, the following is not allowed: `(var x, y) = MyMethod();`.</span></span> <span data-ttu-id="cbfd3-274">*x* はかっこ内で宣言されており、*y* は他の場所で以前に宣言されているため、これによりエラー CS8184 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-274">This produces error CS8184 because *x* is declared inside the parentheses and *y* is previously declared elsewhere.</span></span>

### <a name="deconstructing-user-defined-types"></a><span data-ttu-id="cbfd3-275">ユーザー定義型の分解</span><span class="sxs-lookup"><span data-stu-id="cbfd3-275">Deconstructing user-defined types</span></span>

<span data-ttu-id="cbfd3-276">上に示したように、すべてのタプル型を分解できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-276">Any tuple type can be deconstructed as shown above.</span></span> <span data-ttu-id="cbfd3-277">また、ユーザー定義型 (クラス、構造体、またはインターフェイス) も簡単に分解できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-277">It's also easy to enable deconstruction on any user-defined type (classes, structs, or even interfaces).</span></span>

<span data-ttu-id="cbfd3-278">型の作成者は、型を構成するデータ要素を表す任意の数の `Deconstruct` 変数に対して値を割り当てる `out` メソッドを 1 つ以上定義できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-278">The type author can define one or more `Deconstruct` methods that assign values to any number of `out` variables representing the data elements that make up the type.</span></span> <span data-ttu-id="cbfd3-279">たとえば、次の `Person` 型は、person オブジェクトを、名と姓を表す要素に分解する `Deconstruct` メソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-279">For example, the following `Person` type defines a `Deconstruct` method that deconstructs a person object into the elements representing the first name and last name:</span></span>

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

<span data-ttu-id="cbfd3-280">deconstruct メソッドを使用すると、`Person` から、`FirstName` プロパティと `LastName` プロパティを表す 2 つの文字列を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-280">The deconstruct method enables assignment from a `Person` to two strings, representing the `FirstName` and `LastName` properties:</span></span>

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

<span data-ttu-id="cbfd3-281">自分で作成していない型を分解することもできます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-281">You can enable deconstruction even for types you did not author.</span></span>
<span data-ttu-id="cbfd3-282">`Deconstruct` メソッドは、オブジェクトのアクセス可能なデータ メンバーを展開する拡張メソッドとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-282">The `Deconstruct` method can be an extension method that unpackages the accessible data members of an object.</span></span> <span data-ttu-id="cbfd3-283">次の例は、`Student` から派生した `Person` 型と、`Student` を 3 つの変数 `FirstName`、`LastName`、`GPA` に分解する拡張メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-283">The example below shows a `Student` type, derived from the `Person` type, and an extension method that deconstructs a `Student` into three variables, representing the `FirstName`, the `LastName`, and the `GPA`:</span></span>

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

<span data-ttu-id="cbfd3-284">`Student` オブジェクトには、アクセス可能な `Deconstruct` メソッドが 2 つあります。`Student` 型に対して宣言された拡張メソッドと、`Person` 型のメンバーです。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-284">A `Student` object now has two accessible `Deconstruct` methods: the extension method declared for `Student` types, and the member of the `Person` type.</span></span> <span data-ttu-id="cbfd3-285">両方ともスコープ内にあり、`Student` を 2 つまたは 3 つの変数に分解できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-285">Both are in scope, and that enables a `Student` to be deconstructed into either two variables or three.</span></span>
<span data-ttu-id="cbfd3-286">student を 3 つの変数に割り当てると、名、姓、GPA のすべてが返されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-286">If you assign a student to three variables, the first name, last name, and GPA are all returned.</span></span> <span data-ttu-id="cbfd3-287">student を 2 つの変数に割り当てると、名と姓のみが返されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-287">If you assign a student to two variables, only the first name and the last name are returned.</span></span>

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

<span data-ttu-id="cbfd3-288">クラスまたはクラス階層で複数の `Deconstruct` メソッドを定義するときには注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-288">You should be careful defining multiple `Deconstruct` methods in a class or a class hierarchy.</span></span> <span data-ttu-id="cbfd3-289">`Deconstruct` パラメーターの数が同じ `out` メソッドが複数あると、あいまいさが生じ、</span><span class="sxs-lookup"><span data-stu-id="cbfd3-289">Multiple `Deconstruct` methods that have the same number of `out` parameters can quickly cause ambiguities.</span></span> <span data-ttu-id="cbfd3-290">呼び出し元が、必要な `Deconstruct` メソッドを簡単には呼び出せなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-290">Callers may not be able to easily call the desired `Deconstruct` method.</span></span>

<span data-ttu-id="cbfd3-291">この例では、出力パラメーターが `Deconstruct` の `Person` メソッドには 2 つ、`Deconstruct` の `Student` メソッドには 3 つ含まれるため、呼び出しが不明確になる可能性は最小限に抑えられています。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-291">In this example, there is minimal chance for an ambiguous call because the `Deconstruct` method for `Person` has two output parameters, and the `Deconstruct` method for `Student` has three.</span></span>

<span data-ttu-id="cbfd3-292">分解演算子は、等値性のテストには参加しません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-292">Deconstruction operators do not participate in testing equality.</span></span> <span data-ttu-id="cbfd3-293">次の例ではコンパイラ エラー CS0019 が生成されます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-293">The following example generates compiler error CS0019:</span></span>

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

<span data-ttu-id="cbfd3-294">`Deconstruct` メソッドは `Person` オブジェクト `p` を 2 つの文字列を含むタプルに変換できますが、これを等値テストのコンテキストで適用することはできません。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-294">The `Deconstruct` method could convert the `Person` object `p` to a tuple containing two strings, but it is not applicable in the context of equality tests.</span></span>

## <a name="tuples-as-out-parameters"></a><span data-ttu-id="cbfd3-295">out パラメーターとしてのタプル</span><span class="sxs-lookup"><span data-stu-id="cbfd3-295">Tuples as out parameters</span></span>

<span data-ttu-id="cbfd3-296">タプルは、"*それ自体*" を out パラメーターとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-296">Tuples can be used as out parameters *themselves*.</span></span> <span data-ttu-id="cbfd3-297">前述の「[分解](#deconstruction)」セクションで説明したあいまいさと混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-297">Not to be confused with any ambiguity previously mentioned in the [Deconstruction](#deconstruction) section.</span></span> <span data-ttu-id="cbfd3-298">メソッド呼び出しでは、タプルのシェイプについてのみ記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-298">In a method call, you need only describe the tuple's shape:</span></span>

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

<span data-ttu-id="cbfd3-299">または、[_unnamed_](#named-and-unnamed-tuples) タプルを使用し、そのフィールドを `Item1` および `Item2` として参照することもできます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-299">Alternatively, you could use an [_unnamed_](#named-and-unnamed-tuples) tuple and refer to its fields as `Item1` and `Item2`:</span></span>

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a><span data-ttu-id="cbfd3-300">まとめ</span><span class="sxs-lookup"><span data-stu-id="cbfd3-300">Conclusion</span></span>

<span data-ttu-id="cbfd3-301">クラスや構造体では動作の定義が必要であるため、新しい言語とライブラリで名前付きタプルがサポートされたことで、動作を定義せずに複数の要素を格納するデータ構造設計が格段に扱いやすくなりました。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-301">The new language and library support for named tuples makes it much easier to work with designs that use data structures that store multiple elements but do not define behavior, as classes and structs do.</span></span> <span data-ttu-id="cbfd3-302">こうした型に対してタプルを使用するのは簡単です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-302">It's easy and concise to use tuples for those types.</span></span> <span data-ttu-id="cbfd3-303">詳細な `class` または `struct` 構文を使用して型を作成しなくても、静的な型チェックのすべてのメリットを利用できます。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-303">You get all the benefits of static type checking, without needing to author types using the more verbose `class` or `struct` syntax.</span></span> <span data-ttu-id="cbfd3-304">とは言っても、class や struct は、`private` や `internal` のユーティリティ メソッドにとっては非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-304">Even so, they are most useful for utility methods that are `private`, or `internal`.</span></span> <span data-ttu-id="cbfd3-305">複数の要素を含む値がパブリック メソッドによって返される場合は、ユーザー定義型、`class` または`struct` を作成します。</span><span class="sxs-lookup"><span data-stu-id="cbfd3-305">Create user-defined types, either `class` or `struct` types when your public methods return a value that has multiple elements.</span></span>
