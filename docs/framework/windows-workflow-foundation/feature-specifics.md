---
title: Windows Workflow Foundation の機能仕様
ms.date: 03/30/2017
ms.assetid: e84d12da-a055-45f6-b4d1-878d127b46b6
ms.openlocfilehash: 11bde5edea44f09ef1a5658cdf0e20ec1349c84b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182923"
---
# <a name="windows-workflow-foundation-feature-specifics"></a>Windows Workflow Foundation の機能仕様

.NET Framework 4 では、Windows ワークフローファウンデーションに多数の機能が追加されています。 このドキュメントでは、いくつかの新機能について説明し、役に立つ可能性のあるシナリオの詳細を示します。

## <a name="messaging-activities"></a>メッセージング アクティビティ

メッセージング アクティビティ (<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply>、 <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.ReceiveReply>、 、 ) は、ワークフローから WCF メッセージを送受信するために使用されます。 <xref:System.ServiceModel.Activities.Receive>アクティビティ<xref:System.ServiceModel.Activities.SendReply>は、標準の WCF Web サービスと同様に WSDL を介して公開される Windows 通信基盤 (WCF) サービス操作を形成するために使用されます。 <xref:System.ServiceModel.Activities.Send>WCF<xref:System.ServiceModel.Activities.ReceiveReply><xref:System.ServiceModel.ChannelFactory>に似た Web サービスを使用するために使用されます。事前に構成されたアクティビティを生成するワークフロー ファンデーションにも、**サービス参照の追加**エクスペリエンスが存在します。

### <a name="getting-started-with-messaging-activities"></a>メッセージング アクティビティの概要

- Visual Studio 2012 で、WCF ワークフロー サービス アプリケーション プロジェクトを作成します。 <xref:System.ServiceModel.Activities.Receive> と <xref:System.ServiceModel.Activities.SendReply> のペアがキャンバスに配置されます。

- プロジェクトを右クリックし、[**サービス参照の追加 ]** を選択します。 既存の Web サービス WSDL をポイントし **、[OK]** をクリックします。 生成されたアクティビティ ( を使用して実装された<xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.ReceiveReply>、 を使用して ) をツールボックスに表示するプロジェクトをビルドします。

- [ワークフロー サービスのドキュメント](../wcf/feature-details/workflow-services.md)

### <a name="messaging-activities-example-scenario"></a>メッセージング アクティビティのシナリオ例

サービス`BestPriceFinder`は、特定のルートの最高の航空券価格を見つけるために、複数の航空会社のサービスに呼び出します。 このシナリオを実装するには、メッセージ アクティビティを使用して価格要求を受信し、バックエンド サービスから価格を取得し、価格要求に最適な価格で返信する必要があります。 また、最適価格を計算するためのビジネス ロジックを作成するには、他のアウトオブボックス アクティビティを使用する必要もあります。

## <a name="workflowservicehost"></a>WorkflowServiceHost

<xref:System.ServiceModel.WorkflowServiceHost>は、複数のインスタンス、構成、および WCF メッセージングをサポートする、通常のワークフロー ホストです (ただし、ワークフローは、ホストされるためにメッセージングを使用する必要はありません)。 また、一連のサービス動作を介して永続性、追跡、およびインスタンス コントロールを統合します。 WCF<xref:System.ServiceModel.ServiceHost>と同様に<xref:System.ServiceModel.WorkflowServiceHost>、コンソール/WinForms/WPF アプリケーションまたは Windows サービス、または IIS または WAS の Web ホスト (.xamlx ファイルとして) で自己ホストできます。

### <a name="getting-started-with-workflow-service-host"></a>ワークフロー サービス ホストの概要

- Visual Studio 2010 で、WCF ワークフロー サービス アプリケーション プロジェクトを作成する:<xref:System.ServiceModel.WorkflowServiceHost>このプロジェクトは、Web ホスト環境で使用するように設定されます。

