---
title: ICorDebug::EnumerateProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
ms.openlocfilehash: 14a2fa36393135a1e5ccecb69879113a62a9d065
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895399"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="a8375-102">ICorDebug::EnumerateProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="a8375-102">ICorDebug::EnumerateProcesses Method</span></span>
<span data-ttu-id="a8375-103">デバッグ中のプロセスの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="a8375-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8375-104">構文</span><span class="sxs-lookup"><span data-stu-id="a8375-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8375-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a8375-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="a8375-106">デバッグ中のプロセスの列挙子である、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a8375-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8375-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="a8375-107">Requirements</span></span>  
 <span data-ttu-id="a8375-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a8375-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8375-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a8375-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a8375-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a8375-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a8375-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8375-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8375-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="a8375-112">See also</span></span>

- [<span data-ttu-id="a8375-113">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a8375-113">ICorDebug Interface</span></span>](icordebug-interface.md)
