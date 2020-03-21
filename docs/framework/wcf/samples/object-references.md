---
title: オブジェクトの参照
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183461"
---
# <a name="object-references"></a><span data-ttu-id="0110c-102">オブジェクトの参照</span><span class="sxs-lookup"><span data-stu-id="0110c-102">Object References</span></span>
<span data-ttu-id="0110c-103">このサンプルでは、サーバーとクライアント間でオブジェクトを参照渡しする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0110c-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="0110c-104">サンプルでは、シミュレートされた*ソーシャルネットワーク*を使用しています。</span><span class="sxs-lookup"><span data-stu-id="0110c-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="0110c-105">ソーシャル ネットワークは、友人のリストを含んでいる `Person` クラスで構成され、このリストの各友人は、それぞれ独自の友人のリストを持つ `Person` クラスのインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="0110c-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="0110c-106">これにより、オブジェクトのグラフが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0110c-106">This creates a graph of objects.</span></span> <span data-ttu-id="0110c-107">このようなソーシャル ネットワークに対する操作は、サービスによって公開されます。</span><span class="sxs-lookup"><span data-stu-id="0110c-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="0110c-108">この例では、サービスはインターネット インフォメーション サービス (IIS) によってホストされています。クライアントはコンソール アプリケーション (.exe) です。</span><span class="sxs-lookup"><span data-stu-id="0110c-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0110c-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0110c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="0110c-110">サービス</span><span class="sxs-lookup"><span data-stu-id="0110c-110">Service</span></span>  
 <span data-ttu-id="0110c-111">`Person` クラスに <xref:System.Runtime.Serialization.DataContractAttribute> 属性が適用され、参照型であることを宣言するため <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> フィールドが `true` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="0110c-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="0110c-112">すべてのプロパティに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性が適用されます。</span><span class="sxs-lookup"><span data-stu-id="0110c-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 <span data-ttu-id="0110c-113">`GetPeopleInNetwork` 操作では、`Person` 型のパラメータを受け取り、ネットワーク内のすべてのユーザー (`friends` リストに含まれるすべてのユーザー、友人の友人など) を重複することなく返します。</span><span class="sxs-lookup"><span data-stu-id="0110c-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="0110c-114">`GetMutualFriends` 操作では、`Person` 型のパラメータを受け取り、自分の `friends` リストにこの人物も存在するリスト内のすべての友人を返します。</span><span class="sxs-lookup"><span data-stu-id="0110c-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 <span data-ttu-id="0110c-115">`GetCommonFriends` 操作では、`Person` 型のリストを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0110c-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="0110c-116">このリストには、2 つの `Person` オブジェクトが存在します。</span><span class="sxs-lookup"><span data-stu-id="0110c-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="0110c-117">この操作では、入力リストの両方の `Person` オブジェクトの `friends` リスト内にある `Person` オブジェクトのリストを返します。</span><span class="sxs-lookup"><span data-stu-id="0110c-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="0110c-118">Client</span><span class="sxs-lookup"><span data-stu-id="0110c-118">Client</span></span>  
 <span data-ttu-id="0110c-119">クライアント プロキシは、Visual Studio の**サービス参照の追加**機能を使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="0110c-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="0110c-120">5 つの `Person` オブジェクトで構成されるソーシャル ネットワークが作成されます。</span><span class="sxs-lookup"><span data-stu-id="0110c-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="0110c-121">クライアントは、サービスの 3 つのメソッドをそれぞれ呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0110c-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0110c-122">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="0110c-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0110c-123">[Windows コミュニケーションファウンデーション サンプルのワンタイム セットアップ手順を](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="0110c-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0110c-124">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0110c-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0110c-125">単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。</span><span class="sxs-lookup"><span data-stu-id="0110c-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0110c-126">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0110c-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0110c-127">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0110c-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0110c-128">このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="0110c-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0110c-129">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0110c-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="0110c-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="0110c-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="0110c-131">相互運用可能なオブジェクト参照</span><span class="sxs-lookup"><span data-stu-id="0110c-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
