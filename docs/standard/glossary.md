---
title: .NET 用語集
description: .NET のドキュメントで使われている用語からいくつか選択してその意味を説明します。
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: b79580baa12cc8081346678f06d49a9d0455375c
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2020
ms.locfileid: "89415011"
---
# <a name="net-glossary"></a><span data-ttu-id="66a4b-103">.NET 用語集</span><span class="sxs-lookup"><span data-stu-id="66a4b-103">.NET Glossary</span></span>

<span data-ttu-id="66a4b-104">この用語集の主な目的は、.NET のドキュメントで定義なしに頻繁に出現する用語と頭字語の意味を明確にすることです。</span><span class="sxs-lookup"><span data-stu-id="66a4b-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="66a4b-105">AOT</span><span class="sxs-lookup"><span data-stu-id="66a4b-105">AOT</span></span>

<span data-ttu-id="66a4b-106">Ahead Of Time コンパイラ。</span><span class="sxs-lookup"><span data-stu-id="66a4b-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="66a4b-107">[JIT](#jit) と同様に、このコンパイラも [IL](#il) をマシン コードに変換します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="66a4b-108">JIT コンパイルとは異なり、AOT コンパイルはアプリケーションが実行される前に行われ、通常は、別のコンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="66a4b-109">AOT ツール チェーンは実行時にコンパイルされないので、コンパイルに費やされる時間を最小限に抑える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="66a4b-109">Because AOT tool chains don't compile at run time, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="66a4b-110">つまり、より多くの時間を最適化に費やすことができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="66a4b-111">AOT のコンテキストはアプリケーション全体であるため、AOT コンパイラはモジュール間のリンクとプログラム全体の分析も実行します。これは、すべての参照が追跡されて、1 つの実行可能ファイルが生成されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="66a4b-112">「[CoreRT](#corert)」と「[.NET Native](#net-native)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="66a4b-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="66a4b-113">ASP.NET</span></span>

<span data-ttu-id="66a4b-114">.NET Framework に付属している ASP.NET の元の実装。</span><span class="sxs-lookup"><span data-stu-id="66a4b-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="66a4b-115">ASP.NET は、ASP.NET Core を含む ASP.NET の両方の実装を指す包括的な用語として使われることがあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="66a4b-116">どちらを意味するかはコンテキストによって決まります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="66a4b-117">両方の実装を意味するために ASP.NET を使っているのではないことを明確にしたい場合は、ASP.NET 4.x を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="66a4b-118">[ASP.NET のドキュメント](/aspnet/#pivot=aspnet)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="66a4b-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="66a4b-119">ASP.NET Core</span></span>

<span data-ttu-id="66a4b-120">ASP.NET のクロスプラットフォームで高パフォーマンスなオープンソースの実装。</span><span class="sxs-lookup"><span data-stu-id="66a4b-120">A cross-platform, high-performance, open-source implementation of ASP.NET.</span></span>

