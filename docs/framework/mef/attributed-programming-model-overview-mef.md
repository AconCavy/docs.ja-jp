---
title: 属性付きプログラミング モデルの概要 (MEF)
description: .NET で Managed Extensibility Framework (MEF) の既定プログラミング モデルとなる属性付きプログラミング モデルの概要について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MEF, attributed programming model
- attributed programming model [MEF]
ms.assetid: 49b787ff-2741-4836-ad51-c3017dc592d4
ms.openlocfilehash: aea3a19ffe6f177901e5c0839b618bb36f573beb
ms.sourcegitcommit: 97ce5363efa88179dd76e09de0103a500ca9b659
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/13/2020
ms.locfileid: "86281369"
---
# <a name="attributed-programming-model-overview-mef"></a><span data-ttu-id="aef55-103">属性付きプログラミング モデルの概要 (MEF)</span><span class="sxs-lookup"><span data-stu-id="aef55-103">Attributed Programming Model Overview (MEF)</span></span>

<span data-ttu-id="aef55-104">MEF (Managed Extensibility Framework) における *プログラミング モデル* とは、MEF で操作する一連の概念オブジェクトを定義するための特定の方法です。</span><span class="sxs-lookup"><span data-stu-id="aef55-104">In the Managed Extensibility Framework (MEF), a *programming model* is a particular method of defining the set of conceptual objects on which MEF operates.</span></span> <span data-ttu-id="aef55-105">これらの概念オブジェクトには、パート、インポート、およびエクスポートが含まれます。</span><span class="sxs-lookup"><span data-stu-id="aef55-105">These conceptual objects include parts, imports, and exports.</span></span> <span data-ttu-id="aef55-106">MEF では、これらのオブジェクトが使用されますが、その表現方法は指定されていません。</span><span class="sxs-lookup"><span data-stu-id="aef55-106">MEF uses these objects, but does not specify how they should be represented.</span></span> <span data-ttu-id="aef55-107">そのため、カスタマイズしたプログラミング モデルを含むさまざまなプログラミング モデルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-107">Therefore, a wide variety of programming models are possible, including customized programming models.</span></span>

<span data-ttu-id="aef55-108">MEF で使用される既定のプログラミング モデルは、 *属性付きプログラミング モデル*です。</span><span class="sxs-lookup"><span data-stu-id="aef55-108">The default programming model used in MEF is the *attributed programming model*.</span></span> <span data-ttu-id="aef55-109">属性付きプログラミング モデルでは、パート、インポート、エクスポート、およびその他のオブジェクトを、通常の .NET Framework クラスを装飾する属性を使用して定義します。</span><span class="sxs-lookup"><span data-stu-id="aef55-109">In the attributed programming model parts, imports, exports, and other objects are defined with attributes that decorate ordinary .NET Framework classes.</span></span> <span data-ttu-id="aef55-110">ここでは、属性付きプログラミング モデルの属性を使用して MEF アプリケーションを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="aef55-110">This topic explains how to use the attributes provided by the attributed programming model to create a MEF application.</span></span>

<a name="import_and_export_basics"></a>

## <a name="import-and-export-basics"></a><span data-ttu-id="aef55-111">インポートとエクスポートの基本</span><span class="sxs-lookup"><span data-stu-id="aef55-111">Import and Export Basics</span></span>

<span data-ttu-id="aef55-112">*エクスポート* とは、パートがコンテナー内の他のパートに提供する値です。 *インポート* とは、パートがコンテナーに対して示す要件で、使用可能なエクスポートによって満たされます。</span><span class="sxs-lookup"><span data-stu-id="aef55-112">An *export* is a value that a part provides to other parts in the container, and an *import* is a requirement that a part expresses to the container, to be filled from the available exports.</span></span> <span data-ttu-id="aef55-113">属性付きプログラミング モデルでインポートとエクスポートを宣言するには、クラスやメンバーを `Import` 属性と `Export` 属性で装飾します。</span><span class="sxs-lookup"><span data-stu-id="aef55-113">In the attributed programming model, imports and exports are declared by decorating classes or members with the `Import` and `Export` attributes.</span></span> <span data-ttu-id="aef55-114">`Export` 属性で装飾できるのは、クラス、フィールド、プロパティ、およびメソッドです。 `Import` 属性で装飾できるのは、フィールド、プロパティ、およびコンストラクター パラメーターです。</span><span class="sxs-lookup"><span data-stu-id="aef55-114">The `Export` attribute can decorate a class, field, property, or method, while the `Import` attribute can decorate a field, property, or constructor parameter.</span></span>

<span data-ttu-id="aef55-115">インポートとエクスポートが一致するには、インポートとエクスポートの *コントラクト*が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-115">In order for an import to be matched with an export, the import and export must have the same *contract*.</span></span> <span data-ttu-id="aef55-116">コントラクトは、 *コントラクト名*と呼ばれる文字列と、 *コントラクト型*と呼ばれる型 (エクスポートまたはインポートされるオブジェクトの型) で構成されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-116">The contract consists of a string, called the *contract name*, and the type of the exported or imported object, called the *contract type*.</span></span> <span data-ttu-id="aef55-117">エクスポートが特定のインポートを満たすと見なされるのは、コントラクト名とコントラクト型の両方が一致する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="aef55-117">Only if both the contract name and contract type match is an export considered to fulfill a particular import.</span></span>

<span data-ttu-id="aef55-118">これらのコントラクト パラメーターは、どちらも明示的でも暗黙的でもかまいません。</span><span class="sxs-lookup"><span data-stu-id="aef55-118">Either or both of the contract parameters can be implicit or explicit.</span></span> <span data-ttu-id="aef55-119">次のコードは、基本的なインポートを宣言するクラスを示しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-119">The following code shows a class that declares a basic import.</span></span>

```vb
Public Class MyClass1
    <Import()>
    Public Property MyAddin As IMyAddin
End Class
```

```csharp
public class MyClass
{
    [Import]
    public IMyAddin MyAddin { get; set; }
}
```

<span data-ttu-id="aef55-120">このインポートでは、 `Import` 属性にコントラクト型のパラメーターもコントラクト名のパラメーターもアタッチされていません。</span><span class="sxs-lookup"><span data-stu-id="aef55-120">In this import, the `Import` attribute has neither a contract type nor a contract name parameter attached.</span></span> <span data-ttu-id="aef55-121">したがって、これらは両方とも、装飾されたプロパティから推論されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-121">Therefore, both will be inferred from the decorated property.</span></span> <span data-ttu-id="aef55-122">この例では、コントラクト型は `IMyAddin`になり、コントラクト名は、コントラクト型から作成される一意の文字列になります</span><span class="sxs-lookup"><span data-stu-id="aef55-122">In this case, the contract type will be `IMyAddin`, and the contract name will be a unique string created from the contract type.</span></span> <span data-ttu-id="aef55-123">(したがって、このコントラクト名と一致するのは、同じように `IMyAddin`型から推論された名前を持つエクスポートだけです)。</span><span class="sxs-lookup"><span data-stu-id="aef55-123">(In other words, the contract name will match only exports whose names are also inferred from the type `IMyAddin`.)</span></span>

<span data-ttu-id="aef55-124">上のインポートと一致するエクスポートの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="aef55-124">The following shows an export that matches the previous import.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="aef55-125">このエクスポートのコントラクト型は `IMyAddin` です。これは、 `Export` 属性のパラメーターとして指定されています。</span><span class="sxs-lookup"><span data-stu-id="aef55-125">In this export, the contract type is `IMyAddin` because it is specified as a parameter of the `Export` attribute.</span></span> <span data-ttu-id="aef55-126">エクスポートされる型は、コントラクト型と同じ型、コントラクト型から派生する型、またはコントラクト型を実装する型 (コントラクト型がインターフェイスの場合) のいずれかである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-126">The exported type must be either the same as the contract type, derive from the contract type, or implement the contract type if it is an interface.</span></span> <span data-ttu-id="aef55-127">このエクスポートの実際の型は `MyLogger` で、 `IMyAddin`インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-127">In this export, the actual type `MyLogger` implements the interface `IMyAddin`.</span></span> <span data-ttu-id="aef55-128">このエクスポートのコントラクト名はコントラクト型から推論されるため、このエクスポートは前のインポートと一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-128">The contract name is inferred from the contract type, which means that this export will match the previous import.</span></span>

> [!NOTE]
> <span data-ttu-id="aef55-129">エクスポートとインポートは、パブリック クラスかパブリック メンバーで宣言するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="aef55-129">Exports and imports should usually be declared on public classes or members.</span></span> <span data-ttu-id="aef55-130">その他の宣言もサポートされていますが、プライベート、プロテクト、または内部のメンバーをエクスポートしたりインポートしたりすると、パートの分離モデルが壊れるため、推奨されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-130">Other declarations are supported, but exporting or importing a private, protected, or internal member breaks the isolation model for the part and is therefore not recommended.</span></span>

<span data-ttu-id="aef55-131">エクスポートとインポートが一致と見なされるには、コントラクト型が厳密に一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-131">The contract type must match exactly for the export and import to be considered a match.</span></span> <span data-ttu-id="aef55-132">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aef55-132">Consider the following export.</span></span>

