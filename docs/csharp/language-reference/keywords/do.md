---
title: do - C# リファレンス
ms.date: 05/28/2018
f1_keywords:
- do_CSharpKeyword
- do
helpviewer_keywords:
- do keyword [C#]
ms.assetid: 50725f79-9ba6-4898-aa78-6e331568a1bb
ms.openlocfilehash: 38224ce70c19ff67ad80b99d3da52155849f1341
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713597"
---
# <a name="do-c-reference"></a><span data-ttu-id="31710-102">do (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="31710-102">do (C# Reference)</span></span>

<span data-ttu-id="31710-103">`do` ステートメントでは、指定されたブール式が `true` と評価される間、ステートメントまたはステートメント ブロックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="31710-103">The `do` statement executes a statement or a block of statements while a specified Boolean expression evaluates to `true`.</span></span> <span data-ttu-id="31710-104">ループの各実行の後に式が評価されるため、`do-while` ループは 1 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="31710-104">Because that expression is evaluated after each execution of the loop, a `do-while` loop executes one or more times.</span></span> <span data-ttu-id="31710-105">[while](while.md) ループは、これとは異なり、0 回以上実行されます。</span><span class="sxs-lookup"><span data-stu-id="31710-105">This differs from the [while](while.md) loop, which executes zero or more times.</span></span>

<span data-ttu-id="31710-106">`do` ステートメント ブロック内の任意の位置で、[break](break.md) ステートメントを使用してループを抜けることができます。</span><span class="sxs-lookup"><span data-stu-id="31710-106">At any point within the `do` statement block, you can break out of the loop by using the [break](break.md) statement.</span></span>

<span data-ttu-id="31710-107">`while`continue[ ステートメントを使用すると、](continue.md) 式の評価に直接ステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="31710-107">You can step directly to the evaluation of the `while` expression by using the [continue](continue.md) statement.</span></span> <span data-ttu-id="31710-108">式の評価が `true` の場合、ループの最初のステートメントから実行が続行されます。</span><span class="sxs-lookup"><span data-stu-id="31710-108">If the expression evaluates to `true`, execution continues at the first statement in the loop.</span></span> <span data-ttu-id="31710-109">それ以外の場合、実行は、ループの後の最初のステートメントから続行されます。</span><span class="sxs-lookup"><span data-stu-id="31710-109">Otherwise, execution continues at the first statement after the loop.</span></span>

<span data-ttu-id="31710-110">また、`do-while`goto[、](goto.md)return[、](return.md)throw[ ステートメントのいずれかを使って ](throw.md) ループを終了することもできます。</span><span class="sxs-lookup"><span data-stu-id="31710-110">You also can exit a `do-while` loop by the [goto](goto.md), [return](return.md), or [throw](throw.md) statements.</span></span>

## <a name="example"></a><span data-ttu-id="31710-111">例</span><span class="sxs-lookup"><span data-stu-id="31710-111">Example</span></span>

<span data-ttu-id="31710-112">`do` ステートメントの使用方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="31710-112">The following example shows the usage of the `do` statement.</span></span> <span data-ttu-id="31710-113">**[実行]** を選択して、コード例を実行します。</span><span class="sxs-lookup"><span data-stu-id="31710-113">Select **Run** to run the example code.</span></span> <span data-ttu-id="31710-114">その後に、コードを変更し、もう一度実行することができます。</span><span class="sxs-lookup"><span data-stu-id="31710-114">After that you can modify the code and run it again.</span></span>

[!code-csharp-interactive[do loop example](~/samples/snippets/csharp/keywords/IterationKeywordsExamples.cs#4)]

## <a name="c-language-specification"></a><span data-ttu-id="31710-115">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="31710-115">C# language specification</span></span>

<span data-ttu-id="31710-116">詳細については、「[C# 言語仕様](~/_csharplang/spec/statements.md#the-do-statement)」の [do ステートメント](/dotnet/csharp/language-reference/language-specification/introduction)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="31710-116">For more information, see [The do statement](~/_csharplang/spec/statements.md#the-do-statement) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>

## <a name="see-also"></a><span data-ttu-id="31710-117">参照</span><span class="sxs-lookup"><span data-stu-id="31710-117">See also</span></span>

- [<span data-ttu-id="31710-118">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="31710-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="31710-119">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="31710-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="31710-120">C# のキーワード</span><span class="sxs-lookup"><span data-stu-id="31710-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="31710-121">while ステートメント</span><span class="sxs-lookup"><span data-stu-id="31710-121">while statement</span></span>](while.md)
