---
title: ICorDebugAppDomain4::GetObjectForCCW メソッド
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: a175a6b6c91c284348580e1d9dc9ef0c5f5fc5df
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895117"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="b9d1b-102">ICorDebugAppDomain4::GetObjectForCCW メソッド</span><span class="sxs-lookup"><span data-stu-id="b9d1b-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="b9d1b-103">COM 呼び出し可能ラッパー (CCW: COM Callable Wrapper) ポインターからマネージド オブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9d1b-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9d1b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9d1b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9d1b-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="b9d1b-106">[in] COM 呼び出し可能ラッパー (CCW) ポインター。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="b9d1b-107">入出力指定された CCW ポインターに対応するマネージオブジェクトを表す "ICorDebugValue" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9d1b-108">解説</span><span class="sxs-lookup"><span data-stu-id="b9d1b-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9d1b-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="b9d1b-109">Requirements</span></span>  
 <span data-ttu-id="b9d1b-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9d1b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9d1b-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9d1b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9d1b-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9d1b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9d1b-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9d1b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9d1b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9d1b-114">See also</span></span>

- [<span data-ttu-id="b9d1b-115">ICorDebugAppDomain4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9d1b-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="b9d1b-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9d1b-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
