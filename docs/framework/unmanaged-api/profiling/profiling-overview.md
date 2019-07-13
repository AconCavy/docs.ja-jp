---
title: プロファイリングの概要
ms.date: 03/30/2017
helpviewer_keywords:
- managed code, profiling API support
- unmanaged code, combining with managed code in profiling
- notification threads [.NET Framework profiling]
- unmanaged code, profiling
- profiling API [.NET Framework], and COM
- profiling API [.NET Framework], unmanaged code profiling
- profilers, writing
- profiling API [.NET Framework], call stacks
- code profilers, writing
- profiling API [.NET Framework], security considerations
- profiling API [.NET Framework], managed code support
- common language runtime, profiling
- profiling API [.NET Framework], notification threads
- call stacks [.NET Framework profiling]
- profiling API [.NET Framework], stack depth
- common language runtime, writing a profiler
- profiling API [.NET Framework], information retrieval interfaces
- shadow stacks [.NET Framework profiling]
- COM, using in the profiling API
- stack snapshots [.NET Framework profiling]
- profiling API [.NET Framework], supported features
- profiling API [.NET Framework], overview
- security, profiling API considerations
- stack depth [.NET Framework profiling]
ms.assetid: 864c2344-71dc-46f9-96b2-ed59fb6427a8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dbf36cec1bcd2ec1e96d57a889ddd9d9baef269
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663887"
---
# <a name="profiling-overview"></a>プロファイリングの概要

<a name="top"></a> プロファイラーは、別のアプリケーションの実行を監視するツールです。 共通言語ランタイム (CLR: Common Language Runtime) プロファイラーは、プロファイル API を使用して CLR とのメッセージの送受信を行う関数で構成されるダイナミック リンク ライブラリ (DLL: Dynamic Link Library) です。 プロファイラー DLL は、実行時に CLR によって読み込まれます。

従来のプロファイリング ツールは、アプリケーションの実行を測定することに重点を置いていました。 その主な役割は、各関数の実行にかかる時間やアプリケーションのメモリ使用状況を一定期間にわたって測定することでした。 プロファイル API は、コード カバレッジ ユーティリティや高度なデバッグ支援ツールなど、より幅広い診断ツールを対象にしています。 これらの用途には、いずれも診断的な性質があります。 プロファイル API は、アプリケーションの実行を測定するだけでなく、監視も行います。 そのため、プロファイル API をアプリケーション自体が使用することは避ける必要があります。また、アプリケーションの実行がプロファイラーに依存したり、プロファイラーの影響を受けたりしないようにする必要もあります。

CLR アプリケーションのプロファイリングには、通常のコンパイル済みマシン語コードのプロファイリングよりも多くのサポートが必要です。 その理由は、CLR には、アプリケーション ドメイン、ガベージ コレクション、マネージド例外処理、コードの Just-In-Time (JIT) コンパイル (Microsoft Intermediate Language (MSIL) コードからネイティブ マシン語コードへの変換) などの概念や同様の機能が採り入れられているためです。 通常のプロファイリング機構では、これらの機能に関する有益な情報を見つけたり、提供したりすることはできません。 プロファイル API は、CLR およびプロファイリングされたアプリケーションのパフォーマンスに大きな影響を与えることなく、この欠落した情報を効率的に提供します。

実行時に行われる JIT コンパイルは、プロファイリングを行ううえで絶好のタイミングとなります。 プロファイル API を使用すると、プロファイラーは、ルーチンの JIT コンパイルが行われる前に、ルーチンのメモリ内 MSIL コード ストリームを変更することができます。 この方法により、プロファイラーは、さらに詳細な調査が必要な特定のルーチンに動的にインストルメンテーション コードを追加できます。 この方法は従来のシナリオでも可能ですが、プロファイル API を使用する CLR の方が、実装はずっと簡単です。

この概要は、次のセクションで構成されています。

