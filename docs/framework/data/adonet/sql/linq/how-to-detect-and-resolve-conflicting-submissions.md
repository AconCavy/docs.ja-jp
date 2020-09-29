---
title: '方法: 送信の競合を検出および解決する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
ms.openlocfilehash: 96e96208d9bb28092701164e6cd5943ef81515a5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91147724"
---
# <a name="how-to-detect-and-resolve-conflicting-submissions"></a><span data-ttu-id="63d3b-102">方法: 送信の競合を検出および解決する</span><span class="sxs-lookup"><span data-stu-id="63d3b-102">How to: Detect and Resolve Conflicting Submissions</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="63d3b-103">には、複数のユーザーがデータベースを変更するために生じる競合を、検出および解決するための多くのリソースが用意されています。</span><span class="sxs-lookup"><span data-stu-id="63d3b-103">provides many resources for detecting and resolving conflicts that stem from multi-user changes to the database.</span></span> <span data-ttu-id="63d3b-104">詳細については、[変更の競合を管理する](how-to-manage-change-conflicts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63d3b-104">For more information, see [How to: Manage Change Conflicts](how-to-manage-change-conflicts.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="63d3b-105">例</span><span class="sxs-lookup"><span data-stu-id="63d3b-105">Example</span></span>  

 <span data-ttu-id="63d3b-106"><xref:System.Data.Linq.ChangeConflictException> 例外をキャッチする `try`/`catch` ブロックの例を次にします。</span><span class="sxs-lookup"><span data-stu-id="63d3b-106">The following example shows a `try`/`catch` block that catches a <xref:System.Data.Linq.ChangeConflictException> exception.</span></span> <span data-ttu-id="63d3b-107">各競合のエンティティおよびメンバー情報が、コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="63d3b-107">Entity and member information for each conflict is displayed in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="63d3b-108">情報の取得をサポートするには、`using System.Reflection` ディレクティブ (Visual Basic の場合は `Imports System.Reflection`) を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="63d3b-108">You must include the `using System.Reflection` directive (`Imports System.Reflection` in Visual Basic) to support the information retrieval.</span></span> <span data-ttu-id="63d3b-109">詳細については、「<xref:System.Reflection>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63d3b-109">For more information, see <xref:System.Reflection>.</span></span>  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="63d3b-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="63d3b-110">See also</span></span>

- [<span data-ttu-id="63d3b-111">データの変更と変更の送信</span><span class="sxs-lookup"><span data-stu-id="63d3b-111">Making and Submitting Data Changes</span></span>](making-and-submitting-data-changes.md)
- [<span data-ttu-id="63d3b-112">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="63d3b-112">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
