---
title: SqlTypes と DataSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9172c20a-9876-4b3b-9c97-1963c02b1993
ms.openlocfilehash: dea5a2017479443cb747d31e253c1c83585ddd09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791493"
---
# <a name="sqltypes-and-the-dataset"></a><span data-ttu-id="c9066-102">SqlTypes と DataSet</span><span class="sxs-lookup"><span data-stu-id="c9066-102">SqlTypes and the DataSet</span></span>
<span data-ttu-id="c9066-103">ADO.NET 2.0 では、`DataSet` 名前空間を介した <xref:System.Data.SqlTypes> の型のサポートが拡張されました。</span><span class="sxs-lookup"><span data-stu-id="c9066-103">ADO.NET 2.0 introduced enhanced type support for the `DataSet` through the  <xref:System.Data.SqlTypes> namespace.</span></span> <span data-ttu-id="c9066-104"><xref:System.Data.SqlTypes> の型は、SQL Server データベースのデータ型と同じセマンティクスおよび精度を持つデータ型を提供することを目的にデザインされています。</span><span class="sxs-lookup"><span data-stu-id="c9066-104">The types in <xref:System.Data.SqlTypes> are designed to provide data types with the same semantics and precision as the data types in a SQL Server database.</span></span> <span data-ttu-id="c9066-105"><xref:System.Data.SqlTypes> の個々のデータ型には、それに相当する SQL Server のデータ型があり、基本となるデータ表現はいずれも同じです。</span><span class="sxs-lookup"><span data-stu-id="c9066-105">Each data type in <xref:System.Data.SqlTypes> has an equivalent data type in SQL Server, with the same underlying data representation.</span></span>  
  
 <span data-ttu-id="c9066-106"><xref:System.Data.DataSet> で <xref:System.Data.SqlTypes> を直接使用すると、SQL Server データ型を操作する際にいくつかの利点があります。</span><span class="sxs-lookup"><span data-stu-id="c9066-106">Using <xref:System.Data.SqlTypes> directly in a <xref:System.Data.DataSet> confers several benefits when working with SQL Server data types.</span></span> <span data-ttu-id="c9066-107"><xref:System.Data.SqlTypes> では、SQL Server ネイティブのデータ型と同じセマンティクスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c9066-107"><xref:System.Data.SqlTypes> supports the same semantics as SQL Server native data types.</span></span> <span data-ttu-id="c9066-108"><xref:System.Data.SqlTypes> の定義でいずれかの <xref:System.Data.DataColumn> を指定することで、decimal データ型または numeric データ型をいずれかの共通言語ランタイム (CLR) データ型に変換するときの精度の低下を防止します。</span><span class="sxs-lookup"><span data-stu-id="c9066-108">Specifying one of the <xref:System.Data.SqlTypes> in the definition of a <xref:System.Data.DataColumn> eliminates the loss of precision that can occur when converting decimal or numeric data types to one of the common language runtime (CLR) data types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9066-109">例</span><span class="sxs-lookup"><span data-stu-id="c9066-109">Example</span></span>  
 <span data-ttu-id="c9066-110">次の例では、<xref:System.Data.DataTable> オブジェクトを作成し、CLR データ型の代わりに <xref:System.Data.DataColumn> を使用して、<xref:System.Data.SqlTypes> のデータ型を明示的に定義します。</span><span class="sxs-lookup"><span data-stu-id="c9066-110">The following example creates a <xref:System.Data.DataTable> object, explicitly defining the <xref:System.Data.DataColumn> data types by using <xref:System.Data.SqlTypes> instead of CLR types.</span></span> <span data-ttu-id="c9066-111">このコードは、SQL Server の AdventureWorks データベースの Sales.SalesOrderDetail テーブルから取得されたデータを <xref:System.Data.DataTable> に挿入します。</span><span class="sxs-lookup"><span data-stu-id="c9066-111">The code fills the <xref:System.Data.DataTable> with data from the Sales.SalesOrderDetail table in the AdventureWorks database in SQL Server.</span></span> <span data-ttu-id="c9066-112">コンソール ウィンドウには、各列のデータ型および SQL Server から取得された値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="c9066-112">The output displayed in the console window shows the data type of each column, and the values retrieved from SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.GetTypeAW#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.GetTypeAW/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c9066-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c9066-113">See also</span></span>

- [<span data-ttu-id="c9066-114">SQL Server データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="c9066-114">SQL Server Data Type Mappings</span></span>](../sql-server-data-type-mappings.md)
- [<span data-ttu-id="c9066-115">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="c9066-115">Configuring Parameters and Parameter Data Types</span></span>](../configuring-parameters-and-parameter-data-types.md)
- [<span data-ttu-id="c9066-116">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c9066-116">ADO.NET Overview</span></span>](../ado-net-overview.md)
