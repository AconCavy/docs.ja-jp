---
title: dotnet list package コマンド
description: "\"dotnet list package\" コマンドでは、プロジェクトまたはソリューションのパッケージ参照を列挙する便利なオプションが提供されています。"
ms.date: 06/26/2019
ms.openlocfilehash: 98cc456fff02364310cec98f0282700f7697f07e
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421952"
---
# <a name="dotnet-list-package"></a>dotnet list package

[!INCLUDE [topic-appliesto-net-core-22plus](../../../includes/topic-appliesto-net-core-22plus.md)]

## <a name="name"></a>name

`dotnet list package` - プロジェクトまたはソリューションのパッケージ参照を一覧表示します。

## <a name="synopsis"></a>構文

```
dotnet list [<PROJECT>|<SOLUTION>] package [--config] [--framework] [--highest-minor] [--highest-patch] 
   [--include-prerelease] [--include-transitive] [--interactive] [--outdated] [--source]
dotnet list package [-h|--help]
```

## <a name="description"></a>説明

`dotnet list package` コマンドでは、特定のプロジェクトまたはソリューションのすべての NuGet パッケージ参照を列挙する便利なオプションが提供されています。 このコマンドで処理するために必要なアセットを用意するには、最初にプロジェクトをビルドする必要があります。 次の例では、[SentimentAnalysis](https://github.com/dotnet/samples/tree/master/machine-learning/tutorials/SentimentAnalysis) プロジェクトに対する `dotnet list package` コマンドの出力を示します。

```output
Project 'SentimentAnalysis' has the following package references
   [netcoreapp2.1]:
   Top-level Package               Requested   Resolved
   > Microsoft.ML                  0.11.0      0.11.0
   > Microsoft.NETCore.App   (A)   [2.1.0, )   2.1.0

(A) : Auto-referenced package.
```

**[Requested]** 列は、プロジェクト ファイルで指定されているパッケージのバージョンを示し、範囲で示されることもあります。 **[Resolved]** 列には、プロジェクトで現在使用されているバージョンが一覧表示され、常に単一の値です。 名前の隣に `(A)` と表示されているパッケージは、プロジェクトの設定から推論される[暗黙的なパッケージ参照](csproj.md#implicit-package-references)を表します (`Sdk` 型、`<TargetFramework>` プロパティ、`<TargetFrameworks>` プロパティなど)。

プロジェクトで使用されているパッケージのさらに新しいバージョンを利用可能かどうかを調べるには、`--outdated` オプションを使用します。 既定では、解決済みのバージョンがプレリリース バージョンでもある場合を除き、`--outdated` では最新の安定したパッケージが一覧表示されます。 新しいバージョンを一覧表示するときにプレリリース版を含めるには、`--include-prerelease` オプションも指定します。 次の例では、前の例と同じプロジェクトに対する `dotnet list package --outdated --include-prerelease` コマンドの出力を示します。

```output
The following sources were used:
   https://api.nuget.org/v3/index.json

Project `SentimentAnalysis` has the following updates to its packages
   [netcoreapp2.1]:
   Top-level Package      Requested   Resolved   Latest
   > Microsoft.ML         0.11.0      0.11.0     1.0.0-preview
```

プロジェクトに推移的依存関係があるかどうかを確認する必要がある場合は、`--include-transitive` オプションを使用します。 推移的依存関係は、プロジェクトに追加したパッケージがさらに別のパッケージに依存している場合に発生します。 次の例では、[HelloPlugin](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin/HelloPlugin) プロジェクトに対して `dotnet list package --include-transitive` コマンドを実行した出力を示します、最上位のパッケージと、それらが依存しているパッケージが表示されています。

```output
Project 'HelloPlugin' has the following package references
   [netcoreapp3.0]:
   Top-level Package                      Requested                    Resolved
   > Microsoft.NETCore.Platforms    (A)   [3.0.0-preview3.19128.7, )   3.0.0-preview3.19128.7
   > Microsoft.WindowsDesktop.App   (A)   [3.0.0-preview3-27504-2, )   3.0.0-preview3-27504-2

   Transitive Package               Resolved
   > Microsoft.NETCore.Targets      2.0.0
   > PluginBase                     1.0.0

(A) : Auto-referenced package.
```

## <a name="arguments"></a>引数

`PROJECT | SOLUTION`

対象のプロジェクトまたはソリューションのファイル。 指定されていない場合、現在のディレクトリで検索されます。 複数のソリューションまたはプロジェクトが見つかった場合は、エラーがスローされます。

## <a name="options"></a>オプション

* **`--config <SOURCE>`**

  より新しいパッケージを検索するときに使用する NuGet ソース。 `--outdated` オプションが必要です。

* **`--framework <FRAMEWORK>`**

  指定した[ターゲット フレームワーク](../../standard/frameworks.md)に該当するパッケージのみを表示します。 複数のフレームワークを指定するには、オプションを複数回繰り返します。 たとえば、`--framework netcoreapp2.2 --framework netstandard2.0` のように指定します。

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`--highest-minor`**

  新しいパッケージを検索するときに、メジャー バージョン番号が一致するパッケージのみを考慮します。 `--outdated` オプションが必要です。

* **`--highest-patch`**

  新しいパッケージを検索するときに、メジャー バージョン番号とマイナー バージョン番号が一致するパッケージのみを考慮します。 `--outdated` オプションが必要です。

* **`--include-prerelease`**

  新しいパッケージを検索するときに、プレリリース バージョンのパッケージを考慮します。 `--outdated` オプションが必要です。

* **`--include-transitive`**

  最上位のパッケージに加えて、推移的なパッケージを一覧表示します。 このオプションを指定すると、最上位のパッケージが依存しているパッケージの一覧が表示されます。

* **`--interactive`**

  コマンドを停止して、ユーザーの入力または操作のために待機させることができます。 たとえば、認証を完了する場合があります。 .NET Core 3.0 SDK 以降で使用できます。

* **`--outdated`**

  より新しいバージョンを使用できるパッケージを一覧表示します。

* **`-s|--source <SOURCE>`**

  より新しいパッケージを検索するときに使用する NuGet ソース。 `--outdated` オプションが必要です。

## <a name="examples"></a>使用例

* 特定のプロジェクトのパッケージ参照を一覧表示します。

  ```console
  dotnet list SentimentAnalysis.csproj package
  ```

* プレリリース バージョンを含め、さらに新しいバージョンを使用できるパッケージ参照を一覧表示します。

  ```console
  dotnet list package --outdated --include-prerelease
  ```

* 特定のターゲット フレームワークのパッケージ参照を一覧表示します。

  ```console
  dotnet list package --framework netcoreapp3.0
  ```