- 非メッセージング ワークフローをホストするには、メッセージに基づいてインスタンスを作成するカスタム <xref:System.ServiceModel.Activities.WorkflowHostingEndpoint> を追加します。

- ワークフロー インスタンスは、<xref:System.ServiceModel.Activities.WorkflowControlEndpoint> を <xref:System.ServiceModel.WorkflowServiceHost> に追加し、<xref:System.ServiceModel.Activities.WorkflowControlClient> を使用することで制御 (中断や終了など) できます。

- <xref:System.ServiceModel.WorkflowServiceHost> のサンプルは次のセクションにあります。

  - [実行](./samples/execution.md)

  - アプリケーション:[中断されたインスタンス管理](./samples/suspended-instance-management.md)

- [ワークフロー サービスのホスティングの概要](../wcf/feature-details/hosting-workflow-services-overview.md)

### <a name="workflowservicehost-scenario"></a>WorkflowServiceHost のシナリオ

BestPriceFinderサービスは、特定のルートに最適な航空券価格を見つけるために、複数の航空会社のサービスに呼び出します。 このシナリオを実装するには、 で<xref:System.ServiceModel.WorkflowServiceHost>ワークフローをホストする必要があります。 また、メッセージ アクティビティを使用して価格要求を受信し、バックエンド サービスから価格を取得し、価格要求に最適な価格で返信します。

## <a name="correlation"></a>Correlation

相関関係は次の 2 つのいずれかです。

- メッセージをグループ化する方法。つまり、要求メッセージとその応答の関係。

- サービス インスタンスにデータの一部をマッピングする方法。

### <a name="getting-started"></a>作業の開始

- 相関を開始するには、Visual Studio で新規プロジェクトを作成します。 <xref:System.ServiceModel.Activities.CorrelationHandle> 型の変数を作成します。

- メッセージのグループ化に使用する相関関係の例は、メッセージをグループ化する要求/応答の相関関係です。

  - <xref:System.ServiceModel.Activities.Receive>アクティビティで、プロパティを<xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A>クリックし、上記の最初<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>の手順で作成した CorrelationHandle を使用してを追加します。

  - アクティビティを<xref:System.ServiceModel.Activities.SendReply>作成するには、 を右クリック<xref:System.ServiceModel.Activities.Receive>し、[SendReply の作成] をクリックします。 これをワークフローの <xref:System.ServiceModel.Activities.Receive> アクティビティの後に貼り付けます。

- データの一部をサービス インスタンスにマッピングする例は、データの一部 (オーダー ID など) を特定のワークフロー インスタンスにマップするコンテンツ ベースの相関関係です。

  - 任意のメッセージング アクティビティで、`CorrelationInitializers` プロパティをクリックし、上記で作成した <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> 変数を使用して <xref:System.ServiceModel.Activities.CorrelationHandle> を追加します。 ドロップダウン メニューで、メッセージ上の目的のプロパティ (OrderID など) をダブルクリックします。 `CorrelatesWith` プロパティを上記で使用した <xref:System.ServiceModel.Activities.CorrelationHandle> 変数に設定します。

- [相関関係の概念説明ドキュメント](../wcf/feature-details/correlation.md)

### <a name="correlation-scenario"></a>相関関係のシナリオ

注文処理ワークフローは、新しい注文の作成を処理し、処理中の既存の注文を更新するために使用されます。 このシナリオを実装するには、ワークフローをで<xref:System.ServiceModel.WorkflowServiceHost>ホストし、メッセージング アクティビティを使用する必要があります。 また、正しいワークフロー`orderId`に対して確実に更新を行うために、 に基づく相関関係が必要になります。

## <a name="simplified-configuration"></a>簡略化された構成

WCF 構成スキーマは複雑で、多くの機能を見つけるのが難しいユーザーを提供します。 では[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]、WCF ユーザーが次の機能を使用してサービスを構成する手助けに重点を置いています。

