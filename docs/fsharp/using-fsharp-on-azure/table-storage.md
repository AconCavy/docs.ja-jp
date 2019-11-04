---
title: F# を使用した Azure Table Storage の概要
description: Azure Table storage または Azure Cosmos DB を使用して、構造化データをクラウドに格納します。
author: sylvanc
ms.date: 03/26/2018
ms.openlocfilehash: 6833e2264f7543f50b94892b6980140e4bf1cdd1
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424605"
---
# <a name="get-started-with-azure-table-storage-and-the-azure-cosmos-db-table-api-using-f"></a>F\# を使用して Azure Table storage と Azure Cosmos DB Table API を開始する

Azure Table storage は、構造化された NoSQL データをクラウドに格納するサービスです。 Table storage は、スキーマなしの設計によるキー/属性ストアです。 テーブルストレージはスキーマ aless であるため、アプリケーションのニーズの進化に合わせてデータを簡単に調整できます。 データへのアクセスは、あらゆる種類のアプリケーションで高速かつコスト効率の高い方法で実現できます。 通常、テーブルストレージは、類似したデータ量に対して従来の SQL よりも大幅に低コストになります。

Table storage を使用すると、web アプリケーションのユーザーデータ、アドレス帳、デバイス情報、およびサービスに必要なその他の種類のメタデータなど、柔軟なデータセットを格納できます。 テーブルには任意の数のエンティティを格納できます。ストレージアカウントには、ストレージアカウントの容量制限まで、任意の数のテーブルを含めることができます。

Azure Cosmos DB は、Azure Table storage 用に作成されたアプリケーションの Table API を提供し、次のような premium 機能を必要とします。

- ターンキーグローバル配信。
- 全世界の専用スループット。
- 99パーセンタイルでの1桁のミリ秒待機時間。
- 高可用性が保証されます。
- 自動セカンダリインデックス作成。

Azure Table storage 用に作成されたアプリケーションは、コードを変更せずに Table API を使用して Azure Cosmos DB に移行し、premium 機能を活用できます。 Table API には、.NET、Java、Python、および node.js で使用できるクライアント Sdk があります。

詳細については、「 [Azure Cosmos DB Table API の概要](https://docs.microsoft.com/azure/cosmos-db/table-introduction)」を参照してください。

## <a name="about-this-tutorial"></a>このチュートリアルについて

このチュートリアルでは、Azure F# table storage または Azure Cosmos DB Table API を使用して、テーブルの作成と削除、テーブルデータの挿入、更新、削除、クエリなどの一般的なタスクを実行するコードを記述する方法について説明します。

## <a name="prerequisites"></a>必要条件

このガイドを使用するには、最初に[Azure ストレージアカウント](/azure/storage/storage-create-storage-account)または[Azure Cosmos DB アカウント](https://azure.microsoft.com/try/cosmosdb/)を作成する必要があります。

## <a name="create-an-f-script-and-start-f-interactive"></a>F#スクリプトを作成してF#対話形式で起動する

この記事のサンプルは、 F#アプリケーションまたはF#スクリプトで使用できます。 F#スクリプトを作成するには、 F#開発環境で `.fsx` 拡張子を持つファイルを作成します (例: `tables.fsx`)。

次に、[パケット](https://fsprojects.github.io/Paket/)や[NuGet](https://www.nuget.org/)などの[パッケージマネージャー](package-management.md)を使用して、`#r` ディレクティブを使用してスクリプトに `WindowsAzure.Storage` パッケージと参照 `WindowsAzure.Storage.dll` をインストールします。 Microsoft Azure 名前空間を取得するために、`Microsoft.WindowsAzure.ConfigurationManager` に対してもう一度実行します。

### <a name="add-namespace-declarations"></a>名前空間宣言の追加

次の `open` ステートメントを `tables.fsx` ファイルの先頭に追加します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L1-L5)]

### <a name="get-your-azure-storage-connection-string"></a>Azure Storage 接続文字列を取得する

Azure Storage Table service に接続している場合は、このチュートリアルで使用する接続文字列が必要になります。 Azure portal から接続文字列をコピーできます。 接続文字列の詳細については、「[ストレージ接続文字列の構成](/azure/storage/storage-configure-connection-string)」を参照してください。

### <a name="get-your-azure-cosmos-db-connection-string"></a>Azure Cosmos DB 接続文字列を取得する

Azure Cosmos DB に接続している場合は、このチュートリアルで使用する接続文字列が必要になります。 Azure portal から接続文字列をコピーできます。 Azure portal の Cosmos DB アカウントで、 **[設定]**  >  **[接続文字列]** にアクセスし、 **[コピー]** ボタンをクリックしてプライマリ接続文字列をコピーします。

このチュートリアルでは、次の例のように、スクリプトに接続文字列を入力します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L11-L11)]

