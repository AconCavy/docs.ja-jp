---
title: エンドポイント アドレス
ms.date: 03/30/2017
helpviewer_keywords:
- addresses [WCF]
- Windows Communication Foundation [WCF], addresses
- WCF [WCF], addresses
ms.assetid: 13f269e3-ebb1-433c-86cf-54fbd866a627
ms.openlocfilehash: a59e47e529a5002c806e37dba7267b2cf8318a35
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64912711"
---
# <a name="endpoint-addresses"></a>エンドポイント アドレス
すべてのエンドポイントにはこれと関連するアドレスがあり、エンドポイントの検索と識別に使用されます。 このアドレスは主にエンドポイントの位置を指定する URI (Uniform Resource Identifier) で構成されます。 エンドポイント アドレスが、Windows Communication Foundation (WCF) のプログラミング モデルで表される、<xref:System.ServiceModel.EndpointAddress>クラスを含む、省略可能な<xref:System.ServiceModel.EndpointAddress.Identity%2A>他のエンドポイントによるエンドポイントの認証を有効にするプロパティをメッセージをおよび一連の省略可能な交換<xref:System.ServiceModel.EndpointAddress.Headers%2A>プロパティで、サービスに到達するために必要な SOAP ヘッダーを定義します。 オプションのヘッダーは、サービス エンドポイントの識別または対話のために、より詳細なアドレス指定情報を提供します。 エンドポイントのアドレスは、ネットワーク上では WS-Addressing エンドポイント参照 (EPR) として表されます。  
  
## <a name="uri-structure-of-an-address"></a>アドレスの URI 構造  
 ほとんどのトランスポートの URI アドレスは、4 つの部分から構成されます。 URI の 4 つの部分ではたとえば、 `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` 次のように取り上げることができます。  
  
- スキーム: `http:`
  
- マシンの場合: `www.fabrikam.com`  
  
- (省略可能)ポート:322  
  
- パス : /mathservice.svc/secureEndpoint  
  
## <a name="defining-an-address-for-a-service"></a>サービスのアドレスの定義  
 サービスのエンドポイント アドレスは、コードを使用して命令的に、または構成を通じて宣言的に指定できます。 設置済みサービスのバインドおよびアドレスは一般的に、サービスの開発中に使用されるものとは異なるので、コード内でエンドポイントを定義することは通常、実用的ではありません。 一般に、サービス エンドポイントの定義にはコードではなく、構成を使用する方がより実用的です。 バインディング情報とアドレス情報をコードに含めないことで、変更時にアプリケーションの再コンパイルや再展開を行う必要がなくなります。  
  
### <a name="defining-an-address-in-configuration"></a>構成によるアドレス定義  
 構成ファイルでエンドポイントを定義するには、使用、 [\<エンドポイント >](../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)要素。 詳細と例では、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)します。  
  
### <a name="defining-an-address-in-code"></a>コードによるアドレス定義  
 エンドポイント アドレスは、コードで <xref:System.ServiceModel.EndpointAddress> クラスを使用して作成できます。 詳細と例では、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)します。  
  
### <a name="endpoints-in-wsdl"></a>WSDL のエンドポイント  
 エンドポイント アドレスは、対応するエンドポイントの `wsdl:port` 要素内の WS-Addressing EPR 要素として WSDL で表すこともできます。 EPR には、エンドポイントのアドレスのほかに、アドレスのすべてのプロパティが含まれます。 詳細と例では、次を参照してください。[エンドポイント アドレスを指定する](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)します。  
  
## <a name="multiple-iis-binding-support-in-net-framework-35"></a>複数の IIS バインディングで .NET Framework 3.5 のサポート  
 インターネット サービス プロバイダーは、多くの場合、サイトの密度を高めて総所有コストを抑えるため、同じサーバーまたはサイト上で複数のアプリケーションをホストしています。 通常、これらのアプリケーションは、異なるベース アドレスにバインドされています。 インターネット インフォメーション サービス (IIS) Web サイトは、複数のアプリケーションを格納できます。 サイト内のアプリケーションに、1 つ以上の IIS バインディングからアクセスできます。  
  
 IIS バインディングは、バインディング プロトコルとバインディング情報という 2 つの情報を提供します。 バインディング プロトコルは通信を行うスキームを定義するもので、バインディング情報はサイトにアクセスするために使用する情報です。  
  
 IIS バインディングに使用されるコンポーネントの例を次に示します。  
  
