---
title: シーケンスの最初の要素の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: 9faeed754942d7b176872484ac776c1df592bbd8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792712"
---
# <a name="return-the-first-element-in-a-sequence"></a><span data-ttu-id="a7445-102">シーケンスの最初の要素の取得</span><span class="sxs-lookup"><span data-stu-id="a7445-102">Return the First Element in a Sequence</span></span>
<span data-ttu-id="a7445-103"><xref:System.Linq.Enumerable.First%2A> 演算子を使用すると、シーケンスの内最初の要素を返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a7445-103">Use the <xref:System.Linq.Enumerable.First%2A> operator to return the first element in a sequence.</span></span> <span data-ttu-id="a7445-104"><xref:System.Linq.Enumerable.First%2A> を使用するクエリは直ちに実行されます。</span><span class="sxs-lookup"><span data-stu-id="a7445-104">Queries that use <xref:System.Linq.Enumerable.First%2A> are executed immediately.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="a7445-105">は <xref:System.Linq.Enumerable.Last%2A> 演算子をサポートしません。</span><span class="sxs-lookup"><span data-stu-id="a7445-105">does not support the <xref:System.Linq.Enumerable.Last%2A> operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7445-106">例</span><span class="sxs-lookup"><span data-stu-id="a7445-106">Example</span></span>  
 <span data-ttu-id="a7445-107">次のコードは、テーブル内の最初の `Shipper` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="a7445-107">The following code finds the first `Shipper` in a table:</span></span>  
  
 <span data-ttu-id="a7445-108">Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a7445-108">If you run this query against the Northwind sample database, the results are</span></span>  
  
 <span data-ttu-id="a7445-109">`ID = 1, Company = Speedy Express`。</span><span class="sxs-lookup"><span data-stu-id="a7445-109">`ID = 1, Company = Speedy Express`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="a7445-110">例</span><span class="sxs-lookup"><span data-stu-id="a7445-110">Example</span></span>  
 <span data-ttu-id="a7445-111">次のコードは、`Customer` が BONAP の単一の `CustomerID` を見つけます。</span><span class="sxs-lookup"><span data-stu-id="a7445-111">The following code finds the single `Customer` that has the `CustomerID` BONAP.</span></span>  
  
 <span data-ttu-id="a7445-112">Northwind サンプル データベースに対してこのクエリを実行すると、結果は `ID = BONAP, Contact = Laurence Lebihan` になります。</span><span class="sxs-lookup"><span data-stu-id="a7445-112">If you run this query against the Northwind sample database, the results are `ID = BONAP, Contact = Laurence Lebihan`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="a7445-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="a7445-113">See also</span></span>

- [<span data-ttu-id="a7445-114">クエリの例</span><span class="sxs-lookup"><span data-stu-id="a7445-114">Query Examples</span></span>](query-examples.md)
- [<span data-ttu-id="a7445-115">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="a7445-115">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