- サービスごとの明示的な構成の必要性をなくします。 サービスのサービス>要素\<を構成せず、サービスがプログラムでエンドポイントを定義しない場合、エンドポイントのセットはサービスベース アドレスごとに 1 つずつ、サービスによって実装されたコントラクトごとに自動的に追加されます。

- 明示的な構成のないサービスに適用される WCF バインディングおよび動作の既定値をユーザーが定義できるようにします。

- 標準のエンドポイントは、事前に構成された再利用可能なエンドポイントを定義します。このエンドポイントは、1 つ以上のエンドポイント プロパティ (アドレス、バインド、およびコントラクト) に対して固定値を持ち、カスタム プロパティを定義できるようにします。

- 最後に、 <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601> WCF クライアント構成の集中管理を行うことができます。

### <a name="getting-started"></a>作業の開始

- [WCF 4.0 開発者ガイド](https://docs.microsoft.com/previous-versions/dotnet/articles/ee354381(v=msdn.10))

- [構成チャネル ファクトリ](xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601)

- [標準エンドポイント要素](xref:System.ServiceModel.Configuration.StandardEndpointElement)

- [.NET Framework 4 のサービス構成の改善](https://docs.microsoft.com/archive/blogs/endpoint/service-configuration-improvements-in-net-4)

- [.NET 4 でよくあるユーザーの誤り: WF/WCF サービス構成名の入力ミス](https://docs.microsoft.com/archive/blogs/endpoint/common-user-mistake-in-net-4-mistyping-the-wfwcf-service-configuration-name)

### <a name="simplified-configuration-scenarios"></a>簡略化された構成のシナリオ

- 経験豊富な ASMX 開発者が WCF の使用を開始したいと考えています。 しかし、WCF は複雑すぎるようです。 構成ファイルに書き込む必要のある情報は何ですか。 .NET 4 では、構成ファイルをまったく使用しないこともできます。

- 既存の WCF サービスのセットは構成とメンテナンスが非常に困難です。 構成ファイルには、変更するのが非常に危険な XML コードが何千行もあります。 コード量を管理しやすい量に減らすための支援が必要です。

## <a name="data-contract-resolver"></a>データ コントラクト リゾルバー

.NET 3.5 では、既知の型の設計にはいくつかの制限がありました。

- シリアル化または逆シリアル化中に既知の型を動的に追加することはできませんでした。

- シリアライザーは不明な xsi:type の情報を処理できませんでした。

- ユーザーは、ネットワーク上のシリアル化インスタンスのサイズを小さくするなど、ネットワーク上に出現する xsi:type を指定できませんでした。

[データ コントラクトリゾルバー](../wcf/samples/datacontractresolver.md)は、.NET 4.5 でこれらの問題を解決します。

### <a name="getting-started"></a>作業の開始

- [データ コントラクト リゾルバー API のドキュメント](xref:System.Runtime.Serialization.DataContractResolver)

- [データ コントラクト リゾルバーの概要](https://docs.microsoft.com/archive/blogs/youssefm/configuring-known-types-dynamically-introducing-the-datacontractresolver)

- サンプル:

  - [DataContractResolver](../wcf/samples/datacontractresolver.md)

  - [KnownAssemblyAttribute](../wcf/samples/knownassemblyattribute.md)

### <a name="data-contract-resolver-scenarios"></a>データ コントラクト リゾルバーのシナリオ

- 数十の <xref:System.Runtime.Serialization.KnownTypeAttribute> オブジェクトをサービスで宣言する必要性の回避。

- XML BLOB のサイズの削減。

## <a name="flowchart"></a>フローチャート

フローチャートは、ドメインの問題を視覚的に表すための既知のパラダイムです。 これは、.NET 4 で導入される新しい制御フロー スタイルです。 フローチャートの主な特性は、一度に 1 つのアクティビティのみ実行されることです。 フローチャートはループと代替結果を表すことができますが、その性質上、複数ノードの同時実行を表すことはできません。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 で、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーにフローチャートを追加します。

- フローチャート機能では、次のクラスを使用します。

  - <xref:System.Activities.Statements.Flowchart>

  - <xref:System.Activities.Statements.FlowNode>

  - <xref:System.Activities.Statements.FlowDecision>

  - <xref:System.Activities.Statements.FlowStep>

  - <xref:System.Activities.Statements.FlowSwitch%601>

- サンプル:

  - [TryCatch を使用した Flowchart アクティビティでのエラー処理](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

  - [雇用プロセス](./samples/hiring-process.md)

- デザイナー ドキュメント:

  - [フローチャート アクティビティ デザイナー](/visualstudio/workflow-designer/flowchart-activity-designers)

### <a name="flowchart-scenarios"></a>フローチャートのシナリオ

フローチャート アクティビティを使用して推測ゲームを実装できます。 推測ゲームは非常に単純です。コンピューターによってランダムな数値が選択され、プレーヤーはその数値を推測する必要があります。 プレイヤーが各推測を送信すると、コンピュータはヒントを表示します(つまり、「より低い数値を試す」)。 プレイヤーが7回未満の試行で数字を見つけた場合、彼らはコンピュータから特別な祝福を受けます。 このゲームは、次の手続き型アクティビティの組み合わせで実装できます。

- <xref:System.Activities.Statements.Sequence>

- <xref:System.Activities.Statements.While>

- <xref:System.Activities.Statements.Switch%601>

- <xref:System.Activities.Statements.TryCatch>

- <xref:System.Activities.Statements.Assign%601>

- <xref:System.Activities.Statements.If>

## <a name="procedural-activities-sequence-if-foreach-switch-assign-dowhile-while"></a>手続き型アクティビティ (Sequence、If、ForEach、Switch、Assign、DoWhile、While)

手続き型アクティビティは、プログラマになじみのある概念を使用してシーケンシャル制御フローをモデル化するメカニズムを提供します。 これらのアクティビティを使用すると、従来の構造化プログラミング言語コンストラクトが可能になり、必要に応じて C# や Visual Basic などの一般的な手続き言語と言語のパリティを提供します。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 で、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーで、手続き型アクティビティを追加します。

- サンプル:

  - [雇用プロセス](./samples/hiring-process.md)

  - [企業の購買プロセス](./samples/corporate-purchase-process.md)

- デザイナー ドキュメント:

  - [Parallel アクティビティ デザイナー](/visualstudio/workflow-designer/parallel-activity-designer)

  - [アクティビティ デザイナー\<>](/visualstudio/workflow-designer/parallelforeach-t-activity-designer)

### <a name="procedural-activity-scenarios"></a>手続き型アクティビティのシナリオ

- <xref:System.Activities.Statements.Parallel>: イントラネットのドキュメント管理システムには、ドキュメント承認ワークフローがあります。 ドキュメントは、イントラネットに公開する前に、複数の部門の担当者によって承認する必要があります。 承認に対して確立された注文はありません。ドキュメントが「承認待ち」フェーズにある間はいつでも発生します。 ユーザーがレビュー用にドキュメントを送信する場合、そのドキュメントは、直接管理者、イントラネット管理者、および内部コミュニケーション マネージャによって承認される必要があります。

- <xref:System.Activities.Statements.ParallelForEach%601>: WF アプリケーションは、大規模企業内での企業購買を管理します。 企業の規則では、購買作業を計画する前に 3 社の異なるベンダーを評価する必要があると規定されています。 購買部門の従業員が、会社の仕入先リストから 3 つの仕入先を選択します。 これらのベンダーを選択し、通知した後で、企業は経済提案書を待ちます。 提案書は任意の順序で到着します。 WF でこのシナリオを実装するには、ベンダーのコレクションを反復処理して経済提案書を求める <xref:System.Activities.Statements.ParallelForEach%601> を使用します。 すべての提案が収集された後で、最良の提案が選択されて表示されます。

## <a name="invokemethod"></a>InvokeMethod

<xref:System.Activities.Statements.InvokeMethod> アクティビティでは、オブジェクト内のパブリック メソッドまたはスコープ内の型を呼び出すことができます。 パラメーター付きまたはパラメーターなし (パラメーター配列を含む) でのインスタンス メソッドおよび静的メソッドの呼び出し、および汎用メソッドの呼び出しがサポートされます。 メソッドを同期および非同期で実行することもできます。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 で、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーに <xref:System.Activities.Statements.InvokeMethod> アクティビティを追加し、そこに静的メソッドとインスタンス メソッドを構成します。

- デザイナー ドキュメント: [InvokeMethod アクティビティ デザイナー](/visualstudio/workflow-designer/invokemethod-activity-designer)

### <a name="invokemethod-scenarios"></a>InvokeMethod のシナリオ

- スコープ内のオブジェクトのメソッドを呼び出す必要があります。 たとえば、辞書に値を追加する必要があります。 辞書のインスタンスの Add メソッドが呼び出され、キーと値が指定されます。

- レガシー CLR オブジェクトに対してメソッドを呼び出す必要があります。 カスタム アクティビティを作成してそのレガシー クラスの呼び出しをラップする代わりに、ワークフロー実行中にそのクラスがスコープ内にある場合には <xref:System.Activities.Statements.InvokeMethod> を使用できます。

## <a name="error-handling-activities"></a>エラー処理アクティビティ

この<xref:System.Activities.Statements.TryCatch>アクティビティは、一連の包含アクティビティの実行中に発生する例外をキャッチするメカニズムを提供します (C# および Visual Basic の Try/Catch コンストラクトと同様)。 <xref:System.Activities.Statements.TryCatch> はワークフロー レベルの例外処理を提供します。 ハンドルされない例外がスローされると、ワークフローは中止され、Finally ブロックは実行されません。 この動作は C# と一貫性があります。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 で、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーで <xref:System.Activities.Statements.TryCatch> アクティビティを追加します。

- サンプル: [tryCatch を使用したフローチャート アクティビティでのフォルト処理](./samples/fault-handling-in-a-flowchart-activity-using-trycatch.md)

- デザイナー ドキュメント:[エラー処理アクティビティ デザイナー](/visualstudio/workflow-designer/error-handling-activity-designers)

### <a name="error-handling-scenarios"></a>エラー処理のシナリオ

アクティビティのセットを実行する必要があり、エラーの発生時に特定のロジックを実行する必要があります。 そのエラー処理ロジック中にエラーが回復不能であることがわかった場合は、例外が再スローされ、親アクティビティ (またはホスト) によって問題が処理されます。

## <a name="pick-activity"></a>Pick アクティビティ

<xref:System.Activities.Statements.Pick> アクティビティは、WF でイベント ベースの制御フロー モデリングを提供します。 <xref:System.Activities.Statements.Pick> には、多数の分岐が含まれています。各分岐は、特定のイベントが発生すると実行されます。 この設定では、<xref:System.Activities.Statements.Pick> は、アクティビティがリッスンしているイベント セットの 1 つのみを実行する <xref:System.Activities.Statements.Switch%601> と同様に動作します。 各分岐はイベント ドリブンなので、発生したイベントが対応する分岐を実行します。 他のすべての分岐は、イベントのリッスンをキャンセルし、停止します。

### <a name="getting-started"></a>作業の開始

- Visual Studio 2012 で、ワークフロー コンソール アプリケーションを作成します。 ワークフロー デザイナーで <xref:System.Activities.Statements.Pick> アクティビティを追加します。

- サンプル:[ピッキングアクティビティの使用](./samples/using-the-pick-activity.md)

- デザイナーのドキュメント:[アクティビティ デザイナーの選択](/visualstudio/workflow-designer/pick-activity-designer)

### <a name="pick-scenario"></a>Pick のシナリオ

ユーザーに入力を求めるプロンプトを表示する必要があります。 通常の状況では、開発者はメソッド呼び出し<xref:System.Console.ReadLine%2A>を使用して、ユーザーの入力を求めます。 この設定の問題は、ユーザーが何か入力するまでプログラムが待機することです。 このシナリオでは、ブロッキング アクティビティのブロックを解除するためにタイムアウトが必要です。 一般的なシナリオでは、特定の期間内にタスクが完了する必要があります。 ブロッキング アクティビティのタイムアウトは、Pick が大量の値を追加するシナリオです。

## <a name="wcf-routing-service"></a>WCF ルーティング サービス

ルーティング サービスは、クライアントとサービス間で WCF メッセージがどのように流れるかを制御できる汎用ソフトウェア ルーターとして設計されています。 ルーティング サービスを使用すると、クライアントをサービスから切り離すことができます。 NET 3.5 では、クライアントとサービスが緊密に結合されていました。クライアントは、話し合う必要があるすべてのサービスと、その場所について知る必要がありました。 さらに、.NET Framework 3.5 の WCF には、次の制限がありました。

- ロジックをクライアントにハードコーディングする必要があったため、エラー処理が複雑でした。

- クライアントとサービスは常に同じバインディングを使用する必要がありました。

- サービスが適切に分類されていることはほとんどありませんでした。複数のサービス間で選択するよりも、クライアントがすべてを実装する 1 つのサービスと対話する方が簡単です。

.NET 4 のルーティング サービスは、これらの問題を簡単に解決できるように設計されています。 新しいルーティング サービスには次の機能があります。

1. コンテント ベースのルーティング (<xref:System.ServiceModel.Dispatcher.MessageFilter> オブジェクトがメッセージを調べて送信先を判断します。)

2. プロトコル ブリッジ (トランスポート & メッセージ)

3. エラー処理 (ルーターは、通信例外をキャッチし、バックアップ エンドポイントにフェールオーバーします)

4. <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> およびルーティング構成の動的 (メモリ内) 更新。

### <a name="getting-started"></a>作業の開始

1. ドキュメント:[ルーティング](../wcf/feature-details/routing.md)

2. サンプル: [WCF サンプル&#93;&#91;ルーティング サービス](../wcf/samples/routing-services.md)

3. ブログ:[ルーティングルール!](https://docs.microsoft.com/archive/blogs/RoutingRules/)

### <a name="routing-scenarios"></a>ルーティング シナリオ

ルーティング サービスは、次のシナリオに役立ちます。

- クライアントは、複数のサービスを直接アドレス指定することなく、これらのサービスと対話できます。

- クライアントは、ルーティング先を判断するためにクライアント要求で追加のロジックを実行できます。

- クライアントをリファクタリングすることなく、クライアントが実行する操作を複数のサービス実装に分解します。

- クライアントとサービスは、異なるセキュリティ設定の異なるバインディングで会話できます。

- クライアントは、障害またはサービスの使用不能に対してより堅牢になることができます。

## <a name="wcf-discovery"></a>WCF Discovery

WCF Discovery は、アプリケーション インフラストラクチャに探索メカニズムを組み込むことができるフレームワーク テクノロジです。 これを使用して、サービスを探索可能にし、サービスを検索するようにクライアントを構成できます。 クライアントはエンドポイントでハードコーディングする必要がなくなるため、アプリケーションはより堅牢になりフォールト トレランスが向上します。 探索は、アプリケーションに自動構成機能をビルドするための最適なプラットフォームです。

製品は、WS-Discovery 標準の上に構築されます。 相互運用可能で、拡張可能で、汎用的な設計をしています。 製品では 2 つの操作モードがサポートされます。

1. マネージド: 既存のサービスに関する知識を持つエンティティがネットワーク上にあり、クライアントは情報を直接クエリします。 これは Active Directory に類似しています。

2. アドホック: クライアントはマルチキャスト メッセージを使用してサービスを特定します。

さらに、探索メッセージはネットワーク プロトコルに依存しません。モード要件をサポートする任意のプロトコル上でこれらを使用できます。 たとえば、探索マルチキャスト メッセージは UDP チャネルまたはマルチキャスト メッセージングをサポートする他のネットワークを介して送信できます。 これらの設計ポイントと機能の柔軟性を組み合わせることで、ソリューションに合わせて検出を調整できます。

### <a name="getting-started"></a>作業の開始

- ドキュメント: [WCF ディスカバリ](../wcf/feature-details/wcf-discovery.md)

- サンプル:[検出 (サンプル)](../wcf/samples/discovery-samples.md)

### <a name="discovery-scenarios"></a>探索のシナリオ

サービスがいつ使用可能になるかが不明なため、開発者はエンドポイントのハードコーディングを望みません。 代わりに、開発者は実行時にサービスを選択することを望んでいます。 アプリケーションのコンポーネント間に、切り離し、堅牢性、および自動構成がさらに必要です。

## <a name="tracking"></a>追跡

ワークフロー追跡は、ワークフロー インスタンスの実行に関する洞察を提供します。 追跡イベントは、ワークフロー インスタンス レベルでワークフローから生成され、ワークフロー内のアクティビティが実行されるときに生成されます。 追跡レコードを定期受信するにはワークフロー追跡参加要素をワークフロー ホストに追加する必要があります。 追跡レコードは、追跡プロファイルを使用してフィルター処理されます。 .NET Framework は ETW (Windows 用イベント トレース) 追跡参加要素を提供し、基本プロファイルが machine.config ファイルにインストールされます。

### <a name="getting-started"></a>作業の開始

1. Visual Studio 2010 で、WCF ワークフロー サービス アプリケーション プロジェクトを作成します。 開始するキャンバスに <xref:System.ServiceModel.Activities.Receive> と <xref:System.ServiceModel.Activities.SendReply> のペアが配置されます。

2. web.config を開き、プロファイルなしで ETW 追跡動作を追加します。

    1. 既定のプロファイルが使用されます。

    2. イベント ビューアを開き、次のノードで分析チャネルを有効に**します。** **Applications and Services Logs** **Microsoft** **Windows** **Application Server-Applications** **[分析**] を右クリックし、[**ログの有効化**] を選択します。

    3. ワークフロー サービスを実行します。

    4. イベント ビューアーでワークフロー追跡イベントを確認します。

3. サンプル:[トラッキング](./samples/tracking.md)

4. 概念ドキュメント:[ワークフローの追跡とトレース](workflow-tracking-and-tracing.md)

## <a name="sql-workflow-instance-store"></a>SQL Workflow Instance Store

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> は、SQL Server ベースのインスタンス ストアの実装です。 インスタンス ストアは、実行中のインスタンスの状態を、そのインスタンスの読み込みと再開に必要なすべてのデータと共に格納します。 サービス ホストは、ワークフローが永続的な場合にインスタンス状態を保存するようインスタンス ストアに指示し、そのインスタンスのメッセージが到着するか遅延アクティビティが期限切れになったときにインスタンス状態を読み込むようインスタンス ストアに指示します。

### <a name="getting-started"></a>作業の開始

1. Visual Studio 2012 では、暗黙的または明示的<xref:System.Activities.Statements.Persist>なアクティビティを含むワークフローを作成します。 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 動作をワークフロー サービス ホストに追加します。 これはコードまたはアプリケーション構成ファイルで行うことができます。

2. サンプル:[永続性](/previous-versions/dotnet/netframework-4.0/dd699769(v%3dvs.100))

3. 概念ドキュメント: [SQL ワークフロー インスタンス ストア](sql-workflow-instance-store.md)
