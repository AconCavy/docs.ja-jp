---
title: '方法 : 複数のデータ型に同一の機能を提供できるクラスを定義する'
ms.date: 07/20/2015
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
ms.openlocfilehash: d80623d9e55358d37aa45f11f1525c80a09b91a6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350041"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a><span data-ttu-id="03f55-102">方法: 複数のデータ型に同一の機能を提供できるクラスを定義する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03f55-102">How to: Define a Class That Can Provide Identical Functionality on Different Data Types (Visual Basic)</span></span>
<span data-ttu-id="03f55-103">複数の異なるデータ型に同一の機能を提供するオブジェクトを作成するために使用できるクラスを定義できます。</span><span class="sxs-lookup"><span data-stu-id="03f55-103">You can define a class from which you can create objects that provide identical functionality on different data types.</span></span> <span data-ttu-id="03f55-104">これを行うには、1 つ以上の *型パラメーター* を定義内で指定します。</span><span class="sxs-lookup"><span data-stu-id="03f55-104">To do this, you specify one or more *type parameters* in the definition.</span></span> <span data-ttu-id="03f55-105">このようなクラスは、さまざまなデータ型を使用するオブジェクトのテンプレートとして使用できます。</span><span class="sxs-lookup"><span data-stu-id="03f55-105">The class can then serve as a template for objects that use various data types.</span></span> <span data-ttu-id="03f55-106">この方法で定義したクラスは、 *ジェネリック クラス*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="03f55-106">A class defined in this way is called a *generic class*.</span></span>  
  
 <span data-ttu-id="03f55-107">ジェネリック クラスを定義する利点は、クラスを一度だけ定義すれば、コードの中でそれを使って、さまざまなデータ型を使用する多くのオブジェクトを作成できることです。</span><span class="sxs-lookup"><span data-stu-id="03f55-107">The advantage of defining a generic class is that you define it just once, and your code can use it to create many objects that use a wide variety of data types.</span></span> <span data-ttu-id="03f55-108">これにより、クラスを `Object` 型で定義した場合よりパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="03f55-108">This results in better performance than defining the class with the `Object` type.</span></span>  
  
 <span data-ttu-id="03f55-109">クラスに加えて、ジェネリックの構造体、インターフェイス、プロシージャ、デリゲートを定義して利用することもできます。</span><span class="sxs-lookup"><span data-stu-id="03f55-109">In addition to classes, you can also define and use generic structures, interfaces, procedures, and delegates.</span></span>  
  
### <a name="to-define-a-class-with-a-type-parameter"></a><span data-ttu-id="03f55-110">型パラメーターを持つクラスを定義するには</span><span class="sxs-lookup"><span data-stu-id="03f55-110">To define a class with a type parameter</span></span>  
  
1. <span data-ttu-id="03f55-111">通常の方法でクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="03f55-111">Define the class in the normal way.</span></span>  
  
2. <span data-ttu-id="03f55-112">クラス名の直後に `(Of` *typeparameter*`)` を追加し、型パラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="03f55-112">Add `(Of` *typeparameter*`)` immediately after the class name to specify a type parameter.</span></span>  
  
3. <span data-ttu-id="03f55-113">複数の型パラメーターがある場合は、かっこ内にコンマ区切りのリストを指定します。</span><span class="sxs-lookup"><span data-stu-id="03f55-113">If you have more than one type parameter, make a comma-separated list inside the parentheses.</span></span> <span data-ttu-id="03f55-114">`Of` キーワードは繰り返さないでください。</span><span class="sxs-lookup"><span data-stu-id="03f55-114">Do not repeat the `Of` keyword.</span></span>  
  
