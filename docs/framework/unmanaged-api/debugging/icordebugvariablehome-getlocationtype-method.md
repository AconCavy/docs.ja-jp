---
title: 'いい変数 Home:: GetLocationType メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 8874deede8b46b93df0e298fb3970fa153b51415
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396570"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="1b278-102">いい変数 Home:: GetLocationType メソッド</span><span class="sxs-lookup"><span data-stu-id="1b278-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="1b278-103">変数のネイティブな場所の型を取得します。</span><span class="sxs-lookup"><span data-stu-id="1b278-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b278-104">構文</span><span class="sxs-lookup"><span data-stu-id="1b278-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1b278-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1b278-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="1b278-106">入出力変数のネイティブな場所の型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1b278-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="1b278-107">詳細については、 [VariableLocationType](variablelocationtype-enumeration.md)列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b278-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b278-108">要件</span><span class="sxs-lookup"><span data-stu-id="1b278-108">Requirements</span></span>  
 <span data-ttu-id="1b278-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1b278-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b278-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b278-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b278-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b278-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b278-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b278-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b278-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1b278-113">See also</span></span>

- [<span data-ttu-id="1b278-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1b278-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="1b278-115">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="1b278-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
