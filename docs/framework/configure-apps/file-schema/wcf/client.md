---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 2e0352efdd5b709984338fe4484b120bddb7d545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704298"
---
# <a name="client"></a>\<client>
`client` 要素は、クライアントが接続可能なエンドポイントの一覧を定義します。  
  
 \<system.ServiceModel >  
\<client>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|このクライアントが接続可能なエンドポイントを指定するエンドポイント要素のコレクションを含みます。|  
|[\<metadata >](../../../../../docs/framework/configure-apps/file-schema/wcf/metadata.md)|メタデータを処理するための設定を含みます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。|  
  
## <a name="remarks"></a>Remarks  
 `client` セクションは、クライアントが接続可能なエンドポイントの一覧を定義します。 クライアント セクションに示される各エンドポイントは、独自のバインディング、動作、およびコントラクトを定義します。 各エンドポイントは、`name` 属性と `contract` 属性の組み合わせで一意に識別されます。 クライアント コードは、クライアントが実装するサービスのエンドポイントに接続するための `name` を指定します。 `name` 属性が省略されている場合、クライアントが実装するコントラクトのエンドポイントが既定のエンドポイントとして機能します。  
  
 さらに、このセクションはメタデータを処理するための設定も指定します。  
  
## <a name="example"></a>例  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [WCF クライアントの構成](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [クライアント](../../../../../docs/framework/wcf/feature-details/clients.md)
