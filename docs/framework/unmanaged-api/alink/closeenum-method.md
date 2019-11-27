---
title: CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
ms.openlocfilehash: 018af6929ad4023c70bfb975b9be010912415dd7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446565"
---
# <a name="closeenum-method"></a><span data-ttu-id="95085-102">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="95085-102">CloseEnum Method</span></span>
<span data-ttu-id="95085-103">指定された列挙体を閉じ、関連付けられているリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="95085-103">Closes the indicated enumeration and frees associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95085-104">構文</span><span class="sxs-lookup"><span data-stu-id="95085-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="95085-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="95085-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="95085-106">閉じられる列挙体のハンドル。</span><span class="sxs-lookup"><span data-stu-id="95085-106">Handle of enumeration to be closed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95085-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="95085-107">Return Value</span></span>  
 <span data-ttu-id="95085-108">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="95085-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95085-109">要件</span><span class="sxs-lookup"><span data-stu-id="95085-109">Requirements</span></span>  
 <span data-ttu-id="95085-110">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="95085-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95085-111">参照</span><span class="sxs-lookup"><span data-stu-id="95085-111">See also</span></span>

- [<span data-ttu-id="95085-112">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="95085-112">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="95085-113">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="95085-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="95085-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="95085-114">ALink API</span></span>](index.md)
