---
title: 診断ツールの概要 - .NET Core
description: .NET Core アプリケーションの診断に使用できるツールと手法の概要。
ms.date: 07/16/2020
ms.topic: overview
ms.openlocfilehash: 568f237e131cde18dad7c87ddff2fdd3d4bc5b8b
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/09/2020
ms.locfileid: "89597977"
---
# <a name="what-diagnostic-tools-are-available-in-net-core"></a>.NET Core で使用できる診断ツール

ソフトウェアは期待どおりに動作するとは限りませんが、.NET Core には、そのような問題を迅速かつ効果的に診断するために役立つツールと API が用意されています。

この記事は、必要な各種ツールを見つけるために役立ちます。

## <a name="managed-debuggers"></a>マネージド デバッガー

[マネージド デバッガー](managed-debuggers.md)を使用すると、プログラムと対話することができます。 一時停止、段階的な実行、調査、および再開によって、コードの動作を分析できます。 デバッガーは、簡単に再現できる機能の問題を診断するための最初の選択肢です。

## <a name="logging-and-tracing"></a>ログとトレース

[ログとトレース](logging-tracing.md)は、関連する手法です。 ログ ファイルを作成するためのコードのインストルメント化を指します。 ファイルには、プログラムの機能の詳細が記録されます。 これらの詳細は、複雑度の高い問題を診断するために使用できます。 タイム スタンプと組み合わせると、これらの手法はパフォーマンスの調査にも役立ちます。

## <a name="unit-testing"></a>単体テスト

[単体テスト](../testing/index.md)は、高品質のソフトウェアを継続的に統合して展開するための重要なコンポーネントです。 単体テストは、何かを中断するときに早期警告を提供するように設計されています。

## <a name="debug-linux-dumps"></a>Linux ダンプのデバッグ

「[Linux ダンプのデバッグ](debug-linux-dumps.md)」では、Linux でダンプを収集して分析する方法について説明します。

## <a name="net-core-diagnostic-global-tools"></a>.NET Core 診断グローバル ツール

### <a name="dotnet-counters"></a>dotnet-カウンター

[dotnet-カウンター](dotnet-counters.md)は、第 1 レベルの正常性監視とパフォーマンス調査のためのパフォーマンス監視ツールです。 <xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視します。 たとえば、CPU 使用率や、.NET Core アプリケーションでスローされる例外の発生率などをすばやく監視できます。

### <a name="dotnet-dump"></a>dotnet-ダンプ

[dotnet-ダンプ](dotnet-dump.md) ツールは、ネイティブ デバッガーを使用せずに Windows と Linux のコア ダンプを収集して分析する方法です。

### <a name="dotnet-gcdump"></a>dotnet-gcdump

[dotnet-gcdump](dotnet-gcdump.md) ツールは、ライブ .NET プロセスの GC (ガベージ コレクター) ダンプを収集する手段です。

### <a name="dotnet-trace"></a>dotnet-トレース

.NET Core には、診断データが公開される `EventPipe` と呼ばれるものが含まれています。 [dotnet-トレース](dotnet-trace.md) ツールを使用すると、アプリから興味深いプロファイル データを使用できます。これは、アプリケーションの実行速度が低下する可能性のあるシナリオに役立ちます。

### <a name="dotnet-symbol"></a>dotnet-symbol

[dotnet-symbol](dotnet-symbol.md) によって、コア ダンプまたはミニダンプを開くために必要なファイル (シンボル、DAC/DBI、ホスト ファイルなど) をダウンロードできます。 別のコンピューターでキャプチャされたダンプ ファイルをデバッグするためにシンボルとモジュールが必要な場合は、このツールを使用します。

### <a name="dotnet-sos"></a>dotnet-sos

[dotnet-sos](dotnet-sos.md) を使用すると、Linux または MacOS (または、以前のデバッグ ツールを使用している場合は Windows) に [SOS デバッガー拡張](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension)をインストールできます。

## <a name="net-core-diagnostics-tutorials"></a>.NET Core 診断チュートリアル

### <a name="debug-a-memory-leak"></a>メモリ リークをデバッグする

[チュートリアル: メモリ リークをデバッグする](debug-memory-leak.md)では、メモリ リークを検出する手順について説明します。 リークを確認するには [dotnet-counters](dotnet-counters.md) ツールを使用し、リークを診断するには [dotnet-dump](dotnet-dump.md) ツールを使用します。

### <a name="debug-high-cpu-usage"></a>高い CPU 使用率をデバッグする

[チュートリアル: 高い CPU 使用率をデバッグする](debug-highcpu.md) に関するページに、高い CPU 使用率の調査方法が示されています。 高い CPU 使用率を確認するために、[dotnet-counters](dotnet-counters.md) ツールが使用されます。 次に、[パフォーマンス分析ユーティリティ (`dotnet-trace`) 用のトレース](dotnet-trace.md)または Linux `perf` を使用して、CPU 使用率プロファイルを収集および表示する手順について説明します。

### <a name="debug-deadlock"></a>デッドロックをデバッグする

[チュートリアル: デッドロックのデバッグ](debug-deadlock.md)に関するページに、[dotnet-dump](dotnet-dump.md) ツールを使用してスレッドとロックを調査する方法が示されています。
