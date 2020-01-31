---
title: ICorDebugProcess インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess
helpviewer_keywords:
- ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: be86f4b5-418a-4c5c-a67c-97148c65ed8c
topic_type:
- apiref
ms.openlocfilehash: b2429052173a187297b67c756213e5d27a79298b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792601"
---
# <a name="icordebugprocess-interface"></a><span data-ttu-id="e5ab3-102">ICorDebugProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e5ab3-102">ICorDebugProcess Interface</span></span>
<span data-ttu-id="e5ab3-103">マネージド コードを実行しているプロセスを表します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-103">Represents a process that is executing managed code.</span></span> <span data-ttu-id="e5ab3-104">このインターフェイスは、というコントロールのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-104">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5ab3-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-105">Methods</span></span>  
  
|<span data-ttu-id="e5ab3-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-106">Method</span></span>|<span data-ttu-id="e5ab3-107">説明</span><span class="sxs-lookup"><span data-stu-id="e5ab3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5ab3-108">ClearCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-108">ClearCurrentException Method</span></span>](icordebugprocess-clearcurrentexception-method.md)|<span data-ttu-id="e5ab3-109">指定されたスレッドで現在のアンマネージ例外をクリアします。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-109">Clears the current unmanaged exception on the given thread.</span></span>|  
|[<span data-ttu-id="e5ab3-110">EnableLogMessages メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-110">EnableLogMessages Method</span></span>](icordebugprocess-enablelogmessages-method.md)|<span data-ttu-id="e5ab3-111">デバッガーへのログメッセージの送信を有効または無効にします。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-111">Enables and disables the sending of log messages to the debugger.</span></span>|  
|[<span data-ttu-id="e5ab3-112">EnumerateAppDomains メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-112">EnumerateAppDomains Method</span></span>](icordebugprocess-enumerateappdomains-method.md)|<span data-ttu-id="e5ab3-113">プロセス内のすべてのアプリケーションドメインを列挙します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-113">Enumerates all of the application domains in the process.</span></span>|  
|[<span data-ttu-id="e5ab3-114">EnumerateObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-114">EnumerateObjects Method</span></span>](icordebugprocess-enumerateobjects-method.md)|<span data-ttu-id="e5ab3-115">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-115">Not implemented.</span></span>|  
|[<span data-ttu-id="e5ab3-116">GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-116">GetHandle Method</span></span>](icordebugprocess-gethandle-method.md)|<span data-ttu-id="e5ab3-117">プロセスを処理するハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-117">Gets a handle to the process.</span></span>|  
|[<span data-ttu-id="e5ab3-118">GetHelperThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-118">GetHelperThreadID Method</span></span>](icordebugprocess-gethelperthreadid-method.md)|<span data-ttu-id="e5ab3-119">デバッガーの内部ヘルパースレッドのオペレーティングシステム (OS) スレッド ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-119">Gets the operating system (OS) thread ID for the debugger's internal helper thread.</span></span>|  
|[<span data-ttu-id="e5ab3-120">GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-120">GetID Method</span></span>](icordebugprocess-getid-method.md)|<span data-ttu-id="e5ab3-121">プロセスのオペレーティングシステム (OS) ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-121">Gets the operating system (OS) ID of the process.</span></span>|  
|[<span data-ttu-id="e5ab3-122">GetObject メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-122">GetObject Method</span></span>](icordebugprocess-getobject-method.md)|<span data-ttu-id="e5ab3-123">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-123">Not implemented.</span></span>|  
|[<span data-ttu-id="e5ab3-124">GetThread メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-124">GetThread Method</span></span>](icordebugprocess-getthread-method.md)|<span data-ttu-id="e5ab3-125">指定された OS スレッド ID を持つコードスレッドインスタンスを取得します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-125">Gets the ICorDebugThread instance that has the specified OS thread ID.</span></span>|  
|[<span data-ttu-id="e5ab3-126">GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-126">GetThreadContext Method</span></span>](icordebugprocess-getthreadcontext-method.md)|<span data-ttu-id="e5ab3-127">指定されたスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-127">Gets the context for the given thread.</span></span>|  
|[<span data-ttu-id="e5ab3-128">IsOSSuspended メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-128">IsOSSuspended Method</span></span>](icordebugprocess-isossuspended-method.md)|<span data-ttu-id="e5ab3-129">デバッガーがプロセスを停止した結果としてスレッドが中断されたかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-129">Determines whether the thread has been suspended as a result of the debugger stopping the process.</span></span>|  
|[<span data-ttu-id="e5ab3-130">IsTransitionStub メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-130">IsTransitionStub Method</span></span>](icordebugprocess-istransitionstub-method.md)|<span data-ttu-id="e5ab3-131">マネージコードへの遷移を発生させるスタブ内にアドレスがあるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-131">Determines whether an address is inside a stub that will cause a transition to managed code.</span></span>|  
|[<span data-ttu-id="e5ab3-132">ModifyLogSwitch メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-132">ModifyLogSwitch Method</span></span>](icordebugprocess-modifylogswitch-method.md)|<span data-ttu-id="e5ab3-133">指定されたログスイッチの重大度レベルを設定します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-133">Sets the severity level of the specified log switch.</span></span>|  
|[<span data-ttu-id="e5ab3-134">ReadMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-134">ReadMemory Method</span></span>](icordebugprocess-readmemory-method.md)|<span data-ttu-id="e5ab3-135">プロセスからメモリを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-135">Reads memory from the process.</span></span>|  
|[<span data-ttu-id="e5ab3-136">SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-136">SetThreadContext Method</span></span>](icordebugprocess-setthreadcontext-method.md)|<span data-ttu-id="e5ab3-137">指定されたスレッドのコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-137">Sets the context for the given thread.</span></span>|  
|[<span data-ttu-id="e5ab3-138">ThreadForFiberCookie メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-138">ThreadForFiberCookie Method</span></span>](icordebugprocess-threadforfibercookie-method.md)|<span data-ttu-id="e5ab3-139">非推奨。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-139">Deprecated.</span></span>|  
|[<span data-ttu-id="e5ab3-140">WriteMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="e5ab3-140">WriteMemory Method</span></span>](icordebugprocess-writememory-method.md)|<span data-ttu-id="e5ab3-141">プロセスのメモリ領域にデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-141">Writes data to an area of memory in the process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5ab3-142">コメント</span><span class="sxs-lookup"><span data-stu-id="e5ab3-142">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e5ab3-143">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-143">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5ab3-144">要件</span><span class="sxs-lookup"><span data-stu-id="e5ab3-144">Requirements</span></span>  
 <span data-ttu-id="e5ab3-145">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e5ab3-145">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5ab3-146">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5ab3-146">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5ab3-147">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5ab3-147">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5ab3-148">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5ab3-148">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5ab3-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="e5ab3-149">See also</span></span>

- [<span data-ttu-id="e5ab3-150">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e5ab3-150">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="e5ab3-151">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e5ab3-151">Debugging Interfaces</span></span>](debugging-interfaces.md)
