---
title: ICLRDataTarget::Request メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: b913affb4728dc80ba67438384cbeac87265f76d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860538"
---
# <a name="iclrdatatargetrequest-method"></a><span data-ttu-id="5dd2c-102">ICLRDataTarget::Request メソッド</span><span class="sxs-lookup"><span data-stu-id="5dd2c-102">ICLRDataTarget::Request Method</span></span>
<span data-ttu-id="5dd2c-103">実装で定義されているように、操作を要求するために、共通言語ランタイム (CLR) データアクセスサービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-103">Called by the common language runtime (CLR) data access services to request an operation, as defined by the implementation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd2c-104">構文</span><span class="sxs-lookup"><span data-stu-id="5dd2c-104">Syntax</span></span>  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5dd2c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5dd2c-105">Parameters</span></span>  
 `reqCode`  
 <span data-ttu-id="5dd2c-106">からユーザー定義。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-106">[in] User-defined.</span></span>  
  
 `inBufferSize`  
 <span data-ttu-id="5dd2c-107">から受信要求に使用される入力バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-107">[in] The size of the input buffer, which is used for the incoming request.</span></span>  
  
 `inBuffer`  
 <span data-ttu-id="5dd2c-108">から要求を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-108">[in] A buffer containing the request.</span></span>  
  
 `outBufferSize`  
 <span data-ttu-id="5dd2c-109">から応答に使用される出力バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-109">[in] The size of the output buffer, which is used for the response.</span></span>  
  
 `outBuffer`  
 <span data-ttu-id="5dd2c-110">入出力応答を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-110">[out] A Buffer containing the response.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5dd2c-111">解説</span><span class="sxs-lookup"><span data-stu-id="5dd2c-111">Remarks</span></span>  
 <span data-ttu-id="5dd2c-112">メソッド`Request`は、指定されていないカスタム操作の追加を容易にします。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-112">The `Request` method facilitates the addition of unspecified custom operations.</span></span> <span data-ttu-id="5dd2c-113">つまり、このメソッドは、インターフェイス定義のリビジョンを必要とせずに、拡張機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-113">That is, this method provides extensibility without requiring revision of the interface definition.</span></span>  
  
 <span data-ttu-id="5dd2c-114">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-114">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dd2c-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="5dd2c-115">Requirements</span></span>  
 <span data-ttu-id="5dd2c-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5dd2c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dd2c-117">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="5dd2c-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5dd2c-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5dd2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5dd2c-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dd2c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd2c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5dd2c-120">See also</span></span>

- [<span data-ttu-id="5dd2c-121">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5dd2c-121">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
