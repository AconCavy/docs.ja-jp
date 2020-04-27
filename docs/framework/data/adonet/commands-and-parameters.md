---
title: コマンドおよびパラメーター
ms.date: 03/30/2017
ms.assetid: b623f810-d871-49a5-b0f5-078cc3c34db6
ms.openlocfilehash: 1d0c3adb56e5ff44b5c5e065ac040f25584a1946
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784952"
---
# <a name="commands-and-parameters"></a><span data-ttu-id="1077f-102">コマンドおよびパラメーター</span><span class="sxs-lookup"><span data-stu-id="1077f-102">Commands and Parameters</span></span>
<span data-ttu-id="1077f-103">データ ソースへの接続を確立した後、<xref:System.Data.Common.DbCommand> オブジェクトを使用してコマンドを実行し、データ ソースから結果を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="1077f-103">After establishing a connection to a data source, you can execute commands and return results from the data source using a <xref:System.Data.Common.DbCommand> object.</span></span> <span data-ttu-id="1077f-104">コマンドは、使用している .NET Framework データ プロバイダーのいずれかのコマンド コンストラクターで作成できます。</span><span class="sxs-lookup"><span data-stu-id="1077f-104">You can create a command using one of the command constructors for the .NET Framework data provider you are working with.</span></span> <span data-ttu-id="1077f-105">コンストラクターには、データ ソースで実行する SQL ステートメント、<xref:System.Data.Common.DbConnection> オブジェクト、<xref:System.Data.Common.DbTransaction> オブジェクトなど、オプションの引数を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="1077f-105">Constructors can take optional arguments, such as an SQL statement to execute at the data source, a <xref:System.Data.Common.DbConnection> object, or a <xref:System.Data.Common.DbTransaction> object.</span></span> <span data-ttu-id="1077f-106">これらのオブジェクトをコマンドのプロパティとして構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1077f-106">You can also configure those objects as properties of the command.</span></span> <span data-ttu-id="1077f-107">また、<xref:System.Data.Common.DbConnection.CreateCommand%2A> オブジェクトの `DbConnection` メソッドを使用して、特定の接続用のコマンドを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1077f-107">You can also create a command for a particular connection using the <xref:System.Data.Common.DbConnection.CreateCommand%2A> method of a `DbConnection` object.</span></span> <span data-ttu-id="1077f-108">コマンドによって実行される SQL ステートメントは、<xref:System.Data.Common.DbCommand.CommandText%2A> プロパティを使って構成できます。</span><span class="sxs-lookup"><span data-stu-id="1077f-108">The SQL statement being executed by the command can be configured using the <xref:System.Data.Common.DbCommand.CommandText%2A> property.</span></span>  
  
 <span data-ttu-id="1077f-109">.NET Framework に含まれている各 .NET Framework データ プロバイダーは、`Command` オブジェクトを持ちます。</span><span class="sxs-lookup"><span data-stu-id="1077f-109">Each .NET Framework data provider included with the .NET Framework has a `Command` object.</span></span> <span data-ttu-id="1077f-110">.NET Framework Data Provider for OLE DB には <xref:System.Data.OleDb.OleDbCommand> オブジェクト、.NET Framework Data Provider for SQL Server には <xref:System.Data.SqlClient.SqlCommand> オブジェクト、.NET Framework Data Provider for ODBC には <xref:System.Data.Odbc.OdbcCommand> オブジェクト、.NET Framework Data Provider for Oracle には <xref:System.Data.OracleClient.OracleCommand> があります。</span><span class="sxs-lookup"><span data-stu-id="1077f-110">The .NET Framework Data Provider for OLE DB includes an <xref:System.Data.OleDb.OleDbCommand> object, the .NET Framework Data Provider for SQL Server includes a <xref:System.Data.SqlClient.SqlCommand> object, the .NET Framework Data Provider for ODBC includes an <xref:System.Data.Odbc.OdbcCommand> object, and the .NET Framework Data Provider for Oracle includes an <xref:System.Data.OracleClient.OracleCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1077f-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="1077f-111">In This Section</span></span>  
 [<span data-ttu-id="1077f-112">コマンドの実行</span><span class="sxs-lookup"><span data-stu-id="1077f-112">Executing a Command</span></span>](executing-a-command.md)  
 <span data-ttu-id="1077f-113">ADO.NET の `Command` オブジェクトと、それを使用してデータ ソースに対してクエリやコマンドを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1077f-113">Describes the ADO.NET `Command` object and how to use it to execute queries and commands against a data source.</span></span>  
  
 [<span data-ttu-id="1077f-114">パラメーターおよびパラメーター データ型の構成</span><span class="sxs-lookup"><span data-stu-id="1077f-114">Configuring Parameters and Parameter Data Types</span></span>](configuring-parameters-and-parameter-data-types.md)  
 <span data-ttu-id="1077f-115">`Command` のパラメーターの使用 (方向、データ型、パラメーター構文など) について説明します。</span><span class="sxs-lookup"><span data-stu-id="1077f-115">Describes working with `Command` parameters, including direction, data types, and parameter syntax.</span></span>  
  
 [<span data-ttu-id="1077f-116">CommandBuilder でのコマンドの生成</span><span class="sxs-lookup"><span data-stu-id="1077f-116">Generating Commands with CommandBuilders</span></span>](generating-commands-with-commandbuilders.md)  
 <span data-ttu-id="1077f-117">`DataAdapter` に単一テーブルを対象とする SELECT コマンドが割り当てられているときに、コマンド ビルダーを使用して INSERT、UPDATE、DELETE の各コマンドを自動的に生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1077f-117">Describes how to use command builders to automatically generate INSERT, UPDATE, and DELETE commands for a `DataAdapter` that has a single-table SELECT command.</span></span>  
  
 [<span data-ttu-id="1077f-118">データベースからの単一の値の取得</span><span class="sxs-lookup"><span data-stu-id="1077f-118">Obtaining a Single Value from a Database</span></span>](obtaining-a-single-value-from-a-database.md)  
 <span data-ttu-id="1077f-119">`ExecuteScalar` オブジェクトの `Command` メソッドを使用してデータベース クエリから単一の値を返す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1077f-119">Describes how to use the `ExecuteScalar` method of a `Command` object to return a single value from a database query.</span></span>  
  
 [<span data-ttu-id="1077f-120">コマンドを使用したデータ変更</span><span class="sxs-lookup"><span data-stu-id="1077f-120">Using Commands to Modify Data</span></span>](using-commands-to-modify-data.md)  
 <span data-ttu-id="1077f-121">データ プロバイダーを使用して、ストアド プロシージャまたはデータ定義言語 (DDL) のステートメントを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="1077f-121">Describes how to use a data provider to execute stored procedures or data definition language (DDL) statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1077f-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1077f-122">See also</span></span>

- [<span data-ttu-id="1077f-123">DataAdapter と DataReader</span><span class="sxs-lookup"><span data-stu-id="1077f-123">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="1077f-124">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="1077f-124">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="1077f-125">データ ソースへの接続</span><span class="sxs-lookup"><span data-stu-id="1077f-125">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)
- [<span data-ttu-id="1077f-126">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="1077f-126">ADO.NET Overview</span></span>](ado-net-overview.md)
