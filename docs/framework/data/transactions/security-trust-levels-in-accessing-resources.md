---
title: リソースへのアクセス時のセキュリティ信頼レベル
description: .NET でのリソースへのアクセス時のセキュリティ信頼レベルを理解します。 System.Transactions には主な信頼レベルが 3 つあります。
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: cbae3e87fc11a4230ba8f62cdbc273677e220bfb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152911"
---
# <a name="security-trust-levels-in-accessing-resources"></a><span data-ttu-id="89032-104">リソースへのアクセス時のセキュリティ信頼レベル</span><span class="sxs-lookup"><span data-stu-id="89032-104">Security Trust Levels in Accessing Resources</span></span>

<span data-ttu-id="89032-105">ここでは、<xref:System.Transactions> が公開するリソースの種類に対して、アクセスがどのように制限されるかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="89032-105">This topic discusses how access is restricted on the types of resources that <xref:System.Transactions> exposes.</span></span>  
  
 <span data-ttu-id="89032-106"><xref:System.Transactions> には、主に 3 つの信頼レベルがあります。</span><span class="sxs-lookup"><span data-stu-id="89032-106">There are three main levels of trust for <xref:System.Transactions>.</span></span> <span data-ttu-id="89032-107">信頼レベルは、<xref:System.Transactions> が公開するリソースの種類と、そのリソースにアクセスするために必要な信頼レベルに基づいて定義されます。</span><span class="sxs-lookup"><span data-stu-id="89032-107">The trust levels are defined based on the types of resources that <xref:System.Transactions> exposes, and the level of trust that should be required to access those resources.</span></span> <span data-ttu-id="89032-108"><xref:System.Transactions> がアクセスを提供するリソースは、システム メモリ、プロセス全体の共有リソース、およびシステム全体のリソースです。</span><span class="sxs-lookup"><span data-stu-id="89032-108">The resources that <xref:System.Transactions> provides access to are system memory, shared process wide resources, and system wide resources.</span></span> <span data-ttu-id="89032-109">次のようなレベルがあります。</span><span class="sxs-lookup"><span data-stu-id="89032-109">The levels are:</span></span>  
  
- <span data-ttu-id="89032-110">単一のアプリケーション ドメイン内でトランザクションを使用するアプリケーション用の **AllowPartiallyTrustedCallers** (APTCA)。</span><span class="sxs-lookup"><span data-stu-id="89032-110">**AllowPartiallyTrustedCallers** (APTCA) for applications using transactions within a single application domain.</span></span>  
  
- <span data-ttu-id="89032-111">分散トランザクションを使用するアプリケーション用の **DistributedTransactionPermission** (DTP)。</span><span class="sxs-lookup"><span data-stu-id="89032-111">**DistributedTransactionPermission** (DTP) for applications using distributed transactions.</span></span>  
  
- <span data-ttu-id="89032-112">永続性リソース、構成管理アプリケーション、およびレガシ相互運用アプリケーション用の完全信頼。</span><span class="sxs-lookup"><span data-stu-id="89032-112">Full trust for durable resources, configuration management applications, and legacy interop applications.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="89032-113">偽装されたコンテキストで参加インターフェイスを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="89032-113">You should not call any of the enlistment interfaces with impersonated contexts.</span></span>  
  
## <a name="trust-levels"></a><span data-ttu-id="89032-114">信頼レベル</span><span class="sxs-lookup"><span data-stu-id="89032-114">Trust Levels</span></span>  
  
### <a name="aptca-partial-trust"></a><span data-ttu-id="89032-115">APTCA (部分的信頼)</span><span class="sxs-lookup"><span data-stu-id="89032-115">APTCA (Partial Trust)</span></span>  

 <span data-ttu-id="89032-116"><xref:System.Transactions> アセンブリは、**AllowPartiallyTrustedCallers** 属性 (APTCA) でマークされているため、部分的に信頼されているコードから呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="89032-116">The <xref:System.Transactions> assembly can be called by partially trusted code because it has been marked with the **AllowPartiallyTrustedCallers** attribute (APTCA).</span></span> <span data-ttu-id="89032-117">この属性は基本的に、**FullTrust** アクセス許可セットの暗黙的な <xref:System.Security.Permissions.SecurityAction.LinkDemand> を削除します。削除しない場合、これは各種類のパブリックにアクセスできるメソッドに自動的に配置されます。</span><span class="sxs-lookup"><span data-stu-id="89032-117">This attribute essentially removes the implicit <xref:System.Security.Permissions.SecurityAction.LinkDemand> for the **FullTrust** permission set that is otherwise automatically placed on each publicly accessible method in each type.</span></span> <span data-ttu-id="89032-118">ただし、種類やメンバーによっては、さらに強力なアクセス許可が必要となります。</span><span class="sxs-lookup"><span data-stu-id="89032-118">However, some types and members still require stronger permissions.</span></span>  
  
 <span data-ttu-id="89032-119">APTCA 属性により、アプリケーションは単一のアプリケーション ドメイン内で、部分的に信頼してトランザクションを使用できます。</span><span class="sxs-lookup"><span data-stu-id="89032-119">The APTCA attribute enables applications to use transactions in partial trust within a single application domain.</span></span> <span data-ttu-id="89032-120">これにより、エラー処理で使用できる非エスカレーション トランザクションと揮発性の参加リストが有効になります。</span><span class="sxs-lookup"><span data-stu-id="89032-120">This enables non-escalated transactions and volatile enlistments that can be used for error handling.</span></span> <span data-ttu-id="89032-121">こうした例の 1 つが、トランザクション処理されたハッシュ テーブルとそれを使用するアプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="89032-121">One example of this is a transacted hash table and an application that uses it.</span></span> <span data-ttu-id="89032-122">単一トランザクション下で、ハッシュ テーブルに対してデータを追加および削除できます。</span><span class="sxs-lookup"><span data-stu-id="89032-122">Data can be added to and removed from the hash table under a single transaction.</span></span> <span data-ttu-id="89032-123">トランザクションが後でロール バックされた場合、そのトランザクション下でハッシュ テーブルに加えられたすべての変更を元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="89032-123">If the transaction is later rolled back, all of the changes made to the hash table under that transaction can be undone.</span></span>  
  
