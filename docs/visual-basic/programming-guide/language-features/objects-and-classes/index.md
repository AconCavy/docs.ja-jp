---
title: オブジェクトとクラス
ms.date: 05/26/2020
helpviewer_keywords:
- classes [Visual Basic]
- objects [Visual Basic]
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
ms.openlocfilehash: 9e3cf262ef617a1ae5ee92bcc3d6fd5c691602f9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "85503845"
---
# <a name="objects-and-classes-in-visual-basic"></a><span data-ttu-id="b6c4d-102">Visual Basic のオブジェクトとクラス</span><span class="sxs-lookup"><span data-stu-id="b6c4d-102">Objects and classes in Visual Basic</span></span>

<span data-ttu-id="b6c4d-103">"*オブジェクト*" は、1 つの単位として扱うことができるコードとデータの組み合わせです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-103">An *object* is a combination of code and data that can be treated as a unit.</span></span> <span data-ttu-id="b6c4d-104">オブジェクトは、コントロールやフォームのように、アプリケーションの一部になることができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-104">An object can be a piece of an application, like a control or a form.</span></span> <span data-ttu-id="b6c4d-105">アプリケーション全体も、オブジェクトになることができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-105">An entire application can also be an object.</span></span>

<span data-ttu-id="b6c4d-106">Visual Basic でアプリケーションを作成するときは、常にオブジェクトを操作します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-106">When you create an application in Visual Basic, you constantly work with objects.</span></span> <span data-ttu-id="b6c4d-107">Visual Basic に用意されている、コントロール、フォーム、データ アクセスなどのオブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-107">You can use objects provided by Visual Basic, such as controls, forms, and data access objects.</span></span> <span data-ttu-id="b6c4d-108">他のアプリケーションのオブジェクトを、作成中の Visual Basic アプリケーションの中で使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-108">You can also use objects from other applications within your Visual Basic application.</span></span> <span data-ttu-id="b6c4d-109">独自のオブジェクトを作成し、それらのプロパティとメソッドを追加で定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-109">You can even create your own objects and define additional properties and methods for them.</span></span> <span data-ttu-id="b6c4d-110">オブジェクトはプログラムの作成済みの構成要素として機能し、コードを一度記述すれば、何度も再利用できます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-110">Objects act like prefabricated building blocks for programs — they let you write a piece of code once and reuse it over and over.</span></span>

<span data-ttu-id="b6c4d-111">このトピックでは、オブジェクトの詳細について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-111">This topic discusses objects in detail.</span></span>

## <a name="objects-and-classes"></a><span data-ttu-id="b6c4d-112">オブジェクトとクラス</span><span class="sxs-lookup"><span data-stu-id="b6c4d-112">Objects and classes</span></span>

<span data-ttu-id="b6c4d-113">Visual Basic 内の各オブジェクトは、"*クラス*" によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-113">Each object in Visual Basic is defined by a *class*.</span></span> <span data-ttu-id="b6c4d-114">クラスは、オブジェクトの変数、プロパティ、プロシージャ、およびイベントを記述します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-114">A class describes the variables, properties, procedures, and events of an object.</span></span> <span data-ttu-id="b6c4d-115">オブジェクトはクラスのインスタンスです。クラスを定義したら、必要な数のオブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-115">Objects are instances of classes; you can create as many objects you need once you have defined a class.</span></span>

<span data-ttu-id="b6c4d-116">オブジェクトとそのクラス間の関係を理解するために、クッキーの抜き型とクッキーを考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-116">To understand the relationship between an object and its class, think of cookie cutters and cookies.</span></span> <span data-ttu-id="b6c4d-117">クッキーの抜き型はクラスです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-117">The cookie cutter is the class.</span></span> <span data-ttu-id="b6c4d-118">それは、クッキーの特徴 (大きさや形など) を定義します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-118">It defines the characteristics of each cookie, for example size and shape.</span></span> <span data-ttu-id="b6c4d-119">クラスを使用して、オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-119">The class is used to create objects.</span></span> <span data-ttu-id="b6c4d-120">オブジェクトはクッキーです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-120">The objects are the cookies.</span></span>

<span data-ttu-id="b6c4d-121">メンバーにアクセスするには、そのオブジェクトを作成する必要があります。ただし、クラスのオブジェクトを使用せずにアクセスできる [`Shared`](../../../language-reference/modifiers/shared.md) のメンバーは除きます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-121">You must create an object before you can access its members, except for [`Shared`](../../../language-reference/modifiers/shared.md) members which can be accessed without an object of the class.</span></span>

### <a name="create-an-object-from-a-class"></a><span data-ttu-id="b6c4d-122">クラスからオブジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="b6c4d-122">Create an object from a class</span></span>

1. <span data-ttu-id="b6c4d-123">オブジェクトの作成元となるクラスを決定するか、独自のクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-123">Determine from which class you want to create an object, or define your own class.</span></span> <span data-ttu-id="b6c4d-124">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-124">For example:</span></span>

   ```vb
   Public Class Customer
       Public Property AccountNumber As Integer
   End Class
   ```

2. <span data-ttu-id="b6c4d-125">[Dim ステートメント](../../../language-reference/statements/dim-statement.md)を記述して、クラス インスタンスを割り当てることができる変数を作成します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-125">Write a [Dim Statement](../../../language-reference/statements/dim-statement.md) to create a variable to which you can assign a class instance.</span></span> <span data-ttu-id="b6c4d-126">変数は、目的のクラスの型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-126">The variable should be of the type of the desired class.</span></span>

   ```vb
   Dim nextCustomer As Customer
   ```

