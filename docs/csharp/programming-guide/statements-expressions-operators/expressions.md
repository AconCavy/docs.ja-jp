---
title: 式 - C# プログラミング ガイド
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 4bbee8f15c2591e8b172df9a6759449d48697804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699094"
---
# <a name="expressions-c-programming-guide"></a><span data-ttu-id="9a8a3-102">式 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="9a8a3-102">Expressions (C# Programming Guide)</span></span>

<span data-ttu-id="9a8a3-103">"*式*" とは、1 つの値、オブジェクト、メソッド、または名前空間に評価できる、1 つ以上のオペランドと 0 個以上の[演算子](../../language-reference/operators/index.md)のシーケンスです。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-103">An *expression* is a sequence of one or more operands and zero or more [operators](../../language-reference/operators/index.md) that can be evaluated to a single value, object, method, or namespace.</span></span> <span data-ttu-id="9a8a3-104">式には、リテラル値、メソッドの呼び出し、演算子とそのオペランド、または*簡易名*を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-104">Expressions can consist of a literal value, a method invocation, an operator and its operands, or a *simple name*.</span></span> <span data-ttu-id="9a8a3-105">単純な名前には、変数、型メンバー、メソッド パラメーター、名前空間、または型の名前を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-105">Simple names can be the name of a variable, type member, method parameter, namespace or type.</span></span>  
  
 <span data-ttu-id="9a8a3-106">式では、他の式をパラメーターとして使用する演算子、またはパラメーターが他のメソッド呼び出しであるメソッド呼び出しを使用できます。そのため、式には単純なものもあれば、非常に複雑なものもあります。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-106">Expressions can use operators that in turn use other expressions as parameters, or method calls whose parameters are in turn other method calls, so expressions can range from simple to very complex.</span></span> <span data-ttu-id="9a8a3-107">次に式の例を 2 つ示します。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-107">Following are two examples of expressions:</span></span>  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a><span data-ttu-id="9a8a3-108">式の値</span><span class="sxs-lookup"><span data-stu-id="9a8a3-108">Expression values</span></span>

 <span data-ttu-id="9a8a3-109">ステートメントやメソッド パラメーターなど、式が使用されるコンテキストの大部分では、式はなんらかの値に評価されることが期待されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-109">In most of the contexts in which expressions are used, for example in statements or method parameters, the expression is expected to evaluate to some value.</span></span> <span data-ttu-id="9a8a3-110">たとえば、x と y が整数である場合、式 `x + y` は数値に評価されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-110">If x and y are integers, the expression `x + y` evaluates to a numeric value.</span></span> <span data-ttu-id="9a8a3-111">式 `new MyClass()` は、`MyClass` クラスの新しいインスタンスへの参照に評価されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-111">The expression `new MyClass()` evaluates to a reference to a new instance of a `MyClass` class.</span></span> <span data-ttu-id="9a8a3-112">式 `myClass.ToString()` は、メソッドの戻り値の型である文字列に評価されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-112">The expression `myClass.ToString()` evaluates to a string because that is the return type of the method.</span></span> <span data-ttu-id="9a8a3-113">ただし、名前空間名については、分類上は式として扱われますが、値には評価されないため、式の最終結果になることはありません。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-113">However, although a namespace name is classified as an expression, it does not evaluate to a value and therefore can never be the final result of any expression.</span></span> <span data-ttu-id="9a8a3-114">名前空間名は、メソッド パラメーターに渡すことはできません。また、新しい式で使用したり、変数に割り当てたりすることもできません。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-114">You cannot pass a namespace name to a method parameter, or use it in a new expression, or assign it to a variable.</span></span> <span data-ttu-id="9a8a3-115">名前空間名は、より大きい式の部分式としてのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-115">You can only use it as a sub-expression in a larger expression.</span></span> <span data-ttu-id="9a8a3-116">同じことが、型 (<xref:System.Type?displayProperty=nameWithType> オブジェクトとは異なります)、メソッド グループ名 (特定のメソッドとは異なります)、およびイベント アクセサーである [add](../../language-reference/keywords/add.md) と [remove](../../language-reference/keywords/remove.md) にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-116">The same is true for types (as distinct from <xref:System.Type?displayProperty=nameWithType> objects), method group names (as distinct from specific methods), and event [add](../../language-reference/keywords/add.md) and [remove](../../language-reference/keywords/remove.md) accessors.</span></span>  
  
 <span data-ttu-id="9a8a3-117">すべての値には、型が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-117">Every value has an associated type.</span></span> <span data-ttu-id="9a8a3-118">たとえば、x と y が両方とも型 `int` の変数である場合、式 `x + y` の値も `int` として型指定されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-118">For example, if x and y are both variables of type `int`, the value of the expression `x + y` is also typed as `int`.</span></span> <span data-ttu-id="9a8a3-119">異なる型の変数に値が割り当てられた場合や、x と y の型が異なる場合は、型変換の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-119">If the value is assigned to a variable of a different type, or if x and y are different types, the rules of type conversion are applied.</span></span> <span data-ttu-id="9a8a3-120">このような変換の動作方法の詳細については、「[キャストと型変換](../types/casting-and-type-conversions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-120">For more information about how such conversions work, see [Casting and Type Conversions](../types/casting-and-type-conversions.md).</span></span>  
  