ただし、実際のプロジェクトではこの方法は**お勧めできません**。 ストレージアカウントキーは、ストレージアカウントのルートパスワードに似ています。 ストレージアカウントキーは常に慎重に保護してください。 他のユーザーに配布したり、ハードコーディングしたり、他のユーザーがアクセスできるプレーンテキストファイルに保存したりしないでください。 侵害された可能性があると思われる場合は、Azure ポータルを使用してキーを再生成することができます。

実際のアプリケーションでは、ストレージ接続文字列を維持する最善の方法は構成ファイルにあります。 構成ファイルから接続文字列を取得するには、次の手順を実行します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L13-L15)]

Azure Configuration Manager の使用は省略可能です。 .NET Framework の `ConfigurationManager` の種類などの API を使用することもできます。

### <a name="parse-the-connection-string"></a>接続文字列を解析する

接続文字列を解析するには、次のように指定します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L21-L22)]

`CloudStorageAccount`が返されます。

### <a name="create-the-table-service-client"></a>Table service クライアントを作成する

`CloudTableClient` クラスを使用すると、テーブルストレージ内のテーブルとエンティティを取得できます。 サービスクライアントを作成する方法の1つを次に示します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L28-L29)]

これで、からデータを読み取り、テーブルストレージにデータを書き込むコードを記述する準備ができました。

### <a name="create-a-table"></a>テーブルを作成する

この例では、テーブルがまだ存在しない場合に作成する方法を示します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L35-L39)]

### <a name="add-an-entity-to-a-table"></a>エンティティをテーブルに追加する

エンティティには `TableEntity` から継承する型が必要です。 任意の方法で `TableEntity` を拡張できますが、型にはパラメーターのないコンストラクターが*必要*です。 `get` と `set` の両方を持つプロパティのみが Azure テーブルに格納されます。

エンティティのパーティションキーと行キーは、テーブル内のエンティティを一意に識別します。 同じパーティションキーを持つエンティティは、異なるパーティションキーを持つエンティティよりも迅速に照会できますが、多様なパーティションキーを使用すると、並列操作のスケーラビリティが向上します。

`lastName` をパーティションキーとして使用し、`firstName` を行キーとして使用する `Customer` の例を次に示します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L45-L52)]

次に、`Customer` をテーブルに追加します。 これを行うには、テーブルで実行する `TableOperation` を作成します。 この場合は、`Insert` 操作を作成します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L54-L55)]

### <a name="insert-a-batch-of-entities"></a>エンティティのバッチを挿入する

1回の書き込み操作を使用して、エンティティのバッチをテーブルに挿入できます。 バッチ操作を使用すると、複数の操作を1回の実行にまとめることができますが、いくつかの制限があります。

- 同じバッチ操作で、更新、削除、および挿入を実行できます。
- バッチ操作には、最大100のエンティティを含めることができます。
- バッチ操作内のすべてのエンティティは、同じパーティションキーを持つ必要があります。
- バッチ操作でクエリを実行することはできますが、バッチ内の唯一の操作である必要があります。

バッチ操作に2つの挿入を結合するコードを次に示します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L62-L71)]

### <a name="retrieve-all-entities-in-a-partition"></a>パーティション内のすべてのエンティティを取得する

テーブルに対してパーティション内のすべてのエンティティを照会するには、`TableQuery` オブジェクトを使用します。 ここでは、"Smith" がパーティションキーであるエンティティをフィルター処理します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L77-L82)]

結果は次のように印刷されます。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L84-L85)]