3. <span data-ttu-id="b6c4d-127">[New 演算子](../../../language-reference/operators/new-operator.md)キーワードを追加して、変数をクラスの新しいインスタンスに初期化します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-127">Add the [New Operator](../../../language-reference/operators/new-operator.md) keyword to initialize the variable to a new instance of the class.</span></span>

   ```vb
   Dim nextCustomer As New Customer
   ```

4. <span data-ttu-id="b6c4d-128">これで、オブジェクト変数を使用してクラスのメンバーにアクセスできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-128">You can now access the members of the class through the object variable.</span></span>

   ```vb
   nextCustomer.AccountNumber = lastAccountNumber + 1
   ```

> [!NOTE]
> <span data-ttu-id="b6c4d-129">可能であれば、変数は、変数に割り当てる予定のクラスの型で宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-129">Whenever possible, you should declare the variable to be of the class type you intend to assign to it.</span></span> <span data-ttu-id="b6c4d-130">これは、*事前バインディング*と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-130">This is called *early binding*.</span></span> <span data-ttu-id="b6c4d-131">コンパイル時にクラスの型を把握していない場合は、変数を [Object データ型](../../../language-reference/data-types/object-data-type.md)で宣言することで、*遅延バインディング*を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-131">If you don't know the class type at compile time, you can invoke *late binding* by declaring the variable to be of the [Object Data Type](../../../language-reference/data-types/object-data-type.md).</span></span> <span data-ttu-id="b6c4d-132">ただし、遅延バインディングでは、パフォーマンスが低下し、実行時のオブジェクトのメンバーへのアクセスが制限される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-132">However, late binding can make performance slower and limit access to the run-time object's members.</span></span> <span data-ttu-id="b6c4d-133">詳細については、「[オブジェクト変数の宣言](../variables/object-variable-declaration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-133">For more information, see [Object Variable Declaration](../variables/object-variable-declaration.md).</span></span>

### <a name="multiple-instances"></a><span data-ttu-id="b6c4d-134">複数インスタンス</span><span class="sxs-lookup"><span data-stu-id="b6c4d-134">Multiple instances</span></span>

<span data-ttu-id="b6c4d-135">多くの場合、クラスから新しく作成されたオブジェクトは互いに同一です。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-135">Objects newly created from a class are often identical to each other.</span></span> <span data-ttu-id="b6c4d-136">ただし、個々のオブジェクトとして存在した後、それぞれの変数とプロパティは、他のインスタンスとは無関係に変更することができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-136">Once they exist as individual objects, however, their variables and properties can be changed independently of the other instances.</span></span> <span data-ttu-id="b6c4d-137">たとえば、次の 3 つのチェック ボックスをフォームに追加する場合、各チェック ボックスのオブジェクトは、<xref:System.Windows.Forms.CheckBox> クラスのインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-137">For example, if you add three check boxes to a form, each check box object is an instance of the <xref:System.Windows.Forms.CheckBox> class.</span></span> <span data-ttu-id="b6c4d-138">個々の <xref:System.Windows.Forms.CheckBox> オブジェクトは、クラスによって定義された特性と機能 (プロパティ、変数、プロシージャ、およびイベント) の共通セットを共有します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-138">The individual <xref:System.Windows.Forms.CheckBox> objects share a common set of characteristics and capabilities (properties, variables, procedures, and events) defined by the class.</span></span> <span data-ttu-id="b6c4d-139">ただし、それぞれが独自の名前を持ち、別々に有効または無効にすることができ、フォームの異なる場所に配置することができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-139">However, each has its own name, can be separately enabled and disabled, and can be placed in a different location on the form.</span></span>

## <a name="object-members"></a><span data-ttu-id="b6c4d-140">オブジェクトのメンバー</span><span class="sxs-lookup"><span data-stu-id="b6c4d-140">Object members</span></span>

<span data-ttu-id="b6c4d-141">オブジェクトはアプリケーションの要素であり、クラスの "*インスタンス*" を表しています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-141">An object is an element of an application, representing an *instance* of a class.</span></span> <span data-ttu-id="b6c4d-142">フィールド、プロパティ、メソッド、およびイベントは、オブジェクトの構成要素であり、オブジェクトの*メンバー*を構成します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-142">Fields, properties, methods, and events are the building blocks of objects and constitute their *members*.</span></span>

### <a name="member-access"></a><span data-ttu-id="b6c4d-143">メンバー アクセス</span><span class="sxs-lookup"><span data-stu-id="b6c4d-143">Member Access</span></span>

