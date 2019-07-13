---
ms.openlocfilehash: 1b68caebb3abad36f1809ff3ba096b24de3e1ab4
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65212001"
---
### <a name="aspnet-accessibility-improvements-in-net-framework-471"></a>.NET Framework 4.7.1 の ASP.NET アクセシビリティ機能の強化

|   |   |
|---|---|
|説明|.NET Framework 4.7.1 以降、ASP.NET のお客様のサポートを改善する目的で、ASP.NET Web コントロールによる Visual Studio のアクセシビリティ テクノロジの処理方法が向上しています。  この機能強化には次の変更内容が含まれています。<ul><li>[詳細の表示] ウィザードの [フィールドの追加] ダイアログや ListView ウィザードの [ListView の構成] ダイアログなど、コントロールで不足していた UI アクセシビリティ パターンを実装するための変更。</li><li>データ ページャー フィールド エディターなど、ハイ コントラスト モードでの表示を改善するための変更。</li><li>DataPager コントロールの [ページャーのフィールドを編集] ウィザードの [フィールド] ダイアログ、[ObjectContext の構成] ダイアログ、[データ ソースの構成] ウィザードの [データの選択の構成] ダイアログなど、キーボードの操作性を改善するための変更。</li></ul>|
|提案される解決策|<strong>以上の変更を選択する方法と選択しない方法</strong> Visual Studio デザイナーの場合、.NET Framework 4.7.1 以降で実行しなければ、以上の変更から改善を得ることはありません。 Web アプリケーションの場合、次のいずれかの手法をとることで、以上の変更によって機能が強化されます。<ul><li>Visual Studio 2017 15.3 以降をインストールする。このバージョンからは既定で、次の項目にある AppContext スイッチで新しいアクセシビリティ機能に対応しています。</li><li>下の例のように、devenv.exe.config ファイルの <code>&lt;runtime&gt;</code> セクションに <code>Switch.UseLegacyAccessibilityFeatures</code> AppContext スイッチを追加し、それを <code>false</code> に設定することで、以前のアクセシビリティ動作を無効にする。</li></ul><pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;...&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false&#39;  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;...&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>.NET Framework 4.7.1 以降を対象とするアプリケーションで以前のアクセシビリティ動作を残す場合、この AppContext スイッチを明示的に <code>true</code> に設定することで以前のアクセシビリティ機能を選択できます。|
|スコープ|マイナー|
|Version|4.7.1|
|型|再ターゲット中|
