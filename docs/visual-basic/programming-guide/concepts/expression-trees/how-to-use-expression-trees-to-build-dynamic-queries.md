---
title: '方法: 式ツリーを使用して動的クエリをビルドする'
ms.date: 07/20/2015
ms.assetid: 16278787-7532-4b65-98b2-7a412406c4ee
ms.openlocfilehash: 1f686c37b5d04263ac5ae0dd6883aa8a519ed19e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410980"
---
# <a name="how-to-use-expression-trees-to-build-dynamic-queries-visual-basic"></a><span data-ttu-id="665b7-102">方法: 式ツリーを使用して動的クエリをビルドする (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="665b7-102">How to: Use Expression Trees to Build Dynamic Queries (Visual Basic)</span></span>

<span data-ttu-id="665b7-103">LINQ では、<xref:System.Linq.IQueryable%601> を実装するデータ ソースをターゲットとする構造化されたクエリを表すために、式ツリーが使われます。</span><span class="sxs-lookup"><span data-stu-id="665b7-103">In LINQ, expression trees are used to represent structured queries that target sources of data that implement <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="665b7-104">たとえば、LINQ プロバイダーは、リレーショナル データ ストアのクエリを行うために、<xref:System.Linq.IQueryable%601> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="665b7-104">For example, the LINQ provider implements the <xref:System.Linq.IQueryable%601> interface for querying relational data stores.</span></span> <span data-ttu-id="665b7-105">Visual Basic コンパイラは、このようなデータ ソースをターゲットとするクエリをコンパイルして、実行時に式ツリーを作成するコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="665b7-105">The Visual Basic compiler compiles queries that target such data sources into code that builds an expression tree at runtime.</span></span> <span data-ttu-id="665b7-106">クエリ プロバイダーは式ツリー データ構造を走査して、データ ソースに適したクエリ言語に変換できます。</span><span class="sxs-lookup"><span data-stu-id="665b7-106">The query provider can then traverse the expression tree data structure and translate it into a query language appropriate for the data source.</span></span>

<span data-ttu-id="665b7-107">LINQ では、<xref:System.Linq.Expressions.Expression%601> 型の変数に代入されるラムダ式を表すためにも、式ツリーが使われます。</span><span class="sxs-lookup"><span data-stu-id="665b7-107">Expression trees are also used in LINQ to represent lambda expressions that are assigned to variables of type <xref:System.Linq.Expressions.Expression%601>.</span></span>

<span data-ttu-id="665b7-108">このトピックでは、式ツリーを使って動的な LINQ クエリを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="665b7-108">This topic describes how to use expression trees to create dynamic LINQ queries.</span></span> <span data-ttu-id="665b7-109">動的クエリは、コンパイル時にクエリの詳細がわからない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="665b7-109">Dynamic queries are useful when the specifics of a query are not known at compile time.</span></span> <span data-ttu-id="665b7-110">たとえば、データをフィルター処理するための述語をエンド ユーザーが指定できるユーザー インターフェイスをアプリケーションで提供することがあります。</span><span class="sxs-lookup"><span data-stu-id="665b7-110">For example, an application might provide a user interface that enables the end user to specify one or more predicates to filter the data.</span></span> <span data-ttu-id="665b7-111">クエリに LINQ を使うには、このようなアプリケーションでは式ツリーを使って実行時に LINQ クエリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="665b7-111">In order to use LINQ for querying, this kind of application must use expression trees to create the LINQ query at runtime.</span></span>

## <a name="example"></a><span data-ttu-id="665b7-112">例</span><span class="sxs-lookup"><span data-stu-id="665b7-112">Example</span></span>

<span data-ttu-id="665b7-113">次の例では、式ツリーを使って `IQueryable` データ ソースに対するクエリを作成して実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="665b7-113">The following example shows you how to use expression trees to construct a query against an `IQueryable` data source and then execute it.</span></span> <span data-ttu-id="665b7-114">このコードは、次のクエリを表す式ツリーを作成します。</span><span class="sxs-lookup"><span data-stu-id="665b7-114">The code builds an expression tree to represent the following query:</span></span>

`companies.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16).OrderBy(Function(company) company)`

<span data-ttu-id="665b7-115">クエリ全体を構成する式を表す式ツリーの作成には、<xref:System.Linq.Expressions> 名前空間のファクトリ メソッドが使われます。</span><span class="sxs-lookup"><span data-stu-id="665b7-115">The factory methods in the <xref:System.Linq.Expressions> namespace are used to create expression trees that represent the expressions that make up the overall query.</span></span> <span data-ttu-id="665b7-116">標準クエリ演算子メソッドの呼び出しを表す式は、これらのメソッドの <xref:System.Linq.Queryable> の実装を参照します。</span><span class="sxs-lookup"><span data-stu-id="665b7-116">The expressions that represent calls to the standard query operator methods refer to the <xref:System.Linq.Queryable> implementations of these methods.</span></span> <span data-ttu-id="665b7-117">最終的な式ツリーが、`IQueryable` データ ソースのプロバイダーの <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> 実装に渡されて、`IQueryable` 型の実行可能なクエリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="665b7-117">The final expression tree is passed to the <xref:System.Linq.IQueryProvider.CreateQuery%60%601%28System.Linq.Expressions.Expression%29> implementation of the provider of the `IQueryable` data source to create an executable query of type `IQueryable`.</span></span> <span data-ttu-id="665b7-118">結果は、そのクエリ変数を列挙することにより取得されます。</span><span class="sxs-lookup"><span data-stu-id="665b7-118">The results are obtained by enumerating that query variable.</span></span>

