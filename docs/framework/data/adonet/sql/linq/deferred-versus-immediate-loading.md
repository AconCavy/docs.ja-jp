---
title: 遅延読み込みと即時読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d1d7247f-a3b7-460b-b342-5c1a2365aa1a
ms.openlocfilehash: 4e2cb7c90eb703985cbb1b8673522a9e253564d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164299"
---
# <a name="deferred-versus-immediate-loading"></a><span data-ttu-id="d6818-102">遅延読み込みと即時読み込み</span><span class="sxs-lookup"><span data-stu-id="d6818-102">Deferred versus Immediate Loading</span></span>

<span data-ttu-id="d6818-103">オブジェクトに対してクエリを実行すると、要求したオブジェクトだけが実際に取得されます。</span><span class="sxs-lookup"><span data-stu-id="d6818-103">When you query for an object, you actually retrieve only the object you requested.</span></span> <span data-ttu-id="d6818-104">"*関連*" オブジェクトが同時に自動的にフェッチされることはありません。</span><span class="sxs-lookup"><span data-stu-id="d6818-104">The *related* objects are not automatically fetched at the same time.</span></span> <span data-ttu-id="d6818-105">(詳しくは、「[リレーションシップを介したクエリの実行](querying-across-relationships.md)」をご覧ください。)ただし、関連オブジェクトにアクセスしようとすると、それらを取得する要求が生成されるため、関連オブジェクトがまだ読み込まれていない状態を識別することはできません。</span><span class="sxs-lookup"><span data-stu-id="d6818-105">(For more information, see [Querying Across Relationships](querying-across-relationships.md).) You cannot see the fact that the related objects are not already loaded, because an attempt to access them produces a request that retrieves them.</span></span>  
  
 <span data-ttu-id="d6818-106">たとえば、特定の注文のセットを取得するクエリを実行し、そのうちの一部についてだけ特定の顧客にメール通知を送信するものとします。</span><span class="sxs-lookup"><span data-stu-id="d6818-106">For example, you might want to query for a particular set of orders and then only occasionally send an email notification to particular customers.</span></span> <span data-ttu-id="d6818-107">最初から注文ごとにすべての顧客データを取得する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="d6818-107">You would not necessarily need initially to retrieve all customer data with every order.</span></span> <span data-ttu-id="d6818-108">遅延読み込みを使用すると、関連情報が実際に必要になるまで、その情報の取得を遅らせることができます。</span><span class="sxs-lookup"><span data-stu-id="d6818-108">You can use deferred loading to defer retrieval of extra information until you absolutely have to.</span></span> <span data-ttu-id="d6818-109">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="d6818-109">Consider the following example:</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#1)]
 [!code-vb[DLinqQueryConcepts#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#1)]  
  
 <span data-ttu-id="d6818-110">その反対も同様です。</span><span class="sxs-lookup"><span data-stu-id="d6818-110">The opposite might also be true.</span></span> <span data-ttu-id="d6818-111">顧客データと注文データを同時に表示する必要のあるアプリケーションがあるとします。</span><span class="sxs-lookup"><span data-stu-id="d6818-111">You might have an application that has to view customer and order data at the same time.</span></span> <span data-ttu-id="d6818-112">両方のデータが必要であることがわかっています。</span><span class="sxs-lookup"><span data-stu-id="d6818-112">You know you need both sets of data.</span></span> <span data-ttu-id="d6818-113">このアプリケーションでは、結果を取得するのと同時に、各顧客の注文情報が必要になります。</span><span class="sxs-lookup"><span data-stu-id="d6818-113">You know your application needs order information for each customer as soon as you get the results.</span></span> <span data-ttu-id="d6818-114">すべての顧客について注文を照会する個別のクエリを発行するのは適切ではありません。</span><span class="sxs-lookup"><span data-stu-id="d6818-114">You would not want to submit individual queries for orders for every customer.</span></span> <span data-ttu-id="d6818-115">ここで必要なのは、注文データと顧客データを同時に収集することです。</span><span class="sxs-lookup"><span data-stu-id="d6818-115">What you really want is to retrieve the order data together with the customers.</span></span>  
  
 [!code-csharp[DLinqQueryConcepts#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#2)]
 [!code-vb[DLinqQueryConcepts#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#2)]  
  
 <span data-ttu-id="d6818-116">1 つのクエリでクロス積によって顧客データと注文データを結合し、すべての関連データを大きな 1 つの投影として取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="d6818-116">You can also join customers and orders in a query by forming the cross-product and retrieving all the relative bits of data as one large projection.</span></span> <span data-ttu-id="d6818-117">ただし、このような結果はエンティティではありません </span><span class="sxs-lookup"><span data-stu-id="d6818-117">But these results are not entities.</span></span> <span data-ttu-id="d6818-118">(詳しくは、「[LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)」をご覧ください)。</span><span class="sxs-lookup"><span data-stu-id="d6818-118">(For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md)).</span></span> <span data-ttu-id="d6818-119">エンティティとは、識別子を持ち、変更が可能なオブジェクトですが、これらの結果は投影であり、変更や永続化はできません。</span><span class="sxs-lookup"><span data-stu-id="d6818-119">Entities are objects that have identity and that you can modify, whereas these results would be projections that cannot be changed and persisted.</span></span> <span data-ttu-id="d6818-120">さらに、平坦な結合出力では、注文ごとに各顧客が繰り返し現れるため、余分なデータが大量に取得されることになります。</span><span class="sxs-lookup"><span data-stu-id="d6818-120">Even worse, you would be retrieving lots of redundant data as each customer repeats for each order in the flattened join output.</span></span>  
  
 <span data-ttu-id="d6818-121">ここで必要なのは、関連オブジェクトのセットを同時に取得することです。</span><span class="sxs-lookup"><span data-stu-id="d6818-121">What you really need is a way to retrieve a set of related objects at the same time.</span></span> <span data-ttu-id="d6818-122">このセットは、目的の用途に必要十分なデータだけを取得できるように、グラフ上に線引きされた区画に相当します。</span><span class="sxs-lookup"><span data-stu-id="d6818-122">The set is a delineated section of a graph so that you would never be retrieving more or less than was necessary for your intended use.</span></span> <span data-ttu-id="d6818-123">この目的のため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] には、オブジェクト モデルの特定の領域の即時読み込みを行う <xref:System.Data.Linq.DataLoadOptions> が用意されています。</span><span class="sxs-lookup"><span data-stu-id="d6818-123">For this purpose, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides <xref:System.Data.Linq.DataLoadOptions> for immediate loading of a region of your object model.</span></span> <span data-ttu-id="d6818-124">次のメソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="d6818-124">Methods include:</span></span>  
  
- <span data-ttu-id="d6818-125"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> メソッド。メイン ターゲットに関連するデータを即時に読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d6818-125">The  <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method, to immediately load data related to the main target.</span></span>  
  
- <span data-ttu-id="d6818-126"><xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> メソッド。特定のリレーションシップに対して取得されるオブジェクトにフィルターを適用します。</span><span class="sxs-lookup"><span data-stu-id="d6818-126">The <xref:System.Data.Linq.DataLoadOptions.AssociateWith%2A> method, to filter objects retrieved for a particular relationship.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6818-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6818-127">See also</span></span>

- [<span data-ttu-id="d6818-128">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="d6818-128">Query Concepts</span></span>](query-concepts.md)
