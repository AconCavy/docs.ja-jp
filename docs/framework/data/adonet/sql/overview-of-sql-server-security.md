---
title: SQL Server セキュリティの概要
ms.date: 03/30/2017
ms.assetid: ae66dd75-5c16-4cc0-9e12-774dd26d3fb9
ms.openlocfilehash: adc1ce661d49c468de09552ea36a2cd58d6343f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780939"
---
# <a name="overview-of-sql-server-security"></a><span data-ttu-id="5159d-102">SQL Server セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="5159d-102">Overview of SQL Server Security</span></span>
<span data-ttu-id="5159d-103">セキュリティを幾重にも重ねて講じる多層防御は、セキュリティ上の脅威に対抗する最も有効な手段です。</span><span class="sxs-lookup"><span data-stu-id="5159d-103">A defense-in-depth strategy, with overlapping layers of security, is the best way to counter security threats.</span></span> <span data-ttu-id="5159d-104">SQL Server のセキュリティ アーキテクチャは、データベースの管理者および開発者が安全なデータベース アプリケーションを作成して脅威に対応できるように設計されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-104">SQL Server provides a security architecture that is designed to allow database administrators and developers to create secure database applications and counter threats.</span></span> <span data-ttu-id="5159d-105">SQL Server は、前のバージョンに新しい機能を導入することによって絶えず進化してきました。</span><span class="sxs-lookup"><span data-stu-id="5159d-105">Each version of SQL Server has improved on previous versions of SQL Server with the introduction of new features and functionality.</span></span> <span data-ttu-id="5159d-106">しかし、セキュリティを箱詰めして出荷することはできません。</span><span class="sxs-lookup"><span data-stu-id="5159d-106">However, security does not ship in the box.</span></span> <span data-ttu-id="5159d-107">アプリケーションには、それぞれ固有のセキュリティ要件があります。</span><span class="sxs-lookup"><span data-stu-id="5159d-107">Each application is unique in its security requirements.</span></span> <span data-ttu-id="5159d-108">開発者は、既知の脅威に対してどのような機能を組み合わせるのが最も効果的かを理解し、将来発生する可能性のある脅威を予測する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5159d-108">Developers need to understand which combination of features and functionality are most appropriate to counter known threats, and to anticipate threats that may arise in the future.</span></span>  
  
 <span data-ttu-id="5159d-109">SQL Server のインスタンスは、サーバーを頂点とする階層形式のエンティティのコレクションを持ちます。</span><span class="sxs-lookup"><span data-stu-id="5159d-109">A SQL Server instance contains a hierarchical collection of entities, starting with the server.</span></span> <span data-ttu-id="5159d-110">各サーバーには複数のデータベースが存在し、各データベースには、セキュリティ保護可能なオブジェクトのコレクションが存在します。</span><span class="sxs-lookup"><span data-stu-id="5159d-110">Each server contains multiple databases, and each database contains a collection of securable objects.</span></span> <span data-ttu-id="5159d-111">SQL Server へのアクセスが許可されたユーザー、グループ、またはプロセスを "*プリンシパル*" と呼び、SQL Server のセキュリティ保護可能なリソースにはすべて、プリンシパルに対して付与することのできる "*権限*" が関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="5159d-111">Every SQL Server securable has associated *permissions* that can be granted to a *principal*, which is an individual, group or process granted access to SQL Server.</span></span> <span data-ttu-id="5159d-112">SQL Server セキュリティ フレームワークでは、"*認証*" および "*承認*" を使用して、セキュリティ保護可能なエンティティへのアクセスを管理します。</span><span class="sxs-lookup"><span data-stu-id="5159d-112">The SQL Server security framework manages access to securable entities through *authentication* and *authorization*.</span></span>  
  
- <span data-ttu-id="5159d-113">認証は SQL Server にログオンするプロセスです。プリンシパルは、サーバーによって評価される資格情報を送信することによってアクセスを要求します。</span><span class="sxs-lookup"><span data-stu-id="5159d-113">Authentication is the process of logging on to SQL Server by which a principal requests access by submitting credentials that the server evaluates.</span></span> <span data-ttu-id="5159d-114">認証対象となるユーザーまたはプロセスの ID は、認証によって確立されます。</span><span class="sxs-lookup"><span data-stu-id="5159d-114">Authentication establishes the identity of the user or process being authenticated.</span></span>  
  