### <a name="distributedtransactionpermission-dtp"></a><span data-ttu-id="89032-124">DTP (DistributedTransactionPermission)</span><span class="sxs-lookup"><span data-stu-id="89032-124">DistributedTransactionPermission (DTP)</span></span>  

 <span data-ttu-id="89032-125">MSDTC で管理されるように <xref:System.Transactions> トランザクションがエスカレーションされた場合、<xref:System.Transactions> は分散トランザクションを作成するために <xref:System.Transactions.DistributedTransactionPermission> (DTP) を要求します。</span><span class="sxs-lookup"><span data-stu-id="89032-125">When a <xref:System.Transactions> transaction is escalated to be managed by MSDTC, <xref:System.Transactions> demands the <xref:System.Transactions.DistributedTransactionPermission> (DTP) to create the distributed transaction.</span></span> <span data-ttu-id="89032-126">これは、(シリアル化や追加の永続参加リストなどを介して) トランザクションをエスカレーションするコードに DTP を付与する必要があることを意味します。</span><span class="sxs-lookup"><span data-stu-id="89032-126">This means that the code that causes the transaction to be escalated (such as through serialization or additional durable enlistments) would need to be granted DTP.</span></span> <span data-ttu-id="89032-127"><xref:System.Transactions> トランザクションを最初に作成したコードでは、このアクセス許可を必ずしも所有する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89032-127">The code that originally created the <xref:System.Transactions> transaction does not necessarily need to possess this permission.</span></span>  
  
### <a name="fulltrust-link-demands"></a><span data-ttu-id="89032-128">FullTrust リンク要求</span><span class="sxs-lookup"><span data-stu-id="89032-128">FullTrust Link Demands</span></span>  

 <span data-ttu-id="89032-129">このアクセス許可レベルは、永続性リソースに書き込むアプリケーションを制限することを目的としています。</span><span class="sxs-lookup"><span data-stu-id="89032-129">This permission level is intended to restrict applications that are writing to durable resources.</span></span> <span data-ttu-id="89032-130">エラー発生時に、アプリケーションはトランザクション マネージャーにより回復し、トランザクションの最終結果を判定して永続的なデータを更新できるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="89032-130">Upon failure, the application needs to be able to recover with the transaction manager to determine the final outcome of the transaction, so that it can update permanent data.</span></span> <span data-ttu-id="89032-131">この種類のアプリケーションは、永続的リソース マネージャーと呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="89032-131">This type of application is known as a durable source manager.</span></span> <span data-ttu-id="89032-132">この種類のアプリケーションの典型的な例が SQL です。</span><span class="sxs-lookup"><span data-stu-id="89032-132">A classic example of this type of application is SQL.</span></span>  
  
 <span data-ttu-id="89032-133">回復を有効にするため、この種類のアプリケーションにはシステム リソースを永続的に消費する機能があります。</span><span class="sxs-lookup"><span data-stu-id="89032-133">To enable recovery, this type of application has the ability to permanently consume system resources.</span></span> <span data-ttu-id="89032-134">これは、トランザクションに参加しているすべての永続的リソース マネージャーが結果を受信したことを確認するまで、回復可能なトランザクション マネージャーはコミットしたトランザクションを記憶する必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="89032-134">This is because the recoverable transaction manager must remember transactions that have committed until it can confirm that all durable resource managers that are participating in the transaction have received the outcome.</span></span> <span data-ttu-id="89032-135">したがって、この種類のアプリケーションには完全な信頼が必要です。完全な信頼レベルが付与されない限り、実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="89032-135">Therefore, this type of application requires full trust and should not be run unless that level of trust has been granted.</span></span>  
  
 <span data-ttu-id="89032-136">永続参加リストと回復の詳細については、「[トランザクションの参加要素としてのリソースの参加](enlisting-resources-as-participants-in-a-transaction.md)」および「[回復の実行](performing-recovery.md)」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="89032-136">For more information on durable enlistments and recovery, see the [Enlisting Resources as Participants in a Transaction](enlisting-resources-as-participants-in-a-transaction.md) and [Performing Recovery](performing-recovery.md) topics.</span></span>  
  
 <span data-ttu-id="89032-137">COM+ とのレガシ相互運用を実行するアプリケーションにも、完全な信頼が必要です。</span><span class="sxs-lookup"><span data-stu-id="89032-137">Applications that perform legacy interop work with COM+ are also required to have full trust.</span></span>  
  
 <span data-ttu-id="89032-138">以下に示す型とメンバーは、**FullTrust** 宣言セキュリティ属性で装飾されているため、部分的に信頼されたコードで呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="89032-138">The following is a list of types and members that are not callable by partially trusted code because they are decorated with the **FullTrust** declarative security attribute:</span></span>  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 <span data-ttu-id="89032-139">これらの型やメソッドを使用するために設定された **FullTrust** アクセス許可を所有する必要があるのは、直前の呼び出し元のみです。</span><span class="sxs-lookup"><span data-stu-id="89032-139">Only the immediate caller is required to possess the **FullTrust** permission set to use the above types or methods.</span></span>
