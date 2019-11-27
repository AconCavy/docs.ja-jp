---
title: エラー メッセージ
ms.date: 07/20/2015
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
ms.openlocfilehash: 15d12802c92e7b9ed99c83885bd38e381c8b687d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353707"
---
# <a name="error-messages-visual-basic"></a><span data-ttu-id="0b95e-102">エラー メッセージ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0b95e-102">Error Messages (Visual Basic)</span></span>
<span data-ttu-id="0b95e-103">Visual Basic アプリケーションを作成、コンパイル、実行する際は、次の種類のエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0b95e-103">When you write, compile, or run a Visual Basic application, the following types of errors can occur:</span></span>  
  
1. <span data-ttu-id="0b95e-104">デザイン時エラー: Visual Studio でアプリケーションを作成するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="0b95e-104">Design-time errors, which occur when you write an application in Visual Studio.</span></span>  
  
2. <span data-ttu-id="0b95e-105">コンパイル時エラー: Visual Studio またはコマンド プロンプトでアプリケーションをコンパイルするときに発生します。</span><span class="sxs-lookup"><span data-stu-id="0b95e-105">Compile-time errors, which occur when you compile an application in Visual Studio or at a command prompt.</span></span>  
  
3. <span data-ttu-id="0b95e-106">実行時エラー: Visual Studio でアプリケーションまたはスタンドアロンの実行可能ファイルを実行するときに発生します。</span><span class="sxs-lookup"><span data-stu-id="0b95e-106">Run-time errors, which occur when you run an application in Visual Studio or as a stand-alone executable file.</span></span>  
  
 <span data-ttu-id="0b95e-107">特定のエラーのトラブルシューティング方法については、「[Visual Basic プログラマのための追加リソース](../../../visual-basic/getting-started/additional-resources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b95e-107">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md).</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="0b95e-108">実行時エラー</span><span class="sxs-lookup"><span data-stu-id="0b95e-108">Run Time Errors</span></span>  
 <span data-ttu-id="0b95e-109">Visual Basic アプリケーションが、システムが実行できない操作を実行しようとすると、実行時エラーが発生し、Visual Basic は `Exception` オブジェクトをスローします。</span><span class="sxs-lookup"><span data-stu-id="0b95e-109">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and Visual Basic throws an `Exception` object.</span></span> <span data-ttu-id="0b95e-110">Visual Basic は、`Throw` ステートメントを使用して、`Exception` オブジェクトを含む任意のデータ型のカスタムエラーを生成できます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-110">Visual Basic can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="0b95e-111">アプリケーションは、キャッチされた例外のエラー番号とメッセージを表示して、エラーを識別できます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-111">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="0b95e-112">エラーがキャッチされない場合、アプリケーションは終了します。</span><span class="sxs-lookup"><span data-stu-id="0b95e-112">If an error isn't caught, the application ends.</span></span>  
  
 <span data-ttu-id="0b95e-113">実行時エラーはコードでトラップして調べることができます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-113">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="0b95e-114">エラーが発生するコードを `Try` ブロックで囲むと、スローされたエラーを対応する `Catch` ブロック内でキャッチできます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-114">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="0b95e-115">実行時にエラーをトラップしてコードで対処する方法については、「[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b95e-115">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="compile-time-errors"></a><span data-ttu-id="0b95e-116">コンパイル時エラー</span><span class="sxs-lookup"><span data-stu-id="0b95e-116">Compile Time Errors</span></span>  
 <span data-ttu-id="0b95e-117">Visual Basic コンパイラがコード内で問題を検出すると、コンパイル時エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="0b95e-117">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="0b95e-118">コード エディターでは、エラーの原因となったコード行の下に波線が表示されるため、簡単にその行を特定できます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-118">In the Code Editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="0b95e-119">波線をポイントするか**エラー一覧**を開くと、エラー メッセージが表示されます。エラー一覧には他のメッセージも表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-119">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>  
  
 <span data-ttu-id="0b95e-120">識別子の下に波線があり、右端の文字の下に短い下線が表示されている場合は、クラス、コンストラクター、メソッド、プロパティ、フィールド、または列挙型のスタブを生成できます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-120">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field or enum.</span></span> <span data-ttu-id="0b95e-121">詳細については、「[Generate From Usage](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage)」(使用法から生成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b95e-121">For more information, see [Generate From Usage](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>
  
 <span data-ttu-id="0b95e-122">Visual Basic コンパイラからのエラーを解決することにより、高速に実行されるバグの少ないコードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-122">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="0b95e-123">これらの警告では、アプリケーションの実行時にエラーを発生させるコードが示されます。</span><span class="sxs-lookup"><span data-stu-id="0b95e-123">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="0b95e-124">たとえば、ユーザーが、割り当てが行われていないオブジェクト変数のメンバーを呼び出そうとしたり、戻り値を設定せずに関数から戻ろうとしたり、例外をキャッチするロジックにエラーがある `Try` ブロックを実行しようとしたりすると、コンパイラは警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="0b95e-124">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="0b95e-125">警告の表示/非表示を切り替える方法など、警告の詳細については、「[Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b95e-125">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>
