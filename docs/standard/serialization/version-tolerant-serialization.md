---
title: バージョン トレラントなシリアル化
description: .NET Framework 2.0 では、シリアル化可能な型を簡単に変更できるようにする機能のセットであるバージョン トレラントなシリアル化が導入されました。
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: afc822e1f8873bac069f6634fdf1d4665d392e69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762592"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="cba72-103">バージョン トレラントなシリアル化</span><span class="sxs-lookup"><span data-stu-id="cba72-103">Version tolerant serialization</span></span>

<span data-ttu-id="cba72-104">.NET Framework のバージョン 1.0 および 1.1 では、アプリケーションのあるバージョンから次のバージョンに移行しても再利用できる、シリアル化可能な型の作成に問題がありました。</span><span class="sxs-lookup"><span data-stu-id="cba72-104">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="cba72-105">フィールドを追加して型を変更すると、次のような問題が発生していました。</span><span class="sxs-lookup"><span data-stu-id="cba72-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="cba72-106">以前のバージョンのアプリケーションは、古い型の新しいバージョンを逆シリアル化するように要求すると例外をスローする。</span><span class="sxs-lookup"><span data-stu-id="cba72-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="cba72-107">新しいバージョンのアプリケーションは、データが欠落している以前のバージョンの型を逆シリアル化すると例外をスローする。</span><span class="sxs-lookup"><span data-stu-id="cba72-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="cba72-108">バージョン トレラントなシリアル化 (VTS: Version Tolerant Serialization) は、.NET Framework 2.0 で導入された機能セットで、シリアル化可能な型を、長期にわたって簡単に変更できるようにします。</span><span class="sxs-lookup"><span data-stu-id="cba72-108">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="cba72-109">具体的には、VTS 機能が、ジェネリック型を含め、<xref:System.SerializableAttribute> 属性が適用されているクラスに対して有効です。</span><span class="sxs-lookup"><span data-stu-id="cba72-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="cba72-110">VTS を使用すると、他のバージョンの型との互換性を失うことなく、これらのクラスに新しいフィールドを追加できます。</span><span class="sxs-lookup"><span data-stu-id="cba72-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="cba72-111">動作するサンプル アプリケーションについては、「[Version Tolerant Serialization Technology Sample](basic-serialization-technology-sample.md)」(バージョン トレラントなシリアル化テクノロジのサンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cba72-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](basic-serialization-technology-sample.md).</span></span>

