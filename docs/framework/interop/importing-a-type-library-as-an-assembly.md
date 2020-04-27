---
title: タイプ ライブラリのアセンブリとしてのインポート
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
ms.openlocfilehash: e1a21175bcabc72b86a328d4f73ecec37140c304
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107597"
---
# <a name="importing-a-type-library-as-an-assembly"></a><span data-ttu-id="7ce0c-102">タイプ ライブラリのアセンブリとしてのインポート</span><span class="sxs-lookup"><span data-stu-id="7ce0c-102">Importing a Type Library as an Assembly</span></span>

<span data-ttu-id="7ce0c-103">通常、COM 型の定義は、タイプ ライブラリに存在します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-103">COM type definitions usually reside in a type library.</span></span> <span data-ttu-id="7ce0c-104">これに対し、CLS 準拠のコンパイラはアセンブリ内に型のメタデータを生成します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-104">In contrast, CLS-compliant compilers produce type metadata in an assembly.</span></span> <span data-ttu-id="7ce0c-105">型情報の 2 つのソースは大きく異なります。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-105">The two sources of type information are quite different.</span></span> <span data-ttu-id="7ce0c-106">このトピックでは、タイプ ライブラリからメタデータを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-106">This topic describes techniques for generating metadata from a type library.</span></span> <span data-ttu-id="7ce0c-107">結果のアセンブリは相互運用機能アセンブリと呼ばれ、含まれる型情報により、.NET Framework アプリケーションで COM 型を使用できます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-107">The resulting assembly is called an interop assembly, and the type information it contains enables .NET Framework applications to use COM types.</span></span>

<span data-ttu-id="7ce0c-108">この型情報をアプリケーションに使用できるようにする 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-108">There are two ways to make this type information available to your application:</span></span>

- <span data-ttu-id="7ce0c-109">デザイン時専用の相互運用アセンブリの使用:.NET Framework 4 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-109">Using design-time-only interop assemblies: Beginning with the .NET Framework 4, you can instruct the compiler to embed type information from the interop assembly into your executable.</span></span> <span data-ttu-id="7ce0c-110">コンパイラは、アプリケーションで使用する型情報のみを埋め込みます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-110">The compiler embeds only the type information that your application uses.</span></span> <span data-ttu-id="7ce0c-111">アプリケーションで相互運用機能アセンブリを配置する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-111">You do not have to deploy the interop assembly with your application.</span></span> <span data-ttu-id="7ce0c-112">この手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-112">This is the recommended technique.</span></span>

- <span data-ttu-id="7ce0c-113">相互運用機能アセンブリの展開:相互運用機能アセンブリへの標準の参照を作成できます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-113">Deploying interop assemblies: You can create a standard reference to the interop assembly.</span></span> <span data-ttu-id="7ce0c-114">この場合、アプリケーションで相互運用機能アセンブリを展開する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-114">In this case, the interop assembly must be deployed with your application.</span></span> <span data-ttu-id="7ce0c-115">この手法を採用し、プライベートの COM コンポーネントを使用しない場合は、常に、マネージド コードに組み込む予定の COM コンポーネントの作成者によって発行されたプライマリ相互運用機能アセンブリ (PIA) を参照します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-115">If you employ this technique, and you are not using a private COM component, always reference the primary interop assembly (PIA) published by the author of the COM component you intend to incorporate in your managed code.</span></span> <span data-ttu-id="7ce0c-116">プライマリ相互運用機能アセンブリの生成と使用の詳細については、「[プライマリ相互運用機能](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-116">For more information about producing and using primary interop assemblies, see [Primary Interop Assemblies](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).</span></span>

<span data-ttu-id="7ce0c-117">設計時専用の相互運用機能アセンブリを使用する場合は、COM コンポーネントの作成者によってパブリッシュされたプライマリ相互運用機能アセンブリから型情報を埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-117">When you use design-time-only interop assemblies, you can embed type information from the primary interop assembly published by the author of the COM component.</span></span> <span data-ttu-id="7ce0c-118">ただし、アプリケーションを使用してプライマリ相互運用機能アセンブリを展開する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-118">However, you do not have to deploy the primary interop assembly with your application.</span></span>

