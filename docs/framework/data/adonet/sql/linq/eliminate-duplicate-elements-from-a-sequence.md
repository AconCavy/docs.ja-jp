---
title: シーケンスからの重複する要素の削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 9b8e19ac76869c33d01a59ee3aad104a7ddbb8f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782218"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a><span data-ttu-id="3eb12-102">シーケンスからの重複する要素の削除</span><span class="sxs-lookup"><span data-stu-id="3eb12-102">Eliminate Duplicate Elements from a Sequence</span></span>
<span data-ttu-id="3eb12-103">重複する要素をシーケンスから削除するには、<xref:System.Linq.Queryable.Distinct%2A> 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="3eb12-103">Use the <xref:System.Linq.Queryable.Distinct%2A> operator to eliminate duplicate elements from a sequence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3eb12-104">例</span><span class="sxs-lookup"><span data-stu-id="3eb12-104">Example</span></span>  
 <span data-ttu-id="3eb12-105">次の例では、<xref:System.Linq.Queryable.Distinct%2A> を使用して、顧客の住所がある市のシーケンスを選択します。それぞれの市はシーケンス内で重複しません。</span><span class="sxs-lookup"><span data-stu-id="3eb12-105">The following example uses <xref:System.Linq.Queryable.Distinct%2A> to select a sequence of the unique cities that have customers.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a><span data-ttu-id="3eb12-106">関連項目</span><span class="sxs-lookup"><span data-stu-id="3eb12-106">See also</span></span>

- [<span data-ttu-id="3eb12-107">クエリの例</span><span class="sxs-lookup"><span data-stu-id="3eb12-107">Query Examples</span></span>](query-examples.md)
