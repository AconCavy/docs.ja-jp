---
title: アセンブリ名
ms.date: 08/19/2019
helpviewer_keywords:
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
ms.openlocfilehash: a35be7c2a2cb4b499496f526d263bb1825a3614b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107127"
---
# <a name="assembly-names"></a><span data-ttu-id="9c5f9-102">アセンブリ名</span><span class="sxs-lookup"><span data-stu-id="9c5f9-102">Assembly names</span></span>
<span data-ttu-id="9c5f9-103">アセンブリの名前は、メタデータに保存され、アセンブリのスコープに重大な影響があり、アプリケーションによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-103">An assembly's name is stored in metadata and has a significant impact on the assembly's scope and use by an application.</span></span> <span data-ttu-id="9c5f9-104">厳密な名前のアセンブリには、アセンブリの名前、カルチャ、公開キー、バージョン番号を含む、完全修飾名があります。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-104">A strong-named assembly has a fully qualified name that includes the assembly's name, culture, public key, and version number.</span></span> <span data-ttu-id="9c5f9-105">これは、表示名として、また、<xref:System.Reflection.Assembly.FullName%2A> プロパティを使用して取得できる読み込まれたアセンブリに対して、頻繁に参照されます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-105">This is frequently referred to as the display name, and for loaded assemblies can be obtained by using the <xref:System.Reflection.Assembly.FullName%2A> property.</span></span>  
  
 <span data-ttu-id="9c5f9-106">ランタイムはこの情報を使用して、アセンブリを検索し、同じ名前のその他のアセンブリと区別します。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-106">The runtime uses this information to locate the assembly and differentiate it from other assemblies with the same name.</span></span> <span data-ttu-id="9c5f9-107">たとえば、`myTypes` と呼ばれる厳密な名前のアセンブリは、次の完全修飾名を持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-107">For example, a strong-named assembly called `myTypes` could have the following fully qualified name:</span></span>  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
> <span data-ttu-id="9c5f9-108">プロセッサ アーキテクチャは、アセンブリのプロセッサ固有バージョンを許可するために、.NET Framework バージョン 2.0 のアセンブリ ID に追加されます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-108">Processor architecture is added to the assembly identity in the .NET Framework version 2.0, to allow processor-specific versions of assemblies.</span></span> <span data-ttu-id="9c5f9-109">ID のプロセッサ アーキテクチャ (たとえば、32 ビットおよび 64 ビットのプロセッサ固有バージョン) のみが異なる、アセンブリのバージョンを作成できます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-109">You can create versions of an assembly whose identity differs only by processor architecture, for example 32-bit and 64-bit processor-specific versions.</span></span> <span data-ttu-id="9c5f9-110">プロセッサ アーキテクチャは、厳密な名前には必要ありません。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-110">Processor architecture is not required for strong names.</span></span> <span data-ttu-id="9c5f9-111">詳細については、<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-111">For more information, see <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9c5f9-112">この例の完全修飾名は、`myTypes` アセンブリには公開キー トークンを持つ厳密な名前があり、英語 (米国) のカルチャの値があり、1.0.1234.0 のバージョン番号があることを示しています。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-112">In this example, the fully qualified name indicates that the `myTypes` assembly has a strong name with a public key token, has the culture value for US English, and has a version number of 1.0.1234.0.</span></span> <span data-ttu-id="9c5f9-113">そのプロセッサ アーキテクチャは "msil" です。つまり、オペレーティング システムやプロセッサに応じて、32 ビット コードまたは 64 ビット コードに Just-In-Time (JIT) でコンパイルされるということです。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-113">Its processor architecture is "msil", which means that it will be just-in-time (JIT)-compiled to 32-bit code or 64-bit code depending on the operating system and processor.</span></span>  
  
 <span data-ttu-id="9c5f9-114">アセンブリの型を要求するコードは、完全修飾のアセンブリ名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-114">Code that requests types in an assembly must use a fully qualified assembly name.</span></span> <span data-ttu-id="9c5f9-115">これは、完全修飾のバインドと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-115">This is called fully qualified binding.</span></span> <span data-ttu-id="9c5f9-116">アセンブリ名のみを指定する部分的バインドは、.NET Framework のアセンブリを参照している場合は許可されません。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-116">Partial binding, which specifies only an assembly name, is not permitted when referencing assemblies in the .NET Framework.</span></span>  
  
 <span data-ttu-id="9c5f9-117">また、.NET Framework を構成するアセンブリを参照するアセンブリにはすべて、アセンブリの完全修飾名も含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-117">All assembly references to assemblies that make up the .NET Framework must also contain the fully qualified name of the assembly.</span></span> <span data-ttu-id="9c5f9-118">たとえば、バージョン 1.0 の System.Data .NET Framework アセンブリを参照するには、次が含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-118">For example, a reference to the System.Data .NET Framework assembly for version 1.0 would include:</span></span>  
  
```  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
```  
  
 <span data-ttu-id="9c5f9-119">このバージョンは、.NET Framework バージョン 1.0 に同梱されているすべての .NET Framework アセンブリのバージョン番号に対応しています。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-119">Note that the version corresponds to the version number of all .NET Framework assemblies that shipped with .NET Framework version 1.0.</span></span> <span data-ttu-id="9c5f9-120">.NET Framework アセンブリでは、カルチャの値は常にニュートラルであり、公開キーは上記の例に示したものと同じです。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-120">For .NET Framework assemblies, the culture value is always neutral, and the public key is the same as shown in the above example.</span></span>  
  
 <span data-ttu-id="9c5f9-121">たとえば、トレース リスナーを設定するために、構成ファイルにアセンブリ参照を追加するには、システムの .NET Framework アセンブリの完全修飾名を含めます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-121">For example, to add an assembly reference in a configuration file to set up a trace listener, you would include the fully qualified name of the system .NET Framework assembly:</span></span>  
  
