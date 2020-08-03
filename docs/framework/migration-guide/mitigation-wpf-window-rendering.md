---
title: '軽減策: WPF ウィンドウのレンダリング'
description: Windows 8 以降で実行されている .NET Framework 4.6 の WPF ウィンドウ レンダリングの影響と軽減策について説明します。
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
ms.openlocfilehash: d624478d17a4076107438f71b0a86eeb6d9f3ea4
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475334"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="5670c-103">軽減策:WPF ウィンドウのレンダリング</span><span class="sxs-lookup"><span data-stu-id="5670c-103">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="5670c-104">Windows 8 以上で実行している .NET Framework 4.6 では、マルチ モニターのシナリオで 1 つのディスプレイの外部にウィンドウを拡張すると、ウィンドウ全体がクリッピングなしでレンダリングされます。</span><span class="sxs-lookup"><span data-stu-id="5670c-104">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="5670c-105">影響</span><span class="sxs-lookup"><span data-stu-id="5670c-105">Impact</span></span>

<span data-ttu-id="5670c-106">一般に、複数のモニターで、クリッピングなしでウィンドウ全体を表示することが期待の動作です。</span><span class="sxs-lookup"><span data-stu-id="5670c-106">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="5670c-107">ただし、Windows 7 以前のバージョンでは、2 つ目のモニターにウィンドウの一部をレンダリングするとパフォーマンスに大きな影響があるため、WPF ウィンドウが 1 つのディスプレイの外部に拡張されるときにはクリッピングされます。</span><span class="sxs-lookup"><span data-stu-id="5670c-107">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="5670c-108">Windows 8 以上で複数のモニターに WPF ウィンドウをレンダリングする際の詳細な影響は、多数の要因に依存しているために、正確に数量化することはできません。</span><span class="sxs-lookup"><span data-stu-id="5670c-108">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="5670c-109">場合によっては、グラフィックを多用するアプリケーションを実行するユーザーや複数のモニターに及ぶウィンドウを使用するユーザーの場合は特に、依然としてパフォーマンスに望ましくない影響が生じることがあります。</span><span class="sxs-lookup"><span data-stu-id="5670c-109">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="5670c-110">または、.NET Framework の複数のバージョン間で一貫性のある動作が実現できれば十分な場合もあります 。</span><span class="sxs-lookup"><span data-stu-id="5670c-110">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="5670c-111">軽減策</span><span class="sxs-lookup"><span data-stu-id="5670c-111">Mitigation</span></span>

<span data-ttu-id="5670c-112">この変更を無効にして、WPF ウィンドウが 1 つのディスプレイを超える場合にクリッピングされるという、以前の動作に戻すこともできます。</span><span class="sxs-lookup"><span data-stu-id="5670c-112">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="5670c-113">これには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="5670c-113">There are two ways to do this:</span></span>

- <span data-ttu-id="5670c-114">`<EnableMultiMonitorDisplayClipping>` 要素をアプリケーションの構成ファイルの `<appSettings>` セクションに追加することにより、Windows 8 以降で実行中のアプリケーションでこの動作を無効にしたり有効にしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="5670c-114">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="5670c-115">たとえば、次の構成セクションにより、クリッピングなしのレンダリングが無効になります。</span><span class="sxs-lookup"><span data-stu-id="5670c-115">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="5670c-116">`<EnableMultiMonitorDisplayClipping>` 構成設定には、次の 2 つの値のいずれかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="5670c-116">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="5670c-117">`true` を指定すると、レンダリングの際にウィンドウをモニターの境界でクリッピングすることを有効にします。</span><span class="sxs-lookup"><span data-stu-id="5670c-117">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="5670c-118">`false` を指定すると、レンダリングの際にウィンドウをモニターの境界でクリッピングすることを無効にします。</span><span class="sxs-lookup"><span data-stu-id="5670c-118">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="5670c-119">これを行うには、アプリの起動時に <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="5670c-119">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="5670c-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="5670c-120">See also</span></span>

- [<span data-ttu-id="5670c-121">アプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="5670c-121">Application compatibility</span></span>](application-compatibility.md)
