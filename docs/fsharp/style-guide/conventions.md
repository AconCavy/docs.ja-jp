---
title: F# のコーディング規則
description: 'F # コードを記述するときの一般的なガイドラインと表現方法について説明します。'
ms.date: 01/15/2020
ms.openlocfilehash: 47e9183ce22689a050878cf10d7a9bcf3b929ec6
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143532"
---
# <a name="f-coding-conventions"></a><span data-ttu-id="bbadf-103">F# のコーディング規則</span><span class="sxs-lookup"><span data-stu-id="bbadf-103">F# coding conventions</span></span>

<span data-ttu-id="bbadf-104">次の規則は、大きな F # コードベースの使用経験からのものです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-104">The following conventions are formulated from experience working with large F# codebases.</span></span> <span data-ttu-id="bbadf-105">[優れた F # コードの5つの原則](index.md#five-principles-of-good-f-code)は、各推奨事項の基礎となります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-105">The [Five principles of good F# code](index.md#five-principles-of-good-f-code) are the foundation of each recommendation.</span></span> <span data-ttu-id="bbadf-106">これらは、 [f # コンポーネントのデザインガイドライン](component-design-guidelines.md)に関連していますが、ライブラリなどのコンポーネントだけでなく、すべての f # コードに適用されます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-106">They are related to the [F# component design guidelines](component-design-guidelines.md), but are applicable for any F# code, not just components such as libraries.</span></span>

## <a name="organizing-code"></a><span data-ttu-id="bbadf-107">コードの整理</span><span class="sxs-lookup"><span data-stu-id="bbadf-107">Organizing code</span></span>

<span data-ttu-id="bbadf-108">F # には、コードを整理するための主な方法として、モジュールと名前空間の2つがあります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-108">F# features two primary ways to organize code: modules and namespaces.</span></span> <span data-ttu-id="bbadf-109">これらは似ていますが、次の点が異なります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-109">These are similar, but do have the following differences:</span></span>

* <span data-ttu-id="bbadf-110">名前空間は、.NET 名前空間としてコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-110">Namespaces are compiled as .NET namespaces.</span></span> <span data-ttu-id="bbadf-111">モジュールは静的クラスとしてコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-111">Modules are compiled as static classes.</span></span>
* <span data-ttu-id="bbadf-112">名前空間は常に最上位レベルです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-112">Namespaces are always top level.</span></span> <span data-ttu-id="bbadf-113">モジュールはトップレベルで、他のモジュール内で入れ子にすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-113">Modules can be top-level and nested within other modules.</span></span>
* <span data-ttu-id="bbadf-114">名前空間は、複数のファイルにまたがることができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-114">Namespaces can span multiple files.</span></span> <span data-ttu-id="bbadf-115">モジュールはできません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-115">Modules cannot.</span></span>
* <span data-ttu-id="bbadf-116">モジュールは、およびで修飾でき `[<RequireQualifiedAccess>]` `[<AutoOpen>]` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-116">Modules can be decorated with `[<RequireQualifiedAccess>]` and `[<AutoOpen>]`.</span></span>

<span data-ttu-id="bbadf-117">次のガイドラインは、これらを使用してコードを整理する際に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-117">The following guidelines will help you use these to organize your code.</span></span>

### <a name="prefer-namespaces-at-the-top-level"></a><span data-ttu-id="bbadf-118">最上位レベルで名前空間を優先する</span><span class="sxs-lookup"><span data-stu-id="bbadf-118">Prefer namespaces at the top level</span></span>

<span data-ttu-id="bbadf-119">パブリックに使用できるコードでは、最上位レベルのモジュールに対して名前空間が優先されます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-119">For any publicly consumable code, namespaces are preferential to modules at the top level.</span></span> <span data-ttu-id="bbadf-120">これらは .NET 名前空間としてコンパイルされるため、C# では問題なく使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-120">Because they are compiled as .NET namespaces, they are consumable from C# with no issue.</span></span>

```fsharp
// Good!
namespace MyCode

type MyClass() =
    ...
```

<span data-ttu-id="bbadf-121">最上位のモジュールの使用は、F # からのみ呼び出された場合は異なる場合がありますが、C# のコンシューマーにとっては、モジュールで修飾する必要があるため、呼び出し元が驚かれる可能性があり `MyClass` `MyCode` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-121">Using a top-level module may not appear different when called only from F#, but for C# consumers, callers may be surprised by having to qualify `MyClass` with the `MyCode` module.</span></span>

```fsharp
// Bad!
module MyCode

type MyClass() =
    ...
```

### <a name="carefully-apply-autoopen"></a><span data-ttu-id="bbadf-122">慎重に適用する`[<AutoOpen>]`</span><span class="sxs-lookup"><span data-stu-id="bbadf-122">Carefully apply `[<AutoOpen>]`</span></span>

<span data-ttu-id="bbadf-123">この `[<AutoOpen>]` 構成体は、呼び出し元が使用できるもののスコープを汚染ことができます。また、その結果は "マジック" になります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-123">The `[<AutoOpen>]` construct can pollute the scope of what is available to callers, and the answer to where something comes from is "magic".</span></span> <span data-ttu-id="bbadf-124">これは適切な方法ではありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-124">This is not a good thing.</span></span> <span data-ttu-id="bbadf-125">このルールの例外として、F # コアライブラリ自体があります (ただし、これは少しの議論でもあります)。</span><span class="sxs-lookup"><span data-stu-id="bbadf-125">An exception to this rule is the F# Core Library itself (though this fact is also a bit controversial).</span></span>

<span data-ttu-id="bbadf-126">ただし、パブリック api のヘルパー機能があり、パブリック api とは別に整理する必要がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-126">However, it is a convenience if you have helper functionality for a public API that you wish to organize separately from that public API.</span></span>

```fsharp
module MyAPI =
    [<AutoOpen>]
    module private Helpers =
        let helper1 x y z =
            ...

    let myFunction1 x =
        let y = ...
        let z = ...

        helper1 x y z
```

<span data-ttu-id="bbadf-127">これにより、呼び出しのたびにヘルパーを完全に修飾することなく、関数のパブリック API から実装の詳細を明確に分離できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-127">This lets you cleanly separate implementation details from the public API of a function without having to fully qualify a helper each time you call it.</span></span>

<span data-ttu-id="bbadf-128">さらに、拡張メソッドおよび式ビルダーを名前空間レベルで公開することは、ではより簡潔に表現でき `[<AutoOpen>]` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-128">Additionally, exposing extension methods and expression builders at the namespace level can be neatly expressed with `[<AutoOpen>]`.</span></span>

### <a name="use-requirequalifiedaccess-whenever-names-could-conflict-or-you-feel-it-helps-with-readability"></a><span data-ttu-id="bbadf-129">`[<RequireQualifiedAccess>]`名前が競合する場合や、読みやすさを向上させる場合に使用します</span><span class="sxs-lookup"><span data-stu-id="bbadf-129">Use `[<RequireQualifiedAccess>]` whenever names could conflict or you feel it helps with readability</span></span>

<span data-ttu-id="bbadf-130">モジュールに属性を追加すると、モジュールが `[<RequireQualifiedAccess>]` 開かれていないこと、およびモジュールの要素への参照に明示的な修飾アクセスが必要であることが示されます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-130">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="bbadf-131">たとえば、モジュールに `Microsoft.FSharp.Collections.List` はこの属性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-131">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="bbadf-132">これは、モジュールの関数と値の名前が、他のモジュールの名前と競合する可能性がある場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-132">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="bbadf-133">修飾されたアクセスを必要とすると、ライブラリの長期的な保守性と発展性を大幅に向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-133">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

```fsharp
[<RequireQualifiedAccess>]
module StringTokenization =
    let parse s = ...

...

let s = getAString()
let parsed = StringTokenization.parse s // Must qualify to use 'parse'
```

### <a name="sort-open-statements-topologically"></a><span data-ttu-id="bbadf-134">Sort `open` ステートメント位相的</span><span class="sxs-lookup"><span data-stu-id="bbadf-134">Sort `open` statements topologically</span></span>

<span data-ttu-id="bbadf-135">F # では、ステートメントを含め、宣言の順序が重要に `open` なります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-135">In F#, the order of declarations matters, including with `open` statements.</span></span> <span data-ttu-id="bbadf-136">これは、C# とは異なります。との効果は、 `using` `using static` ファイル内のステートメントの順序に依存しません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-136">This is unlike C#, where the effect of `using` and `using static` is independent of the ordering of those statements in a file.</span></span>

<span data-ttu-id="bbadf-137">F # では、スコープ内で開かれた要素は、既に存在する他の要素をシャドウできます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-137">In F#, elements opened into a scope can shadow others already present.</span></span> <span data-ttu-id="bbadf-138">これは、並べ替えステートメントによって `open` コードの意味が変更される可能性があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-138">This means that reordering `open` statements could alter the meaning of code.</span></span> <span data-ttu-id="bbadf-139">その結果、すべての `open` ステートメント (たとえば、英数字順) の任意の並べ替えを使用することは推奨されません。ようを使用すると、必要に応じて異なる動作を生成できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-139">As a result, any arbitrary sorting of all `open` statements (for example, alphanumerically) is not recommended, lest you generate different behavior that you might expect.</span></span>

