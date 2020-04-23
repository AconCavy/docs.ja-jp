---
title: 複数の文字列を連結する方法 (C# ガイド)
description: C# で文字列を連結する方法は複数あります。 各選択のオプションと、それを選ぶ理由も示します。
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: bbdeba4ee3526140de29ac0d7c97e9a593729d47
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389532"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="13dde-104">複数の文字列を連結する方法 (C# ガイド)</span><span class="sxs-lookup"><span data-stu-id="13dde-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="13dde-105">*連結*とは、ある文字列を別の文字列の末尾に追加するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="13dde-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="13dde-106">文字列を連結するには、`+` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="13dde-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="13dde-107">文字列リテラルと文字列定数の場合、連結はコンパイル時に行われ、実行時には行われません。</span><span class="sxs-lookup"><span data-stu-id="13dde-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="13dde-108">文字列変数の連結は実行時にのみ行われます。</span><span class="sxs-lookup"><span data-stu-id="13dde-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="13dde-109">次の例では、ソース コードを読みやすくするために、連結を使用して長い文字列リテラルを短い文字列に分割しています。</span><span class="sxs-lookup"><span data-stu-id="13dde-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="13dde-110">これらの部分は、コンパイル時に単一の文字列に連結されます。</span><span class="sxs-lookup"><span data-stu-id="13dde-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="13dde-111">関係する文字列の数に関係なく、実行時にパフォーマンス コストは発生しません。</span><span class="sxs-lookup"><span data-stu-id="13dde-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp-interactive[Combining strings at compile time](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#1)]  

<span data-ttu-id="13dde-112">文字列変数を連結する場合は、`+` または `+=` 演算子、[文字列補間](../language-reference/tokens/interpolated.md)または <xref:System.String.Format%2A?displayProperty=nameWithType>、<xref:System.String.Concat%2A?displayProperty=nameWithType>、<xref:System.String.Join%2A?displayProperty=nameWithType>、<xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="13dde-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="13dde-113">`+` 演算子は使い方が簡単で、直感的なコードにすることができます。</span><span class="sxs-lookup"><span data-stu-id="13dde-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="13dde-114">1 つのステートメントで複数の `+` 演算子を使用している場合でも、文字列の内容がコピーされるのは 1 回のみです。</span><span class="sxs-lookup"><span data-stu-id="13dde-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="13dde-115">次のコードは、`+` および `+=` 演算子を使用して文字列を連結する例を示しています。</span><span class="sxs-lookup"><span data-stu-id="13dde-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

[!code-csharp-interactive[combining strings using +](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#2)]  

<span data-ttu-id="13dde-116">式によっては、次のコードに示すように、文字列補間を使用して文字列を連結する方が簡単な場合があります。</span><span class="sxs-lookup"><span data-stu-id="13dde-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>
  
[!code-csharp-interactive[building strings using string interpolation](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#3)]  
  
> [!NOTE]
> <span data-ttu-id="13dde-117">文字列連結操作において、C# コンパイラでは null 文字列は空の文字列と同様に扱われます。</span><span class="sxs-lookup"><span data-stu-id="13dde-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="13dde-118">文字列を連結する他のメソッドとして、<xref:System.String.Format%2A?displayProperty=nameWithType> があります。</span><span class="sxs-lookup"><span data-stu-id="13dde-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="13dde-119">このメソッドは、少数のコンポーネント文字列から文字列を作成する場合に有効です。</span><span class="sxs-lookup"><span data-stu-id="13dde-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="13dde-120">他にも、結合するソース文字列の数がわからないループ内の文字列を結合する場合、ソース文字列の実際の数は大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13dde-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="13dde-121"><xref:System.Text.StringBuilder> クラスは、このようなシナリオのために設計されています。</span><span class="sxs-lookup"><span data-stu-id="13dde-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="13dde-122">次のコードでは、<xref:System.Text.StringBuilder> クラスの <xref:System.Text.StringBuilder.Append%2A> メソッドを使用して文字列を連結しています。</span><span class="sxs-lookup"><span data-stu-id="13dde-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>  
  
[!code-csharp-interactive[string concatenation using string builder](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#4)]  

<span data-ttu-id="13dde-123">[文字列の連結または `StringBuilder` クラスを選択する理由](xref:System.Text.StringBuilder#StringAndSB)に関するページで詳細をご確認ください。</span><span class="sxs-lookup"><span data-stu-id="13dde-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](xref:System.Text.StringBuilder#StringAndSB).</span></span>

<span data-ttu-id="13dde-124">コレクションからの文字列を結合する別のオプションとして、<xref:System.String.Concat%2A?displayProperty=nameWithType> メソッドを使用する方法があります。</span><span class="sxs-lookup"><span data-stu-id="13dde-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="13dde-125">ソース文字列を区切り記号で区切る必要がある場合は、<xref:System.String.Join%2A?displayProperty=nameWithType> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="13dde-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="13dde-126">次のコードでは、両方のメソッドを使用して単語の配列を結合します。</span><span class="sxs-lookup"><span data-stu-id="13dde-126">The following code combines an array of words using both methods:</span></span>

[!code-csharp-interactive[concatenation of string collection](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#5)]

<span data-ttu-id="13dde-127">最後に、[LINQ](../programming-guide/concepts/linq/index.md) および <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> メソッドを使用して、コレクションからの文字列を結合できます。</span><span class="sxs-lookup"><span data-stu-id="13dde-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="13dde-128">このメソッドは、ラムダ式を使用してソース文字列を結合します。</span><span class="sxs-lookup"><span data-stu-id="13dde-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="13dde-129">ラムダ式は、各文字列を既存の蓄積に追加する処理を行います。</span><span class="sxs-lookup"><span data-stu-id="13dde-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="13dde-130">次の例では、配列内の各単語の間にスペースを追加することによって単語の配列を結合します。</span><span class="sxs-lookup"><span data-stu-id="13dde-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

[!code-csharp-interactive[string concatenation using LINQ expressions](../../../samples/snippets/csharp/how-to/strings/Concatenate.cs#6)]  

<span data-ttu-id="13dde-131">[サンプル コード](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)を見て、これらのサンプルを試すことができます。</span><span class="sxs-lookup"><span data-stu-id="13dde-131">You can try these samples by looking at the [sample code](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="13dde-132">または、サンプルを [zip ファイルとして](../../../samples/snippets/csharp/how-to/strings.zip)ダウンロードすることができます。</span><span class="sxs-lookup"><span data-stu-id="13dde-132">Or, you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="13dde-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="13dde-133">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="13dde-134">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="13dde-134">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="13dde-135">文字列</span><span class="sxs-lookup"><span data-stu-id="13dde-135">Strings</span></span>](../programming-guide/strings/index.md)
