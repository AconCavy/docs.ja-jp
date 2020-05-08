---
title: SQL Server における所有権とユーザーとスキーマの分離
ms.date: 03/30/2017
ms.assetid: 242830c1-31b5-4427-828c-cc22ff339f30
ms.openlocfilehash: 5ad3d927bcf3534e134db2c98b79842b0e6148f3
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894425"
---
# <a name="ownership-and-user-schema-separation-in-sql-server"></a><span data-ttu-id="e7ea6-102">SQL Server における所有権とユーザーとスキーマの分離</span><span class="sxs-lookup"><span data-stu-id="e7ea6-102">Ownership and User-Schema Separation in SQL Server</span></span>
<span data-ttu-id="e7ea6-103">オブジェクトの所有者は、それを管理するための取り消し不可能な権限を持ちます。これは SQL Server のセキュリティの核となる概念です。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-103">A core concept of SQL Server security is that owners of objects have irrevocable permissions to administer them.</span></span> <span data-ttu-id="e7ea6-104">オブジェクトの所有者から権限を削除することはできません。また、特定のユーザーがデータベース内のオブジェクトを所有しているときに、そのユーザーをデータベースから削除することもできません。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-104">You cannot remove privileges from an object owner, and you cannot drop users from a database if they own objects in it.</span></span>  
  
## <a name="user-schema-separation"></a><span data-ttu-id="e7ea6-105">ユーザーとスキーマの分離</span><span class="sxs-lookup"><span data-stu-id="e7ea6-105">User-Schema Separation</span></span>  
 <span data-ttu-id="e7ea6-106">ユーザーとスキーマの分離により、データベース オブジェクトの権限をより柔軟に管理できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-106">User-schema separation allows for more flexibility in managing database object permissions.</span></span> <span data-ttu-id="e7ea6-107">"*スキーマ*" は、データベース オブジェクトの名前付きのコンテナーです。これにより、複数のオブジェクトを個別の名前空間にグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-107">A *schema* is a named container for database objects, which allows you to group objects into separate namespaces.</span></span> <span data-ttu-id="e7ea6-108">たとえば、AdventureWorks サンプル データベースには、Production、Sales、および HumanResources というスキーマが格納されています。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-108">For example, the AdventureWorks sample database contains schemas for Production, Sales, and HumanResources.</span></span>  
  
 <span data-ttu-id="e7ea6-109">オブジェクトを参照する 4 つの部分から成る命名構文では、スキーマ名が指定されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-109">The four-part naming syntax for referring to objects specifies the schema name.</span></span>  
  
```text
Server.Database.DatabaseSchema.DatabaseObject  
```  
  
### <a name="schema-owners-and-permissions"></a><span data-ttu-id="e7ea6-110">スキーマの所有者と権限</span><span class="sxs-lookup"><span data-stu-id="e7ea6-110">Schema Owners and Permissions</span></span>  
 <span data-ttu-id="e7ea6-111">スキーマは任意のデータベース プリンシパルが所有できるほか、1 つのプリンシパルが複数のスキーマを所有することもできます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-111">Schemas can be owned by any database principal, and a single principal can own multiple schemas.</span></span> <span data-ttu-id="e7ea6-112">スキーマにはセキュリティ ルールを適用できます。適用されたセキュリティ ルールは、そのスキーマのすべてのオブジェクトによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-112">You can apply security rules to a schema, which are inherited by all objects in the schema.</span></span> <span data-ttu-id="e7ea6-113">スキーマに対してアクセス権限を設定すると、そのスキーマに追加された新しいオブジェクトにこれらの権限が自動的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-113">Once you set up access permissions for a schema, those permissions are automatically applied as new objects are added to the schema.</span></span> <span data-ttu-id="e7ea6-114">ユーザーに既定のスキーマを割り当て、複数のデータベース ユーザーでその同じスキーマを共有できます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-114">Users can be assigned a default schema, and multiple database users can share the same schema.</span></span>  
  
 <span data-ttu-id="e7ea6-115">既定では、開発者がスキーマにオブジェクトを作成した場合、そのオブジェクトは、開発者ではなく、そのスキーマを所有するセキュリティ プリンシパルによって所有されることになります。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-115">By default, when developers create objects in a schema, the objects are owned by the security principal that owns the schema, not the developer.</span></span> <span data-ttu-id="e7ea6-116">オブジェクトの所有権は、Transact-SQL ステートメント ALTER AUTHORIZATION で転送できます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-116">Object ownership can be transferred with ALTER AUTHORIZATION Transact-SQL statement.</span></span> <span data-ttu-id="e7ea6-117">1 つのスキーマに対し、それぞれ異なるユーザーによって所有されたオブジェクトを追加することもできます。そうすることで、スキーマそのものに割り当てるよりも権限を細かく管理できますが、権限の管理が煩雑になるため、この方法はお勧めできません。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-117">A schema can also contain objects that are owned by different users and have more granular permissions than those assigned to the schema, although this is not recommended because it adds complexity to managing permissions.</span></span> <span data-ttu-id="e7ea6-118">オブジェクトはスキーマ間で移動できるほか、プリンシパル間でスキーマの所有権を転送することもできます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-118">Objects can be moved between schemas, and schema ownership can be transferred between principals.</span></span> <span data-ttu-id="e7ea6-119">データベース ユーザーを削除してもスキーマには影響しません。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-119">Database users can be dropped without affecting schemas.</span></span>  
  
