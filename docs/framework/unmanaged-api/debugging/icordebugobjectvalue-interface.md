---
title: ICorDebugObjectValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: 603ab20b57dc4ba736b0342797d0be649a5bebc4
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207489"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="30793-102">ICorDebugObjectValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30793-102">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="30793-103">オブジェクトを含む値を表す "ICorDebugValue" のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="30793-103">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="30793-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-104">Methods</span></span>  
  
|<span data-ttu-id="30793-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-105">Method</span></span>|<span data-ttu-id="30793-106">説明</span><span class="sxs-lookup"><span data-stu-id="30793-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="30793-107">GetClass メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-107">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="30793-108"><xref:System.Type>このが参照するオブジェクトの共通言語ランタイム (CLR) へのインターフェイスポインターを取得し `ICorDebugObjectValue` ます。</span><span class="sxs-lookup"><span data-stu-id="30793-108">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="30793-109">GetContext メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-109">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="30793-110">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="30793-110">Not implemented.</span></span>|  
|[<span data-ttu-id="30793-111">GetFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-111">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="30793-112">指定したクラスの指定したフィールドの値を表す、 [ICorDebugValue](icordebugvalue-interface.md)へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="30793-112">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="30793-113">GetManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-113">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="30793-114">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="30793-114">Obsolete.</span></span> <span data-ttu-id="30793-115">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="30793-115">Do not call this method.</span></span>|  
|[<span data-ttu-id="30793-116">GetVirtualMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-116">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="30793-117">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="30793-117">Not implemented.</span></span>|  
|[<span data-ttu-id="30793-118">IsValueClass メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-118">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="30793-119">このによって参照されるオブジェクトが値型かどうかを示す値を取得し `ICorDebugObjectValue` ます。</span><span class="sxs-lookup"><span data-stu-id="30793-119">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="30793-120">SetFromManagedCopy メソッド</span><span class="sxs-lookup"><span data-stu-id="30793-120">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="30793-121">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="30793-121">Obsolete.</span></span> <span data-ttu-id="30793-122">このメソッドは呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="30793-122">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30793-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="30793-123">Remarks</span></span>  
 <span data-ttu-id="30793-124">は、 `ICorDebugObjectValue` デバッグ中のプロセスが続行されるまで有効なままです。</span><span class="sxs-lookup"><span data-stu-id="30793-124">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30793-125">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="30793-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30793-126">必要条件</span><span class="sxs-lookup"><span data-stu-id="30793-126">Requirements</span></span>  
 <span data-ttu-id="30793-127">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30793-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30793-128">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30793-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30793-129">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30793-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30793-130">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30793-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30793-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="30793-131">See also</span></span>

- [<span data-ttu-id="30793-132">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="30793-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
