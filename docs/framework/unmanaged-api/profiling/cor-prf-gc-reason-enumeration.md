---
title: COR_PRF_GC_REASON 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
ms.openlocfilehash: 409a21238f172e5ecdaa8d5bfa237a9f3fe46345
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500911"
---
# <a name="cor_prf_gc_reason-enumeration"></a><span data-ttu-id="46afd-102">COR_PRF_GC_REASON 列挙型</span><span class="sxs-lookup"><span data-stu-id="46afd-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="46afd-103">ガベージ コレクションが発生している理由を示します。</span><span class="sxs-lookup"><span data-stu-id="46afd-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46afd-104">構文</span><span class="sxs-lookup"><span data-stu-id="46afd-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="46afd-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="46afd-105">Members</span></span>  
  
|<span data-ttu-id="46afd-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="46afd-106">Member</span></span>|<span data-ttu-id="46afd-107">説明</span><span class="sxs-lookup"><span data-stu-id="46afd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="46afd-108">ガベージコレクションは、メソッドによって発生しました <xref:System.GC.Collect%2A> 。</span><span class="sxs-lookup"><span data-stu-id="46afd-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="46afd-109">理由が指定されていません。</span><span class="sxs-lookup"><span data-stu-id="46afd-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46afd-110">要件</span><span class="sxs-lookup"><span data-stu-id="46afd-110">Requirements</span></span>  
 <span data-ttu-id="46afd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46afd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46afd-112">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="46afd-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46afd-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46afd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46afd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46afd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46afd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="46afd-115">See also</span></span>

- [<span data-ttu-id="46afd-116">列挙体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="46afd-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
