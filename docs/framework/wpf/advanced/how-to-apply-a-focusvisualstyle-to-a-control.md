---
title: '方法: FocusVisualStyle をコントロールに適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- properties [WPF], FocusVisualStyle
- FocusVisualStyle property [WPF]
ms.assetid: 363de99e-8ecc-438c-ac4a-f9147432ebd6
ms.openlocfilehash: 53d4984946143c15c4a2b71095529fb5ee7de4b1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051326"
---
# <a name="how-to-apply-a-focusvisualstyle-to-a-control"></a>方法: FocusVisualStyle をコントロールに適用する
この例は、リソースにフォーカスの visual スタイルを作成し、コントロールにスタイルを適用する方法を示しますを使用して、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティ。  
  
## <a name="example"></a>例  
 次の例は、そのコントロールがキーボードでフォーカスの場合にのみ適用される追加のコントロールの複合を作成するスタイルを定義、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。 スタイルを定義することでこれは、 <xref:System.Windows.Controls.ControlTemplate>、参照リソースとしてのスタイルを設定するときにその後、<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>プロパティ。  
  
 境界線に似た、外部の四角形は四角形領域の外側に配置されます。 スタイルのサイズ設定を使用して、それ以外の場合は変更しない限り、<xref:System.Windows.FrameworkElement.ActualHeight%2A>と<xref:System.Windows.FrameworkElement.ActualWidth%2A>の場合、フォーカスの視覚スタイルが適用される四角形のコントロール。 この例は、負の値を設定、<xref:System.Windows.FrameworkElement.Margin%2A>フォーカスされたコントロール外に若干の枠を作成します。  
  
 [!code-xaml[FEFocusVisualStyle#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFocusVisualStyle/CS/page1.xaml#xaml)]  
  
 A<xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>が付属している任意のコントロール テンプレートのスタイルに明示的なスタイルまたはテーマ スタイル; からコントロールの主なスタイルも作成できますを使用して、<xref:System.Windows.Controls.ControlTemplate>にそのスタイルを設定して、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ。  
  
 フォーカスの視覚スタイルはテーマまたは、UI 全体で一貫して使用する必要があります、異なる 2 つのフォーカスを設定できる各要素を使用するのではなく。 詳細については、次を参照してください。[コントロール、および FocusVisualStyle フォーカスのスタイル](styling-for-focus-in-controls-and-focusvisualstyle.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.FocusVisualStyle%2A>
- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [コントロールのフォーカスのスタイルと FocusVisualStyle](styling-for-focus-in-controls-and-focusvisualstyle.md)
