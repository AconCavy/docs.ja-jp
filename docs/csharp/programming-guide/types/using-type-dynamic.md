---
title: dynamic 型の使用 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- dynamic [C#], about dynamic type
- dynamic type [C#]
ms.assetid: 3828989d-c967-4a51-b948-857ebc8fdf26
ms.openlocfilehash: 248f0410aa8fc7c4aa92b844bda19f51fcf09c6d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417594"
---
# <a name="using-type-dynamic-c-programming-guide"></a><span data-ttu-id="ad592-102">dynamic 型の使用 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ad592-102">Using type dynamic (C# Programming Guide)</span></span>

<span data-ttu-id="ad592-103">C# 4 では、`dynamic` という新しい型が導入されています。</span><span class="sxs-lookup"><span data-stu-id="ad592-103">C# 4 introduces a new type, `dynamic`.</span></span> <span data-ttu-id="ad592-104">この型は静的な型ですが、`dynamic` 型のオブジェクトは静的な型チェックをバイパスします。</span><span class="sxs-lookup"><span data-stu-id="ad592-104">The type is a static type, but an object of type `dynamic` bypasses static type checking.</span></span> <span data-ttu-id="ad592-105">ほとんどの場合、`object` 型を使用する場合と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="ad592-105">In most cases, it functions like it has type `object`.</span></span> <span data-ttu-id="ad592-106">コンパイル時には、`dynamic` として型指定された要素はあらゆる操作をサポートすると見なされます。</span><span class="sxs-lookup"><span data-stu-id="ad592-106">At compile time, an element that is typed as `dynamic` is assumed to support any operation.</span></span> <span data-ttu-id="ad592-107">したがって、オブジェクトが COM API、IronPython などの動的言語、HTML ドキュメント オブジェクト モデル (DOM)、リフレクション、プログラムの他の場所のいずれから値を取得するのかを考慮する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ad592-107">Therefore, you do not have to be concerned about whether the object gets its value from a COM API, from a dynamic language such as IronPython, from the HTML Document Object Model (DOM), from reflection, or from somewhere else in the program.</span></span> <span data-ttu-id="ad592-108">ただし、コードが無効な場合には、実行時にエラーが検出されます。</span><span class="sxs-lookup"><span data-stu-id="ad592-108">However, if the code is not valid, errors are caught at run time.</span></span>

<span data-ttu-id="ad592-109">たとえば、次のコードの `exampleMethod1` インスタンス メソッドにパラメーターが 1 つしかない場合、`ec.exampleMethod1(10, 4)` メソッドへの最初の呼び出しは引数を 2 つ含むため、コンパイラはこの呼び出しを無効と認識します。</span><span class="sxs-lookup"><span data-stu-id="ad592-109">For example, if instance method `exampleMethod1` in the following code has only one parameter, the compiler recognizes that the first call to the method, `ec.exampleMethod1(10, 4)`, is not valid because it contains two arguments.</span></span> <span data-ttu-id="ad592-110">この呼び出しではコンパイラ エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="ad592-110">The call causes a compiler error.</span></span> <span data-ttu-id="ad592-111">`dynamic_ec.exampleMethod1(10, 4)` メソッドの 2 番目の呼び出しは、`dynamic_ec` の型が `dynamic` であるため、コンパイラによってチェックされません。</span><span class="sxs-lookup"><span data-stu-id="ad592-111">The second call to the method, `dynamic_ec.exampleMethod1(10, 4)`, is not checked by the compiler because the type of `dynamic_ec` is `dynamic`.</span></span> <span data-ttu-id="ad592-112">そのため、コンパイラ エラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="ad592-112">Therefore, no compiler error is reported.</span></span> <span data-ttu-id="ad592-113">ただし、このエラーがいつまでも検出されないということではありません。</span><span class="sxs-lookup"><span data-stu-id="ad592-113">However, the error does not escape notice indefinitely.</span></span> <span data-ttu-id="ad592-114">実行時に検出されて実行時例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="ad592-114">It is caught at run time and causes a run-time exception.</span></span>

[!code-csharp[CsProgGuideTypes#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#50)]

[!code-csharp[CsProgGuideTypes#56](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#56)]

<span data-ttu-id="ad592-115">これらの例におけるコンパイラの役割は、`dynamic` として型指定されたオブジェクトまたは式に対して各ステートメントが何を実行しようとしているかについて、情報をまとめてパッケージ化することです。</span><span class="sxs-lookup"><span data-stu-id="ad592-115">The role of the compiler in these examples is to package together information about what each statement is proposing to do to the object or expression that is typed as `dynamic`.</span></span> <span data-ttu-id="ad592-116">格納された情報が実行時に調べられ、無効なステートメントがある場合は実行時例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="ad592-116">At run time, the stored information is examined, and any statement that is not valid causes a run-time exception.</span></span>

<span data-ttu-id="ad592-117">ほとんどの動的操作は、結果自体が `dynamic` です。</span><span class="sxs-lookup"><span data-stu-id="ad592-117">The result of most dynamic operations is itself `dynamic`.</span></span> <span data-ttu-id="ad592-118">たとえば、次の例では `testSum` を使用している箇所にマウス ポインターを置くと、IntelliSense によって型が **(ローカル変数) dynamic testSum** と表示されます。</span><span class="sxs-lookup"><span data-stu-id="ad592-118">For example, if you rest the mouse pointer over the use of `testSum` in the following example, IntelliSense displays the type **(local variable) dynamic testSum**.</span></span>

[!code-csharp[CsProgGuideTypes#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#51)]

<span data-ttu-id="ad592-119">結果が `dynamic` ではない操作を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ad592-119">Operations in which the result is not `dynamic` include:</span></span>

* <span data-ttu-id="ad592-120">`dynamic` から別の型への変換。</span><span class="sxs-lookup"><span data-stu-id="ad592-120">Conversions from `dynamic` to another type.</span></span>
* <span data-ttu-id="ad592-121">`dynamic` 型の引数を含むコンストラクターの呼び出し。</span><span class="sxs-lookup"><span data-stu-id="ad592-121">Constructor calls that include arguments of type `dynamic`.</span></span>

<span data-ttu-id="ad592-122">たとえば、次の宣言の `testInstance` の型は、`dynamic` ではなく、`ExampleClass` です。</span><span class="sxs-lookup"><span data-stu-id="ad592-122">For example, the type of `testInstance` in the following declaration is `ExampleClass`, not `dynamic`:</span></span>

[!code-csharp[CsProgGuideTypes#52](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#52)]

<span data-ttu-id="ad592-123">次の「変換」のセクションに変換例を示します。</span><span class="sxs-lookup"><span data-stu-id="ad592-123">Conversion examples are shown in the following section, "Conversions."</span></span>

## <a name="conversions"></a><span data-ttu-id="ad592-124">変換</span><span class="sxs-lookup"><span data-stu-id="ad592-124">Conversions</span></span>

<span data-ttu-id="ad592-125">動的オブジェクトとその他の型との変換は簡単です。</span><span class="sxs-lookup"><span data-stu-id="ad592-125">Conversions between dynamic objects and other types are easy.</span></span> <span data-ttu-id="ad592-126">そのため、開発者は動的な動作と動的でない動作を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="ad592-126">This enables the developer to switch between dynamic and non-dynamic behavior.</span></span>

<span data-ttu-id="ad592-127">次の例に示すように、任意のオブジェクトを動的な型に暗黙的に変換できます。</span><span class="sxs-lookup"><span data-stu-id="ad592-127">Any object can be converted to dynamic type implicitly, as shown in the following examples.</span></span>

[!code-csharp[CsProgGuideTypes#53](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#53)]

<span data-ttu-id="ad592-128">逆に、`dynamic` 型の任意の式に暗黙的な変換を動的に適用できます。</span><span class="sxs-lookup"><span data-stu-id="ad592-128">Conversely, an implicit conversion can be dynamically applied to any expression of type `dynamic`.</span></span>

[!code-csharp[CsProgGuideTypes#54](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#54)]

## <a name="overload-resolution-with-arguments-of-type-dynamic"></a><span data-ttu-id="ad592-129">dynamic 型の引数を使用したオーバーロードの解決</span><span class="sxs-lookup"><span data-stu-id="ad592-129">Overload resolution with arguments of type dynamic</span></span>

<span data-ttu-id="ad592-130">メソッド呼び出しの 1 つ以上の引数が `dynamic` 型を指定している場合、またはメソッド呼び出しの受信側が `dynamic` 型である場合は、コンパイル時ではなく実行時にオーバーロードの解決が実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad592-130">Overload resolution occurs at run time instead of at compile time if one or more of the arguments in a method call have the type `dynamic`, or if the receiver of the method call is of type `dynamic`.</span></span> <span data-ttu-id="ad592-131">次の例では、唯一のアクセス可能な `exampleMethod2` メソッドが文字列引数を受け取るように定義されている場合、`d1` を引数として送信すると、コンパイラ エラーは発生しませんが、実行時例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="ad592-131">In the following example, if the only accessible `exampleMethod2` method is defined to take a string argument, sending `d1` as the argument does not cause a compiler error, but it does cause a run-time exception.</span></span> <span data-ttu-id="ad592-132">`d1` の実行時の型は `int` であり、`exampleMethod2` には文字列が必要であるため、オーバーロードの解決は実行時に失敗します。</span><span class="sxs-lookup"><span data-stu-id="ad592-132">Overload resolution fails at run time because the run-time type of `d1` is `int`, and `exampleMethod2` requires a string.</span></span>

[!code-csharp[CsProgGuideTypes#55](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/usingdynamic.cs#55)]

## <a name="dynamic-language-runtime"></a><span data-ttu-id="ad592-133">動的言語ランタイム</span><span class="sxs-lookup"><span data-stu-id="ad592-133">Dynamic language runtime</span></span>

<span data-ttu-id="ad592-134">動的言語ランタイム (DLR) は、.NET Framework 4 の新しい API です。</span><span class="sxs-lookup"><span data-stu-id="ad592-134">The dynamic language runtime (DLR) is a new API in .NET Framework 4.</span></span> <span data-ttu-id="ad592-135">DLR は、C# の `dynamic` 型だけでなく、IronPython や IronRuby などの動的プログラミング言語の実装もサポートするインフラストラクチャを提供します。</span><span class="sxs-lookup"><span data-stu-id="ad592-135">It provides the infrastructure that supports the `dynamic` type in C#, and also the implementation of dynamic programming languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="ad592-136">DLR の詳細については、「[動的言語ランタイムの概要](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad592-136">For more information about the DLR, see [Dynamic Language Runtime Overview](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md).</span></span>

## <a name="com-interop"></a><span data-ttu-id="ad592-137">COM 相互運用</span><span class="sxs-lookup"><span data-stu-id="ad592-137">COM interop</span></span>

<span data-ttu-id="ad592-138">C# 4 には、Office オートメーション API などの COM API との相互運用エクスペリエンスを強化する複数の機能があります。</span><span class="sxs-lookup"><span data-stu-id="ad592-138">C# 4 includes several features that improve the experience of interoperating with COM APIs such as the Office Automation APIs.</span></span> <span data-ttu-id="ad592-139">この機能強化には、`dynamic` 型の使用、および[名前付き引数と省略可能な引数](../classes-and-structs/named-and-optional-arguments.md)の使用が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ad592-139">Among the improvements are the use of the `dynamic` type, and of [named and optional arguments](../classes-and-structs/named-and-optional-arguments.md).</span></span>

<span data-ttu-id="ad592-140">多くの COM メソッドでは、型を `object` と指定することによって、引数の型と戻り値の型にバリエーションを持たせることができます。</span><span class="sxs-lookup"><span data-stu-id="ad592-140">Many COM methods allow for variation in argument types and return type by designating the types as `object`.</span></span> <span data-ttu-id="ad592-141">このためには、C# で厳密に型指定された変数と連携できるように値の明示的なキャストが必要でした。</span><span class="sxs-lookup"><span data-stu-id="ad592-141">This has necessitated explicit casting of the values to coordinate with strongly typed variables in C#.</span></span> <span data-ttu-id="ad592-142">[-link (C# コンパイラ オプション)](../../language-reference/compiler-options/link-compiler-option.md) オプションを使用してコンパイルする場合、`dynamic` 型が導入されて COM シグネチャの `object` のオカレンスを `dynamic` 型と同様に処理できるようになったため、ほとんどのキャストを回避できます。</span><span class="sxs-lookup"><span data-stu-id="ad592-142">If you compile by using the [-link (C# Compiler Options)](../../language-reference/compiler-options/link-compiler-option.md) option, the introduction of the `dynamic` type enables you to treat the occurrences of `object` in COM signatures as if they were of type `dynamic`, and thereby to avoid much of the casting.</span></span> <span data-ttu-id="ad592-143">たとえば、Microsoft Office Excel スプレッドシートのセルに `dynamic` 型を使用してアクセスする方法と、`dynamic` 型を使用しないでアクセスする方法の対比を次のステートメントに示します。</span><span class="sxs-lookup"><span data-stu-id="ad592-143">For example, the following statements contrast how you access a cell in a Microsoft Office Excel spreadsheet with the `dynamic` type and without the `dynamic` type.</span></span>

[!code-csharp[csOfficeWalkthrough#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#12)]

[!code-csharp[csOfficeWalkthrough#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#13)]

## <a name="related-topics"></a><span data-ttu-id="ad592-144">関連トピック</span><span class="sxs-lookup"><span data-stu-id="ad592-144">Related topics</span></span>

|<span data-ttu-id="ad592-145">Title</span><span class="sxs-lookup"><span data-stu-id="ad592-145">Title</span></span>|<span data-ttu-id="ad592-146">説明</span><span class="sxs-lookup"><span data-stu-id="ad592-146">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="ad592-147">dynamic</span><span class="sxs-lookup"><span data-stu-id="ad592-147">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)|<span data-ttu-id="ad592-148">`dynamic` キーワードの使用法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad592-148">Describes the usage of the `dynamic` keyword.</span></span>|
|[<span data-ttu-id="ad592-149">動的言語ランタイムの概要</span><span class="sxs-lookup"><span data-stu-id="ad592-149">Dynamic Language Runtime Overview</span></span>](../../../framework/reflection-and-codedom/dynamic-language-runtime-overview.md)|<span data-ttu-id="ad592-150">DLR の概要について説明します。DLR は動的言語の一連のサービスを共通言語ランタイム (CLR) に追加するランタイム環境です。</span><span class="sxs-lookup"><span data-stu-id="ad592-150">Provides an overview of the DLR, which is a runtime environment that adds a set of services for dynamic languages to the common language runtime (CLR).</span></span>|
|[<span data-ttu-id="ad592-151">チュートリアル: 動的オブジェクトの作成と使用</span><span class="sxs-lookup"><span data-stu-id="ad592-151">Walkthrough: Creating and Using Dynamic Objects</span></span>](walkthrough-creating-and-using-dynamic-objects.md)|<span data-ttu-id="ad592-152">動的なカスタム オブジェクト、および `IronPython` ライブラリにアクセスするプロジェクトを作成するための詳細な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad592-152">Provides step-by-step instructions for creating a custom dynamic object and for creating a project that accesses an `IronPython` library.</span></span>|
|[<span data-ttu-id="ad592-153">方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする</span><span class="sxs-lookup"><span data-stu-id="ad592-153">How to: Access Office Interop Objects by Using Visual C# Features</span></span>](../interop/how-to-access-office-onterop-objects.md)|<span data-ttu-id="ad592-154">名前付き引数と省略可能な引数、`dynamic` 型、および Office API オブジェクトへのアクセスを簡単にするその他の強化機能を使用するプロジェクトを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ad592-154">Demonstrates how to create a project that uses named and optional arguments, the `dynamic` type, and other enhancements that simplify access to Office API objects.</span></span>|
