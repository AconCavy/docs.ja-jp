---
title: ADO.NET および LINQ to SQL
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49ac6da0-f2e1-46fa-963e-1b6dcb63fef7
ms.openlocfilehash: 4d2376a2e32ff099497a5dbcd6cb68d8ed526884
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980003"
---
# <a name="adonet-and-linq-to-sql"></a><span data-ttu-id="2abb9-102">ADO.NET および LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2abb9-102">ADO.NET and LINQ to SQL</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="2abb9-103">は、ADO.NET テクノロジ ファミリの一部です。</span><span class="sxs-lookup"><span data-stu-id="2abb9-103">is part of the ADO.NET family of technologies.</span></span> <span data-ttu-id="2abb9-104">ADO.NET プロバイダー モデルによって提供されるサービスが基になっています。</span><span class="sxs-lookup"><span data-stu-id="2abb9-104">It is based on services provided by the ADO.NET provider model.</span></span> <span data-ttu-id="2abb9-105">したがって、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のコードを既存の ADO.NET アプリケーションと混在させることができ、現在の ADO.NET ソリューションを [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] に移行できます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-105">You can therefore mix [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] code with existing ADO.NET applications and migrate current ADO.NET solutions to [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="2abb9-106">次の図は、この関係を高いレベルから見たものです。</span><span class="sxs-lookup"><span data-stu-id="2abb9-106">The following illustration provides a high-level view of the relationship.</span></span>  
  
 <span data-ttu-id="2abb9-107">![LINQ to SQL と ADO.NET](./media/dlinq-3.png "DLinq_3")</span><span class="sxs-lookup"><span data-stu-id="2abb9-107">![LINQ to SQL and ADO.NET](./media/dlinq-3.png "DLinq_3")</span></span>  
  
