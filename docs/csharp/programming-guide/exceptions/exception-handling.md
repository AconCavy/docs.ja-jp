---
title: 例外処理 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: ee1e5bd15183dad9ffe97824f9b194668e9d3b17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705302"
---
# <a name="exception-handling-c-programming-guide"></a><span data-ttu-id="206c7-102">例外処理 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="206c7-102">Exception Handling (C# Programming Guide)</span></span>
<span data-ttu-id="206c7-103">[try](../../language-reference/keywords/try-catch.md) ブロックは、例外の影響を受ける可能性があるコードを区分化するために、 C# プログラマによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="206c7-103">A [try](../../language-reference/keywords/try-catch.md) block is used by C# programmers to partition code that might be affected by an exception.</span></span> <span data-ttu-id="206c7-104">関連付けられた [catch](../../language-reference/keywords/try-catch.md) ブロックは、スローされた例外を処理するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="206c7-104">Associated [catch](../../language-reference/keywords/try-catch.md) blocks are used to handle any resulting exceptions.</span></span> <span data-ttu-id="206c7-105">[finally](../../language-reference/keywords/try-finally.md) ブロックには、`try` ブロックで例外がスローされたかどうかにかかわらず実行されるコードが記述されます (`try` ブロックに割り当てられたリソースの解放など)。</span><span class="sxs-lookup"><span data-stu-id="206c7-105">A [finally](../../language-reference/keywords/try-finally.md) block contains code that is run regardless of whether or not an exception is thrown in the `try` block, such as releasing resources that are allocated in the `try` block.</span></span> <span data-ttu-id="206c7-106">`try` ブロックには、1 つ以上の `catch` ブロック、`finally` ブロック、またはその両方が関連付けられる必要があります。</span><span class="sxs-lookup"><span data-stu-id="206c7-106">A `try` block requires one or more associated `catch` blocks, or a `finally` block, or both.</span></span>  
  
 <span data-ttu-id="206c7-107">次のコードは、`try-catch` ステートメント、`try-finally` ステートメント、および `try-catch-finally` ステートメントの例です。</span><span class="sxs-lookup"><span data-stu-id="206c7-107">The following examples show a `try-catch` statement, a `try-finally` statement, and a `try-catch-finally` statement.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 <span data-ttu-id="206c7-108">`try` ブロックに `catch` または `finally` ブロックがない場合は、コンパイル エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="206c7-108">A `try` block without a `catch` or `finally` block causes a compiler error.</span></span>  
  
