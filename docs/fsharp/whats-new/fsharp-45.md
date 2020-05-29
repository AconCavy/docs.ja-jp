---
title: 'F # 4.5 の新機能-F # ガイド'
description: 'F # 4.5 で利用可能な新機能の概要を説明します。'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202349"
---
# <a name="whats-new-in-f-45"></a><span data-ttu-id="24930-103">F # 4.5 の新機能</span><span class="sxs-lookup"><span data-stu-id="24930-103">What's new in F# 4.5</span></span>

<span data-ttu-id="24930-104">F # 4.5 では、F # 言語に複数の機能強化が加えられています。</span><span class="sxs-lookup"><span data-stu-id="24930-104">F# 4.5 adds multiple improvements to the F# language.</span></span> <span data-ttu-id="24930-105">これらの機能の多くは、F # で効率的なコードを記述できるようにするためにまとめられています。また、このコードが安全であることを保証します。</span><span class="sxs-lookup"><span data-stu-id="24930-105">Many of these features were added together to enable you to write efficient code in F# while also ensuring this code is safe.</span></span> <span data-ttu-id="24930-106">これにより、言語にいくつかの概念が追加され、これらのコンストラクトを使用するときに大量のコンパイラ分析が行われることになります。</span><span class="sxs-lookup"><span data-stu-id="24930-106">Doing so means adding a few concepts to the language and a significant amount of compiler analysis when using these constructs.</span></span>

## <a name="get-started"></a><span data-ttu-id="24930-107">作業開始</span><span class="sxs-lookup"><span data-stu-id="24930-107">Get started</span></span>

<span data-ttu-id="24930-108">F # 4.5 は、すべての .NET Core ディストリビューションと Visual Studio ツールで使用できます。</span><span class="sxs-lookup"><span data-stu-id="24930-108">F# 4.5 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="24930-109">詳細については、 [F # の概要に関する](../get-started/index.md)ページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="24930-109">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="span-and-byref-like-structs"></a><span data-ttu-id="24930-110">Span および byref に似た構造体</span><span class="sxs-lookup"><span data-stu-id="24930-110">Span and byref-like structs</span></span>

<span data-ttu-id="24930-111"><xref:System.Span%601>.Net Core で導入された型を使用すると、厳密に型指定された方法でメモリ内のバッファーを表すことができます。 f # 4.5 で始まる f # で使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="24930-111">The <xref:System.Span%601> type introduced in .NET Core allows you to represent buffers in memory in a strongly typed manner, which is now allowed in F# starting with F# 4.5.</span></span> <span data-ttu-id="24930-112">次の例は、 <xref:System.Span%601> 別のバッファー表現を使用して、で動作する関数を再利用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="24930-112">The following example shows how you can re-use a function operating on a <xref:System.Span%601> with different buffer representations:</span></span>

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

