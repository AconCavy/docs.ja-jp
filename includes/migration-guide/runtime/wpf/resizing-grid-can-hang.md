---
ms.openlocfilehash: 8dc1b4d94d01813a8124d1340b50fa78a9b157f8
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497330"
---
### <a name="resizing-a-grid-can-hang"></a>グリッドのサイズを変更すると、ハングする可能性がある

#### <a name="details"></a>説明

次の状況では、<code>T:System.Windows.Controls.Grid</code> のレイアウト中に無限ループが発生する可能性があります。<ul><li>行の定義に、MinHeight と MaxHeight の両方を宣言する、2 つの \*-row が含まれている。</li><li>\*-row の内容が対応する MaxHeight を超えていない</li><li>最初の MinHeight (その他の固定または自動の行を含む) がグリッドの利用可能な高さを超えている。</li><li>アプリの対象を .NET Framework 4.7 とする、または <code>Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=false</code> を設定して、4.7 割り当てアルゴリズムを利用することを選択する。</li></ul>また、3 つ以上の行または列でループが発生します。 この問題は .NET Framework 4.7.1 で修正されます。

#### <a name="suggestion"></a>提案される解決策

.NET Framework 4.7.1 にアップグレードします。  4\.7 割り当てアルゴリズムが必要でない場合は、次の構成設定を使用することもできます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| 名前    | 値       |
|:--------|:------------|
| スコープ   |エッジ|
|バージョン|4.7|
|種類|ランタイム|

#### <a name="affected-apis"></a>影響を受ける API

API 分析では検出できません。

<!--

#### Affected APIs

Not detectable via API analysis.

-->
