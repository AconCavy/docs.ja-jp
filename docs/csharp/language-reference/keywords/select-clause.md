---
title: select 句 - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- select_CSharpKeyword
- select
helpviewer_keywords:
- select keyword [C#]
- select clause [C#]
ms.assetid: df01e266-5781-4aaa-80c4-67cf28ea093f
ms.openlocfilehash: b4d25f80e4cdb08fbc28fa4db3cb1c790b1145e6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713093"
---
# <a name="select-clause-c-reference"></a><span data-ttu-id="6bd19-102">select 句 (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6bd19-102">select clause (C# Reference)</span></span>

<span data-ttu-id="6bd19-103">クエリ式で、`select` 句は、クエリが実行されたときに生成される値の型を指定します。</span><span class="sxs-lookup"><span data-stu-id="6bd19-103">In a query expression, the `select` clause specifies the type of values that will be produced when the query is executed.</span></span> <span data-ttu-id="6bd19-104">結果は、以前のすべての句の評価と `select` 句自体の式に基づいています。</span><span class="sxs-lookup"><span data-stu-id="6bd19-104">The result is based on the evaluation of all the previous clauses and on any expressions in the `select` clause itself.</span></span> <span data-ttu-id="6bd19-105">クエリ式は、`select` 句または [group](group-clause.md) 句のいずれかで終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6bd19-105">A query expression must terminate with either a `select` clause or a [group](group-clause.md) clause.</span></span>

<span data-ttu-id="6bd19-106">次の例は、クエリ式での単純な `select` 句を示したものです。</span><span class="sxs-lookup"><span data-stu-id="6bd19-106">The following example shows a simple `select` clause in a query expression.</span></span>

[!code-csharp[cscsrefQueryKeywords#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#8)]  

<span data-ttu-id="6bd19-107">`select` 句によって生成されるシーケンスの型は、クエリ変数 `queryHighScores` の型を決定します。</span><span class="sxs-lookup"><span data-stu-id="6bd19-107">The type of the sequence produced by the `select` clause determines the type of the query variable `queryHighScores`.</span></span> <span data-ttu-id="6bd19-108">最も簡単なケースでは、`select` 句は、範囲変数だけを指定します。</span><span class="sxs-lookup"><span data-stu-id="6bd19-108">In the simplest case, the `select` clause just specifies the range variable.</span></span> <span data-ttu-id="6bd19-109">これにより、返されるシーケンスにデータ ソースと同じ型の要素が含まれます。</span><span class="sxs-lookup"><span data-stu-id="6bd19-109">This causes the returned sequence to contain elements of the same type as the data source.</span></span> <span data-ttu-id="6bd19-110">詳細については、「[LINQ クエリ操作での型の関係](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd19-110">For more information, see [Type Relationships in LINQ Query Operations](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span> <span data-ttu-id="6bd19-111">ただし、`select` 句は、ソース データを新しい型に変換する (または*投影*する) ための強力なメカニズムも提供します。</span><span class="sxs-lookup"><span data-stu-id="6bd19-111">However, the `select` clause also provides a powerful mechanism for transforming (or *projecting*) source data into new types.</span></span> <span data-ttu-id="6bd19-112">詳細については、「[LINQ によるデータ変換 (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd19-112">For more information, see [Data Transformations with LINQ (C#)](../../programming-guide/concepts/linq/data-transformations-with-linq.md).</span></span>

## <a name="example"></a><span data-ttu-id="6bd19-113">例</span><span class="sxs-lookup"><span data-stu-id="6bd19-113">Example</span></span>

<span data-ttu-id="6bd19-114">次の例は、`select` 句のすべての異なる形式を示しています。</span><span class="sxs-lookup"><span data-stu-id="6bd19-114">The following example shows all the different forms that a `select` clause may take.</span></span> <span data-ttu-id="6bd19-115">各クエリで、`select` 句と *クエリ変数* (`studentQuery1`、`studentQuery2`など) の型の関係に注意してください。</span><span class="sxs-lookup"><span data-stu-id="6bd19-115">In each query, note the relationship between the `select` clause and the type of the *query variable* (`studentQuery1`, `studentQuery2`, and so on).</span></span>

[!code-csharp[cscsrefQueryKeywords#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Select.cs#9)]

<span data-ttu-id="6bd19-116">前の例の `studentQuery8` に示すように、返されるシーケンスの要素にソース要素のプロパティのサブセットのみを含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="6bd19-116">As shown in `studentQuery8` in the previous example, sometimes you might want the elements of the returned sequence to contain only a subset of the properties of the source elements.</span></span> <span data-ttu-id="6bd19-117">返されるシーケンスをできるだけ小さく維持することで、メモリ要件を減らし、クエリの実行の速度を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="6bd19-117">By keeping the returned sequence as small as possible you can reduce the memory requirements and increase the speed of the execution of the query.</span></span> <span data-ttu-id="6bd19-118">これを行うには、`select` 句で匿名型を作成し、オブジェクト初期化子を使用して、ソース要素からの適切なプロパティで初期化します。</span><span class="sxs-lookup"><span data-stu-id="6bd19-118">You can accomplish this by creating an anonymous type in the `select` clause and using an object initializer to initialize it with the appropriate properties from the source element.</span></span> <span data-ttu-id="6bd19-119">これを行う方法の例については、「[オブジェクト初期化子とコレクション初期化子](../../programming-guide/classes-and-structs/object-and-collection-initializers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6bd19-119">For an example of how to do this, see [Object and Collection Initializers](../../programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="6bd19-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="6bd19-120">Remarks</span></span>

<span data-ttu-id="6bd19-121">コンパイル時に、`select` 句は、<xref:System.Linq.Enumerable.Select%2A> 標準クエリ演算子へのメソッドの呼び出しに変換されます。</span><span class="sxs-lookup"><span data-stu-id="6bd19-121">At compile time, the `select` clause is translated to a method call to the <xref:System.Linq.Enumerable.Select%2A> standard query operator.</span></span>

## <a name="see-also"></a><span data-ttu-id="6bd19-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="6bd19-122">See also</span></span>

- [<span data-ttu-id="6bd19-123">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="6bd19-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6bd19-124">クエリ キーワード (LINQ)</span><span class="sxs-lookup"><span data-stu-id="6bd19-124">Query Keywords (LINQ)</span></span>](query-keywords.md)
- [<span data-ttu-id="6bd19-125">from 句</span><span class="sxs-lookup"><span data-stu-id="6bd19-125">from clause</span></span>](from-clause.md)
- [<span data-ttu-id="6bd19-126">partial (メソッド) (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="6bd19-126">partial (Method) (C# Reference)</span></span>](partial-method.md)
- [<span data-ttu-id="6bd19-127">匿名型</span><span class="sxs-lookup"><span data-stu-id="6bd19-127">Anonymous Types</span></span>](../../programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="6bd19-128">C# での LINQ</span><span class="sxs-lookup"><span data-stu-id="6bd19-128">LINQ in C#</span></span>](../../linq/index.md)
- [<span data-ttu-id="6bd19-129">C# の LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="6bd19-129">Getting Started with LINQ in C#</span></span>](/dotnet/csharp/programming-guide/concepts/linq/)
