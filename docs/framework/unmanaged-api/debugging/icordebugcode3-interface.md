---
title: ICorDebugCode3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: 6f66e4a903be2e9b12a573f74638a62c58005689
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893454"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="306e0-102">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="306e0-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="306e0-103">"" のコード "と" ICorDebugCode2 "を拡張して、マネージ戻り値に関する情報を提供するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="306e0-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="306e0-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="306e0-104">Methods</span></span>  
  
|<span data-ttu-id="306e0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="306e0-105">Method</span></span>|<span data-ttu-id="306e0-106">説明</span><span class="sxs-lookup"><span data-stu-id="306e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="306e0-107">GetReturnValueLiveOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="306e0-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="306e0-108">指定した IL オフセットについて、デバッガーが関数からの戻り値を取得できるように、ブレークポイントを配置する必要があるネイティブなオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="306e0-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="306e0-109">解説</span><span class="sxs-lookup"><span data-stu-id="306e0-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="306e0-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="306e0-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="306e0-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="306e0-111">Requirements</span></span>  
 <span data-ttu-id="306e0-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="306e0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="306e0-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="306e0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="306e0-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="306e0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="306e0-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="306e0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306e0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="306e0-116">See also</span></span>

- [<span data-ttu-id="306e0-117">ICorDebugILFrame3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="306e0-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="306e0-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="306e0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
