---
title: コード コントラクト
description: .NET コードで、事前条件、事後条件、およびオブジェクト不変を指定する方法を提供するコードコントラクトについて説明します。
ms.date: 09/05/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Code contracts
ms.assetid: 84526045-496f-489d-8517-a258cf76f040
ms.openlocfilehash: 60f794373af75bd3f745c224e0a8c7a84192e4c4
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904144"
---
# <a name="code-contracts"></a><span data-ttu-id="ec1c6-103">コード コントラクト</span><span class="sxs-lookup"><span data-stu-id="ec1c6-103">Code Contracts</span></span>

<span data-ttu-id="ec1c6-104">コード コントラクトを使用すると、事前条件、事後条件、およびオブジェクト不変条件をコードで指定できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-104">Code contracts provide a way to specify preconditions, postconditions, and object invariants in your code.</span></span> <span data-ttu-id="ec1c6-105">事前条件とは、メソッドやプロパティに入るときに満たされている必要がある要件です。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-105">Preconditions are requirements that must be met when entering a method or property.</span></span> <span data-ttu-id="ec1c6-106">事後条件は、メソッドやプロパティのコードが終了するときの予測を表します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-106">Postconditions describe expectations at the time the method or property code exits.</span></span> <span data-ttu-id="ec1c6-107">オブジェクト不変条件は、正しい状態のクラスに対して予期される状態を表します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-107">Object invariants describe the expected state for a class that is in a good state.</span></span>

<span data-ttu-id="ec1c6-108">コード コントラクトには、コードをマーク付けするためのクラス、コンパイル時の分析のための静的アナライザー、およびランタイム アナライザーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-108">Code contracts include classes for marking your code, a static analyzer for compile-time analysis, and a runtime analyzer.</span></span> <span data-ttu-id="ec1c6-109">コード コントラクトのクラスは <xref:System.Diagnostics.Contracts> 名前空間にあります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-109">The classes for code contracts can be found in the <xref:System.Diagnostics.Contracts> namespace.</span></span>

<span data-ttu-id="ec1c6-110">コード コントラクトには次のような利点があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-110">The benefits of code contracts include the following:</span></span>

- <span data-ttu-id="ec1c6-111">テストの強化: コード コントラクトでは、コントラクトの静的検証、ランタイム チェック、およびドキュメントの生成がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-111">Improved testing: Code contracts provide static contract verification, runtime checking, and documentation generation.</span></span>

- <span data-ttu-id="ec1c6-112">自動テスト ツール: コード コントラクトを使用すると、事前条件を満たさない無意味なテスト引数をフィルターで除外して、より意味のある単体テストを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-112">Automatic testing tools: You can use code contracts to generate more meaningful unit tests by filtering out meaningless test arguments that do not satisfy preconditions.</span></span>

- <span data-ttu-id="ec1c6-113">静的検証: 静的チェックにより、コントラクト違反がないかどうかをプログラムを実行せずに確認できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-113">Static verification: The static checker can decide whether there are any contract violations without running the program.</span></span> <span data-ttu-id="ec1c6-114">暗黙的なコントラクト (null の逆参照、配列の範囲など) と明示的なコントラクトがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-114">It checks for implicit contracts, such as null dereferences and array bounds, and explicit contracts.</span></span>

