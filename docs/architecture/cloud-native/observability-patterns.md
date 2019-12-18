---
title: 監視パターン
description: クラウドネイティブアプリケーションの可観測性パターン
ms.date: 09/23/2019
ms.openlocfilehash: 23320144c03278d631b8a1fcc1d1c0954e907296
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2019
ms.locfileid: "73841067"
---
# <a name="observability-patterns"></a>監視パターン

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

アプリケーションのコードのレイアウトを支援するために開発されたパターンと同じように、信頼性の高い方法でアプリケーションを運用するためのパターンがあります。 アプリケーションの管理において、ログ記録、監視、アラートという3つの便利なパターンが登場しました。

## <a name="when-to-use-logging"></a>ログ記録を使用する場合

どのように注意しても、アプリケーションはほとんどの場合、実稼働環境では予期しない方法で動作します。 ユーザーがアプリケーションに関する問題を報告する場合は、問題が発生したときにアプリの状況を確認できるようにすると非常に便利です。 アプリケーションが実行されているときの動作に関する情報をキャプチャする方法として最もよく見られるものの1つは、アプリケーションが実行している内容を書き留めておくことです。 このプロセスはログ記録と呼ばれます。 運用環境で障害や問題が発生した場合は、非運用環境で障害が発生した状況を再現することが目標となります。 適切なログ記録を使用することにより、開発者はテストと実験が可能な環境で問題を再現するためのロードマップが得られます。

### <a name="logging-in-cloud-native-applications"></a>クラウドネイティブアプリケーションでのログ記録

すべてのプログラミング言語には、ログの書き込みを可能にするツールが用意されています。通常、これらのログを書き込むためのオーバーヘッドは低くなります。 ログ記録ライブラリの多くは、実行時にチューニングできるさまざまな種類の criticalities のログ記録を提供しています。 たとえば、Serilog ライブラリは、次のログレベルを提供する .NET 用の一般的な構造化ログライブラリです。

* 詳細
* デバッグ
* 情報
* ［警告］
* エラー
* 致命的

これらのさまざまなログレベルにより、ログの粒度が向上します。 アプリケーションが運用環境で正常に機能している場合は、重要なメッセージのみをログに記録するように構成できます。 アプリケーションの動作が不適切な場合は、より詳細なログが収集されるようにログレベルを上げることができます。 これにより、デバッグが容易になるというバランスでパフォーマンスが低下します。

ログツールの高パフォーマンスと、詳細レベルのチューニング機能により、開発者は頻繁にログを記録することをお勧めします。 多くの場合、各メソッドのエントリと終了をログに記録するパターンを優先します。 このアプローチは過剰な場合があるかもしれませんが、開発者がログ記録の量を少なくすることはあまりありません。 実際には、問題のあるメソッドのログ記録を追加することだけを目的としてデプロイを実行することは珍しくありません。 ログ記録が過剰になっていますが、それほど多くはありません。 この種のログを自動的に提供するために、一部のツールを使用できることに注意してください。

従来のアプリケーションでは、通常、ログファイルはローカルコンピューターに格納されていました。 実際、Unix のようなオペレーティングシステムでは、すべてのログを保持するために定義されたフォルダー構造があります (通常は `/var/log`の下)。 1台のコンピューター上のフラットファイルへのログ記録の有用性は、クラウド環境で大幅に削減されます。 ログを生成するアプリケーションはローカルディスクにアクセスできない場合があります。また、コンテナーは物理マシンに対してシャッフルされるため、ローカルディスクが非常に一時的なものである可能性があります。

マイクロサービスアーキテクチャを使用して開発されたクラウドネイティブアプリケーションにも、ファイルベースの logger に関するいくつかの課題があります。 ユーザーの要求が、異なるコンピューター上で実行される複数のサービスにまたがることができるようになりました。また、ローカルファイルシステムへのアクセスをまったく持たないサーバーレス関数を含めることもできます。 このような多くのサービスやコンピューターで、ユーザーまたはセッションのログを相互に関連付けることは、非常に困難です。

最後に、一部のクラウドネイティブアプリケーションのユーザー数が多くなっています。 各ユーザーがアプリケーションにログインすると、500行のログメッセージが生成されると想像してください。 分離では、管理は容易ですが、10万人のユーザーとログの量が大きくなります。

幸いにも、ファイルシステムベースのログ記録を使用することには、いくつかの優れた方法があります。 すべてのログを送信する一元化されたログサーバーは、これらの問題をすべて修正します。 ログは、アプリケーションによって収集され、ログのインデックスを作成して格納する中央ログアプリケーションに付属しています。 このクラスのシステムは、毎日数万のログを取り込むことができます。

