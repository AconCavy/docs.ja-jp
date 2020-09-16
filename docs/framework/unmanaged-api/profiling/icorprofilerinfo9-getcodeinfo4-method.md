---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: ecaff179378eb417393c0a0d17d0a00d3b99e5a4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541299"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="36f7e-102">ICorProfilerInfo9:: GetCodeInfo4 メソッド</span><span class="sxs-lookup"><span data-stu-id="36f7e-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="36f7e-103">ネイティブコードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。</span><span class="sxs-lookup"><span data-stu-id="36f7e-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="36f7e-104">構文</span><span class="sxs-lookup"><span data-stu-id="36f7e-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="36f7e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36f7e-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="36f7e-106">\[) ネイティブ関数の先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="36f7e-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="36f7e-107">\[in] 配列のサイズ `codeInfos` 。</span><span class="sxs-lookup"><span data-stu-id="36f7e-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="36f7e-108">\[out] 使用可能な [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体の総数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="36f7e-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="36f7e-109">\[out] 呼び出し元が指定したバッファー。</span><span class="sxs-lookup"><span data-stu-id="36f7e-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="36f7e-110">メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。</span><span class="sxs-lookup"><span data-stu-id="36f7e-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36f7e-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="36f7e-111">Remarks</span></span>

<span data-ttu-id="36f7e-112">メソッドは、 `GetCodeInfo4` メソッドのさまざまなネイティブバージョンのコード情報を検索できる点を除いて、 [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md)に似ています。</span><span class="sxs-lookup"><span data-stu-id="36f7e-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="36f7e-113">`GetCodeInfo4` ガベージコレクションをトリガーできます。</span><span class="sxs-lookup"><span data-stu-id="36f7e-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="36f7e-114">エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="36f7e-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="36f7e-115">が返された後 `GetCodeInfo4` 、バッファーが `codeInfos` すべての [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造を格納するのに十分な大きさであったことを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="36f7e-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="36f7e-116">これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。</span><span class="sxs-lookup"><span data-stu-id="36f7e-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="36f7e-117">`cCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md)構造体のサイズで除算されたがより小さい場合は `pcCodeInfos` 、大きいバッファーを割り当て、を `codeInfos` `cCodeInfos` 新しい大きいサイズに更新して、を `GetCodeInfo4` 再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="36f7e-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="36f7e-118">別の方法として、最初に `GetCodeInfo4` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。</span><span class="sxs-lookup"><span data-stu-id="36f7e-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="36f7e-119">次に、 `codeInfos` バッファーサイズをで返された値に設定し、 `pcCodeInfos` [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) 構造体のサイズを乗算して、を `GetCodeInfo4` 再度呼び出します。</span><span class="sxs-lookup"><span data-stu-id="36f7e-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="36f7e-120">必要条件</span><span class="sxs-lookup"><span data-stu-id="36f7e-120">Requirements</span></span>

<span data-ttu-id="36f7e-121">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36f7e-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>

<span data-ttu-id="36f7e-122">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="36f7e-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="36f7e-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36f7e-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="36f7e-124">**.Net のバージョン:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36f7e-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="36f7e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="36f7e-125">See also</span></span>

- [<span data-ttu-id="36f7e-126">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36f7e-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)
