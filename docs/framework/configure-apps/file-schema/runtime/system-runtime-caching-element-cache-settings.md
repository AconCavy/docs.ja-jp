---
title: <system.runtime.caching> 要素 (キャッシュ設定)
ms.date: 03/30/2017
helpviewer_keywords:
- <system.runtime.caching> element
- caching [.NET Framework], configuration
- system.runtime.caching element
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
ms.openlocfilehash: 70573f92f1799a54116bc91f7a39d157a7ae5b36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115515"
---
# <a name="systemruntimecaching-element-cache-settings"></a><span data-ttu-id="b3c5d-102">\<system.runtime.caching> 要素 (キャッシュ設定)</span><span class="sxs-lookup"><span data-stu-id="b3c5d-102">\<system.runtime.caching> Element (Cache Settings)</span></span>

<span data-ttu-id="b3c5d-103">構成ファイル内の <xref:System.Runtime.Caching.ObjectCache> エントリを使用して既定のメモリ内の `memoryCache` の実装の構成を提供します。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-103">Provides configuration for the default in-memory <xref:System.Runtime.Caching.ObjectCache> implementation through the `memoryCache` entry in the configuration file.</span></span>  
  
<span data-ttu-id="b3c5d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b3c5d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b3c5d-105">&nbsp;&nbsp; **\<system.runtime.caching>**</span><span class="sxs-lookup"><span data-stu-id="b3c5d-105">&nbsp;&nbsp;**\<system.runtime.caching>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3c5d-106">構文</span><span class="sxs-lookup"><span data-stu-id="b3c5d-106">Syntax</span></span>  
  
```xml  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3c5d-107">属性および要素</span><span class="sxs-lookup"><span data-stu-id="b3c5d-107">Attributes and Elements</span></span>

<span data-ttu-id="b3c5d-108">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3c5d-109">属性</span><span class="sxs-lookup"><span data-stu-id="b3c5d-109">Attributes</span></span>

`None`  

### <a name="child-elements"></a><span data-ttu-id="b3c5d-110">子要素</span><span class="sxs-lookup"><span data-stu-id="b3c5d-110">Child Elements</span></span>

|<span data-ttu-id="b3c5d-111">要素</span><span class="sxs-lookup"><span data-stu-id="b3c5d-111">Element</span></span>|<span data-ttu-id="b3c5d-112">説明</span><span class="sxs-lookup"><span data-stu-id="b3c5d-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3c5d-113">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="b3c5d-113">\<memoryCache></span></span>](memorycache-element-cache-settings.md)|<span data-ttu-id="b3c5d-114"><xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-114">Defines an element that is used to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3c5d-115">親要素</span><span class="sxs-lookup"><span data-stu-id="b3c5d-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b3c5d-116">要素</span><span class="sxs-lookup"><span data-stu-id="b3c5d-116">Element</span></span>|<span data-ttu-id="b3c5d-117">説明</span><span class="sxs-lookup"><span data-stu-id="b3c5d-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b3c5d-118">\<configuration></span><span class="sxs-lookup"><span data-stu-id="b3c5d-118">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="b3c5d-119">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-119">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c5d-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="b3c5d-120">Remarks</span></span>

<span data-ttu-id="b3c5d-121">この名前空間のクラスは、ASP.NET のキャッシュ機能と同様のキャッシュ機能を使用する方法を提供しますが、 `System.Web` アセンブリに依存しません。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-121">The classes in this namespace provide a way to use caching facilities like those in ASP.NET, but without a dependency on the `System.Web` assembly.</span></span> <span data-ttu-id="b3c5d-122">詳細については、「 [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-122">For more information, see [Caching in .NET Framework Applications](../../../performance/caching-in-net-framework-applications.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b3c5d-123"><xref:System.Runtime.Caching> 名前空間の出力キャッシュ機能と型は、.NET Framework 4 で新たに追加されています。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-123">The output caching functionality and types in the <xref:System.Runtime.Caching> namespace are new in .NET Framework 4.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3c5d-124">例</span><span class="sxs-lookup"><span data-stu-id="b3c5d-124">Example</span></span>

<span data-ttu-id="b3c5d-125">次の例では、 <xref:System.Runtime.Caching.MemoryCache> クラスを元にしたキャッシュの構成方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-125">The following example shows how to configure a cache that is based on the <xref:System.Runtime.Caching.MemoryCache> class.</span></span> <span data-ttu-id="b3c5d-126">この例では、メモリ キャッシュ用の `namedCaches` エントリのインスタンスの構成を方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-126">The example shows how to configure an instance of the `namedCaches` entry for memory cache.</span></span> <span data-ttu-id="b3c5d-127">キャッシュの名前は、`name` 属性を "Default" に設定することによって、既定のキャッシュエントリ名に設定されます。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-127">The name of the cache is set to the default cache entry name by setting the `name` attribute to "Default".</span></span>  
  
<span data-ttu-id="b3c5d-128">`cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-128">The `cacheMemoryLimitMegabytes` attribute and the `physicalMemoryPercentage` attribute are set to zero.</span></span> <span data-ttu-id="b3c5d-129">これらの属性をゼロに設定すると、 <xref:System.Runtime.Caching.MemoryCache> の自動サイズ調整ヒューリスティックが既定で使用されることになります。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-129">Setting these attributes to zero means that the <xref:System.Runtime.Caching.MemoryCache> autosizing heuristics are used by default.</span></span> <span data-ttu-id="b3c5d-130">キャッシュの実装では、現在のメモリ負荷と絶対およびパーセントのメモリ制限を 2 分ごとに比較する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b3c5d-130">The cache implementation should compare the current memory load against the absolute and percentage-based memory limits every two minutes.</span></span>  
  
```xml  
<configuration>  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="Default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryLimitPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3c5d-131">関連項目</span><span class="sxs-lookup"><span data-stu-id="b3c5d-131">See also</span></span>

- [<span data-ttu-id="b3c5d-132">\<memoryCache> 要素 (キャッシュ設定)</span><span class="sxs-lookup"><span data-stu-id="b3c5d-132">\<memoryCache> Element (Cache Settings)</span></span>](memorycache-element-cache-settings.md)
