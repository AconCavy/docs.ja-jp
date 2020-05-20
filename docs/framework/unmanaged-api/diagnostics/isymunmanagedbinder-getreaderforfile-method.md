---
title: ISymUnmanagedBinder::GetReaderForFile メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
ms.openlocfilehash: c4416e8e4395c4e1967155310d12a1eb68c42d83
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441735"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="f26fe-102">ISymUnmanagedBinder::GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="f26fe-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="f26fe-103">メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい[ISymUnmanagedReader](isymunmanagedreader-interface.md)インターフェイスが返されます。</span><span class="sxs-lookup"><span data-stu-id="f26fe-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="f26fe-104">このメソッドは、プログラムデータベース (PDB) ファイルが実行可能ファイルの横にある場合にのみ、ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="f26fe-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="f26fe-105">この変更は、セキュリティ上の目的で行われています。</span><span class="sxs-lookup"><span data-stu-id="f26fe-105">This change has been made for security purposes.</span></span> <span data-ttu-id="f26fe-106">PDB ファイルをより広範囲に検索する必要がある場合は、 [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md)メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f26fe-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f26fe-107">構文</span><span class="sxs-lookup"><span data-stu-id="f26fe-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f26fe-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f26fe-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="f26fe-109">からメタデータインポートインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f26fe-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="f26fe-110">からファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="f26fe-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="f26fe-111">から検索パスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f26fe-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="f26fe-112">入出力返された[ISymUnmanagedReader](isymunmanagedreader-interface.md)インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="f26fe-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f26fe-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="f26fe-113">Return Value</span></span>  
 <span data-ttu-id="f26fe-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f26fe-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f26fe-115">要件</span><span class="sxs-lookup"><span data-stu-id="f26fe-115">Requirements</span></span>  
 <span data-ttu-id="f26fe-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f26fe-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26fe-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f26fe-117">See also</span></span>

- [<span data-ttu-id="f26fe-118">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f26fe-118">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="f26fe-119">GetReaderForFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="f26fe-119">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)
