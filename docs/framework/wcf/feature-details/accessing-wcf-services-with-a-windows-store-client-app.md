---
title: Windows ストア クライアント アプリを使用した WCF サービスへのアクセス
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: a7d87e6014f26842c35b0d1bf5028682a4cf69e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784320"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a>Windows ストア クライアント アプリを使用した WCF サービスへのアクセス
Windows 8 では、Windows ストア アプリケーションと呼ばれる新しい種類のアプリケーションが導入されています。 これらのアプリケーションはタッチ スクリーンのインターフェイスを念頭にデザインされています。 .NET Framework 4.5 により、Windows ストア アプリケーションから WCF サービスを呼び出すことができます。  
  
## <a name="wcf-support-in-windows-store-applications"></a>Windows ストア アプリケーションでの WCF のサポート  
 WCF 機能の一部は、Windows ストア アプリケーション内から利用できます。詳細については、以降のセクションを参照してください。  
  
> [!IMPORTANT]
>  WCF で公開される API ではなく、WinRT 配信 API を使用してください。 詳細については、「 [Windows.Web.Syndication 名前空間](https://go.microsoft.com/fwlink/?LinkId=236265)」を参照してください。  
  
> [!WARNING]
>  サービス参照の追加を使用して Windows ランタイム コンポーネントへの Web サービス参照を追加することはサポートされていません。  
  
### <a name="supported-bindings"></a>サポートされているバインド  
 Windows ストア アプリケーションでは、以下の WCF バインドがサポートされています。  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 Windows ストア アプリケーションでは、以下のバインド要素がサポートされています。  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 テキスト エンコードとバイナリ エンコードの両方がサポートされています。 すべての WCF 転送モードがサポートされています。 詳細については、「 [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)」を参照してください。  
  
### <a name="add-service-reference"></a>サービス参照の追加  
 WCF サービスを Windows ストア アプリケーションから呼び出すには、Visual Studio 2012 の "サービス参照の追加" 機能を使用します。 Windows ストア アプリケーションでは、"サービス参照の追加" 機能にいくつかの変更が行われていることがわかります。 まず、構成ファイルが生成されません。 Windows ストア アプリケーションでは構成ファイルが使用されないため、コードで構成する必要があります。 この構成コードは、"サービス参照の追加" によって生成される References.cs ファイルにあります。 このファイルを表示するには、ソリューション エクスプ ローラーで"すべてのファイルを表示 を選択してください。 このファイルは、[サービス参照] の下のプロジェクト内の Reference.svcmap ノードにあります。 Windows ストア アプリケーション内で WCF サービスに対して生成されるすべての操作は非同期で、タスク ベースの非同期パターンが使用されます。 詳細については、次を参照してください。[非同期タスクのタスクを使用した非同期プログラミングを簡略化](https://msdn.microsoft.com/magazine/ff959203.aspx)します。  
  
 構成がコードで生成されるようになったため、サービス参照を更新するたびに、Reference.cs ファイルで行ったすべての変更が上書きされます。 この状況に対処するために、構成コードは部分メソッド内に生成され、これをクライアント プロキシ クラスで実装できます。 部分メソッドは次のように宣言されています。  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 その後、この部分メソッドを実装し、次のように、クライアント プロキシ クラスのバインドまたはエンドポイントを変更できます。  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {   
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,   
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==   
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a>シリアル化  
 Windows ストア アプリケーションでは、次のシリアライザーがサポートされています。  
  
1. DataContractSerializer  
  
2. DataContractJsonSerializer  
  
3. XmlSerializer  
  
> [!WARNING]
>  XmlDictionaryWriter.Write(DateTime) は、DateTime オブジェクトを文字列として出力するようになりました。  
  
### <a name="security"></a>セキュリティ  

Windows ストア アプリケーションでは、次のセキュリティ モードがサポートされています。
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
Windows ストア アプリケーションでは、次のクライアント資格情報の種類がサポートされています。
  
1. なし  
  
2. Basic  
  
3. Digest  
  
4. Negotiate  
  
5. NTLM  
  
6. Windows  
  
7. ユーザー名 (メッセージ セキュリティ)  
  
8. Windows (トランスポート セキュリティ)  
  
 Windows ストア アプリケーションから既定の Windows 資格情報にアクセスして送信するためには、Package.appmanifest ファイル内でこの機能を有効にする必要があります。 このファイルを開くと、[機能] タブを選択し、「既定の Windows 資格情報」を選択します。 これにより、ドメイン資格情報を必要とするイントラネット リソースにアプリケーションが接続できるようになります。  
  
> [!IMPORTANT]
>  Windows ストア アプリケーションをコンピューター間の呼び出しの順序では、「ホーム/社内ネットワーク」と呼ばれる別の機能を有効にする必要があります。 この設定は、Package.appmanifest ファイル内の [機能] タブにもあります。[ホーム/社内ネットワーク] チェック ボックスをオンにします。 これで、アプリケーションは、自宅や職場など、ユーザーが信頼できる場所のネットワークに着信および発信アクセスできるようになります。 着信方向の重要なポートは常にブロックされます。 また、インターネット上のサービスにアクセスするには、インターネット (クライアント) の機能も有効にする必要があります。  
  
### <a name="misc"></a>[その他]  
 Windows ストア アプリケーションでは、次のクラスの使用がサポートされています。  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a>サービス コントラクトの定義  
 非同期サービス操作の定義には、タスク ベースの非同期パターンのみを使用することをお勧めします。 これにより、サービス操作の呼び出し中も、Windows ストア アプリケーションの応答が維持されます。  
  
> [!WARNING]
>  同期操作を定義した場合でも例外はスローされませんが、非同期操作のみを定義することを強くお勧めします。  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a>Windows ストア アプリケーションからの WCF サービスの呼び出し  
 既に説明したように、すべての構成は、生成されたプロキシ クラスの GetBindingForEndpoint メソッドのコード内で行う必要があります。 次のコードに示すように、サービス操作の呼び出しは、タスク ベースの非同期メソッドの呼び出しと同じように実行されます。  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 非同期呼び出しを行うメソッドでは async キーワード、非同期メソッドの呼び出し時には await キーワードが使用されていることに注意してください。  
  
## <a name="see-also"></a>関連項目

- [Windows ストア アプリ ブログの WCF](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [WCF Windows ストア クライアントおよびセキュリティ](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [Windows ストア アプリとコンピューター間の呼び出し](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [Windows ストア アプリから Azure にデプロイされた WCF サービスの呼び出し](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [バインディング](../../../../docs/framework/wcf/bindings.md)
