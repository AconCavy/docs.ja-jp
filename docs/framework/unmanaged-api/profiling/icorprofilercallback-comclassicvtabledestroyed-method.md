---
title: ICorProfilerCallback::COMClassicVTableDestroyed メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
ms.openlocfilehash: 98d5dcf3b691f16f63390851e207f518bf26ab11
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866521"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="23f81-102">ICorProfilerCallback::COMClassicVTableDestroyed メソッド</span><span class="sxs-lookup"><span data-stu-id="23f81-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="23f81-103">COM 相互運用機能の vtable が破棄されていることをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="23f81-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23f81-104">このコールバックは、vtable の破棄がシャットダウンに非常に近いために発生することはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="23f81-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23f81-105">構文</span><span class="sxs-lookup"><span data-stu-id="23f81-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23f81-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="23f81-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="23f81-107">\[] この vtable が作成されたクラスの ID。</span><span class="sxs-lookup"><span data-stu-id="23f81-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="23f81-108">\[] クラスによって実装されるインターフェイスの ID。</span><span class="sxs-lookup"><span data-stu-id="23f81-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="23f81-109">この値は、インターフェイスが内部でのみ使用されている場合は NULL になります。</span><span class="sxs-lookup"><span data-stu-id="23f81-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="23f81-110">\[] には、vtable の先頭へのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="23f81-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="23f81-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="23f81-111">Remarks</span></span>  
 <span data-ttu-id="23f81-112">プロファイラーは、このメソッドの実装でブロックしないでください。スタックがガベージコレクションを許可する状態にならないため、プリエンプティブガベージコレクションを有効にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="23f81-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="23f81-113">プロファイラーがここでブロックし、ガベージコレクションを実行しようとすると、このコールバックが戻るまでランタイムはブロックします。</span><span class="sxs-lookup"><span data-stu-id="23f81-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="23f81-114">プロファイラーによるこのメソッドの実装では、マネージコードを呼び出さないようにするか、マネージメモリ割り当てを発生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="23f81-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23f81-115">要件</span><span class="sxs-lookup"><span data-stu-id="23f81-115">Requirements</span></span>  
 <span data-ttu-id="23f81-116">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="23f81-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23f81-117">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="23f81-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="23f81-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="23f81-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23f81-119">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23f81-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23f81-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="23f81-120">See also</span></span>

- [<span data-ttu-id="23f81-121">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="23f81-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="23f81-122">COMClassicVTableCreated メソッド</span><span class="sxs-lookup"><span data-stu-id="23f81-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
