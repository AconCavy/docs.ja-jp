---
title: ICorProfilerCallback::ExceptionCLRCatcherFound メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: 4f4d53b086453adce38902518f2de3dde1f2812f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500248"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="86e08-102">ICorProfilerCallback::ExceptionCLRCatcherFound メソッド</span><span class="sxs-lookup"><span data-stu-id="86e08-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="86e08-103">`catch`例外のブロックが共通言語ランタイム (CLR) 自体で見つかった場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="86e08-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="86e08-104">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="86e08-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86e08-105">構文</span><span class="sxs-lookup"><span data-stu-id="86e08-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="86e08-106">要件</span><span class="sxs-lookup"><span data-stu-id="86e08-106">Requirements</span></span>  
 <span data-ttu-id="86e08-107">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86e08-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86e08-108">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86e08-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86e08-109">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86e08-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86e08-110">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="86e08-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e08-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="86e08-111">See also</span></span>

- [<span data-ttu-id="86e08-112">ICorProfilerCallback インターフェイス</span><span class="sxs-lookup"><span data-stu-id="86e08-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="86e08-113">ExceptionCLRCatcherExecute メソッド</span><span class="sxs-lookup"><span data-stu-id="86e08-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
