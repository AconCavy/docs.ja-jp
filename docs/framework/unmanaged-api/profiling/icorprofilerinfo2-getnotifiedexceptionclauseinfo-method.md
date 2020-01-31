---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: a430631948230d16e5d04c869625b4c670faaf02
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868643"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="31546-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="31546-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="31546-103">実行される、または実行される直前の例外句 (`catch`/`finally`/`filter`) のネイティブアドレスとフレーム情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="31546-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31546-104">構文</span><span class="sxs-lookup"><span data-stu-id="31546-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31546-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="31546-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="31546-106">入出力現在の exception 句のインスタンスとそれに関連付けられているフレームを記述する[COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md)構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="31546-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31546-107">コメント</span><span class="sxs-lookup"><span data-stu-id="31546-107">Remarks</span></span>  
 <span data-ttu-id="31546-108">例外通知を受信すると、`GetNotifiedExceptionClauseInfo` を使用して、実行しようとしている例外句 (`catch`/`finally`/`filter`) のネイティブアドレスとフレーム情報を取得できます ([ICorProfilerCallback:: ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)、 [ICorProfilerCallback:: ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)、または[ICorProfilerCallback:: exceptionsearchfilterenter](icorprofilercallback-exceptionsearchfilterenter-method.md)コールバックは profiler によって受信されます)[。](icorprofilercallback-exceptioncatcherleave-method.md)、 [ICorProfilerCallback:: ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)、または[ICorProfilerCallback:: exceptionsearchfilterleave](icorprofilercallback-exceptionsearchfilterleave-method.md)コールバックがプロファイラーによって受信されます)。</span><span class="sxs-lookup"><span data-stu-id="31546-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="31546-109">この呼び出しは、一致する Leave コールバックが受信されるか、または現在の句で入れ子になった例外がスローされるまで、任意の時点でいつでも実行できます。その場合、その句には Leave 通知がありません。</span><span class="sxs-lookup"><span data-stu-id="31546-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="31546-110">スローされた例外が `filter` exception 句をエスケープすることはできないので、その場合は常に Leave 通知が存在することに注意してください。</span><span class="sxs-lookup"><span data-stu-id="31546-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31546-111">要件</span><span class="sxs-lookup"><span data-stu-id="31546-111">Requirements</span></span>  
 <span data-ttu-id="31546-112">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="31546-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31546-113">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31546-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31546-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31546-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31546-115">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31546-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31546-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="31546-116">See also</span></span>

- [<span data-ttu-id="31546-117">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31546-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="31546-118">ICorProfilerInfo2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="31546-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
