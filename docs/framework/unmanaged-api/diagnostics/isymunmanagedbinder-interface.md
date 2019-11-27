---
title: ISymUnmanagedBinder インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
ms.openlocfilehash: f23df98abc5355f0b25d7253b5f2ae808b3446a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449376"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="644b0-102">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="644b0-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="644b0-103">アンマネージコードのシンボルバインダーを表します。</span><span class="sxs-lookup"><span data-stu-id="644b0-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="644b0-104">信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。</span><span class="sxs-lookup"><span data-stu-id="644b0-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="644b0-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="644b0-105">Methods</span></span>  
  
|<span data-ttu-id="644b0-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="644b0-106">Method</span></span>|<span data-ttu-id="644b0-107">説明</span><span class="sxs-lookup"><span data-stu-id="644b0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="644b0-108">GetReaderForFile メソッド</span><span class="sxs-lookup"><span data-stu-id="644b0-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="644b0-109">メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい[ISymUnmanagedReader](isymunmanagedreader-interface.md)構造体が返されます。</span><span class="sxs-lookup"><span data-stu-id="644b0-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="644b0-110">GetReaderFromStream メソッド</span><span class="sxs-lookup"><span data-stu-id="644b0-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="644b0-111">メタデータインターフェイスと、シンボルストアを含むストリームが指定された場合、は、指定されたシンボルストアからデバッグシンボルを読み取る正しい[ISymUnmanagedReader](isymunmanagedreader-interface.md)構造体を返します。</span><span class="sxs-lookup"><span data-stu-id="644b0-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="644b0-112">要件</span><span class="sxs-lookup"><span data-stu-id="644b0-112">Requirements</span></span>  
 <span data-ttu-id="644b0-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="644b0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="644b0-114">参照</span><span class="sxs-lookup"><span data-stu-id="644b0-114">See also</span></span>

- [<span data-ttu-id="644b0-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="644b0-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="644b0-116">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="644b0-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="644b0-117">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="644b0-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
