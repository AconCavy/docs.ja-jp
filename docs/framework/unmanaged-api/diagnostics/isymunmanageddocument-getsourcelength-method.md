---
title: ISymUnmanagedDocument::GetSourceLength メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
ms.openlocfilehash: e84639c1d63e6935b9b363f01c12bf0fbd3390e3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615619"
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="3f511-102">ISymUnmanagedDocument::GetSourceLength メソッド</span><span class="sxs-lookup"><span data-stu-id="3f511-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="3f511-103">埋め込まれたソースの長さをバイト数で取得します。</span><span class="sxs-lookup"><span data-stu-id="3f511-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f511-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f511-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f511-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f511-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3f511-106">入出力埋め込まれたソースの長さ (バイト単位) を示す変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3f511-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3f511-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3f511-107">Return Value</span></span>  
 <span data-ttu-id="3f511-108">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="3f511-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f511-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f511-109">See also</span></span>

- [<span data-ttu-id="3f511-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f511-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
