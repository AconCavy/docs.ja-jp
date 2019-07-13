---
title: ストリーミング プロバイダー (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, binary data
- streaming data provider [WCF Data Services]
- WCF Data Services, streams
ms.assetid: f0978fe4-5f9f-42aa-a5c2-df395d7c9495
ms.openlocfilehash: eff4ee3cb8502645d3b6d9a8986c9c410fe73f1a
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877586"
---
# <a name="streaming-provider-wcf-data-services"></a>ストリーミング プロバイダー (WCF Data Services)

データ サービスは、ラージ オブジェクトのバイナリ データを公開できます。 このバイナリ データは、ビデオ ストリームとオーディオ ストリーム、画像、ドキュメント ファイル、またはその他の種類のバイナリのメディアを表すことができます。 データ モデルのエンティティに 1 つ以上のバイナリ プロパティが含まれている場合、データ サービスは、このバイナリ データを応答フィードのエントリ内に Base-64 としてエンコードして返します。 読み込みと、この方法で大きなバイナリ データをシリアル化するには、パフォーマンスに影響するので、[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]が所属するエンティティの独立したバイナリ データを取得するためのメカニズムを定義します。 これは、バイナリ データとエンティティを分離して 1 つ以上のデータ ストリームを生成することで実現されます。

- メディア リソース - エンティティに属するバイナリ データ (ビデオ、オーディオ、画像、その他の種類のメディア リソース ストリームなど)。

- メディア リンク エントリ - 関連するメディア リソース ストリームへの参照を含むエンティティ。

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、ストリーミング データ プロバイダーを実装してバイナリ リソース ストリームを定義します。 ストリーミング プロバイダーの実装として特定のエンティティに関連付けられたメディア リソース ストリームをデータ サービスを提供する、<xref:System.IO.Stream>オブジェクト。 この実装によって、データ サービスでは、指定された MIME の種類のバイナリ データ ストリームとしてメディア リソースを HTTP 経由で受け入れて、返すことができます。

バイナリ データのストリーミングをサポートするデータ サービスを構成するには、次の手順に従う必要があります。

1. データ モデル内の 1 つ以上のエンティティをメディア リンク エントリとして属性化します。 これらのエンティティには、ストリーミング対象のバイナリ データを含めないでください。 エンティティのバイナリ プロパティは、常に Base-64 でエンコードされたバイナリとしてエントリで返されます。

2. T:System.Data.Services.Providers.IDataServiceStreamProvider インターフェイスを実装します。

3. <xref:System.IServiceProvider> インターフェイスを実装するデータ サービスを定義します。 データ サービスは、<xref:System.IServiceProvider.GetService%2A> の実装を使用してストリーミング データ プロバイダーの実装にアクセスします。 このメソッドは、適切なストリーミング プロバイダーの実装を返します。

4. Web アプリケーション構成で大きいメッセージ ストリームを有効にします。

5. サーバー上またはデータ ソース内のバイナリ リソースへのアクセスを有効にします。

このトピックの例ではストリーミング フォト サービスは、投稿の詳細については、サンプルに基づきます[Data Services ストリーミング プロバイダー シリーズ。ストリーミング プロバイダー (パート 1) を実装する](https://go.microsoft.com/fwlink/?LinkID=198989)します。 このサンプル サービスのソース コードは、[ストリーミング フォト データ サービスのサンプル ページ](https://go.microsoft.com/fwlink/?LinkID=198988)MSDN Code Gallery 上。

## <a name="defining-a-media-link-entry-in-the-data-model"></a>データ モデル内のメディア リンク エントリの定義

エンティティがデータ モデル内のメディア リンク エントリとして定義される方法は、データ ソース プロバイダーによって決定されます。

**Entity Framework プロバイダー**

エンティティがメディア リンク エントリであることを示すには、概念モデルのエンティティ型定義に `HasStream` 属性を追加します。次にその例を示します。

[!code-xml[Astoria Photo Streaming Service#HasStream](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_photo_streaming_service/xml/photodata.edmx#hasstream)]

また、エンティティまたはデータ モデルを定義する .edmx ファイルまたは .csdl ファイルのルートに名前空間 `xmlns:m=http://schemas.microsoft.com/ado/2007/08/dataservices/metadata` を追加する必要があります。

使用するデータ サービスの例については、[!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]プロバイダー メディア リソースを公開、投稿を参照してください。 [Data Services ストリーミング プロバイダー シリーズ。ストリーミング プロバイダー (パート 1) を実装する](https://go.microsoft.com/fwlink/?LinkID=198989)します。

**リフレクション プロバイダー**

エンティティがメディア リンク エントリであることを示すには、リフレクション プロバイダーのエンティティ型を定義するクラスに <xref:System.Data.Services.Common.HasStreamAttribute> を追加します。

**カスタム データ サービス プロバイダー**

カスタム サービス プロバイダーを使用する場合は、<xref:System.Data.Services.Providers.IDataServiceMetadataProvider> インターフェイスを実装してデータ サービスのメタデータを定義します。 詳細については、次を参照してください。[カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)します。 エンティティ型 (メディア リンク エントリ) を表す <xref:System.Data.Services.Providers.ResourceType> で <xref:System.Data.Services.Providers.ResourceType.IsMediaLinkEntry%2A> プロパティを `true` に設定して、バイナリ リソース ストリームが <xref:System.Data.Services.Providers.ResourceType> に属することを示します。

## <a name="implementing-the-idataservicestreamprovider-interface"></a>IDataServiceStreamProvider インターフェイスの実装

バイナリ データ ストリームをサポートするデータ サービスを作成するには、<xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスを実装する必要があります。 これを実装すると、データ サービスはバイナリ データをストリームとしてクライアントに返し、クライアントから送信されたストリームとしてバイナリ データを使用できます。 データ サービスでは、バイナリ データへのストリームとしてのアクセスが必要になるたびに、このインターフェイスのインスタンスを作成します。 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> インターフェイスでは次のメンバーを指定します。

|メンバー名|説明|
|-----------------|-----------------|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A>|このメソッドはデータ サービスにより呼び出され、メディア リンク エントリが削除されたときに対応するメディア リソースを削除します。 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> を実装する場合、このメソッドには、指定されたメディア リンク エントリに関連付けられたメディア リソースを削除するコードが含まれます。|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A>|このメソッドはデータ サービスにより呼び出され、メディア リソースをストリームとして返します。 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> を実装する場合、このメソッドには、指定されたメディア リンク エントリに関連付けられたメディア リソースを返すためにデータ サービスが使用するストリームを提供するコードが含まれます。|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStreamUri%2A>|このメソッドはデータ サービスにより呼び出され、メディア リンク エントリのメディア リソースを要求するために使用される URI を返します。 この値を使用して、メディア リンク エントリのコンテンツ要素の `src` 属性が作成され、データ ストリームが要求されます。 このメソッドから `null` が返されると、データ サービスによって URI が自動的に決定されます。 このメソッドは、ストリーミング プロバイダーを使用しないバイナリ データへの直接アクセスをクライアントに提供する必要がある場合に使用します。|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamContentType%2A>|このメソッドはデータ サービスにより呼び出され、指定されたメディア リンク エントリに関連付けられたメディア リソースの Content-Type 値を返します。|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetStreamETag%2A>|このメソッドはデータ サービスにより呼び出され、指定されたエンティティに関連付けられたデータ ストリームの eTag を返します。 このメソッドは、バイナリ データの同時実行を管理する場合に使用されます。 このメソッドが null を返す場合、データ サービスでは同時実行が追跡されません。|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A>|このメソッドはデータ サービスにより呼び出され、クライアントから送信されたストリームの受信時に使用されるストリームを取得します。 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> を実装する場合、データ サービスが受信したストリーム データを書き込む先である書き込み可能なストリームを返す必要があります。|
|<xref:System.Data.Services.Providers.IDataServiceStreamProvider.ResolveType%2A>|名前空間で修飾された型名を返します。この型は、挿入されるメディア リソースのデータ ストリームに関連付けられたメディア リンク エントリに対してデータ サービス ランタイムが作成する必要がある型を表します。|

## <a name="creating-the-streaming-data-service"></a>ストリーミング データ サービスの作成

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ランタイムに <xref:System.Data.Services.Providers.IDataServiceStreamProvider> の実装へのアクセスを提供するには、作成するデータ サービスで <xref:System.IServiceProvider> インターフェイスも実装する必要があります。 次の例は、<xref:System.IServiceProvider.GetService%2A> メソッドを実装して、`PhotoServiceStreamProvider` を実装する <xref:System.Data.Services.Providers.IDataServiceStreamProvider> クラスのインスタンスを返す方法を示しています。

[!code-csharp[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_photo_streaming_service/cs/photodata.svc.cs#photoservicestreamingprovider)]
[!code-vb[Astoria Photo Streaming Service#PhotoServiceStreamingProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_photo_streaming_service/vb/photodata.svc.vb#photoservicestreamingprovider)]

データ サービスを作成する方法については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)します。

## <a name="enabling-large-binary-streams-in-the-hosting-environment"></a>ホスト環境での大きなバイナリ ストリームの有効化

ASP.NET Web アプリケーションでデータ サービスを作成するときに、Windows Communication Foundation (WCF) は、HTTP プロトコルを実装に使用されます。 既定では、WCF では HTTP メッセージのサイズは 65K バイトのみに制限されます。 また、データ サービスに対する大きなバイナリ データのストリーミングを可能にするには、大きなバイナリ ファイルを有効にして、転送にストリームを使用するように Web アプリケーションを構成する必要もあります。 そのためには、アプリケーションの Web.config ファイルの `<configuration />` 要素に次の内容を追加します。

> [!NOTE]
> 使用する必要があります、<xref:System.ServiceModel.TransferMode.Streamed?displayProperty=nameWithType>転送モードを要求と応答のメッセージでバイナリ データがストリーミングし、WCF によってバッファリングされないことを確認します。

詳細については、次を参照してください。 [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)と[トランスポート クォータ](../../../../docs/framework/wcf/feature-details/transport-quotas.md)します。

また、既定では、インターネット インフォメーション サービス (IIS) でも要求のサイズが 4 MB に制限されます。 IIS で実行されているときに、4 MB を超えるストリームを受信するデータ サービスを有効にする必要がありますも設定する、`maxRequestLength`の属性、 [httpRuntime 要素 (ASP.NET 設定スキーマ)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e1f13641(v=vs.100))で、`<system.web />`構成のセクションとして次の例に示します。

## <a name="using-data-streams-in-a-client-application"></a>クライアント アプリケーションでのデータ ストリームの使用

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] クライアント ライブラリを使用すると、クライアントのバイナリ ストリームとして公開されたリソースを取得および更新できます。 詳細については、次を参照してください。[バイナリ データを扱う](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)します。

## <a name="considerations-for-working-with-a-streaming-provider"></a>ストリーミング プロバイダーの使用に関する考慮事項

ストリーミング プロバイダーを実装する場合およびデータ サービスからメディア リソースにアクセスする場合には、次の点を考慮してください。

- MERGE 要求は、メディア リソースではサポートされません。 既存のエンティティのメディア リソースを変更するには、PUT 要求を使用します。

- POST 要求を使用して新しいメディア リンク エントリを作成することはできません。 代わりに、POST 要求を発行して新しいメディア リソースを作成する必要があります。データ サービスによって、既定値で新しいメディア リンク エントリが作成されます。 その後に MERGE 要求または PUT 要求を使用してこの新しいエンティティを更新できます。 プロパティ値を POST 要求の Slug ヘッダーの値に設定するなど、エンティティをキャッシュしてディスポーザーで更新を行うこともできます。

- POST 要求を受信すると、データ サービスは <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> を呼び出してメディア リソースを作成してから、<xref:System.Data.Services.IUpdatable.SaveChanges%2A> を呼び出してメディア リンク エントリを作成します。

- <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> を実装すると、<xref:System.IO.MemoryStream> オブジェクトは返されません。 この種類のストリームを使用すると、サービスが非常に大きなデータ ストリームを受信した場合に、メモリ リソースの問題が発生します。

- データベースにメディア リソースを格納する場合は、次の点を考慮してください。

  - メディア リソースであるバイナリ プロパティをデータ モデルに含めないようにしてください。 データ モデルで公開されるプロパティはすべて、応答フィードのエントリで返されます。

  - 大きなバイナリ ストリームのパフォーマンスを向上させるには、カスタム ストリーム クラスを作成してバイナリ データをデータベースに格納することをお勧めします。 このクラスは、<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> の実装によって返され、バイナリ データをチャンク単位でデータベースに送信します。 SQL Server データベースでは、バイナリ データが 1 MB を超える場合、データベースに FILESTREAM データのストリームを使用することをお勧めします。

  - データ サービスによって受信される大きなバイナリ ストリームを格納できるようにデータベースが設計されていることを確認してください。

  - クライアントが POST 要求を送信して、1 回の要求でメディア リソースと共にメディア リンク エントリを挿入する場合は、データ サービスによって新しいエンティティがデータベースに挿入される前に、<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> を呼び出してストリームを取得します。 ストリーミング プロバイダーは、このデータ サービスの動作を処理できるように実装する必要があります。 エンティティがデータベースに挿入されるまで、個別のデータ テーブルを使用してバイナリ データを格納するか、データ ストリームをファイルに格納することを検討してください。

- <xref:System.Data.Services.Providers.IDataServiceStreamProvider.DeleteStream%2A> メソッド、<xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetReadStream%2A> メソッド、または <xref:System.Data.Services.Providers.IDataServiceStreamProvider.GetWriteStream%2A> メソッドを実装する場合は、メソッドのパラメーターとして指定される eTag 値および Content-Type 値を使用する必要があります。 <xref:System.Data.Services.Providers.IDataServiceStreamProvider> プロバイダーの実装には、eTag ヘッダーまたは Content-Type ヘッダーを設定しないでください。

- 既定では、クライアントはチャンクされた HTTP Transfer-Encoding を使用して、大きなバイナリ ストリームを送信します。 ASP.NET 開発サーバーがこの種類のエンコーディングをサポートしていないために、大きなバイナリ ストリームを受け取る必要があるストリーミング データ サービスをホストするのにこの Web サーバーを使用することはできません。 ASP.NET 開発サーバーの詳細については、次を参照してください。 [ASP.NET Web プロジェクト用の Visual Studio で Web サーバー](https://docs.microsoft.com/previous-versions/aspnet/58wxa9w5(v=vs.120))します。

<a name="versioning"></a>

## <a name="versioning-requirements"></a>バージョン管理の要件

ストリーミング プロバイダーには、次に示す [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルのバージョン管理の要件があります。

- ストリーミング プロバイダーを使用するには、データ サービスでバージョン 2.0 以降の [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] プロトコルがサポートされている必要があります。

詳細については、次を参照してください。[データ サービスのバージョン管理](../../../../docs/framework/data/wcf/data-service-versioning-wcf-data-services.md)します。

## <a name="see-also"></a>関連項目

- [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [カスタム データ サービス プロバイダー](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md)
- [バイナリ データの操作](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)