## <a name="overflows"></a><span data-ttu-id="9a8a3-121">オーバーフロー</span><span class="sxs-lookup"><span data-stu-id="9a8a3-121">Overflows</span></span>

 <span data-ttu-id="9a8a3-122">値の型の最大値よりも値が大きくなると、数式でオーバーフローが発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-122">Numeric expressions may cause overflows if the value is larger than the maximum value of the value's type.</span></span> <span data-ttu-id="9a8a3-123">詳細については、[Checked と Unchecked](../../language-reference/keywords/checked-and-unchecked.md) に関する記事と[組み込みの数値変換](../../language-reference/builtin-types/numeric-conversions.md)に関する記事の「[明示的な数値変換](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-123">For more information, see [Checked and Unchecked](../../language-reference/keywords/checked-and-unchecked.md) and the [Explicit numeric conversions](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) section of the [Built-in numeric conversions](../../language-reference/builtin-types/numeric-conversions.md) article.</span></span>
  
## <a name="operator-precedence-and-associativity"></a><span data-ttu-id="9a8a3-124">演算子の優先順位と結合規則</span><span class="sxs-lookup"><span data-stu-id="9a8a3-124">Operator precedence and associativity</span></span>

 <span data-ttu-id="9a8a3-125">式の評価方法は、結合規則と演算子の優先順位によって決まります。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-125">The manner in which an expression is evaluated is governed by the rules of associativity and operator precedence.</span></span> <span data-ttu-id="9a8a3-126">詳細については、「 [オペレーター](../../language-reference/operators/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-126">For more information, see [Operators](../../language-reference/operators/index.md).</span></span>  
  
 <span data-ttu-id="9a8a3-127">代入式とメソッドの呼び出し式を除き、ほとんどの式はステートメントに埋め込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-127">Most expressions, except assignment expressions and method invocation expressions, must be embedded in a statement.</span></span> <span data-ttu-id="9a8a3-128">詳細については、「[ステートメント](./statements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-128">For more information, see [Statements](./statements.md).</span></span>  
  
