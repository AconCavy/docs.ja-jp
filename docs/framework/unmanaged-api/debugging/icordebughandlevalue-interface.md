---
title: ICorDebugHandleValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: c901e21521e941c51939958175a5316808890e9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208617"
---
# <a name="icordebughandlevalue-interface"></a><span data-ttu-id="afc2a-102">ICorDebugHandleValue インターフェイス</span><span class="sxs-lookup"><span data-stu-id="afc2a-102">ICorDebugHandleValue Interface</span></span>

<span data-ttu-id="afc2a-103">デバッガーがガベージコレクションのハンドルを作成した参照値を表す、値のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="afc2a-103">A subclass of ICorDebugReferenceValue that represents a reference value to which the debugger has created a handle for garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="afc2a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="afc2a-104">Methods</span></span>  
  
|<span data-ttu-id="afc2a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="afc2a-105">Method</span></span>|<span data-ttu-id="afc2a-106">説明</span><span class="sxs-lookup"><span data-stu-id="afc2a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="afc2a-107">Dispose メソッド</span><span class="sxs-lookup"><span data-stu-id="afc2a-107">Dispose Method</span></span>](icordebughandlevalue-dispose-method.md)|<span data-ttu-id="afc2a-108">`ICorDebugHandleValue`インターフェイスポインターを明示的に解放せずに、このオブジェクトによって参照されるハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="afc2a-108">Releases the handle referenced by this `ICorDebugHandleValue` object without explicitly releasing the interface pointer.</span></span>|  
|[<span data-ttu-id="afc2a-109">GetHandleType メソッド</span><span class="sxs-lookup"><span data-stu-id="afc2a-109">GetHandleType Method</span></span>](icordebughandlevalue-gethandletype-method.md)|<span data-ttu-id="afc2a-110">このによって参照されるハンドルの種類を記述する CorDebugHandleType 値を取得し `ICorDebugHandleValue` ます。</span><span class="sxs-lookup"><span data-stu-id="afc2a-110">Gets a CorDebugHandleType value that describes the kind of handle referenced by this `ICorDebugHandleValue`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afc2a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="afc2a-111">Remarks</span></span>  
 <span data-ttu-id="afc2a-112">`ICorDebugReferenceValue`デバッグ対象のコードの実行が中断された場合、オブジェクトは無効になります。</span><span class="sxs-lookup"><span data-stu-id="afc2a-112">An `ICorDebugReferenceValue` object is invalidated by a break in the execution of debugged code.</span></span> <span data-ttu-id="afc2a-113">は、 `ICorDebugHandleValue` 明示的に解放されるまで、中断および継続による参照を保持します。</span><span class="sxs-lookup"><span data-stu-id="afc2a-113">An `ICorDebugHandleValue` maintains its reference through breaks and continuations, until it is explicitly released.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afc2a-114">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="afc2a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afc2a-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="afc2a-115">Requirements</span></span>  
 <span data-ttu-id="afc2a-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afc2a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afc2a-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afc2a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afc2a-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afc2a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afc2a-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afc2a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc2a-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="afc2a-120">See also</span></span>

- [<span data-ttu-id="afc2a-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="afc2a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
