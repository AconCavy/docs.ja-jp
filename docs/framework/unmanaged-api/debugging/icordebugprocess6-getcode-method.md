---
title: ICorDebugProcess6::GetCode メソッド
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 1588728f486ffb3db583439de05aff34e3dc59f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792267"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="4fe88-102">ICorDebugProcess6::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="4fe88-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="4fe88-103">特定のコード アドレスで、マネージド コードに関する情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="4fe88-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe88-104">構文</span><span class="sxs-lookup"><span data-stu-id="4fe88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4fe88-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fe88-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="4fe88-106">からマネージコードセグメントの開始アドレスを指定する[CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)値。</span><span class="sxs-lookup"><span data-stu-id="4fe88-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="4fe88-107">入出力マネージコードのセグメントを表す "" コード "オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="4fe88-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4fe88-108">コメント</span><span class="sxs-lookup"><span data-stu-id="4fe88-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4fe88-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="4fe88-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fe88-110">要件</span><span class="sxs-lookup"><span data-stu-id="4fe88-110">Requirements</span></span>  
 <span data-ttu-id="4fe88-111">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fe88-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe88-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4fe88-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4fe88-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4fe88-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4fe88-114">**.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe88-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe88-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fe88-115">See also</span></span>

- [<span data-ttu-id="4fe88-116">ICorDebugProcess6 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fe88-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="4fe88-117">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4fe88-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