- <span data-ttu-id="5159d-115">承認は、プリンシパルがアクセスできる、セキュリティ保護可能なリソースと、これらのリソースに対して許可された操作を特定するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="5159d-115">Authorization is the process of determining which securable resources a principal can access, and which operations are allowed for those resources.</span></span>  
  
 <span data-ttu-id="5159d-116">このセクションの各トピックでは、SQL Server のセキュリティの基礎を取り上げています。より詳細な情報を確認できるように、該当するバージョンの SQL Server オンライン ブックへのリンクも用意されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-116">The topics in this section cover SQL Server security fundamentals, providing links to the complete documentation in the relevant version of SQL Server Books Online.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5159d-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="5159d-117">In This Section</span></span>  
 [<span data-ttu-id="5159d-118">SQL Server での認証</span><span class="sxs-lookup"><span data-stu-id="5159d-118">Authentication in SQL Server</span></span>](authentication-in-sql-server.md)  
 <span data-ttu-id="5159d-119">SQL Server のログインと認証の説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-119">Describes logins and authentication in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="5159d-120">SQL Server のサーバー ロールとデータベース ロール</span><span class="sxs-lookup"><span data-stu-id="5159d-120">Server and Database Roles in SQL Server</span></span>](server-and-database-roles-in-sql-server.md)  
 <span data-ttu-id="5159d-121">固定サーバー ロールと固定データベース ロール、カスタム データベース ロール、組み込みアカウントの説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-121">Describes fixed server and database roles, custom database roles, and built-in accounts and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="5159d-122">SQL Server における所有権とユーザーとスキーマの分離</span><span class="sxs-lookup"><span data-stu-id="5159d-122">Ownership and User-Schema Separation in SQL Server</span></span>](ownership-and-user-schema-separation-in-sql-server.md)  
 <span data-ttu-id="5159d-123">オブジェクトの所有権とユーザーとスキーマの分離の説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-123">Describes object ownership and  user-schema separation and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="5159d-124">SQL Server の承認とアクセス許可</span><span class="sxs-lookup"><span data-stu-id="5159d-124">Authorization and Permissions in SQL Server</span></span>](authorization-and-permissions-in-sql-server.md)  
 <span data-ttu-id="5159d-125">最小特権の原則に基づく権限の付与について説明しているほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-125">Describes granting permissions using the principle of least privilege and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="5159d-126">SQL Server でのデータの暗号化</span><span class="sxs-lookup"><span data-stu-id="5159d-126">Data Encryption in SQL Server</span></span>](data-encryption-in-sql-server.md)  
 <span data-ttu-id="5159d-127">SQL Server におけるデータの暗号化オプションの説明のほか、各種リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-127">Describes data encryption options in SQL Server and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="5159d-128">SQL Server の CLR 統合セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5159d-128">CLR Integration Security in SQL Server</span></span>](clr-integration-security-in-sql-server.md)  
 <span data-ttu-id="5159d-129">CLR 統合セキュリティ関連リソースへのリンクが記載されています。</span><span class="sxs-lookup"><span data-stu-id="5159d-129">Provides links to CLR integration security resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5159d-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="5159d-130">See also</span></span>

- [<span data-ttu-id="5159d-131">ADO.NET アプリケーションのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="5159d-131">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="5159d-132">SQL Server のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="5159d-132">SQL Server Security</span></span>](sql-server-security.md)
- [<span data-ttu-id="5159d-133">SQL Server におけるアプリケーション セキュリティのシナリオ</span><span class="sxs-lookup"><span data-stu-id="5159d-133">Application Security Scenarios in SQL Server</span></span>](application-security-scenarios-in-sql-server.md)
- [<span data-ttu-id="5159d-134">ADO.NET の概要</span><span class="sxs-lookup"><span data-stu-id="5159d-134">ADO.NET Overview</span></span>](../ado-net-overview.md)
