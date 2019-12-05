---
title: セキュリティ
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: 0fd77ce335848c58a7b734236124b90999355270
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837676"
---
# <a name="security"></a><span data-ttu-id="3c39a-102">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3c39a-102">Security</span></span>
<span data-ttu-id="3c39a-103">SQL Workflow Instance Store は、次のデータベース セキュリティ ロールを使用して、永続性データベースのインスタンス状態情報へのアクセスをセキュリティ保護します。</span><span class="sxs-lookup"><span data-stu-id="3c39a-103">The SQL Workflow Instance Store uses the following database security roles to secure access to instance state information in the persistence database.</span></span>  
  
- <span data-ttu-id="3c39a-104">**System.activities.durableinstancing.instances を処理**します。</span><span class="sxs-lookup"><span data-stu-id="3c39a-104">**System.Activities.DurableInstancing.InstanceStoreUsers**.</span></span> <span data-ttu-id="3c39a-105">このロールには、パブリック ビューへの読み取りおよび書き込みのアクセス権と、インスタンスの作成、読み込み、保存に関連するストアド プロシージャへの実行権限があります。</span><span class="sxs-lookup"><span data-stu-id="3c39a-105">This role has read and write access to public views and execution rights to stored procedures that are involved in creating, loading and saving instances.</span></span>  
  
- <span data-ttu-id="3c39a-106">**System.activities.durableinstancing.instances. InstanceStoreObservers**。</span><span class="sxs-lookup"><span data-stu-id="3c39a-106">**System.Activities.DurableInstancing.InstanceStoreObservers**.</span></span> <span data-ttu-id="3c39a-107">このロールには、パブリック ビューへの読み取り専用アクセス権があります。</span><span class="sxs-lookup"><span data-stu-id="3c39a-107">This role has read-only access to public views.</span></span>  
  
- <span data-ttu-id="3c39a-108">**System.activities.durableinstancing.instances. WorkflowActivationUsers**.</span><span class="sxs-lookup"><span data-stu-id="3c39a-108">**System.Activities.DurableInstancing.WorkflowActivationUsers**.</span></span> <span data-ttu-id="3c39a-109">このロールには、インスタンスのアクティベーション プロセスにかかわるストアド プロシージャへの実行権限があります。</span><span class="sxs-lookup"><span data-stu-id="3c39a-109">This role has execution rights to stored procedures that are involved in the instance activation process.</span></span> <span data-ttu-id="3c39a-110">インスタンスのアクティブ化の詳細については、「[インスタンスのアクティブ化](instance-activation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c39a-110">For more information about instance activation, see [Instance Activation](instance-activation.md).</span></span> <span data-ttu-id="3c39a-111">汎用ホスト (Windows Server AppFabric のホスト機能のワークフロー管理サービスなど) を実行するユーザーアカウントは、このデータベースロールに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c39a-111">The user account under which a generic host (such as the Workflow Management Service of the hosting features of Windows Server AppFabric) runs should be added to this database role.</span></span>  
  
 <span data-ttu-id="3c39a-112">Windows Server App Fabric での永続化ストアのセキュリティの詳細については、「 [App fabric の永続ストアのセキュリティ構成](https://docs.microsoft.com/previous-versions/appfabric/ff431727(v=azure.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c39a-112">For more information about security for persistence stores with Windows Server App Fabric, see [Security Configuration for Persistence Stores in App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff431727(v=azure.10))</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="3c39a-113">インスタンス ストア内にある固有のインスタンス データへのアクセス権を持つクライアントは、同じインスタンス ストア内にあるその他すべてのインスタンスにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="3c39a-113">A client that has access to its own instance data in the instance store has access to all other instances in the same instance store.</span></span> <span data-ttu-id="3c39a-114">インスタンス ストアでは、インスタンス レベルでセキュリティ アクセス許可を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="3c39a-114">The instance store does not support specifying security permissions at the instance level.</span></span> <span data-ttu-id="3c39a-115">個別のインスタンス ストアを作成し、ストアごとに、各グループやユーザーのアクセス権を設定します。</span><span class="sxs-lookup"><span data-stu-id="3c39a-115">You should create separate instance stores and map different groups/users to have access to different stores.</span></span>