### <a name="built-in-schemas"></a><span data-ttu-id="e7ea6-120">組み込みスキーマ</span><span class="sxs-lookup"><span data-stu-id="e7ea6-120">Built-In Schemas</span></span>  
 <span data-ttu-id="e7ea6-121">SQL Server には、組み込みのデータベース ユーザーおよびロールと同じ名前を持った 10 個の定義済みスキーマが付属しています。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-121">SQL Server ships with ten pre-defined schemas that have the same names as the built-in database users and roles.</span></span> <span data-ttu-id="e7ea6-122">これらは主に下位互換性を確保するために存在します。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-122">These exist mainly for backward compatibility.</span></span> <span data-ttu-id="e7ea6-123">固定データベース ロールと同じ名前のスキーマは、不要であれば削除してもかまいません。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-123">You can drop the schemas that have the same names as the fixed database roles if you do not need them.</span></span> <span data-ttu-id="e7ea6-124">次のスキーマを削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-124">You cannot drop the following schemas:</span></span>  
  
- `dbo`  
  
- `guest`  
  
- `sys`  
  
- `INFORMATION_SCHEMA`  
  
 <span data-ttu-id="e7ea6-125">これらを model データベースから削除した場合、新しいデータベースにはこれらのスキーマが存在しなくなります。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-125">If you drop them from the model database, they will not appear in new databases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7ea6-126">`sys` スキーマおよび `INFORMATION_SCHEMA` スキーマは、システム オブジェクト用に予約されています。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-126">The `sys` and `INFORMATION_SCHEMA` schemas are reserved for system objects.</span></span> <span data-ttu-id="e7ea6-127">これらのスキーマにオブジェクトを作成することはできません。また、これらのスキーマを削除することもできません。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-127">You cannot create objects in these schemas and you cannot drop them.</span></span>  
  
#### <a name="the-dbo-schema"></a><span data-ttu-id="e7ea6-128">dbo スキーマ</span><span class="sxs-lookup"><span data-stu-id="e7ea6-128">The dbo Schema</span></span>  
 <span data-ttu-id="e7ea6-129">`dbo` スキーマは、新しく作成されたデータベースに使用される既定のスキーマです。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-129">The `dbo` schema is the default schema for a newly created database.</span></span> <span data-ttu-id="e7ea6-130">`dbo` スキーマは、`dbo` ユーザー アカウントによって所有されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-130">The `dbo` schema is owned by the `dbo` user account.</span></span> <span data-ttu-id="e7ea6-131">既定では、Transact-SQL コマンド CREATE USER で作成されたユーザーには、`dbo` が既定のスキーマとして割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-131">By default, users created with the CREATE USER Transact-SQL command have `dbo` as their default schema.</span></span>  
  
 <span data-ttu-id="e7ea6-132">`dbo` スキーマが割り当てられたユーザーは、`dbo` ユーザー アカウントの権限を継承しません。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-132">Users who are assigned the `dbo` schema do not inherit the permissions of the `dbo` user account.</span></span> <span data-ttu-id="e7ea6-133">スキーマの権限はユーザーによって継承されるのではなく、そのスキーマに含まれたデータベース オブジェクトによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-133">No permissions are inherited from a schema by users; schema permissions are inherited by the database objects contained in the schema.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7ea6-134">1 部構成の名前を使用してデータベース オブジェクトを参照すると、まずユーザーの既定のスキーマが検索されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-134">When database objects are referenced by using a one-part name, SQL Server first looks in the user's default schema.</span></span> <span data-ttu-id="e7ea6-135">そこで目的のオブジェクトが見つからなかった場合は、`dbo` スキーマ内が検索されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-135">If the object is not found there, SQL Server looks next in the `dbo` schema.</span></span> <span data-ttu-id="e7ea6-136">`dbo` スキーマ内にオブジェクトが見つからなかった場合は、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-136">If the object is not in the `dbo` schema, an error is returned.</span></span>  
  
## <a name="external-resources"></a><span data-ttu-id="e7ea6-137">外部リソース</span><span class="sxs-lookup"><span data-stu-id="e7ea6-137">External Resources</span></span>  
 <span data-ttu-id="e7ea6-138">オブジェクトの所有権とスキーマの詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-138">For more information on object ownership and schemas, see the following resources.</span></span>  
  
|<span data-ttu-id="e7ea6-139">リソース</span><span class="sxs-lookup"><span data-stu-id="e7ea6-139">Resource</span></span>|<span data-ttu-id="e7ea6-140">説明</span><span class="sxs-lookup"><span data-stu-id="e7ea6-140">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="e7ea6-141">[ユーザーとスキーマの分離](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span><span class="sxs-lookup"><span data-stu-id="e7ea6-141">[User-Schema Separation](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/ms190387(v=sql.105))</span></span>|<span data-ttu-id="e7ea6-142">ユーザーとスキーマの分離によって導入された変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-142">Describes the changes introduced by user-schema separation.</span></span> <span data-ttu-id="e7ea6-143">新しい動作とそれが所有権、カタログ ビュー、および権限に与える影響を取り上げています。</span><span class="sxs-lookup"><span data-stu-id="e7ea6-143">Includes new behavior, its impact on ownership, catalog views, and permissions.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7ea6-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="e7ea6-144">See also</span></span>

- [<span data-ttu-id="e7ea6-145">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="e7ea6-145">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="e7ea6-146">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="e7ea6-146">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="e7ea6-147">SQL Server での認証</span><span class="sxs-lookup"><span data-stu-id="e7ea6-147">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)
- [<span data-ttu-id="e7ea6-148">SQL Server のサーバー ロールとデータベース ロール</span><span class="sxs-lookup"><span data-stu-id="e7ea6-148">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)
- [<span data-ttu-id="e7ea6-149">SQL Server の承認とアクセス許可</span><span class="sxs-lookup"><span data-stu-id="e7ea6-149">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)
- [<span data-ttu-id="e7ea6-150">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="e7ea6-150">ADO.NET Overview</span></span>](../ado-net-overview.md)
