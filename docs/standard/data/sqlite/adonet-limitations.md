---
title: ADO.NET の制限事項
ms.date: 12/13/2019
description: 経験する可能性がある ADO.NET の制限事項について説明します。
ms.openlocfilehash: 8664b73071fc859ed30080f549b05e7d6ed020f4
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901261"
---
# <a name="adonet-limitations"></a><span data-ttu-id="e21a1-103">ADO.NET の制限事項</span><span class="sxs-lookup"><span data-stu-id="e21a1-103">ADO.NET limitations</span></span>

<span data-ttu-id="e21a1-104">Microsoft.Data.Sqlite には、ADO.NET 抽象化の多くが実装されていますが、いくつかの制限事項があります。</span><span class="sxs-lookup"><span data-stu-id="e21a1-104">Microsoft.Data.Sqlite provides implementations of many of the ADO.NET abstractions, but there are some limitations.</span></span>

## <a name="database-schema-information"></a><span data-ttu-id="e21a1-105">データベース スキーマの情報</span><span class="sxs-lookup"><span data-stu-id="e21a1-105">Database schema information</span></span>

<span data-ttu-id="e21a1-106">クエリ結果に関するメタデータは、<xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> メソッドを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="e21a1-106">Metadata about query results is available using the <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> method.</span></span>

<span data-ttu-id="e21a1-107">`DbConnection.GetSchema()` は実装されていません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-107">`DbConnection.GetSchema()` isn't implemented.</span></span> <span data-ttu-id="e21a1-108">この API は適切に定義されていないため、[sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) テーブルや [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA などの標準 SQLite API を使用して、データベースのメタデータを直接取得することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e21a1-108">This API isn't well-defined, so we recommend retrieving database metadata directly using standard SQLite APIs like the [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) table and the [table_info](https://www.sqlite.org/pragma.html#pragma_table_info) PRAGMA.</span></span>

<span data-ttu-id="e21a1-109">詳細については、「[メタデータ](metadata.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e21a1-109">For more information, see [Metadata](metadata.md).</span></span>

## <a name="systemtransactions"></a><span data-ttu-id="e21a1-110">System.Transactions</span><span class="sxs-lookup"><span data-stu-id="e21a1-110">System.Transactions</span></span>

<span data-ttu-id="e21a1-111">Microsoft.Data.Sqlite では、System.Transactions はまだサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-111">Microsoft.Data.Sqlite doesn't yet support System.Transactions.</span></span> <span data-ttu-id="e21a1-112">代わりに ADO.NET トランザクションを使用してください。</span><span class="sxs-lookup"><span data-stu-id="e21a1-112">Use ADO.NET transactions instead.</span></span> <span data-ttu-id="e21a1-113">詳細については、「[トランザクション](transactions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e21a1-113">For more information, see [Transactions](transactions.md).</span></span>

<span data-ttu-id="e21a1-114">問題 [#13825](https://github.com/dotnet/efcore/issues/13825) で、System.Transactions がサポートされていないことに関するフィードバックをお送りください。</span><span class="sxs-lookup"><span data-stu-id="e21a1-114">Provide feedback about the lack of support for System.Transactions on issue [#13825](https://github.com/dotnet/efcore/issues/13825).</span></span>

## <a name="data-adapters"></a><span data-ttu-id="e21a1-115">データ アダプター</span><span class="sxs-lookup"><span data-stu-id="e21a1-115">Data adapters</span></span>

<span data-ttu-id="e21a1-116">`DbDataAdapter` は、Microsoft.Data.Sqlite ではまだ実装されていません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-116">`DbDataAdapter` isn't yet implemented by Microsoft.Data.Sqlite.</span></span> <span data-ttu-id="e21a1-117">つまり、ADO.NET の `DataSet` と `DataTable` はデータの読み込むのみに使用でき、更新には使用できません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-117">This means you can only use ADO.NET `DataSet` and `DataTable` to load data and not update it.</span></span>

<span data-ttu-id="e21a1-118">`DbDataAdapter` の実装に関するフィードバックを送信するには、問題 [#13838](https://github.com/dotnet/efcore/issues/13838) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="e21a1-118">Use issue [#13838](https://github.com/dotnet/efcore/issues/13838) to provide feedback about implementing `DbDataAdapter`.</span></span>

## <a name="output-parameters"></a><span data-ttu-id="e21a1-119">出力パラメーター</span><span class="sxs-lookup"><span data-stu-id="e21a1-119">Output parameters</span></span>

<span data-ttu-id="e21a1-120">SQLite では、出力パラメーターはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-120">SQLite doesn't support output parameters.</span></span>

## <a name="positional-parameters"></a><span data-ttu-id="e21a1-121">位置指定パラメーター</span><span class="sxs-lookup"><span data-stu-id="e21a1-121">Positional parameters</span></span>

<span data-ttu-id="e21a1-122">Microsoft.Data.Sqlite では、名前付きの[パラメーター](parameters.md)だけがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e21a1-122">Microsoft.Data.Sqlite only supports named [parameters](parameters.md).</span></span> <span data-ttu-id="e21a1-123">位置指定パラメーターはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-123">Positional parameters aren't supported.</span></span>

## <a name="stored-procedures"></a><span data-ttu-id="e21a1-124">ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="e21a1-124">Stored procedures</span></span>

<span data-ttu-id="e21a1-125">SQLite ではストアド プロシージャはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-125">SQLite doesn't support stored procedures.</span></span>

## <a name="isolation-levels"></a><span data-ttu-id="e21a1-126">分離レベル</span><span class="sxs-lookup"><span data-stu-id="e21a1-126">Isolation levels</span></span>

<span data-ttu-id="e21a1-127">SQLite トランザクションでは、分離レベル `Chaos` と `Snapshot` はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e21a1-127">The `Chaos` and `Snapshot` isolation levels aren't supported in SQLite transactions.</span></span>

## <a name="see-also"></a><span data-ttu-id="e21a1-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="e21a1-128">See also</span></span>

* [<span data-ttu-id="e21a1-129">非同期の制限事項</span><span class="sxs-lookup"><span data-stu-id="e21a1-129">Async limitations</span></span>](async.md)
* [<span data-ttu-id="e21a1-130">データ型</span><span class="sxs-lookup"><span data-stu-id="e21a1-130">Data types</span></span>](types.md)
* [<span data-ttu-id="e21a1-131">トランザクション</span><span class="sxs-lookup"><span data-stu-id="e21a1-131">Transactions</span></span>](transactions.md)
