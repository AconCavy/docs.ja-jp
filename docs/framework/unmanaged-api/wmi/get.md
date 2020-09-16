---
title: Get 関数 (アンマネージ API リファレンス)
description: Get 関数は、指定されたプロパティ値を取得します。
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 7cc0c285f79b2791863fce251e4683aa7b55341b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553689"
---
# <a name="get-function"></a><span data-ttu-id="a4656-103">Get 関数</span><span class="sxs-lookup"><span data-stu-id="a4656-103">Get function</span></span>

<span data-ttu-id="a4656-104">指定されたプロパティ値が存在する場合は、その値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a4656-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a4656-105">構文</span><span class="sxs-lookup"><span data-stu-id="a4656-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="a4656-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a4656-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a4656-107">からこのパラメーターは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="a4656-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a4656-108">から [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a4656-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="a4656-109">からプロパティの名前。</span><span class="sxs-lookup"><span data-stu-id="a4656-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="a4656-110">[in] 予約されています。</span><span class="sxs-lookup"><span data-stu-id="a4656-110">[in] Reserved.</span></span> <span data-ttu-id="a4656-111">このパラメーターには0を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4656-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="a4656-112">入出力関数が正常に返された場合、はプロパティの値を格納し `wszName` ます。</span><span class="sxs-lookup"><span data-stu-id="a4656-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="a4656-113">引数には、 `pval` 修飾子の正しい型と値が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="a4656-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="a4656-114">入出力関数が正常に返された場合、はプロパティの型を示す [CIM 型の定数](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) を格納します。</span><span class="sxs-lookup"><span data-stu-id="a4656-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="a4656-115">また、値もにすることができ `null` ます。</span><span class="sxs-lookup"><span data-stu-id="a4656-115">Its value can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="a4656-116">入出力関数が正常に返された場合、はプロパティの配信元に関する情報を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="a4656-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="a4656-117">この値には `null` 、 *WbemCli* ヘッダーファイルで定義されている、次のいずれかの WBEM_FLAVOR_TYPE 定数を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a4656-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span>

|<span data-ttu-id="a4656-118">一定</span><span class="sxs-lookup"><span data-stu-id="a4656-118">Constant</span></span>  |<span data-ttu-id="a4656-119">値</span><span class="sxs-lookup"><span data-stu-id="a4656-119">Value</span></span>  |<span data-ttu-id="a4656-120">説明</span><span class="sxs-lookup"><span data-stu-id="a4656-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="a4656-121">0x40</span><span class="sxs-lookup"><span data-stu-id="a4656-121">0x40</span></span> | <span data-ttu-id="a4656-122">プロパティは、標準のシステムプロパティです。</span><span class="sxs-lookup"><span data-stu-id="a4656-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="a4656-123">0x20</span><span class="sxs-lookup"><span data-stu-id="a4656-123">0x20</span></span> | <span data-ttu-id="a4656-124">クラスの場合: プロパティは親クラスから継承されます。</span><span class="sxs-lookup"><span data-stu-id="a4656-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="a4656-125">インスタンスの場合: 親クラスから継承されたプロパティは、インスタンスによって変更されていません。</span><span class="sxs-lookup"><span data-stu-id="a4656-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="a4656-126">0</span><span class="sxs-lookup"><span data-stu-id="a4656-126">0</span></span> | <span data-ttu-id="a4656-127">クラスの場合: プロパティは派生クラスに属します。</span><span class="sxs-lookup"><span data-stu-id="a4656-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="a4656-128">インスタンスの場合: プロパティは、インスタンスによって変更されます。つまり、値が指定されたか、または修飾子が追加または変更されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="a4656-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="a4656-129">戻り値</span><span class="sxs-lookup"><span data-stu-id="a4656-129">Return value</span></span>

<span data-ttu-id="a4656-130">この関数によって返される次の値は、 *WbemCli* ヘッダーファイルで定義されています。また、コード内で定数として定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4656-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a4656-131">一定</span><span class="sxs-lookup"><span data-stu-id="a4656-131">Constant</span></span>  |<span data-ttu-id="a4656-132">値</span><span class="sxs-lookup"><span data-stu-id="a4656-132">Value</span></span>  |<span data-ttu-id="a4656-133">説明</span><span class="sxs-lookup"><span data-stu-id="a4656-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a4656-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a4656-134">0x80041001</span></span> | <span data-ttu-id="a4656-135">一般的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="a4656-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a4656-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a4656-136">0x80041008</span></span> | <span data-ttu-id="a4656-137">1つ以上のパラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="a4656-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a4656-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a4656-138">0x80041002</span></span> | <span data-ttu-id="a4656-139">指定されたプロパティが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="a4656-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a4656-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a4656-140">0x80041006</span></span> | <span data-ttu-id="a4656-141">メモリ不足のため、操作を完了できません。</span><span class="sxs-lookup"><span data-stu-id="a4656-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a4656-142">0</span><span class="sxs-lookup"><span data-stu-id="a4656-142">0</span></span> | <span data-ttu-id="a4656-143">関数の呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="a4656-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a4656-144">Remarks</span><span class="sxs-lookup"><span data-stu-id="a4656-144">Remarks</span></span>

<span data-ttu-id="a4656-145">この関数は、 [IWbemClassObject:: Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) メソッドの呼び出しをラップします。</span><span class="sxs-lookup"><span data-stu-id="a4656-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="a4656-146">関数は、 `Get` システムプロパティも返すことができます。</span><span class="sxs-lookup"><span data-stu-id="a4656-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="a4656-147">この `pVal` 引数には、修飾子と COM [VariantInit](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) 関数の正しい型と値が割り当てられています。</span><span class="sxs-lookup"><span data-stu-id="a4656-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="a4656-148">必要条件</span><span class="sxs-lookup"><span data-stu-id="a4656-148">Requirements</span></span>

 <span data-ttu-id="a4656-149">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4656-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="a4656-150">**ヘッダー:** WMINet_Utils .idl</span><span class="sxs-lookup"><span data-stu-id="a4656-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="a4656-151">**.NET Framework のバージョン:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a4656-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a4656-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4656-152">See also</span></span>

- [<span data-ttu-id="a4656-153">WMI およびパフォーマンス カウンター (アンマネージド API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a4656-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
