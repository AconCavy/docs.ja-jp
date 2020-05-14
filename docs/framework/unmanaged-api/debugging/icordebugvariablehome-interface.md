---
title: ICorDebugVariableHome インターフェイス
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: caf6a24207be98be9afb10be2bd027b51405fa3b
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396545"
---
# <a name="icordebugvariablehome-interface"></a><span data-ttu-id="2e677-102">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e677-102">ICorDebugVariableHome Interface</span></span>
<span data-ttu-id="2e677-103">関数のローカル変数または引数を表します。</span><span class="sxs-lookup"><span data-stu-id="2e677-103">Represents a local variable or argument of a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e677-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-104">Methods</span></span>  
  
|<span data-ttu-id="2e677-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-105">Method</span></span>|<span data-ttu-id="2e677-106">説明</span><span class="sxs-lookup"><span data-stu-id="2e677-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e677-107">GetArgumentIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-107">GetArgumentIndex Method</span></span>](icordebugvariablehome-getargumentindex-method.md)|<span data-ttu-id="2e677-108">関数の引数のインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2e677-108">Gets the index of a function argument.</span></span>|  
|[<span data-ttu-id="2e677-109">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-109">GetCode Method</span></span>](icordebugvariablehome-getcode-method.md)|<span data-ttu-id="2e677-110">このオブジェクトを含む "コード" インスタンスを取得し `ICorDebugVariableHome` ます。</span><span class="sxs-lookup"><span data-stu-id="2e677-110">Gets the "ICorDebugCode" instance that contains this `ICorDebugVariableHome` object.</span></span>|  
|[<span data-ttu-id="2e677-111">GetLiveRange メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-111">GetLiveRange Method</span></span>](icordebugvariablehome-getliverange-method.md)|<span data-ttu-id="2e677-112">この変数がライブであるネイティブ範囲を取得します。</span><span class="sxs-lookup"><span data-stu-id="2e677-112">Gets the native range over which this variable is live.</span></span>|  
|[<span data-ttu-id="2e677-113">GetLocationType メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-113">GetLocationType Method</span></span>](icordebugvariablehome-getlocationtype-method.md)|<span data-ttu-id="2e677-114">変数のネイティブな場所の型を取得します。</span><span class="sxs-lookup"><span data-stu-id="2e677-114">Gets the type of the variable's native location.</span></span>|  
|[<span data-ttu-id="2e677-115">GetOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-115">GetOffset Method</span></span>](icordebugvariablehome-getoffset-method.md)|<span data-ttu-id="2e677-116">変数の基本レジスタからのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="2e677-116">Gets the offset from the base register for a variable.</span></span>|  
|[<span data-ttu-id="2e677-117">GetRegister メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-117">GetRegister Method</span></span>](icordebugvariablehome-getregister-method.md)|<span data-ttu-id="2e677-118">の場所の種類がである変数 `VLT_REGISTER` と、の場所の種類がの変数の基本レジスタを含むレジスタを取得し `VLT_REGISTER_RELATIVE` ます。</span><span class="sxs-lookup"><span data-stu-id="2e677-118">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>|  
|[<span data-ttu-id="2e677-119">GetSlotIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="2e677-119">GetSlotIndex Method</span></span>](icordebugvariablehome-getslotindex-method.md)|<span data-ttu-id="2e677-120">ローカル変数のマネージドスロットインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="2e677-120">Gets the managed slot-index of a local variable.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2e677-121">例</span><span class="sxs-lookup"><span data-stu-id="2e677-121">Example</span></span>  
 <span data-ttu-id="2e677-122">次のコード片では、という名前の[ICorDebugCode4](icordebugcode4-interface.md)オブジェクトを使用し `pCode4` ます。</span><span class="sxs-lookup"><span data-stu-id="2e677-122">The following code fragment uses the [ICorDebugCode4](icordebugcode4-interface.md) object named `pCode4`.</span></span>  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a><span data-ttu-id="2e677-123">要件</span><span class="sxs-lookup"><span data-stu-id="2e677-123">Requirements</span></span>  
 <span data-ttu-id="2e677-124">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e677-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e677-125">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e677-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e677-126">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e677-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e677-127">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e677-127">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e677-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e677-128">See also</span></span>

- [<span data-ttu-id="2e677-129">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e677-129">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="2e677-130">ICorDebugVariableHomeEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e677-130">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
