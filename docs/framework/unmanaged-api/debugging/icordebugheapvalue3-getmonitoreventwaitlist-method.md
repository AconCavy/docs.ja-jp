---
title: ICorDebugHeapValue3::GetMonitorEventWaitList メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
ms.openlocfilehash: 923e9b0821788143fff59eafe10d1802583df7a6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210424"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a><span data-ttu-id="abdd5-102">ICorDebugHeapValue3::GetMonitorEventWaitList メソッド</span><span class="sxs-lookup"><span data-stu-id="abdd5-102">ICorDebugHeapValue3::GetMonitorEventWaitList Method</span></span>
<span data-ttu-id="abdd5-103">モニターロックに関連付けられているイベントでキューに登録されているスレッドの順序付きリストを提供します。</span><span class="sxs-lookup"><span data-stu-id="abdd5-103">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abdd5-104">構文</span><span class="sxs-lookup"><span data-stu-id="abdd5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abdd5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="abdd5-105">Parameters</span></span>  
 `ppThreadEnum`  
 <span data-ttu-id="abdd5-106">入出力順序付けされたスレッドのリストを提供する、の型の定数列挙子。</span><span class="sxs-lookup"><span data-stu-id="abdd5-106">[out] The ICorDebugThreadEnum enumerator that provides the ordered list of threads.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="abdd5-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="abdd5-107">Return Value</span></span>  
 <span data-ttu-id="abdd5-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="abdd5-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="abdd5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="abdd5-109">HRESULT</span></span>|<span data-ttu-id="abdd5-110">説明</span><span class="sxs-lookup"><span data-stu-id="abdd5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="abdd5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="abdd5-111">S_OK</span></span>|<span data-ttu-id="abdd5-112">The list is not empty.</span><span class="sxs-lookup"><span data-stu-id="abdd5-112">The list is not empty.</span></span>|  
|<span data-ttu-id="abdd5-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="abdd5-113">S_FALSE</span></span>|<span data-ttu-id="abdd5-114">リストが空です。</span><span class="sxs-lookup"><span data-stu-id="abdd5-114">The list is empty.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="abdd5-115">例外</span><span class="sxs-lookup"><span data-stu-id="abdd5-115">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abdd5-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="abdd5-116">Remarks</span></span>  
 <span data-ttu-id="abdd5-117">リスト内の最初のスレッドは、の次の呼び出しによって解放される最初のスレッドです <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="abdd5-117">The first thread in the list is the first thread that is released by the next call to <xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>.</span></span> <span data-ttu-id="abdd5-118">リスト内の次のスレッドは、次の呼び出しで解放されます。</span><span class="sxs-lookup"><span data-stu-id="abdd5-118">The next thread in the list is released on the following call, and so on.</span></span>  
  
 <span data-ttu-id="abdd5-119">リストが空でない場合、このメソッドは S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="abdd5-119">If the list is not empty, this method returns S_OK.</span></span> <span data-ttu-id="abdd5-120">リストが空の場合、メソッドは S_FALSE を返します。この場合、列挙体は空ですが、有効です。</span><span class="sxs-lookup"><span data-stu-id="abdd5-120">If the list is empty, the method returns S_FALSE; in this case, the enumeration is still valid, although it is empty.</span></span>  
  
 <span data-ttu-id="abdd5-121">どちらの場合も、列挙インターフェイスは、現在の同期された状態の間のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="abdd5-121">In either case, the enumeration interface is usable only for the duration of the current synchronized state.</span></span> <span data-ttu-id="abdd5-122">ただし、スレッドのインターフェイスディスペンサーは、スレッドが終了するまで有効です。</span><span class="sxs-lookup"><span data-stu-id="abdd5-122">However, the thread's interfaces dispensed from it are valid until the thread exits.</span></span>  
  
 <span data-ttu-id="abdd5-123">`ppThreadEnum`が有効なポインターでない場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="abdd5-123">If `ppThreadEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="abdd5-124">どのスレッドがモニターを待機しているかを特定できないようなエラーが発生した場合、メソッドはエラーを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="abdd5-124">If an error occurs such that it cannot be determined which, if any, threads are waiting for the monitor, the method returns an HRESULT that indicates failure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abdd5-125">必要条件</span><span class="sxs-lookup"><span data-stu-id="abdd5-125">Requirements</span></span>  
 <span data-ttu-id="abdd5-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="abdd5-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abdd5-127">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abdd5-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abdd5-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abdd5-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abdd5-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abdd5-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abdd5-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="abdd5-130">See also</span></span>

- [<span data-ttu-id="abdd5-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="abdd5-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="abdd5-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="abdd5-132">Debugging</span></span>](index.md)
