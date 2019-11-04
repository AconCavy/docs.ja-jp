---
title: ポインター変換 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: b0a517eacc505376c9502e9d095c7aac0cd54555
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417526"
---
# <a name="pointer-conversions-c-programming-guide"></a><span data-ttu-id="2d7f3-102">ポインター変換 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="2d7f3-102">Pointer Conversions (C# Programming Guide)</span></span>
<span data-ttu-id="2d7f3-103">定義済みの暗黙的なポインター変換を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="2d7f3-103">The following table shows the predefined implicit pointer conversions.</span></span> <span data-ttu-id="2d7f3-104">暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="2d7f3-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
## <a name="implicit-pointer-conversions"></a><span data-ttu-id="2d7f3-105">暗黙的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="2d7f3-105">Implicit pointer conversions</span></span>  
  
|<span data-ttu-id="2d7f3-106">From</span><span class="sxs-lookup"><span data-stu-id="2d7f3-106">From</span></span>|<span data-ttu-id="2d7f3-107">終了</span><span class="sxs-lookup"><span data-stu-id="2d7f3-107">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="2d7f3-108">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-108">Any pointer type</span></span>|<span data-ttu-id="2d7f3-109">void\*</span><span class="sxs-lookup"><span data-stu-id="2d7f3-109">void\*</span></span>|  
|<span data-ttu-id="2d7f3-110">null</span><span class="sxs-lookup"><span data-stu-id="2d7f3-110">null</span></span>|<span data-ttu-id="2d7f3-111">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-111">Any pointer type</span></span>|  
  
 <span data-ttu-id="2d7f3-112">明示的なポインター変換は、暗黙的な変換がない場合に、キャスト式を使用して、変換を実行するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2d7f3-112">Explicit pointer conversion is used to perform conversions, for which there is no implicit conversion, by using a cast expression.</span></span> <span data-ttu-id="2d7f3-113">次の表はこの変換についてまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="2d7f3-113">The following table shows these conversions.</span></span>  
  
## <a name="explicit-pointer-conversions"></a><span data-ttu-id="2d7f3-114">明示的なポインター変換</span><span class="sxs-lookup"><span data-stu-id="2d7f3-114">Explicit pointer conversions</span></span>  
  
|<span data-ttu-id="2d7f3-115">From</span><span class="sxs-lookup"><span data-stu-id="2d7f3-115">From</span></span>|<span data-ttu-id="2d7f3-116">終了</span><span class="sxs-lookup"><span data-stu-id="2d7f3-116">To</span></span>|  
|----------|--------|  
|<span data-ttu-id="2d7f3-117">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-117">Any pointer type</span></span>|<span data-ttu-id="2d7f3-118">その他のポインター型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-118">Any other pointer type</span></span>|  
|<span data-ttu-id="2d7f3-119">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="2d7f3-119">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|<span data-ttu-id="2d7f3-120">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-120">Any pointer type</span></span>|  
|<span data-ttu-id="2d7f3-121">任意のポインター型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-121">Any pointer type</span></span>|<span data-ttu-id="2d7f3-122">sbyte、byte、short、ushort、int、uint、long または ulong</span><span class="sxs-lookup"><span data-stu-id="2d7f3-122">sbyte, byte, short, ushort, int, uint, long, or ulong</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2d7f3-123">例</span><span class="sxs-lookup"><span data-stu-id="2d7f3-123">Example</span></span>  
 <span data-ttu-id="2d7f3-124">次の例では、`int` へのポインターは `byte` へのポインターに変換されます。</span><span class="sxs-lookup"><span data-stu-id="2d7f3-124">In the following example, a pointer to `int` is converted to a pointer to `byte`.</span></span> <span data-ttu-id="2d7f3-125">ポインターは、変数の最下位バイト アドレスを指すことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="2d7f3-125">Notice that the pointer points to the lowest addressed byte of the variable.</span></span> <span data-ttu-id="2d7f3-126">`int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="2d7f3-126">When you successively increment the result, up to the size of `int` (4 bytes), you can display the remaining bytes of the variable.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a><span data-ttu-id="2d7f3-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d7f3-127">See also</span></span>

- [<span data-ttu-id="2d7f3-128">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="2d7f3-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2d7f3-129">ポインター型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-129">Pointer types</span></span>](./pointer-types.md)
- [<span data-ttu-id="2d7f3-130">型</span><span class="sxs-lookup"><span data-stu-id="2d7f3-130">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="2d7f3-131">unsafe</span><span class="sxs-lookup"><span data-stu-id="2d7f3-131">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
- [<span data-ttu-id="2d7f3-132">fixed ステートメント</span><span class="sxs-lookup"><span data-stu-id="2d7f3-132">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="2d7f3-133">stackalloc</span><span class="sxs-lookup"><span data-stu-id="2d7f3-133">stackalloc</span></span>](../../language-reference/operators/stackalloc.md)
