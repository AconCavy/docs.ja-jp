---
title: ICLRDataTarget::SetTLSValue メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
ms.openlocfilehash: 6e6e157c7176a0f4f1ad3c585977e2cfb31c33d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793684"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="a629b-102">ICLRDataTarget::SetTLSValue メソッド</span><span class="sxs-lookup"><span data-stu-id="a629b-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="a629b-103">ターゲットプロセス内の指定したスレッドのスレッドローカルストレージ (TLS) の値を設定します。</span><span class="sxs-lookup"><span data-stu-id="a629b-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="a629b-104">このメソッドは、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a629b-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a629b-105">構文</span><span class="sxs-lookup"><span data-stu-id="a629b-105">Syntax</span></span>  
  
```cpp  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a629b-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a629b-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="a629b-107">からターゲットプロセス内のスレッドのオペレーティングシステム識別子。</span><span class="sxs-lookup"><span data-stu-id="a629b-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="a629b-108">から位置のインデックス。</span><span class="sxs-lookup"><span data-stu-id="a629b-108">[in] The index of the location.</span></span> <span data-ttu-id="a629b-109">この値は、指定されたスレッドのローカルストア内の有効なインデックスである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a629b-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="a629b-110">から指定した TLS の場所に配置する値を指定する `CLRDATA_ADDRESS` 値。</span><span class="sxs-lookup"><span data-stu-id="a629b-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a629b-111">コメント</span><span class="sxs-lookup"><span data-stu-id="a629b-111">Remarks</span></span>  
 <span data-ttu-id="a629b-112">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="a629b-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a629b-113">要件</span><span class="sxs-lookup"><span data-stu-id="a629b-113">Requirements</span></span>  
 <span data-ttu-id="a629b-114">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a629b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a629b-115">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="a629b-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="a629b-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a629b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a629b-117">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a629b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a629b-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a629b-118">See also</span></span>

- [<span data-ttu-id="a629b-119">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a629b-119">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