<span data-ttu-id="7ce0c-119">設計時専用の相互運用機能アセンブリを使用すると、ほとんどのアプリケーションは、COM コンポーネントのすべての機能を使用しないため、アプリケーションのサイズが小さくなります。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-119">Using design-time-only interop assemblies reduces the size of your application, because most applications do not use all the features of a COM component.</span></span> <span data-ttu-id="7ce0c-120">型情報を埋め込む場合に、コンパイラは非常に効率的です。アプリケーションが、COM インターフェイスでメソッドの一部のみを使用する場合、コンパイラは、使用されないメソッドを埋め込みません。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-120">The compiler is very efficient when it embeds type information; if your application uses only some of the methods on a COM interface, the compiler does not embed the unused methods.</span></span> <span data-ttu-id="7ce0c-121">型情報が埋め込まれているアプリケーションが、そのような別のアプリケーションと対話するか、プライマリ相互運用機能アセンブリを使用するアプリケーションと対話する場合、共通言語ランタイムは、型等価性の規則を使用して、同じ名前の 2 つの型が同じ COM 型を表すかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-121">When an application that has embedded type information interacts with another such application, or interacts with an application that uses a primary interop assembly, the common language runtime uses type equivalence rules to determine whether two types with the same name represent the same COM type.</span></span> <span data-ttu-id="7ce0c-122">COM オブジェクトを使用するためにこれらの規則を理解する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-122">You do not have to know these rules to use COM objects.</span></span> <span data-ttu-id="7ce0c-123">ただし、規則に興味がある場合は、「[Type Equivalence and Embedded Interop Types](type-equivalence-and-embedded-interop-types.md)」(型の等価性と埋め込まれた相互運用機能型) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-123">However, if you are interested in the rules, see [Type Equivalence and Embedded Interop Types](type-equivalence-and-embedded-interop-types.md).</span></span>

## <a name="generating-metadata"></a><span data-ttu-id="7ce0c-124">メタデータ ファイルの生成</span><span class="sxs-lookup"><span data-stu-id="7ce0c-124">Generating Metadata</span></span>

<span data-ttu-id="7ce0c-125">COM タイプ ライブラリには、Loanlib.tlb などの .tlb 拡張子を持つスタンドアロンのファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-125">COM type libraries can be stand-alone files that have a .tlb extension, such as Loanlib.tlb.</span></span> <span data-ttu-id="7ce0c-126">一部のタイプ ライブラリは、.dll または .exe ファイルのリソース セクションに埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-126">Some type libraries are embedded in the resource section of a .dll or .exe file.</span></span> <span data-ttu-id="7ce0c-127">タイプ ライブラリ情報の他のソースは、.olb ファイルおよび .ocx ファイルです。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-127">Other sources of type library information are .olb and .ocx files.</span></span>

<span data-ttu-id="7ce0c-128">対象とする COM 型の実装を格納するタイプ ライブラリを特定した後は、型のメタデータを含む相互運用機能アセンブリを生成するための次のオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-128">After you locate the type library that contains the implementation of your target COM type, you have the following options for generating an interop assembly containing type metadata:</span></span>

- <span data-ttu-id="7ce0c-129">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7ce0c-129">Visual Studio</span></span>

  <span data-ttu-id="7ce0c-130">Visual Studio は、タイプ ライブラリ内の COM 型をアセンブリ内のメタデータに自動的に変換します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-130">Visual Studio automatically converts COM types in a type library to metadata in an assembly.</span></span> <span data-ttu-id="7ce0c-131">手順については、「[方法:タイプ ライブラリへの参照を追加する](how-to-add-references-to-type-libraries.md)」にあります。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-131">For instructions, see [How to: Add References to Type Libraries](how-to-add-references-to-type-libraries.md).</span></span>

- [<span data-ttu-id="7ce0c-132">タイプ ライブラリ インポーター (Tlbimp.exe)</span><span class="sxs-lookup"><span data-stu-id="7ce0c-132">Type Library Importer (Tlbimp.exe)</span></span>](../tools/tlbimp-exe-type-library-importer.md)

  <span data-ttu-id="7ce0c-133">タイプ ライブラリ インポーターは、結果の相互運用機能のファイルのメタデータを調整するコマンド ライン オプションを提供し、既存のタイプ ライブラリから型をインポートし、相互運用機能アセンブリと名前空間を生成します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-133">The Type Library Importer provides command-line options to adjust metadata in the resulting interop file, imports types from an existing type library, and generates an interop assembly and a namespace.</span></span> <span data-ttu-id="7ce0c-134">手順については、「[方法:相互運用機能アセンブリをタイプ ライブラリから生成する](how-to-generate-interop-assemblies-from-type-libraries.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-134">For instructions, see [How to: Generate Interop Assemblies from Type Libraries](how-to-generate-interop-assemblies-from-type-libraries.md).</span></span>

