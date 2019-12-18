---
title: 最新の Web アプリケーションの特徴
description: ASP.NET Core と Azure を使用した最新の Web アプリケーションの設計 | 最新の Web アプリケーションの特徴
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: d3848f3b0cf993930bfc3801ce40c5eac30f094d
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374086"
---
# <a name="characteristics-of-modern-web-applications"></a>最新の Web アプリケーションの特徴

> "… 設計が適切であれば、低コストで機能を提供できます。 このアプローチは困難ですが、成功は継続します」  
> _\- Dennis Ritchie_

最新の Web アプリケーションに対するユーザーの期待と要求は、これまでよりも高くなります。 現代の Web アプリケーションは、世界中どこからでも 24 時間 365 日いつでも利用でき、ほぼあらゆるデバイスや画面サイズから使用できることが期待されます。 Web アプリケーションは、需要の急増に対応するために、セキュリティで保護され、柔軟性が高く、スケーラブルである必要があります。 ますます複雑になっているシナリオに対して、JavaScript を使用し、Web API を介して効率的に通信する高度なユーザー エクスペリエンスをクライアント上に構築して対処する必要があります。

ASP.NET Core は、最新の Web アプリケーションとクラウドベースのホスティング シナリオに合わせて最適化されています。 モジュール式の設計なので、アプリケーションは実際に使用する機能のみに依存することができます。さらに、アプリケーションのセキュリティとパフォーマンスが向上し、ホスティングのリソース要件は軽減されます。

## <a name="reference-application-eshoponweb"></a>参照アプリケーション: eShopOnWeb

このガイダンスには、いくつかの原則と推奨事項を示す参照アプリケーション _eShopOnWeb_ が含まれています。 このアプリケーションは単純なオンライン ストアです。シャツ、コーヒー マグなどの商品のカタログを閲覧することができます。 この参照アプリケーションは、わかりやすくするために意図的に単純にしています。

![eShopOnWeb](./media/image2-1.png)

**図 2-1** eShopOnWeb

> ### <a name="reference-application"></a>参照アプリケーション
>
> - **eShopOnWeb**  
>   <https://github.com/dotnet/eShopOnWeb>

## <a name="cloud-hosted-and-scalable"></a>クラウドでのホストとスケーラビリティ

ASP.NET Core は、メモリ使用量が低く高スループットなので、クラウド (パブリック クラウド、プライベート クラウド、クラウド) に合わせて最適化されています。 ASP.NET Core アプリケーションのフットプリントが小さくなると、同じハードウェアでより多くの情報をホストできます。また、従量制のクラウド ホスティング サービスを利用している場合は使用料金も安くなります。 スループットが高くなると、同じハードウェアを使用するアプリケーションからより多くのユーザーにサービスを提供できます。また、サーバーやホスティング インフラストラクチャに投資する必要性も軽減されます。

## <a name="cross-platform"></a>クロス プラットフォーム

ASP.NET Core はクロスプラットフォームであり、Linux、macOS、Windows で動作します。 そのため、ASP.NET Core で構築されたアプリケーションの開発と展開には新しい多くの選択肢があります。 Docker コンテナーは、Linux の場合も Windows の場合も、ASP.NET Core アプリケーションをホストすることができるので、[コンテナーとマイクロサービス](../microservices/index.md)の利点を活用できます。

## <a name="modular-and-loosely-coupled"></a>モジュール式と疎結合

NuGet パッケージは .NET Core の第一級コンポーネントであり、ASP.NET Core アプリケーションは NuGet を介した多数のライブラリで構成されています。 この機能の細分性によって、アプリケーションは実際に必要な機能に依存し、展開することができるので、フットプリントとセキュリティ脆弱性の攻撃面を減らすことができます。

