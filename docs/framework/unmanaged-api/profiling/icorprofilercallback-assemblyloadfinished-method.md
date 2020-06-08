---
title: ICorProfilerCallback::AssemblyLoadFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500443"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="6adbf-102">ICorProfilerCallback::AssemblyLoadFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="6adbf-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="6adbf-103">アセンブリの読み込みが完了したことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="6adbf-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6adbf-104">構文</span><span class="sxs-lookup"><span data-stu-id="6adbf-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6adbf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6adbf-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="6adbf-106">\[in] は、読み込まれたアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="6adbf-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="6adbf-107">\[in] アセンブリの読み込みが正常に完了したかどうかを示す HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6adbf-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="6adbf-108">解説</span><span class="sxs-lookup"><span data-stu-id="6adbf-108">Remarks</span></span>  
 <span data-ttu-id="6adbf-109">の値 `assemblyId` は、 `AssemblyLoadFinished` メソッドが呼び出されるまで、情報要求に対して有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="6adbf-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="6adbf-110">アセンブリの読み込みの一部は、コールバック後も続行される場合があり `AssemblyLoadFinished` ます。</span><span class="sxs-lookup"><span data-stu-id="6adbf-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="6adbf-111">のエラー HRESULT は `hrStatus` エラーを示します。</span><span class="sxs-lookup"><span data-stu-id="6adbf-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6adbf-112">ただし、の成功 HRESULT は、 `hrStatus` アセンブリの読み込みの最初の部分が成功したことを示します。</span><span class="sxs-lookup"><span data-stu-id="6adbf-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6adbf-113">要件</span><span class="sxs-lookup"><span data-stu-id="6adbf-113">Requirements</span></span>  
 <span data-ttu-id="6adbf-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6adbf-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6adbf-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6adbf-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6adbf-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6adbf-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6adbf-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6adbf-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6adbf-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="6adbf-118">See also</span></span>

- [<span data-ttu-id="6adbf-119">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6adbf-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