- バインディング プロトコル。HTTP  
  
- バインド情報。IP アドレス、ポート、ホスト ヘッダー  
  
 IIS ではサイトごとに複数の IIS バインディングを指定でき、これによりスキームごとに複数のベース アドレスをサポートできます。 前のバージョン[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)]、WCF はスキーマの複数のアドレスをサポートされていませんでしたし、指定された場合にスロー、<xref:System.ArgumentException>アクティブ化時にします。  
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] により、インターネット サービス プロバイダーは同じサイト上の同じスキームに対して別のベース アドレスを使用して複数のアプリケーションをホストできます。  
  
 たとえば、サイトで次のベース アドレスを使用できます。  
  
- `http://payroll.myorg.com/Service.svc`
  
- `http://shipping.myorg.com/Service.svc`
  
 [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] では、構成ファイルの AppDomain レベルでプレフィックス フィルターを指定できます。 これには、 [ \<baseAddressPrefixFilters >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)要素で、プレフィックスの一覧が含まれています。 IIS によって指定される受信ベース アドレスは、オプションのプレフィックス一覧に基づいてフィルター処理されます。 既定では、プレフィックスを指定しない場合、すべてのアドレスが渡されます。 プレフィックスを指定すると、そのスキームに一致するベース アドレスだけが渡されます。  
  
 プレフィックス フィルターを使用する構成コード例を次に示します。  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://payroll.myorg.com:8000"/>  
        <add prefix="http://shipping.myorg.com:8000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 前の例では、`net.tcp://payroll.myorg.com:8000`と`http://shipping.myorg.com:8000`経由で渡される、それぞれのスキーム、唯一のベース アドレスします。  
  
 `baseAddressPrefixFilter` では、ワイルカードはサポートされません。  
  
 IIS が提供するベース アドレスには、`baseAddressPrefixFilters` 一覧に存在しない他のスキームにバインドされたアドレスが指定される場合があります。 これらのアドレスはフィルターで除外されません。  
  
## <a name="multiple-iis-binding-support-in-net-framework-4-and-later"></a>.NET Framework 4 以降での複数の IIS バインディングのサポート  
 .NET 4 以降、<xref:System.ServiceModel.ServiceHostingEnvironment> の <xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A> 設定を true に設定するだけで、1 つのベース アドレスを選択しなくても、IIS で複数のバインディングのサポートが有効になります。 このサポートは、HTTP プロトコル スキームに限定されます。  
  
 MultipleSiteBindingsEnabled を使用する構成コードの例を次に[ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)します。  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment multipleSiteBindingsEnabled="true" >  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 複数のサイト バインディングがこの設定を使用して有効になっている場合、HTTP プロトコルと非 HTTP プロトコルの両方について、baseAddressPrefixFilters 設定は無視されます。  
  
 詳細と例については、次を参照してください。[複数の IIS サイト バインディングをサポートしている](../../../../docs/framework/wcf/feature-details/supporting-multiple-iis-site-bindings.md)と<xref:System.ServiceModel.ServiceHostingEnvironment.MultipleSiteBindingsEnabled%2A>します。  
  
## <a name="extending-addressing-in-wcf-services"></a>WCF サービスによるアドレスの拡張  
 既定のアドレス指定の WCF サービスのモデルでは、次の目的のエンドポイント アドレス URI を使用します。  
  
- サービスがリッスンするアドレス、つまりエンドポイントがメッセージをリッスンする位置の指定  
  
- SOAP アドレス フィルター、つまりエンドポイントが SOAP ヘッダーとして待機するアドレスの指定  
  
 これらの目的で使用する値は個別に指定することができるため、アドレス指定の拡張が可能になり、次に示すような役に立つシナリオに対応します。  
  
