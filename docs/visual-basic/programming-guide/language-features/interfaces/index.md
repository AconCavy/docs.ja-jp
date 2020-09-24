---
title: インターフェイス
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, interfaces
- interfaces [Visual Basic], Visual Basic
- interfaces
- interfaces [Visual Basic]
ms.assetid: 61b06674-12c9-430b-be68-cc67ecee1f5b
ms.openlocfilehash: ac5db62fec3548bfd4a99477958f4f29463267c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057833"
---
# <a name="interfaces-visual-basic"></a><span data-ttu-id="27bf0-102">インターフェイス (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27bf0-102">Interfaces (Visual Basic)</span></span>

<span data-ttu-id="27bf0-103">*インターフェイス*は、クラスが実装できるプロパティ、メソッド、およびイベントを定義します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-103">*Interfaces* define the properties, methods, and events that classes can implement.</span></span> <span data-ttu-id="27bf0-104">インターフェイスでは、密接に関連するプロパティ、メソッド、およびイベントの小さなグループとして機能を定義できます。これにより、既存のコードを損なうことなく、インターフェイスを拡張して実装を開発できるため、互換性の問題を減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-104">Interfaces allow you to define features as small groups of closely related properties, methods, and events; this reduces compatibility problems because you can develop enhanced implementations for your interfaces without jeopardizing existing code.</span></span> <span data-ttu-id="27bf0-105">追加のインターフェイスと実装を開発することで、いつでも新しい機能を追加できます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-105">You can add new features at any time by developing additional interfaces and implementations.</span></span>  
  
 <span data-ttu-id="27bf0-106">クラスの継承の代わりにインターフェイスを使用する方が望ましい理由が、その他にもいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="27bf0-106">There are several other reasons why you might want to use interfaces instead of class inheritance:</span></span>  
  
- <span data-ttu-id="27bf0-107">インターフェイスは、アプリケーションが特定の機能を提供するために関連性の低い多数のオブジェクトの種類を必要とする状況に、より適しています。</span><span class="sxs-lookup"><span data-stu-id="27bf0-107">Interfaces are better suited to situations in which your applications require many possibly unrelated object types to provide certain functionality.</span></span>  
  
- <span data-ttu-id="27bf0-108">インターフェイスは、複数のインターフェイスを実装できる単一の実装を定義できるため、基底クラスよりも柔軟です。</span><span class="sxs-lookup"><span data-stu-id="27bf0-108">Interfaces are more flexible than base classes because you can define a single implementation that can implement multiple interfaces.</span></span>  
  
- <span data-ttu-id="27bf0-109">インターフェイスは、基底クラスから実装を継承する必要がない状況に、より適しています。</span><span class="sxs-lookup"><span data-stu-id="27bf0-109">Interfaces are better in situations in which you do not have to inherit implementation from a base class.</span></span>  
  
- <span data-ttu-id="27bf0-110">インターフェイスは、クラスの継承を使用できない場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="27bf0-110">Interfaces are useful when you cannot use class inheritance.</span></span> <span data-ttu-id="27bf0-111">たとえば、構造体はクラスから継承できませんが、インターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-111">For example, structures cannot inherit from classes, but they can implement interfaces.</span></span>  
  