```vb
<Export()> 'WILL NOT match the previous import!
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export] //WILL NOT match the previous import!
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="aef55-133">このエクスポートのコントラクト型は、 `MyLogger` ではなく `IMyAddin`です。</span><span class="sxs-lookup"><span data-stu-id="aef55-133">In this export, the contract type is `MyLogger` instead of `IMyAddin`.</span></span> <span data-ttu-id="aef55-134">`MyLogger` は `IMyAddin`を実装するため、 `IMyAddin` オブジェクトにキャストできますが、コントラクト型が同じではないため、このエクスポートは前のインポートと一致しません。</span><span class="sxs-lookup"><span data-stu-id="aef55-134">Even though `MyLogger` implements `IMyAddin`, and therefore could be cast to an `IMyAddin` object, this export will not match the previous import because the contract types are not the same.</span></span>

<span data-ttu-id="aef55-135">一般に、ほとんどのコントラクトはコントラクト型とメタデータで定義する必要があり、コントラクト名を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="aef55-135">In general, it is not necessary to specify the contract name, and most contracts should be defined in terms of the contract type and metadata.</span></span> <span data-ttu-id="aef55-136">ただし、コントラクト名を直接指定することが重要である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="aef55-136">However, under certain circumstances, it is important to specify the contract name directly.</span></span> <span data-ttu-id="aef55-137">最も一般的なのは、プリミティブなどの一般的な型を共有する複数の値をクラスでエクスポートする場合です。</span><span class="sxs-lookup"><span data-stu-id="aef55-137">The most common case is when a class exports several values that share a common type, such as primitives.</span></span> <span data-ttu-id="aef55-138">コントラクト名を指定するには、 `Import` 属性または `Export` 属性の最初のパラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="aef55-138">The contract name can be specified as the first parameter of the `Import` or `Export` attribute.</span></span> <span data-ttu-id="aef55-139">次のコードでは、インポートとエクスポートに `MajorRevision`というコントラクト名が指定されています。</span><span class="sxs-lookup"><span data-stu-id="aef55-139">The following code shows an import and an export with a specified contract name of `MajorRevision`.</span></span>

```vb
Public Class MyExportClass

    'This one will match
    <Export("MajorRevision")>
    Public ReadOnly Property MajorRevision As Integer
        Get
            Return 4
        End Get
    End Property

    <Export("MinorRevision")>
    Public ReadOnly Property MinorRevision As Integer
        Get
            Return 16
        End Get
    End Property
End Class
```

```csharp
public class MyClass
{
    [Import("MajorRevision")]
    public int MajorRevision { get; set; }
}

public class MyExportClass
{
    [Export("MajorRevision")] //This one will match.
    public int MajorRevision = 4;

    [Export("MinorRevision")]
    public int MinorRevision = 16;
}
```

<span data-ttu-id="aef55-140">コントラクト型は、指定しなくても、インポートやエクスポートの型から推論されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-140">If the contract type is not specified, it will still be inferred from the type of the import or export.</span></span> <span data-ttu-id="aef55-141">ただし、インポートとエクスポートが一致と見なされるには、コントラクト名が明示的に指定されていても、コントラクト型も一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-141">However, even if the contract name is specified explicitly, the contract type must also match exactly for the import and export to be considered a match.</span></span> <span data-ttu-id="aef55-142">たとえば、上の `MajorRevision` フィールドが文字列だった場合は、推論されるコントラクト型が一致しなくなるため、コントラクト名が同じであっても、エクスポートとインポートが一致しなくなります。</span><span class="sxs-lookup"><span data-stu-id="aef55-142">For example, if the `MajorRevision` field was a string, the inferred contract types would not match and the export would not match the import, despite having the same contract name.</span></span>

### <a name="importing-and-exporting-a-method"></a><span data-ttu-id="aef55-143">メソッドのインポートとエクスポート</span><span class="sxs-lookup"><span data-stu-id="aef55-143">Importing and Exporting a Method</span></span>

<span data-ttu-id="aef55-144">`Export` 属性は、クラス、プロパティ、または関数と同じようにメソッドを装飾することもできます。</span><span class="sxs-lookup"><span data-stu-id="aef55-144">The `Export` attribute can also decorate a method, in the same way as a class, property, or function.</span></span> <span data-ttu-id="aef55-145">型は推論できないため、メソッドのエクスポートではコントラクト型またはコントラクト名を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-145">Method exports must specify a contract type or contract name, as the type cannot be inferred.</span></span> <span data-ttu-id="aef55-146">型には、カスタム デリゲートまたはジェネリック型 ( `Func`など) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-146">The specified type can be either a custom delegate or a generic type, such as `Func`.</span></span> <span data-ttu-id="aef55-147">次のクラスは、 `DoSomething`というメソッドをエクスポートしています。</span><span class="sxs-lookup"><span data-stu-id="aef55-147">The following class exports a method named `DoSomething`.</span></span>

```vb
Public Class MyAddin

    'Explicitly specifying a generic type
    <Export(GetType(Func(Of Integer, String)))>
    Public Function DoSomething(ByVal TheParam As Integer) As String
        Return Nothing 'Function body goes here
    End Function

End Class
```

```csharp
public class MyAddin
{
    //Explicitly specifying a generic type.
    [Export(typeof(Func<int, string>))]
    public string DoSomething(int TheParam);
}
```

<span data-ttu-id="aef55-148">このクラスの `DoSomething` メソッドは、1 つの `int` パラメーターを受け取って `string`を返します。</span><span class="sxs-lookup"><span data-stu-id="aef55-148">In this class, the `DoSomething` method takes a single `int` parameter and returns a `string`.</span></span> <span data-ttu-id="aef55-149">このエクスポートに一致するには、インポート側のパートで適切なメンバーが宣言されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-149">To match this export, the importing part must declare an appropriate member.</span></span> <span data-ttu-id="aef55-150">`DoSomething` メソッドをインポートするクラスを次に示します。</span><span class="sxs-lookup"><span data-stu-id="aef55-150">The following class imports the `DoSomething` method.</span></span>

```vb
Public Class MyClass1

    'Contract name must match!
    <Import()>
    Public Property MajorRevision As Func(Of Integer, String)
End Class
```

```csharp
public class MyClass
{
    [Import] //Contract name must match!
    public Func<int, string> DoSomething { get; set; }
}
```

<span data-ttu-id="aef55-151">`Func<T, T>` オブジェクトの使用方法の詳細については、「 <xref:System.Func%602>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aef55-151">For more information about how to use of the `Func<T, T>` object, see <xref:System.Func%602>.</span></span>

<a name="types_of_imports"></a>

## <a name="types-of-imports"></a><span data-ttu-id="aef55-152">インポートの種類</span><span class="sxs-lookup"><span data-stu-id="aef55-152">Types of Imports</span></span>

<span data-ttu-id="aef55-153">MEF では、動的インポート、遅延インポート、前提条件インポート、省略可能インポートなど、複数の種類のインポートがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aef55-153">MEF support several import types, including dynamic, lazy, prerequisite, and optional.</span></span>

### <a name="dynamic-imports"></a><span data-ttu-id="aef55-154">動的インポート</span><span class="sxs-lookup"><span data-stu-id="aef55-154">Dynamic Imports</span></span>

<span data-ttu-id="aef55-155">インポート側のクラスが、特定のコントラクト名を持つ任意の型のエクスポートと一致するようにするには、</span><span class="sxs-lookup"><span data-stu-id="aef55-155">In some cases, the importing class may want to match exports of any type that have a particular contract name.</span></span> <span data-ttu-id="aef55-156">クラスで *動的インポート*を宣言します。</span><span class="sxs-lookup"><span data-stu-id="aef55-156">In this scenario, the class can declare a *dynamic import*.</span></span> <span data-ttu-id="aef55-157">次のインポートは、コントラクト名が "TheString" の任意のエクスポートと一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-157">The following import matches any export with contract name "TheString".</span></span>

```vb
Public Class MyClass1

    <Import("TheString")>
    Public Property MyAddin