- SOAP 中継局 : クライアントが送信したメッセージは、最終目的地に到達する前にメッセージを処理する 1 つ以上の追加サービスを経由します。 SOAP 中継局は、メッセージのキャッシュ、ルーティング、負荷分散、スキーム検証など多様なタスクを実行できます。 このシナリオは、最終的な送信先である論理アドレス (`via`) ではなく、中継局を目的とする独立した物理アドレス (`wsa:To`) にメッセージを送信することによって実現されます。  
  
- エンドポイントがリッスンするアドレスはプライベート URI であり、`listenURI` プロパティとは異なる値が設定されます。  
  
 `via` が指定するトランスポート アドレスはメッセージが最初に送信される場所で、この後にメッセージは、`to` パラメーターによって指定された、サービスが存在する別のリモート アドレスに送信されます。 インターネットの場合、`via` URI は、サービスの最終的な <xref:System.ServiceModel.EndpointAddress.Uri%2A> アドレスの `to` プロパティと同じになります。 この 2 つのアドレスを区別するのは、手動ルーティングを行う必要がある場合のみです。  
  
### <a name="addressing-headers"></a>ヘッダーのアドレス指定  
 エンドポイントは、基本となる URI だけでなく、1 つ以上の SOAP ヘッダーによってアドレス指定することもできます。 これが役に立つのは、エンドポイントのクライアントに中継局を指す SOAP ヘッダーを含める必要がある、SOAP 中継局のシナリオの場合です。  
  
 カスタムのアドレス ヘッダーは、コードまたは構成のいずれかを使用して次のように定義できます。  
  
- コードを使用する場合、カスタムのアドレス ヘッダーは <xref:System.ServiceModel.Channels.AddressHeader> クラスを使用して作成し、<xref:System.ServiceModel.EndpointAddress> の構築時に使用されます。  
  
- 構成でカスタム[\<ヘッダー >](../../configure-apps/file-schema/wcf/headers.md)の子として指定されて、 [\<エンドポイント >](../../configure-apps/file-schema/wcf/endpoint-of-client.md)要素。  
  
 配置後もヘッダーを変更できるため、コードよりも構成を使用する方法を一般的にお勧めします。  
  
### <a name="custom-listening-addresses"></a>カスタム リッスン アドレス  
 リッスンするアドレスには、エンドポイントの URI とは異なる値を設定できます。 これは、SOAP アドレスがパブリックな SOAP 中継局として公開される一方、エンドポイントが実際にリッスンするアドレスはプライベートなネットワーク アドレスであるような中継局シナリオの場合に便利です。  
  
 カスタム リッスン アドレスは、コードまたは構成のいずれかを使用して指定できます。  
  
- コードを使用する場合、カスタム リッスン アドレスはエンドポイントの動作コレクションに <xref:System.ServiceModel.Description.ClientViaBehavior> クラスを追加して指定します。  
  
- 構成では、カスタム リッスン アドレスを指定します、`ListenUri`サービスの属性[\<エンドポイント >](../../configure-apps/file-schema/wcf/endpoint-element.md)要素。  
  
### <a name="custom-soap-address-filter"></a>カスタム SOAP アドレス フィルター  
 エンドポイントの SOAP アドレス フィルター (<xref:System.ServiceModel.EndpointAddress.Uri%2A>) を定義するには、<xref:System.ServiceModel.EndpointAddress.Headers%2A> に任意の <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> プロパティを組み合わせて使用します。 既定では、このフィルターは受信メッセージの `To` メッセージ ヘッダーが、エンドポイントの URI に一致し、必要なすべてのエンドポイント ヘッダーがメッセージ内に存在していることを検証します。  
  
 シナリオによっては、適切な `To` ヘッダーを持つメッセージだけではなく、基になるトランスポートに到着したすべてのメッセージをエンドポイントで受信します。 これを行うには、ユーザーは <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> クラスを使用します。  
  
## <a name="see-also"></a>関連項目

- [エンドポイント アドレスの指定](../../../../docs/framework/wcf/specifying-an-endpoint-address.md)
- [サービス ID と認証](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
