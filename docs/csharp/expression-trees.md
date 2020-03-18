---
title: 式ツリー
description: .NET Core の式ツリーについて、また、それを利用し、検査、変更、実行が可能な構造体としてコードを表す方法について説明します。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: e1026ef70860da519b688a9d67181b88d03f6f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145840"
---
# <a name="expression-trees"></a><span data-ttu-id="45488-103">式ツリー</span><span class="sxs-lookup"><span data-stu-id="45488-103">Expression Trees</span></span>

<span data-ttu-id="45488-104">LINQ を使ったことがあれば、API セットに `Func` 型が含まれる豊富なライブラリを利用したのではないでしょうか</span><span class="sxs-lookup"><span data-stu-id="45488-104">If you have used LINQ, you have experience with a rich library where the `Func` types are part of the API set.</span></span> <span data-ttu-id="45488-105">(LINQ の知識があまりない場合は、この記事の前に、[LINQ のチュートリアル](linq/index.md)と[ラムダ式](./programming-guide/statements-expressions-operators/lambda-expressions.md)に関する記事を読むことをお勧めします)。*式ツリー*には、関数である引数とのさまざまな相互作用があります。</span><span class="sxs-lookup"><span data-stu-id="45488-105">(If you are not familiar with LINQ, you probably want to read [the LINQ tutorial](linq/index.md) and the article about [lambda expressions](./programming-guide/statements-expressions-operators/lambda-expressions.md) before this one.) *Expression Trees* provide richer interaction with the arguments that are functions.</span></span>

<span data-ttu-id="45488-106">LINQ クエリを作成するときに関数の引数を作成するには、通常、ラムダ式を使用します。</span><span class="sxs-lookup"><span data-stu-id="45488-106">You write function arguments, typically using Lambda Expressions, when you create LINQ queries.</span></span> <span data-ttu-id="45488-107">一般的な LINQ クエリでは、このような関数の引数は、コンパイラで作成されるデリゲートに変換されます。</span><span class="sxs-lookup"><span data-stu-id="45488-107">In a typical LINQ query, those function arguments are transformed into a delegate the compiler creates.</span></span>

<span data-ttu-id="45488-108">さまざまな相互作用を使用するには、*式ツリー*を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="45488-108">When you want to have a richer interaction, you need to use *Expression Trees*.</span></span>
<span data-ttu-id="45488-109">式ツリーは、確認、変更、または実行が可能な構造としてコードを表します。</span><span class="sxs-lookup"><span data-stu-id="45488-109">Expression Trees represent code as a structure that you can examine, modify, or execute.</span></span> <span data-ttu-id="45488-110">このようなツールを使用すると、実行時にコードを操作できるようになります。</span><span class="sxs-lookup"><span data-stu-id="45488-110">These tools give you the power to manipulate code during run time.</span></span> <span data-ttu-id="45488-111">実行中のアルゴリズムを確認するコードや、新しい機能を挿入するコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="45488-111">You can write code that examines running algorithms, or injects new capabilities.</span></span> <span data-ttu-id="45488-112">より高度なシナリオの場合、実行中のアルゴリズムを変更し、別の環境で実行できるように C# 式を別の形式に変換することもできます。</span><span class="sxs-lookup"><span data-stu-id="45488-112">In more advanced scenarios, you can modify running algorithms, and even translate C# expressions into another form for execution in another environment.</span></span>

<span data-ttu-id="45488-113">式ツリーを使用するコードは既に作成してきました。</span><span class="sxs-lookup"><span data-stu-id="45488-113">You've likely already written code that uses Expression Trees.</span></span> <span data-ttu-id="45488-114">Entity Framework の LINQ API では、LINQ クエリ式パターンの引数として式ツリーを使用できます。</span><span class="sxs-lookup"><span data-stu-id="45488-114">Entity Framework's LINQ APIs accept Expression Trees as the arguments for the LINQ Query Expression Pattern.</span></span>
<span data-ttu-id="45488-115">そのため、[Entity Framework](/ef/) では、C# で作成したクエリをデータベース エンジンで実行される SQL に変換することができます。</span><span class="sxs-lookup"><span data-stu-id="45488-115">That enables [Entity Framework](/ef/) to translate the query you wrote in C# into SQL that executes in the database engine.</span></span> <span data-ttu-id="45488-116">もう 1 つの例として [Moq](https://github.com/Moq/moq) があります。Moq は、.NET でよく使われるモック作成フレームワークです。</span><span class="sxs-lookup"><span data-stu-id="45488-116">Another example is [Moq](https://github.com/Moq/moq), which is a popular mocking framework for .NET.</span></span>

