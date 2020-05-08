---
title: Oracle および ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8ee8e389-53cf-45cf-80bd-1df63ef34f2e
ms.openlocfilehash: 5683f2b4ba57021ff6dda3a51baca016f886b605
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980081"
---
# <a name="oracle-and-adonet"></a><span data-ttu-id="11db2-102">Oracle および ADO.NET</span><span class="sxs-lookup"><span data-stu-id="11db2-102">Oracle and ADO.NET</span></span>
> [!NOTE]
> <span data-ttu-id="11db2-103"><xref:System.Data.OracleClient> の型は非推奨になっています。</span><span class="sxs-lookup"><span data-stu-id="11db2-103">The types in <xref:System.Data.OracleClient> are deprecated.</span></span> <span data-ttu-id="11db2-104">これらの型は、.NET Framework の現在のバージョンでは引き続きサポートされていますが、今後のリリースでは削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="11db2-104">The types remain supported in the current version of.NET Framework but will be removed in a future release.</span></span> <span data-ttu-id="11db2-105">サードパーティの Oracle プロバイダーを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="11db2-105">Microsoft recommends that you use a third-party Oracle provider.</span></span>  
  
 <span data-ttu-id="11db2-106">このセクションでは、.NET Framework Data Provider for Oracle 固有の機能および動作について説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-106">This section describes features and behaviors that are specific to the .NET Framework Data Provider for Oracle.</span></span>  
  
 <span data-ttu-id="11db2-107">.NET Framework Data Provider for Oracle では、Oracle Client ソフトウェアとして提供されている Oracle Call Interface (OCI) を使用して Oracle データベースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="11db2-107">The .NET Framework Data Provider for Oracle provides access to an Oracle database using the Oracle Call Interface (OCI) as provided by Oracle Client software.</span></span> <span data-ttu-id="11db2-108">このデータ プロバイダーの機能は、SQL Server、OLE DB、ODBC に対する .NET Framework データ プロバイダーの機能と同等になるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="11db2-108">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for SQL Server, OLE DB, and ODBC.</span></span>  
  
 <span data-ttu-id="11db2-109">.NET Framework Data Provider for Oracle を使用するには、アプリケーションで以下のように <xref:System.Data.OracleClient> 名前空間を参照する必要があります。</span><span class="sxs-lookup"><span data-stu-id="11db2-109">To use the .NET Framework Data Provider for Oracle, an application must reference the <xref:System.Data.OracleClient> namespace as follows:</span></span>  
  
```vb  
Imports System.Data.OracleClient  
```  
  
```csharp  
using System.Data.OracleClient;  
```  
  
 <span data-ttu-id="11db2-110">コードをコンパイルするには、DLL への参照も必要です。</span><span class="sxs-lookup"><span data-stu-id="11db2-110">You also must include a reference to the DLL when you compile your code.</span></span> <span data-ttu-id="11db2-111">たとえば、C# プログラムをコンパイルする場合、コマンド ラインに以下のコードを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="11db2-111">For example, if you are compiling a C# program, your command line should include:</span></span>  
  
