---
title: メソッド ベースのクエリ構文例:リレーションシップの操作
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a0bfa4b1-99e5-4dd1-9912-4b825a9dc25c
ms.openlocfilehash: bb40d10165592b25cc6afc1eac799a05b4504e8d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191971"
---
# <a name="method-based-query-syntax-examples-navigating-relationships"></a><span data-ttu-id="718ec-102">メソッド ベースのクエリ構文例:リレーションシップの操作</span><span class="sxs-lookup"><span data-stu-id="718ec-102">Method-Based Query Syntax Examples: Navigating Relationships</span></span>

<span data-ttu-id="718ec-103">Entity Framework のナビゲーション プロパティは、アソシエーションの末尾にあるエンティティを見つけるために使用できるショートカット プロパティです。</span><span class="sxs-lookup"><span data-stu-id="718ec-103">Navigation properties in the Entity Framework are shortcut properties used to locate the entities at the ends of an association.</span></span> <span data-ttu-id="718ec-104">ナビゲーション プロパティを使用すると、ユーザーは、エンティティ間をナビゲートしたり、あるエンティティからアソシエーション セットを介して関連エンティティにナビゲートしたりできます。</span><span class="sxs-lookup"><span data-stu-id="718ec-104">Navigation properties allow a user to navigate from one entity to another, or from one entity to related entities through an association set.</span></span> <span data-ttu-id="718ec-105">このトピックでは、LINQ to Entities のクエリ内でナビゲーション プロパティを介してリレーションシップをナビゲートするためのメソッド ベースのクエリ構文の例を示します。</span><span class="sxs-lookup"><span data-stu-id="718ec-105">This topic provides examples in method-based query syntax of how to navigate relationships through navigation properties in LINQ to Entities queries.</span></span>  
  
 <span data-ttu-id="718ec-106">これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。</span><span class="sxs-lookup"><span data-stu-id="718ec-106">The AdventureWorks Sales Model used in these examples is built from the Contact, Address, Product, SalesOrderHeader, and SalesOrderDetail tables in the AdventureWorks sample database.</span></span>  
  
 <span data-ttu-id="718ec-107">このトピックの例には、次の `using`/`Imports` ステートメントが使用されています。</span><span class="sxs-lookup"><span data-stu-id="718ec-107">The examples in this topic use the following `using`/`Imports` statements:</span></span>  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="example"></a><span data-ttu-id="718ec-108">例</span><span class="sxs-lookup"><span data-stu-id="718ec-108">Example</span></span>  

 <span data-ttu-id="718ec-109">次の例では、メソッドベースのクエリ構文で <xref:System.Linq.Queryable.SelectMany%2A> メソッドを使用して、姓が "Zhou" である連絡先のすべての注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="718ec-109">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.SelectMany%2A> method to get all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="718ec-110">`Contact.SalesOrderHeader` ナビゲーション プロパティは、各連絡先の `SalesOrderHeader` オブジェクトのコレクションを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="718ec-110">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders_mq)]  
  
## <a name="example"></a><span data-ttu-id="718ec-111">例</span><span class="sxs-lookup"><span data-stu-id="718ec-111">Example</span></span>  

 <span data-ttu-id="718ec-112">次の例では、メソッドベースのクエリ構文で <xref:System.Linq.Queryable.Select%2A> メソッドを使用して、姓が "Zhou" である連絡先のすべての連絡先 ID と、各連絡先の合計支払額の総計を取得します。</span><span class="sxs-lookup"><span data-stu-id="718ec-112">The following example in method-based query syntax uses the <xref:System.Linq.Queryable.Select%2A> method to get all the contact IDs and the sum of the total due for each contact whose last name is "Zhou".</span></span> <span data-ttu-id="718ec-113">`Contact.SalesOrderHeader` ナビゲーション プロパティは、各連絡先の `SalesOrderHeader` オブジェクトのコレクションを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="718ec-113">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="718ec-114">`Sum` メソッドは、`Contact.SalesOrderHeader` ナビゲーション プロパティを使用して、それぞれの連絡先のすべての注文の合計支払額を合計します。</span><span class="sxs-lookup"><span data-stu-id="718ec-114">The `Sum` method uses the `Contact.SalesOrderHeader` navigation property to sum the total due of all the orders for each contact.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders2_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders2_mq)]  
  
