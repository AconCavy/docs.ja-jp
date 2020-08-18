---
title: LINQ をサポートする C# の機能
description: LINQ クエリおよびその他のコンテキストで使用する C# の機能について説明します。 これらの言語構成要素は、C# 3.0 で導入されました。
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], features supporting LINQ
ms.assetid: 524b0078-ebfd-45a7-b390-f2ceb9d84797
ms.openlocfilehash: 13254c69193e04ffcf11e3e23f1deb460063a6c1
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063693"
---
# <a name="c-features-that-support-linq"></a><span data-ttu-id="fe17d-104">LINQ をサポートする C# の機能</span><span class="sxs-lookup"><span data-stu-id="fe17d-104">C# Features That Support LINQ</span></span>

<span data-ttu-id="fe17d-105">このセクションでは、C# 3.0 で導入された新しい言語構成要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="fe17d-105">The following section introduces new language constructs introduced in C# 3.0.</span></span> <span data-ttu-id="fe17d-106">これらの新機能はすべてある程度まで LINQ クエリで使用されていますが、LINQ だけでなく、これらの機能が役立つと思われるあらゆる状況で使用できます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-106">Although these new features are all used to a degree with LINQ queries, they are not limited to LINQ and can be used in any context where you find them useful.</span></span>

## <a name="query-expressions"></a><span data-ttu-id="fe17d-107">クエリ式</span><span class="sxs-lookup"><span data-stu-id="fe17d-107">Query Expressions</span></span>

<span data-ttu-id="fe17d-108">クエリ式は、SQL や XQuery に似た宣言型構文を使用して、IEnumerable コレクションを照会します。</span><span class="sxs-lookup"><span data-stu-id="fe17d-108">Query expressions use a declarative syntax similar to SQL or XQuery to query over IEnumerable collections.</span></span> <span data-ttu-id="fe17d-109">クエリ構文は、コンパイル時に、LINQ プロバイダーの標準クエリ演算子拡張メソッドの実装に対するメソッド呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-109">At compile time query syntax is converted to method calls to a LINQ provider's implementation of the standard query operator extension methods.</span></span> <span data-ttu-id="fe17d-110">アプリケーションは、`using` ディレクティブを使用して適切な名前空間を指定することにより、スコープ内の標準クエリ演算子を制御します。</span><span class="sxs-lookup"><span data-stu-id="fe17d-110">Applications control the standard query operators that are in scope by specifying the appropriate namespace with a `using` directive.</span></span> <span data-ttu-id="fe17d-111">次のクエリ式では、文字列の配列を受け取り、文字列の最初の文字を基に文字列をグループ化し、グループを並び替えています。</span><span class="sxs-lookup"><span data-stu-id="fe17d-111">The following query expression takes an array of strings, groups them according to the first character in the string, and orders the groups.</span></span>

```csharp
var query = from str in stringArray
            group str by str[0] into stringGroup
            orderby stringGroup.Key
            select stringGroup;
```