<span data-ttu-id="b6c4d-144">オブジェクトのメンバーにアクセスするには、オブジェクト変数の名前、ピリオド (`.`)、およびメンバーの名前をこの順序で指定します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-144">You access a member of an object by specifying, in order, the name of the object variable, a period (`.`), and the name of the member.</span></span> <span data-ttu-id="b6c4d-145"><xref:System.Windows.Forms.Label> オブジェクトの <xref:System.Windows.Forms.Control.Text%2A> プロパティを設定する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-145">The following example sets the <xref:System.Windows.Forms.Control.Text%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
warningLabel.Text = "Data not saved"
```

#### <a name="intellisense-listing-of-members"></a><span data-ttu-id="b6c4d-146">メンバーの IntelliSense の一覧</span><span class="sxs-lookup"><span data-stu-id="b6c4d-146">IntelliSense listing of members</span></span>

<span data-ttu-id="b6c4d-147">IntelliSense は、[メンバーの一覧] オプションが呼び出されたとき (たとえばメンバー アクセス演算子としてピリオド (`.`) が入力されたとき) に、クラスのメンバーを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-147">IntelliSense lists members of a class when you invoke its List Members option, for example when you type a period (`.`) as a member-access operator.</span></span> <span data-ttu-id="b6c4d-148">ピリオドに続けて、そのクラスのインスタンスとして宣言された変数の名前を入力すると、IntelliSense は、すべてのインスタンス メンバーを表示しますが、共有メンバーは表示しません。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-148">If you type the period following the name of a variable declared as an instance of that class, IntelliSense lists all the instance members and none of the shared members.</span></span> <span data-ttu-id="b6c4d-149">クラス名に続けてピリオドを入力すると、IntelliSense は、すべての共有メンバーを表示し、インスタンス メンバーは表示しません。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-149">If you type the period following the class name itself, IntelliSense lists all the shared members and none of the instance members.</span></span> <span data-ttu-id="b6c4d-150">詳細については、「[IntelliSense の使用](/visualstudio/ide/using-intellisense)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-150">For more information, see [Using IntelliSense](/visualstudio/ide/using-intellisense).</span></span>

### <a name="fields-and-properties"></a><span data-ttu-id="b6c4d-151">フィールドとプロパティ</span><span class="sxs-lookup"><span data-stu-id="b6c4d-151">Fields and properties</span></span>

<span data-ttu-id="b6c4d-152">"*フィールド*" と "*プロパティ*" は、オブジェクトに格納されている情報を表します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-152">*Fields* and *properties* represent information stored in an object.</span></span> <span data-ttu-id="b6c4d-153">代入ステートメントによる値の取得と設定は、プロシージャでローカル変数の取得と設定を行うのと同じ方法で実行します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-153">You retrieve and set their values with assignment statements the same way you retrieve and set local variables in a procedure.</span></span> <span data-ttu-id="b6c4d-154">次の例では <xref:System.Windows.Forms.Control.Width%2A> プロパティを取得し、<xref:System.Windows.Forms.Label> オブジェクトの <xref:System.Windows.Forms.Control.ForeColor%2A> プロパティを設定しています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-154">The following example retrieves the <xref:System.Windows.Forms.Control.Width%2A> property and sets the <xref:System.Windows.Forms.Control.ForeColor%2A> property of a <xref:System.Windows.Forms.Label> object.</span></span>

```vb
Dim warningWidth As Integer = warningLabel.Width
warningLabel.ForeColor = System.Drawing.Color.Red
```

<span data-ttu-id="b6c4d-155">フィールドは、"*メンバー変数*" とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-155">Note that a field is also called a *member variable*.</span></span>

<span data-ttu-id="b6c4d-156">次の場合は、プロパティ プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-156">Use property procedures when:</span></span>

- <span data-ttu-id="b6c4d-157">値を設定または取得するタイミングと方法を制御する必要がある。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-157">You need to control when and how a value is set or retrieved.</span></span>

- <span data-ttu-id="b6c4d-158">プロパティに、検証する必要がある適切に定義された一連の値がある。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-158">The property has a well-defined set of values that need to be validated.</span></span>

- <span data-ttu-id="b6c4d-159">値を設定することで、オブジェクトの状態をはっきりと変更する (例: `IsVisible` プロパティ)。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-159">Setting the value causes some perceptible change in the object's state, such as an `IsVisible` property.</span></span>

- <span data-ttu-id="b6c4d-160">プロパティを設定することで、他の内部変数またはその他のプロパティの値を変更する。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-160">Setting the property causes changes to other internal variables or to the values of other properties.</span></span>

- <span data-ttu-id="b6c4d-161">プロパティを設定または取得する前に、一連の手順を実行する必要がある。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-161">A set of steps must be performed before the property can be set or retrieved.</span></span>

<span data-ttu-id="b6c4d-162">次の場合は、フィールドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-162">Use fields when:</span></span>

- <span data-ttu-id="b6c4d-163">値は自己検証型である。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-163">The value is of a self-validating type.</span></span> <span data-ttu-id="b6c4d-164">たとえば、`Boolean` 変数に `True` または `False` の値が割り当てられた場合は、エラーまたはデータの自動変換が発生します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-164">For example, an error or automatic data conversion occurs if a value other than `True` or `False` is assigned to a `Boolean` variable.</span></span>

- <span data-ttu-id="b6c4d-165">データ型によってサポートされている範囲の値はすべて有効である。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-165">Any value in the range supported by the data type is valid.</span></span> <span data-ttu-id="b6c4d-166">これは、`Single` 型または `Double` 型の多くのプロパティに当てはまります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-166">This is true of many properties of type `Single` or `Double`.</span></span>

- <span data-ttu-id="b6c4d-167">プロパティは `String` データ型であり、文字列のサイズまたは値に制限がない。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-167">The property is a `String` data type, and there is no constraint on the size or value of the string.</span></span>

- <span data-ttu-id="b6c4d-168">詳細については、「[プロパティ プロシージャ](../procedures/property-procedures.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-168">For more information, see [Property Procedures](../procedures/property-procedures.md).</span></span>

> [!TIP]
> <span data-ttu-id="b6c4d-169">定数でないフィールドは常に非公開にしておいてください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-169">Always keep the non-constant fields private.</span></span> <span data-ttu-id="b6c4d-170">公開する場合は、代わりにプロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-170">When you want to make it public, use a property instead.</span></span>

### <a name="methods"></a><span data-ttu-id="b6c4d-171">メソッド</span><span class="sxs-lookup"><span data-stu-id="b6c4d-171">Methods</span></span>

<span data-ttu-id="b6c4d-172">"*メソッド*" は、オブジェクトが実行できる処理です。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-172">A *method* is an action that an object can perform.</span></span> <span data-ttu-id="b6c4d-173">たとえば、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> は、コンボ ボックスに新しいエントリを追加する <xref:System.Windows.Forms.ComboBox> オブジェクトのメソッドです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-173">For example, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> is a method of the <xref:System.Windows.Forms.ComboBox> object that adds a new entry to a combo box.</span></span>

<span data-ttu-id="b6c4d-174">次の例は、<xref:System.Windows.Forms.Timer> オブジェクトの <xref:System.Windows.Forms.Timer.Start%2A> メソッドを示しています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-174">The following example demonstrates the <xref:System.Windows.Forms.Timer.Start%2A> method of a <xref:System.Windows.Forms.Timer> object.</span></span>

```vb
Dim safetyTimer As New System.Windows.Forms.Timer
safetyTimer.Start()
```

<span data-ttu-id="b6c4d-175">メソッドは、オブジェクトによって公開される "*プロシージャ*" です。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-175">Note that a method is simply a *procedure* that is exposed by an object.</span></span>

<span data-ttu-id="b6c4d-176">詳細については、「[プロシージャ](../procedures/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-176">For more information, see [Procedures](../procedures/index.md).</span></span>

### <a name="events"></a><span data-ttu-id="b6c4d-177">イベント</span><span class="sxs-lookup"><span data-stu-id="b6c4d-177">Events</span></span>

<span data-ttu-id="b6c4d-178">イベントは、マウスのクリックやキーの押下などのオブジェクトによって認識される操作であり、それに応答するコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-178">An event is an action recognized by an object, such as clicking the mouse or pressing a key, and for which you can write code to respond.</span></span> <span data-ttu-id="b6c4d-179">イベントは、ユーザーの操作またはプログラム コードの結果として発生する可能性がありますが、システムによって発生する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-179">Events can occur as a result of a user action or program code, or they can be caused by the system.</span></span> <span data-ttu-id="b6c4d-180">イベントを通知するコードを、イベントを "*発生させる*" と言い、イベントに応答するコードを、イベントを "*処理する*" と言います。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-180">Code that signals an event is said to *raise* the event, and code that responds to it is said to *handle* it.</span></span>

<span data-ttu-id="b6c4d-181">オブジェクトによって発生する独自のカスタム イベントを作成し、その他のオブジェクトで処理することもできます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-181">You can also develop your own custom events to be raised by your objects and handled by other objects.</span></span> <span data-ttu-id="b6c4d-182">詳細については、「[イベント](../events/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-182">For more information, see [Events](../events/index.md).</span></span>

### <a name="instance-members-and-shared-members"></a><span data-ttu-id="b6c4d-183">インスタンス メンバーと共有メンバー</span><span class="sxs-lookup"><span data-stu-id="b6c4d-183">Instance members and shared members</span></span>

<span data-ttu-id="b6c4d-184">クラスからオブジェクトを作成した結果が、そのクラスのインスタンスになります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-184">When you create an object from a class, the result is an instance of that class.</span></span> <span data-ttu-id="b6c4d-185">[Shared](../../../language-reference/modifiers/shared.md) キーワードなしで宣言されたメンバーは、"*インスタンス メンバー*" になり、特定のインスタンスにのみ属します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-185">Members that are not declared with the [Shared](../../../language-reference/modifiers/shared.md) keyword are *instance members*, which belong strictly to that particular instance.</span></span> <span data-ttu-id="b6c4d-186">あるインスタンスのインスタンス メンバーは、同じクラスの別のインスタンスに同じメンバーがあっても互いに独立しています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-186">An instance member in one instance is independent of the same member in another instance of the same class.</span></span> <span data-ttu-id="b6c4d-187">たとえばインスタンス メンバー変数は、インスタンスごとに異なる値を持つことができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-187">An instance member variable, for example, can have different values in different instances.</span></span>

<span data-ttu-id="b6c4d-188">`Shared` キーワード付きで宣言されたメンバーは "*共有メンバー*" になり、全体がクラスに属し、特定のインスタンスには属しません。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-188">Members declared with the `Shared` keyword are *shared members*, which belong to the class as a whole and not to any particular instance.</span></span> <span data-ttu-id="b6c4d-189">共有メンバーは、作成するクラスのインスタンスの数に関係なく 1 度だけ存在します。これは、インスタンスを作成していない場合でも同じです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-189">A shared member exists only once, no matter how many instances of its class you create, or even if you create no instances.</span></span> <span data-ttu-id="b6c4d-190">たとえば共有メンバー変数は、クラスにアクセスできるすべてのコードが使用できる 1 つの値のみを持っています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-190">A shared member variable, for example, has only one value, which is available to all code that can access the class.</span></span>

#### <a name="accessing-non-shared-members"></a><span data-ttu-id="b6c4d-191">非共有メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b6c4d-191">Accessing non-shared members</span></span>

1. <span data-ttu-id="b6c4d-192">オブジェクトがクラスから作成され、オブジェクト変数に割り当てられていることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-192">Make sure the object has been created from its class and assigned to an object variable.</span></span>

   ```vb
   Dim secondForm As New System.Windows.Forms.Form
   ```

2. <span data-ttu-id="b6c4d-193">メンバーにアクセスするステートメントで、オブジェクト変数名に続けて、"*メンバー アクセス演算子"*  (`.`) とメンバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-193">In the statement that accesses the member, follow the object variable name with the *member-access operator* (`.`) and then the member name.</span></span>

   ```vb
   secondForm.Show()
   ```

#### <a name="accessing-shared-members"></a><span data-ttu-id="b6c4d-194">共有メンバーへのアクセス</span><span class="sxs-lookup"><span data-stu-id="b6c4d-194">Accessing shared members</span></span>

- <span data-ttu-id="b6c4d-195">クラス名に続けて、"*メンバー アクセス演算子*" (`.`) とメンバー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-195">Follow the class name with the *member-access operator* (`.`) and then the member name.</span></span> <span data-ttu-id="b6c4d-196">オブジェクトの `Shared` メンバーは、常にクラス名から直接アクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-196">You should always access a `Shared` member of the object directly through the class name.</span></span>

   ```vb
   Console.WriteLine("This computer is called " & Environment.MachineName)
   ```

- <span data-ttu-id="b6c4d-197">既にクラスからオブジェクトを作成している場合は、オブジェクト変数を使用して `Shared` メンバーにアクセスすることもできます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-197">If you have already created an object from the class, you can alternatively access a `Shared` member through the object's variable.</span></span>

### <a name="differences-between-classes-and-modules"></a><span data-ttu-id="b6c4d-198">クラスとモジュールの違い</span><span class="sxs-lookup"><span data-stu-id="b6c4d-198">Differences between classes and modules</span></span>

<span data-ttu-id="b6c4d-199">クラスとモジュールの主な違いは、クラスはオブジェクトとしてインスタンス化できますが、標準モジュールではできないことです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-199">The main difference between classes and modules is that classes can be instantiated as objects while standard modules cannot.</span></span> <span data-ttu-id="b6c4d-200">標準モジュールのデータは 1 つしかないため、プログラムのある部分が標準モジュールのパブリック変数を変更した場合、その後、プログラムの他の部分がその変数を読み取ると、変更後の値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-200">Because there is only one copy of a standard module's data, when one part of your program changes a public variable in a standard module, any other part of the program gets the same value if it then reads that variable.</span></span> <span data-ttu-id="b6c4d-201">これに対し、オブジェクト データは、インスタンス化されたオブジェクトごとに個別に存在します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-201">In contrast, object data exists separately for each instantiated object.</span></span> <span data-ttu-id="b6c4d-202">別の相違点は、標準モジュールとは異なり、クラスはインターフェイスを実装できることです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-202">Another difference is that unlike standard modules, classes can implement interfaces.</span></span> <span data-ttu-id="b6c4d-203">クラスが [MustInherit](../../../language-reference/modifiers/mustinherit.md) 修飾子でマークされている場合、それを直接インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-203">If a class is marked with the [MustInherit](../../../language-reference/modifiers/mustinherit.md) modifier, it can't be instantiated directly.</span></span> <span data-ttu-id="b6c4d-204">ただし、これはモジュールとは異なります。モジュールとは異なり、継承できるためです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-204">However, it's still different from a module as it can be inherited while modules can't be inherited.</span></span>

> [!NOTE]
> <span data-ttu-id="b6c4d-205">`Shared` 修飾子は、クラス メンバーに適用された場合は、クラスの特定のインスタンスではなく、クラス自体に関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-205">When the `Shared` modifier is applied to a class member, it is associated with the class itself instead of a particular instance of the class.</span></span> <span data-ttu-id="b6c4d-206">メンバーへのアクセスは、モジュール メンバーへのアクセス方法と同じように、クラス名を使用して直接行います。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-206">The member is accessed directly by using the class name, the same way module members are accessed.</span></span>

<span data-ttu-id="b6c4d-207">さらに、クラスとモジュールは、メンバーに対して異なるスコープを使用します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-207">Classes and modules also use different scopes for their members.</span></span> <span data-ttu-id="b6c4d-208">クラス内に定義されているメンバーのスコープはクラスの特定のインスタンス内に限られ、オブジェクトの有効期間のみ存在します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-208">Members defined within a class are scoped within a specific instance of the class and exist only for the lifetime of the object.</span></span> <span data-ttu-id="b6c4d-209">クラスの外部からクラス メンバーにアクセスするには、"*オブジェクト*.*メンバー*" 形式の完全修飾名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-209">To access class members from outside a class, you must use fully qualified names in the format of *Object*.*Member*.</span></span>

<span data-ttu-id="b6c4d-210">その一方で、モジュール内に宣言されているメンバーは、既定ではパブリックにアクセスすることができ、モジュールにアクセスできるすべてのコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-210">On the other hand, members declared within a module are publicly accessible by default, and can be accessed by any code that can access the module.</span></span> <span data-ttu-id="b6c4d-211">つまり、標準モジュール内の変数は、プロジェクト内の任意の場所から参照でき、プログラムが実行されている間は存在するため、実質的にはグローバル変数です。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-211">This means that variables in a standard module are effectively global variables because they are visible from anywhere in your project, and they exist for the life of the program.</span></span>

## <a name="reusing-classes-and-objects"></a><span data-ttu-id="b6c4d-212">クラスとオブジェクトの再利用</span><span class="sxs-lookup"><span data-stu-id="b6c4d-212">Reusing classes and objects</span></span>

<span data-ttu-id="b6c4d-213">オブジェクトを使用すると、変数とプロシージャを 1 度宣言した後、必要に応じていつでもそれらを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-213">Objects let you declare variables and procedures once and then reuse them whenever needed.</span></span> <span data-ttu-id="b6c4d-214">たとえば、スペル チェック機能をアプリケーションに追加する場合は、スペル チェック機能を提供するためのすべての変数とサポート機能を定義することができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-214">For example, if you want to add a spelling checker to an application you could define all the variables and support functions to provide spell-checking functionality.</span></span> <span data-ttu-id="b6c4d-215">スペル チェック機能をクラスとして作成した場合は、コンパイルされたアセンブリへの参照を追加することで、他のアプリケーションで再利用できます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-215">If you create your spelling checker as a class, you can then reuse it in other applications by adding a reference to the compiled assembly.</span></span> <span data-ttu-id="b6c4d-216">さらに、誰かが既に開発したスペル チェック機能のクラスを使用することで、作業の手間を省くことができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-216">Better yet, you may be able to save yourself some work by using a spelling checker class that someone else has already developed.</span></span>

<span data-ttu-id="b6c4d-217">.NET には、使用可能なコンポーネントの例が多数用意されています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-217">.NET provides many examples of components that are available for use.</span></span> <span data-ttu-id="b6c4d-218">次の例では、<xref:System> 名前空間に <xref:System.TimeZone> クラスが使用されています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-218">The following example uses the <xref:System.TimeZone> class in the <xref:System> namespace.</span></span> <span data-ttu-id="b6c4d-219"><xref:System.TimeZone> は、現在のコンピューター システムのタイム ゾーンに関する情報を取得できるメンバーを提供します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-219"><xref:System.TimeZone> provides members that allow you to retrieve information about the time zone of the current computer system.</span></span>

```vb
Public Sub ExamineTimeZone()
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone
    Dim s As String = "Current time zone is "
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "
    s &= "different from UTC (coordinated universal time)"
    s &= vbCrLf & "and is currently "
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "
    s &= "on ""summer time""."
    Console.WriteLine(s)
