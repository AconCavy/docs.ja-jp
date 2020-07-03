---
title: マネージド スレッド処理の基本
description: 例外、データの同期、フォアグラウンド スレッドとバックグラウンド スレッド、ローカル ストレージなど、マネージド スレッド処理に関する他の記事へのリンクを示します。
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework], multiple threads
- threading [.NET Framework], about threading
- managed threading
ms.assetid: b2944911-0e8f-427d-a8bb-077550618935
ms.openlocfilehash: d4a4ceabf29bd0f6f537e59ba477f9da686b1ef5
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769094"
---
# <a name="managed-threading-basics"></a><span data-ttu-id="ec67e-103">マネージド スレッド処理の基本</span><span class="sxs-lookup"><span data-stu-id="ec67e-103">Managed threading basics</span></span>

<span data-ttu-id="ec67e-104">このセクションの最初の 5 つのトピックは、マネージド スレッド処理を使用するタイミングを判断するのに役立つように設計されており、また、いくつかの基本的な機能について説明するためのものです。</span><span class="sxs-lookup"><span data-stu-id="ec67e-104">The first five topics of this section are designed to help you determine when to use managed threading and to explain some basic features.</span></span> <span data-ttu-id="ec67e-105">その他の機能を提供するクラスについては、「[スレッド処理オブジェクトと機能](threading-objects-and-features.md)」と「[同期プリミティブの概要](overview-of-synchronization-primitives.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ec67e-105">For information on classes that provide additional features, see [Threading Objects and Features](threading-objects-and-features.md) and [Overview of Synchronization Primitives](overview-of-synchronization-primitives.md).</span></span>  
  
 <span data-ttu-id="ec67e-106">このセクションの残りのトピックには、マネージド スレッド処理と Windows オペレーティング システムとの相互作用など、高度なトピックが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ec67e-106">The rest of the topics in this section cover advanced topics, including the interaction of managed threading with the Windows operating system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ec67e-107">.NET Framework 4 では、タスク並列ライブラリと PLINQ によって、マルチスレッド プログラムでのタスクとデータの並列処理のための API が提供されます。</span><span class="sxs-lookup"><span data-stu-id="ec67e-107">In the .NET Framework 4, the Task Parallel Library and PLINQ provide APIs for task and data parallelism in multi-threaded programs.</span></span> <span data-ttu-id="ec67e-108">詳細については、[並列プログラミング](../parallel-programming/index.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="ec67e-108">For more information, see [Parallel Programming](../parallel-programming/index.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec67e-109">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="ec67e-109">In this section</span></span>

 [<span data-ttu-id="ec67e-110">スレッドおよびスレッド処理</span><span class="sxs-lookup"><span data-stu-id="ec67e-110">Threads and Threading</span></span>](threads-and-threading.md)  
 <span data-ttu-id="ec67e-111">複数のスレッドの利点と欠点について説明し、スレッドを作成またはスレッド プール スレッドを使用する可能性のあるシナリオの概要を示します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-111">Discusses the advantages and drawbacks of multiple threads, and outlines the scenarios in which you might create threads or use thread pool threads.</span></span>  
  
 [<span data-ttu-id="ec67e-112">マネージド スレッドの例外</span><span class="sxs-lookup"><span data-stu-id="ec67e-112">Exceptions in Managed Threads</span></span>](exceptions-in-managed-threads.md)  
 <span data-ttu-id="ec67e-113">さまざまなバージョンの .NET Framework のスレッドでのハンドルされていない例外の動作、特に、アプリケーションの終了の原因となる状況について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-113">Describes the behavior of unhandled exceptions in threads for different versions of the .NET Framework, in particular the situations in which they result in termination of the application.</span></span>  
  
 [<span data-ttu-id="ec67e-114">マルチスレッド処理のためのデータの同期</span><span class="sxs-lookup"><span data-stu-id="ec67e-114">Synchronizing Data for Multithreading</span></span>](synchronizing-data-for-multithreading.md)  
 <span data-ttu-id="ec67e-115">複数のスレッドで使用されるクラスのデータを同期する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-115">Describes strategies for synchronizing data in classes that will be used with multiple threads.</span></span>  
  
 [<span data-ttu-id="ec67e-116">フォアグラウンド スレッドとバックグラウンド スレッド</span><span class="sxs-lookup"><span data-stu-id="ec67e-116">Foreground and Background Threads</span></span>](foreground-and-background-threads.md)  
 <span data-ttu-id="ec67e-117">フォアグラウンド スレッドとバック グラウンド スレッドの違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-117">Explains the differences between foreground and background threads.</span></span>  
  
 [<span data-ttu-id="ec67e-118">Windows でのマネージド スレッド処理とアンマネージド スレッド処理</span><span class="sxs-lookup"><span data-stu-id="ec67e-118">Managed and Unmanaged Threading in Windows</span></span>](managed-and-unmanaged-threading-in-windows.md)  
 <span data-ttu-id="ec67e-119">マネージド スレッド処理とアンマネージド スレッド処理の関係について説明し、Windows のスレッド処理 API に相当するマネージド API をリストし、COM アパートメントとマネージド スレッドの相互作用について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-119">Discusses the relationship between managed and unmanaged threading, lists managed equivalents for Windows threading APIs, and discusses the interaction of COM apartments and managed threads.</span></span>  
  
 [<span data-ttu-id="ec67e-120">スレッド ローカル ストレージ:スレッド相対静的フィールドとデータ スロット</span><span class="sxs-lookup"><span data-stu-id="ec67e-120">Thread Local Storage: Thread-Relative Static Fields and Data Slots</span></span>](thread-local-storage-thread-relative-static-fields-and-data-slots.md)  
 <span data-ttu-id="ec67e-121">スレッド相対ストレージ メカニズムについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-121">Describes thread-relative storage mechanisms.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ec67e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec67e-122">Reference</span></span>

 <xref:System.Threading.Thread>  
 <span data-ttu-id="ec67e-123">**Thread** クラスのリファレンス ドキュメントです。このクラスは、アンマネージド コードから作成されたか、マネージド アプリケーションで作成されたかにかかわらず、マネージド スレッドを表します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-123">Provides reference documentation for the **Thread** class, which represents a managed thread, whether it came from unmanaged code or was created in a managed application.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="ec67e-124">ユーザー インターフェイス オブジェクトと共にマルチスレッドを実装するための安全な方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-124">Provides a safe way to implement multithreading in conjunction with user-interface objects.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec67e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="ec67e-125">Related sections</span></span>

 [<span data-ttu-id="ec67e-126">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="ec67e-126">Overview of Synchronization Primitives</span></span>](overview-of-synchronization-primitives.md)  
 <span data-ttu-id="ec67e-127">複数のスレッドのアクティビティを同期するために使用されるマネージド クラスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-127">Describes the managed classes used to synchronize the activities of multiple threads.</span></span>  
  
 [<span data-ttu-id="ec67e-128">マネージド スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="ec67e-128">Managed Threading Best Practices</span></span>](managed-threading-best-practices.md)  
 <span data-ttu-id="ec67e-129">マルチスレッドに関する一般的な問題と、問題を回避するための方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-129">Describes common problems with multithreading and strategies for avoiding problems.</span></span>  
  
 [<span data-ttu-id="ec67e-130">並列プログラミング</span><span class="sxs-lookup"><span data-stu-id="ec67e-130">Parallel Programming</span></span>](../parallel-programming/index.md)  
 <span data-ttu-id="ec67e-131">非同期およびマルチスレッドの .NET Framework アプリケーションを作成する作業を大幅に簡素化する、タスク並列ライブラリと PLINQ について説明します。</span><span class="sxs-lookup"><span data-stu-id="ec67e-131">Describes the Task Parallel Library and PLINQ, which greatly simplify the work of creating asynchronous and multi-threaded .NET Framework applications.</span></span>
