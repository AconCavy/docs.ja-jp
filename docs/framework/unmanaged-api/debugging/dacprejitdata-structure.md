---
title: DacpReJitData 構造体
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 4436ece72b0a6a405fc41cba5413093fc42ce750
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860779"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="88561-102">DacpReJitData 構造体</span><span class="sxs-lookup"><span data-stu-id="88561-102">DacpReJitData Structure</span></span>

<span data-ttu-id="88561-103">プロファイラーによってインストルメント化された特定のメソッドに関する基本情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="88561-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="88561-104">構文</span><span class="sxs-lookup"><span data-stu-id="88561-104">Syntax</span></span>

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="88561-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="88561-105">Members</span></span>

| <span data-ttu-id="88561-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="88561-106">Member</span></span>           | <span data-ttu-id="88561-107">説明</span><span class="sxs-lookup"><span data-stu-id="88561-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="88561-108">メソッドの ReJit リビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="88561-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="88561-109">指定されたバージョンのメソッドの ReJit インストルメンテーションの現在の状態を示すフラグ。</span><span class="sxs-lookup"><span data-stu-id="88561-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="88561-110">メソッドの rejitted 実装のベースアドレス。</span><span class="sxs-lookup"><span data-stu-id="88561-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="88561-111">解説</span><span class="sxs-lookup"><span data-stu-id="88561-111">Remarks</span></span>

<span data-ttu-id="88561-112">この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。</span><span class="sxs-lookup"><span data-stu-id="88561-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="88561-113">これを使用するには、前に示したように構造体を定義します。</span><span class="sxs-lookup"><span data-stu-id="88561-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="88561-114">Microsoft コンパイラを使用してい`ms_struct`ない場合は、パッキングを使用して構造体を定義する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="88561-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="88561-115">必要条件</span><span class="sxs-lookup"><span data-stu-id="88561-115">Requirements</span></span>
<span data-ttu-id="88561-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="88561-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="88561-117">**ヘッダー:** 存在</span><span class="sxs-lookup"><span data-stu-id="88561-117">**Header:** None</span></span>  
<span data-ttu-id="88561-118">**ライブラリ:** 存在</span><span class="sxs-lookup"><span data-stu-id="88561-118">**Library:** None</span></span>  
<span data-ttu-id="88561-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="88561-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="88561-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="88561-120">See also</span></span>

- [<span data-ttu-id="88561-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="88561-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="88561-122">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="88561-122">Debugging Structures</span></span>](debugging-structures.md)
