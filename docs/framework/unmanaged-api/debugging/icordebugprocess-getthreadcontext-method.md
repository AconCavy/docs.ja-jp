---
title: ICorDebugProcess::GetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
ms.openlocfilehash: 2bdbf373144e2fb49074cfd035e7b0ffe3c8c291
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212890"
---
# <a name="icordebugprocessgetthreadcontext-method"></a><span data-ttu-id="2fb61-102">ICorDebugProcess::GetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="2fb61-102">ICorDebugProcess::GetThreadContext Method</span></span>
<span data-ttu-id="2fb61-103">このプロセス内の指定されたスレッドのコンテキストを取得します。</span><span class="sxs-lookup"><span data-stu-id="2fb61-103">Gets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fb61-104">構文</span><span class="sxs-lookup"><span data-stu-id="2fb61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fb61-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2fb61-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="2fb61-106">からコンテキストを取得するスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="2fb61-106">[in] The ID of the thread for which to retrieve the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="2fb61-107">[in] `context` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="2fb61-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="2fb61-108">[入力、出力]スレッドのコンテキストを記述するバイト配列。</span><span class="sxs-lookup"><span data-stu-id="2fb61-108">[in, out] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="2fb61-109">コンテキストは、スレッドが実行されているプロセッサのアーキテクチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="2fb61-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fb61-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="2fb61-110">Remarks</span></span>  
 <span data-ttu-id="2fb61-111">デバッガーは、Win32 メソッドではなく、このメソッドを呼び出す必要があります。これは、 `GetThreadContext` スレッドが実際には "ハイジャック" 状態にあり、そのコンテキストが一時的に変更されている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="2fb61-111">The debugger should call this method rather than the Win32 `GetThreadContext` method, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="2fb61-112">このメソッドは、スレッドがネイティブコード内にある場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="2fb61-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="2fb61-113">マネージコード内のスレッドには、コード[を使用し](icordebugregisterset-interface.md)ます。</span><span class="sxs-lookup"><span data-stu-id="2fb61-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span>  
  
 <span data-ttu-id="2fb61-114">返されるデータは、現在のプラットフォームのコンテキスト構造です。</span><span class="sxs-lookup"><span data-stu-id="2fb61-114">The data returned is a context structure for the current platform.</span></span> <span data-ttu-id="2fb61-115">Win32 メソッドの場合と同様に、 `GetThreadContext` 呼び出し元は、 `context` このメソッドを呼び出す前にパラメーターを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2fb61-115">Just as with the Win32 `GetThreadContext` method, the caller should initialize the `context` parameter before calling this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fb61-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="2fb61-116">Requirements</span></span>  
 <span data-ttu-id="2fb61-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fb61-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fb61-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fb61-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fb61-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fb61-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fb61-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fb61-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
