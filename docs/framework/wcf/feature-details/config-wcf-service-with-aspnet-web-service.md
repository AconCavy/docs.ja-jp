---
title: '方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 48e1cd90-de80-4d6c-846e-631878955762
ms.openlocfilehash: 8b43ae8345fe8c4286f00f4b6e4f6373746e8bbe
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882166"
---
# <a name="how-to-configure-wcf-service-to-interoperate-with-aspnet-web-service-clients"></a>方法: WCF サービスおよび ASP.NET Web サービス クライアントを相互運用するために構成する
ASP.NET Web サービス クライアントを相互運用できるように Windows Communication Foundation (WCF) サービス エンドポイントを構成するには、使用、<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>サービス エンドポイントのバインドの種類として。  
  
 必要に応じて、HTTPS およびトランスポート レベルのクライアント認証のサポートをバインディングで有効にできます。 ASP.NET Web サービス クライアントは MTOM メッセージのエンコーディングをサポートしていないため、<xref:System.ServiceModel.BasicHttpBinding.MessageEncoding%2A?displayProperty=nameWithType>プロパティは、これは、既定値として残しておく必要がある<xref:System.ServiceModel.WSMessageEncoding.Text?displayProperty=nameWithType>します。 また、ASP.Net Web サービス クライアントでは WS-Security がサポートされていないため、<xref:System.ServiceModel.BasicHttpBinding.Security%2A?displayProperty=nameWithType> を <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定する必要があります。  
  
 WCF サービスのメタデータを ASP.NET Web サービス プロキシ生成ツールを使用できるようにする (つまり、 [Web サービス記述言語ツール (Wsdl.exe)](https://go.microsoft.com/fwlink/?LinkId=73833)、 [Web サービス検出ツール (Disco.exe)](https://go.microsoft.com/fwlink/?LinkId=73834)、Visual Studio で Web 参照の追加機能) と、HTTP/GET メタデータ エンドポイントを公開する必要があります。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-code"></a>コードを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには  
  
1. 新しい <xref:System.ServiceModel.BasicHttpBinding> インスタンスを作成します。  
  
2. 必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインディングのトランスポート セキュリティを有効にします。 詳細については、「[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)します。  
  
3. 上で作成したバインディング インスタンスを使用して、サービス ホストに新しいアプリケーション エンドポイントを追加します。 サービス エンドポイントをコードに追加する方法の詳細については、次を参照してください。、[方法。コードでサービス エンドポイントを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)します。  
  
4. サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細を参照してください[方法。コードを使用してサービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)します。  
  
### <a name="to-add-a-wcf-endpoint-that-is-compatible-with-aspnet-web-service-clients-in-a-configuration-file"></a>構成ファイルを使用して ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加するには  
  
1. 新しい <xref:System.ServiceModel.BasicHttpBinding> バインド構成を作成します。 詳細については、次を参照してください。、[方法。構成でサービス バインディング指定](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)します。  
  
2. 必要に応じて、バインディングのセキュリティ モードを <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> に設定して、このサービス エンドポイント バインド構成のトランスポート セキュリティを有効にします。 詳細については、次を参照してください。[トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)します。  
  
3. 上で作成したバインド構成を使用して、サービスに新しいアプリケーション エンドポイントを構成します。 構成ファイルでサービス エンドポイントを追加する方法の詳細については、次を参照してください。、[方法。サービス エンドポイントの構成で作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)です。  
  
4. サービス用に HTTP/GET メタデータのエンドポイントを有効にします。 詳細を参照してください、[方法。構成ファイルを使用してサービスのメタデータを公開](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)します。  
  
## <a name="example"></a>例  
 次のコード例は、コードで ASP.NET Web サービス クライアントと互換性のある WCF エンドポイントを追加する方法を示します、または構成ファイルにします。  
  
 [!code-csharp[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/cs/program.cs#0)] 
 [!code-vb[C_HowTo-WCFServiceAndASMXClient#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/vb/program.vb#0)] 
 [!code-xml[C_HowTo-WCFServiceAndASMXClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto-wcfserviceandasmxclient/common/app.config#1)]     
  
## <a name="see-also"></a>関連項目

- [方法: コードでサービス エンドポイントを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)
- [方法: コードを使用してサービスのメタデータを公開します。](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)
- [方法: 構成でサービス バインディングを指定します。](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [方法: 構成でサービス エンドポイントを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
- [方法: 構成ファイルを使用してサービスのメタデータを公開します。](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [メタデータを使用する](../../../../docs/framework/wcf/feature-details/using-metadata.md)
