---
title: クライアントのセキュリティ保護
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: 7f9a02bc650f54338dfcb1d3f41397e745483430
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959537"
---
# <a name="securing-clients"></a>クライアントのセキュリティ保護
Windows Communication Foundation (WCF) では、サービスはクライアントのセキュリティ要件を決定します。 つまり、使用するセキュリティ モード、およびクライアントが資格情報を提供するかどうかは、サービスによって指定されます。 そのため、クライアントをセキュリティで保護するプロセスは、サービスから取得したメタデータ (公開されている場合) を使用してクライアントを構築するという簡単なものになります。 クライアントを構成する方法は、メタデータによって指定されます。 クライアントが資格情報を提供することをサービスが要求する場合、要件に適した資格情報を取得する必要があります。 ここでは、このプロセスについて詳しく説明します。 セキュリティで保護されたサービスの作成の詳細については、「[サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)」を参照してください。  
  
## <a name="the-service-specifies-security"></a>サービスによるセキュリティの指定  
 既定では、WCF バインドではセキュリティ機能が有効になっています。 (<xref:System.ServiceModel.BasicHttpBinding> を除く)。このため、WCF を使用してサービスを作成した場合、認証、機密性、および整合性を確保するためにセキュリティを実装する可能性が高くなります。 この場合、サービスが提供するメタデータによって、セキュリティで保護された通信チャネルの確立に必要なものが示されます。 サービス メタデータにセキュリティ要件がまったく含まれていない場合には、サービスでセキュリティ スキーム (SSL (Secure Sockets Layer) over HTTP など) を強制する方法はありません。 ただし、サービスがクライアントに資格情報の提供を求める場合は、クライアントの開発者、展開担当者、または管理者は、クライアントがサービスに対して認証を受けるときに実際に使用する資格情報を提供する必要があります。  
  