## <a name="literals-and-simple-names"></a><span data-ttu-id="9a8a3-129">リテラルと簡易名</span><span class="sxs-lookup"><span data-stu-id="9a8a3-129">Literals and simple names</span></span>

 <span data-ttu-id="9a8a3-130">式の中で最も単純なものはリテラルと簡易名です。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-130">The two simplest types of expressions are literals and simple names.</span></span> <span data-ttu-id="9a8a3-131">リテラルは、名前を持たない定数値です。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-131">A literal is a constant value that has no name.</span></span> <span data-ttu-id="9a8a3-132">たとえば、次のコード例の `5` と `"Hello World"` は共にリテラル値です。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-132">For example, in the following code example, both `5` and `"Hello World"` are literal values:</span></span>  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 <span data-ttu-id="9a8a3-133">リテラルの詳細については、「[型](/dotnet/csharp/language-reference/keywords)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-133">For more information on literals, see [Types](/dotnet/csharp/language-reference/keywords).</span></span>  
  
 <span data-ttu-id="9a8a3-134">前の例の `i` と `s` は、どちらもローカル変数を識別する簡易名です。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-134">In the preceding example, both `i` and `s` are simple names that identify local variables.</span></span> <span data-ttu-id="9a8a3-135">これらの変数を式で使用すると、変数名は、変数のメモリ位置に現在格納されている値に評価されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-135">When those variables are used in an expression, the variable name evaluates to the value that is currently stored in the variable's location in memory.</span></span> <span data-ttu-id="9a8a3-136">以下の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-136">This is shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a><span data-ttu-id="9a8a3-137">Invocation 式</span><span class="sxs-lookup"><span data-stu-id="9a8a3-137">Invocation expressions</span></span>

 <span data-ttu-id="9a8a3-138">次のコード例では、`DoWork` の呼び出しが Invocation 式です。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-138">In the following code example, the call to `DoWork` is an invocation expression.</span></span>  
  
```csharp
DoWork();  
```  
  
 <span data-ttu-id="9a8a3-139">メソッドの呼び出しでは、メソッドの名前 (上の例のような名前、または別の式の結果としての名前) を使用し、その後にかっことメソッド パラメーターを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-139">A method invocation requires the name of the method, either as a name as in the previous example, or as the result of another expression, followed by parenthesis and any method parameters.</span></span> <span data-ttu-id="9a8a3-140">詳細については、「[メソッド](../classes-and-structs/methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-140">For more information, see [Methods](../classes-and-structs/methods.md).</span></span> <span data-ttu-id="9a8a3-141">デリゲートの呼び出しでは、デリゲートの名前とメソッド パラメーターをかっこで囲んで使用します。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-141">A delegate invocation uses the name of a delegate and method parameters in parenthesis.</span></span> <span data-ttu-id="9a8a3-142">詳細については、「 [デリゲート](../delegates/index.md)で定義されているインターフェイスのプライベート C++ 固有の実装です。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-142">For more information, see [Delegates](../delegates/index.md).</span></span> <span data-ttu-id="9a8a3-143">メソッドの呼び出しとデリゲートの呼び出しは、メソッドが値を返す場合、メソッドの戻り値に評価されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-143">Method invocations and delegate invocations evaluate to the return value of the method, if the method returns a value.</span></span> <span data-ttu-id="9a8a3-144">void を返すメソッドは、式の値の代わりに使用できません。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-144">Methods that return void cannot be used in place of a value in an expression.</span></span>  

## <a name="query-expressions"></a><span data-ttu-id="9a8a3-145">クエリ式</span><span class="sxs-lookup"><span data-stu-id="9a8a3-145">Query expressions</span></span>

 <span data-ttu-id="9a8a3-146">一般的な式の規則と同じ規則がクエリ式に適用されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-146">The same rules for expressions in general apply to query expressions.</span></span> <span data-ttu-id="9a8a3-147">詳細については、[LINQ](../../linq/index.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-147">For more information, see [LINQ](../../linq/index.md).</span></span>  
  
## <a name="lambda-expressions"></a><span data-ttu-id="9a8a3-148">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="9a8a3-148">Lambda expressions</span></span>

 <span data-ttu-id="9a8a3-149">ラムダ式は、名前がないが入力パラメーターおよび複数のステートメントを持つことができる "インライン メソッド" を表します。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-149">Lambda expressions represent "inline methods" that have no name but can have input parameters and multiple statements.</span></span> <span data-ttu-id="9a8a3-150">LINQ では、メソッドに引数を渡すために広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-150">They are used extensively in LINQ to pass arguments to methods.</span></span> <span data-ttu-id="9a8a3-151">ラムダ式は、使用されるコンテキストに応じて、デリゲートまたは式ツリーにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-151">Lambda expressions are compiled to either delegates or expression trees depending on the context in which they are used.</span></span> <span data-ttu-id="9a8a3-152">詳しくは、「[ラムダ式](lambda-expressions.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-152">For more information, see [Lambda Expressions](lambda-expressions.md).</span></span>  
  
