---
title: '方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e93fea43-7e03-4d7d-9fee-2517b8b88cba
ms.openlocfilehash: aa750ef088ee045c8d1045b2509d8fc4bde014ce
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854628"
---
# <a name="how-to-execute-a-parameterized-entity-sql-query-using-entitycommand"></a><span data-ttu-id="6ed59-102">方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行する</span><span class="sxs-lookup"><span data-stu-id="6ed59-102">How to: Execute a Parameterized Entity SQL Query Using EntityCommand</span></span>
<span data-ttu-id="6ed59-103">このトピックでは、<xref:System.Data.EntityClient.EntityCommand> オブジェクトを使用して、パラメーターのある [!INCLUDE[esql](../../../../../includes/esql-md.md)] クエリを実行する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6ed59-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that has parameters by using an <xref:System.Data.EntityClient.EntityCommand> object.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="6ed59-104">この例のコードを実行するには</span><span class="sxs-lookup"><span data-stu-id="6ed59-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="6ed59-105">[AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) をプロジェクトに追加し、Entity Framework が使用されるようにプロジェクトを構成します。</span><span class="sxs-lookup"><span data-stu-id="6ed59-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="6ed59-106">詳細については、[Entity Data Model ウィザードを使用する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6ed59-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="6ed59-107">アプリケーションのコード ページで、次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。</span><span class="sxs-lookup"><span data-stu-id="6ed59-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
## <a name="example"></a><span data-ttu-id="6ed59-108">例</span><span class="sxs-lookup"><span data-stu-id="6ed59-108">Example</span></span>  
 <span data-ttu-id="6ed59-109">次の例では、2 つのパラメーターを持つクエリ文字列を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6ed59-109">The following example shows how to construct a query string with two parameters.</span></span> <span data-ttu-id="6ed59-110">次に、<xref:System.Data.EntityClient.EntityCommand> を作成した後、2 つのパラメーターを <xref:System.Data.EntityClient.EntityParameter> の <xref:System.Data.EntityClient.EntityCommand> コレクションに追加し、`Contact` アイテムのコレクションに対して反復処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="6ed59-110">It then creates an <xref:System.Data.EntityClient.EntityCommand>, adds two parameters to the <xref:System.Data.EntityClient.EntityParameter> collection of that <xref:System.Data.EntityClient.EntityCommand>, and iterates through the collection of `Contact` items.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#parameterizedquerywithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ParameterizedQueryWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#parameterizedquerywithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="6ed59-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="6ed59-111">See also</span></span>

- <span data-ttu-id="6ed59-112">[方法: パラメーター化されたクエリを実行する](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="6ed59-112">[How to: Execute a Parameterized Query](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))</span></span>
- [<span data-ttu-id="6ed59-113">Entity SQL 言語</span><span class="sxs-lookup"><span data-stu-id="6ed59-113">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
