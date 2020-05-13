---
title: ICorDebugSymbolProvider2::GetFrameProps メソッド
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ad44c5a7b2d901967ae354f3c30218a8c7f2c2de
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379333"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="ba1e8-102">ICorDebugSymbolProvider2::GetFrameProps メソッド</span><span class="sxs-lookup"><span data-stu-id="ba1e8-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="ba1e8-103">メソッドのメソッド開始位置を示す相対仮想アドレスと、指定されたコード相対仮想アドレスを持つ親フレームを返します。</span><span class="sxs-lookup"><span data-stu-id="ba1e8-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba1e8-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba1e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba1e8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ba1e8-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="ba1e8-106">[in] コード相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="ba1e8-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="ba1e8-107">[out] メソッドの開始相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ba1e8-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="ba1e8-108">[out] フレームの開始相対仮想アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ba1e8-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba1e8-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba1e8-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba1e8-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ba1e8-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba1e8-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="ba1e8-111">Requirements</span></span>  
 <span data-ttu-id="ba1e8-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ba1e8-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba1e8-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba1e8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba1e8-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba1e8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba1e8-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba1e8-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba1e8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba1e8-116">See also</span></span>

- [<span data-ttu-id="ba1e8-117">ICorDebugSymbolProvider2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba1e8-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="ba1e8-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ba1e8-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
