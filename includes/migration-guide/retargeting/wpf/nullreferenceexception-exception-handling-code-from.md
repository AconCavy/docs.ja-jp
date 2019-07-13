---
ms.openlocfilehash: e4cf139d308a1c12425d966a84d59a0c3bb89712
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236455"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>ImageSourceConverter.ConvertFrom からの例外処理コード内の NullReferenceException

|   |   |
|---|---|
|説明|<xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> の例外処理コードのエラーは、目的の例外 (<xref:System.IO.DirectoryNotFoundException?displayProperty=name>、<xref:System.IO.FileNotFoundException?displayProperty=name> など) の代わりにスローされる誤った <xref:System.NullReferenceException?displayProperty=name> を発生させていました。 この変更によりエラーが修正されるため、このメソッドは正しい例外をスローするようになりました。 <p/>既定では、.NET Framework 4.6.2 以前を対象とするすべてのアプリケーションが、引き続き互換性のために <xref:System.NullReferenceException?displayProperty=name> をスローします。 .NET Framework 4.7 以降を使用する開発者には、正しい例外が表示されます。|
|提案される解決策|NET Framework 4.7 を対象とする場合に <xref:System.NullReferenceException?displayProperty=name> を取得する構成に戻したい開発者は、アプリケーションの App.config ファイルに次のコードを追加/マージします。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
