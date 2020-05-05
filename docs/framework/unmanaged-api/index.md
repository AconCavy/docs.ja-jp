---
title: アンマネージ API リファレンス
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: 9b8671f2bd278e9e6153476d742f43150a4f6e3e
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795613"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="2ccb2-102">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="2ccb2-102">Unmanaged API Reference</span></span>
<span data-ttu-id="2ccb2-103">このセクションには、ランタイム ホスト、コンパイラ、逆アセンブラー、難読化ツール、デバッガー、プロファイラーなど、マネージ コード関連のアプリケーションが使用できるアンマネージ API に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ccb2-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="2ccb2-104">In This Section</span></span>  
 [<span data-ttu-id="2ccb2-105">共有のデータ型</span><span class="sxs-lookup"><span data-stu-id="2ccb2-105">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="2ccb2-106">特にアンマネージ プロファイリング API とデバッギング API で使用される一般的なデータ型を示します。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="2ccb2-107">ALink</span><span class="sxs-lookup"><span data-stu-id="2ccb2-107">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="2ccb2-108">ALink API について説明します。この API は .NET Framework アセンブリおよび非バインド モジュールの作成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="2ccb2-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="2ccb2-109">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="2ccb2-110">Authenticode XrML ライセンスの作成および検証モジュールをサポートします。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="2ccb2-111">定数</span><span class="sxs-lookup"><span data-stu-id="2ccb2-111">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="2ccb2-112">CorSym.idl で定義される定数について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="2ccb2-113">[カスタム インターフェイス属性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2ccb2-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="2ccb2-114">コンポーネント オブジェクト モデル (COM) のカスタム インターフェイス属性について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="2ccb2-115">デバッグ</span><span class="sxs-lookup"><span data-stu-id="2ccb2-115">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="2ccb2-116">デバッグ API について説明します。これによりデバッガーは、共通言語ランタイム (CLR) 環境で実行するコードをデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="2ccb2-117">シンボル ストア診断</span><span class="sxs-lookup"><span data-stu-id="2ccb2-117">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="2ccb2-118">シンボル ストア診断 API について説明します。これによりコンパイラは、デバッガーが使用するためのシンボル情報を生成できます。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="2ccb2-119">Fusion</span><span class="sxs-lookup"><span data-stu-id="2ccb2-119">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="2ccb2-120">Fusion API について説明します。これによりランタイム ホストは、アプリケーションに対するリソースの正しいバージョンを見つけるために、アプリケーションのリソースのプロパティにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="2ccb2-121">ホスティング</span><span class="sxs-lookup"><span data-stu-id="2ccb2-121">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="2ccb2-122">ホスト API について説明します。これにより、アンマネージ ホストが CLR をホストのアプリケーションに統合できます。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="2ccb2-123">メタデータ</span><span class="sxs-lookup"><span data-stu-id="2ccb2-123">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="2ccb2-124">メタデータ API について説明します。これによりコンパイラなどのクライアントは、CLR によって読み込まれる型を使用せずに、コンポーネントのメタデータを生成したり、メタデータにアクセスしたりできます。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="2ccb2-125">プロファイル</span><span class="sxs-lookup"><span data-stu-id="2ccb2-125">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="2ccb2-126">プロファイル API について説明します。これによりプロファイラーは CLR によるプログラムの実行を監視できます。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="2ccb2-127">厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="2ccb2-127">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="2ccb2-128">厳密な名前付け API について説明します。これによりクライアントは、アセンブリに対する厳密な名前の署名を管理できます。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="2ccb2-129">WMI およびパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="2ccb2-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="2ccb2-130">Windows Management Instrumentation (WMI) ライブラリへの呼び出しをラッピングするAPI について説明します。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="2ccb2-131">Tlbexp ヘルパー関数</span><span class="sxs-lookup"><span data-stu-id="2ccb2-131">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="2ccb2-132">タイプ ライブラリ エクスポーター (Tlbexp.exe) がアセンブリからタイプ ライブラリへの変換プロセス中に使用する、2 つのヘルパー関数とインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="2ccb2-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2ccb2-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="2ccb2-133">Related Sections</span></span>  
 [<span data-ttu-id="2ccb2-134">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="2ccb2-134">Development Guide</span></span>](../development-guide.md)  
