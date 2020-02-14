---
title: デバッグ、トレース、およびプロファイリング
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
ms.openlocfilehash: 1a43c7fbcb810b22ff9bc409c233d2b1da67370e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217399"
---
# <a name="debugging-tracing-and-profiling"></a><span data-ttu-id="9a50d-102">デバッグ、トレース、およびプロファイリング</span><span class="sxs-lookup"><span data-stu-id="9a50d-102">Debugging, Tracing, and Profiling</span></span>
<span data-ttu-id="9a50d-103">.NET Framework アプリケーションをデバッグするには、アプリケーションにデバッガーをアタッチできるようにコンパイラとランタイム環境を構成する必要があり、可能であれば、アプリケーションとそれに対応する Microsoft Intermediate Language (MSIL) について記号マップと行マップの両方を生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9a50d-103">To debug a .NET Framework application, the compiler and runtime environment must be configured to enable a debugger to attach to the application and to produce both symbols and line maps, if possible, for the application and its corresponding Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="9a50d-104">マネージド アプリケーションのデバッグが完了した後は、パフォーマンスを向上するようにプロファイルできます。</span><span class="sxs-lookup"><span data-stu-id="9a50d-104">After a managed application has been debugged, it can be profiled to boost performance.</span></span> <span data-ttu-id="9a50d-105">プロファイルでは、最も頻繁に実行されるコードを生成するソース コード行と、そのコードの実行に要する時間を評価して記述します。</span><span class="sxs-lookup"><span data-stu-id="9a50d-105">Profiling evaluates and describes the lines of source code that generate the most frequently executed code, and how much time it takes to execute them.</span></span>  
  
 <span data-ttu-id="9a50d-106">.NET Framework アプリケーションは、構成の詳細の多くを処理する Visual Studio を使用すると容易にデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="9a50d-106">.NET Framework applications are easily debugged by using Visual Studio, which handles many of the configuration details.</span></span> <span data-ttu-id="9a50d-107">Visual Studio がインストールされていない場合は、.NET Framework の <xref:System.Diagnostics> 名前空間に含まれるデバッグ用のクラスを使用して .NET Framework アプリケーションのパフォーマンスを確認して向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="9a50d-107">If Visual Studio is not installed, you can examine and improve the performance of .NET Framework applications by using the debugging classes in the .NET Framework <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="9a50d-108">この名前空間には、実行フローをトレースするためのクラスとして <xref:System.Diagnostics.Trace>、<xref:System.Diagnostics.Debug>、および <xref:System.Diagnostics.TraceSource> が含まれ、コードをプロファイルするためのクラスとして <xref:System.Diagnostics.Process>、<xref:System.Diagnostics.EventLog>、および <xref:System.Diagnostics.PerformanceCounter> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="9a50d-108">This namespace includes the <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, and <xref:System.Diagnostics.TraceSource> classes for tracing execution flow, and the <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, and <xref:System.Diagnostics.PerformanceCounter> classes for profiling code.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9a50d-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9a50d-109">In This Section</span></span>  
 [<span data-ttu-id="9a50d-110">JIT アタッチ デバッグの有効化</span><span class="sxs-lookup"><span data-stu-id="9a50d-110">Enabling JIT-Attach Debugging</span></span>](enabling-jit-attach-debugging.md)  
 <span data-ttu-id="9a50d-111">.NET Framework アプリケーションにデバッグ エンジンを JIT アタッチするようにレジストリを構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9a50d-111">Shows how to configure the registry to JIT-attach a debug engine to a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="9a50d-112">イメージのデバッグの簡略化</span><span class="sxs-lookup"><span data-stu-id="9a50d-112">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)  
 <span data-ttu-id="9a50d-113">アセンブリをデバッグしやすくするために JIT 追跡を有効にし、最適化を無効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9a50d-113">Shows how to turn JIT tracking on and optimization off to make an assembly easier to debug.</span></span>  
  
 [<span data-ttu-id="9a50d-114">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="9a50d-114">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)  
 <span data-ttu-id="9a50d-115">アプリケーションの実行中にアプリケーションの実行をモニターする方法、アプリケーションの実行が順調かどうか、何かの障害が発生しているかどうかを表示するようにアプリケーションをインストルメント化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a50d-115">Describes how to monitor the execution of your application while it is running, and how to instrument it to display how well it is performing or whether something has gone wrong.</span></span>  
  
 [<span data-ttu-id="9a50d-116">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="9a50d-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)  
 <span data-ttu-id="9a50d-117">マネージド デバッグ アシスタント (MDA) について説明します。これは、共通言語ランタイム (CLR: Common Language Runtime) と連携してランタイム状態に関する情報を提供するデバッグ支援ツールです。</span><span class="sxs-lookup"><span data-stu-id="9a50d-117">Describes managed debugging assistants (MDAs), which are debugging aids that work in conjunction with the common language runtime (CLR) to provide information on runtime state.</span></span>  
  
 [<span data-ttu-id="9a50d-118">デバッガー表示属性によるデバッグ機能の拡張</span><span class="sxs-lookup"><span data-stu-id="9a50d-118">Enhancing Debugging with the Debugger Display Attributes</span></span>](enhancing-debugging-with-the-debugger-display-attributes.md)  
 <span data-ttu-id="9a50d-119">型の開発者が、その型をデバッガーで表示した場合にどのように見えるかを指定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a50d-119">Describes how the developer of a type can specify what that type will look like when it is displayed in a debugger.</span></span>  
  
 [<span data-ttu-id="9a50d-120">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="9a50d-120">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="9a50d-121">アプリケーションのパフォーマンスを追跡するために使用できるカウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="9a50d-121">Describes the counters that you can use to track the performance of an application.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9a50d-122">関連セクション</span><span class="sxs-lookup"><span data-stu-id="9a50d-122">Related Sections</span></span>  
 [<span data-ttu-id="9a50d-123">Visual Studio での ASP.NET または ASP.NET Core アプリのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9a50d-123">Debug ASP.NET or ASP.NET Core apps in Visual Studio</span></span>](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 <span data-ttu-id="9a50d-124">開発時と配置後に ASP.NET アプリケーションをデバッグするための要件と手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="9a50d-124">Provides prerequisites and instructions for how to debug an ASP.NET application during development or after deployment.</span></span>  
  
 [<span data-ttu-id="9a50d-125">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="9a50d-125">Development Guide</span></span>](../development-guide.md)  
 <span data-ttu-id="9a50d-126">アプリケーションの作成、構成、デバッグ、セキュリティ、配置、および動的プログラミング、相互運用性、拡張性、メモリ管理、スレッド処理に関する情報を含む、アプリケーション開発用の主要な技術領域とタスクのすべてについての手引書です。</span><span class="sxs-lookup"><span data-stu-id="9a50d-126">Provides a guide to all key technology areas and tasks for application development, including creating, configuring, debugging, securing, and deploying your application, and information about dynamic programming, interoperability, extensibility, memory management, and threading.</span></span>
