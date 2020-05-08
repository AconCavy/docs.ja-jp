---
title: ID キャッシュからのオブジェクトの取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 96c13903-ccb6-4a0e-ab6a-8ca955ca314d
ms.openlocfilehash: d14b15f72bd196d8b3a61f22c614516e17d2e95b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781244"
---
# <a name="retrieving-objects-from-the-identity-cache"></a><span data-ttu-id="183ad-102">ID キャッシュからのオブジェクトの取得</span><span class="sxs-lookup"><span data-stu-id="183ad-102">Retrieving Objects from the Identity Cache</span></span>
<span data-ttu-id="183ad-103">このトピックでは、<xref:System.Data.Linq.DataContext> によって管理される ID キャッシュからオブジェクトを返す、LINQ to SQL クエリの種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="183ad-103">This topic describes the types of LINQ to SQL queries that return an object from the identity cache that is managed by the <xref:System.Data.Linq.DataContext>.</span></span>  
  
 <span data-ttu-id="183ad-104">LINQ to SQL では、<xref:System.Data.Linq.DataContext> がクエリの実行に応じてオブジェクトの ID を ID キャッシュにログして、オブジェクトを管理する場合があります。</span><span class="sxs-lookup"><span data-stu-id="183ad-104">In LINQ to SQL, one of the ways in which the <xref:System.Data.Linq.DataContext> manages objects is by logging object identities in an identity cache as queries are executed.</span></span> <span data-ttu-id="183ad-105">場合によっては、データベースに対してクエリを実行する前に、LINQ to SQL が ID キャッシュからオブジェクトの取得を試みることがあります。</span><span class="sxs-lookup"><span data-stu-id="183ad-105">In some cases, LINQ to SQL will attempt to retrieve an object from the identity cache before executing a query in the database.</span></span>  
  
 <span data-ttu-id="183ad-106">通常、LINQ to SQL で ID キャッシュからオブジェクトを取得するには、そのクエリがオブジェクトのプライマリ キーに基づき、1 つのオブジェクトを返すようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="183ad-106">In general, for a LINQ to SQL query to return an object from the identity cache, the query must be based on the primary key of an object and must return a single object.</span></span> <span data-ttu-id="183ad-107">特に、次に示す一般的な形式のいずれかでクエリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="183ad-107">In particular, the query must be in one of the general forms shown below.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="183ad-108">プリコンパイル済みクエリでは、ID キャッシュからオブジェクトが返されません。</span><span class="sxs-lookup"><span data-stu-id="183ad-108">Pre-compiled queries will not return objects from the identity cache.</span></span> <span data-ttu-id="183ad-109">プリコンパイル済みクエリの詳細については、「<xref:System.Data.Linq.CompiledQuery>」および「[方法:クエリを格納および再利用する](how-to-store-and-reuse-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="183ad-109">For more information about pre-compiled queries, see <xref:System.Data.Linq.CompiledQuery> and [How to: Store and Reuse Queries](how-to-store-and-reuse-queries.md).</span></span>  
  
 <span data-ttu-id="183ad-110">オブジェクトを ID キャッシュから取得するには、次に示す一般的な形式のいずれかでクエリを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="183ad-110">A query must be in one of the following general forms to retrieve an object from the identity cache:</span></span>  
  
- <span data-ttu-id="183ad-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span><span class="sxs-lookup"><span data-stu-id="183ad-111"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `)`</span></span>  
  
- <span data-ttu-id="183ad-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span><span class="sxs-lookup"><span data-stu-id="183ad-112"><xref:System.Data.Linq.Table%601> `.Function1(` `predicate` `).Function2()`</span></span>  
  
 <span data-ttu-id="183ad-113">これらの一般的な形式では、`Function1`、`Function2`、および `predicate` が次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="183ad-113">In these general forms, `Function1`, `Function2`, and `predicate` are defined as follows.</span></span>  
  
 <span data-ttu-id="183ad-114">`Function1` は、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="183ad-114">`Function1` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.Where%2A>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="183ad-115">`Function2` は、次のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="183ad-115">`Function2` can be any of the following:</span></span>  
  
- <xref:System.Linq.Queryable.First%2A>  
  
- <xref:System.Linq.Queryable.FirstOrDefault%2A>  
  
- <xref:System.Linq.Queryable.Single%2A>  
  
- <xref:System.Linq.Queryable.SingleOrDefault%2A>  
  
 <span data-ttu-id="183ad-116">`predicate` は、オブジェクトのプライマリ キー プロパティが定数値に設定された式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="183ad-116">`predicate` must be an expression in which the object's primary key property is set to a constant value.</span></span> <span data-ttu-id="183ad-117">オブジェクトのプライマリ キーが複数のプロパティで定義されている場合は、それぞれのプライマリ キー プロパティが定数値に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="183ad-117">If an object has a primary key defined by more than one property, each primary key property must be set to a constant value.</span></span> <span data-ttu-id="183ad-118">`predicate` に使用する必要がある形式の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="183ad-118">The following are examples of the form `predicate` must take:</span></span>  
  
- `c => c.PK == constant_value`  
  
- `c => c.PK1 == constant_value1 && c=> c.PK2 == constant_value2`  
  
## <a name="example"></a><span data-ttu-id="183ad-119">例</span><span class="sxs-lookup"><span data-stu-id="183ad-119">Example</span></span>  
 <span data-ttu-id="183ad-120">次のコードは、ID キャッシュからオブジェクトを取得する LINQ to SQL クエリの例です。</span><span class="sxs-lookup"><span data-stu-id="183ad-120">The following code provides examples of the types of LINQ to SQL queries that retrieve an object from the identity cache.</span></span>  
  
 [!code-csharp[L2S_QueryCache#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/l2s_querycache/cs/program.cs#1)]
 [!code-vb[L2S_QueryCache#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/l2s_querycache/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="183ad-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="183ad-121">See also</span></span>

- [<span data-ttu-id="183ad-122">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="183ad-122">Query Concepts</span></span>](query-concepts.md)
- [<span data-ttu-id="183ad-123">オブジェクト ID</span><span class="sxs-lookup"><span data-stu-id="183ad-123">Object Identity</span></span>](object-identity.md)
- [<span data-ttu-id="183ad-124">背景情報</span><span class="sxs-lookup"><span data-stu-id="183ad-124">Background Information</span></span>](background-information.md)
- [<span data-ttu-id="183ad-125">オブジェクト ID</span><span class="sxs-lookup"><span data-stu-id="183ad-125">Object Identity</span></span>](object-identity.md)