End Class
```

```csharp
public class MyClass
{
    [Import("TheString")]
    public dynamic MyAddin { get; set; }
}
```

<span data-ttu-id="aef55-158">`dynamic` キーワードから推論されるコントラクト型は、任意のコントラクト型と一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-158">When the contract type is inferred from the `dynamic` keyword, it will match any contract type.</span></span> <span data-ttu-id="aef55-159">この場合、インポートで **常に** コントラクト名を指定する必要があります</span><span class="sxs-lookup"><span data-stu-id="aef55-159">In this case, an import should **always** specify a contract name to match on.</span></span> <span data-ttu-id="aef55-160">(コントラクト名が指定されていないと、そのインポートはどのエクスポートとも一致しないと見なされます)。次のエクスポートは、どちらも前のインポートと一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-160">(If no contract name is specified, the import will be considered to match no exports.) Both of the following exports would match the previous import.</span></span>

```vb
<Export("TheString", GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class

<Export("TheString")>
Public Class MyToolbar

End Class
```

```csharp
[Export("TheString", typeof(IMyAddin))]
public class MyLogger : IMyAddin { }

[Export("TheString")]
public class MyToolbar { }
```

<span data-ttu-id="aef55-161">当然ながら、インポート側のクラスが任意の型のオブジェクトに対応できるようになっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-161">Obviously, the importing class must be prepared to deal with an object of arbitrary type.</span></span>

### <a name="lazy-imports"></a><span data-ttu-id="aef55-162">遅延インポート</span><span class="sxs-lookup"><span data-stu-id="aef55-162">Lazy Imports</span></span>

<span data-ttu-id="aef55-163">インポート側のクラスで、インポートされるオブジェクトへの間接参照を使用して、そのオブジェクトがすぐにインスタンス化されないようにするには、</span><span class="sxs-lookup"><span data-stu-id="aef55-163">In some cases, the importing class may require an indirect reference to the imported object, so that the object is not instantiated immediately.</span></span> <span data-ttu-id="aef55-164">クラスで *のコントラクト型を使用して、* 遅延インポート `Lazy<T>`を宣言します。</span><span class="sxs-lookup"><span data-stu-id="aef55-164">In this scenario, the class can declare a *lazy import* by using a contract type of `Lazy<T>`.</span></span> <span data-ttu-id="aef55-165">次のインポート側プロパティは遅延インポートを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-165">The following importing property declares a lazy import.</span></span>

```vb
Public Class MyClass1

    <Import()>
    Public Property MyAddin As Lazy(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [Import]
    public Lazy<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="aef55-166">`Lazy<T>` のコントラクト型は、合成エンジンでは `T`のコントラクト型と同じと見なされます。</span><span class="sxs-lookup"><span data-stu-id="aef55-166">From the point of view of the composition engine, a contract type of `Lazy<T>` is considered identical to contract type of `T`.</span></span> <span data-ttu-id="aef55-167">したがって、上のインポートは次のエクスポートと一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-167">Therefore, the previous import would match the following export.</span></span>

```vb
<Export(GetType(IMyAddin))>
Public Class MyLogger
    Implements IMyAddin

End Class
```

```csharp
[Export(typeof(IMyAddin))]
public class MyLogger : IMyAddin { }
```

<span data-ttu-id="aef55-168">`Import` 属性でコントラクト名とコントラクト型を指定する方法については、前の「インポートとエクスポートの基本」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aef55-168">The contract name and contract type can be specified in the `Import` attribute for a lazy import, as described earlier in the "Basic Imports and Exports" section.</span></span>

### <a name="prerequisite-imports"></a><span data-ttu-id="aef55-169">前提条件インポート</span><span class="sxs-lookup"><span data-stu-id="aef55-169">Prerequisite Imports</span></span>

<span data-ttu-id="aef55-170">エクスポートされる MEF パートは、通常、直接要求された場合や、一致したインポートを満たす必要がある場合に、合成エンジンによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-170">Exported MEF parts are typically created by the composition engine, in response to a direct request or the need to fill a matched import.</span></span> <span data-ttu-id="aef55-171">合成エンジンがパートを作成するとき、既定ではパラメーターなしのコンストラクターが使用されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-171">By default, when creating a part, the composition engine uses the parameter-less constructor.</span></span> <span data-ttu-id="aef55-172">別のコンストラクターが使用されるようにするには、そのコンストラクターを `ImportingConstructor` 属性でマークします。</span><span class="sxs-lookup"><span data-stu-id="aef55-172">To make the engine use a different constructor, you can mark it with the `ImportingConstructor` attribute.</span></span>

<span data-ttu-id="aef55-173">合成エンジンで使用するコンストラクターは、各パートで 1 つだけ指定できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-173">Each part may have only one constructor for use by the composition engine.</span></span> <span data-ttu-id="aef55-174">パラメーターなしのコンストラクターも `ImportingConstructor` 属性も指定されていない場合、または複数の `ImportingConstructor` 属性が指定されている場合は、エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="aef55-174">Providing no parameterless constructor and no `ImportingConstructor` attribute, or providing more than one `ImportingConstructor` attribute, will produce an error.</span></span>

<span data-ttu-id="aef55-175">`ImportingConstructor` 属性でマークされたコンストラクターでは、パラメーターを設定するために、すべてのパラメーターが自動的にインポートとして宣言されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-175">To fill the parameters of a constructor marked with the `ImportingConstructor` attribute, all of those parameters are automatically declared as imports.</span></span> <span data-ttu-id="aef55-176">これは、パートの初期化の際に使用されるインポートを宣言するのに便利です。</span><span class="sxs-lookup"><span data-stu-id="aef55-176">This is a convenient way to declare imports that are used during part initialization.</span></span> <span data-ttu-id="aef55-177">次のクラスは、 `ImportingConstructor` を使用してインポートを宣言しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-177">The following class uses `ImportingConstructor` to declare an import.</span></span>

```vb
Public Class MyClass1

    Private _theAddin As IMyAddin

    'Parameterless constructor will NOT be used
    'because the ImportingConstructor
    'attribute is present.
    Public Sub New()

    End Sub

    'This constructor will be used.
    'An import with contract type IMyAddin
    'is declared automatically.
    <ImportingConstructor()>
    Public Sub New(ByVal MyAddin As IMyAddin)
        _theAddin = MyAddin
    End Sub

End Class
```

```csharp
public class MyClass
{
    private IMyAddin _theAddin;

    //Parameterless constructor will NOT be
    //used because the ImportingConstructor
    //attribute is present.
    public MyClass() { }

    //This constructor will be used.
    //An import with contract type IMyAddin is
    //declared automatically.
    [ImportingConstructor]
    public MyClass(IMyAddin MyAddin)
    {
        _theAddin = MyAddin;
    }
}
```

<span data-ttu-id="aef55-178">`ImportingConstructor` 属性では、すべてのパラメーター インポートに対して、推論されるコントラクト型とコントラクト名が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-178">By default, the `ImportingConstructor` attribute uses inferred contract types and contract names for all of the parameter imports.</span></span> <span data-ttu-id="aef55-179">これをオーバーライドするには、パラメーターを `Import` 属性で装飾して、コントラクト型とコントラクト名を明示的に定義します。</span><span class="sxs-lookup"><span data-stu-id="aef55-179">It is possible to override this by decorating the parameters with `Import` attributes, which can then define the contract type and contract name explicitly.</span></span> <span data-ttu-id="aef55-180">次のコードは、この構文を使用して親クラスの代わりに派生クラスをインポートするコンストラクターを示しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-180">The following code demonstrates a constructor that uses this syntax to import a derived class instead of a parent class.</span></span>

```vb
<ImportingConstructor()>
Public Sub New(<Import(GetType(IMySubAddin))> ByVal MyAddin As IMyAddin)

End Sub
```

```csharp
[ImportingConstructor]
public MyClass([Import(typeof(IMySubAddin))]IMyAddin MyAddin)
{
    _theAddin = MyAddin;
}
```

<span data-ttu-id="aef55-181">コレクション パラメーターには特別な注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="aef55-181">In particular, you should be careful with collection parameters.</span></span> <span data-ttu-id="aef55-182">たとえば、 `ImportingConstructor` 型のパラメーターを持つコンストラクターに対して `IEnumerable<int>`を指定すると、そのインポートは、 `IEnumerable<int>`型の一連のエクスポートではなく、 `int`型の 1 つのエクスポートと一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-182">For example, if you specify `ImportingConstructor` on a constructor with a parameter of type `IEnumerable<int>`, the import will match a single export of type `IEnumerable<int>`, instead of a set of exports of type `int`.</span></span> <span data-ttu-id="aef55-183">`int`型の一連のエクスポートと一致するようにするには、そのパラメーターを `ImportMany` 属性で装飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-183">To match a set of exports of type `int`, you have to decorate the parameter with the `ImportMany` attribute.</span></span>

<span data-ttu-id="aef55-184">`ImportingConstructor` 属性でインポートとして宣言したパラメーターは、 *前提条件インポート*としてもマークされます。</span><span class="sxs-lookup"><span data-stu-id="aef55-184">Parameters declared as imports by the `ImportingConstructor` attribute are also marked as *prerequisite imports*.</span></span> <span data-ttu-id="aef55-185">MEF では、通常はエクスポートとインポートが *循環参照*を形成することが許可されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-185">MEF normally allows exports and imports to form a *cycle*.</span></span> <span data-ttu-id="aef55-186">循環参照とは、たとえば、オブジェクト A がオブジェクト B をインポートし、そのオブジェクト B がオブジェクト A をインポートするような場合です。通常は、循環参照が問題になることはなく、合成コンテナーで両方のオブジェクトが正常に構築されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-186">For example, a cycle is where object A imports object B, which in turn imports object A. Under ordinary circumstances, a cycle is not a problem, and the composition container constructs both objects normally.</span></span>

<span data-ttu-id="aef55-187">パートのコンストラクターで、インポートされる値が必要な場合、そのオブジェクトは循環参照に参加できません。</span><span class="sxs-lookup"><span data-stu-id="aef55-187">When an imported value is required by the constructor of a part, that object cannot participate in a cycle.</span></span> <span data-ttu-id="aef55-188">オブジェクト A を構築するには先にオブジェクト B が構築されている必要がある場合に、オブジェクト B がオブジェクト A をインポートしていると、循環参照を解決できなくなるため、合成エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="aef55-188">If object A requires that object B be constructed before it can be constructed itself, and object B imports object A, then the cycle will be unable to resolve and a composition error will occur.</span></span> <span data-ttu-id="aef55-189">したがって、コンストラクターのパラメーターで宣言されているインポートは前提条件インポートになります。前提条件インポートとは、それらがすべて満たされないと、それらを必要とするオブジェクトのエクスポートを使用できるようにならないインポートです。</span><span class="sxs-lookup"><span data-stu-id="aef55-189">Imports declared on constructor parameters are therefore prerequisite imports, which must all be filled before any of the exports from the object that requires them can be used.</span></span>

### <a name="optional-imports"></a><span data-ttu-id="aef55-190">省略可能インポート</span><span class="sxs-lookup"><span data-stu-id="aef55-190">Optional Imports</span></span>

<span data-ttu-id="aef55-191">`Import` 属性は、パートが機能するための要件を指定します。</span><span class="sxs-lookup"><span data-stu-id="aef55-191">The `Import` attribute specifies a requirement for the part to function.</span></span> <span data-ttu-id="aef55-192">インポートが満たされないと、パートの合成が失敗し、そのパートを使用できません。</span><span class="sxs-lookup"><span data-stu-id="aef55-192">If an import cannot be fulfilled, the composition of that part will fail and the part will not be available.</span></span>

<span data-ttu-id="aef55-193">*プロパティを使用すると、インポートを* 省略可能 `AllowDefault` として指定できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-193">You can specify that an import is *optional* by using the `AllowDefault` property.</span></span> <span data-ttu-id="aef55-194">この場合、インポートに一致するエクスポートがなくても合成が成功し、インポート側のプロパティがそのプロパティ型の既定値に設定されます (オブジェクト プロパティの場合は `null`、ブール型プロパティの場合は `false`、数値プロパティの場合は 0)。次のクラスは省略可能インポートを使用しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-194">In this case, the composition will succeed even if the import does not match any available exports, and the importing property will be set to the default for its property type (`null` for object properties, `false` for Booleans, or zero for numeric properties.) The following class uses an optional import.</span></span>

```vb
Public Class MyClass1

    <Import(AllowDefault:=True)>
    Public Property thePlugin As Plugin

    'If no matching export is available,
    'thePlugin will be set to null.
End Class
```

```csharp
public class MyClass
{
    [Import(AllowDefault = true)]
    public Plugin thePlugin { get; set; }

    //If no matching export is available,
    //thePlugin will be set to null.
}
```

### <a name="importing-multiple-objects"></a><span data-ttu-id="aef55-195">複数のオブジェクトのインポート</span><span class="sxs-lookup"><span data-stu-id="aef55-195">Importing Multiple Objects</span></span>

<span data-ttu-id="aef55-196">`Import` 属性が正しく合成されるのは、1 つのエクスポートのみと一致する場合だけです。</span><span class="sxs-lookup"><span data-stu-id="aef55-196">The `Import` attribute will only be successfully composed when it matches one and only one export.</span></span> <span data-ttu-id="aef55-197">それ以外の場合は合成エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-197">Other cases will produce a composition error.</span></span> <span data-ttu-id="aef55-198">同じコントラクトに一致する複数のエクスポートをインポートするには、 `ImportMany` 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="aef55-198">To import more than one export that matches the same contract, use the `ImportMany` attribute.</span></span> <span data-ttu-id="aef55-199">この属性でマークされているインポートは常に省略可能です。</span><span class="sxs-lookup"><span data-stu-id="aef55-199">Imports marked with this attribute are always optional.</span></span> <span data-ttu-id="aef55-200">たとえば、一致するエクスポートが存在しなくても合成は失敗しません。</span><span class="sxs-lookup"><span data-stu-id="aef55-200">For example, composition will not fail if no matching exports are present.</span></span> <span data-ttu-id="aef55-201">次のクラスは、 `IMyAddin`型の任意の数のエクスポートをインポートします。</span><span class="sxs-lookup"><span data-stu-id="aef55-201">The following class imports any number of exports of type `IMyAddin`.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of IMyAddin)

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<IMyAddin> MyAddin { get; set; }
}
```

<span data-ttu-id="aef55-202">インポートされた配列にアクセスするには、通常の `IEnumerable<T>` の構文とメソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="aef55-202">The imported array can be accessed by using ordinary `IEnumerable<T>` syntax and methods.</span></span> <span data-ttu-id="aef55-203">通常の配列 (`IMyAddin[]`) を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="aef55-203">It is also possible to use an ordinary array (`IMyAddin[]`) instead.</span></span>

<span data-ttu-id="aef55-204">このパターンは、 `Lazy<T>` 構文と組み合わせて使用する場合に非常に重要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-204">This pattern can be very important when you use it in combination with the `Lazy<T>` syntax.</span></span> <span data-ttu-id="aef55-205">たとえば、 `ImportMany`、 `IEnumerable<T>`、および `Lazy<T>`を使用すると、任意の数のオブジェクトへの間接参照をインポートして、必要になったものだけをインスタンス化できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-205">For example, by using `ImportMany`, `IEnumerable<T>`, and `Lazy<T>`, you can import indirect references to any number of objects and only instantiate the ones that become necessary.</span></span> <span data-ttu-id="aef55-206">次のクラスはこのパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-206">The following class shows this pattern.</span></span>

```vb
Public Class MyClass1

    <ImportMany()>
    Public Property MyAddin As IEnumerable(Of Lazy(Of IMyAddin))

End Class
```

```csharp
public class MyClass
{
    [ImportMany]
    public IEnumerable<Lazy<IMyAddin>> MyAddin { get; set; }
}
```

<a name="avoiding_discovery"></a>

## <a name="avoiding-discovery"></a><span data-ttu-id="aef55-207">検出の回避</span><span class="sxs-lookup"><span data-stu-id="aef55-207">Avoiding Discovery</span></span>

<span data-ttu-id="aef55-208">パートがカタログの一部として検出されないようにしたい場合があります</span><span class="sxs-lookup"><span data-stu-id="aef55-208">In some cases, you may want to prevent a part from being discovered as part of a catalog.</span></span> <span data-ttu-id="aef55-209">(パートが、使用ではなく継承を目的とする基底クラスである場合など)。</span><span class="sxs-lookup"><span data-stu-id="aef55-209">For example, the part may be a base class intended to be inherited from, but not used.</span></span> <span data-ttu-id="aef55-210">これを実現するには 2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-210">There are two ways to accomplish this.</span></span> <span data-ttu-id="aef55-211">最初の方法は、パート クラスで `abstract` キーワードを使用する方法です。</span><span class="sxs-lookup"><span data-stu-id="aef55-211">First, you can use the `abstract` keyword on the part class.</span></span> <span data-ttu-id="aef55-212">抽象クラスではエクスポートは提供されませんが、その抽象クラスから派生するクラスに、継承されたエクスポートが提供されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-212">Abstract classes never provide exports, although they can provide inherited exports to classes that derive from them.</span></span>

<span data-ttu-id="aef55-213">クラスを抽象クラスにできない場合は、 `PartNotDiscoverable` 属性で装飾できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-213">If the class cannot be made abstract, you can decorate it with the `PartNotDiscoverable` attribute.</span></span> <span data-ttu-id="aef55-214">この属性で装飾されたパートは、カタログに含まれません。</span><span class="sxs-lookup"><span data-stu-id="aef55-214">A part decorated with this attribute will not be included in any catalogs.</span></span> <span data-ttu-id="aef55-215">次の例は、これらのパターンを示しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-215">The following example demonstrates these patterns.</span></span> <span data-ttu-id="aef55-216">`DataOne` は、カタログによって検出されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-216">`DataOne` will be discovered by the catalog.</span></span> <span data-ttu-id="aef55-217">`DataTwo` は、抽象クラスであるため検出されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-217">Since `DataTwo` is abstract, it will not be discovered.</span></span> <span data-ttu-id="aef55-218">`DataThree` は、 `PartNotDiscoverable` 属性を使用しているため検出されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-218">Since `DataThree` used the `PartNotDiscoverable` attribute, it will not be discovered.</span></span>

```vb
<Export()>
Public Class DataOne
    'This part will be discovered
    'as normal by the catalog.
End Class

<Export()>
Public MustInherit Class DataTwo
    'This part will not be discovered
    'by the catalog.
End Class

<PartNotDiscoverable()>
<Export()>
Public Class DataThree
    'This part will also not be discovered
    'by the catalog.
End Class
```

```csharp
[Export]
public class DataOne
{
    //This part will be discovered
    //as normal by the catalog.
}

[Export]
public abstract class DataTwo
{
    //This part will not be discovered
    //by the catalog.
}

[PartNotDiscoverable]
[Export]
public class DataThree
{
    //This part will also not be discovered
    //by the catalog.
}
```

<a name="metadata_and_metadata_views"></a>

## <a name="metadata-and-metadata-views"></a><span data-ttu-id="aef55-219">メタデータとメタデータ ビュー</span><span class="sxs-lookup"><span data-stu-id="aef55-219">Metadata and Metadata Views</span></span>

<span data-ttu-id="aef55-220">エクスポートでは、 *メタデータ*と呼ばれる自身に関する追加情報を提供できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-220">Exports can provide additional information about themselves known as *metadata*.</span></span> <span data-ttu-id="aef55-221">メタデータを使用すると、エクスポートされるオブジェクトのプロパティをインポート側のパートに伝えることができます。</span><span class="sxs-lookup"><span data-stu-id="aef55-221">Metadata can be used to convey properties of the exported object to the importing part.</span></span> <span data-ttu-id="aef55-222">インポート側のパートでは、そのデータを使用して、使用するエクスポートを決定したり、エクスポートを構築せずにその情報を収集したりできます。</span><span class="sxs-lookup"><span data-stu-id="aef55-222">The importing part can use this data to decide which exports to use, or to gather information about an export without having to construct it.</span></span> <span data-ttu-id="aef55-223">そのため、メタデータを使用するインポートは、遅延インポートである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-223">For this reason, an import must be lazy to use metadata.</span></span>

<span data-ttu-id="aef55-224">メタデータを使用するには、 *メタデータ ビュー*と呼ばれるインターフェイスを宣言して、使用できるようにするメタデータを宣言するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="aef55-224">To use metadata, you typically declare an interface known as a *metadata view*, which declares what metadata will be available.</span></span> <span data-ttu-id="aef55-225">メタデータ ビュー インターフェイスには、それぞれが `get` アクセサーを持つプロパティのみを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-225">The metadata view interface must have only properties, and those properties must have `get` accessors.</span></span> <span data-ttu-id="aef55-226">次のインターフェイスはメタデータ ビューの例です。</span><span class="sxs-lookup"><span data-stu-id="aef55-226">The following interface is an example metadata view.</span></span>

```vb
Public Interface IPluginMetadata

    ReadOnly Property Name As String

    <DefaultValue(1)>
    ReadOnly Property Version As Integer

End Interface
```

```csharp
public interface IPluginMetadata
{
    string Name { get; }

    [DefaultValue(1)]
    int Version { get; }
}
```

<span data-ttu-id="aef55-227">ジェネリック コレクションの `IDictionary<string, object>`をメタデータ ビューとして使用することもできますが、型チェックの利点がなくなるため、使用しないことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="aef55-227">It is also possible to use a generic collection, `IDictionary<string, object>`, as a metadata view, but this forfeits the benefits of type checking and should be avoided.</span></span>

<span data-ttu-id="aef55-228">通常は、メタデータ ビューに含まれているすべてのプロパティが必要になり、それらを提供していないエクスポートは一致と見なされませんが、</span><span class="sxs-lookup"><span data-stu-id="aef55-228">Ordinarily, all of the properties named in the metadata view are required, and any exports that do not provide them will not be considered a match.</span></span> <span data-ttu-id="aef55-229">`DefaultValue` 属性を指定すると、プロパティを省略可能にすることができます。</span><span class="sxs-lookup"><span data-stu-id="aef55-229">The `DefaultValue` attribute specifies that a property is optional.</span></span> <span data-ttu-id="aef55-230">この場合、そのプロパティが含まれていないと、 `DefaultValue`のパラメーターとして指定した既定値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="aef55-230">If the property is not included, it will be assigned the default value specified as a parameter of `DefaultValue`.</span></span> <span data-ttu-id="aef55-231">次の例は、メタデータで装飾された 2 つの異なるクラスです。</span><span class="sxs-lookup"><span data-stu-id="aef55-231">The following are two different classes decorated with metadata.</span></span> <span data-ttu-id="aef55-232">これらのクラスは、どちらも前のメタデータ ビューと一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-232">Both of these classes would match the previous metadata view.</span></span>

```vb
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class MyLogger
    Implements IPlugin

End Class

'Version is not required because of the DefaultValue
<Export(GetType(IPlugin))>
<ExportMetadata("Name", "Disk Writer")>
Public Class DWriter
    Implements IPlugin

End Class
```

```csharp
[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
}

[Export(typeof(IPlugin)),
    ExportMetadata("Name", "Disk Writer")]
    //Version is not required because of the DefaultValue
public class DWriter : IPlugin
{
}
```

<span data-ttu-id="aef55-233">メタデータは、 `Export` 属性の後に `ExportMetadata` 属性を使用して指定します。</span><span class="sxs-lookup"><span data-stu-id="aef55-233">Metadata is expressed after the `Export` attribute by using the `ExportMetadata` attribute.</span></span> <span data-ttu-id="aef55-234">各メタデータは名前/値のペアで構成され、</span><span class="sxs-lookup"><span data-stu-id="aef55-234">Each piece of metadata is composed of a name/value pair.</span></span> <span data-ttu-id="aef55-235">メタデータの名前の部分が、メタデータ ビューの対応するプロパティの名前と一致する必要があります。一致した場合は、メタデータの値がそのプロパティに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="aef55-235">The name portion of the metadata must match the name of the appropriate property in the metadata view, and the value will be assigned to that property.</span></span>

<span data-ttu-id="aef55-236">使用するメタデータ ビューを指定するのはインポーターです。</span><span class="sxs-lookup"><span data-stu-id="aef55-236">It is the importer that specifies what metadata view, if any, will be in use.</span></span> <span data-ttu-id="aef55-237">メタデータを含むインポートは遅延インポートとして宣言され、 `Lazy<T,T>`の 2 番目の型パラメーターとしてメタデータ インターフェイスが指定されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-237">An import with metadata is declared as a lazy import, with the metadata interface as the second type parameter to `Lazy<T,T>`.</span></span> <span data-ttu-id="aef55-238">次のクラスは、前のパートをメタデータと共にインポートします。</span><span class="sxs-lookup"><span data-stu-id="aef55-238">The following class imports the previous part with metadata.</span></span>

```vb
Public Class Addin

    <Import()>
    Public Property plugin As Lazy(Of IPlugin, IPluginMetadata)
End Class
```

```csharp
public class Addin
{
    [Import]
    public Lazy<IPlugin, IPluginMetadata> plugin;
}
```

<span data-ttu-id="aef55-239">メタデータは、多くの場合、 `ImportMany` 属性と組み合わせて使用されます。これにより、使用可能なインポートを解析して 1 つのインポートだけを選択してインスタンス化したり、コレクションをフィルター処理して特定の条件に一致するものを抽出したりできます。</span><span class="sxs-lookup"><span data-stu-id="aef55-239">In many cases, you will want to combine metadata with the `ImportMany` attribute, in order to parse through the available imports and choose and instantiate only one, or filter a collection to match a certain condition.</span></span> <span data-ttu-id="aef55-240">次のクラスでは、 `IPlugin` の値が "Logger" である `Name` オブジェクトのみをインスタンス化しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-240">The following class instantiates only `IPlugin` objects that have the `Name` value "Logger".</span></span>

```vb
Public Class User

    <ImportMany()>
    Public Property plugins As IEnumerable(Of Lazy(Of IPlugin, IPluginMetadata))

    Public Function InstantiateLogger() As IPlugin

        Dim logger As IPlugin
        logger = Nothing

        For Each Plugin As Lazy(Of IPlugin, IPluginMetadata) In plugins
            If Plugin.Metadata.Name = "Logger" Then
                logger = Plugin.Value
            End If
        Next
        Return logger
    End Function

End Class
```

```csharp
public class User
{
    [ImportMany]
    public IEnumerable<Lazy<IPlugin, IPluginMetadata>> plugins;

    public IPlugin InstantiateLogger()
    {
        IPlugin logger = null;

        foreach (Lazy<IPlugin, IPluginMetadata> plugin in plugins)
        {
            if (plugin.Metadata.Name == "Logger")
                logger = plugin.Value;
        }
        return logger;
    }
}
```

<a name="import_and_export_inheritance"></a>

## <a name="import-and-export-inheritance"></a><span data-ttu-id="aef55-241">インポートとエクスポートの継承</span><span class="sxs-lookup"><span data-stu-id="aef55-241">Import and Export Inheritance</span></span>

<span data-ttu-id="aef55-242">クラスがパートを継承する場合、そのクラスもパートになることがあります。</span><span class="sxs-lookup"><span data-stu-id="aef55-242">If a class inherits from a part, that class may also become a part.</span></span> <span data-ttu-id="aef55-243">インポートは常にサブクラスに継承されるため、</span><span class="sxs-lookup"><span data-stu-id="aef55-243">Imports are always inherited by subclasses.</span></span> <span data-ttu-id="aef55-244">パートのサブクラスは常に、同じインポートを親クラスとするパートになります。</span><span class="sxs-lookup"><span data-stu-id="aef55-244">Therefore, a subclass of a part will always be a part, with the same imports as its parent class.</span></span>

<span data-ttu-id="aef55-245">`Export` 属性を使用して宣言したエクスポートは、サブクラスに継承されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-245">Exports declared by using the `Export` attribute are not inherited by subclasses.</span></span> <span data-ttu-id="aef55-246">ただし、 `InheritedExport` 属性を使用すると、パート自体をエクスポートできます。</span><span class="sxs-lookup"><span data-stu-id="aef55-246">However, a part can export itself by using the `InheritedExport` attribute.</span></span> <span data-ttu-id="aef55-247">この場合、そのパートのサブクラスは、コントラクト名およびコントラクト型を含め、同じエクスポートを継承して提供します。</span><span class="sxs-lookup"><span data-stu-id="aef55-247">Subclasses of the part will inherit and provide the same export, including contract name and contract type.</span></span> <span data-ttu-id="aef55-248">`Export` は、 `InheritedExport` 属性とは違って、適用できるのはクラス レベルだけであり、メンバー レベルでは適用できません。</span><span class="sxs-lookup"><span data-stu-id="aef55-248">Unlike an `Export` attribute, `InheritedExport` can be applied only at the class level, and not at the member level.</span></span> <span data-ttu-id="aef55-249">したがって、メンバー レベルのエクスポートを継承することはできません。</span><span class="sxs-lookup"><span data-stu-id="aef55-249">Therefore, member-level exports can never be inherited.</span></span>

<span data-ttu-id="aef55-250">次の 4 つのクラスは、インポートとエクスポートの継承の基本原則を示しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-250">The following four classes demonstrate the principles of import and export inheritance.</span></span> <span data-ttu-id="aef55-251">`NumTwo` は `NumOne`を継承するため、 `NumTwo` は `IMyData`をインポートします。</span><span class="sxs-lookup"><span data-stu-id="aef55-251">`NumTwo` inherits from `NumOne`, so `NumTwo` will import `IMyData`.</span></span> <span data-ttu-id="aef55-252">通常のエクスポートは継承されないため、 `NumTwo` は何もエクスポートしません。</span><span class="sxs-lookup"><span data-stu-id="aef55-252">Ordinary exports are not inherited, so `NumTwo` will not export anything.</span></span> <span data-ttu-id="aef55-253">`NumFour` は `NumThree`を継承します。</span><span class="sxs-lookup"><span data-stu-id="aef55-253">`NumFour` inherits from `NumThree`.</span></span> <span data-ttu-id="aef55-254">`NumThree` では `InheritedExport`が使用されているため、 `NumFour` には、コントラクト型が `NumThree`の 1 つのエクスポートがあります。</span><span class="sxs-lookup"><span data-stu-id="aef55-254">Because `NumThree` used `InheritedExport`, `NumFour` has one export with contract type `NumThree`.</span></span> <span data-ttu-id="aef55-255">メンバー レベルのエクスポートは継承されないため、 `IMyData` はエクスポートされません。</span><span class="sxs-lookup"><span data-stu-id="aef55-255">Member-level exports are never inherited, so `IMyData` is not exported.</span></span>

```vb
<Export()>
Public Class NumOne
    <Import()>
    Public Property MyData As IMyData
End Class

Public Class NumTwo
    Inherits NumOne

    'Imports are always inherited, so NumTwo will
    'Import IMyData

    'Ordinary exports are not inherited, so
    'NumTwo will NOT export anything.  As a result it
    'will not be discovered by the catalog!

End Class

<InheritedExport()>
Public Class NumThree

    <Export()>
    Public Property MyData As IMyData

    'This part provides two exports, one of
    'contract type NumThree, and one of
    'contract type IMyData.

End Class

Public Class NumFour
    Inherits NumThree

    'Because NumThree used InheritedExport,
    'this part has one export with contract
    'type NumThree.

    'Member-level exports are never inherited,
    'so IMyData is not exported.

End Class
```

```csharp
[Export]
public class NumOne
{
    [Import]
    public IMyData MyData { get; set; }
}

public class NumTwo : NumOne
{
    //Imports are always inherited, so NumTwo will
    //import IMyData.

    //Ordinary exports are not inherited, so
    //NumTwo will NOT export anything. As a result it
    //will not be discovered by the catalog!
}

[InheritedExport]
public class NumThree
{
    [Export]
    Public IMyData MyData { get; set; }

    //This part provides two exports, one of
    //contract type NumThree, and one of
    //contract type IMyData.
}

public class NumFour : NumThree
{
    //Because NumThree used InheritedExport,
    //this part has one export with contract
    //type NumThree.

    //Member-level exports are never inherited,
    //so IMyData is not exported.
}
```

<span data-ttu-id="aef55-256">`InheritedExport` 属性にメタデータが関連付けられている場合は、そのメタデータも継承されます</span><span class="sxs-lookup"><span data-stu-id="aef55-256">If there is metadata associated with an `InheritedExport` attribute, that metadata will also be inherited.</span></span> <span data-ttu-id="aef55-257">(詳細については、前の「メタデータとメタデータ ビュー」を参照してください)。継承されたメタデータをサブクラスで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="aef55-257">(For more information, see the earlier "Metadata and Metadata Views" section.) Inherited metadata cannot be modified by the subclass.</span></span> <span data-ttu-id="aef55-258">ただし、同じコントラクト名およびコントラクト型と新しいメタデータを使用して `InheritedExport` 属性を再宣言すると、継承されたメタデータをサブクラスで新しいメタデータに置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="aef55-258">However, by re-declaring the `InheritedExport` attribute with the same contract name and contract type, but with new metadata, the subclass can replace the inherited metadata with new metadata.</span></span> <span data-ttu-id="aef55-259">次のクラスはこの基本原則を示しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-259">The following class demonstrates this principle.</span></span> <span data-ttu-id="aef55-260">ここでは、 `MegaLogger` を継承する `Logger` パートに `InheritedExport` 属性が含まれています。</span><span class="sxs-lookup"><span data-stu-id="aef55-260">The `MegaLogger` part inherits from `Logger` and includes the `InheritedExport` attribute.</span></span> <span data-ttu-id="aef55-261">`MegaLogger` で Status という新しいメタデータが再宣言されているため、 `Logger`のメタデータの Name と Version は継承されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-261">Since `MegaLogger` re-declares new metadata named Status, it does not inherit the Name and Version metadata from `Logger`.</span></span>

```vb
<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Name", "Logger")>
<ExportMetadata("Version", 4)>
Public Class Logger
    Implements IPlugin

    'Exports with contract type IPlugin
    'and metadata "Name" and "Version".
End Class

Public Class SuperLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Name" and "Version", exactly the same
    'as the Logger class.

End Class

<InheritedExport(GetType(IPlugin))>
<ExportMetadata("Status", "Green")>
Public Class MegaLogger
    Inherits Logger

    'Exports with contract type IPlugin and
    'metadata "Status" only. Re-declaring
    'the attribute replaces all metadata.

End Class
```

```csharp
[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Name", "Logger"),
    ExportMetadata("Version", 4)]
public class Logger : IPlugin
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version".
}

