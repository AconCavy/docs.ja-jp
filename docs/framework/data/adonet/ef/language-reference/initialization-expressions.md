---
title: 初期化式
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98daef1f-15d4-483e-985c-d78ea3abe8c8
ms.openlocfilehash: 93f590e1c177adf541baca85a48fee5f9eb8d1d0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203632"
---
# <a name="initialization-expressions"></a><span data-ttu-id="1e132-102">初期化式</span><span class="sxs-lookup"><span data-stu-id="1e132-102">Initialization Expressions</span></span>

<span data-ttu-id="1e132-103">初期化式は、新しいオブジェクトを初期化します。</span><span class="sxs-lookup"><span data-stu-id="1e132-103">An initialization expression initializes a new object.</span></span> <span data-ttu-id="1e132-104">初期化式は、ほとんどの新しい C# 3.0 および Visual Basic 9.0 初期化式を含め、ほとんどがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1e132-104">Most initialization expressions are supported, including most new C# 3.0 and Visual Basic 9.0 initialization expressions.</span></span> <span data-ttu-id="1e132-105">次の型は、LINQ to Entities クエリによって初期化して返すことができます。</span><span class="sxs-lookup"><span data-stu-id="1e132-105">The following types can be initialized and returned by a LINQ to Entities query:</span></span>  
  
- <span data-ttu-id="1e132-106">0 個以上の型指定されたエンティティ オブジェクトのコレクション、または概念モデルで定義された複合型のプロジェクション。</span><span class="sxs-lookup"><span data-stu-id="1e132-106">A collection of zero or more typed entity objects or a projection of complex types that are defined in the conceptual model.</span></span>  
  
- <span data-ttu-id="1e132-107">Entity Framework でサポートされる CLR 型。</span><span class="sxs-lookup"><span data-stu-id="1e132-107">CLR types supported by the Entity Framework.</span></span>
  
- <span data-ttu-id="1e132-108">インライン コレクション。</span><span class="sxs-lookup"><span data-stu-id="1e132-108">Inline collections.</span></span>  
  
- <span data-ttu-id="1e132-109">匿名型。</span><span class="sxs-lookup"><span data-stu-id="1e132-109">Anonymous types.</span></span>  
  
 <span data-ttu-id="1e132-110">クエリ式構文の次の例では、匿名型の初期化を示します。</span><span class="sxs-lookup"><span data-stu-id="1e132-110">Anonymous type initialization is shown in the following example in query expression syntax:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization)]  
  
 <span data-ttu-id="1e132-111">メソッドベースのクエリ構文の次の例では、匿名型の初期化を示します。</span><span class="sxs-lookup"><span data-stu-id="1e132-111">The following example in method-based query syntax shows anonymous type initialization:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#anonymoustypeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#AnonymousTypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#anonymoustypeinitialization_mq)]  
  
 <span data-ttu-id="1e132-112">ユーザー定義クラスの初期化もサポートされています。</span><span class="sxs-lookup"><span data-stu-id="1e132-112">User-defined class initialization is also supported.</span></span> <span data-ttu-id="1e132-113">C# 3.0 および Visual Basic 9.0 の初期化パターンがサポートされており、getter と setter のプロパティは対称であることが前提となります。</span><span class="sxs-lookup"><span data-stu-id="1e132-113">The C# 3.0 and Visual Basic 9.0 initialization pattern is supported and assumes that the property getter and setter are symmetric.</span></span> <span data-ttu-id="1e132-114">クエリ式構文の次の例では、クエリ内で初期化されるカスタム クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="1e132-114">The following example in query expression syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#myorder)]
 [!code-vb[DP L2E Conceptual Examples#MyOrder](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#myorder)]  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization)]  
  
 <span data-ttu-id="1e132-115">メソッドベース クエリ構文の次の例では、クエリ内で初期化されるカスタム クラスを示します。</span><span class="sxs-lookup"><span data-stu-id="1e132-115">The following example in method-based query syntax shows a custom class being initialized in the query:</span></span>  
  
 [!code-csharp[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#typeinitialization_mq)]
 [!code-vb[DP L2E Conceptual Examples#TypeInitialization_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#typeinitialization_mq)]  
  
## <a name="see-also"></a><span data-ttu-id="1e132-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1e132-116">See also</span></span>

- [<span data-ttu-id="1e132-117">LINQ to Entities クエリ内の式</span><span class="sxs-lookup"><span data-stu-id="1e132-117">Expressions in LINQ to Entities Queries</span></span>](expressions-in-linq-to-entities-queries.md)
