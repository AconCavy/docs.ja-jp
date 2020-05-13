---
title: ICorDebugSymbolProvider::GetCodeRange メソッド
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: a9c1a4a625196d7430e365916cc7c2b67bf94127
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83376089"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="5a2a3-102">ICorDebugSymbolProvider::GetCodeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="5a2a3-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="5a2a3-103">メソッド内の指定の相対仮想アドレス (RVA: relative virtual address) で、メソッド開始アドレスとサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a2a3-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a2a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="5a2a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a2a3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a2a3-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="5a2a3-106">[in] メソッド内の相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="5a2a3-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="5a2a3-107">[out] メソッドの開始アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5a2a3-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="5a2a3-108">メソッドのコードのサイズ (メソッドのコードのバイト数) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5a2a3-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a2a3-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="5a2a3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5a2a3-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5a2a3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a2a3-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="5a2a3-111">Requirements</span></span>  
 <span data-ttu-id="5a2a3-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a2a3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a2a3-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5a2a3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5a2a3-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5a2a3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5a2a3-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a2a3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a2a3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a2a3-116">See also</span></span>

- [<span data-ttu-id="5a2a3-117">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a2a3-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="5a2a3-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a2a3-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
