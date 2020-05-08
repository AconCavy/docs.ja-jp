---
title: ICorDebugBreakpoint::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint::IsActive
helpviewer_keywords:
- ICorDebugBreakpoint::IsActive method [.NET Framework debugging]
- IsActive method, ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: 06e583d6-d88a-4ff5-bb95-5c48618a461c
topic_type:
- apiref
ms.openlocfilehash: 64a30ca85a75ebd11918ff630daffbb85c97f6dc
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894724"
---
# <a name="icordebugbreakpointisactive-method"></a><span data-ttu-id="a35aa-102">ICorDebugBreakpoint::IsActive メソッド</span><span class="sxs-lookup"><span data-stu-id="a35aa-102">ICorDebugBreakpoint::IsActive Method</span></span>
<span data-ttu-id="a35aa-103">この`ICorDebugBreakpoint`がアクティブかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a35aa-103">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a35aa-104">構文</span><span class="sxs-lookup"><span data-stu-id="a35aa-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a35aa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a35aa-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="a35aa-106">入出力`true`このブレークポイントがアクティブである場合は。それ以外`false`の場合は。</span><span class="sxs-lookup"><span data-stu-id="a35aa-106">[out] `true` if this breakpoint is active; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a35aa-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="a35aa-107">Requirements</span></span>  
 <span data-ttu-id="a35aa-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a35aa-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a35aa-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a35aa-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a35aa-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a35aa-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a35aa-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a35aa-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