また、多くのサービスにまたがるログ記録を作成する際には、いくつかの標準的なプラクティスに従うことをお勧めします。 たとえば、時間のかかる相互作用の開始時に[相関 ID](https://blog.rapid7.com/2016/12/23/the-value-of-correlation-ids/)を生成し、その相互作用に関連するメッセージごとにログを記録すると、関連するすべてのメッセージを検索しやすくなります。 1つのメッセージだけを検索し、相関 ID を抽出して、関連するすべてのメッセージを検索する必要があります。 別の例として、使用する言語やログライブラリにかかわらず、すべてのサービスでログ形式が同じであることを確認します。 この標準化により、ログの読み取りがはるかに簡単になります。 図7-1 は、マイクロサービスアーキテクチャがワークフローの一部として集中ログを活用する方法を示しています。

さまざまなソースからの ![ログは、集中管理されたログストアに取り込まれたます。](./media/centralized-logging.png)
**図 7-1**。 さまざまなソースからのログは、一元化されたログストアに取り込まれたます。

## <a name="when-to-use-monitoring"></a>監視を使用する場合

アプリケーションによっては、ミッションクリティカルではないものもあります。 これらは内部的にのみ使用され、問題が発生した場合、ユーザーはチームに連絡して、アプリケーションを再起動できる可能性があります。 しかし、多くの場合、顧客は使用するアプリケーションに対して高い期待をしています。 ユーザーがアプリケーションで発生*する前*、またはユーザーに通知する前に問題が発生したことを知る必要がある場合は、その現在の状態を監視する必要があります。 適切に実装すると、問題の原因となる条件についての監視が可能になり、ユーザーが影響を受ける前に基になる条件に対処できます。

## <a name="monitoring-considerations"></a>監視に関する考慮事項

一元化されたログ記録システムには、純粋なログ以外でテレメトリを収集するための追加の役割があります。 データベースクエリの実行時間、web サーバーからの平均応答時間、オペレーティングシステムによって報告された CPU 負荷の平均とメモリの負荷など、メトリックを収集できます。 これらのシステムでは、ログと組み合わせて、システム内のノードとアプリケーション全体の正常性を総合的に把握することができます。

監視ツールのメトリック収集機能は、アプリケーション内から手動で渡すこともできます。 新規ユーザーのサインアップや注文の発注など、特に関心のあるビジネスフローは、中央監視システムのカウンターをインクリメントするようにインストルメント化することができます。 これにより、アプリケーションの正常性を監視するだけでなく、ビジネスの正常性を監視するために、監視ツールのロックが解除されます。

クエリは、特定の統計またはパターンを検索するために、ログ集計ツールで作成できます。これは、カスタムダッシュボードにグラフィカルな形式で表示できます。 多くの場合、チームは、アプリケーションに関連する統計情報をローテーションする、大きな壁にマウントされたディスプレイに投資します。 これにより、発生した問題を簡単に確認できます。

## <a name="when-to-use-alerts"></a>アラートを使用する場合

アプリケーションの問題に対処する必要がある場合は、適切な担当者に通知する何らかの方法が必要です。 これは、3番目のクラウドネイティブアプリケーション可観測性パターンであり、ログ記録と監視に依存します。 アプリケーションでは、問題の診断を可能にするためにログを記録し、場合によっては監視ツールにフィードする必要があります。 アプリケーションメトリックと正常性データを1か所で集計するには、監視が必要です。 この設定が完了すると、特定のメトリックが許容可能なレベルを超えたときにアラートをトリガーするルールを作成できます。

## <a name="alerts"></a>アラート

監視ツールに対するクエリを作成して、既知のエラー状態を調べることができます。 たとえば、クエリで受信ログを検索して、web サーバー上の問題を示す HTTP 状態コード500を検出することができます。 これらのうちの1つが検出されるとすぐに、調査を開始できる送信元サービスの所有者に電子メールまたは SMS を送信することができます。

通常、問題が発生したことを判断するには、1つの500エラーでは不十分です。 これは、ユーザーがパスワードを入力したか、形式が正しくないデータを入力したことを意味します。 警告クエリは、500エラーの平均値を超えた場合にのみ発生するように細工できます。

アラートに含まれる最も損傷のあるパターンの1つは、人が調査するアラートの数が多すぎることです。 サービスの所有者は、前に調査したエラーや問題が発生していないことがすぐに desensitized になります。 真のエラーが発生すると、何百も偽陽性が発生した場合に、そのノイズが失われます。 [かわいくウルフの人](https://en.wikipedia.org/wiki/The_Boy_Who_Cried_Wolf)は、この非常に危険なことを警告するために、多くの場合、子供に伝えます。 発生するアラートが実際の問題を示すものであることを確認することが重要です。

>[!div class="step-by-step"]
>[前へ](monitoring-health.md)
>[次へ](logging-with-elastic-stack.md)