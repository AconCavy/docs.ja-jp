---
title: IMetaDataDispenser::OpenScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007469"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="25163-102">IMetaDataDispenser::OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="25163-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="25163-103">ディスク上の既存のファイルを開き、そのメタデータをメモリにマップします。</span><span class="sxs-lookup"><span data-stu-id="25163-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25163-104">構文</span><span class="sxs-lookup"><span data-stu-id="25163-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25163-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="25163-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="25163-106">から開くファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="25163-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="25163-107">ファイルには、共通言語ランタイム (CLR) メタデータが含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="25163-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="25163-108">から開くためのモード (読み取り、書き込みなど) を指定する[Coropenflags](coropenflags-enumeration.md)列挙体の値。</span><span class="sxs-lookup"><span data-stu-id="25163-108">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="25163-109">から返される、必要なメタデータインターフェイスの IID。呼び出し元は、インターフェイスを使用して、メタデータのインポート (読み取り) または出力 (書き込み) を行います。</span><span class="sxs-lookup"><span data-stu-id="25163-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="25163-110">の値には `riid` 、"import" インターフェイスまたは "emit" インターフェイスのいずれかを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="25163-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="25163-111">有効な値は、IID_IMetaDataEmit、IID_IMetaDataImport、IID_IMetaDataAssemblyEmit、IID_IMetaDataAssemblyImport、IID_IMetaDataEmit2、または IID_IMetaDataImport2 です。</span><span class="sxs-lookup"><span data-stu-id="25163-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="25163-112">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="25163-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25163-113">コメント</span><span class="sxs-lookup"><span data-stu-id="25163-113">Remarks</span></span>  
 <span data-ttu-id="25163-114">メタデータのメモリ内コピーは、"import" インターフェイスのいずれかのメソッドを使用してクエリを実行するか、"emit" インターフェイスのいずれかのメソッドを使用してに追加できます。</span><span class="sxs-lookup"><span data-stu-id="25163-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="25163-115">ターゲットファイルに CLR メタデータが含まれていない場合、 `OpenScope` メソッドは失敗します。</span><span class="sxs-lookup"><span data-stu-id="25163-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="25163-116">.NET Framework バージョン1.0 およびバージョン1.1 では、ofRead に設定してスコープを開くと、 `dwOpenFlags` 共有の対象になります。</span><span class="sxs-lookup"><span data-stu-id="25163-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="25163-117">つまり、それ以降の呼び出し `OpenScope` で、以前に開いたファイルの名前が渡された場合、既存のスコープが再利用され、新しいデータ構造体のセットは作成されません。</span><span class="sxs-lookup"><span data-stu-id="25163-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="25163-118">ただし、この共有によって問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="25163-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="25163-119">.NET Framework バージョン2.0 では、ofRead に設定して開いたスコープ `dwOpenFlags` は共有されなくなりました。</span><span class="sxs-lookup"><span data-stu-id="25163-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="25163-120">スコープを共有できるようにするには、ofReadOnly 値を使用します。</span><span class="sxs-lookup"><span data-stu-id="25163-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="25163-121">スコープが共有されると、"読み取り/書き込み" メタデータインターフェイスを使用するクエリは失敗します。</span><span class="sxs-lookup"><span data-stu-id="25163-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25163-122">必要条件</span><span class="sxs-lookup"><span data-stu-id="25163-122">Requirements</span></span>  
 <span data-ttu-id="25163-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="25163-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25163-124">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="25163-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25163-125">**ライブラリ:** Mscoree.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="25163-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25163-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25163-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25163-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="25163-127">See also</span></span>

- [<span data-ttu-id="25163-128">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-128">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="25163-129">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="25163-130">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-130">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="25163-131">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-131">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="25163-132">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="25163-133">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="25163-134">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-134">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="25163-135">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="25163-135">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
