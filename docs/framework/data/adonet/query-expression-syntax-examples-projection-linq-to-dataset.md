---
title: クエリ式の構文例:プロジェクション (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48c9f5ed-76bf-4228-ab10-5217bbb295a3
ms.openlocfilehash: e003c4356c2ab32814ac7a76ce008e21fb34192e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183170"
---
# <a name="query-expression-syntax-examples-projection--linq-to-dataset"></a><span data-ttu-id="7475a-102">クエリ式の構文例:プロジェクション (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="7475a-102">Query Expression Syntax Examples: Projection  (LINQ to DataSet)</span></span>

<span data-ttu-id="7475a-103">このトピックでは、<xref:System.Linq.Enumerable.Select%2A> メソッドおよび <xref:System.Linq.Enumerable.SelectMany%2A> メソッドで、クエリ式の構文を使って <xref:System.Data.DataSet> に対するクエリを実行する例を紹介しています。</span><span class="sxs-lookup"><span data-stu-id="7475a-103">The examples in this topic demonstrate how to use the <xref:System.Linq.Enumerable.Select%2A> and <xref:System.Linq.Enumerable.SelectMany%2A> methods to query a <xref:System.Data.DataSet> using the query expression syntax.</span></span>  
  
 <span data-ttu-id="7475a-104">これらの例で使用されている `FillDataSet` メソッドの指定については、「[DataSet へのデータの読み込み](loading-data-into-a-dataset.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7475a-104">The `FillDataSet` method used in these examples is specified in [Loading Data Into a DataSet](loading-data-into-a-dataset.md).</span></span>  
  
 <span data-ttu-id="7475a-105">このトピックの例には、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="7475a-105">The examples in this topic use the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="7475a-106">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="7475a-106">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP LINQ to DataSet Examples#ImportsUsing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#importsusing)]  
  
 <span data-ttu-id="7475a-107">詳細については、[Visual Studio で LINQ to DataSet プロジェクトを作成する](how-to-create-a-linq-to-dataset-project-in-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7475a-107">For more information, see [How to: Create a LINQ to DataSet Project In Visual Studio](how-to-create-a-linq-to-dataset-project-in-vs.md).</span></span>  
  
## <a name="select"></a><span data-ttu-id="7475a-108">選択</span><span class="sxs-lookup"><span data-stu-id="7475a-108">Select</span></span>  
  
### <a name="example"></a><span data-ttu-id="7475a-109">例</span><span class="sxs-lookup"><span data-stu-id="7475a-109">Example</span></span>  

 <span data-ttu-id="7475a-110">この例では、<xref:System.Linq.Enumerable.Select%2A> メソッドを使用して `Product` テーブルからすべての行を取得し、製品名を表示しています。</span><span class="sxs-lookup"><span data-stu-id="7475a-110">This example uses the <xref:System.Linq.Enumerable.Select%2A> method to return all the rows from the `Product` table and display the product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="example"></a><span data-ttu-id="7475a-111">例</span><span class="sxs-lookup"><span data-stu-id="7475a-111">Example</span></span>  

 <span data-ttu-id="7475a-112">この例では、<xref:System.Linq.Enumerable.Select%2A> を使用して、製品名のみのシーケンスを取得しています。</span><span class="sxs-lookup"><span data-stu-id="7475a-112">This example uses <xref:System.Linq.Enumerable.Select%2A> to return a sequence of only product names.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple2)]  
  
## <a name="selectmany"></a><span data-ttu-id="7475a-113">SelectMany</span><span class="sxs-lookup"><span data-stu-id="7475a-113">SelectMany</span></span>  
  
### <a name="example"></a><span data-ttu-id="7475a-114">例</span><span class="sxs-lookup"><span data-stu-id="7475a-114">Example</span></span>  

 <span data-ttu-id="7475a-115">この例では、`From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> と同等のメソッド) を使用して、`TotalDue` が 500.00 に満たないすべての注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="7475a-115">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where `TotalDue` is less than 500.00.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom)]  
  
### <a name="example"></a><span data-ttu-id="7475a-116">例</span><span class="sxs-lookup"><span data-stu-id="7475a-116">Example</span></span>  

 <span data-ttu-id="7475a-117">この例では、`From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> と同等のメソッド) を使用して、2002 年 10 月 1 日に受けたすべての注文を選択します。</span><span class="sxs-lookup"><span data-stu-id="7475a-117">This example uses `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order was made on October 1, 2002 or later.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanycompoundfrom2)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyCompoundFrom2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanycompoundfrom2)]  
  
### <a name="example"></a><span data-ttu-id="7475a-118">例</span><span class="sxs-lookup"><span data-stu-id="7475a-118">Example</span></span>  

 <span data-ttu-id="7475a-119">この例では、`From …, …` (<xref:System.Linq.Enumerable.SelectMany%2A> と同等のメソッド) を使用して、注文の合計が 10000.00 を超えるすべての注文を選択します。このとき、`From` 割り当てを使用して、合計を 2 回要求しないようにしています。</span><span class="sxs-lookup"><span data-stu-id="7475a-119">This example uses a `From …, …` (the equivalent of the <xref:System.Linq.Enumerable.SelectMany%2A> method) to select all orders where the order total is greater than 10000.00 and uses `From` assignment to avoid requesting the total twice.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectmanyfromassignment)]
 [!code-vb[DP LINQ to DataSet Examples#SelectManyFromAssignment](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectmanyfromassignment)]  
  
## <a name="see-also"></a><span data-ttu-id="7475a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="7475a-120">See also</span></span>

- [<span data-ttu-id="7475a-121">DataSet へのデータの読み込み</span><span class="sxs-lookup"><span data-stu-id="7475a-121">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
- [<span data-ttu-id="7475a-122">LINQ to DataSet の例</span><span class="sxs-lookup"><span data-stu-id="7475a-122">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="7475a-123">標準クエリ演算子の概要 (C#)</span><span class="sxs-lookup"><span data-stu-id="7475a-123">Standard Query Operators Overview (C#)</span></span>](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="7475a-124">標準クエリ演算子の概要 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7475a-124">Standard Query Operators Overview (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