```console
csc /r:System.Data.OracleClient.dll  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="11db2-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="11db2-112">In This Section</span></span>  
 [<span data-ttu-id="11db2-113">システム要件</span><span class="sxs-lookup"><span data-stu-id="11db2-113">System Requirements</span></span>](system-requirements-for-the-dotnet-data-provider-for-oracle.md)  
 <span data-ttu-id="11db2-114">.NET Framework Data Provider for Oracle を使用するための要件を説明し、その際に知っておくべきさまざまなことについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-114">Describes requirements for using the .NET Framework Data Provider for Oracle, and describes a number of issues to be aware when using it.</span></span>  
  
 [<span data-ttu-id="11db2-115">Oracle BFILE</span><span class="sxs-lookup"><span data-stu-id="11db2-115">Oracle BFILEs</span></span>](oracle-bfiles.md)  
 <span data-ttu-id="11db2-116"><xref:System.Data.OracleClient.OracleBFile> クラスについて説明します。このクラスは、Oracle BFILE データ型を操作するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="11db2-116">Describes the <xref:System.Data.OracleClient.OracleBFile> class, which is used to work with the Oracle BFILE data type.</span></span>  
  
 [<span data-ttu-id="11db2-117">Oracle LOB</span><span class="sxs-lookup"><span data-stu-id="11db2-117">Oracle LOBs</span></span>](oracle-lobs.md)  
 <span data-ttu-id="11db2-118"><xref:System.Data.OracleClient.OracleLob> クラスについて説明します。このクラスは、Oracle LOB データ型を操作するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="11db2-118">Describes the <xref:System.Data.OracleClient.OracleLob> class, which is used to work with Oracle LOB data types.</span></span>  
  
 [<span data-ttu-id="11db2-119">Oracle REF CURSOR</span><span class="sxs-lookup"><span data-stu-id="11db2-119">Oracle REF CURSORs</span></span>](oracle-ref-cursors.md)  
 <span data-ttu-id="11db2-120">Oracle REF CURSOR データ型のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-120">Describes support for the Oracle REF CURSOR data type.</span></span>  
  
 [<span data-ttu-id="11db2-121">OracleTypes</span><span class="sxs-lookup"><span data-stu-id="11db2-121">OracleTypes</span></span>](oracletypes.md)  
 <span data-ttu-id="11db2-122"><xref:System.Data.OracleClient.OracleNumber> や <xref:System.Data.OracleClient.OracleString> など、Oracle データ型を操作するために使用する構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-122">Describes structures you can use to work with Oracle data types, including <xref:System.Data.OracleClient.OracleNumber> and <xref:System.Data.OracleClient.OracleString>.</span></span>  
  
 [<span data-ttu-id="11db2-123">Oracle シーケンス</span><span class="sxs-lookup"><span data-stu-id="11db2-123">Oracle Sequences</span></span>](oracle-sequences.md)  
 <span data-ttu-id="11db2-124">サーバーによって生成されたキー値 (Oracle シーケンス) を取得するためのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-124">Describes support for retrieving the server-generated key Oracle Sequence values.</span></span>  
  
 [<span data-ttu-id="11db2-125">Oracle データ型のマッピング</span><span class="sxs-lookup"><span data-stu-id="11db2-125">Oracle Data Type Mappings</span></span>](oracle-data-type-mappings.md)  
 <span data-ttu-id="11db2-126">Oracle データ型およびその <xref:System.Data.OracleClient.OracleDataReader> へのマップを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="11db2-126">Lists Oracle data types and their mappings to the <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 [<span data-ttu-id="11db2-127">Oracle 分散トランザクション</span><span class="sxs-lookup"><span data-stu-id="11db2-127">Oracle Distributed Transactions</span></span>](oracle-distributed-transactions.md)  
 <span data-ttu-id="11db2-128"><xref:System.Data.OracleClient.OracleConnection> オブジェクトが、トランザクションがアクティブであると判断した場合に、既存の分散トランザクションに自動的に参加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-128">Describes how the <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11db2-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="11db2-129">Related Sections</span></span>  
 [<span data-ttu-id="11db2-130">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="11db2-130">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="11db2-131">ADO.NET を使用する場合の安全なコーディング方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-131">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="11db2-132">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="11db2-132">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)  
 <span data-ttu-id="11db2-133">`DataSets`、型指定された `DataSets`、`DataTables`、および `DataViews` の作成方法と使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-133">Describes how to create and use `DataSets`, typed `DataSets`, `DataTables`, and `DataViews`.</span></span>  
  
 [<span data-ttu-id="11db2-134">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="11db2-134">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="11db2-135">ADO.NET でのデータの操作方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-135">Describes how to work with data in ADO.NET.</span></span>  
  
 [<span data-ttu-id="11db2-136">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="11db2-136">SQL Server and ADO.NET</span></span>](./sql/index.md)  
 <span data-ttu-id="11db2-137">SQL Server 固有の機能の使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-137">Describes how to work with features and functionality that are specific to SQL Server.</span></span>  
  
 [<span data-ttu-id="11db2-138">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="11db2-138">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="11db2-139">ADO.NET でプロバイダーに依存しないコードを記述するための Generic クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="11db2-139">Describes generic classes that allow you to write provider-independent code in ADO.NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11db2-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="11db2-140">See also</span></span>

- [<span data-ttu-id="11db2-141">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="11db2-141">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="11db2-142">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="11db2-142">ADO.NET Overview</span></span>](ado-net-overview.md)
