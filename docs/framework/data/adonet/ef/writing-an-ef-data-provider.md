---
title: Entity Framework データ プロバイダーの作成
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854165"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="705bd-102">Entity Framework データ プロバイダーの作成</span><span class="sxs-lookup"><span data-stu-id="705bd-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="705bd-103">ここでは、SQL Server 以外のデータ ソースをサポートするための Entity Framework プロバイダーの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="705bd-103">This section discusses how to write an Entity Framework provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="705bd-104">Entity Framework には、SQL Server をサポートするプロバイダーが含まれています。</span><span class="sxs-lookup"><span data-stu-id="705bd-104">The Entity Framework includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="705bd-105">Entity Framework プロバイダー モデルの概要</span><span class="sxs-lookup"><span data-stu-id="705bd-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="705bd-106">Entity Framework はデータベースに依存しません。ADO.NET プロバイダー モデルを使用して、さまざまなデータ ソースに接続するプロバイダーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="705bd-106">The Entity Framework is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="705bd-107">ADO.NET データ プロバイダー モデルを使用して構築された Entity Framework データ プロバイダーは、次の機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="705bd-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="705bd-108">Entity Data Model (EDM) プリミティブ型をプロバイダー型にマップします。</span><span class="sxs-lookup"><span data-stu-id="705bd-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="705bd-109">プロバイダー固有の関数を公開します。</span><span class="sxs-lookup"><span data-stu-id="705bd-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="705bd-110">Entity Framework クエリをサポートするために、指定された DbQueryCommandTree に対するプロバイダー固有のコマンドを生成します。</span><span class="sxs-lookup"><span data-stu-id="705bd-110">Generates provider-specific commands for a given DbQueryCommandTree to support Entity Framework queries.</span></span>  
  
- <span data-ttu-id="705bd-111">Entity Framework を介した更新をサポートするため、指定された DbModificationCommandTree に対するプロバイダー固有の更新コマンドを生成します。</span><span class="sxs-lookup"><span data-stu-id="705bd-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the Entity Framework.</span></span>  
  
- <span data-ttu-id="705bd-112">ストア スキーマ定義のマッピング ファイルを公開して、データベースに基づくモデルの生成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="705bd-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="705bd-113">概念モデルを使用してメタデータ (テーブルとビューなど) を公開します。</span><span class="sxs-lookup"><span data-stu-id="705bd-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="705bd-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="705bd-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="705bd-115">サンプル</span><span class="sxs-lookup"><span data-stu-id="705bd-115">Sample</span></span>  
 <span data-ttu-id="705bd-116">SQL Server 以外のデータ ソースをサポートする Entity Framework プロバイダーのサンプルについては、「[Entity Framework サンプル プロバイダー](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="705bd-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an Entity Framework provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="705bd-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="705bd-117">In This Section</span></span>  
 [<span data-ttu-id="705bd-118">SQL 生成</span><span class="sxs-lookup"><span data-stu-id="705bd-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="705bd-119">変更 SQL 生成</span><span class="sxs-lookup"><span data-stu-id="705bd-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="705bd-120">プロバイダー マニフェストの仕様</span><span class="sxs-lookup"><span data-stu-id="705bd-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="705bd-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="705bd-121">See also</span></span>

- [<span data-ttu-id="705bd-122">データ プロバイダーの操作</span><span class="sxs-lookup"><span data-stu-id="705bd-122">Working with Data Providers</span></span>](working-with-data-providers.md)
