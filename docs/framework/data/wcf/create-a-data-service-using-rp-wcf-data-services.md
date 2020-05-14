---
title: '方法: リフレクション プロバイダーを使用してデータ サービスを作成する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: cf20c1d27f22c0248217541763eaa617ed9493db
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569290"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="9adc0-102">方法: リフレクション プロバイダーを使用してデータ サービスを作成する (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9adc0-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
<span data-ttu-id="9adc0-103">WCF Data Services では、<xref:System.Linq.IQueryable%601> インターフェイスを実装するオブジェクトとして公開されているクラスに基づいてデータ モデルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="9adc0-103">WCF Data Services enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="9adc0-104">詳細については、「[Data Services プロバイダー](data-services-providers-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9adc0-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9adc0-105">例</span><span class="sxs-lookup"><span data-stu-id="9adc0-105">Example</span></span>  
 <span data-ttu-id="9adc0-106">次の例は、`Orders` および `Items` を含むデータ モデルを定義します。</span><span class="sxs-lookup"><span data-stu-id="9adc0-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="9adc0-107">エンティティ コンテナー クラス `OrderItemData` には、<xref:System.Linq.IQueryable%601> インターフェイスを返す 2 つのパブリック メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="9adc0-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="9adc0-108">これらのインターフェイスは、`Orders` エンティティ型と `Items` エンティティ型のエンティティ セットです。</span><span class="sxs-lookup"><span data-stu-id="9adc0-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="9adc0-109">`Order` には複数の `Items` を含めることができるので、`Orders` エンティティ型には `Items` オブジェクトのコレクションを返す `Items` ナビゲーション プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="9adc0-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="9adc0-110">`OrderItemData` エンティティ コンテナー クラスは、<xref:System.Data.Services.DataService%601> データ サービスが派生する `OrderItems` クラスのジェネリック型です。</span><span class="sxs-lookup"><span data-stu-id="9adc0-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9adc0-111">この例はメモリ内のデータ プロバイダーを示し、変更は現在のオブジェクト インスタンスの外部で永続化されないので、<xref:System.Data.Services.IUpdatable> インターフェイスを実装する利点はありません。</span><span class="sxs-lookup"><span data-stu-id="9adc0-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="9adc0-112"><xref:System.Data.Services.IUpdatable> インターフェイスを実装する例については、「[方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する](create-a-data-service-using-linq-to-sql-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9adc0-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="9adc0-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9adc0-113">See also</span></span>

- [<span data-ttu-id="9adc0-114">方法: LINQ to SQL データ ソースを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="9adc0-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="9adc0-115">Data Services プロバイダー</span><span class="sxs-lookup"><span data-stu-id="9adc0-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="9adc0-116">方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="9adc0-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
