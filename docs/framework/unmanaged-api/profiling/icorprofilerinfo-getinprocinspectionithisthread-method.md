---
title: ICorProfilerInfo::GetInprocInspectionIThisThread メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
ms.openlocfilehash: 0a4cb365ca8f7d52be505368a3d769a9728983bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502965"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="52d19-102">ICorProfilerInfo::GetInprocInspectionIThisThread メソッド</span><span class="sxs-lookup"><span data-stu-id="52d19-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="52d19-103">のオブジェクトインターフェイスに対してクエリを実行できるオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="52d19-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="52d19-104">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="52d19-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d19-105">構文</span><span class="sxs-lookup"><span data-stu-id="52d19-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52d19-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52d19-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="52d19-107">インターフェイスに対してクエリを実行できる[out](/cpp/atl/iunknown)オブジェクト `ICorDebugThread` 。</span><span class="sxs-lookup"><span data-stu-id="52d19-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52d19-108">解説</span><span class="sxs-lookup"><span data-stu-id="52d19-108">Remarks</span></span>  
 <span data-ttu-id="52d19-109">共通言語ランタイム (CLR) のデバッグサービスでは、.NET Framework バージョン1.0 でサポートされているプロセス内デバッグが制限されています。</span><span class="sxs-lookup"><span data-stu-id="52d19-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="52d19-110">インプロセスデバッグでは、デバッグ API の検査部分を使用するプロファイラーが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="52d19-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="52d19-111">お客様からのフィードバックの結果として、プロセス内デバッグはバージョン2.0 の .NET Framework から削除され、プロファイル API により多くの機能を備えた一連の機能に置き換えられました。</span><span class="sxs-lookup"><span data-stu-id="52d19-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52d19-112">要件</span><span class="sxs-lookup"><span data-stu-id="52d19-112">Requirements</span></span>  
 <span data-ttu-id="52d19-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52d19-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52d19-114">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="52d19-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52d19-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52d19-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52d19-116">**.NET Framework のバージョン:** 1.0</span><span class="sxs-lookup"><span data-stu-id="52d19-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52d19-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="52d19-117">See also</span></span>

- [<span data-ttu-id="52d19-118">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52d19-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
