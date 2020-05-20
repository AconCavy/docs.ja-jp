---
title: try-catch-finally - C# リファレンス
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 5d98f6967595c7c32b23ba5422a8d9ca79f7f54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713041"
---
# <a name="try-catch-finally-c-reference"></a><span data-ttu-id="46fd3-102">try-catch-finally (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="46fd3-102">try-catch-finally (C# Reference)</span></span>

<span data-ttu-id="46fd3-103">通常、`catch` および `finally` は、`try` ブロックのリソースを取得して使用する場合に、対で記述されます。`catch` ブロックで例外的な状況を処理し、`finally` ブロックでリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="46fd3-103">A common usage of `catch` and `finally` together is to obtain and use resources in a `try` block, deal with exceptional circumstances in a `catch` block, and release the resources in the `finally` block.</span></span>

 <span data-ttu-id="46fd3-104">例外の再スローの使用例を含む詳細については、「[try-catch](try-catch.md)」および[例外のスロー](../../../standard/exceptions/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46fd3-104">For more information and examples on re-throwing exceptions, see [try-catch](try-catch.md) and [Throwing Exceptions](../../../standard/exceptions/index.md).</span></span> <span data-ttu-id="46fd3-105">`finally` ブロックの詳細については、「[try-finally](try-finally.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46fd3-105">For more information about the `finally` block, see [try-finally](try-finally.md).</span></span>

## <a name="example"></a><span data-ttu-id="46fd3-106">例</span><span class="sxs-lookup"><span data-stu-id="46fd3-106">Example</span></span>

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a><span data-ttu-id="46fd3-107">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="46fd3-107">C# language specification</span></span>

<span data-ttu-id="46fd3-108">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の「[try ステートメント](~/_csharplang/spec/statements.md#the-try-statement)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="46fd3-108">For more information, see [The try statement](~/_csharplang/spec/statements.md#the-try-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46fd3-109">参照</span><span class="sxs-lookup"><span data-stu-id="46fd3-109">See also</span></span>

- [<span data-ttu-id="46fd3-110">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="46fd3-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="46fd3-111">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="46fd3-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="46fd3-112">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="46fd3-112">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="46fd3-113">try、throw、catch ステートメント (C++)</span><span class="sxs-lookup"><span data-stu-id="46fd3-113">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [<span data-ttu-id="46fd3-114">throw</span><span class="sxs-lookup"><span data-stu-id="46fd3-114">throw</span></span>](throw.md)
- [<span data-ttu-id="46fd3-115">方法: 例外を明示的にスローする</span><span class="sxs-lookup"><span data-stu-id="46fd3-115">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [<span data-ttu-id="46fd3-116">using ステートメント</span><span class="sxs-lookup"><span data-stu-id="46fd3-116">using Statement</span></span>](using-statement.md)
