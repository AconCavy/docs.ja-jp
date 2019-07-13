---
title: WCF Web HTTP プログラミング オブジェクト モデル
ms.date: 03/30/2017
ms.assetid: ed96b5fc-ca2c-4b0d-bdba-d06b77c3cb2a
ms.openlocfilehash: 2401a8a051ed4dcd386c7794a2197672709ea423
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487689"
---
# <a name="wcf-web-http-programming-object-model"></a>WCF Web HTTP プログラミング オブジェクト モデル
WCF WEB HTTP プログラミング モデルでは、SOAP は必要ありません、基本的な HTTP 要求から、Windows Communication Foundation (WCF) Web サービスを公開できます。 WCF WEB HTTP プログラミング モデルは、既存の WCF 機能拡張モデル上に構築されます。 Web HTTP プログラミング モデルでは、次のクラスが定義されます。  
  
 **プログラミング モデル:**  
  
- <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>  
  
- <xref:System.ServiceModel.Web.WebGetAttribute>  
  
- <xref:System.ServiceModel.Web.WebInvokeAttribute>  
  
- <xref:System.ServiceModel.Web.WebServiceHost>  
  
 **チャネルおよびディスパッチャー インフラストラクチャ:**  
  
- <xref:System.ServiceModel.WebHttpBinding>  
  
- <xref:System.ServiceModel.Description.WebHttpBehavior>  
  
 **ユーティリティ クラスと機能拡張ポイント:**  
  
- <xref:System.UriTemplate>  
  
- <xref:System.UriTemplateTable>  
  
- <xref:System.ServiceModel.Dispatcher.QueryStringConverter>  
  
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>  
  
## <a name="aspnetcacheprofileattribute"></a>AspNetCacheProfileAttribute  
 <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> は、サービス操作に適用された場合に、構成ファイル内の ASP.NET 出力キャッシュ プロファイルを示します。この構成ファイルを使用して ASP .NET 出力キャッシュに操作の応答がキャッシュされます。 このプロパティが受け取るパラメーターは 1 つ (構成ファイルでキャッシュ設定を指定するキャッシュ プロファイル名) だけです。  
  
## <a name="webgetattribute"></a>WebGetAttribute  
 <xref:System.ServiceModel.Web.WebGetAttribute> 属性は、サービス操作を HTTP GET 要求に応答する操作としてマークするために使用されます。 メタデータを操作の説明に追加する受信操作の動作です (<xref:System.ServiceModel.Description.IOperationBehavior> メソッドは何の処理も行いません)。 このメタデータを操作の説明で検索する動作 (特に <xref:System.ServiceModel.Web.WebGetAttribute>) がサービスの動作コレクションに追加されていない場合は、<xref:System.ServiceModel.Description.WebHttpBehavior> を適用しても機能しません。 <xref:System.ServiceModel.Web.WebGetAttribute> 属性には、次の表に示すパラメーターをオプションで指定できます。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`BodyStyle`|属性が適用されているサービス操作との間で送受信される要求と応答をラップするかどうかを制御します。|  
|`RequestFormat`|要求メッセージの書式設定方法を制御します。|  
|`ResponseFormat`|応答メッセージの書式設定方法を制御します。|  
|`UriTemplate`|属性が適用されているサービス操作にマップされた HTTP 要求を制御する URI テンプレートを指定します。|  
  
## <a name="webhttpbinding"></a>WebHttpBinding  
 <xref:System.ServiceModel.WebHttpBinding> クラスは、<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> を使用して、XML、JSON、および生のバイナリ データのサポートを組み込みます。 これは、<xref:System.ServiceModel.Channels.HttpsTransportBindingElement>、<xref:System.ServiceModel.Channels.HttpTransportBindingElement>、および <xref:System.ServiceModel.WebHttpSecurity> オブジェクトから構成されています。 <xref:System.ServiceModel.WebHttpBinding> は、<xref:System.ServiceModel.Description.WebHttpBehavior> と組み合わせて使用するようにデザインされています。  
  