public class SuperLogger : Logger
{
    //Exports with contract type IPlugin and
    //metadata "Name" and "Version", exactly the same
    //as the Logger class.
}

[InheritedExport(typeof(IPlugin)),
    ExportMetadata("Status", "Green")]
public class MegaLogger : Logger        {
    //Exports with contract type IPlugin and
    //metadata "Status" only. Re-declaring
    //the attribute replaces all metadata.
}
```

<span data-ttu-id="aef55-262">`InheritedExport` 属性を再宣言してメタデータをオーバーライドする際は、コントラクト型が同じであることを確認してください</span><span class="sxs-lookup"><span data-stu-id="aef55-262">When re-declaring the `InheritedExport` attribute to override metadata, make sure that the contract types are the same.</span></span> <span data-ttu-id="aef55-263">(上の例では、`IPlugin` がコントラクト型です)。コントラクト型が違っていると、メタデータがオーバーライドされる代わりに、2 つ目の属性によって別の 2 つ目のエクスポートが作成されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-263">(In the previous example, `IPlugin` is the contract type.) If they differ, instead of overriding, the second attribute will create a second, independent export from the part.</span></span> <span data-ttu-id="aef55-264">したがって、 `InheritedExport` 属性をオーバーライドする際は、一般に、上の例のようにコントラクト型を明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-264">Generally, this means that you will have to explicitly specify the contract type when you override an `InheritedExport` attribute, as shown in the previous example.</span></span>

<span data-ttu-id="aef55-265">インターフェイスは直接インスタンス化できないため、通常は `Export` 属性や `Import` 属性で装飾できませんが、</span><span class="sxs-lookup"><span data-stu-id="aef55-265">Since interfaces cannot be instantiated directly, they generally cannot be decorated with `Export` or `Import` attributes.</span></span> <span data-ttu-id="aef55-266">インターフェイス レベルで `InheritedExport` 属性を使用すると、インターフェイスを装飾できます。この場合、そのエクスポートは、関連付けられているメタデータと共に、そのインターフェイスを実装するすべてのクラスに継承されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-266">However, an interface can be decorated with an `InheritedExport` attribute at the interface level, and that export along with any associated metadata will be inherited by any implementing classes.</span></span> <span data-ttu-id="aef55-267">ただし、そのインターフェイス自体をパートとして使用できるようにはなりません。</span><span class="sxs-lookup"><span data-stu-id="aef55-267">The interface itself will not be available as a part, however.</span></span>

<a name="custom_export_attributes"></a>

## <a name="custom-export-attributes"></a><span data-ttu-id="aef55-268">カスタム エクスポート属性</span><span class="sxs-lookup"><span data-stu-id="aef55-268">Custom Export Attributes</span></span>

<span data-ttu-id="aef55-269">基本エクスポート属性の `Export` および `InheritedExport`を拡張して、メタデータを属性プロパティとして含めることができます。</span><span class="sxs-lookup"><span data-stu-id="aef55-269">The basic export attributes, `Export` and `InheritedExport`, can be extended to include metadata as attribute properties.</span></span> <span data-ttu-id="aef55-270">この手法は、多数のパートに同じようなメタデータを適用したり、メタデータ属性の継承ツリーを作成したりするのに便利です。</span><span class="sxs-lookup"><span data-stu-id="aef55-270">This technique is useful for applying similar metadata to many parts, or creating an inheritance tree of metadata attributes.</span></span>

<span data-ttu-id="aef55-271">カスタム属性では、コントラクト型、コントラクト名、またはその他のメタデータを指定できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-271">A custom attribute can specify the contract type, the contract name, or any other metadata.</span></span> <span data-ttu-id="aef55-272">カスタム属性を定義するには、 `ExportAttribute` (または `InheritedExportAttribute`) を継承するクラスを `MetadataAttribute` 属性で装飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-272">In order to define a custom attribute, a class inheriting from `ExportAttribute` (or `InheritedExportAttribute`) must be decorated with the `MetadataAttribute` attribute.</span></span> <span data-ttu-id="aef55-273">次のクラスはカスタム属性を定義しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-273">The following class defines a custom attribute.</span></span>

```vb
<MetadataAttribute()>
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=false)>
Public Class MyAttribute
    Inherits ExportAttribute

    Public Property MyMetadata As String

    Public Sub New(ByVal myMetadata As String)
        MyBase.New(GetType(IMyAddin))

        myMetadata = myMetadata
    End Sub

