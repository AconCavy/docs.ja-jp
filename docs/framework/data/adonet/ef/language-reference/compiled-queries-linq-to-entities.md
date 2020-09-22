---
title: コンパイル済みクエリ (LINQ to Entities)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8025ba1d-29c7-4407-841b-d5a3bed40b7a
ms.openlocfilehash: f3270147f0cf38a646efac603f058173daa78547
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541136"
---
# <a name="compiled-queries--linq-to-entities"></a><span data-ttu-id="a6b16-102">コンパイル済みクエリ (LINQ to Entities)</span><span class="sxs-lookup"><span data-stu-id="a6b16-102">Compiled queries  (LINQ to Entities)</span></span>

<span data-ttu-id="a6b16-103">似たような構造のクエリを Entity Framework で何度も実行するアプリケーションがある場合は、クエリを一度コンパイルし、異なるパラメーターを指定して複数回実行することで、パフォーマンスを改善できる場合がよくあります。</span><span class="sxs-lookup"><span data-stu-id="a6b16-103">When you have an application that executes structurally similar queries many times in the Entity Framework, you can frequently increase performance by compiling the query one time and executing it several times with different parameters.</span></span> <span data-ttu-id="a6b16-104">たとえば、アプリケーションで特定の市区町村に住む顧客をすべて取得する必要がある場合は、ユーザーが実行時にフォーム内で市区町村を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-104">For example, an application might have to retrieve all the customers in a particular city; the city is specified at runtime by the user in a form.</span></span> <span data-ttu-id="a6b16-105">LINQ to Entities では、この目的のためにコンパイル済みクエリをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a6b16-105">LINQ to Entities supports using compiled queries for this purpose.</span></span>  
  
 <span data-ttu-id="a6b16-106">.NET Framework 4.5 以降では、LINQ クエリは自動的にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-106">Starting with .NET Framework 4.5, LINQ queries are cached automatically.</span></span> <span data-ttu-id="a6b16-107">ただし、引き続きコンパイル済み LINQ クエリを使用して後続の実行でさらにコストを削減できます。コンパイル済みクエリは、自動的にキャッシュされる LINQ クエリよりも効率的である場合があります。</span><span class="sxs-lookup"><span data-stu-id="a6b16-107">However, you can still use compiled LINQ queries to reduce this cost in later executions and compiled queries can be more efficient than LINQ queries that are automatically cached.</span></span> <span data-ttu-id="a6b16-108">メモリ内コレクションへ `Enumerable.Contains` 演算子を追加する LINQ to Entities クエリは自動的にキャッシュされません。</span><span class="sxs-lookup"><span data-stu-id="a6b16-108">LINQ to Entities queries that apply the `Enumerable.Contains` operator to in-memory collections are not automatically cached.</span></span> <span data-ttu-id="a6b16-109">また、コンパイル済み LINQ クエリのメモリ内コレクションをパラメーターで表すことは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="a6b16-109">Also, parameterizing in-memory collections in compiled LINQ queries is not allowed.</span></span>  
  
 <span data-ttu-id="a6b16-110"><xref:System.Data.Objects.CompiledQuery> クラスは、クエリをコンパイルおよびキャッシュして、再利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="a6b16-110">The <xref:System.Data.Objects.CompiledQuery> class provides compilation and caching of queries for reuse.</span></span> <span data-ttu-id="a6b16-111">このクラスには、概念上、<xref:System.Data.Objects.CompiledQuery> の `Compile` メソッドとその複数のオーバーロードが存在します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-111">Conceptually, this class contains a <xref:System.Data.Objects.CompiledQuery>'s `Compile` method with several overloads.</span></span> <span data-ttu-id="a6b16-112">`Compile` メソッドを呼び出すと、コンパイル済みクエリを表す新しいデリゲートを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-112">Call the `Compile` method to create a new delegate to represent the compiled query.</span></span> <span data-ttu-id="a6b16-113">`Compile` およびパラメーター値が指定された <xref:System.Data.Objects.ObjectContext> メソッドは、なんらかの結果 (<xref:System.Linq.IQueryable%601> インスタンスなど) をもたらすデリゲートを返します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-113">The `Compile` methods, provided with a <xref:System.Data.Objects.ObjectContext> and parameter values, return a delegate that produces some result (such as an <xref:System.Linq.IQueryable%601> instance).</span></span> <span data-ttu-id="a6b16-114">クエリは、初回実行時に 1 回だけコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-114">The query compiles once during only the first execution.</span></span> <span data-ttu-id="a6b16-115">コンパイル時にクエリに対して設定したマージ オプションは、後から変更できません。</span><span class="sxs-lookup"><span data-stu-id="a6b16-115">The merge options set for the query at the time of the compilation cannot be changed later.</span></span> <span data-ttu-id="a6b16-116">一度クエリがコンパイルされると、プリミティブ型のパラメーターを指定することだけはできますが、生成された SQL を変更するクエリの部分を置き換えることはできません。</span><span class="sxs-lookup"><span data-stu-id="a6b16-116">Once the query is compiled, you can only supply parameters of primitive type but you cannot replace parts of the query that would change the generated SQL.</span></span> <span data-ttu-id="a6b16-117">詳しくは、「[EF マージ オプションとコンパイル済みクエリ](/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a6b16-117">For more information, see [EF Merge Options and Compiled Queries](/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries).</span></span>
  
 <span data-ttu-id="a6b16-118"><xref:System.Data.Objects.CompiledQuery> の `Compile` メソッドによってコンパイルされる LINQ to Entities クエリの式は、<xref:System.Func%605> などのジェネリック `Func` デリゲートのいずれかによって表されます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-118">The LINQ to Entities query expression that the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method compiles is represented by one of the generic `Func` delegates, such as <xref:System.Func%605>.</span></span> <span data-ttu-id="a6b16-119">クエリ式は、最大で、`ObjectContext` パラメーター、戻りパラメーター、および 16 個のクエリ パラメーターをカプセル化できます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-119">At most, the query expression can encapsulate an `ObjectContext` parameter, a return parameter, and 16 query parameters.</span></span> <span data-ttu-id="a6b16-120">17 個以上のクエリ パラメーターが必要な場合は、クエリ パラメーターを表すプロパティを持つ構造体を作成できます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-120">If more than 16 query parameters are required, you can create a structure whose properties represent query parameters.</span></span> <span data-ttu-id="a6b16-121">次に、その構造体のプロパティを設定した後、それらのプロパティをクエリ式で使用できます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-121">You can then use the properties on the structure in the query expression after you set the properties.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="a6b16-122">例 1</span><span class="sxs-lookup"><span data-stu-id="a6b16-122">Example 1</span></span>  
 <span data-ttu-id="a6b16-123">次の例では、入力パラメーターとして <xref:System.Decimal> を受け取り、合計支払額が $200.00 以上である一連の注文を返すクエリをコンパイルして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-123">The following example compiles and then invokes a query that accepts a <xref:System.Decimal> input parameter and returns a sequence of orders where the total due is greater than or equal to $200.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query 2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery2)]
 [!code-vb[DP L2E Conceptual Examples - compiled query2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery2)]  
  
## <a name="example-2"></a><span data-ttu-id="a6b16-124">例 2</span><span class="sxs-lookup"><span data-stu-id="a6b16-124">Example 2</span></span>  
 <span data-ttu-id="a6b16-125">次の例では、<xref:System.Data.Objects.ObjectQuery%601> のインスタンスを返すクエリをコンパイルして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-125">The following example compiles and then invokes a query that returns an <xref:System.Data.Objects.ObjectQuery%601> instance:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery1_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery1_mq)]  
  
## <a name="example-3"></a><span data-ttu-id="a6b16-126">例 3</span><span class="sxs-lookup"><span data-stu-id="a6b16-126">Example 3</span></span>  
 <span data-ttu-id="a6b16-127">次の例では、製品の定価の平均を <xref:System.Decimal> 値として返すクエリをコンパイルして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-127">The following example compiles and then invokes a query that returns the average of the product list prices as a <xref:System.Decimal> value:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery3_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery3_mq)]  
  
## <a name="example-4"></a><span data-ttu-id="a6b16-128">例 4</span><span class="sxs-lookup"><span data-stu-id="a6b16-128">Example 4</span></span>  
 <span data-ttu-id="a6b16-129">次の例では、入力パラメーターとして <xref:System.String> を受け取り、指定された文字列でメール アドレスが始まる `Contact` を返すクエリをコンパイルして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-129">The following example compiles and then invokes a query that accepts a <xref:System.String> input parameter and then returns a `Contact` whose email address starts with the specified string:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query4_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery4_mq)]
 [!code-vb[DP L2E Conceptual Examples - compiled query4_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery4_mq)]  
  
## <a name="example-5"></a><span data-ttu-id="a6b16-130">例 5</span><span class="sxs-lookup"><span data-stu-id="a6b16-130">Example 5</span></span>  
 <span data-ttu-id="a6b16-131">次の例では、入力パラメーターとして <xref:System.DateTime> および <xref:System.Decimal> を受け取り、注文日が 2003 年 3 月 8 日より遅く合計支払額が $300.00 未満である一連の注文を返すクエリをコンパイルして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-131">The following example compiles and then invokes a query that accepts <xref:System.DateTime> and <xref:System.Decimal> input parameters and returns a sequence of orders where the order date is later than March 8, 2003, and the total due is less than $300.00:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery5)]
 [!code-vb[DP L2E Conceptual Examples - compiled query5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery5)]  
  
## <a name="example-6"></a><span data-ttu-id="a6b16-132">例 6</span><span class="sxs-lookup"><span data-stu-id="a6b16-132">Example 6</span></span>  
 <span data-ttu-id="a6b16-133">次の例では、入力パラメーターとして <xref:System.DateTime> を受け取り、注文日が 2004 年 3 月 8 日より遅い一連の注文を返すクエリをコンパイルして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-133">The following example compiles and then invokes a query that accepts a <xref:System.DateTime> input parameter and returns a sequence of orders where the order date is later than March 8, 2004.</span></span> <span data-ttu-id="a6b16-134">このクエリは、注文情報を一連の匿名型として返します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-134">This query returns the order information as a sequence of anonymous types.</span></span> <span data-ttu-id="a6b16-135">匿名型はコンパイラによって推論されるので、型パラメーターを <xref:System.Data.Objects.CompiledQuery> の `Compile` メソッドに指定することはできず、型はクエリ自体で定義されます。</span><span class="sxs-lookup"><span data-stu-id="a6b16-135">Anonymous types are inferred by the compiler, so you cannot specify type parameters in the <xref:System.Data.Objects.CompiledQuery>'s `Compile` method and the type is defined in the query itself.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery6)]
 [!code-vb[DP L2E Conceptual Examples - compiled query6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery6)]  
  
## <a name="example-7"></a><span data-ttu-id="a6b16-136">例 7</span><span class="sxs-lookup"><span data-stu-id="a6b16-136">Example 7</span></span>  
 <span data-ttu-id="a6b16-137">次の例では、入力パラメーターとしてユーザー定義の構造体を受け取り、一連の注文を返すクエリをコンパイルして呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-137">The following example compiles and then invokes a query that accepts a user-defined structure input parameter and returns a sequence of orders.</span></span> <span data-ttu-id="a6b16-138">この構造体では開始日、終了日、合計支払額のクエリ パラメーターを定義しており、クエリは、2003 年 3 月 3 日から 3 月 8 日までに出荷された、合計支払額が $700.00 を超える注文を返します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-138">The structure defines start date, end date, and total due query parameters, and the query returns orders shipped between March 3 and March 8, 2003 with a total due greater than $700.00.</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - compiled query7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#compiledquery7)]
 [!code-vb[DP L2E Conceptual Examples - compiled query7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#compiledquery7)]  
  
 <span data-ttu-id="a6b16-139">クエリ パラメーターを定義する構造体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="a6b16-139">The structure that defines the query parameters:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples - MyParamsStruct](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myparamsstruct)]
 [!code-vb[DP L2E Conceptual Examples - MyParamsStruct](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myparamsstruct)]  
  
## <a name="see-also"></a><span data-ttu-id="a6b16-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6b16-140">See also</span></span>

- [<span data-ttu-id="a6b16-141">ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="a6b16-141">ADO.NET Entity Framework</span></span>](../index.md)
- [<span data-ttu-id="a6b16-142">LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="a6b16-142">LINQ to Entities</span></span>](linq-to-entities.md)
- [<span data-ttu-id="a6b16-143">EF マージ オプションとコンパイル済みクエリ</span><span class="sxs-lookup"><span data-stu-id="a6b16-143">EF Merge Options and Compiled Queries</span></span>](/archive/blogs/dsimmons/ef-merge-options-and-compiled-queries)
