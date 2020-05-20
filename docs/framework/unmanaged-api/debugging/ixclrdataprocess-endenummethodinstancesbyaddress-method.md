---
title: 'IXCLRDataProcess:: EndEnumMethodInstancesByAddress メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 5960d08ccfc09010a20d28a22c2e2f3f5b339c7d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420826"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="610cc-102">IXCLRDataProcess:: EndEnumMethodInstancesByAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="610cc-102">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="610cc-103">インスタンスの列挙中に使用される内部反復子によって使用されるリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="610cc-103">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="610cc-104">構文</span><span class="sxs-lookup"><span data-stu-id="610cc-104">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="610cc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="610cc-105">Parameters</span></span>

`handle`\
<span data-ttu-id="610cc-106">入出力メソッドインスタンスを列挙するハンドル。</span><span class="sxs-lookup"><span data-stu-id="610cc-106">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="610cc-107">解説</span><span class="sxs-lookup"><span data-stu-id="610cc-107">Remarks</span></span>

<span data-ttu-id="610cc-108">指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの30スロットに対応します。</span><span class="sxs-lookup"><span data-stu-id="610cc-108">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="610cc-109">要件</span><span class="sxs-lookup"><span data-stu-id="610cc-109">Requirements</span></span>

<span data-ttu-id="610cc-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="610cc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="610cc-111">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="610cc-111">**Header:** None</span></span>  
<span data-ttu-id="610cc-112">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="610cc-112">**Library:** None</span></span>  
<span data-ttu-id="610cc-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="610cc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="610cc-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="610cc-114">See also</span></span>

- [<span data-ttu-id="610cc-115">CLRDataSourceType 列挙型</span><span class="sxs-lookup"><span data-stu-id="610cc-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="610cc-116">デバッグ</span><span class="sxs-lookup"><span data-stu-id="610cc-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="610cc-117">IXCLRDataProcess インターフェイス</span><span class="sxs-lookup"><span data-stu-id="610cc-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