```vb
' Add an Imports statement for System.Linq.Expressions.

Dim companies =
    {"Consolidated Messenger", "Alpine Ski House", "Southridge Video", "City Power & Light",
     "Coho Winery", "Wide World Importers", "Graphic Design Institute", "Adventure Works",
     "Humongous Insurance", "Woodgrove Bank", "Margie's Travel", "Northwind Traders",
     "Blue Yonder Airlines", "Trey Research", "The Phone Company",
     "Wingtip Toys", "Lucerne Publishing", "Fourth Coffee"}

' The IQueryable data to query.
Dim queryableData As IQueryable(Of String) = companies.AsQueryable()

' Compose the expression tree that represents the parameter to the predicate.
Dim pe As ParameterExpression = Expression.Parameter(GetType(String), "company")

' ***** Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16) *****
' Create an expression tree that represents the expression: company.ToLower() = "coho winery".
Dim left As Expression = Expression.Call(pe, GetType(String).GetMethod("ToLower", System.Type.EmptyTypes))
Dim right As Expression = Expression.Constant("coho winery")
Dim e1 As Expression = Expression.Equal(left, right)

' Create an expression tree that represents the expression: company.Length > 16.
left = Expression.Property(pe, GetType(String).GetProperty("Length"))
right = Expression.Constant(16, GetType(Integer))
Dim e2 As Expression = Expression.GreaterThan(left, right)

' Combine the expressions to create an expression tree that represents the
' expression: company.ToLower() = "coho winery" OrElse company.Length > 16).
Dim predicateBody As Expression = Expression.OrElse(e1, e2)

' Create an expression tree that represents the expression:
' queryableData.Where(Function(company) company.ToLower() = "coho winery" OrElse company.Length > 16)
Dim whereCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "Where",
        New Type() {queryableData.ElementType},
        queryableData.Expression,
        Expression.Lambda(Of Func(Of String, Boolean))(predicateBody, New ParameterExpression() {pe}))
' ***** End Where *****

' ***** OrderBy(Function(company) company) *****
' Create an expression tree that represents the expression:
' whereCallExpression.OrderBy(Function(company) company)
Dim orderByCallExpression As MethodCallExpression = Expression.Call(
        GetType(Queryable),
        "OrderBy",
        New Type() {queryableData.ElementType, queryableData.ElementType},
        whereCallExpression,
        Expression.Lambda(Of Func(Of String, String))(pe, New ParameterExpression() {pe}))
' ***** End OrderBy *****

' Create an executable query from the expression tree.
Dim results As IQueryable(Of String) = queryableData.Provider.CreateQuery(Of String)(orderByCallExpression)

' Enumerate the results.
For Each company As String In results
    Console.WriteLine(company)
Next

' This code produces the following output:
'
' Blue Yonder Airlines
' City Power & Light
' Coho Winery
' Consolidated Messenger
' Graphic Design Institute
' Humongous Insurance
' Lucerne Publishing
' Northwind Traders
' The Phone Company
' Wide World Importers
```

<span data-ttu-id="665b7-119">このコードでは、`Queryable.Where` メソッドに渡される述語で固定数の式を使います。</span><span class="sxs-lookup"><span data-stu-id="665b7-119">This code uses a fixed number of expressions in the predicate that is passed to the `Queryable.Where` method.</span></span> <span data-ttu-id="665b7-120">ただし、ユーザー入力に依存する可変個の述語式を結合するアプリケーションを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="665b7-120">However, you can write an application that combines a variable number of predicate expressions that depends on the user input.</span></span> <span data-ttu-id="665b7-121">また、ユーザーからの入力に応じて、クエリで呼び出される標準クエリ演算子を変えることもできます。</span><span class="sxs-lookup"><span data-stu-id="665b7-121">You can also vary the standard query operators that are called in the query, depending on the input from the user.</span></span>

## <a name="compile-the-code"></a><span data-ttu-id="665b7-122">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="665b7-122">Compile the code</span></span>

- <span data-ttu-id="665b7-123">新しい**コンソール アプリケーション** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="665b7-123">Create a new **Console Application** project.</span></span>

- <span data-ttu-id="665b7-124">System.Linq.Expressions 名前空間をインクルードします。</span><span class="sxs-lookup"><span data-stu-id="665b7-124">Include the System.Linq.Expressions namespace.</span></span>

- <span data-ttu-id="665b7-125">例のコードをコピーして、`Main` `Sub` プロシージャに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="665b7-125">Copy the code from the example and paste it into the `Main` `Sub` procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="665b7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="665b7-126">See also</span></span>

- [<span data-ttu-id="665b7-127">式ツリー (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="665b7-127">Expression Trees (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="665b7-128">方法: 式ツリーを実行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="665b7-128">How to: Execute Expression Trees (Visual Basic)</span></span>](how-to-execute-expression-trees.md)
