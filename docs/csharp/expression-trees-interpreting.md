---
title: 式の解釈
description: 式ツリーの構造を調べるためのコードの記述方法について説明します。
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: adf73dde-1e52-4df3-9929-2e0670e28e16
ms.openlocfilehash: 1283d7d957c72558652b96cb428efd0f071f0184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146009"
---
# <a name="interpreting-expressions"></a><span data-ttu-id="3a219-103">式の解釈</span><span class="sxs-lookup"><span data-stu-id="3a219-103">Interpreting Expressions</span></span>

[<span data-ttu-id="3a219-104">前へ -- 式の実行</span><span class="sxs-lookup"><span data-stu-id="3a219-104">Previous -- Executing Expressions</span></span>](expression-trees-execution.md)

<span data-ttu-id="3a219-105">ここでは、*式ツリー*の構造を調べるコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a219-105">Now, let's write some code to examine the structure of an *expression tree*.</span></span> <span data-ttu-id="3a219-106">式ツリー内のすべてのノードは、`Expression` から派生したクラスのオブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="3a219-106">Every node in an expression tree will be an object of a class that is derived from `Expression`.</span></span>

<span data-ttu-id="3a219-107">そうした設計上、式ツリーのすべてのノードへのアクセスには、比較的単純な再帰的操作を使用します。</span><span class="sxs-lookup"><span data-stu-id="3a219-107">That design makes visiting all the nodes in an expression tree a relatively straight forward recursive operation.</span></span> <span data-ttu-id="3a219-108">一般的な方法では、はじめにルート ノードの種類を確認します。</span><span class="sxs-lookup"><span data-stu-id="3a219-108">The general strategy is to start at the root node and determine what kind of node it is.</span></span>

<span data-ttu-id="3a219-109">ノード型に子がある場合は、再帰的に子にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3a219-109">If the node type has children, recursively visit the children.</span></span> <span data-ttu-id="3a219-110">それぞれの子ノードで、ルート ノードで使用したプロセスを繰り返します。つまり、種類を確認し、型に子がある場合は、それぞれの子にアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3a219-110">At each child node, repeat the process used at the root node: determine the type, and if the type has children, visit each of the children.</span></span>

## <a name="examining-an-expression-with-no-children"></a><span data-ttu-id="3a219-111">子を持たない式の確認</span><span class="sxs-lookup"><span data-stu-id="3a219-111">Examining an Expression with No Children</span></span>
<span data-ttu-id="3a219-112">ここでは、非常に単純な式ツリーの各ノードにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="3a219-112">Let's start by visiting each node in a very simple expression tree.</span></span>
<span data-ttu-id="3a219-113">次に示すのは、定数式を作成し、次にそのプロパティを調べるコードです。</span><span class="sxs-lookup"><span data-stu-id="3a219-113">Here's the code that creates a constant expression and then examines its properties:</span></span>

```csharp
var constant = Expression.Constant(24, typeof(int));

Console.WriteLine($"This is a/an {constant.NodeType} expression type");
Console.WriteLine($"The type of the constant value is {constant.Type}");
Console.WriteLine($"The value of the constant value is {constant.Value}");
```

<span data-ttu-id="3a219-114">このコードの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3a219-114">This will print the following:</span></span>

```output
This is an Constant expression type
The type of the constant value is System.Int32
The value of the constant value is 24
```

<span data-ttu-id="3a219-115">では、この式を調べ、式に関する重要なプロパティを書き込むコードを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a219-115">Now, let's write the code that would examine this expression and write out some important properties about it.</span></span> <span data-ttu-id="3a219-116">次に示すのがそのコードです。</span><span class="sxs-lookup"><span data-stu-id="3a219-116">Here's that code:</span></span>

## <a name="examining-a-simple-addition-expression"></a><span data-ttu-id="3a219-117">単純な加算式の確認</span><span class="sxs-lookup"><span data-stu-id="3a219-117">Examining a simple Addition Expression</span></span>