### <a name="retrieve-a-range-of-entities-in-a-partition"></a>パーティション内のエンティティの範囲を取得する

パーティション内のすべてのエンティティに対してクエリを実行しない場合は、パーティションキーフィルターと行キーフィルターを組み合わせて範囲を指定できます。 ここでは、2つのフィルターを使用して、行キー (名) がアルファベットの "M" よりも前の文字で始まる "Smith" パーティション内のすべてのエンティティを取得します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L91-L100)]

結果は次のように印刷されます。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L102-L103)]

### <a name="retrieve-a-single-entity"></a>1つのエンティティを取得する

1つの特定のエンティティを取得するクエリを記述できます。 ここでは、`TableOperation` を使用して、"Ben Smith" という顧客を指定します。 コレクションではなく `Customer` が返されます。 クエリでパーティションキーと行キーの両方を指定することは、Table service から単一のエンティティを取得する最速の方法です。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L109-L111)]

結果は次のように印刷されます。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L113-L115)]

### <a name="replace-an-entity"></a>エンティティの置換

エンティティを更新するには、エンティティを Table service から取得し、エンティティオブジェクトを変更してから、`Replace` 操作を使用して Table service に変更を保存し直します。 これにより、サーバー上でエンティティが完全に置換されます。ただし、取得後にサーバー上のエンティティが変更された場合、操作は失敗します。 このエラーは、他のソースからの変更がアプリケーションによって誤って上書きされないようにするためのものです。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L121-L128)]

### <a name="insert-or-replace-an-entity"></a>エンティティの挿入または置換

場合によっては、テーブルにエンティティが存在するかどうかがわかりません。 その場合、現在格納されている値は不要になります。 エンティティを作成するには `InsertOrReplace` を使用し、状態にかかわらず、エンティティが存在する場合は置換します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L134-L141)]

### <a name="query-a-subset-of-entity-properties"></a>エンティティのプロパティのサブセットを照会する

テーブルクエリでは、エンティティのすべてではなく、いくつかのプロパティのみを取得できます。 射影と呼ばれるこの手法は、特に大規模なエンティティの場合に、クエリのパフォーマンスを向上させることができます。 ここでは、`DynamicTableEntity` と `EntityResolver` を使用して電子メールアドレスのみを返します。 プロジェクションはローカルストレージエミュレーターではサポートされていないため、このコードは Table service でアカウントを使用している場合にのみ実行します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L147-L158)]

### <a name="retrieve-entities-in-pages-asynchronously"></a>ページ内のエンティティを非同期に取得する

多数のエンティティを読み取っているときに、すべてのエンティティが返されるのを待機するのではなく、取得時に処理する場合は、セグメント化されたクエリを使用できます。 ここでは、非同期ワークフローを使用してページ内の結果を返し、多数の結果が返されるのを待機している間に実行がブロックされないようにします。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L163-L178)]

ここで、この計算を同期的に実行します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L180-L180)]

### <a name="delete-an-entity"></a>エンティティの削除

エンティティは、取得後に削除できます。 エンティティの更新と同様に、エンティティを取得した後にエンティティが変更された場合、これは失敗します。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L186-L187)]

### <a name="delete-a-table"></a>テーブルを削除する

ストレージアカウントからテーブルを削除できます。 削除されたテーブルは、削除後の一定期間、再作成することはできません。

[!code-fsharp[TableStorage](~/samples/snippets/fsharp/azure/table-storage.fsx#L193-L193)]

## <a name="next-steps"></a>次のステップ

これで、Table storage の基本を学習できました。さらに複雑なストレージタスクと Azure Cosmos DB Table API については、次のリンク先を参照してください。

- [Azure Cosmos DB Table API の概要](https://docs.microsoft.com/azure/cosmos-db/table-introduction)
- [.NET 用ストレージクライアントライブラリのリファレンス](https://docs.microsoft.com/dotnet/api/overview/azure/storage)
- [Azure Storage 型プロバイダー](https://fsprojects.github.io/AzureStorageTypeProvider/)
- [Azure Storage チームのブログ](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [接続文字列の構成](https://docs.microsoft.com/azure/storage/common/storage-configure-connection-string)
