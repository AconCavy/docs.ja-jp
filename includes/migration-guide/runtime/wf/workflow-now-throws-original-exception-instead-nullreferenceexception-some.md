---
ms.openlocfilehash: 470fc2ddcfbb29a677cadb6e7e1d2e55784d7ac2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2020
ms.locfileid: "67802514"
---
### <a name="workflow-now-throws-original-exception-instead-of-nullreferenceexception-in-some-cases"></a><span data-ttu-id="61917-101">場合によって、ワークフローで NullReferenceException ではなく、元の例外がスローされるようになった</span><span class="sxs-lookup"><span data-stu-id="61917-101">Workflow now throws original exception instead of NullReferenceException in some cases</span></span>

|   |   |
|---|---|
|<span data-ttu-id="61917-102">説明</span><span class="sxs-lookup"><span data-stu-id="61917-102">Details</span></span>|<span data-ttu-id="61917-103">.NET Framework 4.6.2 ワークフロー アクティビティの Execute メソッドを使用して例外をスローした場合、以前のバージョンで、<code>null</code>値を<xref:System.Exception.Message>プロパティ、System.Activities ワークフロー ランタイムは、スロー、 <xref:System.NullReferenceException?displayProperty=name>、マスク、元の例外。 .NET Framework 4.7 以前マスクは、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="61917-103">In the .NET Framework 4.6.2 and earlier versions, when the Execute method of a workflow activity throws an exception with a <code>null</code> value for the <xref:System.Exception.Message> property, the System.Activities Workflow runtime throws a <xref:System.NullReferenceException?displayProperty=name>, masking the original exception.In the .NET Framework 4.7, the previously masked exception is thrown.</span></span>|
|<span data-ttu-id="61917-104">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="61917-104">Suggestion</span></span>|<span data-ttu-id="61917-105">コードが <xref:System.NullReferenceException?displayProperty=name> の処理に依存する場合は、カスタム アクティビティからスローされる可能性のある例外をキャッチするように変更します。</span><span class="sxs-lookup"><span data-stu-id="61917-105">If your code relies on handling the <xref:System.NullReferenceException?displayProperty=name>, change it to catch the exceptions that could be thrown from your custom activities.</span></span>|
|<span data-ttu-id="61917-106">スコープ</span><span class="sxs-lookup"><span data-stu-id="61917-106">Scope</span></span>|<span data-ttu-id="61917-107">Minor</span><span class="sxs-lookup"><span data-stu-id="61917-107">Minor</span></span>|
|<span data-ttu-id="61917-108">バージョン</span><span class="sxs-lookup"><span data-stu-id="61917-108">Version</span></span>|<span data-ttu-id="61917-109">4.7</span><span class="sxs-lookup"><span data-stu-id="61917-109">4.7</span></span>|
|<span data-ttu-id="61917-110">[種類]</span><span class="sxs-lookup"><span data-stu-id="61917-110">Type</span></span>|<span data-ttu-id="61917-111">ランタイム</span><span class="sxs-lookup"><span data-stu-id="61917-111">Runtime</span></span>|
|<span data-ttu-id="61917-112">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="61917-112">Affected APIs</span></span>|<ul><li><xref:System.Activities.CodeActivity.Execute(System.Activities.CodeActivityContext)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.AsyncCodeActivity%601.BeginExecute(System.Activities.AsyncCodeActivityContext,System.AsyncCallback,System.Object)?displayProperty=nameWithType></li><li><xref:System.Activities.WorkflowInvoker.Invoke?displayProperty=nameWithType></li></ul>|
