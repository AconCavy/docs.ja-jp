---
ms.openlocfilehash: 08a9292c5a41e7b9b7c1bcc18ec96460de19863f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621183"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a><span data-ttu-id="b776b-101">Unicode が存在する場合の特別な相対 URI 表記のサポート</span><span class="sxs-lookup"><span data-stu-id="b776b-101">Support special relative URI notation when Unicode is present</span></span>

#### <a name="details"></a><span data-ttu-id="b776b-102">説明</span><span class="sxs-lookup"><span data-stu-id="b776b-102">Details</span></span>

<span data-ttu-id="b776b-103"><xref:System.Uri> では、Unicode を含む特定の相対 URI で <xref:System.Uri.TryCreate%2A> を呼び出したときに、<xref:System.NullReferenceException> がスローされなくなります。</span><span class="sxs-lookup"><span data-stu-id="b776b-103"><xref:System.Uri> will no longer throw a <xref:System.NullReferenceException> when calling <xref:System.Uri.TryCreate%2A> on certain relative URIs containing Unicode.</span></span> <span data-ttu-id="b776b-104"><xref:System.NullReferenceException> の最も単純な再現を以下に示します。2 つのステートメントは同等です。</span><span class="sxs-lookup"><span data-stu-id="b776b-104">The simplest reproduction of the <xref:System.NullReferenceException> is below, with the two statements being equivalent:</span></span><pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><span data-ttu-id="b776b-105"><xref:System.NullReferenceException> を再現するには、次の項目が true である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b776b-105">To reproduce the <xref:System.NullReferenceException>, the following items must be true:</span></span><ul><li><span data-ttu-id="b776b-106">URI は、前に "http:" を付加し、その後に "//" を付けずに相対として指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b776b-106">The URI must be specified as relative by prepending it with ‘http:’ and not following it with ‘//’.</span></span></li><li><span data-ttu-id="b776b-107">URI には、パーセントでエンコードされた Unicode または予約されていないシンボルを含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="b776b-107">The URI must contain percent-encoded Unicode or unreserved symbols.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="b776b-108">提案される解決策</span><span class="sxs-lookup"><span data-stu-id="b776b-108">Suggestion</span></span>

<span data-ttu-id="b776b-109">相対 URI を許可しないようにするためにこの動作に依存しているユーザーは、URI の作成時に代わりに <xref:System.UriKind.Absolute?displayProperty=nameWithType> を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b776b-109">Users depending on this behavior to disallow relative URIs should instead specify <xref:System.UriKind.Absolute?displayProperty=nameWithType> when creating a URI.</span></span>

| <span data-ttu-id="b776b-110">名前</span><span class="sxs-lookup"><span data-stu-id="b776b-110">Name</span></span>    | <span data-ttu-id="b776b-111">[値]</span><span class="sxs-lookup"><span data-stu-id="b776b-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b776b-112">スコープ</span><span class="sxs-lookup"><span data-stu-id="b776b-112">Scope</span></span>   |<span data-ttu-id="b776b-113">エッジ</span><span class="sxs-lookup"><span data-stu-id="b776b-113">Edge</span></span>|
|<span data-ttu-id="b776b-114">バージョン</span><span class="sxs-lookup"><span data-stu-id="b776b-114">Version</span></span>|<span data-ttu-id="b776b-115">4.7.2</span><span class="sxs-lookup"><span data-stu-id="b776b-115">4.7.2</span></span>|
|<span data-ttu-id="b776b-116">種類</span><span class="sxs-lookup"><span data-stu-id="b776b-116">Type</span></span>|<span data-ttu-id="b776b-117">ランタイム</span><span class="sxs-lookup"><span data-stu-id="b776b-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b776b-118">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="b776b-118">Affected APIs</span></span>

-<xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
