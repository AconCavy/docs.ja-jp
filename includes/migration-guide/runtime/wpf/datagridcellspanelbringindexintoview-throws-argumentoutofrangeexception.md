---
ms.openlocfilehash: 1a1fc91ea2bb81e0f94b64323085ccf99072a1f5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59236043"
---
### <a name="datagridcellspanelbringindexintoview-throws-argumentoutofrangeexception"></a>DataGridCellsPanel.BringIndexIntoView で ArgumentOutOfRangeException がスローされる

|   |   |
|---|---|
|説明|列の仮想化は有効になっているが、列の幅がまだ決定されていない場合、<xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> は非同期で動作します。  非同期動作が発生する前に列が削除されると、<xref:System.ArgumentOutOfRangeException?displayProperty=name> が発生する場合があります。|
|提案される解決策|以下のいずれかを実行してください。<ol><li>.NET Framework 4.7 にアップグレードします。</li><li>.NET Framework 4.6.2 の最新のサービス パッチをインストールします。</li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)> に対する非同期応答が完了するまでは列を削除しないようにする。</li></ol>|
|スコープ|エッジ|
|Version|4.6.2|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object)?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.ScrollIntoView(System.Object,System.Windows.Controls.DataGridColumn)?displayProperty=nameWithType></li></ul>|
