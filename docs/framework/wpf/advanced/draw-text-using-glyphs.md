---
title: グリフを使用したテキストの描画
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 55bbc50de519d6607a843fcd633f2c07db53109f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010372"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="3dea6-102">グリフを使用したテキストの描画</span><span class="sxs-lookup"><span data-stu-id="3dea6-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="3dea6-103">このトピックでは、低レベルの <xref:System.Windows.Documents.Glyphs> オブジェクトを使用して [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] にテキストを表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3dea6-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="3dea6-104">例</span><span class="sxs-lookup"><span data-stu-id="3dea6-104">Example</span></span>  
 <span data-ttu-id="3dea6-105">次の例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] の <xref:System.Windows.Documents.Glyphs> オブジェクトのプロパティを定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3dea6-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="3dea6-106"><xref:System.Windows.Documents.Glyphs> オブジェクトによって、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の <xref:System.Windows.Media.GlyphRun> の出力を表します。</span><span class="sxs-lookup"><span data-stu-id="3dea6-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="3dea6-107">この例では、Arial、Courier New、Times New Roman フォントがローカル コンピューターの C:\WINDOWS\Fonts フォルダーにインストールされていると想定しています。</span><span class="sxs-lookup"><span data-stu-id="3dea6-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="3dea6-108">この例は、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の <xref:System.Windows.Documents.Glyphs> オブジェクトの他のプロパティを定義する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="3dea6-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="3dea6-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="3dea6-109">See also</span></span>

- [<span data-ttu-id="3dea6-110">WPF のタイポグラフィ</span><span class="sxs-lookup"><span data-stu-id="3dea6-110">Typography in WPF</span></span>](typography-in-wpf.md)