<span data-ttu-id="66a4b-121">[ASP.NET Core のドキュメント](/aspnet/#pivot=core)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="66a4b-122">アセンブリ</span><span class="sxs-lookup"><span data-stu-id="66a4b-122">assembly</span></span>

<span data-ttu-id="66a4b-123">アプリケーションまたは他のアセンブリから呼び出すことができる API のコレクションを含む *.dll*/ *.exe* ファイル。</span><span class="sxs-lookup"><span data-stu-id="66a4b-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="66a4b-124">アセンブリは、インターフェイス、クラス、構造体、列挙型、デリゲートなどの種類を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="66a4b-125">プロジェクトの *bin* フォルダー内のアセンブリは、"*バイナリ*" と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="66a4b-126">「[ライブラリ](#library)」もご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-126">See also [library](#library).</span></span>

## <a name="bcl"></a><span data-ttu-id="66a4b-127">BCL</span><span class="sxs-lookup"><span data-stu-id="66a4b-127">BCL</span></span>

<span data-ttu-id="66a4b-128">基本クラス ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="66a4b-128">Base Class Library.</span></span> <span data-ttu-id="66a4b-129">"*フレームワーク ライブラリ*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-129">Also known as *framework libraries*.</span></span>

<span data-ttu-id="66a4b-130">System.\* (および限られた範囲の Microsoft.\*) 名前空間を構成するライブラリのセット。</span><span class="sxs-lookup"><span data-stu-id="66a4b-130">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="66a4b-131">BCL は汎用の下位レベル フレームワークであり、ASP.NET Core などの上位レベル アプリケーション フレームワークはそれを基にして構築されています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-131">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span>

<span data-ttu-id="66a4b-132">[.NET 5 (および .NET Core) 以降のバージョン](#net-5-and-later-versions)用の BCL のソース コードは、[.NET ランタイム リポジトリ](https://github.com/dotnet/runtime)に含まれています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-132">The source code of the BCL for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions) is contained in the [.NET runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="66a4b-133">この新しい .NET の実装用の BCL API の大部分は、.NET Framework でも使用できるため、このソース コードは、.NET Framework BCL ソース コードが分岐したものと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-133">The majority of the BCL APIs for this newer implementation of .NET are also available in .NET Framework, so you can think of this source code as a fork of the .NET Framework BCL source code.</span></span>

## <a name="clr"></a><span data-ttu-id="66a4b-134">CLR</span><span class="sxs-lookup"><span data-stu-id="66a4b-134">CLR</span></span>

<span data-ttu-id="66a4b-135">共通言語ランタイム (Common Language Runtime)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-135">Common Language Runtime.</span></span>

<span data-ttu-id="66a4b-136">厳密な意味はコンテキストによって異なります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-136">The exact meaning depends on the context.</span></span> <span data-ttu-id="66a4b-137">共通言語ランタイムは、通常、[.NET Framework](#net-framework) のランタイム、または [.NET 5 (および .NET Core) 以降のバージョン](#net-5-and-later-versions)のランタイムを指します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-137">Common Language Runtime usually refers to the runtime of [.NET Framework](#net-framework) or the runtime of [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

<span data-ttu-id="66a4b-138">CLR によって、メモリの割り当てと管理が処理されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-138">A CLR handles memory allocation and management.</span></span> <span data-ttu-id="66a4b-139">CLR は、アプリの実行だけでなく、[JIT](#jit) コンパイラを使って実行時にコードを生成してコンパイルする仮想マシンでもあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-139">A CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span>

<span data-ttu-id="66a4b-140">.NET Framework の CLR 実装は Windows のみです。</span><span class="sxs-lookup"><span data-stu-id="66a4b-140">The CLR implementation for .NET Framework is Windows only.</span></span>

<span data-ttu-id="66a4b-141">.NET 5 以降のバージョンの CLR 実装 (Core CLR とも呼ばれる) は、.NET Framework CLR と同じコード ベースから構築されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-141">The CLR implementation for .NET 5 and later versions (also known as the Core CLR) is built from the same code base as the .NET Framework CLR.</span></span> <span data-ttu-id="66a4b-142">当初は、Core CLR は Silverlight のランタイムであり、複数のプラットフォーム (特に Windows と OS X) で実行するように設計されていました。これはまだ[クロスプラットフォーム](#cross-platform) ランタイムですが、多くの Linux ディストリビューションのサポートが含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="66a4b-142">Originally, the Core CLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span>

<span data-ttu-id="66a4b-143">「[ランタイム](#runtime)」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-143">See also [runtime](#runtime).</span></span>

## <a name="core-clr"></a><span data-ttu-id="66a4b-144">Core CLR</span><span class="sxs-lookup"><span data-stu-id="66a4b-144">Core CLR</span></span>

<span data-ttu-id="66a4b-145">[.NET 5 (および .NET Core) 以降のバージョン](#net-5-and-later-versions)の共通言語ランタイム。</span><span class="sxs-lookup"><span data-stu-id="66a4b-145">The Common Language Runtime for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

<span data-ttu-id="66a4b-146">「[CLR](#clr)」を参照してください</span><span class="sxs-lookup"><span data-stu-id="66a4b-146">See [CLR](#clr)</span></span>

## <a name="corert"></a><span data-ttu-id="66a4b-147">CoreRT</span><span class="sxs-lookup"><span data-stu-id="66a4b-147">CoreRT</span></span>

<span data-ttu-id="66a4b-148">[CLR](#clr) とは異なり、CoreRT は仮想マシンではありません。つまり、[JIT](#jit) が含まれないため、実行時にコードを生成して実行する機能はありません。</span><span class="sxs-lookup"><span data-stu-id="66a4b-148">In contrast to the [CLR](#clr), CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="66a4b-149">ただし、[GC](#gc) およびランタイム型識別 (RTTI) とリフレクションの機能は備えています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-149">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="66a4b-150">ただ、CoreRT の型システムはリフレクション用のメタデータが必要ないように設計されています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="66a4b-151">メタデータが必要ないと、[AOT](#aot) ツール チェーンで余分なメタデータのリンクを削除し、(さらに重要なこととして) アプリが使っていないコードを特定することができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-151">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="66a4b-152">CoreRT は開発中です。</span><span class="sxs-lookup"><span data-stu-id="66a4b-152">CoreRT is in development.</span></span>

<span data-ttu-id="66a4b-153">[.NET Native と CoreRT の概要](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="66a4b-154">クロスプラットフォーム</span><span class="sxs-lookup"><span data-stu-id="66a4b-154">cross-platform</span></span>

<span data-ttu-id="66a4b-155">Linux、Windows、iOS など、複数の異なるオペレーティング システム上で使用できるアプリケーションを開発し、実行することができます。OS ごとに作成し直す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="66a4b-155">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="66a4b-156">そのため、異なるプラットフォーム上のアプリケーション間でコードを再利用し、一貫性を保つことができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-156">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="66a4b-157">エコシステム</span><span class="sxs-lookup"><span data-stu-id="66a4b-157">ecosystem</span></span>

<span data-ttu-id="66a4b-158">特定のテクノロジ用のアプリケーションを構築して実行するために使われるすべての実行時ソフトウェア、開発ツール、およびコミュニティ リソース。</span><span class="sxs-lookup"><span data-stu-id="66a4b-158">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="66a4b-159">".NET エコシステム" という用語は ".NET スタック" などの用語と似ていますが、サードパーティのアプリとライブラリを含む点が異なります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-159">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="66a4b-160">文章での使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-160">Here's an example in a sentence:</span></span>

- <span data-ttu-id="66a4b-161">"[.NET Standard](#net-standard) の背後にある意図は、.NET エコシステムの高度な統一性を確立することです。"</span><span class="sxs-lookup"><span data-stu-id="66a4b-161">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="66a4b-162">フレームワーク</span><span class="sxs-lookup"><span data-stu-id="66a4b-162">framework</span></span>

<span data-ttu-id="66a4b-163">一般に、特定のテクノロジに基づくアプリケーションの開発と展開を容易にする API の包括的なコレクション。</span><span class="sxs-lookup"><span data-stu-id="66a4b-163">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="66a4b-164">この一般的な意味でのアプリケーション フレームワークの例としては、ASP.NET Core や Windows フォームなどがあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-164">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="66a4b-165">「[ライブラリ](#library)」もご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-165">See also [library](#library).</span></span>

<span data-ttu-id="66a4b-166">以下の用語の "フレームワーク" という単語には、別の意味があります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-166">The word "framework" has a different meaning in the following terms:</span></span>

- [<span data-ttu-id="66a4b-167">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="66a4b-167">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="66a4b-168">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="66a4b-168">target framework</span></span>](#target-framework)
- [<span data-ttu-id="66a4b-169">TFM (ターゲット フレームワーク モニカー)</span><span class="sxs-lookup"><span data-stu-id="66a4b-169">TFM (target framework moniker)</span></span>](#tfm)
- [<span data-ttu-id="66a4b-170">フレームワークに依存するアプリ</span><span class="sxs-lookup"><span data-stu-id="66a4b-170">framework-dependent app</span></span>](../core/deploying/index.md#publish-framework-dependent)

<span data-ttu-id="66a4b-171">従来の .NET ドキュメントでは、"フレームワーク" は [.NET の実装](#implementation-of-net)を指している場合があります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-171">In legacy .NET documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="66a4b-172">たとえば、ある記事では .NET 5 をフレームワークと呼んでいる場合があります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-172">For example, an article may call .NET 5 a framework.</span></span>

## <a name="gc"></a><span data-ttu-id="66a4b-173">[GC]</span><span class="sxs-lookup"><span data-stu-id="66a4b-173">GC</span></span>

<span data-ttu-id="66a4b-174">ガベージ コレクター (Garbage Collector)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-174">Garbage collector.</span></span>

<span data-ttu-id="66a4b-175">ガベージ コレクターは、自動メモリ管理の実装です。</span><span class="sxs-lookup"><span data-stu-id="66a4b-175">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="66a4b-176">GC は、使われなくなったオブジェクトによって占有されているメモリを解放します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-176">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="66a4b-177">「[ガベージ コレクション](garbage-collection/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-177">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="66a4b-178">IL</span><span class="sxs-lookup"><span data-stu-id="66a4b-178">IL</span></span>

<span data-ttu-id="66a4b-179">中間言語 (Intermediate Language)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-179">Intermediate language.</span></span>

<span data-ttu-id="66a4b-180">C# などの高レベル .NET 言語は、中間言語 (IL) と呼ばれるハードウェアに依存しない命令セットにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-180">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="66a4b-181">IL は、MSIL (Microsoft IL) や CIL (Common IL) などと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-181">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="66a4b-182">JIT</span><span class="sxs-lookup"><span data-stu-id="66a4b-182">JIT</span></span>

<span data-ttu-id="66a4b-183">Just-In-Time コンパイラ。</span><span class="sxs-lookup"><span data-stu-id="66a4b-183">Just-in-time compiler.</span></span>

<span data-ttu-id="66a4b-184">[AOT](#aot) と同様に、このコンパイラは [IL](#il) をプロセッサが理解するマシン コードに変換します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-184">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="66a4b-185">AOT とは異なり、JIT のコンパイルはオンデマンドで行われ、コードを実行する必要があるコンピューター上で実行されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-185">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="66a4b-186">JIT コンパイルはアプリケーションの実行中に行われるため、コンパイル時間は実行時間の一部になります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-186">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="66a4b-187">したがって、JIT コンパイラでは、コードの最適化に要する時間と、結果のコードによって得られる時間の節約のバランスを考える必要があります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-187">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="66a4b-188">ただし、JIT は実際のハードウェアを認識するので、開発者はさまざまな実装を出荷する必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-188">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="66a4b-189">.NET の実装</span><span class="sxs-lookup"><span data-stu-id="66a4b-189">implementation of .NET</span></span>

<span data-ttu-id="66a4b-190">.NET の実装には次のものが含まれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-190">An implementation of .NET includes:</span></span>

- <span data-ttu-id="66a4b-191">1 つまたは複数のランタイム。</span><span class="sxs-lookup"><span data-stu-id="66a4b-191">One or more runtimes.</span></span> <span data-ttu-id="66a4b-192">次に例を示します。 [CLR](#clr)、[CoreRT](#corert)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-192">Examples: [CLR](#clr), [CoreRT](#corert).</span></span>
- <span data-ttu-id="66a4b-193">.NET Standard の 1 つのバージョンを実装し、他の API を含むことができるクラス ライブラリ。</span><span class="sxs-lookup"><span data-stu-id="66a4b-193">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="66a4b-194">たとえば、[.NET Framework](#net-framework) および [.NET 5 (および .NET Core) 以降のバージョン](#net-5-and-later-versions)の [BCL](#bcl) です。</span><span class="sxs-lookup"><span data-stu-id="66a4b-194">Examples: the [BCLs](#bcl) for [.NET Framework](#net-framework) and [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>
- <span data-ttu-id="66a4b-195">必要に応じて、1 つまたは複数のアプリケーション フレームワーク。</span><span class="sxs-lookup"><span data-stu-id="66a4b-195">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="66a4b-196">次に例を示します。 .NET Framework と .NET 5 には、[ASP.NET](#aspnet)、Windows フォーム、WPF が含まれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-196">Examples: [ASP.NET](#aspnet), Windows Forms, and WPF are included in the .NET Framework and .NET 5.</span></span>
- <span data-ttu-id="66a4b-197">必要に応じて、開発ツール。</span><span class="sxs-lookup"><span data-stu-id="66a4b-197">Optionally, development tools.</span></span> <span data-ttu-id="66a4b-198">一部の開発ツールは、複数の実装間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-198">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="66a4b-199">.NET の実装の例:</span><span class="sxs-lookup"><span data-stu-id="66a4b-199">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="66a4b-200">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="66a4b-200">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="66a4b-201">.NET 5 以降のバージョン (.NET Core 2.1 から 3.1 を含む)</span><span class="sxs-lookup"><span data-stu-id="66a4b-201">.NET 5 and later versions (including .NET Core 2.1-3.1</span></span>](#net-5-and-later-versions)
- [<span data-ttu-id="66a4b-202">ユニバーサル Windows プラットフォーム (UWP)</span><span class="sxs-lookup"><span data-stu-id="66a4b-202">Universal Windows Platform (UWP)</span></span>](#uwp)
- [<span data-ttu-id="66a4b-203">Mono</span><span class="sxs-lookup"><span data-stu-id="66a4b-203">Mono</span></span>](#mono)

## <a name="library"></a><span data-ttu-id="66a4b-204">ライブラリ</span><span class="sxs-lookup"><span data-stu-id="66a4b-204">library</span></span>

<span data-ttu-id="66a4b-205">アプリまたは他のライブラリで呼び出すことができる API のコレクション。</span><span class="sxs-lookup"><span data-stu-id="66a4b-205">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="66a4b-206">.NET ライブラリは 1 つ以上の[アセンブリ](#assembly)で構成されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-206">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="66a4b-207">ライブラリと[フレームワーク](#framework)は同義語として使われることがよくあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-207">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="mono"></a><span data-ttu-id="66a4b-208">Mono</span><span class="sxs-lookup"><span data-stu-id="66a4b-208">Mono</span></span>

<span data-ttu-id="66a4b-209">Mono はオープン ソースであり、主に小規模なランタイムが必要な場合に使用される[クロスプラットフォーム](#cross-platform)の .NET 実装です。</span><span class="sxs-lookup"><span data-stu-id="66a4b-209">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="66a4b-210">Android、Mac、iOS、tvOS、および watchOS 上の Xamarin アプリケーションで利用されるランタイムであり、フットプリントの小さいアプリに重点が置かれています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-210">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="66a4b-211">現在公開されているすべての .NET Standard バージョンをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-211">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="66a4b-212">これまで Mono は .NET Framework の多数の API を実装し、Unix で人気の高い機能の一部をエミュレートしていました。</span><span class="sxs-lookup"><span data-stu-id="66a4b-212">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="66a4b-213">また、Unix のそのような機能に依存する .NET アプリケーションを実行するために使用されることもあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-213">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="66a4b-214">一般的に Mono は、[Just-In-Time コンパイラ](#jit)と共に使用されますが、iOS のようなプラットフォームに使用される完全な[静的コンパイラ (Ahead Of Time コンパイル)](#aot) としても機能します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-214">Mono is typically used with a [just-in-time compiler](#jit), but it also features a full [static compiler (ahead-of-time compilation)](#aot) that is used on platforms like iOS.</span></span>

<span data-ttu-id="66a4b-215">[Mono のドキュメント](https://www.mono-project.com/docs/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-215">See the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="66a4b-216">.NET</span><span class="sxs-lookup"><span data-stu-id="66a4b-216">.NET</span></span>

<span data-ttu-id="66a4b-217">[.NET Standard](#net-standard) とすべての [.NET の実装](#implementation-of-net)およびワークロードを表す包括的な用語。</span><span class="sxs-lookup"><span data-stu-id="66a4b-217">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="66a4b-218">常にすべて大文字で表し、".Net" とは表記されません。</span><span class="sxs-lookup"><span data-stu-id="66a4b-218">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="66a4b-219">[.NET 5](#net-5-and-later-versions) (現在、プレビュー段階) がリリースされると、すべての新しい .NET 開発で推奨される .NET 実装となります。そのため、一部のコンテキストでは、".NET" は ".NET 5 以降のバージョン" を意味します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-219">When [.NET 5](#net-5-and-later-versions) (currently in preview) is released, it will be the recommended .NET implementation for all new .NET development, and so in some contexts ".NET" will imply ".NET 5 and later versions."</span></span>

<span data-ttu-id="66a4b-220">[.NET の基礎](../fundamentals/index.yml)に関するページを参照してください</span><span class="sxs-lookup"><span data-stu-id="66a4b-220">See [.NET fundamentals](../fundamentals/index.yml)</span></span>

## <a name="net-5-and-later-versions"></a><span data-ttu-id="66a4b-221">.NET 5 以降のバージョン</span><span class="sxs-lookup"><span data-stu-id="66a4b-221">.NET 5 and later versions</span></span>

<span data-ttu-id="66a4b-222">.NET のクロスプラットフォームで高パフォーマンスなオープンソースの実装。</span><span class="sxs-lookup"><span data-stu-id="66a4b-222">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="66a4b-223">共通言語ランタイム ([CLR](#clr))、[AOT](#aot) ランタイム ([CoreRT](#corert)。開発中)、基本クラス ライブラリ ([BCL](#bcl))、および [.NET SDK](#net-sdk) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-223">Includes a Common Language Runtime ([CLR](#clr)), an [AOT](#aot) runtime ([CoreRT](#corert), in development), a Base Class Library ([BCL](#bcl)), and the [.NET SDK](#net-sdk).</span></span>

<span data-ttu-id="66a4b-224">この .NET 実装の以前のバージョンは、.NET Core と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-224">Earlier versions of this .NET implementation are known as .NET Core.</span></span> <span data-ttu-id="66a4b-225">.Net 5.0 は、.NET Core 3.1 の次のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="66a4b-225">.NET 5.0 is the next version following .NET Core 3.1.</span></span> <span data-ttu-id="66a4b-226">バージョン 4 は、この .NET の新しい実装を、[.NET Framework](#net-framework) と呼ばれる古い実装と混同しないようにするためにスキップされました。</span><span class="sxs-lookup"><span data-stu-id="66a4b-226">Version 4 was skipped to avoid confusing this newer implementation of .NET with the older implementation that is known as [.NET Framework](#net-framework).</span></span> <span data-ttu-id="66a4b-227">.NET Framework の現在のバージョンは 4.8 です。</span><span class="sxs-lookup"><span data-stu-id="66a4b-227">The current version of .NET Framework is 4.8.</span></span>

<span data-ttu-id="66a4b-228">[.NET の基礎](../fundamentals/index.yml)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-228">See [.NET fundamentals](../fundamentals/index.yml).</span></span>

## <a name="net-cli"></a><span data-ttu-id="66a4b-229">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="66a4b-229">.NET CLI</span></span>

<span data-ttu-id="66a4b-230">[.NET 5 (および .NET Core) 以降のバージョン](#net-5-and-later-versions)用のアプリケーションとライブラリを開発するためのクロスプラットフォーム ツールチェーン。</span><span class="sxs-lookup"><span data-stu-id="66a4b-230">A cross-platform toolchain for developing applications and libraries for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span> <span data-ttu-id="66a4b-231">.NET Core CLI とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-231">Also known as the .NET Core CLI.</span></span>

<span data-ttu-id="66a4b-232">[.NET CLI](../core/tools/index.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-232">See [.NET CLI](../core/tools/index.md).</span></span>

## <a name="net-core"></a><span data-ttu-id="66a4b-233">.NET Core</span><span class="sxs-lookup"><span data-stu-id="66a4b-233">.NET Core</span></span>

<span data-ttu-id="66a4b-234">「[.NET 5.0 以降のバージョン](#net-5-and-later-versions)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-234">See [.NET 5 and later versions](#net-5-and-later-versions).</span></span>

## <a name="net-framework"></a><span data-ttu-id="66a4b-235">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="66a4b-235">.NET Framework</span></span>

<span data-ttu-id="66a4b-236">Windows でのみ動作する .NET の実装。</span><span class="sxs-lookup"><span data-stu-id="66a4b-236">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="66a4b-237">共通言語ランタイム ([CLR](#clr))、基本クラス ライブラリ ([BCL](#bcl))、および [ASP.NET](#aspnet)、Windows フォーム、WPF などのアプリケーション フレームワーク ライブラリが含まれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-237">Includes the Common Language Runtime ([CLR](#clr)), the Base Class Library ([BCL](#bcl)), and application framework libraries such as [ASP.NET](#aspnet), Windows Forms, and WPF.</span></span>

<span data-ttu-id="66a4b-238">「[.NET Framework ガイド](../framework/index.yml)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-238">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="66a4b-239">.NET Native</span><span class="sxs-lookup"><span data-stu-id="66a4b-239">.NET Native</span></span>

<span data-ttu-id="66a4b-240">Just-In-Time ([JIT](#jit)) ではなく、Ahead Of Time ([AOT](#aot)) でネイティブ コードを生成するコンパイラ ツール チェーン。</span><span class="sxs-lookup"><span data-stu-id="66a4b-240">A compiler tool chain that produces native code ahead-of-time ([AOT](#aot)), as opposed to just-in-time ([JIT](#jit)).</span></span>

<span data-ttu-id="66a4b-241">コンパイルは、C++ のコンパイラやリンカーと同様に、開発者のコンピューターで行われます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-241">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="66a4b-242">未使用のコードが削除され、より多くの時間がコードの最適化に費やされます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-242">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="66a4b-243">ライブラリからコードを抽出し、実行可能ファイルにそれらをマージします。</span><span class="sxs-lookup"><span data-stu-id="66a4b-243">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="66a4b-244">結果は、アプリ全体を表す 1 つのモジュールです。</span><span class="sxs-lookup"><span data-stu-id="66a4b-244">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="66a4b-245">UWP は、.NET Native によってサポートされる最初のアプリケーション フレームワークでした。</span><span class="sxs-lookup"><span data-stu-id="66a4b-245">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="66a4b-246">現在では、Windows、macOS、Linux 用のネイティブ コンソール アプリの構築がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-246">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="66a4b-247">「[Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)」(.NET Native と CoreRT の概要) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-247">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-sdk"></a><span data-ttu-id="66a4b-248">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="66a4b-248">.NET SDK</span></span>

<span data-ttu-id="66a4b-249">[.NET 5 (および .NET Core) 以降のバージョン](#net-5-and-later-versions)用の .NET アプリケーションとライブラリを開発者が作成できるようにする、一連のライブラリとツール。</span><span class="sxs-lookup"><span data-stu-id="66a4b-249">A set of libraries and tools that allow developers to create .NET applications and libraries for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span> <span data-ttu-id="66a4b-250">.NET Core SDK とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-250">Also known as the .NET Core SDK.</span></span>

<span data-ttu-id="66a4b-251">アプリ構築用の [.NET CLI](#net-cli)、アプリの構築および実行用の .NET ライブラリとランタイム、CLI コマンドとアプリケーションを実行する dotnet 実行可能ファイル (*dotnet.exe*) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-251">Includes the [.NET CLI](#net-cli) for building apps, .NET libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="66a4b-252">[.NET SDK の概要](../core/sdk.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-252">See [.NET SDK Overview](../core/sdk.md).</span></span>

## <a name="net-standard"></a><span data-ttu-id="66a4b-253">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="66a4b-253">.NET Standard</span></span>

<span data-ttu-id="66a4b-254">.NET の各実装で使用可能な .NET API の正式な仕様。</span><span class="sxs-lookup"><span data-stu-id="66a4b-254">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="66a4b-255">.NET Standard の仕様は、ドキュメントではライブラリとも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-255">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="66a4b-256">ライブラリには仕様 (インターフェイス) だけでなく API の実装も含まれるため、.NET Standard を "ライブラリ" と呼ぶのは誤解を招きます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-256">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span>

<span data-ttu-id="66a4b-257">「[.NET Standard](net-standard.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-257">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="66a4b-258">NGEN</span><span class="sxs-lookup"><span data-stu-id="66a4b-258">NGEN</span></span>

<span data-ttu-id="66a4b-259">ネイティブ (イメージ) 生成。</span><span class="sxs-lookup"><span data-stu-id="66a4b-259">Native (image) generation.</span></span>

<span data-ttu-id="66a4b-260">このテクノロジは、永続的な [JIT](#jit) コンパイラと考えることができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-260">You can think of this technology as a persistent [JIT](#jit) compiler.</span></span> <span data-ttu-id="66a4b-261">通常はコードが実行されるコンピューター上でコードをコンパイルしますが、一般にコンパイルはインストール時に行われます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-261">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="66a4b-262">package</span><span class="sxs-lookup"><span data-stu-id="66a4b-262">package</span></span>

<span data-ttu-id="66a4b-263">NuGet パッケージ &mdash; または単にパッケージ &mdash; は、同じ名前の 1 つまたは複数のアセンブリと、作成者名などの追加メタデータを含む、 *.zip* ファイルです。</span><span class="sxs-lookup"><span data-stu-id="66a4b-263">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="66a4b-264">*.zip* ファイルは、拡張子が *.nupkg* であり、複数のターゲット フレームワークとバージョンで使う *.dll* ファイルや *.xml* ファイルなどのアセットを含むことができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-264">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="66a4b-265">アプリまたはライブラリでインストールされるときに、アプリまたはライブラリで指定されているターゲット フレームワークに基づいて適切なアセットが選択されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-265">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="66a4b-266">インターフェイスを定義するアセットは *ref* フォルダーにあり、実装を定義するアセットは *lib* フォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-266">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="66a4b-267">platform</span><span class="sxs-lookup"><span data-stu-id="66a4b-267">platform</span></span>

<span data-ttu-id="66a4b-268">オペレーティング システムとそれが動作するハードウェア (Windows、macOS、Linux、iOS、Android)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-268">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="66a4b-269">文章での使用例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-269">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="66a4b-270">".NET Core は、.NET のクロスプラットフォームの実装です。"</span><span class="sxs-lookup"><span data-stu-id="66a4b-270">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="66a4b-271">"PCL プロファイルは Microsoft のプラットフォームを表し、.NET Standard はプラットフォームに依存しません。"</span><span class="sxs-lookup"><span data-stu-id="66a4b-271">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="66a4b-272">従来の .NET のドキュメントでは、[.NET の実装](#implementation-of-net)、またはすべての実装を含む .NET [スタック](#stack)の意味で ".NET プラットフォーム" が使われることがあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-272">Legacy .NET documentation sometimes uses ".NET platform" to mean either an [implementation of .NET](#implementation-of-net) or the .NET [stack](#stack) including all implementations.</span></span> <span data-ttu-id="66a4b-273">これらの使用法はどちらも本来の (OS およびハードウェア) の意味と紛らわしい場合があるので、これらの使用法は避けるようにしています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-273">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we try to avoid these usages.</span></span>

<span data-ttu-id="66a4b-274">"開発者プラットフォーム" という語句の "プラットフォーム" には、別の意味があります。これは、アプリをビルドして実行するためのツールとライブラリを提供するソフトウェアを指します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-274">"Platform" has a different meaning in the phrase "developer platform," which refers to software that provides tools and libraries for building and running apps.</span></span> <span data-ttu-id="66a4b-275">.NET は、さまざまな種類のアプリケーションをビルドするためのクロスプラットフォームでオープンソースの開発者プラットフォームです。</span><span class="sxs-lookup"><span data-stu-id="66a4b-275">.NET is a cross-platform, open source developer platform for building many different types of applications.</span></span>

## <a name="runtime"></a><span data-ttu-id="66a4b-276">ランタイム</span><span class="sxs-lookup"><span data-stu-id="66a4b-276">runtime</span></span>

<span data-ttu-id="66a4b-277">一般的には、マネージド プログラムの実行環境です。</span><span class="sxs-lookup"><span data-stu-id="66a4b-277">In general, the execution environment for a managed program.</span></span> <span data-ttu-id="66a4b-278">OS は、ランタイム環境の一部ですが、.NET ランタイムの一部ではありません。</span><span class="sxs-lookup"><span data-stu-id="66a4b-278">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="66a4b-279">この単語の意味での .NET ランタイムの例をいくつか以下に示します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-279">Here are some examples of .NET runtimes in this sense of the word:</span></span>

- <span data-ttu-id="66a4b-280">共通言語ランタイム ([CLR](#clr))</span><span class="sxs-lookup"><span data-stu-id="66a4b-280">Common Language Runtime ([CLR](#clr))</span></span>
- <span data-ttu-id="66a4b-281">.NET Native (UWP の場合)</span><span class="sxs-lookup"><span data-stu-id="66a4b-281">.NET Native (for UWP)</span></span>
- <span data-ttu-id="66a4b-282">Mono ランタイム</span><span class="sxs-lookup"><span data-stu-id="66a4b-282">Mono runtime</span></span>

<span data-ttu-id="66a4b-283">以下のコンテキストでの "ランタイム" という単語には、別の意味があります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-283">The word "runtime" has a different meaning in the following contexts:</span></span>

* <span data-ttu-id="66a4b-284">[.NET ダウンロード ページ](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-284">The [.NET download page](https://dotnet.microsoft.com/download).</span></span>

  <span data-ttu-id="66a4b-285">ここでの "ランタイム" は、[CLR](#clr) と [BCL](#bcl) (フレームワーク ライブラリ) を合わせた意味となります。これは、コンピューター上で[フレームワークに依存する](../core/deploying/index.md#publish-framework-dependent)アプリを実行できるように、そのコンピューターにダウンロードしてインストールすることができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-285">"Runtime" here means the [CLR](#clr) together with the [BCL](#bcl) (framework libraries), that you can download and install on a machine so that you can run [framework-dependent](../core/deploying/index.md#publish-framework-dependent) apps on the machine.</span></span>

* <span data-ttu-id="66a4b-286">[.NET 5 (および .NET Core) 以降のバージョン](#net-5-and-later-versions)の[ランタイム識別子 (RID)](../core/rid-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-286">The [Runtime Identifier (RID)](../core/rid-catalog.md) for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

  <span data-ttu-id="66a4b-287">ここでの "ランタイム" は、.NET アプリが実行されている OS プラットフォームと CPU アーキテクチャを意味します (例: `linux-x64`)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-287">"Runtime" here means the OS platform and CPU architecture that a .NET app runs on, for example: `linux-x64`.</span></span>

<span data-ttu-id="66a4b-288">従来の .NET ドキュメントでは、次の例に示すように、[.NET の実装](#implementation-of-net)の意味で "ランタイム" を使用することがあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-288">Legacy .NET documentation sometimes uses "runtime" in the sense of an [implementation of .NET](#implementation-of-net), as in the following examples:</span></span>

- <span data-ttu-id="66a4b-289">"さまざまな .NET ランタイムで、.NET Standard の特定のバージョンが実装されます。"</span><span class="sxs-lookup"><span data-stu-id="66a4b-289">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="66a4b-290">"複数のランタイムでの実行を意図したライブラリは、このフレームワークを対象とする必要があります。"</span><span class="sxs-lookup"><span data-stu-id="66a4b-290">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="66a4b-291">(.NET Standard を指している場合)</span><span class="sxs-lookup"><span data-stu-id="66a4b-291">(referring to .NET Standard)</span></span>
- <span data-ttu-id="66a4b-292">"さまざまな .NET ランタイムで、.NET Standard の特定のバージョンが実装されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-292">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="66a4b-293">…</span><span class="sxs-lookup"><span data-stu-id="66a4b-293">…</span></span> <span data-ttu-id="66a4b-294">.NET ランタイムの各バージョンは、サポートしている .NET Standard の最高のバージョンをアドバタイズします …"</span><span class="sxs-lookup"><span data-stu-id="66a4b-294">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

## <a name="stack"></a><span data-ttu-id="66a4b-295">スタック</span><span class="sxs-lookup"><span data-stu-id="66a4b-295">stack</span></span>

<span data-ttu-id="66a4b-296">全体としてアプリケーションの構築と実行に使われるプログラミング テクノロジのセット。</span><span class="sxs-lookup"><span data-stu-id="66a4b-296">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="66a4b-297">".NET スタック" は、.NET Standard および .NET のすべての実装を指します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-297">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="66a4b-298">".NET スタック" という語句が .NET の 1 つの実装を示すこともあります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-298">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="66a4b-299">ターゲット フレームワーク</span><span class="sxs-lookup"><span data-stu-id="66a4b-299">target framework</span></span>

<span data-ttu-id="66a4b-300">.NET アプリまたはライブラリが依存する API のコレクション。</span><span class="sxs-lookup"><span data-stu-id="66a4b-300">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="66a4b-301">アプリまたはライブラリでは、.NET Standard の 1 つのバージョン (.NET Standard 2.0 など) をターゲットにできます。これは、.NET のすべての実装で標準化された API のセットの仕様です。</span><span class="sxs-lookup"><span data-stu-id="66a4b-301">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is a specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="66a4b-302">また、アプリまたはライブラリは、.NET の特定の実装のバージョンをターゲットにすることもでき、その場合は実装固有の API にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-302">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="66a4b-303">たとえば、Xamarin.iOS をターゲットにするアプリは、Xamarin が提供する iOS API ラッパーにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-303">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="66a4b-304">一部のターゲット フレームワーク (.NET Framework など) では、使用可能な API は .NET の実装がシステムにインストールするアセンブリによって定義され、アプリケーション フレームワーク API (たとえば ASP.NET、WinForms) を含む場合があります。</span><span class="sxs-lookup"><span data-stu-id="66a4b-304">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="66a4b-305">パッケージ ベースのターゲット フレームワーク (.NET Standard、.NET Core など) では、フレームワーク API はアプリまたはライブラリでインストールされるパッケージによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-305">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="66a4b-306">その場合、ターゲット フレームワークで、全体としてフレームワークを構成するすべてのパッケージを参照するパッケージが暗黙的に指定されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-306">In that case, the target framework implicitly specifies a package that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="66a4b-307">「[ターゲット フレームワーク](frameworks.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-307">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="66a4b-308">TFM</span><span class="sxs-lookup"><span data-stu-id="66a4b-308">TFM</span></span>

<span data-ttu-id="66a4b-309">ターゲット フレームワーク モニカー (Target Framework Moniker)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-309">Target framework moniker.</span></span>

<span data-ttu-id="66a4b-310">.NET アプリまたはライブラリのターゲット フレームワークを指定するための標準化されたトークン形式。</span><span class="sxs-lookup"><span data-stu-id="66a4b-310">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="66a4b-311">通常、ターゲット フレームワークは短い名前によって参照されます (`net462` など)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-311">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="66a4b-312">長い形式の TFM (.NETFramework,Version=4.6.2 など) も存在しますが、一般に、ターゲット フレームワークの指定には使われません。</span><span class="sxs-lookup"><span data-stu-id="66a4b-312">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="66a4b-313">「[ターゲット フレームワーク](frameworks.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="66a4b-313">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="66a4b-314">UWP</span><span class="sxs-lookup"><span data-stu-id="66a4b-314">UWP</span></span>

<span data-ttu-id="66a4b-315">ユニバーサル Windows プラットフォーム (Universal Windows Platform)。</span><span class="sxs-lookup"><span data-stu-id="66a4b-315">Universal Windows Platform.</span></span>

<span data-ttu-id="66a4b-316">モノのインターネット (IoT) のために最新のタッチ対応の Windows アプリケーションとソフトウェアを構築するために使われる .NET の実装。</span><span class="sxs-lookup"><span data-stu-id="66a4b-316">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="66a4b-317">PC、タブレット、携帯電話、Xbox など、ターゲットにされる可能性があるさまざまな種類のデバイスを統一するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="66a4b-317">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="66a4b-318">UWP は、一元的なアプリ ストア、実行環境 (AppContainer)、Win32 の代わりに使う Windows API のセット (WinRT) など、多くのサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="66a4b-318">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="66a4b-319">アプリは、C++、C#、Visual Basic、および JavaScript で記述することができます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-319">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="66a4b-320">C# と Visual Basic を使用する場合は、.NET 5 (および .NET Core) 以降のバージョンで .NET API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="66a4b-320">When using C# and Visual Basic, the .NET APIs are provided by .NET 5 (and .NET Core) and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="66a4b-321">関連項目</span><span class="sxs-lookup"><span data-stu-id="66a4b-321">See also</span></span>

- [<span data-ttu-id="66a4b-322">.NET の基礎</span><span class="sxs-lookup"><span data-stu-id="66a4b-322">.NET fundamentals</span></span>](../fundamentals/index.yml)
- [<span data-ttu-id="66a4b-323">.NET Framework ガイド</span><span class="sxs-lookup"><span data-stu-id="66a4b-323">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="66a4b-324">ASP.NET の概要</span><span class="sxs-lookup"><span data-stu-id="66a4b-324">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="66a4b-325">ASP.NET Core の概要</span><span class="sxs-lookup"><span data-stu-id="66a4b-325">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