## <a name="declaring-interfaces"></a><span data-ttu-id="27bf0-112">インターフェイスの宣言</span><span class="sxs-lookup"><span data-stu-id="27bf0-112">Declaring Interfaces</span></span>  

 <span data-ttu-id="27bf0-113">インターフェイスの定義は、`Interface` ステートメントと `End Interface` ステートメントで囲みます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-113">Interface definitions are enclosed within the `Interface` and `End Interface` statements.</span></span> <span data-ttu-id="27bf0-114">`Interface` ステートメントの後に、オプションで`Inherits` ステートメントを追加して、継承されるインターフェイスを 1 つ以上指定することができます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-114">Following the `Interface` statement, you can add an optional `Inherits` statement that lists one or more inherited interfaces.</span></span> <span data-ttu-id="27bf0-115">`Inherits` ステートメントは、宣言内のコメントを除く他のすべてのステートメントより前に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27bf0-115">The `Inherits` statements must precede all other statements in the declaration except comments.</span></span> <span data-ttu-id="27bf0-116">インターフェイス定義の残りのステートメントは、`Event`、`Sub`、`Function`、`Property`、`Interface`、`Class`、`Structure`、および `Enum` ステートメントです。</span><span class="sxs-lookup"><span data-stu-id="27bf0-116">The remaining statements in the interface definition should be `Event`, `Sub`, `Function`, `Property`, `Interface`, `Class`, `Structure`, and `Enum` statements.</span></span> <span data-ttu-id="27bf0-117">インターフェイスには、`End Sub` や `End Property` など、実装コードや実装コードに関連付けられているステートメントを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="27bf0-117">Interfaces cannot contain any implementation code or statements associated with implementation code, such as `End Sub` or `End Property`.</span></span>  
  
 <span data-ttu-id="27bf0-118">名前空間内で、インターフェイス ステートメントは既定では `Friend` ですが、明示的に `Public` または `Friend` として宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-118">In a namespace, interface statements are `Friend` by default, but they can also be explicitly declared as `Public` or `Friend`.</span></span> <span data-ttu-id="27bf0-119">クラス、モジュール、インターフェイス、および構造体内で定義されたインターフェイスは、既定では `Public` ですが、明示的に `Public`、`Friend`、`Protected`、または `Private` として宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-119">Interfaces defined within classes, modules, interfaces, and structures are `Public` by default, but they can also be explicitly declared as `Public`, `Friend`, `Protected`, or `Private`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="27bf0-120">`Shadows` キーワードは、すべてのインターフェイス メンバーに適用できます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-120">The `Shadows` keyword can be applied to all interface members.</span></span> <span data-ttu-id="27bf0-121">`Overloads` キーワードは、インターフェイス定義で宣言された `Sub`、`Function`、および `Property` ステートメントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-121">The `Overloads` keyword can be applied to `Sub`, `Function`, and `Property` statements declared in an interface definition.</span></span> <span data-ttu-id="27bf0-122">さらに、`Property` ステートメントには `Default`、`ReadOnly`、または `WriteOnly` 修飾子を付けることができます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-122">In addition, `Property` statements can have the `Default`, `ReadOnly`, or `WriteOnly` modifiers.</span></span> <span data-ttu-id="27bf0-123">他の修飾子 (`Public`、`Private`、`Friend`、`Protected`、`Shared`、`Overrides`、`MustOverride`、または `Overridable`) は許可されていません。</span><span class="sxs-lookup"><span data-stu-id="27bf0-123">None of the other modifiers—`Public`, `Private`, `Friend`, `Protected`, `Shared`, `Overrides`, `MustOverride`, or `Overridable`—are allowed.</span></span> <span data-ttu-id="27bf0-124">詳細については、「[宣言コンテキストと既定のアクセス レベル](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27bf0-124">For more information, see [Declaration Contexts and Default Access Levels](../../../language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="27bf0-125">たとえば、次のコードは、1 つの関数、1 つのプロパティ、および 1 つのイベントを持つインターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-125">For example, the following code defines an interface with one function, one property, and one event.</span></span>  
  
 [!code-vb[VbVbalrOOP#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#17)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="27bf0-126">インターフェイスの実装</span><span class="sxs-lookup"><span data-stu-id="27bf0-126">Implementing Interfaces</span></span>  

 <span data-ttu-id="27bf0-127">Visual Basic では、予約語 `Implements` が 2 つの方法で使用されます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-127">The Visual Basic reserved word `Implements` is used in two ways.</span></span> <span data-ttu-id="27bf0-128">`Implements` ステートメントは、クラスまたは構造体がインターフェイスを実装することを示します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-128">The `Implements` statement signifies that a class or structure implements an interface.</span></span> <span data-ttu-id="27bf0-129">`Implements` キーワードは、クラス メンバーまたは構造体メンバーが特定のインターフェイス メンバーを実装することを示します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-129">The `Implements` keyword signifies that a class member or structure member implements a specific interface member.</span></span>  
  
### <a name="implements-statement"></a><span data-ttu-id="27bf0-130">Implements ステートメント</span><span class="sxs-lookup"><span data-stu-id="27bf0-130">Implements Statement</span></span>  

 <span data-ttu-id="27bf0-131">クラスまたは構造体が 1 つ以上のインターフェイスを実装する場合は、`Implements` ステートメントを `Class` または `Structure` ステートメントの直後に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27bf0-131">If a class or structure implements one or more interfaces, it must include the `Implements` statement immediately after the `Class` or `Structure` statement.</span></span> <span data-ttu-id="27bf0-132">`Implements` ステートメントには、クラスによって実装されるインターフェイスのコンマ区切りのリストが必要です。</span><span class="sxs-lookup"><span data-stu-id="27bf0-132">The `Implements` statement requires a comma-separated list of interfaces to be implemented by a class.</span></span> <span data-ttu-id="27bf0-133">クラスまたは構造体は、すべてのインターフェイス メンバーを `Implements` キーワードを使用して実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27bf0-133">The class or structure must implement all interface members using the `Implements` keyword.</span></span>  
  
### <a name="implements-keyword"></a><span data-ttu-id="27bf0-134">Implements キーワード</span><span class="sxs-lookup"><span data-stu-id="27bf0-134">Implements Keyword</span></span>  

 <span data-ttu-id="27bf0-135">`Implements` キーワードには、実装されるインターフェイス メンバーのコンマ区切りのリストが必要です。</span><span class="sxs-lookup"><span data-stu-id="27bf0-135">The `Implements` keyword requires a comma-separated list of interface members to be implemented.</span></span> <span data-ttu-id="27bf0-136">一般的には、1 つのインターフェイス メンバーのみが指定されますが、複数のメンバーを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-136">Generally, only a single interface member is specified, but you can specify multiple members.</span></span> <span data-ttu-id="27bf0-137">インターフェイス メンバーの指定は、クラス内の implements ステートメントで指定する必要があるインターフェイス名と、ピリオドと、実装されるメンバー関数、プロパティ、またはイベントの名前で構成されます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-137">The specification of an interface member consists of the interface name, which must be specified in an implements statement within the class; a period; and the name of the member function, property, or event to be implemented.</span></span> <span data-ttu-id="27bf0-138">インターフェイス メンバーを実装するメンバーの名前には、有効な任意の識別子を使用できます。また、Visual Basic の以前のバージョンで使用されている `InterfaceName_MethodName` 規則の制限を受けません。</span><span class="sxs-lookup"><span data-stu-id="27bf0-138">The name of a member that implements an interface member can use any legal identifier, and it is not limited to the `InterfaceName_MethodName` convention used in earlier versions of Visual Basic.</span></span>  
  
 <span data-ttu-id="27bf0-139">たとえば、次のコードは、インターフェイスのメソッドを実装する `Sub1` という名前のサブルーチンを宣言する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="27bf0-139">For example, the following code shows how to declare a subroutine named `Sub1` that implements a method of an interface:</span></span>  
  
 [!code-vb[VbVbalrOOP#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#69)]  
  
 <span data-ttu-id="27bf0-140">実装するメンバーのパラメーターの型と戻り値の型は、インターフェイスのインターフェイス プロパティまたはメンバー宣言と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27bf0-140">The parameter types and return types of the implementing member must match the interface property or member declaration in the interface.</span></span> <span data-ttu-id="27bf0-141">インターフェイスの要素を実装する最も一般的な方法は、前の例で示されているように、インターフェイスと同じ名前を持つメンバーを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="27bf0-141">The most common way to implement an element of an interface is with a member that has the same name as the interface, as shown in the previous example.</span></span>  
  
 <span data-ttu-id="27bf0-142">インターフェイス メソッドの実装を宣言するには、インスタンス メソッドの宣言で有効な任意の属性を使用できます。たとえば、`Overloads`、`Overrides`、`Overridable`、`Public`、`Private`、`Protected`、`Friend`、`Protected Friend`、`MustOverride`、`Default`、`Static` などです。</span><span class="sxs-lookup"><span data-stu-id="27bf0-142">To declare the implementation of an interface method, you can use any attributes that are legal on instance method declarations, including `Overloads`, `Overrides`, `Overridable`, `Public`, `Private`, `Protected`, `Friend`, `Protected Friend`, `MustOverride`, `Default`, and `Static`.</span></span> <span data-ttu-id="27bf0-143">`Shared` 属性は、インスタンス メソッドではなくクラスを定義するため、無効です。</span><span class="sxs-lookup"><span data-stu-id="27bf0-143">The `Shared` attribute is not legal since it defines a class rather than an instance method.</span></span>  
  
 <span data-ttu-id="27bf0-144">`Implements` を使用すると、次の例のように、インターフェイスで定義されている複数のメソッドを実装する 1 つのメソッドを記述することもできます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-144">Using `Implements`, you can also write a single method that implements multiple methods defined in an interface, as in the following example:</span></span>  
  
 [!code-vb[VbVbalrOOP#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#70)]  
  
 <span data-ttu-id="27bf0-145">インターフェイス メンバーを実装するには、プライベート メンバーを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-145">You can use a private member to implement an interface member.</span></span> <span data-ttu-id="27bf0-146">プライベート メンバーでインターフェイスのメンバーを実装すると、そのメンバーは、クラスのオブジェクト変数で直接利用できない場合でも、インターフェイスを通じて利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="27bf0-146">When a private member implements a member of an interface, that member becomes available by way of the interface even though it is not available directly on object variables for the class.</span></span>  
  
### <a name="interface-implementation-examples"></a><span data-ttu-id="27bf0-147">インターフェイスの実装の例</span><span class="sxs-lookup"><span data-stu-id="27bf0-147">Interface Implementation Examples</span></span>  

 <span data-ttu-id="27bf0-148">インターフェイスを実装するクラスは、そのすべてのプロパティ、メソッド、およびイベントを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27bf0-148">Classes that implement an interface must implement all its properties, methods, and events.</span></span>  
  
 <span data-ttu-id="27bf0-149">次の例では、2 つのインターフェイスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-149">The following example defines two interfaces.</span></span> <span data-ttu-id="27bf0-150">2 番目のインターフェイス `Interface2` は `Interface1` を継承し、追加のプロパティとメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-150">The second interface, `Interface2`, inherits `Interface1` and defines an additional property and method.</span></span>  
  
 [!code-vb[VbVbalrOOP#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#39)]  
  
 <span data-ttu-id="27bf0-151">次の例は、前の例で定義されたインターフェイスである `Interface1` を実装します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-151">The next example implements `Interface1`, the interface defined in the previous example:</span></span>  
  
 [!code-vb[VbVbalrOOP#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#40)]  
  
 <span data-ttu-id="27bf0-152">最後の例は、`Interface1` から継承されたメソッドを含めて、`Interface2` を実装します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-152">The final example implements `Interface2`, including a method inherited from `Interface1`:</span></span>  
  
 [!code-vb[VbVbalrOOP#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#41)]  
  
 <span data-ttu-id="27bf0-153">readwrite プロパティを使用して、readonly プロパティを実装できます (つまり、実装するクラスで readonly を宣言する必要はありません)。</span><span class="sxs-lookup"><span data-stu-id="27bf0-153">You can implement a readonly property with a readwrite property (that is, you do not have to declare it readonly in the implementing class).</span></span>  <span data-ttu-id="27bf0-154">インターフェイスを実装する場合、少なくともインターフェイスが宣言しているメンバーを実装することになりますが、プロパティを書き込み可能にするなど、追加の機能を提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="27bf0-154">Implementing an interface promises to implement at least the members that the interface declares, but you can offer more functionality, such as allowing your property to be writable.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="27bf0-155">関連トピック</span><span class="sxs-lookup"><span data-stu-id="27bf0-155">Related Topics</span></span>  
  
|<span data-ttu-id="27bf0-156">Title</span><span class="sxs-lookup"><span data-stu-id="27bf0-156">Title</span></span>|<span data-ttu-id="27bf0-157">説明</span><span class="sxs-lookup"><span data-stu-id="27bf0-157">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="27bf0-158">チュートリアル: インターフェイスの作成と実装</span><span class="sxs-lookup"><span data-stu-id="27bf0-158">Walkthrough: Creating and Implementing Interfaces</span></span>](walkthrough-creating-and-implementing-interfaces.md)|<span data-ttu-id="27bf0-159">独自のインターフェイスを定義および実装する処理の詳細な手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-159">Provides a detailed procedure that takes you through the process of defining and implementing your own interface.</span></span>|  
|[<span data-ttu-id="27bf0-160">ジェネリック インターフェイスの分散</span><span class="sxs-lookup"><span data-stu-id="27bf0-160">Variance in Generic Interfaces</span></span>](../../concepts/covariance-contravariance/variance-in-generic-interfaces.md)|<span data-ttu-id="27bf0-161">ジェネリック インターフェイスでの共変性と反変性について説明し、.NET Framework でのバリアント ジェネリック インターフェイスの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="27bf0-161">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
