---
title: ISymUnmanagedWriter2::DefineConstant2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter2.DefineConstant2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter2::DefineConstant2
helpviewer_keywords:
- DefineConstant2 method [.NET Framework debugging]
- ISymUnmanagedWriter2::DefineConstant2 method [.NET Framework debugging]
ms.assetid: dd2bc956-7dbe-49fc-a646-daa0d267f2df
topic_type:
- apiref
ms.openlocfilehash: 70ee853ff657a75dcc4df1454c4354f9d3f8202f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614722"
---
# <a name="isymunmanagedwriter2defineconstant2-method"></a><span data-ttu-id="2e778-102">ISymUnmanagedWriter2::DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="2e778-102">ISymUnmanagedWriter2::DefineConstant2 Method</span></span>
<span data-ttu-id="2e778-103">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="2e778-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e778-104">構文</span><span class="sxs-lookup"><span data-stu-id="2e778-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant2(  
    [in] const WCHAR  *name,  
    [in] VARIANT      value,  
    [in] mdSignature  sigToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e778-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2e778-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="2e778-106">から定数名。</span><span class="sxs-lookup"><span data-stu-id="2e778-106">[in] The constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="2e778-107">から定数の値。</span><span class="sxs-lookup"><span data-stu-id="2e778-107">[in] The value of the constant.</span></span>  
  
 `sigToken`  
 <span data-ttu-id="2e778-108">から定数のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="2e778-108">[in] The metadata token of the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e778-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="2e778-109">Return Value</span></span>  
 <span data-ttu-id="2e778-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="2e778-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e778-111">要件</span><span class="sxs-lookup"><span data-stu-id="2e778-111">Requirements</span></span>  
 <span data-ttu-id="2e778-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="2e778-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e778-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e778-113">See also</span></span>

- [<span data-ttu-id="2e778-114">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2e778-114">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="2e778-115">DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="2e778-115">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)
