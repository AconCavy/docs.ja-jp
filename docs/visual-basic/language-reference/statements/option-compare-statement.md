---
title: Option Compare ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: 7538466c8f4b90e2e655a2ec762d8c545546a481
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344425"
---
# <a name="option-compare-statement"></a><span data-ttu-id="c7395-102">Option Compare ステートメント</span><span class="sxs-lookup"><span data-stu-id="c7395-102">Option Compare Statement</span></span>
<span data-ttu-id="c7395-103">文字列データを比較するときに使用する既定の比較方法を宣言します。</span><span class="sxs-lookup"><span data-stu-id="c7395-103">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7395-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7395-104">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="c7395-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="c7395-105">Parts</span></span>  
  
|<span data-ttu-id="c7395-106">用語</span><span class="sxs-lookup"><span data-stu-id="c7395-106">Term</span></span>|<span data-ttu-id="c7395-107">定義</span><span class="sxs-lookup"><span data-stu-id="c7395-107">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="c7395-108">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c7395-108">Optional.</span></span> <span data-ttu-id="c7395-109">文字列比較は、文字の内部バイナリ表現から派生した並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="c7395-109">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="c7395-110">この種類の比較は、文字列にテキストとして解釈されない文字を含めることができる場合に特に便利です。</span><span class="sxs-lookup"><span data-stu-id="c7395-110">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="c7395-111">この場合、大文字と小文字の区別など、アルファベットの等値比較にバイアスをかけないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="c7395-111">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="c7395-112">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="c7395-112">Optional.</span></span> <span data-ttu-id="c7395-113">文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。</span><span class="sxs-lookup"><span data-stu-id="c7395-113">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="c7395-114">この種類の比較は、文字列にすべてのテキスト文字が含まれており、大文字と小文字を区別しないことや類縁の文字など、アルファベットの等値を考慮して文字列を比較する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c7395-114">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="c7395-115">たとえば、`A` と `a` は等しく、`Ä` と `ä` は `B` と `b` よりも前に位置すると見なされるようにできます。</span><span class="sxs-lookup"><span data-stu-id="c7395-115">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7395-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="c7395-116">Remarks</span></span>  
 <span data-ttu-id="c7395-117">使用した場合、`Option Compare` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7395-117">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="c7395-118">`Option Compare` ステートメントでは、文字列の比較方法 (`Binary` または `Text`) を指定します。</span><span class="sxs-lookup"><span data-stu-id="c7395-118">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="c7395-119">既定のテキスト比較方法は `Binary` です。</span><span class="sxs-lookup"><span data-stu-id="c7395-119">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="c7395-120">`Binary` 比較では、各文字列の各文字の Unicode 数値が比較されます。</span><span class="sxs-lookup"><span data-stu-id="c7395-120">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="c7395-121">`Text` 比較では、現在のカルチャでの語彙的意味に基づいて各 Unicode 文字が比較されます。</span><span class="sxs-lookup"><span data-stu-id="c7395-121">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="c7395-122">Microsoft Windows では、並べ替え順序はコード ページによって決まります。</span><span class="sxs-lookup"><span data-stu-id="c7395-122">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="c7395-123">詳細については、「[コード ページ](/cpp/c-runtime-library/code-pages)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7395-123">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="c7395-124">次の例では、英語/ヨーロッパ言語のコード ページ (ANSI 1252) の文字が、`Option Compare Binary` を使用して並べ替えられ、一般的なバイナリ並べ替え順序が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c7395-124">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="c7395-125">`Option Compare Text` を使用して同じコード ページの同じ文字を並べ替えると、次のテキスト並べ替え順序が生成されます。</span><span class="sxs-lookup"><span data-stu-id="c7395-125">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="c7395-126">Option Compare ステートメントが指定されていない場合</span><span class="sxs-lookup"><span data-stu-id="c7395-126">When an Option Compare Statement Is Not Present</span></span>  
 <span data-ttu-id="c7395-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span><span class="sxs-lookup"><span data-stu-id="c7395-127">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="c7395-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span><span class="sxs-lookup"><span data-stu-id="c7395-128">If you use the command-line compiler, the setting specified by the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="c7395-129">IDE で Option Compare を設定するには</span><span class="sxs-lookup"><span data-stu-id="c7395-129">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="c7395-130">**ソリューション エクスプローラー**でプロジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="c7395-130">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="c7395-131">**[プロジェクト]** メニューの **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7395-131">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="c7395-132">**[コンパイル]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7395-132">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="c7395-133">Set the value in the **Option Compare** box.</span><span class="sxs-lookup"><span data-stu-id="c7395-133">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="c7395-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span><span class="sxs-lookup"><span data-stu-id="c7395-134">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="c7395-135">To change this setting, on the **Tools** menu, click **Options**.</span><span class="sxs-lookup"><span data-stu-id="c7395-135">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="c7395-136">**[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c7395-136">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="c7395-137">The initial default setting in **VB Defaults** is **Binary**.</span><span class="sxs-lookup"><span data-stu-id="c7395-137">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="c7395-138">コマンド ラインで Option Compare を設定するには</span><span class="sxs-lookup"><span data-stu-id="c7395-138">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="c7395-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span><span class="sxs-lookup"><span data-stu-id="c7395-139">Include the [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7395-140">例</span><span class="sxs-lookup"><span data-stu-id="c7395-140">Example</span></span>  
 <span data-ttu-id="c7395-141">次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法としてバイナリ比較を設定します。</span><span class="sxs-lookup"><span data-stu-id="c7395-141">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="c7395-142">このコードを使用するには、`Option Compare Binary` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。</span><span class="sxs-lookup"><span data-stu-id="c7395-142">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="c7395-143">例</span><span class="sxs-lookup"><span data-stu-id="c7395-143">Example</span></span>  
 <span data-ttu-id="c7395-144">次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法として大文字と小文字を区別しないテキスト並べ替え順序を設定します。</span><span class="sxs-lookup"><span data-stu-id="c7395-144">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="c7395-145">このコードを使用するには、`Option Compare Text` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。</span><span class="sxs-lookup"><span data-stu-id="c7395-145">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="c7395-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7395-146">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="c7395-147">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="c7395-147">-optioncompare</span></span>](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="c7395-148">比較演算子</span><span class="sxs-lookup"><span data-stu-id="c7395-148">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="c7395-149">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7395-149">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="c7395-150">Like 演算子</span><span class="sxs-lookup"><span data-stu-id="c7395-150">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="c7395-151">文字列関数</span><span class="sxs-lookup"><span data-stu-id="c7395-151">String Functions</span></span>](../../../visual-basic/language-reference/functions/string-functions.md)
- [<span data-ttu-id="c7395-152">Option Explicit ステートメント</span><span class="sxs-lookup"><span data-stu-id="c7395-152">Option Explicit Statement</span></span>](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [<span data-ttu-id="c7395-153">Option Strict ステートメント</span><span class="sxs-lookup"><span data-stu-id="c7395-153">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
