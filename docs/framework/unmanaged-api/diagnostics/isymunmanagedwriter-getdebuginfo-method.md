---
title: ISymUnmanagedWriter::GetDebugInfo メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: f8eb4cb6bad95295e10a72812fa8dbb0adfcc898
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614787"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="e77ec-102">ISymUnmanagedWriter::GetDebugInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="e77ec-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="e77ec-103">コンパイラがポータブル実行可能 (PE) ファイルヘッダーにデバッグディレクトリエントリを書き込むために必要な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="e77ec-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="e77ec-104">シンボルライターは、およびを除くすべてのフィールドを入力し `TimeDateStamp` `PointerToRawData` ます。</span><span class="sxs-lookup"><span data-stu-id="e77ec-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="e77ec-105">(コンパイラは、これらの2つのフィールドを適切に設定する必要があります)。</span><span class="sxs-lookup"><span data-stu-id="e77ec-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="e77ec-106">コンパイラは、このメソッドを呼び出し、PE ファイルにデータ blob を出力します。次に、 `PointerToRawData` 生成されたデータを指すように IMAGE_DEBUG_DIRECTORY のフィールドを設定し、IMAGE_DEBUG_DIRECTORY を pe ファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="e77ec-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="e77ec-107">また、コンパイラは、 `TimeDateStamp` `TimeDateStamp` 生成される PE ファイルのと同じフィールドをに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e77ec-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e77ec-108">構文</span><span class="sxs-lookup"><span data-stu-id="e77ec-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e77ec-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e77ec-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="e77ec-110">[入力、出力]シンボルライターが入力する IMAGE_DEBUG_DIRECTORY へのポインター。</span><span class="sxs-lookup"><span data-stu-id="e77ec-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="e77ec-111">から`DWORD`デバッグデータのサイズを格納している。</span><span class="sxs-lookup"><span data-stu-id="e77ec-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="e77ec-112">入出力`DWORD`デバッグデータを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e77ec-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="e77ec-113">入出力シンボルストアのデバッグデータを保持するのに十分な大きさのバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e77ec-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e77ec-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="e77ec-114">Return Value</span></span>  
 <span data-ttu-id="e77ec-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e77ec-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e77ec-116">要件</span><span class="sxs-lookup"><span data-stu-id="e77ec-116">Requirements</span></span>  
 <span data-ttu-id="e77ec-117">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e77ec-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77ec-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e77ec-118">See also</span></span>

- [<span data-ttu-id="e77ec-119">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e77ec-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
