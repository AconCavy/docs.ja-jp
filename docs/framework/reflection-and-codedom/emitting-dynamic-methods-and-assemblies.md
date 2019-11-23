---
title: 動的メソッドおよびアセンブリの出力
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: 4578b708b10e93a7f5def5b9dc040eeb646bdc8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130231"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a><span data-ttu-id="09c70-102">動的メソッドおよびアセンブリの出力</span><span class="sxs-lookup"><span data-stu-id="09c70-102">Emitting Dynamic Methods and Assemblies</span></span>

<span data-ttu-id="09c70-103">ここでは、<xref:System.Reflection.Emit> 名前空間のマネージド型のセットについて説明します。これらのマネージド型を使用すると、コンパイラやツールでメタデータおよび Microsoft Intermediate Language (MSIL) を実行時に出力できます。また、ポータブル実行可能 (PE) ファイルをディスク上に生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="09c70-103">This section describes a set of managed types in the <xref:System.Reflection.Emit> namespace that allow a compiler or tool to emit metadata and Microsoft intermediate language (MSIL) at run time and optionally generate a portable executable (PE) file on disk.</span></span> <span data-ttu-id="09c70-104">この名前空間を使用する主な機能は、スクリプト エンジンとコンパイラです。</span><span class="sxs-lookup"><span data-stu-id="09c70-104">Script engines and compilers are the primary users of this namespace.</span></span> <span data-ttu-id="09c70-105">ここでは、リフレクション出力と呼ばれる <xref:System.Reflection.Emit> 名前空間の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="09c70-105">In this section, the functionality provided by the <xref:System.Reflection.Emit> namespace is referred to as reflection emit.</span></span>  
  
<span data-ttu-id="09c70-106">リフレクション出力は、以下の機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="09c70-106">Reflection emit provides the following capabilities:</span></span>  
  
- <span data-ttu-id="09c70-107">実行時に <xref:System.Reflection.Emit.DynamicMethod> クラスを使用して軽量のグローバル メソッドを定義し、デリゲートを使用してそのメソッドを実行します。</span><span class="sxs-lookup"><span data-stu-id="09c70-107">Define lightweight global methods at run time, using the <xref:System.Reflection.Emit.DynamicMethod> class, and execute them using delegates.</span></span>  
  
- <span data-ttu-id="09c70-108">実行時にアセンブリを定義し、次に、それらを実行するか、ディスクに保存します。</span><span class="sxs-lookup"><span data-stu-id="09c70-108">Define assemblies at run time and then run them and/or save them to disk.</span></span>  
  
- <span data-ttu-id="09c70-109">実行時にアセンブリを定義し、それらを実行した後、それらをアンロードし、ガベージ コレクションがリソースを再利用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="09c70-109">Define assemblies at run time, run them, and then unload them and allow garbage collection to reclaim their resources.</span></span>  
  
- <span data-ttu-id="09c70-110">実行時に新しいアセンブリのモジュールを定義し、次に、モジュールを実行するか、ディスクに保存します。</span><span class="sxs-lookup"><span data-stu-id="09c70-110">Define modules in new assemblies at run time and then run and/or save them to disk.</span></span>  
  
- <span data-ttu-id="09c70-111">実行時にモジュール内の型を定義し、その型のインスタンスを作成してメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="09c70-111">Define types in modules at run time, create instances of these types, and invoke their methods.</span></span>  
  
- <span data-ttu-id="09c70-112">デバッガーまたはコード プロファイラなどのツールで使用できる、定義されたモジュールのシンボリック情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="09c70-112">Define symbolic information for defined modules that can be used by tools such as debuggers and code profilers.</span></span>  
  
<span data-ttu-id="09c70-113"><xref:System.Reflection.Emit> 名前空間のマネージド型に加えて、アンマネージド メタデータ インターフェイスもあります。これについては、[メタデータ インターフェイス](../unmanaged-api/metadata/metadata-interfaces.md)に関するリファレンス ドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="09c70-113">In addition to the managed types in the <xref:System.Reflection.Emit> namespace, there are unmanaged metadata interfaces which are described in the [Metadata Interfaces](../unmanaged-api/metadata/metadata-interfaces.md) reference documentation.</span></span> <span data-ttu-id="09c70-114">マネージド リフレクション出力は、アンマネージド メタデータ インターフェイスよりも強力なセマンティック エラー チェック機能、より高水準なメタデータの抽象化クラスを提供します。</span><span class="sxs-lookup"><span data-stu-id="09c70-114">Managed reflection emit provides stronger semantic error checking and a higher level of abstraction of the metadata than the unmanaged metadata interfaces.</span></span>  
  
<span data-ttu-id="09c70-115">メタデータと MSIL を使用する際に役立つリソースとしては、他に、共通言語基盤 (CLI: Common Language Infrastructure) のドキュメント、特に「Partition II: Metadata Definition and Semantics」と「Partition III: CIL Instruction Set」などもあります。</span><span class="sxs-lookup"><span data-stu-id="09c70-115">Another useful resource for working with metadata and MSIL is the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics" and "Partition III: CIL Instruction Set".</span></span> <span data-ttu-id="09c70-116">このドキュメントは、オンラインの [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) と [Ecma の Web サイト](https://go.microsoft.com/fwlink/?LinkId=116487)で参照できます。</span><span class="sxs-lookup"><span data-stu-id="09c70-116">The documentation is available online on [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) and at the [Ecma Web site](https://go.microsoft.com/fwlink/?LinkId=116487).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09c70-117">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="09c70-117">In This Section</span></span>
  