<span data-ttu-id="bbadf-140">代わりに、[位相的](https://en.wikipedia.org/wiki/Topological_sorting)を並べ替えることをお勧めします。つまり、ステートメントは、 `open` システムの_層_が定義されている順序で並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-140">Instead, we recommend that you sort them [topologically](https://en.wikipedia.org/wiki/Topological_sorting); that is, order your `open` statements in the order in which _layers_ of your system are defined.</span></span> <span data-ttu-id="bbadf-141">異なるトポロジレイヤー内で英数字の並べ替えを行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-141">Doing alphanumeric sorting within different topological layers may also be considered.</span></span>

<span data-ttu-id="bbadf-142">例として、F # コンパイラサービスパブリック API ファイルのトポロジの並べ替えを次に示します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-142">As an example, here is the topological sorting for the F# compiler service public API file:</span></span>

```fsharp
namespace Microsoft.FSharp.Compiler.SourceCodeServices

open System
open System.Collections.Generic
open System.Collections.Concurrent
open System.Diagnostics
open System.IO
open System.Reflection
open System.Text

open Microsoft.FSharp.Compiler
open Microsoft.FSharp.Compiler.AbstractIL
open Microsoft.FSharp.Compiler.AbstractIL.Diagnostics
open Microsoft.FSharp.Compiler.AbstractIL.IL
open Microsoft.FSharp.Compiler.AbstractIL.ILBinaryReader
open Microsoft.FSharp.Compiler.AbstractIL.Internal
open Microsoft.FSharp.Compiler.AbstractIL.Internal.Library

open Microsoft.FSharp.Compiler.AccessibilityLogic
open Microsoft.FSharp.Compiler.Ast
open Microsoft.FSharp.Compiler.CompileOps
open Microsoft.FSharp.Compiler.CompileOptions
open Microsoft.FSharp.Compiler.Driver
open Microsoft.FSharp.Compiler.ErrorLogger
open Microsoft.FSharp.Compiler.Infos
open Microsoft.FSharp.Compiler.InfoReader
open Microsoft.FSharp.Compiler.Lexhelp
open Microsoft.FSharp.Compiler.Layout
open Microsoft.FSharp.Compiler.Lib
open Microsoft.FSharp.Compiler.NameResolution
open Microsoft.FSharp.Compiler.PrettyNaming
open Microsoft.FSharp.Compiler.Parser
open Microsoft.FSharp.Compiler.Range
open Microsoft.FSharp.Compiler.Tast
open Microsoft.FSharp.Compiler.Tastops
open Microsoft.FSharp.Compiler.TcGlobals
open Microsoft.FSharp.Compiler.TypeChecker
open Microsoft.FSharp.Compiler.SourceCodeServices.SymbolHelpers

open Internal.Utilities
open Internal.Utilities.Collections
```

<span data-ttu-id="bbadf-143">1本の改行では、各レイヤーが後で英数字順に並べ替えられるように、トポロジレイヤーが分離されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-143">Note that a line break separates topological layers, with each layer being sorted alphanumerically afterwards.</span></span> <span data-ttu-id="bbadf-144">これにより、誤って値をシャドウすることなくコードを整理できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-144">This cleanly organizes code without accidentally shadowing values.</span></span>

## <a name="use-classes-to-contain-values-that-have-side-effects"></a><span data-ttu-id="bbadf-145">クラスを使用して副作用のある値を格納する</span><span class="sxs-lookup"><span data-stu-id="bbadf-145">Use classes to contain values that have side effects</span></span>

<span data-ttu-id="bbadf-146">値の初期化には、データベースまたはその他のリモートリソースへのコンテキストのインスタンス化など、副作用が生じる場合が多くあります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-146">There are many times when initializing a value can have side effects, such as instantiating a context to a database or other remote resource.</span></span> <span data-ttu-id="bbadf-147">モジュール内でこのような処理を初期化し、後続の関数で使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-147">It is tempting to initialize such things in a module and use it in subsequent functions:</span></span>

```fsharp
// This is bad!
module MyApi =
    let dep1 = File.ReadAllText "/Users/{your name}/connectionstring.txt"
    let dep2 = Environment.GetEnvironmentVariable "DEP_2"

    let private r = Random()
    let dep3() = r.Next() // Problematic if multiple threads use this

    let function1 arg = doStuffWith dep1 dep2 dep3 arg
    let function2 arg = doSutffWith dep1 dep2 dep3 arg
```

<span data-ttu-id="bbadf-148">多くの場合、これは次のような理由で不適切です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-148">This is frequently a bad idea for a few reasons:</span></span>

<span data-ttu-id="bbadf-149">最初に、アプリケーション構成はとを使用してコードベースにプッシュされ `dep1` `dep2` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-149">First, application configuration is pushed into the codebase with `dep1` and `dep2`.</span></span> <span data-ttu-id="bbadf-150">これは、より大きなコードベースで維持するのは困難です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-150">This is difficult to maintain in larger codebases.</span></span>

<span data-ttu-id="bbadf-151">2番目に、静的に初期化されたデータには、コンポーネントが複数のスレッドを使用する場合に、スレッドセーフではない値を含めないでください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-151">Second, statically initialized data should not include values that are not thread safe if your component will itself use multiple threads.</span></span> <span data-ttu-id="bbadf-152">これは、によって明確に違反され `dep3` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-152">This is clearly violated by `dep3`.</span></span>

<span data-ttu-id="bbadf-153">最後に、モジュールの初期化は、コンパイルユニット全体の静的コンストラクターにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-153">Finally, module initialization compiles into a static constructor for the entire compilation unit.</span></span> <span data-ttu-id="bbadf-154">このモジュールの let バインド値の初期化でエラーが発生した場合、そのモジュールはとしてマニフェストを `TypeInitializationException` 持ち、アプリケーションの有効期間全体にわたってキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-154">If any error occurs in let-bound value initialization in that module, it manifests as a `TypeInitializationException` that is then cached for the entire lifetime of the application.</span></span> <span data-ttu-id="bbadf-155">これは診断が困難な場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-155">This can be difficult to diagnose.</span></span> <span data-ttu-id="bbadf-156">通常は、その理由を試みることができる内部例外がありますが、存在しない場合、根本的な原因については何も通知されません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-156">There is usually an inner exception that you can attempt to reason about, but if there is not, then there is no telling what the root cause is.</span></span>

<span data-ttu-id="bbadf-157">代わりに、単純なクラスを使用して依存関係を保持するだけです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-157">Instead, just use a simple class to hold dependencies:</span></span>

```fsharp
type MyParametricApi(dep1, dep2, dep3) =
    member _.Function1 arg1 = doStuffWith dep1 dep2 dep3 arg1
    member _.Function2 arg2 = doStuffWith dep1 dep2 dep3 arg2
```

<span data-ttu-id="bbadf-158">これにより、次のことが可能になります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-158">This enables the following:</span></span>

1. <span data-ttu-id="bbadf-159">API 自体の外部に依存状態をプッシュします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-159">Pushing any dependent state outside of the API itself.</span></span>
2. <span data-ttu-id="bbadf-160">API の外部で構成を実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bbadf-160">Configuration can now be done outside of the API.</span></span>
3. <span data-ttu-id="bbadf-161">依存する値の初期化でエラーが発生しても、としてマニフェストが使用されない可能性があり `TypeInitializationException` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-161">Errors in initialization for dependent values are not likely to manifest as a `TypeInitializationException`.</span></span>
4. <span data-ttu-id="bbadf-162">API のテストが簡単になりました。</span><span class="sxs-lookup"><span data-stu-id="bbadf-162">The API is now easier to test.</span></span>

## <a name="error-management"></a><span data-ttu-id="bbadf-163">エラー管理</span><span class="sxs-lookup"><span data-stu-id="bbadf-163">Error management</span></span>

<span data-ttu-id="bbadf-164">大規模なシステムでのエラー管理は複雑で微妙な的な作業であり、システムがフォールトトレラントで動作しているかどうかを確認するためのシルバーの箇条書きはありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-164">Error management in large systems is a complex and nuanced endeavor, and there are no silver bullets in ensuring your systems are fault-tolerant and behave well.</span></span> <span data-ttu-id="bbadf-165">次のガイドラインでは、このような困難な領域に移動する際のガイダンスを提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-165">The following guidelines should offer guidance in navigating this difficult space.</span></span>

### <a name="represent-error-cases-and-illegal-state-in-types-intrinsic-to-your-domain"></a><span data-ttu-id="bbadf-166">ドメインに固有の型のエラーケースと無効な状態を表します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-166">Represent error cases and illegal state in types intrinsic to your domain</span></span>

<span data-ttu-id="bbadf-167">[判別共用体](../language-reference/discriminated-unions.md)を使用すると、F # では、型システム内の問題のあるプログラムの状態を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-167">With [Discriminated Unions](../language-reference/discriminated-unions.md), F# gives you the ability to represent faulty program state in your type system.</span></span> <span data-ttu-id="bbadf-168">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-168">For example:</span></span>

```fsharp
type MoneyWithdrawalResult =
    | Success of amount:decimal
    | InsufficientFunds of balance:decimal
    | CardExpired of DateTime
    | UndisclosedFailure
```

<span data-ttu-id="bbadf-169">この場合、銀行口座からの送金に失敗する可能性がある既知の方法が3つあります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-169">In this case, there are three known ways that withdrawing money from a bank account can fail.</span></span> <span data-ttu-id="bbadf-170">各エラーケースは型で表されるため、プログラム全体で安全に処理できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-170">Each error case is represented in the type, and can thus be dealt with safely throughout the program.</span></span>

```fsharp
let handleWithdrawal amount =
    let w = withdrawMoney amount
    match w with
    | Success am -> printfn "Successfully withdrew %f" am
    | InsufficientFunds balance -> printfn "Failed: balance is %f" balance
    | CardExpired expiredDate -> printfn "Failed: card expired on %O" expiredDate
    | UndisclosedFailure -> printfn "Failed: unknown"
```

<span data-ttu-id="bbadf-171">一般に、ドメイン内で何らかのエラーが**発生**する可能性のあるさまざまな方法をモデル化できる場合、通常のプログラムフローに加えて、エラー処理コードは処理する必要のあるものとして扱われなくなりました。</span><span class="sxs-lookup"><span data-stu-id="bbadf-171">In general, if you can model the different ways that something can **fail** in your domain, then error handling code is no longer treated as something you must deal with in addition to regular program flow.</span></span> <span data-ttu-id="bbadf-172">これは単に通常のプログラムフローの一部であり、**例外的**とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-172">It is simply a part of normal program flow, and not considered **exceptional**.</span></span> <span data-ttu-id="bbadf-173">これには主に次の2つの利点があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-173">There are two primary benefits to this:</span></span>

1. <span data-ttu-id="bbadf-174">時間の経過と共にドメインが変化するため、保守が容易になります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-174">It is easier to maintain as your domain changes over time.</span></span>
2. <span data-ttu-id="bbadf-175">エラーケースは、単体テストの方が簡単です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-175">Error cases are easier to unit test.</span></span>

### <a name="use-exceptions-when-errors-cannot-be-represented-with-types"></a><span data-ttu-id="bbadf-176">エラーを型で表すことができない場合に例外を使用する</span><span class="sxs-lookup"><span data-stu-id="bbadf-176">Use exceptions when errors cannot be represented with types</span></span>

<span data-ttu-id="bbadf-177">問題のあるドメインでは、すべてのエラーを表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-177">Not all errors can be represented in a problem domain.</span></span> <span data-ttu-id="bbadf-178">この種のエラーは本質的に*例外的*であり、F # で例外を発生させたりキャッチしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-178">These kinds of faults are *exceptional* in nature, hence the ability to raise and catch exceptions in F#.</span></span>

<span data-ttu-id="bbadf-179">まず、[例外のデザインガイドライン](../../standard/design-guidelines/exceptions.md)を読むことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-179">First, it is recommended that you read the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md).</span></span> <span data-ttu-id="bbadf-180">これらは F # にも適用できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-180">These are also applicable to F#.</span></span>

<span data-ttu-id="bbadf-181">例外を発生させるために F # で使用できる主な構成要素は、次の優先順位で考慮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-181">The main constructs available in F# for the purposes of raising exceptions should be considered in the following order of preference:</span></span>

| <span data-ttu-id="bbadf-182">機能</span><span class="sxs-lookup"><span data-stu-id="bbadf-182">Function</span></span> | <span data-ttu-id="bbadf-183">構文</span><span class="sxs-lookup"><span data-stu-id="bbadf-183">Syntax</span></span> | <span data-ttu-id="bbadf-184">目的</span><span class="sxs-lookup"><span data-stu-id="bbadf-184">Purpose</span></span> |
|----------|--------|---------|
| `nullArg` | `nullArg "argumentName"` | <span data-ttu-id="bbadf-185">指定し `System.ArgumentNullException` た引数名を使用してを発生させます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-185">Raises a `System.ArgumentNullException` with the specified argument name.</span></span> |
| `invalidArg` | `invalidArg "argumentName" "message"` | <span data-ttu-id="bbadf-186">`System.ArgumentException`指定された引数名とメッセージを使用して、を発生させます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-186">Raises a `System.ArgumentException` with a specified argument name and message.</span></span> |
| `invalidOp` | `invalidOp "message"` | <span data-ttu-id="bbadf-187">指定し `System.InvalidOperationException` たメッセージを使用して、を発生させます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-187">Raises a `System.InvalidOperationException` with the specified message.</span></span> |
|`raise`| `raise (ExceptionType("message"))` | <span data-ttu-id="bbadf-188">例外をスローするための汎用的な機構。</span><span class="sxs-lookup"><span data-stu-id="bbadf-188">General-purpose mechanism for throwing exceptions.</span></span> |
| `failwith` | `failwith "message"` | <span data-ttu-id="bbadf-189">指定し `System.Exception` たメッセージを使用して、を発生させます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-189">Raises a `System.Exception` with the specified message.</span></span> |
| `failwithf` | `failwithf "format string" argForFormatString` | <span data-ttu-id="bbadf-190">`System.Exception`書式指定文字列とその入力によって決定されたメッセージを使用して、を発生させます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-190">Raises a `System.Exception` with a message determined by the format string and its inputs.</span></span> |

<span data-ttu-id="bbadf-191">`nullArg`、、 `invalidArg` および `invalidOp` `ArgumentNullException` 必要に応じて、をスローする機構としてを使用し `ArgumentException` `InvalidOperationException` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-191">Use `nullArg`, `invalidArg` and `invalidOp` as the mechanism to throw `ArgumentNullException`, `ArgumentException` and `InvalidOperationException` when appropriate.</span></span>

<span data-ttu-id="bbadf-192">`failwith`関数と関数は、通常、特定の例外では `failwithf` なく基本型を生成するため、回避する必要があり `Exception` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-192">The `failwith` and `failwithf` functions should generally be avoided because they raise the base `Exception` type, not a specific exception.</span></span> <span data-ttu-id="bbadf-193">[例外のデザインガイドライン](../../standard/design-guidelines/exceptions.md)に従って、可能な限りより具体的な例外を生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-193">As per the [Exception Design Guidelines](../../standard/design-guidelines/exceptions.md), you want to raise more specific exceptions when you can.</span></span>

### <a name="using-exception-handling-syntax"></a><span data-ttu-id="bbadf-194">例外処理構文の使用</span><span class="sxs-lookup"><span data-stu-id="bbadf-194">Using exception-handling syntax</span></span>

<span data-ttu-id="bbadf-195">F # では、次の構文を使用して例外パターンをサポートしてい `try...with` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-195">F# supports exception patterns via the `try...with` syntax:</span></span>

```fsharp
try
    tryGetFileContents()
with
| :? System.IO.FileNotFoundException as e -> // Do something with it here
| :? System.Security.SecurityException as e -> // Do something with it here
```

<span data-ttu-id="bbadf-196">パターンマッチングを使用して例外が発生したときに実行する機能を調整することは、コードをクリーンな状態に保つ必要がある場合に少し厄介になることがあります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-196">Reconciling functionality to perform in the face of an exception with pattern matching can be a bit tricky if you wish to keep the code clean.</span></span> <span data-ttu-id="bbadf-197">このような処理を行う1つの方法として、[アクティブパターン](../language-reference/active-patterns.md)を使用して、エラーの発生したケースを例外自体にグループ化する方法があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-197">One such way to handle this is to use [active patterns](../language-reference/active-patterns.md) as a means to group functionality surrounding an error case with an exception itself.</span></span> <span data-ttu-id="bbadf-198">たとえば、例外がスローされたときに、例外メタデータで重要な情報を囲む API を使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-198">For example, you may be consuming an API that, when it throws an exception, encloses valuable information in the exception metadata.</span></span> <span data-ttu-id="bbadf-199">アクティブパターン内でキャプチャされた例外の本体にある有用な値をラップ解除し、状況によってはこの値を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-199">Unwrapping a useful value in the body of the captured exception inside the Active Pattern and returning that value can be helpful in some situations.</span></span>

### <a name="do-not-use-monadic-error-handling-to-replace-exceptions"></a><span data-ttu-id="bbadf-200">Monadic のエラー処理を使用して例外を置き換えることはできません</span><span class="sxs-lookup"><span data-stu-id="bbadf-200">Do not use monadic error handling to replace exceptions</span></span>

<span data-ttu-id="bbadf-201">関数型プログラミングでは、例外がいくつかのタブに表示されます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-201">Exceptions are seen as somewhat taboo in functional programming.</span></span> <span data-ttu-id="bbadf-202">実際には、例外は純粋性に違反するため、非常に機能していないと考えるのは安全です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-202">Indeed, exceptions violate purity, so it's safe to consider them not-quite functional.</span></span> <span data-ttu-id="bbadf-203">ただし、これにより、コードを実行する必要がある場合は無視され、実行時エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-203">However, this ignores the reality of where code must run, and that runtime errors can occur.</span></span> <span data-ttu-id="bbadf-204">一般に、望ましくない問題を最小限に抑えるために、ほとんどのものが純粋でも合計でもないことを前提としてコードを記述します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-204">In general, write code on the assumption that most things are neither pure nor total, to minimize unpleasant surprises.</span></span>

<span data-ttu-id="bbadf-205">.NET ランタイムでの関連性と妥当性、および言語間のエコシステム全体に関して、例外の次の主要な長所や側面を考慮することが重要です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-205">It is important to consider the following core strengths/aspects of Exceptions with respect to their relevance and appropriateness in the .NET runtime and cross-language ecosystem as a whole:</span></span>

1. <span data-ttu-id="bbadf-206">これらには詳細な診断情報が含まれており、問題をデバッグするときに非常に便利です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-206">They contain detailed diagnostic information, which is very helpful when debugging an issue.</span></span>
2. <span data-ttu-id="bbadf-207">これらは、ランタイムやその他の .NET 言語によってよく理解されています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-207">They are well-understood by the runtime and other .NET languages.</span></span>
3. <span data-ttu-id="bbadf-208">これらのコードを使用すると、セマンティクスの一部のサブセットをアドホックベースで実装することによって例外を*回避*するコードと比較すると、重要な定型句を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-208">They can reduce significant boilerplate when compared with code that goes out of its way to *avoid* exceptions by implementing some subset of their semantics on an ad-hoc basis.</span></span>

<span data-ttu-id="bbadf-209">この3番目のポイントは重要です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-209">This third point is critical.</span></span> <span data-ttu-id="bbadf-210">複雑な操作の場合、例外を使用しないと、次のような構造体が処理される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-210">For nontrivial complex operations, failing to use exceptions can result in dealing with structures like this:</span></span>

```fsharp
Result<Result<MyType, string>, string list>
```

<span data-ttu-id="bbadf-211">これは、"stringly 型の" エラーでのパターンマッチングのような脆弱なコードにつながる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-211">Which can easily lead to fragile code like pattern matching on "stringly-typed" errors:</span></span>

```fsharp
let result = doStuff()
match result with
| Ok r -> ...
| Error e ->
    if e.Contains "Error string 1" then ...
    elif e.Contains "Error string 2" then ...
    else ... // Who knows?
```

<span data-ttu-id="bbadf-212">さらに、"飲み込む" 型を返す "単純な" 関数を希望する場合には、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-212">Additionally, it can be tempting to swallow any exception in the desire for a "simple" function that returns a "nicer" type:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with _ -> None
```

<span data-ttu-id="bbadf-213">残念ながら、は、 `tryReadAllText` ファイルシステムで発生する可能性のある多数の例外に基づいて多数の例外をスローすることがあります。このコードでは、実際の環境で実際に問題が発生する可能性がある情報を破棄します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-213">Unfortunately, `tryReadAllText` can throw numerous exceptions based on the myriad of things that can happen on a file system, and this code discards away any information about what might actually be going wrong in your environment.</span></span> <span data-ttu-id="bbadf-214">このコードを結果の型に置き換えると、"stringly" というエラーメッセージの解析に戻ります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-214">If you replace this code with a result type, then you're back to "stringly-typed" error message parsing:</span></span>

```fsharp
// This is bad!
let tryReadAllText (path : string) =
    try System.IO.File.ReadAllText path |> Ok
    with e -> Error e.Message

let r = tryReadAllText "path-to-file"
match r with
| Ok text -> ...
| Error e ->
    if e.Contains "uh oh, here we go again..." then ...
    else ...
```

<span data-ttu-id="bbadf-215">例外オブジェクト自体をコンストラクターに配置すると、 `Error` 関数ではなく、呼び出しサイトで例外の型を適切に処理するだけです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-215">And placing the exception object itself in the `Error` constructor just forces you to properly deal with the exception type at the call site rather than in the function.</span></span> <span data-ttu-id="bbadf-216">これを有効にすると、確認済みの例外が効果的に作成されます。これは、API の呼び出し元として扱うことができないことが周知されています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-216">Doing this effectively creates checked exceptions, which are notoriously unfun to deal with as a caller of an API.</span></span>

<span data-ttu-id="bbadf-217">上記の例の代わりに、*特定*の例外をキャッチし、その例外のコンテキストで意味のある値を返す方法があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-217">A good alternative to the above examples is to catch *specific* exceptions and return a meaningful value in the context of that exception.</span></span> <span data-ttu-id="bbadf-218">関数を次のように変更すると `tryReadAllText` 、の `None` 意味が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-218">If you modify the `tryReadAllText` function as follows, `None` has more meaning:</span></span>

```fsharp
let tryReadAllTextIfPresent (path : string) =
    try System.IO.File.ReadAllText path |> Some
    with :? FileNotFoundException -> None
```

<span data-ttu-id="bbadf-219">この関数は、キャッチ全体として機能するのではなく、ファイルが見つからなかった場合に適切に処理し、その意味を戻り値に割り当てるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bbadf-219">Instead of functioning as a catch-all, this function will now properly handle the case when a file was not found and assign that meaning to a return.</span></span> <span data-ttu-id="bbadf-220">この戻り値は、そのエラーケースにマップできますが、コンテキスト情報を破棄したり、コード内のその時点で関連しない可能性のあるケースを呼び出し元に処理したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-220">This return value can map to that error case, while not discarding any contextual information or forcing callers to deal with a case that may not be relevant at that point in the code.</span></span>

<span data-ttu-id="bbadf-221">などの型 `Result<'Success, 'Error>` は、入れ子になっていない基本操作に適しています。また、F # の省略可能な型は、*何か\*\*何*かを返すことができる場合に最適です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-221">Types such as `Result<'Success, 'Error>` are appropriate for basic operations where they aren't nested, and F# optional types are perfect for representing when something could either return *something* or *nothing*.</span></span> <span data-ttu-id="bbadf-222">ただし、例外の代わりにはなりませんが、例外の置換を試行する場合には使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-222">They are not a replacement for exceptions, though, and should not be used in an attempt to replace exceptions.</span></span> <span data-ttu-id="bbadf-223">代わりに、対象の方法で例外およびエラー管理ポリシーの特定の側面に対処するために、慎重に適用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-223">Rather, they should be applied judiciously to address specific aspects of exception and error management policy in targeted ways.</span></span>

## <a name="partial-application-and-point-free-programming"></a><span data-ttu-id="bbadf-224">部分的なアプリケーションとポイントフリープログラミング</span><span class="sxs-lookup"><span data-stu-id="bbadf-224">Partial application and point-free programming</span></span>

<span data-ttu-id="bbadf-225">F # では、部分的なアプリケーションをサポートしているため、ポイントフリースタイルでプログラミングするさまざまな方法がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-225">F# supports partial application, and thus, various ways to program in a point-free style.</span></span> <span data-ttu-id="bbadf-226">これは、モジュール内でのコードの再利用や何らかの実装に役立ちますが、パブリックに公開するものではありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-226">This can be beneficial for code reuse within a module or the implementation of something, but it is not something to expose publicly.</span></span> <span data-ttu-id="bbadf-227">一般に、ポイントフリープログラミングは、それ自体とは関係がありません。そのため、スタイルに専念ない人にとって重要な認知バリアを追加できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-227">In general, point-free programming is not a virtue in and of itself, and can add a significant cognitive barrier for people who are not immersed in the style.</span></span>

### <a name="do-not-use-partial-application-and-currying-in-public-apis"></a><span data-ttu-id="bbadf-228">パブリック Api で部分的なアプリケーションとカリー化を使用しない</span><span class="sxs-lookup"><span data-stu-id="bbadf-228">Do not use partial application and currying in public APIs</span></span>

<span data-ttu-id="bbadf-229">例外がほとんどない場合、パブリック Api で部分的なアプリケーションを使用すると、コンシューマーにとって混乱を招く可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-229">With little exception, the use of partial application in public APIs can be confusing for consumers.</span></span> <span data-ttu-id="bbadf-230">`let`F # コードでは通常、**値**は**関数値**ではなく値です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-230">Usually, `let`-bound values in F# code are **values**, not **function values**.</span></span> <span data-ttu-id="bbadf-231">値と関数の値を混在させると、十分な数のコードを exchange に保存することができます。これは特に、などの演算子と組み合わせて `>>` 関数を作成する場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-231">Mixing together values and function values can result in saving a small number of lines of code in exchange for quite a bit of cognitive overhead, especially if combined with operators such as `>>` to compose functions.</span></span>

### <a name="consider-the-tooling-implications-for-point-free-programming"></a><span data-ttu-id="bbadf-232">ポイントフリープログラミングのツールへの影響について検討する</span><span class="sxs-lookup"><span data-stu-id="bbadf-232">Consider the tooling implications for point-free programming</span></span>

<span data-ttu-id="bbadf-233">カリー化関数では、引数にラベルが付けられません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-233">Curried functions do not label their arguments.</span></span> <span data-ttu-id="bbadf-234">これにはツールの影響があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-234">This has tooling implications.</span></span> <span data-ttu-id="bbadf-235">次の2つの関数について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-235">Consider the following two functions:</span></span>

```fsharp
let func name age =
    printfn "My name is %s and I am %d years old!" name age

let funcWithApplication =
    printfn "My name is %s and I am %d years old!"
```

<span data-ttu-id="bbadf-236">どちらも有効な関数ですが、 `funcWithApplication` はカリー化関数です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-236">Both are valid functions, but `funcWithApplication` is a curried function.</span></span> <span data-ttu-id="bbadf-237">エディターでその型をポイントすると、次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-237">When you hover over their types in an editor, you see this:</span></span>

```fsharp
val func : name:string -> age:int -> unit

val funcWithApplication : (string -> int -> unit)
```

<span data-ttu-id="bbadf-238">呼び出しサイトでは、Visual Studio などのツールのツールヒントには、 `string` 入力型と入力型が実際に表す内容に関する意味のある情報は含まれません `int` 。</span><span class="sxs-lookup"><span data-stu-id="bbadf-238">At the call site, tooltips in tooling such as Visual Studio will not give you meaningful information as to what the `string` and `int` input types actually represent.</span></span>

<span data-ttu-id="bbadf-239">パブリックに使用できるようなポイントフリーのコードが発生した場合は `funcWithApplication` 、ηを完全に展開することをお勧めします。これにより、ツールが引数の意味のある名前を取得できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-239">If you encounter point-free code like `funcWithApplication` that is publicly consumable, it is recommended to do a full η-expansion so that tooling can pick up on meaningful names for arguments.</span></span>

<span data-ttu-id="bbadf-240">さらに、ポイントフリーのコードのデバッグは困難な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-240">Furthermore, debugging point-free code can be challenging, if not impossible.</span></span> <span data-ttu-id="bbadf-241">デバッグツールは、名前にバインドされた値 (たとえば、バインド) に依存しているので、 `let` 実行の途中で中間値を検査できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-241">Debugging tools rely on values bound to names (for example, `let` bindings) so that you can inspect intermediate values midway through execution.</span></span> <span data-ttu-id="bbadf-242">コードに検査する値がない場合、デバッグするものはありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-242">When your code has no values to inspect, there is nothing to debug.</span></span> <span data-ttu-id="bbadf-243">将来的には、デバッグツールは、以前に実行されたパスに基づいてこれらの値を合成するために発展することがありますが、*潜在的*なデバッグ機能については、お客様のコンテンツを生垣するのは得策ではありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-243">In the future, debugging tools may evolve to synthesize these values based on previously executed paths, but it's not a good idea to hedge your bets on *potential* debugging functionality.</span></span>

### <a name="consider-partial-application-as-a-technique-to-reduce-internal-boilerplate"></a><span data-ttu-id="bbadf-244">内部の定型句を減らすための手法として部分的なアプリケーションを検討する</span><span class="sxs-lookup"><span data-stu-id="bbadf-244">Consider partial application as a technique to reduce internal boilerplate</span></span>

<span data-ttu-id="bbadf-245">前の点とは対照的に、部分的なアプリケーションは、アプリケーション内の定型句または API の深い内部構造を減らすための優れたツールです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-245">In contrast to the previous point, partial application is a wonderful tool for reducing boilerplate inside of an application or the deeper internals of an API.</span></span> <span data-ttu-id="bbadf-246">これは、より複雑な Api の実装を単体テストする場合に役立ちます。これは、多くの場合、定型的な処理は面倒です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-246">It can be helpful for unit testing the implementation of more complicated APIs, where boilerplate is often a pain to deal with.</span></span> <span data-ttu-id="bbadf-247">たとえば、次のコードは、このようなフレームワークに外部の依存関係を持たず、関連するオーダーメイド API を習得することなく、ほとんどのモックフレームワークで提供される機能を実現する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-247">For example, the following code shows how you can accomplish what most mocking frameworks give you without taking an external dependency on such a framework and having to learn a related bespoke API.</span></span>

<span data-ttu-id="bbadf-248">たとえば、次のようなソリューションについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-248">For example, consider the following solution topography:</span></span>

```
MySolution.sln
|_/ImplementationLogic.fsproj
|_/ImplementationLogic.Tests.fsproj
|_/API.fsproj
```

<span data-ttu-id="bbadf-249">`ImplementationLogic.fsproj`は、次のようなコードを公開する場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-249">`ImplementationLogic.fsproj` might expose code such as:</span></span>

```fsharp
module Transactions =
    let doTransaction txnContext txnType balance =
        ...

type Transactor(ctx, currentBalance) =
    member _.ExecuteTransaction(txnType) =
        Transactions.doTransaction ctx txtType currentBalance
        ...
```

<span data-ttu-id="bbadf-250">の単体 `Transactions.doTransaction` テスト `ImplementationLogic.Tests.fsproj` は簡単です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-250">Unit testing `Transactions.doTransaction` in `ImplementationLogic.Tests.fsproj` is easy:</span></span>

```fsharp
namespace TransactionsTestingUtil

open Transactions

module TransactionsTestable =
    let getTestableTransactionRoutine mockContext = Transactions.doTransaction mockContext
```

<span data-ttu-id="bbadf-251">モックコンテキストオブジェクトを部分的 `doTransaction` に適用すると、毎回モックコンテキストを構築しなくても、すべての単体テストで関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-251">Partially applying `doTransaction` with a mocking context object lets you call the function in all of your unit tests without needing to construct a mocked context each time:</span></span>

```fsharp
namespace TransactionTests

open Xunit
open TransactionTypes
open TransactionsTestingUtil
open TransactionsTestingUtil.TransactionsTestable

let testableContext =
    { new ITransactionContext with
        member _.TheFirstMember() = ...
        member _.TheSecondMember() = ... }

let transactionRoutine = getTestableTransactionRoutine testableContext

[<Fact>]
let ``Test withdrawal transaction with 0.0 for balance``() =
    let expected = ...
    let actual = transactionRoutine TransactionType.Withdraw 0.0
    Assert.Equal(expected, actual)
```

<span data-ttu-id="bbadf-252">この手法は、コードベース全体に対して汎用的に適用するべきではありませんが、複雑な内部構造およびそれらの内部の単体テストのために定型句を減らすことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-252">This technique should not be universally applied to your entire codebase, but it is a good way to reduce boilerplate for complicated internals and unit testing those internals.</span></span>

## <a name="access-control"></a><span data-ttu-id="bbadf-253">アクセス制御</span><span class="sxs-lookup"><span data-stu-id="bbadf-253">Access control</span></span>

<span data-ttu-id="bbadf-254">F # には、.NET ランタイムで使用できるものから継承された[アクセス制御](../language-reference/access-control.md)のための複数のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-254">F# has multiple options for [Access control](../language-reference/access-control.md), inherited from what is available in the .NET runtime.</span></span> <span data-ttu-id="bbadf-255">これらは、型では使用できません。関数にも使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-255">These are not just usable for types - you can use them for functions, too.</span></span>

* <span data-ttu-id="bbadf-256">`public`パブリックに使用できるようにするには、非型メンバーとメンバーを優先します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-256">Prefer non-`public` types and members until you need them to be publicly consumable.</span></span> <span data-ttu-id="bbadf-257">これにより、コンシューマーの数を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-257">This also minimizes what consumers couple to.</span></span>
* <span data-ttu-id="bbadf-258">すべてのヘルパー機能を維持 `private` してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-258">Strive to keep all helper functionality `private`.</span></span>
* <span data-ttu-id="bbadf-259">`[<AutoOpen>]`ヘルパー関数が多数になる場合は、プライベートモジュールでを使用することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-259">Consider the use of `[<AutoOpen>]` on a private module of helper functions if they become numerous.</span></span>

## <a name="type-inference-and-generics"></a><span data-ttu-id="bbadf-260">型の推論とジェネリック</span><span class="sxs-lookup"><span data-stu-id="bbadf-260">Type inference and generics</span></span>

<span data-ttu-id="bbadf-261">型の推定では、大量の定型句を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-261">Type inference can save you from typing a lot of boilerplate.</span></span> <span data-ttu-id="bbadf-262">また、F # コンパイラでの自動汎化は、追加の作業をほとんど必要とせずに、より汎用的なコードを作成するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-262">And automatic generalization in the F# compiler can help you write more generic code with almost no extra effort on your part.</span></span> <span data-ttu-id="bbadf-263">ただし、これらの機能は、一般には良好ではありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-263">However, these features are not universally good.</span></span>

* <span data-ttu-id="bbadf-264">パブリック Api に明示的な型を使用して引数名にラベルを付けることを検討し、このの型の推定に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-264">Consider labeling argument names with explicit types in public APIs and do not rely on type inference for this.</span></span>

    <span data-ttu-id="bbadf-265">その理由は、コンパイラではなく、API の形状を制御**する必要があるため**です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-265">The reason for this is that **you** should be in control of the shape of your API, not the compiler.</span></span> <span data-ttu-id="bbadf-266">コンパイラは、型を推測する場合でも、適切なジョブを実行できますが、内部的に依存している型が変更されている場合は、API を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-266">Although the compiler can do a fine job at inferring types for you, it is possible to have the shape of your API change if the internals it relies on have changed types.</span></span> <span data-ttu-id="bbadf-267">これは必要なものになりますが、ほとんどの場合、ダウンストリームのコンシューマーが対処する必要がある、API の変更が中断されます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-267">This may be what you want, but it will almost certainly result in a breaking API change that downstream consumers will then have to deal with.</span></span> <span data-ttu-id="bbadf-268">代わりに、パブリック API の構造を明示的に制御する場合は、これらの重大な変更を制御できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-268">Instead, if you explicitly control the shape of your public API, then you can control these breaking changes.</span></span> <span data-ttu-id="bbadf-269">DDD の用語では、これは破損対策レイヤーと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-269">In DDD terms, this can be thought of as an Anti-corruption layer.</span></span>

* <span data-ttu-id="bbadf-270">汎用引数にわかりやすい名前を付けることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-270">Consider giving a meaningful name to your generic arguments.</span></span>

    <span data-ttu-id="bbadf-271">特定のドメインに固有ではない実際の汎用コードを記述する場合を除き、わかりやすい名前を付けることで、他のプログラマが作業中のドメインを理解するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-271">Unless you are writing truly generic code that is not specific to a particular domain, a meaningful name can help other programmers understanding the domain they're working in.</span></span> <span data-ttu-id="bbadf-272">たとえば、ドキュメントデータベースと対話するコンテキストでという名前の型パラメーターを使用すると、一般的なドキュメントの種類が、 `'Document` 作業している関数またはメンバーによって受け入れられることがわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-272">For example, a type parameter named `'Document` in the context of interacting with a document database makes it clearer that generic document types can be accepted by the function or member you are working with.</span></span>

* <span data-ttu-id="bbadf-273">汎用型パラメーターには、パラメーターを使用して名前を付けることを検討してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-273">Consider naming generic type parameters with PascalCase.</span></span>

    <span data-ttu-id="bbadf-274">これは .NET での作業を行うための一般的な方法であるため、snake_case またはキャメルケースではなく、パスワードを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-274">This is the general way to do things in .NET, so it's recommended that you use PascalCase rather than snake_case or camelCase.</span></span>

<span data-ttu-id="bbadf-275">最後に、F # または大規模なコードベースを初めて使用するユーザーにとっては、自動汎化が常に行われるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-275">Finally, automatic generalization is not always a boon for people who are new to F# or a large codebase.</span></span> <span data-ttu-id="bbadf-276">汎用のコンポーネントを使用する場合、認識オーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-276">There is cognitive overhead in using components that are generic.</span></span> <span data-ttu-id="bbadf-277">さらに、自動的に一般化された関数がさまざまな入力型で使用されていない場合 (そのように使用することを意図している場合のみ)、その時点でジェネリックになるという実際の利点はありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-277">Furthermore, if automatically generalized functions are not used with different input types (let alone if they are intended to be used as such), then there is no real benefit to them being generic at that point in time.</span></span> <span data-ttu-id="bbadf-278">記述しているコードが実際にジェネリックになるかどうかを常に考慮してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-278">Always consider if the code you are writing will actually benefit from being generic.</span></span>

## <a name="performance"></a><span data-ttu-id="bbadf-279">パフォーマンス</span><span class="sxs-lookup"><span data-stu-id="bbadf-279">Performance</span></span>

### <a name="prefer-structs-for-small-data-types"></a><span data-ttu-id="bbadf-280">小さいデータ型に対して構造体を優先する</span><span class="sxs-lookup"><span data-stu-id="bbadf-280">Prefer structs for small data types</span></span>

<span data-ttu-id="bbadf-281">構造体 (値型とも呼ばれます) を使用すると、多くの場合、オブジェクトの割り当てが回避されるため、一部のコードのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-281">Using structs (also called Value Types) can often result in higher performance for some code because it typically avoids allocating objects.</span></span> <span data-ttu-id="bbadf-282">ただし、構造体は常に "高速に進む" ボタンではありません。構造体のデータのサイズが16バイトを超えた場合、データをコピーすると、参照型を使用するよりも多くの CPU 時間が消費される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-282">However, structs are not always a "go faster" button: if the size of the data in a struct exceeds 16 bytes, copying the data can often result in more CPU time spend than using a reference type.</span></span>

<span data-ttu-id="bbadf-283">構造体を使用する必要があるかどうかを判断するには、次の条件を考慮してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-283">To determine if you should use a struct, consider the following conditions:</span></span>

- <span data-ttu-id="bbadf-284">データのサイズが16バイト以下の場合。</span><span class="sxs-lookup"><span data-stu-id="bbadf-284">If the size of your data is 16 bytes or smaller.</span></span>
- <span data-ttu-id="bbadf-285">これらのデータ型の多くが、実行中のプログラムのメモリに常駐している可能性が高い場合。</span><span class="sxs-lookup"><span data-stu-id="bbadf-285">If you're likely to have many of these data types resident in memory in a running program.</span></span>

<span data-ttu-id="bbadf-286">最初の条件が適用される場合は、通常、構造体を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-286">If the first condition applies, you should generally use a struct.</span></span> <span data-ttu-id="bbadf-287">両方とも適用される場合は、ほとんどの場合、構造体を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-287">If both apply, you should almost always use a struct.</span></span> <span data-ttu-id="bbadf-288">前の条件が適用される場合もありますが、構造体の使用は参照型を使用するよりも適切ではなく、最悪の場合もあります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-288">There may be some cases where the previous conditions apply, but using a struct is no better or worse than using a reference type, but they are likely to be rare.</span></span> <span data-ttu-id="bbadf-289">ただし、このような変更を行う場合は常に測定することが重要です。また、想定または直感には作用しません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-289">It's important to always measure when making changes like this, though, and not operate on assumption or intuition.</span></span>

#### <a name="prefer-struct-tuples-when-grouping-small-value-types"></a><span data-ttu-id="bbadf-290">小さい値の型をグループ化するときに構造体の組を優先する</span><span class="sxs-lookup"><span data-stu-id="bbadf-290">Prefer struct tuples when grouping small value types</span></span>

<span data-ttu-id="bbadf-291">次の2つの関数について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-291">Consider the following two functions:</span></span>

```fsharp
let rec runWithTuple t offset times =
    let offsetValues x y z offset =
        (x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let (x, y, z) = t
        let r = offsetValues x y z offset
        runWithTuple r offset (times - 1)

let rec runWithStructTuple t offset times =
    let offsetValues x y z offset =
        struct(x + offset, y + offset, z + offset)

    if times <= 0 then
        t
    else
        let struct(x, y, z) = t
        let r = offsetValues x y z offset
        runWithStructTuple r offset (times - 1)
```

<span data-ttu-id="bbadf-292">これらの関数を[BenchmarkDotNet](https://benchmarkdotnet.org/)のような統計ベンチマークツールでベンチマークする場合は、 `runWithStructTuple` 構造体のタプルを使用する関数が40% 高速に実行され、メモリが割り当てられないことがわかります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-292">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that the `runWithStructTuple` function that uses struct tuples runs 40% faster and allocates no memory.</span></span>

<span data-ttu-id="bbadf-293">ただし、これらの結果は、常に独自のコードには当てはまりません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-293">However, these results won't always be the case in your own code.</span></span> <span data-ttu-id="bbadf-294">関数をとしてマークすると `inline` 、参照タプルを使用するコードが追加の最適化を行うことがあります。また、割り当てられるコードは単に最適化されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-294">If you mark a function as `inline`, code that uses reference tuples may get some additional optimizations, or code that would allocate could simply be optimized away.</span></span> <span data-ttu-id="bbadf-295">パフォーマンスに懸念がある場合は常に結果を測定し、想定または直感に基づいて動作することはありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-295">You should always measure results whenever performance is concerned, and never operate based on assumption or intuition.</span></span>

#### <a name="prefer-struct-records-when-the-data-type-is-small"></a><span data-ttu-id="bbadf-296">データ型が小さい場合に構造体レコードを優先する</span><span class="sxs-lookup"><span data-stu-id="bbadf-296">Prefer struct records when the data type is small</span></span>

<span data-ttu-id="bbadf-297">前述の経験則では、 [F # のレコード型](../language-reference/records.md)についても保持しています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-297">The rule of thumb described earlier also holds for [F# record types](../language-reference/records.md).</span></span> <span data-ttu-id="bbadf-298">これらを処理する次のデータ型と関数について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-298">Consider the following data types and functions that process them:</span></span>

```fsharp
type Point = { X: float; Y: float; Z: float }

[<Struct>]
type SPoint = { X: float; Y: float; Z: float }

let rec processPoint (p: Point) offset times =
    let inline offsetValues (p: Point) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processPoint r offset (times - 1)

let rec processStructPoint (p: SPoint) offset times =
    let inline offsetValues (p: SPoint) offset =
        { p with X = p.X + offset; Y = p.Y + offset; Z = p.Z + offset }

    if times <= 0 then
        p
    else
        let r = offsetValues p offset
        processStructPoint r offset (times - 1)
```

<span data-ttu-id="bbadf-299">これは前の組コードに似ていますが、今回の例ではレコードとインライン内部関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-299">This is similar to the previous tuple code, but this time the example uses records and an inlined inner function.</span></span>

<span data-ttu-id="bbadf-300">これらの関数を[BenchmarkDotNet](https://benchmarkdotnet.org/)のような統計ベンチマークツールでベンチマークする場合は、が `processStructPoint` 約60% 高速に実行され、マネージヒープには何も割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-300">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `processStructPoint` runs nearly 60% faster and allocates nothing on the managed heap.</span></span>

#### <a name="prefer-struct-discriminated-unions-when-the-data-type-is-small"></a><span data-ttu-id="bbadf-301">データ型が小さい場合に構造体の判別共用体を優先する</span><span class="sxs-lookup"><span data-stu-id="bbadf-301">Prefer struct discriminated unions when the data type is small</span></span>

<span data-ttu-id="bbadf-302">構造体の組とレコードを使用したパフォーマンスに関する前の観察でも、 [F # 判別共用体](../language-reference/discriminated-unions.md)が保持されます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-302">The previous observations about performance with struct tuples and records also holds for [F# Discriminated Unions](../language-reference/discriminated-unions.md).</span></span> <span data-ttu-id="bbadf-303">次のコードがあるとします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-303">Consider the following code:</span></span>

```fsharp
    type Name = Name of string

    [<Struct>]
    type SName = SName of string

    let reverseName (Name s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> Name

    let structReverseName (SName s) =
        s.ToCharArray()
        |> Array.rev
        |> string
        |> SName
```

<span data-ttu-id="bbadf-304">ドメインのモデリングには、このような単一ケースの判別共用体を定義するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-304">It's common to define single-case Discriminated Unions like this for domain modeling.</span></span> <span data-ttu-id="bbadf-305">これらの関数を[BenchmarkDotNet](https://benchmarkdotnet.org/)のような統計ベンチマークツールでベンチマークすると、 `structReverseName` 小さい文字列の場合よりも約25% 高速に実行さ `reverseName` れます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-305">When you benchmark these functions with a statistical benchmarking tool like [BenchmarkDotNet](https://benchmarkdotnet.org/), you'll find that `structReverseName` runs about 25% faster than `reverseName` for small strings.</span></span> <span data-ttu-id="bbadf-306">大きな文字列の場合は、どちらも同じを実行します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-306">For large strings, both perform about the same.</span></span> <span data-ttu-id="bbadf-307">そのため、この場合は、常に構造体を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-307">So, in this case, it's always preferable to use a struct.</span></span> <span data-ttu-id="bbadf-308">既に説明したように、は常に測定し、想定または直感には作用しません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-308">As previously mentioned, always measure and do not operate on assumptions or intuition.</span></span>

<span data-ttu-id="bbadf-309">前の例では、struct 判別共用体がパフォーマンスを向上させたことが示されていましたが、ドメインをモデル化する場合は、より大きな判別共用体を使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-309">Although the previous example showed that a struct Discriminated Union yielded better performance, it is common to have larger Discriminated Unions when modeling a domain.</span></span> <span data-ttu-id="bbadf-310">このような大規模なデータ型は、それに対する操作に応じて構造体である場合には、より多くのコピーが関係する可能性があるため、実行できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-310">Larger data types like that may not perform as well if they are structs depending on the operations on them, since more copying could be involved.</span></span>

### <a name="functional-programming-and-mutation"></a><span data-ttu-id="bbadf-311">関数型プログラミングと変異</span><span class="sxs-lookup"><span data-stu-id="bbadf-311">Functional programming and mutation</span></span>

<span data-ttu-id="bbadf-312">F # の値は、既定では変更できません。これにより、特定のクラスのバグ (特に同時実行性と並列処理を伴うもの) を回避できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-312">F# values are immutable by default, which allows you to avoid certain classes of bugs (especially those involving concurrency and parallelism).</span></span> <span data-ttu-id="bbadf-313">ただし、場合によっては、実行時間やメモリの割り当てを最適 (または妥当な方法で) 効率よく実現するために、状態のインプレース変化を使用して作業の範囲を実装することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="bbadf-313">However, in certain cases, in order to achieve optimal (or even reasonable) efficiency of execution time or memory allocations, a span of work may best be implemented by using in-place mutation of state.</span></span> <span data-ttu-id="bbadf-314">これは、キーワードを使用して F # を使用すると、オプトインされる可能性があり `mutable` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-314">This is possible in an opt-in basis with F# with the `mutable` keyword.</span></span>

<span data-ttu-id="bbadf-315">`mutable`F # でを使用すると、機能的な純度があると思われる場合があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-315">Use of `mutable` in F# may feel at odds with functional purity.</span></span> <span data-ttu-id="bbadf-316">これは理解しやすいものですが、パフォーマンスの目標に関しては、あらゆる場所で機能的な純度を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-316">This is understandable, but functional purity everywhere can be at odds with performance goals.</span></span> <span data-ttu-id="bbadf-317">妥協点は、呼び出し元が関数を呼び出したときの動作を気にする必要がないように、変異をカプセル化することです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-317">A compromise is to encapsulate mutation such that callers need not care about what happens when they call a function.</span></span> <span data-ttu-id="bbadf-318">これにより、パフォーマンスクリティカルなコードのために、変異型の実装に対して機能インターフェイスを記述できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-318">This allows you to write a functional interface over a mutation-based implementation for performance-critical code.</span></span>

#### <a name="wrap-mutable-code-in-immutable-interfaces"></a><span data-ttu-id="bbadf-319">変更可能なコードを変更できないインターフェイスにラップする</span><span class="sxs-lookup"><span data-stu-id="bbadf-319">Wrap mutable code in immutable interfaces</span></span>

<span data-ttu-id="bbadf-320">参照の透明性を目標として、パフォーマンスが重要な関数の変更可能な underbelly を公開しないコードを記述することが重要です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-320">With referential transparency as a goal, it is critical to write code that does not expose the mutable underbelly of performance-critical functions.</span></span> <span data-ttu-id="bbadf-321">たとえば、次のコードでは、 `Array.contains` F # コアライブラリに関数が実装されています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-321">For example, the following code implements the `Array.contains` function in the F# core library:</span></span>

```fsharp
[<CompiledName("Contains")>]
let inline contains value (array:'T[]) =
    checkNonNull "array" array
    let mutable state = false
    let mutable i = 0
    while not state && i < array.Length do
        state <- value = array.[i]
        i <- i + 1
    state
```

<span data-ttu-id="bbadf-322">この関数を複数回呼び出しても、基になる配列が変更されることはありません。また、使用中に変更可能な状態を維持する必要もありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-322">Calling this function multiple times does not change the underlying array, nor does it require you to maintain any mutable state in consuming it.</span></span> <span data-ttu-id="bbadf-323">その中のほぼすべてのコード行で変異が使用されていても、透過的に透過的になります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-323">It is referentially transparent, even though almost every line of code within it uses mutation.</span></span>

#### <a name="consider-encapsulating-mutable-data-in-classes"></a><span data-ttu-id="bbadf-324">変更可能なデータをクラスにカプセル化することを検討する</span><span class="sxs-lookup"><span data-stu-id="bbadf-324">Consider encapsulating mutable data in classes</span></span>

<span data-ttu-id="bbadf-325">前の例では、変更可能なデータを使用して操作をカプセル化するために単一の関数を使用しています</span><span class="sxs-lookup"><span data-stu-id="bbadf-325">The previous example used a single function to encapsulate operations using mutable data.</span></span> <span data-ttu-id="bbadf-326">これは、より複雑なデータセットには必ずしも十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-326">This is not always sufficient for more complex sets of data.</span></span> <span data-ttu-id="bbadf-327">次の一連の関数について考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-327">Consider the following sets of functions:</span></span>

```fsharp
open System.Collections.Generic

let addToClosureTable (key, value) (t: Dictionary<_,_>) =
    if not (t.ContainsKey(key)) then
        t.Add(key, value)
    else
        t.[key] <- value

let closureTableCount (t: Dictionary<_,_>) = t.Count

let closureTableContains (key, value) (t: Dictionary<_, HashSet<_>>) =
    match t.TryGetValue(key) with
    | (true, v) -> v.Equals(value)
    | (false, _) -> false
```

<span data-ttu-id="bbadf-328">このコードはパフォーマンスに優れていますが、呼び出し元が保持する変異ベースのデータ構造を公開しています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-328">This code is performant, but it exposes the mutation-based data structure that callers are responsible for maintaining.</span></span> <span data-ttu-id="bbadf-329">これは、次のように変更できる基になるメンバーを持たないクラスの内部にラップできます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-329">This can be wrapped inside of a class with no underlying members that can change:</span></span>

```fsharp
open System.Collections.Generic

/// The results of computing the LALR(1) closure of an LR(0) kernel
type Closure1Table() =
    let t = Dictionary<Item0, HashSet<TerminalIndex>>()

    member _.Add(key, value) =
        if not (t.ContainsKey(key)) then
            t.Add(key, value)
        else
            t.[key] <- value

    member _.Count = t.Count

    member _.Contains(key, value) =
        match t.TryGetValue(key) with
        | (true, v) -> v.Equals(value)
        | (false, _) -> false
```

<span data-ttu-id="bbadf-330">`Closure1Table`基になる変異ベースのデータ構造体をカプセル化し、呼び出し元が基になるデータ構造を維持することを強制しません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-330">`Closure1Table` encapsulates the underlying mutation-based data structure, thereby not forcing callers to maintain the underlying data structure.</span></span> <span data-ttu-id="bbadf-331">クラスは、呼び出し元に詳細情報を公開せずに、変異ベースのデータとルーチンをカプセル化するための強力な方法です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-331">Classes are a powerful way to encapsulate data and routines that are mutation-based without exposing the details to callers.</span></span>

#### <a name="prefer-let-mutable-to-reference-cells"></a><span data-ttu-id="bbadf-332">`let mutable`参照セルを優先</span><span class="sxs-lookup"><span data-stu-id="bbadf-332">Prefer `let mutable` to reference cells</span></span>

<span data-ttu-id="bbadf-333">参照セルは、値自体ではなく、値への参照を表す方法です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-333">Reference cells are a way to represent the reference to a value rather than the value itself.</span></span> <span data-ttu-id="bbadf-334">パフォーマンスクリティカルなコードには使用できますが、推奨されません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-334">Although they can be used for performance-critical code, they are not recommended.</span></span> <span data-ttu-id="bbadf-335">次の例を確認してください。</span><span class="sxs-lookup"><span data-stu-id="bbadf-335">Consider the following example:</span></span>

```fsharp
let kernels =
    let acc = ref Set.empty

    processWorkList startKernels (fun kernel ->
        if not ((!acc).Contains(kernel)) then
            acc := (!acc).Add(kernel)
        ...)

    !acc |> Seq.toList
```

<span data-ttu-id="bbadf-336">参照セルを使用すると、後続のすべてのコードで、基になるデータを逆参照して再参照する必要があることが "汚染" になります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-336">The use of a reference cell now "pollutes" all subsequent code with having to dereference and re-reference the underlying data.</span></span> <span data-ttu-id="bbadf-337">代わりに、次の点を考慮してください `let mutable` 。</span><span class="sxs-lookup"><span data-stu-id="bbadf-337">Instead, consider `let mutable`:</span></span>

```fsharp
let kernels =
    let mutable acc = Set.empty

    processWorkList startKernels (fun kernel ->
        if not (acc.Contains(kernel)) then
            acc <- acc.Add(kernel)
        ...)

    acc |> Seq.toList
```

<span data-ttu-id="bbadf-338">ラムダ式の途中での変化点の1つではありませんが、他のすべてのコードは、 `acc` 通常のバインドされた変更できない値の使用とは異なる方法で実行でき `let` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-338">Aside from the single point of mutation in the middle of the lambda expression, all other code that touches `acc` can do so in a manner that is no different to the usage of a normal `let`-bound immutable value.</span></span> <span data-ttu-id="bbadf-339">これにより、時間の経過と共に簡単に変更できるようになります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-339">This will make it easier to change over time.</span></span>

## <a name="object-programming"></a><span data-ttu-id="bbadf-340">オブジェクトプログラミング</span><span class="sxs-lookup"><span data-stu-id="bbadf-340">Object programming</span></span>

<span data-ttu-id="bbadf-341">F # では、オブジェクトとオブジェクト指向 (OO) の概念が完全にサポートされています。</span><span class="sxs-lookup"><span data-stu-id="bbadf-341">F# has full support for objects and object-oriented (OO) concepts.</span></span> <span data-ttu-id="bbadf-342">多くの OO 概念は強力で便利ですが、すべての概念を使用するのが理想的であるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-342">Although many OO concepts are powerful and useful, not all of them are ideal to use.</span></span> <span data-ttu-id="bbadf-343">次の一覧は、高度なレベルでの OO 特徴のカテゴリに関するガイダンスを提供します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-343">The following lists offer guidance on categories of OO features at a high level.</span></span>

<span data-ttu-id="bbadf-344">**さまざまな状況でこれらの機能を使用することを検討してください。**</span><span class="sxs-lookup"><span data-stu-id="bbadf-344">**Consider using these features in many situations:**</span></span>

* <span data-ttu-id="bbadf-345">ドット表記 ( `x.Length` )</span><span class="sxs-lookup"><span data-stu-id="bbadf-345">Dot notation (`x.Length`)</span></span>
* <span data-ttu-id="bbadf-346">インスタンスのメンバー</span><span class="sxs-lookup"><span data-stu-id="bbadf-346">Instance members</span></span>
* <span data-ttu-id="bbadf-347">暗黙的なコンストラクター</span><span class="sxs-lookup"><span data-stu-id="bbadf-347">Implicit constructors</span></span>
* <span data-ttu-id="bbadf-348">静的メンバー</span><span class="sxs-lookup"><span data-stu-id="bbadf-348">Static members</span></span>
* <span data-ttu-id="bbadf-349">インデクサー表記 ( `arr.[x]` )</span><span class="sxs-lookup"><span data-stu-id="bbadf-349">Indexer notation (`arr.[x]`)</span></span>
* <span data-ttu-id="bbadf-350">名前付き引数と省略可能な引数</span><span class="sxs-lookup"><span data-stu-id="bbadf-350">Named and Optional arguments</span></span>
* <span data-ttu-id="bbadf-351">インターフェイスとインターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="bbadf-351">Interfaces and interface implementations</span></span>

<span data-ttu-id="bbadf-352">**これらの機能については先にしないでください。問題を解決するのに便利な場合は、慎重に適用してください。**</span><span class="sxs-lookup"><span data-stu-id="bbadf-352">**Don't reach for these features first, but do judiciously apply them when they are convenient to solve a problem:**</span></span>

* <span data-ttu-id="bbadf-353">メソッドのオーバーロード</span><span class="sxs-lookup"><span data-stu-id="bbadf-353">Method overloading</span></span>
* <span data-ttu-id="bbadf-354">カプセル化された変更可能なデータ</span><span class="sxs-lookup"><span data-stu-id="bbadf-354">Encapsulated mutable data</span></span>
* <span data-ttu-id="bbadf-355">型の演算子</span><span class="sxs-lookup"><span data-stu-id="bbadf-355">Operators on types</span></span>
* <span data-ttu-id="bbadf-356">自動プロパティ</span><span class="sxs-lookup"><span data-stu-id="bbadf-356">Auto properties</span></span>
* <span data-ttu-id="bbadf-357">`IDisposable`およびの実装`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="bbadf-357">Implementing `IDisposable` and `IEnumerable`</span></span>
* <span data-ttu-id="bbadf-358">型拡張</span><span class="sxs-lookup"><span data-stu-id="bbadf-358">Type extensions</span></span>
* <span data-ttu-id="bbadf-359">events</span><span class="sxs-lookup"><span data-stu-id="bbadf-359">Events</span></span>
* <span data-ttu-id="bbadf-360">構造体</span><span class="sxs-lookup"><span data-stu-id="bbadf-360">Structs</span></span>
* <span data-ttu-id="bbadf-361">代理人</span><span class="sxs-lookup"><span data-stu-id="bbadf-361">Delegates</span></span>
* <span data-ttu-id="bbadf-362">列挙型</span><span class="sxs-lookup"><span data-stu-id="bbadf-362">Enums</span></span>

<span data-ttu-id="bbadf-363">**一般に、これらの機能を使用する必要がない場合は、次のようにしてください。**</span><span class="sxs-lookup"><span data-stu-id="bbadf-363">**Generally avoid these features unless you must use them:**</span></span>

* <span data-ttu-id="bbadf-364">継承に基づく型の階層と実装の継承</span><span class="sxs-lookup"><span data-stu-id="bbadf-364">Inheritance-based type hierarchies and implementation inheritance</span></span>
* <span data-ttu-id="bbadf-365">Null と`Unchecked.defaultof<_>`</span><span class="sxs-lookup"><span data-stu-id="bbadf-365">Nulls and `Unchecked.defaultof<_>`</span></span>

### <a name="prefer-composition-over-inheritance"></a><span data-ttu-id="bbadf-366">継承を使ってコンポジションを優先する</span><span class="sxs-lookup"><span data-stu-id="bbadf-366">Prefer composition over inheritance</span></span>

<span data-ttu-id="bbadf-367">[継承](https://en.wikipedia.org/wiki/Composition_over_inheritance)を使用したコンポジションは、優れた F # コードに従うことができる長い表現形式です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-367">[Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance) is a long-standing idiom that good F# code can adhere to.</span></span> <span data-ttu-id="bbadf-368">基本的な原則は、基底クラスを公開せずに、呼び出し元がその基底クラスから継承して機能を取得する必要があることです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-368">The fundamental principle is that you should not expose a base class and force callers to inherit from that base class to get functionality.</span></span>

### <a name="use-object-expressions-to-implement-interfaces-if-you-dont-need-a-class"></a><span data-ttu-id="bbadf-369">クラスが不要な場合は、オブジェクト式を使用してインターフェイスを実装する</span><span class="sxs-lookup"><span data-stu-id="bbadf-369">Use object expressions to implement interfaces if you don't need a class</span></span>

<span data-ttu-id="bbadf-370">[オブジェクト式](../language-reference/object-expressions.md)を使用すると、インターフェイスを即座に実装し、実装されたインターフェイスをクラス内ではなく値にバインドできます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-370">[Object Expressions](../language-reference/object-expressions.md) allow you to implement interfaces on the fly, binding the implemented interface to a value without needing to do so inside of a class.</span></span> <span data-ttu-id="bbadf-371">これは特に、インターフェイスを実装_する必要があり、_ 完全なクラスを必要としない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-371">This is convenient, especially if you _only_ need to implement the interface and have no need for a full class.</span></span>

<span data-ttu-id="bbadf-372">たとえば、次に示すのは、ステートメントのないシンボルを追加した場合にコード修正アクションを提供するために[Ionide](https://ionide.io/)で実行されるコードです `open` 。</span><span class="sxs-lookup"><span data-stu-id="bbadf-372">For example, here is the code that is run in [Ionide](https://ionide.io/) to provide a code fix action if you've added a symbol that you don't have an `open` statement for:</span></span>

```fsharp
    let private createProvider () =
        { new CodeActionProvider with
            member this.provideCodeActions(doc, range, context, ct) =
                let diagnostics = context.diagnostics
                let diagnostic = diagnostics |> Seq.tryFind (fun d -> d.message.Contains "Unused open statement")
                let res =
                    match diagnostic with
                    | None -> [||]
                    | Some d ->
                        let line = doc.lineAt d.range.start.line
                        let cmd = createEmpty<Command>
                        cmd.title <- "Remove unused open"
                        cmd.command <- "fsharp.unusedOpenFix"
                        cmd.arguments <- Some ([| doc |> unbox; line.range |> unbox; |] |> ResizeArray)
                        [|cmd |]
                res
                |> ResizeArray
                |> U2.Case1
        }
```

<span data-ttu-id="bbadf-373">Visual Studio Code API と対話するときにはクラスは不要であるため、オブジェクト式はこのための最適なツールです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-373">Because there is no need for a class when interacting with the Visual Studio Code API, Object Expressions are an ideal tool for this.</span></span> <span data-ttu-id="bbadf-374">また、テストルーチンを使用してインターフェイスをアドホックにスタブする必要がある場合に、単体テストにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-374">They are also valuable for unit testing, when you want to stub out an interface with test routines in an ad hoc manner.</span></span>

## <a name="consider-type-abbreviations-to-shorten-signatures"></a><span data-ttu-id="bbadf-375">型略称を検討して署名を短縮する</span><span class="sxs-lookup"><span data-stu-id="bbadf-375">Consider Type Abbreviations to shorten signatures</span></span>

<span data-ttu-id="bbadf-376">[型略称](../language-reference/type-abbreviations.md)は、関数シグネチャやより複雑な型など、ラベルを別の型に割り当てるのに便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-376">[Type Abbreviations](../language-reference/type-abbreviations.md) are a convenient way to assign a label to another type, such as a function signature or a more complex type.</span></span> <span data-ttu-id="bbadf-377">たとえば、次のエイリアスは、ディープラーニングライブラリである[Cntk](https://docs.microsoft.com/cognitive-toolkit/)で計算を定義するために必要なラベルを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-377">For example, the following alias assigns a label to what's needed to define a computation with [CNTK](https://docs.microsoft.com/cognitive-toolkit/), a deep learning library:</span></span>

```fsharp
open CNTK

// DeviceDescriptor, Variable, and Function all come from CNTK
type Computation = DeviceDescriptor -> Variable -> Function
```

<span data-ttu-id="bbadf-378">名前は、エイリアスが記述されている `Computation` シグネチャに一致する任意の関数を示す便利な方法です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-378">The `Computation` name is a convenient way to denote any function that matches the signature it is aliasing.</span></span> <span data-ttu-id="bbadf-379">このような型の省略形を使用すると便利で、より簡潔なコードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-379">Using Type Abbreviations like this is convenient and allows for more succinct code.</span></span>

### <a name="avoid-using-type-abbreviations-to-represent-your-domain"></a><span data-ttu-id="bbadf-380">ドメインを表すために型の省略形を使用しない</span><span class="sxs-lookup"><span data-stu-id="bbadf-380">Avoid using Type Abbreviations to represent your domain</span></span>

<span data-ttu-id="bbadf-381">型の省略形は、関数のシグネチャに名前を付ける場合に便利ですが、他の型を取りすると混乱する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-381">Although Type Abbreviations are convenient for giving a name to function signatures, they can be confusing when abbreviating other types.</span></span> <span data-ttu-id="bbadf-382">次の略語を考えてみます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-382">Consider this abbreviation:</span></span>

```fsharp
// Does not actually abstract integers.
type BufferSize = int
```

<span data-ttu-id="bbadf-383">これは、次のような複数の方法で混乱する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-383">This can be confusing in multiple ways:</span></span>

* <span data-ttu-id="bbadf-384">`BufferSize`は抽象ではありません。これは、整数の別の名前にすぎません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-384">`BufferSize` is not an abstraction; it is just another name for an integer.</span></span>
* <span data-ttu-id="bbadf-385">`BufferSize`がパブリック API で公開されている場合、単にではなく、誤って解釈される可能性があり `int` ます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-385">If `BufferSize` is exposed in a public API, it can easily be misinterpreted to mean more than just `int`.</span></span> <span data-ttu-id="bbadf-386">通常、ドメイン型には複数の属性があり、のようなプリミティブ型ではありません `int` 。</span><span class="sxs-lookup"><span data-stu-id="bbadf-386">Generally, domain types have multiple attributes to them and are not primitive types like `int`.</span></span> <span data-ttu-id="bbadf-387">この略語は、このような仮定に違反します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-387">This abbreviation violates that assumption.</span></span>
* <span data-ttu-id="bbadf-388">の大文字と小文字の区別は、 `BufferSize` この型がより多くのデータを保持することを意味します。</span><span class="sxs-lookup"><span data-stu-id="bbadf-388">The casing of `BufferSize` (PascalCase) implies that this type holds more data.</span></span>
* <span data-ttu-id="bbadf-389">関数に名前付き引数を指定する場合と比べて、この別名ではわかりやすさが向上していません。</span><span class="sxs-lookup"><span data-stu-id="bbadf-389">This alias does not offer increased clarity compared with providing a named argument to a function.</span></span>
* <span data-ttu-id="bbadf-390">省略形はコンパイルされた IL のマニフェストではありません。これは整数であり、このエイリアスはコンパイル時の構造体です。</span><span class="sxs-lookup"><span data-stu-id="bbadf-390">The abbreviation will not manifest in compiled IL; it is just an integer and this alias is a compile-time construct.</span></span>

```fsharp
module Networking =
    ...
    let send data (bufferSize: int) = ...
```

<span data-ttu-id="bbadf-391">要約すると、型略称の落とし穴は、それらが取りされている型に抽象では**ない**ということです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-391">In summary, the pitfall with Type Abbreviations is that they are **not** abstractions over the types they are abbreviating.</span></span> <span data-ttu-id="bbadf-392">前の例で `BufferSize` は、は、 `int` 追加データを含まない、または `int` 既に含まれているもの以外の型システムの利点を備えただけです。</span><span class="sxs-lookup"><span data-stu-id="bbadf-392">In the previous example, `BufferSize` is just an `int` under the covers, with no additional data, nor any benefits from the type system besides what `int` already has.</span></span>

<span data-ttu-id="bbadf-393">型略称を使用してドメインを表す別の方法として、単一ケース判別共用体を使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-393">An alternative approach to using type abbreviations to represent a domain is to use single-case discriminated unions.</span></span> <span data-ttu-id="bbadf-394">前のサンプルは次のようにモデル化できます。</span><span class="sxs-lookup"><span data-stu-id="bbadf-394">The previous sample can be modeled as follows:</span></span>

```fsharp
type BufferSize = BufferSize of int
```

<span data-ttu-id="bbadf-395">とその基になる値の観点で動作するコードを記述する場合は `BufferSize` 、任意の整数を渡すのではなく、1つを構築する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-395">If you write code that operates in terms of `BufferSize` and its underlying value, you need to construct one rather than pass in any arbitrary integer:</span></span>

```fsharp
module Networking =
    ...
    let send data (BufferSize size) =
    ...
```

<span data-ttu-id="bbadf-396">これにより、関数の `send` `BufferSize` 呼び出し前に値をラップするために呼び出し元が型を構築する必要があるため、任意の整数を誤って関数に渡す可能性が低くなります。</span><span class="sxs-lookup"><span data-stu-id="bbadf-396">This reduces the likelihood of mistakenly passing an arbitrary integer into the `send` function, because the caller must construct a `BufferSize` type to wrap a value before calling the function.</span></span>
