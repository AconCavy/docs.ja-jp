---
title: ICorDebug::CanLaunchOrAttach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 354df02b27e87550ba602fe102352455c227441b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82859680"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="de277-102">ICorDebug::CanLaunchOrAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="de277-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="de277-103">現在のコンピューターおよびランタイム構成のコンテキスト内で、新しいプロセスを起動するか、指定した既存のプロセスにアタッチするかを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="de277-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de277-104">構文</span><span class="sxs-lookup"><span data-stu-id="de277-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de277-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de277-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="de277-106">から既存のプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="de277-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="de277-107">からWin32 デバッグ`true`を有効にして起動する場合、または win32 デバッグを有効にしてアタッチする場合は、を渡します。それ以外の`false`場合は、を渡します。</span><span class="sxs-lookup"><span data-stu-id="de277-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de277-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="de277-108">Return Value</span></span>  
 <span data-ttu-id="de277-109">現在のコンピューターと実行時の構成に関する情報を指定して、デバッグサービスによって新しいプロセスの起動または特定のプロセスへのアタッチが可能かどうかを判断する場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="de277-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="de277-110">使用できる HRESULT 値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="de277-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="de277-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="de277-111">S_OK</span></span>  
  
- <span data-ttu-id="de277-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="de277-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="de277-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="de277-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="de277-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="de277-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de277-115">解説</span><span class="sxs-lookup"><span data-stu-id="de277-115">Remarks</span></span>  
 <span data-ttu-id="de277-116">このメソッドは純粋な情報です。</span><span class="sxs-lookup"><span data-stu-id="de277-116">This method is purely informational.</span></span> <span data-ttu-id="de277-117">インターフェイスは、によって`CanLaunchOrAttach`返される値に関係なく、プロセスの起動やアタッチを停止することはありません。</span><span class="sxs-lookup"><span data-stu-id="de277-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="de277-118">Win32 デバッグが有効になっている状態で起動する場合、または Win32 `true`デバッグ`win32DebuggingEnabled`を有効にしてアタッチする場合は、にを渡します。</span><span class="sxs-lookup"><span data-stu-id="de277-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="de277-119">このオプションを使用`CanLaunchOrAttach`すると、によって返される HRESULT が異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="de277-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de277-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="de277-120">Requirements</span></span>  
 <span data-ttu-id="de277-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de277-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de277-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de277-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de277-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de277-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de277-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de277-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de277-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="de277-125">See also</span></span>

- [<span data-ttu-id="de277-126">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de277-126">ICorDebug Interface</span></span>](icordebug-interface.md)
