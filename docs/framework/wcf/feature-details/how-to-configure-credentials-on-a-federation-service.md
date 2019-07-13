---
title: '方法: フェデレーション サービスで資格情報を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 149ab165-0ef3-490a-83a9-4322a07bd98a
ms.openlocfilehash: 7b09578bf39a081b1bed83614cff755f234f8e45
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487097"
---
# <a name="how-to-configure-credentials-on-a-federation-service"></a>方法: フェデレーション サービスで資格情報を設定する
Windows Communication Foundation (WCF) では、フェデレーション サービスを作成する、次の主な手順で構成されます。  
  
1. <xref:System.ServiceModel.WSFederationHttpBinding> または同様のカスタム バインディングの構成。 適切なバインディングを作成する方法の詳細については、次を参照してください。[方法。WSFederationHttpBinding を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)です。  
  
2. サービスに提示される発行済みトークンの認証方法を制御する <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> の構成。  
  
 このトピックでは、2 番目の手順について詳しく説明します。 フェデレーション サービスの動作方法の詳細については、次を参照してください。[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)します。  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-code"></a>コードで IssuedTokenServiceCredential のプロパティを設定するには  
  
1. <xref:System.ServiceModel.Description.ServiceCredentials.IssuedTokenAuthentication%2A> クラスの <xref:System.ServiceModel.Description.ServiceCredentials> プロパティを使用して、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential> インスタンスへの参照を返します。 このプロパティは、<xref:System.ServiceModel.ServiceHostBase.Credentials%2A> クラスの <xref:System.ServiceModel.ServiceHostBase> プロパティからアクセスされます。  
  
2. 設定、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A>プロパティを`true`CardSpace カードなど自己発行のトークンが認証される場合。 既定値は `false` です。  
  
3. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> プロパティによって返されるコレクションに <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> クラスのインスタンスを設定します。 各インスタンスは、サービスが認証を行うトークンの発行者を表します。  
  
    > [!NOTE]
    >  <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A> プロパティによって返されるクライアント側のコレクションとは異なり、既知の証明書コレクションはキー付きのコレクションではありません。 指定した証明書が発行するトークンは、発行済みトークンを含むメッセージを送信したクライアントのアドレスとは無関係に、サービスによって受け入れられます (その他の制約については以下で説明します)。  
  
4. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> プロパティを <xref:System.ServiceModel.Security.X509CertificateValidationMode> 列挙値のいずれかに設定します。 これは、コードでのみ設定することができます。 既定値は <xref:System.IdentityModel.Selectors.X509CertificateValidator.ChainTrust%2A> です。  
  
5. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> プロパティが <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> に設定されている場合、カスタム <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスのインスタンスを <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CustomCertificateValidator%2A> プロパティに割り当てます。  
  
6. <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> が `ChainTrust` または `PeerOrChainTrust` に設定されている場合、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.RevocationMode%2A> プロパティを <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 列挙値にある適切な値に設定します。 失効モードは `PeerTrust` または `Custom` 検証モードでは使用されないことに注意してください。  
  
7. 必要に応じて、カスタム <xref:System.IdentityModel.Tokens.SamlSerializer> クラスのインスタンスを <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.SamlSerializer%2A> プロパティに割り当てます。 カスタム SAML (Security Assertions Markup Language) アサーションの解析などには、カスタム SAML シリアライザーが必要です。  
  
### <a name="to-set-the-properties-of-issuedtokenservicecredential-in-configuration"></a>構成で IssuedTokenServiceCredential のプロパティを設定するには  
  
1. 作成、`<issuedTokenAuthentication>`要素の子として、<`serviceCredentials`> 要素。  
  
2. 設定、`allowUntrustedRsaIssuers`の属性、`<issuedTokenAuthentication>`要素`true`CardSpace カードなどの自己発行されたトークンを認証する場合。  
  
3. `<knownCertificates>` 要素の子要素として `<issuedTokenAuthentication>` 要素を作成します。  
  
4. `<add>` 要素の子要素として 0 個以上の `<knownCertificates>` 要素を作成し、`storeLocation`、`storeName`、`x509FindType`、および `findValue` 属性を使用して証明書の検索方法を指定します。  
  
5. 必要に応じて、設定、`samlSerializer`の属性、<`issuedTokenAuthentication`> 要素、カスタムの型名を<xref:System.IdentityModel.Tokens.SamlSerializer>クラス。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential> のプロパティをコードで設定しています。  
  
 [!code-csharp[C_FederatedService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federatedservice/cs/source.cs#2)]
 [!code-vb[C_FederatedService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federatedservice/vb/source.vb#2)]  
  
 クライアントがフェデレーション サービスによって認証されるためには、発行済みトークンが次のことを満たす必要があります。  
  
- 発行済みトークンのデジタル署名が RSA セキュリティ キー識別子を使用している場合、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowUntrustedRsaIssuers%2A> プロパティを `true` にする必要があります。  
  
- 発行済みトークンの署名に X.509 発行者シリアル番号、X.509 サブジェクト キー識別子、または X.509 拇印セキュリティ識別子が使用されている場合、発行済みトークンは <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> クラスの <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> プロパティによって返されたコレクションにある証明書で署名されている必要があります。  
  
- 発行済みトークンが X.509 証明書を使用して署名されている場合、証明書が <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> として証明書利用者に送信されたか、<xref:System.IdentityModel.Tokens.X509RawDataKeyIdentifierClause> プロパティから取得されたかに関係なく、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A> プロパティの値で指定されるセマンティックスごとに証明書を検証する必要があります。 X.509 証明書の検証の詳細については、次を参照してください。 [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)します。  
  
 たとえば、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A> を <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerTrust> に設定すると、その署名の証明書が `TrustedPeople` 証明書ストアに格納されている任意の発行済みトークンが認証されます。 この場合、<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.TrustedStoreLocation%2A> プロパティを <xref:System.Security.Cryptography.X509Certificates.StoreLocation.CurrentUser> または <xref:System.Security.Cryptography.X509Certificates.StoreLocation.LocalMachine> に設定します。 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> を含めて、他のモードを選択できます。 `Custom` を選択した場合、<xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスのインスタンスを <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CustomCertificateValidator%2A> プロパティに割り当てる必要があります。 カスタム検証では、任意の基準を使用して証明書を検証できます。 詳細については、「[方法 :カスタム証明書の検証を使用するサービスを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)します。  
  
## <a name="see-also"></a>関連項目

- [フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)
- [フェデレーションと信頼](../../../../docs/framework/wcf/feature-details/federation-and-trust.md)
- [フェデレーション サンプル](../../../../docs/framework/wcf/samples/federation-sample.md)
- [方法: WSFederationHttpBinding のセキュリティで保護されたセッションを無効にします。](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [方法: WSFederationHttpBinding を作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
- [方法: フェデレーション クライアントを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)
