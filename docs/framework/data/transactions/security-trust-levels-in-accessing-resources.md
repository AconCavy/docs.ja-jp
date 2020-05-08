---
title: リソースへのアクセス時のセキュリティ信頼レベル
ms.date: 03/30/2017
ms.assetid: fb5be924-317d-4d69-b33a-3d18ecfb9d6e
ms.openlocfilehash: 7070d82c430b762059153c544e26478dc2d7ae39
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205875"
---
# <a name="security-trust-levels-in-accessing-resources"></a>リソースへのアクセス時のセキュリティ信頼レベル
ここでは、<xref:System.Transactions> が公開するリソースの種類に対して、アクセスがどのように制限されるかについて説明します。  
  
 <xref:System.Transactions> には、主に 3 つの信頼レベルがあります。 信頼レベルは、<xref:System.Transactions> が公開するリソースの種類と、そのリソースにアクセスするために必要な信頼レベルに基づいて定義されます。 <xref:System.Transactions> がアクセスを提供するリソースは、システム メモリ、プロセス全体の共有リソース、およびシステム全体のリソースです。 次のようなレベルがあります。  
  
- 単一のアプリケーション ドメイン内でトランザクションを使用するアプリケーション用の **AllowPartiallyTrustedCallers** (APTCA)。  
  
- 分散トランザクションを使用するアプリケーション用の **DistributedTransactionPermission** (DTP)。  
  
- 永続性リソース、構成管理アプリケーション、およびレガシ相互運用アプリケーション用の完全信頼。  
  
> [!NOTE]
> 偽装されたコンテキストで参加インターフェイスを呼び出さないでください。  
  
## <a name="trust-levels"></a>信頼レベル  
  
### <a name="aptca-partial-trust"></a>APTCA (部分的信頼)  
 <xref:System.Transactions> アセンブリは、**AllowPartiallyTrustedCallers** 属性 (APTCA) でマークされているため、部分的に信頼されているコードから呼び出すことができます。 この属性は基本的に、**FullTrust** アクセス許可セットの暗黙的な <xref:System.Security.Permissions.SecurityAction.LinkDemand> を削除します。削除しない場合、これは各種類のパブリックにアクセスできるメソッドに自動的に配置されます。 ただし、種類やメンバーによっては、さらに強力なアクセス許可が必要となります。  
  
 APTCA 属性により、アプリケーションは単一のアプリケーション ドメイン内で、部分的に信頼してトランザクションを使用できます。 これにより、エラー処理で使用できる非エスカレーション トランザクションと揮発性の参加リストが有効になります。 こうした例の 1 つが、トランザクション処理されたハッシュ テーブルとそれを使用するアプリケーションです。 単一トランザクション下で、ハッシュ テーブルに対してデータを追加および削除できます。 トランザクションが後でロール バックされた場合、そのトランザクション下でハッシュ テーブルに加えられたすべての変更を元に戻すことができます。  
  
### <a name="distributedtransactionpermission-dtp"></a>DTP (DistributedTransactionPermission)  
 MSDTC で管理されるように <xref:System.Transactions> トランザクションがエスカレーションされた場合、<xref:System.Transactions> は分散トランザクションを作成するために <xref:System.Transactions.DistributedTransactionPermission> (DTP) を要求します。 これは、(シリアル化や追加の永続参加リストなどを介して) トランザクションをエスカレーションするコードに DTP を付与する必要があることを意味します。 <xref:System.Transactions> トランザクションを最初に作成したコードでは、このアクセス許可を必ずしも所有する必要はありません。  
  
### <a name="fulltrust-link-demands"></a>FullTrust リンク要求  
 このアクセス許可レベルは、永続性リソースに書き込むアプリケーションを制限することを目的としています。 エラー発生時に、アプリケーションはトランザクション マネージャーにより回復し、トランザクションの最終結果を判定して永続的なデータを更新できるようにする必要があります。 この種類のアプリケーションは、永続的リソース マネージャーと呼ばれています。 この種類のアプリケーションの典型的な例が SQL です。  
  
 回復を有効にするため、この種類のアプリケーションにはシステム リソースを永続的に消費する機能があります。 これは、トランザクションに参加しているすべての永続的リソース マネージャーが結果を受信したことを確認するまで、回復可能なトランザクション マネージャーはコミットしたトランザクションを記憶する必要があるためです。 したがって、この種類のアプリケーションには完全な信頼が必要です。完全な信頼レベルが付与されない限り、実行しないでください。  
  
 永続参加リストと回復の詳細については、「[トランザクションの参加要素としてのリソースの参加](enlisting-resources-as-participants-in-a-transaction.md)」および「[回復の実行](performing-recovery.md)」のトピックを参照してください。  
  
 COM+ とのレガシ相互運用を実行するアプリケーションにも、完全な信頼が必要です。  
  
 以下に示す型とメンバーは、**FullTrust** 宣言セキュリティ属性で装飾されているため、部分的に信頼されたコードで呼び出すことはできません。  
  
 `PermissionSetAttribute(SecurityAction.LinkDemand, Name := "FullTrust")`  
  
- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>  
  
- <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>  
  
- <xref:System.Transactions.TransactionInterop>  
  
- <xref:System.Transactions.TransactionManager.DistributedTransactionStarted>  
  
- <xref:System.Transactions.HostCurrentTransactionCallback>  
  
- <xref:System.Transactions.TransactionManager.Reenlist%2A>  
  
- <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>  
  
- <xref:System.Transactions.TransactionScope.%23ctor%28System.Transactions.TransactionScopeOption%2CSystem.Transactions.TransactionOptions%2CSystem.Transactions.EnterpriseServicesInteropOption%29>  
  
 これらの型やメソッドを使用するために設定された **FullTrust** アクセス許可を所有する必要があるのは、直前の呼び出し元のみです。