## <a name="connections"></a><span data-ttu-id="2abb9-108">接続</span><span class="sxs-lookup"><span data-stu-id="2abb9-108">Connections</span></span>  
 <span data-ttu-id="2abb9-109">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] の <xref:System.Data.Linq.DataContext> を作成するときに、既存の ADO.NET 接続を提供できます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-109">You can supply an existing ADO.NET connection when you create a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.DataContext>.</span></span> <span data-ttu-id="2abb9-110"><xref:System.Data.Linq.DataContext> に対するすべての操作 (クエリを含む) で、この提供した接続が使用されます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-110">All operations against the <xref:System.Data.Linq.DataContext> (including queries) use this provided connection.</span></span> <span data-ttu-id="2abb9-111">接続が既に開かれていた場合、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で使い終わった後も接続はそのままになります。</span><span class="sxs-lookup"><span data-stu-id="2abb9-111">If the connection is already open, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] leaves it as is when you are finished with it.</span></span>  
  
 [!code-csharp[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCommunicatingWithDatabase/cs/Program.cs#4)]
 [!code-vb[DLinqCommunicatingWithDatabase#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCommunicatingWithDatabase/vb/Module1.vb#4)]  
  
 <span data-ttu-id="2abb9-112">次のコードに示すとおり、<xref:System.Data.Linq.DataContext.Connection%2A> プロパティを使用して、いつでも接続にアクセスしたり、任意に閉じたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-112">You can always access the connection and close it yourself by using the <xref:System.Data.Linq.DataContext.Connection%2A> property, as in the following code:</span></span>  
  
 [!code-csharp[DLinqAdoNet#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#1)]
 [!code-vb[DLinqAdoNet#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#1)]  
  
## <a name="transactions"></a><span data-ttu-id="2abb9-113">トランザクション</span><span class="sxs-lookup"><span data-stu-id="2abb9-113">Transactions</span></span>  
 <span data-ttu-id="2abb9-114">既に独自のデータベース トランザクションを初期化していて、<xref:System.Data.Linq.DataContext> をトランザクションに使用する必要がある場合は、<xref:System.Data.Linq.DataContext> をトランザクションに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-114">You can supply your <xref:System.Data.Linq.DataContext> with your own database transaction when your application has already initiated the transaction and you want your <xref:System.Data.Linq.DataContext> to be involved.</span></span>  
  
 <span data-ttu-id="2abb9-115">.NET Framework でトランザクションを実行する場合は、<xref:System.Transactions.TransactionScope> オブジェクトの使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2abb9-115">The preferred method of doing transactions with the .NET Framework is to use the <xref:System.Transactions.TransactionScope> object.</span></span> <span data-ttu-id="2abb9-116">この方法を使うと、データベースと他のメモリ常駐リソース マネージャー間で動作する分散トランザクションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-116">By using this approach, you can make distributed transactions that work across databases and other memory-resident resource managers.</span></span> <span data-ttu-id="2abb9-117">トランザクション スコープは、わずかなリソースで開始されます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-117">Transaction scopes require few resources to start.</span></span> <span data-ttu-id="2abb9-118">トランザクションのスコープ内に複数の接続がある場合のみ、このトランザクションは分散トランザクションに昇格します。</span><span class="sxs-lookup"><span data-stu-id="2abb9-118">They promote themselves to distributed transactions only when there are multiple connections within the scope of the transaction.</span></span>  
  
 [!code-csharp[DLinqAdoNet#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#2)]
 [!code-vb[DLinqAdoNet#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#2)]  
  
 <span data-ttu-id="2abb9-119">この方法は、すべてのデータベースに使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="2abb9-119">You cannot use this approach for all databases.</span></span> <span data-ttu-id="2abb9-120">たとえば、SqlClient 接続を SQL Server 2000 サーバーに使用する場合、この接続はシステム トランザクションに昇格できません。</span><span class="sxs-lookup"><span data-stu-id="2abb9-120">For example, the SqlClient connection cannot promote system transactions when it works against a SQL Server 2000 server.</span></span> <span data-ttu-id="2abb9-121">代わりに、トランザクション スコープが使用されているときは、完全な分散トランザクションに自動的に参加します。</span><span class="sxs-lookup"><span data-stu-id="2abb9-121">Instead, it automatically enlists to a full, distributed transaction whenever it sees a transaction scope being used.</span></span>  
  
## <a name="direct-sql-commands"></a><span data-ttu-id="2abb9-122">直接 SQL コマンド</span><span class="sxs-lookup"><span data-stu-id="2abb9-122">Direct SQL Commands</span></span>  
 <span data-ttu-id="2abb9-123">ときには、クエリを実行したり変更内容を送信したりする <xref:System.Data.Linq.DataContext> 機能に不足があり、実行する必要がある特別なタスクを完了できないこともあります。</span><span class="sxs-lookup"><span data-stu-id="2abb9-123">At times you can encounter situations where the ability of the <xref:System.Data.Linq.DataContext> to query or submit changes is insufficient for the specialized task you want to perform.</span></span> <span data-ttu-id="2abb9-124">このような場合は、<xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドを使用して、SQL コマンドをデータベースに発行し、クエリ結果をオブジェクトに変換することができます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-124">In these circumstances you can use the <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method to issue SQL commands to the database and convert the query results to objects.</span></span>  
  
 <span data-ttu-id="2abb9-125">たとえば、`Customer` クラスのデータが 2 つのテーブル (customer1 および customer2) に含まれているとします。</span><span class="sxs-lookup"><span data-stu-id="2abb9-125">For example, assume that the data for the `Customer` class is spread over two tables (customer1 and customer2).</span></span> <span data-ttu-id="2abb9-126">次のクエリは `Customer` オブジェクトのシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="2abb9-126">The following query returns a sequence of `Customer` objects:</span></span>  
  
 [!code-csharp[DLinqAdoNet#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#3)]
 [!code-vb[DLinqAdoNet#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#3)]  
  
 <span data-ttu-id="2abb9-127">表形式の結果の列名がエンティティ クラスの列のプロパティと一致する限り、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] によって SQL クエリからオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-127">As long as the column names in the tabular results match column properties of your entity class, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] creates your objects out of any SQL query.</span></span>  
  
### <a name="parameters"></a><span data-ttu-id="2abb9-128">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2abb9-128">Parameters</span></span>  
 <span data-ttu-id="2abb9-129"><xref:System.Data.Linq.DataContext.ExecuteQuery%2A> メソッドは、パラメーターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="2abb9-129">The <xref:System.Data.Linq.DataContext.ExecuteQuery%2A> method accepts parameters.</span></span> <span data-ttu-id="2abb9-130">次のコードでは、パラメーター化されたクエリが実行されます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-130">The following code executes a parameterized query:</span></span>  
  
 [!code-csharp[DlinqAdoNet#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqAdoNet/cs/Program.cs#4)]
 [!code-vb[DlinqAdoNet#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqAdoNet/vb/Module1.vb#4)]  
  
> [!NOTE]
> <span data-ttu-id="2abb9-131">パラメーターは、`Console.WriteLine()` および `String.Format()` で使用されるものと同じ中かっこ表記でクエリ テキストに表現されます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-131">Parameters are expressed in the query text by using the same curly notation used by `Console.WriteLine()` and `String.Format()`.</span></span> <span data-ttu-id="2abb9-132">`String.Format()` は、指定されたクエリ文字列を受け取り、中かっこで囲まれたパラメーターを、`@p0`、`@p1` …、`@p(n)` などの、生成されたパラメーター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="2abb9-132">`String.Format()` takes the query string you provide and substitutes the curly-braced parameters with generated parameter names such as `@p0`, `@p1` …, `@p(n)`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2abb9-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="2abb9-133">See also</span></span>

- [<span data-ttu-id="2abb9-134">背景情報</span><span class="sxs-lookup"><span data-stu-id="2abb9-134">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="2abb9-135">方法: ADO.NET コマンドおよび DataContext 間の接続を再利用する</span><span class="sxs-lookup"><span data-stu-id="2abb9-135">How to: Reuse a Connection Between an ADO.NET Command and a DataContext</span></span>](how-to-reuse-a-connection-between-an-ado-net-command-and-a-datacontext.md)
