---
title: 'チュートリアル: 属性を使用する - C#'
description: C# での属性の機能について説明します。
author: mgroves
ms.technology: csharp-fundamentals
ms.date: 03/06/2017
ms.assetid: b152cf36-76e4-43a5-b805-1a1952e53b79
ms.openlocfilehash: 24cb7d35a89fda78511dc4ba725b69c5d601a008
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937470"
---
# <a name="use-attributes-in-c"></a><span data-ttu-id="968b0-103">C\# で属性を使用する</span><span class="sxs-lookup"><span data-stu-id="968b0-103">Use Attributes in C\#</span></span>

<span data-ttu-id="968b0-104">属性は、情報をコードに宣言的に関連付けるための手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="968b0-104">Attributes provide a way of associating information with code in a declarative way.</span></span> <span data-ttu-id="968b0-105">また、さまざまなターゲットに適用できる再利用可能な要素も提供します。</span><span class="sxs-lookup"><span data-stu-id="968b0-105">They can also provide a reusable element that can be applied to a variety of targets.</span></span>

<span data-ttu-id="968b0-106">たとえば `[Obsolete]` 属性について考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="968b0-106">Consider the `[Obsolete]` attribute.</span></span> <span data-ttu-id="968b0-107">この属性はクラス、構造体、メソッド、コンストラクトなどに適用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-107">It can be applied to classes, structs, methods, constructors, and more.</span></span> <span data-ttu-id="968b0-108">これは、その要素が古いことを "_宣言_" します。</span><span class="sxs-lookup"><span data-stu-id="968b0-108">It _declares_ that the element is obsolete.</span></span> <span data-ttu-id="968b0-109">この属性を検索して、対応する何らかのアクションを実行するのは、C# コンパイラの役目です。</span><span class="sxs-lookup"><span data-stu-id="968b0-109">It's then up to the C# compiler to look for this attribute, and do some action in response.</span></span>

<span data-ttu-id="968b0-110">このチュートリアルでは、コードに属性を追加する方法、独自の属性を作成して使用する方法、.NET Core に組み込まれているいくつかの属性を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="968b0-110">In this tutorial, you'll be introduced to how to add attributes to your code, how to create and use your own attributes, and how to use some attributes that are built into .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="968b0-111">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="968b0-111">Prerequisites</span></span>
<span data-ttu-id="968b0-112">お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968b0-112">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="968b0-113">インストールの手順については、[.NET Core のダウンロード](https://dotnet.microsoft.com/download) ページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="968b0-113">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span>
<span data-ttu-id="968b0-114">このアプリケーションは、Windows、Ubuntu Linux、macOS または Docker コンテナーで実行できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-114">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="968b0-115">お好みのコード エディターをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="968b0-115">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="968b0-116">次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="968b0-116">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="968b0-117">しかし、他の使い慣れたツールを使用しても構いません。</span><span class="sxs-lookup"><span data-stu-id="968b0-117">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="968b0-118">アプリケーションを作成する</span><span class="sxs-lookup"><span data-stu-id="968b0-118">Create the Application</span></span>

<span data-ttu-id="968b0-119">すべてのツールをインストールしたら、新しい .NET Core アプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="968b0-119">Now that you've installed all the tools, create a new .NET Core application.</span></span> <span data-ttu-id="968b0-120">コマンド ライン ジェネレーターを使用するには、お使いのシェルで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="968b0-120">To use the command line generator, execute the following command in your favorite shell:</span></span>

`dotnet new console`

<span data-ttu-id="968b0-121">このコマンドにより、必要最小限の .NET Core プロジェクト ファイルが作成されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-121">This command will create bare-bones .NET core project files.</span></span> <span data-ttu-id="968b0-122">`dotnet restore` を実行して、このプロジェクトのコンパイルに必要な依存関係を復元する必要があります。</span><span class="sxs-lookup"><span data-stu-id="968b0-122">You will need to execute `dotnet restore` to restore the dependencies needed to compile this project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="968b0-123">プログラムを実行するには `dotnet run` を使用します。</span><span class="sxs-lookup"><span data-stu-id="968b0-123">To execute the program, use `dotnet run`.</span></span> <span data-ttu-id="968b0-124">コンソールに "Hello, World" という出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-124">You should see "Hello, World" output to the console.</span></span>

## <a name="how-to-add-attributes-to-code"></a><span data-ttu-id="968b0-125">コードに属性を追加する方法</span><span class="sxs-lookup"><span data-stu-id="968b0-125">How to add attributes to code</span></span>

