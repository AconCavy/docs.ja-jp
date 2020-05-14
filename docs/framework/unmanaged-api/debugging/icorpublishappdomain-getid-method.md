---
title: ICorPublishAppDomain::GetID メソッド
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
ms.openlocfilehash: 36c5c674f3cdf867107b9ee85a5befadc9246d78
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396306"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="1dcf6-102">ICorPublishAppDomain::GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="1dcf6-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="1dcf6-103">この[ICorPublishAppDomain](icorpublishappdomain-interface.md)の一意の識別子を取得します。</span><span class="sxs-lookup"><span data-stu-id="1dcf6-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dcf6-104">構文</span><span class="sxs-lookup"><span data-stu-id="1dcf6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dcf6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1dcf6-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="1dcf6-106">入出力アプリケーションドメインの識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1dcf6-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dcf6-107">解説</span><span class="sxs-lookup"><span data-stu-id="1dcf6-107">Remarks</span></span>  
 <span data-ttu-id="1dcf6-108">識別子は、含んでいるプロセスのスコープ内でのみ一意です。</span><span class="sxs-lookup"><span data-stu-id="1dcf6-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dcf6-109">要件</span><span class="sxs-lookup"><span data-stu-id="1dcf6-109">Requirements</span></span>  
 <span data-ttu-id="1dcf6-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1dcf6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dcf6-111">**ヘッダー:** CorPub .idl、CorPub .h</span><span class="sxs-lookup"><span data-stu-id="1dcf6-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1dcf6-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dcf6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dcf6-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dcf6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dcf6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="1dcf6-114">See also</span></span>

- [<span data-ttu-id="1dcf6-115">ICorPublishAppDomain インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1dcf6-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
