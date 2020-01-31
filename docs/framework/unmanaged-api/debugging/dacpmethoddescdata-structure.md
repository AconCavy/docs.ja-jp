---
title: DacpMethodDescData 構造体
ms.date: 02/01/2019
api.name:
- DacpMethodDescData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpMethodDescData Structure
helpviewer.keywords:
- DacpMethodDescData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: cc54664ea8ad61005de3f3fae7407946d1c861b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793842"
---
# <a name="dacpmethoddescdata-structure"></a><span data-ttu-id="ef05b-102">DacpMethodDescData 構造体</span><span class="sxs-lookup"><span data-stu-id="ef05b-102">DacpMethodDescData Structure</span></span>

<span data-ttu-id="ef05b-103">メソッドのランタイム情報のトランスポートバッファーを定義します。</span><span class="sxs-lookup"><span data-stu-id="ef05b-103">Defines a transport buffer for a method's runtime information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ef05b-104">構文</span><span class="sxs-lookup"><span data-stu-id="ef05b-104">Syntax</span></span>

```cpp
struct DacpMethodDescData
{
    int             bHasNativeCode;
    int             bIsDynamic;
    unsigned short  wSlotNumber;
    CLRDATA_ADDRESS NativeCodeAddr;
    CLRDATA_ADDRESS data;
    CLRDATA_ADDRESS MethodDescPtr;
    CLRDATA_ADDRESS nativeCodeInfo;
    CLRDATA_ADDRESS moduleInfo;
    mdToken         MDToken;
    CLRDATA_ADDRESS payloadGC;
    CLRDATA_ADDRESS payloadGC2;
    CLRDATA_ADDRESS managedDynamicMethodObject;
    CLRDATA_ADDRESS requestedIP;
    DacpReJitData   rejitDataCurrent;
    DacpReJitData   rejitDataRequested;
    unsigned long   cJittedRejitVersions;
};
```

## <a name="members"></a><span data-ttu-id="ef05b-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ef05b-105">Members</span></span>

| <span data-ttu-id="ef05b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ef05b-106">Member</span></span>                       | <span data-ttu-id="ef05b-107">説明</span><span class="sxs-lookup"><span data-stu-id="ef05b-107">Description</span></span>                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------- |
| `bHasNativeCode`             | <span data-ttu-id="ef05b-108">メソッドの特定のインスタンス化に対してランタイムにネイティブコードがあるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ef05b-108">Indicates if the runtime has native code available for the given instantiation of the method.</span></span> |
| `bIsDynamic`                 | <span data-ttu-id="ef05b-109">軽量コード生成によってメソッドが動的に生成されるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ef05b-109">Indicates if the method is generated dynamically through lightweight code generation.</span></span>           |
| `wSlotNumber`                | <span data-ttu-id="ef05b-110">メソッドテーブル内のメソッドのスロット番号。</span><span class="sxs-lookup"><span data-stu-id="ef05b-110">The method's slot number in the method table.</span></span>                                                   |
| `NativeCodeAddr`             | <span data-ttu-id="ef05b-111">メソッドの初期ネイティブアドレス。</span><span class="sxs-lookup"><span data-stu-id="ef05b-111">The method's initial native address.</span></span>                                                            |
| `data`                       | <span data-ttu-id="ef05b-112">ランタイムによって内部的に使用されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef05b-112">Pointer to a buffer used internally by the runtime.</span></span>                                             |
| `MethodDescPtr`              | <span data-ttu-id="ef05b-113">ランタイム内の `MethodDesc` へのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef05b-113">Pointer to the `MethodDesc` in the runtime.</span></span>                                                     |
| `nativeCodeInfo`             | <span data-ttu-id="ef05b-114">メソッドを追跡するためにランタイムによって内部的に使用されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef05b-114">Pointer to a buffer used internally by the runtime to track methods.</span></span>                            |
| `moduleInfo`                 | <span data-ttu-id="ef05b-115">モジュール情報のランタイムによって内部的に使用されるバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef05b-115">Pointer to a buffer used internally by the runtime for module information.</span></span>                      |
| `MDToken`                    | <span data-ttu-id="ef05b-116">指定したメソッドに関連付けられているトークン。</span><span class="sxs-lookup"><span data-stu-id="ef05b-116">Token associated with the given method.</span></span>                                                         |
| `payloadGC`                  | <span data-ttu-id="ef05b-117">ランタイムによって内部的に使用されるガベージコレクションバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef05b-117">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `payloadGC2`                 | <span data-ttu-id="ef05b-118">ランタイムによって内部的に使用されるガベージコレクションバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ef05b-118">Pointer to a garbage collection buffer used internally by the runtime.</span></span>                          |
| `managedDynamicMethodObject` | <span data-ttu-id="ef05b-119">メソッドが動的である場合、ランタイムは情報追跡のためにこのバッファーを内部的に使用します。</span><span class="sxs-lookup"><span data-stu-id="ef05b-119">If the method is dynamic, the runtime uses this buffer internally for information tracking.</span></span>     |
| `requestedIP`                | <span data-ttu-id="ef05b-120">ネイティブコードアドレスが指定された場合に、要求ごとに構造体を設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="ef05b-120">Used to populate the structure per request when given a native code address.</span></span>                    |
| `rejitDataCurrent`           | <span data-ttu-id="ef05b-121">メソッドのインストルメント化された最新バージョンに関する情報。</span><span class="sxs-lookup"><span data-stu-id="ef05b-121">Information about the latest instrumented version of the method.</span></span>                                   |
| `rejitDataRequested`         | <span data-ttu-id="ef05b-122">要求されたネイティブアドレスの rejit 情報。</span><span class="sxs-lookup"><span data-stu-id="ef05b-122">Rejit information for the requested native address.</span></span>                                             |
| `cJittedRejitVersions`       | <span data-ttu-id="ef05b-123">メソッドがインストルメンテーションによって rejitted された回数。</span><span class="sxs-lookup"><span data-stu-id="ef05b-123">Number of times the method has been rejitted through instrumentation.</span></span>                           |

## <a name="remarks"></a><span data-ttu-id="ef05b-124">コメント</span><span class="sxs-lookup"><span data-stu-id="ef05b-124">Remarks</span></span>

<span data-ttu-id="ef05b-125">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="ef05b-125">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="ef05b-126">これを使用するには、前に示したように構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="ef05b-126">To use it, define the structure as specified above.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef05b-127">要件</span><span class="sxs-lookup"><span data-stu-id="ef05b-127">Requirements</span></span>
<span data-ttu-id="ef05b-128">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef05b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ef05b-129">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="ef05b-129">**Header:** None</span></span>  
<span data-ttu-id="ef05b-130">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="ef05b-130">**Library:** None</span></span>  
<span data-ttu-id="ef05b-131">**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ef05b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ef05b-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef05b-132">See also</span></span>

- [<span data-ttu-id="ef05b-133">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ef05b-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="ef05b-134">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="ef05b-134">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="ef05b-135">共有のデータ型</span><span class="sxs-lookup"><span data-stu-id="ef05b-135">Common Data Types</span></span>](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)
