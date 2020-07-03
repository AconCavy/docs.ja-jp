---
title: イベント ベースの非同期パターン (EAP)
description: .NET のイベント ベースの非同期パターン (EAP) に関する記事へのリンクを示します。これには、実装、ベスト プラクティス、EAP クライアントの実装などについての記事が含まれます。
ms.date: 07/23/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous calls
- asynchronous programming, design patterns
- asynchronous programming
ms.assetid: c6baed9f-2a25-4728-9a9a-53b7b14840cf
ms.openlocfilehash: 03b4d914d72b96b882c774565654c022b145b5f2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768873"
---
# <a name="event-based-asynchronous-pattern-eap"></a><span data-ttu-id="a9d91-103">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="a9d91-103">Event-based Asynchronous Pattern (EAP)</span></span>

<span data-ttu-id="a9d91-104">非同期機能をクライアント コードに公開する方法は数多くあります。</span><span class="sxs-lookup"><span data-stu-id="a9d91-104">There are a number of ways to expose asynchronous features to client code.</span></span> <span data-ttu-id="a9d91-105">イベント ベースの非同期パターンは、クラスが非同期動作を示す 1 つの方法を規定します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-105">The Event-based Asynchronous Pattern prescribes one way for classes to present asynchronous behavior.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9d91-106">.NET Framework 4 以降では、タスク並列ライブラリによって非同期/並列プログラミングの新しいモデルが提供されます。</span><span class="sxs-lookup"><span data-stu-id="a9d91-106">Starting with the .NET Framework 4, the Task Parallel Library provides a new model for asynchronous and parallel programming.</span></span> <span data-ttu-id="a9d91-107">詳細については、「[タスク並列ライブラリ (TPL)](../parallel-programming/task-parallel-library-tpl.md)」および「[タスク ベースの非同期パターン (TAP)](task-based-asynchronous-pattern-tap.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a9d91-107">For more information, see [Task Parallel Library (TPL)](../parallel-programming/task-parallel-library-tpl.md) and [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="a9d91-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a9d91-108">In This Section</span></span>

 [<span data-ttu-id="a9d91-109">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="a9d91-109">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)  
 <span data-ttu-id="a9d91-110">イベント ベースの非同期パターンによって、マルチスレッド デザイン固有の多くの複雑な問題を気にせずに、マルチスレッド アプリケーションの利点を活用できるしくみを説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-110">Describes how the Event-based Asynchronous Pattern makes available the advantages of multithreaded applications while hiding many of the complex issues inherent in multithreaded design.</span></span>  
  
 [<span data-ttu-id="a9d91-111">イベントベースの非同期パターンの実装</span><span class="sxs-lookup"><span data-stu-id="a9d91-111">Implementing the Event-based Asynchronous Pattern</span></span>](implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="a9d91-112">非同期機能を持つクラスをパッケージ化するための標準的な方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-112">Describes the standardized way to package a class that has asynchronous features.</span></span>  
  
 [<span data-ttu-id="a9d91-113">イベントベースの非同期パターンを実装するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="a9d91-113">Best Practices for Implementing the Event-based Asynchronous Pattern</span></span>](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="a9d91-114">イベント ベースの非同期パターンに従って非同期機能を公開するための要件について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-114">Describes the requirements for exposing asynchronous features according to the Event-based Asynchronous Pattern.</span></span>  
  
 [<span data-ttu-id="a9d91-115">イベントベースの非同期パターンをいつ実装するかの決定</span><span class="sxs-lookup"><span data-stu-id="a9d91-115">Deciding When to Implement the Event-based Asynchronous Pattern</span></span>](deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="a9d91-116">どのような場合に、[非同期プログラミング モデル (APM)](asynchronous-programming-model-apm.md) で表される <xref:System.IAsyncResult> パターンではなく、イベント ベースの非同期パターンの実装を選択するかを判断する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-116">Describes how to determine when you should choose to implement the Event-based Asynchronous Pattern instead of the <xref:System.IAsyncResult> pattern represented by the [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md)</span></span>
  
 [<span data-ttu-id="a9d91-117">方法: イベントベースの非同期パターンをサポートするコンポーネントを実装する</span><span class="sxs-lookup"><span data-stu-id="a9d91-117">How to: Implement a Component That Supports the Event-based Asynchronous Pattern</span></span>](component-that-supports-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="a9d91-118">イベント ベースの非同期パターンを実装するコンポーネントの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-118">Describes how to create a component that implements the Event-based Asynchronous Pattern.</span></span> <span data-ttu-id="a9d91-119">これは、<xref:System.ComponentModel?displayProperty=nameWithType> 名前空間のヘルパー クラスを使用して実装します。これにより、コンポーネントは任意のアプリケーション モデルで正常に動作します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-119">It is implemented using helper classes from the <xref:System.ComponentModel?displayProperty=nameWithType> namespace, which ensures that the component works correctly under any application model.</span></span>  

 [<span data-ttu-id="a9d91-120">方法: イベントベースの非同期パターンのクライアントを実装する</span><span class="sxs-lookup"><span data-stu-id="a9d91-120">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>](how-to-implement-a-client-of-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="a9d91-121">イベント ベースの非同期パターンを実装するコンポーネントを使用するクライアントの作成方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-121">Describes how to create a client that uses a component that implements the Event-based Asynchronous Pattern.</span></span>
  
 [<span data-ttu-id="a9d91-122">方法: イベントベースの非同期パターンをサポートするコンポーネントを使用する</span><span class="sxs-lookup"><span data-stu-id="a9d91-122">How to: Use Components That Support the Event-based Asynchronous Pattern</span></span>](how-to-use-components-that-support-the-event-based-asynchronous-pattern.md)  
 <span data-ttu-id="a9d91-123">イベント ベースの非同期パターンをサポートするコンポーネントの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-123">Describes how to use a component that supports the Event-based Asynchronous Pattern.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a9d91-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9d91-124">Reference</span></span>

 <xref:System.ComponentModel.AsyncOperation>  
 <span data-ttu-id="a9d91-125"><xref:System.ComponentModel.AsyncOperation> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-125">Describes the <xref:System.ComponentModel.AsyncOperation> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <span data-ttu-id="a9d91-126"><xref:System.ComponentModel.AsyncOperationManager> クラスについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-126">Describes the <xref:System.ComponentModel.AsyncOperationManager> class and has links to all its members.</span></span>  
  
 <xref:System.ComponentModel.BackgroundWorker>  
 <span data-ttu-id="a9d91-127"><xref:System.ComponentModel.BackgroundWorker> コンポーネントについて説明し、すべてのメンバーへのリンクの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-127">Describes the <xref:System.ComponentModel.BackgroundWorker> component and has links to all its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a9d91-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9d91-128">Related Sections</span></span>

 [<span data-ttu-id="a9d91-129">タスク並列ライブラリ (TPL)</span><span class="sxs-lookup"><span data-stu-id="a9d91-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)  
 <span data-ttu-id="a9d91-130">非同期操作および並列操作のプログラミング モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-130">Describes a programming model for asynchronous and parallel operations.</span></span>  
  
 [<span data-ttu-id="a9d91-131">スレッド化</span><span class="sxs-lookup"><span data-stu-id="a9d91-131">Threading</span></span>](../threading/index.md)  
 <span data-ttu-id="a9d91-132">.NET のマルチスレッド機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9d91-132">Describes multithreading features in .NET.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d91-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="a9d91-133">See also</span></span>

- [<span data-ttu-id="a9d91-134">マネージド スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="a9d91-134">Managed Threading Best Practices</span></span>](../threading/managed-threading-best-practices.md)
- [<span data-ttu-id="a9d91-135">イベント</span><span class="sxs-lookup"><span data-stu-id="a9d91-135">Events</span></span>](../events/index.md)
- [<span data-ttu-id="a9d91-136">非同期プログラミングのデザイン パターン</span><span class="sxs-lookup"><span data-stu-id="a9d91-136">Asynchronous Programming Design Patterns</span></span>](index.md)
