---
title: ISymUnmanagedVariable::GetAttributes メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 29869abdd39f61c6c9cb51d6b2be50fa462c5b70
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615255"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="cfa5d-102">ISymUnmanagedVariable::GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="cfa5d-102">ISymUnmanagedVariable::GetAttributes Method</span></span>
<span data-ttu-id="cfa5d-103">この変数の属性フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="cfa5d-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa5d-104">構文</span><span class="sxs-lookup"><span data-stu-id="cfa5d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfa5d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cfa5d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="cfa5d-106">入出力属性を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="cfa5d-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="cfa5d-107">返される値は、 [Corsymvarflag](corsymvarflag-enumeration.md)列挙で定義されている値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="cfa5d-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cfa5d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="cfa5d-108">Return Value</span></span>  
 <span data-ttu-id="cfa5d-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="cfa5d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa5d-110">要件</span><span class="sxs-lookup"><span data-stu-id="cfa5d-110">Requirements</span></span>  
 <span data-ttu-id="cfa5d-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="cfa5d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa5d-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="cfa5d-112">See also</span></span>

- [<span data-ttu-id="cfa5d-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cfa5d-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
