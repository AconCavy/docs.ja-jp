---
title: '方法 : IIS で WCF サービスをホストする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: 580b380a6c6349c6a4efa26e3eefe38bd660fa1b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184920"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a>方法 : IIS で WCF サービスをホストする
このトピックでは、インターネット インフォメーション サービス (IIS) でホストされている Windows 通信基盤 (WCF) サービスを作成するために必要な基本的な手順について説明します。 このトピックは、IIS に関する知識があり、IIS 管理ツールを使用して IIS アプリケーションを作成および管理する方法を理解していることを前提としています。 IIS の詳細については、「[インターネット インフォメーション サービス](https://www.iis.net/)」を参照してください。 IIS 環境で実行される WCF サービスは、プロセスのリサイクル、アイドル 状態のシャットダウン、プロセスの状態監視、メッセージ ベースのアクティブ化などの IIS 機能を最大限に活用します。 このホスト オプションでは、IIS が正しく構成されている必要がありますが、アプリケーションの一部としてホスト コードを書く必要はありません。 IIS ホストは、HTTP トランスポートでのみ使用できます。  
  
 WCF と ASP.NETの対話方法の詳細については、「 [WCF サービスとASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)」を参照してください。 セキュリティの構成の詳細については、「[セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)」を参照してください。  
  
 この例のソース コピーについては、「[インライン コードを使用した IIS のホスティング](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)」を参照してください。  
  
### <a name="to-create-a-service-hosted-by-iis"></a>IIS でホストされるサービスを作成するには  
  
1. コンピューターに IIS がインストールされ、実行されていることを確認します。 IIS のインストールと構成の詳細については[、「IIS 7.0 のインストールと構成」を](https://docs.microsoft.com/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)参照してください。  
  
2. "IISHostedCalcService" という名前のアプリケーション ファイル用の新しいフォルダを作成し、ASP.NETがフォルダの内容にアクセスできることを確認し、IIS 管理ツールを使用して、このアプリケーション ディレクトリに物理的に配置された新しい IIS アプリケーションを作成します。 アプリケーション ディレクトリのエイリアスを作成する場合は、"IISHostedCalc" を使用します。  
  
3. "service.svc" という新しいファイルをアプリケーション ディレクトリに作成します。 このファイルを編集するには、次@ServiceHostの要素を追加します。  
  
   ```
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. アプリケーション ディレクトリ内に App_Code サブディレクトリを作成します。  
  
5. App_Code サブディレクトリに Service.cs というコード ファイルを作成します。  
  
6. Service.cs ファイルの先頭に次の using ステートメントを追加します。  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. using ステートメントの後に、次の名前空間宣言を追加します。  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. 次のコードに示すように、名前空間宣言内にサービス コントラクトを定義します。  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. 次のコードに示すように、サービス コントラクト定義の後に、サービス コントラクトを実装します。  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. アプリケーション ディレクトリ内に "Web.config" というファイルを作成し、次の構成コードをファイルに追加します。 実行時に、WCF インフラストラクチャは、クライアント アプリケーションが通信できるエンドポイントを構築するのには、情報を使用します。  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     この例では、構成ファイルにエンドポイントを明示的に指定します。 エンドポイントをサービスに追加しない場合、ランタイムによって既定のエンドポイントが追加されます。 既定のエンドポイント、バインド、および動作の詳細については、「 [WCF サービスの](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)[構成の簡略化](../../../../docs/framework/wcf/simplified-configuration.md)と簡略化 」を参照してください。  
  
11. サービスが正確にホストされるようにするには、Internet Explorer のインスタンスを開き、サービスの URL: `http://localhost/IISHostedCalc/Service.svc` を参照します。  
  
## <a name="example"></a>例  
 IIS がホストする電卓サービスのコードの完全な一覧を次に示します。  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a>関連項目

- [インターネット インフォメーション サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)
- [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)
- [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [セキュリティ](../../../../docs/framework/wcf/feature-details/security.md)
- [AppFabric のホスティング機能](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
