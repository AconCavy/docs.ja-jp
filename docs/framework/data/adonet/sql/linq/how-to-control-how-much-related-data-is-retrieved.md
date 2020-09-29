---
title: '方法: 取得する関連データの量を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 77ac29eeeaa30ef438b635364dc8e883a0e4c158
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91161335"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="6d1e5-102">方法: 取得する関連データの量を制御する</span><span class="sxs-lookup"><span data-stu-id="6d1e5-102">How to: Control How Much Related Data Is Retrieved</span></span>

<span data-ttu-id="6d1e5-103">メイン ターゲットと一緒にどの関連データを取得するかを指定するには、<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="6d1e5-104">たとえば、顧客の注文に関する情報が必要になることがわかっている場合は、<xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> を使用して、顧客情報と同時に注文情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="6d1e5-105">この方法によって、データベースへの 1 回のアクセスで 2 種類の情報セットを両方とも取得できます。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6d1e5-106">メイン ターゲットである顧客に関連して注文データも取得する場合など、クエリのメイン ターゲットに関連するデータを取得するには、クロス積を 1 つの大きな投影として取得する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="6d1e5-107">ただし、多くの場合、この方法には欠点があります。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="6d1e5-108">たとえば、この結果は単なる射影であり、エンティティではないため、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] で変更して永続化することはできません。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="6d1e5-109">また、不要なデータが大量に取得される可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d1e5-110">例</span><span class="sxs-lookup"><span data-stu-id="6d1e5-110">Example</span></span>  

 <span data-ttu-id="6d1e5-111">次の例では、クエリを実行すると、ロンドンに住んでいるすべての `Orders` のすべての `Customers` が取得されます。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="6d1e5-112">その結果、それ以降 `Orders` オブジェクトの `Customer` プロパティにアクセスしても、新しいデータベース クエリは実行されません。</span><span class="sxs-lookup"><span data-stu-id="6d1e5-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6d1e5-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d1e5-113">See also</span></span>

- [<span data-ttu-id="6d1e5-114">データベースに対するクエリの実行</span><span class="sxs-lookup"><span data-stu-id="6d1e5-114">Querying the Database</span></span>](querying-the-database.md)
