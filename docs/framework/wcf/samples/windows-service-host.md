---
title: Windows サービス ホスト
ms.date: 03/30/2017
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
ms.openlocfilehash: 2f2024a984111a826adab31ca15f1a46f9733de5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045404"
---
# <a name="windows-service-host"></a>Windows サービス ホスト
このサンプルでは、マネージ Windows サービスでホストされている Windows Communication Foundation (WCF) サービスを示します。 Windows サービスのサービス アプレットを使用して、制御 **コントロール パネルの** システムの再起動後に自動的に起動するように構成できます。 このサンプルは、クライアント プログラムと Windows サービス プログラムで構成されています。 サービスは .exe プログラムとして実装され、独自のホスティング コードが指定されます。 Windows プロセス アクティブ化サービス (WAS) やインターネット インフォメーション サービス (IIS) などの他のホスト環境では、ホスティング コードを記述する必要はありません。

> [!NOTE]
> このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 このサービスをビルドしたら、他の Windows サービスと同様、Installutil.exe ユーティリティを使用してインストールする必要があります。 サービスを変更する場合は、`installutil /u` を使用して、まずそのサービスをアンインストールする必要があります。 このサンプルに含まれている Setup.bat ファイルは Windows Service をインストールして起動するコマンド ファイルです。同様にこのサンプルに含まれている Cleanup.bat ファイルは、Windows サービスをシャットダウンしてアンインストールするコマンド ファイルです。 WCF サービスは、Windows サービスが実行されている場合にのみ、クライアントに応答できます。 サービス アプレットを使用して Windows サービスを停止するかどうかは **コントロール パネルの**  クライアントを実行し、<xref:System.ServiceModel.EndpointNotFoundException>例外は、クライアントがサービスにアクセスしようとしたときに発生します。 Windows サービスを再起動してクライアントを再実行した場合は、通信が正常に行われます。  
  
 サービスコードには、インストーラークラス、ICalculator コントラクトを実装する WCF サービス実装クラス、およびランタイムホストとして機能する Windows サービスクラスが含まれています。 インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを NT サービスとしてインストールできます。 サービス実装クラス`WcfCalculatorService`は、基本的なサービスコントラクトを実装する WCF サービスです。 この WCF サービスは、という名前`WindowsCalculatorService`の Windows サービスクラス内でホストされます。 Windows サービスとして限定するため、このクラスは <xref:System.ServiceProcess.ServiceBase> を継承し、<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドを実装しています。 <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> では、<xref:System.ServiceModel.ServiceHost> 型の `WcfCalculatorService` オブジェクトが作成され、開かれます。 <xref:System.ServiceProcess.ServiceBase.OnStop> では、<xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> オブジェクトの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されて ServiceHost が閉じられます。 ホストのベースアドレスは、 [ \<add >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)要素を使用して構成されます。これは、 [ \<ホスト >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)要素の子である[ \<baseaddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)の子です。これは、 [ \<サービス >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)要素。  
  
 定義されているエンドポイントは、ベースアドレスと[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を使用します。 ベース アドレスの構成と CalculatorService を公開するエンドポイントのサンプルを次に示します。  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. [Windows Communication Foundation サンプルの1回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。  
  
2. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3. ソリューションがビルドされたら、管理者特権で Visual Studio 2012 コマンドプロンプトから Setup.exe を実行し、Installutil.exe ツールを使用して Windows サービスをインストールします。 このサービスは、[サービス] に表示されます。  
  
4. サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
## <a name="see-also"></a>関連項目

- [AppFabric のホスティングと永続化のサンプル](https://go.microsoft.com/fwlink/?LinkId=193961)