<span data-ttu-id="24930-113">これにとって重要な点は、Span とその他の[byref に似た構造体](../language-reference/structures.md#byreflike-structs)は、コンパイラによって実行される静的分析が非常に厳密であり、予期しない状態になる可能性がある方法でその使用を制限することです。</span><span class="sxs-lookup"><span data-stu-id="24930-113">An important aspect to this is that Span and other [byref-like structs](../language-reference/structures.md#byreflike-structs) have very rigid static analysis performed by the compiler that restrict their usage in ways you might find to be unexpected.</span></span> <span data-ttu-id="24930-114">これは、F # 4.5 で導入されたパフォーマンス、表現力、および安全性の基本的なトレードオフです。</span><span class="sxs-lookup"><span data-stu-id="24930-114">This is the fundamental tradeoff between performance, expressiveness, and safety that is introduced in F# 4.5.</span></span>

## <a name="revamped-byrefs"></a><span data-ttu-id="24930-115">Byref の改良</span><span class="sxs-lookup"><span data-stu-id="24930-115">Revamped byrefs</span></span>

<span data-ttu-id="24930-116">F # 4.5 より前では、F # の[byref](../language-reference/byrefs.md)は安全ではないため、多くのアプリケーションでは聞こえませんでした。</span><span class="sxs-lookup"><span data-stu-id="24930-116">Prior to F# 4.5, [Byrefs](../language-reference/byrefs.md) in F# were unsafe and unsound for numerous applications.</span></span> <span data-ttu-id="24930-117">Byref に関する束縛の問題が F # 4.5 で対処されており、span と byref に似た構造体に対して実行される同じ静的分析も適用されました。</span><span class="sxs-lookup"><span data-stu-id="24930-117">Soundness issues around byrefs have been addressed in F# 4.5 and the same static analysis done for span and byref-like structs was also applied.</span></span>

### <a name="inreft-and-outreft"></a><span data-ttu-id="24930-118">inref< ' t> および outref< '></span><span class="sxs-lookup"><span data-stu-id="24930-118">inref<'T> and outref<'T></span></span>

<span data-ttu-id="24930-119">読み取り専用、書き込み専用、および読み取り/書き込みマネージポインターの概念を表すために、F # 4.5 では、 `inref<'T>` `outref<'T>` それぞれ読み取り専用ポインターと書き込み専用ポインターを表す型が導入されています。</span><span class="sxs-lookup"><span data-stu-id="24930-119">To represent the notion of a read-only, write-only, and read/write managed pointer, F# 4.5 introduces the `inref<'T>`, `outref<'T>` types to represent read-only and write-only pointers, respectively.</span></span> <span data-ttu-id="24930-120">それぞれに異なるセマンティクスがあります。</span><span class="sxs-lookup"><span data-stu-id="24930-120">Each have different semantics.</span></span> <span data-ttu-id="24930-121">たとえば、に書き込むことはできません `inref<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="24930-121">For example, you cannot write to an `inref<'T>`:</span></span>

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

<span data-ttu-id="24930-122">既定では、型の推定は、 `inref<'T>` 変更可能として既に宣言されていない限り、F # コードの不変の性質を持つとして、マネージポインターをとして推論します。</span><span class="sxs-lookup"><span data-stu-id="24930-122">By default, type inference will infer managed pointers as `inref<'T>` to be in line with the immutable nature of F# code, unless something has already been declared as mutable.</span></span> <span data-ttu-id="24930-123">何かを書き込み可能にするには、その `mutable` アドレスを操作する関数またはメンバーに渡す前に、型をとして宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="24930-123">To make something writable, you'll need to declare a type as `mutable` before passing its address to a function or member that manipulates it.</span></span> <span data-ttu-id="24930-124">詳細については、「 [byref](../language-reference/byrefs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24930-124">To learn more, see [Byrefs](../language-reference/byrefs.md).</span></span>

## <a name="readonly-structs"></a><span data-ttu-id="24930-125">Readonly 構造体</span><span class="sxs-lookup"><span data-stu-id="24930-125">Readonly structs</span></span>

<span data-ttu-id="24930-126">F # 4.5 以降では、次のようにを使用して構造体に注釈を付けることができ <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="24930-126">Starting with F# 4.5, you can annotate a struct with <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> as such:</span></span>

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

<span data-ttu-id="24930-127">これにより、構造体で変更可能なメンバーを宣言し、アセンブリから使用するときに F # と C# が読み取り専用として扱うことができるメタデータを生成することはできません。</span><span class="sxs-lookup"><span data-stu-id="24930-127">This disallows you from declaring a mutable member in the struct and emits metadata that allows F# and C# to treat it as readonly when consumed from an assembly.</span></span> <span data-ttu-id="24930-128">詳細については、「 [ReadOnly 構造体](../language-reference/structures.md#readonly-structs)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24930-128">To learn more, see [ReadOnly structs](../language-reference/structures.md#readonly-structs).</span></span>

## <a name="void-pointers"></a><span data-ttu-id="24930-129">Void ポインター</span><span class="sxs-lookup"><span data-stu-id="24930-129">Void pointers</span></span>

<span data-ttu-id="24930-130">`voidptr`型は、次の関数のように F # 4.5 に追加されます。</span><span class="sxs-lookup"><span data-stu-id="24930-130">The `voidptr` type is added to F# 4.5, as are the following functions:</span></span>

* <span data-ttu-id="24930-131">`NativePtr.ofVoidPtr`void ポインターをネイティブ int ポインターに変換するには</span><span class="sxs-lookup"><span data-stu-id="24930-131">`NativePtr.ofVoidPtr` to convert a void pointer into a native int pointer</span></span>
* <span data-ttu-id="24930-132">`NativePtr.toVoidPtr`ネイティブの int ポインターを void ポインターに変換するには</span><span class="sxs-lookup"><span data-stu-id="24930-132">`NativePtr.toVoidPtr` to convert a native int pointer to a void pointer</span></span>

<span data-ttu-id="24930-133">これは、void ポインターを使用するネイティブコンポーネントと相互運用する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="24930-133">This is helpful when interoperating with a native component that makes use of void pointers.</span></span>

## <a name="the-match-keyword"></a><span data-ttu-id="24930-134">`match!` キーワード</span><span class="sxs-lookup"><span data-stu-id="24930-134">The `match!` keyword</span></span>

<span data-ttu-id="24930-135">キーワードは、 `match!` コンピュテーション式の内部でパターンマッチングを強化します。</span><span class="sxs-lookup"><span data-stu-id="24930-135">The `match!` keyword enhances pattern matching when inside a computation expression:</span></span>

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

<span data-ttu-id="24930-136">これにより、非同期などのコンピュテーション式でオプション (または他の型) を混在させることが多いコードを短縮できます。</span><span class="sxs-lookup"><span data-stu-id="24930-136">This allows you to shorten code that often involves mixing options (or other types) with computation expressions such as async.</span></span> <span data-ttu-id="24930-137">詳細については、「 [match!](../language-reference/computation-expressions.md#match)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24930-137">To learn more, see [match!](../language-reference/computation-expressions.md#match).</span></span>

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a><span data-ttu-id="24930-138">配列、リスト、およびシーケンス式における緩やかなキャストの要件</span><span class="sxs-lookup"><span data-stu-id="24930-138">Relaxed upcasting requirements in array, list, and sequence expressions</span></span>

<span data-ttu-id="24930-139">配列、リスト、およびシーケンス式の内部で別の型から継承する可能性のある型を混在させるには、またはを使用して派生型をその親型にアップキャストする必要がありました `:>` `upcast` 。</span><span class="sxs-lookup"><span data-stu-id="24930-139">Mixing types where one may inherit from another inside of array, list, and sequence expressions has traditionally required you to upcast any derived type to its parent type with `:>` or `upcast`.</span></span> <span data-ttu-id="24930-140">これは、次に示すように、緩和されました。</span><span class="sxs-lookup"><span data-stu-id="24930-140">This is now relaxed, demonstrated as follows:</span></span>

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a><span data-ttu-id="24930-141">配列とリスト式のインデント緩和</span><span class="sxs-lookup"><span data-stu-id="24930-141">Indentation relaxation for array and list expressions</span></span>

<span data-ttu-id="24930-142">F # 4.5 より前では、メソッド呼び出しに引数として渡すときに、配列とリスト式を過度にインデントする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="24930-142">Prior to F# 4.5, you needed to excessively indent array and list expressions when passed as arguments to method calls.</span></span> <span data-ttu-id="24930-143">これは必要なくなりました。</span><span class="sxs-lookup"><span data-stu-id="24930-143">This is no longer required:</span></span>

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
