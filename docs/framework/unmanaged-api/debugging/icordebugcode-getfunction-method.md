---
title: ICorDebugCode::GetFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
ms.openlocfilehash: 9f785eafa8925324e3bd269ca08a3b1367b74c44
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893587"
---
# <a name="icordebugcodegetfunction-method"></a><span data-ttu-id="6d739-102">ICorDebugCode::GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="6d739-102">ICorDebugCode::GetFunction Method</span></span>
<span data-ttu-id="6d739-103">この "コード" に関連付けられている "コード" を取得します。</span><span class="sxs-lookup"><span data-stu-id="6d739-103">Gets the "ICorDebugFunction" associated with this "ICorDebugCode".</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d739-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d739-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d739-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d739-105">Parameters</span></span>  
 `ppFunction`  
 <span data-ttu-id="6d739-106">入出力関数のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6d739-106">[out] A pointer to the address of the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d739-107">解説</span><span class="sxs-lookup"><span data-stu-id="6d739-107">Remarks</span></span>  
 <span data-ttu-id="6d739-108">`ICorDebugCode`と`ICorDebugFunction`は、一対一のリレーションシップを維持します。</span><span class="sxs-lookup"><span data-stu-id="6d739-108">`ICorDebugCode` and `ICorDebugFunction` maintain a one-to-one relationship.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d739-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="6d739-109">Requirements</span></span>  
 <span data-ttu-id="6d739-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d739-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d739-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d739-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d739-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d739-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d739-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d739-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
