---
title: ICLRHostBindingPolicyManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRHostBindingPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostBindingPolicyManager
helpviewer_keywords:
- ICLRHostBindingPolicyManager interface [.NET Framework hosting]
ms.assetid: f9da168b-366b-4b2b-bdb9-330b6bad5a6b
topic_type:
- apiref
ms.openlocfilehash: 3cf2a945607bf85a51dbec35342ff5ac46878bca
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703569"
---
# <a name="iclrhostbindingpolicymanager-interface"></a><span data-ttu-id="018fd-102">ICLRHostBindingPolicyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="018fd-102">ICLRHostBindingPolicyManager Interface</span></span>
<span data-ttu-id="018fd-103">ホストが現在のバインドポリシーを評価し、指定されたアセンブリのポリシー変更を伝達するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="018fd-103">Provides methods for the host to evaluate current binding policy and communicate policy changes for a specified assembly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="018fd-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="018fd-104">Methods</span></span>  
  
|<span data-ttu-id="018fd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="018fd-105">Method</span></span>|<span data-ttu-id="018fd-106">説明</span><span class="sxs-lookup"><span data-stu-id="018fd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="018fd-107">EvaluatePolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="018fd-107">EvaluatePolicy Method</span></span>](iclrhostbindingpolicymanager-evaluatepolicy-method.md)|<span data-ttu-id="018fd-108">ホストの代わりにバインドポリシーを評価します。</span><span class="sxs-lookup"><span data-stu-id="018fd-108">Evaluates binding policy on behalf of the host.</span></span>|  
|[<span data-ttu-id="018fd-109">ModifyApplicationPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="018fd-109">ModifyApplicationPolicy Method</span></span>](iclrhostbindingpolicymanager-modifyapplicationpolicy-method.md)|<span data-ttu-id="018fd-110">指定したアセンブリのバインディングポリシーを変更し、新しいバージョンのポリシーを作成します。</span><span class="sxs-lookup"><span data-stu-id="018fd-110">Modifies the binding policy for the specified assembly, and creates a new version of the policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="018fd-111">要件</span><span class="sxs-lookup"><span data-stu-id="018fd-111">Requirements</span></span>  
 <span data-ttu-id="018fd-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="018fd-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="018fd-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="018fd-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="018fd-114">**ライブラリ:** Mscoree.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="018fd-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="018fd-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="018fd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="018fd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="018fd-116">See also</span></span>

- [<span data-ttu-id="018fd-117">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="018fd-117">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="018fd-118">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="018fd-118">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="018fd-119">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="018fd-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