End Class
```

```csharp
[MetadataAttribute]
[AttributeUsage(AttributeTargets.Class, AllowMultiple=false)]
public class MyAttribute : ExportAttribute
{
    public MyAttribute(string myMetadata)
        : base(typeof(IMyAddin))
    {
        MyMetadata = myMetadata;
    }

    public string MyMetadata { get; private set; }
}
```

<span data-ttu-id="aef55-274">このクラスは、 `MyAttribute` というコントラクト型と `IMyAddin` というメタデータを含む `MyMetadata`というカスタム属性を定義しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-274">This class defines a custom attribute named `MyAttribute` with contract type `IMyAddin` and some metadata named `MyMetadata`.</span></span> <span data-ttu-id="aef55-275">`MetadataAttribute` 属性でマークされているクラスのすべてのプロパティは、カスタム属性で定義されているメタデータと見なされます</span><span class="sxs-lookup"><span data-stu-id="aef55-275">All properties in a class marked with the `MetadataAttribute` attribute are considered to be metadata defined in the custom attribute.</span></span> <span data-ttu-id="aef55-276">次の 2 つの宣言は等価です。</span><span class="sxs-lookup"><span data-stu-id="aef55-276">The following two declarations are equivalent.</span></span>

```vb
<Export(GetType(IMyAddin))>
<ExportMetadata("MyMetadata", "theData")>
Public Property myAddin As MyAddin
```

```vb
<MyAttribute("theData")>
Public Property myAddin As MyAddin
```

```csharp
[Export(typeof(IMyAddin)),
    ExportMetadata("MyMetadata", "theData")]
