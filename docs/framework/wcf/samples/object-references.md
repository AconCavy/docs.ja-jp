---
title: オブジェクト参照
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 2a2da82d913d43aa9bc3ccfeb9f1f1eda12b0562
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008060"
---
# <a name="object-references"></a>オブジェクト参照
このサンプルでは、サーバーとクライアント間でオブジェクトを参照渡しする方法を示します。 シミュレートされたサンプルは*ソーシャル ネットワーク*します。 ソーシャル ネットワークは、友人のリストを含んでいる `Person` クラスで構成され、このリストの各友人は、それぞれ独自の友人のリストを持つ `Person` クラスのインスタンスです。 これにより、オブジェクトのグラフが作成されます。 このようなソーシャル ネットワークに対する操作は、サービスによって公開されます。  
  
 この例では、サービスはインターネット インフォメーション サービス (IIS) によってホストされています。クライアントはコンソール アプリケーション (.exe) です。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
## <a name="service"></a>サービス  
 `Person` クラスに <xref:System.Runtime.Serialization.DataContractAttribute> 属性が適用され、参照型であることを宣言するため <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> フィールドが `true` に設定されます。 すべてのプロパティに <xref:System.Runtime.Serialization.DataMemberAttribute> 属性が適用されます。  
  
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
  
 `GetPeopleInNetwork` 操作では、`Person` 型のパラメータを受け取り、ネットワーク内のすべてのユーザー (`friends` リストに含まれるすべてのユーザー、友人の友人など) を重複することなく返します。  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 `GetMutualFriends` 操作では、`Person` 型のパラメータを受け取り、自分の `friends` リストにこの人物も存在するリスト内のすべての友人を返します。  
  
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
  
 `GetCommonFriends` 操作では、`Person` 型のリストを受け取ります。 このリストには、2 つの `Person` オブジェクトが存在します。 この操作では、入力リストの両方の `Person` オブジェクトの `friends` リスト内にある `Person` オブジェクトのリストを返します。  
  
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
  
## <a name="client"></a>クライアント  
 使用して、クライアント プロキシを作成、**サービス参照の追加**Visual Studio の機能です。  
  
 5 つの `Person` オブジェクトで構成されるソーシャル ネットワークが作成されます。 クライアントは、サービスの 3 つのメソッドをそれぞれ呼び出します。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. 1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [相互運用可能なオブジェクト参照](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
