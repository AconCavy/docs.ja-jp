---
ms.openlocfilehash: feae645fdb06d5a578832e0b18981668c42d4ad1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804353"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle が HWND 値を受け取るようになる

|   |   |
|---|---|
|説明|.NET Framework 2.0 で導入された <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> 値をアプリケーションに使用すると、親ウィンドウのハンドル値を登録できます。これを利用して、キーにアクセスする必要がある UI (PIN プロンプトや同意を求めるダイアログなど) を、指定したウィンドウの子のモーダルとして開くことができます。 .NET Framework 4.7 を対象とするアプリ以降では、Windows フォーム アプリケーションは、次のようなコードを使用して、<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> プロパティを設定できます。<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>以前のバージョンの .NET Framework では、[HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) 値が置かれているメモリ内の場所を表す <xref:System.IntPtr?displayProperty=name> が値として必要でした。 Windows 7 以前のバージョンでこのプロパティを form.Handle に設定しても影響はありませんでしたが、Windows 8 以降のバージョンでは、&quot;<xref:System.Security.Cryptography.CryptographicException?displayProperty=name>:パラメーターが正しくありません&quot; が表示されます。|
|提案される解決策|.NET Framework 4.7 以降をターゲットとするアプリケーションで親ウィンドウの関係を登録する場合、次のように単純な形式を使用することをお勧めします。<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>渡すべき正しい値が値 <code>form.Handle</code> を保持していたメモリ内の場所のアドレスであったことを特定していた場合、AppContext スイッチ <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> を <code>true</code> に設定し、動作変更を無効にできます。<ol><li>プログラムで AppContext の互換性スイッチを設定する (説明は[こちらに](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)あります)</li><li>app.config ファイルの <code>&lt;runtime&gt;</code> セクションに以下の行を追加する:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>逆に、アプリケーションが以前のバージョンの .NET Framework の下で読み込むとき、.NET Framework 4.7 ランタイムで新しい動作を選択する場合、AppContext スイッチを <code>false</code> に設定できます。|
|スコープ|マイナー|
|Version|4.7|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|
