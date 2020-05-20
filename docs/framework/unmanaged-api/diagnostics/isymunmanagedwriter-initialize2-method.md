---
title: ISymUnmanagedWriter::Initialize2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 869d7d36ac24bfeee5b2361dd569945ad77eaf7f
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610068"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="e94b9-102">ISymUnmanagedWriter::Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="e94b9-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="e94b9-103">このライターが関連付けられるメタデータエミッタインターフェイスを設定し、デバッグシンボルの書き込み先となる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="e94b9-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="e94b9-104">この方法では、プログラムデータベース (PDB) ファイルの最終的な場所を設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="e94b9-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e94b9-105">構文</span><span class="sxs-lookup"><span data-stu-id="e94b9-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e94b9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e94b9-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="e94b9-107">からメタデータエミッタインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e94b9-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="e94b9-108">から`WCHAR`デバッグシンボルが書き込まれるファイル名を格納しているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e94b9-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="e94b9-109">ファイル名を使用しないライターに対してファイル名を指定した場合、このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="e94b9-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="e94b9-110">から指定されている場合、シンボルライターは、 <xref:System.Runtime.InteropServices.ComTypes.IStream> パラメーターで指定されたファイルではなく、指定されたにシンボルを出力し `filename` ます。</span><span class="sxs-lookup"><span data-stu-id="e94b9-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="e94b9-111">`pIStream` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="e94b9-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="e94b9-112">[入力] `true`完全な再構築の場合は、`false`インクリメンタルコンパイルの場合は。</span><span class="sxs-lookup"><span data-stu-id="e94b9-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="e94b9-113">から`WCHAR`PDB ファイルの最終的な場所へのパス文字列であるへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e94b9-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e94b9-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="e94b9-114">Return Value</span></span>  
 <span data-ttu-id="e94b9-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e94b9-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e94b9-116">要件</span><span class="sxs-lookup"><span data-stu-id="e94b9-116">Requirements</span></span>  
 <span data-ttu-id="e94b9-117">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e94b9-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e94b9-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e94b9-118">See also</span></span>

- [<span data-ttu-id="e94b9-119">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e94b9-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="e94b9-120">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="e94b9-120">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)