- <span data-ttu-id="ec1c6-115">リファレンス ドキュメント: ドキュメント生成機能により、既存の XML ドキュメント ファイルにコントラクトの情報が追加されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-115">Reference documentation: The documentation generator augments existing XML documentation files with contract information.</span></span> <span data-ttu-id="ec1c6-116">生成されるドキュメントのページにコントラクトのセクションが含まれるようにするための、[Sandcastle](https://github.com/EWSoftware/SHFB) で使用できるスタイル シートも用意されています。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-116">There are also style sheets that can be used with [Sandcastle](https://github.com/EWSoftware/SHFB) so that the generated documentation pages have contract sections.</span></span>

<span data-ttu-id="ec1c6-117">コントラクトは、すべての .NET Framework 言語ですぐに使用できます。特別なパーサーやコンパイラを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-117">All .NET Framework languages can immediately take advantage of contracts; you do not have to write a special parser or compiler.</span></span> <span data-ttu-id="ec1c6-118">実行するコード コントラクト分析のレベルを指定できる Visual Studio アドインや、</span><span class="sxs-lookup"><span data-stu-id="ec1c6-118">A Visual Studio add-in lets you specify the level of code contract analysis to be performed.</span></span> <span data-ttu-id="ec1c6-119">コントラクトの形式が正しいかどうかを確認したり (型チェックおよび名前解決)、コンパイルされた形式 (MSIL (Microsoft Intermediate Language) 形式) のコントラクトを生成したりできるアナライザーも用意されています。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-119">The analyzers can confirm that the contracts are well-formed (type checking and name resolution) and can produce a compiled form of the contracts in Microsoft intermediate language (MSIL) format.</span></span> <span data-ttu-id="ec1c6-120">Visual Studio でコントラクトを作成する場合は、Visual Studio の標準の IntelliSense も利用できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-120">Authoring contracts in Visual Studio lets you take advantage of the standard IntelliSense provided by the tool.</span></span>

<span data-ttu-id="ec1c6-121">コントラクト クラスのほとんどのメソッドは、条件付きでコンパイルされます。したがって、それらのメソッドの呼び出しは、`#define` ディレクティブを使用して CONTRACTS_FULL という特別なシンボルを定義した場合にのみコンパイラで生成されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-121">Most methods in the contract class are conditionally compiled; that is, the compiler emits calls to these methods only when  you define a special symbol, CONTRACTS_FULL, by using the `#define` directive.</span></span> <span data-ttu-id="ec1c6-122">CONTRACTS_FULL を使用すると、コードで `#ifdef` ディレクティブを使用せずにコントラクトを記述して、コントラクトを含むものと含まないものなど、さまざまなビルドを生成できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-122">CONTRACTS_FULL lets you write contracts in your code without using `#ifdef` directives; you can produce different builds, some with contracts, and some without.</span></span>

<span data-ttu-id="ec1c6-123">コードコントラクトを使用するためのツールと詳細な手順については、Visual Studio marketplace サイトの[コードコントラクト](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-123">For tools and detailed instructions for using code contracts, see [Code Contracts](https://marketplace.visualstudio.com/items?itemName=RiSEResearchinSoftwareEngineering.CodeContractsforNET) on the Visual Studio marketplace site.</span></span>

## <a name="preconditions"></a><span data-ttu-id="ec1c6-124">Preconditions</span><span class="sxs-lookup"><span data-stu-id="ec1c6-124">Preconditions</span></span>

<span data-ttu-id="ec1c6-125">事前条件を指定するには、<xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-125">You can express preconditions by using the <xref:System.Diagnostics.Contracts.Contract.Requires%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ec1c6-126">事前条件では、メソッドが呼び出される状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-126">Preconditions specify state when a method is invoked.</span></span> <span data-ttu-id="ec1c6-127">通常は、有効なパラメーター値を指定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-127">They are generally used to specify valid parameter values.</span></span> <span data-ttu-id="ec1c6-128">事前条件で参照されるすべてのメンバーは、アクセス レベルが少なくともメソッド自体と同じである必要があります。そうでない場合、メソッドのすべての呼び出し元がその事前条件を理解できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-128">All members that are mentioned in preconditions must be at least as accessible as the method itself; otherwise, the precondition might not be understood by all callers of a method.</span></span> <span data-ttu-id="ec1c6-129">また、条件に副作用がないようにする必要もあります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-129">The condition must have no side-effects.</span></span> <span data-ttu-id="ec1c6-130">事前条件が満たされなかった場合の実行時の動作は、ランタイム アナライザーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-130">The run-time behavior of failed preconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="ec1c6-131">たとえば、次の事前条件は、パラメーター `x` が null 以外である必要があることを表しています。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-131">For example, the following precondition expresses that parameter `x` must be non-null.</span></span>

```csharp
Contract.Requires(x != null);
```

<span data-ttu-id="ec1c6-132">事前条件が満たされなかった場合に特定の例外をスローする必要がある場合には、次のように、<xref:System.Diagnostics.Contracts.Contract.Requires%2A> のジェネリック オーバーロードを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-132">If your code must throw a particular exception on failure of a precondition, you can use the generic overload of <xref:System.Diagnostics.Contracts.Contract.Requires%2A> as follows.</span></span>

```csharp
Contract.Requires<ArgumentNullException>(x != null, "x");
```

### <a name="legacy-requires-statements"></a><span data-ttu-id="ec1c6-133">レガシ requires ステートメント</span><span class="sxs-lookup"><span data-stu-id="ec1c6-133">Legacy Requires Statements</span></span>

<span data-ttu-id="ec1c6-134">ほとんどのコードには、`if`-`then`-`throw` コードの形式のパラメーター検証が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-134">Most code contains some parameter validation in the form of `if`-`then`-`throw` code.</span></span> <span data-ttu-id="ec1c6-135">以下の場合は、それらのステートメントがコントラクト ツールで事前条件として認識されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-135">The contract tools recognize these statements as preconditions in the following cases:</span></span>

- <span data-ttu-id="ec1c6-136">それらのステートメントがメソッド内で他のステートメントより前にある場合。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-136">The statements appear before any other statements in a method.</span></span>

- <span data-ttu-id="ec1c6-137">それらのステートメント全体の後に <xref:System.Diagnostics.Contracts.Contract> メソッドの明示的な呼び出し (<xref:System.Diagnostics.Contracts.Contract.Requires%2A>、<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>、<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>、または <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> のいずれかのメソッドの呼び出しなど) がある場合。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-137">The entire set of such statements is followed by an explicit <xref:System.Diagnostics.Contracts.Contract> method call, such as a call to the <xref:System.Diagnostics.Contracts.Contract.Requires%2A>, <xref:System.Diagnostics.Contracts.Contract.Ensures%2A>, <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>, or <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> method.</span></span>

<span data-ttu-id="ec1c6-138">`if`-`then`-`throw` ステートメントがこのような形式になっている場合、それらのステートメントはレガシ `requires` ステートメントとして認識されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-138">When `if`-`then`-`throw` statements appear in this form, the tools recognize them as legacy `requires` statements.</span></span> <span data-ttu-id="ec1c6-139">`if`-`then`-`throw` というシーケンスの後に他のコントラクトがない場合は、<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> メソッドでコードを終了します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-139">If no other contracts follow the `if`-`then`-`throw` sequence, end the code with the <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A?displayProperty=nameWithType> method.</span></span>

```csharp
if (x == null) throw new ...
Contract.EndContractBlock(); // All previous "if" checks are preconditions
```

<span data-ttu-id="ec1c6-140">上のテストの条件は否定の事前条件であることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-140">Note that the condition in the preceding test is a negated precondition.</span></span> <span data-ttu-id="ec1c6-141">(実際の前提条件はになり `x != null` ます)。否定の事前条件は厳しく制限されています。前の例のように記述する必要があります。つまり、句が含まれておらず、 `else` 句の本体が単一のステートメントである必要があり `then` `throw` ます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-141">(The actual precondition would be `x != null`.) A negated precondition is highly restricted: It must be written as shown in the previous example; that is, it should contain no `else` clauses, and the body of the `then` clause must be a single `throw` statement.</span></span> <span data-ttu-id="ec1c6-142">`if` テストには純粋性と可視性の両方の規則が適用されますが (「[使用方法のガイドライン](#usage_guidelines)」を参照)、`throw` 式に適用されるのは純粋性の規則だけです。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-142">The `if` test is subject to both purity and visibility rules (see [Usage Guidelines](#usage_guidelines)), but the `throw` expression is subject only to purity rules.</span></span> <span data-ttu-id="ec1c6-143">ただし、スローされる例外の型には、そのコントラクトが存在するメソッドと同じレベルの可視性が必要です。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-143">However, the type of the exception thrown must be as visible as the method in which the contract occurs.</span></span>

## <a name="postconditions"></a><span data-ttu-id="ec1c6-144">実行後の状態</span><span class="sxs-lookup"><span data-stu-id="ec1c6-144">Postconditions</span></span>

<span data-ttu-id="ec1c6-145">事後条件は、メソッドの終了時の状態についてのコントラクトで、</span><span class="sxs-lookup"><span data-stu-id="ec1c6-145">Postconditions are contracts for the state of a method when it terminates.</span></span> <span data-ttu-id="ec1c6-146">メソッドが終了する直前にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-146">The postcondition is checked just before exiting a method.</span></span> <span data-ttu-id="ec1c6-147">事後条件が満たされなかった場合の実行時の動作は、ランタイム アナライザーによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-147">The run-time behavior of failed postconditions is determined by the runtime analyzer.</span></span>

<span data-ttu-id="ec1c6-148">事後条件では、事前条件とは違って、可視性のレベルがメソッドより低いメンバーも参照できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-148">Unlike preconditions, postconditions may reference members with less visibility.</span></span> <span data-ttu-id="ec1c6-149">事後条件でプライベートの状態を使用して指定した情報は、クライアントが理解できなかったり利用できなかったりする場合もありますが、そのためにクライアントがメソッドを正しく使用できなくなることはありません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-149">A client may not be able to understand or make use of some of the information expressed by a postcondition using private state, but this does not affect the client's ability to use the method correctly.</span></span>

### <a name="standard-postconditions"></a><span data-ttu-id="ec1c6-150">標準の事後条件</span><span class="sxs-lookup"><span data-stu-id="ec1c6-150">Standard Postconditions</span></span>

<span data-ttu-id="ec1c6-151">標準の事後条件を指定するには、<xref:System.Diagnostics.Contracts.Contract.Ensures%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-151">You can express standard postconditions by using the <xref:System.Diagnostics.Contracts.Contract.Ensures%2A> method.</span></span> <span data-ttu-id="ec1c6-152">事後条件は、メソッドが正常に終了した場合に `true` になる必要がある条件を表します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-152">Postconditions express a condition that must be `true` upon normal termination of the method.</span></span>

```csharp
Contract.Ensures(this.F > 0);
```

### <a name="exceptional-postconditions"></a><span data-ttu-id="ec1c6-153">例外の事後条件</span><span class="sxs-lookup"><span data-stu-id="ec1c6-153">Exceptional Postconditions</span></span>

<span data-ttu-id="ec1c6-154">例外の事後条件とは、メソッドによって特定の例外がスローされた場合に `true` になる必要がある事後条件です。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-154">Exceptional postconditions are postconditions that should be `true` when a particular exception is thrown by a method.</span></span> <span data-ttu-id="ec1c6-155">これらの事後条件を指定するには、次の例で示されているように、<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-155">You can specify these postconditions by using the <xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A?displayProperty=nameWithType> method, as the following example shows.</span></span>

```csharp
Contract.EnsuresOnThrow<T>(this.F > 0);
```

<span data-ttu-id="ec1c6-156">引数は、`T` のサブタイプである例外がスローされた場合に `true` になる必要がある条件です。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-156">The argument is the condition that must be `true` whenever an exception that is a subtype of `T` is thrown.</span></span>

<span data-ttu-id="ec1c6-157">例外型の中には、例外の事後条件で使用するのが困難なものもあります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-157">There are some exception types that are difficult to use in an exceptional postcondition.</span></span> <span data-ttu-id="ec1c6-158">たとえば、`T` に対して <xref:System.Exception> 型を使用する場合は、指定する条件が、スローされる例外の型に関係なく (スタック オーバーフローなどの制御不可能な例外の場合でも) メソッドによって保証される必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-158">For example, using the type <xref:System.Exception> for `T` requires the method to guarantee the condition regardless of the type of exception that is thrown, even if it is a stack overflow or other impossible-to-control exception.</span></span> <span data-ttu-id="ec1c6-159">例外の事後条件は、メンバーが呼び出されたときにスローされる可能性がある特定の例外に対してのみ使用するようにしてください (<xref:System.TimeZoneInfo> メソッドの呼び出しに対して <xref:System.InvalidTimeZoneException> がスローされる場合など)。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-159">You should use exceptional postconditions only for specific exceptions that might be thrown when a member is called, for example, when an <xref:System.InvalidTimeZoneException> is thrown for a <xref:System.TimeZoneInfo> method call.</span></span>

### <a name="special-postconditions"></a><span data-ttu-id="ec1c6-160">特殊な事後条件</span><span class="sxs-lookup"><span data-stu-id="ec1c6-160">Special Postconditions</span></span>

<span data-ttu-id="ec1c6-161">次のメソッドは、事後条件の中でのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-161">The following methods may be used only within postconditions:</span></span>

- <span data-ttu-id="ec1c6-162">事後条件でメソッドの戻り値を参照するには、`Contract.Result<T>()` という式を使用します。`T` はメソッドの戻り値の型に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-162">You can refer to method return values in postconditions by using the expression `Contract.Result<T>()`, where `T` is replaced by the return type of the method.</span></span> <span data-ttu-id="ec1c6-163">コンパイラが型を推論できない場合は明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-163">When the compiler is unable to infer the type, you must explicitly provide it.</span></span> <span data-ttu-id="ec1c6-164">たとえば、C# コンパイラでは、引数を受け取らないメソッドの型は推論できないため、`Contract.Ensures(0 <Contract.Result<int>())` という事後条件を使用する必要があります。戻り値の型が `void` のメソッドの事後条件では `Contract.Result<T>()` を参照できません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-164">For example, the C# compiler is unable to infer types for methods that do not take any arguments, so it requires the following postcondition: `Contract.Ensures(0 <Contract.Result<int>())` Methods with a return type of `void` cannot refer to `Contract.Result<T>()` in their postconditions.</span></span>

- <span data-ttu-id="ec1c6-165">事後条件の前の状態の値は、メソッドまたはプロパティの開始時の式の値を表します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-165">A prestate value in a postcondition refers to the value of an expression at the start of a method or property.</span></span> <span data-ttu-id="ec1c6-166">使用される式は `Contract.OldValue<T>(e)` で、`T` は `e` の型です。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-166">It uses the expression `Contract.OldValue<T>(e)`, where `T` is the type of `e`.</span></span> <span data-ttu-id="ec1c6-167">その型をコンパイラが推論できる場合は、このジェネリック型引数を省略できます</span><span class="sxs-lookup"><span data-stu-id="ec1c6-167">You can omit the generic type argument whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="ec1c6-168">(たとえば、C# コンパイラは、引数を受け取るため、常に型を推測します)。で発生する可能性のある制限事項と、古い式を表示できるコンテキストには、いくつかの制限があり `e` ます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-168">(For example, the C# compiler always infers the type because it takes an argument.) There are several restrictions on what can occur in `e` and the contexts in which an old expression may appear.</span></span> <span data-ttu-id="ec1c6-169">まず、古い式に別の古い式を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-169">An old expression cannot contain another old expression.</span></span> <span data-ttu-id="ec1c6-170">また、最も重要な点として、古い式で参照する値は、メソッドの事前条件の状態に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-170">Most importantly, an old expression must refer to a value that existed in the method's precondition state.</span></span> <span data-ttu-id="ec1c6-171">つまり、古い式は、メソッドの事前条件が `true` であれば評価できる式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-171">In other words, it must be an expression that can be evaluated as long as the method's precondition is `true`.</span></span> <span data-ttu-id="ec1c6-172">この規則のいくつかの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-172">Here are several instances of that rule.</span></span>

  - <span data-ttu-id="ec1c6-173">値がメソッドの事前条件の状態に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-173">The value must exist in the method's precondition state.</span></span> <span data-ttu-id="ec1c6-174">オブジェクトのフィールドを参照するには、事前条件でオブジェクトが常に null 以外であることを保証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-174">In order to reference a field on an object, the preconditions must guarantee that the object is always non-null.</span></span>

  - <span data-ttu-id="ec1c6-175">古い式でメソッドの戻り値を参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-175">You cannot refer to the method's return value in an old expression:</span></span>

      ```csharp
      Contract.OldValue(Contract.Result<int>() + x) // ERROR
      ```

  - <span data-ttu-id="ec1c6-176">古い式で `out` パラメーターを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-176">You cannot refer to `out` parameters in an old expression.</span></span>

  - <span data-ttu-id="ec1c6-177">量指定子の範囲がメソッドの戻り値に依存する場合は、量指定子のバインド変数に依存する古い式は使用できません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-177">An old expression cannot depend on the bound variable of a quantifier if the range of the quantifier depends on the return value of the method:</span></span>

      ```csharp
      Contract.ForAll(0, Contract.Result<int>(), i => Contract.OldValue(xs[i]) > 3); // ERROR
      ```

  - <span data-ttu-id="ec1c6-178">古い式で <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> または <xref:System.Diagnostics.Contracts.Contract.Exists%2A> の呼び出しの匿名デリゲートのパラメーターを参照することはできません (メソッド呼び出しのインデクサーまたは引数として使用されている場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-178">An old expression cannot refer to the parameter of the anonymous delegate in a <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> call unless it is used as an indexer or argument to a method call:</span></span>

      ```csharp
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(xs[i]) > 3); // OK
      Contract.ForAll(0, xs.Length, i => Contract.OldValue(i) > 3); // ERROR
      ```

  - <span data-ttu-id="ec1c6-179">古い式の値が匿名デリゲートのパラメーターに依存している場合、古い式をその匿名デリゲートの本体に含めることはできません (匿名デリゲートが <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> メソッドまたは <xref:System.Diagnostics.Contracts.Contract.Exists%2A> メソッドの引数である場合を除く)。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-179">An old expression cannot occur in the body of an anonymous delegate if the value of the old expression depends on any of the parameters of the anonymous delegate, unless the anonymous delegate is an argument to the <xref:System.Diagnostics.Contracts.Contract.ForAll%2A> or <xref:System.Diagnostics.Contracts.Contract.Exists%2A> method:</span></span>

      ```csharp
      Method(... (T t) => Contract.OldValue(... t ...) ...); // ERROR
      ```

  - <span data-ttu-id="ec1c6-180">コントラクトはメソッド本体の前にあるため、`Out` パラメーターは問題になります。ほとんどのコンパイラでは、事後条件で `out` パラメーターを参照することは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-180">`Out` parameters present a problem because contracts appear before the body of the method, and most compilers do not allow references to `out` parameters in postconditions.</span></span> <span data-ttu-id="ec1c6-181">この問題を解決するために、<xref:System.Diagnostics.Contracts.Contract> クラスには <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> メソッドが用意されています。このメソッドを使用すると、`out` パラメーターに基づく事後条件を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-181">To solve this problem, the <xref:System.Diagnostics.Contracts.Contract> class provides the <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method, which allows a postcondition based on an `out` parameter.</span></span>

      ```csharp
      public void OutParam(out int x)
      {
          Contract.Ensures(Contract.ValueAtReturn(out x) == 3);
          x = 3;
      }
      ```

      <span data-ttu-id="ec1c6-182"><xref:System.Diagnostics.Contracts.Contract.OldValue%2A> メソッドと同様に、コンパイラが型を推論できる場合はジェネリック型パラメーターを省略できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-182">As with the <xref:System.Diagnostics.Contracts.Contract.OldValue%2A> method, you can omit the generic type parameter whenever the compiler is able to infer its type.</span></span> <span data-ttu-id="ec1c6-183">このメソッドの呼び出しは、コントラクト リライターによって `out` パラメーターの値に置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-183">The contract rewriter replaces the method call with the value of the `out` parameter.</span></span> <span data-ttu-id="ec1c6-184"><xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> メソッドは事後条件でしか使用できません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-184">The <xref:System.Diagnostics.Contracts.Contract.ValueAtReturn%2A> method may appear only in postconditions.</span></span> <span data-ttu-id="ec1c6-185">このメソッドの引数は、`out` パラメーターか、構造体の `out` パラメーターのフィールド</span><span class="sxs-lookup"><span data-stu-id="ec1c6-185">The argument to the method must be an `out` parameter or a field of a structure `out` parameter.</span></span> <span data-ttu-id="ec1c6-186">(構造体コンストラクターの事後条件でフィールドを参照する場合にも便利です) でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-186">The latter is also useful when referring to fields in the postcondition of a structure constructor.</span></span>

      > [!NOTE]
      > <span data-ttu-id="ec1c6-187">現在、コード コントラクト分析ツールでは、`out` パラメーターが正しく初期化されているかどうかはチェックされません。事後条件に含まれていても無視されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-187">Currently, the code contract analysis tools do not check whether `out` parameters are initialized properly and disregard their mention in the postcondition.</span></span> <span data-ttu-id="ec1c6-188">したがって、前の例で、コントラクトの後の行で `x` に整数を代入せずにこの値をそのまま使用しても、コンパイラで適切なエラーが生成されません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-188">Therefore, in the previous example, if the line after the contract had used the value of `x` instead of assigning an integer to it, a compiler would not issue the correct error.</span></span> <span data-ttu-id="ec1c6-189">ただし、CONTRACTS_FULL プリプロセッサ シンボルが定義されていないビルド (リリース ビルドなど) では、コンパイラでエラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-189">However, on a build where the CONTRACTS_FULL preprocessor symbol is not defined (such asa release build), the compiler will issue an error.</span></span>

## <a name="invariants"></a><span data-ttu-id="ec1c6-190">インバリアント</span><span class="sxs-lookup"><span data-stu-id="ec1c6-190">Invariants</span></span>

<span data-ttu-id="ec1c6-191">オブジェクト不変条件とは、そのオブジェクトがクライアントに表示される場合に常にクラスの各インスタンスに対して true になる必要があり、</span><span class="sxs-lookup"><span data-stu-id="ec1c6-191">Object invariants are conditions that should be true for each instance of a class whenever that object is visible to a client.</span></span> <span data-ttu-id="ec1c6-192">オブジェクトが正しいと見なされる条件を表します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-192">They express the conditions under which the object is considered to be correct.</span></span>

<span data-ttu-id="ec1c6-193">インバリアントなメソッドは、<xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> 属性でマークされることによって識別されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-193">The invariant methods are identified by being marked with the <xref:System.Diagnostics.Contracts.ContractInvariantMethodAttribute> attribute.</span></span> <span data-ttu-id="ec1c6-194">インバリアントなメソッドには、<xref:System.Diagnostics.Contracts.Contract.Invariant%2A> メソッドの一連の呼び出し以外のコードが含まれていない必要があります。それらの呼び出しでは、次の例のように、個々の不変式を指定します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-194">The invariant methods must contain no code except for a sequence of calls to the <xref:System.Diagnostics.Contracts.Contract.Invariant%2A> method, each of which specifies an individual invariant, as shown in the following example.</span></span>

```csharp
[ContractInvariantMethod]
protected void ObjectInvariant ()
{
    Contract.Invariant(this.y >= 0);
    Contract.Invariant(this.x > this.y);
    ...
}
```

<span data-ttu-id="ec1c6-195">不変式は、CONTRACTS_FULL プリプロセッサ シンボルによって条件付きで定義され、</span><span class="sxs-lookup"><span data-stu-id="ec1c6-195">Invariants are conditionally defined by the CONTRACTS_FULL preprocessor symbol.</span></span> <span data-ttu-id="ec1c6-196">ランタイム チェックで各パブリック メソッドの最後にチェックされます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-196">During run-time checking, invariants are checked at the end of each public method.</span></span> <span data-ttu-id="ec1c6-197">不変式が同じクラスのパブリック メソッドを参照している場合は、通常ならそのパブリック メソッドの最後に実行される不変式のチェックが無効になり、</span><span class="sxs-lookup"><span data-stu-id="ec1c6-197">If an invariant mentions a public method in the same class, the invariant check that would normally happen at the end of that public method is disabled.</span></span> <span data-ttu-id="ec1c6-198">そのクラスの一番外側のメソッド呼び出しの最後にのみチェックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-198">Instead, the check occurs only at the end of the outermost method call to that class.</span></span> <span data-ttu-id="ec1c6-199">別のクラスのメソッドの呼び出しのためにクラスへの再入がなされる場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-199">This also happens if the class is re-entered because of a call to a method on another class.</span></span> <span data-ttu-id="ec1c6-200">オブジェクトファイナライザーとの実装では、インバリアントはチェックされません <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-200">Invariants are not checked for an object finalizer and an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span>

<a name="usage_guidelines"></a>

## <a name="usage-guidelines"></a><span data-ttu-id="ec1c6-201">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="ec1c6-201">Usage Guidelines</span></span>

### <a name="contract-ordering"></a><span data-ttu-id="ec1c6-202">コントラクトの順序</span><span class="sxs-lookup"><span data-stu-id="ec1c6-202">Contract Ordering</span></span>

<span data-ttu-id="ec1c6-203">メソッドのコントラクトを記述する際に使用する必要がある要素の順序を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-203">The following table shows the order of elements you should use when you write method contracts.</span></span>

|`If-then-throw statements`|<span data-ttu-id="ec1c6-204">下位互換性のあるパブリックな事前条件。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-204">Backward-compatible public preconditions</span></span>|
|-|-|
|<xref:System.Diagnostics.Contracts.Contract.Requires%2A>|<span data-ttu-id="ec1c6-205">すべてのパブリックな事前条件。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-205">All public preconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="ec1c6-206">すべてのパブリックな (標準の) 事後条件。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-206">All public (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="ec1c6-207">すべてのパブリックな例外の事後条件。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-207">All public exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.Ensures%2A>|<span data-ttu-id="ec1c6-208">すべてのプライベートな/内部の (標準の) 事後条件。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-208">All private/internal (normal) postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EnsuresOnThrow%2A>|<span data-ttu-id="ec1c6-209">すべてのプライベートな/内部の例外の事後条件。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-209">All private/internal exceptional postconditions.</span></span>|
|<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A>|<span data-ttu-id="ec1c6-210">`if`-`then`-`throw` スタイルの事前条件を他のコントラクトなしで使用する場合は、<xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> を呼び出して、前の if チェックがすべて事前条件であることを示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-210">If using `if`-`then`-`throw` style preconditions without any other contracts, place a call to <xref:System.Diagnostics.Contracts.Contract.EndContractBlock%2A> to indicate that all previous if checks are preconditions.</span></span>|

<a name="purity"></a>

### <a name="purity"></a><span data-ttu-id="ec1c6-211">純粋性</span><span class="sxs-lookup"><span data-stu-id="ec1c6-211">Purity</span></span>

<span data-ttu-id="ec1c6-212">コントラクトの中で呼び出されるメソッドは、すべて純粋である (既存の状態を更新しない) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-212">All methods that are called within a contract must be pure; that is, they must not update any preexisting state.</span></span> <span data-ttu-id="ec1c6-213">メソッドに入った後に作成されたオブジェクトは、そのピュア メソッドによって変更できます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-213">A pure method is allowed to modify objects that have been created after entry into the pure method.</span></span>

<span data-ttu-id="ec1c6-214">コード コントラクト ツールでは、現在、次のコード要素が純粋と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-214">Code contract tools currently assume that the following code elements are pure:</span></span>

- <span data-ttu-id="ec1c6-215"><xref:System.Diagnostics.Contracts.PureAttribute> でマークされたメソッド。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-215">Methods that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span>

- <span data-ttu-id="ec1c6-216"><xref:System.Diagnostics.Contracts.PureAttribute> でマークされた型 (この属性はその型のすべてのメソッドに適用されます)。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-216">Types that are marked with the <xref:System.Diagnostics.Contracts.PureAttribute> (the attribute applies to all the type's methods).</span></span>

- <span data-ttu-id="ec1c6-217">プロパティの get アクセサー。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-217">Property get accessors.</span></span>

- <span data-ttu-id="ec1c6-218">演算子 (名前が "op" で始まり、1 つか 2 つのパラメーターを持ち、戻り値の型が void ではない静的メソッド)。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-218">Operators (static methods whose names start with "op", and that have one or two parameters and a non-void return type).</span></span>

- <span data-ttu-id="ec1c6-219">完全修飾名が "System.Diagnostics.Contracts.Contract"、"System.String"、"System.IO.Path"、または "System.Type" で始まるメソッド。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-219">Any method whose fully qualified name begins with "System.Diagnostics.Contracts.Contract", "System.String", "System.IO.Path", or "System.Type".</span></span>

- <span data-ttu-id="ec1c6-220">呼び出されたデリゲート (デリゲート型自体に <xref:System.Diagnostics.Contracts.PureAttribute> 属性が設定されている場合)。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-220">Any invoked delegate, provided that the delegate type itself is attributed with the <xref:System.Diagnostics.Contracts.PureAttribute>.</span></span> <span data-ttu-id="ec1c6-221">デリゲート型の <xref:System.Predicate%601?displayProperty=nameWithType> と <xref:System.Comparison%601?displayProperty=nameWithType> は純粋と見なされます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-221">The delegate types <xref:System.Predicate%601?displayProperty=nameWithType> and <xref:System.Comparison%601?displayProperty=nameWithType> are considered pure.</span></span>

<a name="visibility"></a>

### <a name="visibility"></a><span data-ttu-id="ec1c6-222">表示</span><span class="sxs-lookup"><span data-stu-id="ec1c6-222">Visibility</span></span>

<span data-ttu-id="ec1c6-223">コントラクトで参照されるすべてのメンバーには、少なくとも親のメソッドと同じレベルの可視性が必要です。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-223">All members mentioned in a contract must be at least as visible as the method in which they appear.</span></span> <span data-ttu-id="ec1c6-224">たとえば、パブリック メソッドの事前条件でプライベート フィールドを参照することはできません。そのようなコントラクトは、クライアントがメソッドの呼び出しの前に検証できません。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-224">For example, a private field cannot be mentioned in a precondition for a public method; clients cannot validate such a contract before they call the method.</span></span> <span data-ttu-id="ec1c6-225">ただし、そのフィールドが <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute> でマークされている場合は、これらの規則から除外されます。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-225">However, if the field is marked with the <xref:System.Diagnostics.Contracts.ContractPublicPropertyNameAttribute>, it is exempt from these rules.</span></span>

## <a name="example"></a><span data-ttu-id="ec1c6-226">例</span><span class="sxs-lookup"><span data-stu-id="ec1c6-226">Example</span></span>

<span data-ttu-id="ec1c6-227">次に、コード コントラクトの使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="ec1c6-227">The following example shows the use of code contracts.</span></span>

[!code-csharp[ContractExample#1](../../../samples/snippets/csharp/VS_Snippets_CLR/contractexample/cs/program.cs#1)]
[!code-vb[ContractExample#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/contractexample/vb/program.vb#1)]
