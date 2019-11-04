---
title: 式ツリーの実行
description: 式ツリーの実行について説明します。式ツリーを実行可能な中間言語 (IL) 命令に変換します。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: 109e0ac5-2a9c-48b4-ac68-9b6219cdbccf
ms.openlocfilehash: 9af4b346962cb743daddf774e8b3c1f8fa722ae4
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037116"
---
# <a name="executing-expression-trees"></a><span data-ttu-id="c20b4-103">式ツリーの実行</span><span class="sxs-lookup"><span data-stu-id="c20b4-103">Executing Expression Trees</span></span>

[<span data-ttu-id="c20b4-104">前へ -- 式ツリーをサポートするフレームワークの型</span><span class="sxs-lookup"><span data-stu-id="c20b4-104">Previous -- Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

<span data-ttu-id="c20b4-105">*式ツリー*はコードを表すデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="c20b4-105">An *expression tree* is a data structure that represents some code.</span></span>
<span data-ttu-id="c20b4-106">式ツリーはコンパイル済みの実行可能なコードではありません。</span><span class="sxs-lookup"><span data-stu-id="c20b4-106">It is not compiled and executable code.</span></span> <span data-ttu-id="c20b4-107">式ツリーで表される .NET コードを実行する場合は、実行可能な IL 命令に変換する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-107">If you want to execute the .NET code that is represented by an expression tree, you must convert it into executable IL instructions.</span></span>

## <a name="lambda-expressions-to-functions"></a><span data-ttu-id="c20b4-108">ラムダ式から関数への変換</span><span class="sxs-lookup"><span data-stu-id="c20b4-108">Lambda Expressions to Functions</span></span>

<span data-ttu-id="c20b4-109">すべての LambdaExpression、または LambdaExpression の派生型は、実行可能な IL に変換できます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-109">You can convert any LambdaExpression, or any type derived from LambdaExpression into executable IL.</span></span> <span data-ttu-id="c20b4-110">その他の式の型は直接コードに変換できません。</span><span class="sxs-lookup"><span data-stu-id="c20b4-110">Other expression types cannot be directly converted into code.</span></span> <span data-ttu-id="c20b4-111">実際には、この制限はほとんど影響がありません。</span><span class="sxs-lookup"><span data-stu-id="c20b4-111">This restriction has little effect in practice.</span></span> <span data-ttu-id="c20b4-112">ラムダ式は、実行可能な中間言語 (IL) に変換して実行する唯一の式の型です。</span><span class="sxs-lookup"><span data-stu-id="c20b4-112">Lambda expressions are the only types of expressions that you would want to execute by converting to executable intermediate language (IL).</span></span> <span data-ttu-id="c20b4-113">(直接 `ConstantExpression` を実行することにどのような意味があるでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c20b4-113">(Think about what it would mean to directly execute a `ConstantExpression`.</span></span> <span data-ttu-id="c20b4-114">何かに役立つでしょうか。)`LambdaExpression` である式ツリー、または `LambdaExpression` の派生型はすべて IL に変換できます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-114">Would it mean anything useful?) Any expression tree that is a `LambdaExpression`, or a type derived from `LambdaExpression` can be converted to IL.</span></span>
<span data-ttu-id="c20b4-115">式の型 `Expression<TDelegate>` は .NET Core ライブラリで唯一の具体的な例です。</span><span class="sxs-lookup"><span data-stu-id="c20b4-115">The expression type `Expression<TDelegate>` is the only concrete example in the .NET Core libraries.</span></span> <span data-ttu-id="c20b4-116">この型は任意のデリゲート型にマップされる式を表すのに使用されます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-116">It's used to represent an expression that maps to any delegate type.</span></span> <span data-ttu-id="c20b4-117">この型はデリゲート型にマップされるため、.NET で式を検証し、ラムダ式のシグネチャと一致する適切なデリゲートの IL を生成することができます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-117">Because this type maps to a delegate type, .NET can examine the expression, and generate IL for an appropriate delegate that matches the signature of the lambda expression.</span></span> 

<span data-ttu-id="c20b4-118">通常、これによって式とそれに対応するデリゲートの間で単純なマッピングが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-118">In most cases, this creates a simple mapping between an expression, and its corresponding delegate.</span></span> <span data-ttu-id="c20b4-119">たとえば、`Expression<Func<int>>` によって表される式ツリーは、`Func<int>` 型のデリゲートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-119">For example, an expression tree that is represented by `Expression<Func<int>>` would be converted to a delegate of the type `Func<int>`.</span></span> <span data-ttu-id="c20b4-120">任意の戻り値の型と引数リストをもつラムダ式の場合、そのラムダ式によって表される実行可能コードのターゲット型となるデリゲート型が存在します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-120">For a lambda expression with any return type and argument list, there exists a delegate type that is the target type for the executable code represented by that lambda expression.</span></span>

<span data-ttu-id="c20b4-121">`LambdaExpression` 型には、式ツリーを実行可能コードに変換するために使用する `Compile` と `CompileToMethod` メンバーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-121">The `LambdaExpression` type contains `Compile` and `CompileToMethod` members that you would use to convert an expression tree to executable code.</span></span> <span data-ttu-id="c20b4-122">`Compile` メソッドはデリゲートを作成します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-122">The `Compile` method creates a delegate.</span></span> <span data-ttu-id="c20b4-123">`CompileToMethod` メソッドは、式ツリーのコンパイル済み出力を表す IL によって `MethodBuilder` オブジェクトを更新します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-123">The `CompileToMethod` method updates a `MethodBuilder` object with the IL that represents the compiled output of the expression tree.</span></span> <span data-ttu-id="c20b4-124">なお、`CompileToMethod` は完全なデスクトップ フレームワークでのみ利用可能で、.NET Core では利用できません。</span><span class="sxs-lookup"><span data-stu-id="c20b4-124">Note that `CompileToMethod` is only available in the full desktop framework, not in the .NET Core.</span></span>

<span data-ttu-id="c20b4-125">必要に応じて、生成されたデリゲート オブジェクトのシンボル デバッグ情報を受け取る `DebugInfoGenerator` を用意することもできます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-125">Optionally, you can also provide a `DebugInfoGenerator` that will receive the symbol debugging information for the generated delegate object.</span></span> <span data-ttu-id="c20b4-126">これにより、式ツリーをデリゲート オブジェクトに変換し、生成されたデリゲートの完全なデバッグ情報を入手できます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-126">This enables you to convert the expression tree into a delegate object, and have full debugging information about the generated delegate.</span></span>

<span data-ttu-id="c20b4-127">次のコードを使用して、式をデリゲートに変換します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-127">You would convert an expression into a delegate using the following code:</span></span>

```csharp
Expression<Func<int>> add = () => 1 + 2;
var func = add.Compile(); // Create Delegate
var answer = func(); // Invoke Delegate
Console.WriteLine(answer);
```

<span data-ttu-id="c20b4-128">デリゲート型は式の型が基になっています。</span><span class="sxs-lookup"><span data-stu-id="c20b4-128">Notice that the delegate type is based on the expression type.</span></span> <span data-ttu-id="c20b4-129">厳密に型指定された方法でデリゲート オブジェクトを使用する場合は、戻り値の型および引数リストを把握する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-129">You must know the return type and the argument list if you want to use the delegate object in a strongly typed manner.</span></span> <span data-ttu-id="c20b4-130">`LambdaExpression.Compile()` メソッドは `Delegate` 型を返します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-130">The `LambdaExpression.Compile()` method returns the `Delegate` type.</span></span> <span data-ttu-id="c20b4-131">コンパイル時ツールを使用して、引数リストまたは戻り値の型を確認するには、適切なデリゲート型にキャストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-131">You will have to cast it to the correct delegate type to have any compile-time tools check the argument list or return type.</span></span>

## <a name="execution-and-lifetimes"></a><span data-ttu-id="c20b4-132">実行と有効期間</span><span class="sxs-lookup"><span data-stu-id="c20b4-132">Execution and Lifetimes</span></span>

<span data-ttu-id="c20b4-133">`LambdaExpression.Compile()` を呼び出したときに作成されたデリゲートを呼び出して、コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-133">You execute the code by invoking the delegate created when you called `LambdaExpression.Compile()`.</span></span> <span data-ttu-id="c20b4-134">上の例の `add.Compile()` がデリゲートを返す部分に、これが表示されています。</span><span class="sxs-lookup"><span data-stu-id="c20b4-134">You can see this above where `add.Compile()` returns a delegate.</span></span> <span data-ttu-id="c20b4-135">`func()` を呼び出して、デリゲートを呼び出すことにより、コードを実行します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-135">Invoking that delegate, by calling `func()` executes the code.</span></span>

<span data-ttu-id="c20b4-136">そのデリゲートは式ツリーのコードを表します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-136">That delegate represents the code in the expression tree.</span></span> <span data-ttu-id="c20b4-137">そのデリゲートのハンドルを保持して、後で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-137">You can retain the handle to that delegate and invoke it later.</span></span> <span data-ttu-id="c20b4-138">デリゲートが表すコードを実行するたびに、式ツリーをコンパイルする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c20b4-138">You don't need to compile the expression tree each time you want to execute the code it represents.</span></span> <span data-ttu-id="c20b4-139">(式ツリーは不変であるため、あとで同じ式ツリーをコンパイルしても、同じコードを実行するデリゲートが作成されます。)</span><span class="sxs-lookup"><span data-stu-id="c20b4-139">(Remember that expression trees are immutable, and compiling the same expression tree later will create a delegate that executes the same code.)</span></span>

<span data-ttu-id="c20b4-140">より高度なキャッシュ機構を作成して、不要なコンパイルの呼び出しを回避することで、パフォーマンスを向上させようとしないように気を付けてください。</span><span class="sxs-lookup"><span data-stu-id="c20b4-140">I will caution you against trying to create any more sophisticated caching mechanisms to increase performance by avoiding unnecessary compile calls.</span></span> <span data-ttu-id="c20b4-141">また、2 つの任意の式ツリーを比較して、同じアルゴリズムを表しているかどうかを確認することも、実行に時間がかかります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-141">Comparing two arbitrary expression trees to determine if they represent the same algorithm will also be time consuming to execute.</span></span> <span data-ttu-id="c20b4-142">`LambdaExpression.Compile()` への余分な呼び出しを回避して、コンピューティング時間を削減しても、2 つの異なる式ツリーから同じ実行可能コードが得られることを確認するコードを実行するのにもっと多くの時間がかかってしまいます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-142">You'll likely find that the compute time you save avoiding any extra calls to `LambdaExpression.Compile()` will be more than consumed by the time executing code that determines of two different expression trees result in the same executable code.</span></span>

## <a name="caveats"></a><span data-ttu-id="c20b4-143">注意事項</span><span class="sxs-lookup"><span data-stu-id="c20b4-143">Caveats</span></span>

<span data-ttu-id="c20b4-144">ラムダ式をデリゲートにコンパイルして、そのデリゲートを呼び出すのは、式ツリーで実行する最も単純な操作の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="c20b4-144">Compiling a lambda expression to a delegate and invoking that delegate is one of the simplest operations you can perform with an expression tree.</span></span> <span data-ttu-id="c20b4-145">ただし、この簡単な操作にも気をつけるべき点があります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-145">However, even with this simple operation, there are caveats you must be aware of.</span></span> 

<span data-ttu-id="c20b4-146">ラムダ式は、式で参照される任意のローカル変数に対するクロージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-146">Lambda Expressions create closures over any local variables that are referenced in the expression.</span></span> <span data-ttu-id="c20b4-147">デリゲートの一部となる任意の変数は、`Compile` を呼び出す場所で使用でき、得られたデリゲートを実行するときに使用できるように保証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-147">You must guarantee that any variables that would be part of the delegate are usable at the location where you call `Compile`, and when you execute the resulting delegate.</span></span>

<span data-ttu-id="c20b4-148">通常は、このことが true であることをコンパイラが確認します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-148">In general, the compiler will ensure that this is true.</span></span> <span data-ttu-id="c20b4-149">しかし、式が `IDisposable` を実装する変数にアクセスする場合、式ツリーでオブジェクトが保持されている一方で、コードがオブジェクトを破棄する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-149">However, if your expression accesses a variable that implements `IDisposable`, it's possible that your code might dispose of the object while it is still held by the expression tree.</span></span>

<span data-ttu-id="c20b4-150">たとえば、次のコードは `int` が `IDisposable` を実装しないため、正常に機能します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-150">For example, this code works fine, because `int` does not implement `IDisposable`:</span></span>

```csharp
private static Func<int, int> CreateBoundFunc()
{
    var constant = 5; // constant is captured by the expression tree
    Expression<Func<int, int>> expression = (b) => constant + b;
    var rVal = expression.Compile();
    return rVal;
}
```

<span data-ttu-id="c20b4-151">デリゲートはローカル変数 `constant` への参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-151">The delegate has captured a reference to the local variable `constant`.</span></span>
<span data-ttu-id="c20b4-152">`CreateBoundFunc` によって返される関数をあとで実行するとき、その変数はいつでもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-152">That variable is accessed at any time later, when the function returned by `CreateBoundFunc` executes.</span></span>

<span data-ttu-id="c20b4-153">しかし、次の `IDisposable` を実装するクラス (かなり不自然です) はどうでしょうか。</span><span class="sxs-lookup"><span data-stu-id="c20b4-153">However, consider this (rather contrived) class that implements `IDisposable`:</span></span>

```csharp
public class Resource : IDisposable
{
    private bool isDisposed = false;
    public int Argument
    {
        get
        {
            if (!isDisposed)
                return 5;
            else throw new ObjectDisposedException("Resource");
        }
    }

    public void Dispose()
    {
        isDisposed = true;
    }
}
```

<span data-ttu-id="c20b4-154">下記に示す式で使用する場合、`Resource.Argument`プロパティによって参照されるコードを実行すると、`ObjectDisposedException` が得られます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-154">If you use it in an expression as shown below, you'll get an `ObjectDisposedException` when you execute the code referenced by the `Resource.Argument` property:</span></span>

```csharp
private static Func<int, int> CreateBoundResource()
{
    using (var constant = new Resource()) // constant is captured by the expression tree
    {
        Expression<Func<int, int>> expression = (b) => constant.Argument + b;
        var rVal = expression.Compile();
        return rVal;
    }
}
```

<span data-ttu-id="c20b4-155">このメソッドから返されたデリゲートは、`constant` オブジェクトを捕捉しますが、このオブジェクトはすでに破棄されています。</span><span class="sxs-lookup"><span data-stu-id="c20b4-155">The delegate returned from this method has closed over the `constant` object, which has been disposed of.</span></span> <span data-ttu-id="c20b4-156">(オブジェクトは `using` ステートメントで宣言されたため、破棄されています。)</span><span class="sxs-lookup"><span data-stu-id="c20b4-156">(It's been disposed, because it was declared in a `using` statement.)</span></span> 

<span data-ttu-id="c20b4-157">このため、このメソッドから返されたデリゲートを実行すると、実行時に `ObjectDisposedException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-157">Now, when you execute the delegate returned from this method, you'll have a `ObjectDisposedException` thrown at the point of execution.</span></span>

<span data-ttu-id="c20b4-158">コンパイル時の構成要素を表す実行時エラーが発生するのは変だと思うかもしれませんが、式ツリーを扱う場合はそういうものです。</span><span class="sxs-lookup"><span data-stu-id="c20b4-158">It does seem strange to have a runtime error representing a compile-time construct, but that's the world we enter when we work with expression trees.</span></span>

<span data-ttu-id="c20b4-159">この問題はさまざまなバリエーションがあるため、これを回避する一般的なガイダンスを提供することは困難です。</span><span class="sxs-lookup"><span data-stu-id="c20b4-159">There are a lot of permutations of this problem, so it's hard to offer general guidance to avoid it.</span></span> <span data-ttu-id="c20b4-160">式を定義するときにローカル変数へのアクセスに注意するとともに、パブリック API によって返される可能性がある式ツリーを作成する場合、(`this` によって表される) 現在のオブジェクトでのアクセス状態に注意してください。</span><span class="sxs-lookup"><span data-stu-id="c20b4-160">Be careful about accessing local variables when defining expressions, and be careful about accessing state in the current object (represented by `this`) when creating an expression tree that can be returned by a public API.</span></span>

<span data-ttu-id="c20b4-161">式のコードが他のアセンブリのメソッドまたはプロパティを参照する場合があります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-161">The code in your expression may reference methods or properties in other assemblies.</span></span> <span data-ttu-id="c20b4-162">そのアセンブリには、式の定義時、式のコンパイル時、得られたデリゲートの呼び出し時にアクセスが必要になります。</span><span class="sxs-lookup"><span data-stu-id="c20b4-162">That assembly must be accessible when the expression is defined, and when it is compiled, and when the resulting delegate is invoked.</span></span> <span data-ttu-id="c20b4-163">アセンブリが存在しない場合、`ReferencedAssemblyNotFoundException` が発生します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-163">You'll be met with a `ReferencedAssemblyNotFoundException` in cases where it is not present.</span></span>

## <a name="summary"></a><span data-ttu-id="c20b4-164">まとめ</span><span class="sxs-lookup"><span data-stu-id="c20b4-164">Summary</span></span>

<span data-ttu-id="c20b4-165">ラムダ式を表す式ツリーをコンパイルすると、実行可能なデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c20b4-165">Expression Trees that represent lambda expressions can be compiled to create a delegate that you can execute.</span></span> <span data-ttu-id="c20b4-166">この方法は、式ツリーが表すコードを実行するメカニズムの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="c20b4-166">This provides one mechanism to execute the code represented by an expression tree.</span></span>

<span data-ttu-id="c20b4-167">式ツリーは、作成した任意の構成要素を実行するコードを表わしています。</span><span class="sxs-lookup"><span data-stu-id="c20b4-167">The Expression Tree does represent the code that would execute for any given construct you create.</span></span> <span data-ttu-id="c20b4-168">コードをコンパイルして実行する環境が、式を作成する環境と一致している限り、すべてが期待どおりに動作します。</span><span class="sxs-lookup"><span data-stu-id="c20b4-168">As long as the environment where you compile and execute the code matches the environment where you create the expression, everything works as expected.</span></span> <span data-ttu-id="c20b4-169">環境が一致していない場合、エラーが確実に予想されます。このエラーは、式ツリーを使用するコードを最初にテストする段階で発見されるはずです。</span><span class="sxs-lookup"><span data-stu-id="c20b4-169">When that doesn't happen, the errors are very predictable, and they will be caught in your first tests of any code using the expression trees.</span></span>

[<span data-ttu-id="c20b4-170">次へ -- 式の解釈</span><span class="sxs-lookup"><span data-stu-id="c20b4-170">Next -- Interpreting Expressions</span></span>](expression-trees-interpreting.md)
