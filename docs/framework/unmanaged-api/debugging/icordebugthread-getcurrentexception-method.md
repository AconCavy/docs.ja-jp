---
title: ICorDebugThread::GetCurrentException メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: 3a4da6f958407c0b704ffb7372a77b7f022fc824
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379767"
---
# <a name="icordebugthreadgetcurrentexception-method"></a><span data-ttu-id="28d57-102">ICorDebugThread::GetCurrentException メソッド</span><span class="sxs-lookup"><span data-stu-id="28d57-102">ICorDebugThread::GetCurrentException Method</span></span>
<span data-ttu-id="28d57-103">現在マネージコードによってスローされている例外を表す、ICorDebugValue オブジェクトへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="28d57-103">Gets an interface pointer to an ICorDebugValue object that represents an exception that is currently being thrown by managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28d57-104">構文</span><span class="sxs-lookup"><span data-stu-id="28d57-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28d57-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="28d57-105">Parameters</span></span>  
 `ppExceptionObject`  
 <span data-ttu-id="28d57-106">入出力`ICorDebugValue`現在マネージコードによってスローされている例外を表すオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="28d57-106">[out] A pointer to the address of an `ICorDebugValue` object that represents the exception that is currently being thrown by managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28d57-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="28d57-107">Remarks</span></span>  
 <span data-ttu-id="28d57-108">例外オブジェクトは、ブロックの末尾まで例外がスローされた時点から存在し `catch` ます。</span><span class="sxs-lookup"><span data-stu-id="28d57-108">The exception object will exist from the time the exception is thrown until the end of the `catch` block.</span></span> <span data-ttu-id="28d57-109">関数の評価は、テキストの評価メソッドによって実行され、セットアップ時に例外オブジェクトをクリアし、完了時に復元します。</span><span class="sxs-lookup"><span data-stu-id="28d57-109">A function evaluation, which is performed by the ICorDebugEval methods, will clear out the exception object on setup and restore it on completion.</span></span>  
  
 <span data-ttu-id="28d57-110">例外は入れ子にすることができます (たとえば、フィルターまたは関数評価で例外がスローされた場合)。そのため、1つのスレッドで複数の未処理の例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28d57-110">Exceptions can be nested (for example, if an exception is thrown in a filter or in a function evaluation), so there may be multiple outstanding exceptions on a single thread.</span></span> <span data-ttu-id="28d57-111">`GetCurrentException`最新の例外を返します。</span><span class="sxs-lookup"><span data-stu-id="28d57-111">`GetCurrentException` returns the most current exception.</span></span>  
  
 <span data-ttu-id="28d57-112">例外オブジェクトと型は、例外が発生したときに変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="28d57-112">The exception object and type may change throughout the life of the exception.</span></span> <span data-ttu-id="28d57-113">たとえば、型 x の例外がスローされた後、共通言語ランタイム (CLR) がメモリ不足になり、メモリ不足の例外に昇格することがあります。</span><span class="sxs-lookup"><span data-stu-id="28d57-113">For example, after an exception of type x is thrown, the common language runtime (CLR) may run out of memory and promote it to an out-of-memory exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28d57-114">必要条件</span><span class="sxs-lookup"><span data-stu-id="28d57-114">Requirements</span></span>  
 <span data-ttu-id="28d57-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28d57-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d57-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28d57-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28d57-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28d57-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28d57-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d57-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
