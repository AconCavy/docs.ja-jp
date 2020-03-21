---
title: <transport> の <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: 1cb165fed9266307335482166116c4c1d62efe7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152958"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<\<トランスポート>を指定する>
メッセージ キュー統合トランスポートのセキュリティ設定を定義します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<システム.サービスモデル>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<バインディング>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>をバインドします。**](msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<バインド>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<セキュリティ>**](security-of-msmqintegrationbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<輸送>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|MSMQ トランスポートによるメッセージの認証方法を指定します。 これが `None` に設定されている場合、`msmqProtectionLevel` 属性の値も `None` に設定する必要があります。<br /><br /> 有効な値は次のとおりです。<br /><br /> - なし: 認証なし。<br />- Windows ドメイン: 認証メカニズムは、Active Directory を使用して、メッセージに関連付けられた SID の X.509 証明書を取得します。 次に、これを使用してキューの ACL がチェックされ、ユーザーがキューに書き込む権限を持っていることが確認されます。<br />- 証明書: チャネルは証明書ストアから証明書を取得します。<br /><br /> 既定値は WindowsDomain です。 この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。|  
|`msmqEncryptionAlgorithm`|メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> - RC4ストリーム<br />- AES<br /><br /> 既定値は RC4Stream です。 この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。|  
|`msmqProtectionLevel`|MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。 暗号化はメッセージの整合性を保証し、EncryptAndSign はメッセージの整合性と否認防止の両方を保証します。つまり、メッセージは実際に送信者から来ており、送信者は彼らが誰であるかを示します。<br /><br /> - 有効な値は次のとおりです。<br />- なし:保護なし。<br />- 署名: メッセージは署名されています。<br />- 暗号化と署名: メッセージは暗号化され、署名されています。<br /><br /> 既定値は Sign です。 この属性は、ProtectionLevel 型です。|  
|`msmqSecureHashAlgorithm`|- 署名の一部としてダイジェストの計算に使用するアルゴリズムを指定します。 有効な値は次のとおりです。<br />- MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> 既定値は SHA1 です。 この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。<br>MD5 と SHA1 の衝突の問題のため、マイクロソフトは SHA256 以上を推奨します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<セキュリティ>](security-of-basichttpbinding.md)|MSMQ バインディングのセキュリティ設定を定義します。|  
  
## <a name="remarks"></a>解説  
 この要素は、メッセージ キュー統合トランスポートのセキュリティ設定をカプセル化します。 設定は、メッセージ キュー統合トランスポートとキューに置かれているトランスポートの両方で同じです。 この設定を使用すると、認証モード、暗号化アルゴリズム、セキュア ハッシュ アルゴリズム、および保護レベルを設定できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインド](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<バインド>](bindings.md)