public MyAddin myAddin { get; set; }
```

```csharp
[MyAttribute("theData")]
public MyAddin myAddin { get; set; }
```

<span data-ttu-id="aef55-277">1 つ目の宣言では、コントラクト型とメタデータが明示的に定義されています。</span><span class="sxs-lookup"><span data-stu-id="aef55-277">In the first declaration, the contract type and metadata are explicitly defined.</span></span> <span data-ttu-id="aef55-278">2 つ目の宣言では、コントラクト型とメタデータがカスタム属性で暗黙的に定義されています。</span><span class="sxs-lookup"><span data-stu-id="aef55-278">In the second declaration, the contract type and metadata are implicit in the customized attribute.</span></span> <span data-ttu-id="aef55-279">カスタム属性を使用すると、特に、多数のパートに同じ大量のメタデータを適用する必要がある場合 (著者情報や著作権情報の場合など) には、多くの時間を節約し、作業の繰り返しを削減できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-279">Particularly in cases where a large amount of identical metadata must be applied to many parts (for example, author or copyright information), using a custom attribute can save a lot of time and duplication.</span></span> <span data-ttu-id="aef55-280">さらに、カスタム属性の継承ツリーを作成して、バリエーションに対応できるようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="aef55-280">Further, inheritance trees of custom attributes can be created to allow for variations.</span></span>

<span data-ttu-id="aef55-281">カスタム属性で省略可能なメタデータを作成するには、 `DefaultValue` 属性を使用します。</span><span class="sxs-lookup"><span data-stu-id="aef55-281">To create optional metadata in a custom attribute, you can use the `DefaultValue` attribute.</span></span> <span data-ttu-id="aef55-282">この属性をカスタム属性クラスのプロパティに適用すると、そのプロパティが省略可能に指定され、エクスポーターによって指定される必要がなくなります。</span><span class="sxs-lookup"><span data-stu-id="aef55-282">When this attribute is applied to a property in a custom attribute class, it specifies that the decorated property is optional and does not have to be supplied by an exporter.</span></span> <span data-ttu-id="aef55-283">値が指定されていない場合は、そのプロパティ型の既定値 (通常は、 `null`、 `false`、または 0) が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="aef55-283">If a value for the property is not supplied, it will be assigned the default value for its property type (usually `null`, `false`, or 0.)</span></span>

<a name="creation_policies"></a>

## <a name="creation-policies"></a><span data-ttu-id="aef55-284">作成ポリシー</span><span class="sxs-lookup"><span data-stu-id="aef55-284">Creation Policies</span></span>

<span data-ttu-id="aef55-285">パートでインポートが指定され、合成が実行される場合、合成コンテナーは、一致するエクスポートを検索します。</span><span class="sxs-lookup"><span data-stu-id="aef55-285">When a part specifies an import and composition is performed, the composition container attempts to find a matching export.</span></span> <span data-ttu-id="aef55-286">インポートと一致するエクスポートが見つかった場合は、インポート側のメンバーが、エクスポートされるオブジェクトのインスタンスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-286">If it matches the import with an export successfully, the importing member is set to an instance of the exported object.</span></span> <span data-ttu-id="aef55-287">このインスタンスがどこから取得されるかは、エクスポート側のパートの *作成ポリシー*によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-287">Where this instance comes from is controlled by the exporting part's *creation policy*.</span></span>

<span data-ttu-id="aef55-288">作成ポリシーには、 *共有* と *非共有*の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-288">The two possible creation policies are *shared* and *non-shared*.</span></span> <span data-ttu-id="aef55-289">共有の作成ポリシーを持つパートは、そのコントラクトを持つパートのコンテナー内のすべてのインポートの間で共有されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-289">A part with a creation policy of shared will be shared between every import in the container for a part with that contract.</span></span> <span data-ttu-id="aef55-290">合成エンジンで一致が検出され、インポート側のプロパティが設定される場合は、そのパートがまだ存在しないときにのみ新しいコピーがインスタンス化され、それ以外のときは既存のコピーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-290">When the composition engine finds a match and has to set an importing property, it will instantiate a new copy of the part only if one does not already exist; otherwise, it will supply the existing copy.</span></span> <span data-ttu-id="aef55-291">したがって、多数のオブジェクトが同じパートを参照する場合もあります。</span><span class="sxs-lookup"><span data-stu-id="aef55-291">This means that many objects may have references to the same part.</span></span> <span data-ttu-id="aef55-292">このポリシーは、場所によって変化する可能性がある内部状態に依存するパートに対しては使用できません。</span><span class="sxs-lookup"><span data-stu-id="aef55-292">Such parts should not rely on internal state that might be changed from many places.</span></span> <span data-ttu-id="aef55-293">このポリシーは、静的なパート、サービスを提供するパート、メモリやその他のリソースを大量に消費するパートに適しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-293">This policy is appropriate for static parts, parts that provide services, and parts that consume a lot of memory or other resources.</span></span>

<span data-ttu-id="aef55-294">非共有の作成ポリシーを持つパートは、そのいずれかのエクスポートと一致するインポートが検出されるたびに作成されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-294">A part with the creation policy of non-shared will be created every time a matching import for one of its exports is found.</span></span> <span data-ttu-id="aef55-295">したがって、パートのエクスポートされたコントラクトのいずれかに一致するコンテナー内のすべてのインポートに対して新しいコピーがインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-295">A new copy will therefore be instantiated for every import in the container that matches one of the part's exported contracts.</span></span> <span data-ttu-id="aef55-296">それらのコピーの内部状態は共有されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-296">The internal state of these copies will not be shared.</span></span> <span data-ttu-id="aef55-297">このポリシーは、各インポートに固有の内部状態が必要なパートに適しています。</span><span class="sxs-lookup"><span data-stu-id="aef55-297">This policy is appropriate for parts where each import requires its own internal state.</span></span>

<span data-ttu-id="aef55-298">パートの作成ポリシーは、インポートとエクスポートの両方で指定できます。値は、 `Shared`、 `NonShared`、または `Any`の中から選択できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-298">Both the import and the export can specify the creation policy of a part, from among the values `Shared`, `NonShared`, or `Any`.</span></span> <span data-ttu-id="aef55-299">既定値は、インポートもエクスポートも `Any` です。</span><span class="sxs-lookup"><span data-stu-id="aef55-299">The default is `Any` for both imports and exports.</span></span> <span data-ttu-id="aef55-300">`Shared` または `NonShared` が指定されているエクスポートは、同じ値か `Any`が指定されているインポートとのみ一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-300">An export that specifies `Shared` or `NonShared` will only match an import that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="aef55-301">同様に、 `Shared` または `NonShared` が指定されているインポートは、同じ値か `Any`が指定されているエクスポートとのみ一致します。</span><span class="sxs-lookup"><span data-stu-id="aef55-301">Similarly, an import that specifies `Shared` or `NonShared` will only match an export that specifies the same, or that specifies `Any`.</span></span> <span data-ttu-id="aef55-302">互換性のない作成ポリシーを持つインポートとエクスポートは、コントラクト名やコントラクト型が一致しない場合と同様に、一致とは見なされません。</span><span class="sxs-lookup"><span data-stu-id="aef55-302">Imports and exports with incompatible creation policies are not considered a match, in the same way as an import and export whose contract name or contract type are not a match.</span></span> <span data-ttu-id="aef55-303">インポートとエクスポートの両方で `Any`が指定されている場合、および作成ポリシーが指定されていないために既定値の `Any`が使用される場合は、既定で共有の作成ポリシーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-303">If both import and export specify `Any`, or do not specify a creation policy and default to `Any`, the creation policy will default to shared.</span></span>

<span data-ttu-id="aef55-304">次の例では、インポートとエクスポートの両方で作成ポリシーが指定されています。</span><span class="sxs-lookup"><span data-stu-id="aef55-304">The following example shows both imports and exports specifying creation policies.</span></span> <span data-ttu-id="aef55-305">`PartOne` では作成ポリシーが指定されていないため、既定値の `Any`が使用されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-305">`PartOne` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="aef55-306">`PartTwo` では作成ポリシーが指定されていないため、既定値の `Any`が使用されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-306">`PartTwo` does not specify a creation policy, so the default is `Any`.</span></span> <span data-ttu-id="aef55-307">インポートとエクスポートの両方で既定値の `Any`が使用されるため、 `PartOne` は共有されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-307">Since both import and export default to `Any`, `PartOne` will be shared.</span></span> <span data-ttu-id="aef55-308">`PartThree` では `Shared` の作成ポリシーが指定されているため、 `PartTwo` と `PartThree` は `PartOne`の同じコピーを共有します。</span><span class="sxs-lookup"><span data-stu-id="aef55-308">`PartThree` specifies a `Shared` creation policy, so `PartTwo` and `PartThree` will share the same copy of `PartOne`.</span></span> <span data-ttu-id="aef55-309">`PartFour` では `NonShared` の作成ポリシーが指定されているため、 `PartFour` は `PartFive`で共有されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-309">`PartFour` specifies a `NonShared` creation policy, so `PartFour` will be non-shared in `PartFive`.</span></span> <span data-ttu-id="aef55-310">`PartSix` では `NonShared` の作成ポリシーが指定されているため、</span><span class="sxs-lookup"><span data-stu-id="aef55-310">`PartSix` specifies a `NonShared` creation policy.</span></span> <span data-ttu-id="aef55-311">`PartFive` と `PartSix` は、どちらも `PartFour`とは別のコピーを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="aef55-311">`PartFive` and `PartSix` will each receive separate copies of `PartFour`.</span></span> <span data-ttu-id="aef55-312">`PartSeven` では `Shared` の作成ポリシーが指定されているため、</span><span class="sxs-lookup"><span data-stu-id="aef55-312">`PartSeven` specifies a `Shared` creation policy.</span></span> <span data-ttu-id="aef55-313">`PartFour` の作成ポリシーを持つ `Shared`はエクスポートされていないため、 `PartSeven` のインポートは一致が検出されず、満たされません。</span><span class="sxs-lookup"><span data-stu-id="aef55-313">Because there is no exported `PartFour` with a creation policy of `Shared`, the `PartSeven` import does not match anything and will not be filled.</span></span>

```vb
<Export()>
Public Class PartOne
    'The default creation policy for an export is Any.
