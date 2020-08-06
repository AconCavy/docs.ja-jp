---
title: インターフェイスのインデクサー - C# プログラミング ガイド
description: C# では、インターフェイスでインデクサーを宣言することができます。 インターフェイスのインデクサーのアクセサーが、クラスのインデクサーのアクセサーと異なる点について説明します。
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303102"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="ca7a5-104">インターフェイスのインデクサー (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="ca7a5-104">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="ca7a5-105">[interface](../../language-reference/keywords/interface.md) でインデクサーを宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-105">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="ca7a5-106">インターフェイスのインデクサーのアクセサーは、[クラス](../../language-reference/keywords/class.md)のインデクサーのアクセサーと次の点で異なります。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-106">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="ca7a5-107">インターフェイスのアクセサーは、修飾子は使用しません。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-107">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="ca7a5-108">インターフェイスのアクセサーには通常、本文がありません。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-108">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="ca7a5-109">アクセサーの目的は、インデクサーが読み取り/書き込み、読み取り専用、書き込み専用のどれかを示すことです。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-109">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="ca7a5-110">インデクサーの実装をインターフェイスに定義できますが、めったに行われません。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-110">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="ca7a5-111">インデクサーでは通常、データ フィールドにアクセスするための API が定義されます。データ フィールドはインターフェイスで定義できません。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-111">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="ca7a5-112">インターフェイスのインデクサー アクセサーの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-112">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="ca7a5-113">インデクサーのシグネチャは、同じインターフェイスで宣言されている他のすべてのインデクサーの署名とは異なる必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-113">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="ca7a5-114">例</span><span class="sxs-lookup"><span data-stu-id="ca7a5-114">Example</span></span>

<span data-ttu-id="ca7a5-115">次の例では、インターフェイスのインデクサーを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-115">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="ca7a5-116">前の例では、インターフェイス メンバーの完全修飾名を使用して明示的なインターフェイス メンバーの実装を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-116">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="ca7a5-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-117">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="ca7a5-118">ただし、完全修飾名は、クラスが同じインデクサーの署名を持つ 2 つ以上のインターフェイスを実装するときにあいまいさを避けるためにのみ必要です。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-118">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="ca7a5-119">たとえば、`Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスが同じインデクサーの署名を持っている場合、明示的なインターフェイス メンバーの実装が必要です。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-119">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="ca7a5-120">つまり、次のインデクサーの宣言があります。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-120">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
```

<span data-ttu-id="ca7a5-121">これは、`IEmployee` インターフェイス上でインデクサーを実装します。次の宣言があります。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-121">implements the indexer on the `IEmployee` interface, while the following declaration:</span></span>

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="ca7a5-122">これは、`ICitizen` インターフェイスでインデクサーを実装します。</span><span class="sxs-lookup"><span data-stu-id="ca7a5-122">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="ca7a5-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ca7a5-123">See also</span></span>

- [<span data-ttu-id="ca7a5-124">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="ca7a5-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ca7a5-125">インデクサー</span><span class="sxs-lookup"><span data-stu-id="ca7a5-125">Indexers</span></span>](./index.md)
- [<span data-ttu-id="ca7a5-126">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ca7a5-126">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="ca7a5-127">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ca7a5-127">Interfaces</span></span>](../interfaces/index.md)
