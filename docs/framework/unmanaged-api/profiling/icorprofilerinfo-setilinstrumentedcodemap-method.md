---
title: ICorProfilerInfo::SetILInstrumentedCodeMap メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetILInstrumentedCodeMap
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap
helpviewer_keywords:
- ICorProfilerInfo::SetILInstrumentedCodeMap method [.NET Framework profiling]
- SetILInstrumentedCodeMap method [.NET Framework profiling]
ms.assetid: bce1dcf8-b4ec-4e73-a917-f2df1ad49c8a
topic_type:
- apiref
ms.openlocfilehash: cac8e9570dab55af6b6e1fcf6f53b6a697727972
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502913"
---
# <a name="icorprofilerinfosetilinstrumentedcodemap-method"></a><span data-ttu-id="c0d3c-102">ICorProfilerInfo::SetILInstrumentedCodeMap メソッド</span><span class="sxs-lookup"><span data-stu-id="c0d3c-102">ICorProfilerInfo::SetILInstrumentedCodeMap Method</span></span>

<span data-ttu-id="c0d3c-103">指定された MSIL (Microsoft 中間言語) マップエントリを使用して、指定された関数のコードマップを設定します。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-103">Sets a code map for the specified function using the specified Microsoft intermediate language (MSIL) map entries.</span></span>

> [!NOTE]
> <span data-ttu-id="c0d3c-104">.NET Framework バージョン2.0 では、 `SetILInstrumentedCodeMap` `FunctionID` 特定のアプリケーションドメインのジェネリック関数を表すでを呼び出すと、アプリケーションドメイン内のその関数のすべてのインスタンスに影響します。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-104">In the .NET Framework version 2.0, calling `SetILInstrumentedCodeMap` on a `FunctionID` that represents a generic function in a particular application domain will affect all instances of that function in the application domain.</span></span>

## <a name="syntax"></a><span data-ttu-id="c0d3c-105">構文</span><span class="sxs-lookup"><span data-stu-id="c0d3c-105">Syntax</span></span>

```cpp
HRESULT SetILInstrumentedCodeMap(
    [in]  FunctionID functionId,
    [in]  BOOL       fStartJit,
    [in]  ULONG      cILMapEntries,
    [in, size_is(cILMapEntries)] COR_IL_MAP rgILMapEntries[]);
```

## <a name="parameters"></a><span data-ttu-id="c0d3c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c0d3c-106">Parameters</span></span>

`functionId`\
<span data-ttu-id="c0d3c-107">からコードマップを設定する関数の ID。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-107">[in] The ID of the function for which to set the code map.</span></span>

`fStartJit`\
<span data-ttu-id="c0d3c-108">からメソッドの呼び出し `SetILInstrumentedCodeMap` が、特定のの最初のメソッドであるかどうかを示すブール値 `FunctionID` 。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-108">[in] A Boolean value that indicates whether the call to the `SetILInstrumentedCodeMap` method is the first for a particular `FunctionID`.</span></span> <span data-ttu-id="c0d3c-109">`fStartJit`指定されたの最初の呼び出しでをに設定し、それ以降の場合はに設定し `true` `SetILInstrumentedCodeMap` `FunctionID` `false` ます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-109">Set `fStartJit` to `true` in the first call to `SetILInstrumentedCodeMap` for a given `FunctionID`, and to `false` thereafter.</span></span>

`cILMapEntries`\
<span data-ttu-id="c0d3c-110">から配列内の要素の数 `cILMapEntries` 。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-110">[in] The number of elements in the `cILMapEntries` array.</span></span>

`rgILMapEntries`\
<span data-ttu-id="c0d3c-111">からCOR_IL_MAP 構造体の配列。それぞれが MSIL オフセットを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-111">[in] An array of COR_IL_MAP structures, each of which specifies an MSIL offset.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0d3c-112">解説</span><span class="sxs-lookup"><span data-stu-id="c0d3c-112">Remarks</span></span>

<span data-ttu-id="c0d3c-113">多くの場合、プロファイラーは、メソッドのソースコード内にステートメントを挿入して、そのメソッドをインストルメント化します (たとえば、特定のソース行に到達したときに通知します)。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-113">A profiler often inserts statements within the source code of a method in order to instrument that method (for example, to notify when a given source line is reached).</span></span> <span data-ttu-id="c0d3c-114">`SetILInstrumentedCodeMap`プロファイラーが元の MSIL 命令を新しい場所にマップできるようにします。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-114">`SetILInstrumentedCodeMap` enables a profiler to map the original MSIL instructions to their new locations.</span></span> <span data-ttu-id="c0d3c-115">プロファイラーは、 [ICorProfilerInfo:: GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md)メソッドを使用して、指定されたネイティブオフセットの元の MSIL オフセットを取得できます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-115">A profiler can use the [ICorProfilerInfo::GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md) method to get the original MSIL offset for a given native offset.</span></span>

