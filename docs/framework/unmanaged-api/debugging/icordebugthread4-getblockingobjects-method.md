---
title: ICorDebugThread4::GetBlockingObjects メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetBlockingObjects Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetBlockingObjects
helpviewer_keywords:
- GetBlockingObjects method [.NET Framework debugging]
- ICorDebugThread4::GetBlockingObjects method [.NET Framework debugging]
ms.assetid: a7e6c54e-7be9-4e52-bbb4-95f52458e8e4
topic_type:
- apiref
ms.openlocfilehash: 366b5124cc66a4e9a1c3bd4e77f604f15ba8d8a8
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379681"
---
# <a name="icordebugthread4getblockingobjects-method"></a><span data-ttu-id="8b9f6-102">ICorDebugThread4::GetBlockingObjects メソッド</span><span class="sxs-lookup"><span data-stu-id="8b9f6-102">ICorDebugThread4::GetBlockingObjects Method</span></span>
<span data-ttu-id="8b9f6-103">スレッドブロック情報を提供する[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体の順序付けられた列挙体を提供します。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-103">Provides an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures that provide thread blocking information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b9f6-104">構文</span><span class="sxs-lookup"><span data-stu-id="8b9f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlockingObjects (  
    [out] ICorDebugBlockingObjectEnum **ppBlockingObjectEnum  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b9f6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8b9f6-105">Parameters</span></span>  
 `ppBlockingObjectEnum`  
 <span data-ttu-id="8b9f6-106">入出力[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体の順序付けられた列挙体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-106">[out] A pointer to an ordered enumeration of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b9f6-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="8b9f6-107">Remarks</span></span>  
 <span data-ttu-id="8b9f6-108">返された列挙体の最初の要素は、スレッドをブロックしている最初の構造体に対応します。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-108">The first element in the returned enumeration corresponds to the first structure that is blocking the thread.</span></span> <span data-ttu-id="8b9f6-109">2番目の要素は、非同期プロシージャ呼び出し (APC) の実行中に検出されるブロッキング項目に対応します。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-109">The second element corresponds to a blocking item that is encountered while running an asynchronous procedure call (APC) when blocked on the first, and so on.</span></span>  
  
 <span data-ttu-id="8b9f6-110">列挙は、現在の同期済みの状態の間のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-110">The enumeration is valid only for the duration of the current synchronized state.</span></span>  
  
 <span data-ttu-id="8b9f6-111">このメソッドは、デバッグ対象が synchronized 状態のときに呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-111">This method must be called while the debuggee is in a synchronized state.</span></span>  
  
 <span data-ttu-id="8b9f6-112">`ppBlockingObjectEnum`が有効なポインターでない場合、結果は未定義になります。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-112">If `ppBlockingObjectEnum` is not a valid pointer, the result is undefined.</span></span>  
  
 <span data-ttu-id="8b9f6-113">スレッドがブロックされていて、エラーを特定できない場合、メソッドは失敗を示す HRESULT を返します。それ以外の場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-113">If a thread is blocked and the error cannot be determined, the method returns an HRESULT that indicates failure; otherwise, it returns S_OK.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b9f6-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="8b9f6-114">Requirements</span></span>  
 <span data-ttu-id="8b9f6-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8b9f6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b9f6-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b9f6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b9f6-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b9f6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b9f6-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b9f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b9f6-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="8b9f6-119">See also</span></span>

- [<span data-ttu-id="8b9f6-120">ICorDebugThread4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b9f6-120">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="8b9f6-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8b9f6-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8b9f6-122">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8b9f6-122">Debugging</span></span>](index.md)
