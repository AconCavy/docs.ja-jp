---
title: '方法: ページからウィンドウの高さを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007311"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a>方法: ページからウィンドウの高さを設定する
この例からウィンドウの高さを設定する方法を示しています、<xref:System.Windows.Controls.Page>します。  
  
## <a name="example"></a>例  
 A<xref:System.Windows.Controls.Page>を設定して、そのホスト ウィンドウの高さを設定できます<xref:System.Windows.Controls.Page.WindowHeight%2A>します。 このプロパティにより、<xref:System.Windows.Controls.Page>をそれをホストするウィンドウの種類の明示的な知識を持たない。  
  
> [!NOTE]
>  使用してウィンドウの高さを設定する<xref:System.Windows.Controls.Page.WindowHeight%2A>、<xref:System.Windows.Controls.Page>ウィンドウの子である必要があります。  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
