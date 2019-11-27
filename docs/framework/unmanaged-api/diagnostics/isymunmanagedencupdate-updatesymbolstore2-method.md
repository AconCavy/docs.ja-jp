---
title: ISymUnmanagedENCUpdate::UpdateSymbolStore2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.UpdateSymbolStore2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2
helpviewer_keywords:
- ISymUnmanagedENCUpdate::UpdateSymbolStore2 method [.NET Framework debugging]
- UpdateSymbolStore2 method [.NET Framework debugging]
ms.assetid: 35588317-6184-485c-ab41-4b15fc1765d9
topic_type:
- apiref
ms.openlocfilehash: 393984241412f543b6ac082484cf5e23edb2d9f4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448985"
---
# <a name="isymunmanagedencupdateupdatesymbolstore2-method"></a><span data-ttu-id="5a8e2-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 メソッド</span><span class="sxs-lookup"><span data-stu-id="5a8e2-102">ISymUnmanagedENCUpdate::UpdateSymbolStore2 Method</span></span>
<span data-ttu-id="5a8e2-103">行情報が要件を満たしている場合に、コンパイラがプログラムデータベース (PDB) ストリームから変更されていない関数を省略できるようにします。</span><span class="sxs-lookup"><span data-stu-id="5a8e2-103">Allows a compiler to omit functions that have not been modified from the program database (PDB) stream, provided the line information meets the requirements.</span></span> <span data-ttu-id="5a8e2-104">正しい行情報は、古い PDB 行情報と、関数内のすべての行に対して1つのデルタで判別できます。</span><span class="sxs-lookup"><span data-stu-id="5a8e2-104">The correct line information can be determined with the old PDB line information and one delta for all lines in the function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a8e2-105">構文</span><span class="sxs-lookup"><span data-stu-id="5a8e2-105">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore2(  
    [in]  IStream      *pIStream,  
    [in]  SYMLINEDELTA* pDeltaLines,  
    [in]  ULONG         cDeltaLines);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5a8e2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a8e2-106">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="5a8e2-107">から行情報を格納している[IStream](/windows/desktop/api/objidl/nn-objidl-istream)へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5a8e2-107">[in] A pointer to an [IStream](/windows/desktop/api/objidl/nn-objidl-istream) that contains the line information.</span></span>  
  
 `pDeltaLines`  
 <span data-ttu-id="5a8e2-108">から変更された行を含む[Symlinedelta](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md)構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5a8e2-108">[in] A pointer to a [SYMLINEDELTA](../../../../docs/framework/unmanaged-api/diagnostics/symlinedelta-structure.md) structure that contains the lines that have changed.</span></span>  
  
 `cDeltaLines`  
 <span data-ttu-id="5a8e2-109">から変更された行の数を表す `ULONG`。</span><span class="sxs-lookup"><span data-stu-id="5a8e2-109">[in] A `ULONG` that represents the number of lines that have changed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a8e2-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="5a8e2-110">Return Value</span></span>  
 <span data-ttu-id="5a8e2-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5a8e2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a8e2-112">要件</span><span class="sxs-lookup"><span data-stu-id="5a8e2-112">Requirements</span></span>  
 <span data-ttu-id="5a8e2-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="5a8e2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a8e2-114">参照</span><span class="sxs-lookup"><span data-stu-id="5a8e2-114">See also</span></span>

- [<span data-ttu-id="5a8e2-115">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a8e2-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
