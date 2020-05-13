---
title: ICorDebugLoadedModule インターフェイス
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: d9b8245d8c37867971aa48ed3befb9cf22bd5b04
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210164"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="ea66b-102">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea66b-102">ICorDebugLoadedModule Interface</span></span>
<span data-ttu-id="ea66b-103">読み込まれたモジュールについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ea66b-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea66b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ea66b-104">Methods</span></span>  
  
|<span data-ttu-id="ea66b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ea66b-105">Method</span></span>|<span data-ttu-id="ea66b-106">説明</span><span class="sxs-lookup"><span data-stu-id="ea66b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea66b-107">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="ea66b-107">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="ea66b-108">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ea66b-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="ea66b-109">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="ea66b-109">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="ea66b-110">読み込まれたモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea66b-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="ea66b-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="ea66b-111">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="ea66b-112">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ea66b-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea66b-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="ea66b-113">Remarks</span></span>  
 <span data-ttu-id="ea66b-114">`ICorDebugLoadedModule` インターフェイスはデバッガーによって実装され、CLR デバッグ インターフェイスが、デバッガーから読み込まれたモジュールに関する情報を取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="ea66b-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea66b-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="ea66b-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ea66b-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="ea66b-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea66b-117">必要条件</span><span class="sxs-lookup"><span data-stu-id="ea66b-117">Requirements</span></span>  
 <span data-ttu-id="ea66b-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea66b-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea66b-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ea66b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ea66b-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea66b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea66b-121">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea66b-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea66b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea66b-122">See also</span></span>

- [<span data-ttu-id="ea66b-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ea66b-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ea66b-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ea66b-124">Debugging</span></span>](index.md)
