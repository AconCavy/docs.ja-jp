---
title: '方法: クエリ (WCF Data Services) によって返されるエンティティの数を決定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, row count
ms.assetid: 03d41a82-df95-40ac-8439-a6c327d37ba8
ms.openlocfilehash: f723d91dd30817f6e15be11dd1bc1432a5939647
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774635"
---
# <a name="how-to-determine-the-number-of-entities-returned-by-a-query-wcf-data-services"></a>方法: クエリ (WCF Data Services) によって返されるエンティティの数を決定します。
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] を使用すると、クエリ URI によって指定されたエンティティ セット内のエンティティの数を確認できます。 この数は、クエリ結果と一緒に、または整数値として含まれます。 詳細については、次を参照してください。[データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスを作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> メソッドを呼び出した後でクエリを実行します。 <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> プロパティが、`Customers` エンティティ セット内のエンティティの数を返します。  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomers)]
 [!code-vb[Astoria Northwind Client#CountAllCustomers](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomers)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Linq.Enumerable.Count%2A> エンティティ セット内のエンティティの数である整数値のみを返す `Customers` メソッドを呼び出します。  
  
 [!code-csharp[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#countallcustomersvalueonly)]
 [!code-vb[Astoria Northwind Client#CountAllCustomersValueOnly](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#countallcustomersvalueonly)]  
  
## <a name="see-also"></a>関連項目

- [データ サービスに対するクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