<span data-ttu-id="3a219-118">このセクションの導入として、加算のサンプルから始めます。</span><span class="sxs-lookup"><span data-stu-id="3a219-118">Let's start with the addition sample from the introduction to this section.</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2;
```

> <span data-ttu-id="3a219-119">この式ツリーを宣言するために `var` を使用していません。それは代入の右側は暗黙的に型指定されているためです。</span><span class="sxs-lookup"><span data-stu-id="3a219-119">I'm not using `var` to declare this expression tree, as it is not possible because the right-hand side of the assignment is implicitly typed.</span></span> <span data-ttu-id="3a219-120">このことを詳しく理解するには、[ここ](implicitly-typed-lambda-expressions.md)をお読みください。</span><span class="sxs-lookup"><span data-stu-id="3a219-120">To understand this more deeply, read [here](implicitly-typed-lambda-expressions.md).</span></span>

<span data-ttu-id="3a219-121">ルート ノードは `LambdaExpression` です。</span><span class="sxs-lookup"><span data-stu-id="3a219-121">The root node is a `LambdaExpression`.</span></span> <span data-ttu-id="3a219-122">`=>` 演算子の右側で関心があるコードを取得するため、`LambdaExpression` の子のいずれかを検索する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a219-122">In order to get the interesting code on the right hand side of the `=>` operator, you need to find one of the children of the `LambdaExpression`.</span></span> <span data-ttu-id="3a219-123">このセクションのすべての式について、この操作を行います。</span><span class="sxs-lookup"><span data-stu-id="3a219-123">We'll do that with all the expressions in this section.</span></span> <span data-ttu-id="3a219-124">親ノードは `LambdaExpression` の戻り値の型を検索するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="3a219-124">The parent node does help us find the return type of the `LambdaExpression`.</span></span>

<span data-ttu-id="3a219-125">この式の各ノードを調べるには、いくつかのノードに再帰的にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a219-125">To examine each node in this expression, we'll need to recursively visit a number of nodes.</span></span> <span data-ttu-id="3a219-126">次に示すのは、最初の単純な実装です。</span><span class="sxs-lookup"><span data-stu-id="3a219-126">Here's a simple first implementation:</span></span>

```csharp
Expression<Func<int, int, int>> addition = (a, b) => a + b;

Console.WriteLine($"This expression is a {addition.NodeType} expression type");
Console.WriteLine($"The name of the lambda is {((addition.Name == null) ? "<null>" : addition.Name)}");
Console.WriteLine($"The return type is {addition.ReturnType.ToString()}");
Console.WriteLine($"The expression has {addition.Parameters.Count} arguments. They are:");
foreach(var argumentExpression in addition.Parameters)
{
    Console.WriteLine($"\tParameter Type: {argumentExpression.Type.ToString()}, Name: {argumentExpression.Name}");
}

var additionBody = (BinaryExpression)addition.Body;
Console.WriteLine($"The body is a {additionBody.NodeType} expression");
Console.WriteLine($"The left side is a {additionBody.Left.NodeType} expression");
var left = (ParameterExpression)additionBody.Left;
Console.WriteLine($"\tParameter Type: {left.Type.ToString()}, Name: {left.Name}");
Console.WriteLine($"The right side is a {additionBody.Right.NodeType} expression");
var right= (ParameterExpression)additionBody.Right;
Console.WriteLine($"\tParameter Type: {right.Type.ToString()}, Name: {right.Name}");
```

<span data-ttu-id="3a219-127">このサンプル コードから、次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="3a219-127">This sample prints the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 arguments. They are:
        Parameter Type: System.Int32, Name: a
        Parameter Type: System.Int32, Name: b
The body is a/an Add expression
The left side is a Parameter expression
        Parameter Type: System.Int32, Name: a
The right side is a Parameter expression
        Parameter Type: System.Int32, Name: b
```

<span data-ttu-id="3a219-128">上記のサンプル コードには、繰り返しが多数あることがわかります。</span><span class="sxs-lookup"><span data-stu-id="3a219-128">You'll notice a lot of repetition in the code sample above.</span></span>
<span data-ttu-id="3a219-129">ここで、繰り返しを整理して、より汎用的な式ノード ビジターを作成します。</span><span class="sxs-lookup"><span data-stu-id="3a219-129">Let's clean that up and build a more general purpose expression node visitor.</span></span> <span data-ttu-id="3a219-130">それには、再帰的なアルゴリズムを記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a219-130">That's going to require us to write a recursive algorithm.</span></span> <span data-ttu-id="3a219-131">どのノードにも子を持つ型である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3a219-131">Any node could be of a type that might have children.</span></span>
<span data-ttu-id="3a219-132">子を持つすべてのノードで、その子にアクセスし、ノードの種類を確認することが必要です。</span><span class="sxs-lookup"><span data-stu-id="3a219-132">Any node that has children requires us to visit those children and determine what that node is.</span></span> <span data-ttu-id="3a219-133">次に示す整理したバージョンでは、加算操作にアクセスするために再帰を使用しています。</span><span class="sxs-lookup"><span data-stu-id="3a219-133">Here's the cleaned up version that utilizes recursion to visit the addition operations:</span></span>

