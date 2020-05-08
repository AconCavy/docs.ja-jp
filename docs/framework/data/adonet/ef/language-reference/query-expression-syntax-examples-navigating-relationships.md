---
title: クエリ式の構文例:リレーションシップの操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0d4a7f41-c758-4059-8f83-d2e9c2745593
ms.openlocfilehash: a99d7d31ce23629bf7a0f390244c1fe67b4554e3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854409"
---
# <a name="query-expression-syntax-examples-navigating-relationships"></a><span data-ttu-id="5a490-102">クエリ式の構文例:リレーションシップの操作</span><span class="sxs-lookup"><span data-stu-id="5a490-102">Query Expression Syntax Examples: Navigating Relationships</span></span>
<span data-ttu-id="5a490-103">Entity Framework のナビゲーション プロパティは、アソシエーションの末尾にあるエンティティを見つけるために使用できるショートカット プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5a490-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="5a490-104">ナビゲーション プロパティを使用すると、ユーザーは、エンティティ間をナビゲートしたり、あるエンティティからアソシエーション セットを介して関連エンティティにナビゲートしたりできます。</span><span class="sxs-lookup"><span data-stu-id="5a490-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="5a490-105">このトピックでは、LINQ to Entities のクエリ内でナビゲーション プロパティを介してリレーションシップをナビゲートするためのクエリ式の構文例を示します。</span><span class="sxs-lookup"><span data-stu-id="5a490-105">This topic provides examples in query expression syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="5a490-106">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="5a490-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="5a490-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="5a490-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="5a490-108">例</span><span class="sxs-lookup"><span data-stu-id="5a490-108">Example</span></span>  
 <span data-ttu-id="5a490-109">次の例では、<xref:System.Linq.Queryable.Select%2A> メソッドを使用して、姓が "Zhou" である連絡先のすべての連絡先 ID と、各連絡先の合計支払額の総計を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a490-109">The following example uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="5a490-110">`Contact.SalesOrderHeader` ナビゲーション プロパティは、各連絡先の `SalesOrderHeader` オブジェクトのコレクションを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5a490-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="5a490-111">`Sum` メソッドは、`Contact.SalesOrderHeader` ナビゲーション プロパティを使用して、それぞれの連絡先のすべての注文の合計支払額を合計します。</span><span class="sxs-lookup"><span data-stu-id="5a490-111">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2)]  
  
## <a name="example"></a><span data-ttu-id="5a490-112">例</span><span class="sxs-lookup"><span data-stu-id="5a490-112">Example</span></span>  
 <span data-ttu-id="5a490-113">次の例では、姓が "Zhou" である連絡先のすべての注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a490-113">The following example gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="5a490-114">`Contact.SalesOrderHeader` ナビゲーション プロパティは、各連絡先の `SalesOrderHeader` オブジェクトのコレクションを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="5a490-114">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="5a490-115">連絡先の名前と注文が匿名型で返されます。</span><span class="sxs-lookup"><span data-stu-id="5a490-115">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3)]  
  
## <a name="example"></a><span data-ttu-id="5a490-116">例</span><span class="sxs-lookup"><span data-stu-id="5a490-116">Example</span></span>  
 <span data-ttu-id="5a490-117">次の例では、`SalesOrderHeader.Address` ナビゲーション プロパティと `SalesOrderHeader.Contact` ナビゲーション プロパティを使用して、互いに関連付けられている `Address` オブジェクトと `Contact` オブジェクトのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a490-117">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="5a490-118">各注文の連絡先の姓、住所、販売注文番号、および Seattle 市に対する合計支払額が匿名型で返されます。</span><span class="sxs-lookup"><span data-stu-id="5a490-118">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships)]  
  
### <a name="example"></a><span data-ttu-id="5a490-119">例</span><span class="sxs-lookup"><span data-stu-id="5a490-119">Example</span></span>  
 <span data-ttu-id="5a490-120">次の例では、`Where` メソッドを使用して、2003 年 12 月 1 日以降に受けた注文を検索します。次に、`order.SalesOrderDetail` ナビゲーション プロパティを使用して、各注文の詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="5a490-120">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="5a490-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a490-121">See also</span></span>

- [<span data-ttu-id="5a490-122">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="5a490-122">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
