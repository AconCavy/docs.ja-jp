---
title: メソッドからクエリを返す
description: クエリを返す方法。
ms.date: 11/30/2016
ms.assetid: db220f79-c35b-41f2-886c-cd068672d42d
ms.openlocfilehash: 646e771d637aa242231e3fe216d4a856bb156649
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203333"
---
# <a name="how-to-return-a-query-from-a-method-c-programming-guide"></a><span data-ttu-id="6a006-103">メソッドからクエリを返す方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="6a006-103">How to return a query from a method (C# Programming Guide)</span></span>

<span data-ttu-id="6a006-104">この例では、メソッドから、クエリを戻り値として返す方法と `out` パラメーターとして返す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="6a006-104">This example shows how to return a query from a method as the return value and as an `out` parameter.</span></span>  
  
 <span data-ttu-id="6a006-105">クエリ オブジェクトはコンポーザブルです。つまり、メソッドからクエリを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="6a006-105">Query objects are composable, meaning that you can return a query from a method.</span></span> <span data-ttu-id="6a006-106">クエリを表すオブジェクトには、結果のコレクションではなく、必要に応じて結果を生成する手順が格納されます。</span><span class="sxs-lookup"><span data-stu-id="6a006-106">Objects that represent queries do not store the resulting collection, but rather the steps to produce the results when needed.</span></span> <span data-ttu-id="6a006-107">メソッドからクエリ オブジェクトを返すメリットは、そのオブジェクトをさらに構成したり変更したりできることです。</span><span class="sxs-lookup"><span data-stu-id="6a006-107">The advantage of returning query objects from methods is that they can be further composed or modified.</span></span> <span data-ttu-id="6a006-108">そのため、クエリを返すメソッドの戻り値または `out` パラメーターも同じ型である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6a006-108">Therefore any return value or `out` parameter of a method that returns a query must also have that type.</span></span> <span data-ttu-id="6a006-109">メソッドがクエリを具象型 <xref:System.Collections.Generic.List%601> または <xref:System.Array> に実体化する場合は、そのメソッドは、クエリ自体ではなくクエリ結果を返すと見なされます。</span><span class="sxs-lookup"><span data-stu-id="6a006-109">If a method materializes a query into a concrete <xref:System.Collections.Generic.List%601> or <xref:System.Array> type, it is considered to be returning the query results instead of the query itself.</span></span> <span data-ttu-id="6a006-110">メソッドから返されたクエリ変数は、引き続き構成または変更できます。</span><span class="sxs-lookup"><span data-stu-id="6a006-110">A query variable that is returned from a method can still be composed or modified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a006-111">例</span><span class="sxs-lookup"><span data-stu-id="6a006-111">Example</span></span>  

 <span data-ttu-id="6a006-112">次の例は、最初のメソッドはクエリを戻り値として返し、2 番目のメソッドはクエリを `out` パラメーターとして返しています。</span><span class="sxs-lookup"><span data-stu-id="6a006-112">In the following example, the first method returns a query as a return value, and the second method returns a query as an `out` parameter.</span></span> <span data-ttu-id="6a006-113">どちらの場合も返されるのはクエリであり、クエリ結果ではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="6a006-113">Note that in both cases it is a query that is  returned, not query results.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#80](~/samples/snippets/csharp/concepts/linq/how-to-return-a-query-from-a-method_1.cs)]  

## <a name="see-also"></a><span data-ttu-id="6a006-114">参照</span><span class="sxs-lookup"><span data-stu-id="6a006-114">See also</span></span>

- [<span data-ttu-id="6a006-115">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6a006-115">Language Integrated Query (LINQ)</span></span>](index.md)