End Class

Public Class PartTwo

    <Import()>
    Public Property partOne As PartOne

    'The default creation policy for an import is Any.
    'If both policies are Any, the part will be shared.

End Class

Public Class PartThree

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partOne As PartOne

    'The Shared creation policy is explicitly specified.
    'PartTwo and PartThree will receive references to the
    'SAME copy of PartOne.

End Class

<Export()>
<PartCreationPolicy(CreationPolicy.NonShared)>
Public Class PartFour
    'The NonShared creation policy is explicitly specified.
End Class

Public Class PartFive

    <Import()>
    Public Property partFour As PartFour

    'The default creation policy for an import is Any.
    'Since the export's creation policy was explicitly
    'defined, the creation policy for this property will
    'be non-shared.

End Class

Public Class PartSix

    <Import(RequiredCreationPolicy:=CreationPolicy.NonShared)>
    Public Property partFour As PartFour

    'Both import and export specify matching creation
    'policies.  PartFive and PartSix will each receive
    'SEPARATE copies of PartFour, each with its own
    'internal state.

End Class

Public Class PartSeven

    <Import(RequiredCreationPolicy:=CreationPolicy.Shared)>
    Public Property partFour As PartFour

    'A creation policy mismatch.  Because there is no
    'exported PartFour with a creation policy of Shared,
    'this import does not match anything and will not be
    'filled.

