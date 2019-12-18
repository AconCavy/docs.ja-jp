---
title: サーバーレス アーキテクチャに関する考慮事項 - サーバーレス アプリ
description: 状態管理や永続的ストレージから、スケーリング、ログ記録、トレース、診断まで、サーバーレス アプリケーションを設計する際の課題について説明します。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522431"
---
# <a name="serverless-architecture-considerations"></a>サーバーレス アーキテクチャの考慮事項

サーバーレス アーキテクチャを採用することには、いくつかの課題が伴います。 このセクションでは、注意すべき一般的な考慮事項をいくつか説明します。 これらの課題にはすべて解決策が存在します。 すべてのアーキテクチャの選択肢と同様に、サーバーレスにするかどうかの決定は、長所と短所を慎重に検討した上で行う必要があります。 アプリケーションのニーズによっては、サーバーレス実装が特定のコンポーネントには適した解決策ではないと判断する場合もあります。

## <a name="managing-state"></a>状態の管理

一般にマイクロサービスと同様に、サーバーレス関数は既定でステートレスです。 状態を回避することで、サーバーレスを一時的なものにすることができます。また、スケールアウトし、中央障害点なしで回復性を提供することができます。 状況によっては、ビジネス プロセスで状態が必要になる場合があります。 プロセスに状態が必要な場合は、2 つのオプションがあります。 サーバーレス以外のモデルを採用すること、または状態を提供する別のサービスとやり取りすることができます。 状態を追加すると、ソリューションが複雑になり、スケーリングが難しくなり、単一障害点が生じる可能性があります。 関数で状態が絶対的に必要であるかどうかを慎重に検討してください。 答えが「はい」の場合は、それでもサーバーレスで実装するのが理にかなっているのかどうかを判断します。

サーバーレスの利点を損なうことなく状態を導入するための解決策がいくつか存在します。 一般的な解決策には、次のようなものがあります。

- Redis などの一時的なデータ ストアまたは分散キャッシュを使用する
- SQL や CosmosDB などのデータベースに状態を格納する
- Durable Functions のようなワークフロー エンジンを使用して状態を処理する

最後の行は、サーバーレスで実装することを検討しているプロセス内で、状態管理が必要であることを認識する必要があるということです。

## <a name="long-running-processes"></a>実行時間の長いプロセス

サーバーレスの多くの利点は、プロセスが一時的なものであるということに依存します。 実行時間が短いことにより、サーバーレス プロバイダーは、関数の終了時にリソースを解放し、ホスト間で関数を共有することが容易になります。 ほとんどのクラウド プロバイダーでは、関数が実行可能な合計時間が約 10 分に制限されています。 プロセスにかかる時間が長くなる場合は、別の実装を検討してください。

いくつかの例外と解決策が存在します。 解決策の 1 つは、プロセスを小さなコンポーネントに分割して、個々の実行に要する時間を短縮することです。 依存関係が原因でプロセスが長時間実行される場合は、Durable Functions などのソリューションを使用した非同期ワークフローを検討することもできます。 Durable Functions では、外部プロセスが終了するのを待機している間に、プロセスの状態が一時停止され維持されます。 非同期処理により、実際のプロセスの実行時間が短縮されます。

## <a name="startup-time"></a>起動時間

サーバーレス実装で考えられる問題の 1 つは、起動時間です。 リソースを節約するために、多くのサーバーレス プロバイダーは "オンデマンド" でインフラストラクチャを作成します。 サーバーレス関数が一定時間の経過後にトリガーされる場合、その関数をホストするためのリソースを作成または再起動する必要がある場合があります。 場合によっては、コールド スタートによって数秒の遅延が発生することがあります。 起動時間は、プロバイダーとサービス レベルによって異なります。 アプリが正常に機能するために起動時間を最小限に抑えることが重要な場合は、いくつかの対処方法があります。

- 一部のプロバイダーでは、ユーザーはインフラストラクチャが "常にオン" になっていることを保証するサービス レベルに対して支払いを行うことができます。
- keep-alive 機構を実装します (エンドポイントに ping を実行して、"起動状態" のままにします)。
- コンテナー化された関数の手法で Kubernetes のようなオーケストレーションを使用します (ホストは既に実行されているため、新しいインスタンスの起動が非常に高速になります)。

## <a name="database-updates-and-migrations"></a>データベースの更新と移行

サーバーレス コードの利点は、アプリケーション全体を再展開しなくても、新しい関数をリリースできることです。 この利点は、リレーショナル データベースがある場合に欠点になる可能性があります。 データベース スキーマに対する変更は、サーバーレスの更新と同期するのが困難です。 不具合があるため変更をロールバックする必要がある場合は、さらに問題が発生します。 マイクロサービスやサーバーレス関数のベスト プラクティスは独自のデータを所有していることであるという理由の 1 つが、データ整合性です。 変更は、コンピューティングとデータの 1 つの単位として展開することができます。 現実には、多くのレガシ システムは、サーバーレス アーキテクチャで調整する必要がある大規模なバックエンド データベースを特徴としています。

スキーマのバージョン管理を解決するための一般的な方法は、既存のプロパティや列を決して変更せずに、新しい情報を追加することです。 たとえば、Todo リストのブール値 [完了] フラグから [完了日] に移動する変更を考えてみます。 古いフィールドを削除するのではなく、データベースを次のように変更します。

1. 新しい [完了日] フィールドを追加します。
1. [完了] ブール値フィールドを、完了日が現在の日付より後であるかどうかを評価する計算関数に変換します。
1. [完了] ブール値が true に設定されている場合に現在の日付を完了日として設定するトリガーを追加します。

一連の変更によって、レガシ コードが "そのまま" 実行され、新しいサーバーレス関数では新しいフィールドを利用できます。