4. <span data-ttu-id="03f55-115">型パラメーターに対して単純な代入以外の操作を実行する場合は、その型パラメーターの後に `As` 句を付けて 1 つ以上の *制約*を追加します。</span><span class="sxs-lookup"><span data-stu-id="03f55-115">If your code performs operations on a type parameter other than simple assignment, follow that type parameter with an `As` clause to add one or more *constraints*.</span></span> <span data-ttu-id="03f55-116">制約は、その型パラメーターに渡される型が、たとえば以下のような要件を満たすことを保証します。</span><span class="sxs-lookup"><span data-stu-id="03f55-116">A constraint guarantees that the type supplied for that type parameter satisfies a requirement such as the following:</span></span>  
  
    - <span data-ttu-id="03f55-117">コードで実行する `>`などの演算をサポートする</span><span class="sxs-lookup"><span data-stu-id="03f55-117">Supports an operation, such as `>`, that your code performs</span></span>  
  
    - <span data-ttu-id="03f55-118">コードでアクセスするメソッドなどのメンバーをサポートする</span><span class="sxs-lookup"><span data-stu-id="03f55-118">Supports a member, such as a method, that your code accesses</span></span>  
  
    - <span data-ttu-id="03f55-119">パラメーターなしのコンストラクターを公開する</span><span class="sxs-lookup"><span data-stu-id="03f55-119">Exposes a parameterless constructor</span></span>  
  
     <span data-ttu-id="03f55-120">制約を指定しない場合、コードで使用できる演算とメンバーは、 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md)でサポートされるものだけになります。</span><span class="sxs-lookup"><span data-stu-id="03f55-120">If you do not specify any constraints, the only operations and members your code can use are those supported by the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="03f55-121">詳細については、「 [Type List](../../../../visual-basic/language-reference/statements/type-list.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03f55-121">For more information, see [Type List](../../../../visual-basic/language-reference/statements/type-list.md).</span></span>  
  
5. <span data-ttu-id="03f55-122">渡された型を使って宣言する必要のある各クラス メンバーを識別し、それを `As` `typeparameter`として宣言します。</span><span class="sxs-lookup"><span data-stu-id="03f55-122">Identify every class member that is to be declared with a supplied type, and declare it `As` `typeparameter`.</span></span> <span data-ttu-id="03f55-123">これは、内部ストレージ、プロシージャのパラメーター、戻り値に適用されます。</span><span class="sxs-lookup"><span data-stu-id="03f55-123">This applies to internal storage, procedure parameters, and return values.</span></span>  
  
6. <span data-ttu-id="03f55-124">コードでは、 `itemType`に渡される可能性があるすべてのデータ型でサポートされる演算とメソッドだけを使用します。</span><span class="sxs-lookup"><span data-stu-id="03f55-124">Be sure your code uses only operations and methods that are supported by any data type it can supply to `itemType`.</span></span>  
  
     <span data-ttu-id="03f55-125">次のコード例は、ごく単純なリストを管理するクラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="03f55-125">The following example defines a class that manages a very simple list.</span></span> <span data-ttu-id="03f55-126">このクラスは、リストを内部配列 `items`に格納します。このクラスを使用するコードでは、このリストの要素のデータ型を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="03f55-126">It holds the list in the internal array `items`, and the using code can declare the data type of the list elements.</span></span> <span data-ttu-id="03f55-127">パラメーター化されたコンストラクターを使用すると、コードを使用して `items`の上限を設定でき、パラメーターなしのコンストラクターはこれを9に設定します (合計10個の項目)。</span><span class="sxs-lookup"><span data-stu-id="03f55-127">A parameterized constructor allows the using code to set the upper bound of `items`, and the parameterless constructor sets this to 9 (for a total of 10 items).</span></span>  
  
     [!code-vb[VbVbalrDataTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#7)]  
  
     <span data-ttu-id="03f55-128">`simpleList` からは、 `Integer` 値のリストを格納するクラス、 `String` 値のリストを格納するクラス、 `Date` 値のリストを格納するクラスなどを宣言できます。</span><span class="sxs-lookup"><span data-stu-id="03f55-128">You can declare a class from `simpleList` to hold a list of `Integer` values, another class to hold a list of `String` values, and another to hold `Date` values.</span></span> <span data-ttu-id="03f55-129">リスト メンバーのデータ型が異なるだけで、これらすべてのクラスから作成されるオブジェクトの動作はまったく同じです。</span><span class="sxs-lookup"><span data-stu-id="03f55-129">Except for the data type of the list members, objects created from all these classes behave identically.</span></span>  
  
     <span data-ttu-id="03f55-130">使用するコードから `itemType` に渡す型引数としては、 `Boolean` や `Double`などの組み込みの型、構造体、列挙、任意の型のクラス (アプリケーションで独自に定義したクラスを含む) を使用できます。</span><span class="sxs-lookup"><span data-stu-id="03f55-130">The type argument that the using code supplies to `itemType` can be an intrinsic type such as `Boolean` or `Double`, a structure, an enumeration, or any type of class, including one that your application defines.</span></span>  
  
     <span data-ttu-id="03f55-131">`simpleList` クラスをテストするには、次のコードを使用します。</span><span class="sxs-lookup"><span data-stu-id="03f55-131">You can test the class `simpleList` with the following code.</span></span>  
  
     [!code-vb[VbVbalrDataTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDataTypes/VB/Class1.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="03f55-132">参照</span><span class="sxs-lookup"><span data-stu-id="03f55-132">See also</span></span>

- [<span data-ttu-id="03f55-133">データの種類</span><span class="sxs-lookup"><span data-stu-id="03f55-133">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="03f55-134">Visual Basic におけるジェネリック型</span><span class="sxs-lookup"><span data-stu-id="03f55-134">Generic Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="03f55-135">言語への非依存性、および言語非依存コンポーネント</span><span class="sxs-lookup"><span data-stu-id="03f55-135">Language Independence and Language-Independent Components</span></span>](../../../../standard/language-independence-and-language-independent-components.md)
- [<span data-ttu-id="03f55-136">Of</span><span class="sxs-lookup"><span data-stu-id="03f55-136">Of</span></span>](../../../../visual-basic/language-reference/statements/of-clause.md)
- [<span data-ttu-id="03f55-137">型リスト</span><span class="sxs-lookup"><span data-stu-id="03f55-137">Type List</span></span>](../../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="03f55-138">方法 : ジェネリック クラスを使用する</span><span class="sxs-lookup"><span data-stu-id="03f55-138">How to: Use a Generic Class</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="03f55-139">Object Data Type</span><span class="sxs-lookup"><span data-stu-id="03f55-139">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
