---
title: FormatFromRawValue 関数 (アンマネージ API リファレンス)
description: FormatFromRawValue 関数は、生のパフォーマンスデータを指定された形式に変換します。
ms.date: 11/21/2017
api_name:
- FormatFromRawValue
api_location:
- PerfCounter.dll
api_type:
- DLLExport
f1_keywords:
- FormatFromRawValue
helpviewer_keywords:
- FormatFromRawValue function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e7f3e4eef4a7e378529c2097a8fe1a753a98c961
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553715"
---
# <a name="formatfromrawvalue-function"></a><span data-ttu-id="f070c-103">FormatFromRawValue 関数</span><span class="sxs-lookup"><span data-stu-id="f070c-103">FormatFromRawValue function</span></span>
<span data-ttu-id="f070c-104">1 つの生のパフォーマンス データ値が指定した形式に変換されます。この形式変換が時間ベースである場合は、2 つの生のパフォーマンス データ値が変換されます。</span><span class="sxs-lookup"><span data-stu-id="f070c-104">Converts one raw performance data value to the specified format, or two raw performance data values if the format conversion is time-based.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f070c-105">構文</span><span class="sxs-lookup"><span data-stu-id="f070c-105">Syntax</span></span>

```cpp
int FormatFromRawValue (
   [in] uint                    dwCounterType,
   [in] uint                    dwFormat,
   [in] long*                   pTimeBase,
   [in] PDH_RAW_COUNTER*        pRawValue1,
   [in] PDH_RAW_COUNTER*        pRawValue2,
   [out] PDH_FMT_COUNTERVALUE*  pFmtValue
);
```

## <a name="parameters"></a><span data-ttu-id="f070c-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f070c-106">Parameters</span></span>

`dwCounterType`\
<span data-ttu-id="f070c-107">からカウンターの種類。</span><span class="sxs-lookup"><span data-stu-id="f070c-107">[in] The counter type.</span></span> <span data-ttu-id="f070c-108">カウンターの種類の一覧については、「 [WMI パフォーマンスカウンターの種類](/windows/desktop/WmiSdk/wmi-performance-counter-types)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f070c-108">For a list of counter types, see [WMI Performance Counter Types](/windows/desktop/WmiSdk/wmi-performance-counter-types).</span></span> <span data-ttu-id="f070c-109">`dwCounterType` には、およびを除く任意の種類のカウンターを指定でき `PERF_LARGE_RAW_FRACTION` `PERF_LARGE_RAW_BASE` ます。</span><span class="sxs-lookup"><span data-stu-id="f070c-109">`dwCounterType` can be any counter type except for `PERF_LARGE_RAW_FRACTION` and `PERF_LARGE_RAW_BASE`.</span></span>

`dwFormat`\
<span data-ttu-id="f070c-110">から生のパフォーマンスデータを変換する形式。</span><span class="sxs-lookup"><span data-stu-id="f070c-110">[in] The format to which to convert the raw performance data.</span></span> <span data-ttu-id="f070c-111">次のいずれかの値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="f070c-111">It can be one of the following values:</span></span>

