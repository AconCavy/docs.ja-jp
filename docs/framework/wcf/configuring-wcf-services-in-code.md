---
title: コード内での WCF サービスの構成
ms.date: 03/30/2017
ms.assetid: 193c725d-134f-4d31-a8f8-4e575233bff6
ms.openlocfilehash: 4ff49b4e17ae179426cc033a955ecf2c71f2a3e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174811"
---
# <a name="configuring-wcf-services-in-code"></a>コード内での WCF サービスの構成
Windows 通信基盤 (WCF) を使用すると、開発者は構成ファイルまたはコードを使用してサービスを構成できます。  構成ファイルは、サービスを配置した後に構成する必要がある場合に便利です。 構成ファイルを使用する場合、IT 専門家は構成ファイルを更新するだけで、再コンパイルの必要はありません。 ただし、構成ファイルの管理は複雑で難しくなる場合があります。 構成ファイルのデバッグはサポートされていません。また、構成要素は名前で参照されるため、構成ファイルの作成時にエラーが発生しやすく、構成ファイルの作成が困難になります。 WCF では、コードでサービスを構成することもできます。 以前のバージョンの WCF (4.0 以前) では、コードでサービスを構成する自己ホスト型のシナリオ<xref:System.ServiceModel.ServiceHost>では簡単でしたが、クラスでは ServiceHost.Open を呼び出す前にエンドポイントと動作を構成できました。 ただし、Web ホストのシナリオでは、<xref:System.ServiceModel.ServiceHost> クラスに直接アクセスできません。 Web ホスト サービスを構成するには、`System.ServiceModel.ServiceHostFactory` を作成して必要な構成を実行する <xref:System.ServiceModel.Activation.ServiceHostFactory> を作成する必要がありました。 NET 4.5 以降、WCF は、コードで自己ホスト型サービスと Web ホスト サービスの両方を構成する簡単な方法を提供します。  
  
## <a name="the-configure-method"></a>Configure メソッド  
 サービス実装クラスで、次のシグネチャを持つ `Configure` という名前のパブリックな静的メソッドを定義します。  
  
```csharp  
public static void Configure(ServiceConfiguration config)  
```  
  
 Configure メソッドは、開発者がエンドポイントおよび動作を追加できるようにする <xref:System.ServiceModel.ServiceConfiguration> インスタンスを受け取ります。 このメソッドは、サービス ホストを開く前に WCF によって呼び出されます。 app.config ファイルまたは web.config ファイルで指定されたすべてのサービスの構成設定は、定義されている場合、無視されます。  
  
 次のコード スニペットは、`Configure` メソッドを定義し、サービス エンドポイント、エンドポイントの動作、およびサービスの動作を追加する方法を示しています。  
  
```csharp  
public class Service1 : IService1  
    {  
        public static void Configure(ServiceConfiguration config)  
        {  
            ServiceEndpoint se = new ServiceEndpoint(new ContractDescription("IService1"), new BasicHttpBinding(), new EndpointAddress("basic"));  
            se.Behaviors.Add(new MyEndpointBehavior());  
            config.AddServiceEndpoint(se);  
  
            config.Description.Behaviors.Add(new ServiceMetadataBehavior { HttpGetEnabled = true });  
            config.Description.Behaviors.Add(new ServiceDebugBehavior { IncludeExceptionDetailInFaults = true });  
        }  
  
        public string GetData(int value)  
        {  
            return $"You entered: {value}";
        }  
  
        public CompositeType GetDataUsingDataContract(CompositeType composite)  
        {  
            if (composite == null)  
            {  
                throw new ArgumentNullException("composite");  
            }  
            if (composite.BoolValue)  
            {  
                composite.StringValue += "Suffix";  
            }  
            return composite;  
        }  
    }  
```  
  
 サービスで https などのプロトコルを有効にするには、プロトコルを使用するエンドポイントを明示的に追加するか、ServiceConfiguration.EnableProtocol(Binding) を呼び出すことによって自動的にエンドポイントを追加します。このメソッドは、プロトコルおよび定義された各サービス コントラクトと互換性がある各ベース アドレスのエンドポイントを追加します。 次のコードは、ServiceConfiguration.EnableProtocol メソッドを使用する方法を示しています。  
  
```csharp  
public class Service1 : IService1
{
    public string GetData(int value);
    public static void Configure(ServiceConfiguration config)
    {
        // Enable "Add Service Reference" support
       config.Description.Behaviors.Add( new ServiceMetadataBehavior { HttpGetEnabled = true });
       // set up support for http, https, net.tcp, net.pipe
       config.EnableProtocol(new BasicHttpBinding());
       config.EnableProtocol(new BasicHttpsBinding());
       config.EnableProtocol(new NetTcpBinding());
       config.EnableProtocol(new NetNamedPipeBinding());
       // add an extra BasicHttpBinding endpoint at http:///basic
       config.AddServiceEndpoint(typeof(IService1), new BasicHttpBinding(),"basic");
    }
}
```  
  
 [<>]`protocolMappings`セクションの設定は、アプリケーション エンドポイントがプログラムによって追加されていない場合<xref:System.ServiceModel.ServiceConfiguration>にのみ使用されます。必要に応じて、既定のアプリケーション構成ファイルからサービス構成を呼び<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A>出して読み込み、設定を変更できます。 <xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration> クラスを使って、集中化された構成から構成を読み込むこともできます。 これを実装する方法を次のコードに示します。  
  
```csharp
public class Service1 : IService1
{
    public void DoWork();
    public static void Configure(ServiceConfiguration config)
    {
          config.LoadFromConfiguration(ConfigurationManager.OpenMappedExeConfiguration(new ExeConfigurationFileMap { ExeConfigFilename = @"c:\sharedConfig\MyConfig.config" }, ConfigurationUserLevel.None));
    }
}  
```  
  
> [!IMPORTANT]
> >の<xref:System.ServiceModel.ServiceConfiguration.LoadFromConfiguration%2A><>`host``service`タグ内の<>設定<無視されることに`system.serviceModel`注意してください。 概念的には`host`、<>はサービス構成ではなくホスト構成に関するものであり、Configure メソッドが実行される前に読み込まれます。  
  
## <a name="see-also"></a>関連項目

- [構成ファイルを使用してサービスを構成する方法](configuring-services-using-configuration-files.md)
- [クライアントの動作の構成](configuring-client-behaviors.md)
- [簡略化された構成](simplified-configuration.md)
- [構成](./samples/configuration-sample.md)
- [IIS と WAS における構成ベースのアクティブ化](./feature-details/configuration-based-activation-in-iis-and-was.md)
- [構成とメタデータのサポート](./extending/configuration-and-metadata-support.md)
- [構成](./diagnostics/exceptions-reference/configuration.md)
- [方法: 構成でサービス バインディングを指定する](how-to-specify-a-service-binding-in-configuration.md)
- [方法 : 構成にサービス エンドポイントを作成する](./feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [方法 : 構成ファイルを使用してサービスのメタデータを公開する](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [方法: 構成でクライアント バインディングを指定する](how-to-specify-a-client-binding-in-configuration.md)
