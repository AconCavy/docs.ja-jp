---
title: '方法: Navigate 演算子でリレーションシップをナビゲートする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 79996d2d-9b03-4a9d-82cc-7c5e7c2ad93d
ms.openlocfilehash: dca8c25babcbc1676552af8ef49b7a7e71cd6136
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854531"
---
# <a name="how-to-navigate-relationships-with-the-navigate-operator"></a><span data-ttu-id="893ff-102">方法: Navigate 演算子でリレーションシップをナビゲートする</span><span class="sxs-lookup"><span data-stu-id="893ff-102">How to: Navigate Relationships with the Navigate Operator</span></span>
<span data-ttu-id="893ff-103">このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して概念モデルに対してコマンドを実行する方法と、<xref:System.Data.Metadata.Edm.RefType> を使用して <xref:System.Data.EntityClient.EntityDataReader> の結果を取得する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="893ff-103">This topic shows how to execute a command against a conceptual model by using an <xref:System.Data.EntityClient.EntityCommand> object, and how to retrieve the <xref:System.Data.Metadata.Edm.RefType> results by using an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="893ff-104">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="893ff-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="893ff-105">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="893ff-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="893ff-106">詳細については、[Entity Data Model ウィザードを使用する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="893ff-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="893ff-107">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="893ff-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="893ff-108">例</span><span class="sxs-lookup"><span data-stu-id="893ff-108">Example</span></span>  
 <span data-ttu-id="893ff-109">次の例では、[!INCLUDE[esql](../../../../../includes/esql-md.md)] で [NAVIGATE](./language-reference/navigate-entity-sql.md) 演算子を使用してリレーションシップをナビゲートする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="893ff-109">The following example shows how to navigate relationships in [!INCLUDE[esql](../../../../../includes/esql-md.md)] by using the [NAVIGATE](./language-reference/navigate-entity-sql.md) operator.</span></span> <span data-ttu-id="893ff-110">`Navigate` 演算子は、エンティティのインスタンス、リレーションシップの種類、リレーションシップの終端エンティティ、および、リレーションシップの開始エンティティをパラメーターとして受け取ります。</span><span class="sxs-lookup"><span data-stu-id="893ff-110">The `Navigate` operator takes the following parameters: an instance of an entity, the relationship type, the end of the relationship, and the beginning of the relationship.</span></span> <span data-ttu-id="893ff-111">必要に応じて、`Navigate` 演算子には、エンティティのインスタンスとリレーションシップの種類だけを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="893ff-111">Optionally, you can pass only an instance of an entity and the relationship type to the `Navigate` operator.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#navigatewithnavoperatorwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#NavigateWithNavOperatorWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#navigatewithnavoperatorwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="893ff-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="893ff-112">See also</span></span>

- [<span data-ttu-id="893ff-113">Entity Framework 用の EntityClient プロバイダー</span><span class="sxs-lookup"><span data-stu-id="893ff-113">EntityClient Provider for the Entity Framework</span></span>](entityclient-provider-for-the-entity-framework.md)
- [<span data-ttu-id="893ff-114">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="893ff-114">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
