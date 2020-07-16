---
title: C# 7.1 の新機能
description: C# 7.1 の新機能の概要。
ms.date: 04/09/2019
ms.openlocfilehash: fe6e49eb01e24a27bc7970900c05150378ab194a
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174771"
---
# <a name="whats-new-in-c-71"></a><span data-ttu-id="6676f-103">C# 7.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="6676f-103">What's new in C# 7.1</span></span>

<span data-ttu-id="6676f-104">C# 7.1 は C# 言語の最初のポイント リリースです。</span><span class="sxs-lookup"><span data-stu-id="6676f-104">C# 7.1 is the first point release to the C# language.</span></span> <span data-ttu-id="6676f-105">この言語のリリース サイクルが増えたことになります。</span><span class="sxs-lookup"><span data-stu-id="6676f-105">It marks an increased release cadence for the language.</span></span> <span data-ttu-id="6676f-106">新機能は間もなく使用できます。理論的には、各々の新機能が用意できたときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-106">You can use the new features sooner, ideally when each new feature is ready.</span></span> <span data-ttu-id="6676f-107">C# 7.1 では、特定のバージョンの言語に合わせるようにコンパイラを構成する機能が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6676f-107">C# 7.1 adds the ability to configure the compiler to match a specified version of the language.</span></span> <span data-ttu-id="6676f-108">ツールをアップグレードする決定と言語バージョンをアップグレードする決定を分けることができます。</span><span class="sxs-lookup"><span data-stu-id="6676f-108">That enables you to separate the decision to upgrade tools from the decision to upgrade language versions.</span></span>

<span data-ttu-id="6676f-109">C# 7.1 では、[言語バージョン選択](../language-reference/configure-language-version.md)構成要素、3 つの新しい言語機能、新しいコンパイラ動作が追加されます。</span><span class="sxs-lookup"><span data-stu-id="6676f-109">C# 7.1 adds the [language version selection](../language-reference/configure-language-version.md) configuration element, three new language features, and new compiler behavior.</span></span>

<span data-ttu-id="6676f-110">このリリースの新しい言語機能は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="6676f-110">The new language features in this release are:</span></span>

