---
title: ICorProfilerFunctionEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: a212a0499b1091f1c77b52951ecef2cb2cace4df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447836"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="a3056-102">ICorProfilerFunctionEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="a3056-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="a3056-103">この[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a3056-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3056-104">構文</span><span class="sxs-lookup"><span data-stu-id="a3056-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a3056-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a3056-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="a3056-106">入出力インターフェイスポインターへのポインター。これにより、この[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)インターフェイスのコピーが参照されます。</span><span class="sxs-lookup"><span data-stu-id="a3056-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="a3056-107">列挙子のコピーは、この列挙子とは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="a3056-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="a3056-108">ただし、コピーの初期カーソル位置は、この列挙子の現在のカーソル位置と同じです。</span><span class="sxs-lookup"><span data-stu-id="a3056-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3056-109">要件</span><span class="sxs-lookup"><span data-stu-id="a3056-109">Requirements</span></span>  
 <span data-ttu-id="a3056-110">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a3056-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3056-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a3056-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3056-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3056-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3056-113">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3056-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3056-114">参照</span><span class="sxs-lookup"><span data-stu-id="a3056-114">See also</span></span>

- [<span data-ttu-id="a3056-115">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3056-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="a3056-116">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a3056-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
