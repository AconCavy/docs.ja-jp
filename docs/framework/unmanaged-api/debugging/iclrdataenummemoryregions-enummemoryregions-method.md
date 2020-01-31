---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: f2b2bbe8bcecf71f6d3016fb35dfbf5ba1353aea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785635"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a><span data-ttu-id="00fd8-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions メソッド</span><span class="sxs-lookup"><span data-stu-id="00fd8-102">ICLRDataEnumMemoryRegions::EnumMemoryRegions Method</span></span>
<span data-ttu-id="00fd8-103">指定されたメモリ領域を列挙します。</span><span class="sxs-lookup"><span data-stu-id="00fd8-103">Enumerates specified areas of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00fd8-104">構文</span><span class="sxs-lookup"><span data-stu-id="00fd8-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00fd8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="00fd8-105">Parameters</span></span>  
 `callback`  
 <span data-ttu-id="00fd8-106">から結果をデバッガーに通知するために、列挙される各メモリ領域に対してこのメソッドによって呼び出される[ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="00fd8-106">[in] A pointer to an [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance that is called by this method for each memory region being enumerated to notify the debugger of the result.</span></span>  
  
 <span data-ttu-id="00fd8-107">コールバックがエラーを示す場合でも、メモリ領域の列挙は続行されます。</span><span class="sxs-lookup"><span data-stu-id="00fd8-107">The enumeration of memory regions continues even if the callback indicates a failure.</span></span>  
  
 `miniDumpFlags`  
 <span data-ttu-id="00fd8-108">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="00fd8-108">[in] Not used.</span></span>  
  
 `clrFlags`  
 <span data-ttu-id="00fd8-109">から列挙するメモリ領域を指定する[Clrdataenummemoryflags](clrdataenummemoryflags-enumeration.md)列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="00fd8-109">[in] A value of the [CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md) enumeration that specifies the regions of memory to be enumerated.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00fd8-110">コメント</span><span class="sxs-lookup"><span data-stu-id="00fd8-110">Remarks</span></span>  
 <span data-ttu-id="00fd8-111">このメソッドは、指定された[ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)インスタンスを使用して、結果を呼び出し元に通知します。</span><span class="sxs-lookup"><span data-stu-id="00fd8-111">This method uses the specified [ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md) instance to notify the caller of results.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00fd8-112">要件</span><span class="sxs-lookup"><span data-stu-id="00fd8-112">Requirements</span></span>  
 <span data-ttu-id="00fd8-113">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00fd8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00fd8-114">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="00fd8-114">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="00fd8-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00fd8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00fd8-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00fd8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00fd8-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="00fd8-117">See also</span></span>

- [<span data-ttu-id="00fd8-118">ICLRDataEnumMemoryRegions インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00fd8-118">ICLRDataEnumMemoryRegions Interface</span></span>](iclrdataenummemoryregions-interface.md)
