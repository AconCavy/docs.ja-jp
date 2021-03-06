---
title: '破壊的変更: WPF アプリと WinForms アプリで OutputType が WinExe に設定されている'
description: .NET SDK 5.0.100 での破壊的変更について学習します。Windows フォーム アプリで OutputType が自動的に WinExe に設定されます。
ms.date: 09/18/2020
ms.openlocfilehash: 0b56db57d5242f2fb001c4de339a7f696c088dfc
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633858"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a>WPF アプリと WinForms アプリで OutputType が WinExe に設定されている

`OutputType` は、Windows Presentation Foundation (WPF) アプリと Windows フォーム アプリでは、自動的に `WinExe` に設定されます。 `OutputType` が `WinExe` に設定されている場合、アプリの実行時にコンソール ウィンドウは開きません。

## <a name="change-description"></a>変更内容

以前のバージョンの .NET SDK では、プロジェクト ファイルで `OutputType` に指定されている値が使用されます。 次に例を示します。

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

.NET SDK の 5.0.100 バージョンより、.NET Framework を含むあらゆるフレームワーク バージョンを対象にする WPF アプリと Windows フォーム アプリには `OutputType` が自動的に `WinExe` に設定されます。 次に例を示します。

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a>変更理由

WPF アプリまたは Windows フォーム アプリの実行時に、ほとんどのユーザーがコンソール ウィンドウを開かないことを前提としています。 さらに、[これらの種類のアプリケーションでは .NET SDK が使用され](sdk-and-target-framework-change.md) (Windows Desktop SDK が使用されるのではなく)、正しい既定値が設定されるようになります。 さらに、iOS と Android を対象としたサポートが追加されると、これらすべてで同じ出力の種類が使用される場合に、複数のプラットフォーム間で複数のターゲットを指定することが容易になります。

## <a name="version-introduced"></a>導入されたバージョン

.NET 5.0.100

## <a name="recommended-action"></a>推奨アクション

ユーザー側の対応は必要ありません。 ただし、以前の動作に戻す場合は、プロジェクト ファイルの `DisableWinExeOutputInference` プロパティを `true` に設定します。

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