<span data-ttu-id="968b0-126">C# では、属性は `Attribute` 基底クラスを継承するクラスです。</span><span class="sxs-lookup"><span data-stu-id="968b0-126">In C#, attributes are classes that inherit from the `Attribute` base class.</span></span> <span data-ttu-id="968b0-127">`Attribute` クラスから継承したクラスは、コードの他の部分で一種の "タグ" として使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-127">Any class that inherits from `Attribute` can be used as a sort of "tag" on other pieces of code.</span></span>
<span data-ttu-id="968b0-128">たとえば `ObsoleteAttribute` という名前の属性があります。</span><span class="sxs-lookup"><span data-stu-id="968b0-128">For instance, there is an attribute called `ObsoleteAttribute`.</span></span> <span data-ttu-id="968b0-129">これは、そのコードが古いので現在は使用できないことを警告するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-129">This is used to signal that code is obsolete and shouldn't be used anymore.</span></span> <span data-ttu-id="968b0-130">この属性を、角かっこを使用して、たとえばクラスに適用することができます。</span><span class="sxs-lookup"><span data-stu-id="968b0-130">You can place this attribute on a class, for instance, by using square brackets.</span></span>

[!code-csharp[Obsolete attribute example](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample1)]

<span data-ttu-id="968b0-131">この属性の名前は `ObsoleteAttribute` ですが、コードでは `[Obsolete]` と記述するだけで使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-131">Note that while the class is called `ObsoleteAttribute`, it's only necessary to use `[Obsolete]` in the code.</span></span> <span data-ttu-id="968b0-132">これは C# が準拠している規則によります。</span><span class="sxs-lookup"><span data-stu-id="968b0-132">This is a convention that C# follows.</span></span>
<span data-ttu-id="968b0-133">完全な名前 `[ObsoleteAttribute]` も使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-133">You can use the full name `[ObsoleteAttribute]` if you choose.</span></span>

<span data-ttu-id="968b0-134">クラスを現在使用されていないとマークするときは、その "*理由*" と、代わりに "*何を*" 使用べきかについての情報を提供することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="968b0-134">When marking a class obsolete, it's a good idea to provide some information as to *why* it's obsolete, and/or *what* to use instead.</span></span> <span data-ttu-id="968b0-135">これは、Obsolete 属性に文字列パラメーターを渡すことで行います。</span><span class="sxs-lookup"><span data-stu-id="968b0-135">Do this by passing a string parameter to the Obsolete attribute.</span></span>

[!code-csharp[Obsolete attribute example with parameters](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ObsoleteExample2)]

<span data-ttu-id="968b0-136">この文字列は、`var attr = new ObsoleteAttribute("some string")` と記述した場合と同様に、`ObsoleteAttribute` コンストラクターに引数として渡されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-136">The string is being passed as an argument to an `ObsoleteAttribute` constructor, just as if you were writing `var attr = new ObsoleteAttribute("some string")`.</span></span>

<span data-ttu-id="968b0-137">属性コンストラクターに渡すパラメーターは、単純な型/リテラル (`bool, int, double, string, Type, enums, etc`) とそれらの配列のみに限られます。</span><span class="sxs-lookup"><span data-stu-id="968b0-137">Parameters to an attribute constructor are limited to simple types/literals: `bool, int, double, string, Type, enums, etc` and arrays of those types.</span></span>
<span data-ttu-id="968b0-138">式または変数は使用できません。</span><span class="sxs-lookup"><span data-stu-id="968b0-138">You can not use an expression or a variable.</span></span> <span data-ttu-id="968b0-139">位置指定パラメーターや名前付きパラメーターは自由に使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-139">You are free to use positional or named parameters.</span></span>

## <a name="how-to-create-your-own-attribute"></a><span data-ttu-id="968b0-140">独自の属性を作成する方法</span><span class="sxs-lookup"><span data-stu-id="968b0-140">How to create your own attribute</span></span>

<span data-ttu-id="968b0-141">属性の作成は、`Attribute` 基底クラスからの継承と同じくらいに簡単です。</span><span class="sxs-lookup"><span data-stu-id="968b0-141">Creating an attribute is as simple as inheriting from the `Attribute` base class.</span></span>

[!code-csharp[Create your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample1)]

<span data-ttu-id="968b0-142">これで、`[MySpecial]` (または `[MySpecialAttribute]`) をコード ベースの他の場所で属性として使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-142">With the above, I can now use `[MySpecial]` (or `[MySpecialAttribute]`) as an attribute elsewhere in the code base.</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CreateAttributeExample2)]

