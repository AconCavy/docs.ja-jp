---
title: ICorDebugExceptionDebugEvent::GetFlags メソッド
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: aaf137b1d851d0de86bde697c9e3a512f34d2aa9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782915"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="26dfe-102">ICorDebugExceptionDebugEvent::GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="26dfe-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>
<span data-ttu-id="26dfe-103">例外をインターセプトできるかどうかを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="26dfe-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26dfe-104">構文</span><span class="sxs-lookup"><span data-stu-id="26dfe-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26dfe-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="26dfe-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="26dfe-106">入出力例外をインターセプトできるかどうかを示す[Cordebugexceptionflags](cordebugexceptionflags-enumeration.md)値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="26dfe-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26dfe-107">コメント</span><span class="sxs-lookup"><span data-stu-id="26dfe-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26dfe-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="26dfe-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26dfe-109">要件</span><span class="sxs-lookup"><span data-stu-id="26dfe-109">Requirements</span></span>  
 <span data-ttu-id="26dfe-110">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="26dfe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26dfe-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26dfe-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26dfe-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26dfe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26dfe-113">**.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26dfe-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26dfe-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="26dfe-114">See also</span></span>

- [<span data-ttu-id="26dfe-115">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26dfe-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="26dfe-116">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="26dfe-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
