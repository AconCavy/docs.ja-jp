---
title: ISymUnmanagedWriter::DefineConstant メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineConstant
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineConstant
helpviewer_keywords:
- DefineConstant method [.NET Framework debugging]
- ISymUnmanagedWriter::DefineConstant method [.NET Framework debugging]
ms.assetid: 9e986986-2223-4d5f-b040-85d716146924
topic_type:
- apiref
ms.openlocfilehash: c8d0145b9dffe1c0ff6ed3281c90f3bcec082ab8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428064"
---
# <a name="isymunmanagedwriterdefineconstant-method"></a><span data-ttu-id="a6034-102">ISymUnmanagedWriter::DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="a6034-102">ISymUnmanagedWriter::DefineConstant Method</span></span>
<span data-ttu-id="a6034-103">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="a6034-103">Defines a name for a constant value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6034-104">構文</span><span class="sxs-lookup"><span data-stu-id="a6034-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineConstant(  
    [in] const WCHAR *name,  
    [in] VARIANT value,  
    [in] ULONG32 cSig,  
    [in, size_is(cSig)] unsigned char signature[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6034-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a6034-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="a6034-106">から定数名を定義する `WCHAR` へのポインター。</span><span class="sxs-lookup"><span data-stu-id="a6034-106">[in] A pointer to a `WCHAR` that defines the constant name.</span></span>  
  
 `value`  
 <span data-ttu-id="a6034-107">から定数の値。</span><span class="sxs-lookup"><span data-stu-id="a6034-107">[in] The value of the constant.</span></span>  
  
 `cSig`  
 <span data-ttu-id="a6034-108">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="a6034-108">[in] The size of the `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="a6034-109">から定数の型シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="a6034-109">[in] The type signature for the constant.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6034-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="a6034-110">Return Value</span></span>  
 <span data-ttu-id="a6034-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6034-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6034-112">要件</span><span class="sxs-lookup"><span data-stu-id="a6034-112">Requirements</span></span>  
 <span data-ttu-id="a6034-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a6034-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6034-114">参照</span><span class="sxs-lookup"><span data-stu-id="a6034-114">See also</span></span>

- [<span data-ttu-id="a6034-115">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a6034-115">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="a6034-116">DefineConstant2 メソッド</span><span class="sxs-lookup"><span data-stu-id="a6034-116">DefineConstant2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-defineconstant2-method.md)