<span data-ttu-id="45488-117">以降、このチュートリアルでは、式ツリーの概要、式ツリーをサポートするフレームワーク クラス、式ツリーの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45488-117">The remaining sections of this tutorial will explore what Expression Trees are, examine the framework classes that support expression trees, and show you how to work with expression trees.</span></span> <span data-ttu-id="45488-118">式ツリーの読み方、式ツリーの作成方法、変更を加えた式ツリーの作成方法、式ツリーで表されるコードの実行方法を学びます。</span><span class="sxs-lookup"><span data-stu-id="45488-118">You'll learn how to read expression trees, how to create expression trees, how to create modified expression trees, and how to execute the code represented by expression trees.</span></span> <span data-ttu-id="45488-119">チュートリアルを読み終わると、これらの構造を使用し、高度な適合アルゴリズムを作成できるようになります。</span><span class="sxs-lookup"><span data-stu-id="45488-119">After reading, you will be ready to use these structures to create rich adaptive algorithms.</span></span>

1. [<span data-ttu-id="45488-120">式ツリーの説明</span><span class="sxs-lookup"><span data-stu-id="45488-120">Expression Trees Explained</span></span>](expression-trees-explained.md)

    <span data-ttu-id="45488-121">*式ツリー*の構造と概念を理解します。</span><span class="sxs-lookup"><span data-stu-id="45488-121">Understand the structure and concepts behind *Expression Trees*.</span></span>

2. [<span data-ttu-id="45488-122">式ツリーをサポートするフレームワークの型</span><span class="sxs-lookup"><span data-stu-id="45488-122">Framework Types Supporting Expression Trees</span></span>](expression-classes.md)

    <span data-ttu-id="45488-123">式ツリーを定義し、操作する構造とクラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="45488-123">Learn about the structures and classes that define and manipulate expression trees.</span></span>

3. [<span data-ttu-id="45488-124">式の実行</span><span class="sxs-lookup"><span data-stu-id="45488-124">Executing Expressions</span></span>](expression-trees-execution.md)

    <span data-ttu-id="45488-125">ラムダ式で表される式ツリーをデリゲートに変換し、結果のデリゲートを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45488-125">Learn how to convert an expression tree represented as a Lambda Expression into a delegate and execute the resulting delegate.</span></span>

4. [<span data-ttu-id="45488-126">式の解釈</span><span class="sxs-lookup"><span data-stu-id="45488-126">Interpreting Expressions</span></span>](expression-trees-interpreting.md)

    <span data-ttu-id="45488-127">式ツリーを走査して確認し、*式ツリー*が表すコードの内容を理解する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45488-127">Learn how to traverse and examine *expression trees* to understand what code the expression tree represents.</span></span>

5. [<span data-ttu-id="45488-128">式の構築</span><span class="sxs-lookup"><span data-stu-id="45488-128">Building Expressions</span></span>](expression-trees-building.md)

    <span data-ttu-id="45488-129">式ツリーのノードを構築し、式ツリーを構築する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45488-129">Learn how to construct the nodes for an expression tree and build expression trees.</span></span>

6. [<span data-ttu-id="45488-130">式の変換</span><span class="sxs-lookup"><span data-stu-id="45488-130">Translating Expressions</span></span>](expression-trees-translating.md)

    <span data-ttu-id="45488-131">式ツリーに変更を加えたコピーを構築する方法、または式ツリーを別の形式に変換する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="45488-131">Learn how to build a modified copy of an expression tree, or translate an expression tree into a different format.</span></span>

7. [<span data-ttu-id="45488-132">まとめ</span><span class="sxs-lookup"><span data-stu-id="45488-132">Summing up</span></span>](expression-trees-summary.md)

    <span data-ttu-id="45488-133">式ツリーに関する情報のまとめです。</span><span class="sxs-lookup"><span data-stu-id="45488-133">Review the information on expression trees.</span></span>
