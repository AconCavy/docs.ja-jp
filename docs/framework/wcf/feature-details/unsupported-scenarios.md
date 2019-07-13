---
title: サポートされていないシナリオ
ms.date: 03/30/2017
ms.assetid: 72027d0f-146d-40c5-9d72-e94392c8bb40
ms.openlocfilehash: 884349739730510c356e1efc1f866d146f6ed946
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959957"
---
# <a name="unsupported-scenarios"></a>サポートされていないシナリオ
さまざまな理由は、Windows Communication Foundation (WCF) は一部の特定のセキュリティ シナリオをサポートしていません。 たとえば、 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] Home Edition は SSPI または Kerberos 認証プロトコルを実装していないため WCF サポートしていないプラットフォームで Windows 認証を使用したサービスを実行します。 ユーザー名/パスワードや HTTP/HTTPS 統合認証などの他の認証メカニズムは、Windows XP Home Edition で WCF を実行している場合にサポートされます。  
  
## <a name="impersonation-scenarios"></a>偽装シナリオ  
  
### <a name="impersonated-identity-might-not-flow-when-clients-make-asynchronous-calls"></a>クライアントが非同期呼び出しを行うと、偽装 ID はフローしない場合がある  
 WCF クライアントが、偽装で Windows 認証を使用して WCF サービスへの非同期呼び出しを行うと、偽装 ID ではなくクライアント プロセスの ID で認証が行われる場合があります。  
  
### <a name="windows-xp-and-secure-context-token-cookie-enabled"></a>Windows XP と有効化されたセキュリティ コンテキスト トークン クッキー  
 WCF が偽装をサポートしていません、<xref:System.InvalidOperationException>が、次の条件が存在する場合にスローされます。  
  
- オペレーティング システムが [!INCLUDE[wxp](../../../../includes/wxp-md.md)] である。  
  
- 認証モードで Windows ID が生成された。  
  
- <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> の <xref:System.ServiceModel.OperationBehaviorAttribute> プロパティが <xref:System.ServiceModel.ImpersonationOption.Required> に設定されます。  
  
- 状態ベースのセキュリティ コンテキスト トークン (SCT: Security Context Token) が作成された (既定では、作成は無効になっています)。  
  
 状態ベースの SCT はカスタム バインドの使用によってのみ作成できます。 詳細については、「[方法 :セキュリティ コンテキストを作成、セキュリティで保護されたセッションのトークン](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md))。コードでトークンを有効にするには、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> メソッドまたは <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> メソッドを使用して、セキュリティ バインディング要素 (<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%28System.Boolean%29?displayProperty=nameWithType> または <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%28System.ServiceModel.Channels.SecurityBindingElement%2CSystem.Boolean%29?displayProperty=nameWithType>) を作成し、`requireCancellation` パラメーターを `false` に設定します。 このパラメーターは、SCT のキャッシュを参照します。 値を `false` に設定することによって、状態ベースの SCT 機能が有効になります。  
  
 または、構成において、<`customBinding`> を作成し、<`security`> 要素を追加して `authenticationMode` 属性に SecureConversation および `requireSecurityContextCancellation` 属性に `true` を設定することによってもトークンが有効になります。  
  
> [!NOTE]
>  上記の要件は限定的です。 たとえば、<xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> は Windows ID を生成するバインド要素を作成しますが、SCT を確立しません。 したがって、`Required` で [!INCLUDE[wxp](../../../../includes/wxp-md.md)] オプションと共に使用できます。  
  
### <a name="possible-aspnet-conflict"></a>考えられる ASP.NET との競合  
 WCF と ASP.NET できます両方を有効にするまたは偽装を無効にします。 ASP.NET では、WCF アプリケーションをホスト、ときに、WCF と ASP.NET の構成設定の間の競合を引き起こすことがあります。 競合が発生した場合、WCF 設定が優先しない限り、<xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A>プロパティに設定されて<xref:System.ServiceModel.ImpersonationOption.NotAllowed>、場合、ASP.NET 偽装設定が優先されます。  
  
