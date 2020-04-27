---
title: クエリ通知の有効化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a5333e19-8e55-4aa9-82dc-ca8745e516ed
ms.openlocfilehash: 84048a3fba2b32b1ae745160e2b405c04b738c65
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040235"
---
# <a name="enabling-query-notifications"></a><span data-ttu-id="c54d5-102">クエリ通知の有効化</span><span class="sxs-lookup"><span data-stu-id="c54d5-102">Enabling Query Notifications</span></span>
<span data-ttu-id="c54d5-103">クエリ通知を使用するアプリケーションには、いくつか共通する要件があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-103">Applications that consume query notifications have a common set of requirements.</span></span> <span data-ttu-id="c54d5-104">SQL クエリ通知をサポートするには、データ ソースが正しく設定され、ユーザーがクライアント側およびサーバー側の正しい権限を所有している必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-104">Your data source must be correctly configured to support SQL query notifications, and the user must have the correct client-side and server-side permissions.</span></span>  
  
 <span data-ttu-id="c54d5-105">クエリ通知を使用するためには、次のことが必要です。</span><span class="sxs-lookup"><span data-stu-id="c54d5-105">To use query notifications you must:</span></span>  
  
- <span data-ttu-id="c54d5-106">データベースのクエリ通知を有効にします。</span><span class="sxs-lookup"><span data-stu-id="c54d5-106">Enable query notifications for your database.</span></span>  
  
- <span data-ttu-id="c54d5-107">データベースへの接続に使用するユーザー ID に必要なアクセス許可があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="c54d5-107">Ensure that the user ID used to connect to the database has the necessary permissions.</span></span>  
  
- <span data-ttu-id="c54d5-108"><xref:System.Data.SqlClient.SqlCommand> オブジェクトを使用して、通知オブジェクト (<xref:System.Data.SqlClient.SqlDependency> または <xref:System.Data.Sql.SqlNotificationRequest> のいずれか) が関連付けられている有効な SELECT ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="c54d5-108">Use a <xref:System.Data.SqlClient.SqlCommand> object to execute a valid SELECT statement with an associated notification object—either <xref:System.Data.SqlClient.SqlDependency> or <xref:System.Data.Sql.SqlNotificationRequest>.</span></span>  
  
- <span data-ttu-id="c54d5-109">監視対象のデータが変更された場合に通知を処理するコードを設定する</span><span class="sxs-lookup"><span data-stu-id="c54d5-109">Provide code to process the notification if the data being monitored changes.</span></span>  
  
## <a name="query-notifications-requirements"></a><span data-ttu-id="c54d5-110">クエリ通知の要件</span><span class="sxs-lookup"><span data-stu-id="c54d5-110">Query Notifications Requirements</span></span>  
 <span data-ttu-id="c54d5-111">クエリ通知は、特定の要件を満たす SELECT ステートメントでのみサポートされます。</span><span class="sxs-lookup"><span data-stu-id="c54d5-111">Query notifications are supported only for SELECT statements that meet a list of specific requirements.</span></span> <span data-ttu-id="c54d5-112">次の表に、SQL Server オンライン ブックの Service Broker とクエリ通知のドキュメントへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="c54d5-112">The following table provides links to the Service Broker and Query Notifications documentation in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="c54d5-113">**SQL Server のドキュメント**</span><span class="sxs-lookup"><span data-stu-id="c54d5-113">**SQL Server documentation**</span></span>  
  
