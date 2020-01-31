---
title: ICorDebugBlockingObjectEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: c25f26bb0f1f34e3799bab4bec7e697d393cccb4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784513"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="71ef6-102">ICorDebugBlockingObjectEnum::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="71ef6-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="71ef6-103">現在の位置から開始して、指定した数の[CorDebugBlockingObject](cordebugblockingobject-structure.md)オブジェクトを列挙から取得します。</span><span class="sxs-lookup"><span data-stu-id="71ef6-103">Gets the specified number of [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71ef6-104">構文</span><span class="sxs-lookup"><span data-stu-id="71ef6-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="71ef6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71ef6-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="71ef6-106">から取得するオブジェクトの数。</span><span class="sxs-lookup"><span data-stu-id="71ef6-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="71ef6-107">入出力[CorDebugBlockingObject](cordebugblockingobject-structure.md)オブジェクトへのポインターの配列。</span><span class="sxs-lookup"><span data-stu-id="71ef6-107">[out] An array of pointers to [CorDebugBlockingObject](cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="71ef6-108">入出力取得されたオブジェクトの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="71ef6-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71ef6-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="71ef6-109">Return Value</span></span>  
 <span data-ttu-id="71ef6-110">このメソッドは、次の特定の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="71ef6-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="71ef6-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="71ef6-111">HRESULT</span></span>|<span data-ttu-id="71ef6-112">説明</span><span class="sxs-lookup"><span data-stu-id="71ef6-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="71ef6-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="71ef6-113">S_OK</span></span>|<span data-ttu-id="71ef6-114">メソッドは正常に終了しました。</span><span class="sxs-lookup"><span data-stu-id="71ef6-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="71ef6-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="71ef6-115">S_FALSE</span></span>|<span data-ttu-id="71ef6-116">`pceltFetched` は `celt` と一致しません。</span><span class="sxs-lookup"><span data-stu-id="71ef6-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71ef6-117">コメント</span><span class="sxs-lookup"><span data-stu-id="71ef6-117">Remarks</span></span>  
 <span data-ttu-id="71ef6-118">このメソッドは、一般的な COM 列挙子と同様に機能します。</span><span class="sxs-lookup"><span data-stu-id="71ef6-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="71ef6-119">入力配列の値は `celt`以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ef6-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="71ef6-120">配列には、列挙体の次の `celt` 値、または `celt` 未満の値が残っている場合は、残りのすべての値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="71ef6-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="71ef6-121">このメソッドから制御が戻るときに、取得された値の数が `pceltFetched` に格納されます。</span><span class="sxs-lookup"><span data-stu-id="71ef6-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="71ef6-122">`values` に無効なポインターが含まれている場合、または `celt`より小さいバッファーを指している場合、または `pceltFetched` が無効なポインターである場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="71ef6-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71ef6-123">[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体を解放する必要はありませんが、その中の "ICorDebugValue" インターフェイスは解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="71ef6-123">Although the [CorDebugBlockingObject](cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71ef6-124">要件</span><span class="sxs-lookup"><span data-stu-id="71ef6-124">Requirements</span></span>  
 <span data-ttu-id="71ef6-125">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="71ef6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71ef6-126">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71ef6-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71ef6-127">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71ef6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71ef6-128">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71ef6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71ef6-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="71ef6-129">See also</span></span>

- [<span data-ttu-id="71ef6-130">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71ef6-130">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="71ef6-131">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71ef6-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="71ef6-132">デバッグ</span><span class="sxs-lookup"><span data-stu-id="71ef6-132">Debugging</span></span>](index.md)
