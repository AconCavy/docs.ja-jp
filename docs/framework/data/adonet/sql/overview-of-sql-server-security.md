---
title: SQL Server セキュリティの概要
description: 既知の脅威に対抗するための機能を理解し、将来の脅威を予測するうえで必要な、SQL Server のセキュリティ アーキテクチャについて説明します。
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: c423a408e607c51c048ad08b91122a1fe06e31b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286276"
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="d4a6e-103">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="d4a6e-103">Overview of SQL Server Security</span></span>
<span data-ttu-id="d4a6e-104">セキュリティを幾重にも重ねて講じる多層防御は、セキュリティ上の脅威に対抗する最も有効な手段です。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-104">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="d4a6e-105">SQL Server のセキュリティ アーキテクチャは、データベースの管理者および開発者が安全なデータベース アプリケーションを作成して脅威に対応できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-105">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="d4a6e-106">SQL Server は、前のバージョンに新しい機能を導入することによって絶えず進化してきました。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-106">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="d4a6e-107">しかし、セキュリティを箱詰めして出荷することはできません。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-107">However, security does not ship in the box.</span></span> <span data-ttu-id="d4a6e-108">アプリケーションには、それぞれ固有のセキュリティ要件があります。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-108">Each application is unique in its security requirements.</span></span> <span data-ttu-id="d4a6e-109">開発者は、既知の脅威に対してどのような機能を組み合わせるのが最も効果的かを理解し、将来発生する可能性のある脅威を予測する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-109">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="d4a6e-110">SQL Server のインスタンスは、サーバーを頂点とする階層形式のエンティティのコレクションを持ちます。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-110">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="d4a6e-111">各サーバーには複数のデータベースが存在し、各データベースには、セキュリティ保護可能なオブジェクトのコレクションが存在します。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-111">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="d4a6e-112">SQL Server へのアクセスが許可されたユーザー、グループ、またはプロセスを "*プリンシパル*" と呼び、SQL Server のセキュリティ保護可能なリソースにはすべて、プリンシパルに対して付与することのできる "*権限*" が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-112">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="d4a6e-113">SQL Server セキュリティ フレームワークでは、"*認証*" および "*承認*" を使用して、セキュリティ保護可能なエンティティへのアクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-113">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
- <span data-ttu-id="d4a6e-114">認証は SQL Server にログオンするプロセスです。プリンシパルは、サーバーによって評価される資格情報を送信することによってアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-114">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="d4a6e-115">認証対象となるユーザーまたはプロセスの ID は、認証によって確立されます。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-115">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
- <span data-ttu-id="d4a6e-116">承認は、プリンシパルがアクセスできる、セキュリティ保護可能なリソースと、これらのリソースに対して許可された操作を特定するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-116">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="d4a6e-117">このセクションの各トピックでは、SQL Server のセキュリティの基礎を取り上げています。より詳細な情報を確認できるように、該当するバージョンの SQL Server オンライン ブックへのリンクも用意されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-117">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d4a6e-118">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d4a6e-118">In This Section</span></span>  
 [<span data-ttu-id="d4a6e-119">SQL Server での認証</span><span class="sxs-lookup"><span data-stu-id="d4a6e-119">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)  
 <span data-ttu-id="d4a6e-120">SQL Server のログインと認証の説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-120">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="d4a6e-121">SQL Server のサーバー ロールとデータベース ロール</span><span class="sxs-lookup"><span data-stu-id="d4a6e-121">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="d4a6e-122">固定サーバー ロールと固定データベース ロール、カスタム データベース ロール、組み込みアカウントの説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-122">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="d4a6e-123">SQL Server における所有権とユーザーとスキーマの分離</span><span class="sxs-lookup"><span data-stu-id="d4a6e-123">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="d4a6e-124">オブジェクトの所有権とユーザーとスキーマの分離の説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-124">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="d4a6e-125">SQL Server の承認とアクセス許可</span><span class="sxs-lookup"><span data-stu-id="d4a6e-125">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="d4a6e-126">最小特権の原則に基づく権限の付与について説明しているほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-126">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="d4a6e-127">SQL Server でのデータの暗号化</span><span class="sxs-lookup"><span data-stu-id="d4a6e-127">Data Encryption in SQL Server</span></span>](data-encryption-in-sql-server.md)  
 <span data-ttu-id="d4a6e-128">SQL Server におけるデータの暗号化オプションの説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-128">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="d4a6e-129">SQL Server の CLR 統合セキュリティ</span><span class="sxs-lookup"><span data-stu-id="d4a6e-129">CLR Integration Security in SQL Server</span></span>](clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="d4a6e-130">CLR 統合セキュリティ関連リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="d4a6e-130">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4a6e-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4a6e-131">See also</span></span>

- [<span data-ttu-id="d4a6e-132">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d4a6e-132">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="d4a6e-133">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="d4a6e-133">SQL Server Security</span></span>](sql-server-security.md)
- [<span data-ttu-id="d4a6e-134">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="d4a6e-134">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="d4a6e-135">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="d4a6e-135">ADO.NET Overview</span></span>](../ado-net-overview.md)
