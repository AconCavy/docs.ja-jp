---
title: シーケンス
description: '大量の順序付けられたデータのコレクションがあり、必ずしもすべての要素を使用するとは限らない場合に、F # シーケンスを使用する方法について説明します。'
ms.date: 11/04/2019
ms.openlocfilehash: fa5073f33b9dae52371c249bfb257a2446b4d26a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855323"
---
# <a name="sequences"></a><span data-ttu-id="19809-103">シーケンス</span><span class="sxs-lookup"><span data-stu-id="19809-103">Sequences</span></span>

<span data-ttu-id="19809-104">*シーケンス*は、すべて1つの型からなる論理的な一連の要素です。</span><span class="sxs-lookup"><span data-stu-id="19809-104">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="19809-105">シーケンスは、大量の順序付けられたデータのコレクションがあり、すべての要素を使用するとは限らない場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="19809-105">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="19809-106">個々のシーケンス要素は必要に応じてのみ計算されるので、すべての要素が使用されるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="19809-106">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="19809-107">シーケンスは、のエイリアスである型によって表され `seq<'T>` <xref:System.Collections.Generic.IEnumerable%601> ます。</span><span class="sxs-lookup"><span data-stu-id="19809-107">Sequences are represented by the `seq<'T>` type, which is an alias for <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="19809-108">したがって、インターフェイスを実装するすべての .NET 型を <xref:System.Collections.Generic.IEnumerable%601> シーケンスとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="19809-108">Therefore, any .NET type that implements <xref:System.Collections.Generic.IEnumerable%601> interface can be used as a sequence.</span></span> <span data-ttu-id="19809-109">[Seq モジュール](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)は、シーケンスに関連する操作のサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="19809-109">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

> [!NOTE]
> <span data-ttu-id="19809-110">F # の docs.microsoft.com API リファレンスが完全ではありません。</span><span class="sxs-lookup"><span data-stu-id="19809-110">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="19809-111">壊れたリンクが見つかった場合は、代わりに[F # コアライブラリのドキュメント](https://fsharp.github.io/fsharp-core-docs/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19809-111">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="19809-112">シーケンス式</span><span class="sxs-lookup"><span data-stu-id="19809-112">Sequence Expressions</span></span>

<span data-ttu-id="19809-113">*シーケンス式*は、シーケンスに評価される式です。</span><span class="sxs-lookup"><span data-stu-id="19809-113">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="19809-114">シーケンス式は、さまざまな形式を取ることができます。</span><span class="sxs-lookup"><span data-stu-id="19809-114">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="19809-115">最も単純な形式は範囲を指定します。</span><span class="sxs-lookup"><span data-stu-id="19809-115">The simplest form specifies a range.</span></span> <span data-ttu-id="19809-116">たとえば、は、 `seq { 1 .. 5 }` エンドポイント1と5を含む5つの要素を含むシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="19809-116">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="19809-117">2つの2つの期間の間にインクリメント (またはデクリメント) を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="19809-117">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="19809-118">たとえば、次のコードでは、10の倍数のシーケンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="19809-118">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="19809-119">シーケンス式は、シーケンスの値を生成する F # の式で構成されます。</span><span class="sxs-lookup"><span data-stu-id="19809-119">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="19809-120">プログラムで値を生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="19809-120">You can also generate values programmatically:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="19809-121">前のサンプルでは、演算子を使用して `->` います。これにより、値がシーケンスの一部になる式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="19809-121">The previous sample uses the `->` operator, which allows you to specify an expression whose value will become a part of the sequence.</span></span> <span data-ttu-id="19809-122">は、 `->` その後のコードのすべての部分が値を返す場合にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="19809-122">You can only use `->` if every part of the code that follows it returns a value.</span></span>

<span data-ttu-id="19809-123">または、キーワードを指定し、次のオプションを指定することもでき `do` `yield` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-123">Alternatively, you can specify the `do` keyword, with an optional `yield` that follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="19809-124">次のコードでは、グリッドを表す配列へのインデックスと共に、座標ペアのリストが生成されます。</span><span class="sxs-lookup"><span data-stu-id="19809-124">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span> <span data-ttu-id="19809-125">最初の式では、を指定する必要があることに注意して `for` `do` ください。</span><span class="sxs-lookup"><span data-stu-id="19809-125">Note that the first `for` expression requires a `do` to be specified.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="19809-126">`if`シーケンスで使用される式は、フィルターです。</span><span class="sxs-lookup"><span data-stu-id="19809-126">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="19809-127">たとえば、型の関数があると仮定して、素数だけのシーケンスを生成するには、次のように `isprime` `int -> bool` シーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="19809-127">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="19809-128">前に説明したように、を `do` 使用する分岐がないため、ここではを指定する必要があり `else` `if` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-128">As mentioned previously, `do` is required here because there is no `else` branch that goes with the `if`.</span></span> <span data-ttu-id="19809-129">を使用しようとすると `->` 、すべてのブランチが値を返さないというエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="19809-129">If you try to use `->`, you'll get an error saying that not all branches return a value.</span></span>