```csharp
// Base Visitor class:
public abstract class Visitor
{
    private readonly Expression node;

    protected Visitor(Expression node)
    {
        this.node = node;
    }

    public abstract void Visit(string prefix);

    public ExpressionType NodeType => this.node.NodeType;
    public static Visitor CreateFromExpression(Expression node)
    {
        switch(node.NodeType)
        {
            case ExpressionType.Constant:
                return new ConstantVisitor((ConstantExpression)node);
            case ExpressionType.Lambda:
                return new LambdaVisitor((LambdaExpression)node);
            case ExpressionType.Parameter:
                return new ParameterVisitor((ParameterExpression)node);
            case ExpressionType.Add:
                return new BinaryVisitor((BinaryExpression)node);
            default:
                Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
                return default(Visitor);
        }
    }
}

// Lambda Visitor
public class LambdaVisitor : Visitor
{
    private readonly LambdaExpression node;
    public LambdaVisitor(LambdaExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression type");
        Console.WriteLine($"{prefix}The name of the lambda is {((node.Name == null) ? "<null>" : node.Name)}");
        Console.WriteLine($"{prefix}The return type is {node.ReturnType.ToString()}");
        Console.WriteLine($"{prefix}The expression has {node.Parameters.Count} argument(s). They are:");
        // Visit each parameter:
        foreach (var argumentExpression in node.Parameters)
        {
            var argumentVisitor = Visitor.CreateFromExpression(argumentExpression);
            argumentVisitor.Visit(prefix + "\t");
        }
        Console.WriteLine($"{prefix}The expression body is:");
        // Visit the body:
        var bodyVisitor = Visitor.CreateFromExpression(node.Body);
        bodyVisitor.Visit(prefix + "\t");
    }
}

// Binary Expression Visitor:
public class BinaryVisitor : Visitor
{
    private readonly BinaryExpression node;
    public BinaryVisitor(BinaryExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This binary expression is a {NodeType} expression");
        var left = Visitor.CreateFromExpression(node.Left);
        Console.WriteLine($"{prefix}The Left argument is:");
        left.Visit(prefix + "\t");
        var right = Visitor.CreateFromExpression(node.Right);
        Console.WriteLine($"{prefix}The Right argument is:");
        right.Visit(prefix + "\t");
    }
}

// Parameter visitor:
public class ParameterVisitor : Visitor
{
    private readonly ParameterExpression node;
    public ParameterVisitor(ParameterExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}Type: {node.Type.ToString()}, Name: {node.Name}, ByRef: {node.IsByRef}");
    }
}

// Constant visitor:
public class ConstantVisitor : Visitor
{
    private readonly ConstantExpression node;
    public ConstantVisitor(ConstantExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This is an {NodeType} expression type");
        Console.WriteLine($"{prefix}The type of the constant value is {node.Type}");
        Console.WriteLine($"{prefix}The value of the constant value is {node.Value}");
    }
}
```

<span data-ttu-id="3a219-134">このアルゴリズムは、任意の `LambdaExpression` にアクセスするアルゴリズムの基礎となります。</span><span class="sxs-lookup"><span data-stu-id="3a219-134">This algorithm is the basis of an algorithm that can visit any arbitrary `LambdaExpression`.</span></span> <span data-ttu-id="3a219-135">このコードには穴が多数あります。つまり、ここで作成したコードは、検出する可能性がある一連の式ツリーのノードのうち、ごく一部のサンプルしか探索しません。</span><span class="sxs-lookup"><span data-stu-id="3a219-135">There are a lot of holes, namely that the code I created only looks for a very small sample of the possible sets of expression tree nodes that it may encounter.</span></span> <span data-ttu-id="3a219-136">それでも、このコードからかなりのことを学ぶことができます。</span><span class="sxs-lookup"><span data-stu-id="3a219-136">However, you can still learn quite a bit from what it produces.</span></span> <span data-ttu-id="3a219-137">(`Visitor.CreateFromExpression` メソッドの default case では、新しいノード型が検出されると、エラー コンソールにメッセージが出力されます。</span><span class="sxs-lookup"><span data-stu-id="3a219-137">(The default case in the `Visitor.CreateFromExpression` method prints a message to the error console when a new node type is encountered.</span></span> <span data-ttu-id="3a219-138">これによって、新しい式の型を追加する必要があることがわかります。)</span><span class="sxs-lookup"><span data-stu-id="3a219-138">That way, you know to add a new expression type.)</span></span>