- [プロファイル API](#profiling_api)

- [サポートされる機能](#support)

- [通知スレッド](#notification_threads)

- [セキュリティ](#security)

- [マネージし、アンマネージ コード Profiler でのコードの結合](#combining_managed_unmanaged)

- [アンマネージ コードのプロファイリング](#unmanaged)

- [COM の使用](#com)

- [呼び出し履歴](#call_stacks)

- [コールバックとスタックの深さ](#callbacks)

- [関連トピック](#related_topics)

<a name="profiling_api"></a>

## <a name="the-profiling-api"></a>プロファイル API

通常、プロファイル API が書き込みに使用、*コード プロファイラー*、マネージ アプリケーションの実行を監視するプログラムであります。

プロファイル API は、プロファイラー DLL によって使用されます。プロファイラー DLL は、プロファイリング対象アプリケーションと同じプロセスに読み込まれます。 プロファイラー DLL は、コールバック インターフェイスを実装 ([ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) .NET Framework version 1.0 および 1.1 で[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)バージョン 2.0 以降)。 CLR は、このインターフェイス内のメソッドを呼び出して、プロファイリングされたプロセスのイベントをプロファイラーに通知します。 プロファイラーにコールバックするで、ランタイム内のメソッドを使用して、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)と[ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)インターフェイス、プロファイリングされたアプリケーションの状態に関する情報を取得します。

> [!NOTE]
> プロファイリングされたアプリケーションと同じプロセスで実行するのは、プロファイラー ソリューションのデータ収集の部分だけにしてください。 ユーザー インターフェイスとデータ分析は、すべて別のプロセスで実行する必要があります。

次の図は、プロファイラー DLL がプロファイリング対象アプリケーションおよび CLR とやり取りする方法を示しています。

![プロファイリング アーキテクチャを示すスクリーン ショット。](./media/profiling-overview/profiling-architecture.png)

### <a name="the-notification-interfaces"></a>通知インターフェイス

[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)と[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)通知インターフェイスと見なすことができます。 これらのインターフェイスで構成されているメソッドのなど[ClassLoadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)、 [ClassLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)、および[JITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)します。 クラスのロードまたはアンロード、関数のコンパイルなどを行うたびに、プロファイラーの `ICorProfilerCallback` インターフェイスまたは `ICorProfilerCallback2` インターフェイスの対応するメソッドが呼び出されます。

たとえば、プロファイラーでは、2 つの通知関数を使用してコードのパフォーマンスを測定でした。[FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)と[FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)します。 この場合は、各通知のタイムスタンプを記録し、結果を累積して、アプリケーションの実行時に CPU またはウォール クロック時間を最も多く使用した関数を示す一覧を出力します。

### <a name="the-information-retrieval-interfaces"></a>情報取得インターフェイス

プロファイルに関連するその他のメイン インターフェイスは[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)と[ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)します。 プロファイラーは、分析に役立つ追加情報を取得する必要がある場合に、これらのインターフェイスを呼び出します。 たとえば、CLR を呼び出すたびに、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)関数、関数の識別子が指定されます。 プロファイラーは呼び出すことでその関数の詳細についてを取得することができます、 [icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)関数の親クラス、その名前、および具合を探索する方法。

[ページのトップへ](#top)

<a name="support"></a>

## <a name="supported-features"></a>サポートされている機能

プロファイル API は、共通言語ランタイムで発生するさまざまなイベントとアクションについての情報を提供します。 この情報を使用して、プロセスの内部動作を監視し、.NET Framework アプリケーションのパフォーマンスを分析できます。

プロファイル API は、CLR で発生する以下のアクションとイベントについての情報を取得します。

- CLR のスタートアップ イベントとシャットダウン イベント。

- アプリケーション ドメインの作成イベントとシャットダウン イベント。

- アセンブリの読み込みイベントとアンロード イベント。

- モジュールの読み込みイベントとアンロード イベント。

- COM vtable の作成イベントと破棄イベント。

- Just-In-Time (JIT) コンパイル イベントとコード ピッチ イベント。

- クラスの読み込みイベントとアンロード イベント。

- スレッドの作成イベントと破棄イベント。

- 関数の開始イベントと終了イベント。

- 例外。

- マネージド コードとアンマネージド コードの実行の切り替え。

- 異なるランタイム コンテキスト間の切り替え。

- ランタイムの中断に関する情報。

- ランタイムのメモリ ヒープとガベージ コレクションのアクティビティに関する情報。

プロファイル API は、任意の (非マネージ) COM 互換言語から呼び出すことができます。

API は、CPU とメモリの消費に関しては効率的です。 プロファイルを実行しても、誤った結果をもたらすほどの大きい変化がプロファイリング対象のアプリケーションで発生することはありません。

プロファイル API は、サンプリング プロファイラーと非サンプリング プロファイラーの両方に役立ちます。 A*サンプリング プロファイラー*検査一定のクロック ティック単位でプロファイルと答えると、5 ミリ秒間隔。 A*非サンプリング プロファイラー*イベントの原因になったスレッドで同期的にイベントが通知されます。

### <a name="unsupported-functionality"></a>サポートされていない機能

プロファイル API は、以下の機能をサポートしていません。

- 従来の Win32 メソッドを使用してプロファイリングする必要があるアンマネージ コード。 ただし、CLR プロファイラーには、マネージド コードとアンマネージド コードの境界を判定するための遷移イベントが含まれます。

- アスペクト指向プログラミングなどの目的で自身のコードを変更する自動変更アプリケーション。

- 範囲チェック (プロファイル API がこの情報を提供しないため)。 CLR には、すべてのマネージド コードの範囲チェックのための組み込みサポートが用意されています。

- リモート プロファイル。次の理由によりサポートされません。

  - リモート プロファイルは実行時間が長くなります。 プロファイル インターフェイスを使用するときは、プロファイリングの結果が必要以上に影響を受けないように、実行時間を最小限にする必要があります。 実行パフォーマンスを監視するときには、これが特に重要です。 ただし、メモリの使用状況を監視するため、またはスタック フレームやオブジェクトなどについてのランタイム情報を取得するためにプロファイル インターフェイスを使用するときは、リモート プロファイルは制約になりません。

  - CLR コード プロファイラーは、プロファイリング対象のアプリケーションが実行しているローカル コンピューターのランタイムに、1 つ以上のコールバック インターフェイスを登録する必要があります。 これにより、リモート コード プロファイラーの作成が制限されます。

- 高可用性が必要な稼働環境でのプロファイル。 プロファイル API は、開発時の診断をサポートするために作成された API です。 稼働環境をサポートするために必要な厳密なテストは実施されていません。

[ページのトップへ](#top)

<a name="notification_threads"></a>

## <a name="notification-threads"></a>通知スレッド

通常は、イベントを生成するスレッドが通知も実行します。 このような通知 (たとえば、 [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)と[FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md))、明示的なを指定する必要はありません`ThreadID`します。 また、プロファイラーでは、グローバル ストレージに分析ブロックのインデックスを作成するのではなく、影響を受けるスレッドの `ThreadID` を基に、スレッド ローカル ストレージを使用して分析ブロックを格納および更新する方法を採用する場合があります。

これらのコールバックはシリアル化されないことに注意してください。 ユーザーは、スレッド セーフなデータ構造を作成すると共に、必要に応じてプロファイラー コードをロックして、複数のスレッドからの並行アクセスを防ぐことで、コードを保護する必要があります。 そのため、状況によっては、通常とは異なるシーケンスでコールバックを受け取る場合があります。 たとえば、マネージド アプリケーションで、まったく同じコードを実行する 2 つのスレッドを生成するとします。 ここを受信することは、 [icorprofilercallback::jitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)イベントを 1 つのスレッドからのいくつかの関数と`FunctionEnter`受信する前に、その他のスレッドからのコールバック、 [Icorprofilercallback::jitcompilationfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)コールバック。 この場合、ユーザーは、まだ完全に Just-In-Time (JIT) コンパイルが行われていない可能性がある関数についての `FunctionEnter` コールバックを受け取ります。

[ページのトップへ](#top)

<a name="security"></a>

## <a name="security"></a>セキュリティ

プロファイラーの DLL は、共通言語ランタイムの実行エンジンの一部として動作するアンマネージ DLL です。 そのため、プロファイラー DLL のコードは、マネージド コード アクセス セキュリティの制限を受けません。 プロファイラー DLL に対する唯一の制限は、プロファイリング対象のアプリケーションを実行しているユーザーに適用されるオペレーティング システムの制限です。

プロファイラーを作成するときは、セキュリティ関連の問題が発生しないように、適切な予防措置を講じる必要があります。 たとえば、インストール時には、プロファイラー DLL をアクセス制御リスト (ACL: Access Control List) に追加して、悪意のあるユーザーが DLL を変更できないようにします。

[ページのトップへ](#top)

<a name="combining_managed_unmanaged"></a>

## <a name="combining-managed-and-unmanaged-code-in-a-code-profiler"></a>コード プロファイラーでのマネージド コードとアンマネージド コードの結合

プロファイラーが正しく記述されていないと、循環参照が発生し、予期しない動作が引き起こされることがあります。

CLR プロファイル API をレビューすると、マネージド コンポーネントとアンマネージド コンポーネントの両方を使用してプロファイラーを作成し、COM 相互運用機能や間接呼び出しを通して互いを呼び出すことができるような印象を受けるかもしれません。

これは設計上は可能ですが、プロファイル API はマネージド コンポーネントをサポートしていません。 CLR プロファイラーは完全にアンマネージにする必要があります。 CLR プロファイラーでマネージド コードとアンマネージド コードを組み合わせようとすると、アクセス違反、プログラム エラー、またはデッドロックが発生する可能性があります。 プロファイラーのマネージド コンポーネントからアンマネージド コンポーネントに対してイベントが生成され、そのイベントでマネージド コンポーネントが再度呼び出されて、循環参照が発生することになります。

CLR プロファイラーがマネージド コードを安全に呼び出すことができる唯一の場所は、Microsoft Intermediate Language (MSIL) で表されたメソッドの本体です。 MSIL 本体を変更するための推奨される方法は、JIT 再コンパイル メソッドを使用する、 [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)インターフェイス。

また、MSIL を変更するために古いインストルメンテーション メソッドを使用することもできます。 プロファイラーがメソッドと、JIT コンパイルの MSIL 本体にマネージ呼び出しを挿入できる関数の・ イン タイム (JIT) コンパイルが完了する前に (を参照してください、 [icorprofilerinfo::getilfunctionbody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)メソッド)。 この方法で、マネージド コードの選択的インストルメンテーションや、JIT に関する統計およびパフォーマンス データの収集を行うことができます。

または、コード プロファイラーを使用して、アンマネージド コードを呼び出すすべてのマネージド関数の MSIL 本体にネイティブ フックを挿入することもできます。 この方法は、インストルメンテーションやカバレッジに使用できます。 たとえば、コード プロファイラーで各 MSIL ブロックの後ろにインストルメンテーション フックを挿入すると、そのブロックが実行されたことを確認できます。 メソッドの MSIL 本体の変更には細心の注意が要求され、多くの要素を検討する必要があります。

[ページのトップへ](#top)

<a name="unmanaged"></a>

## <a name="profiling-unmanaged-code"></a>アンマネージ コードのプロファイリング

共通言語ランタイム (CLR: Common Language Runtime) には、アンマネージ コードのプロファイリングについて最小限のサポートが用意されています。 次の機能があります。

- スタック チェーンの列挙。 この機能を使用すると、コード プロファイラーはマネージド コードとアンマネージド コードの境界を特定できます。

- スタック チェーンがマネージド コードまたはネイティブ コードに対応するかどうかの判定。

.NET Framework Versions 1.0 および 1.1 では、これらのメソッドは CLR デバッグ API のインプロセス サブセットを通して使用することができます。 これらは CorDebug.idl ファイルに定義されています。

.NET Framework 2.0 以降では、使用、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)この機能のためのメソッド。

[ページのトップへ](#top)

<a name="com"></a>

## <a name="using-com"></a>COM の使用

プロファイリングのインターフェイスは COM インターフェイスとして定義されますが、共通言語ランタイム (CLR: Common Language Runtime) は、これらのインターフェイスを使用するための COM の初期化を行いません。 使用して、スレッド処理モデルを設定しなくてもすむようにするため、 [CoInitialize](/windows/desktop/api/objbase/nf-objbase-coinitialize)関数の前に、マネージ アプリケーションの目的のスレッド処理モデルを指定することができます。 同様に、プロファイラーでも、プロファイリング対象アプリケーションと互換性のないスレッド処理モデルが選択されてアプリケーション エラーが発生する可能性を避けるために、`CoInitialize` を呼び出さないようにする必要があります。

[ページのトップへ](#top)

<a name="call_stacks"></a>

## <a name="call-stacks"></a>呼び出し履歴

プロファイル API には、呼び出し履歴を呼び出す 2 とおりの方法が用意されています。スタック スナップショットによる方法では呼び出し履歴を少ない頻度で収集でき、シャドウ スタックによる方法では呼び出し履歴を常時追跡します。

### <a name="stack-snapshot"></a>スタック スナップショット

スタック スナップショットは、ある特定の時点でのスレッドのスタックのトレースです。 プロファイル API はスタックでのマネージド関数のトレースをサポートしますが、アンマネージド 関数のトレースはプロファイラー独自のスタック ウォーカーで処理する必要があります。

プロファイラーでマネージ スタックをプログラムする方法の詳細については、次を参照してください。、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)このドキュメント セット内のメソッドと[、.NET Framework 2.0 における Profiler スタック ウォーク。基本、そしてその向こう](https://go.microsoft.com/fwlink/?LinkId=73638)します。

### <a name="shadow-stack"></a>シャドウ スタック

スナップショット方式を頻繁に使用すると、すぐにパフォーマンスの問題につながる可能性があります。 使用して場合、プロファイラーで代わりに、シャドウ スタックを構築スタック トレースを頻繁に行う場合は、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)、 [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)、[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)例外コールバック。 シャドウ スタックは常に最新であり、スタック スナップショットが必要なときいつでも簡単にストレージにコピーできます。

シャドウ スタックでは、関数の引数、戻り値、およびジェネリックなインスタンス化に関する情報を取得できます。 この情報は、シャドウ スタックを通してのみ使用でき、制御が関数に渡されたときに取得できます。 ただし、後から関数の実行中にこの情報を使用することはできません。

[ページのトップへ](#top)

<a name="callbacks"></a>

## <a name="callbacks-and-stack-depth"></a>コールバックとスタックの深さ

プロファイラー コールバックはスタックが非常に制約された環境で発行される場合があり、プロファイラー コールバックでスタック オーバーフローが発生すると、プロセスが直ちに終了することになります。 プロファイラーは、コールバックへの応答で使用するスタックを可能な限り少なくする必要があります。 スタック オーバーフローに対して耐性のあるプロセスでプロファイラーを使用する場合は、プロファイラー自体もスタック オーバーフローを発生させないようにする必要があります。

[ページのトップへ](#top)

<a name="related_topics"></a>

## <a name="related-topics"></a>関連トピック

|タイトル|説明|
|-----------|-----------------|
|[プロファイル環境の設定](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)|プロファイラーを初期化し、イベント通知を設定して、Windows サービスをプロファイリングする方法について説明します。|
|[プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)|プロファイル API で使用されるアンマネージ インターフェイスについて説明します。|
|[グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)|プロファイル API で使用されるアンマネージ グローバル静的関数について説明します。|
|[列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)|プロファイル API で使用されるアンマネージ列挙体について説明します。|
|[構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)|プロファイル API で使用されるアンマネージ構造体について説明します。|
