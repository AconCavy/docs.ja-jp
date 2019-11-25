---
title: '軽減策: WPF レイアウト'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 7a074698fd203d0c5f9b799bfee8a6a9cb40800e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457786"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="35d5b-102">軽減策: WPF レイアウト</span><span class="sxs-lookup"><span data-stu-id="35d5b-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="35d5b-103">WPF コントロールのレイアウトが若干変化する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="35d5b-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="35d5b-104">影響</span><span class="sxs-lookup"><span data-stu-id="35d5b-104">Impact</span></span>  
 <span data-ttu-id="35d5b-105">この変更の結果、以下のようになります。</span><span class="sxs-lookup"><span data-stu-id="35d5b-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="35d5b-106">要素の幅または高さが最大で 1 ピクセル拡大または縮小することがあります。</span><span class="sxs-lookup"><span data-stu-id="35d5b-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="35d5b-107">オブジェクトの配置が最大で 1 ピクセル移動することがあります。</span><span class="sxs-lookup"><span data-stu-id="35d5b-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="35d5b-108">中央揃えの要素が中央から最大で 1 ピクセル垂直まは水平方向にずれることがあります。</span><span class="sxs-lookup"><span data-stu-id="35d5b-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="35d5b-109">既定では、この新しいレイアウトは .NET Framework の 4.6 を対象とするアプリに対してのみ有効となります。</span><span class="sxs-lookup"><span data-stu-id="35d5b-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="35d5b-110">軽減策</span><span class="sxs-lookup"><span data-stu-id="35d5b-110">Mitigation</span></span>  
 <span data-ttu-id="35d5b-111">この変更では、DPI が高いときにWPF コントロールの一番右または一番下でクリッピングの発生を除去する傾向があるため、app.config ファイルの `<runtime>` セクションに次の行を追加することによって、以前のバージョンの .NET Framework を対象としながら .NET Framework 4.6 上で実行されているアプリがこの新しい動作を選択ことができます。</span><span class="sxs-lookup"><span data-stu-id="35d5b-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="35d5b-112">.NET Framework 4.6 を対象としながら以前のレイアウト アルゴリズムを使用して WPF コントロールをレンダリングする必要があるアプリの場合、app.config ファイルの `<runtime>` セクションに次の行を追加することによってそれを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="35d5b-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="35d5b-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="35d5b-113">See also</span></span>

- [<span data-ttu-id="35d5b-114">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="35d5b-114">Application compatibility</span></span>](application-compatibility.md)
