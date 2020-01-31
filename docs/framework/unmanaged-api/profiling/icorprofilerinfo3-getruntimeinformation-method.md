---
title: ICorProfilerInfo3::GetRuntimeInformation メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: e3d167be9a4091ae57a3283424186142e90ca7a1
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868552"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a><span data-ttu-id="3741b-102">ICorProfilerInfo3::GetRuntimeInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="3741b-102">ICorProfilerInfo3::GetRuntimeInformation Method</span></span>
<span data-ttu-id="3741b-103">プロファイリングされている共通言語ランタイム (CLR) に関するバージョン情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="3741b-103">Provides version information about the common language runtime (CLR) that is being profiled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3741b-104">構文</span><span class="sxs-lookup"><span data-stu-id="3741b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3741b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3741b-105">Parameters</span></span>  
 `pClrInstanceId`  
 <span data-ttu-id="3741b-106">入出力プロセス内で実行されている CLR インスタンスの代表 ID。</span><span class="sxs-lookup"><span data-stu-id="3741b-106">[out] The representative ID of a running CLR instance in a process.</span></span> <span data-ttu-id="3741b-107">これは、event tracing for Windows (ETW) のスタートアップイベントで報告される `ClrInstanceID` と同じです。</span><span class="sxs-lookup"><span data-stu-id="3741b-107">This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.</span></span>  
  
 `pRuntimeType`  
 <span data-ttu-id="3741b-108">入出力ランタイム型。</span><span class="sxs-lookup"><span data-stu-id="3741b-108">[out] The runtime type.</span></span> <span data-ttu-id="3741b-109">このパラメーターは、CLR のデスクトップバージョンの `COR_PRF_DESKTOP_CLR`、または Silverlight で使用される CLR のコアバージョンの `COR_PRF_CORE_CLR` を返します。</span><span class="sxs-lookup"><span data-stu-id="3741b-109">This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.</span></span>  
  
 `pMajorVersion`  
 <span data-ttu-id="3741b-110">入出力CLR のメジャーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3741b-110">[out] The major version number of the CLR.</span></span>  
  
 `pMinorVersion`  
 <span data-ttu-id="3741b-111">入出力CLR のマイナーバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3741b-111">[out] The minor version number of the CLR.</span></span>  
  
 `pBuildVersion`  
 <span data-ttu-id="3741b-112">入出力CLR のビルドバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3741b-112">[out] The build version number of the CLR.</span></span>  
  
 `pQFEVersion`  
 <span data-ttu-id="3741b-113">入出力ソフトウェア更新プログラムに関連付けられている CLR のバージョン番号。</span><span class="sxs-lookup"><span data-stu-id="3741b-113">[out] The version number of the CLR that is associated with a software update.</span></span>  
  
 `cchVersionString`  
 <span data-ttu-id="3741b-114">から`szVersionString` が指すバッファーの長さ (文字数)。</span><span class="sxs-lookup"><span data-stu-id="3741b-114">[in] The length, in characters, of the buffer that `szVersionString` points to.</span></span>  
  
 `pcchVersionString`  
 <span data-ttu-id="3741b-115">入出力`szVersionString`の長さ (文字数)。</span><span class="sxs-lookup"><span data-stu-id="3741b-115">[out] The length, in characters, of `szVersionString`.</span></span>  
  
 `szVersionString`  
 <span data-ttu-id="3741b-116">入出力CLR のバージョン文字列。</span><span class="sxs-lookup"><span data-stu-id="3741b-116">[out] The CLR version string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3741b-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="3741b-117">Remarks</span></span>  
 <span data-ttu-id="3741b-118">任意のパラメーターに null を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="3741b-118">You may pass null for any parameter.</span></span> <span data-ttu-id="3741b-119">ただし、`szVersionString` が null の場合を除き、`pcchVersionString` を null にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="3741b-119">However, `pcchVersionString` cannot be null unless `szVersionString` is also null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3741b-120">要件</span><span class="sxs-lookup"><span data-stu-id="3741b-120">Requirements</span></span>  
 <span data-ttu-id="3741b-121">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3741b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3741b-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3741b-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3741b-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3741b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3741b-124">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3741b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3741b-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3741b-125">See also</span></span>

- [<span data-ttu-id="3741b-126">ICorProfilerInfo3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3741b-126">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="3741b-127">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3741b-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3741b-128">プロファイル</span><span class="sxs-lookup"><span data-stu-id="3741b-128">Profiling</span></span>](index.md)