## <a name="the-yield-keyword"></a><span data-ttu-id="19809-130">`yield!` キーワード</span><span class="sxs-lookup"><span data-stu-id="19809-130">The `yield!` keyword</span></span>

<span data-ttu-id="19809-131">場合によっては、要素のシーケンスを別のシーケンスに含めることが必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="19809-131">Sometimes, you may wish to include a sequence of elements into another sequence.</span></span> <span data-ttu-id="19809-132">シーケンスを別のシーケンス内に含めるには、キーワードを使用する必要があり `yield!` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-132">To include a sequence within another sequence, you'll need to use the `yield!` keyword:</span></span>

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

<span data-ttu-id="19809-133">を考えるもう1つの方法は、内部シーケンスを平坦化し、 `yield!` それを含んでいるシーケンスに含めることです。</span><span class="sxs-lookup"><span data-stu-id="19809-133">Another way of thinking of `yield!` is that it flattens an inner sequence and then includes that in the containing sequence.</span></span>

<span data-ttu-id="19809-134">`yield!`が式で使用されている場合、他のすべての単一の値ではキーワードを使用する必要があり `yield` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-134">When `yield!` is used in an expression, all other single values must use the `yield` keyword:</span></span>

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

<span data-ttu-id="19809-135">前の例でのみを指定する `x` と、シーケンスに値が生成されなくなります。</span><span class="sxs-lookup"><span data-stu-id="19809-135">Specifying only `x` in the previous example will result in the sequence generating no values.</span></span>

## <a name="examples"></a><span data-ttu-id="19809-136">例</span><span class="sxs-lookup"><span data-stu-id="19809-136">Examples</span></span>

<span data-ttu-id="19809-137">最初の例では、反復処理、フィルター、および yield を含むシーケンス式を使用して、配列を生成します。</span><span class="sxs-lookup"><span data-stu-id="19809-137">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="19809-138">このコードは、1から100までの一連の素数をコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="19809-138">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="19809-139">次の例では、3つの要素の組で構成される乗算テーブルを作成します。各要素は2つの要素と製品で構成されています。</span><span class="sxs-lookup"><span data-stu-id="19809-139">The following example creates a multiplication table that consists of tuples of three elements, each consisting of two factors and the product:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="19809-140">次の例では、を使用して `yield!` 個々のシーケンスを1つの最終シーケンスに結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="19809-140">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="19809-141">この場合、バイナリツリー内の各サブツリーのシーケンスは、最後のシーケンスを生成するために再帰関数で連結されます。</span><span class="sxs-lookup"><span data-stu-id="19809-141">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a><span data-ttu-id="19809-142">シーケンスの使用</span><span class="sxs-lookup"><span data-stu-id="19809-142">Using Sequences</span></span>

<span data-ttu-id="19809-143">シーケンスは、[リスト](lists.md)と同じ機能の多くをサポートします。</span><span class="sxs-lookup"><span data-stu-id="19809-143">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="19809-144">シーケンスは、キー生成関数を使用したグループ化やカウントなどの操作もサポートします。</span><span class="sxs-lookup"><span data-stu-id="19809-144">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="19809-145">シーケンスは、サブシーケンスを抽出するためのさまざまな関数もサポートします。</span><span class="sxs-lookup"><span data-stu-id="19809-145">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="19809-146">リスト、配列、セット、マップなどの多くのデータ型は、列挙可能なコレクションであるため、暗黙的にシーケンスされます。</span><span class="sxs-lookup"><span data-stu-id="19809-146">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="19809-147">引数としてシーケンスを受け取る関数は、を実装するすべての .NET データ型に加えて、一般的な F # データ型に対して機能し `System.Collections.Generic.IEnumerable<'T>` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-147">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="19809-148">リストを引数として受け取る関数と比較します。この関数はリストを受け取ることしかできません。</span><span class="sxs-lookup"><span data-stu-id="19809-148">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="19809-149">型は、 `seq<'T>` の型略称です `IEnumerable<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="19809-149">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="19809-150">つまり、ジェネリックを実装する任意の型 `System.Collections.Generic.IEnumerable<'T>` (F # の配列、リスト、セット、マップを含む) と、ほとんどの .net コレクション型は、型と互換性があり、 `seq` シーケンスが必要な場合はどこでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="19809-150">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>

