---
ms.openlocfilehash: 34d7395e72f6ef252ac68366bcd346cd8d464036
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236128"
---
### <a name="support-special-relative-uri-notation-when-unicode-is-present"></a>Unicode が存在する場合の特別な相対 URI 表記のサポート

|   |   |
|---|---|
|説明|Unicode を含む特定の相対 URI で <xref:System.Uri.TryCreate%2A> を呼び出したときに、<xref:System.Uri> では <xref:System.NullReferenceException> がスローされなくなります。<xref:System.NullReferenceException> の最も単純な再現を以下に示します。2 つのステートメントは同等です。<pre><code class="lang-csharp">bool success = Uri.TryCreate(&quot;http:%C3%A8&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;bool success = Uri.TryCreate(&quot;http:&#232;&quot;, UriKind.RelativeOrAbsolute, out Uri href);&#13;&#10;</code></pre><xref:System.NullReferenceException> を再現するには、次の項目が true である必要があります。<ul><li>URI は、前に "http:" を付加し、その後に "//" を付けずに相対として指定する必要があります。</li><li>URI には、パーセントでエンコードされた Unicode または予約されていないシンボルを含める必要があります。</li></ul>|
|提案される解決策|相対 URI を許可しないようにするためにこの動作に依存しているユーザーは、URI の作成時に代わりに <xref:System.UriKind.Absolute?displayProperty=nameWithType> を指定する必要があります。|
|スコープ|エッジ|
|Version|4.7.2|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li></ul>|