<span data-ttu-id="968b0-143">.NET の基本クラス ライブラリに含まれる `ObsoleteAttribute` のような属性は、コンパイラ内で特定の動作をトリガーします。</span><span class="sxs-lookup"><span data-stu-id="968b0-143">Attributes in the .NET base class library like `ObsoleteAttribute` trigger certain behaviors within the compiler.</span></span> <span data-ttu-id="968b0-144">しかし、作成した属性はメタデータとしてのみ機能するため、属性クラス内のコードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="968b0-144">However, any attribute you create acts only as metadata, and doesn't result in any code within the attribute class being executed.</span></span> <span data-ttu-id="968b0-145">そのメタデータを、コードの他の場所で操作する必要があります (詳細については、このチュートリアルの公判で説明します)。</span><span class="sxs-lookup"><span data-stu-id="968b0-145">It's up to you to act on that metadata elsewhere in your code (more on that later in the tutorial).</span></span>

<span data-ttu-id="968b0-146">ここに注意すべき "罠" があります。</span><span class="sxs-lookup"><span data-stu-id="968b0-146">There is a 'gotcha' here to watch out for.</span></span> <span data-ttu-id="968b0-147">前述のように、属性を使用するときは、特定の型のみを引数として渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="968b0-147">As mentioned above, only certain types are allowed to be passed as arguments when using attributes.</span></span> <span data-ttu-id="968b0-148">しかし、属性の型を作成するときに、C# コンパイラによってパラメーターの作成が阻止されることはありません。</span><span class="sxs-lookup"><span data-stu-id="968b0-148">However, when creating an attribute type, the C# compiler won't stop you from creating those parameters.</span></span> <span data-ttu-id="968b0-149">下の例では、正常にコンパイルされるコンストラクターを使用して属性を作成しています。</span><span class="sxs-lookup"><span data-stu-id="968b0-149">In the below example, I've created an attribute with a constructor that compiles just fine.</span></span>

[!code-csharp[Valid constructor used in an attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGothca1)]

<span data-ttu-id="968b0-150">しかし、このコンストラクターは属性構文では使用できません。</span><span class="sxs-lookup"><span data-stu-id="968b0-150">However, you will be unable to use this constructor with attribute syntax.</span></span>

[!code-csharp[Invalid attempt to use the attribute constructor](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeGotcha2)]

<span data-ttu-id="968b0-151">上のコードでは、次のようなエラーが発生します。`Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`</span><span class="sxs-lookup"><span data-stu-id="968b0-151">The above will cause a compiler error like `Attribute constructor parameter 'myClass' has type 'Foo', which is not a valid attribute parameter type`</span></span>

## <a name="how-to-restrict-attribute-usage"></a><span data-ttu-id="968b0-152">属性の用途を制限する方法</span><span class="sxs-lookup"><span data-stu-id="968b0-152">How to restrict attribute usage</span></span>

<span data-ttu-id="968b0-153">属性はさまざまな "ターゲット" に対して使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-153">Attributes can be used on a number of "targets".</span></span> <span data-ttu-id="968b0-154">上の例ではクラスに使用しましたが、次のターゲットに対しても使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-154">The above examples show them on classes, but they can also be used on:</span></span>

* <span data-ttu-id="968b0-155">Assembly</span><span class="sxs-lookup"><span data-stu-id="968b0-155">Assembly</span></span>
* <span data-ttu-id="968b0-156">クラス</span><span class="sxs-lookup"><span data-stu-id="968b0-156">Class</span></span>
* <span data-ttu-id="968b0-157">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="968b0-157">Constructor</span></span>
* <span data-ttu-id="968b0-158">Delegate</span><span class="sxs-lookup"><span data-stu-id="968b0-158">Delegate</span></span>
* <span data-ttu-id="968b0-159">Enum</span><span class="sxs-lookup"><span data-stu-id="968b0-159">Enum</span></span>
* <span data-ttu-id="968b0-160">event</span><span class="sxs-lookup"><span data-stu-id="968b0-160">Event</span></span>
* <span data-ttu-id="968b0-161">フィールド</span><span class="sxs-lookup"><span data-stu-id="968b0-161">Field</span></span>
* <span data-ttu-id="968b0-162">GenericParameter</span><span class="sxs-lookup"><span data-stu-id="968b0-162">GenericParameter</span></span>
* <span data-ttu-id="968b0-163">Interface</span><span class="sxs-lookup"><span data-stu-id="968b0-163">Interface</span></span>
* <span data-ttu-id="968b0-164">メソッド</span><span class="sxs-lookup"><span data-stu-id="968b0-164">Method</span></span>
* <span data-ttu-id="968b0-165">Module</span><span class="sxs-lookup"><span data-stu-id="968b0-165">Module</span></span>
* <span data-ttu-id="968b0-166">パラメーター</span><span class="sxs-lookup"><span data-stu-id="968b0-166">Parameter</span></span>
* <span data-ttu-id="968b0-167">プロパティ</span><span class="sxs-lookup"><span data-stu-id="968b0-167">Property</span></span>
* <span data-ttu-id="968b0-168">ReturnValue</span><span class="sxs-lookup"><span data-stu-id="968b0-168">ReturnValue</span></span>
* <span data-ttu-id="968b0-169">構造体</span><span class="sxs-lookup"><span data-stu-id="968b0-169">Struct</span></span>