- [<span data-ttu-id="6676f-111">`async` `Main`メソッド</span><span class="sxs-lookup"><span data-stu-id="6676f-111">`async` `Main` method</span></span>](#async-main)
  - <span data-ttu-id="6676f-112">アプリケーションのエントリ ポイントに `async` 修飾子を設定できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-112">The entry point for an application can have the `async` modifier.</span></span>
- [<span data-ttu-id="6676f-113">`default` リテラル式</span><span class="sxs-lookup"><span data-stu-id="6676f-113">`default` literal expressions</span></span>](#default-literal-expressions)
  - <span data-ttu-id="6676f-114">ターゲットの種類を推論できるとき、既定の値式で既定のリテラル式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-114">You can use default literal expressions in default value expressions when the target type can be inferred.</span></span>
- [<span data-ttu-id="6676f-115">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="6676f-115">Inferred tuple element names</span></span>](#inferred-tuple-element-names)
  - <span data-ttu-id="6676f-116">タプル要素の名前は、多くの場合、タプル初期化から推論できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-116">The names of tuple elements can be inferred from tuple initialization in many cases.</span></span>
- [<span data-ttu-id="6676f-117">ジェネリック型パラメーターのパターン マッチ</span><span class="sxs-lookup"><span data-stu-id="6676f-117">Pattern matching on generic type parameters</span></span>](#pattern-matching-on-generic-type-parameters)
  - <span data-ttu-id="6676f-118">型がジェネリック型パラメーターである変数にパターン マッチ式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-118">You can use pattern match expressions on variables whose type is a generic type parameter.</span></span>

<span data-ttu-id="6676f-119">最後に、コンパイラには、[参照アセンブリ生成](#reference-assembly-generation)を制御する 2 つのオプション、`-refout` と `-refonly` があります。</span><span class="sxs-lookup"><span data-stu-id="6676f-119">Finally, the compiler has two options `-refout` and `-refonly` that control [reference assembly generation](#reference-assembly-generation).</span></span>

<span data-ttu-id="6676f-120">ポイント リリースで最新の機能を使用するには、[コンパイラ言語バージョンを構成](../language-reference/configure-language-version.md)し、バージョンを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6676f-120">To use the latest features in a point release, you need to [configure the compiler language version](../language-reference/configure-language-version.md) and select the version.</span></span>

<span data-ttu-id="6676f-121">この記事の残りでは、各機能の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="6676f-121">The remainder of this article provides an overview of each feature.</span></span> <span data-ttu-id="6676f-122">機能ごとに、その背後にある論拠のほか、</span><span class="sxs-lookup"><span data-stu-id="6676f-122">For each feature, you'll learn the reasoning behind it.</span></span> <span data-ttu-id="6676f-123">構文についても説明します。</span><span class="sxs-lookup"><span data-stu-id="6676f-123">You'll learn the syntax.</span></span> <span data-ttu-id="6676f-124">`dotnet try` グローバル ツールを使って、これらの機能をご自身の環境で調べることができます。</span><span class="sxs-lookup"><span data-stu-id="6676f-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="6676f-125">[dotnet try](https://github.com/dotnet/try/blob/master/README.md#setup) グローバル ツールをインストールします。</span><span class="sxs-lookup"><span data-stu-id="6676f-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="6676f-126">[dotnet/try-samples](https://github.com/dotnet/try-samples) リポジトリを複製します。</span><span class="sxs-lookup"><span data-stu-id="6676f-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="6676f-127">現在のディレクトリを、*try-samples* リポジトリの *csharp7* サブディレクトリに設定します。</span><span class="sxs-lookup"><span data-stu-id="6676f-127">Set the current directory to the *csharp7* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="6676f-128">`dotnet try` を実行します。</span><span class="sxs-lookup"><span data-stu-id="6676f-128">Run `dotnet try`.</span></span>

## <a name="async-main"></a><span data-ttu-id="6676f-129">async main</span><span class="sxs-lookup"><span data-stu-id="6676f-129">Async main</span></span>

<span data-ttu-id="6676f-130">*async main* メソッドにより、`Main` メソッドで `await` を使用できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-130">An *async main* method enables you to use `await` in your `Main` method.</span></span>
<span data-ttu-id="6676f-131">以前は次のように記述する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="6676f-131">Previously you would need to write:</span></span>

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

<span data-ttu-id="6676f-132">それが次のように記述できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6676f-132">You can now write:</span></span>

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

<span data-ttu-id="6676f-133">プログラムによって終了コードが返されない場合、<xref:System.Threading.Tasks.Task> を返す `Main` メソッドを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-133">If your program doesn't return an exit code, you can declare a `Main` method that returns a <xref:System.Threading.Tasks.Task>:</span></span>

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

<span data-ttu-id="6676f-134">プログラミング ガイドの [async main](../programming-guide/main-and-command-args/index.md) の記事に詳細があります。</span><span class="sxs-lookup"><span data-stu-id="6676f-134">You can read more about the details in the [async main](../programming-guide/main-and-command-args/index.md) article in the programming guide.</span></span>

## <a name="default-literal-expressions"></a><span data-ttu-id="6676f-135">既定のリテラル式</span><span class="sxs-lookup"><span data-stu-id="6676f-135">Default literal expressions</span></span>

<span data-ttu-id="6676f-136">既定のリテラル式は既定の値式の拡張版です。</span><span class="sxs-lookup"><span data-stu-id="6676f-136">Default literal expressions are an enhancement to default value expressions.</span></span>
<span data-ttu-id="6676f-137">これらの式によって変数が初期化され、既定値になります。</span><span class="sxs-lookup"><span data-stu-id="6676f-137">These expressions initialize a variable to the default value.</span></span> <span data-ttu-id="6676f-138">以前は次のように記述していました。</span><span class="sxs-lookup"><span data-stu-id="6676f-138">Where you previously would write:</span></span>

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

<span data-ttu-id="6676f-139">それが今では、初期化の右項で種類を省略できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="6676f-139">You can now omit the type on the right-hand side of the initialization:</span></span>

```csharp
Func<string, bool> whereClause = default;
```

<span data-ttu-id="6676f-140">詳しくは、「[default 演算子](../language-reference/operators/default.md)」記事の「[default リテラル](../language-reference/operators/default.md#default-literal)」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6676f-140">For more information, see the [default literal](../language-reference/operators/default.md#default-literal) section of the [default operator](../language-reference/operators/default.md) article.</span></span>

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="6676f-141">推論されたタプル要素の名前</span><span class="sxs-lookup"><span data-stu-id="6676f-141">Inferred tuple element names</span></span>

<span data-ttu-id="6676f-142">この機能は、C# 7.0 で導入されたタプル機能の小規模拡張です。</span><span class="sxs-lookup"><span data-stu-id="6676f-142">This feature is a small enhancement to the tuples feature introduced in C# 7.0.</span></span> <span data-ttu-id="6676f-143">タプルを何度初期化しても、代入の右項に使用される変数は、タプル要素に使用するものと同じ名前になります。</span><span class="sxs-lookup"><span data-stu-id="6676f-143">Many times when you initialize a tuple, the variables used for the right side of the assignment are the same as the names you'd like for the tuple elements:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

<span data-ttu-id="6676f-144">タプル要素の名前は、C# 7.1 でタプルの初期化に使用される変数から推測できます。</span><span class="sxs-lookup"><span data-stu-id="6676f-144">The names of tuple elements can be inferred from the variables used to initialize the tuple in C# 7.1:</span></span>

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

<span data-ttu-id="6676f-145">この機能の詳細については、[タプルの型](../language-reference/builtin-types/value-tuples.md)に関する記事を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6676f-145">You can learn more about this feature in the [Tuple types](../language-reference/builtin-types/value-tuples.md) article.</span></span>

## <a name="pattern-matching-on-generic-type-parameters"></a><span data-ttu-id="6676f-146">ジェネリック型パラメーターのパターン マッチ</span><span class="sxs-lookup"><span data-stu-id="6676f-146">Pattern matching on generic type parameters</span></span>

<span data-ttu-id="6676f-147">C#7.1 以降では、`is` 型パターンと `switch` 型パターンのパターン式は、ジェネリック型パラメーターの型を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="6676f-147">Beginning with C# 7.1, the pattern expression for `is` and the `switch` type pattern may have the type of a generic type parameter.</span></span> <span data-ttu-id="6676f-148">これは `struct` 型か `class` 型のいずれかである可能性がある型を確認し、ボックス化を回避するときに最も役立ちます。</span><span class="sxs-lookup"><span data-stu-id="6676f-148">This can be most useful when checking types that may be either `struct` or `class` types, and you want to avoid boxing.</span></span>

## <a name="reference-assembly-generation"></a><span data-ttu-id="6676f-149">参照アセンブリ生成</span><span class="sxs-lookup"><span data-stu-id="6676f-149">Reference assembly generation</span></span>

<span data-ttu-id="6676f-150">"*参照専用アセンブリ*" を生成する新しい 2 つのコンパイラ オプション [-refout](../language-reference/compiler-options/refout-compiler-option.md) と [-refonly](../language-reference/compiler-options/refonly-compiler-option.md) があります。</span><span class="sxs-lookup"><span data-stu-id="6676f-150">There are two new compiler options that generate *reference-only assemblies*: [-refout](../language-reference/compiler-options/refout-compiler-option.md) and [-refonly](../language-reference/compiler-options/refonly-compiler-option.md).</span></span>
<span data-ttu-id="6676f-151">リンク先の記事には、オプションと参照アセンブリに関する詳細があります。</span><span class="sxs-lookup"><span data-stu-id="6676f-151">The linked articles explain these options and reference assemblies in more detail.</span></span>
