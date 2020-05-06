---
title: ICLRDataTarget3::GetExceptionThreadID メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
ms.openlocfilehash: 63c92e3f34527f895552f45d43f332f778470b13
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860425"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="50485-102">ICLRDataTarget3::GetExceptionThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="50485-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="50485-103">例外をスローしたスレッドの ID を取得するために、共通言語ランタイム (CLR) データ アクセス サービスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="50485-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50485-104">構文</span><span class="sxs-lookup"><span data-stu-id="50485-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50485-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50485-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="50485-106">[out] 例外をスローしたスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="50485-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50485-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="50485-107">Return Value</span></span>  
 <span data-ttu-id="50485-108">戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。</span><span class="sxs-lookup"><span data-stu-id="50485-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="50485-109">次が `HRESULT` コードに含まれることはありますが、限定されているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="50485-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="50485-110">リターン コード</span><span class="sxs-lookup"><span data-stu-id="50485-110">Return code</span></span>|<span data-ttu-id="50485-111">説明</span><span class="sxs-lookup"><span data-stu-id="50485-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="50485-112">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="50485-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="50485-113">例外の有効なスレッド ID を見つけることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="50485-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50485-114">解説</span><span class="sxs-lookup"><span data-stu-id="50485-114">Remarks</span></span>  
 <span data-ttu-id="50485-115">このメソッドは、デバッグ アプリケーションの作成者によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="50485-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50485-116">必要条件</span><span class="sxs-lookup"><span data-stu-id="50485-116">Requirements</span></span>  
 <span data-ttu-id="50485-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50485-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50485-118">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="50485-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="50485-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="50485-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50485-120">**.NET Framework のバージョン:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="50485-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50485-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="50485-121">See also</span></span>

- [<span data-ttu-id="50485-122">ICLRDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="50485-122">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="50485-123">GetExceptionContextRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="50485-123">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="50485-124">GetExceptionRecord メソッド</span><span class="sxs-lookup"><span data-stu-id="50485-124">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
