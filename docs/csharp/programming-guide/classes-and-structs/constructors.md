---
title: コンストラクター - C# プログラミング ガイド
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 9c57ff6dd9acd8a8bcff6de4fce7d898f1135703
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714962"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="b927e-102">コンストラクター (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="b927e-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="b927e-103">[クラス](../../language-reference/keywords/class.md)または[構造体](../../language-reference/keywords/struct.md)を作成するたびに、コンストラクターが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b927e-103">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="b927e-104">クラスまたは構造体には、異なる引数を取るコンストラクターが複数含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="b927e-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="b927e-105">プログラマーはコンストラクターを利用することで、既定値を設定したり、インスタンス化を制限したり、柔軟で読みやすいコードを記述したりできます。</span><span class="sxs-lookup"><span data-stu-id="b927e-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="b927e-106">詳細と例については、「[コンストラクターの使用](./using-constructors.md)」と「[インスタンス コンストラクター](./instance-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b927e-106">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="b927e-107">パラメーターなしのコンストラクター</span><span class="sxs-lookup"><span data-stu-id="b927e-107">Parameterless constructors</span></span>
  
<span data-ttu-id="b927e-108">クラスにコンストラクターを指定しない場合、C# では既定でコンストラクターが 1 つ作成されます。そのコンストラクターによりオブジェクトがインスタンス化され、「[既定値の一覧表](../../language-reference/keywords/default-values-table.md)」の一覧にある既定値にメンバー変数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="b927e-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="b927e-109">構造体にコンストラクターを指定しない場合、C# では、*暗黙的なパラメーターなしのコンストラクター*を利用し、「[既定値の一覧表](../../language-reference/keywords/default-values-table.md)」の一覧にある既定値に値の型の各フィールドが自動的に初期化されます。</span><span class="sxs-lookup"><span data-stu-id="b927e-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="b927e-110">詳細と例については、「[インスタンス コンストラクター](./instance-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b927e-110">For more information and examples, see [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="b927e-111">コンストラクターの構文</span><span class="sxs-lookup"><span data-stu-id="b927e-111">Constructor syntax</span></span>

<span data-ttu-id="b927e-112">コンストラクターは、名前がその型の名前と同じメソッドです。</span><span class="sxs-lookup"><span data-stu-id="b927e-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="b927e-113">メソッド シグネチャには、メソッド名とそのパラメーター リストだけが含まれます。戻り値の型は含まれません。</span><span class="sxs-lookup"><span data-stu-id="b927e-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="b927e-114">次の例は、`Person` という名前のクラスのコンストラクターを示しています。</span><span class="sxs-lookup"><span data-stu-id="b927e-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="b927e-115">コンストラクターを 1 つのステートメントとして実装できる場合、[式の本体の定義](../statements-expressions-operators/expression-bodied-members.md)を利用できます。</span><span class="sxs-lookup"><span data-stu-id="b927e-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="b927e-116">次の例では、コンストラクターに *name* という名前の文字列パラメーターが 1 つある `Location` クラスが定義されています。</span><span class="sxs-lookup"><span data-stu-id="b927e-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="b927e-117">式の本体の定義により `locationName` フィールドに引数が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b927e-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="b927e-118">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b927e-118">Static constructors</span></span>

<span data-ttu-id="b927e-119">前の例には、表示されるすべてのインスタンス コンストラクターがあり、それが新しいオブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b927e-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="b927e-120">クラスまたは構造体には静的コンストラクターを与えることもできます。静的コンストラクターは型の静的メンバーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b927e-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="b927e-121">静的コンストラクターにはパラメーターがありません。</span><span class="sxs-lookup"><span data-stu-id="b927e-121">Static constructors are parameterless.</span></span> <span data-ttu-id="b927e-122">静的コンストラクターを指定して静的フィールドを初期化しない場合、C# コンパイラは、「[既定値の一覧表](../../language-reference/keywords/default-values-table.md)」の一覧にある既定値に静的フィールドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="b927e-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default Values Table](../../language-reference/keywords/default-values-table.md).</span></span>

<span data-ttu-id="b927e-123">次の例では、静的コンストラクターを使用して静的フィールドを初期化しています。</span><span class="sxs-lookup"><span data-stu-id="b927e-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="b927e-124">式の本体の定義で静的コンストラクターを定義することもできます。次の例をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b927e-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="b927e-125">詳細と例については、「[静的コンストラクター](./static-constructors.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b927e-125">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b927e-126">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="b927e-126">In This Section</span></span>  
 [<span data-ttu-id="b927e-127">コンストラクターの使用</span><span class="sxs-lookup"><span data-stu-id="b927e-127">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="b927e-128">インスタンス コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b927e-128">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="b927e-129">プライベート コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b927e-129">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="b927e-130">静的コンストラクター</span><span class="sxs-lookup"><span data-stu-id="b927e-130">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="b927e-131">コピー コンストラクターを記述する方法</span><span class="sxs-lookup"><span data-stu-id="b927e-131">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="b927e-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="b927e-132">See also</span></span>

- [<span data-ttu-id="b927e-133">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="b927e-133">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b927e-134">クラスと構造体</span><span class="sxs-lookup"><span data-stu-id="b927e-134">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b927e-135">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="b927e-135">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="b927e-136">static</span><span class="sxs-lookup"><span data-stu-id="b927e-136">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="b927e-137">初期化子がコンストラクターとは反対の順序で実行される理由その 1</span><span class="sxs-lookup"><span data-stu-id="b927e-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
