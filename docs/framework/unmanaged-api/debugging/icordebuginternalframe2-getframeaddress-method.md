---
title: ICorDebugInternalFrame2::GetFrameAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame2.GetFrameAddress Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2::GetFrameAddress
helpviewer_keywords:
- GetFrameAddress method [.NET Framework debugging]
- ICorDebugInternalFrame2::GetFrameAddress method [.NET Framework debugging]
ms.assetid: 4ee8d058-ffc8-4967-9133-a5adfef4e518
topic_type:
- apiref
ms.openlocfilehash: 51c8f9a2b66d7b2553949056f7cdbedcf5ea37d6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209917"
---
# <a name="icordebuginternalframe2getframeaddress-method"></a><span data-ttu-id="b9c7c-102">ICorDebugInternalFrame2::GetFrameAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="b9c7c-102">ICorDebugInternalFrame2::GetFrameAddress Method</span></span>
<span data-ttu-id="b9c7c-103">内部フレームのスタックアドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-103">Returns the stack address of the internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c7c-104">構文</span><span class="sxs-lookup"><span data-stu-id="b9c7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameAddress([out] CORDB_ADDRESS *pAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9c7c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b9c7c-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="b9c7c-106">入出力`CORDB_ADDRESS`内部フレームのへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-106">[out] Pointer to the `CORDB_ADDRESS` for the internal frame.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9c7c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="b9c7c-107">Return Value</span></span>  
 <span data-ttu-id="b9c7c-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b9c7c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b9c7c-109">HRESULT</span></span>|<span data-ttu-id="b9c7c-110">説明</span><span class="sxs-lookup"><span data-stu-id="b9c7c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b9c7c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b9c7c-111">S_OK</span></span>|<span data-ttu-id="b9c7c-112">内部フレームのアドレスが正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-112">The address of the internal frame was successfully returned.</span></span>|  
|<span data-ttu-id="b9c7c-113">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b9c7c-113">E_FAIL</span></span>|<span data-ttu-id="b9c7c-114">内部フレームのアドレスを返すことができませんでした。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-114">The address of the internal frame could not be returned.</span></span>|  
|<span data-ttu-id="b9c7c-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b9c7c-115">E_INVALIDARG</span></span>|<span data-ttu-id="b9c7c-116">`pAddress` は `null` です。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-116">`pAddress` is `null`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9c7c-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9c7c-117">Remarks</span></span>  
 <span data-ttu-id="b9c7c-118">で返される値を使用して、 `pAddress` スタック上の他のフレームに対する内部フレームの位置を判断できます。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-118">The value returned in `pAddress` can be used to determine the location of the internal frame relative to other frames on the stack.</span></span> <span data-ttu-id="b9c7c-119">IA-64 ベースのコンピューターでも、内部フレームはスタックのみに存在し、バッキングストアへの対応するポインターは存在しません。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-119">Even on IA-64-based computers, the internal frame lives on the stack only, and there is no corresponding pointer to a backing store.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c7c-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="b9c7c-120">Requirements</span></span>  
 <span data-ttu-id="b9c7c-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b9c7c-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9c7c-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9c7c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9c7c-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9c7c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9c7c-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9c7c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c7c-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="b9c7c-125">See also</span></span>

- [<span data-ttu-id="b9c7c-126">ICorDebugInternalFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9c7c-126">ICorDebugInternalFrame2 Interface</span></span>](icordebuginternalframe2-interface.md)
- [<span data-ttu-id="b9c7c-127">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="b9c7c-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b9c7c-128">デバッグ</span><span class="sxs-lookup"><span data-stu-id="b9c7c-128">Debugging</span></span>](index.md)