## <a name="module-functions"></a><span data-ttu-id="19809-151">モジュール関数</span><span class="sxs-lookup"><span data-stu-id="19809-151">Module Functions</span></span>

<span data-ttu-id="19809-152">[Fsharp.core 名前空間](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)の[Seq モジュール](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)には、シーケンスを操作するための関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="19809-152">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="19809-153">これらの関数は、リスト、配列、マップ、およびセットとも連動します。これらの型はすべて列挙可能であるため、シーケンスとして扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="19809-153">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>

## <a name="creating-sequences"></a><span data-ttu-id="19809-154">シーケンスの作成</span><span class="sxs-lookup"><span data-stu-id="19809-154">Creating Sequences</span></span>

<span data-ttu-id="19809-155">シーケンス式を使用してシーケンスを作成するには、前に説明したように、または特定の関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="19809-155">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="19809-156">空のシーケンスは、 [seq](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)を使用して作成できます。また、 [seq. シングルトン](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)を使用して、指定した要素のシーケンスを1つだけ作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="19809-156">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="19809-157">[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)を使用して、指定した関数を使用して要素が作成されるシーケンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="19809-157">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="19809-158">シーケンスのサイズも指定します。</span><span class="sxs-lookup"><span data-stu-id="19809-158">You also provide a size for the sequence.</span></span> <span data-ttu-id="19809-159">この関数は[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)と同じですが、シーケンスを反復処理するまで要素は作成されません。</span><span class="sxs-lookup"><span data-stu-id="19809-159">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="19809-160">次のコードは、`Seq.init` の使用例です。</span><span class="sxs-lookup"><span data-stu-id="19809-160">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="19809-161">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="19809-161">The output is</span></span>

```console
0 10 20 30 40
```

