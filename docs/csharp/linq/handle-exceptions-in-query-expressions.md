---
title: クエリ式の例外の処理 (C# での LINQ)
description: C# で LINQ クエリ式の例外を処理する方法について説明します。
ms.date: 12/01/2016
ms.assetid: 2bf0c397-13fb-4f68-bc2b-531c6c88a167
ms.openlocfilehash: f900669412026e69598d3939c51ff8208b51b7ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "61688502"
---
# <a name="handle-exceptions-in-query-expressions"></a><span data-ttu-id="d6d08-103">クエリ式の例外の処理</span><span class="sxs-lookup"><span data-stu-id="d6d08-103">Handle exceptions in query expressions</span></span>

<span data-ttu-id="d6d08-104">クエリ式のコンテキストで任意のメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d6d08-104">It's possible to call any method in the context of a query expression.</span></span> <span data-ttu-id="d6d08-105">ただし、データ ソースのコンテンツが変更されたり例外がスローされたりするなどの副作用が生じる可能性のあるクエリ式では、メソッドを呼び出さないようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="d6d08-105">However, we recommend that you avoid calling any method in a query expression that can create a side effect such as modifying the contents of the data source or throwing an exception.</span></span> <span data-ttu-id="d6d08-106">この例では、クエリ式でメソッドを呼び出すときに、例外処理に関する .NET の全般的なガイドラインに違反することなく例外の発生を避ける方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d6d08-106">This example shows how to avoid raising exceptions when you call methods in a query expression without violating the general .NET guidelines on exception handling.</span></span> <span data-ttu-id="d6d08-107">ガイドラインでは、特定のコンテキストで特定の例外がスローされる理由がわかっているときにその例外をキャッチすることは認められています。</span><span class="sxs-lookup"><span data-stu-id="d6d08-107">Those guidelines state that it's acceptable to catch a specific exception when you understand why it's thrown in a given context.</span></span> <span data-ttu-id="d6d08-108">詳細については、「[例外の推奨事項](../../standard/exceptions/best-practices-for-exceptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6d08-108">For more information, see [Best Practices for Exceptions](../../standard/exceptions/best-practices-for-exceptions.md).</span></span>

<span data-ttu-id="d6d08-109">最後の例では、クエリの実行中に例外をスローする必要がある場合の処理方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d6d08-109">The final example shows how to handle those cases when you must throw an exception during execution of a query.</span></span>

## <a name="example"></a><span data-ttu-id="d6d08-110">例</span><span class="sxs-lookup"><span data-stu-id="d6d08-110">Example</span></span>

<span data-ttu-id="d6d08-111">次の例では、例外処理コードをクエリ式の外側に移動する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d6d08-111">The following example shows how to move exception handling code outside a query expression.</span></span> <span data-ttu-id="d6d08-112">この方法は、メソッドがクエリのローカル変数に依存しない場合にのみ可能です。</span><span class="sxs-lookup"><span data-stu-id="d6d08-112">This is only possible when the method does not depend on any variables local to the query.</span></span>

[!code-csharp[csProgGuideLINQ#10](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_1.cs)]

## <a name="example"></a><span data-ttu-id="d6d08-113">例</span><span class="sxs-lookup"><span data-stu-id="d6d08-113">Example</span></span>

<span data-ttu-id="d6d08-114">場合によっては、クエリ内からスローされる例外に対する最適な応答は、クエリの実行をすぐに停止することです。</span><span class="sxs-lookup"><span data-stu-id="d6d08-114">In some cases, the best response to an exception that is thrown from within a query might be to stop the query execution immediately.</span></span> <span data-ttu-id="d6d08-115">次の例では、クエリ本体の内部からスローされる例外を処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d6d08-115">The following example shows how to handle exceptions that might be thrown from inside a query body.</span></span> <span data-ttu-id="d6d08-116">`SomeMethodThatMightThrow` で、クエリの実行を停止することが必要な例外が発生する可能性があるとします。</span><span class="sxs-lookup"><span data-stu-id="d6d08-116">Assume that `SomeMethodThatMightThrow` can potentially cause an exception that requires the query execution to stop.</span></span>

<span data-ttu-id="d6d08-117">`try` ブロックは `foreach` ループを囲み、クエリ自体を囲むのではありません。</span><span class="sxs-lookup"><span data-stu-id="d6d08-117">Note that the `try` block encloses the `foreach` loop, and not the query itself.</span></span> <span data-ttu-id="d6d08-118">その理由は、`foreach` ループがクエリの実際の実行ポイントであるためです。</span><span class="sxs-lookup"><span data-stu-id="d6d08-118">This is because the `foreach` loop is the point at which the query is actually executed.</span></span> <span data-ttu-id="d6d08-119">詳細については、「[LINQ クエリの概要](../programming-guide/concepts/linq/introduction-to-linq-queries.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6d08-119">For more information, see [Introduction to LINQ queries](../programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>

[!code-csharp[csProgGuideLINQ#12](~/samples/snippets/csharp/concepts/linq/how-to-handle-exceptions-in-query-expressions_2.cs)]

## <a name="see-also"></a><span data-ttu-id="d6d08-120">参照</span><span class="sxs-lookup"><span data-stu-id="d6d08-120">See also</span></span>

- [<span data-ttu-id="d6d08-121">統合言語クエリ (LINQ)</span><span class="sxs-lookup"><span data-stu-id="d6d08-121">Language Integrated Query (LINQ)</span></span>](index.md)
