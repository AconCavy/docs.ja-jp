---
title: COR_PRF_EX_CLAUSE_INFO 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: 5c764031f709eefe61022d0662f37bc5d3f3e281
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501002"
---
# <a name="cor_prf_ex_clause_info-structure"></a><span data-ttu-id="636bc-102">COR_PRF_EX_CLAUSE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="636bc-102">COR_PRF_EX_CLAUSE_INFO Structure</span></span>
<span data-ttu-id="636bc-103">特定の例外句インスタンスおよび関連するフレームに関する情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="636bc-103">Stores information about a specific exception clause instance and its associated frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="636bc-104">構文</span><span class="sxs-lookup"><span data-stu-id="636bc-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="636bc-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="636bc-105">Members</span></span>  
  
|<span data-ttu-id="636bc-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="636bc-106">Member</span></span>|<span data-ttu-id="636bc-107">説明</span><span class="sxs-lookup"><span data-stu-id="636bc-107">Description</span></span>|  
|------------|-----------------|  
|`clauseType`|<span data-ttu-id="636bc-108">入力または左にあるコードの例外句の種類を指定する[COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md)列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="636bc-108">A value of the [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) enumeration that specifies the type of exception clause the code just entered or left.</span></span>|  
|`programCounter`|<span data-ttu-id="636bc-109">句ハンドラーのネイティブエントリポイント (たとえば、X86 EIP レジスタの内容)。</span><span class="sxs-lookup"><span data-stu-id="636bc-109">The native entry point of the clause handler — for example, the contents of the X86 EIP register.</span></span>|  
|`framePointer`|<span data-ttu-id="636bc-110">句ハンドラーの論理フレームへのポインター。たとえば、X86 EBP レジスタの内容。</span><span class="sxs-lookup"><span data-stu-id="636bc-110">The pointer to the logical frame for the clause handler — for example, the contents of the X86 EBP register.</span></span>|  
|`shadowStackPointer`|<span data-ttu-id="636bc-111">シャドウスタックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="636bc-111">The pointer to the shadow stack.</span></span> <span data-ttu-id="636bc-112">この値は、BSP レジスタの内容であり、IA64 にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="636bc-112">This value is the contents of the BSP register and applies only to IA64.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="636bc-113">解説</span><span class="sxs-lookup"><span data-stu-id="636bc-113">Remarks</span></span>  
 <span data-ttu-id="636bc-114">例外通知が受信されると、 [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)を使用して、実行しようとし `catch` / `finally` ているまたは実行されたばかりの例外句 (フィルター) のネイティブアドレスとフレーム情報を取得できます。</span><span class="sxs-lookup"><span data-stu-id="636bc-114">When an exception notification is received, [ICorProfilerInfo2::GetNotifiedExceptionClauseInfo](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) can be used to get the native address and frame information for the exception clause (`catch`/`finally`/filter) that is about to be run or has just been run.</span></span>  
  
 <span data-ttu-id="636bc-115">Exception 句の実行には、共通言語ランタイム (CLR) からのこれらのコールバックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="636bc-115">Execution of an exception clause involves these callbacks from the common language runtime (CLR):</span></span>  
  
- [<span data-ttu-id="636bc-116">ICorProfilerCallback:: ExceptionCatcherEnter</span><span class="sxs-lookup"><span data-stu-id="636bc-116">ICorProfilerCallback::ExceptionCatcherEnter</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [<span data-ttu-id="636bc-117">ICorProfilerCallback:: ExceptionUnwindFinallyEnter</span><span class="sxs-lookup"><span data-stu-id="636bc-117">ICorProfilerCallback::ExceptionUnwindFinallyEnter</span></span>](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [<span data-ttu-id="636bc-118">ICorProfilerCallback:: ExceptionSearchFilterEnter</span><span class="sxs-lookup"><span data-stu-id="636bc-118">ICorProfilerCallback::ExceptionSearchFilterEnter</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [<span data-ttu-id="636bc-119">ICorProfilerCallback:: ExceptionCatcherLeave</span><span class="sxs-lookup"><span data-stu-id="636bc-119">ICorProfilerCallback::ExceptionCatcherLeave</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [<span data-ttu-id="636bc-120">ICorProfilerCallback:: ExceptionUnwindFinallyLeave</span><span class="sxs-lookup"><span data-stu-id="636bc-120">ICorProfilerCallback::ExceptionUnwindFinallyLeave</span></span>](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [<span data-ttu-id="636bc-121">ICorProfilerCallback:: ExceptionSearchFilterLeave</span><span class="sxs-lookup"><span data-stu-id="636bc-121">ICorProfilerCallback::ExceptionSearchFilterLeave</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a><span data-ttu-id="636bc-122">要件</span><span class="sxs-lookup"><span data-stu-id="636bc-122">Requirements</span></span>  
 <span data-ttu-id="636bc-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="636bc-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="636bc-124">**ヘッダー:** Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="636bc-124">**Header:** CorProf.idl</span></span>  
  
 <span data-ttu-id="636bc-125">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="636bc-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="636bc-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="636bc-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="636bc-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="636bc-127">See also</span></span>

- [<span data-ttu-id="636bc-128">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="636bc-128">Profiling Structures</span></span>](profiling-structures.md)
