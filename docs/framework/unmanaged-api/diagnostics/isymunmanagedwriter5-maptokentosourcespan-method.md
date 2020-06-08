---
title: ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド
ms.date: 03/30/2017
ms.assetid: d0fbbf61-71c6-4fb1-8c9f-d619ca5d7d68
ms.openlocfilehash: 0f00dd34ffbdd58a46260132d8d7ace74ec2f294
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501678"
---
# <a name="isymunmanagedwriter5maptokentosourcespan-method"></a><span data-ttu-id="789cf-102">ISymUnmanagedWriter5::MapTokenToSourceSpan メソッド</span><span class="sxs-lookup"><span data-stu-id="789cf-102">ISymUnmanagedWriter5::MapTokenToSourceSpan Method</span></span>
<span data-ttu-id="789cf-103">指定されたメタデータトークンを、指定されたソースファイル内の指定されたソース行スパンにマップします。</span><span class="sxs-lookup"><span data-stu-id="789cf-103">Maps the given metadata token to the given source line span in the specified source file.</span></span>  
  
 <span data-ttu-id="789cf-104">[Openmaptokenstosourcespans メソッド](isymunmanagedwriter5-openmaptokenstosourcespans-method.md)と[CloseMapTokensToSourceSpans メソッド](isymunmanagedwriter5-closemaptokenstosourcespans-method.md)の呼び出しの間で、を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="789cf-104">Must be called between calls to [OpenMapTokensToSourceSpans Method](isymunmanagedwriter5-openmaptokenstosourcespans-method.md) and [CloseMapTokensToSourceSpans Method](isymunmanagedwriter5-closemaptokenstosourcespans-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789cf-105">構文</span><span class="sxs-lookup"><span data-stu-id="789cf-105">Syntax</span></span>  
  
```idl  
HRESULT MapTokenToSourceSpan(    [in] mdToken token,    [in] ISymUnmanagedDocumentWriter* document,    [in] ULONG32 line,    [in] ULONG32 column,    [in] ULONG32 endLine,    [in] ULONG32 endColumn);  
```  
  
## <a name="parameters"></a><span data-ttu-id="789cf-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="789cf-106">Parameters</span></span>  
  
|<span data-ttu-id="789cf-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="789cf-107">Parameter</span></span>|<span data-ttu-id="789cf-108">説明</span><span class="sxs-lookup"><span data-stu-id="789cf-108">Description</span></span>|  
|---------------|-----------------|  
|`token`||  
|`document`||  
|`line`||  
|`column`||  
|`endLine`||  
|`endColumn`||  
  
## <a name="return-value"></a><span data-ttu-id="789cf-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="789cf-109">Return Value</span></span>  
 <span data-ttu-id="789cf-110">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="789cf-110">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="789cf-111">要件</span><span class="sxs-lookup"><span data-stu-id="789cf-111">Requirements</span></span>  
 <span data-ttu-id="789cf-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="789cf-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="789cf-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="789cf-113">See also</span></span>

- [<span data-ttu-id="789cf-114">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="789cf-114">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)
