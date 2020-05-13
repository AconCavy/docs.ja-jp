---
title: ICorDebugMetaDataLocator インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugMetaDataLocator
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMetaDataLocator
helpviewer_keywords:
- ICorDebugMetaDataLocator interface [.NET Framework debugging]
ms.assetid: 287f5ecd-863f-4090-a615-077859f0257b
topic_type:
- apiref
ms.openlocfilehash: 7b7b7a42edea775d1aaa850ccfc532ef86749991
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210025"
---
# <a name="icordebugmetadatalocator-interface"></a><span data-ttu-id="7da1e-102">ICorDebugMetaDataLocator インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7da1e-102">ICorDebugMetaDataLocator Interface</span></span>
<span data-ttu-id="7da1e-103">デバッガーにメタデータ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="7da1e-103">Provides metadata information to the debugger.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7da1e-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="7da1e-104">Methods</span></span>  
  
|<span data-ttu-id="7da1e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7da1e-105">Method</span></span>|<span data-ttu-id="7da1e-106">説明</span><span class="sxs-lookup"><span data-stu-id="7da1e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7da1e-107">GetMetaData メソッド</span><span class="sxs-lookup"><span data-stu-id="7da1e-107">GetMetaData Method</span></span>](icordebugmetadatalocator-getmetadata-method.md)|<span data-ttu-id="7da1e-108">デバッガーが要求した操作を完了するために必要となるメタデータが含まれているモジュールの完全パスを返すように、デバッガーに求めます。</span><span class="sxs-lookup"><span data-stu-id="7da1e-108">Asks the debugger to return the full path to a module whose metadata is needed to complete an operation the debugger requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7da1e-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="7da1e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7da1e-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="7da1e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7da1e-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="7da1e-111">Requirements</span></span>  
 <span data-ttu-id="7da1e-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7da1e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7da1e-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7da1e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7da1e-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7da1e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7da1e-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da1e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da1e-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="7da1e-116">See also</span></span>

- [<span data-ttu-id="7da1e-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="7da1e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7da1e-118">デバッグ</span><span class="sxs-lookup"><span data-stu-id="7da1e-118">Debugging</span></span>](index.md)
