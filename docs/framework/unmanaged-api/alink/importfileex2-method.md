---
title: ImportFileEx2 メソッド
ms.date: 03/30/2017
api_name:
- IALink2.ImportFileEx2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportFileEx2
helpviewer_keywords:
- ImportFileEx2 method
ms.assetid: 02c789fd-16fc-48c6-9619-56e87e2a37ca
topic_type:
- apiref
ms.openlocfilehash: 7e270dbfc63c03e77cb4b0694296e48c2035b8a6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445696"
---
# <a name="importfileex2-method"></a><span data-ttu-id="854b6-102">ImportFileEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="854b6-102">ImportFileEx2 Method</span></span>
<span data-ttu-id="854b6-103">アセンブリとバインドされていないモジュールをインポートします。</span><span class="sxs-lookup"><span data-stu-id="854b6-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="854b6-104">このメソッドは[Importfile メソッド](importfile-method.md)に似ていますが、インポートされるファイルがディスク上に存在しない場合でも機能します。</span><span class="sxs-lookup"><span data-stu-id="854b6-104">This method is like [ImportFile Method](importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="854b6-105">構文</span><span class="sxs-lookup"><span data-stu-id="854b6-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportFileEx2(  
    LPCWSTR pszFilename,  
    LPCWSTR pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL fSmartImport,  
    DWORD dwOpenFlags,  
    mdToken* pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD* pdwCountOfScopes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="854b6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="854b6-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="854b6-107">インポートするファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="854b6-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="854b6-108">ターゲットファイルの名前 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="854b6-108">Optional name of target file.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="854b6-109">省略可能なインポートスコープ[IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="854b6-109">Optional import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="854b6-110">TRUE の場合、ImportTypes が使用されます。それ以外の場合は、インポートを手動で実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="854b6-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="854b6-111">[Openscope メソッド](../metadata/imetadatadispenser-openscope-method.md)に渡されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="854b6-111">Flags to be passed along to [OpenScope Method](../metadata/imetadatadispenser-openscope-method.md).</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="854b6-112">アセンブリまたはファイルの一意の ID を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="854b6-112">Receives unique ID for the assembly or file.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="854b6-113">アセンブリインポートスコープ[IMetaDataAssemblyImport インターフェイス](../metadata/imetadataassemblyimport-interface.md)インターフェイスを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="854b6-113">Receives assembly import scope [IMetaDataAssemblyImport Interface](../metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="854b6-114">ファイルがアセンブリでない場合は NULL を指定できます。</span><span class="sxs-lookup"><span data-stu-id="854b6-114">Can be NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="854b6-115">インポートされたファイルまたはスコープの数を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="854b6-115">Receives the number of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="854b6-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="854b6-116">Return Value</span></span>  
 <span data-ttu-id="854b6-117">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="854b6-117">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="854b6-118">要件</span><span class="sxs-lookup"><span data-stu-id="854b6-118">Requirements</span></span>  
 <span data-ttu-id="854b6-119">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="854b6-119">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="854b6-120">参照</span><span class="sxs-lookup"><span data-stu-id="854b6-120">See also</span></span>

- [<span data-ttu-id="854b6-121">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="854b6-121">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="854b6-122">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="854b6-122">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="854b6-123">ALink API</span><span class="sxs-lookup"><span data-stu-id="854b6-123">ALink API</span></span>](index.md)
