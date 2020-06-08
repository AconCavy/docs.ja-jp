---
title: ICorProfilerFunctionEnum::Skip メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
ms.openlocfilehash: 0f096f76ec47cfe3399e9184eb82bf20040efbbb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503043"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="8a726-102">ICorProfilerFunctionEnum::Skip メソッド</span><span class="sxs-lookup"><span data-stu-id="8a726-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="8a726-103">指定した数の要素がスキップされるように、この列挙子のカーソルを現在の位置から進めます。</span><span class="sxs-lookup"><span data-stu-id="8a726-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a726-104">構文</span><span class="sxs-lookup"><span data-stu-id="8a726-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a726-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8a726-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="8a726-106">からスキップする要素の数。</span><span class="sxs-lookup"><span data-stu-id="8a726-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a726-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="8a726-107">Return Value</span></span>  
 <span data-ttu-id="8a726-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="8a726-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8a726-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a726-109">HRESULT</span></span>|<span data-ttu-id="8a726-110">説明</span><span class="sxs-lookup"><span data-stu-id="8a726-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a726-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a726-111">S_OK</span></span>|<span data-ttu-id="8a726-112">`celt`要素はスキップされました。</span><span class="sxs-lookup"><span data-stu-id="8a726-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="8a726-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8a726-113">S_FALSE</span></span>|<span data-ttu-id="8a726-114">より小さい `celt` 要素がスキップされました。これは、要素がこれ以上存在しないことを示します。</span><span class="sxs-lookup"><span data-stu-id="8a726-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a726-115">解説</span><span class="sxs-lookup"><span data-stu-id="8a726-115">Remarks</span></span>  
 <span data-ttu-id="8a726-116">この列挙子のカーソルの新しい位置は、(現在位置) + `celt` です。</span><span class="sxs-lookup"><span data-stu-id="8a726-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a726-117">要件</span><span class="sxs-lookup"><span data-stu-id="8a726-117">Requirements</span></span>  
 <span data-ttu-id="8a726-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a726-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a726-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8a726-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a726-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a726-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a726-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a726-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a726-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a726-122">See also</span></span>

- [<span data-ttu-id="8a726-123">ICorProfilerFunctionEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a726-123">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="8a726-124">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8a726-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
