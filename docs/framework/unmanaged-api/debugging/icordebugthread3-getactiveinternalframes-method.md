---
title: ICorDebugThread3::GetActiveInternalFrames メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: 953b7c1cb5e471072776fe03e53a46d3ff19c0ac
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379862"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a><span data-ttu-id="fdb22-102">ICorDebugThread3::GetActiveInternalFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="fdb22-102">ICorDebugThread3::GetActiveInternalFrames Method</span></span>
<span data-ttu-id="fdb22-103">スタック上の内部フレーム ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) の配列を返します。</span><span class="sxs-lookup"><span data-stu-id="fdb22-103">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdb22-104">構文</span><span class="sxs-lookup"><span data-stu-id="fdb22-104">Syntax</span></span>  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a><span data-ttu-id="fdb22-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fdb22-105">Parameters</span></span>  
 `cInternalFrames`  
 <span data-ttu-id="fdb22-106">からで予期される内部フレームの数 `ppInternalFrames` 。</span><span class="sxs-lookup"><span data-stu-id="fdb22-106">[in] The number of internal frames expected in `ppInternalFrames`.</span></span>  
  
 `pcInternalFrames`  
 <span data-ttu-id="fdb22-107">入出力`ULONG32`スタック上の内部フレームの数を格納しているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fdb22-107">[out] A pointer to a `ULONG32` that contains the number of internal frames on the stack.</span></span>  
  
 `ppInternalFrames`  
 <span data-ttu-id="fdb22-108">[入力、出力]スタック上の内部フレームの配列のアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="fdb22-108">[in, out] A pointer to the address of an array of internal frames on the stack.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fdb22-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="fdb22-109">Return Value</span></span>  
 <span data-ttu-id="fdb22-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="fdb22-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="fdb22-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fdb22-111">HRESULT</span></span>|<span data-ttu-id="fdb22-112">説明</span><span class="sxs-lookup"><span data-stu-id="fdb22-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fdb22-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fdb22-113">S_OK</span></span>|<span data-ttu-id="fdb22-114">[ICorDebugInternalFrame2](icordebuginternalframe2-interface.md)オブジェクトが正常に作成されました。</span><span class="sxs-lookup"><span data-stu-id="fdb22-114">The [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) object was successfully created.</span></span>|  
|<span data-ttu-id="fdb22-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="fdb22-115">E_INVALIDARG</span></span>|<span data-ttu-id="fdb22-116">`cInternalFrames`が0では `ppInternalFrames` なく `null` 、がであるか、または `pcInternalFrames` がです `null` 。</span><span class="sxs-lookup"><span data-stu-id="fdb22-116">`cInternalFrames` is not zero and `ppInternalFrames` is `null`, or `pcInternalFrames` is `null`.</span></span>|  
|<span data-ttu-id="fdb22-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="fdb22-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>|<span data-ttu-id="fdb22-118">`ppInternalFrames`が内部フレームの数より小さくなっています。</span><span class="sxs-lookup"><span data-stu-id="fdb22-118">`ppInternalFrames` is smaller than the count of internal frames.</span></span>|  
  
## <a name="exceptions"></a><span data-ttu-id="fdb22-119">例外</span><span class="sxs-lookup"><span data-stu-id="fdb22-119">Exceptions</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fdb22-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="fdb22-120">Remarks</span></span>  
 <span data-ttu-id="fdb22-121">内部フレームは、一時データを格納するためにランタイムによってスタックにプッシュされるデータ構造です。</span><span class="sxs-lookup"><span data-stu-id="fdb22-121">Internal frames are data structures pushed onto the stack by the runtime to store temporary data.</span></span>  
  
 <span data-ttu-id="fdb22-122">を初めて呼び出すときは、 `GetActiveInternalFrames` パラメーターを `cInternalFrames` 0 (ゼロ) に設定し、パラメーターを null に設定する必要があり `ppInternalFrames` ます。</span><span class="sxs-lookup"><span data-stu-id="fdb22-122">When you first call `GetActiveInternalFrames`, you should set the `cInternalFrames` parameter to 0 (zero), and the `ppInternalFrames` parameter to null.</span></span> <span data-ttu-id="fdb22-123">最初にが返されるときに `GetActiveInternalFrames` 、 `pcInternalFrames` スタック上の内部フレームの数を格納します。</span><span class="sxs-lookup"><span data-stu-id="fdb22-123">When `GetActiveInternalFrames` first returns, `pcInternalFrames` contains the count of the internal frames on the stack.</span></span>  
  
 <span data-ttu-id="fdb22-124">`GetActiveInternalFrames`次に、を2回目に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fdb22-124">`GetActiveInternalFrames` should then be called a second time.</span></span> <span data-ttu-id="fdb22-125">パラメーターに適切なカウント () を渡し、 `pcInternalFrames` `cInternalFrames` で適切にサイズ設定された配列へのポインターを指定する必要があり `ppInternalFrames` ます。</span><span class="sxs-lookup"><span data-stu-id="fdb22-125">You should pass the proper count (`pcInternalFrames`) in the `cInternalFrames` parameter, and specify a pointer to an appropriately sized array in `ppInternalFrames`.</span></span>  
  
 <span data-ttu-id="fdb22-126">実際のスタックフレームを返すには、の[テキスト](icordebugthread3-getactiveinternalframes-method.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="fdb22-126">Use the [ICorDebugStackWalk::GetFrame](icordebugthread3-getactiveinternalframes-method.md) method to return actual stack frames.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdb22-127">必要条件</span><span class="sxs-lookup"><span data-stu-id="fdb22-127">Requirements</span></span>  
 <span data-ttu-id="fdb22-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fdb22-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdb22-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdb22-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdb22-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdb22-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdb22-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdb22-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb22-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="fdb22-132">See also</span></span>

- [<span data-ttu-id="fdb22-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="fdb22-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fdb22-134">デバッグ</span><span class="sxs-lookup"><span data-stu-id="fdb22-134">Debugging</span></span>](index.md)
