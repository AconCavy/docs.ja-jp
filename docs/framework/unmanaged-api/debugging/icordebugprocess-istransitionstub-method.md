---
title: ICorDebugProcess::IsTransitionStub メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: ab2121605f974fdf3f9053214a4d29d8b0dd72db
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/12/2020
ms.locfileid: "83211148"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="58910-102">ICorDebugProcess::IsTransitionStub メソッド</span><span class="sxs-lookup"><span data-stu-id="58910-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="58910-103">アドレスが、マネージコードへの遷移を発生させるスタブ内にあるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="58910-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58910-104">構文</span><span class="sxs-lookup"><span data-stu-id="58910-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58910-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="58910-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="58910-106">から`CORDB_ADDRESS`対象のアドレスを示す値です。</span><span class="sxs-lookup"><span data-stu-id="58910-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="58910-107">入出力`true`指定されたアドレスが、マネージコードへの遷移を発生させるスタブ内にある場合は、それ以外の場合 `pbTransitionStub` はとなるブール値へのポインター。 `false`</span><span class="sxs-lookup"><span data-stu-id="58910-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58910-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="58910-108">Remarks</span></span>  
 <span data-ttu-id="58910-109">`IsTransitionStub`アンマネージステッピングコードでは、メソッドを使用して、管理対象のステッパにステップ実行コントロールをいつ返すかを決定できます。</span><span class="sxs-lookup"><span data-stu-id="58910-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="58910-110">ポータブル実行可能 (PE) ファイルの情報を参照して、遷移スタブを識別することもできます。</span><span class="sxs-lookup"><span data-stu-id="58910-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58910-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="58910-111">Requirements</span></span>  
 <span data-ttu-id="58910-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58910-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58910-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58910-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58910-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58910-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58910-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58910-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
