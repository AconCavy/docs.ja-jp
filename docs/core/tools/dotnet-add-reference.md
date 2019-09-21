---
title: dotnet-add reference コマンド
description: dotnet add 参照コマンドは、プロジェクト間参照を追加する便利なオプションを提供します。
ms.date: 06/26/2019
ms.openlocfilehash: 867596058aad8f9c38918e6d6657709d0d0699b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784048"
---
# <a name="dotnet-add-reference"></a>dotnet-add 参照

**この記事の対象: ✓** .NET Core 1.x SDK 以降のバージョン

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>name

`dotnet add reference` - プロジェクト間 (P2P) 参照を追加します。

## <a name="synopsis"></a>構文

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>説明

`dotnet add reference` コマンドは、プロジェクトにプロジェクト参照を追加する便利なオプションを提供します。 このコマンドを実行すると、`<ProjectReference>` 要素がプロジェクト ファイルに追加されます。

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>引数

* **`PROJECT`**

  プロジェクト ファイルを指定します。 指定されていない場合、現在のディレクトリで検索されます。

* **`PROJECT_REFERENCES`**

  追加するプロジェクト間参照 (P2P) です。 1 つ以上のプロジェクトを指定します。 [glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースのシステムで利用できます。

## <a name="options"></a>オプション

* **`-h|--help`**

  コマンドの短いヘルプを印刷します。

* **`-f|--framework <FRAMEWORK>`**

  特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、プロジェクト参照を追加します。

* **`--interactive`**

  コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。 .NET Core 3.0 SDK 以降で使用できます。

## <a name="examples"></a>使用例

* プロジェクト参照を追加する:

  ```console
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

* 現在のディレクトリのプロジェクトに複数のプロジェクト参照を追加する:

  ```console
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

* Linux/Unix で glob パターンを使って複数のプロジェクト参照を追加する:

  ```console
  dotnet add app/app.csproj reference **/*.csproj
  ```