<span data-ttu-id="3a219-139">上記の加算式でこのビジターを実行すると、次のような出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="3a219-139">When you run this visitor on the addition expression shown above, you get the following output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This is an Parameter expression type
                Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="3a219-140">こうして、より汎用的なビジターを実装すると、多種多様な式の型にアクセスして処理できるようになります。</span><span class="sxs-lookup"><span data-stu-id="3a219-140">Now that you've built a more general visitor implementation, you can visit and process many more different types of expressions.</span></span>

## <a name="examining-an-addition-expression-with-many-levels"></a><span data-ttu-id="3a219-141">さまざまなレベルの加算式の確認</span><span class="sxs-lookup"><span data-stu-id="3a219-141">Examining an Addition Expression with Many Levels</span></span>

<span data-ttu-id="3a219-142">次に、もっと複雑な例を取り上げます。ただし、ノード型は引き続き加算だけにとどめます。</span><span class="sxs-lookup"><span data-stu-id="3a219-142">Let's try a more complicated example, yet still limit the node types to addition only:</span></span>

```csharp
Expression<Func<int>> sum = () => 1 + 2 + 3 + 4;
```

<span data-ttu-id="3a219-143">これをビジター アルゴリズムで実行する前に、出力がどうなるか、思考訓練をしてください。</span><span class="sxs-lookup"><span data-stu-id="3a219-143">Before you run this on the visitor algorithm, try a thought exercise to work out what the output might be.</span></span> <span data-ttu-id="3a219-144">`+` 演算子は*二項演算子*です。つまり、左側オペランドと右側オペランドを表す 2 つの子を持っている必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a219-144">Remember that the `+` operator is a *binary operator*: it must have two children, representing the left and right operands.</span></span> <span data-ttu-id="3a219-145">正しいと考えられるツリーを構築する方法はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="3a219-145">There are several possible ways to construct a tree that could be correct:</span></span>

```csharp
Expression<Func<int>> sum1 = () => 1 + (2 + (3 + 4));
Expression<Func<int>> sum2 = () => ((1 + 2) + 3) + 4;

Expression<Func<int>> sum3 = () => (1 + 2) + (3 + 4);
Expression<Func<int>> sum4 = () => 1 + ((2 + 3) + 4);
Expression<Func<int>> sum5 = () => (1 + (2 + 3)) + 4;
```

<span data-ttu-id="3a219-146">可能性のある答えを 2 つに分けて考えれば、最も見込みがある答えに着目できます。</span><span class="sxs-lookup"><span data-stu-id="3a219-146">You can see the separation into two possible answers to highlight the most promising.</span></span> <span data-ttu-id="3a219-147">1 つ目は、*結合規則が右から左*の式です。</span><span class="sxs-lookup"><span data-stu-id="3a219-147">The first represents *right associative* expressions.</span></span> <span data-ttu-id="3a219-148">2 つ目は、*結合規則が左から右*の式です。</span><span class="sxs-lookup"><span data-stu-id="3a219-148">The second represent *left associative* expressions.</span></span>
<span data-ttu-id="3a219-149">これら 2 つの書式の利点は、任意の数の加算式に拡張できる点です。</span><span class="sxs-lookup"><span data-stu-id="3a219-149">The advantage of both of those two formats is that the format scales to any arbitrary number of addition expressions.</span></span>

<span data-ttu-id="3a219-150">この式をビジターで実行すると、表示された出力から、単純な加算式では*結合関係が左から右*に評価されることを検証できます。</span><span class="sxs-lookup"><span data-stu-id="3a219-150">If you do run this expression through the visitor, you will see this this output, verifying that the simple addition expression is *left associative*.</span></span>

