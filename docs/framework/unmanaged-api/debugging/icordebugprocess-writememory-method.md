---
title: ICorDebugProcess::WriteMemory メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.WriteMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::WriteMemory
helpviewer_keywords:
- ICorDebugProcess::WriteMemory method [.NET Framework debugging]
- WriteMemory method [.NET Framework debugging]
ms.assetid: d5c07d86-045d-4391-893b-0bcd2959f90e
topic_type:
- apiref
ms.openlocfilehash: 0a433ccb81ef62ac92a4553a838a2c98a04fc7c1
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212816"
---
# <a name="icordebugprocesswritememory-method"></a><span data-ttu-id="1191a-102">ICorDebugProcess::WriteMemory メソッド</span><span class="sxs-lookup"><span data-stu-id="1191a-102">ICorDebugProcess::WriteMemory Method</span></span>
<span data-ttu-id="1191a-103">このプロセスのメモリ領域にデータを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="1191a-103">Writes data to an area of memory in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1191a-104">構文</span><span class="sxs-lookup"><span data-stu-id="1191a-104">Syntax</span></span>  
  
```cpp  
HRESULT WriteMemory(  
    [in]  CORDB_ADDRESS address,  
    [in]  DWORD size,  
    [in, size_is(size)] BYTE buffer[],  
    [out] SIZE_T *written);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1191a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1191a-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="1191a-106">から`CORDB_ADDRESS`データが書き込まれるメモリ領域のベースアドレスを表す値。</span><span class="sxs-lookup"><span data-stu-id="1191a-106">[in] A `CORDB_ADDRESS` value that is the base address of the memory area to which data is written.</span></span> <span data-ttu-id="1191a-107">データ転送が行われる前に、システムは、ベースアドレスを開始位置として、指定したサイズのメモリ領域が書き込み可能であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1191a-107">Before data transfer occurs, the system verifies that the memory area of the specified size, beginning at the base address, is accessible for writing.</span></span> <span data-ttu-id="1191a-108">アクセスできない場合、メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="1191a-108">If it is not accessible, the method fails.</span></span>  
  
 `size`  
 <span data-ttu-id="1191a-109">からメモリ領域に書き込まれるバイト数。</span><span class="sxs-lookup"><span data-stu-id="1191a-109">[in] The number of bytes to be written to the memory area.</span></span>  
  
 `buffer`  
 <span data-ttu-id="1191a-110">から書き込むデータを格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="1191a-110">[in] A buffer that contains data to be written.</span></span>  
  
 `written`  
 <span data-ttu-id="1191a-111">入出力このプロセスのメモリ領域に書き込まれたバイト数を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1191a-111">[out] A pointer to a variable that receives the number of bytes written to the memory area in this process.</span></span> <span data-ttu-id="1191a-112">`written`が NULL の場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="1191a-112">If `written` is NULL, this parameter is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1191a-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="1191a-113">Remarks</span></span>  
 <span data-ttu-id="1191a-114">データは、ブレークポイントの背後に自動的に書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="1191a-114">Data is automatically written behind any breakpoints.</span></span> <span data-ttu-id="1191a-115">.NET Framework バージョン2.0 では、ネイティブデバッガーは、このメソッドを使用して命令ストリームにブレークポイントを挿入することはできません。</span><span class="sxs-lookup"><span data-stu-id="1191a-115">In the .NET Framework version 2.0, native debuggers should not use this method to inject breakpoints into the instruction stream.</span></span> <span data-ttu-id="1191a-116">代わりに[ICorDebugProcess2:: SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md)を使用してください。</span><span class="sxs-lookup"><span data-stu-id="1191a-116">Use [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md) instead.</span></span>  
  
 <span data-ttu-id="1191a-117">メソッドは、 `WriteMemory` マネージコードの外部でのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1191a-117">The `WriteMemory` method should be used only outside of managed code.</span></span> <span data-ttu-id="1191a-118">不適切に使用された場合、このメソッドはランタイムを破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="1191a-118">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1191a-119">必要条件</span><span class="sxs-lookup"><span data-stu-id="1191a-119">Requirements</span></span>  
 <span data-ttu-id="1191a-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1191a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1191a-121">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1191a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1191a-122">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1191a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1191a-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1191a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
