---
title: パブリッシュされた出力を dotnet vstest でテストします
description: dotnet vstest コマンドを使用して、ソース コードではなく、パブリッシュされたライブラリでテストを実行する方法を説明します。
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 660b966c6d02353b855e5728094083042a561558
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59126088"
---
# <a name="test-published-output-with-dotnet-vstest"></a>パブリッシュされた出力を dotnet vstest でテストします

`dotnet vstest` コマンドを使用して、パブリッシュ済みの出力に対してテストを行えます。 これは xUnit、MSTest、および NUnit の各テストで機能します。 次のように、パブリッシュされた出力の一部であった DLL ファイルを見つけて実行するだけです。

```
dotnet vstest <MyPublishedTests>.dll
```

`<MyPublishedTests>` はパブリッシュされたテスト プロジェクトの名前です。

## <a name="example"></a>例

次のコマンドは、パブリッシュされた DLL でのテストの実行を示しています。

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> メモ:アプリが `netcoreapp` 以外のフレームワークを対象とする場合でも、対象のフレームワークでフレームワーク フラグを付けて渡すことで `dotnet vstest` コマンドを実行できます。 たとえば、`dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"` のようにします。 Visual Studio 2017 Update 5 では、望ましいフレームワークが自動的に検出されます。

## <a name="see-also"></a>関連項目

- [dotnet テストおよび xUnit を使用した単体テスト](unit-testing-with-dotnet-test.md)
- [dotnet テストおよび NUnit を使用した単体テスト](unit-testing-with-nunit.md)
- [dotnet テストおよび MSTest を使用した単体テスト](unit-testing-with-mstest.md)
