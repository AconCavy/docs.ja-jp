---
title: アンマネージ リソースのクリーンアップ
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: e05cfb949ee3f206f212ca7015f3ff4c22cd2a12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "73423037"
---
# <a name="cleaning-up-unmanaged-resources"></a><span data-ttu-id="561d5-102">アンマネージ リソースのクリーンアップ</span><span class="sxs-lookup"><span data-stu-id="561d5-102">Cleaning Up Unmanaged Resources</span></span>

<span data-ttu-id="561d5-103">アプリケーションで作成するオブジェクトの大部分については、.NET のガベージ コレクターにメモリ管理を任せることができます。</span><span class="sxs-lookup"><span data-stu-id="561d5-103">For the majority of the objects that your app creates, you can rely on .NET's garbage collector to handle memory management.</span></span> <span data-ttu-id="561d5-104">しかし、アンマネージ リソースを含むオブジェクトを作成する場合は、アプリケーションでそのオブジェクトの使用が終了した時点で、そのリソースを明示的に解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="561d5-104">However, when you create objects that include unmanaged resources, you must explicitly release those resources when you finish using them in your app.</span></span> <span data-ttu-id="561d5-105">アンマネージ リソースの種類で最も一般的なのは、ファイル、ウィンドウ、ネットワーク接続、データベース接続などのオペレーティング システム リソースをラップしたオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="561d5-105">The most common types of unmanaged resource are objects that wrap operating system resources, such as files, windows, network connections, or database connections.</span></span> <span data-ttu-id="561d5-106">ガベージ コレクターは、アンマネージ リソースをカプセル化したオブジェクトを有効期間全体にわたって監視できますが、アンマネージ リソースを解放しクリーンアップする方法については情報を持っていません。</span><span class="sxs-lookup"><span data-stu-id="561d5-106">Although the garbage collector is able to track the lifetime of an object that encapsulates an unmanaged resource, it doesn't know how to release and clean up the unmanaged resource.</span></span>

<span data-ttu-id="561d5-107">型でアンマネージ リソースを使用している場合は、次のようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="561d5-107">If your types use unmanaged resources, you should do the following:</span></span>

- <span data-ttu-id="561d5-108">[dispose パターン](implementing-dispose.md)を実装します。</span><span class="sxs-lookup"><span data-stu-id="561d5-108">Implement the [dispose pattern](implementing-dispose.md).</span></span> <span data-ttu-id="561d5-109">これは、アンマネージ リソースの確定的解放を有効にするために <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="561d5-109">This requires that you provide an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to enable the deterministic release of  unmanaged resources.</span></span> <span data-ttu-id="561d5-110">型のコンシューマーはオブジェクト (および使用するリソース) が不要になると <xref:System.IDisposable.Dispose%2A> を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="561d5-110">A consumer of your type calls <xref:System.IDisposable.Dispose%2A> when the object (and the resources it uses) is no longer needed.</span></span> <span data-ttu-id="561d5-111"><xref:System.IDisposable.Dispose%2A> メソッドはアンマネージ リソースを直ちに解放します。</span><span class="sxs-lookup"><span data-stu-id="561d5-111">The <xref:System.IDisposable.Dispose%2A> method immediately releases the unmanaged resources.</span></span>

- <span data-ttu-id="561d5-112">型のコンシューマーが <xref:System.IDisposable.Dispose%2A> の呼び出しを忘れた場合にアンマネージ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="561d5-112">Provide for your unmanaged resources to be released in the event that a consumer of your type forgets to call <xref:System.IDisposable.Dispose%2A>.</span></span> <span data-ttu-id="561d5-113">この作業を実行する 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="561d5-113">There are two ways to do this:</span></span>

  - <span data-ttu-id="561d5-114">アンマネージ リソースをラップするセーフ ハンドルを使用します。</span><span class="sxs-lookup"><span data-stu-id="561d5-114">Use a safe handle to wrap your unmanaged resource.</span></span> <span data-ttu-id="561d5-115">この手法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="561d5-115">This is the recommended technique.</span></span> <span data-ttu-id="561d5-116">セーフ ハンドルは <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> クラスから派生し、堅牢な <xref:System.Object.Finalize%2A> メソッドを含みます。</span><span class="sxs-lookup"><span data-stu-id="561d5-116">Safe handles are derived from the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> class and include a robust <xref:System.Object.Finalize%2A> method.</span></span> <span data-ttu-id="561d5-117">セーフ ハンドルを使用するときは、単純に <xref:System.IDisposable> インターフェイスを実装し、<xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> の実装でセーフ ハンドルの <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="561d5-117">When you use a safe handle, you simply implement the <xref:System.IDisposable> interface and call your safe handle's <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> method in your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="561d5-118">セーフ ハンドルのファイナライザーは、<xref:System.IDisposable.Dispose%2A> メソッドが呼び出されなかった場合、ガベージ コレクターによって自動的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="561d5-118">The safe handle's finalizer is called automatically by the garbage collector if its <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

    <span data-ttu-id="561d5-119">— または —</span><span class="sxs-lookup"><span data-stu-id="561d5-119">—or—</span></span>

  - <span data-ttu-id="561d5-120"><xref:System.Object.Finalize%2A?displayProperty=nameWithType> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="561d5-120">Override the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="561d5-121">終了処理では、型のコンシューマーが <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> を呼び出してアンマネージ リソースを確定的に破棄しなかった場合に、リソースを非確定的に解放できます。</span><span class="sxs-lookup"><span data-stu-id="561d5-121">Finalization enables the non-deterministic release of unmanaged resources when the consumer of a type fails to call <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> to dispose of them deterministically.</span></span> <span data-ttu-id="561d5-122">ただし、オブジェクトの終了処理は複雑でエラーが発生しやすい操作であるため、独自のファイナライザーを用意する代わりに、セーフ ハンドルを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="561d5-122">However, because object finalization can be a complex and error-prone operation, we recommend that you use a safe handle instead of providing your own finalizer.</span></span>

