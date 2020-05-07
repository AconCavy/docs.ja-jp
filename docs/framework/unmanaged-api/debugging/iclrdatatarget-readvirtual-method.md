---
title: ICLRDataTarget::ReadVirtual メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.ReadVirtual
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::ReadVirtual
helpviewer_keywords:
- ReadVirtual method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::ReadVirtual method [.NET Framework debugging]
ms.assetid: da3769eb-1828-4aa1-b9ed-db4842136a43
topic_type:
- apiref
ms.openlocfilehash: e285df37d83ff73fe29fe293380a4053cb5a9eea
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860553"
---
# <a name="iclrdatatargetreadvirtual-method"></a><span data-ttu-id="97b7e-102">ICLRDataTarget::ReadVirtual メソッド</span><span class="sxs-lookup"><span data-stu-id="97b7e-102">ICLRDataTarget::ReadVirtual Method</span></span>
<span data-ttu-id="97b7e-103">指定された仮想メモリアドレスから指定されたバッファーにデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="97b7e-103">Reads data from the specified virtual memory address into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97b7e-104">構文</span><span class="sxs-lookup"><span data-stu-id="97b7e-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadVirtual (  
    [in] CLRDATA_ADDRESS    address,  
    [out, size_is(bytesRequested), length_is(*bytesRead)]
        BYTE                *buffer,  
    [in] ULONG32            bytesRequested,  
    [out] ULONG32           *bytesRead  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97b7e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="97b7e-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="97b7e-106">から仮想メモリアドレスを格納する CLRDATA_ADDRESS。</span><span class="sxs-lookup"><span data-stu-id="97b7e-106">[in] A CLRDATA_ADDRESS that stores the virtual memory address.</span></span>  
  
 `buffer`  
 <span data-ttu-id="97b7e-107">入出力データを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="97b7e-107">[out] A pointer to a buffer that receives the data.</span></span>  
  
 `bytesRequested`  
 <span data-ttu-id="97b7e-108">からバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="97b7e-108">[in] The length of the buffer.</span></span>  
  
 `bytesRead`  
 <span data-ttu-id="97b7e-109">入出力返されたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="97b7e-109">[out] A pointer to the number of bytes returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97b7e-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="97b7e-110">Requirements</span></span>  
 <span data-ttu-id="97b7e-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="97b7e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97b7e-112">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="97b7e-112">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="97b7e-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97b7e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97b7e-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97b7e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b7e-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="97b7e-115">See also</span></span>

- [<span data-ttu-id="97b7e-116">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="97b7e-116">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
