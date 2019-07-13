---
ms.openlocfilehash: 088ebad0f822f791d05a8a8dafb0f7fd74f5581a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774198"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>ピクセルの高さが異なる項目を含むフラット リストでの項目スクロール

|   |   |
|---|---|
|説明|<xref:System.Windows.Controls.ItemsControl?displayProperty=name> に仮想化 (<code>IsVirtualizing=true</code>) と項目スクロール (<code>ScrollUnit=Item</code>) を使うコレクションが表示される場合、およびコントロールがスクロールされ、近隣項目と異なる高さ (ピクセル単位) の項目が表示される場合、<xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name> ではコレクション内のすべての項目に対してイテレーションが行われます。 このイテレーション中に UI は応答しません。コレクションのサイズが大きい場合、ハングとして認識される場合があります。他の状況では、以前の .NET Framework のリリースであっても、イテレーションは発生します。 たとえば、これは、ピクセル スクロール (<code>ScrollUnit=Pixel</code>) が高さの異なる項目 (ピクセル単位) を検出した場合、および階層データの項目スクロール (<xref:System.Windows.Controls.TreeView?displayProperty=name> や、グループ化が有効になっている <xref:System.Windows.Controls.ItemsControl?displayProperty=name> など) が近隣項目と異なる数の子項目を持つ項目を検出した場合に発生します。項目スクロールと高さが異なる (ピクセル単位) 場合の対処方として、階層データのレイアウトのバグを修正できるようイテレーションが .NET Framework 4.6.1 で導入されました。  データがフラットである場合 (階層がない場合) は必要ないため、そのような状況では .NET Framework 4.6.2 はイテレーションを行いません。|
|提案される解決策|.NET Framework 4.6.1 でイテレーションが発生し、以前のリリースでは発生しない場合、つまり <xref:System.Windows.Controls.ItemsControl?displayProperty=name> が異なる高さの (ピクセル単位) の項目を含むフラットなリストを項目スクロールしている場合、実行できる対応策は以下の 2 つです。<ol><li>.NET Framework 4.6.2 をインストールします。</li><li>.NET Framework 4.6.1 の修正プログラム HR 1605 をインストールします。</li></ol>|
|スコープ|マイナー|
|Version|4.6.1|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|
