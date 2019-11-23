---
title: FreeWin32ResBlob メソッド
ms.date: 03/30/2017
api_name:
- IALink.FreeWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- FreeWin32ResBlob
helpviewer_keywords:
- FreeWin32ResBlob method
ms.assetid: d941102b-2679-4c49-b15e-c0fc9c53e11f
topic_type:
- apiref
ms.openlocfilehash: 2b1addc752c7238116e072c6e957d2b277ceb1e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449403"
---
# <a name="freewin32resblob-method"></a><span data-ttu-id="c975d-102">FreeWin32ResBlob メソッド</span><span class="sxs-lookup"><span data-stu-id="c975d-102">FreeWin32ResBlob Method</span></span>
<span data-ttu-id="c975d-103">Releases the Win32 resource blob and associated resources.</span><span class="sxs-lookup"><span data-stu-id="c975d-103">Releases the Win32 resource blob and associated resources.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c975d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c975d-104">Syntax</span></span>  
  
```cpp  
HRESULT FreeWin32ResBlob(  
    const void** ppResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c975d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c975d-105">Parameters</span></span>  
 `ppResBlob`  
 <span data-ttu-id="c975d-106">The resource blob to be released.</span><span class="sxs-lookup"><span data-stu-id="c975d-106">The resource blob to be released.</span></span> <span data-ttu-id="c975d-107">This method assigns the blob pointer to NULL.</span><span class="sxs-lookup"><span data-stu-id="c975d-107">This method assigns the blob pointer to NULL.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c975d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="c975d-108">Return Value</span></span>  
 <span data-ttu-id="c975d-109">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="c975d-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c975d-110">［要件］</span><span class="sxs-lookup"><span data-stu-id="c975d-110">Requirements</span></span>  
 <span data-ttu-id="c975d-111">Requires alink.h</span><span class="sxs-lookup"><span data-stu-id="c975d-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c975d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="c975d-112">See also</span></span>

- [<span data-ttu-id="c975d-113">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c975d-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c975d-114">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c975d-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c975d-115">ALink API</span><span class="sxs-lookup"><span data-stu-id="c975d-115">ALink API</span></span>](index.md)
