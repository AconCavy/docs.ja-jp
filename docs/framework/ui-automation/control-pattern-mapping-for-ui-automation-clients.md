---
title: UI オートメーション クライアントのコントロール パターン マッピング
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 48298cb8d89958c701d7150aeb497e82d565bde1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433861"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>UI オートメーション クライアントのコントロール パターン マッピング
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。  
  
 このトピックでは、コントロール型とそれに関連するコントロール パターンを示します。  
  
 次の表に、コントロール パターンを次のカテゴリに整理して示します。  
  
- サポートしています。 コントロールはこのコントロール パターンをサポートする必要があります。  
  
- 条件付きサポート。 コントロールは、その状態に応じてこのコントロール パターンをサポートする場合があります。  
  
- サポートされていません。 コントロールはこのコントロール パターンをサポートしません。カスタム コントロールは、このコントロール パターンをサポートする場合があります。  
  
> [!NOTE]
> 一部のコントロールは、その機能に応じて複数のコントロール パターンを条件付きでサポートします。 たとえば、メニュー項目コントロールは、メニュー コントロール内での機能に応じて、 <xref:System.Windows.Automation.InvokePattern>、 <xref:System.Windows.Automation.ExpandCollapsePattern>、 <xref:System.Windows.Automation.TogglePattern>、または <xref:System.Windows.Automation.SelectionItemPattern> コントロール パターンを条件付きでサポートします。  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>クライアントの UI オートメーション コントロール パターン  
  
|コントロール型|サポート状況|条件付きサポート|サポート非対象|  
|------------------|---------------|-------------------------|-------------------|  
|Button|None|呼び出し、トグル、展開/折りたたみ|None|  
|予定表|グリッド、テーブル|選択、スクロール|[値]|  
|チェック ボックス|切り替え|None|None|  
|コンボ ボックス|展開/折りたたみ|選択、値|スクロール|  
|データ グリッド|グリッド|スクロール、選択、テーブル|None|  
|データ項目|選択項目|展開/折りたたみ、グリッド項目、スクロール項目、テーブル、トグル、値|None|  
|ドキュメント|テキスト|スクロール、値|None|  
|編集|None|テキスト、範囲の値、値|None|  
|グループ化|None|展開/折りたたみ|None|  
|Header|None|Transform|None|  
|ヘッダー項目|None|変換、呼び出し|None|  
|ハイパーリンク|呼び出し|[値]|None|  
|Image|None|グリッド項目、テーブル項目|呼び出し、選択項目|  
|リスト|None|グリッド、複数のビュー、スクロール、選択|テーブル|  
|リスト項目|選択項目|展開/折りたたみ、グリッド項目、呼び出し、スクロール項目、トグル、値|None|  
|メニュー|None|None|None|  
|メニュー バー|None|展開/折りたたみ、ドック、変換|None|  
|メニュー項目|None|展開/折りたたみ、呼び出し、選択項目、トグル|None|  
|ペイン|None|ドック、 スクロール、変換|[Window]|  
|進行状況バー|None|範囲の値、値|None|  
|オプション ボタン|選択項目|None|切り替え|  
|スクロール バー|None|範囲値|スクロール|  
|区切り記号|None|None|None|  
|Slider|None|範囲の値、選択、値|None|  
|Spinner|None|範囲の値、選択、値|None|  
|分割ボタン|呼び出し、展開/折りたたみ|None|None|  
|ステータス バー|None|グリッド|None|  
|タブ|選択ツール|スクロール|None|  
|タブ項目|選択項目|None|呼び出し|  
|テーブル|グリッド、グリッド項目、テーブル、テーブル項目|None|None|  
|テキスト|None|グリッド項目、テーブル項目、テキスト|[値]|  
|つまみ|Transform|None|None|  
|タイトル バー|None|None|None|  
|ツール バー|None|ドック、展開/折りたたみ、変換|None|  
|ツール ヒント|None|テキスト、ウィンドウ|None|  
|ツリー|None|スクロール、選択|None|  
|ツリー項目|展開/折りたたみ|呼び出し、スクロール項目、選択項目、トグル|None|  
|[Window]|変換、ウィンドウ|ドッキング|None|  
  
> [!NOTE]
> 上記のサポート対象のコントロール パターンが存在せず、条件付きサポートのコントロール パターンが 1 つ以上存在するコントロール型では、それらの条件付きコントロール パターンのうちの 1 つが必ずサポートされます。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションの概要](ui-automation-overview.md)
