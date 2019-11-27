---
title: プログラム構造とコード規則
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions
- Visual Basic code, coding conventions
- coding conventions [Visual Basic], Visual Basic
- programs [Visual Basic], structure
- program structure [Visual Basic]
- naming conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- Visual Basic code
- programming [Visual Basic], Visual Basic coding conventions
ms.assetid: dd9be76f-6944-4e78-ad72-0b6084a3fc13
ms.openlocfilehash: bacd532361de18936bac96c631f7f7247246b1de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347285"
---
# <a name="program-structure-and-code-conventions-visual-basic"></a><span data-ttu-id="bdc62-102">プログラム構造とコード規則 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bdc62-102">Program Structure and Code Conventions (Visual Basic)</span></span>
<span data-ttu-id="bdc62-103">このセクションでは、一般的な Visual Basic プログラムの構造、シンプルな Visual Basic プログラム "Hello, World"、Visual Basic のコード規則について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-103">This section introduces the typical Visual Basic program structure, provides a simple Visual Basic program, "Hello, World", and discusses Visual Basic code conventions.</span></span> <span data-ttu-id="bdc62-104">コード規則は、プログラムのロジックではなくプログラムの物理的な構造と外観に焦点を合わせた提案です。</span><span class="sxs-lookup"><span data-stu-id="bdc62-104">Code conventions are suggestions that focus not on a program's logic but on its physical structure and appearance.</span></span> <span data-ttu-id="bdc62-105">コード規則に従うと、コードの読み取り、理解、保守が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="bdc62-105">Following them makes your code easier to read, understand, and maintain.</span></span> <span data-ttu-id="bdc62-106">コード規則には、以下の内容が含まれます。</span><span class="sxs-lookup"><span data-stu-id="bdc62-106">Code conventions can include, among others:</span></span>  
  
- <span data-ttu-id="bdc62-107">コードのラベル付けとコメント付けに関する標準化された書式</span><span class="sxs-lookup"><span data-stu-id="bdc62-107">Standardized formats for labeling and commenting code.</span></span>  
  
- <span data-ttu-id="bdc62-108">コードのスペーシング、書式指定、およびインデント設定に関するガイドライン</span><span class="sxs-lookup"><span data-stu-id="bdc62-108">Guidelines for spacing, formatting, and indenting code.</span></span>  
  
