---
description: switch (C# リファレンス)
title: C# switch ステートメント
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
- defaultcase_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 2d12091f3c3f10048a98f5f0ecf6a381087faf41
ms.sourcegitcommit: e078b7540a8293ca1b604c9c0da1ff1506f0170b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/13/2020
ms.locfileid: "91997689"
---
# <a name="switch-c-reference"></a><span data-ttu-id="0d52e-103">switch (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0d52e-103">switch (C# reference)</span></span>

<span data-ttu-id="0d52e-104">この記事では、`switch` ステートメントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-104">This article covers the `switch` statement.</span></span> <span data-ttu-id="0d52e-105">`switch` 式 (C# 8.0 で導入) については、[式と演算子](../operators/index.md)のセクションの [`switch` 式](../operators/switch-expression.md)に関する記事をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0d52e-105">For information on the `switch` expression (introduced in C# 8.0), see the article on [`switch` expressions](../operators/switch-expression.md) in the [expressions and operators](../operators/index.md) section.</span></span>

<span data-ttu-id="0d52e-106">`switch` ステートメントは選択ステートメントです。このステートメントは、実行する 1 つの "*switch セクション*" を候補のリストから "*match 式*" によるパターン マッチに基づいて選択します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-106">`switch` is a selection statement that chooses a single *switch section* to execute from a list of candidates based on a pattern match with the *match expression*.</span></span>

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

<span data-ttu-id="0d52e-107">`switch` ステートメントは、1 つの式が 3 つ以上の条件に対してテストされる場合に、[if-else](if-else.md) コンストラクトの代わりとしてよく使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-107">The `switch` statement is often used as an alternative to an [if-else](if-else.md) construct if a single expression is tested against three or more conditions.</span></span> <span data-ttu-id="0d52e-108">たとえば、次の `switch` ステートメントは、`Color` 型の変数に 3 つの値のいずれかが含まれているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-108">For example, the following `switch` statement determines whether a variable of type `Color` has one of three values:</span></span>

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

<span data-ttu-id="0d52e-109">これは、`if`-`else` コンストラクトを使用する次の例に相当します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-109">It's equivalent to the following example that uses an `if`-`else` construct.</span></span>

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a><span data-ttu-id="0d52e-110">match 式</span><span class="sxs-lookup"><span data-stu-id="0d52e-110">The match expression</span></span>

<span data-ttu-id="0d52e-111">match 式は、`case` ラベルのパターンと照合する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-111">The match expression provides the value to match against the patterns in `case` labels.</span></span> <span data-ttu-id="0d52e-112">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0d52e-112">Its syntax is:</span></span>

```csharp
   switch (expr)
```

<span data-ttu-id="0d52e-113">C# 6 以前では、match 式は、次の型の値を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-113">In C# 6 and earlier, the match expression must be an expression that returns a value of the following types:</span></span>

- <span data-ttu-id="0d52e-114">[char](../builtin-types/char.md)。</span><span class="sxs-lookup"><span data-stu-id="0d52e-114">a [char](../builtin-types/char.md).</span></span>
- <span data-ttu-id="0d52e-115">[string](../builtin-types/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0d52e-115">a [string](../builtin-types/reference-types.md).</span></span>
- <span data-ttu-id="0d52e-116">[bool](../builtin-types/bool.md)。</span><span class="sxs-lookup"><span data-stu-id="0d52e-116">a [bool](../builtin-types/bool.md).</span></span>
- <span data-ttu-id="0d52e-117">[integral](../builtin-types/integral-numeric-types.md) 値。`int` や `long` など。</span><span class="sxs-lookup"><span data-stu-id="0d52e-117">an [integral](../builtin-types/integral-numeric-types.md) value, such as an `int` or a `long`.</span></span>
- <span data-ttu-id="0d52e-118">[enum](../builtin-types/enum.md)値。</span><span class="sxs-lookup"><span data-stu-id="0d52e-118">an [enum](../builtin-types/enum.md) value.</span></span>

<span data-ttu-id="0d52e-119">C# 7.0 以降は、match 式は NULL 以外の式にできます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-119">Starting with C# 7.0, the match expression can be any non-null expression.</span></span>

## <a name="the-switch-section"></a><span data-ttu-id="0d52e-120">switch セクション</span><span class="sxs-lookup"><span data-stu-id="0d52e-120">The switch section</span></span>

<span data-ttu-id="0d52e-121">`switch` ステートメントには、1 つ以上の switch セクションが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-121">A `switch` statement includes one or more switch sections.</span></span> <span data-ttu-id="0d52e-122">各 switch セクションには、1 つ以上の "*case ラベル*" (case ラベルまたは default ラベルのいずれか) と、その後に続く 1 つ以上のステートメントのリストが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-122">Each switch section contains one or more *case labels* (either a case or default label) followed by one or more statements.</span></span> <span data-ttu-id="0d52e-123">`switch` ステートメントでは、任意の switch セクションに少なくとも 1 つの default ラベルを配置することができます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-123">The `switch` statement may include at most one default label placed in any switch section.</span></span> <span data-ttu-id="0d52e-124">次の例に、3 つの switch セクションを持つシンプルな `switch` ステートメントを示します。各セクションには 2 つのステートメントがあります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-124">The following example shows a simple `switch` statement that has three switch sections, each containing two statements.</span></span> <span data-ttu-id="0d52e-125">2 番目の switch セクションには、`case 2:` ラベルと `case 3:` ラベルが含められています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-125">The second switch section contains the `case 2:` and `case 3:` labels.</span></span>

<span data-ttu-id="0d52e-126">`switch` ステートメントには、任意の数の switch セクションを含めることができます。また、次の例に示すように、各セクションに 1 つ以上の case ラベルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-126">A `switch` statement can include any number of switch sections, and each section can have one or more case labels, as shown in the following example.</span></span> <span data-ttu-id="0d52e-127">ただし、複数の case ラベルで同じ式を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="0d52e-127">However, no two case labels may contain the same expression.</span></span>

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

<span data-ttu-id="0d52e-128">1 つの switch ステートメントでは、1 つの switch セクションのみが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-128">Only one switch section in a switch statement executes.</span></span> <span data-ttu-id="0d52e-129">C# では 1 つの switch セクションから次のセクションへ実行が連続することが許可されません。</span><span class="sxs-lookup"><span data-stu-id="0d52e-129">C# doesn't allow execution to continue from one switch section to the next.</span></span> <span data-ttu-id="0d52e-130">このため、次のコードでは、コンパイラ エラー CS0163:"コントロールは 1 つの case ラベルから別のラベル (\<case label>) へ流れ落ちることはできません。" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-130">Because of this, the following code generates a compiler error, CS0163: "Control cannot fall through from one case label (\<case label>) to another."</span></span>

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

<span data-ttu-id="0d52e-131">この要件は、通常、[break](break.md) ステートメント、[goto](goto.md) ステートメント、または [return](return.md) ステートメントを使用して、switch セクションを明示的に終了することによって満たされます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-131">This requirement is usually met by explicitly exiting the switch section by using a [break](break.md), [goto](goto.md), or [return](return.md) statement.</span></span> <span data-ttu-id="0d52e-132">ただし、次のコードも有効です。このコードでは、プログラムの制御が `default` switch セクションにフォール スルー (流れ落ちる、case ラベルを超えてコードを実行することが) できないためです。</span><span class="sxs-lookup"><span data-stu-id="0d52e-132">However, the following code is also valid, because it ensures that program control can't fall through to the `default` switch section.</span></span>

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

<span data-ttu-id="0d52e-133">match 式に一致する case ラベルが含まれた switch セクションにおけるステートメント リストの実行は、ステートメント リストに沿って最初のステートメントから順に開始され、通常は、`break`、`goto case`、`goto label`、`return`、または`throw` などのジャンプ ステートメントに達するまで続きます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-133">Execution of the statement list in the switch section with a case label that matches the match expression begins with the first statement and proceeds through the statement list, typically until a jump statement, such as a `break`, `goto case`, `goto label`, `return`, or `throw`, is reached.</span></span> <span data-ttu-id="0d52e-134">この時点で、制御は `switch` ステートメントの外側、または他の case ラベルに移動します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-134">At that point, control is transferred outside the `switch` statement or to another case label.</span></span> <span data-ttu-id="0d52e-135">`goto` ステートメントを使用する場合は、制御を constant ラベルに転送する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-135">A `goto` statement, if it's used, must transfer control to a constant label.</span></span> <span data-ttu-id="0d52e-136">この制約が必要になるのは、非 constant ラベルに制御を転送しようとすると望ましくない副作用 (コード内の意図しない場所に制御を転送してしまったり、無限ループを作成してしまったりなど) が生じる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="0d52e-136">This restriction is necessary, since attempting to transfer control to a non-constant label can have undesirable side-effects, such transferring control to an unintended location in code or creating an endless loop.</span></span>

## <a name="case-labels"></a><span data-ttu-id="0d52e-137">case ラベル</span><span class="sxs-lookup"><span data-stu-id="0d52e-137">Case labels</span></span>

<span data-ttu-id="0d52e-138">各 case ラベルで、match 式と比較するためのパターンを指定します (前の例では `caseSwitch` 変数)。</span><span class="sxs-lookup"><span data-stu-id="0d52e-138">Each case label specifies a pattern to compare to the match expression (the `caseSwitch` variable in the previous examples).</span></span> <span data-ttu-id="0d52e-139">一致すると、**最初の**一致 case を含む switch セクションに制御が移ります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-139">If they match, control is transferred to the switch section that contains the **first** matching case label.</span></span> <span data-ttu-id="0d52e-140">match 式と一致する case ラベル パターンがない場合は、`default` case ラベルがあれば、制御はそのラベルを含むセクションに移ります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-140">If no case label pattern matches the match expression, control is transferred to the section with the `default` case label, if there's one.</span></span> <span data-ttu-id="0d52e-141">`default` case がない場合は、どの switch セクションのステートメントも実行されず、制御は `switch` ステートメント外に移ります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-141">If there's no `default` case, no statements in any switch section are executed, and control is transferred outside the `switch` statement.</span></span>

<span data-ttu-id="0d52e-142">`switch` ステートメントとパターン マッチングの詳細については、「[`switch` ステートメントによるパターン マッチング](#pattern-matching-with-the-switch-statement)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d52e-142">For information on the `switch` statement and pattern matching, see the [Pattern matching with the `switch` statement](#pattern-matching-with-the-switch-statement) section.</span></span>

<span data-ttu-id="0d52e-143">C# 6 でサポートされるのは定数パターンのみで、定数値の繰り返しは許可されません。このため、case ラベルでは相互に排他的な値が定義され、match 式と一致するのは 1 つのパターンだけです。</span><span class="sxs-lookup"><span data-stu-id="0d52e-143">Because C# 6 supports only the constant pattern and doesn't allow the repetition of constant values, case labels define mutually exclusive values, and only one pattern can match the match expression.</span></span> <span data-ttu-id="0d52e-144">そのため、`case` ステートメントが表示される順序は重要ではありません。</span><span class="sxs-lookup"><span data-stu-id="0d52e-144">As a result, the order in which `case` statements appear is unimportant.</span></span>

<span data-ttu-id="0d52e-145">一方、C# 7.0 では他のパターンがサポートされているため、case ラベルで定義する値が相互に排他的である必要はなく、match 式と一致するパターンが複数存在する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-145">In C# 7.0, however, because other patterns are supported, case labels need not define mutually exclusive values, and multiple patterns can match the match expression.</span></span> <span data-ttu-id="0d52e-146">一致するパターンを含む最初の switch セクションのステートメントのみが実行されるので、ここでは、`case` ステートメントが表示される順序が重要になってきます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-146">Because only the statements in the first switch section that contains the matching pattern are executed, the order in which `case` statements appear is now important.</span></span> <span data-ttu-id="0d52e-147">C# によって switch セクションが検出され、その switch セクションの case ステートメントが前のステートメントと同じだったり、そのステートメントのサブセットだったりすると、コンパイラ エラー CS8120 "switch case は既に以前のケースで処理されています" が生成されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-147">If C# detects a switch section whose case statement or statements are equivalent to or are subsets of previous statements, it generates a compiler error, CS8120, "The switch case has already been handled by a previous case."</span></span>

<span data-ttu-id="0d52e-148">次の例は、相互に排他的でない各種パターンを使用する `switch` ステートメントを示しています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-148">The following example illustrates a `switch` statement that uses a variety of non-mutually exclusive patterns.</span></span> <span data-ttu-id="0d52e-149">`case 0:` switch セクションを移動し、そのセクションが `switch` ステートメントの最初のセクションでなくなると、C# によってコンパイラ エラーが生成されます。値がゼロの整数は、整数すべてのサブセットであるためです。これは、`case int val` ステートメントで定義されているパターンです。</span><span class="sxs-lookup"><span data-stu-id="0d52e-149">If you move the `case 0:` switch section so that it's no longer the first section in the `switch` statement, C# generates a compiler error because an integer whose value is zero is a subset of all integers, which is the pattern defined by the `case int val` statement.</span></span>

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

<span data-ttu-id="0d52e-150">この問題を修正し、コンパイラの警告が表示されないようにするには、次の 2 つのいずれかの方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-150">You can correct this issue and eliminate the compiler warning in one of two ways:</span></span>

- <span data-ttu-id="0d52e-151">switch セクションの順序を変更する。</span><span class="sxs-lookup"><span data-stu-id="0d52e-151">By changing the order of the switch sections.</span></span>

- <span data-ttu-id="0d52e-152">`case` ラベルで [when 句](#the-case-statement-and-the-when-clause) を使用する。</span><span class="sxs-lookup"><span data-stu-id="0d52e-152">By using a [when clause](#the-case-statement-and-the-when-clause) in the `case` label.</span></span>

## <a name="the-default-case"></a><span data-ttu-id="0d52e-153">`default` case</span><span class="sxs-lookup"><span data-stu-id="0d52e-153">The `default` case</span></span>

<span data-ttu-id="0d52e-154">`default` case では、match 式がどの `case` ラベルとも一致しない場合に実行する switch セクションを指定します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-154">The `default` case specifies the switch section to execute if the match expression doesn't match any other `case` label.</span></span> <span data-ttu-id="0d52e-155">`default` case を指定しない場合、match 式がどの `case` ラベルとも一致しないと、プログラム フローが `switch` ステートメントにフォール スルーします。</span><span class="sxs-lookup"><span data-stu-id="0d52e-155">If a `default` case is not present and the match expression doesn't match any other `case` label, program flow falls through the `switch` statement.</span></span>

<span data-ttu-id="0d52e-156">`default` case は、`switch` ステートメントで任意の順序で指定できます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-156">The `default` case can appear in any order in the `switch` statement.</span></span> <span data-ttu-id="0d52e-157">この case は、ソース コード内での順序に関係なく、すべての `case` ラベルが評価された後、最後に評価されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-157">Regardless of its order in the source code, it's always evaluated last, after all `case` labels have been evaluated.</span></span>

## <a name="pattern-matching-with-the-switch-statement"></a><span data-ttu-id="0d52e-158">`switch` ステートメントによるパターン マッチング</span><span class="sxs-lookup"><span data-stu-id="0d52e-158">Pattern matching with the `switch` statement</span></span>

<span data-ttu-id="0d52e-159">各 `case` ステートメントで定義されたパターンが match 式と一致した場合に、switch セクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-159">Each `case` statement defines a pattern that, if it matches the match expression, causes its  containing switch section to be executed.</span></span> <span data-ttu-id="0d52e-160">定数パターンは、すべてのバージョンの C# でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-160">All versions of C# support the constant pattern.</span></span> <span data-ttu-id="0d52e-161">それ以外のパターンは、C# 7.0 以降でサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-161">The remaining patterns are supported beginning with C# 7.0.</span></span>

### <a name="constant-pattern"></a><span data-ttu-id="0d52e-162">定数パターン</span><span class="sxs-lookup"><span data-stu-id="0d52e-162">Constant pattern</span></span>

<span data-ttu-id="0d52e-163">定数パターンでは、match 式が、指定された定数と等しいかどうかがテストされます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-163">The constant pattern tests whether the match expression equals a specified constant.</span></span> <span data-ttu-id="0d52e-164">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0d52e-164">Its syntax is:</span></span>

```csharp
   case constant:
```

<span data-ttu-id="0d52e-165">ここで *constant* はテスト対象の値です。</span><span class="sxs-lookup"><span data-stu-id="0d52e-165">where *constant* is the value to test for.</span></span> <span data-ttu-id="0d52e-166">*constant* には、次のいずれかの定数式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-166">*constant* can be any of the following constant expressions:</span></span>

- <span data-ttu-id="0d52e-167">[bool](../builtin-types/bool.md) リテラル。`true` または `false`。</span><span class="sxs-lookup"><span data-stu-id="0d52e-167">A [bool](../builtin-types/bool.md) literal: either `true` or `false`.</span></span>
- <span data-ttu-id="0d52e-168">任意の [integral](../builtin-types/integral-numeric-types.md) 定数。`int`、`long`、`byte` など。</span><span class="sxs-lookup"><span data-stu-id="0d52e-168">Any [integral](../builtin-types/integral-numeric-types.md) constant, such as an `int`, a `long`, or a `byte`.</span></span>
- <span data-ttu-id="0d52e-169">宣言された `const` 変数の名前。</span><span class="sxs-lookup"><span data-stu-id="0d52e-169">The name of a declared `const` variable.</span></span>
- <span data-ttu-id="0d52e-170">列挙定数。</span><span class="sxs-lookup"><span data-stu-id="0d52e-170">An enumeration constant.</span></span>
- <span data-ttu-id="0d52e-171">[char](../builtin-types/char.md) リテラル。</span><span class="sxs-lookup"><span data-stu-id="0d52e-171">A [char](../builtin-types/char.md) literal.</span></span>
- <span data-ttu-id="0d52e-172">[string](../builtin-types/reference-types.md) リテラル。</span><span class="sxs-lookup"><span data-stu-id="0d52e-172">A [string](../builtin-types/reference-types.md) literal.</span></span>

<span data-ttu-id="0d52e-173">定数式は以下のように評価されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-173">The constant expression is evaluated as follows:</span></span>

- <span data-ttu-id="0d52e-174">*expr* と *constant* が整数型の場合、式から `true` が返されるかどうか (つまり、`expr == constant` であるかどうか) が C# の等値演算子によって判定されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-174">If *expr* and *constant* are integral types, the C# equality operator determines whether the expression returns `true` (that is, whether `expr == constant`).</span></span>

- <span data-ttu-id="0d52e-175">それ以外の場合、式の値は静的 [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) メソッドの呼び出しによって判定されます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-175">Otherwise, the value of the expression is determined by a call to the static [Object.Equals(expr, constant)](xref:System.Object.Equals(System.Object,System.Object)) method.</span></span>

<span data-ttu-id="0d52e-176">次の例では、定数パターンを使用して、特定の日付が、週末か、週の開始日または最終日か、週の途中かを判断します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-176">The following example uses the constant pattern to determine whether a particular date is a weekend, the first day of the work week, the last day of the work week, or the middle of the work week.</span></span> <span data-ttu-id="0d52e-177">つまり、現在の日付の <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> プロパティを、<xref:System.DayOfWeek> 列挙のメンバーと照合します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-177">It evaluates the <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> property of the current day against the members of the <xref:System.DayOfWeek> enumeration.</span></span>

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

<span data-ttu-id="0d52e-178">次の例では、定数パターンを使用して、自動コーヒー メーカーをシミュレートするコンソール アプリケーションのユーザー入力を処理します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-178">The following example uses the constant pattern to handle user input in a console application that simulates an automatic coffee machine.</span></span>

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a><span data-ttu-id="0d52e-179">型パターン</span><span class="sxs-lookup"><span data-stu-id="0d52e-179">Type pattern</span></span>

<span data-ttu-id="0d52e-180">型パターンを使用すると、型の評価と変換を簡潔に記述できます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-180">The type pattern enables concise type evaluation and conversion.</span></span> <span data-ttu-id="0d52e-181">`switch` ステートメントと共に使用してパターン マッチングを実行すると、指定された型に式を変換できるかどうかがテストされ、変換できる場合は、その型の変数にキャストされます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-181">When used with the `switch` statement to perform pattern matching, it tests whether an expression can be converted to a specified type and, if it can be, casts it to a variable of that type.</span></span> <span data-ttu-id="0d52e-182">構文は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0d52e-182">Its syntax is:</span></span>

```csharp
   case type varname
```

<span data-ttu-id="0d52e-183">ここで *type* は、*expr* の結果が変換される型の名前、*varname* は、一致した場合に *expr* の結果が変換されるオブジェクトを表しています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-183">where *type* is the name of the type to which the result of *expr* is to be converted, and *varname* is the object to which the result of *expr* is converted if the match succeeds.</span></span> <span data-ttu-id="0d52e-184">コンパイル時の型 *expr* は、C# 7.1 以降では、ジェネリック型パラメーターにすることができます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-184">The compile-time type of *expr* may be a generic type parameter, starting with C# 7.1.</span></span>

<span data-ttu-id="0d52e-185">以下のいずれかの条件が true である場合に `case` 式は `true` となります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-185">The `case` expression is `true` if any of the following is true:</span></span>

- <span data-ttu-id="0d52e-186">*expr* が *type* と同じ型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="0d52e-186">*expr* is an instance of the same type as *type*.</span></span>

- <span data-ttu-id="0d52e-187">*expr* が *type* から派生した型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="0d52e-187">*expr* is an instance of a type that derives from *type*.</span></span> <span data-ttu-id="0d52e-188">つまり、*expr* の結果を *type* のインスタンスにアップキャストできる。</span><span class="sxs-lookup"><span data-stu-id="0d52e-188">In other words, the result of *expr* can be upcast to an instance of *type*.</span></span>

- <span data-ttu-id="0d52e-189">*expr* のコンパイル時の型が *type* の基底クラスであり、*expr* の実行時の型が *type* または *type* から派生した型である。</span><span class="sxs-lookup"><span data-stu-id="0d52e-189">*expr* has a compile-time type that is a base class of *type*, and *expr* has a runtime type that is *type* or is derived from *type*.</span></span> <span data-ttu-id="0d52e-190">変数の "*コンパイル時の型*" とは、その変数の型宣言で定義されている型です。</span><span class="sxs-lookup"><span data-stu-id="0d52e-190">The *compile-time type* of a variable is the variable's type as defined in its type declaration.</span></span> <span data-ttu-id="0d52e-191">変数の "*実行時の型*" とは、その変数に代入されているインスタンスの型です。</span><span class="sxs-lookup"><span data-stu-id="0d52e-191">The *runtime type* of a variable is the type of the instance that is assigned to that variable.</span></span>

- <span data-ttu-id="0d52e-192">*expr* が、*type* インターフェイスを実装する型のインスタンスである。</span><span class="sxs-lookup"><span data-stu-id="0d52e-192">*expr* is an instance of a type that implements the *type* interface.</span></span>

<span data-ttu-id="0d52e-193">case 式が true の場合は、*varname* が確実に割り当てられ、switch セクションにのみローカル スコープが含まれます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-193">If the case expression is true, *varname* is definitely assigned and has local scope within the switch section only.</span></span>

<span data-ttu-id="0d52e-194">`null` は型と一致しないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="0d52e-194">Note that `null` doesn't match a type.</span></span> <span data-ttu-id="0d52e-195">`null` を一致させるには、次の `case` ラベルを使用します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-195">To match a `null`, you use the following `case` label:</span></span>

```csharp
case null:
```

<span data-ttu-id="0d52e-196">次の例では、型パターンを使用して、さまざまな種類のコレクション型に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="0d52e-196">The following example uses the type pattern to provide information about various kinds of collection types.</span></span>

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

<span data-ttu-id="0d52e-197">次のコードに示すように、`object` の代わりに、コレクションの型を型パラメーターとして使用して、ジェネリック メソッドを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-197">Instead of `object`, you could make a generic method, using the type of the collection as the type parameter, as shown in the following code:</span></span>

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

<span data-ttu-id="0d52e-198">ジェネリック バージョンは、2 つの点で最初のサンプルと異なります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-198">The generic version is different than the first sample in two ways.</span></span> <span data-ttu-id="0d52e-199">まず、`null` の case を使用できません。</span><span class="sxs-lookup"><span data-stu-id="0d52e-199">First, you can't use the `null` case.</span></span> <span data-ttu-id="0d52e-200">コンパイラは任意の型 `T` を `object` 以外の型に変換できないため、定数の case は使用できません。</span><span class="sxs-lookup"><span data-stu-id="0d52e-200">You can't use any constant case because the compiler can't convert any arbitrary type `T` to any type other than `object`.</span></span> <span data-ttu-id="0d52e-201">`default` の case だったものは、null 以外の `object` をテストするようになりました。</span><span class="sxs-lookup"><span data-stu-id="0d52e-201">What had been the `default` case now tests for a non-null `object`.</span></span> <span data-ttu-id="0d52e-202">つまり、`default` の case は `null` のみをテストします。</span><span class="sxs-lookup"><span data-stu-id="0d52e-202">That means the `default` case tests only for `null`.</span></span>

<span data-ttu-id="0d52e-203">パターン マッチングを使用しない場合、このコードは次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-203">Without pattern matching, this code might be written as follows.</span></span> <span data-ttu-id="0d52e-204">型パターン マッチングを使用することにより、変換結果が `null` であるかどうかをテストしたり、キャストを繰り返したりする必要がなくなるため、コードがよりコンパクトで読みやすくなります。</span><span class="sxs-lookup"><span data-stu-id="0d52e-204">The use of type pattern matching produces more compact, readable code by eliminating the need to test whether the result of a conversion is a `null` or to perform repeated casts.</span></span>

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><span data-ttu-id="0d52e-205">`case` ステートメントおよび `when` 句</span><span class="sxs-lookup"><span data-stu-id="0d52e-205">The `case` statement and the `when` clause</span></span>

<span data-ttu-id="0d52e-206">C# 7.0 以降では、case ステートメントは相互に排他的である必要がないため、`when` 句を追加して、case ステートメントを true に評価するために満たされなければならない条件を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-206">Starting with C# 7.0, because case statements need not be mutually exclusive, you can add a `when` clause to specify an additional condition that must be satisfied for the case statement to evaluate to true.</span></span> <span data-ttu-id="0d52e-207">`when` 句には、ブール値を返す任意の式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="0d52e-207">The `when` clause can be any expression that returns a Boolean value.</span></span>

<span data-ttu-id="0d52e-208">次の例では、`Shape` 基底クラス、`Shape` から派生する `Rectangle` クラス、および `Rectangle` から派生する `Square` クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-208">The following example defines a base `Shape` class, a `Rectangle` class that derives from `Shape`, and a `Square` class that derives from `Rectangle`.</span></span> <span data-ttu-id="0d52e-209">ここでは `when` 句を使用して、同じ長さと幅が割り当てられている `Rectangle` オブジェクトが、`Square` オブジェクトとしてインスタンス化されていなくても、`ShowShapeInfo` によって確実に `Square` として処理されるようにしています。</span><span class="sxs-lookup"><span data-stu-id="0d52e-209">It uses the `when` clause to ensure that the `ShowShapeInfo` treats a `Rectangle` object that has been assigned equal lengths and widths as a `Square` even if it hasn't been instantiated as a `Square` object.</span></span> <span data-ttu-id="0d52e-210">このメソッドは、`null` オブジェクトの情報や、面積がゼロの図形の情報を表示しようとしません。</span><span class="sxs-lookup"><span data-stu-id="0d52e-210">The method doesn't attempt to display information either about an object that is `null` or a shape whose area is zero.</span></span>

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

<span data-ttu-id="0d52e-211">この例で、`Shape` オブジェクトが `null` かどうかをテストしようとする `when` 句は実行されません。</span><span class="sxs-lookup"><span data-stu-id="0d52e-211">Note that the `when` clause in the example that attempts to test whether a `Shape` object is `null` doesn't execute.</span></span> <span data-ttu-id="0d52e-212">`null` をテストするための正しい型パターンは `case null:` です。</span><span class="sxs-lookup"><span data-stu-id="0d52e-212">The correct type pattern to test for a `null` is `case null:`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0d52e-213">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="0d52e-213">C# language specification</span></span>

<span data-ttu-id="0d52e-214">詳細については、[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)に関するページの「[switch ステートメント](~/_csharplang/spec/statements.md#the-switch-statement)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d52e-214">For more information, see [The switch statement](~/_csharplang/spec/statements.md#the-switch-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="0d52e-215">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="0d52e-215">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d52e-216">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d52e-216">See also</span></span>

- [<span data-ttu-id="0d52e-217">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="0d52e-217">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d52e-218">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="0d52e-218">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0d52e-219">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="0d52e-219">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0d52e-220">if-else</span><span class="sxs-lookup"><span data-stu-id="0d52e-220">if-else</span></span>](if-else.md)
- [<span data-ttu-id="0d52e-221">パターン一致</span><span class="sxs-lookup"><span data-stu-id="0d52e-221">Pattern Matching</span></span>](../../pattern-matching.md)