<span data-ttu-id="968b0-170">C# の既定では、属性クラスを作成した場合、その属性は可能なすべての属性ターゲットに使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-170">When you create an attribute class, by default, C# will allow you to use that attribute on any of the possible attribute targets.</span></span> <span data-ttu-id="968b0-171">属性を特定のターゲットにのみ使用できるように制限するには、属性クラスに対して`AttributeUsageAttribute` を使用します。</span><span class="sxs-lookup"><span data-stu-id="968b0-171">If you want to restrict your attribute to certain targets, you can do so by using the `AttributeUsageAttribute` on your attribute class.</span></span> <span data-ttu-id="968b0-172">つまり、属性に属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="968b0-172">That's right, an attribute on an attribute!</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample1)]

<span data-ttu-id="968b0-173">クラスまたは構造体以外のターゲットに上の属性を設定しようとすると、次のようなコンパイラ エラーが発生します。`Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`</span><span class="sxs-lookup"><span data-stu-id="968b0-173">If you attempt to put the above attribute on something that's not a class or a struct, you will get a compiler error like `Attribute 'MyAttributeForClassAndStructOnly' is not valid on this declaration type. It is only valid on 'class, struct' declarations`</span></span>

[!code-csharp[Using your own attribute](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#AttributeUsageExample2)]

## <a name="how-to-use-attributes-attached-to-a-code-element"></a><span data-ttu-id="968b0-174">コード要素にアタッチされた属性を使用する方法</span><span class="sxs-lookup"><span data-stu-id="968b0-174">How to use attributes attached to a code element</span></span>

<span data-ttu-id="968b0-175">属性はメタデータとして機能します。</span><span class="sxs-lookup"><span data-stu-id="968b0-175">Attributes act as metadata.</span></span> <span data-ttu-id="968b0-176">外からの力が働かないかぎり、実際には何の処理も実行しません。</span><span class="sxs-lookup"><span data-stu-id="968b0-176">Without some outward force, they won't actually do anything.</span></span>

<span data-ttu-id="968b0-177">属性を見つけて操作するには、通常、[Reflection](../programming-guide/concepts/reflection.md) が必要になります。</span><span class="sxs-lookup"><span data-stu-id="968b0-177">To find and act on attributes, [Reflection](../programming-guide/concepts/reflection.md) is generally needed.</span></span> <span data-ttu-id="968b0-178">このチュートリアルでは Reflection について詳しく説明しませんが、基本的な考えとしては、Reflection を使用すると C# で他のコードを調べるコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-178">I won't cover Reflection in-depth in this tutorial, but the basic idea is that Reflection allows you to write code in C# that examines other code.</span></span>

<span data-ttu-id="968b0-179">たとえば、Reflection を使用して次のクラスに関する情報を取得できます (コードの先頭に `using System.Reflection;` を追加する)。</span><span class="sxs-lookup"><span data-stu-id="968b0-179">For instance, you can use Reflection to get information about a class(add `using System.Reflection;` at the head of your code):</span></span>

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample1)]

<span data-ttu-id="968b0-180">出力は次のようになります。`The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="968b0-180">That will print out something like: `The assembly qualified name of MyClass is ConsoleApplication.MyClass, attributes, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>