- <span data-ttu-id="bdc62-109">オブジェクト、変数、およびプロシージャの名前付け規則</span><span class="sxs-lookup"><span data-stu-id="bdc62-109">Naming conventions for objects, variables, and procedures.</span></span>  
  
 <span data-ttu-id="bdc62-110">次のトピックでは、Visual Basic プログラムの一連のプログラミングガイドラインと、適切な使用例を示します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-110">The following topics present a set of programming guidelines for Visual Basic programs, along with examples of good usage.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bdc62-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bdc62-111">In This Section</span></span>  
 [<span data-ttu-id="bdc62-112">Visual Basic プログラムの構造</span><span class="sxs-lookup"><span data-stu-id="bdc62-112">Structure of a Visual Basic Program</span></span>](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 <span data-ttu-id="bdc62-113">Visual Basic プログラムを構成する要素の概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-113">Provides an overview of the elements that make up a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="bdc62-114">Visual Basic の Main プロシージャ</span><span class="sxs-lookup"><span data-stu-id="bdc62-114">Main Procedure in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/main-procedure.md)  
 <span data-ttu-id="bdc62-115">アプリケーションの開始点となり、アプリケーションの総合的な制御を行うプロシージャについて説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-115">Discusses the procedure that serves as the starting point and overall control for your application.</span></span>  
  
 [<span data-ttu-id="bdc62-116">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="bdc62-116">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 <span data-ttu-id="bdc62-117">他のアセンブリのオブジェクトを参照する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-117">Discusses how to reference objects in other assemblies.</span></span>  
  
 [<span data-ttu-id="bdc62-118">Visual Basic 内の名前空間</span><span class="sxs-lookup"><span data-stu-id="bdc62-118">Namespaces in Visual Basic</span></span>](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 <span data-ttu-id="bdc62-119">アセンブリ内のオブジェクトが名前空間でどのように編成されているのかを説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-119">Describes how namespaces organize objects within assemblies.</span></span>  
  
 [<span data-ttu-id="bdc62-120">Visual Basic 名前付け規則</span><span class="sxs-lookup"><span data-stu-id="bdc62-120">Visual Basic Naming Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 <span data-ttu-id="bdc62-121">プロシージャ、定数、変数、引数、およびオブジェクトの名前付けに関する一般的なガイドラインを示します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-121">Includes general guidelines for naming procedures, constants, variables, arguments, and objects.</span></span>  
  
 [<span data-ttu-id="bdc62-122">Visual Basic のコーディング規則</span><span class="sxs-lookup"><span data-stu-id="bdc62-122">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 <span data-ttu-id="bdc62-123">このドキュメントのサンプルを開発するときに使用したガイドラインについてレビューします。</span><span class="sxs-lookup"><span data-stu-id="bdc62-123">Reviews the guidelines used in developing the samples in this documentation.</span></span>  
  
 [<span data-ttu-id="bdc62-124">条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="bdc62-124">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 <span data-ttu-id="bdc62-125">特定のコード ブロックを選択的にコンパイルし、その間は他のコード ブロックを無視する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-125">Describes how to compile particular blocks of code selectively while directing the compiler to ignore others.</span></span>  
  
 [<span data-ttu-id="bdc62-126">方法 : コード内でステートメントを分割および連結する</span><span class="sxs-lookup"><span data-stu-id="bdc62-126">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 <span data-ttu-id="bdc62-127">長いステートメントを複数の行に分割する方法と、複数の短いステートメントを 1 行に結合する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-127">Shows how to divide long statements into multiple lines and combine short statements on one line.</span></span>  
  
 [<span data-ttu-id="bdc62-128">方法 : コードのセクションを折りたたんで非表示にする</span><span class="sxs-lookup"><span data-stu-id="bdc62-128">How to: Collapse and Hide Sections of Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)  
 <span data-ttu-id="bdc62-129">Visual Basic コードエディターでコードのセクションを折りたたんで非表示にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-129">Shows how to collapse and hide sections of code in the Visual Basic code editor.</span></span>  
  
 [<span data-ttu-id="bdc62-130">方法 : ステートメントへのラベル付け</span><span class="sxs-lookup"><span data-stu-id="bdc62-130">How to: Label Statements</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)  
 <span data-ttu-id="bdc62-131">`On Error Goto` などのステートメントで使用するために、コード行に識別用のマーキングをする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-131">Shows how to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 [<span data-ttu-id="bdc62-132">コード内の特殊文字</span><span class="sxs-lookup"><span data-stu-id="bdc62-132">Special Characters in Code</span></span>](../../../visual-basic/programming-guide/program-structure/special-characters-in-code.md)  
 <span data-ttu-id="bdc62-133">英数字以外の文字を使用する方法と場所について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-133">Shows how and where to use non-numeric and non-alphabetic characters.</span></span>  
  
 [<span data-ttu-id="bdc62-134">コード内のコメント</span><span class="sxs-lookup"><span data-stu-id="bdc62-134">Comments in Code</span></span>](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)  
 <span data-ttu-id="bdc62-135">説明的なコメントをコードに追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-135">Discusses how to add descriptive comments to your code.</span></span>  
  
 [<span data-ttu-id="bdc62-136">コード内の要素名としてのキーワード</span><span class="sxs-lookup"><span data-stu-id="bdc62-136">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 <span data-ttu-id="bdc62-137">角かっこ (`[]`) を使用して、Visual Basic キーワードでもある変数名を区切る方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-137">Describes how to use brackets (`[]`) to delimit variable names that are also Visual Basic keywords.</span></span>  
  
 [<span data-ttu-id="bdc62-138">Me、My、MyBase、および MyClass</span><span class="sxs-lookup"><span data-stu-id="bdc62-138">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 <span data-ttu-id="bdc62-139">Visual Basic プログラムの要素を参照するさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-139">Describes various ways to refer to elements of a Visual Basic program.</span></span>  
  
 [<span data-ttu-id="bdc62-140">Visual Basic の制限事項</span><span class="sxs-lookup"><span data-stu-id="bdc62-140">Visual Basic Limitations</span></span>](../../../visual-basic/programming-guide/program-structure/limitations.md)  
 <span data-ttu-id="bdc62-141">Visual Basic 内での既知のコーディング制限の削除について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-141">Discusses the removal of known coding limits within Visual Basic.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bdc62-142">関連セクション</span><span class="sxs-lookup"><span data-stu-id="bdc62-142">Related Sections</span></span>  
 [<span data-ttu-id="bdc62-143">表記規則とコード規則</span><span class="sxs-lookup"><span data-stu-id="bdc62-143">Typographic and Code Conventions</span></span>](../../../visual-basic/language-reference/typographic-and-code-conventions.md)  
 <span data-ttu-id="bdc62-144">Visual Basic の標準コーディング規則を提供します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-144">Provides standard coding conventions for Visual Basic.</span></span>  
  
 [<span data-ttu-id="bdc62-145">コードの作成</span><span class="sxs-lookup"><span data-stu-id="bdc62-145">Writing Code</span></span>](/visualstudio/ide/writing-code-in-the-code-and-text-editor)  
 <span data-ttu-id="bdc62-146">コードの記述と管理を容易にする機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="bdc62-146">Describes features that make it easier for you to write and manage your code.</span></span>
