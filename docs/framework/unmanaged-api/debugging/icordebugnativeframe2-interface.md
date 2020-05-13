---
title: ICorDebugNativeFrame2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
ms.openlocfilehash: cd2a2821128ad9265e8a831f7b02792e6453b1ee
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213791"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="45c8d-102">ICorDebugNativeFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45c8d-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="45c8d-103">子と親のフレームの関係をテストするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="45c8d-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="45c8d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="45c8d-104">Methods</span></span>  
  
|<span data-ttu-id="45c8d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="45c8d-105">Method</span></span>|<span data-ttu-id="45c8d-106">説明</span><span class="sxs-lookup"><span data-stu-id="45c8d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45c8d-107">IsChild メソッド</span><span class="sxs-lookup"><span data-stu-id="45c8d-107">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="45c8d-108">現在のフレームが子フレームであるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="45c8d-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="45c8d-109">IsMatchingParentFrame メソッド</span><span class="sxs-lookup"><span data-stu-id="45c8d-109">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="45c8d-110">指定したフレームが現在のフレームの親であるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="45c8d-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="45c8d-111">GetStackParameterSize メソッド</span><span class="sxs-lookup"><span data-stu-id="45c8d-111">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="45c8d-112">X86 オペレーティングシステムのスタックのパラメーターの累積サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="45c8d-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45c8d-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="45c8d-113">Remarks</span></span>  
 <span data-ttu-id="45c8d-114">このインターフェイスは、"" の "テキスト" インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="45c8d-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="45c8d-115">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="45c8d-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45c8d-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="45c8d-116">Requirements</span></span>  
 <span data-ttu-id="45c8d-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="45c8d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45c8d-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="45c8d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="45c8d-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45c8d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45c8d-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45c8d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c8d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="45c8d-121">See also</span></span>

- [<span data-ttu-id="45c8d-122">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="45c8d-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="45c8d-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="45c8d-123">Debugging</span></span>](index.md)
