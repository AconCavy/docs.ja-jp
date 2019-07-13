---
title: 複数の IIS サイト バインディングのサポート
ms.date: 03/30/2017
ms.assetid: 40440495-254d-45c8-a8c6-b29f364892ba
ms.openlocfilehash: 5a8b06d86b505452f9ded808f727343b1453e592
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61696107"
---
# <a name="supporting-multiple-iis-site-bindings"></a>複数の IIS サイト バインディングのサポート
Windows Communication Foundation (WCF) サービスでは、インターネット情報サービス (IIS) 7.0 をホストする場合、同じサイトで同じプロトコルを使用する複数のベース アドレスを提供したい場合があります。 これにより、同じサービスで多数の異なる URI に応答できます。 リッスンするサービスをホストする場合に便利ですが `http://www.contoso.com` と `http://contoso.com` です。 また、内部ユーザー用に 1 つのベース アドレスを持ち、外部ユーザー用に別のベース アドレスを持つサービスを作成するのにも役立ちます。 例: `http://internal.contoso.com` と `http://www.contoso.com` です。  
  
> [!NOTE]
>  この機能は、HTTP プロトコルを使用してのみ、使用可能です。  
  
## <a name="multiple-base-addresses"></a>複数のベース アドレス  
 この機能は、IIS でホストされている WCF サービスで使用できるだけです。 この機能は、既定では有効にされません。 追加を有効にする必要があります、`multipleSiteBindingsEnabled`属性を <`serviceHostingEnvironment`>、Web.config 内の要素に設定ファイルを開き`true`次の例のようにします。  
  
```xml  
<serviceHostingEnvironment multipleSiteBindingsEnabled="true"/>  
```  
  
 IIS で WCF サービスをホストする場合、IIS は、アプリケーションを含む仮想ディレクトリへの URI に基づいて 1 つのベース アドレスを作成します。 インターネット インフォメーション サービス マネージャーを使用して、同じプロトコルを使用するベース アドレスを追加し、1 つ以上のバインディングを Web サイトに追加できます。 それぞれのバインディングに対して、プロトコル (HTTP または HTTPS)、IP アドレス、ポート、およびホスト名を指定します。 詳細については、インターネット インフォメーション サービス マネージャーを使用して、次を参照してください。 [IIS マネージャー (IIS 7)](https://go.microsoft.com/fwlink/?LinkId=164057)します。 サイトにバインドを追加する方法の詳細については、次を参照してください[Web サイト (IIS 7) を作成します。](https://go.microsoft.com/fwlink/?LinkId=164060)  
  
 同じサイトの複数のベース アドレスを指定するには、スキーマ、およびサービスによって生成される WSDL/MEX 情報をインポートする WCF ヘルプ ページのコンテンツに影響します。 WCF ヘルプ ページには、使用して、サービスと通信できる WCF クライアントを生成するコマンド ラインが表示されます。 このコマンド ラインには、その Web サイト用の IIS バインディングで指定された最初のアドレスだけが含まれています。 同様に、スキーマをインポートするときには、IIS バインディングで指定された最初のベース アドレスだけが使用されます。 WSDL および MEX データには、IIS バインディングで指定されたすべてのベース アドレスが含まれています。  
  
> [!WARNING]
>  つまり、サービスに 2 つのベース アドレス (1 つは内部ユーザー用、もう 1 つは外部ユーザー用) がある場合、サービスによって生成される WSDL/MEX 情報では、両方のベース アドレスが指定されます。
