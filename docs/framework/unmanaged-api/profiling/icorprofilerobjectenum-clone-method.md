---
title: ICorProfilerObjectEnum::Clone メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
ms.openlocfilehash: a2a54c32c0713b4b69d8f2a0272687cbe9420610
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494775"
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="c45c6-102">ICorProfilerObjectEnum::Clone メソッド</span><span class="sxs-lookup"><span data-stu-id="c45c6-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="c45c6-103">この[ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md)インターフェイスのコピーへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c45c6-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c45c6-104">構文</span><span class="sxs-lookup"><span data-stu-id="c45c6-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c45c6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c45c6-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="c45c6-106">入出力このインターフェイスのコピーを指すインターフェイスポインターへのポインター `ICorProfilerObjectEnum` 。</span><span class="sxs-lookup"><span data-stu-id="c45c6-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="c45c6-107">コピーは、このコピーとは別に独自の列挙状態を保持します。</span><span class="sxs-lookup"><span data-stu-id="c45c6-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="c45c6-108">ただし、コピーの初期カーソル位置は、この列挙子の現在のカーソル位置と同じになります。</span><span class="sxs-lookup"><span data-stu-id="c45c6-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c45c6-109">要件</span><span class="sxs-lookup"><span data-stu-id="c45c6-109">Requirements</span></span>  
 <span data-ttu-id="c45c6-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c45c6-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c45c6-111">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c45c6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c45c6-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c45c6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c45c6-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c45c6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c45c6-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c45c6-114">See also</span></span>

- [<span data-ttu-id="c45c6-115">ICorProfilerObjectEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c45c6-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
