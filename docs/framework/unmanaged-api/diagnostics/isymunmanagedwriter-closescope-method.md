---
title: ISymUnmanagedWriter::CloseScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseScope
helpviewer_keywords:
- CloseScope method [.NET Framework debugging]
- ISymUnmanagedWriter::CloseScope method [.NET Framework debugging]
ms.assetid: 6dade525-7770-4cb4-bafd-4bb995ad0d87
topic_type:
- apiref
ms.openlocfilehash: e2e911fb1d737ebb6b2106c89ac11335788ace4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501730"
---
# <a name="isymunmanagedwriterclosescope-method"></a><span data-ttu-id="0de4c-102">ISymUnmanagedWriter::CloseScope メソッド</span><span class="sxs-lookup"><span data-stu-id="0de4c-102">ISymUnmanagedWriter::CloseScope Method</span></span>
<span data-ttu-id="0de4c-103">現在の構文のスコープを閉じます。</span><span class="sxs-lookup"><span data-stu-id="0de4c-103">Closes the current lexical scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de4c-104">構文</span><span class="sxs-lookup"><span data-stu-id="0de4c-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseScope(  
    [in] ULONG32 endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de4c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0de4c-105">Parameters</span></span>  
 `endOffset`  
 <span data-ttu-id="0de4c-106">から構文のスコープの最後の命令の末尾にある点の、メソッドの先頭からのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="0de4c-106">[in] The offset from the beginning of the method of the point at the end of the last instruction in the lexical scope, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0de4c-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="0de4c-107">Return Value</span></span>  
 <span data-ttu-id="0de4c-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0de4c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0de4c-109">解説</span><span class="sxs-lookup"><span data-stu-id="0de4c-109">Remarks</span></span>  
 <span data-ttu-id="0de4c-110">スコープを閉じた後は、それ以上の変数を定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="0de4c-110">Once a scope is closed, no more variables can be defined within it.</span></span>  
  
 <span data-ttu-id="0de4c-111">[ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md)は、 [ISymUnmanagedWriter:: SetScopeRange](isymunmanagedwriter-setscoperange-method.md)と共に使用してスコープの開始オフセットと終了オフセットを後で定義できる、不透明なスコープ識別子を返します。</span><span class="sxs-lookup"><span data-stu-id="0de4c-111">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with [ISymUnmanagedWriter::SetScopeRange](isymunmanagedwriter-setscoperange-method.md) to later define a scope's starting and ending offset.</span></span> <span data-ttu-id="0de4c-112">この場合、`ISymUnmanagedWriter::OpenScope` と `ISymUnmanagedWriter::CloseScope` に渡したオフセットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="0de4c-112">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and `ISymUnmanagedWriter::CloseScope` are ignored.</span></span> <span data-ttu-id="0de4c-113">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="0de4c-113">Scope identifiers are valid only in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de4c-114">要件</span><span class="sxs-lookup"><span data-stu-id="0de4c-114">Requirements</span></span>  
 <span data-ttu-id="0de4c-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0de4c-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de4c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0de4c-116">See also</span></span>

- [<span data-ttu-id="0de4c-117">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0de4c-117">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
