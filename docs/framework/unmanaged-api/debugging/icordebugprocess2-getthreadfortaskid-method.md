---
title: ICorDebugProcess2::GetThreadForTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetThreadForTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetThreadForTaskID
helpviewer_keywords:
- ICorDebugProcess2::GetThreadForTaskId method [.NET Framework debugging]
- GetThreadForTaskID method [.NET Framework debugging]
ms.assetid: 32d54a5b-8ad3-405b-a1b9-0936a3b49d1e
topic_type:
- apiref
ms.openlocfilehash: 89be29c770098d92ce3c47f7c45b1bb8580f2edb
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213518"
---
# <a name="icordebugprocess2getthreadfortaskid-method"></a><span data-ttu-id="fc194-102">ICorDebugProcess2::GetThreadForTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="fc194-102">ICorDebugProcess2::GetThreadForTaskID Method</span></span>
<span data-ttu-id="fc194-103">指定した id を持つタスクが実行されているスレッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="fc194-103">Gets the thread on which the task with the specified identifier is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc194-104">構文</span><span class="sxs-lookup"><span data-stu-id="fc194-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadForTaskID (  
    [in]  TASKID            taskid,  
    [out] ICorDebugThread2  **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc194-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc194-105">Parameters</span></span>  
 `taskid`  
 <span data-ttu-id="fc194-106">からタスクの識別子です。</span><span class="sxs-lookup"><span data-stu-id="fc194-106">[in] The identifier of the task.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="fc194-107">入出力取得するスレッドを表す ICorDebugThread2 オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fc194-107">[out] A pointer to the address of an ICorDebugThread2 object that represents the thread to be retrieved.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc194-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc194-108">Remarks</span></span>  
 <span data-ttu-id="fc194-109">ホストは、 [ICLRTask:: SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md)メソッドを使用してタスク識別子を設定できます。</span><span class="sxs-lookup"><span data-stu-id="fc194-109">The host can set the task identifier by using the [ICLRTask::SetTaskIdentifier](../hosting/iclrtask-settaskidentifier-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc194-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="fc194-110">Requirements</span></span>  
 <span data-ttu-id="fc194-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc194-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc194-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc194-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc194-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc194-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc194-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc194-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
