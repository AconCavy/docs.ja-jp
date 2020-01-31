---
title: ICorDebugManagedCallback::UnloadClass メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
ms.openlocfilehash: f2f19987d22502acbe06bd5e5c14b0d6c17cbe24
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781582"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="a2a89-102">ICorDebugManagedCallback::UnloadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="a2a89-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="a2a89-103">クラスがアンロードされていることをデバッガーに通知します。</span><span class="sxs-lookup"><span data-stu-id="a2a89-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2a89-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2a89-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2a89-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2a89-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="a2a89-106">からクラスを含むアプリケーションドメインを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a2a89-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="a2a89-107">からクラスを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a2a89-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2a89-108">コメント</span><span class="sxs-lookup"><span data-stu-id="a2a89-108">Remarks</span></span>  
 <span data-ttu-id="a2a89-109">この呼び出しの後にクラスを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="a2a89-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2a89-110">要件</span><span class="sxs-lookup"><span data-stu-id="a2a89-110">Requirements</span></span>  
 <span data-ttu-id="a2a89-111">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2a89-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2a89-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2a89-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2a89-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2a89-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2a89-114">**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2a89-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2a89-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2a89-115">See also</span></span>

- [<span data-ttu-id="a2a89-116">LoadClass メソッド</span><span class="sxs-lookup"><span data-stu-id="a2a89-116">LoadClass Method</span></span>](icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="a2a89-117">ICorDebugManagedCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2a89-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