## <a name="webinvokeattribute"></a>WebInvokeAttribute  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性は <xref:System.ServiceModel.Web.WebGetAttribute> 属性によく似ていますが、サービス操作を GET 以外の HTTP 要求に応答する操作としてマークするために使用されます。 メタデータを操作の説明に追加する受信操作の動作です (<xref:System.ServiceModel.Description.IOperationBehavior> メソッドは何の処理も行いません)。 このメタデータを操作の説明で検索する動作 (特に <xref:System.ServiceModel.Web.WebInvokeAttribute>) がサービスの動作コレクションに追加されていない場合は、<xref:System.ServiceModel.Description.WebHttpBehavior> を適用しても機能しません。  
  
 <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性には、次の表に示すパラメーターをオプションで指定できます。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`BodyStyle`|属性が適用されているサービス操作との間で送受信される要求と応答をラップするかどうかを制御します。|  
|`Method`|サービス操作がマップされる HTTP メソッドを指定します。|  
|`RequestFormat`|要求メッセージの書式設定方法を制御します。|  
|`ResponseFormat`|応答メッセージの書式設定方法を制御します。|  
|`UriTemplate`|属性が適用されているサービス操作にマップされた GET 要求を制御する URI テンプレートを指定します。|  
  
## <a name="uritemplate"></a>UriTemplate  
 <xref:System.UriTemplate> クラスでは、構造が似ている URI のセットを定義できます。 テンプレートは、パスとクエリの 2 つの部分から構成されています。 パスは、スラッシュ (/) で区切られた一連のセグメントから構成されています。 各セグメントはリテラル値、変数の値 (書き込まれる中かっこ [{}] 内で正確に 1 つのセグメントの内容と一致する制約)、またはワイルドカードを持つことができます (アスタリスクのように [\*]、「残りのパス」に一致する) に表示される必要がありますパスの末尾。 クエリ式は、すべて省略することができます。 存在する場合、クエリ式は順序なしの一連の名前/値ペアを指定します。 クエリ式の要素は、リテラル ペア (ですか? x = 2) または変数ペア (? x = {*値*})。 対になっていない値は使用できません。 <xref:System.UriTemplate> 内部的に使用で WCF WEB HTTP プログラミング モデルで特定の Uri や Uri のグループをサービス操作にマップします。  
  
## <a name="uritemplatetable"></a>UriTemplateTable  
 <xref:System.UriTemplateTable> クラスは、開発者が選択したオブジェクトにバインドされた <xref:System.UriTemplate> オブジェクトの結合セットを表します。 これにより、セット内のテンプレートと候補 URI (Uniform Resource Identifier) を照合し、一致したテンプレートに関連付けられているデータを取得することができます。 <xref:System.UriTemplateTable> 内部的に使用で WCF WEB HTTP プログラミング モデルで特定の Uri や Uri のグループをサービス操作にマップします。  
  
## <a name="webservicehost"></a>WebServiceHost  
 <xref:System.ServiceModel.Web.WebServiceHost> は <xref:System.ServiceModel.ServiceHost> を拡張するため、SOAP 以外の Web スタイル サービスを容易にホストできます。 <xref:System.ServiceModel.Web.WebServiceHost> では、サービスの説明にエンドポイントが見つからない場合、サービスのベース アドレスに既定のエンドポイントを自動的に作成します。 既定の HTTP エンドポイントを作成するときに、<xref:System.ServiceModel.Web.WebServiceHost> は、HTTP ヘルプ ページと Web サービス記述言語 (WSDL) GET 機能を無効にして、メタデータ エンドポイントが既定の HTTP エンドポイントに干渉しないようにします。 また、<xref:System.ServiceModel.Web.WebServiceHost> は、<xref:System.ServiceModel.WebHttpBinding> を使用するすべてのエンドポイントに必要な <xref:System.ServiceModel.Description.WebHttpBehavior> がアタッチされるようにもします。 最後に、<xref:System.ServiceModel.Web.WebServiceHost> は、エンドポイントのバインディングを、安全な仮想ディレクトリで使用するときに、関連付けられたインターネット インフォメーション サービス (IIS) のセキュリティ設定と連携して動作するよう自動的に構成します。  
  