<span data-ttu-id="3a219-151">このサンプルを実行して、完全な式ツリーを表示するために、ソースの式ツリーに 1 つ変更を加える必要がありました。</span><span class="sxs-lookup"><span data-stu-id="3a219-151">In order to run this sample, and see the full expression tree, I had to make one change to the source expression tree.</span></span> <span data-ttu-id="3a219-152">式ツリーに含まれるのがすべて定数である場合、結果のツリーに含まれるのは定数値の `10` だけです。</span><span class="sxs-lookup"><span data-stu-id="3a219-152">When the expression tree contains all constants, the resulting tree simply contains the constant value of `10`.</span></span> <span data-ttu-id="3a219-153">コンパイラはすべての加算を実行し、式を最も単純な形式に変換します。</span><span class="sxs-lookup"><span data-stu-id="3a219-153">The compiler performs all the addition and reduces the expression to its simplest form.</span></span> <span data-ttu-id="3a219-154">元のツリーを確認するには、式に 1 つの変数を追加するだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="3a219-154">Simply adding one variable in the expression is sufficient to see the original tree:</span></span>

```csharp
Expression<Func<int, int>> sum = (a) => 1 + a + 3 + 4;
```

<span data-ttu-id="3a219-155">これを合計するビジターを作成し、実行すれば、次の出力が得られます。</span><span class="sxs-lookup"><span data-stu-id="3a219-155">Create a visitor for this sum and run the visitor you'll see this output:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This binary expression is a Add expression
                        The Left argument is:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                        The Right argument is:
                                This is an Parameter expression type
                                Type: System.Int32, Name: a, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
        The Right argument is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 4
```

<span data-ttu-id="3a219-156">このビジター コードを使用して、他のサンプルを実行すれば、そのコードが表わすツリーを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3a219-156">You can also run any of the other samples through the visitor code and see what tree it represents.</span></span> <span data-ttu-id="3a219-157">次に示す例は、上記の `sum3` 式です (コンパイラが定数を計算するのを防ぐためにパラメーターを追加しています)。</span><span class="sxs-lookup"><span data-stu-id="3a219-157">Here's an example of the `sum3` expression above (with an additional parameter to prevent the compiler from computing the constant):</span></span>

```csharp
Expression<Func<int, int, int>> sum3 = (a, b) => (1 + a) + (3 + b);
```

<span data-ttu-id="3a219-158">ビジターからの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3a219-158">Here's the output from the visitor:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 2 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: a, ByRef: False
        This is an Parameter expression type
        Type: System.Int32, Name: b, ByRef: False
The expression body is:
        This binary expression is a Add expression
        The Left argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 1
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: a, ByRef: False
        The Right argument is:
                This binary expression is a Add expression
                The Left argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 3
                The Right argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: b, ByRef: False
```

<span data-ttu-id="3a219-159">かっこは出力の一部ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="3a219-159">Notice that the parentheses are not part of the output.</span></span> <span data-ttu-id="3a219-160">入力式のかっこを表すノードは、式ツリーの中にありません。</span><span class="sxs-lookup"><span data-stu-id="3a219-160">There are no nodes in the expression tree that represent the parentheses in the input expression.</span></span> <span data-ttu-id="3a219-161">式ツリーの構造体には、優先順位を伝達するために必要なすべての情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3a219-161">The structure of the expression tree contains all the information necessary to communicate the precedence.</span></span>

## <a name="extending-from-this-sample"></a><span data-ttu-id="3a219-162">このサンプルの拡張</span><span class="sxs-lookup"><span data-stu-id="3a219-162">Extending from this sample</span></span>

<span data-ttu-id="3a219-163">このサンプルは、最も基本的な式ツリーのみを処理します。</span><span class="sxs-lookup"><span data-stu-id="3a219-163">The sample deals with only the most rudimentary expression trees.</span></span> <span data-ttu-id="3a219-164">このセクションに示されるコードでは、整数定数と二項演算子 `+` のみを扱います。</span><span class="sxs-lookup"><span data-stu-id="3a219-164">The code you've seen in this section only handles constant integers and the binary `+` operator.</span></span> <span data-ttu-id="3a219-165">次に、最後のサンプルとして、より複雑な式を扱うビジターに更新します。</span><span class="sxs-lookup"><span data-stu-id="3a219-165">As a final sample, let's update the visitor to handle a more complicated expression.</span></span> <span data-ttu-id="3a219-166">次の式に対応させることにします。</span><span class="sxs-lookup"><span data-stu-id="3a219-166">Let's make it work for this:</span></span>

```csharp
Expression<Func<int, int>> factorial = (n) =>
    n == 0 ?
    1 :
    Enumerable.Range(1, n).Aggregate((product, factor) => product * factor);
```

