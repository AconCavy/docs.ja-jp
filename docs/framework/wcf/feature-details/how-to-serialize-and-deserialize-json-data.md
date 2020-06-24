---
title: '方法: DataContractJsonSerializer を使用する'
description: .NET 型オブジェクトを JSON エンコードされたデータにシリアル化してから、そのようなデータを .NET 型のインスタンスに逆シリアル化する方法について説明します。
ms.date: 03/25/2019
ms.assetid: 88abc1fb-8196-4ee3-a23b-c6934144d1dd
ms.openlocfilehash: 4ffa0e9dec0a677a38d244b4a0da476d91852da5
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246806"
---
# <a name="how-to-use-datacontractjsonserializer"></a><span data-ttu-id="f70f7-103">DataContractJsonSerializer の使用方法</span><span class="sxs-lookup"><span data-stu-id="f70f7-103">How to use DataContractJsonSerializer</span></span>

> [!NOTE]
> <span data-ttu-id="f70f7-104">この記事では、について説明 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-104">This article is about <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span> <span data-ttu-id="f70f7-105">JSON のシリアル化と逆シリアル化を含むほとんどのシナリオでは、[名前空間のSystem.Text.Js](../../../standard/serialization/system-text-json-overview.md)で api を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="f70f7-105">For most scenarios that involve serializing and deserializing JSON, we recommend the APIs in the [System.Text.Json namespace](../../../standard/serialization/system-text-json-overview.md).</span></span>

<span data-ttu-id="f70f7-106">JSON (JavaScript Object Notation) は、クライアント ブラウザーと AJAX 対応の Web サービスとの間で、少量のデータを高速に交換できる効率的なデータ エンコード形式です。</span><span class="sxs-lookup"><span data-stu-id="f70f7-106">JSON (JavaScript Object Notation) is an efficient data encoding format that enables fast exchanges of small amounts of data between client browsers and AJAX-enabled Web services.</span></span>

<span data-ttu-id="f70f7-107">この記事では、.NET 型オブジェクトを JSON エンコードされたデータにシリアル化し、JSON 形式のデータを .NET 型のインスタンスに逆シリアル化する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-107">This article demonstrates how to serialize .NET type objects into JSON-encoded data and then deserialize data in the JSON format back into instances of .NET types.</span></span> <span data-ttu-id="f70f7-108">この例では、データコントラクトを使用して、ユーザー定義型のシリアル化と逆シリアル化を示し `Person` 、を使用し <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ます。</span><span class="sxs-lookup"><span data-stu-id="f70f7-108">This example uses a data contract to demonstrate serialization and deserialization of a user-defined `Person` type and uses <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<span data-ttu-id="f70f7-109">通常、AJAX 対応のエンドポイントで公開されるサービス操作でデータコントラクト型を使用する場合、JSON のシリアル化と逆シリアル化は、Windows Communication Foundation (WCF) によって自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="f70f7-109">Normally, JSON serialization and deserialization are handled automatically by Windows Communication Foundation (WCF) when you use data contract types in service operations that are exposed over AJAX-enabled endpoints.</span></span> <span data-ttu-id="f70f7-110">ただし、場合によっては、JSON データを直接操作する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f70f7-110">However, in some cases you may need to work with JSON data directly.</span></span>

<span data-ttu-id="f70f7-111">この記事は、 [DataContractJsonSerializer サンプル](../samples/json-serialization.md)を基にしています。</span><span class="sxs-lookup"><span data-stu-id="f70f7-111">This article is based on the [DataContractJsonSerializer sample](../samples/json-serialization.md).</span></span>

## <a name="to-define-the-data-contract-for-a-person-type"></a><span data-ttu-id="f70f7-112">個人の種類のデータコントラクトを定義するには</span><span class="sxs-lookup"><span data-stu-id="f70f7-112">To define the data contract for a Person type</span></span>

1. <span data-ttu-id="f70f7-113">クラスに `Person` をアタッチし、シリアル化するメンバーに <xref:System.Runtime.Serialization.DataContractAttribute> 属性をアタッチすることで、<xref:System.Runtime.Serialization.DataMemberAttribute> のデータ コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-113">Define the data contract for `Person` by attaching the <xref:System.Runtime.Serialization.DataContractAttribute> to the class and <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to the members you want to serialize.</span></span> <span data-ttu-id="f70f7-114">データコントラクトの詳細については、「[サービスコントラクトの設計](../designing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f70f7-114">For more information about data contracts, see [Designing service contracts](../designing-service-contracts.md).</span></span>

    ```csharp
    [DataContract]
    internal class Person
    {
        [DataMember]
        internal string name;

        [DataMember]
        internal int age;
    }
    ```

