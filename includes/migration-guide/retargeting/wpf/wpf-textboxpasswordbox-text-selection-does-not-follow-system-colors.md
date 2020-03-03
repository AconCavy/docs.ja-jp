---
ms.openlocfilehash: 3f88c8b80518aa65c082dc3da2d75b5221dd00f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774100"
---
### <a name="wpf-textboxpasswordbox-text-selection-does-not-follow-system-colors"></a>WPF TextBox/PasswordBox のテキスト選択がシステム カラーに従っていない

|   |   |
|---|---|
|説明|.NET Framework 4.7.1 以前のバージョンでは、WPF の <code>System.Windows.Controls.TextBox</code> および <code>System.Windows.Controls.PasswordBox</code> は装飾層のテキスト選択のみをレンダリングできました。 そのため、一部のシステム テーマではテキストが遮られ、読みにくくなっていました。  .NET framework 4.7.2 以降では、開発者は、この問題を軽減する非装飾ベースの選択レンダリング スキームを有効にするオプションを選択することができます。|
|提案される解決策|この変更を利用する開発者は、次の AppContext フラグを適切に設定する必要があります。  この機能を利用するには、インストールされている .NET Framework のバージョンが 4.7.2 以上である必要があります。非装飾ベースの選択を有効にするには、次の AppContext フラグを使用します。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Text.UseAdornerForTextboxSelectionRendering=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7.2|
|型|再ターゲット中|
