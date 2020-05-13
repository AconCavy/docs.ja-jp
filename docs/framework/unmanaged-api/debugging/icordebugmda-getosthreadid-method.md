---
title: ICorDebugMDA::GetOSThreadId メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: c7ab77e9316023a97d2eafe8bcccc2b45e240cd0
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207817"
---
# <a name="icordebugmdagetosthreadid-method"></a><span data-ttu-id="04197-102">ICorDebugMDA::GetOSThreadId メソッド</span><span class="sxs-lookup"><span data-stu-id="04197-102">ICorDebugMDA::GetOSThreadId Method</span></span>
<span data-ttu-id="04197-103">によって表されるマネージデバッグアシスタント (MDA) が実行さ[れている](icordebugmda-interface.md)オペレーティングシステム (os) スレッド識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="04197-103">Gets the operating system (OS) thread identifier upon which the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md) is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04197-104">構文</span><span class="sxs-lookup"><span data-stu-id="04197-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04197-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="04197-105">Parameters</span></span>  
 `pOsTid`  
 <span data-ttu-id="04197-106">入出力OS スレッド識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="04197-106">[out] A pointer to the OS thread identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04197-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="04197-107">Remarks</span></span>  
 <span data-ttu-id="04197-108">システムスレッドを使用すると、ネイティブスレッドで、またはまだマネージコードを入力していないマネージスレッド上で MDA が発生する状況に対応できます。</span><span class="sxs-lookup"><span data-stu-id="04197-108">The OS thread is used instead of an ICorDebugThread to allow for situations in which an MDA is fired either on a native thread or on a managed thread that has not yet entered managed code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04197-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="04197-109">Requirements</span></span>  
 <span data-ttu-id="04197-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="04197-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04197-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04197-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04197-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04197-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04197-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04197-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04197-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="04197-114">See also</span></span>

- [<span data-ttu-id="04197-115">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="04197-115">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="04197-116">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="04197-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