サーバーレス アーキテクチャのデータの詳細については、「[分散データ管理に関する課題と解決策](../microservices/architect-microservice-container-applications/distributed-data-management.md)」を参照してください。

## <a name="scaling"></a>スケーリング

サーバーレスは "サーバーなし" を意味するという誤解がよくあります。 実際には、"少ないサーバー" です。 スケーリングに関しては、バッキング ンフラストラクチャが重要であることを理解しておくことが重要です。 ほとんどのサーバーレス プラットフォームでは、イベント密度が増加したときにインフラストラクチャがどのようにスケーリングされる必要があるのかを処理するコントロールのセットが提供されます。 さまざまなオプションから選択できますが、その方法は関数によって異なる場合があります。 さらに、関数は通常関連するホストで実行されるので、同じホスト上の関数のスケール オプションは同じになります。 そのため、スケール要件に基づいてホストされる関数を整理し、実行する必要があります。

多くの場合、スケールアップ (ホスト リソースの増加) とスケールアウト (ホスト インスタンスの数の増加) の方法が、さまざまなパラメーターに基づいてルールで指定されます。 スケールのトリガーには、スケジュール、要求レート、CPU 使用率、メモリ使用量などがあります。 多くの場合、高パフォーマンスはコストが高くなります。 コストが安く、使用量ベースの方法の場合、要求レートが突然増加した場合にはすぐにはスケーリングされないことがあります。 前払いの "保険コスト" を支払うことと、"従量課金制" で厳密に支払い需要が急激に増加することによる応答速度の低下のリスクを負うことの間で、トレードオフが存在します。

## <a name="monitoring-tracing-and-logging"></a>監視、トレース、およびログ記録

DevOps の見落としがちな側面に、展開されたアプリケーションの監視があります。 サーバーレス関数を監視するための戦略を用意することが重要です。 最大の課題は、多くの場合、ユーザーが同じ操作の一部として複数の関数を呼び出すときの、相関関係、または認識です。 ほとんどのサーバーレス プラットフォームでは、サードパーティ製ツールにインポートできるコンソールのログ記録を使用できます。 詳細な分析情報を提供するための、テレメトリの収集の自動化、関連付け ID の生成と追跡、および特定のアクションの監視オプションもあります。 Azure には、監視と分析のための高度な [Application Insights プラットフォーム](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)が用意されています。

## <a name="inter-service-dependencies"></a>サービス間の依存関係

サーバーレス アーキテクチャには、他の関数に依存する関数が含まれている場合があります。 実際、サーバーレス アーキテクチャでは、相互作用または分散トランザクションの一部として複数のサービスが相互に呼び出されることは珍しくありません。 密接な結びつきを避けるために、サービスは互いに直接参照しないことをお勧めします。 サービスのエンドポイントを変更する必要がある場合、直接参照によって大幅なリファクタリングが行われる可能性があります。 推奨される解決策は、要求の種類に対して適切なエンドポイントを提供する、レジストリなどのサービス検出メカニズムを提供することです。 もう 1 つの解決策は、サービス間の通信に関するキューやトピックなどのメッセージング サービスを利用することです。

## <a name="managing-failure-and-providing-resiliency"></a>障害の管理と回復性の提供

*サーキット ブレーカー パターン*を考慮することも重要です。何らかの理由でサービスが継続的に失敗する場合は、そのサービスを繰り返し呼び出すことはお勧めできません。 代わりに、代替サービスが呼び出されるか、依存するサービスの正常性が再確立されるまでメッセージが返されます。 サーバーレス アーキテクチャでは、サービス間の依存関係を解決および管理するための戦略を考慮する必要があります。

サーキット ブレーカー パターンを継続するには、サービスがフォールト トレランスと回復性を備えている必要があります。 フォールト トレランスとは、予期しない例外が発生した場合や無効な状態が検出された場合でも、アプリケーションの実行を継続する能力を指します。 フォールト トレランスは、通常コード自体の機能であり、例外を処理するためにどのように記述されているかを示します。 回復性とは、アプリが障害から回復する能力を指します。 回復性は多くの場合、サーバーレス プラットフォームによって管理されます。 既存のサーバーに障害が発生した場合、プラットフォームは新しいサーバーレス関数インスタンスを起動できる必要があります。 また、プラットフォームは、新しいインスタンスがすべて失敗する場合に、新しいインスタンスの起動を停止できるインテリジェンスも備えている必要があります。

詳細については、「[サーキット ブレーカー パターンを実装する](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)」を参照してください。

## <a name="versioning-and-greenblue-deployments"></a>バージョン管理とグリーン/ブルー展開

サーバーレスの大きな利点は、アプリケーション全体を再展開しなくても、特定の関数をアップグレードできることです。 アップグレードを正常に実行するには、関数を呼び出すサービスが正しいバージョンのコードにルーティングされるように、関数をバージョン管理する必要があります。 新しいバージョンを展開するための戦略も重要です。 一般的な方法は、"グリーン/ブルー展開" を使用することです。 グリーン展開は、現在の関数です。 新しい "ブルー" バージョンが運用環境に展開され、テストされます。 テストに合格すると、新しいバージョンが公開されるように、グリーンとブルーのバージョンが交換されます。 問題が発生した場合は、交換を元に戻すことができます。 バージョン管理とグリーン/ブルー展開をサポートするには、バージョンの変更に対応する関数を作成し、サーバーレス プラットフォームを使用して展開を処理する必要があります。 考えられる方法の 1 つとして、プロキシを使用する方法があります。これについては [Azure サーバーレス プラットフォーム](azure-functions.md#proxies)に関する章を参照してください。

>[!div class="step-by-step"]
>[前へ](serverless-architecture.md)
>[次へ](serverless-design-examples.md)