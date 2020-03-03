---
ms.openlocfilehash: 74ce1bbc9a887aee3a33eaf05084e8c2000967c2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379677"
---
### <a name="wpf-textbox-selected-text-appears-a-different-color-when-the-text-box-is-inactive"></a>WPF TextBox で選択されているテキストが、テキスト ボックスがアクティブでないときに異なる色で表示される

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、WPF テキスト ボックス コントロールがアクティブでないとき (フォーカスがないとき)、ボックス内で選択されているテキストは、コントロールがアクティブなときとは別の色で表示されます。|
|提案される解決策|<xref:System.Windows.FrameworkCompatibilityPreferences.AreInactiveSelectionHighlightBrushKeysSupported> プロパティを <code>false</code> に設定することで、以前 (.NET Framework 4.0) の動作が復元される可能性があります。|
|スコープ|エッジ|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