End Sub
```

<span data-ttu-id="b6c4d-220">上記の例では、最初の [Dim ステートメント](../../../language-reference/statements/dim-statement.md)が <xref:System.TimeZone> 型のオブジェクト変数を宣言し、<xref:System.TimeZone.CurrentTimeZone%2A> プロパティによって返された <xref:System.TimeZone> オブジェクトに割り当てています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-220">In the preceding example, the first [Dim Statement](../../../language-reference/statements/dim-statement.md) declares an object variable of type <xref:System.TimeZone> and assigns to it a <xref:System.TimeZone> object returned by the <xref:System.TimeZone.CurrentTimeZone%2A> property.</span></span>

## <a name="relationships-among-objects"></a><span data-ttu-id="b6c4d-221">オブジェクト間の関係</span><span class="sxs-lookup"><span data-stu-id="b6c4d-221">Relationships among objects</span></span>

<span data-ttu-id="b6c4d-222">オブジェクトは、いくつかの方法で相互に関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-222">Objects can be related to each other in several ways.</span></span> <span data-ttu-id="b6c4d-223">リレーションシップの主要な種類は、"*階層*" と "*含有*" です。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-223">The principal kinds of relationship are *hierarchical* and *containment*.</span></span>

### <a name="hierarchical-relationship"></a><span data-ttu-id="b6c4d-224">階層関係</span><span class="sxs-lookup"><span data-stu-id="b6c4d-224">Hierarchical relationship</span></span>

<span data-ttu-id="b6c4d-225">より基礎的なクラスから派生したクラスは、"*階層関係*" があると言います。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-225">When classes are derived from more fundamental classes, they are said to have a *hierarchical relationship*.</span></span> <span data-ttu-id="b6c4d-226">クラスの階層は、より一般的なクラスのサブタイプである項目を記述する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-226">Class hierarchies are useful when describing items that are a subtype of a more general class.</span></span>

<span data-ttu-id="b6c4d-227">次の例では、通常の <xref:System.Windows.Forms.Button> と同じように機能しますが、前景と背景の色を逆転させるメソッドも公開する、特殊な <xref:System.Windows.Forms.Button> を定義します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-227">In the following example, suppose you want to define a special kind of <xref:System.Windows.Forms.Button> that acts like a normal <xref:System.Windows.Forms.Button> but also exposes a method that reverses the foreground and background colors.</span></span>

#### <a name="define-a-class-that-is-derived-from-an-already-existing-class"></a><span data-ttu-id="b6c4d-228">既に存在するクラスから派生するクラスを定義する</span><span class="sxs-lookup"><span data-stu-id="b6c4d-228">Define a class that is derived from an already existing class</span></span>

1. <span data-ttu-id="b6c4d-229">[Class ステートメント](../../../language-reference/statements/class-statement.md)を使用して、必要なオブジェクトの作成元となるクラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-229">Use a [Class Statement](../../../language-reference/statements/class-statement.md) to define a class from which to create the object you need.</span></span>

   ```vb
   Public Class ReversibleButton
   ```

   <span data-ttu-id="b6c4d-230">クラスのコードの最後の行の後に、必ず `End Class` ステートメントを指定してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-230">Be sure an `End Class` statement follows the last line of code in your class.</span></span> <span data-ttu-id="b6c4d-231">統合開発環境 (IDE) では、既定により、`Class` ステートメントを入力すると、`End Class` が自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-231">By default, the integrated development environment (IDE) automatically generates an `End Class` when you enter a `Class` statement.</span></span>

2. <span data-ttu-id="b6c4d-232">`Class` ステートメントの直後に、[Inherits ステートメント](../../../language-reference/statements/inherits-statement.md)を記述します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-232">Follow the `Class` statement immediately with an [Inherits Statement](../../../language-reference/statements/inherits-statement.md).</span></span> <span data-ttu-id="b6c4d-233">新しいクラスの派生元クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-233">Specify the class from which your new class derives.</span></span>

   ```vb
   Inherits System.Windows.Forms.Button
   ```

   <span data-ttu-id="b6c4d-234">新しいクラスは、基本クラスによって定義されたすべてのメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-234">Your new class inherits all the members defined by the base class.</span></span>

3. <span data-ttu-id="b6c4d-235">派生クラスで公開される追加のメンバー用のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-235">Add the code for the additional members your derived class exposes.</span></span> <span data-ttu-id="b6c4d-236">たとえば、`ReverseColors` メソッドを追加すると、派生クラスは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-236">For example, you might add a `ReverseColors` method, and your derived class might look as follows:</span></span>

   ```vb
   Public Class ReversibleButton
       Inherits System.Windows.Forms.Button
           Public Sub ReverseColors()
               Dim saveColor As System.Drawing.Color = Me.BackColor
               Me.BackColor = Me.ForeColor
               Me.ForeColor = saveColor
          End Sub
   End Class
   ```

   <span data-ttu-id="b6c4d-237">`ReversibleButton` クラスからオブジェクトを作成すると、オブジェクトは、<xref:System.Windows.Forms.Button> クラスのすべてのメンバーだけでなく、`ReverseColors` メソッドと `ReversibleButton` に定義したその他の新しいメンバーにもアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-237">If you create an object from the `ReversibleButton` class, it can access all the members of the <xref:System.Windows.Forms.Button> class, as well as the `ReverseColors` method and any other new members you define in `ReversibleButton`.</span></span>

<span data-ttu-id="b6c4d-238">派生クラスは、派生元のクラスからメンバーを継承するため、クラス階層が深くなるにつれて、クラスをより複雑にすることができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-238">Derived classes inherit members from the class they are based on, allowing you to add complexity as you progress in a class hierarchy.</span></span> <span data-ttu-id="b6c4d-239">詳細については、「[継承の基本](inheritance-basics.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-239">For more information, see [Inheritance Basics](inheritance-basics.md).</span></span>

### <a name="compile-the-code"></a><span data-ttu-id="b6c4d-240">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b6c4d-240">Compile the code</span></span>

<span data-ttu-id="b6c4d-241">コンパイラが、新しいクラスの派生元となるクラスにアクセスできることを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-241">Be sure the compiler can access the class from which you intend to derive your new class.</span></span> <span data-ttu-id="b6c4d-242">これは、上記の例のように名前を完全に修飾するか、名前空間を [Imports ステートメント (.NET 名前空間と型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) で識別することを意味する場合があります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-242">This might mean fully qualifying its name, as in the preceding example, or identifying its namespace in an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="b6c4d-243">クラスが別のプロジェクト内にある場合は、そのプロジェクトへの参照の追加が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-243">If the class is in a different project, you might need to add a reference to that project.</span></span> <span data-ttu-id="b6c4d-244">詳細については、「[プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-244">For more information, see [Managing references in a project](/visualstudio/ide/managing-references-in-a-project).</span></span>

### <a name="containment-relationship"></a><span data-ttu-id="b6c4d-245">含有リレーションシップ</span><span class="sxs-lookup"><span data-stu-id="b6c4d-245">Containment relationship</span></span>

<span data-ttu-id="b6c4d-246">オブジェクトを関連付けることのできる別の方法は、"*含有関係*" にすることです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-246">Another way that objects can be related is a *containment relationship*.</span></span> <span data-ttu-id="b6c4d-247">コンテナー オブジェクトは、その他のオブジェクトを論理的にカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-247">Container objects logically encapsulate other objects.</span></span> <span data-ttu-id="b6c4d-248">たとえば、<xref:System.OperatingSystem> オブジェクトには、その <xref:System.OperatingSystem.Version%2A> プロパティによって返される <xref:System.Version> オブジェクトが論理的に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-248">For example, the <xref:System.OperatingSystem> object logically contains a <xref:System.Version> object, which it returns through its <xref:System.OperatingSystem.Version%2A> property.</span></span> <span data-ttu-id="b6c4d-249">コンテナー オブジェクトが物理的にその他のオブジェクトを含んでいるわけではないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-249">Note that the container object does not physically contain any other object.</span></span>

#### <a name="collections"></a><span data-ttu-id="b6c4d-250">コレクション</span><span class="sxs-lookup"><span data-stu-id="b6c4d-250">Collections</span></span>

<span data-ttu-id="b6c4d-251">特別な種類のオブジェクトの含有として、"*コレクション*" と表現されるものがあります。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-251">One particular type of object containment is represented by *collections*.</span></span> <span data-ttu-id="b6c4d-252">コレクションは、列挙することができる類似のオブジェクトの集まりです。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-252">Collections are groups of similar objects that can be enumerated.</span></span> <span data-ttu-id="b6c4d-253">Visual Basic では、[For Each...Next ステートメント](../../../language-reference/statements/for-each-next-statement.md) で特別な構文をサポートしています。これを使用して、コレクションの項目を反復処理することができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-253">Visual Basic supports a specific syntax in the [For Each...Next Statement](../../../language-reference/statements/for-each-next-statement.md) that allows you to iterate through the items of a collection.</span></span> <span data-ttu-id="b6c4d-254">さらに、多くの場合、コレクションでは、<xref:Microsoft.VisualBasic.Collection.Item%2A> を使用して、その要素を、インデックスまたは一意の文字列の関連付けによって取得することができます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-254">Additionally, collections often allow you to use an <xref:Microsoft.VisualBasic.Collection.Item%2A> to retrieve elements by their index or by associating them with a unique string.</span></span> <span data-ttu-id="b6c4d-255">コレクションは、インデックスなしで項目を削除または追加できるため、配列よりも簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-255">Collections can be easier to use than arrays because they allow you to add or remove items without using indexes.</span></span> <span data-ttu-id="b6c4d-256">簡単に使用できるため、多くの場合、コレクションは、フォームとコントロールを格納するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-256">Because of their ease of use, collections are often used to store forms and controls.</span></span>

## <a name="related-topics"></a><span data-ttu-id="b6c4d-257">関連トピック</span><span class="sxs-lookup"><span data-stu-id="b6c4d-257">Related topics</span></span>

<span data-ttu-id="b6c4d-258">[チュートリアル: クラスの定義](walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="b6c4d-258">[Walkthrough: Defining Classes](walkthrough-defining-classes.md)</span></span>\
<span data-ttu-id="b6c4d-259">クラスを作成する方法を手順を追って説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-259">Provides a step-by-step description of how to create a class.</span></span>

<span data-ttu-id="b6c4d-260">[オーバーロードされたプロパティとメソッド](overloaded-properties-and-methods.md)</span><span class="sxs-lookup"><span data-stu-id="b6c4d-260">[Overloaded Properties and Methods](overloaded-properties-and-methods.md)</span></span>\
<span data-ttu-id="b6c4d-261">オーバーロードされたプロパティとメソッド</span><span class="sxs-lookup"><span data-stu-id="b6c4d-261">Overloaded Properties and Methods</span></span>

<span data-ttu-id="b6c4d-262">[継承の基本](inheritance-basics.md)</span><span class="sxs-lookup"><span data-stu-id="b6c4d-262">[Inheritance Basics](inheritance-basics.md)</span></span>\
<span data-ttu-id="b6c4d-263">継承修飾子、メソッドとプロパティのオーバーライド、MyClass、および MyBase について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-263">Covers inheritance modifiers, overriding methods and properties, MyClass, and MyBase.</span></span>

<span data-ttu-id="b6c4d-264">[オブジェクトの有効期間: オブジェクトの作成と破棄](object-lifetime-how-objects-are-created-and-destroyed.md)</span><span class="sxs-lookup"><span data-stu-id="b6c4d-264">[Object Lifetime: How Objects Are Created and Destroyed](object-lifetime-how-objects-are-created-and-destroyed.md)</span></span>\
<span data-ttu-id="b6c4d-265">クラス インスタンスの作成と破棄について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-265">Discusses creating and disposing of class instances.</span></span>

<span data-ttu-id="b6c4d-266">[匿名型](anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="b6c4d-266">[Anonymous Types](anonymous-types.md)</span></span>\
<span data-ttu-id="b6c4d-267">匿名型を作成して使用する方法について説明します。匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-267">Describes how to create and use anonymous types, which allow you to create objects without writing a class definition for the data type.</span></span>

<span data-ttu-id="b6c4d-268">[オブジェクト初期化子: 名前付きの型と匿名型](object-initializers-named-and-anonymous-types.md)</span><span class="sxs-lookup"><span data-stu-id="b6c4d-268">[Object Initializers: Named and Anonymous Types](object-initializers-named-and-anonymous-types.md)</span></span>\
<span data-ttu-id="b6c4d-269">1 つの式で名前付きの型と匿名型のインスタンスを作成するために使用する、オブジェクト初期化子について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-269">Discusses object initializers, which are used to create instances of named and anonymous types by using a single expression.</span></span>

<span data-ttu-id="b6c4d-270">[方法: 匿名型の宣言におけるプロパティ名と型を推論する](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span><span class="sxs-lookup"><span data-stu-id="b6c4d-270">[How to: Infer Property Names and Types in Anonymous Type Declarations](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)</span></span>\
<span data-ttu-id="b6c4d-271">匿名型で宣言されたプロパティの名前と型を推論する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-271">Explains how to infer property names and types in anonymous type declarations.</span></span> <span data-ttu-id="b6c4d-272">推論の成功例と失敗例を示します。</span><span class="sxs-lookup"><span data-stu-id="b6c4d-272">Provides examples of successful and unsuccessful inference.</span></span>