<span data-ttu-id="c0d3c-116">デバッガーは、古い各オフセットが元の変更されていない MSIL コード内の MSIL オフセットを参照し、新しい各オフセットが新しいインストルメント化されたコード内の MSIL オフセットを参照することを想定します。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-116">The debugger will assume that each old offset refers to an MSIL offset within the original, unmodified MSIL code, and that each new offset refers to the MSIL offset within the new, instrumented code.</span></span> <span data-ttu-id="c0d3c-117">マップは昇順に並べ替える必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-117">The map should be sorted in increasing order.</span></span> <span data-ttu-id="c0d3c-118">ステップ実行を正常に行うには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-118">For stepping to work properly, follow these guidelines:</span></span>

- <span data-ttu-id="c0d3c-119">インストルメント化された MSIL コードの順序を変更しません。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-119">Do not reorder instrumented MSIL code.</span></span>

- <span data-ttu-id="c0d3c-120">元の MSIL コードは削除しないでください。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-120">Do not remove the original MSIL code.</span></span>

- <span data-ttu-id="c0d3c-121">マップ内のプログラムデータベース (PDB) ファイルからのすべてのシーケンスポイントのエントリを含めます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-121">Include entries for all the sequence points from the program database (PDB) file in the map.</span></span> <span data-ttu-id="c0d3c-122">マップでは、不足しているエントリは補間されません。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-122">The map does not interpolate missing entries.</span></span> <span data-ttu-id="c0d3c-123">そのため、次のマップを指定します。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-123">So, given the following map:</span></span>

  <span data-ttu-id="c0d3c-124">(古い0、新規 0)</span><span class="sxs-lookup"><span data-stu-id="c0d3c-124">(0 old, 0 new)</span></span>

  <span data-ttu-id="c0d3c-125">(5 歳、10新規)</span><span class="sxs-lookup"><span data-stu-id="c0d3c-125">(5 old, 10 new)</span></span>

  <span data-ttu-id="c0d3c-126">(9 歳、20新規)</span><span class="sxs-lookup"><span data-stu-id="c0d3c-126">(9 old, 20 new)</span></span>

  - <span data-ttu-id="c0d3c-127">古いオフセット0、1、2、3、または4が新しいオフセット0にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-127">An old offset of 0, 1, 2, 3, or 4 will be mapped to new offset 0.</span></span>

  - <span data-ttu-id="c0d3c-128">古いオフセット5、6、7、または8は、新しいオフセット10にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-128">An old offset of 5, 6, 7, or 8 will be mapped to new offset 10.</span></span>

  - <span data-ttu-id="c0d3c-129">9以上の古いオフセットは、新しいオフセット20にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-129">An old offset of 9 or higher will be mapped to new offset 20.</span></span>

  - <span data-ttu-id="c0d3c-130">新しいオフセット0、1、2、3、4、5、6、7、8、または9が古いオフセット0にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-130">A new offset of 0, 1, 2, 3, 4, 5, 6, 7, 8, or 9 will be mapped to old offset 0.</span></span>

  - <span data-ttu-id="c0d3c-131">新しいオフセット10、11、12、13、14、15、16、17、18、19は、古いオフセット5にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-131">A new offset of 10, 11, 12, 13, 14, 15, 16, 17, 18, or 19 will be mapped to old offset 5.</span></span>

  - <span data-ttu-id="c0d3c-132">20以上の新しいオフセットは、古いオフセット9にマップされます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-132">A new offset of 20 or higher will be mapped to old offset 9.</span></span>

<span data-ttu-id="c0d3c-133">.NET Framework 3.5 およびそれ以前のバージョンでは、 `rgILMapEntries` [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc)メソッドを呼び出すことによって配列を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-133">In the .NET Framework 3.5 and previous versions, you allocate the `rgILMapEntries` array by calling the [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) method.</span></span> <span data-ttu-id="c0d3c-134">ランタイムはこのメモリの所有権を取得するため、プロファイラーは解放を試みることはできません。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-134">Because the runtime takes ownership of this memory, the profiler should not attempt to free it.</span></span>

## <a name="requirements"></a><span data-ttu-id="c0d3c-135">要件</span><span class="sxs-lookup"><span data-stu-id="c0d3c-135">Requirements</span></span>

<span data-ttu-id="c0d3c-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0d3c-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="c0d3c-137">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0d3c-137">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="c0d3c-138">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0d3c-138">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="c0d3c-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0d3c-139">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="c0d3c-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0d3c-140">See also</span></span>

- [<span data-ttu-id="c0d3c-141">ICorProfilerInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c0d3c-141">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
