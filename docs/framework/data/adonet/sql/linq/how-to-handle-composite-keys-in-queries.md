---
title: '方法: クエリで複合キーを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: bc16dde89f67572b03102b1c091993ed163b443c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203528"
---
# <a name="how-to-handle-composite-keys-in-queries"></a><span data-ttu-id="97e2d-102">方法: クエリで複合キーを処理する</span><span class="sxs-lookup"><span data-stu-id="97e2d-102">How to: Handle Composite Keys in Queries</span></span>

<span data-ttu-id="97e2d-103">演算子によっては、引数を 1 つしか受け取らないものがあります。</span><span class="sxs-lookup"><span data-stu-id="97e2d-103">Some operators can take only one argument.</span></span> <span data-ttu-id="97e2d-104">1 つの演算子にデータベースの複数の列を含めるには、その組み合わせを表す匿名型を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="97e2d-104">If your argument must include more than one column from the database, you must create an anonymous type to represent the combination.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97e2d-105">例</span><span class="sxs-lookup"><span data-stu-id="97e2d-105">Example</span></span>  

 <span data-ttu-id="97e2d-106">`GroupBy` 演算子を使用するクエリを次の例に示します。この演算子は、1 つの `key` 引数だけを受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="97e2d-106">The following example shows a query that invokes the `GroupBy` operator, which can take only one `key` argument.</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="97e2d-107">例</span><span class="sxs-lookup"><span data-stu-id="97e2d-107">Example</span></span>  

 <span data-ttu-id="97e2d-108">次の例に示すように、結合の場合も同様です。</span><span class="sxs-lookup"><span data-stu-id="97e2d-108">The same situation pertains to joins, as in the following example:</span></span>  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="97e2d-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="97e2d-109">See also</span></span>

- [<span data-ttu-id="97e2d-110">クエリの概念</span><span class="sxs-lookup"><span data-stu-id="97e2d-110">Query Concepts</span></span>](query-concepts.md)