### <a name="assembly-loads-may-fail-under-impersonation"></a>偽装を有効にすると、アセンブリの読み込みに失敗する場合がある  
 偽装されたコンテキストにアセンブリを読み込むためのアクセス権がない場合、共通言語ランタイム (CLR: Common Language Runtime) が AppDomain のアセンブリを初めて読み込もうとしたときに、その <xref:System.AppDomain> はエラーをキャッシュします。 この場合、偽装を元に戻した後、元に戻されたコンテキストにアセンブリを読み込むためのアクセス権があったとしても、それ以降のアセンブリの読み込みは失敗します。 これは、ユーザー コンテキストの変更後に、CLR が読み込みを再試行しないためです。 このエラーから回復するには、アプリケーション ドメインを再起動する必要があります。  
  
> [!NOTE]
>  <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> クラスの <xref:System.ServiceModel.Security.WindowsClientCredential> プロパティの既定値は <xref:System.Security.Principal.TokenImpersonationLevel.Identification> です。 ほとんどの場合、ID レベルの偽装コンテキストには、追加のアセンブリを読み込むための権限がありません。 これは既定値であるため、非常に一般的な状態として認識しておく必要があります。 ID レベルの偽装は、偽装プロセスが `SeImpersonate` 権限を持たない場合にも発生します。 詳細については、次を参照してください。[委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)します。  
  
### <a name="delegation-requires-credential-negotiation"></a>委任には資格情報ネゴシエーションが必要  
 委任で Kerberos 認証プロトコルを使用するには、資格情報ネゴシエーションを使用する Kerberos プロトコル ("マルチレッグ" Kerberos または "マルチステップ" Kerberos とも呼ばれます) を実装する必要があります。 資格情報ネゴシエーションを使用しない Kerberos 認証 (ワンショット Kerberos またはシングルレッグ Kerberos とも呼ばれる) を実装した場合は、例外がスローされます。 資格情報ネゴシエーションを実装する方法の詳細については、次を参照してください。 [Windows 認証エラーのデバッグ](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)します。  
  
## <a name="cryptography"></a>暗号  
  
### <a name="sha-256-supported-only-for-symmetric-key-usages"></a>対称キーを使用する場合にのみサポートされる SHA-256  
 WCF には、さまざまな暗号化と、システム指定のバインディングでアルゴリズム スイートを使用して指定できる署名ダイジェスト作成アルゴリズムがサポートしています。 セキュリティを強化は、WCF は、署名ダイジェスト ハッシュを作成するため、セキュア ハッシュ アルゴリズム (SHA) 2 アルゴリズムでは、具体的にはの SHA 256 をサポートします。 このリリースは、Kerberos キーなどの対称キーを使用する場合、およびメッセージに署名するために X.509 証明書を使用しない場合に限り SHA-256 をサポートします。 WCF ではサポートしていません (X.509 証明書で使用する) RSA 署名 rsa-sha256、WinFX で現在のサポートがないのための sha-256 ハッシュを使用します。  
  
### <a name="fips-compliant-sha-256-hashes-not-supported"></a>サポートされていない FIPS 準拠の SHA-256 ハッシュ  
 WCF は sha-256 FIPS 準拠のハッシュをサポートしていないため、システムが FIPS 準拠アルゴリズムの使用が必要な場合の WCF でサポートされていないことを SHA 256 を使用するアルゴリズム スイート。  
  
### <a name="fips-compliant-algorithms-may-fail-if-registry-is-edited"></a>レジストリを編集すると、FIPS 準拠のアルゴリズムが失敗する場合がある  
 連邦情報処理規格 (FIPS: Federal Information Processing Standards) 準拠のアルゴリズムを有効または無効にするには、Microsoft 管理コンソール (MMC: Microsoft Management Console) のローカル セキュリティ設定スナップインを使用します。 レジストリでこの設定にアクセスすることもできます。 ただし、WCF はサポートされないこと、レジストリを使用して、設定をリセットします。 値を 1 または 0 以外に設定すると、CLR とオペレーティング システム間で不整合が発生する可能性があります。  
  
### <a name="fips-compliant-aes-encryption-limitation"></a>FIPS 準拠の AES 暗号化の制限  
 FIPS 準拠の AES 暗号化は、ID レベルの偽装での双方向コールバックでは機能しません。  
  
### <a name="cngksp-certificates"></a>CNG/KSP 証明書  
 *Cryptography API:Next Generation (CNG)* 長期にわたって置き換え、CryptoAPI のです。 この API は、アンマネージ コードで使用できる[!INCLUDE[wv](../../../../includes/wv-md.md)]、[!INCLUDE[lserver](../../../../includes/lserver-md.md)]以降の Windows バージョン。  
  
 .NET framework 4.6.1 と以前のバージョンは、従来の CryptoAPI CNG/KSP 証明書を処理するために使用されるため、これらの証明書をサポートしています。 .NET Framework 4.6.1 と以前のバージョンでこれらの証明書の使用には、例外が発生します。  
  
 証明書に KSP が使用されているかどうかを知る方法は 2 つあります。  
  
