---
title: メタデータ インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], metadata
- metadata interfaces [.NET Framework]
- interfaces (.NET Framework metadata]
ms.assetid: f5cdac93-a28c-48ef-8a19-5773376e9e7c
ms.openlocfilehash: 4d947388afb8d7f8f935ae3b8e8aff81efaf2ee4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84489596"
---
# <a name="metadata-interfaces"></a><span data-ttu-id="d7ad9-102">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-102">Metadata Interfaces</span></span>
<span data-ttu-id="d7ad9-103">このセクションでは、.NET Framework の型、メソッド、フィールドなどによって公開されるメタデータにアクセスできるようにするアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-103">This section describes the unmanaged interfaces that provide access to the metadata exposed by the .NET Framework types, methods, fields, and so on.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d7ad9-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d7ad9-104">In This Section</span></span>  
 [<span data-ttu-id="d7ad9-105">ICeeGen インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-105">ICeeGen Interface</span></span>](iceegen-interface.md)  
 <span data-ttu-id="d7ad9-106">動的なコード コンパイルのためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-106">Provides methods for dynamic code compilation.</span></span>  
  
 [<span data-ttu-id="d7ad9-107">IHostFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-107">IHostFilter Interface</span></span>](ihostfilter-interface.md)  
 <span data-ttu-id="d7ad9-108">ランタイム ホストがメタデータ トークンに処理済みのマークを付けるためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-108">Provides a method for the run-time host to mark metadata tokens for processing.</span></span>  
  
 [<span data-ttu-id="d7ad9-109">IMapToken インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-109">IMapToken Interface</span></span>](imaptoken-interface.md)  
 <span data-ttu-id="d7ad9-110">インポートされたメタデータ署名と生成されたメタデータ署名との間の割り当て機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-110">Provides mapping capabilities between imported and emitted metadata signatures.</span></span>  
  
 [<span data-ttu-id="d7ad9-111">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-111">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)  
 <span data-ttu-id="d7ad9-112">共通言語ランタイム (CLR) がリソースの解決および消費に使用する自己記述モデルをサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-112">Provides methods that support the self-description model used by the common language runtime (CLR) to resolve and consume resources.</span></span>  
  
 [<span data-ttu-id="d7ad9-113">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)  
 <span data-ttu-id="d7ad9-114">アセンブリ マニフェストの内容にアクセスして確認するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-114">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
 [<span data-ttu-id="d7ad9-115">IMetaDataConverter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-115">IMetaDataConverter Interface</span></span>](imetadataconverter-interface.md)  
 <span data-ttu-id="d7ad9-116">タイプ ライブラリをそれぞれのメタデータ署名にマップして、一方から他方に変換するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-116">Provides methods to map type libraries to their metadata signatures, and to convert from one to the other.</span></span>  
  
 [<span data-ttu-id="d7ad9-117">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-117">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)  
 <span data-ttu-id="d7ad9-118">`IMetaDataDispenser` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-118">`IMetaDataDispenser` is obsolete.</span></span> <span data-ttu-id="d7ad9-119">代わりに、`IMetaDataDispenserEx` を使用してください。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-119">Use `IMetaDataDispenserEx` instead.</span></span>  
  
 [<span data-ttu-id="d7ad9-120">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)  
 <span data-ttu-id="d7ad9-121">メタデータを作成または変更するためのメモリ領域を割り当てるメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-121">Provides methods that map areas of memory for creating or modifying metadata.</span></span>  
  
 [<span data-ttu-id="d7ad9-122">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)  
 <span data-ttu-id="d7ad9-123">現在定義されているスコープ内のアセンブリについてのメタデータを作成、変更、格納するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-123">Provides methods to create, modify and store metadata about the assembly in the currently defined scope.</span></span>  
  
 [<span data-ttu-id="d7ad9-124">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-124">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)  
 <span data-ttu-id="d7ad9-125"><xref:System.Type?displayProperty=nameWithType> 型のパラメーターを持つメソッドおよびコンストラクターのメタデータ署名を定義および変更するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-125">Provides methods for defining and modifying the metadata signatures of methods and constructors with parameters of type <xref:System.Type?displayProperty=nameWithType>.</span></span>  
  
 [<span data-ttu-id="d7ad9-126">IMetaDataError インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-126">IMetaDataError Interface</span></span>](imetadataerror-interface.md)  
 <span data-ttu-id="d7ad9-127">アセンブリのメタデータ署名の解決時のエラーを報告するためのコールバック機構を提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-127">Provides a callback mechanism for reporting errors during the resolution of the metadata signature for an assembly.</span></span>  
  
 [<span data-ttu-id="d7ad9-128">IMetaDataFilter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-128">IMetaDataFilter Interface</span></span>](imetadatafilter-interface.md)  
 <span data-ttu-id="d7ad9-129">メタデータ トークンにマークを付け、フィルター処理をして、既に実行されたアクションが繰り返し行われないようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-129">Provides methods for marking and filtering metadata tokens to avoid repeating actions that have already been taken.</span></span>  
  
 [<span data-ttu-id="d7ad9-130">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)  
 <span data-ttu-id="d7ad9-131">他のアセンブリの型をインポートおよび操作するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-131">Provides methods for importing and manipulating types from other assemblies.</span></span>  
  
 [<span data-ttu-id="d7ad9-132">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-132">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)  
 <span data-ttu-id="d7ad9-133">`IMetaDataImport` を拡張して、ジェネリック型を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-133">Extends `IMetaDataImport` to provide the capability of working with generic types.</span></span>  
  
 [<span data-ttu-id="d7ad9-134">IMetaDataInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-134">IMetaDataInfo Interface</span></span>](imetadatainfo-interface.md)  
 <span data-ttu-id="d7ad9-135">ディスク上のファイルからメモリへのメタデータのマッピングに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-135">Provides a method that gets information about the mapping of metadata from an on-disk file into memory.</span></span>  
  
 [<span data-ttu-id="d7ad9-136">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-136">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)  
 <span data-ttu-id="d7ad9-137">テーブル内のメタデータ情報の格納と取得のためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-137">Provides methods for the storage and retrieval of metadata information in tables.</span></span>  
  
 [<span data-ttu-id="d7ad9-138">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-138">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)  
 <span data-ttu-id="d7ad9-139">`IMetaDataTables` を拡張して、メタデータ ストリームを使用するためのメソッドを含めます。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-139">Extends `IMetaDataTables` to include methods for working with metadata streams.</span></span>  
  
 [<span data-ttu-id="d7ad9-140">IMetaDataValidate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d7ad9-140">IMetaDataValidate Interface</span></span>](imetadatavalidate-interface.md)  
 <span data-ttu-id="d7ad9-141">メタデータ署名の検証で使用するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d7ad9-141">Provides methods to use for validation of metadata signatures.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d7ad9-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7ad9-142">Related Sections</span></span>  
 [<span data-ttu-id="d7ad9-143">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="d7ad9-143">Metadata Global Static Functions</span></span>](metadata-global-static-functions.md)  
  
 [<span data-ttu-id="d7ad9-144">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="d7ad9-144">Metadata Enumerations</span></span>](metadata-enumerations.md)  
  
 [<span data-ttu-id="d7ad9-145">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="d7ad9-145">Metadata Structures</span></span>](metadata-structures.md)  
  
 [<span data-ttu-id="d7ad9-146">メタデータ共用体</span><span class="sxs-lookup"><span data-stu-id="d7ad9-146">Metadata Unions</span></span>](metadata-unions.md)
