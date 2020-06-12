---
title: .NET での並列プログラミング
description: .NET での並列プログラミングについて説明します。 .NET ランタイム、クラス ライブラリ型、診断ツールを使用して、.NET 開発を簡略化します。
ms.date: 09/12/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- parallel programming
ms.assetid: 4d83c690-ad2d-489e-a2e0-b85b898a672d
ms.openlocfilehash: 02087cf58720388c64d8aba5424db0b54828219a
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661966"
---
# <a name="parallel-programming-in-net"></a><span data-ttu-id="70e38-104">.NET での並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="70e38-104">Parallel Programming in .NET</span></span>

<span data-ttu-id="70e38-105">多くのパーソナル コンピューターとワークステーションには、複数スレッドの同時実行を可能にする複数の CPU コアがあります。</span><span class="sxs-lookup"><span data-stu-id="70e38-105">Many personal computers and workstations have multiple CPU cores that enable multiple threads to be executed simultaneously.</span></span> <span data-ttu-id="70e38-106">ハードウェアを活用するには、コードを並列化して複数のプロセッサに負荷を分散します。</span><span class="sxs-lookup"><span data-stu-id="70e38-106">To take advantage of the hardware, you can parallelize your code to distribute work across multiple processors.</span></span>

<span data-ttu-id="70e38-107">以前は、並列化には低水準のスレッドおよびロックの操作が必要でした。</span><span class="sxs-lookup"><span data-stu-id="70e38-107">In the past, parallelization required low-level manipulation of threads and locks.</span></span> <span data-ttu-id="70e38-108">Visual Studio と .NET Framework では、ランタイム、クラス ライブラリの型、および診断ツールを提供することで、並列プログラミングのサポートを強化しています。</span><span class="sxs-lookup"><span data-stu-id="70e38-108">Visual Studio and the .NET Framework enhance support for parallel programming by providing a runtime, class library types, and diagnostic tools.</span></span> <span data-ttu-id="70e38-109">.NET Framework 4 で導入されたこれらの機能によって、並行開発が簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="70e38-109">These features, which were introduced with the .NET Framework 4, simplify parallel development.</span></span> <span data-ttu-id="70e38-110">スレッドやスレッド プールを直接操作することなく、効率的で詳細な、拡張性のある並列コードを自然な表現方法で記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="70e38-110">You can write efficient, fine-grained, and scalable parallel code in a natural idiom without having to work directly with threads or the thread pool.</span></span>

<span data-ttu-id="70e38-111">.NET Framework の並列プログラミング アーキテクチャの高度な概要を次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="70e38-111">The following illustration provides a high-level overview of the parallel programming architecture in the .NET Framework:</span></span>

![.NET 並列プログラミング アーキテクチャ](./media/tpl-architecture.png)

## <a name="related-topics"></a><span data-ttu-id="70e38-113">関連トピック</span><span class="sxs-lookup"><span data-stu-id="70e38-113">Related Topics</span></span>

|<span data-ttu-id="70e38-114">テクノロジ</span><span class="sxs-lookup"><span data-stu-id="70e38-114">Technology</span></span>|<span data-ttu-id="70e38-115">説明</span><span class="sxs-lookup"><span data-stu-id="70e38-115">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="70e38-116">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="70e38-116">Task Parallel Library (TPL)</span></span>](task-parallel-library-tpl.md)|<span data-ttu-id="70e38-117">並列バージョンの <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> ループおよび `For` ループを含む `ForEach` クラスに関するドキュメントと、非同期操作の推奨される表現方法を表す <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> クラスに関するドキュメントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="70e38-117">Provides documentation for the <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> class, which includes parallel versions of `For` and `ForEach` loops, and also for the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class, which represents the preferred way to express asynchronous operations.</span></span>|
|[<span data-ttu-id="70e38-118">Parallel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="70e38-118">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)|<span data-ttu-id="70e38-119">さまざまなシナリオでパフォーマンスを大幅に向上させる、LINQ to Objects の並列実装です。</span><span class="sxs-lookup"><span data-stu-id="70e38-119">A parallel implementation of LINQ to Objects that significantly improves performance in many scenarios.</span></span>|
|[<span data-ttu-id="70e38-120">並列プログラミングのデータ構造</span><span class="sxs-lookup"><span data-stu-id="70e38-120">Data Structures for Parallel Programming</span></span>](data-structures-for-parallel-programming.md)|<span data-ttu-id="70e38-121">スレッド セーフなコレクション クラス、軽量な同期型、および限定的な初期化の種類に関するドキュメントへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="70e38-121">Provides links to documentation for thread-safe collection classes, lightweight synchronization types, and types for lazy initialization.</span></span>|
|[<span data-ttu-id="70e38-122">並列診断ツール</span><span class="sxs-lookup"><span data-stu-id="70e38-122">Parallel Diagnostic Tools</span></span>](parallel-diagnostic-tools.md)|<span data-ttu-id="70e38-123">タスクと並列スタック向けの Visual Studio デバッガー ウィンドウ、および[コンカレンシー ビジュアライザー](/visualstudio/profiling/concurrency-visualizer)に関するドキュメントへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="70e38-123">Provides links to documentation for Visual Studio debugger windows for tasks and parallel stacks, and for the [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>|
|[<span data-ttu-id="70e38-124">PLINQ および TPL 用のカスタム パーティショナー</span><span class="sxs-lookup"><span data-stu-id="70e38-124">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)|<span data-ttu-id="70e38-125">パーティションのしくみと、既定のパーティションの設定方法または新しいパーティションの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70e38-125">Describes how partitioners work and how to configure the default partitioners or create a new partitioner.</span></span>|
|[<span data-ttu-id="70e38-126">タスク スケジューラ</span><span class="sxs-lookup"><span data-stu-id="70e38-126">Task Schedulers</span></span>](xref:System.Threading.Tasks.TaskScheduler)|<span data-ttu-id="70e38-127">スケジューラのしくみと既定のスケジューラの構成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="70e38-127">Describes how schedulers work and how the default schedulers may be configured.</span></span>|
|[<span data-ttu-id="70e38-128">PLINQ および TPL のラムダ式</span><span class="sxs-lookup"><span data-stu-id="70e38-128">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)|<span data-ttu-id="70e38-129">C# および Visual Basic のラムダ式について簡単に説明し、PLINQ およびタスク並列ライブラリでラムダ式を使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="70e38-129">Provides a brief overview of lambda expressions in C# and Visual Basic, and shows how they are used in PLINQ and the Task Parallel Library.</span></span>|
|[<span data-ttu-id="70e38-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="70e38-130">For Further Reading</span></span>](for-further-reading-parallel-programming.md)|<span data-ttu-id="70e38-131">.NET での並列プログラミングに関する追加の情報とサンプル リソースへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="70e38-131">Provides links to additional information and sample resources for parallel programming in .NET.</span></span>|

## <a name="see-also"></a><span data-ttu-id="70e38-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="70e38-132">See also</span></span>

- [<span data-ttu-id="70e38-133">非同期の概要</span><span class="sxs-lookup"><span data-stu-id="70e38-133">Async Overview</span></span>](../async.md)
- [<span data-ttu-id="70e38-134">マネージド スレッド処理</span><span class="sxs-lookup"><span data-stu-id="70e38-134">Managed Threading</span></span>](../threading/index.md)