## <a name="webservicehostfactory"></a>WebServiceHostFactory  
 <xref:System.ServiceModel.Activation.WebServiceHostFactory> クラスは、サービスがインターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) でホストされている場合に、<xref:System.ServiceModel.Web.WebServiceHost> を動的に作成するために使用されます。 ホスト アプリケーションが <xref:System.ServiceModel.Web.WebServiceHost> をインスタンス化する自己ホスト型サービスとは異なり、IIS または WAS でホストされているサービスは、このクラスを使用してサービスの <xref:System.ServiceModel.Web.WebServiceHost> を作成します。 <xref:System.ServiceModel.Activation.WebServiceHostFactory.CreateServiceHost%28System.Type%2CSystem.Uri%5B%5D%29> メソッドは、サービスの受信要求の受信時に呼び出されます。  
  
## <a name="webhttpbehavior"></a>WebHttpBehavior  
 <xref:System.ServiceModel.Description.WebHttpBehavior> クラスは、必要なフォーマッタ、操作セレクターなど、サービス モデル レイヤーで Web スタイル サービスをサポートするために必要な内容を提供します。 このパラメーターは (<xref:System.ServiceModel.WebHttpBinding> と共に使用される) エンドポイントの動作として実装され、これにより、フォーマッタと操作セレクターを各エンドポイントに指定できるようになり、さらに、同じサービス実装で SOAP エンドポイントと POX エンドポイントの両方を公開できるようになります。  
  
### <a name="extending-webhttpbehavior"></a>WebHttpBehavior の拡張  
 <xref:System.ServiceModel.Description.WebHttpBehavior> は、仮想メソッド <xref:System.ServiceModel.Description.WebHttpBehavior.GetOperationSelector%28System.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestClientFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、<xref:System.ServiceModel.Description.WebHttpBehavior.GetReplyDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29>、および <xref:System.ServiceModel.Description.WebHttpBehavior.GetRequestDispatchFormatter%28System.ServiceModel.Description.OperationDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%29> を使用して拡張できます。 開発者は、<xref:System.ServiceModel.Description.WebHttpBehavior> から派生クラスを作成し、そのメソッドをオーバーライドして既定の動作をカスタマイズすることができます。  
  
 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> は、<xref:System.ServiceModel.Description.WebHttpBehavior> 拡張の一例です。 <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> ブラウザー ベースの ASP.NET AJAX クライアントから HTTP 要求を受信する Windows Communication Foundation (WCF) エンドポイントを有効にします。 [AJAX サービスを使用して HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)この機能拡張ポイントを使用しての例を示します。  
  
> [!WARNING]
>  <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> を使用する場合、<xref:System.UriTemplate> は、<xref:System.ServiceModel.Web.WebGetAttribute> または <xref:System.ServiceModel.Web.WebInvokeAttribute> 属性内でサポートされません。  
  
## <a name="webhttpdispatchoperationselector"></a>WebHttpDispatchOperationSelector  
 <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector> クラスは、<xref:System.UriTemplate> クラスおよび <xref:System.UriTemplateTable> クラスを使用して、サービス操作に対して呼び出しをディスパッチします。  
  
## <a name="compatibility"></a>互換性  
 WCF WEB HTTP プログラミング モデルを選択し、SOAP ベースのメッセージを使用しないため、サポートされません、ws-* プロトコル。 ただし、SOAP を使用するエンドポイントと SOAP を使用しないその他のエンドポイントの 2 つの異なるエンドポイントを使用して、同じコントラクトを公開できます。 「[方法:コントラクトを SOAP および Web クライアントに公開](../../../../docs/framework/wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)例についてはします。  
  
## <a name="security"></a>セキュリティ  
 WCF WEB HTTP プログラミング モデルはサポートされていません、ws-* プロトコルが WCF WEB HTTP プログラミング モデル上に構築された Web サービスをセキュリティで保護する唯一の方法は、SSL を使用して、サービスを公開します。 IIS 7.0 で SSL の設定の詳細については、次を参照してください[IIS に SSL を実装する方法。](https://go.microsoft.com/fwlink/?LinkId=131613)  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.WebHttpBinding>
- <xref:System.ServiceModel.Web.WebGetAttribute>
- <xref:System.ServiceModel.Web.WebInvokeAttribute>
- <xref:System.ServiceModel.Description.WebHttpBehavior>
- <xref:System.ServiceModel.Dispatcher.WebHttpDispatchOperationSelector>
- [WCF Web HTTP プログラミング モデルの概要](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