## <a name="catch-blocks"></a><span data-ttu-id="206c7-109">catch ブロック</span><span class="sxs-lookup"><span data-stu-id="206c7-109">Catch Blocks</span></span>  
 <span data-ttu-id="206c7-110">`catch` ブロックでは、キャッチする例外の種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="206c7-110">A `catch` block can specify the type of exception to catch.</span></span> <span data-ttu-id="206c7-111">この型指定は、*例外フィルター*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="206c7-111">The type specification is called an *exception filter*.</span></span> <span data-ttu-id="206c7-112">例外の種類は、<xref:System.Exception> から派生している必要があります。</span><span class="sxs-lookup"><span data-stu-id="206c7-112">The exception type should be derived from <xref:System.Exception>.</span></span> <span data-ttu-id="206c7-113">一般に、`try` ブロックでスローされる可能性があるすべての例外の処理方法を把握している場合や、`catch` ブロックの末尾に [throw](../../language-reference/keywords/throw.md) ステートメントを記述している場合を除いては、例外フィルターとして <xref:System.Exception> を指定することは避けてください。</span><span class="sxs-lookup"><span data-stu-id="206c7-113">In general, do not specify <xref:System.Exception> as the exception filter unless either you know how to handle all exceptions that might be thrown in the `try` block, or you have included a [throw](../../language-reference/keywords/throw.md) statement at the end of your `catch` block.</span></span>  
  
 <span data-ttu-id="206c7-114">複数の `catch` ブロックに異なる例外フィルターが含まれている場合は、それらを連結することができます。</span><span class="sxs-lookup"><span data-stu-id="206c7-114">Multiple `catch` blocks with different exception filters can be chained together.</span></span> <span data-ttu-id="206c7-115">`catch` ブロックはコード内で上から下に評価されますが、スローされた各例外に対して実行される `catch` ブロックは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="206c7-115">The `catch` blocks are evaluated from top to bottom in your code, but only one `catch` block is executed for each exception that is thrown.</span></span> <span data-ttu-id="206c7-116">スローされた例外の厳密な型か、その基底クラスを指定する最初の `catch` ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="206c7-116">The first `catch` block that specifies the exact type or a base class of the thrown exception is executed.</span></span> <span data-ttu-id="206c7-117">一致する例外フィルターを指定した `catch` ブロックがない場合は、フィルターのない `catch` ブロックが選択されます (それがステートメント内に存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="206c7-117">If no `catch` block specifies a matching exception filter, a `catch` block that does not have a filter is selected, if one is present in the statement.</span></span> <span data-ttu-id="206c7-118">最初に配置する `catch` ブロックでは、最も具体的な (つまり、最終派生の) 例外の種類を指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="206c7-118">It is important to position `catch` blocks with the most specific (that is, the most derived) exception types first.</span></span>  
  
 <span data-ttu-id="206c7-119">次の条件に該当する場合は、例外をキャッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="206c7-119">You should catch exceptions when the following conditions are true:</span></span>  
  
- <span data-ttu-id="206c7-120">例外がスローされる理由を十分に理解していて、かつ特定の回復手段を実装できる (<xref:System.IO.FileNotFoundException> オブジェクトをキャッチした場合に、ユーザーに新しいファイル名を入力するよう求めるなど)。</span><span class="sxs-lookup"><span data-stu-id="206c7-120">You have a good understanding of why the exception might be thrown, and you can implement a specific recovery, such as prompting the user to enter a new file name when you catch a <xref:System.IO.FileNotFoundException> object.</span></span>  
  
- <span data-ttu-id="206c7-121">より具体的な例外を新規に作成し、スローできる。</span><span class="sxs-lookup"><span data-stu-id="206c7-121">You can create and throw a new, more specific exception.</span></span>  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- <span data-ttu-id="206c7-122">例外を追加処理に渡す前に、その例外を部分的に処理する必要がある。</span><span class="sxs-lookup"><span data-stu-id="206c7-122">You want to partially handle an exception before passing it on for additional handling.</span></span> <span data-ttu-id="206c7-123">次の例では、例外を再スローする前に、エラー ログにエントリを追加する目的で `catch` ブロックが使用されています。</span><span class="sxs-lookup"><span data-stu-id="206c7-123">In the following example, a `catch` block is used to add an entry to an error log before re-throwing the exception.</span></span>  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a><span data-ttu-id="206c7-124">Finally ブロック</span><span class="sxs-lookup"><span data-stu-id="206c7-124">Finally Blocks</span></span>  
 <span data-ttu-id="206c7-125">`finally` ブロックでは、`try` ブロックで実行されるアクションをクリーンアップすることができます。</span><span class="sxs-lookup"><span data-stu-id="206c7-125">A `finally` block enables you to clean up actions that are performed in a `try` block.</span></span> <span data-ttu-id="206c7-126">`finally` ブロック (存在する場合) は、最後 (`try` ブロックおよび一致する `catch` ブロックの後) に実行されます。</span><span class="sxs-lookup"><span data-stu-id="206c7-126">If present, the `finally` block executes last, after the `try` block and any matched `catch` block.</span></span> <span data-ttu-id="206c7-127">`finally` ブロックは、例外がスローされたかどうかや、例外の種類に一致する `catch` ブロックが見つかったかどうかにかかわらず、常に実行されます。</span><span class="sxs-lookup"><span data-stu-id="206c7-127">A `finally` block always runs, regardless of whether an exception is thrown or a `catch` block matching the exception type is found.</span></span>  
  
 <span data-ttu-id="206c7-128">`finally` ブロックは、ランタイム内のガベージ コレクターによってオブジェクトがファイナライズされるのを待つことなく、ファイル ストリーム、データベース接続、グラフィックス ハンドルなどのリソースを解放するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="206c7-128">The `finally` block can be used to release resources such as file streams, database connections, and graphics handles without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="206c7-129">詳しくは、「[using ステートメント](../../language-reference/keywords/using-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="206c7-129">See [using Statement](../../language-reference/keywords/using-statement.md) for more information.</span></span>  
  
 <span data-ttu-id="206c7-130">次の例では、`try` ブロックで開かれたファイルを閉じるために `finally` ブロックが使用されています。</span><span class="sxs-lookup"><span data-stu-id="206c7-130">In the following example, the `finally` block is used to close a file that is opened in the `try` block.</span></span> <span data-ttu-id="206c7-131">ファイルを閉じる前に、ファイル ハンドルの状態が確認されています。</span><span class="sxs-lookup"><span data-stu-id="206c7-131">Notice that the state of the file handle is checked before the file is closed.</span></span> <span data-ttu-id="206c7-132">`try` ブロックがファイルを開けなかった場合は、ファイル ハンドルの値が `null` のままになり、`finally` ブロックはファイルを閉じようとしません。</span><span class="sxs-lookup"><span data-stu-id="206c7-132">If the `try` block cannot open the file, the file handle still has the value `null` and the `finally` block does not try to close it.</span></span> <span data-ttu-id="206c7-133">`try` ブロックでファイルが正常に開かれた場合は、開かれたファイルを `finally` ブロックが閉じます。</span><span class="sxs-lookup"><span data-stu-id="206c7-133">Alternatively, if the file is opened successfully in the `try` block, the `finally` block closes the open file.</span></span>  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="206c7-134">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="206c7-134">C# Language Specification</span></span>  

<span data-ttu-id="206c7-135">詳細については、「[C# 言語仕様](/dotnet/csharp/language-reference/language-specification/introduction)」の[例外](~/_csharplang/spec/exceptions.md)と [try ステートメント](~/_csharplang/spec/statements.md#the-try-statement)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="206c7-135">For more information, see [Exceptions](~/_csharplang/spec/exceptions.md) and [The try statement](~/_csharplang/spec/statements.md#the-try-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="206c7-136">言語仕様は、C# の構文と使用法に関する信頼性のある情報源です。</span><span class="sxs-lookup"><span data-stu-id="206c7-136">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="206c7-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="206c7-137">See also</span></span>

- [<span data-ttu-id="206c7-138">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="206c7-138">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="206c7-139">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="206c7-139">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="206c7-140">例外と例外処理</span><span class="sxs-lookup"><span data-stu-id="206c7-140">Exceptions and Exception Handling</span></span>](./index.md)
- [<span data-ttu-id="206c7-141">try-catch</span><span class="sxs-lookup"><span data-stu-id="206c7-141">try-catch</span></span>](../../language-reference/keywords/try-catch.md)
- [<span data-ttu-id="206c7-142">try-finally</span><span class="sxs-lookup"><span data-stu-id="206c7-142">try-finally</span></span>](../../language-reference/keywords/try-finally.md)
- [<span data-ttu-id="206c7-143">try-catch-finally</span><span class="sxs-lookup"><span data-stu-id="206c7-143">try-catch-finally</span></span>](../../language-reference/keywords/try-catch-finally.md)
- [<span data-ttu-id="206c7-144">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="206c7-144">using Statement</span></span>](../../language-reference/keywords/using-statement.md)