<span data-ttu-id="968b0-181">`TypeInfo` オブジェクト (または `MemberInfo`、`FieldInfo` など) を取得したら、`GetCustomAttributes` メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-181">Once you have a `TypeInfo` object (or a `MemberInfo`, `FieldInfo`, etc), you can use the `GetCustomAttributes` method.</span></span> <span data-ttu-id="968b0-182">このメソッドは `Attribute` オブジェクトのコレクションを返します。</span><span class="sxs-lookup"><span data-stu-id="968b0-182">This will return a collection of `Attribute` objects.</span></span>
<span data-ttu-id="968b0-183">また、`GetCustomAttribute` を使用して Attribute 型を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="968b0-183">You can also use `GetCustomAttribute` and specify an Attribute type.</span></span>

<span data-ttu-id="968b0-184">`MyClass` クラス (前の例で `[Obsolete]` 属性を適用したクラス)の `MemberInfo` インスタンスに対して `GetCustomAttributes` を使用する例を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="968b0-184">Here's an example of using `GetCustomAttributes` on a `MemberInfo` instance for `MyClass` (which we saw earlier has an `[Obsolete]` attribute on it).</span></span>

[!code-csharp[Getting type information with Reflection](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#ReflectionExample2)]

<span data-ttu-id="968b0-185">コンソールには次のように出力されます。`Attribute on MyClass: ObsoleteAttribute`</span><span class="sxs-lookup"><span data-stu-id="968b0-185">That will print to console: `Attribute on MyClass: ObsoleteAttribute`.</span></span> <span data-ttu-id="968b0-186">`MyClass` に他の属性を追加してみてください。</span><span class="sxs-lookup"><span data-stu-id="968b0-186">Try adding other attributes to `MyClass`.</span></span>

<span data-ttu-id="968b0-187">`Attribute` オブジェクトは限定的にインスタンス化されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="968b0-187">It's important to note that these `Attribute` objects are instantiated lazily.</span></span> <span data-ttu-id="968b0-188">つまり、`GetCustomAttribute` または `GetCustomAttributes` を使用するまでインスタンス化されません。</span><span class="sxs-lookup"><span data-stu-id="968b0-188">That is, they won't be instantiated until you use `GetCustomAttribute` or `GetCustomAttributes`.</span></span>
<span data-ttu-id="968b0-189">また、インスタンス化は使用のたびに行われます。</span><span class="sxs-lookup"><span data-stu-id="968b0-189">They are also instantiated each time.</span></span> <span data-ttu-id="968b0-190">行内で `GetCustomAttributes` を 2 回呼び出すと、`ObsoleteAttribute` の異なる 2 つのインスタンスが返されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-190">Calling `GetCustomAttributes` twice in a row will return two different instances of `ObsoleteAttribute`.</span></span>

## <a name="common-attributes-in-the-base-class-library-bcl"></a><span data-ttu-id="968b0-191">基本クラス ライブラリ (BCL) のよく使用される属性</span><span class="sxs-lookup"><span data-stu-id="968b0-191">Common attributes in the base class library (BCL)</span></span>

<span data-ttu-id="968b0-192">属性は、さまざまなツールやフレームワークで使用されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-192">Attributes are used by many tools and frameworks.</span></span> <span data-ttu-id="968b0-193">NUnit は、`[Test]` や `[TestFixture]` などの属性を NUnit テスト ランナーで使用します。</span><span class="sxs-lookup"><span data-stu-id="968b0-193">NUnit uses attributes like `[Test]` and `[TestFixture]` that are used by the NUnit test runner.</span></span> <span data-ttu-id="968b0-194">ASP.NET MVC は、`[Authorize]` などの属性を使用して、MVC アクションに対する横断的な処理を実行するためのアクション フィルター フレームワークを提供します。</span><span class="sxs-lookup"><span data-stu-id="968b0-194">ASP.NET MVC uses attributes like `[Authorize]` and provides an action filter framework to perform cross-cutting concerns on MVC actions.</span></span> <span data-ttu-id="968b0-195">[PostSharp](https://www.postsharp.net) は、属性構文を使用して C# でアスペクト指向プログラミングを行えるようにします。</span><span class="sxs-lookup"><span data-stu-id="968b0-195">[PostSharp](https://www.postsharp.net) uses the attribute syntax to allow aspect-oriented programming in C#.</span></span>

<span data-ttu-id="968b0-196">.NET Core の基本クラス ライブラリに組み込まれている、よく使用される属性のいくつかを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="968b0-196">Here are a few notable attributes built into the .NET Core base class libraries:</span></span>

* <span data-ttu-id="968b0-197">`[Obsolete]`。</span><span class="sxs-lookup"><span data-stu-id="968b0-197">`[Obsolete]`.</span></span> <span data-ttu-id="968b0-198">これは上の例で使用した属性で、`System` 名前空間に格納されています。</span><span class="sxs-lookup"><span data-stu-id="968b0-198">This one was used in the above examples, and it lives in the `System` namespace.</span></span> <span data-ttu-id="968b0-199">この属性は、コード ベースの変更に関する宣言的なドキュメントを提供するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="968b0-199">It is useful to provide declarative documentation about a changing code base.</span></span> <span data-ttu-id="968b0-200">メッセージは文字列の形式で指定でき、別のブール型パラメーターを使用すると、コンパイラの警告をコンパイラのエラーにエスカレートすることができます。</span><span class="sxs-lookup"><span data-stu-id="968b0-200">A message can be provided in the form of a string, and another boolean parameter can be used to escalate from a compiler warning to a compiler error.</span></span>

* <span data-ttu-id="968b0-201">`[Conditional]`。</span><span class="sxs-lookup"><span data-stu-id="968b0-201">`[Conditional]`.</span></span> <span data-ttu-id="968b0-202">この属性は `System.Diagnostics` 名前空間に格納されています。</span><span class="sxs-lookup"><span data-stu-id="968b0-202">This attribute is in the `System.Diagnostics` namespace.</span></span> <span data-ttu-id="968b0-203">この属性はメソッド (または属性クラス) に適用できます。</span><span class="sxs-lookup"><span data-stu-id="968b0-203">This attribute can be applied to methods (or attribute classes).</span></span> <span data-ttu-id="968b0-204">コンス トラクターに文字列を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="968b0-204">You must pass a string to the constructor.</span></span>
<span data-ttu-id="968b0-205">その文字列が `#define` ディレクティブと一致しない場合、そのメソッドの呼び出し (メソッド自体ではありません) が C# コンパイラによって除外されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-205">If that string doesn't match a `#define` directive, then any calls to that method (but not the method itself) will be removed by the C# compiler.</span></span> <span data-ttu-id="968b0-206">通常、この属性はデバッグ (診断) 目的で使用されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-206">Typically this is used for debugging (diagnostics) purposes.</span></span>

* <span data-ttu-id="968b0-207">`[CallerMemberName]`。</span><span class="sxs-lookup"><span data-stu-id="968b0-207">`[CallerMemberName]`.</span></span> <span data-ttu-id="968b0-208">この属性はパラメーターに使用でき、`System.Runtime.CompilerServices` 名前空間に格納されています。</span><span class="sxs-lookup"><span data-stu-id="968b0-208">This attribute can be used on parameters, and lives in the `System.Runtime.CompilerServices` namespace.</span></span> <span data-ttu-id="968b0-209">この属性は、別のメソッドを呼び出しているメソッドの名前を挿入するために使用します。</span><span class="sxs-lookup"><span data-stu-id="968b0-209">This is an attribute that is used to inject the name of the method that is calling another method.</span></span> <span data-ttu-id="968b0-210">これは通常、さまざまな UI フレームワークで INotifyPropertyChanged を実装する際に "マジック文字列" を排除するための方法として使用されます。</span><span class="sxs-lookup"><span data-stu-id="968b0-210">This is typically used as a way to eliminate 'magic strings' when implementing INotifyPropertyChanged in various UI frameworks.</span></span> <span data-ttu-id="968b0-211">以下に例を示します。</span><span class="sxs-lookup"><span data-stu-id="968b0-211">As an example:</span></span>

[!code-csharp[Using CallerMemberName when implementing INotifyPropertyChanged](../../../samples/snippets/csharp/tutorials/attributes/Program.cs#CallerMemberName1)]

<span data-ttu-id="968b0-212">上のコードでは、リテラルの `"Name"` 文字列を使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="968b0-212">In the above code, you don't have to have a literal `"Name"` string.</span></span> <span data-ttu-id="968b0-213">これは入力ミス関連のバグを防ぎ、リファクタリングや名前変更をスムーズにするのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="968b0-213">This can help prevent typo-related bugs and also makes for smoother refactoring/renaming.</span></span>

## <a name="summary"></a><span data-ttu-id="968b0-214">まとめ</span><span class="sxs-lookup"><span data-stu-id="968b0-214">Summary</span></span>

<span data-ttu-id="968b0-215">属性によって C# に宣言機能が追加されますが、それらはメタデータ形式のコードであり、単独では機能しません。</span><span class="sxs-lookup"><span data-stu-id="968b0-215">Attributes bring declarative power to C#, but they are a meta-data form of code and don't act by themselves.</span></span>