<span data-ttu-id="cba72-112">VTS 機能は、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> を使用する場合に有効になります。</span><span class="sxs-lookup"><span data-stu-id="cba72-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="cba72-113">また、<xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> を使用する場合は、外部データの複数バージョン対応機能を除くすべての機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="cba72-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="cba72-114">シリアル化でこれらのクラスを使用する方法の詳細については、「[バイナリ シリアル化](binary-serialization.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cba72-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="cba72-115">機能の一覧</span><span class="sxs-lookup"><span data-stu-id="cba72-115">Feature list</span></span>

<span data-ttu-id="cba72-116">この機能セットの内容は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="cba72-116">The set of features includes the following:</span></span>

- <span data-ttu-id="cba72-117">外部データまたは予期しないデータの複数バージョン対応。</span><span class="sxs-lookup"><span data-stu-id="cba72-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="cba72-118">これにより、型の新しいバージョンから以前のバージョンにデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="cba72-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="cba72-119">欠落しているオプション データの複数バージョン対応。</span><span class="sxs-lookup"><span data-stu-id="cba72-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="cba72-120">これにより、以前のバージョンから新しいバージョンにデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="cba72-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="cba72-121">シリアル化のコールバック。</span><span class="sxs-lookup"><span data-stu-id="cba72-121">Serialization callbacks.</span></span> <span data-ttu-id="cba72-122">これにより、データが欠落している場合に、既定値の高度な設定ができます。</span><span class="sxs-lookup"><span data-stu-id="cba72-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="cba72-123">さらに、オプション フィールドが新たに追加されたときに宣言を生成する機能があります。</span><span class="sxs-lookup"><span data-stu-id="cba72-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="cba72-124">これは、<xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> 属性の <xref:System.Runtime.Serialization.OptionalFieldAttribute> プロパティです。</span><span class="sxs-lookup"><span data-stu-id="cba72-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="cba72-125">これらの機能については、以下のセクションでさらに詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="cba72-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="cba72-126">外部データまたは予期しないデータの複数バージョン対応</span><span class="sxs-lookup"><span data-stu-id="cba72-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="cba72-127">これまで、逆シリアル化中に外部データまたは予期しないデータが検出されると、例外がスローされていました。</span><span class="sxs-lookup"><span data-stu-id="cba72-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="cba72-128">VTS ではこのような場合、例外がスローされるのではなく、外部データまたは予期しないデータがすべて無視されます。</span><span class="sxs-lookup"><span data-stu-id="cba72-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="cba72-129">これにより、新しいバージョンの型 (フィールドが追加されたバージョン) を使用するアプリケーションが、同じ型の以前のバージョンを必要とするアプリケーションに情報を送ることができます。</span><span class="sxs-lookup"><span data-stu-id="cba72-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="cba72-130">次の例では、バージョン 2.0 の `CountryField` クラスの `Address` に含まれる追加データは、以前のアプリケーションで新しいバージョンを逆シリアル化する場合、無視されます。</span><span class="sxs-lookup"><span data-stu-id="cba72-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="cba72-131">欠落しているデータの複数バージョン対応</span><span class="sxs-lookup"><span data-stu-id="cba72-131">Tolerance of missing data</span></span>

<span data-ttu-id="cba72-132"><xref:System.Runtime.Serialization.OptionalFieldAttribute> 属性をフィールドに適用すると、そのフィールドをオプションとしてマークできます。</span><span class="sxs-lookup"><span data-stu-id="cba72-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="cba72-133">逆シリアル化中に、オプション データの欠落が検出されても、シリアル化エンジンはデータが存在しないことを無視し、例外をスローしません。</span><span class="sxs-lookup"><span data-stu-id="cba72-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="cba72-134">そのため、以前のバージョンの型を必要とするアプリケーションから、同じ型の新しいバージョンを必要とするアプリケーションにデータを送信できます。</span><span class="sxs-lookup"><span data-stu-id="cba72-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="cba72-135">バージョン 2.0 の `Address` クラスで、`CountryField` フィールドをオプションとしてマークする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="cba72-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="cba72-136">バージョン 2.0 を必要とする新しいアプリケーションに対して、以前のアプリケーションがバージョン 1 を送信した場合、データが存在しないことは無視されます。</span><span class="sxs-lookup"><span data-stu-id="cba72-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;

    [OptionalField]
    public string CountryField;
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String

    <OptionalField> _
    Public CountryField As String
End Class
```
  
### <a name="serialization-callbacks"></a><span data-ttu-id="cba72-137">シリアル化のコールバック</span><span class="sxs-lookup"><span data-stu-id="cba72-137">Serialization callbacks</span></span>

<span data-ttu-id="cba72-138">シリアル化のコールバックは、次の 4 つの時点でシリアル化プロセスおよび逆シリアル化プロセスにフックする機構です。</span><span class="sxs-lookup"><span data-stu-id="cba72-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="cba72-139">属性</span><span class="sxs-lookup"><span data-stu-id="cba72-139">Attribute</span></span>|<span data-ttu-id="cba72-140">関連するメソッドが呼び出されるタイミング</span><span class="sxs-lookup"><span data-stu-id="cba72-140">When the Associated Method is Called</span></span>|<span data-ttu-id="cba72-141">一般的な用途</span><span class="sxs-lookup"><span data-stu-id="cba72-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="cba72-142">逆シリアル化の前。\*</span><span class="sxs-lookup"><span data-stu-id="cba72-142">Before deserialization.\*</span></span>|<span data-ttu-id="cba72-143">オプション フィールドの既定値を初期化します。</span><span class="sxs-lookup"><span data-stu-id="cba72-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="cba72-144">逆シリアル化の後</span><span class="sxs-lookup"><span data-stu-id="cba72-144">After deserialization.</span></span>|<span data-ttu-id="cba72-145">他のフィールドの内容に基づいて、オプション フィールドの値を修正します。</span><span class="sxs-lookup"><span data-stu-id="cba72-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="cba72-146">シリアル化の前</span><span class="sxs-lookup"><span data-stu-id="cba72-146">Before serialization.</span></span>|<span data-ttu-id="cba72-147">シリアル化の準備をします。</span><span class="sxs-lookup"><span data-stu-id="cba72-147">Prepare for serialization.</span></span> <span data-ttu-id="cba72-148">たとえば、オプションのデータ構造を作成します。</span><span class="sxs-lookup"><span data-stu-id="cba72-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="cba72-149">シリアル化の後</span><span class="sxs-lookup"><span data-stu-id="cba72-149">After serialization.</span></span>|<span data-ttu-id="cba72-150">シリアル化イベントのログを記録します。</span><span class="sxs-lookup"><span data-stu-id="cba72-150">Log serialization events.</span></span>|

 <span data-ttu-id="cba72-151">\* このコールバックは、逆シリアル化コンストラクターの前に呼び出されます (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="cba72-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="cba72-152">コールバックの使用</span><span class="sxs-lookup"><span data-stu-id="cba72-152">Using callbacks</span></span>

<span data-ttu-id="cba72-153">コールバックを使用するには、<xref:System.Runtime.Serialization.StreamingContext> パラメーターを受け取るメソッドに、適切な属性を適用します。</span><span class="sxs-lookup"><span data-stu-id="cba72-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="cba72-154">各属性でマークできるのは、クラスごとに 1 つのメソッドだけです。</span><span class="sxs-lookup"><span data-stu-id="cba72-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="cba72-155">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="cba72-155">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="cba72-156">これらのメソッドの使用目的は、バージョン管理です。</span><span class="sxs-lookup"><span data-stu-id="cba72-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="cba72-157">オプション フィールドにデータがない場合、逆シリアル化の実行中に、このフィールドが正しく初期化されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="cba72-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="cba72-158">この問題を解決するには、正しい値を割り当てるメソッドを作成してから、このメソッドに **OnDeserializingAttribute** 属性または **OnDeserializedAttribute** 属性のいずれかを適用します。</span><span class="sxs-lookup"><span data-stu-id="cba72-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="cba72-159">型のコンテキストで使用されるメソッドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="cba72-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="cba72-160">以前のバージョンのアプリケーションが新しいバージョンのアプリケーションに `Address` クラスのインスタンスを送信すると、`CountryField` フィールドのデータが欠落します。</span><span class="sxs-lookup"><span data-stu-id="cba72-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="cba72-161">しかし、逆シリアル化を行うと、このフィールドは既定値である "Japan" に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cba72-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
    {
        CountryField = "Japan";
    }
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String
    <OptionalField> _
    Public CountryField As String

    <OnDeserializing> _
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="cba72-162">VersionAdded プロパティ</span><span class="sxs-lookup"><span data-stu-id="cba72-162">The VersionAdded property</span></span>

<span data-ttu-id="cba72-163">**OptionalFieldAttribute** には **VersionAdded** プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="cba72-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="cba72-164">.NET Framework バージョン 2.0 では、このプロパティは使用されません。</span><span class="sxs-lookup"><span data-stu-id="cba72-164">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="cba72-165">ただし、このプロパティを正しく設定して、型が今後のシリアル化エンジンと互換性を保つようにすることが重要です。</span><span class="sxs-lookup"><span data-stu-id="cba72-165">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>

<span data-ttu-id="cba72-166">このプロパティは、指定されたフィールドに追加された型のバージョンを示します。</span><span class="sxs-lookup"><span data-stu-id="cba72-166">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="cba72-167">次の例に示すように、このプロパティの値は 2 を開始値として、型が変更されるたびに常に 1 ずつインクリメントする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cba72-167">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

```csharp
// Version 1.0
[Serializable]
public class Person
{
    public string FullName;
}

// Version 2.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded = 2)]
    public string NickName;
    [OptionalField(VersionAdded = 2)]
    public DateTime BirthDate;
}

