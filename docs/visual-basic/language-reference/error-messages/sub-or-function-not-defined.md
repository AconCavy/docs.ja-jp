---
title: Sub または Function が定義されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 8b81460eccb6be8baa2ea7bc68d0f80c9d16398e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349577"
---
# <a name="sub-or-function-not-defined-visual-basic"></a><span data-ttu-id="6b2a3-102">Sub または Function が定義されていません。(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b2a3-102">Sub or Function not defined (Visual Basic)</span></span>
<span data-ttu-id="6b2a3-103">呼び出されるには、`Sub` または `Function` が定義されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-103">A `Sub` or `Function` must be defined in order to be called.</span></span> <span data-ttu-id="6b2a3-104">このエラーでは以下の原因が考えられます。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-104">Possible causes of this error include:</span></span>  
  
- <span data-ttu-id="6b2a3-105">プロシージャ名のスペルが間違っています。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-105">Misspelling the procedure name.</span></span>  
  
- <span data-ttu-id="6b2a3-106">**[参照]** ダイアログ ボックスで、プロジェクトへの参照を明示的に追加せずに、別のプロジェクトからプロシージャを呼び出そうとしています。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-106">Trying to call a procedure from another project without explicitly adding a reference to that project in the **References** dialog box.</span></span>  
  
- <span data-ttu-id="6b2a3-107">呼び出し元のプロシージャから参照できないプロシージャを指定しています。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-107">Specifying a procedure that is not visible to the calling procedure.</span></span>  
  
- <span data-ttu-id="6b2a3-108">指定したライブラリまたはコード リソースにない Windows ダイナミックリンク ライブラリ (DLL) ルーチンまたは Macintosh コードリソース ルーチンを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-108">Declaring a Windows dynamic-link library (DLL) routine or Macintosh code-resource routine that is not in the specified library or code resource.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6b2a3-109">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="6b2a3-109">To correct this error</span></span>  
  
1. <span data-ttu-id="6b2a3-110">プロシージャ名のスペルが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-110">Make sure that the procedure name is spelled correctly.</span></span>  
  
2. <span data-ttu-id="6b2a3-111">**[参照]** ダイアログボックスで、呼び出すプロシージャを含むプロジェクトの名前を見つけます。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-111">Find the name of the project containing the procedure you want to call in the **References** dialog box.</span></span> <span data-ttu-id="6b2a3-112">それが表示されない場合、 **[参照]** ボタンをクリックして検索します。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-112">If it does not appear, click the **Browse** button to search for it.</span></span> <span data-ttu-id="6b2a3-113">プロジェクト名の左側にあるチェック ボックスをオンにして、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-113">Select the check box to the left of the project name, and then click **OK**.</span></span>  
  
3. <span data-ttu-id="6b2a3-114">ルーチンの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="6b2a3-114">Check the name of the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2a3-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="6b2a3-115">See also</span></span>

- [<span data-ttu-id="6b2a3-116">エラーの種類</span><span class="sxs-lookup"><span data-stu-id="6b2a3-116">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="6b2a3-117">プロジェクト内の参照の管理</span><span class="sxs-lookup"><span data-stu-id="6b2a3-117">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
- [<span data-ttu-id="6b2a3-118">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="6b2a3-118">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="6b2a3-119">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="6b2a3-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
