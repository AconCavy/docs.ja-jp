---
title: ICorDebugDataTarget::GetPlatform メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
ms.openlocfilehash: 3654c94975d16e35d5c3d8e762730d17509a2c6d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788875"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="80b61-102">ICorDebugDataTarget::GetPlatform メソッド</span><span class="sxs-lookup"><span data-stu-id="80b61-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="80b61-103">ターゲットプロセスが実行されているプラットフォーム (プロセッサアーキテクチャやオペレーティングシステムなど) に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="80b61-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80b61-104">構文</span><span class="sxs-lookup"><span data-stu-id="80b61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80b61-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="80b61-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="80b61-106">入出力ターゲットプラットフォームを記述する[Cordebugplatformenum](cordebugplatform-enumeration.md)列挙体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="80b61-106">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80b61-107">コメント</span><span class="sxs-lookup"><span data-stu-id="80b61-107">Remarks</span></span>  
 <span data-ttu-id="80b61-108">`CorDebugPlatformEnum` 列挙型の戻り値は、ポインターのサイズ、アドレス空間のレイアウト、レジスタセット、命令形式、コンテキストレイアウト、呼び出し規約など、ターゲットプロセスの詳細を確認するために[ICorDebug](icordebug-interface.md)インターフェイスによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="80b61-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="80b61-109">`pTargetPlatform` 値は、使用されている実際のハードウェアを指定する代わりに、ターゲットに対してエミュレートされるプラットフォームを参照できます。</span><span class="sxs-lookup"><span data-stu-id="80b61-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="80b61-110">たとえば、64-bit エディションの Windows オペレーティングシステムで Windows on Windows (WOW) 環境で実行されているプロセスでは、 [Cordebugplatformenum](cordebugplatform-enumeration.md)列挙型の `CORDB_PLATFORM_WINDOWS_X86` 値を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80b61-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="80b61-111">このメソッドは成功する必要があります。</span><span class="sxs-lookup"><span data-stu-id="80b61-111">This method must succeed.</span></span> <span data-ttu-id="80b61-112">失敗した場合、ターゲットプラットフォームは使用できません。</span><span class="sxs-lookup"><span data-stu-id="80b61-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="80b61-113">メソッドは、次の理由により失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="80b61-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="80b61-114">ターゲットに対してエミュレートされるプラットフォームは使用できません。</span><span class="sxs-lookup"><span data-stu-id="80b61-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="80b61-115">ターゲットプラットフォームの実際のハードウェアは使用できません。</span><span class="sxs-lookup"><span data-stu-id="80b61-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80b61-116">要件</span><span class="sxs-lookup"><span data-stu-id="80b61-116">Requirements</span></span>  
 <span data-ttu-id="80b61-117">**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="80b61-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80b61-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="80b61-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80b61-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="80b61-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80b61-120">**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80b61-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80b61-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="80b61-121">See also</span></span>

- [<span data-ttu-id="80b61-122">ICorDebugDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80b61-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="80b61-123">デバッグ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="80b61-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="80b61-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="80b61-124">Debugging</span></span>](index.md)