End Class
```

```csharp
[Export]
public class PartOne
{
    //The default creation policy for an export is Any.
}

public class PartTwo
{
    [Import]
    public PartOne partOne { get; set; }

    //The default creation policy for an import is Any.
    //If both policies are Any, the part will be shared.
}

public class PartThree
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartOne partOne { get; set; }

    //The Shared creation policy is explicitly specified.
    //PartTwo and PartThree will receive references to the
    //SAME copy of PartOne.
}

[Export]
[PartCreationPolicy(CreationPolicy.NonShared)]
public class PartFour
{
    //The NonShared creation policy is explicitly specified.
}

public class PartFive
{
    [Import]
    public PartFour partFour { get; set; }

    //The default creation policy for an import is Any.
    //Since the export's creation policy was explicitly
    //defined, the creation policy for this property will
    //be non-shared.
}

public class PartSix
{
    [Import(RequiredCreationPolicy = CreationPolicy.NonShared)]
    public PartFour partFour { get; set; }

    //Both import and export specify matching creation
    //policies.  PartFive and PartSix will each receive
    //SEPARATE copies of PartFour, each with its own
    //internal state.
}

public class PartSeven
{
    [Import(RequiredCreationPolicy = CreationPolicy.Shared)]
    public PartFour partFour { get; set; }

    //A creation policy mismatch.  Because there is no
    //exported PartFour with a creation policy of Shared,
    //this import does not match anything and will not be
    //filled.
}
```

<a name="life_cycle_and_disposing"></a>

## <a name="life-cycle-and-disposing"></a><span data-ttu-id="aef55-314">ライフ サイクルと破棄</span><span class="sxs-lookup"><span data-stu-id="aef55-314">Life Cycle and Disposing</span></span>

<span data-ttu-id="aef55-315">パートは合成コンテナーでホストされるため、ライフ サイクルが通常のオブジェクトより複雑になることがあります。</span><span class="sxs-lookup"><span data-stu-id="aef55-315">Because parts are hosted in the composition container, their life cycle can be more complex than ordinary objects.</span></span> <span data-ttu-id="aef55-316">パートには、実装できるライフ サイクル関連の重要なインターフェイスが 2 つあります。1 つは `IDisposable` 、もう 1 つは `IPartImportsSatisfiedNotification`です。</span><span class="sxs-lookup"><span data-stu-id="aef55-316">Parts can implement two important life cycle-related interfaces: `IDisposable` and `IPartImportsSatisfiedNotification`.</span></span>

<span data-ttu-id="aef55-317">終了時に作業を実行したりリソースを解放したりする必要があるパートは、通常の .NET Framework オブジェクトのように `IDisposable`を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-317">Parts that require work to be performed at shut down or that need to release resources should implement `IDisposable`, as usual for .NET Framework objects.</span></span> <span data-ttu-id="aef55-318">ただし、パートの作成や参照の管理はコンテナーで行われるため、パートの `Dispose` メソッドを呼び出すのは、そのパートを所有しているコンテナーだけにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-318">However, since the container creates and maintains references to parts, only the container that owns a part should call the `Dispose` method on it.</span></span> <span data-ttu-id="aef55-319">コンテナー自体にも `IDisposable`が実装されており、その `Dispose` のクリーンアップの一部として、所有しているすべてのパートの `Dispose` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-319">The container itself implements `IDisposable`, and as portion of its cleanup in `Dispose` it will call `Dispose` on all the parts that it owns.</span></span> <span data-ttu-id="aef55-320">そのため、合成コンテナーと、その合成コンテナーが所有しているパートが不要になった場合は、合成コンテナーを破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-320">For this reason, you should always dispose the composition container when it and any parts it owns are no longer needed.</span></span>

<span data-ttu-id="aef55-321">有効期間が長い合成コンテナーでは、非共有の作成ポリシーを持つパートによるメモリの消費が問題になることがあります。</span><span class="sxs-lookup"><span data-stu-id="aef55-321">For long-lived composition containers, memory consumption by parts with a creation policy of non-shared can become a problem.</span></span> <span data-ttu-id="aef55-322">これらのパートは共有されないため、何度も作成される可能性がありますが、コンテナー自体が破棄されるまで破棄されません。</span><span class="sxs-lookup"><span data-stu-id="aef55-322">These non-shared parts can be created multiple times and will not be disposed until the container itself is disposed.</span></span> <span data-ttu-id="aef55-323">この問題に対処するため、コンテナーには `ReleaseExport` メソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="aef55-323">To deal with this, the container provides the `ReleaseExport` method.</span></span> <span data-ttu-id="aef55-324">共有されないエクスポートに対してこのメソッドを呼び出すと、そのエクスポートが合成コンテナーから削除されて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-324">Calling this method on a non-shared export removes that export from the composition container and disposes it.</span></span> <span data-ttu-id="aef55-325">削除されるエクスポートによってのみ使用されるパートも、ツリーの下位にあるものも含め、一緒に削除されて破棄されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-325">Parts that are used only by the removed export, and so on down the tree, are also removed and disposed.</span></span> <span data-ttu-id="aef55-326">これにより、合成コンテナー自体を破棄せずにリソースを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="aef55-326">In this way, resources can be reclaimed without disposing the composition container itself.</span></span>

<span data-ttu-id="aef55-327">`IPartImportsSatisfiedNotification` には、 `OnImportsSatisfied`という 1 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="aef55-327">`IPartImportsSatisfiedNotification` contains one method named `OnImportsSatisfied`.</span></span> <span data-ttu-id="aef55-328">このメソッドは、合成コンテナーにより、このインターフェイスを実装するパートに対して、合成が完了してそのパートのインポートを使用できるようになったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-328">This method is called by the composition container on any parts that implement the interface when composition has been completed and the part's imports are ready for use.</span></span> <span data-ttu-id="aef55-329">パートは、他のパートのインポートを満たすために合成エンジンによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="aef55-329">Parts are created by the composition engine to fill the imports of other parts.</span></span> <span data-ttu-id="aef55-330">パートのインポートが設定されるまでは、パートのコンストラクターで、インポートされる値に依存する初期化や、インポートされる値を操作する初期化を実行できません。初期化を実行できるようにするには、 `ImportingConstructor` 属性を使用して、それらの値を必須として指定します。</span><span class="sxs-lookup"><span data-stu-id="aef55-330">Before the imports of a part have been set, you cannot perform any initialization that relies on or manipulates imported values in the part constructor unless those values have been specified as prerequisites by using the `ImportingConstructor` attribute.</span></span> <span data-ttu-id="aef55-331">通常はこの方法が推奨されますが、コンストラクター インジェクションを使用できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="aef55-331">This is normally the preferred method, but in some cases, constructor injection may not be available.</span></span> <span data-ttu-id="aef55-332">そのような場合は、 `OnImportsSatisfied`で初期化を実行できます。この場合は、パートに `IPartImportsSatisfiedNotification`を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aef55-332">In those cases, initialization can be performed in `OnImportsSatisfied`, and the part should implement `IPartImportsSatisfiedNotification`.</span></span>

## <a name="see-also"></a><span data-ttu-id="aef55-333">関連項目</span><span class="sxs-lookup"><span data-stu-id="aef55-333">See also</span></span>

- [<span data-ttu-id="aef55-334">Channel 9 ビデオ:Managed Extensibility Framework を使用してアプリケーションを開く</span><span class="sxs-lookup"><span data-stu-id="aef55-334">Channel 9 Video: Open Up Your Applications with the Managed Extensibility Framework</span></span>](https://channel9.msdn.com/events/TechEd/NorthAmerica/2009/DTL328)
- [<span data-ttu-id="aef55-335">Channel 9 ビデオ:Managed Extensibility Framework (MEF) 2.0</span><span class="sxs-lookup"><span data-stu-id="aef55-335">Channel 9 Video: Managed Extensibility Framework (MEF) 2.0</span></span>](https://channel9.msdn.com/posts/NET-45-Oleg-Lvovitch-and-Kevin-Ransom-Managed-Extensibility-Framework-MEF-20)