<span data-ttu-id="fe17d-112">詳細については、「[LINQ クエリ式](../../../linq/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe17d-112">For more information, see [LINQ Query Expressions](../../../linq/index.md).</span></span>

## <a name="implicitly-typed-variables-var"></a><span data-ttu-id="fe17d-113">暗黙的に型指定された変数 (var)</span><span class="sxs-lookup"><span data-stu-id="fe17d-113">Implicitly Typed Variables (var)</span></span>

<span data-ttu-id="fe17d-114">変数を宣言して初期化するときに、型を明示的に指定する代わりに、次に示すように [var](../../../language-reference/keywords/var.md) 修飾子を使用すると、コンパイラが型を推論して代入するように指示できます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-114">Instead of explicitly specifying a type when you declare and initialize a variable, you can use the [var](../../../language-reference/keywords/var.md) modifier to instruct the compiler to infer and assign the type, as shown here:</span></span>

```csharp
var number = 5;
var name = "Virginia";
var query = from str in stringArray
            where str[0] == 'm'
            select str;
```

<span data-ttu-id="fe17d-115">`var` として宣言された変数は、明示的に型を指定した変数とまったく同じように厳密に型指定されます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-115">Variables declared as `var` are just as strongly typed as variables whose type you specify explicitly.</span></span> <span data-ttu-id="fe17d-116">`var` を使用すると匿名型を作成できますが、ローカル変数にのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-116">The use of `var` makes it possible to create anonymous types, but it can be used only for local variables.</span></span> <span data-ttu-id="fe17d-117">また、暗黙的な型指定を使用して、配列を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-117">Arrays can also be declared with implicit typing.</span></span>

<span data-ttu-id="fe17d-118">詳細については、「[暗黙的に型指定されるローカル変数](../../classes-and-structs/implicitly-typed-local-variables.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe17d-118">For more information, see [Implicitly Typed Local Variables](../../classes-and-structs/implicitly-typed-local-variables.md).</span></span>

## <a name="object-and-collection-initializers"></a><span data-ttu-id="fe17d-119">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="fe17d-119">Object and Collection Initializers</span></span>

<span data-ttu-id="fe17d-120">オブジェクト初期化子とコレクション初期化子を使用すると、オブジェクトのコンストラクターを明示的に呼び出さなくても、オブジェクトを初期化できます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-120">Object and collection initializers make it possible to initialize objects without explicitly calling a constructor for the object.</span></span> <span data-ttu-id="fe17d-121">通常、初期化子は、ソース データを新しいデータ型に投影するクエリ式で使用されます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-121">Initializers are typically used in query expressions when they project the source data into a new data type.</span></span> <span data-ttu-id="fe17d-122">パブリックな `Name` プロパティと `Phone` プロパティを持つ `Customer` という名前のクラスがある場合、オブジェクト初期化子は次のコードのように使用できます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-122">Assuming a class named `Customer` with public `Name` and `Phone` properties, the object initializer can be used as in the following code:</span></span>

```csharp
var cust = new Customer { Name = "Mike", Phone = "555-1212" };
```

<span data-ttu-id="fe17d-123">引き続き `Customer` クラスの例を進めます。`IncomingOrders` というデータ ソースがあり、`OrderSize` が大きな注文ごとに、その注文に基づいて新しい `Customer` を作成するとします。</span><span class="sxs-lookup"><span data-stu-id="fe17d-123">Continuing with our `Customer` class, assume that there is a data source called `IncomingOrders`, and that for each order with a large `OrderSize`, we would like to create a new `Customer` based off of that order.</span></span> <span data-ttu-id="fe17d-124">LINQ クエリをこのデータ ソースで実行し、オブジェクト初期化を使用してコレクションを満たすことができます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-124">A LINQ query can be executed on this data source and use object initialization to fill a collection:</span></span>

```csharp
var newLargeOrderCustomers = from o in IncomingOrders
                            where o.OrderSize > 5
                            select new Customer { Name = o.Name, Phone = o.Phone };
```

<span data-ttu-id="fe17d-125">データ ソースには、`OrderSize` など、`Customer` クラス以外にもプロパティが存在する可能性がありますが、オブジェクト初期化を利用することで、クエリから返されるデータは目的のデータ型に形成されます。今回のクラスに関連するデータを選択します。</span><span class="sxs-lookup"><span data-stu-id="fe17d-125">The data source may have more properties lying under the hood than the `Customer` class such as `OrderSize`, but with object initialization, the data returned from the query is molded into the desired data type; we choose the data that is relevant to our class.</span></span> <span data-ttu-id="fe17d-126">その結果、必要とする新しい `Customer` が `IEnumerable` に入力されました。</span><span class="sxs-lookup"><span data-stu-id="fe17d-126">As a result, we now have an `IEnumerable` filled with the new `Customer`s we wanted.</span></span> <span data-ttu-id="fe17d-127">上記は次のような LINQ のメソッド構文でも記述できます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-127">The above can also be written in LINQ's method syntax:</span></span>

```csharp
var newLargeOrderCustomers = IncomingOrders.Where(x => x.OrderSize > 5).Select(y => new Customer { Name = y.Name, Phone = y.Phone });
```

<span data-ttu-id="fe17d-128">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="fe17d-128">For more information, see:</span></span>

- [<span data-ttu-id="fe17d-129">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="fe17d-129">Object and Collection Initializers</span></span>](../../classes-and-structs/object-and-collection-initializers.md)

- [<span data-ttu-id="fe17d-130">標準クエリ演算子のクエリ式構文</span><span class="sxs-lookup"><span data-stu-id="fe17d-130">Query Expression Syntax for Standard Query Operators</span></span>](./query-expression-syntax-for-standard-query-operators.md)

## <a name="anonymous-types"></a><span data-ttu-id="fe17d-131">匿名型</span><span class="sxs-lookup"><span data-stu-id="fe17d-131">Anonymous Types</span></span>

<span data-ttu-id="fe17d-132">匿名型はコンパイラによって作成され、型名はコンパイラにしかわかりません。</span><span class="sxs-lookup"><span data-stu-id="fe17d-132">An anonymous type is constructed by the compiler and the type name is only available to the compiler.</span></span> <span data-ttu-id="fe17d-133">匿名型を使用すると、個別に名前付き型を定義しなくても、クエリ結果内のプロパティのセットを一時的にグループ化できるため便利です。</span><span class="sxs-lookup"><span data-stu-id="fe17d-133">Anonymous types provide a convenient way to group a set of properties temporarily in a query result without having to define a separate named type.</span></span> <span data-ttu-id="fe17d-134">次に示すように、匿名型は new 式とオブジェクト初期化子を使用して初期化されます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-134">Anonymous types are initialized with a new expression and an object initializer, as shown here:</span></span>

```csharp
select new {name = cust.Name, phone = cust.Phone};
```

<span data-ttu-id="fe17d-135">詳細については、「[匿名型](../../classes-and-structs/anonymous-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe17d-135">For more information, see [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>

## <a name="extension-methods"></a><span data-ttu-id="fe17d-136">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="fe17d-136">Extension Methods</span></span>

<span data-ttu-id="fe17d-137">拡張メソッドは型に関連付けることができる静的メソッドであるため、その型のインスタンス メソッドと同じように呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-137">An extension method is a static method that can be associated with a type, so that it can be called as if it were an instance method on the type.</span></span> <span data-ttu-id="fe17d-138">この機能を使用すると、既存の型を実際に変更しなくても、その型に新しいメソッドを実質的に "追加" できます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-138">This feature enables you to, in effect, "add" new methods to existing types without actually modifying them.</span></span> <span data-ttu-id="fe17d-139">標準クエリ演算子は、<xref:System.Collections.Generic.IEnumerable%601> を実装する任意の型で LINQ クエリ機能を実現する拡張メソッドのセットです。</span><span class="sxs-lookup"><span data-stu-id="fe17d-139">The standard query operators are a set of extension methods that provide LINQ query functionality for any type that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span>

<span data-ttu-id="fe17d-140">詳細については、「[拡張メソッド](../../classes-and-structs/extension-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fe17d-140">For more information, see [Extension Methods](../../classes-and-structs/extension-methods.md).</span></span>

## <a name="lambda-expressions"></a><span data-ttu-id="fe17d-141">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="fe17d-141">Lambda Expressions</span></span>

<span data-ttu-id="fe17d-142">ラムダ式は、=> 演算子を使用して関数本体からパラメーター入力を分離するインライン関数で、コンパイル時にデリゲートまたは式ツリーに変換されます。</span><span class="sxs-lookup"><span data-stu-id="fe17d-142">A lambda expression is an inline function that uses the => operator to separate input parameters from the function body and can be converted at compile time to a delegate or an expression tree.</span></span> <span data-ttu-id="fe17d-143">LINQ プログラミングでは、標準クエリ演算子に対する直接メソッド呼び出しを行う場合にラムダ式を使用します。</span><span class="sxs-lookup"><span data-stu-id="fe17d-143">In LINQ programming, you will encounter lambda expressions when you make direct method calls to the standard query operators.</span></span>

<span data-ttu-id="fe17d-144">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="fe17d-144">For more information, see:</span></span>

- [<span data-ttu-id="fe17d-145">匿名関数</span><span class="sxs-lookup"><span data-stu-id="fe17d-145">Anonymous Functions</span></span>](../../statements-expressions-operators/anonymous-functions.md)

- [<span data-ttu-id="fe17d-146">ラムダ式</span><span class="sxs-lookup"><span data-stu-id="fe17d-146">Lambda Expressions</span></span>](../../../language-reference/operators/lambda-expressions.md)

- [<span data-ttu-id="fe17d-147">式ツリー (C#)</span><span class="sxs-lookup"><span data-stu-id="fe17d-147">Expression Trees (C#)</span></span>](../expression-trees/index.md)

## <a name="see-also"></a><span data-ttu-id="fe17d-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="fe17d-148">See also</span></span>

- [<span data-ttu-id="fe17d-149">統合言語クエリ (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="fe17d-149">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
