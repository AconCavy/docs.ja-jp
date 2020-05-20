---
title: 定数 - C# プログラミング ガイド
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, constants
- constants [C#]
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
ms.openlocfilehash: 85f6684617b893bdd85eb5b530aa2481941fbc5d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093553"
---
# <a name="constants-c-programming-guide"></a><span data-ttu-id="21932-102">定数 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="21932-102">Constants (C# Programming Guide)</span></span>
<span data-ttu-id="21932-103">定数とは、コンパイル時に既知であり、プログラムの実行期間を通じて変更されない値です。</span><span class="sxs-lookup"><span data-stu-id="21932-103">Constants are immutable values which are known at compile time and do not change for the life of the program.</span></span> <span data-ttu-id="21932-104">定数を宣言するには、[const](../../language-reference/keywords/const.md) 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="21932-104">Constants are declared with the [const](../../language-reference/keywords/const.md) modifier.</span></span> <span data-ttu-id="21932-105">`const` として宣言できるのは、C# [組み込み型](../../language-reference/builtin-types/built-in-types.md) (<xref:System.Object?displayProperty=nameWithType> を除く) のみです。</span><span class="sxs-lookup"><span data-stu-id="21932-105">Only the C# [built-in types](../../language-reference/builtin-types/built-in-types.md) (excluding <xref:System.Object?displayProperty=nameWithType>) may be declared as `const`.</span></span> <span data-ttu-id="21932-106">クラス、構造体、配列などのユーザー定義型を `const` にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="21932-106">User-defined types, including classes, structs, and arrays, cannot be `const`.</span></span> <span data-ttu-id="21932-107">実行時に (コンストラクターなどで) 一度だけ初期化され、その後は変更できないクラス、構造体、または配列を作成するには、[readonly](../../language-reference/keywords/readonly.md) 修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="21932-107">Use the [readonly](../../language-reference/keywords/readonly.md) modifier to create a class, struct, or array that is initialized one time at runtime (for example in a constructor) and thereafter cannot be changed.</span></span>  
  
 <span data-ttu-id="21932-108">C# では、`const` のメソッド、プロパティ、またはイベントはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="21932-108">C# does not support `const` methods, properties, or events.</span></span>  
  
 <span data-ttu-id="21932-109">enum 型を使用すると、組み込みの整数型 (`int`、`uint`、`long` など) の名前付き定数を定義できます。</span><span class="sxs-lookup"><span data-stu-id="21932-109">The enum type enables you to define named constants for integral built-in types (for example `int`, `uint`, `long`, and so on).</span></span> <span data-ttu-id="21932-110">詳細については、「[enum](../../language-reference/builtin-types/enum.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21932-110">For more information, see [enum](../../language-reference/builtin-types/enum.md).</span></span>  
  
 <span data-ttu-id="21932-111">定数は、宣言するときに初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21932-111">Constants must be initialized as they are declared.</span></span> <span data-ttu-id="21932-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="21932-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#64](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#64)]  
  
 <span data-ttu-id="21932-113">この例では、定数 `months` は常に 12 になり、クラス自体によっても変更できません。</span><span class="sxs-lookup"><span data-stu-id="21932-113">In this example, the constant `months` is always 12, and it cannot be changed even by the class itself.</span></span> <span data-ttu-id="21932-114">実際、コンパイラが C# ソース コードで定数の識別子 (この場合は `months`) を検出すると、コンパイラが生成する中間言語 (IL) コードには、識別子の代わりにリテラル値が直接出力されます。</span><span class="sxs-lookup"><span data-stu-id="21932-114">In fact, when the compiler encounters a constant identifier in C# source code (for example, `months`), it substitutes the literal value directly into the intermediate language (IL) code that it produces.</span></span> <span data-ttu-id="21932-115">実行時に定数に関連付けられる変数アドレスが存在しないため、`const` フィールドは、参照渡しすることも、式の左辺値として指定することもできません。</span><span class="sxs-lookup"><span data-stu-id="21932-115">Because there is no variable address associated with a constant at run time, `const` fields cannot be passed by reference and cannot appear as an l-value in an expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21932-116">DLL などの他のコードに定義されている定数値を参照するときは、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="21932-116">Use caution when you refer to constant values defined in other code such as DLLs.</span></span> <span data-ttu-id="21932-117">新しいバージョンの DLL で定数の新しい値を定義しても、その新バージョンを対象にプログラムを再コンパイルするまで、プログラムには古いリテラル値が保持されたままになります。</span><span class="sxs-lookup"><span data-stu-id="21932-117">If a new version of the DLL defines a new value for the constant, your program will still hold the old literal value until it is recompiled against the new version.</span></span>  
  
 <span data-ttu-id="21932-118">同じ型の複数の定数を、次のように同時に宣言できます。</span><span class="sxs-lookup"><span data-stu-id="21932-118">Multiple constants of the same type can be declared at the same time, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#65)]  
  
 <span data-ttu-id="21932-119">定数の初期化に使用する式は、循環参照を形成しない限り別の定数を参照できます。</span><span class="sxs-lookup"><span data-stu-id="21932-119">The expression that is used to initialize a constant can refer to another constant if it does not create a circular reference.</span></span> <span data-ttu-id="21932-120">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="21932-120">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#66](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#66)]  
  
 <span data-ttu-id="21932-121">定数は、[public](../../language-reference/keywords/public.md)、[private](../../language-reference/keywords/private.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md) または [private protected](../../language-reference/keywords/private-protected.md) としてマークできます。</span><span class="sxs-lookup"><span data-stu-id="21932-121">Constants can be marked as [public](../../language-reference/keywords/public.md), [private](../../language-reference/keywords/private.md), [protected](../../language-reference/keywords/protected.md), [internal](../../language-reference/keywords/internal.md), [protected internal](../../language-reference/keywords/protected-internal.md) or [private protected](../../language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="21932-122">これらのアクセス修飾子により、クラスのユーザーが定数にアクセスする方法が定義されます。</span><span class="sxs-lookup"><span data-stu-id="21932-122">These access modifiers define how users of the class can access the constant.</span></span> <span data-ttu-id="21932-123">詳細については、「[アクセス修飾子](./access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21932-123">For more information, see [Access Modifiers](./access-modifiers.md).</span></span>  
  
 <span data-ttu-id="21932-124">定数の値は型のすべてのインスタンスで同じであるため、定数は[静的](../../language-reference/keywords/static.md)フィールドのようにアクセスされます。</span><span class="sxs-lookup"><span data-stu-id="21932-124">Constants are accessed as if they were [static](../../language-reference/keywords/static.md) fields because the value of the constant is the same for all instances of the type.</span></span> <span data-ttu-id="21932-125">定数の宣言に `static` キーワードは使用しません。</span><span class="sxs-lookup"><span data-stu-id="21932-125">You do not use the `static` keyword to declare them.</span></span> <span data-ttu-id="21932-126">定数を定義しているクラスに含まれていない式で定数を使用する場合は、クラス名、ピリオド、定数の名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="21932-126">Expressions that are not in the class that defines the constant must use the class name, a period, and the name of the constant to access the constant.</span></span> <span data-ttu-id="21932-127">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="21932-127">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#67](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#67)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="21932-128">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="21932-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="21932-129">参照</span><span class="sxs-lookup"><span data-stu-id="21932-129">See also</span></span>

- [<span data-ttu-id="21932-130">C# プログラミングガイド</span><span class="sxs-lookup"><span data-stu-id="21932-130">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="21932-131">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="21932-131">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="21932-132">Properties</span><span class="sxs-lookup"><span data-stu-id="21932-132">Properties</span></span>](./properties.md)
- [<span data-ttu-id="21932-133">型</span><span class="sxs-lookup"><span data-stu-id="21932-133">Types</span></span>](../types/index.md)
- [<span data-ttu-id="21932-134">readonly</span><span class="sxs-lookup"><span data-stu-id="21932-134">readonly</span></span>](../../language-reference/keywords/readonly.md)
- [<span data-ttu-id="21932-135">C# の不変性パート 1: 不変性の種類</span><span class="sxs-lookup"><span data-stu-id="21932-135">Immutability in C# Part One: Kinds of Immutability</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/immutability-in-c-part-one-kinds-of-immutability)
