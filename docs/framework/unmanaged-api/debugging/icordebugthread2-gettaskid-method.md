---
title: ICorDebugThread2::GetTaskID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 841af546cc3586529fe290c69e686438f634b90d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377783"
---
# <a name="icordebugthread2gettaskid-method"></a><span data-ttu-id="ced68-102">ICorDebugThread2::GetTaskID メソッド</span><span class="sxs-lookup"><span data-stu-id="ced68-102">ICorDebugThread2::GetTaskID Method</span></span>
<span data-ttu-id="ced68-103">このスレッドで実行されているタスクの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="ced68-103">Gets the identifier of the task running on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ced68-104">構文</span><span class="sxs-lookup"><span data-stu-id="ced68-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ced68-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ced68-105">Parameters</span></span>  
 `pTaskId`  
 <span data-ttu-id="ced68-106">入出力この ICorDebugThread2 オブジェクトによって表されるスレッド上で実行されているタスクの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ced68-106">[out] A pointer to the identifier of the task running on the thread represented by this ICorDebugThread2 object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ced68-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="ced68-107">Remarks</span></span>  
 <span data-ttu-id="ced68-108">スレッドが接続に関連付けられている場合にのみ、スレッドでタスクを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ced68-108">A task can only be running on the thread if the thread is associated with a connection.</span></span> <span data-ttu-id="ced68-109">`GetTaskID``pTaskId`スレッドが接続に関連付けられていない場合は、で0を返します。</span><span class="sxs-lookup"><span data-stu-id="ced68-109">`GetTaskID` returns zero in `pTaskId` if the thread is not associated with a connection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ced68-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="ced68-110">Requirements</span></span>  
 <span data-ttu-id="ced68-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ced68-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ced68-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ced68-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ced68-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ced68-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ced68-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ced68-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