- `p/invoke` を `CertGetCertificateContextProperty` に対して実行し、返された `dwProvType` で `CertGetCertificateContextProperty` を調べる。  
  
- 使用して、`certutil`証明書を調べるためのコマンドラインからコマンド。 詳細については、次を参照してください。[証明書のトラブルシューティングに関する Certutil タスク](https://go.microsoft.com/fwlink/?LinkId=120056)します。  
  
## <a name="message-security-fails-if-using-aspnet-impersonation-and-aspnet-compatibility-is-required"></a>ASP.NET の偽装と ASP.NET 互換を使用する必要がある場合にメッセージ セキュリティが失敗する  
 WCF では、クライアント認証を防止するため、次の設定の組み合わせはサポートされません。  
  
- ASP.NET の偽装が有効になっているとします。 これを行うには、Web.config ファイルで <`identity`> 要素の `impersonate` 属性を `true` に設定します。  
  
- ASP.NET 互換モードが有効になって、`aspNetCompatibilityEnabled`の属性、 [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)に`true`します。  
  
- メッセージ モード セキュリティを使用している。  
  
 回避は、ASP.NET 互換モードをオフにします。 または、ASP.NET 互換モードが必要な場合は、ASP.NET の偽装機能を無効にして、WCF が提供する偽装の代わりに使用します。 詳細については、次を参照してください。[委任と偽装](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)します。  
  
## <a name="ipv6-literal-address-failure"></a>IPv6 リテラル アドレス エラー  
 クライアントとサービスが同じコンピューター上に存在し、サービスに対して IPv6 リテラル アドレスが使用されている場合は、セキュリティ要求が失敗します。  
  
 IPv6 リテラル アドレスは、サービスとクライアントがそれぞれ異なるコンピューター上に存在する場合に機能します。  
  
## <a name="wsdl-retrieval-failures-with-federated-trust"></a>フェデレーション信頼での WSDL 取得エラー  
 WCF では、フェデレーション信頼チェーン内の各ノードの 1 つだけの WSDL ドキュメントが必要です。 エンドポイントを指定するときにループにならないように注意する必要があります。 ループになる場合の例の 1 つは、フェデレーション信頼チェーンの WSDL ダウンロードの使用で、同じ WSDL ドキュメントの中に複数のリンクがある場合です。 この問題がよく発生するシナリオは、セキュリティ トークン サーバーとセキュリティ トークン サービスが同じ ServiceHost の中にあるフェデレーション サービスです。  
  
 そのような状況の例は次の 3 つのエンドポイント アドレスを使うサービスです。  
  
- `http://localhost/CalculatorService/service` (サービス)  
  
- `http://localhost/CalculatorService/issue_ticket` (STS)  
  
- `http://localhost/CalculatorService/mex` (メタデータ エンドポイント)  
  
 これによって例外がスローされます。  
  
 このシナリオでエラーを避けるには、`issue_ticket` エンドポイントを別のところに置きます。  
  
## <a name="wsdl-import-attributes-can-be-lost"></a>WSDL インポート属性が失われる可能性  
 WSDL インポートの際に、WCF は `<wst:Claims>` テンプレート内の `RST` 要素にあるインポート属性を追跡できなくなることがあります。 これは、クレームの種類のコレクションを直接使用する代わりに `<Claims>` を直接 `WSFederationHttpBinding.Security.Message.TokenRequestParameters` または `IssuedSecurityTokenRequestParameters.AdditionalRequestParameters` 内で指定した場合に、WSDL インポートの際に発生します。  インポートが属性を失うので、WSDL を介して正しいバインディングのラウンド トリップが行われません。したがって、クライアント側で不適切になります。  
  
 解決策は、インポートを行った後、クライアント側で直接バインディングを変更することです。  
  
## <a name="see-also"></a>関連項目

- [セキュリティの考慮事項](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [情報の漏えい](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [権限の昇格](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [サービス拒否](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [改変](../../../../docs/framework/wcf/feature-details/tampering.md)
- [リプレイ攻撃](../../../../docs/framework/wcf/feature-details/replay-attacks.md)
