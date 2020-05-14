---
title: 構造体 '<structurename>' は少なくとも 1 つのインスタンス メンバー変数、または 'Custom' に設定されていない少なくとも 1 つのインスタンス イベント宣言を含まなければなりません。
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 4ce24073896326bb5a68e563e2d34aafa09ef1c1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593217"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="45353-102">構造体 '\<structurename>' には少なくとも 1 つのインスタンス メンバー変数、または 'Custom' とマークされていない少なくとも 1 つのインスタンス イベント宣言が含まれていなければなりません</span><span class="sxs-lookup"><span data-stu-id="45353-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="45353-103">構造体の定義には、非共有の変数または非共有の非カスタム イベントは含まれません。</span><span class="sxs-lookup"><span data-stu-id="45353-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="45353-104">すべての構造体には、すべてのインスタンスに対して集合的に ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)) ではなく、特定の各インスタンスに対して (非共有) 適用される変数またはイベントが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="45353-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="45353-105">非共有の定数、プロパティ、およびプロシージャは、この要件を満たしていません。</span><span class="sxs-lookup"><span data-stu-id="45353-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="45353-106">さらに、非共有の変数がなく、1 つの非共有イベントのみが存在する場合、そのイベントを `Custom` イベントにすることはできません。</span><span class="sxs-lookup"><span data-stu-id="45353-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="45353-107">**エラー ID:** BC30941</span><span class="sxs-lookup"><span data-stu-id="45353-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="45353-108">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="45353-108">To correct this error</span></span>  
  
- <span data-ttu-id="45353-109">`Shared` ではない変数またはイベントを少なくとも 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="45353-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="45353-110">イベントを 1 つだけ定義する場合、非共有にするだけでなく、非カスタムにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="45353-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45353-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="45353-111">See also</span></span>

- [<span data-ttu-id="45353-112">構造体</span><span class="sxs-lookup"><span data-stu-id="45353-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="45353-113">方法: 構造体を宣言する</span><span class="sxs-lookup"><span data-stu-id="45353-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="45353-114">Structure ステートメント</span><span class="sxs-lookup"><span data-stu-id="45353-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