また、ASP.NET Core は、内部的にもアプリケーション レベルでも[依存関係の挿入](https://deviq.com/dependency-injection/)を完全にサポートしています。 インターフェイスは、必要に応じてスワップ アウトできる複数の実装を持つことができます。 依存関係の挿入によって、アプリケーションとそのインターフェイスをはっきりした実装ではなく、疎結合することができるので、拡張、保守、テストが簡単になります。

## <a name="easily-tested-with-automated-tests"></a>自動テストで簡単にテスト

ASP.NET Core アプリケーションは単体テストをサポートしています。また、疎結合と依存関係の挿入のサポートにより、テスト目的でインフラストラクチャの懸案事項を偽の実装と簡単に交換することができます。 ASP.NET Core には、メモリ内でアプリケーションをホストするために使用できる TestServer も含まれています。 機能テストでは、このメモリ内サーバーへの要求を実行し、(ミドルウェア、ルーティング、モデルのバインド、フィルターなどの) アプリケーション スタック全体を実行し、応答を受信することができます。また、ごく短時間で実サーバー上でアプリケーションをホストし、ネットワーク層を介して要求を実行することができます。 API のこのようなテストは作成が簡単で価値があり、最新の Web アプリケーションではますます重要になっています。

## <a name="traditional-and-spa-behaviors-supported"></a>サポートされている従来の動作と SPA の動作

従来の Web アプリケーションでは、クライアント側の動作はほとんどありませんでしたが、代わりに、アプリケーションに必要な可能性があるすべてのナビゲーション、クエリ、および更新にはサーバーに依存していました。 ユーザーが実行した個々の新しい操作は新しい Web 要求に変換されるので、結果としてエンド ユーザーのブラウザーでページ全体の再読み込みが実行されます。 一般的に、従来のモデル ビュー コントローラー (MVC) フレームワークはこのアプローチに従い、個々の新しい要求は異なるコントローラー アクションに対応しているので、結果的にモデルと連携し、ビューを返します。 AJAX (Asynchronous JavaScript and XML) 機能を使用すると、特定のページ上の個々の操作が強化される場合がありますが、アプリケーションの全体的なアーキテクチャではさまざまな MVC ビューと URL エンドポイントが使用されていました。 また、ASP.NET Core MVC は、MVC スタイルのページを簡単に整理する方法である Razor Pages に対応しています。

これに対し、シングル ページ アプリケーション (SPA) の場合は、動的に生成されるサーバー側のページ読み込み (存在する場合) はほとんどありません。 多くの SPA は、アプリケーションを起動して実行するために必要な JavaScript ライブラリを読み込む静的 HTML ファイル内で初期化されます。 このようなアプリケーションはデータのニーズに合わせて Web API を多用し、より高度なユーザー エクスペリエンスを提供できます。

多くの Web アプリケーションでは、従来の Web アプリケーションの動作 (通常はコンテンツ用) と SPA (対話機能用) を組み合わせています。 ASP.NET Core は、同じアプリケーション内で同じツール セットと基礎のフレームワーク ライブラリを使用して MVC (ビューまたはページ ベース) と Web API の両方をサポートしています。

## <a name="simple-development-and-deployment"></a>単純な開発と展開

ASP.NET Core アプリケーションは、単純なテキスト エディターやコマンド ライン インターフェイス、または Visual Studio などのフル機能の開発環境を使用して作成できます。 モノリシック アプリケーションは、通常、単一のエンドポイントに展開されます。 継続的インテグレーション (CI) および継続的デリバリー (CD) パイプラインの一部として展開を簡単に自動化できます。 Windows Azure は、従来の CI/CD ツールに加えて git リポジトリを統合的にサポートしており、指定された git ブランチまたはタグへの展開と同様に、自動的に更新プログラムを展開することができます。

## <a name="traditional-aspnet-and-web-forms"></a>従来の ASP.NET と Web フォーム

ASP.NET Core だけでなく、従来の ASP.NET 4.x も、Web アプリケーションの構築に適した堅牢で信頼性の高いプラットフォームです。 ASP.NET は MVC および Web API 開発モデルと Web フォームをサポートしており、高度なページ ベースのアプリケーション開発に適しています。また、豊富なサード パーティのコンポーネント エコシステムを備えています。 Windows Azure は ASP.NET 4.x アプリケーションを長年にわたってサポートしているので、多くの開発者はこのプラットフォームに精通しています。

> ### <a name="references--modern-web-applications"></a>参照 – 最新の Web アプリケーション
>
> - **ASP.NET Core の概要**  
>   <https://docs.microsoft.com/aspnet/core/>
> - **ASP.NET Core が優れていることを示す 6 つの主な利点**  
>   <https://blog.trigent.com/six-key-benefits-of-asp-net-core-1-0-which-make-it-different-better/>
> - **ASP.NET Core でのテスト**  
>   <https://docs.microsoft.com/aspnet/core/testing/>

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](choose-between-traditional-web-and-single-page-apps.md)