---
title: クエリ式の構文例:フィルター処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c27cb89c-1c1d-4988-9f38-950eda3cb275
ms.openlocfilehash: 4ce4e28df3a09ddf718b000725afb0c9125bdd77
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397114"
---
# <a name="query-expression-syntax-examples-filtering"></a><span data-ttu-id="b0b5b-102">クエリ式の構文例:フィルター処理</span><span class="sxs-lookup"><span data-stu-id="b0b5b-102">Query Expression Syntax Examples: Filtering</span></span>
<span data-ttu-id="b0b5b-103">このトピックでは、クエリ式構文で、`Where` メソッドおよび `Where…Contains` メソッドを使用して、[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) を照会する例を取り上げます。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-103">The examples in this topic demonstrate how to use the `Where` and `Where…Contains` methods to query the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) using query expression syntax.</span></span> <span data-ttu-id="b0b5b-104">Where…`Contains`</span><span class="sxs-lookup"><span data-stu-id="b0b5b-104">Note, Where…`Contains`</span></span> <span data-ttu-id="b0b5b-105">を[コンパイル済みクエリ](compiled-queries-linq-to-entities.md)の一部として使用することはできないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-105">cannot be used as a part of a [compiled query](compiled-queries-linq-to-entities.md).</span></span>  
  
 <span data-ttu-id="b0b5b-106">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-106">The AdventureWorks Sales model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="b0b5b-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a><span data-ttu-id="b0b5b-108">Where</span><span class="sxs-lookup"><span data-stu-id="b0b5b-108">Where</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0b5b-109">例</span><span class="sxs-lookup"><span data-stu-id="b0b5b-109">Example</span></span>  
 <span data-ttu-id="b0b5b-110">次の例では、すべてのオンライン注文が返されます。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-110">The following example returns all online orders.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1)]
 [!code-vb[DP L2E Examples#Where1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1)]  
  
### <a name="example"></a><span data-ttu-id="b0b5b-111">例</span><span class="sxs-lookup"><span data-stu-id="b0b5b-111">Example</span></span>  
 <span data-ttu-id="b0b5b-112">次の例では、注文数量が 3 個以上で 5 個以下の注文が返されます。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-112">The following example returns the orders where the order quantity is greater than 2 and less than 6.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2)]
 [!code-vb[DP L2E Examples#Where2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2)]  
  
### <a name="example"></a><span data-ttu-id="b0b5b-113">例</span><span class="sxs-lookup"><span data-stu-id="b0b5b-113">Example</span></span>  
 <span data-ttu-id="b0b5b-114">次の例では、色が赤の製品がすべて返されます。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-114">The following example returns all red colored products.</span></span>  
  
 [!code-csharp[DP L2E Examples#Where3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3)]
 [!code-vb[DP L2E Examples#Where3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3)]  
  
### <a name="example"></a><span data-ttu-id="b0b5b-115">例</span><span class="sxs-lookup"><span data-stu-id="b0b5b-115">Example</span></span>  
 <span data-ttu-id="b0b5b-116">次の例では、`Where` メソッドを使用して、2003 年 12 月 1 日以降に受けた注文を検索します。次に、`order.SalesOrderDetail` ナビゲーション プロパティを使用して、各注文の詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-116">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="wherecontains"></a><span data-ttu-id="b0b5b-117">Where…Contains</span><span class="sxs-lookup"><span data-stu-id="b0b5b-117">Where…Contains</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0b5b-118">例</span><span class="sxs-lookup"><span data-stu-id="b0b5b-118">Example</span></span>  
 <span data-ttu-id="b0b5b-119">次の例では、配列を `Where…Contains` 句の一部として使用し、その配列内の値と一致する `ProductModelID` を持つすべての製品を検出します。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-119">The following example uses an array as part of a `Where…Contains` clause to find all products that have a `ProductModelID` that matches a value in the array.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#1)]
 [!code-vb[DP L2E ArraysAndListsInQueries#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="b0b5b-120">`Where…Contains` 句の述語として、<xref:System.Array>、<xref:System.Collections.Generic.List%601>、または <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装する任意の型のコレクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-120">As part of the predicate in a `Where…Contains` clause, you can use an <xref:System.Array>, a <xref:System.Collections.Generic.List%601>, or a collection of any type that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="b0b5b-121">さらに、LINQ to Entities クエリ内でコレクションを宣言および初期化できます。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-121">You can also declare and initialize a collection within a LINQ to Entities query.</span></span> <span data-ttu-id="b0b5b-122">詳細については、次の例を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-122">See the next example for more information.</span></span>  
  
### <a name="example"></a><span data-ttu-id="b0b5b-123">例</span><span class="sxs-lookup"><span data-stu-id="b0b5b-123">Example</span></span>  
 <span data-ttu-id="b0b5b-124">次の例では、`Where…Contains` 句で配列を宣言および初期化し、その配列内の値と一致する `ProductModelID` または `Size` を持つすべての製品を検出します。</span><span class="sxs-lookup"><span data-stu-id="b0b5b-124">The following example declares and initializes arrays in a `Where…Contains` clause to find all products that have a `ProductModelID` or `Size` that match values in the arrays.</span></span>  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#2)]
 [!code-vb[DP L2E ArraysAndListsInQueries#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="b0b5b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0b5b-125">See also</span></span>

- [<span data-ttu-id="b0b5b-126">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="b0b5b-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