## <a name="example"></a><span data-ttu-id="718ec-115">例</span><span class="sxs-lookup"><span data-stu-id="718ec-115">Example</span></span>  

 <span data-ttu-id="718ec-116">次の例では、メソッド ベースのクエリ構文を使用し、姓が "Zhou" である連絡先のすべての注文を取得します。</span><span class="sxs-lookup"><span data-stu-id="718ec-116">The following example in method-based query syntax gets all the orders of the contacts whose last name is "Zhou".</span></span> <span data-ttu-id="718ec-117">`Contact.SalesOrderHeader` ナビゲーション プロパティは、各連絡先の `SalesOrderHeader` オブジェクトのコレクションを取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="718ec-117">The `Contact.SalesOrderHeader` navigation property is used to get the collection of `SalesOrderHeader` objects for each contact.</span></span> <span data-ttu-id="718ec-118">連絡先の名前と注文が匿名型で返されます。</span><span class="sxs-lookup"><span data-stu-id="718ec-118">The contact's name and orders are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#selecteachcontactsorders3_mq)]
 [!code-vb[DP L2E Examples#SelectEachContactsOrders3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#selecteachcontactsorders3_mq)]  
  
## <a name="example"></a><span data-ttu-id="718ec-119">例</span><span class="sxs-lookup"><span data-stu-id="718ec-119">Example</span></span>  

 <span data-ttu-id="718ec-120">次の例では、`SalesOrderHeader.Address` ナビゲーション プロパティと `SalesOrderHeader.Contact` ナビゲーション プロパティを使用して、互いに関連付けられている `Address` オブジェクトと `Contact` オブジェクトのコレクションを取得します。</span><span class="sxs-lookup"><span data-stu-id="718ec-120">The following example uses the `SalesOrderHeader.Address` and `SalesOrderHeader.Contact` navigation properties to get the collection of `Address` and `Contact` objects associated with each order.</span></span> <span data-ttu-id="718ec-121">各注文の連絡先の姓、住所、販売注文番号、および Seattle 市に対する合計支払額が匿名型で返されます。</span><span class="sxs-lookup"><span data-stu-id="718ec-121">The last name of the contact, the street address, the sales order number, and the total due for each order to the city of Seattle are returned in an anonymous type.</span></span>  
  
 [!code-csharp[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#getorderinfothrurelationships_mq)]
 [!code-vb[DP L2E Examples#GetOrderInfoThruRelationships_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#getorderinfothrurelationships_mq)]  
  
## <a name="example"></a><span data-ttu-id="718ec-122">例</span><span class="sxs-lookup"><span data-stu-id="718ec-122">Example</span></span>  

 <span data-ttu-id="718ec-123">次の例では、`Where` メソッドを使用して、2003 年 12 月 1 日以降に受けた注文を検索します。次に、`order.SalesOrderDetail` ナビゲーション プロパティを使用して、各注文の詳細を取得します。</span><span class="sxs-lookup"><span data-stu-id="718ec-123">The following example uses the `Where` method to find orders that were made after December 1, 2003, and then uses the `order.SalesOrderDetail` navigation property to get the details for each order.</span></span>  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty)]
 [!code-vb[DP L2E Examples#WhereNavProperty](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty)]  
  
## <a name="see-also"></a><span data-ttu-id="718ec-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="718ec-124">See also</span></span>

- [<span data-ttu-id="718ec-125">リレーションシップ、ナビゲーション プロパティ、および外部キー</span><span class="sxs-lookup"><span data-stu-id="718ec-125">Relationships, navigation properties and foreign keys</span></span>](/ef/ef6/fundamentals/relationships)
- [<span data-ttu-id="718ec-126">LINQ to Entities でのクエリ</span><span class="sxs-lookup"><span data-stu-id="718ec-126">Queries in LINQ to Entities</span></span>](queries-in-linq-to-entities.md)