[<span data-ttu-id="09c70-118">リフレクション出力のセキュリティ関連事項</span><span class="sxs-lookup"><span data-stu-id="09c70-118">Security issues in reflection emit</span></span>](security-issues-in-reflection-emit.md)  
<span data-ttu-id="09c70-119">リフレクション出力を使用した動的アセンブリの作成時のセキュリティ関連事項について説明します。</span><span class="sxs-lookup"><span data-stu-id="09c70-119">Describes security issues related to creating dynamic assemblies using reflection emit.</span></span>  

<span data-ttu-id="09c70-120">[方法: 動的メソッドを定義および実行する](how-to-define-and-execute-dynamic-methods.md) </span><span class="sxs-lookup"><span data-stu-id="09c70-120">[How to: Define and execute dynamic methods](how-to-define-and-execute-dynamic-methods.md) </span></span>  
<span data-ttu-id="09c70-121">単純な動的メソッドおよびクラスのインスタンスにバインドされる動的メソッドを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09c70-121">Shows how to execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>

<span data-ttu-id="09c70-122">[方法: リフレクション出力を使用してジェネリック型を定義する](how-to-define-a-generic-type-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="09c70-122">[How to: Define a generic type with reflection emit](how-to-define-a-generic-type-with-reflection-emit.md) </span></span>  
<span data-ttu-id="09c70-123">2 つの型パラメーターを持つ単純なジェネリック型を作成する方法、クラス制約、インターフェイス制約、特殊な制約を型パラメーターに適用する方法、パラメーターの型や戻り値の型としてクラスの型パラメーターを使用するメンバーを作成する方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="09c70-123">Shows how to create a simple generic type with two type parameters, how to apply class, interface, and special constraints to the type parameters, and how to create members that use the type parameters of the class as parameter types and return types.</span></span>

<span data-ttu-id="09c70-124">[方法: リフレクション出力を使用してジェネリック メソッドを定義する](how-to-define-a-generic-method-with-reflection-emit.md) </span><span class="sxs-lookup"><span data-stu-id="09c70-124">[How to: Define a generic method with reflection emit](how-to-define-a-generic-method-with-reflection-emit.md) </span></span>  
<span data-ttu-id="09c70-125">単純なジェネリック メソッドを作成、出力および呼び出す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="09c70-125">Shows how to create, emit, and invoke a simple generic method.</span></span>

<span data-ttu-id="09c70-126">[動的な型生成のための収集可能なアセンブリ](collectible-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="09c70-126">[Collectible assemblies for dynamic type generation](collectible-assemblies.md) </span></span>  
<span data-ttu-id="09c70-127">そのアセンブリが作成されたアプリケーション ドメインをアンロードせずにアンロードできる動的アセンブリである、収集可能なアセンブリについて説明します。</span><span class="sxs-lookup"><span data-stu-id="09c70-127">Introduces collectible assemblies, which are dynamic assemblies that can be unloaded without unloading the application domain in which they were created.</span></span>
  
## <a name="reference"></a><span data-ttu-id="09c70-128">参照</span><span class="sxs-lookup"><span data-stu-id="09c70-128">Reference</span></span>  

<xref:System.Reflection.Emit.OpCodes>  
<span data-ttu-id="09c70-129">メソッド本体の構築に使用できる MSIL 命令コードのカタログを作成します。</span><span class="sxs-lookup"><span data-stu-id="09c70-129">Catalogs the MSIL instruction codes you can use to build method bodies.</span></span>  
  
<xref:System.Reflection.Emit>  
<span data-ttu-id="09c70-130">動的メソッド、アセンブリ、および型の出力に使用するマネージド クラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="09c70-130">Contains managed classes used to emit dynamic methods, assemblies, and types.</span></span>  
  
<xref:System.Type>  
<span data-ttu-id="09c70-131"><xref:System.Type> クラスについて説明します。このクラスは、マネージド リフレクションとリフレクション出力の型を表し、これらのテクノロジを使用するうえで重要なクラスです。</span><span class="sxs-lookup"><span data-stu-id="09c70-131">Describes the <xref:System.Type> class, which represents types in managed reflection and reflection emit, and which is key to the use of these technologies.</span></span>  
  
<xref:System.Reflection>  
<span data-ttu-id="09c70-132">メタデータとマネージド コードの探索に使用するマネージド クラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="09c70-132">Contains managed classes used to explore metadata and managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09c70-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="09c70-133">Related Sections</span></span>  

[<span data-ttu-id="09c70-134">リフレクション</span><span class="sxs-lookup"><span data-stu-id="09c70-134">Reflection</span></span>](reflection.md)  
<span data-ttu-id="09c70-135">メタデータとマネージド コードの探索方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="09c70-135">Explains how to explore metadata and managed code.</span></span>  
  
[<span data-ttu-id="09c70-136">.NET のアセンブリ</span><span class="sxs-lookup"><span data-stu-id="09c70-136">Assemblies in .NET</span></span>](../../standard/assembly/index.md)  
<span data-ttu-id="09c70-137">.NET 実装のアセンブリの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="09c70-137">Provides an overview of assemblies in .NET implementations.</span></span>