<span data-ttu-id="19809-162">Seq. [ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)と[Seq. Ofarray&#60; t&#62; 関数](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)を使用すると、配列とリストからシーケンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="19809-162">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="19809-163">ただし、キャスト演算子を使用して、配列とリストをシーケンスに変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="19809-163">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="19809-164">次のコードは、両方の手法を示しています。</span><span class="sxs-lookup"><span data-stu-id="19809-164">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="19809-165">[Seq. cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)を使用すると、で定義されているような、弱く型指定されたコレクションからシーケンスを作成できます `System.Collections` 。</span><span class="sxs-lookup"><span data-stu-id="19809-165">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="19809-166">このように弱く型指定されたコレクションには要素型があり、 `System.Object` 非ジェネリック型を使用して列挙され `System.Collections.Generic.IEnumerable&#96;1` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-166">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="19809-167">次のコードは、を使用してを `Seq.cast` シーケンスに変換する方法を示してい `System.Collections.ArrayList` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-167">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="19809-168">無限のシーケンスを定義するには、 [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="19809-168">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="19809-169">このようなシーケンスでは、要素のインデックスから各要素を生成する関数を指定します。</span><span class="sxs-lookup"><span data-stu-id="19809-169">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="19809-170">無限のシーケンスは、レイジー評価のために可能です。要素は、必要に応じて、指定した関数を呼び出すことによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="19809-170">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="19809-171">次のコード例では、浮動小数点数の無限のシーケンスが生成されます。この例では、連続した整数の2乗の reciprocals が連続して作成されています。</span><span class="sxs-lookup"><span data-stu-id="19809-171">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="19809-172">[Seq](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)は、状態を受け取るコンピュテーション関数からシーケンスを生成し、シーケンス内の後続の各要素を生成するように変換します。</span><span class="sxs-lookup"><span data-stu-id="19809-172">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="19809-173">状態は、各要素を計算するために使用される値であり、各要素が計算されるたびに変更できます。</span><span class="sxs-lookup"><span data-stu-id="19809-173">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="19809-174">の2番目の引数 `Seq.unfold` は、シーケンスを開始するために使用される初期値です。</span><span class="sxs-lookup"><span data-stu-id="19809-174">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="19809-175">`Seq.unfold`状態にオプションの種類を使用します。これにより、値を返すことによってシーケンスを終了でき `None` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-175">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="19809-176">次のコードは、 `seq1` `fib` 操作によって生成されるシーケンス (と) の2つの例を示して `unfold` います。</span><span class="sxs-lookup"><span data-stu-id="19809-176">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="19809-177">1つ目のは、 `seq1` 数が20までの単純なシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="19809-177">The first, `seq1`, is just a simple sequence with numbers up to 20.</span></span> <span data-ttu-id="19809-178">2番目のは、を `fib` 使用し `unfold` てフィボナッチシーケンスを計算します。</span><span class="sxs-lookup"><span data-stu-id="19809-178">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="19809-179">フィボナッチシーケンス内の各要素は前の2つのフィボナッチ数の合計であるため、状態の値は、シーケンス内の前の2つの数値で構成される組になります。</span><span class="sxs-lookup"><span data-stu-id="19809-179">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="19809-180">初期値は `(1,1)` 、シーケンスの最初の2つの数値です。</span><span class="sxs-lookup"><span data-stu-id="19809-180">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="19809-181">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="19809-181">The output is as follows:</span></span>

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="19809-182">次のコードは、ここで説明するシーケンスモジュール関数の多くを使用して無限シーケンスの値を生成および計算する例です。</span><span class="sxs-lookup"><span data-stu-id="19809-182">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="19809-183">コードの実行には数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="19809-183">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a><span data-ttu-id="19809-184">要素の検索と検索</span><span class="sxs-lookup"><span data-stu-id="19809-184">Searching and Finding Elements</span></span>

<span data-ttu-id="19809-185">シーケンスは、リストで使用できる機能をサポートし[ています](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)。 [list.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)、 [seq、Seq](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)、seq。 [findindex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3) [、Seq](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d). [tryfind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)、および[seq. tryfindindex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。</span><span class="sxs-lookup"><span data-stu-id="19809-185">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="19809-186">シーケンスで使用できるこれらの関数のバージョンによって、シーケンスは検索対象の要素までのみ評価されます。</span><span class="sxs-lookup"><span data-stu-id="19809-186">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="19809-187">例については、「[リスト](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19809-187">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>

## <a name="obtaining-subsequences"></a><span data-ttu-id="19809-188">サブシーケンスの取得</span><span class="sxs-lookup"><span data-stu-id="19809-188">Obtaining Subsequences</span></span>

<span data-ttu-id="19809-189">[Seq. filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)と[seq. choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)は、リストで使用できる対応する関数と似ています。ただし、フィルター処理と選択は、シーケンス要素が評価されるまで発生しません。</span><span class="sxs-lookup"><span data-stu-id="19809-189">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="19809-190">[Seq. truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)は、別のシーケンスからシーケンスを作成しますが、シーケンスは指定した数の要素に制限されます。</span><span class="sxs-lookup"><span data-stu-id="19809-190">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="19809-191">[Seq. take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)は、シーケンスの先頭から指定された数の要素のみを含む新しいシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="19809-191">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="19809-192">指定した数よりも多い要素がシーケンス内にある場合、はを `Seq.take` スロー `System.InvalidOperationException` します。</span><span class="sxs-lookup"><span data-stu-id="19809-192">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="19809-193">との違いは、 `Seq.take` `Seq.truncate` `Seq.truncate` 要素の数が指定した数よりも小さい場合、はエラーを生成しないという点です。</span><span class="sxs-lookup"><span data-stu-id="19809-193">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="19809-194">次のコードは、との動作との違いを示して `Seq.truncate` `Seq.take` います。</span><span class="sxs-lookup"><span data-stu-id="19809-194">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="19809-195">エラーが発生する前の出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19809-195">The output, before the error occurs, is as follows.</span></span>

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="19809-196">[Seq](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)を使用することにより、述語関数 (ブール関数) を指定し、述語が返される元のシーケンスの要素で構成される別のシーケンスからシーケンスを作成でき `true` ます。ただし、述語が返す最初の要素の前には停止し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-196">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="19809-197">[Seq. skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)は、指定された数の別のシーケンスの最初の要素をスキップし、残りの要素を返すシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="19809-197">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="19809-198">[Seq. skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)は、述語が返された場合に別のシーケンスの最初の要素をスキップし、残りの要素を返すシーケンスを返します。このシーケンスは、 `true` 述語が返す最初の要素から始まり `false` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-198">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="19809-199">次のコード例は、の動作と、、、およびの違いを示してい `Seq.takeWhile` `Seq.skip` `Seq.skipWhile` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-199">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="19809-200">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19809-200">The output is as follows.</span></span>

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="19809-201">シーケンスの変換</span><span class="sxs-lookup"><span data-stu-id="19809-201">Transforming Sequences</span></span>

<span data-ttu-id="19809-202">[Seq (ペア](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)) は、入力シーケンスの連続する要素を組にグループ化する新しいシーケンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="19809-202">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="19809-203">[Seq. ウィンドウ](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)は似ていますが `Seq.pairwise` 、組のシーケンスを生成するのではなく、シーケンスから隣接する要素 (*ウィンドウ*) のコピーを格納する配列のシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="19809-203">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="19809-204">各配列で隣接する要素の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="19809-204">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="19809-205">次のコード例は、`Seq.windowed` の使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="19809-205">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="19809-206">この場合、ウィンドウ内の要素の数は3です。</span><span class="sxs-lookup"><span data-stu-id="19809-206">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="19809-207">この例では `printSeq` 、前のコード例で定義されているを使用します。</span><span class="sxs-lookup"><span data-stu-id="19809-207">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="19809-208">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19809-208">The output is as follows.</span></span>

<span data-ttu-id="19809-209">初期シーケンス:</span><span class="sxs-lookup"><span data-stu-id="19809-209">Initial sequence:</span></span>

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="19809-210">複数のシーケンスを持つ操作</span><span class="sxs-lookup"><span data-stu-id="19809-210">Operations with Multiple Sequences</span></span>

<span data-ttu-id="19809-211">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)と[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)は、2つまたは3つのシーケンスを受け取り、組のシーケンスを生成します。</span><span class="sxs-lookup"><span data-stu-id="19809-211">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="19809-212">これらの関数は、[リスト](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)で使用できる対応する関数に似ています。</span><span class="sxs-lookup"><span data-stu-id="19809-212">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="19809-213">1つのシーケンスを2つ以上のシーケンスに分割する対応する機能はありません。</span><span class="sxs-lookup"><span data-stu-id="19809-213">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="19809-214">シーケンスにこの機能が必要な場合は、シーケンスをリストに変換し、 [unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)を使用します。</span><span class="sxs-lookup"><span data-stu-id="19809-214">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="19809-215">並べ替え、比較、およびグループ化</span><span class="sxs-lookup"><span data-stu-id="19809-215">Sorting, Comparing, and Grouping</span></span>

<span data-ttu-id="19809-216">リストでサポートされている並べ替え関数は、シーケンスでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="19809-216">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="19809-217">これに[は、](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) SortBy および[seq](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="19809-217">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="19809-218">これらの関数は、シーケンス全体を反復処理します。</span><span class="sxs-lookup"><span data-stu-id="19809-218">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="19809-219">2つのシーケンスを比較するには、 [Seq. compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="19809-219">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="19809-220">関数は、連続する要素を順番に比較し、最初の等しくないペアが検出されたときに停止します。</span><span class="sxs-lookup"><span data-stu-id="19809-220">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="19809-221">その他の要素は、比較には関与しません。</span><span class="sxs-lookup"><span data-stu-id="19809-221">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="19809-222">`Seq.compareWith` の使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="19809-222">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="19809-223">前のコードでは、最初の要素のみが計算され、検査され、結果は-1 になります。</span><span class="sxs-lookup"><span data-stu-id="19809-223">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="19809-224">[CountBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)は、各要素の*キー*と呼ばれる値を生成する関数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="19809-224">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="19809-225">各要素に対してこの関数を呼び出すことにより、各要素に対してキーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="19809-225">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="19809-226">`Seq.countBy`次に、キー値を含むシーケンスと、キーの各値を生成した要素の数を返します。</span><span class="sxs-lookup"><span data-stu-id="19809-226">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="19809-227">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19809-227">The output is as follows.</span></span>

```console
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="19809-228">前の出力は、キー1、キー2を生成した33値、およびキー0を生成した33値を生成した、元のシーケンスの34要素があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="19809-228">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="19809-229">シーケンスの要素をグループ化するには、 [Seq. groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="19809-229">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="19809-230">`Seq.groupBy`は、シーケンスと、要素からキーを生成する関数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="19809-230">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="19809-231">関数は、シーケンスの各要素に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="19809-231">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="19809-232">`Seq.groupBy`組のシーケンスを返します。各組の最初の要素はキーで、2番目の要素はそのキーを生成する要素のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="19809-232">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="19809-233">次のコード例では、を使用して、 `Seq.groupBy` 0、1、および2の個別のキー値を持つ3つのグループに、1 ~ 100 の一連の数値を分割しています。</span><span class="sxs-lookup"><span data-stu-id="19809-233">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="19809-234">出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="19809-234">The output is as follows.</span></span>

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="19809-235">[Seq](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)を呼び出すことで、重複する要素を排除するシーケンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="19809-235">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="19809-236">または、 [seq.distinctby](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)を使用することもできます。この場合、各要素に対して呼び出されるキー生成関数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="19809-236">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="19809-237">結果のシーケンスには、一意のキーを持つ元のシーケンスの要素が含まれます。それより前の要素に対して重複するキーを生成する要素は破棄されます。</span><span class="sxs-lookup"><span data-stu-id="19809-237">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="19809-238">`Seq.distinct` の使用方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="19809-238">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="19809-239">`Seq.distinct`は、バイナリ数値を表すシーケンスを生成して、個別の要素だけが0と1であることを示すことによって示されます。</span><span class="sxs-lookup"><span data-stu-id="19809-239">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="19809-240">次のコードは、 `Seq.distinctBy` 負の数値と正の数値を格納し、キー生成関数として絶対値関数を使用するシーケンスを使用してを開始することで、を示しています。</span><span class="sxs-lookup"><span data-stu-id="19809-240">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="19809-241">結果のシーケンスには、シーケンス内の負の数値に対応する正の数値がすべて不足しています。負の数値はシーケンスの前に表示されるため、同じ絶対値またはキーを持つ正の数値の代わりに選択されるためです。</span><span class="sxs-lookup"><span data-stu-id="19809-241">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="19809-242">読み取り専用とキャッシュされたシーケンス</span><span class="sxs-lookup"><span data-stu-id="19809-242">Readonly and Cached Sequences</span></span>

<span data-ttu-id="19809-243">[Seq. readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)は、シーケンスの読み取り専用コピーを作成します。</span><span class="sxs-lookup"><span data-stu-id="19809-243">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="19809-244">`Seq.readonly`は、配列などの読み取り/書き込みコレクションがあり、元のコレクションを変更しない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="19809-244">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="19809-245">この関数は、データのカプセル化を維持するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="19809-245">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="19809-246">次のコード例では、配列を含む型が作成されます。</span><span class="sxs-lookup"><span data-stu-id="19809-246">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="19809-247">プロパティは配列を公開しますが、配列を返すのではなく、を使用して配列から作成されたシーケンスを返し `Seq.readonly` ます。</span><span class="sxs-lookup"><span data-stu-id="19809-247">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="19809-248">[Seq. cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)は、シーケンスの格納されているバージョンを作成します。</span><span class="sxs-lookup"><span data-stu-id="19809-248">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="19809-249">`Seq.cache`シーケンスの再評価を避けるため、またはシーケンスを使用する複数のスレッドがある場合は、を使用して、各要素が1回だけ動作するようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="19809-249">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="19809-250">複数のスレッドで使用されているシーケンスがある場合は、元のシーケンスの値を列挙して計算するスレッドを1つ持つことができ、残りのスレッドはキャッシュされたシーケンスを使用できます。</span><span class="sxs-lookup"><span data-stu-id="19809-250">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>

## <a name="performing-computations-on-sequences"></a><span data-ttu-id="19809-251">シーケンスに対する計算の実行</span><span class="sxs-lookup"><span data-stu-id="19809-251">Performing Computations on Sequences</span></span>

<span data-ttu-id="19809-252">単純な算術演算は、 [seq. average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)、seq. [sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)、seq. [AverageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)、 [seq. sumby](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)などのリストのようなものです。</span><span class="sxs-lookup"><span data-stu-id="19809-252">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="19809-253">[Seq](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)、 [Seq](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)、および[seq. scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)は、リストで使用できる対応する関数に似ています。</span><span class="sxs-lookup"><span data-stu-id="19809-253">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="19809-254">シーケンスは、サポートを一覧表示するこれらの関数の全バリエーションのサブセットをサポートします。</span><span class="sxs-lookup"><span data-stu-id="19809-254">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="19809-255">詳細と例については、「[リスト](lists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19809-255">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="19809-256">関連項目</span><span class="sxs-lookup"><span data-stu-id="19809-256">See also</span></span>

- [<span data-ttu-id="19809-257">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="19809-257">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="19809-258">F# の型</span><span class="sxs-lookup"><span data-stu-id="19809-258">F# Types</span></span>](fsharp-types.md)
