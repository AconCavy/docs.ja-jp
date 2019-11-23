---
title: ICorProfilerModuleEnum::GetCount メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::GetCount
helpviewer_keywords:
- ICorProfilerModuleEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: f0a4a5e0-4689-474b-b0f4-37ca0639c918
topic_type:
- apiref
ms.openlocfilehash: 9aaf1a282435e3f52b2c2d8f3d17254b877e61cc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442774"
---
# <a name="icorprofilermoduleenumgetcount-method"></a><span data-ttu-id="5bdc2-102">ICorProfilerModuleEnum::GetCount メソッド</span><span class="sxs-lookup"><span data-stu-id="5bdc2-102">ICorProfilerModuleEnum::GetCount Method</span></span>
<span data-ttu-id="5bdc2-103">アプリケーションによって読み込まれたマネージド モジュールの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="5bdc2-103">Gets the number of managed modules that were loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bdc2-104">構文</span><span class="sxs-lookup"><span data-stu-id="5bdc2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bdc2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5bdc2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5bdc2-106">[out] The number of runtime modules in the collection.</span><span class="sxs-lookup"><span data-stu-id="5bdc2-106">[out] The number of runtime modules in the collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bdc2-107">［要件］</span><span class="sxs-lookup"><span data-stu-id="5bdc2-107">Requirements</span></span>  
 <span data-ttu-id="5bdc2-108">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5bdc2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bdc2-109">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5bdc2-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5bdc2-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bdc2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bdc2-111">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bdc2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bdc2-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="5bdc2-112">See also</span></span>

- [<span data-ttu-id="5bdc2-113">ICorProfilerModuleEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bdc2-113">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="5bdc2-114">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5bdc2-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