<span data-ttu-id="3a219-167">このコードは、数学の*階乗*関数に対して考えられる実装の 1 つです。</span><span class="sxs-lookup"><span data-stu-id="3a219-167">This code represents one possible implementation for the mathematical *factorial* function.</span></span> <span data-ttu-id="3a219-168">このコードの記述方法によって、式にラムダ式を代入して式ツリーを構築する場合の 2 つの制限事項が強調されています。</span><span class="sxs-lookup"><span data-stu-id="3a219-168">The way I've written this code highlights two limitations of building expression trees by assigning lambda expressions to Expressions.</span></span> <span data-ttu-id="3a219-169">第 1 に、ステートメント形式のラムダは使用できません。</span><span class="sxs-lookup"><span data-stu-id="3a219-169">First, statement lambdas are not allowed.</span></span> <span data-ttu-id="3a219-170">つまり、C# で一般的なループ、ブロック、if / else ステートメント、その他の制御構造を使用できないということです。</span><span class="sxs-lookup"><span data-stu-id="3a219-170">That means I can't use loops, blocks, if / else statements, and other control structures common in C#.</span></span> <span data-ttu-id="3a219-171">式の使用だけに制限されます。</span><span class="sxs-lookup"><span data-stu-id="3a219-171">I'm limited to using expressions.</span></span> <span data-ttu-id="3a219-172">第 2 に、同じ式を再帰的に呼び出すことができません。</span><span class="sxs-lookup"><span data-stu-id="3a219-172">Second, I can't recursively call the same expression.</span></span>
<span data-ttu-id="3a219-173">式が既にデリゲートになっている場合は呼び出せますが、式ツリー形式で呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="3a219-173">I could if it were already a delegate, but I can't call it in its expression tree form.</span></span> <span data-ttu-id="3a219-174">これらの制限を克服する手法については、「[式ツリーの構築](expression-trees-building.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a219-174">In the section on [building expression trees](expression-trees-building.md) you'll learn techniques to overcome these limitations.</span></span>

<span data-ttu-id="3a219-175">この式では、次の型のノードすべてが使用されています。</span><span class="sxs-lookup"><span data-stu-id="3a219-175">In this expression, you'll encounter nodes of all these types:</span></span>

1. <span data-ttu-id="3a219-176">等号 (二項式)</span><span class="sxs-lookup"><span data-stu-id="3a219-176">Equal (binary expression)</span></span>
2. <span data-ttu-id="3a219-177">乗算 (二項式)</span><span class="sxs-lookup"><span data-stu-id="3a219-177">Multiply (binary expression)</span></span>
3. <span data-ttu-id="3a219-178">条件付き (?</span><span class="sxs-lookup"><span data-stu-id="3a219-178">Conditional (the ?</span></span> <span data-ttu-id="3a219-179">: 式)</span><span class="sxs-lookup"><span data-stu-id="3a219-179">: expression)</span></span>
4. <span data-ttu-id="3a219-180">メソッド呼び出し式 (`Range()` と `Aggregate()` を呼び出す)</span><span class="sxs-lookup"><span data-stu-id="3a219-180">Method Call Expression (calling `Range()` and `Aggregate()`)</span></span>

<span data-ttu-id="3a219-181">ビジター アルゴリズムを修正する方法の 1 つは、アルゴリズムの実行を繰り返し、`default` 句に行き着くたびにノード型を記述することです。</span><span class="sxs-lookup"><span data-stu-id="3a219-181">One way to modify the visitor algorithm is to keep executing it, and write the node type every time you reach your `default` clause.</span></span> <span data-ttu-id="3a219-182">数回繰り返せば、検出の可能性がある各ノードを確認できます。</span><span class="sxs-lookup"><span data-stu-id="3a219-182">After a few iterations, you'll have seen each of the potential nodes.</span></span> <span data-ttu-id="3a219-183">その段階で、必要なものがすべて揃います。</span><span class="sxs-lookup"><span data-stu-id="3a219-183">Then, you have all you need.</span></span> <span data-ttu-id="3a219-184">結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3a219-184">The result would be something like this:</span></span>

