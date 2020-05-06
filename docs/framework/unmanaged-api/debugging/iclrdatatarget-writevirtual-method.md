---
title: ICLRDataTarget::WriteVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.WriteVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::WriteVirtual
helpviewer_keywords:
- ICLRDataTarget::WriteVirtual method [.NET Framework debugging]
- WriteVirtual method [.NET Framework debugging]
ms.assetid: d627e8b7-a605-40ac-b9bb-da9a3f1b66d9
topic_type:
- apiref
ms.openlocfilehash: 6a7a7736837f7e6bbf1ad4982e78a75550abbeab
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860500"
---
# <a name="iclrdatatargetwritevirtual-method"></a><span data-ttu-id="cadfc-102">ICLRDataTarget::WriteVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="cadfc-102">ICLRDataTarget::WriteVirtual Method</span></span>
<span data-ttu-id="cadfc-103">指定されたバッファーから指定された仮想メモリアドレスにデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="cadfc-103">Writes data from the specified buffer to the specified virtual memory address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cadfc-104">構文</span><span class="sxs-lookup"><span data-stu-id="cadfc-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [in, size_is(bytesRequested)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesWritten  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cadfc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cadfc-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="cadfc-106">から仮想メモリアドレスを格納する CLRDATA_ADDRESS。</span><span class="sxs-lookup"><span data-stu-id="cadfc-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="cadfc-107">から書き込まれるデータを格納するバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cadfc-107">[in] A pointer to a buffer that stores the data to be written.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="cadfc-108">から書き込むバイト数。</span><span class="sxs-lookup"><span data-stu-id="cadfc-108">[in] The number of bytes to be written.</span></span>  
  
 `bytesWritten`  
 <span data-ttu-id="cadfc-109">入出力書き込まれた実際のバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cadfc-109">[out] A pointer to the actual number of bytes that were written.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cadfc-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="cadfc-110">Requirements</span></span>  
 <span data-ttu-id="cadfc-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cadfc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cadfc-112">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="cadfc-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cadfc-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cadfc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cadfc-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cadfc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cadfc-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cadfc-115">See also</span></span>

- [<span data-ttu-id="cadfc-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cadfc-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
