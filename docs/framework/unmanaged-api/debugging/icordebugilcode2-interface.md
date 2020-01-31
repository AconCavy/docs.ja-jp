---
title: ICorDebugILCode2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794363"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="7fcdd-102">ICorDebugILCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fcdd-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="7fcdd-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="7fcdd-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7fcdd-104">では、この[コード](icordebugilcode-interface.md)インターフェイスを論理的に拡張して、関数のローカル変数シグネチャのトークンを返すメソッドを提供し、プロファイラーのインストルメント化された中間言語 (il) オフセットを元のメソッドの il オフセットにマップします。</span><span class="sxs-lookup"><span data-stu-id="7fcdd-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fcdd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="7fcdd-105">Methods</span></span>  
  
|<span data-ttu-id="7fcdd-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="7fcdd-106">Method</span></span>|<span data-ttu-id="7fcdd-107">説明</span><span class="sxs-lookup"><span data-stu-id="7fcdd-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fcdd-108">GetInstrumentedILMap メソッド</span><span class="sxs-lookup"><span data-stu-id="7fcdd-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="7fcdd-109">プロファイラーのインストルメント化された IL オフセットから、このインスタンスに対する元のメソッドの IL オフセットへのマップを返します。</span><span class="sxs-lookup"><span data-stu-id="7fcdd-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="7fcdd-110">GetLocalVarSigToken メソッド</span><span class="sxs-lookup"><span data-stu-id="7fcdd-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="7fcdd-111">このインスタンスで示される関数について、ローカル変数のシグネチャのメタデータ トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="7fcdd-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fcdd-112">要件</span><span class="sxs-lookup"><span data-stu-id="7fcdd-112">Requirements</span></span>  
 <span data-ttu-id="7fcdd-113">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7fcdd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fcdd-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7fcdd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7fcdd-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7fcdd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7fcdd-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fcdd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fcdd-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fcdd-117">See also</span></span>

- [<span data-ttu-id="7fcdd-118">ICorDebugILCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fcdd-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="7fcdd-119">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7fcdd-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7fcdd-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="7fcdd-120">Debugging</span></span>](index.md)