```csharp
public static Visitor CreateFromExpression(Expression node)
{
    switch(node.NodeType)
    {
        case ExpressionType.Constant:
            return new ConstantVisitor((ConstantExpression)node);
        case ExpressionType.Lambda:
            return new LambdaVisitor((LambdaExpression)node);
        case ExpressionType.Parameter:
            return new ParameterVisitor((ParameterExpression)node);
        case ExpressionType.Add:
        case ExpressionType.Equal:
        case ExpressionType.Multiply:
            return new BinaryVisitor((BinaryExpression)node);
        case ExpressionType.Conditional:
            return new ConditionalVisitor((ConditionalExpression)node);
        case ExpressionType.Call:
            return new MethodCallVisitor((MethodCallExpression)node);
        default:
            Console.Error.WriteLine($"Node not processed yet: {node.NodeType}");
            return default(Visitor);
    }
}
```

<span data-ttu-id="3a219-185">ConditionalVisitor と MethodCallVisitor がこれら 2 つのノードを処理します。</span><span class="sxs-lookup"><span data-stu-id="3a219-185">The ConditionalVisitor and MethodCallVisitor process those two nodes:</span></span>

```csharp
public class ConditionalVisitor : Visitor
{
    private readonly ConditionalExpression node;
    public ConditionalVisitor(ConditionalExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        var testVisitor = Visitor.CreateFromExpression(node.Test);
        Console.WriteLine($"{prefix}The Test for this expression is:");
        testVisitor.Visit(prefix + "\t");
        var trueVisitor = Visitor.CreateFromExpression(node.IfTrue);
        Console.WriteLine($"{prefix}The True clause for this expression is:");
        trueVisitor.Visit(prefix + "\t");
        var falseVisitor = Visitor.CreateFromExpression(node.IfFalse);
        Console.WriteLine($"{prefix}The False clause for this expression is:");
        falseVisitor.Visit(prefix + "\t");
    }
}

public class MethodCallVisitor : Visitor
{
    private readonly MethodCallExpression node;
    public MethodCallVisitor(MethodCallExpression node) : base(node)
    {
        this.node = node;
    }

    public override void Visit(string prefix)
    {
        Console.WriteLine($"{prefix}This expression is a {NodeType} expression");
        if (node.Object == null)
            Console.WriteLine($"{prefix}This is a static method call");
        else
        {
            Console.WriteLine($"{prefix}The receiver (this) is:");
            var receiverVisitor = Visitor.CreateFromExpression(node.Object);
            receiverVisitor.Visit(prefix + "\t");
        }

        var methodInfo = node.Method;
        Console.WriteLine($"{prefix}The method name is {methodInfo.DeclaringType}.{methodInfo.Name}");
        // There is more here, like generic arguments, and so on.
        Console.WriteLine($"{prefix}The Arguments are:");
        foreach(var arg in node.Arguments)
        {
            var argVisitor = Visitor.CreateFromExpression(arg);
            argVisitor.Visit(prefix + "\t");
        }
    }
}
```

<span data-ttu-id="3a219-186">式ツリーの出力は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="3a219-186">And the output for the expression tree would be:</span></span>

```output
This expression is a/an Lambda expression type
The name of the lambda is <null>
The return type is System.Int32
The expression has 1 argument(s). They are:
        This is an Parameter expression type
        Type: System.Int32, Name: n, ByRef: False
The expression body is:
        This expression is a Conditional expression
        The Test for this expression is:
                This binary expression is a Equal expression
                The Left argument is:
                        This is an Parameter expression type
                        Type: System.Int32, Name: n, ByRef: False
                The Right argument is:
                        This is an Constant expression type
                        The type of the constant value is System.Int32
                        The value of the constant value is 0
        The True clause for this expression is:
                This is an Constant expression type
                The type of the constant value is System.Int32
                The value of the constant value is 1
        The False clause for this expression is:
                This expression is a Call expression
                This is a static method call
                The method name is System.Linq.Enumerable.Aggregate
                The Arguments are:
                        This expression is a Call expression
                        This is a static method call
                        The method name is System.Linq.Enumerable.Range
                        The Arguments are:
                                This is an Constant expression type
                                The type of the constant value is System.Int32
                                The value of the constant value is 1
                                This is an Parameter expression type
                                Type: System.Int32, Name: n, ByRef: False
                        This expression is a Lambda expression type
                        The name of the lambda is <null>
                        The return type is System.Int32
                        The expression has 2 arguments. They are:
                                This is an Parameter expression type
                                Type: System.Int32, Name: product, ByRef: False
                                This is an Parameter expression type
                                Type: System.Int32, Name: factor, ByRef: False
                        The expression body is:
                                This binary expression is a Multiply expression
                                The Left argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: product, ByRef: False
                                The Right argument is:
                                        This is an Parameter expression type
                                        Type: System.Int32, Name: factor, ByRef: False
```