// Version 3.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded=2)]
    public string NickName;
    [OptionalField(VersionAdded=2)]
    public DateTime BirthDate;

    [OptionalField(VersionAdded=3)]
    public int Weight;
}
```

```vb
' Version 1.0
<Serializable> _
Public Class Person
    Public FullName
End Class

' Version 2.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime
End Class

' Version 3.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime

    <OptionalField(VersionAdded := 3)> _
    Public Weight As Integer
End Class
```

## <a name="serializationbinder"></a><span data-ttu-id="cba72-168">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="cba72-168">SerializationBinder</span></span>

<span data-ttu-id="cba72-169">サーバー上とクライアント上では異なるバージョンのクラスが必要なため、ユーザーによっては、シリアル化するクラスと逆シリアル化するクラスを制御することが必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="cba72-169">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="cba72-170"><xref:System.Runtime.Serialization.SerializationBinder> は、シリアル化中および逆シリアル化中に使用される実際の型を制御するために使用される抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="cba72-170"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="cba72-171">このクラスを使用するには、クラスを <xref:System.Runtime.Serialization.SerializationBinder> から派生させ、<xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> メソッドと <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="cba72-171">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="cba72-172">詳細については、「[SerializationBinder を使用したシリアル化および逆シリアル化の制御](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cba72-172">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="cba72-173">ベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="cba72-173">Best practices</span></span>

<span data-ttu-id="cba72-174">バージョン管理が正しく行われるように、バージョン間で型を変更するときは次の規則に従ってください。</span><span class="sxs-lookup"><span data-stu-id="cba72-174">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="cba72-175">シリアル化したフィールドを削除しない。</span><span class="sxs-lookup"><span data-stu-id="cba72-175">Never remove a serialized field.</span></span>
- <span data-ttu-id="cba72-176">以前のバージョンでフィールドに <xref:System.NonSerializedAttribute> 属性が適用されていない場合、新しいバージョンでもこの属性を適用しない。</span><span class="sxs-lookup"><span data-stu-id="cba72-176">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="cba72-177">シリアル化したフィールドの名前または型を変更しない。</span><span class="sxs-lookup"><span data-stu-id="cba72-177">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="cba72-178">新しいシリアル化フィールドを追加する場合は、**OptionalFieldAttribute** 属性を適用する。</span><span class="sxs-lookup"><span data-stu-id="cba72-178">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="cba72-179">以前のバージョンでシリアル化できなかったフィールドから **NonSerializedAttribute** 属性を削除する場合は、**OptionalFieldAttribute** 属性を適用する。</span><span class="sxs-lookup"><span data-stu-id="cba72-179">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="cba72-180">すべてのオプション フィールドに対して、既定値として 0 または **null** が許容される場合以外は、シリアル化コールバックを使用して意味のある既定値を設定する。</span><span class="sxs-lookup"><span data-stu-id="cba72-180">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="cba72-181">型が今後のシリアル化エンジンと互換性を保つようにするには、次のガイドラインに従ってください。</span><span class="sxs-lookup"><span data-stu-id="cba72-181">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="cba72-182">**OptionalFieldAttribute** 属性には常に **VersionAdded** を設定する。</span><span class="sxs-lookup"><span data-stu-id="cba72-182">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="cba72-183">バージョンの分岐は避ける。</span><span class="sxs-lookup"><span data-stu-id="cba72-183">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="cba72-184">関連項目</span><span class="sxs-lookup"><span data-stu-id="cba72-184">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="cba72-185">バイナリ シリアル化</span><span class="sxs-lookup"><span data-stu-id="cba72-185">Binary Serialization</span></span>](binary-serialization.md)