- <span data-ttu-id="7ce0c-135"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> クラス</span><span class="sxs-lookup"><span data-stu-id="7ce0c-135"><xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType> class</span></span>

  <span data-ttu-id="7ce0c-136">このクラスは、コクラスとタイプ ライブラリ内のインターフェイスをアセンブリ内のメタデータに変換するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-136">This class provides methods to convert coclasses and interfaces in a type library to metadata within an assembly.</span></span> <span data-ttu-id="7ce0c-137">これは Tlbimp.exe と同じメタデータ出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-137">It produces the same metadata output as Tlbimp.exe.</span></span> <span data-ttu-id="7ce0c-138">ただし、Tlbimp.exe とは異なり、<xref:System.Runtime.InteropServices.TypeLibConverter> クラスは、メモリ内のタイプ ライブラリをメタデータに変換できます。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-138">However, unlike Tlbimp.exe, the <xref:System.Runtime.InteropServices.TypeLibConverter> class can convert an in-memory type library to metadata.</span></span>

- <span data-ttu-id="7ce0c-139">カスタム ラッパー</span><span class="sxs-lookup"><span data-stu-id="7ce0c-139">Custom wrappers</span></span>

  <span data-ttu-id="7ce0c-140">タイプ ライブラリが使用できないか正しくない場合、1 つのオプションは、マネージド ソース コードでクラスまたはインターフェイスの重複する定義を作成することです。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-140">When a type library is unavailable or incorrect, one option is to create a duplicate definition of the class or interface in managed source code.</span></span> <span data-ttu-id="7ce0c-141">その後で、アセンブリ内のメタデータを生成するためにランタイムを対象とするコンパイラでソース コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-141">You then compile the source code with a compiler that targets the runtime to produce metadata in an assembly.</span></span>

  <span data-ttu-id="7ce0c-142">COM 型を手動で定義するには、次の項目へのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-142">To define COM types manually, you must have access to the following items:</span></span>

  - <span data-ttu-id="7ce0c-143">定義されているコクラスとインターフェイスの正確な説明。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-143">Precise descriptions of the coclasses and interfaces being defined.</span></span>

  - <span data-ttu-id="7ce0c-144">C# コンパイラなど、適切な .NET Framework のクラス定義を生成できるコンパイラ。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-144">A compiler, such as the C# compiler, that can generate the appropriate .NET Framework class definitions.</span></span>

  - <span data-ttu-id="7ce0c-145">タイプ ライブラリからアセンブリへの変換規則の知識。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-145">Knowledge of the type library-to-assembly conversion rules.</span></span>

  <span data-ttu-id="7ce0c-146">カスタム ラッパーの作成は、高度な手法です。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-146">Writing a custom wrapper is an advanced technique.</span></span> <span data-ttu-id="7ce0c-147">カスタム ラッパーを生成する方法の詳細については、「[標準ラッパーのカスタマイズ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-147">For additional information about how to generate a custom wrapper, see [Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).</span></span>

 <span data-ttu-id="7ce0c-148">COM 相互運用機能のインポート処理の詳細については、「[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))」(タイプ ライブラリからアセンブリへの変換の要約) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7ce0c-148">For more information about the COM interop import process, see [Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ce0c-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="7ce0c-149">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [<span data-ttu-id="7ce0c-150">.NET Framework への COM コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="7ce0c-150">Exposing COM Components to the .NET Framework</span></span>](exposing-com-components.md)
- <span data-ttu-id="7ce0c-151">[タイプ ライブラリからアセンブリへの変換の要約](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7ce0c-151">[Type Library to Assembly Conversion Summary](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))</span></span>
- [<span data-ttu-id="7ce0c-152">Tlbimp.exe (タイプ ライブラリ インポーター)</span><span class="sxs-lookup"><span data-stu-id="7ce0c-152">Tlbimp.exe (Type Library Importer)</span></span>](../tools/tlbimp-exe-type-library-importer.md)
- <span data-ttu-id="7ce0c-153">[標準ラッパーのカスタマイズ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7ce0c-153">[Customizing Standard Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))</span></span>
- <span data-ttu-id="7ce0c-154">[マネージド コードでの COM 型の使用](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7ce0c-154">[Using COM Types in Managed Code](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))</span></span>
- [<span data-ttu-id="7ce0c-155">相互運用プロジェクトのコンパイル</span><span class="sxs-lookup"><span data-stu-id="7ce0c-155">Compiling an Interop Project</span></span>](compiling-an-interop-project.md)
- [<span data-ttu-id="7ce0c-156">相互運用アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="7ce0c-156">Deploying an Interop Application</span></span>](deploying-an-interop-application.md)
- [<span data-ttu-id="7ce0c-157">方法: タイプ ライブラリへの参照を追加する</span><span class="sxs-lookup"><span data-stu-id="7ce0c-157">How to: Add References to Type Libraries</span></span>](how-to-add-references-to-type-libraries.md)
- [<span data-ttu-id="7ce0c-158">方法: 相互運用機能アセンブリをタイプ ライブラリから生成する</span><span class="sxs-lookup"><span data-stu-id="7ce0c-158">How to: Generate Interop Assemblies from Type Libraries</span></span>](how-to-generate-interop-assemblies-from-type-libraries.md)