## <a name="extending-the-sample-library"></a><span data-ttu-id="3a219-187">サンプル ライブラリの拡張</span><span class="sxs-lookup"><span data-stu-id="3a219-187">Extending the Sample Library</span></span>

<span data-ttu-id="3a219-188">このセクションのサンプルでは、式ツリーのノードにアクセスして調べるための中核的な手法を示します。</span><span class="sxs-lookup"><span data-stu-id="3a219-188">The samples in this section show the core techniques to visit and examine nodes in an expression tree.</span></span> <span data-ttu-id="3a219-189">ここでは、式ツリーのノードにアクセスする主要なタスクに重点的に取り組むために必要な多くのアクションについて説明しました。</span><span class="sxs-lookup"><span data-stu-id="3a219-189">I glossed over many actions you might need in order to concentrate on the core tasks of visiting and accessing nodes in an expression tree.</span></span>

<span data-ttu-id="3a219-190">第 1 に、ビジターは整数の定数だけを処理します。</span><span class="sxs-lookup"><span data-stu-id="3a219-190">First, the visitors only handle constants that are integers.</span></span> <span data-ttu-id="3a219-191">定数値は他の数値型になることができ、C# 言語ではそれらの型同士の変換や昇格がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="3a219-191">Constant values could be any other numeric type, and the C# language supports conversions and promotions between those types.</span></span> <span data-ttu-id="3a219-192">このコードのより堅牢なバージョンには、それらすべての機能が反映されています。</span><span class="sxs-lookup"><span data-stu-id="3a219-192">A more robust version of this code would mirror all those capabilities.</span></span>

<span data-ttu-id="3a219-193">最後のサンプルでも、想定されるノード型のサブセットを認識できます。</span><span class="sxs-lookup"><span data-stu-id="3a219-193">Even the last example recognizes a subset of the possible node types.</span></span>
<span data-ttu-id="3a219-194">コードの処理が失敗する式をさらに読み込ませることもできます。</span><span class="sxs-lookup"><span data-stu-id="3a219-194">You can still feed it many expressions that will cause it to fail.</span></span>
<span data-ttu-id="3a219-195">完全な実装は、<xref:System.Linq.Expressions.ExpressionVisitor> という名前で .NET Standard に含まれていて、想定されるすべてのノード型を処理できます。</span><span class="sxs-lookup"><span data-stu-id="3a219-195">A full implementation is included in the .NET Standard under the name <xref:System.Linq.Expressions.ExpressionVisitor> and can handle all the possible node types.</span></span>

<span data-ttu-id="3a219-196">最後に、この記事で使用したライブラリはデモ用および学習用として構築しました。</span><span class="sxs-lookup"><span data-stu-id="3a219-196">Finally, the library I used in this article was built for demonstration and learning.</span></span> <span data-ttu-id="3a219-197">ライブラリの最適化は行っていません。</span><span class="sxs-lookup"><span data-stu-id="3a219-197">It's not optimized.</span></span> <span data-ttu-id="3a219-198">ライブラリを記述したのは、使用した構造体を明確にし、ノードのアクセスに使用した手法を浮き彫りにして、その内容を分析するためです。</span><span class="sxs-lookup"><span data-stu-id="3a219-198">I wrote it to make the structures used very clear, and to highlight the techniques used to visit the nodes and analyze what's there.</span></span> <span data-ttu-id="3a219-199">運用環境への実装では、今回試みたよりもさらにパフォーマンスに注意を払うことになります。</span><span class="sxs-lookup"><span data-stu-id="3a219-199">A production implementation would pay more attention to performance than I have.</span></span>

<span data-ttu-id="3a219-200">こうした制限があるとはいえ、式ツリーを読み、理解するアルゴリズムの作成を問題なく進めていけるはずです。</span><span class="sxs-lookup"><span data-stu-id="3a219-200">Even with those limitations, you should be well on your way to writing algorithms that read and understand expression trees.</span></span>

[<span data-ttu-id="3a219-201">次へ -- 式の構築</span><span class="sxs-lookup"><span data-stu-id="3a219-201">Next -- Building Expressions</span></span>](expression-trees-building.md)
