---
title: INotifySource2::SetNotifyFilter メソッド
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
ms.openlocfilehash: 7ba9f68e102696da107b5cb782c76cb55ed95ee6
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441969"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="ae170-102">INotifySource2::SetNotifyFilter メソッド</span><span class="sxs-lookup"><span data-stu-id="ae170-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="ae170-103">このソースで使用する通知フィルターを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ae170-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae170-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae170-104">Syntax</span></span>  
  
```cpp  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae170-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae170-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="ae170-106">からデバッガー API のコールバックを識別する[NOTIFY_FILTER](notify-filter-enumeration.md)列挙値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="ae170-106">[in] A bitwise combination of the [NOTIFY_FILTER](notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="ae170-107">からデバッガー API のスレッドを識別する[USER_THREAD](user-thread-structure.md)構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ae170-107">[in] A pointer to a [USER_THREAD](user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ae170-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="ae170-108">Return Value</span></span>  
 <span data-ttu-id="ae170-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="ae170-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae170-110">要件</span><span class="sxs-lookup"><span data-stu-id="ae170-110">Requirements</span></span>  
 <span data-ttu-id="ae170-111">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="ae170-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae170-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ae170-112">See also</span></span>

- [<span data-ttu-id="ae170-113">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae170-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="ae170-114">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae170-114">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="ae170-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ae170-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