<span data-ttu-id="561d5-123">これで型のコンシューマーは、<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> の実装を直接呼び出して、アンマネージ リソースで使用されるメモリを解放することができます。</span><span class="sxs-lookup"><span data-stu-id="561d5-123">Consumers of your type can then call your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation directly to free memory used by unmanaged resources.</span></span> <span data-ttu-id="561d5-124"><xref:System.IDisposable.Dispose%2A> メソッドを適切に実装すると、セーフ ハンドルの <xref:System.Object.Finalize%2A> メソッドまたは <xref:System.Object.Finalize%2A?displayProperty=nameWithType> メソッドの独自のオーバーライドは、<xref:System.IDisposable.Dispose%2A> メソッドが呼び出されなかった場合にリソースをクリーンアップするための安全装置になります。</span><span class="sxs-lookup"><span data-stu-id="561d5-124">When you properly implement a <xref:System.IDisposable.Dispose%2A> method, either your safe handle's <xref:System.Object.Finalize%2A> method or your own override of the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method becomes a safeguard to clean up resources in the event that the <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="561d5-125">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="561d5-125">In This Section</span></span>

<span data-ttu-id="561d5-126">[Dispose メソッドの実装](../../../docs/standard/garbage-collection/implementing-dispose.md) アンマネージ リソースを解放する [Dispose パターン](implementing-dispose.md)を実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="561d5-126">[Implementing a Dispose Method](../../../docs/standard/garbage-collection/implementing-dispose.md) Describes how to implement the [dispose pattern](implementing-dispose.md) for releasing unmanaged resources.</span></span>

<span data-ttu-id="561d5-127">[IDisposable を実装するオブジェクトの使用](../../../docs/standard/garbage-collection/using-objects.md) 型のコンシューマーが <xref:System.IDisposable.Dispose%2A> の実装を確実に呼び出す方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="561d5-127">[Using Objects That Implement IDisposable](../../../docs/standard/garbage-collection/using-objects.md) Describes how consumers of a type ensure that its <xref:System.IDisposable.Dispose%2A> implementation is called.</span></span> <span data-ttu-id="561d5-128">このためには、C# の `using` ステートメントまたは Visual Basic の `Using` ステートメントを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="561d5-128">We recommend using the C# `using` statement or the Visual Basic `Using` statement to do this.</span></span>

## <a name="reference"></a><span data-ttu-id="561d5-129">リファレンス</span><span class="sxs-lookup"><span data-stu-id="561d5-129">Reference</span></span>

<xref:System.IDisposable?displayProperty=nameWithType>\
<span data-ttu-id="561d5-130">アンマネージ リソースの解放のための <xref:System.IDisposable.Dispose%2A> メソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="561d5-130">Defines the <xref:System.IDisposable.Dispose%2A> method for releasing unmanaged resources.</span></span>

<xref:System.Object.Finalize%2A?displayProperty=nameWithType>\
<span data-ttu-id="561d5-131">アンマネージ リソースが <xref:System.IDisposable.Dispose%2A> メソッドによって解放されない場合に、オブジェクトの終了処理を提供します。</span><span class="sxs-lookup"><span data-stu-id="561d5-131">Provides for object finalization if unmanaged resources are not released by the <xref:System.IDisposable.Dispose%2A> method.</span></span>

<xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>\
<span data-ttu-id="561d5-132">終了処理を抑制します。</span><span class="sxs-lookup"><span data-stu-id="561d5-132">Suppresses finalization.</span></span> <span data-ttu-id="561d5-133">このメソッドは、慣例的に `Dispose` メソッドから呼び出され、ファイナライザーが実行されないようにします。</span><span class="sxs-lookup"><span data-stu-id="561d5-133">This method is customarily called from a `Dispose` method to prevent a finalizer from executing.</span></span>
