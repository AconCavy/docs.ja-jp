---
ms.openlocfilehash: 5ba2ddb76ab946339449246840667ba4a48e9c66
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620245"
---
### <a name="exceptions-during-unobserved-processing-in-systemthreadingtaskstask-no-longer-propagate-on-finalizer-thread"></a><span data-ttu-id="acb6a-101">System.Threading.Tasks.Task で監視されていない処理中の例外が、ファイナライザー スレッドに伝播されなくなった</span><span class="sxs-lookup"><span data-stu-id="acb6a-101">Exceptions during unobserved processing in System.Threading.Tasks.Task no longer propagate on finalizer thread</span></span>

#### <a name="details"></a><span data-ttu-id="acb6a-102">説明</span><span class="sxs-lookup"><span data-stu-id="acb6a-102">Details</span></span>

<span data-ttu-id="acb6a-103"><xref:System.Threading.Tasks.Task?displayProperty=fullName> クラスは非同期操作を表すため、非同期処理中に発生する重大ではない例外がすべてキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="acb6a-103">Because the <xref:System.Threading.Tasks.Task?displayProperty=fullName> class represents an asynchronous operation, it catches all non-severe exceptions that occur during asynchronous processing.</span></span> <span data-ttu-id="acb6a-104">.NET Framework 4.5 では、例外が監視されていず、コードがタスクを待機していない場合、例外はファイナライザー スレッドに伝播されなくなり、ガベージ コレクション時にプロセスをクラッシュします。</span><span class="sxs-lookup"><span data-stu-id="acb6a-104">In the .NET Framework 4.5, if an exception is not observed and your code never waits on the task, the exception will no longer propagate on the finalizer thread and crash the process during garbage collection.</span></span> <span data-ttu-id="acb6a-105">この変更により、Task クラスを使用して、監視されていない非同期処理を実行するアプリケーションの信頼性が向上します。</span><span class="sxs-lookup"><span data-stu-id="acb6a-105">This change enhances the reliability of applications that use the Task class to perform unobserved asynchronous processing.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="acb6a-106">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="acb6a-106">Suggestion</span></span>

<span data-ttu-id="acb6a-107">アプリが、監視されていない非同期例外のファイナライザー スレッドへの伝播に依存している場合、<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> イベントの適切なハンドラーを提供することによって、または[ランタイム構成要素](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)を設定することによって、以前の動作を復元できます。</span><span class="sxs-lookup"><span data-stu-id="acb6a-107">If an app depends on unobserved asynchronous exceptions propagating to the finalizer thread, the previous behavior can be restored by providing an appropriate handler for the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> event, or by setting a [runtime configuration element](~/docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md).</span></span>

| <span data-ttu-id="acb6a-108">名前</span><span class="sxs-lookup"><span data-stu-id="acb6a-108">Name</span></span>    | <span data-ttu-id="acb6a-109">[値]</span><span class="sxs-lookup"><span data-stu-id="acb6a-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="acb6a-110">スコープ</span><span class="sxs-lookup"><span data-stu-id="acb6a-110">Scope</span></span>   |<span data-ttu-id="acb6a-111">エッジ</span><span class="sxs-lookup"><span data-stu-id="acb6a-111">Edge</span></span>|
|<span data-ttu-id="acb6a-112">バージョン</span><span class="sxs-lookup"><span data-stu-id="acb6a-112">Version</span></span>|<span data-ttu-id="acb6a-113">4.5</span><span class="sxs-lookup"><span data-stu-id="acb6a-113">4.5</span></span>|
|<span data-ttu-id="acb6a-114">種類</span><span class="sxs-lookup"><span data-stu-id="acb6a-114">Type</span></span>|<span data-ttu-id="acb6a-115">ランタイム</span><span class="sxs-lookup"><span data-stu-id="acb6a-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="acb6a-116">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="acb6a-116">Affected APIs</span></span>

-<xref:System.Threading.Tasks.Task.Run(System.Action)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Action,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run(System.Func{System.Threading.Tasks.Task},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{%60%600},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}})?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Run%60%601(System.Func{System.Threading.Tasks.Task{%60%600}},System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start?displayProperty=nameWithType></li><li><xref:System.Threading.Tasks.Task.Start(System.Threading.Tasks.TaskScheduler)?displayProperty=nameWithType></li></ul>|
