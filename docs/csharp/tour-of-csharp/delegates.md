---
title: C# のデリゲート - C# 言語のツアー
description: C# のデリゲートと遅延バインディングについて
ms.date: 02/27/2020
ms.assetid: 3cc27357-3ac2-43a1-aad0-86a77b88f884
ms.openlocfilehash: b1740ddc65dcb0ee8775f4cbaa8356293ea55fae
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159170"
---
# <a name="delegates"></a><span data-ttu-id="9553f-103">デリゲート</span><span class="sxs-lookup"><span data-stu-id="9553f-103">Delegates</span></span>

<span data-ttu-id="9553f-104">***デリゲート型***は、特定のパラメーター リストおよび戻り値を使用してメソッドへの参照を表します。</span><span class="sxs-lookup"><span data-stu-id="9553f-104">A ***delegate type*** represents references to methods with a particular parameter list and return type.</span></span> <span data-ttu-id="9553f-105">デリゲートを使用すると、変数に割り当ててパラメーターとして渡すことのできるエンティティとして、メソッドを処理できます。</span><span class="sxs-lookup"><span data-stu-id="9553f-105">Delegates make it possible to treat methods as entities that can be assigned to variables and passed as parameters.</span></span> <span data-ttu-id="9553f-106">デリゲートは、他の言語で検出された関数ポインターの概念に似ています。</span><span class="sxs-lookup"><span data-stu-id="9553f-106">Delegates are similar to the concept of function pointers found in some other languages.</span></span> <span data-ttu-id="9553f-107">ただし、関数ポインターとは異なり、デリゲートはオブジェクト指向で、タイプ セーフです。</span><span class="sxs-lookup"><span data-stu-id="9553f-107">Unlike function pointers, delegates are object-oriented and type-safe.</span></span>

<span data-ttu-id="9553f-108">次の例では、`Function` という名前のデリゲート型を宣言して使用します。</span><span class="sxs-lookup"><span data-stu-id="9553f-108">The following example declares and uses a delegate type named `Function`.</span></span>

[!code-csharp[DelegateExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L3-L37)]

<span data-ttu-id="9553f-109">`Function` デリゲート型のインスタンスは、`double` 引数を取得して `double` 値を返す任意のメソッドを参照できます。</span><span class="sxs-lookup"><span data-stu-id="9553f-109">An instance of the `Function` delegate type can reference any method that takes a `double` argument and returns a `double` value.</span></span> <span data-ttu-id="9553f-110">`Apply` メソッドは、指定された関数を `double[]` の要素に適用し、`double[]` を結果とともに返します。</span><span class="sxs-lookup"><span data-stu-id="9553f-110">The `Apply` method applies a given Function to the elements of a `double[]`, returning a `double[]` with the results.</span></span> <span data-ttu-id="9553f-111">`Main` メソッドでは、`Apply` は `double[]` に 3 つの異なる関数を適用するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9553f-111">In the `Main` method, `Apply` is used to apply three different functions to a `double[]`.</span></span>

<span data-ttu-id="9553f-112">デリゲートは、静的メソッド (前述の例の `Square` や `Math.Sin` など) またはインスタンス メソッド (前述の例の `m.Multiply` など) のいずれかを参照できます。</span><span class="sxs-lookup"><span data-stu-id="9553f-112">A delegate can reference either a static method (such as `Square` or `Math.Sin` in the previous example) or an instance method (such as `m.Multiply` in the previous example).</span></span> <span data-ttu-id="9553f-113">インスタンス メソッドを参照するデリゲートはまた、特定のオブジェクトを参照し、インスタンス メソッドがデリゲートから呼び出されると、そのオブジェクトは呼び出しで `this` になります。</span><span class="sxs-lookup"><span data-stu-id="9553f-113">A delegate that references an instance method also references a particular object, and when the instance method is invoked through the delegate, that object becomes `this` in the invocation.</span></span>

<span data-ttu-id="9553f-114">宣言時に作成される "インライン メソッド" である匿名関数を使用してデリゲートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="9553f-114">Delegates can also be created using anonymous functions, which are "inline methods" that are created when declared.</span></span> <span data-ttu-id="9553f-115">匿名関数では、周囲のメソッドのローカル変数を確認できます。</span><span class="sxs-lookup"><span data-stu-id="9553f-115">Anonymous functions can see the local variables of the surrounding methods.</span></span> <span data-ttu-id="9553f-116">次の例では、クラスは作成されません。</span><span class="sxs-lookup"><span data-stu-id="9553f-116">The following example doesn't create a class:</span></span>

[!code-csharp[LambdaExample](../../../samples/snippets/csharp/tour/delegates/Program.cs#L44-L44)]

<span data-ttu-id="9553f-117">デリゲートによって、参照されるメソッドのクラスは把握されることも必要とされることもありません。重要なのは、参照されるメソッドがデリゲートと同じパラメーターおよび戻り値の型を持つという点だけです。</span><span class="sxs-lookup"><span data-stu-id="9553f-117">A delegate doesn't know or care about the class of the method it references; all that matters is that the referenced method has the same parameters and return type as the delegate.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9553f-118">[前へ](interfaces.md)
>[次へ](attributes.md)</span><span class="sxs-lookup"><span data-stu-id="9553f-118">[Previous](interfaces.md)
[Next](attributes.md)</span></span>