## <a name="expression-trees"></a><span data-ttu-id="9a8a3-153">式ツリー</span><span class="sxs-lookup"><span data-stu-id="9a8a3-153">Expression trees</span></span>

<span data-ttu-id="9a8a3-154">式ツリーを使用すると、式をデータ構造体として表すことができます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-154">Expression trees enable expressions to be represented as data structures.</span></span> <span data-ttu-id="9a8a3-155">クエリ式を、SQL データベースなどの他のコンテキストで意味を持つコードに変換するために、LINQ プロバイダーにより広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-155">They are used extensively by LINQ providers to translate query expressions into code that is meaningful in some other context, such as a SQL database.</span></span> <span data-ttu-id="9a8a3-156">詳しくは、「[式ツリー (C#)](../concepts/expression-trees/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-156">For more information, see [Expression Trees (C#)](../concepts/expression-trees/index.md).</span></span>
  
## <a name="expression-body-definitions"></a><span data-ttu-id="9a8a3-157">式本体の定義</span><span class="sxs-lookup"><span data-stu-id="9a8a3-157">Expression body definitions</span></span>

<span data-ttu-id="9a8a3-158">C# は*式形式のメンバー*をサポートしています。式形式のメンバーを使用すると、メソッド、コンストラクター、ファイナライザー、プロパティ、およびインデクサー用に簡潔な式本体の定義を指定できます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-158">C# supports *expression-bodied members*, which allow you to supply a concise expression body definition for methods, constructors, finalizers, properties, and indexers.</span></span> <span data-ttu-id="9a8a3-159">詳細については、「[式形式のメンバー](expression-bodied-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-159">For more information, see [Expression-bodied members](expression-bodied-members.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="9a8a3-160">解説</span><span class="sxs-lookup"><span data-stu-id="9a8a3-160">Remarks</span></span>

 <span data-ttu-id="9a8a3-161">変数、オブジェクト プロパティ、またはオブジェクトのインデクサー アクセスが式から識別されると、その項目の値が式の値として使用されます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-161">Whenever a variable, object property, or object indexer access is identified from an expression, the value of that item is used as the value of the expression.</span></span> <span data-ttu-id="9a8a3-162">C# の式は、式が最終的に必要な型に評価される限り、値やオブジェクトが必要とされる任意の位置に配置できます。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-162">An expression can be placed anywhere in C# where a value or object is required, as long as the expression ultimately evaluates to the required type.</span></span>  

## <a name="c-language-specification"></a><span data-ttu-id="9a8a3-163">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="9a8a3-163">C# language specification</span></span>

<span data-ttu-id="9a8a3-164">詳細については、[C# 言語仕様](~/_csharplang/spec/introduction.md)の「[式](~/_csharplang/spec/expressions.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9a8a3-164">For more information, see the [Expressions](~/_csharplang/spec/expressions.md) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a8a3-165">参照</span><span class="sxs-lookup"><span data-stu-id="9a8a3-165">See also</span></span>

- [<span data-ttu-id="9a8a3-166">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="9a8a3-166">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9a8a3-167">オペレーター</span><span class="sxs-lookup"><span data-stu-id="9a8a3-167">Operators</span></span>](../../language-reference/operators/index.md)
- [<span data-ttu-id="9a8a3-168">メソッド</span><span class="sxs-lookup"><span data-stu-id="9a8a3-168">Methods</span></span>](../classes-and-structs/methods.md)
- [<span data-ttu-id="9a8a3-169">デリゲート</span><span class="sxs-lookup"><span data-stu-id="9a8a3-169">Delegates</span></span>](../delegates/index.md)
- [<span data-ttu-id="9a8a3-170">型</span><span class="sxs-lookup"><span data-stu-id="9a8a3-170">Types</span></span>](../types/index.md)
- [<span data-ttu-id="9a8a3-171">LINQ</span><span class="sxs-lookup"><span data-stu-id="9a8a3-171">LINQ</span></span>](../../linq/index.md)
