---
title: SQL Server と ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 6e88c35936de72f0d426c23493bbe5a08e707ee1
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979977"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="6ea01-102">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6ea01-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="6ea01-103">このセクションでは、.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) 固有の機能および動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="6ea01-104"><xref:System.Data.SqlClient> は SQL Server のバージョンへのアクセスを提供し、データベース固有のプロトコルをカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="6ea01-105">このデータ プロバイダーの機能は、OLE DB、ODBC、および Oracle に対する .NET Framework データ プロバイダーの機能と同等になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="6ea01-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="6ea01-106"><xref:System.Data.SqlClient> には、SQL Server と直接通信するための表形式データ ストリーム (TDS) パーサーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="6ea01-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ea01-107">.NET Framework Data Provider for SQL Server を使用するには、アプリケーションで <xref:System.Data.SqlClient> 名前空間を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6ea01-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ea01-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6ea01-108">In This Section</span></span>  
 [<span data-ttu-id="6ea01-109">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="6ea01-109">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="6ea01-110">SQL Server のセキュリティの概要を説明し、アプリケーションのシナリオを交えながら、SQL Server を対象とした安全な ADO.NET アプリケーションを作成するための指針を提供します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="6ea01-111">SQL Server データ型と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6ea01-111">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="6ea01-112">SQL Server のデータ型の操作方法、および .NET Framework データ型との相互作用について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="6ea01-113">SQL Server のバイナリ データと大きな値のデータ</span><span class="sxs-lookup"><span data-stu-id="6ea01-113">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="6ea01-114">SQL Server で大きな値のデータを扱う方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="6ea01-115">ADO.NET における SQL Server データ操作</span><span class="sxs-lookup"><span data-stu-id="6ea01-115">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="6ea01-116">SQL Server でのデータの操作方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="6ea01-117">一括コピー操作、MARS、非同期操作、およびテーブル値パラメーターに関するセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="6ea01-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="6ea01-118">SQL Server の機能と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="6ea01-118">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="6ea01-119">ADO.NET アプリケーション開発者にとって役立つ SQL Server の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="6ea01-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6ea01-120">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="6ea01-121">LINQ to SQL アプリケーションを作成するのに必要な基本的なビルド ブロック、プロセス、および手法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ea01-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="6ea01-122">SQL Server データベース エンジンの詳細なドキュメントについては、使用している SQL Server のバージョンに対応する SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ea01-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="6ea01-123">SQL Server オンライン ブック</span><span class="sxs-lookup"><span data-stu-id="6ea01-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="6ea01-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ea01-124">See also</span></span>

- [<span data-ttu-id="6ea01-125">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6ea01-125">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="6ea01-126">ADO.NET でのデータ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="6ea01-126">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="6ea01-127">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="6ea01-127">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="6ea01-128">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="6ea01-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="6ea01-129">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="6ea01-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
