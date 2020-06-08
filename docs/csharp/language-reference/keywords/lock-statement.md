---
title: lock ステートメント - C# リファレンス
description: C# lock ステートメントを使用し、共有リソースへのスレッド アクセスを同期します
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406691"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="aa8ce-103">lock ステートメント (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="aa8ce-103">lock statement (C# reference)</span></span>

<span data-ttu-id="aa8ce-104">`lock` ステートメントは、指定のオブジェクトに対する相互排他ロックを取得し、ステートメント ブロックを実行してからロックを解放します。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="aa8ce-105">ロックが保持されている間、ロックを保持するスレッドではロックを再度取得し、解放することができます。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="aa8ce-106">他のスレッドはブロックされてロックを取得できず、ロックが解放されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="aa8ce-107">`lock` ステートメントの形式は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="aa8ce-108">`x` は[参照型](reference-types.md)の式です。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="aa8ce-109">これは次にまったく等しくなります。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="aa8ce-110">このコードでは [try...finally](try-finally.md) ブロックが使用されているため、`lock` ステートメントの本文内で例外がスローされた場合でもロックは解放されます。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="aa8ce-111">`lock` ステートメントの本文で [await](../operators/await.md) 演算子を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="aa8ce-112">ガイドライン</span><span class="sxs-lookup"><span data-stu-id="aa8ce-112">Guidelines</span></span>

<span data-ttu-id="aa8ce-113">共有リソースへのスレッド アクセスを同期する場合、専用オブジェクト インスタンス (`private readonly object balanceLock = new object();` など) またはコードの関連のない部分によってロック オブジェクトとして使用される可能性がない別のインスタンスをロックします。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="aa8ce-114">異なる共有リソースに対して同じロック オブジェクト インスタンスを使用することは避けてください。デッドロックやロックの競合が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="aa8ce-115">特に、以下をロック オブジェクトとして使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="aa8ce-116">`this`。ロックとして呼び出し元に使用される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="aa8ce-117"><xref:System.Type> インスタンス。[typeof](../operators/type-testing-and-cast.md#typeof-operator) 演算子またはリフレクションによって取得される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="aa8ce-118">文字列リテラルを含む文字列インスタンス。[インターン処理](/dotnet/api/system.string.intern#remarks)される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="aa8ce-119">ロックの競合を減らすために、できるだけ短い時間ロックを保持します。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="aa8ce-120">例</span><span class="sxs-lookup"><span data-stu-id="aa8ce-120">Example</span></span>

<span data-ttu-id="aa8ce-121">次の例では、専用 `balanceLock` インスタンスをロックすることでそのプライベート `balance` フィールドへのアクセスを同期する `Account` クラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="aa8ce-122">ロッキングに同じインスタンスを使用すると、2 つのスレッドが `Debit` または `Credit` メソッドを同時に呼び出すことによって `balance` フィールドを同時に更新することができなくなります。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="aa8ce-123">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="aa8ce-123">C# language specification</span></span>

<span data-ttu-id="aa8ce-124">詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の [lock ステートメント](~/_csharplang/spec/statements.md#the-lock-statement)に関するセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa8ce-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aa8ce-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa8ce-125">See also</span></span>

- [<span data-ttu-id="aa8ce-126">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="aa8ce-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="aa8ce-127">C# キーワード</span><span class="sxs-lookup"><span data-stu-id="aa8ce-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="aa8ce-128">同期プリミティブの概要</span><span class="sxs-lookup"><span data-stu-id="aa8ce-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
