---
title: メソッドや複数行のラムダの内部では有効でないステートメントです。
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: 9e6c8ddd7851aee6d9fa1928a6854f7337b867b0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593226"
---
# <a name="statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="4a8d0-102">メソッドや複数行のラムダの内部では有効でないステートメントです。</span><span class="sxs-lookup"><span data-stu-id="4a8d0-102">Statement is not valid inside a method/multiline lambda</span></span>
<span data-ttu-id="4a8d0-103">ステートメントは、`Sub`、`Function`、プロパティ `Get`、またはプロパティ `Set` プロシージャ内で無効です。</span><span class="sxs-lookup"><span data-stu-id="4a8d0-103">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="4a8d0-104">一部のステートメントは、モジュール レベルまたはクラス レベルで配置できます。</span><span class="sxs-lookup"><span data-stu-id="4a8d0-104">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="4a8d0-105">`Option Strict` などの他のものは、名前空間レベルで、他のすべての宣言の前に配置する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4a8d0-105">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>  
  
 <span data-ttu-id="4a8d0-106">**エラー ID:** BC30024</span><span class="sxs-lookup"><span data-stu-id="4a8d0-106">**Error ID:** BC30024</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4a8d0-107">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="4a8d0-107">To correct this error</span></span>  
  
- <span data-ttu-id="4a8d0-108">プロシージャからステートメントを削除します。</span><span class="sxs-lookup"><span data-stu-id="4a8d0-108">Remove the statement from the procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a8d0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="4a8d0-109">See also</span></span>

- [<span data-ttu-id="4a8d0-110">Sub ステートメント</span><span class="sxs-lookup"><span data-stu-id="4a8d0-110">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="4a8d0-111">Function ステートメント</span><span class="sxs-lookup"><span data-stu-id="4a8d0-111">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="4a8d0-112">Get ステートメント</span><span class="sxs-lookup"><span data-stu-id="4a8d0-112">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="4a8d0-113">Set ステートメント</span><span class="sxs-lookup"><span data-stu-id="4a8d0-113">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
