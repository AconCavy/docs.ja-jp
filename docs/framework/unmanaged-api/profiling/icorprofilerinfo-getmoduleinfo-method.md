---
title: ICorProfilerInfo::GetModuleInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleInfo
helpviewer_keywords:
- GetModuleInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleInfo method [.NET Framework profiling]
ms.assetid: 5a90d16f-7929-4987-8f83-a631becf564d
topic_type:
- apiref
ms.openlocfilehash: 25c5568e4cae0ead82b59b09dbbb9a11e4bc2df2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863440"
---
# <a name="icorprofilerinfogetmoduleinfo-method"></a><span data-ttu-id="7cecb-102">ICorProfilerInfo::GetModuleInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="7cecb-102">ICorProfilerInfo::GetModuleInfo Method</span></span>
<span data-ttu-id="7cecb-103">モジュール ID を指定して、モジュールのファイル名とモジュールの親アセンブリの ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="7cecb-103">Given a module ID, returns the file name of the module and the ID of the module's parent assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cecb-104">構文</span><span class="sxs-lookup"><span data-stu-id="7cecb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleInfo(  
    [in]  ModuleID   moduleId,  
    [out] LPCBYTE    *ppBaseLoadAddress,  
    [in]  ULONG      cchName,  
    [out] ULONG      *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
          WCHAR      szName[] ,  
    [out] AssemblyID *pAssemblyId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cecb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="7cecb-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="7cecb-106">[in] 情報が取得されるモジュールの ID。</span><span class="sxs-lookup"><span data-stu-id="7cecb-106">[in] The ID of the module for which information will be retrieved.</span></span>  
  
 `ppBaseLoadAddress`  
 <span data-ttu-id="7cecb-107">[out] モジュールが読み込まれるベース アドレス。</span><span class="sxs-lookup"><span data-stu-id="7cecb-107">[out] The base address at which the module is loaded.</span></span>  
  
 `cchName`  
 <span data-ttu-id="7cecb-108">[in] `szName` 戻りバッファーの長さ (文字単位)。</span><span class="sxs-lookup"><span data-stu-id="7cecb-108">[in] The length, in characters, of the `szName` return buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="7cecb-109">[out] 返されるモジュールのファイル名の文字列長の合計へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7cecb-109">[out] A pointer to the total character length of the module's file name that is returned.</span></span>  
  
 `szName`  
 <span data-ttu-id="7cecb-110">[out] 呼び出し元が提供したワイド文字バッファー。</span><span class="sxs-lookup"><span data-stu-id="7cecb-110">[out] A caller-provided wide character buffer.</span></span> <span data-ttu-id="7cecb-111">メソッドから制御が戻るとき、このバッファーにモジュールのファイル名が格納されます。</span><span class="sxs-lookup"><span data-stu-id="7cecb-111">When the method returns, this buffer contains the file name of the module.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="7cecb-112">[out] モジュールの親アセンブリ ID へのポインター。</span><span class="sxs-lookup"><span data-stu-id="7cecb-112">[out] A pointer to the ID of the module's parent assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cecb-113">コメント</span><span class="sxs-lookup"><span data-stu-id="7cecb-113">Remarks</span></span>  
 <span data-ttu-id="7cecb-114">動的モジュールの場合、`szName` パラメーターは空の文字列、ベース アドレスは 0 (ゼロ) になります。</span><span class="sxs-lookup"><span data-stu-id="7cecb-114">For dynamic modules, the `szName` parameter is an empty string, and the base address is 0 (zero).</span></span>  
  
 <span data-ttu-id="7cecb-115">`GetModuleInfo` メソッドは、モジュールの ID が存在するとすぐに呼び出される場合がありますが、プロファイラーが[ICorProfilerCallback:: ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md)コールバックを受け取るまで、親アセンブリの id は使用できません。</span><span class="sxs-lookup"><span data-stu-id="7cecb-115">Although the `GetModuleInfo` method may be called as soon as the module's ID exists, the ID of the parent assembly will not be available until the profiler receives the [ICorProfilerCallback::ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md) callback.</span></span>  
  
 <span data-ttu-id="7cecb-116">`GetModuleInfo` から制御が戻ったら、`szName` バッファーのサイズが十分で、モジュールのファイル名全体を格納できたかどうかを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7cecb-116">When `GetModuleInfo` returns, you must verify that the `szName` buffer was large enough to contain the full file name of the module.</span></span> <span data-ttu-id="7cecb-117">これを行うには、`pcchName` が指している値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="7cecb-117">To do this, compare the value that `pcchName` points to with the value of the `cchName` parameter.</span></span> <span data-ttu-id="7cecb-118">`pcchName` が指している値が `cchName` の値より大きい場合は、`szName` バッファーの割り当てを増やし、`cchName` を新しい大きいサイズに更新して、`GetModuleInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7cecb-118">If `pcchName` points to a value that is larger than `cchName`, allocate a larger `szName` buffer, update `cchName` with the new, larger size, and call `GetModuleInfo` again.</span></span>  
  
 <span data-ttu-id="7cecb-119">別の方法として、最初に `GetModuleInfo` を長さゼロの `szName` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="7cecb-119">Alternatively, you can first call `GetModuleInfo` with a zero-length `szName` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="7cecb-120">その後、バッファーのサイズを `pcchName` で返された値に設定し、`GetModuleInfo` を再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="7cecb-120">You can then set the buffer size to the value returned in `pcchName` and call `GetModuleInfo` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cecb-121">要件</span><span class="sxs-lookup"><span data-stu-id="7cecb-121">Requirements</span></span>  
 <span data-ttu-id="7cecb-122">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7cecb-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cecb-123">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7cecb-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cecb-124">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cecb-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cecb-125">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cecb-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cecb-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7cecb-126">See also</span></span>

- [<span data-ttu-id="7cecb-127">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cecb-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7cecb-128">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7cecb-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="7cecb-129">プロファイル</span><span class="sxs-lookup"><span data-stu-id="7cecb-129">Profiling</span></span>](index.md)
- [<span data-ttu-id="7cecb-130">GetModuleInfo2 メソッド</span><span class="sxs-lookup"><span data-stu-id="7cecb-130">GetModuleInfo2 Method</span></span>](icorprofilerinfo3-getmoduleinfo2-method.md)
