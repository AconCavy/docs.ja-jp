---
title: オブジェクト指向プログラミング (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 121d2e43f6896179756067e661be6d7960a1ee64
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73418043"
---
# <a name="object-oriented-programming-c"></a><span data-ttu-id="be340-102">オブジェクト指向プログラミング (C#)</span><span class="sxs-lookup"><span data-stu-id="be340-102">Object-Oriented Programming (C#)</span></span>

<span data-ttu-id="be340-103">C# は、カプセル化、継承、ポリモーフィズムなど、オブジェクト指向プログラミングを完全にサポートします。</span><span class="sxs-lookup"><span data-stu-id="be340-103">C# provides full support for object-oriented programming including encapsulation, inheritance, and polymorphism.</span></span>

<span data-ttu-id="be340-104">"*カプセル化*" とは、関連するプロパティ、メソッド、およびその他のメンバーのグループが 1 つの単位またはオブジェクトとして扱われることを意味します。</span><span class="sxs-lookup"><span data-stu-id="be340-104">*Encapsulation* means that a group of related properties, methods, and other members are treated as a single unit or object.</span></span>

<span data-ttu-id="be340-105">"*継承*" は、既存のクラスに基づいて新しいクラスを作成する機能です。</span><span class="sxs-lookup"><span data-stu-id="be340-105">*Inheritance* describes the ability to create new classes based on an existing class.</span></span>

<span data-ttu-id="be340-106">"*ポリモーフィズム*" とは、同じプロパティまたはメソッドを異なる方法で実装している複数のクラスを、交換して使用できることです。</span><span class="sxs-lookup"><span data-stu-id="be340-106">*Polymorphism* means that you can have multiple classes that can be used interchangeably, even though each class implements the same properties or methods in different ways.</span></span>

<span data-ttu-id="be340-107">このセクションでは、次の概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="be340-107">This section describes the following concepts:</span></span>

- [<span data-ttu-id="be340-108">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="be340-108">Classes and Objects</span></span>](#Classes)

  - [<span data-ttu-id="be340-109">クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="be340-109">Class Members</span></span>](#Members)

    - [<span data-ttu-id="be340-110">プロパティとフィールド</span><span class="sxs-lookup"><span data-stu-id="be340-110">Properties and Fields</span></span>](#Properties)

    - [<span data-ttu-id="be340-111">メソッド</span><span class="sxs-lookup"><span data-stu-id="be340-111">Methods</span></span>](#Methods)

    - [<span data-ttu-id="be340-112">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="be340-112">Constructors</span></span>](#Constructors)

    - [<span data-ttu-id="be340-113">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="be340-113">Finalizers</span></span>](#Finalizers)

    - [<span data-ttu-id="be340-114">イベント</span><span class="sxs-lookup"><span data-stu-id="be340-114">Events</span></span>](#Events)

    - [<span data-ttu-id="be340-115">入れ子になったクラス</span><span class="sxs-lookup"><span data-stu-id="be340-115">Nested Classes</span></span>](#NestedClasses)

  - [<span data-ttu-id="be340-116">アクセス修飾子とアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="be340-116">Access Modifiers and Access Levels</span></span>](#AccessModifiers)

  - [<span data-ttu-id="be340-117">クラスのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="be340-117">Instantiating Classes</span></span>](#InstantiatingClasses)

  - [<span data-ttu-id="be340-118">静的クラスとメンバー</span><span class="sxs-lookup"><span data-stu-id="be340-118">Static Classes and Members</span></span>](#Static)

  - [<span data-ttu-id="be340-119">匿名型</span><span class="sxs-lookup"><span data-stu-id="be340-119">Anonymous Types</span></span>](#AnonymousTypes)

- [<span data-ttu-id="be340-120">継承</span><span class="sxs-lookup"><span data-stu-id="be340-120">Inheritance</span></span>](#Inheritance)

  - [<span data-ttu-id="be340-121">メンバーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="be340-121">Overriding Members</span></span>](#Overriding)

- [<span data-ttu-id="be340-122">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be340-122">Interfaces</span></span>](#Interfaces)

- [<span data-ttu-id="be340-123">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="be340-123">Generics</span></span>](#Generics)

- [<span data-ttu-id="be340-124">デリゲート</span><span class="sxs-lookup"><span data-stu-id="be340-124">Delegates</span></span>](#Delegates)

## <a name="Classes"></a> <span data-ttu-id="be340-125">クラスとオブジェクト</span><span class="sxs-lookup"><span data-stu-id="be340-125">Classes and Objects</span></span>

<span data-ttu-id="be340-126">"*クラス*" という用語と "*オブジェクト*" という用語は同じ意味で使われる場合がありますが、実際には、クラスはオブジェクトの "*型*" を表すのに対し、オブジェクトはクラスの使用可能な "*インスタンス*" です。</span><span class="sxs-lookup"><span data-stu-id="be340-126">The terms *class* and *object* are sometimes used interchangeably, but in fact, classes describe the *type* of objects, while objects are usable *instances* of classes.</span></span> <span data-ttu-id="be340-127">そのため、オブジェクトを作成する操作は "*インスタンス化*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="be340-127">So, the act of creating an object is called *instantiation*.</span></span> <span data-ttu-id="be340-128">設計図との対比を使って説明すると、クラスは設計図であり、オブジェクトはその設計図を基にした建築物です。</span><span class="sxs-lookup"><span data-stu-id="be340-128">Using the blueprint analogy, a class is a blueprint, and an object is a building made from that blueprint.</span></span>

<span data-ttu-id="be340-129">クラスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-129">To define a class:</span></span>

```csharp
class SampleClass
{
}
```

<span data-ttu-id="be340-130">C# には、"*構造体*" と呼ばれる軽量バージョンのクラスも用意されています。構造体は、大きいオブジェクト配列を作成する必要があり、その配列に使用されるメモリの量を抑えたい場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="be340-130">C# also provides a light version of classes called *structures* that are useful when you need to create large array of objects and do not want to consume too much memory for that.</span></span>

<span data-ttu-id="be340-131">構造体を定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-131">To define a structure:</span></span>

```csharp
struct SampleStruct
{
}
```

<span data-ttu-id="be340-132">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-132">For more information, see:</span></span>

- [<span data-ttu-id="be340-133">class</span><span class="sxs-lookup"><span data-stu-id="be340-133">class</span></span>](../../language-reference/keywords/class.md)

- [<span data-ttu-id="be340-134">struct</span><span class="sxs-lookup"><span data-stu-id="be340-134">struct</span></span>](../../language-reference/keywords/struct.md)

### <a name="Members"></a> <span data-ttu-id="be340-135">クラス メンバー</span><span class="sxs-lookup"><span data-stu-id="be340-135">Class Members</span></span>

<span data-ttu-id="be340-136">各クラスには、さまざまな "*クラス メンバー*" を含めることができます。クラス メンバーには、クラスのデータを記述するプロパティ、クラスの動作を定義するメソッド、異なるクラスやオブジェクト間で通信するためのイベントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="be340-136">Each class can have different *class members* that include properties that describe class data, methods that define class behavior, and events that provide communication between different classes and objects.</span></span>

#### <a name="Properties"></a> <span data-ttu-id="be340-137">プロパティとフィールド</span><span class="sxs-lookup"><span data-stu-id="be340-137">Properties and Fields</span></span>

<span data-ttu-id="be340-138">フィールドとプロパティは、オブジェクトに格納されている情報を表します。</span><span class="sxs-lookup"><span data-stu-id="be340-138">Fields and properties represent information that an object contains.</span></span> <span data-ttu-id="be340-139">フィールドは、直接読み取ったり設定したりできるので変数と似ています。</span><span class="sxs-lookup"><span data-stu-id="be340-139">Fields are like variables because they can be read or set directly.</span></span>

<span data-ttu-id="be340-140">フィールドを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-140">To define a field:</span></span>

```csharp
class SampleClass
{
    public string sampleField;
}
```

<span data-ttu-id="be340-141">プロパティには get プロシージャと set プロシージャがあり、これらを使用することで値の設定方法や戻り値をより細かく制御できます。</span><span class="sxs-lookup"><span data-stu-id="be340-141">Properties have get and set procedures, which provide more control on how values are set or returned.</span></span>

<span data-ttu-id="be340-142">C# では、プロパティ値を格納するプライベート フィールドを作成するか、または自動実装プロパティと呼ばれる手法を使用できます。自動実装プロパティでは、値を格納するフィールドが背後で自動的に作成され、プロパティ プロシージャの基本的なロジックが提供されます。</span><span class="sxs-lookup"><span data-stu-id="be340-142">C# allows you either to create a private field for storing the property value or use so-called auto-implemented properties that create this field automatically behind the scenes and provide the basic logic for the property procedures.</span></span>

<span data-ttu-id="be340-143">自動実装プロパティを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-143">To define an auto-implemented property:</span></span>

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

<span data-ttu-id="be340-144">プロパティ値の読み取りと書き込みのために追加の操作を実行する必要がある場合は、プロパティ値を格納するフィールドを定義し、値を格納および取得する基本的なロジックを実装します。</span><span class="sxs-lookup"><span data-stu-id="be340-144">If you need to perform some additional operations for reading and writing the property value, define a field for storing the property value and provide the basic logic for storing and retrieving it:</span></span>

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

<span data-ttu-id="be340-145">ほとんどのプロパティには、プロパティ値の設定と取得を行うための両方のメソッドまたはプロシージャがあります。</span><span class="sxs-lookup"><span data-stu-id="be340-145">Most properties have methods or procedures to both set and get the property value.</span></span> <span data-ttu-id="be340-146">ただし、読み取り専用または書き込み専用のプロパティを作成して、プロパティの変更や読み取りを制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="be340-146">However, you can create read-only or write-only properties to restrict them from being modified or read.</span></span> <span data-ttu-id="be340-147">C# では、`get` プロパティ メソッドまたは `set` プロパティ メソッドを省略します。</span><span class="sxs-lookup"><span data-stu-id="be340-147">In C#, you can omit the `get` or `set` property method.</span></span> <span data-ttu-id="be340-148">ただし、自動実装プロパティを読み取り専用または書き込み専用にすることはできません。</span><span class="sxs-lookup"><span data-stu-id="be340-148">However, auto-implemented properties cannot be read-only or write-only.</span></span>

<span data-ttu-id="be340-149">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-149">For more information, see:</span></span>

- [<span data-ttu-id="be340-150">get</span><span class="sxs-lookup"><span data-stu-id="be340-150">get</span></span>](../../language-reference/keywords/get.md)

- [<span data-ttu-id="be340-151">set</span><span class="sxs-lookup"><span data-stu-id="be340-151">set</span></span>](../../language-reference/keywords/set.md)

#### <a name="Methods"></a> <span data-ttu-id="be340-152">メソッド</span><span class="sxs-lookup"><span data-stu-id="be340-152">Methods</span></span>

<span data-ttu-id="be340-153">"*メソッド*" は、オブジェクトが実行できる処理です。</span><span class="sxs-lookup"><span data-stu-id="be340-153">A *method* is an action that an object can perform.</span></span>

<span data-ttu-id="be340-154">クラスのメソッドを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-154">To define a method of a class:</span></span>

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

<span data-ttu-id="be340-155">クラスには、同じメソッドに対して、パラメーターの数やパラメーターの型が異なる複数の実装 ("*オーバーロード*") を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="be340-155">A class can have several implementations, or *overloads*, of the same method that differ in the number of parameters or parameter types.</span></span>

<span data-ttu-id="be340-156">メソッドをオーバーロードするコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-156">To overload a method:</span></span>

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

<span data-ttu-id="be340-157">ほとんどの場合、メソッドはクラス定義内で宣言します。</span><span class="sxs-lookup"><span data-stu-id="be340-157">In most cases you declare a method within a class definition.</span></span> <span data-ttu-id="be340-158">ただし、C# では、既存のクラスの実際の定義の外部にメソッドを追加できる "*拡張メソッド*" がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="be340-158">However, C# also supports *extension methods* that allow you to add methods to an existing class outside the actual definition of the class.</span></span>

<span data-ttu-id="be340-159">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-159">For more information, see:</span></span>

- [<span data-ttu-id="be340-160">メソッド</span><span class="sxs-lookup"><span data-stu-id="be340-160">Methods</span></span>](../classes-and-structs/methods.md)

- [<span data-ttu-id="be340-161">拡張メソッド</span><span class="sxs-lookup"><span data-stu-id="be340-161">Extension Methods</span></span>](../classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> <span data-ttu-id="be340-162">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="be340-162">Constructors</span></span>

<span data-ttu-id="be340-163">コンストラクターは、特定の型のオブジェクトを作成するときに自動的に実行されるクラス メソッドです。</span><span class="sxs-lookup"><span data-stu-id="be340-163">Constructors are class methods that are executed automatically when an object of a given type is created.</span></span> <span data-ttu-id="be340-164">コンストラクターは、通常、新しいオブジェクトのデータ メンバーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="be340-164">Constructors usually initialize the data members of the new object.</span></span> <span data-ttu-id="be340-165">コンストラクターは、クラスの作成時に 1 回だけ実行できます。</span><span class="sxs-lookup"><span data-stu-id="be340-165">A constructor can run only once when a class is created.</span></span> <span data-ttu-id="be340-166">また、コンストラクター内のコードは常に、クラス内の他のすべてのコードより先に実行されます。</span><span class="sxs-lookup"><span data-stu-id="be340-166">Furthermore, the code in the constructor always runs before any other code in a class.</span></span> <span data-ttu-id="be340-167">他のメソッドと同じように、コンストラクターにも複数のオーバーロードを作成できます。</span><span class="sxs-lookup"><span data-stu-id="be340-167">However, you can create multiple constructor overloads in the same way as for any other method.</span></span>

<span data-ttu-id="be340-168">クラスのコンストラクターを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-168">To define a constructor for a class:</span></span>

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

<span data-ttu-id="be340-169">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-169">For more information, see:</span></span>

<span data-ttu-id="be340-170">「[コンストラクター](../classes-and-structs/constructors.md)」。</span><span class="sxs-lookup"><span data-stu-id="be340-170">[Constructors](../classes-and-structs/constructors.md).</span></span>

#### <a name="Finalizers"></a> <span data-ttu-id="be340-171">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="be340-171">Finalizers</span></span>

<span data-ttu-id="be340-172">ファイナライザーは、クラスのインスタンスを破棄するために使います。</span><span class="sxs-lookup"><span data-stu-id="be340-172">Finalizers are used to destruct instances of classes.</span></span> <span data-ttu-id="be340-173">.NET Framework では、アプリケーション内のマネージド オブジェクトのメモリの割り当てと解放は、ガベージ コレクターによって自動的に管理されます。</span><span class="sxs-lookup"><span data-stu-id="be340-173">In the .NET Framework, the garbage collector automatically manages the allocation and release of memory for the managed objects in your application.</span></span> <span data-ttu-id="be340-174">ただし、アプリケーションで作成されるアンマネージ リソースを適切にクリーンアップするために、ファイナライザーも必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="be340-174">However, you may still need finalizers to clean up any unmanaged resources that your application creates.</span></span> <span data-ttu-id="be340-175">1 つのクラスに定義できるファイナライザーは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="be340-175">There can be only one finalizers for a class.</span></span>

<span data-ttu-id="be340-176">.NET Framework のファイナライザーおよびガベージ コレクションについて詳しくは、「[ガベージ コレクション](../../../standard/garbage-collection/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="be340-176">For more information about finalizers and garbage collection in the .NET Framework, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>

#### <a name="Events"></a> <span data-ttu-id="be340-177">イベント</span><span class="sxs-lookup"><span data-stu-id="be340-177">Events</span></span>

<span data-ttu-id="be340-178">クラスやオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。</span><span class="sxs-lookup"><span data-stu-id="be340-178">Events enable a class or object to notify other classes or objects when something of interest occurs.</span></span> <span data-ttu-id="be340-179">イベントを送信する (発生させる) クラスは "*パブリッシャー*" と呼ばれ、イベントを受信する (処理する) クラスは "*サブスクライバー*" と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="be340-179">The class that sends (or raises) the event is called the *publisher* and the classes that receive (or handle) the event are called *subscribers*.</span></span> <span data-ttu-id="be340-180">イベント、およびイベントの発生と処理の詳細については、「[イベント](../../../standard/events/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="be340-180">For more information about events, how they are raised and handled, see [Events](../../../standard/events/index.md).</span></span>

- <span data-ttu-id="be340-181">クラスでイベントを宣言するには、[event](../../language-reference/keywords/event.md) キーワードを使います。</span><span class="sxs-lookup"><span data-stu-id="be340-181">To declare an event in a class, use the [event](../../language-reference/keywords/event.md) keyword.</span></span>

- <span data-ttu-id="be340-182">イベントを発生させるには、イベント デリゲートを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="be340-182">To raise an event, invoke the event delegate.</span></span>

- <span data-ttu-id="be340-183">イベントをサブスクライブするには、`+=` 演算子を使用します。イベント サブスクリプションを解除するには、`-=` 演算子を使用します。</span><span class="sxs-lookup"><span data-stu-id="be340-183">To subscribe to an event, use the `+=` operator; to unsubscribe from an event, use the `-=` operator.</span></span>

#### <a name="NestedClasses"></a> <span data-ttu-id="be340-184">入れ子になったクラス</span><span class="sxs-lookup"><span data-stu-id="be340-184">Nested Classes</span></span>

<span data-ttu-id="be340-185">別のクラス内で定義されているクラスを "*入れ子になったクラス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="be340-185">A class defined within another class is called *nested*.</span></span> <span data-ttu-id="be340-186">既定では、入れ子になったクラスはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="be340-186">By default, the nested class is private.</span></span>

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

<span data-ttu-id="be340-187">入れ子になったクラスのインスタンスを作成するには、コンテナー クラスの名前に続けて、ドットと入れ子になったクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="be340-187">To create an instance of the nested class, use the name of the container class followed by the dot and then followed by the name of the nested class:</span></span>

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a> <span data-ttu-id="be340-188">アクセス修飾子とアクセス レベル</span><span class="sxs-lookup"><span data-stu-id="be340-188">Access Modifiers and Access Levels</span></span>

<span data-ttu-id="be340-189">すべてのクラスおよびクラス メンバーでは、"*アクセス修飾子*" を使って、他のクラスに提供するアクセス レベルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="be340-189">All classes and class members can specify what access level they provide to other classes by using *access modifiers*.</span></span>

<span data-ttu-id="be340-190">次のアクセス修飾子を使用できます。</span><span class="sxs-lookup"><span data-stu-id="be340-190">The following access modifiers are available:</span></span>

|<span data-ttu-id="be340-191">C# の修飾子</span><span class="sxs-lookup"><span data-stu-id="be340-191">C# Modifier</span></span>|<span data-ttu-id="be340-192">定義</span><span class="sxs-lookup"><span data-stu-id="be340-192">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="be340-193">public</span><span class="sxs-lookup"><span data-stu-id="be340-193">public</span></span>](../../language-reference/keywords/public.md)|<span data-ttu-id="be340-194">この型またはメンバーには、同じアセンブリ内の他のコードや、そのアセンブリを参照する別のアセンブリ内の任意のコードからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="be340-194">The type or member can be accessed by any other code in the same assembly or another assembly that references it.</span></span>|
|[<span data-ttu-id="be340-195">private</span><span class="sxs-lookup"><span data-stu-id="be340-195">private</span></span>](../../language-reference/keywords/private.md)|<span data-ttu-id="be340-196">この型またはメンバーには、同じクラスのコードのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="be340-196">The type or member can only be accessed by code in the same class.</span></span>|
|[<span data-ttu-id="be340-197">protected</span><span class="sxs-lookup"><span data-stu-id="be340-197">protected</span></span>](../../language-reference/keywords/protected.md)|<span data-ttu-id="be340-198">この型またはメンバーには、同じクラスまたは派生クラスのコードのみがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="be340-198">The type or member can only be accessed by code in the same class or in a derived class.</span></span>|
|[<span data-ttu-id="be340-199">internal</span><span class="sxs-lookup"><span data-stu-id="be340-199">internal</span></span>](../../language-reference/keywords/internal.md)|<span data-ttu-id="be340-200">この型またはメンバーには、同じアセンブリ内の任意のコードからアクセスできますが、別のアセンブリからはアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="be340-200">The type or member can be accessed by any code in the same assembly, but not from another assembly.</span></span>|
|[<span data-ttu-id="be340-201">protected internal</span><span class="sxs-lookup"><span data-stu-id="be340-201">protected internal</span></span>](../../language-reference/keywords/protected-internal.md)|<span data-ttu-id="be340-202">この型またはメンバーには、同じアセンブリ内の任意のコード、または別のアセンブリ内の任意の派生クラスからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="be340-202">The type or member can be accessed by any code in the same assembly, or by any derived class in another assembly.</span></span>|
|[<span data-ttu-id="be340-203">private protected</span><span class="sxs-lookup"><span data-stu-id="be340-203">private protected</span></span>](../../language-reference/keywords/private-protected.md)|<span data-ttu-id="be340-204">この型またはメンバーには、基底クラス アセンブリ内の同じクラスまたは派生クラスのコードがアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="be340-204">The type or member can be accessed by code in the same class or in a derived class within the base class assembly.</span></span>|

<span data-ttu-id="be340-205">詳細については、「[アクセス修飾子](../classes-and-structs/access-modifiers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="be340-205">For more information, see [Access Modifiers](../classes-and-structs/access-modifiers.md).</span></span>

### <a name="InstantiatingClasses"></a> <span data-ttu-id="be340-206">クラスのインスタンス化</span><span class="sxs-lookup"><span data-stu-id="be340-206">Instantiating Classes</span></span>

<span data-ttu-id="be340-207">オブジェクトを作成するには、クラスをインスタンス化する (クラスのインスタンスを作成する) 必要があります。</span><span class="sxs-lookup"><span data-stu-id="be340-207">To create an object, you need to instantiate a class, or create a class instance.</span></span>

```csharp
SampleClass sampleObject = new SampleClass();
```

<span data-ttu-id="be340-208">クラスをインスタンス化した後は、インスタンスのプロパティやフィールドに値を割り当てたり、クラスのメソッドを呼び出したりできます。</span><span class="sxs-lookup"><span data-stu-id="be340-208">After instantiating a class, you can assign values to the instance's properties and fields and invoke class methods.</span></span>

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

<span data-ttu-id="be340-209">クラスのインスタンス化のプロセスでプロパティに値を割り当てるには、オブジェクト初期化子を使用します。</span><span class="sxs-lookup"><span data-stu-id="be340-209">To assign values to properties during the class instantiation process, use object initializers:</span></span>

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="be340-210">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-210">For more information, see:</span></span>

- [<span data-ttu-id="be340-211">new 演算子</span><span class="sxs-lookup"><span data-stu-id="be340-211">new Operator</span></span>](../../language-reference/operators/new-operator.md)

- [<span data-ttu-id="be340-212">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="be340-212">Object and Collection Initializers</span></span>](../classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a> <span data-ttu-id="be340-213">静的クラスとメンバー</span><span class="sxs-lookup"><span data-stu-id="be340-213">Static Classes and Members</span></span>

<span data-ttu-id="be340-214">クラスの静的メンバーは、クラスのすべてのインスタンスで共有されるプロパティ、プロシージャ、またはフィールドです。</span><span class="sxs-lookup"><span data-stu-id="be340-214">A static member of the class is a property, procedure, or field that is shared by all instances of a class.</span></span>

<span data-ttu-id="be340-215">静的メンバーを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-215">To define a static member:</span></span>

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

<span data-ttu-id="be340-216">静的メンバーにアクセスするには、クラスのオブジェクトを作成せずにクラスの名前を使います。</span><span class="sxs-lookup"><span data-stu-id="be340-216">To access the static member, use the name of the class without creating an object of this class:</span></span>

```csharp
Console.WriteLine(SampleClass.SampleString);
```

<span data-ttu-id="be340-217">C# の静的クラスには静的メンバーだけがあり、インスタンス化することはできません。</span><span class="sxs-lookup"><span data-stu-id="be340-217">Static  classes in C# have static members only and cannot be instantiated.</span></span> <span data-ttu-id="be340-218">また、静的メンバーから、非静的のプロパティ、フィールド、またはメソッドにアクセスすることもできません。</span><span class="sxs-lookup"><span data-stu-id="be340-218">Static members also cannot access non-static  properties, fields or methods</span></span>

<span data-ttu-id="be340-219">詳しくは、「[static](../../language-reference/keywords/static.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="be340-219">For more information, see: [static](../../language-reference/keywords/static.md).</span></span>

### <a name="AnonymousTypes"></a> <span data-ttu-id="be340-220">匿名型</span><span class="sxs-lookup"><span data-stu-id="be340-220">Anonymous Types</span></span>

<span data-ttu-id="be340-221">匿名型を使用すると、データ型のクラス定義を記述せずにオブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="be340-221">Anonymous types enable you to create objects without writing a class definition for the data type.</span></span> <span data-ttu-id="be340-222">クラスは、コンパイラによって生成されます。</span><span class="sxs-lookup"><span data-stu-id="be340-222">Instead, the compiler generates a class for you.</span></span> <span data-ttu-id="be340-223">このクラスには使用可能な名前がなく、オブジェクトの宣言時に指定したプロパティが格納されます。</span><span class="sxs-lookup"><span data-stu-id="be340-223">The class has no usable name and contains the properties you specify in declaring the object.</span></span>

<span data-ttu-id="be340-224">匿名型のインスタンスを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-224">To create an instance of an anonymous type:</span></span>

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

<span data-ttu-id="be340-225">詳細については次を参照してください:[匿名型](../classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="be340-225">For more information, see: [Anonymous Types](../classes-and-structs/anonymous-types.md).</span></span>

## <a name="Inheritance"></a> <span data-ttu-id="be340-226">継承</span><span class="sxs-lookup"><span data-stu-id="be340-226">Inheritance</span></span>

<span data-ttu-id="be340-227">継承を使用すると、他のクラスで定義されている動作を再利用、拡張、および変更する新しいクラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="be340-227">Inheritance enables you to create a new class that reuses, extends, and modifies the behavior that is defined in another class.</span></span> <span data-ttu-id="be340-228">メンバーが継承される側のクラスを "*基底クラス*" と呼び、メンバーを継承する側のクラスを "*派生クラス*" と呼びます。</span><span class="sxs-lookup"><span data-stu-id="be340-228">The class whose members are inherited is called the *base class*, and the class that inherits those members is called the *derived class*.</span></span> <span data-ttu-id="be340-229">ただし、C# のすべてのクラスは、.NET のクラス階層構造をサポートしてすべてのクラスに下位レベルのサービスを提供する <xref:System.Object> クラスを暗黙的に継承します。</span><span class="sxs-lookup"><span data-stu-id="be340-229">However, all classes in C# implicitly inherit from the <xref:System.Object> class that supports .NET class hierarchy and provides low-level services to all classes.</span></span>

> [!NOTE]
> <span data-ttu-id="be340-230">C# は多重継承をサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="be340-230">C# doesn't support multiple inheritance.</span></span> <span data-ttu-id="be340-231">つまり、派生クラスに対して指定できる基底クラスは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="be340-231">That is, you can specify only one base class for a derived class.</span></span>

<span data-ttu-id="be340-232">基底クラスを継承するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-232">To inherit from a base class:</span></span>

```csharp
class DerivedClass:BaseClass {}
```

<span data-ttu-id="be340-233">既定では、すべてのクラスが継承可能になります。</span><span class="sxs-lookup"><span data-stu-id="be340-233">By default all classes can be inherited.</span></span> <span data-ttu-id="be340-234">ただし、クラスを基底クラスとして使用できないように指定したり、基底クラスとしてのみ使用できるクラスを作成したりできます。</span><span class="sxs-lookup"><span data-stu-id="be340-234">However, you can specify whether a class must not be used as a base class, or create a class that can be used as a base class only.</span></span>

<span data-ttu-id="be340-235">クラスを基底クラスとして使用できないように指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-235">To specify that a class cannot be used as a base class:</span></span>

```csharp
public sealed class A { }
```

<span data-ttu-id="be340-236">クラスが基底クラスとしてのみ使用され、インスタンス化できないように指定する方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-236">To specify that a class can be used as a base class only and cannot be instantiated:</span></span>

```csharp
public abstract class B { }
```

<span data-ttu-id="be340-237">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-237">For more information, see:</span></span>

- [<span data-ttu-id="be340-238">sealed</span><span class="sxs-lookup"><span data-stu-id="be340-238">sealed</span></span>](../../language-reference/keywords/sealed.md)

- [<span data-ttu-id="be340-239">abstract</span><span class="sxs-lookup"><span data-stu-id="be340-239">abstract</span></span>](../../language-reference/keywords/abstract.md)

### <a name="Overriding"></a> <span data-ttu-id="be340-240">メンバーのオーバーライド</span><span class="sxs-lookup"><span data-stu-id="be340-240">Overriding Members</span></span>

<span data-ttu-id="be340-241">既定では、派生クラスは基底クラスのすべてのメンバーを継承します。</span><span class="sxs-lookup"><span data-stu-id="be340-241">By default, a derived class inherits all members from its base class.</span></span> <span data-ttu-id="be340-242">継承したメンバーの動作を変更する場合は、そのメンバーをオーバーライドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="be340-242">If you want to change the behavior of the inherited member, you need to override it.</span></span> <span data-ttu-id="be340-243">つまり、派生クラスに、メソッド、プロパティ、またはイベントの新しい実装を定義できます。</span><span class="sxs-lookup"><span data-stu-id="be340-243">That is, you can define a new implementation of the method, property or event in the derived class.</span></span>

<span data-ttu-id="be340-244">プロパティやメソッドのオーバーライド方法を制御するには、次の修飾子を使用します。</span><span class="sxs-lookup"><span data-stu-id="be340-244">The following modifiers are used to control how properties and methods are overridden:</span></span>

|<span data-ttu-id="be340-245">C# の修飾子</span><span class="sxs-lookup"><span data-stu-id="be340-245">C# Modifier</span></span>|<span data-ttu-id="be340-246">定義</span><span class="sxs-lookup"><span data-stu-id="be340-246">Definition</span></span>|
|------------------|----------------|
|[<span data-ttu-id="be340-247">virtual</span><span class="sxs-lookup"><span data-stu-id="be340-247">virtual</span></span>](../../language-reference/keywords/virtual.md)|<span data-ttu-id="be340-248">派生クラスでのクラス メンバーのオーバーライドを許可します。</span><span class="sxs-lookup"><span data-stu-id="be340-248">Allows a class member to be overridden in a derived class.</span></span>|
|[<span data-ttu-id="be340-249">override</span><span class="sxs-lookup"><span data-stu-id="be340-249">override</span></span>](../../language-reference/keywords/override.md)|<span data-ttu-id="be340-250">基底クラスで定義されている仮想メンバー (オーバーライドできるメンバー) をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="be340-250">Overrides a virtual (overridable) member defined in the base class.</span></span>|
|[<span data-ttu-id="be340-251">abstract</span><span class="sxs-lookup"><span data-stu-id="be340-251">abstract</span></span>](../../language-reference/keywords/abstract.md)|<span data-ttu-id="be340-252">派生クラスでのクラス メンバーのオーバーライドを必須にします。</span><span class="sxs-lookup"><span data-stu-id="be340-252">Requires that a class member to be overridden in the derived class.</span></span>|
|[<span data-ttu-id="be340-253">new 修飾子</span><span class="sxs-lookup"><span data-stu-id="be340-253">new Modifier</span></span>](../../language-reference/keywords/new-modifier.md)|<span data-ttu-id="be340-254">基底クラスから継承されたメンバーを隠ぺいします。</span><span class="sxs-lookup"><span data-stu-id="be340-254">Hides a member inherited from a base class</span></span>|

## <a name="Interfaces"></a> <span data-ttu-id="be340-255">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be340-255">Interfaces</span></span>

<span data-ttu-id="be340-256">インターフェイスは、クラスと同様にプロパティ、メソッド、およびイベントのセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="be340-256">Interfaces, like classes, define a set of properties, methods, and events.</span></span> <span data-ttu-id="be340-257">ただし、クラスとは異なり、インターフェイスは実装を提供しません。</span><span class="sxs-lookup"><span data-stu-id="be340-257">But unlike classes, interfaces do not provide implementation.</span></span> <span data-ttu-id="be340-258">インターフェイスはクラスによって実装され、クラスとは別のエンティティとして定義されます。</span><span class="sxs-lookup"><span data-stu-id="be340-258">They are implemented by classes, and defined as separate entities from classes.</span></span> <span data-ttu-id="be340-259">インターフェイスを実装するクラスは、そのインターフェイスのあらゆる機能を定義に従って厳密に実装する必要があります。この点で、インターフェイスはコントラクトを表しています。</span><span class="sxs-lookup"><span data-stu-id="be340-259">An interface represents a contract, in that a class that implements an interface must implement every aspect of that interface exactly as it is defined.</span></span>

<span data-ttu-id="be340-260">インターフェイスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-260">To define an interface:</span></span>

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

<span data-ttu-id="be340-261">クラスにインターフェイスを実装するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-261">To implement an interface in a class:</span></span>

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

<span data-ttu-id="be340-262">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-262">For more information, see:</span></span>

[<span data-ttu-id="be340-263">インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be340-263">Interfaces</span></span>](../interfaces/index.md)

[<span data-ttu-id="be340-264">interface</span><span class="sxs-lookup"><span data-stu-id="be340-264">interface</span></span>](../../language-reference/keywords/interface.md)

## <a name="Generics"></a> <span data-ttu-id="be340-265">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="be340-265">Generics</span></span>

<span data-ttu-id="be340-266">.NET Framework のクラス、構造体、インターフェイス、およびメソッドは、格納または使用できるオブジェクトの型を定義する "*型パラメーター*" を含むことができます。</span><span class="sxs-lookup"><span data-stu-id="be340-266">Classes, structures, interfaces and methods in the .NET Framework can include *type parameters* that define types of objects that they can store or use.</span></span> <span data-ttu-id="be340-267">ジェネリックの最も一般的な例として、コレクションがあります。コレクションには、その中に格納されるオブジェクトの型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="be340-267">The most common example of generics is a collection, where you can specify the type of objects to be stored in a collection.</span></span>

<span data-ttu-id="be340-268">ジェネリック クラスを定義するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-268">To define a generic class:</span></span>

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

<span data-ttu-id="be340-269">ジェネリック クラスのインスタンスを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-269">To create an instance of a generic class:</span></span>

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

<span data-ttu-id="be340-270">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-270">For more information, see:</span></span>

- [<span data-ttu-id="be340-271">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="be340-271">Generics</span></span>](../../../standard/generics/index.md)

- [<span data-ttu-id="be340-272">ジェネリック</span><span class="sxs-lookup"><span data-stu-id="be340-272">Generics</span></span>](../generics/index.md)

## <a name="Delegates"></a> <span data-ttu-id="be340-273">デリゲート</span><span class="sxs-lookup"><span data-stu-id="be340-273">Delegates</span></span>

<span data-ttu-id="be340-274">"*デリゲート*" は、メソッド シグネチャを定義する型であり、互換性のあるシグネチャを持つ任意のメソッドへの参照を提供できます。</span><span class="sxs-lookup"><span data-stu-id="be340-274">A *delegate* is a type that defines a method signature, and can provide a reference to any method with a compatible signature.</span></span> <span data-ttu-id="be340-275">メソッドは、デリゲートを使用して起動する (呼び出す) ことができます。</span><span class="sxs-lookup"><span data-stu-id="be340-275">You can invoke (or call) the method through the delegate.</span></span> <span data-ttu-id="be340-276">デリゲートは、他のメソッドへの引数としてメソッドを渡すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="be340-276">Delegates are used to pass methods as arguments to other methods.</span></span>

> [!NOTE]
> <span data-ttu-id="be340-277">イベント ハンドラーは、デリゲートを介して呼び出されるメソッドにすぎません。</span><span class="sxs-lookup"><span data-stu-id="be340-277">Event handlers are nothing more than methods that are invoked through delegates.</span></span> <span data-ttu-id="be340-278">デリゲートを使用したイベント処理について詳しくは、「[イベント](../../../standard/events/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="be340-278">For more information about using delegates in event handling, see [Events](../../../standard/events/index.md).</span></span>

<span data-ttu-id="be340-279">デリゲートを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-279">To create a delegate:</span></span>

```csharp
public delegate void SampleDelegate(string str);
```

<span data-ttu-id="be340-280">デリゲートで指定されたシグネチャに一致するメソッドへの参照を作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="be340-280">To create a reference to a method that matches the signature specified by the delegate:</span></span>

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
    {
        // Add code here.
    }
    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

<span data-ttu-id="be340-281">詳細については次を参照してください:</span><span class="sxs-lookup"><span data-stu-id="be340-281">For more information, see:</span></span>

- [<span data-ttu-id="be340-282">デリゲート</span><span class="sxs-lookup"><span data-stu-id="be340-282">Delegates</span></span>](../delegates/index.md)

- [<span data-ttu-id="be340-283">delegate</span><span class="sxs-lookup"><span data-stu-id="be340-283">delegate</span></span>](../../language-reference/builtin-types/reference-types.md)

## <a name="see-also"></a><span data-ttu-id="be340-284">関連項目</span><span class="sxs-lookup"><span data-stu-id="be340-284">See also</span></span>

- [<span data-ttu-id="be340-285">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="be340-285">C# Programming Guide</span></span>](../index.md)
