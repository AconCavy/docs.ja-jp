---
title: ICorDebugThread::GetActiveChain メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: 70e79378ad8eb2599199a1f7bc57cf530c9b4dd3
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379694"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="8f3fb-102">ICorDebugThread::GetActiveChain メソッド</span><span class="sxs-lookup"><span data-stu-id="8f3fb-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="8f3fb-103">このスレッドオブジェクトのアクティブな (最新の) スタックチェーンへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8f3fb-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f3fb-104">構文</span><span class="sxs-lookup"><span data-stu-id="8f3fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f3fb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8f3fb-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="8f3fb-106">入出力スタックチェーンを表す、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="8f3fb-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f3fb-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="8f3fb-107">Remarks</span></span>  
 <span data-ttu-id="8f3fb-108">`ppChain`現在アクティブになっているスタックチェーンがない場合、パラメーターは null になります。</span><span class="sxs-lookup"><span data-stu-id="8f3fb-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f3fb-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="8f3fb-109">Requirements</span></span>  
 <span data-ttu-id="8f3fb-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f3fb-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f3fb-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f3fb-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f3fb-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f3fb-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f3fb-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f3fb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
