---
title: 概念と用語 (関数型変換) (C#)
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 3e2ecc4c2f70700ae92ee36b6f122059b922332e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "70040627"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a><span data-ttu-id="e83ec-102">概念と用語 (関数型変換) (C#)</span><span class="sxs-lookup"><span data-stu-id="e83ec-102">Concepts and Terminology (Functional Transformation) (C#)</span></span>

<span data-ttu-id="e83ec-103">このトピックでは、純粋関数型変換の概念と用語について説明します。</span><span class="sxs-lookup"><span data-stu-id="e83ec-103">This topic introduces the concepts and terminology of pure functional transformations.</span></span> <span data-ttu-id="e83ec-104">データの変換に対して関数型変換の方法を使用すると、多くの場合、従来の命令型のプログラミングよりすばやいプログラミングが可能になります。また、さまざまな表現を使用した、デバッグや保守の容易なコードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-104">The functional transformation approach to transforming data yields code that is often quicker to program, more expressive, and easier to debug and maintain than more traditional, imperative programming.</span></span>

<span data-ttu-id="e83ec-105">このセクションのトピックでは、関数型プログラミングのすべてを説明するのではなく、</span><span class="sxs-lookup"><span data-stu-id="e83ec-105">Note that the topics in this section are not intended to fully explain functional programming.</span></span> <span data-ttu-id="e83ec-106">XML の変換を容易にするいくつかの機能を紹介することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="e83ec-106">Instead, these topics identify some of the functional programming capabilities that make it easier to transform XML from one shape to another.</span></span>

## <a name="what-is-pure-functional-transformation"></a><span data-ttu-id="e83ec-107">純粋関数型変換とは</span><span class="sxs-lookup"><span data-stu-id="e83ec-107">What Is Pure Functional Transformation?</span></span>

<span data-ttu-id="e83ec-108">"*純粋関数型変換*" では、"*純粋関数*" と呼ばれる一連の関数により、一連の構造化データを元の形式から別の形式に変換する方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-108">In *pure functional transformation*, a set of functions, called *pure functions*, define how to transform a set of structured data from its original form into another form.</span></span> <span data-ttu-id="e83ec-109">"純粋" という語は、それらの関数が "*コンポーザブル*" であることを示しています。関数がコンポーザブルであるためには、次の特性を備えている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e83ec-109">The word "pure" indicates that the functions are *composable*, which requires that they are:</span></span>

- <span data-ttu-id="e83ec-110">"*自己完結している*"。このため、プログラムの他の部分との結び付きや相互依存を気にせずに、関数を自由に並べ替えることができます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-110">*Self-contained*, so that they can be freely ordered and rearranged without entanglement or interdependencies with the rest of the program.</span></span> <span data-ttu-id="e83ec-111">純粋変換では、その環境を考慮する必要はなく、また環境に対して影響を与えることもありません。</span><span class="sxs-lookup"><span data-stu-id="e83ec-111">Pure transformations have no knowledge of or effect upon their environment.</span></span> <span data-ttu-id="e83ec-112">つまり、変換で使用される関数には "*副作用*" がありません。</span><span class="sxs-lookup"><span data-stu-id="e83ec-112">That is, the functions used in the transformation have no *side effects*.</span></span>

- <span data-ttu-id="e83ec-113">"*ステートレス*"。このため、同じ関数または関数のセットを同じ入力に対して実行すると、常に同じ出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-113">*Stateless*, so that executing the same function or specific set of functions on the same input will always result in the same output.</span></span> <span data-ttu-id="e83ec-114">純粋変換には、以前に使用されたときの情報は保持されません。</span><span class="sxs-lookup"><span data-stu-id="e83ec-114">Pure transformations have no memory of their prior use.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e83ec-115">このチュートリアルの以降では、"純粋関数" という用語を、特定の言語機能ではなくプログラミング方法を指す広い意味で使用します。</span><span class="sxs-lookup"><span data-stu-id="e83ec-115">In the rest of this tutorial, the term "pure function" is used in a general sense to indicate a programming approach, and not a specific language feature.</span></span>
>
> <span data-ttu-id="e83ec-116">C# では純粋関数をメソッドとして実装する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-116">Note that pure functions must be implemented as methods in C#.</span></span>
>
> <span data-ttu-id="e83ec-117">また、純粋関数を C++ の純粋仮想メソッドと混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-117">Also, you should not confuse pure functions with pure virtual methods in C++.</span></span> <span data-ttu-id="e83ec-118">純粋仮想メソッドとは、そのメソッドを含むクラスが抽象クラスであり、メソッドの本体が提供されないことを指します。</span><span class="sxs-lookup"><span data-stu-id="e83ec-118">The latter indicates that the containing class is abstract and that no method body is supplied.</span></span>

### <a name="functional-programming"></a><span data-ttu-id="e83ec-119">関数型プログラミング</span><span class="sxs-lookup"><span data-stu-id="e83ec-119">Functional Programming</span></span>

<span data-ttu-id="e83ec-120">"*関数型プログラミング*" とは、純粋関数型変換を直接サポートするプログラミング方法です。</span><span class="sxs-lookup"><span data-stu-id="e83ec-120">*Functional programming* is a programming approach that directly supports pure functional transformation.</span></span>

<span data-ttu-id="e83ec-121">これまで、ML、Scheme、Haskell、F# などの汎用関数型プログラミング言語に対する関心は、主に学術的な分野に限られていました。</span><span class="sxs-lookup"><span data-stu-id="e83ec-121">Historically, general-purpose functional programming languages, such as ML, Scheme, Haskell, and F#, have been primarily of interest to the academic community.</span></span> <span data-ttu-id="e83ec-122">C# では常に純粋関数型変換を記述することが可能でしたが、その難しさから、ほとんどのプログラマにとっては魅力的な選択肢になりませんでした。</span><span class="sxs-lookup"><span data-stu-id="e83ec-122">Although it has always been possible to write pure functional transformations in C#, the difficulty of doing so has not made it an attractive option to most programmers.</span></span> <span data-ttu-id="e83ec-123">しかし、C# の最近のバージョンでは、ラムダ式や型の推定などの新しい言語構成要素により、関数型プログラミングがはるかに簡単で生産性の高いものとなっています。</span><span class="sxs-lookup"><span data-stu-id="e83ec-123">In recent versions of C#, however, new language constructs such as lambda expressions and type inference make it functional programming much easier and more productive.</span></span>

<span data-ttu-id="e83ec-124">関数型プログラミングの詳細については、「[関数型プログラミングと命令型プログラミング (C#)](./functional-programming-vs-imperative-programming.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-124">For more information about functional programming, see [Functional Programming vs. Imperative Programming (C#)](./functional-programming-vs-imperative-programming.md).</span></span>

#### <a name="domain-specific-fp-languages"></a><span data-ttu-id="e83ec-125">特定領域の FP 言語</span><span class="sxs-lookup"><span data-stu-id="e83ec-125">Domain-Specific FP Languages</span></span>

<span data-ttu-id="e83ec-126">広く採用されるに至らなかった汎用関数型プログラミング言語に比べると、特定領域の関数型プログラミング言語は成功していると言えます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-126">Although general functional programming languages have not been widely adopted, specific domain-specific functional programming languages have had better success.</span></span> <span data-ttu-id="e83ec-127">たとえば、カスケード スタイル シート (CSS) は多くの Web ページのルック アンド フィールの決定に利用されていますし、Extensible Stylesheet Language Transformations (XSLT) スタイル シートは XML データ操作に広く利用されています。</span><span class="sxs-lookup"><span data-stu-id="e83ec-127">For example, Cascading Style Sheets (CSS) are used to determine the look and feel of many Web pages, and Extensible Stylesheet Language Transformations (XSLT) style sheets are used extensively in XML data manipulation.</span></span> <span data-ttu-id="e83ec-128">XSLT について詳しくは、「[XSLT 変換](../../../../standard/data/xml/xslt-transformations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-128">For more information about XSLT, see [XSLT Transformations](../../../../standard/data/xml/xslt-transformations.md).</span></span>

## <a name="terminology"></a><span data-ttu-id="e83ec-129">用語</span><span class="sxs-lookup"><span data-stu-id="e83ec-129">Terminology</span></span>

<span data-ttu-id="e83ec-130">次の表に、関数型変換に関連するいくつかの用語の定義を示します。</span><span class="sxs-lookup"><span data-stu-id="e83ec-130">The following table defines some terms related to functional transformations.</span></span>

<span data-ttu-id="e83ec-131">高階 (ファーストクラス) 関数 </span><span class="sxs-lookup"><span data-stu-id="e83ec-131">higher-order (first-class) function </span></span>\
<span data-ttu-id="e83ec-132">プログラム オブジェクトとして扱うことのできる関数です。</span><span class="sxs-lookup"><span data-stu-id="e83ec-132">A function that can be treated as a programmatic object.</span></span> <span data-ttu-id="e83ec-133">たとえば、他の関数に渡したり、他の関数から返したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-133">For example, a higher-order function can be passed to or returned from other functions.</span></span> <span data-ttu-id="e83ec-134">C# では、高階関数をサポートする言語機能として、デリゲートやラムダ式があります。</span><span class="sxs-lookup"><span data-stu-id="e83ec-134">In C#c, delegates and lambda expressions are language features that support higher-order functions.</span></span> <span data-ttu-id="e83ec-135">高階関数を記述するには、デリゲートを受け取る引数を 1 つ以上宣言し、通常はラムダ式を使用して呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e83ec-135">To write a higher-order function, you declare one or more arguments to take delegates, and you often use lambda expressions when calling it.</span></span> <span data-ttu-id="e83ec-136">標準クエリ演算子の多くは高階関数です。</span><span class="sxs-lookup"><span data-stu-id="e83ec-136">Many of the standard query operators are higher-order functions.</span></span>

<span data-ttu-id="e83ec-137">詳細については、「[標準クエリ演算子の概要 (C#)](./standard-query-operators-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-137">For more information, see [Standard Query Operators Overview (C#)](./standard-query-operators-overview.md).</span></span>

<span data-ttu-id="e83ec-138">ラムダ式 </span><span class="sxs-lookup"><span data-stu-id="e83ec-138">lambda expression </span></span>\
<span data-ttu-id="e83ec-139">基本的には、デリゲート型が必要とされる場所で使用できるインラインの匿名関数です。</span><span class="sxs-lookup"><span data-stu-id="e83ec-139">Essentially, an inline anonymous function that can be used wherever a delegate type is expected.</span></span> <span data-ttu-id="e83ec-140">これはラムダ式の簡略化した定義ですが、このチュートリアルの目的には十分です。</span><span class="sxs-lookup"><span data-stu-id="e83ec-140">This is a simplified definition of lambda expressions, but it is adequate for the purposes of this tutorial.</span></span>

<span data-ttu-id="e83ec-141">詳細については、「[ラムダ式](../../statements-expressions-operators/lambda-expressions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-141">For more information about, see [Lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).</span></span>

<span data-ttu-id="e83ec-142">コレクション </span><span class="sxs-lookup"><span data-stu-id="e83ec-142">collection </span></span>\
<span data-ttu-id="e83ec-143">データの構造化されたセットです。コレクション内のデータは同じ型であるのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="e83ec-143">A structured set of data, usually of a uniform type.</span></span> <span data-ttu-id="e83ec-144">コレクションで LINQ との互換性を確保するには、<xref:System.Collections.IEnumerable> インターフェイスか <xref:System.Linq.IQueryable> インターフェイス (または対応するジェネリック インターフェイスである <xref:System.Collections.Generic.IEnumerator%601> か <xref:System.Linq.IQueryable%601>) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e83ec-144">To be compatible with LINQ, a collection must implement the <xref:System.Collections.IEnumerable> interface or the <xref:System.Linq.IQueryable> interface (or one of their generic counterparts, <xref:System.Collections.Generic.IEnumerator%601> or <xref:System.Linq.IQueryable%601>).</span></span>

<span data-ttu-id="e83ec-145">タプル (匿名型) </span><span class="sxs-lookup"><span data-stu-id="e83ec-145">tuple (anonymous types) </span></span>\
<span data-ttu-id="e83ec-146">タプルは数学的概念で、それぞれが特定の型を持つオブジェクトの有限のシーケンスを意味します。</span><span class="sxs-lookup"><span data-stu-id="e83ec-146">A mathematical concept, a tuple is a finite sequence of objects, each of a specific type.</span></span> <span data-ttu-id="e83ec-147">順序付きリストとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-147">A tuple is also known as an ordered list.</span></span> <span data-ttu-id="e83ec-148">匿名型は、この概念の言語実装です。匿名型を使用すると、名前のないクラス型を宣言し、同時にその型のオブジェクトをインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="e83ec-148">Anonymous types are a language implementation of this concept, which enable an unnamed class type to be declared and an object of that type to be instantiated at the same time.</span></span>

<span data-ttu-id="e83ec-149">詳細については、「[匿名型](../../classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-149">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

<span data-ttu-id="e83ec-150">型推論 (暗黙の型指定) </span><span class="sxs-lookup"><span data-stu-id="e83ec-150">type inference (implicit typing) </span></span>\
<span data-ttu-id="e83ec-151">明示的な型宣言がない場合に変数の型を特定するコンパイラの機能です。</span><span class="sxs-lookup"><span data-stu-id="e83ec-151">The ability of a compiler to determine the type of a variable in the absence of an explicit type declaration.</span></span>

<span data-ttu-id="e83ec-152">詳細については、「[暗黙的に型指定されるローカル変数](../../classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-152">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

<span data-ttu-id="e83ec-153">遅延実行とレイジー評価 </span><span class="sxs-lookup"><span data-stu-id="e83ec-153">deferred execution and lazy evaluation </span></span>\
<span data-ttu-id="e83ec-154">解決された値が実際に必要となるまで式の評価を遅らせることを意味します。</span><span class="sxs-lookup"><span data-stu-id="e83ec-154">The delaying of evaluation of an expression until its resolved value is actually required.</span></span> <span data-ttu-id="e83ec-155">遅延実行はコレクションでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e83ec-155">Deferred execution is supported in collections.</span></span>

<span data-ttu-id="e83ec-156">詳細については、「[LINQ クエリの概要 (C#)](./introduction-to-linq-queries.md)」と「[LINQ to XML における遅延実行とレイジー評価 (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e83ec-156">For more information, see [Introduction to LINQ Queries (C#)](./introduction-to-linq-queries.md) and [Deferred Execution and Lazy Evaluation in LINQ to XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).</span></span>

<span data-ttu-id="e83ec-157">これらの言語機能は、このセクション全体にわたってサンプル コードで使用されています。</span><span class="sxs-lookup"><span data-stu-id="e83ec-157">These language features will be used in code samples throughout this section.</span></span>

## <a name="see-also"></a><span data-ttu-id="e83ec-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="e83ec-158">See also</span></span>

- [<span data-ttu-id="e83ec-159">純粋関数型変換の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="e83ec-159">Introduction to Pure Functional Transformations (C#)</span></span>](./introduction-to-pure-functional-transformations.md)
- [<span data-ttu-id="e83ec-160">関数型プログラミングと命令型プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="e83ec-160">Functional Programming vs. Imperative Programming (C#)</span></span>](./functional-programming-vs-imperative-programming.md)
