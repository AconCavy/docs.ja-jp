---
title: ICorProfilerInfo3::GetAppDomainsContainingModule メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
ms.openlocfilehash: 8615deb2e42b039120d97b3eb5af23beb31b0808
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502848"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="df47c-102">ICorProfilerInfo3::GetAppDomainsContainingModule メソッド</span><span class="sxs-lookup"><span data-stu-id="df47c-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="df47c-103">指定したモジュールが読み込まれているアプリケーション ドメインの識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="df47c-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df47c-104">構文</span><span class="sxs-lookup"><span data-stu-id="df47c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df47c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="df47c-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="df47c-106">[in] 読み込まれたモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="df47c-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="df47c-107">[in] `appDomainIds` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="df47c-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="df47c-108">[out] 返される要素の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="df47c-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="df47c-109">[out] アプリケーション ドメイン ID 値の配列。</span><span class="sxs-lookup"><span data-stu-id="df47c-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df47c-110">解説</span><span class="sxs-lookup"><span data-stu-id="df47c-110">Remarks</span></span>  
 <span data-ttu-id="df47c-111">このメソッドは、呼び出し元が割り当てたバッファーを使用します。</span><span class="sxs-lookup"><span data-stu-id="df47c-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df47c-112">要件</span><span class="sxs-lookup"><span data-stu-id="df47c-112">Requirements</span></span>  
 <span data-ttu-id="df47c-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="df47c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df47c-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df47c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df47c-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df47c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df47c-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df47c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df47c-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="df47c-117">See also</span></span>

- [<span data-ttu-id="df47c-118">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df47c-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="df47c-119">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="df47c-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="df47c-120">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="df47c-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="df47c-121">プロファイル</span><span class="sxs-lookup"><span data-stu-id="df47c-121">Profiling</span></span>](index.md)
