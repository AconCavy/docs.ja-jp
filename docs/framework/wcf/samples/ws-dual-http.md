---
title: WS デュアル Http
ms.date: 03/30/2017
ms.assetid: 9997eba5-29ec-48db-86f3-fa77b241fb1a
ms.openlocfilehash: 78b1da22b309e58e9798713e81afd3210d22f937
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881454"
---
# <a name="ws-dual-http"></a>WS デュアル Http
デュアル Http サンプルでは、`WSDualHttpBinding` バインディングを構成する方法を示します。 このサンプルは、クライアント コンソール プログラム (.exe) と、インターネット インフォメーション サービス (IIS) によってホストされるサービス ライブラリ (.dll) で構成されています。 サービスは、双方向コントラクトを実装します。 このコントラクトは `ICalculatorDuplex` インターフェイスによって定義されており、算術演算 (加算、減算、乗算、および 除算) を公開しています。 このサンプルでは、`ICalculatorDuplex` インターフェイスを使用することにより、クライアントは算術演算を実行し、セッション経由で実行結果を計算できます。 サービスは、`ICalculatorDuplexCallback` インターフェイスで結果を個別に返します。 コンテキストを確立して、クライアントとサービスの間で送信される一連のメッセージを相互に関連付ける必要があるため、双方向コントラクトにはセッションが必要です。 `WSDualHttpBinding` バインディングは双方向通信をサポートしています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\DualHttp`  
  
 `WSDualHttpBinding` を使用してサービス エンドポイントを構成するには、次に示すように、エンドポイント構成でバインディングを指定します。  
  
```xml  
<endpoint address=""  
         binding="wsDualHttpBinding"  
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
```  
  
 クライアントで、サーバーがクライアントへの接続に使用するアドレスを構成する必要があります。次のサンプル構成を参照してください。  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
         "http://localhost/servicemodelsamples/service.svc"   
         binding="wsDualHttpBinding"   
         bindingConfiguration="Binding1"   
         contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex" />  
  </client>  
  
  <bindings>  
    <!-- Configure a WSDualHttpBinding that supports duplex -->  
    <!-- communication. -->  
    <wsDualHttpBinding>  
      <binding name="Binding1"  
               clientBaseAddress="http://localhost:8000/myClient/"  
               useDefaultWebProxy="true"  
               bypassProxyOnLocal="false">  
      </binding>  
    </wsDualHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。 クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Press <ENTER> to terminate client once the output is displayed.  
  
Result(100)  
Result(50)  
Result(882.5)  
Result(441.25)  
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)  
```  
  
 サンプルを実行すると、クライアントに戻ってきたメッセージがサービスから送信されたコールバック インターフェイスに表示されます。 それぞれの中間結果が表示され、その後にすべての操作が完了したときの数式全体が表示されます。 Enter キーを押してクライアントをシャットダウンします。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. 次のコマンドを使用して ASP.NET 4.0 をインストールします。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. 実行したことを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)します。  
  
3. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4. 1 つまたは複数コンピュータ構成では、サンプルを実行する手順については、 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)します。  
  
    > [!IMPORTANT]
    >  複数コンピューター構成でクライアントを実行するときに必ず置き換えて両方で localhost、`address`の属性、 [\<エンドポイント > の\<クライアント >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)要素と`clientBaseAddress`属性、 [\<バインド >](../../../../docs/framework/misc/binding.md)の要素、 [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)に示すように、適切なマシンの名前を持つ要素。  
  
    ```xml  
    <client>  
        <endpoint name = ""  
          address=  
         "http://service_machine_name/servicemodelsamples/service.svc"  
        />  
    </client>  
    ...  
    <wsDualHttpBinding>  
        <binding name="DuplexBinding" clientBaseAddress=  
            "http://client_machine_name:8000/myClient/">  
        </binding>  
    </wsDualHttpBinding>  
    ```  
