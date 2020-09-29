---
title: シーケンスのすべての要素が条件を満たしているかどうかの確認
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 65a9a7cf289c2006bab14cb384efb07eaea7f7a0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194428"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="8b8b7-102">シーケンスのすべての要素が条件を満たしているかどうかの確認</span><span class="sxs-lookup"><span data-stu-id="8b8b7-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>

<span data-ttu-id="8b8b7-103"><xref:System.Linq.Enumerable.All%2A> 演算子は、シーケンスのすべての要素が条件を満たす場合に `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="8b8b7-104"><xref:System.Linq.Queryable.Any%2A> 演算子は、シーケンスの要素が 1 つでも条件を満たす場合に `true` を返します。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b8b7-105">例</span><span class="sxs-lookup"><span data-stu-id="8b8b7-105">Example</span></span>  

 <span data-ttu-id="8b8b7-106">次の例では、最低 1 件の注文がある顧客のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="8b8b7-107">`Where`/`where` 句は、指定した `Customer` に `Order` がある場合に `true` と評価されます。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="8b8b7-108">例</span><span class="sxs-lookup"><span data-stu-id="8b8b7-108">Example</span></span>  

 <span data-ttu-id="8b8b7-109">次の Visual Basic コードでは、注文がない顧客のリストを調べ、リストに記載されている顧客に連絡先名があることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="8b8b7-110">例</span><span class="sxs-lookup"><span data-stu-id="8b8b7-110">Example</span></span>  

 <span data-ttu-id="8b8b7-111">次の C# コードでは、注文の `ShipCity` が "C" で始まる顧客のシーケンスを返します。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="8b8b7-112">注文のない顧客も結果に含まれます。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="8b8b7-113">(<xref:System.Linq.Queryable.All%2A> 演算子はシーケンスが空の場合に `true` を返すように設計されています)。注文のない顧客を削除してコンソールに出力するには、`Count` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="8b8b7-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="8b8b7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b8b7-114">See also</span></span>

- [<span data-ttu-id="8b8b7-115">クエリの例</span><span class="sxs-lookup"><span data-stu-id="8b8b7-115">Query Examples</span></span>](query-examples.md)
