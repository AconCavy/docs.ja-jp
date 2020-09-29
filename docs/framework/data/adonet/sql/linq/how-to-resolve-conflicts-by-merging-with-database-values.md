---
title: '方法: データベース値とマージすることで競合を解決する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1988b79c-3bfc-4c5c-a08a-86cf638bbe17
ms.openlocfilehash: fb77c4a23a4c4fa93dc55e63858ee41783c197ee
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166184"
---
# <a name="how-to-resolve-conflicts-by-merging-with-database-values"></a><span data-ttu-id="26060-102">方法: データベース値とマージすることで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="26060-102">How to: Resolve Conflicts by Merging with Database Values</span></span>

<span data-ttu-id="26060-103">変更内容を再送信する前に、データベース内の予期した値と実際の値の違いを調整するために、<xref:System.Data.Linq.RefreshMode.KeepChanges> を使用して、データベース内の値を現在のクライアント メンバー値とマージできます。</span><span class="sxs-lookup"><span data-stu-id="26060-103">To reconcile differences between expected and actual database values before you try to resubmit your changes, you can use <xref:System.Data.Linq.RefreshMode.KeepChanges> to merge database values with the current client member values.</span></span> <span data-ttu-id="26060-104">詳しくは、「[オプティミスティック コンカレンシー: 概要)](optimistic-concurrency-overview.md) の下のステートメントを右クリックします。</span><span class="sxs-lookup"><span data-stu-id="26060-104">For more information, see [Optimistic Concurrency: Overview](optimistic-concurrency-overview.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26060-105">どの場合も、データベースから最新のデータを取得することで、まずクライアントのレコードが更新されます。</span><span class="sxs-lookup"><span data-stu-id="26060-105">In all cases, the record on the client is first refreshed by retrieving the updated data from the database.</span></span> <span data-ttu-id="26060-106">この処理によって、次の更新処理が同じコンカレンシー チェックで失敗することを防止できます。</span><span class="sxs-lookup"><span data-stu-id="26060-106">This action makes sure that the next update try will not fail on the same concurrency checks.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26060-107">例</span><span class="sxs-lookup"><span data-stu-id="26060-107">Example</span></span>  

 <span data-ttu-id="26060-108">このシナリオでは、ユーザー 1 が変更内容を送信しようとしたときに <xref:System.Data.Linq.ChangeConflictException> 例外がスローされます。途中でユーザー 2 が Assistant 列と Department  列を変更したためです。</span><span class="sxs-lookup"><span data-stu-id="26060-108">In this scenario, a <xref:System.Data.Linq.ChangeConflictException> exception is thrown when User1 tries to submit changes, because User2 has in the meantime changed the Assistant and Department columns.</span></span> <span data-ttu-id="26060-109">次の表は、この状況を示しています。</span><span class="sxs-lookup"><span data-stu-id="26060-109">The following table shows the situation.</span></span>  
  
||<span data-ttu-id="26060-110">管理者</span><span class="sxs-lookup"><span data-stu-id="26060-110">Manager</span></span>|<span data-ttu-id="26060-111">Assistant</span><span class="sxs-lookup"><span data-stu-id="26060-111">Assistant</span></span>|<span data-ttu-id="26060-112">Department</span><span class="sxs-lookup"><span data-stu-id="26060-112">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="26060-113">ユーザー 1 およびユーザー 2 が照会した最初のデータベース状態</span><span class="sxs-lookup"><span data-stu-id="26060-113">Original database state when queried by User1 and User2.</span></span>|<span data-ttu-id="26060-114">Alfreds</span><span class="sxs-lookup"><span data-stu-id="26060-114">Alfreds</span></span>|<span data-ttu-id="26060-115">Maria</span><span class="sxs-lookup"><span data-stu-id="26060-115">Maria</span></span>|<span data-ttu-id="26060-116">Sales</span><span class="sxs-lookup"><span data-stu-id="26060-116">Sales</span></span>|  
|<span data-ttu-id="26060-117">ユーザー 1 が送信しようとした変更内容</span><span class="sxs-lookup"><span data-stu-id="26060-117">User1 prepares to submit these changes.</span></span>|<span data-ttu-id="26060-118">Alfred</span><span class="sxs-lookup"><span data-stu-id="26060-118">Alfred</span></span>||<span data-ttu-id="26060-119">Marketing</span><span class="sxs-lookup"><span data-stu-id="26060-119">Marketing</span></span>|  
|<span data-ttu-id="26060-120">ユーザー 2 が既に送信した変更内容</span><span class="sxs-lookup"><span data-stu-id="26060-120">User2 has already submitted these changes.</span></span>||<span data-ttu-id="26060-121">Mary</span><span class="sxs-lookup"><span data-stu-id="26060-121">Mary</span></span>|<span data-ttu-id="26060-122">サービス</span><span class="sxs-lookup"><span data-stu-id="26060-122">Service</span></span>|  
  
 <span data-ttu-id="26060-123">ユーザー 1 は、この競合を解決するために、データベース値を現在のクライアント メンバー値にマージすることに決めます。</span><span class="sxs-lookup"><span data-stu-id="26060-123">User1 decides to resolve this conflict by merging database values with the current client member values.</span></span> <span data-ttu-id="26060-124">その結果、現在の変更セットでも値が変更されているデータベース値のみが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="26060-124">The result will be that database values are overwritten only when the current changeset has also modified that value.</span></span>  
  
 <span data-ttu-id="26060-125">ユーザー 1 が <xref:System.Data.Linq.RefreshMode.KeepChanges> を使用して競合を解決すると、データベース内の結果は次の表のようになります。</span><span class="sxs-lookup"><span data-stu-id="26060-125">When User1 resolves the conflict by using <xref:System.Data.Linq.RefreshMode.KeepChanges>, the result in the database is as in the following table:</span></span>  
  
||<span data-ttu-id="26060-126">管理者</span><span class="sxs-lookup"><span data-stu-id="26060-126">Manager</span></span>|<span data-ttu-id="26060-127">Assistant</span><span class="sxs-lookup"><span data-stu-id="26060-127">Assistant</span></span>|<span data-ttu-id="26060-128">Department</span><span class="sxs-lookup"><span data-stu-id="26060-128">Department</span></span>|  
|------|-------------|---------------|----------------|  
|<span data-ttu-id="26060-129">競合解決後の新しい状態</span><span class="sxs-lookup"><span data-stu-id="26060-129">New state after conflict resolution.</span></span>|<span data-ttu-id="26060-130">Alfred</span><span class="sxs-lookup"><span data-stu-id="26060-130">Alfred</span></span><br /><br /> <span data-ttu-id="26060-131">(ユーザー 1 の値)</span><span class="sxs-lookup"><span data-stu-id="26060-131">(from User1)</span></span>|<span data-ttu-id="26060-132">Mary</span><span class="sxs-lookup"><span data-stu-id="26060-132">Mary</span></span><br /><br /> <span data-ttu-id="26060-133">(ユーザー 2 の値)</span><span class="sxs-lookup"><span data-stu-id="26060-133">(from User2)</span></span>|<span data-ttu-id="26060-134">Marketing</span><span class="sxs-lookup"><span data-stu-id="26060-134">Marketing</span></span><br /><br /> <span data-ttu-id="26060-135">(ユーザー 1 の値)</span><span class="sxs-lookup"><span data-stu-id="26060-135">(from User1)</span></span>|  
  
 <span data-ttu-id="26060-136">次の例では、クライアントでも値が変更されている場合を除き、データベース値を現在のクライアント メンバー値にマージする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="26060-136">The following example shows how to merge database values with the current client member values (unless the client has also changed that value).</span></span> <span data-ttu-id="26060-137">個別のメンバーの競合に対する検査やカスタム ハンドリングは発生しません。</span><span class="sxs-lookup"><span data-stu-id="26060-137">No inspection or custom handling of individual member conflicts occurs.</span></span>  
  
 [!code-csharp[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.refreshmode/cs/program.cs#3)]
 [!code-vb[System.Data.Linq.RefreshMode#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.refreshmode/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="26060-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="26060-138">See also</span></span>

- [<span data-ttu-id="26060-139">方法: データベース値を上書きすることで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="26060-139">How to: Resolve Conflicts by Overwriting Database Values</span></span>](how-to-resolve-conflicts-by-overwriting-database-values.md)
- [<span data-ttu-id="26060-140">方法: データベース値を維持することで競合を解決する</span><span class="sxs-lookup"><span data-stu-id="26060-140">How to: Resolve Conflicts by Retaining Database Values</span></span>](how-to-resolve-conflicts-by-retaining-database-values.md)
- [<span data-ttu-id="26060-141">方法: 変更の競合を管理する</span><span class="sxs-lookup"><span data-stu-id="26060-141">How to: Manage Change Conflicts</span></span>](how-to-manage-change-conflicts.md)
