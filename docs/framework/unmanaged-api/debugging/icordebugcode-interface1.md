---
title: ICorDebugCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 3736627e7f42ad9db6699c31a0a618e993eef770
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893469"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="70944-102">ICorDebugCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70944-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="70944-103">Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="70944-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="70944-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-104">Methods</span></span>  
  
|<span data-ttu-id="70944-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-105">Method</span></span>|<span data-ttu-id="70944-106">説明</span><span class="sxs-lookup"><span data-stu-id="70944-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="70944-107">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="70944-108">指定したオフセット位置にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="70944-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="70944-109">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="70944-110">この `ICorDebugCode` が表すコード セグメントの RVA (Relative Virtual Address) を取得します。</span><span class="sxs-lookup"><span data-stu-id="70944-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="70944-111">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="70944-112">指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="70944-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="70944-113">このメソッドは非推奨とされました。代わりに[ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md)を使用してください。</span><span class="sxs-lookup"><span data-stu-id="70944-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="70944-114">GetEnCRemapSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="70944-115">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="70944-115">Not implemented.</span></span>|  
|[<span data-ttu-id="70944-116">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="70944-117">この`ICorDebugCode`に関連付けられている "の関数" を取得します。</span><span class="sxs-lookup"><span data-stu-id="70944-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="70944-118">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="70944-119">MSIL オフセットからネイティブオフセットへのマッピングを表す "COR_DEBUG_IL_TO_NATIVE_MAP" インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="70944-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="70944-120">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="70944-121">この `ICorDebugCode` で表されるバイナリ コードのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="70944-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="70944-122">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="70944-123">この `ICorDebugCode` が表すコードのバージョンを識別する、1 から始まる数字を取得します。</span><span class="sxs-lookup"><span data-stu-id="70944-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="70944-124">IsIL メソッド</span><span class="sxs-lookup"><span data-stu-id="70944-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="70944-125">この `ICorDebugCode` が MSIL でコンパイルされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="70944-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70944-126">解説</span><span class="sxs-lookup"><span data-stu-id="70944-126">Remarks</span></span>  
 <span data-ttu-id="70944-127">`ICorDebugCode` は、MSIL またはネイティブ コードを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="70944-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="70944-128">MSIL コードを表す "の関数" オブジェクトは、0個または 1 `ICorDebugCode`個のオブジェクトを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="70944-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="70944-129">ネイティブコードを表す "表示関数" オブジェクトには、任意の数`ICorDebugCode`のオブジェクトを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="70944-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="70944-130">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="70944-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70944-131">必要条件</span><span class="sxs-lookup"><span data-stu-id="70944-131">Requirements</span></span>  
 <span data-ttu-id="70944-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70944-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70944-133">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="70944-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="70944-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="70944-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70944-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70944-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70944-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="70944-136">See also</span></span>

- [<span data-ttu-id="70944-137">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="70944-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="70944-138">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="70944-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
