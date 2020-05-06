---
title: CorDebugUserState 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d502b4098016fb14793bccd6feb641e92e3c2611
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795639"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="915d2-102">CorDebugUserState 列挙型</span><span class="sxs-lookup"><span data-stu-id="915d2-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="915d2-103">スレッドのユーザーの状態を示します。</span><span class="sxs-lookup"><span data-stu-id="915d2-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="915d2-104">構文</span><span class="sxs-lookup"><span data-stu-id="915d2-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="915d2-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="915d2-105">Members</span></span>  
  
|<span data-ttu-id="915d2-106">値</span><span class="sxs-lookup"><span data-stu-id="915d2-106">Value</span></span>|<span data-ttu-id="915d2-107">説明</span><span class="sxs-lookup"><span data-stu-id="915d2-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="915d2-108">スレッドの終了が要求されました。</span><span class="sxs-lookup"><span data-stu-id="915d2-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="915d2-109">スレッドの中断が要求されました。</span><span class="sxs-lookup"><span data-stu-id="915d2-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="915d2-110">スレッドがバックグラウンドで実行されています。</span><span class="sxs-lookup"><span data-stu-id="915d2-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="915d2-111">スレッドが実行を開始していません。</span><span class="sxs-lookup"><span data-stu-id="915d2-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="915d2-112">スレッドは終了されました。</span><span class="sxs-lookup"><span data-stu-id="915d2-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="915d2-113">スレッドは、別のスレッドがタスクを完了するのを待機しています。</span><span class="sxs-lookup"><span data-stu-id="915d2-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="915d2-114">スレッドは中断しています。</span><span class="sxs-lookup"><span data-stu-id="915d2-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="915d2-115">スレッドが安全でないポイントにあります。</span><span class="sxs-lookup"><span data-stu-id="915d2-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="915d2-116">つまり、スレッドは、ガベージコレクションをブロックする可能性がある実行中のポイントにあります。</span><span class="sxs-lookup"><span data-stu-id="915d2-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="915d2-117">デバッグイベントは安全でないポイントからディスパッチできますが、アンセーフポイントでスレッドを中断すると、スレッドが再開されるまでデッドロックが発生する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="915d2-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="915d2-118">セーフポイントと unsafe ポイントは、just-in-time (JIT) とガベージコレクションの実装によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="915d2-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="915d2-119">スレッドはスレッドプールからのものです。</span><span class="sxs-lookup"><span data-stu-id="915d2-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="915d2-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="915d2-120">Remarks</span></span>  
 <span data-ttu-id="915d2-121">スレッドのユーザー状態は、デバッガーがそのスレッドを調べたときのスレッドの状態です。</span><span class="sxs-lookup"><span data-stu-id="915d2-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="915d2-122">スレッドには、ユーザー状態を組み合わせて含めることができます。</span><span class="sxs-lookup"><span data-stu-id="915d2-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="915d2-123">スレッドのユーザー状態を取得するには、 [「いい thread:: GetUserState](icordebugthread-getuserstate-method.md)メソッド」を使用します。</span><span class="sxs-lookup"><span data-stu-id="915d2-123">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="915d2-124">必要条件</span><span class="sxs-lookup"><span data-stu-id="915d2-124">Requirements</span></span>  
 <span data-ttu-id="915d2-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="915d2-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="915d2-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="915d2-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="915d2-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="915d2-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="915d2-128">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="915d2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="915d2-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="915d2-129">See also</span></span>

- [<span data-ttu-id="915d2-130">列挙体のデバッグ</span><span class="sxs-lookup"><span data-stu-id="915d2-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