- <span data-ttu-id="c54d5-114">[通知のためのクエリの作成](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c54d5-114">[Creating a Query for Notification](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms181122(v=sql.105))</span></span>  
  
- <span data-ttu-id="c54d5-115">[Service Broker のセキュリティに関する注意点](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="c54d5-115">[Security Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166059(v=sql.90))</span></span>  
  
- <span data-ttu-id="c54d5-116">[セキュリティと保護 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c54d5-116">[Security and Protection (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522911(v=sql.105))</span></span>  
  
- <span data-ttu-id="c54d5-117">[Notification Services のセキュリティに関する注意点](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="c54d5-117">[Security Considerations for Notifications Services](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms172604(v=sql.90))</span></span>  
  
- <span data-ttu-id="c54d5-118">[クエリ通知の権限](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c54d5-118">[Query Notification Permissions](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms188311(v=sql.105))</span></span>  
  
- <span data-ttu-id="c54d5-119">[Service Broker の国際化に関する注意点](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="c54d5-119">[International Considerations for Service Broker](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms166028(v=sql.90))</span></span>  
  
- <span data-ttu-id="c54d5-120">[ソリューション設計に関する考慮事項 (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c54d5-120">[Solution Design Considerations (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522899(v=sql.105))</span></span>  
  
- <span data-ttu-id="c54d5-121">[Service Broker 開発者向けの情報](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c54d5-121">[Service Broker Developer InfoCenter](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms166100(v=sql.105))</span></span>  
  
- <span data-ttu-id="c54d5-122">[開発者ガイド (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="c54d5-122">[Developer's Guide (Service Broker)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/bb522908(v=sql.105))</span></span>  
  
## <a name="enabling-query-notifications-to-run-sample-code"></a><span data-ttu-id="c54d5-123">サンプル コードを実行するためのクエリ通知の有効化</span><span class="sxs-lookup"><span data-stu-id="c54d5-123">Enabling Query Notifications to Run Sample Code</span></span>  
 <span data-ttu-id="c54d5-124">**AdventureWorks** データベースで Service Broker を有効にするには、SQL Server Management Studio を通じて、次の Transact-SQL ステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="c54d5-124">To enable Service Broker on the **AdventureWorks** database by using SQL Server Management Studio, execute the following Transact-SQL statement:</span></span>  
  
 `ALTER DATABASE AdventureWorks SET ENABLE_BROKER;`  
  
 <span data-ttu-id="c54d5-125">クエリ通知のサンプルを正しく実行するには、次の Transact-SQL ステートメントをデータベース サーバー上で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-125">For the query notification samples to run correctly, the following Transact-SQL statements must be executed on the database server.</span></span>  
  
```sql
CREATE QUEUE ContactChangeMessages;  
  
CREATE SERVICE ContactChangeNotifications  
  ON QUEUE ContactChangeMessages  
([http://schemas.microsoft.com/SQL/Notifications/PostQueryNotification]);  
```  
  
## <a name="query-notifications-permissions"></a><span data-ttu-id="c54d5-126">クエリ通知のアクセス許可</span><span class="sxs-lookup"><span data-stu-id="c54d5-126">Query Notifications Permissions</span></span>  
 <span data-ttu-id="c54d5-127">通知を要求するコマンドを実行するユーザーは、特定のサーバーに対する SUBSCRIBE QUERY NOTIFICATIONS データベース アクセス許可を必要とします。</span><span class="sxs-lookup"><span data-stu-id="c54d5-127">Users who execute commands requesting notification must have SUBSCRIBE QUERY NOTIFICATIONS database permission on the server.</span></span>  
  
 <span data-ttu-id="c54d5-128">部分的に信頼される状況で実行されるクライアント側のコードには <xref:System.Data.SqlClient.SqlClientPermission> が必要です。</span><span class="sxs-lookup"><span data-stu-id="c54d5-128">Client-side code that runs in a partial trust situation requires the <xref:System.Data.SqlClient.SqlClientPermission>.</span></span>  
  
 <span data-ttu-id="c54d5-129">次のコードは <xref:System.Data.SqlClient.SqlClientPermission> オブジェクトを作成し、<xref:System.Security.Permissions.PermissionState> を <xref:System.Security.Permissions.PermissionState.Unrestricted> に設定します。</span><span class="sxs-lookup"><span data-stu-id="c54d5-129">The following code creates a <xref:System.Data.SqlClient.SqlClientPermission> object, setting the <xref:System.Security.Permissions.PermissionState> to <xref:System.Security.Permissions.PermissionState.Unrestricted>.</span></span> <span data-ttu-id="c54d5-130"><xref:System.Security.CodeAccessPermission.Demand%2A> を指定すると、呼び出し履歴の上流に、権限の付与されていない呼び出し元が 1 つでも存在した場合、実行時に強制的に <xref:System.Security.SecurityException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="c54d5-130">The <xref:System.Security.CodeAccessPermission.Demand%2A> will force a <xref:System.Security.SecurityException> at run time if all callers higher in the call stack have not been granted the permission.</span></span>  
  
 [!code-csharp[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/CS/source.cs#1)]
 [!code-vb[DataWorks SqlNotification.Perms#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlNotification.Perms/VB/source.vb#1)]  
  
## <a name="choosing-a-notification-object"></a><span data-ttu-id="c54d5-131">通知オブジェクトの選択</span><span class="sxs-lookup"><span data-stu-id="c54d5-131">Choosing a Notification Object</span></span>  
 <span data-ttu-id="c54d5-132">クエリ通知 API は、通知を処理するために <xref:System.Data.SqlClient.SqlDependency> と <xref:System.Data.Sql.SqlNotificationRequest> という 2 つのオブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="c54d5-132">The query notifications API provides two objects to process notifications: <xref:System.Data.SqlClient.SqlDependency> and <xref:System.Data.Sql.SqlNotificationRequest>.</span></span> <span data-ttu-id="c54d5-133">通常、ASP.NET 以外のほとんどのアプリケーションでは、<xref:System.Data.SqlClient.SqlDependency> オブジェクトを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-133">In general, most non-ASP.NET applications should use the <xref:System.Data.SqlClient.SqlDependency> object.</span></span> <span data-ttu-id="c54d5-134">ASP.NET アプリケーションは、高レベルの <xref:System.Web.Caching.SqlCacheDependency> を使用する必要があります。これは <xref:System.Data.SqlClient.SqlDependency> をラップし、通知オブジェクトとキャッシュ オブジェクトを管理するためのフレームワークになります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-134">ASP.NET applications should use the higher-level <xref:System.Web.Caching.SqlCacheDependency>, which wraps <xref:System.Data.SqlClient.SqlDependency> and provides a framework for administering the notification and cache objects.</span></span>  
  
### <a name="using-sqldependency"></a><span data-ttu-id="c54d5-135">SqlDependency の使用</span><span class="sxs-lookup"><span data-stu-id="c54d5-135">Using SqlDependency</span></span>  
 <span data-ttu-id="c54d5-136"><xref:System.Data.SqlClient.SqlDependency> を使用するには、使用する SQL Server データベースに対して Service Broker を有効にし、通知を受け取るためのアクセス許可をユーザーに与える必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-136">To use <xref:System.Data.SqlClient.SqlDependency>, Service Broker must be enabled for the SQL Server database being used, and users must have permissions to receive notifications.</span></span> <span data-ttu-id="c54d5-137">通知キューなどの Service Broker オブジェクトは事前に定義されています。</span><span class="sxs-lookup"><span data-stu-id="c54d5-137">Service Broker objects, such as the notification queue, are predefined.</span></span>  
  
 <span data-ttu-id="c54d5-138">さらに、<xref:System.Data.SqlClient.SqlDependency> によってワーカー スレッドが自動的に起動し、キューにポストされた通知が処理されます。また、Service Broker メッセージも解析され、情報がイベント引数データとして公開されます。</span><span class="sxs-lookup"><span data-stu-id="c54d5-138">In addition, <xref:System.Data.SqlClient.SqlDependency> automatically launches a worker thread to process notifications as they are posted to the queue; it also parses the Service Broker message, exposing the information as event argument data.</span></span> <span data-ttu-id="c54d5-139"><xref:System.Data.SqlClient.SqlDependency> は、`Start` メソッドを呼び出し、データベースに対する依存関係を確立して初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-139"><xref:System.Data.SqlClient.SqlDependency> must be initialized by calling the `Start` method to establish a dependency to the database.</span></span> <span data-ttu-id="c54d5-140">これは、必要となる各データベース接続に対するアプリケーションの初期化中に、1 回だけ呼び出す必要のある静的メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c54d5-140">This is a static method that needs to be called only once during application initialization for each database connection required.</span></span> <span data-ttu-id="c54d5-141">`Stop` メソッドは、作成された依存関係の接続ごとにアプリケーションの終了時に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-141">The `Stop` method should be called at application termination for each dependency connection that was made.</span></span>  
  
### <a name="using-sqlnotificationrequest"></a><span data-ttu-id="c54d5-142">SqlNotificationRequest の使用</span><span class="sxs-lookup"><span data-stu-id="c54d5-142">Using SqlNotificationRequest</span></span>  
 <span data-ttu-id="c54d5-143">これに対して、<xref:System.Data.Sql.SqlNotificationRequest> では、リッスンしているインフラストラクチャ全体を自分で実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-143">In contrast, <xref:System.Data.Sql.SqlNotificationRequest> requires you to implement the entire listening infrastructure yourself.</span></span> <span data-ttu-id="c54d5-144">さらに、キュー、サービス、およびキューでサポートされているメッセージの種類など、サポート対象となるすべての Service Broker オブジェクトを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c54d5-144">In addition, all the supporting Service Broker objects such as the queue, service, and message types supported by the queue must be defined.</span></span> <span data-ttu-id="c54d5-145">手動によるこの方法は、使用しているアプリケーションで特殊な通知メッセージや通知動作が必要な場合、またはそのアプリケーションが Service Broker アプリケーションの一部である場合に使用すると便利です。</span><span class="sxs-lookup"><span data-stu-id="c54d5-145">This manual approach is useful if your application requires special notification messages or notification behaviors, or if your application is part of a larger Service Broker application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c54d5-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="c54d5-146">See also</span></span>

- [<span data-ttu-id="c54d5-147">SQL Server のクエリ通知</span><span class="sxs-lookup"><span data-stu-id="c54d5-147">Query Notifications in SQL Server</span></span>](query-notifications-in-sql-server.md)
- [<span data-ttu-id="c54d5-148">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="c54d5-148">ADO.NET Overview</span></span>](../ado-net-overview.md)
