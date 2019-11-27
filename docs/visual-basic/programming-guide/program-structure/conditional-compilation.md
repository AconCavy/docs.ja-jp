---
title: 条件付きコンパイル
ms.date: 07/20/2015
helpviewer_keywords:
- conditional compilation [Visual Basic], about conditional compilation
- compilation [Visual Basic], conditional
ms.assetid: 9c35e55e-7eee-44fb-a586-dad1f1884848
ms.openlocfilehash: 19a2c70941a9a72574f7e624743def74b80c4e39
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347460"
---
# <a name="conditional-compilation-in-visual-basic"></a><span data-ttu-id="5b0ed-102">Visual Basic での条件付きコンパイル</span><span class="sxs-lookup"><span data-stu-id="5b0ed-102">Conditional Compilation in Visual Basic</span></span>
<span data-ttu-id="5b0ed-103">*条件付きコンパイル*では、プログラム内の特定のコードブロックが選択的にコンパイルされ、他のコードは無視されます。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-103">In *conditional compilation*, particular blocks of code in a program are compiled selectively while others are ignored.</span></span>  
  
 <span data-ttu-id="5b0ed-104">たとえば、同じプログラミングタスクに対するさまざまなアプローチの速度を比較するデバッグステートメントを記述したり、アプリケーションを複数の言語用にローカライズしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-104">For example, you may want to write debugging statements that compare the speed of different approaches to the same programming task, or you may want to localize an application for multiple languages.</span></span> <span data-ttu-id="5b0ed-105">条件付きコンパイルステートメントは、実行時ではなくコンパイル時に実行するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-105">Conditional compilation statements are designed to run during compile time, not at run time.</span></span>  
  
 <span data-ttu-id="5b0ed-106">`#If...Then...#Else` ディレクティブで条件付きでコンパイルされるコードブロックを示します。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-106">You denote blocks of code to be conditionally compiled with the `#If...Then...#Else` directive.</span></span> <span data-ttu-id="5b0ed-107">たとえば、同じソースコードから、同じアプリケーションのフランス語とドイツ語の言語バージョンを作成するには、定義済みの定数 `FrenchVersion` と `GermanVersion`を使用して、`#If...Then` ステートメントにプラットフォーム固有のコードセグメントを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-107">For example, to create French- and German-language versions of the same application from the same source code, you embed platform-specific code segments in `#If...Then` statements using the predefined constants `FrenchVersion` and `GermanVersion`.</span></span> <span data-ttu-id="5b0ed-108">次の例では、その方法を示します。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-108">The following example demonstrates how:</span></span>  
  
 [!code-vb[VbVbalrConditionalComp#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#5)]  
  
 <span data-ttu-id="5b0ed-109">コンパイル時に `FrenchVersion` 条件付きコンパイル定数の値を `True` に設定すると、フランス語バージョンの条件付きコードがコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-109">If you set the value of the `FrenchVersion` conditional compilation constant to `True` at compile time, the conditional code for the French version is compiled.</span></span> <span data-ttu-id="5b0ed-110">`GermanVersion` 定数の値を `True`に設定すると、コンパイラはドイツ語バージョンを使用します。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-110">If you set the value of the `GermanVersion` constant to `True`, the compiler uses the German version.</span></span> <span data-ttu-id="5b0ed-111">どちらも `True`に設定されていない場合は、最後の `Else` ブロックのコードが実行されます。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-111">If neither is set to `True`, the code in the last `Else` block runs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5b0ed-112">コードを編集し、現在のブランチに含まれていない場合、条件付きコンパイルディレクティブを使用すると、オートコンプリートは機能しません。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-112">Autocompletion will not function when editing code and using conditional compilation directives if the code is not part of the current branch.</span></span>  
  
## <a name="declaring-conditional-compilation-constants"></a><span data-ttu-id="5b0ed-113">条件付きコンパイル定数の宣言</span><span class="sxs-lookup"><span data-stu-id="5b0ed-113">Declaring Conditional Compilation Constants</span></span>  
 <span data-ttu-id="5b0ed-114">条件付きコンパイル定数は、次の3つの方法のいずれかで設定できます。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-114">You can set conditional compilation constants in one of three ways:</span></span>  
  
- <span data-ttu-id="5b0ed-115">**プロジェクトデザイナー**で</span><span class="sxs-lookup"><span data-stu-id="5b0ed-115">In the **Project Designer**</span></span>  
  
- <span data-ttu-id="5b0ed-116">コマンドラインコンパイラを使用する場合のコマンドライン</span><span class="sxs-lookup"><span data-stu-id="5b0ed-116">At the command line when using the command-line compiler</span></span>  
  
- <span data-ttu-id="5b0ed-117">コード内</span><span class="sxs-lookup"><span data-stu-id="5b0ed-117">In your code</span></span>  
  
 <span data-ttu-id="5b0ed-118">条件付きコンパイル定数には特別なスコープがあり、標準コードからアクセスすることはできません。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-118">Conditional compilation constants have a special scope and cannot be accessed from standard code.</span></span> <span data-ttu-id="5b0ed-119">条件付きコンパイル定数のスコープは、設定方法によって異なります。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-119">The scope of a conditional compilation constant is dependent on the way it is set.</span></span> <span data-ttu-id="5b0ed-120">次の表は、前述の3つの方法のそれぞれを使用して宣言された定数の範囲を示しています。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-120">The following table lists the scope of constants declared using each of the three ways mentioned above.</span></span>  
  
|<span data-ttu-id="5b0ed-121">定数の設定方法</span><span class="sxs-lookup"><span data-stu-id="5b0ed-121">How constant is set</span></span>|<span data-ttu-id="5b0ed-122">定数のスコープ</span><span class="sxs-lookup"><span data-stu-id="5b0ed-122">Scope of constant</span></span>|  
|---|---|  
|<span data-ttu-id="5b0ed-123">**プロジェクトデザイナー**</span><span class="sxs-lookup"><span data-stu-id="5b0ed-123">**Project Designer**</span></span>|<span data-ttu-id="5b0ed-124">プロジェクト内のすべてのファイルに対してパブリック</span><span class="sxs-lookup"><span data-stu-id="5b0ed-124">Public to all files in the project</span></span>|  
|<span data-ttu-id="5b0ed-125">[パッケージ実行ユーティリティ]</span><span class="sxs-lookup"><span data-stu-id="5b0ed-125">Command line</span></span>|<span data-ttu-id="5b0ed-126">コマンドラインコンパイラに渡されるすべてのファイルに対してパブリック</span><span class="sxs-lookup"><span data-stu-id="5b0ed-126">Public to all files passed to the command-line compiler</span></span>|  
|<span data-ttu-id="5b0ed-127">コード内の `#Const` ステートメント</span><span class="sxs-lookup"><span data-stu-id="5b0ed-127">`#Const` statement in code</span></span>|<span data-ttu-id="5b0ed-128">宣言されているファイルに対してプライベート</span><span class="sxs-lookup"><span data-stu-id="5b0ed-128">Private to the file in which it is declared</span></span>|  
  
|<span data-ttu-id="5b0ed-129">プロジェクトデザイナーで定数を設定するには</span><span class="sxs-lookup"><span data-stu-id="5b0ed-129">To set constants in the Project Designer</span></span>|  
|---|  
|<span data-ttu-id="5b0ed-130">-実行可能ファイルを作成する前に、「[プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)」に記載されている手順に従って、**プロジェクトデザイナー**で定数を設定します。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-130">-   Before creating your executable file, set constants in the **Project Designer** by following the steps provided in [Managing Project and Solution Properties](/visualstudio/ide/managing-project-and-solution-properties).</span></span>|  
  
|<span data-ttu-id="5b0ed-131">コマンドラインで定数を設定するには</span><span class="sxs-lookup"><span data-stu-id="5b0ed-131">To set constants at the command line</span></span>|  
|---|  
|<span data-ttu-id="5b0ed-132">-次の例に示すように、 **-d**スイッチを使用して条件付きコンパイル定数を入力します。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-132">-   Use the **-d** switch to enter conditional compilation constants, as in the following example:</span></span><br />     `vbc MyProj.vb /d:conFrenchVersion=–1:conANSI=0`<br />     <span data-ttu-id="5b0ed-133">**-D**スイッチと最初の定数の間にスペースは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-133">No space is required between the **-d** switch and the first constant.</span></span> <span data-ttu-id="5b0ed-134">詳細については、「 [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-134">For more information, see [-define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md).</span></span><br />     <span data-ttu-id="5b0ed-135">コマンドライン宣言は、**プロジェクトデザイナー**で入力された宣言をオーバーライドしますが、削除はしません。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-135">Command-line declarations override declarations entered in the **Project Designer**, but do not erase them.</span></span> <span data-ttu-id="5b0ed-136">**プロジェクトデザイナー**で設定された引数は、後続のコンパイルに有効なままです。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-136">Arguments set in **Project Designer** remain in effect for subsequent compilations.</span></span><br />     <span data-ttu-id="5b0ed-137">コード自体に定数を記述する場合、そのスコープが宣言されているモジュール全体であるため、配置に関して厳密な規則はありません。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-137">When writing constants in the code itself, there are no strict rules as to their placement, since their scope is the entire module in which they are declared.</span></span>|  
  
|<span data-ttu-id="5b0ed-138">コードに定数を設定するには</span><span class="sxs-lookup"><span data-stu-id="5b0ed-138">To set constants in your code</span></span>|  
|---|  
|<span data-ttu-id="5b0ed-139">-使用されているモジュールの宣言ブロックに定数を配置します。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-139">-   Place the constants in the declaration block of the module in which they are used.</span></span> <span data-ttu-id="5b0ed-140">これにより、コードの整理と読み取りが容易になります。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-140">This helps keep your code organized and easier to read.</span></span>|  
  
## <a name="related-topics"></a><span data-ttu-id="5b0ed-141">関連トピック</span><span class="sxs-lookup"><span data-stu-id="5b0ed-141">Related Topics</span></span>  
  
|<span data-ttu-id="5b0ed-142">タイトル</span><span class="sxs-lookup"><span data-stu-id="5b0ed-142">Title</span></span>|<span data-ttu-id="5b0ed-143">説明</span><span class="sxs-lookup"><span data-stu-id="5b0ed-143">Description</span></span>|  
|---|---|  
|[<span data-ttu-id="5b0ed-144">プログラム構造とコード規則</span><span class="sxs-lookup"><span data-stu-id="5b0ed-144">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)|<span data-ttu-id="5b0ed-145">コードを読みやすく、保守しやすいようにするための推奨事項を示します。</span><span class="sxs-lookup"><span data-stu-id="5b0ed-145">Provides suggestions for making your code easy to read and maintain.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="5b0ed-146">参照</span><span class="sxs-lookup"><span data-stu-id="5b0ed-146">Reference</span></span>  
 [<span data-ttu-id="5b0ed-147">#Const ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="5b0ed-147">#Const Directive</span></span>](../../../visual-basic/language-reference/directives/const-directive.md)  
  
 [<span data-ttu-id="5b0ed-148">#If...Then...#Else ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="5b0ed-148">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
  
 [<span data-ttu-id="5b0ed-149">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b0ed-149">-define (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/define.md)
