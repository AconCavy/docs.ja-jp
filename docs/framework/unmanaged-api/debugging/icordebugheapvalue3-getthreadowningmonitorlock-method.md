---
title: ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetThreadOwningMonitorLock
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetThreadOwningMonitorLock
helpviewer_keywords:
- GetThreadOwningMonitorLock method [.NET Framework debugging]
- ICorDebugHeapValue3::GetThreadOwningMonitorLock method [.NET Framework debugging]
ms.assetid: e06fc19d-2cf4-4cad-81a3-137a68af8969
topic_type:
- apiref
ms.openlocfilehash: 9cc68e39dfef096b8ab6a8ba743f7a516cc349be
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210411"
---
# <a name="icordebugheapvalue3getthreadowningmonitorlock-method"></a><span data-ttu-id="07e3f-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock メソッド</span><span class="sxs-lookup"><span data-stu-id="07e3f-102">ICorDebugHeapValue3::GetThreadOwningMonitorLock Method</span></span>
<span data-ttu-id="07e3f-103">このオブジェクトのモニターロックを所有するマネージスレッドを返します。</span><span class="sxs-lookup"><span data-stu-id="07e3f-103">Returns the managed thread that owns the monitor lock on this object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e3f-104">構文</span><span class="sxs-lookup"><span data-stu-id="07e3f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadOwningMonitorLock (  
    [out] ICorDebugThread   **ppThread,  
    [out] DWORD              *pAcquisitionCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e3f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="07e3f-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="07e3f-106">入出力このオブジェクトのモニターロックを所有するマネージスレッド。</span><span class="sxs-lookup"><span data-stu-id="07e3f-106">[out] The managed thread that owns the monitor lock on this object.</span></span>  
  
 `pAcquisitionCount`  
 <span data-ttu-id="07e3f-107">入出力このスレッドがロックを解除してから、所有が解除されるまでの回数。</span><span class="sxs-lookup"><span data-stu-id="07e3f-107">[out] The number of times this thread would have to release the lock before it returns to being unowned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07e3f-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="07e3f-108">Return Value</span></span>  
 <span data-ttu-id="07e3f-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="07e3f-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="07e3f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="07e3f-110">HRESULT</span></span>|<span data-ttu-id="07e3f-111">説明</span><span class="sxs-lookup"><span data-stu-id="07e3f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="07e3f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="07e3f-112">S_OK</span></span>|<span data-ttu-id="07e3f-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="07e3f-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="07e3f-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="07e3f-114">S_FALSE</span></span>|<span data-ttu-id="07e3f-115">このオブジェクトのモニターロックを所有しているマネージスレッドはありません。</span><span class="sxs-lookup"><span data-stu-id="07e3f-115">No managed thread owns the monitor lock on this object.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="07e3f-116">例外</span><span class="sxs-lookup"><span data-stu-id="07e3f-116">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07e3f-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="07e3f-117">Remarks</span></span>  
 <span data-ttu-id="07e3f-118">マネージスレッドがこのオブジェクトのモニターロックを所有している場合は、次のようになります。</span><span class="sxs-lookup"><span data-stu-id="07e3f-118">If a managed thread owns the monitor lock on this object:</span></span>  
  
- <span data-ttu-id="07e3f-119">メソッドは S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="07e3f-119">The method returns S_OK.</span></span>  
  
- <span data-ttu-id="07e3f-120">スレッドオブジェクトは、スレッドが終了するまで有効です。</span><span class="sxs-lookup"><span data-stu-id="07e3f-120">The thread object is valid until the thread exits.</span></span>  
  
 <span data-ttu-id="07e3f-121">このオブジェクトのモニターロックを所有しているマネージスレッドが存在しない場合、 `ppThread` と `pAcquisitionCount` は変更されず、メソッドは S_FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="07e3f-121">If no managed thread owns the monitor lock on this object, `ppThread` and `pAcquisitionCount` are unchanged, and the method returns S_FALSE.</span></span>  
  
 <span data-ttu-id="07e3f-122">`ppThread`または `pAcquisitionCount` が有効なポインターでない場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="07e3f-122">If `ppThread` or `pAcquisitionCount` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="07e3f-123">このオブジェクトのモニターロックを所有しているスレッドが特定できない場合にエラーが発生すると、メソッドはエラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="07e3f-123">If an error occurs such that it cannot be determined which, if any, thread owns the monitor lock on this object, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e3f-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="07e3f-124">Requirements</span></span>  
 <span data-ttu-id="07e3f-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07e3f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e3f-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07e3f-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07e3f-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07e3f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07e3f-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e3f-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e3f-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="07e3f-129">See also</span></span>

- [<span data-ttu-id="07e3f-130">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="07e3f-130">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="07e3f-131">デバッグ</span><span class="sxs-lookup"><span data-stu-id="07e3f-131">Debugging</span></span>](index.md)