## <a name="obtaining-metadata"></a>メタデータの取得  
 クライアントを作成する場合、最初の手順はクライアントが通信を行うサービスからメタデータを取得することです。 これは、次の 2 つの方法で行うことができます。 最初に、サービスが metadata exchange (MEX) エンドポイントを公開するか、または HTTP または HTTPS 経由でメタデータを使用できるようにする場合、 [ServiceModel メタデータユーティリティツール (svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を使用してメタデータをダウンロードできます。これにより、クライアントの両方のコードファイルが生成されます。構成ファイルも同様です。 (このツールの使用方法の詳細については、「 [WCF クライアントを使用したサービスへのアクセス](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)」を参照してください)。サービスにより MEX エンドポイントが公開されておらず、かつ HTTP または HTTPS 上でメタデータが使用可能になっていない場合は、サービス作成者に連絡して、セキュリティ要件とメタデータについて記述したドキュメントを入手する必要があります。  
  
> [!IMPORTANT]
> メタデータが信頼されたソースのものであり、改ざんされていないことを確認することをお勧めします。 HTTP プロトコルを使用して取得したメタデータはクリア テキストで送信されるため、改ざんされるおそれがあります。 サービスで <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> プロパティおよび <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> プロパティを使用している場合は、サービス作成者から提供された URL で、HTTPS プロトコルを使用してデータをダウンロードします。  
  
## <a name="validating-security"></a>セキュリティの検証  
 メタデータのソースは、信頼されたソースと信頼関係のないソースの 2 つに大きく分けられます。 ソースを信頼しており、そのソースのセキュリティで保護された MEX エンドポイントからクライアント コードとその他のメタデータをダウンロードしている場合、何の懸念もなく、クライアントをビルドし、適切な資格情報を提供して実行できます。  
  
 ただし、ほとんど未知のソースからクライアントとメタデータをダウンロードする場合は、コードで使用しているセキュリティ対策を検証する必要があります。 たとえば、サービスにより (最低でも) 機密性と整合性とが要求されていない場合は、個人情報や財務情報を送信するクライアントを作成するようなことは絶対に避けてください。 この種の情報はサービスの所有者から見ることが可能なので、この種の情報の開示を行ってもよいと判断できる程度にはサービスの所有者を信頼できる必要があります。  
  
 したがって、信頼できないソースから受け取ったコードとメタデータを使用する場合には、それがこちらの必要とするセキュリティ レベルを満たしていることを確認する必要があります。  
  
## <a name="setting-a-client-credential"></a>クライアント資格情報の設定  
 クライアントへの資格情報の設定には、次の 2 つの手順があります。  
  
1. サービスが必要とする*クライアント資格情報の種類*を決定します。 これは、2 つある方法のどちらかによって行います。 1 つ目の方法として、サービス作成者からドキュメントを入手している場合は、このドキュメントにサービスが要求するクライアント資格情報の種類が示されています (クライアント資格情報の種類が指定されている場合)。 2 番目の方法は Svcutil.exe ツールによって作成された構成ファイルしかない場合で、個々のバインディングを調べることで必要な資格情報の種類を特定できます。  
  
2. 実際のクライアント資格情報を指定します。 実際のクライアント資格情報は、型と区別するために*クライアント資格*情報の値と呼ばれます。 たとえば、クライアント資格情報の種類として証明書が指定されている場合、サービスが信頼する証明機関によって発行された X.509 証明書を指定する必要があります。  
  
### <a name="determining-the-client-credential-type"></a>クライアント資格情報の種類の特定  
 Svcutil.exe ツールによって生成された構成ファイルがある場合は、 [ \<バインド >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)セクションを調べて、必要なクライアント資格情報の種類を決定します。 このセクション内には、セキュリティ要件を指定するバインド要素があります。 具体的には、 \<各バインドのセキュリティ > 要素を調べます。 この要素には `mode` 属性が含まれており、3 つの値のいずれか (`Message`、`Transport`、または `TransportWithMessageCredential`) に設定できます。 この属性の値によってモードが決定され、このモードによってどの子要素が有効なのかが決定されます。  
  
 要素に`<transport>`は、要素また`<message>`は要素のいずれか、またはその両方を含めることができます。 `<security>` セキュリティ モードと一致する要素が有効な要素です。 たとえば、次のコードでは、セキュリティ モードを `"Message"`、`<message>` 要素のクライアント資格情報の種類を `"Certificate"` に指定しています。 この場合、`<transport>` 要素は無視できます。 ただし、`<message>` 要素で X.509 証明書を提示する必要があることが指定されています。  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"   
                      realm="" />  
           <message clientCredentialType="Certificate"   
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"   
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 次の例に示すように、`clientCredentialType` 属性が `"Windows"` に設定されている場合は、実際の資格情報の値を指定する必要はありません。 これは、Windows 統合セキュリティでは、クライアントを実行しているユーザーの実際の資格情報 (Kerberos トークン) が提供されるためです。  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>クライアント資格情報の値の設定  
 クライアントが資格情報を提供する必要があると特定された場合は、クライアントを構成する適切なメソッドを使用します。 たとえば、クライアント証明書を設定するには、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> メソッドを使用します。  
  
 X.509 証明書は広く使用されている資格情報の形式です。 資格情報は次の 2 つの方法で提供できます。  
  
- クライアント コードで (`SetCertificate` メソッドを使用して) プログラミングする方法。  
  
 次に示すように、 `clientCredentials`クライアントの構成ファイルの[ \<動作 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)セクションを追加し、要素を使用します。  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>コードで\<の clientCredentials > 値の設定  
 コードに[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)値を設定するには、 <xref:System.ServiceModel.ClientBase%601>クラスの<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>プロパティにアクセスする必要があります。 このプロパティは、次の表に示すように、各種の資格情報の種類にアクセスできる <xref:System.ServiceModel.Description.ClientCredentials> オブジェクトを返します。  
  
|ClientCredential プロパティ|説明|メモ|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> を返します|クライアントがサービスに対して自身を認証するために提供する X.509 証明書を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|<xref:System.ServiceModel.Security.HttpDigestClientCredential> を返します|HTTP ダイジェスト資格情報を表します。 この資格情報は、ユーザー名とパスワードのハッシュです。|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|<xref:System.ServiceModel.Security.IssuedTokenClientCredential> を返します|フェデレーション シナリオで通常使用される、セキュリティ トークン サービスによって発行されるカスタム セキュリティ トークンを表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|<xref:System.ServiceModel.Security.PeerCredential> を返します|Windows ドメインのピア メッシュに参加するためのピア資格情報を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential> を返します|帯域外ネゴシエーションでサービスによって提供される X.509 証明書を表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential> を返します|ユーザー名とパスワードのペアを表します。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|<xref:System.ServiceModel.Security.WindowsClientCredential> を返します|Windows クライアントの資格情報 (Kerberos 資格情報) を表します。 このクラスのプロパティは読み取り専用です。|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>構成で\<の clientCredentials > 値の設定  
 資格情報の値を指定するには、 [ \<](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)エンドポイントの動作を clientCredentials > 要素の子要素として使用します。 使用される要素は、クライアントの資格情報の種類によって異なります。 たとえば、次の例は、<[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)を使用して x.509 証明書を設定する構成を示しています。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"   
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>              
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 構成でクライアント資格情報を設定するには、 [ \<endpointbehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)要素を構成ファイルに追加します。 さらに、次の例に示すように、追加された behavior `behaviorConfiguration`要素は、 [ \<クライアント > 要素\<のエンドポイント >](../configure-apps/file-schema/wcf/endpoint-of-client.md)の属性を使用して、サービスのエンドポイントにリンクされている必要があります。 `behaviorConfiguration` 属性の値は、動作の `name` 属性の値と一致する必要があります。  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> クライアント資格情報の値の中には、アプリケーション構成ファイルを使用して設定できないものがあります (ユーザー名とパスワードや、Windows ユーザーとパスワードの値など)。 このような資格情報の値は、コードでのみ指定できます。  
  
 クライアント資格情報の設定の詳細について[は、「」を参照してください。クライアント資格情報の](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)値を指定します。  
  
> [!NOTE]
> 次の構成例に示すように、`ClientCredentialType` が `SecurityMode` に設定されている場合、`"TransportWithMessageCredential",` は無視されます。  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"   
               establishSecurityContext="false"    
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)
- [構成エディター ツール (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)
- [WCF クライアントを使用したサービスへのアクセス](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [方法: クライアント資格情報の値の指定](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [方法: クライアント資格情報の種類を指定します](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
