---
ms.openlocfilehash: b0e6d6f228647148083d3df64e65f817dc3455d5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379540"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a>System.Threading.Tasks.Task で監視されていない処理中の例外が、ファイナライザー スレッドに伝播されなくなった

|   |   |
|---|---|
|説明|<xref:System.Threading.Tasks.Task?displayProperty=name> クラスは非同期操作を表すため、非同期処理中に発生する重大ではない例外がすべてキャッチされます。 .NET Framework 4.5 では、例外が監視されていず、コードがタスクを待機していない場合、例外はファイナライザー スレッドに伝播されなくなり、ガベージ コレクション時にプロセスをクラッシュします。 この変更により、Task クラスを使用して、監視されていない非同期処理を実行するアプリケーションの信頼性が向上します。|
|提案される解決策|アプリが、監視されていない非同期例外のファイナライザー スレッドへの伝播に依存している場合、<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> イベントの適切なハンドラーを提供することによって、または[ランタイム構成要素](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)を設定することによって、以前の動作を復元できます。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
