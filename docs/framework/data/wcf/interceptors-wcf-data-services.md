---
title: インターセプター (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: e33ae8dc-8069-41d0-99a0-75ff28db7050
ms.openlocfilehash: c9799037ae0ea8b29b5e989859aff29c310593d4
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568980"
---
# <a name="interceptors-wcf-data-services"></a><span data-ttu-id="a1e36-102">インターセプター (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="a1e36-102">Interceptors (WCF Data Services)</span></span>
<span data-ttu-id="a1e36-103">WCF Data Services では、アプリケーションで要求メッセージを先に取得して、操作にカスタム ロジックを追加することができます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-103">WCF Data Services enables an application to intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="a1e36-104">このカスタム ロジックを使用して、受信メッセージのデータを検証できます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-104">You can use this custom logic to validate data in incoming messages.</span></span> <span data-ttu-id="a1e36-105">このカスタム ロジックを使用して、クエリ要求の範囲をさらに制限することもできます (カスタム認証ポリシーを要求ごとに挿入するなど)。</span><span class="sxs-lookup"><span data-stu-id="a1e36-105">You can also use it to further restrict the scope of a query request, such as to insert a custom authorization policy on a per request basis.</span></span>  
  
 <span data-ttu-id="a1e36-106">先に取得するには、データ サービスで特別なメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a1e36-106">Interception is performed by specially attributed methods in the data service.</span></span> <span data-ttu-id="a1e36-107">これらのメソッドは、メッセージ処理の適切なポイントで WCF Data Services によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-107">These methods are called by WCF Data Services at the appropriate point in message processing.</span></span> <span data-ttu-id="a1e36-108">インターセプターはエンティティ セットごとに定義されます。インターセプター メソッドは、サービス操作が行うように要求からパラメーターを受け取ることはできません。</span><span class="sxs-lookup"><span data-stu-id="a1e36-108">Interceptors are defined on a per-entity set basis, and interceptor methods cannot accept parameters from the request like service operations can.</span></span> <span data-ttu-id="a1e36-109">HTTP GET 要求を処理するときに呼び出されるクエリ インターセプター メソッドは、クエリ要求に対してインターセプターのエンティティ セットを返すかどうかを決定するラムダ式を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e36-109">Query interceptor methods, which are called when processing an HTTP GET request, must return a lambda expression that determines whether an instance of the interceptor's entity set should be returned by the query results.</span></span> <span data-ttu-id="a1e36-110">この式は、要求された操作をさらに絞り込むためにデータ サービスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-110">This expression is used by the data service to further refine the requested operation.</span></span> <span data-ttu-id="a1e36-111">次の例は、クエリ インターセプターの定義の例を示します。</span><span class="sxs-lookup"><span data-stu-id="a1e36-111">The following is an example definition of a query interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
 [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
 <span data-ttu-id="a1e36-112">詳細については、[データ サービス メッセージを先に取得する](how-to-intercept-data-service-messages-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e36-112">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a1e36-113">クエリ以外の操作を処理するときに呼び出される変更インターセプターは、`void` (Visual Basic の場合は `Nothing`) を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e36-113">Change interceptors, which are called when processing non-query operations, must return `void` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="a1e36-114">変更インターセプター メソッドは、次の 2 つのパラメーターを受け取る必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e36-114">Change interceptor methods must accept the following two parameters:</span></span>  
  
1. <span data-ttu-id="a1e36-115">エンティティ セットのエンティティ型との互換性がある型のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="a1e36-115">A parameter of a type that is compatible with the entity type of the entity set.</span></span> <span data-ttu-id="a1e36-116">データ サービスが変更インターセプターを呼び出すとき、このパラメーターの値には、要求によって送信されたエンティティ情報が反映されます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-116">When the data service invokes the change interceptor, the value of this parameter will reflect the entity information that is sent by the request.</span></span>  
  
2. <span data-ttu-id="a1e36-117">型 <xref:System.Data.Services.UpdateOperations> のパラメーター。</span><span class="sxs-lookup"><span data-stu-id="a1e36-117">A parameter of type <xref:System.Data.Services.UpdateOperations>.</span></span> <span data-ttu-id="a1e36-118">データ サービスが変更インターセプターを呼び出すとき、このパラメーターの値には、要求が実行しようとしている操作が反映されます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-118">When the data service invokes the change interceptor, the value of this parameter will reflect the operation that the request is trying to perform.</span></span>  
  
 <span data-ttu-id="a1e36-119">次の例は、変更インターセプターの定義の例を示します。</span><span class="sxs-lookup"><span data-stu-id="a1e36-119">The following is an example definition of a change interceptor.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
 <span data-ttu-id="a1e36-120">詳細については、[データ サービス メッセージを先に取得する](how-to-intercept-data-service-messages-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e36-120">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a1e36-121">先に取得する処理には、次の属性がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-121">The following attributes are supported for interception.</span></span>  
  
 <span data-ttu-id="a1e36-122">**[QueryInterceptor(** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="a1e36-122">**[QueryInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="a1e36-123">ターゲットのエンティティ セット リソースに対する HTTP GET 要求が受信されると、<xref:System.Data.Services.QueryInterceptorAttribute> 属性が適用されたメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-123">Methods with the <xref:System.Data.Services.QueryInterceptorAttribute> attribute applied are called when an HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="a1e36-124">これらのメソッドは、常に `Expression<Func<T,bool>>` の形式のラムダ式を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1e36-124">These methods must always return a lambda expression in the form of `Expression<Func<T,bool>>`.</span></span>  
  
 <span data-ttu-id="a1e36-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span><span class="sxs-lookup"><span data-stu-id="a1e36-125">**[ChangeInterceptor(** *EntitySetName* **)]**</span></span>  
 <span data-ttu-id="a1e36-126">ターゲットのエンティティ セット リソースに対する HTTP GET 以外の HTTP 要求が受信されると、<xref:System.Data.Services.ChangeInterceptorAttribute> 属性が適用されたメソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a1e36-126">Methods with the <xref:System.Data.Services.ChangeInterceptorAttribute> attribute applied are called when an HTTP request other than HTTP GET request is received for the targeted entity set resource.</span></span> <span data-ttu-id="a1e36-127">これらのメソッドは、常に `void` (Visual Basic の場合は `Nothing`) を返します。</span><span class="sxs-lookup"><span data-stu-id="a1e36-127">These methods must always return `void` (`Nothing` in Visual Basic).</span></span>  
  
 <span data-ttu-id="a1e36-128">詳細については、[データ サービス メッセージを先に取得する](how-to-intercept-data-service-messages-wcf-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a1e36-128">For more information, see [How to: Intercept Data Service Messages](how-to-intercept-data-service-messages-wcf-data-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e36-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1e36-129">See also</span></span>

- [<span data-ttu-id="a1e36-130">サービス操作</span><span class="sxs-lookup"><span data-stu-id="a1e36-130">Service Operations</span></span>](service-operations-wcf-data-services.md)
