---
title: ICorProfilerCallback::RemotingClientInvocationFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RemotingClientInvocationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RemotingClientInvocationFinished
helpviewer_keywords:
- RemotingClientInvocationFinished method [.NET Framework profiling]
- ICorProfilerCallback::RemotingClientInvocationFinished method [.NET Framework profiling]
ms.assetid: ea4b283b-1210-4f41-a7a2-c398b1adde4e
topic_type:
- apiref
ms.openlocfilehash: c9a750b941b29047206c98410d4b4673d1101a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445839"
---
# <a name="icorprofilercallbackremotingclientinvocationfinished-method"></a><span data-ttu-id="9b45d-102">ICorProfilerCallback::RemotingClientInvocationFinished メソッド</span><span class="sxs-lookup"><span data-stu-id="9b45d-102">ICorProfilerCallback::RemotingClientInvocationFinished Method</span></span>
<span data-ttu-id="9b45d-103">リモート処理呼び出しがクライアントで完了まで実行されたことをプロファイラーに通知します。</span><span class="sxs-lookup"><span data-stu-id="9b45d-103">Notifies the profiler that a remoting call has run to completion on the client.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b45d-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b45d-104">Syntax</span></span>  
  
```cpp  
HRESULT RemotingClientInvocationFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9b45d-105">コメント</span><span class="sxs-lookup"><span data-stu-id="9b45d-105">Remarks</span></span>  
 <span data-ttu-id="9b45d-106">リモート処理の呼び出しが同期されている場合は、サーバー上でも完了まで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9b45d-106">If the remoting call was synchronous, it has also run to completion on the server.</span></span> <span data-ttu-id="9b45d-107">リモート処理呼び出しが非同期の場合は、呼び出しが処理されるときに応答が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="9b45d-107">If the remoting call was asynchronous, a reply might still be expected when the call is handled.</span></span> <span data-ttu-id="9b45d-108">応答が予想される場合は、 [ICorProfilerCallback:: RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)への呼び出しとして、および非同期呼び出しの必要なセカンダリ処理を示すために `RemotingClientInvocationFinished` への追加の呼び出しとして発生します。</span><span class="sxs-lookup"><span data-stu-id="9b45d-108">If a reply is expected, it will occur as a call to [ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and an additional call to `RemotingClientInvocationFinished` to indicate the required secondary processing of an asynchronous call.</span></span>  
  
 <span data-ttu-id="9b45d-109">次のコールバックの各ペアは、同じスレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9b45d-109">Each of the following pairs of callbacks will occur on the same thread:</span></span>  
  
- <span data-ttu-id="9b45d-110">`RemotingClientInvocationStarted` と[ICorProfilerCallback:: RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span><span class="sxs-lookup"><span data-stu-id="9b45d-110">`RemotingClientInvocationStarted` and [ICorProfilerCallback::RemotingClientSendingMessage](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)</span></span>  
  
- <span data-ttu-id="9b45d-111">[ICorProfilerCallback:: RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)と[ICorProfilerCallback:: RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span><span class="sxs-lookup"><span data-stu-id="9b45d-111">[ICorProfilerCallback::RemotingClientReceivingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md) and [ICorProfilerCallback::RemotingClientInvocationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)</span></span>  
  
- <span data-ttu-id="9b45d-112">[ICorProfilerCallback:: RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)と[ICorProfilerCallback:: RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span><span class="sxs-lookup"><span data-stu-id="9b45d-112">[ICorProfilerCallback::RemotingServerInvocationReturned](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md) and [ICorProfilerCallback::RemotingServerSendingReply](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)</span></span>  
  
 <span data-ttu-id="9b45d-113">リモート処理のコールバックでは、次の問題に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9b45d-113">You should be aware of the following issues with the remoting callbacks:</span></span>  
  
- <span data-ttu-id="9b45d-114">リモート処理関数の実行はプロファイラー API によっては反映されないため、クライアントから呼び出され、サーバーで実行される関数の通知は正しく受信されません。</span><span class="sxs-lookup"><span data-stu-id="9b45d-114">Execution of a remoting function is not reflected by the profiler API, so notifications for functions that are called from the client and executed on the server are not properly received.</span></span> <span data-ttu-id="9b45d-115">実際の呼び出しは、プロキシオブジェクトを介して行われます。プロファイラーには、特定の関数が JIT コンパイルされていても使用されていないように見えます。</span><span class="sxs-lookup"><span data-stu-id="9b45d-115">The actual invocation happens via a proxy object; to the profiler, it appears that certain functions are JIT-compiled but never used.</span></span>  
  
- <span data-ttu-id="9b45d-116">プロファイラーは、非同期のリモート処理イベントに対して正確な通知を受信しません。</span><span class="sxs-lookup"><span data-stu-id="9b45d-116">The profiler does not receive accurate notifications for asynchronous remoting events.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b45d-117">要件</span><span class="sxs-lookup"><span data-stu-id="9b45d-117">Requirements</span></span>  
 <span data-ttu-id="9b45d-118">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b45d-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b45d-119">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9b45d-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9b45d-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b45d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b45d-121">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b45d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b45d-122">参照</span><span class="sxs-lookup"><span data-stu-id="9b45d-122">See also</span></span>

- [<span data-ttu-id="9b45d-123">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9b45d-123">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
