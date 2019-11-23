---
title: <system.web> 要素 (Web 設定)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: 5c5c857d4494b6d78b819e56bae4213abc5e2035
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699091"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="e93b3-102">\<system.web > 要素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="e93b3-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="e93b3-103">ASP.NET ホスティングレイヤーがプロセス全体の動作をどのように管理するかについて説明します。</span><span class="sxs-lookup"><span data-stu-id="e93b3-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
[<span data-ttu-id="e93b3-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="e93b3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e93b3-105">&nbsp;&nbsp; **\<system.web >**</span><span class="sxs-lookup"><span data-stu-id="e93b3-105">&nbsp;&nbsp;**\<system.web>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e93b3-106">構文</span><span class="sxs-lookup"><span data-stu-id="e93b3-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e93b3-107">属性と要素</span><span class="sxs-lookup"><span data-stu-id="e93b3-107">Attributes and Elements</span></span>  

<span data-ttu-id="e93b3-108">次のセクションでは、属性、子要素、親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e93b3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e93b3-109">属性</span><span class="sxs-lookup"><span data-stu-id="e93b3-109">Attributes</span></span>  

<span data-ttu-id="e93b3-110">[なし]。</span><span class="sxs-lookup"><span data-stu-id="e93b3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e93b3-111">子要素</span><span class="sxs-lookup"><span data-stu-id="e93b3-111">Child Elements</span></span>  
  
|<span data-ttu-id="e93b3-112">要素</span><span class="sxs-lookup"><span data-stu-id="e93b3-112">Element</span></span>|<span data-ttu-id="e93b3-113">説明</span><span class="sxs-lookup"><span data-stu-id="e93b3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e93b3-114">\<applicationPool></span><span class="sxs-lookup"><span data-stu-id="e93b3-114">\<applicationPool></span></span>](applicationpool-element-web-settings.md)|<span data-ttu-id="e93b3-115">Aspnet ファイル内の IIS アプリケーションプールの構成設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="e93b3-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e93b3-116">親要素</span><span class="sxs-lookup"><span data-stu-id="e93b3-116">Parent Elements</span></span>  
  
|<span data-ttu-id="e93b3-117">要素</span><span class="sxs-lookup"><span data-stu-id="e93b3-117">Element</span></span>|<span data-ttu-id="e93b3-118">説明</span><span class="sxs-lookup"><span data-stu-id="e93b3-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e93b3-119">\<configuration></span><span class="sxs-lookup"><span data-stu-id="e93b3-119">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="e93b3-120">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="e93b3-120">Specifies the root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e93b3-121">コメント</span><span class="sxs-lookup"><span data-stu-id="e93b3-121">Remarks</span></span>  

<span data-ttu-id="e93b3-122">`system.web` 要素とその子 `applicationPool` 要素が .NET Framework 3.5 SP1 の .NET Framework に追加されました。</span><span class="sxs-lookup"><span data-stu-id="e93b3-122">The `system.web` element and its child `applicationPool` element were added to the .NET Framework as of .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="e93b3-123">IIS 7.0 以降のバージョンを統合モードで実行すると、この要素の組み合わせによって、ASP.NET がどのようにスレッドを管理し、ASP.NET が IIS アプリケーションプールでホストされている場合の要求をキューに配置するかを構成できます。</span><span class="sxs-lookup"><span data-stu-id="e93b3-123">When you run IIS 7.0 or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="e93b3-124">IIS 7.0 以降のバージョンをクラシックモードまたは ISAPI モードで実行した場合、これらの設定は無視されます。</span><span class="sxs-lookup"><span data-stu-id="e93b3-124">If you run IIS 7.0 or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e93b3-125">例</span><span class="sxs-lookup"><span data-stu-id="e93b3-125">Example</span></span>  

<span data-ttu-id="e93b3-126">次の例は、ASP.NET が IIS アプリケーションプールでホストされている場合に、ASP.NET ファイルでプロセス全体の動作を構成する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e93b3-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="e93b3-127">この例では、IIS が統合モードで実行されており、アプリケーションが .NET Framework 3.5 SP1 以降のバージョンを使用していることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="e93b3-127">The example assumes that IIS is running in Integrated mode and that the application is using the .NET Framework 3.5 SP1 or a later version.</span></span> <span data-ttu-id="e93b3-128">この動作は、.NET Framework 3.5 SP1 より前のバージョンの .NET Framework では発生しません。</span><span class="sxs-lookup"><span data-stu-id="e93b3-128">This behavior does not occur in versions of the .NET Framework earlier than the .NET Framework 3.5 SP1.</span></span> <span data-ttu-id="e93b3-129">この例の値は既定値です。</span><span class="sxs-lookup"><span data-stu-id="e93b3-129">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="e93b3-130">要素情報</span><span class="sxs-lookup"><span data-stu-id="e93b3-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e93b3-131">Namespace</span><span class="sxs-lookup"><span data-stu-id="e93b3-131">Namespace</span></span>||  
|<span data-ttu-id="e93b3-132">スキーマ名</span><span class="sxs-lookup"><span data-stu-id="e93b3-132">Schema Name</span></span>||  
|<span data-ttu-id="e93b3-133">検証ファイル</span><span class="sxs-lookup"><span data-stu-id="e93b3-133">Validation File</span></span>||  
|<span data-ttu-id="e93b3-134">空にすることができます</span><span class="sxs-lookup"><span data-stu-id="e93b3-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="e93b3-135">参照</span><span class="sxs-lookup"><span data-stu-id="e93b3-135">See also</span></span>

- [<span data-ttu-id="e93b3-136">\<applicationPool> 要素 (Web 設定)</span><span class="sxs-lookup"><span data-stu-id="e93b3-136">\<applicationPool> Element (Web Settings)</span></span>](applicationpool-element-web-settings.md)
