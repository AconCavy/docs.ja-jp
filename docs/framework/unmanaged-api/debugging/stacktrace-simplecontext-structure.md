---
title: StackTrace_SimpleContext 構造体
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
ms.openlocfilehash: c81a5787eb06971e3d52aff5d1c1154a72564daf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790330"
---
# <a name="stacktrace_simplecontext-structure"></a><span data-ttu-id="3747d-102">StackTrace_SimpleContext 構造体</span><span class="sxs-lookup"><span data-stu-id="3747d-102">StackTrace_SimpleContext Structure</span></span>
<span data-ttu-id="3747d-103">完全な `CONTEXT` 構造の代わりに使用できる単純なコンテキストを提供します。</span><span class="sxs-lookup"><span data-stu-id="3747d-103">Provides a simple context that can be used in place of a full `CONTEXT` structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3747d-104">構文</span><span class="sxs-lookup"><span data-stu-id="3747d-104">Syntax</span></span>  
  
```cpp  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a><span data-ttu-id="3747d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="3747d-105">Members</span></span>  
  
|<span data-ttu-id="3747d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="3747d-106">Member</span></span>|<span data-ttu-id="3747d-107">説明</span><span class="sxs-lookup"><span data-stu-id="3747d-107">Description</span></span>|  
|------------|-----------------|  
|`StackOffset`|<span data-ttu-id="3747d-108">スタックポインター、または x86 プラットフォームの enter スタックポインター (ESP)。</span><span class="sxs-lookup"><span data-stu-id="3747d-108">The stack pointer, or the enter stack pointer (ESP) on x86 platforms.</span></span>|  
|`FrameOffset`|<span data-ttu-id="3747d-109">フレームオフセット、または x86 プラットフォームでの EBP レジスタ。</span><span class="sxs-lookup"><span data-stu-id="3747d-109">The frame offset, or the EBP register on x86 platforms.</span></span>|  
|`InstructionOffset`|<span data-ttu-id="3747d-110">命令ポインター、または x86 プラットフォームの enter 命令ポインター (EIP)。</span><span class="sxs-lookup"><span data-stu-id="3747d-110">The instruction pointer, or the enter instruction pointer (EIP) on x86 platforms.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3747d-111">コメント</span><span class="sxs-lookup"><span data-stu-id="3747d-111">Remarks</span></span>  
 <span data-ttu-id="3747d-112">通常、スタックトレース関数はアドレス、フレームオフセット、およびスタックアドレスだけを返す必要があるため、必要に応じて、大きな `CONTEXT` 構造の代わりに `SimpleContext` 構造を使用できます。</span><span class="sxs-lookup"><span data-stu-id="3747d-112">Because stack trace functions typically need to return only the address, frame offset, and stack address, you can optionally use the `SimpleContext` structure instead of a large `CONTEXT` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3747d-113">要件</span><span class="sxs-lookup"><span data-stu-id="3747d-113">Requirements</span></span>  
 <span data-ttu-id="3747d-114">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3747d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3747d-115">**ヘッダー:** SOS_Stacktrace</span><span class="sxs-lookup"><span data-stu-id="3747d-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="3747d-116">**.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3747d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3747d-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3747d-117">See also</span></span>

- [<span data-ttu-id="3747d-118">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="3747d-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3747d-119">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3747d-119">Debugging</span></span>](index.md)
