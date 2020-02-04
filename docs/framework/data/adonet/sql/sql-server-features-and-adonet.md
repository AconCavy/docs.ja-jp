---
title: SQL Server の機能と ADO.NET
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: 2839529b-a79b-4450-be5d-07a98dbc7a0f
ms.openlocfilehash: a4420799a94b5fa5f37b1e25cf6eb37c130de471
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2020
ms.locfileid: "76979795"
---
# <a name="sql-server-features-and-adonet"></a><span data-ttu-id="511f4-102">SQL Server の機能と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="511f4-102">SQL Server Features and ADO.NET</span></span>
<span data-ttu-id="511f4-103">このセクションのトピックでは、ADO.NET を使用したデータベース アプリケーションの開発を目的とする SQL Server の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-103">The topics in this section discuss features in SQL Server that are targeted at developing database applications using ADO.NET.</span></span>  
  
 <span data-ttu-id="511f4-104">詳細については、次の表に示すように、使用する SQL Server のバージョンに対応した SQL Server オンライン ブックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="511f4-104">For more information, see SQL Server Books Online for the version of SQL Server you are using, as listed in the following table.</span></span>  
  
 <span data-ttu-id="511f4-105">**SQL Server オンライン ブック**</span><span class="sxs-lookup"><span data-stu-id="511f4-105">**SQL Server Books Online**</span></span>  
  
1. [<span data-ttu-id="511f4-106">開発 (データベースエンジン)</span><span class="sxs-lookup"><span data-stu-id="511f4-106">Development (Database Engine)</span></span>](https://go.microsoft.com/fwlink/?LinkId=115245)  
  
## <a name="in-this-section"></a><span data-ttu-id="511f4-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="511f4-107">In This Section</span></span>  
 [<span data-ttu-id="511f4-108">SQL Server のインスタンスの列挙 (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="511f4-108">Enumerating Instances of SQL Server (ADO.NET)</span></span>](enumerating-instances-of-sql-server.md)  
 <span data-ttu-id="511f4-109">SQL Server のアクティブなインスタンスを列挙する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-109">Describes how to enumerate active instances of SQL Server.</span></span>  
  
 [<span data-ttu-id="511f4-110">SQL Server のプロバイダー統計情報</span><span class="sxs-lookup"><span data-stu-id="511f4-110">Provider Statistics for SQL Server</span></span>](provider-statistics-for-sql-server.md)  
 <span data-ttu-id="511f4-111">SQL Server の実行時の統計情報の取得のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-111">Describes support for obtaining SQL Server run-time statistics.</span></span>  
  
 [<span data-ttu-id="511f4-112">SQL Server Express ユーザー インスタンス</span><span class="sxs-lookup"><span data-stu-id="511f4-112">SQL Server Express User Instances</span></span>](sql-server-express-user-instances.md)  
 <span data-ttu-id="511f4-113">SQL Server Express のユーザー インターフェイスのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-113">Describes support for SQL Server Express user instances.</span></span>  
  
 [<span data-ttu-id="511f4-114">SQL Server のデータベース ミラーリング</span><span class="sxs-lookup"><span data-stu-id="511f4-114">Database Mirroring in SQL Server</span></span>](database-mirroring-in-sql-server.md)  
 <span data-ttu-id="511f4-115">データベース ミラーリング機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-115">Describes database mirroring functionality.</span></span>  
  
 [<span data-ttu-id="511f4-116">SQL Server の共通言語ランタイム統合</span><span class="sxs-lookup"><span data-stu-id="511f4-116">SQL Server Common Language Runtime Integration</span></span>](sql-server-common-language-runtime-integration.md)  
 <span data-ttu-id="511f4-117">SQL Server で共通言語ランタイム (CLR) データベース オブジェクトからデータにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-117">Describes how data can be accessed from within a common language runtime (CLR) database object in SQL Server.</span></span>  
  
 [<span data-ttu-id="511f4-118">SQL Server のクエリ通知</span><span class="sxs-lookup"><span data-stu-id="511f4-118">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)  
 <span data-ttu-id="511f4-119">.NET Framework アプリケーションで、データが変更されている場合に SQL Server に対して通知を要求する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-119">Describes how .NET Framework applications can request notification from SQL Server when data has changed.</span></span>  
  
 [<span data-ttu-id="511f4-120">SQL Server でのスナップショット分離</span><span class="sxs-lookup"><span data-stu-id="511f4-120">Snapshot Isolation in SQL Server</span></span>](snapshot-isolation-in-sql-server.md)  
 <span data-ttu-id="511f4-121">トランザクション アプリケーションでのブロックの軽減を目的とする行バージョン管理機構であるスナップショット分離のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-121">Describes support for snapshot isolation, a row versioning mechanism designed to reduce blocking in transactional applications.</span></span>  
  
 [<span data-ttu-id="511f4-122">高可用性ディザスター リカバリーのための SqlClient サポート</span><span class="sxs-lookup"><span data-stu-id="511f4-122">SqlClient Support for High Availability, Disaster Recovery</span></span>](sqlclient-support-for-high-availability-disaster-recovery.md)  
 <span data-ttu-id="511f4-123">高可用性ディザスター リカバリー (AlwaysOn) 可用性グループの SqlClient サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-123">Describes SqlClient support for high-availability, disaster recovery (AlwaysOn) availability groups.</span></span>  
  
 [<span data-ttu-id="511f4-124">SqlClient による LocalDB のサポート</span><span class="sxs-lookup"><span data-stu-id="511f4-124">SqlClient Support for LocalDB</span></span>](sqlclient-support-for-localdb.md)  
 <span data-ttu-id="511f4-125">LocalDB データベースの SqlClient サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="511f4-125">Describes SqlClient support for LocalDB databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511f4-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="511f4-126">See also</span></span>

- [<span data-ttu-id="511f4-127">ADO.NET における SQL Server データ操作</span><span class="sxs-lookup"><span data-stu-id="511f4-127">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)
- [<span data-ttu-id="511f4-128">ADO.NET でのデータの取得および変更</span><span class="sxs-lookup"><span data-stu-id="511f4-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="511f4-129">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="511f4-129">LINQ to SQL</span></span>](./linq/index.md)
- [<span data-ttu-id="511f4-130">SQL Server と ADO.NET</span><span class="sxs-lookup"><span data-stu-id="511f4-130">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="511f4-131">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="511f4-131">ADO.NET Overview</span></span>](../ado-net-overview.md)