## <a name="to-serialize-an-instance-of-type-person-to-json"></a><span data-ttu-id="f70f7-115">Person 型のインスタンスを JSON にシリアル化するには</span><span class="sxs-lookup"><span data-stu-id="f70f7-115">To serialize an instance of type Person to JSON</span></span>

> [!NOTE]
> <span data-ttu-id="f70f7-116">サーバー上の送信応答のシリアル化中または他の何らかの理由でエラーが発生した場合、エラーとしてクライアントに返されないことがあります。</span><span class="sxs-lookup"><span data-stu-id="f70f7-116">If an error occurs during serialization of an outgoing reply on the server or for some other reason, it may not get returned to the client as a fault.</span></span>

1. <span data-ttu-id="f70f7-117">`Person` 型のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-117">Create an instance of the `Person` type.</span></span>

    ```csharp
    var p = new Person();
    p.name = "John";
    p.age = 42;
    ```

2. <span data-ttu-id="f70f7-118">を `Person` 使用して、オブジェクトをメモリストリームにシリアル化し <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ます。</span><span class="sxs-lookup"><span data-stu-id="f70f7-118">Serialize the `Person` object to a memory stream by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    var stream1 = new MemoryStream();
    var ser = new DataContractJsonSerializer(typeof(Person));
    ```

3. <span data-ttu-id="f70f7-119">JSON データをストリームに書き込むには、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-119">Use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.WriteObject%2A> method to write JSON data to the stream.</span></span>

    ```csharp
    ser.WriteObject(stream1, p);
    ```

4. <span data-ttu-id="f70f7-120">JSON の出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-120">Show the JSON output.</span></span>

    ```csharp
    stream1.Position = 0;
    var sr = new StreamReader(stream1);
    Console.Write("JSON form of Person object: ");
    Console.WriteLine(sr.ReadToEnd());
    ```

## <a name="to-deserialize-an-instance-of-type-person-from-json"></a><span data-ttu-id="f70f7-121">JSON から Person 型のインスタンスに逆シリアル化するには</span><span class="sxs-lookup"><span data-stu-id="f70f7-121">To deserialize an instance of type Person from JSON</span></span>

1. <span data-ttu-id="f70f7-122">`Person` の <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> メソッドを使用して、JSON エンコードされたデータを <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> の新しいインスタンスに逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-122">Deserialize the JSON-encoded data into a new instance of `Person` by using the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject%2A> method of the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

    ```csharp
    stream1.Position = 0;
    var p2 = (Person)ser.ReadObject(stream1);
    ```

2. <span data-ttu-id="f70f7-123">結果を表示します。</span><span class="sxs-lookup"><span data-stu-id="f70f7-123">Show the results.</span></span>

    ```csharp
    Console.WriteLine($"Deserialized back, got name={p2.name}, age={p2.age}");
    ```

## <a name="example"></a><span data-ttu-id="f70f7-124">例</span><span class="sxs-lookup"><span data-stu-id="f70f7-124">Example</span></span>

```csharp
// Create a User object and serialize it to a JSON stream.
public static string WriteFromObject()
{
    // Create User object.
    var user = new User("Bob", 42);

    // Create a stream to serialize the object to.
    var ms = new MemoryStream();

    // Serializer the User object to the stream.
    var ser = new DataContractJsonSerializer(typeof(User));
    ser.WriteObject(ms, user);
    byte[] json = ms.ToArray();
    ms.Close();
    return Encoding.UTF8.GetString(json, 0, json.Length);
}

// Deserialize a JSON stream to a User object.
public static User ReadToObject(string json)
{
    var deserializedUser = new User();
    var ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
    var ser = new DataContractJsonSerializer(deserializedUser.GetType());
    deserializedUser = ser.ReadObject(ms) as User;
    ms.Close();
    return deserializedUser;
}
```

> [!NOTE]
> <span data-ttu-id="f70f7-125">JSON シリアライザーは、次のサンプル コードに示すように、データ コントラクターの複数のメンバーが同じ名前である場合、シリアル化例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="f70f7-125">The JSON serializer throws a serialization exception for data contracts that have multiple members with the same name, as shown in the following sample code.</span></span>

```csharp
[DataContract]
public class TestDuplicateDataBase
{
    [DataMember]
    public int field1 = 123;
}

[DataContract]
public class TestDuplicateDataDerived : TestDuplicateDataBase
{
    [DataMember]
    public new int field1 = 999;
}
```

## <a name="see-also"></a><span data-ttu-id="f70f7-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="f70f7-126">See also</span></span>

- [<span data-ttu-id="f70f7-127">.NET での JSON のシリアル化</span><span class="sxs-lookup"><span data-stu-id="f70f7-127">JSON serialization in .NET</span></span>](../../../standard/serialization/system-text-json-overview.md)
