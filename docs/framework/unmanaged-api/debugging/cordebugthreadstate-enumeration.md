---
title: CorDebugThreadState 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 69a8aabd1d79bb9bb4248259c99124ce50677600
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789239"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="4f83d-102">CorDebugThreadState 列挙型</span><span class="sxs-lookup"><span data-stu-id="4f83d-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="4f83d-103">デバッグのスレッドの状態を指定します。</span><span class="sxs-lookup"><span data-stu-id="4f83d-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f83d-104">構文</span><span class="sxs-lookup"><span data-stu-id="4f83d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="4f83d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4f83d-105">Members</span></span>  
  
|<span data-ttu-id="4f83d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4f83d-106">Member</span></span>|<span data-ttu-id="4f83d-107">説明</span><span class="sxs-lookup"><span data-stu-id="4f83d-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="4f83d-108">デバッグイベントが発生しない限り、スレッドは自由に実行できます。</span><span class="sxs-lookup"><span data-stu-id="4f83d-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="4f83d-109">スレッドを実行できません。</span><span class="sxs-lookup"><span data-stu-id="4f83d-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f83d-110">コメント</span><span class="sxs-lookup"><span data-stu-id="4f83d-110">Remarks</span></span>  
 <span data-ttu-id="4f83d-111">デバッガーは、`CorDebugThreadState` 列挙体を使用して、スレッドの実行を制御します。</span><span class="sxs-lookup"><span data-stu-id="4f83d-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="4f83d-112">スレッドの状態を設定するには、次のように指定する必要があります: [: SetDebugState](icordebugthread-setdebugstate-method.md)または、モジュール[:: SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md)メソッド。</span><span class="sxs-lookup"><span data-stu-id="4f83d-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="4f83d-113">[ホスティング API](../../../../docs/framework/unmanaged-api/hosting/index.md)に提供されるコールバックによってメッセージポンプが可能になるため、中断された状態は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="4f83d-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f83d-114">要件</span><span class="sxs-lookup"><span data-stu-id="4f83d-114">Requirements</span></span>  
 <span data-ttu-id="4f83d-115">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f83d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f83d-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f83d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f83d-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f83d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f83d-118">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f83d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f83d-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f83d-119">See also</span></span>

- [<span data-ttu-id="4f83d-120">列挙型のデバッグ</span><span class="sxs-lookup"><span data-stu-id="4f83d-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