```xml  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
> <span data-ttu-id="9c5f9-122">アセンブリをバインドするときに、ランタイムは大文字と小文字を区別せずにアセンブリ名を扱いますが、アセンブリ名に使用されている大文字と小文字を保持します。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-122">The runtime treats assembly names as case-insensitive when binding to an assembly, but preserves whatever case is used in an assembly name.</span></span> <span data-ttu-id="9c5f9-123">Windows SDK のいくつかのツールでは、アセンブリ名の大文字小文字を区別して処理します。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-123">Several tools in the Windows SDK handle assembly names as case-sensitive.</span></span> <span data-ttu-id="9c5f9-124">最適な結果を得るには、大文字と小文字を区別するものとして、アセンブリ名を管理します。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-124">For best results, manage assembly names as though they were case-sensitive.</span></span>  
  
## <a name="name-application-components"></a><span data-ttu-id="9c5f9-125">アプリケーション コンポーネントの名前を指定する</span><span class="sxs-lookup"><span data-stu-id="9c5f9-125">Name application components</span></span>  
 <span data-ttu-id="9c5f9-126">アセンブリの ID を特定するときに、ランタイムではファイル名が考慮されません。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-126">The runtime does not consider the file name when determining an assembly's identity.</span></span> <span data-ttu-id="9c5f9-127">アセンブリ名、バージョン、カルチャ、厳密な名前で構成されるアセンブリ ID は、ランタイムに対して明確である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-127">The assembly identity, which consists of the assembly name, version, culture, and strong name, must be clear to the runtime.</span></span>  
  
 <span data-ttu-id="9c5f9-128">たとえば、*myAssembly.dll* という名前のアセンブリを参照する *myAssembly.exe* という名前のアセンブリがある場合は、*myAssembly.exe* を実行すると、バインドが正しく行われます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-128">For example, if you have an assembly called *myAssembly.exe* that references an assembly called *myAssembly.dll*, binding occurs correctly if you execute *myAssembly.exe*.</span></span> <span data-ttu-id="9c5f9-129">ただし、別のアプリケーションによってメソッド <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType> を使用して *myAssembly.exe* が実行された場合、ランタイムでは、*myAssembly.exe* で `myAssembly` へのバインドが要求されるときには、`myAssembly` は既に読み込まれているものと判断されます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-129">However, if another application executes *myAssembly.exe* using the method <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=nameWithType>, the runtime determines that `myAssembly` is already loaded when *myAssembly.exe* requests binding to `myAssembly`.</span></span> <span data-ttu-id="9c5f9-130">この場合、*myAssembly.dll* が読み込まれることはありません。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-130">In this case, *myAssembly.dll* is never loaded.</span></span> <span data-ttu-id="9c5f9-131">*myAssembly.exe* には要求された型が含まれていないため、<xref:System.TypeLoadException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-131">Because *myAssembly.exe* does not contain the requested type, a <xref:System.TypeLoadException> occurs.</span></span>  
  
 <span data-ttu-id="9c5f9-132">この問題を避けるには、アプリケーションを構成するアセンブリが、確実に同じアセンブリ名を持たないように、または異なるディレクトリに同じ名前を持つアセンブリを配置しないようにします。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-132">To avoid this problem, make sure the assemblies that make up your application do not have the same assembly name or place assemblies with the same name in different directories.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c5f9-133">.NET Framework では、グローバル アセンブリ キャッシュに厳密な名前のアセンブリを配置する場合は、アセンブリのファイル名がアセンブリ名と一致している必要があります ( *.exe* や *.dll* などのファイル名拡張子は除きます)。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-133">In the .NET Framework, if you put a strong-named assembly in the global assembly cache, the assembly's file name must match the assembly name, not including the file name extension, such as *.exe* or *.dll*.</span></span> <span data-ttu-id="9c5f9-134">たとえば、アセンブリのファイル名が *myAssembly.dll* である場合、アセンブリ名は `myAssembly` である必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-134">For example, if the file name of an assembly is *myAssembly.dll*, the assembly name must be `myAssembly`.</span></span> <span data-ttu-id="9c5f9-135">ルート アプリケーション ディレクトリにのみ展開されるプライベート アセンブリは、ファイル名とは異なるアセンブリ名を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="9c5f9-135">Private assemblies deployed only in the root application directory can have an assembly name that is different from the file name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c5f9-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c5f9-136">See also</span></span>

- [<span data-ttu-id="9c5f9-137">方法: アセンブリの完全修飾名を特定する</span><span class="sxs-lookup"><span data-stu-id="9c5f9-137">How to: Determine an assembly's fully qualified name</span></span>](find-fully-qualified-name.md)
- [<span data-ttu-id="9c5f9-138">アセンブリを作成する</span><span class="sxs-lookup"><span data-stu-id="9c5f9-138">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="9c5f9-139">厳密な名前付きアセンブリ</span><span class="sxs-lookup"><span data-stu-id="9c5f9-139">Strong-named assemblies</span></span>](strong-named.md)
- [<span data-ttu-id="9c5f9-140">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="9c5f9-140">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="9c5f9-141">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="9c5f9-141">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="9c5f9-142">アセンブリを使用したプログラム</span><span class="sxs-lookup"><span data-stu-id="9c5f9-142">Program with assemblies</span></span>](program.md)