|<span data-ttu-id="f070c-112">一定</span><span class="sxs-lookup"><span data-stu-id="f070c-112">Constant</span></span>  |<span data-ttu-id="f070c-113">値</span><span class="sxs-lookup"><span data-stu-id="f070c-113">Value</span></span>  |<span data-ttu-id="f070c-114">説明</span><span class="sxs-lookup"><span data-stu-id="f070c-114">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_DOUBLE` |<span data-ttu-id="f070c-115">0x00000200</span><span class="sxs-lookup"><span data-stu-id="f070c-115">0x00000200</span></span> | <span data-ttu-id="f070c-116">計算された値を倍精度浮動小数点値として返します。</span><span class="sxs-lookup"><span data-stu-id="f070c-116">Return the calculated value as a double-precision floating point value.</span></span> |
| `PDH_FMT_LARGE` | <span data-ttu-id="f070c-117">0x00000400</span><span class="sxs-lookup"><span data-stu-id="f070c-117">0x00000400</span></span> | <span data-ttu-id="f070c-118">計算された値を64ビット整数として返します。</span><span class="sxs-lookup"><span data-stu-id="f070c-118">Return the calculated value as a 64-bit integer.</span></span> |
| `PDH_FMT_LONG` | <span data-ttu-id="f070c-119">0x00000100</span><span class="sxs-lookup"><span data-stu-id="f070c-119">0x00000100</span></span> | <span data-ttu-id="f070c-120">計算された値を32ビット整数として返します。</span><span class="sxs-lookup"><span data-stu-id="f070c-120">Return the calculated value as a 32-bit integer.</span></span> |

<span data-ttu-id="f070c-121">前の値の1つは、次のいずれかのスケーリングフラグと共に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f070c-121">One of the previous values can be ORed with one of the following scaling flags:</span></span>

|<span data-ttu-id="f070c-122">一定</span><span class="sxs-lookup"><span data-stu-id="f070c-122">Constant</span></span>  |<span data-ttu-id="f070c-123">値</span><span class="sxs-lookup"><span data-stu-id="f070c-123">Value</span></span>  |<span data-ttu-id="f070c-124">説明</span><span class="sxs-lookup"><span data-stu-id="f070c-124">Description</span></span> |
|---------|---------|---------|
| `PDH_FMT_NOSCALE` | <span data-ttu-id="f070c-125">0x00001000</span><span class="sxs-lookup"><span data-stu-id="f070c-125">0x00001000</span></span> | <span data-ttu-id="f070c-126">カウンターのスケールファクターは適用しないでください。</span><span class="sxs-lookup"><span data-stu-id="f070c-126">Do not apply the counter's scaling factors.</span></span> |
| `PDH_FMT_1000` | <span data-ttu-id="f070c-127">0x00002000</span><span class="sxs-lookup"><span data-stu-id="f070c-127">0x00002000</span></span> | <span data-ttu-id="f070c-128">最終的な値を1000で乗算します。</span><span class="sxs-lookup"><span data-stu-id="f070c-128">Multiply the final value by 1,000.</span></span> |

`pTimeBase`\
<span data-ttu-id="f070c-129">から形式変換に必要な場合は、タイムベースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f070c-129">[in] A pointer to the time base, if necessary for the format conversion.</span></span> <span data-ttu-id="f070c-130">形式変換に時間ベース情報が不要な場合、このパラメーターの値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="f070c-130">If time base information is not necessary for the format conversion, the value of this parameter is ignored.</span></span>

`pRawValue1`\
<span data-ttu-id="f070c-131">から [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 生のパフォーマンス値を表す構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f070c-131">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a raw performance value.</span></span>

`pRawValue2`\
<span data-ttu-id="f070c-132">から [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) 2 番目の生のパフォーマンス値を表す構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f070c-132">[in] A pointer to a [`PDH_RAW_COUNTER`](/windows/win32/api/pdh/ns-pdh-pdh_raw_counter) structure that represents a second raw performance value.</span></span> <span data-ttu-id="f070c-133">2番目の生のパフォーマンス値が不要な場合、このパラメーターはにする必要があり `null` ます。</span><span class="sxs-lookup"><span data-stu-id="f070c-133">If a second raw performance value is not necessary, this parameter should be `null`.</span></span>

`pFmtValue`\
<span data-ttu-id="f070c-134">入出力書式設定された [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) パフォーマンス値を受け取る構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f070c-134">[out] A pointer to a [`PDH_FMT_COUNTERVALUE`](/windows/win32/api/pdh/ns-pdh-pdh_fmt_countervalue) structure that receives the formatted performance value.</span></span>

## <a name="return-value"></a><span data-ttu-id="f070c-135">戻り値</span><span class="sxs-lookup"><span data-stu-id="f070c-135">Return value</span></span>

<span data-ttu-id="f070c-136">この関数によって返される値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="f070c-136">The following values are returned by this function:</span></span>

|<span data-ttu-id="f070c-137">一定</span><span class="sxs-lookup"><span data-stu-id="f070c-137">Constant</span></span>  |<span data-ttu-id="f070c-138">値</span><span class="sxs-lookup"><span data-stu-id="f070c-138">Value</span></span>  |<span data-ttu-id="f070c-139">説明</span><span class="sxs-lookup"><span data-stu-id="f070c-139">Description</span></span>  |
|---------|---------|---------|
| `ERROR_SUCCESS` | <span data-ttu-id="f070c-140">0</span><span class="sxs-lookup"><span data-stu-id="f070c-140">0</span></span> | <span data-ttu-id="f070c-141">関数の呼び出しは成功しました。</span><span class="sxs-lookup"><span data-stu-id="f070c-141">The function call is successful.</span></span> |
| `PDH_INVALID_ARGUMENT` | <span data-ttu-id="f070c-142">0xC0000BBD</span><span class="sxs-lookup"><span data-stu-id="f070c-142">0xC0000BBD</span></span> | <span data-ttu-id="f070c-143">必須の引数が指定されていないか、正しくありません。</span><span class="sxs-lookup"><span data-stu-id="f070c-143">A required argument is missing or incorrect.</span></span> |
| `PDH_INVALID_HANDLE` | <span data-ttu-id="f070c-144">0xC0000BBC</span><span class="sxs-lookup"><span data-stu-id="f070c-144">0xC0000BBC</span></span> | <span data-ttu-id="f070c-145">ハンドルは、有効な PDH オブジェクトではありません。</span><span class="sxs-lookup"><span data-stu-id="f070c-145">The handle is not a valid PDH object.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f070c-146">Remarks</span><span class="sxs-lookup"><span data-stu-id="f070c-146">Remarks</span></span>

<span data-ttu-id="f070c-147">この関数は、 [FormatFromRawValue](/previous-versions/ms231047(v=vs.85)) 関数の呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="f070c-147">This function wraps a call to the [FormatFromRawValue](/previous-versions/ms231047(v=vs.85)) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f070c-148">必要条件</span><span class="sxs-lookup"><span data-stu-id="f070c-148">Requirements</span></span>

 <span data-ttu-id="f070c-149">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f070c-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="f070c-150">**ライブラリ:** PerfCounter.dll</span><span class="sxs-lookup"><span data-stu-id="f070c-150">**Library:** PerfCounter.dll</span></span>

 <span data-ttu-id="f070c-151">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f070c-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f070c-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="f070c-152">See also</span></span>

- [<span data-ttu-id="f070c-153">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f070c-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
