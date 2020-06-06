---
title: <performanceCounters> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <performanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
ms.openlocfilehash: f52fdb2d5b0b7911de63f96663e70735d2f2496c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697152"
---
# <a name="performancecounters-element"></a><span data-ttu-id="7259c-102">\<performanceCounters> 要素</span><span class="sxs-lookup"><span data-stu-id="7259c-102">\<performanceCounters> Element</span></span>

<span data-ttu-id="7259c-103">パフォーマンス カウンターが共有するグローバル メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="7259c-103">Specifies the size of the global memory shared by performance counters.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**  

## <a name="syntax"></a><span data-ttu-id="7259c-104">構文</span><span class="sxs-lookup"><span data-stu-id="7259c-104">Syntax</span></span>

```xml
<performanceCounters filemappingsize="524288" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7259c-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="7259c-105">Attributes and Elements</span></span>

<span data-ttu-id="7259c-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="7259c-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7259c-107">属性</span><span class="sxs-lookup"><span data-stu-id="7259c-107">Attributes</span></span>

|<span data-ttu-id="7259c-108">属性</span><span class="sxs-lookup"><span data-stu-id="7259c-108">Attribute</span></span>|<span data-ttu-id="7259c-109">説明</span><span class="sxs-lookup"><span data-stu-id="7259c-109">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="7259c-110">filemappingsize</span><span class="sxs-lookup"><span data-stu-id="7259c-110">filemappingsize</span></span>|<span data-ttu-id="7259c-111">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="7259c-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="7259c-112">パフォーマンス カウンターが共有するグローバル メモリのサイズをバイト単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="7259c-112">Specifies the size, in bytes, of the global memory shared by performance counters.</span></span> <span data-ttu-id="7259c-113">既定値は 524288 です。</span><span class="sxs-lookup"><span data-stu-id="7259c-113">The default is 524288.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7259c-114">子要素</span><span class="sxs-lookup"><span data-stu-id="7259c-114">Child Elements</span></span>

<span data-ttu-id="7259c-115">なし。</span><span class="sxs-lookup"><span data-stu-id="7259c-115">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7259c-116">親要素</span><span class="sxs-lookup"><span data-stu-id="7259c-116">Parent Elements</span></span>

|<span data-ttu-id="7259c-117">要素</span><span class="sxs-lookup"><span data-stu-id="7259c-117">Element</span></span>|<span data-ttu-id="7259c-118">Description</span><span class="sxs-lookup"><span data-stu-id="7259c-118">Description</span></span>|
|-------------|-----------------|
|`Configuration`|<span data-ttu-id="7259c-119">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="7259c-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`system.diagnostics`|<span data-ttu-id="7259c-120">ASP.NET 構成セクションのルート要素を指定します。</span><span class="sxs-lookup"><span data-stu-id="7259c-120">Specifies the root element for the ASP.NET configuration section.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7259c-121">解説</span><span class="sxs-lookup"><span data-stu-id="7259c-121">Remarks</span></span>

<span data-ttu-id="7259c-122">パフォーマンスカウンターは、メモリマップトファイルまたは共有メモリを使用して、パフォーマンスデータをパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="7259c-122">Performance counters use a memory mapped file, or shared memory, to publish performance data.</span></span>  <span data-ttu-id="7259c-123">共有メモリのサイズによって、一度に使用できるインスタンスの数が決まります。</span><span class="sxs-lookup"><span data-stu-id="7259c-123">The size of the shared memory determines how many instances can be used at once.</span></span>  <span data-ttu-id="7259c-124">共有メモリには、グローバル共有メモリと個別の共有メモリの2種類があります。</span><span class="sxs-lookup"><span data-stu-id="7259c-124">There are two types of shared memory: global shared memory and separate shared memory.</span></span>  <span data-ttu-id="7259c-125">グローバル共有メモリは、.NET Framework バージョン1.0 または1.1 と共にインストールされたすべてのパフォーマンスカウンターカテゴリによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="7259c-125">The global shared memory is used by all performance counter categories installed with the .NET Framework versions 1.0 or 1.1.</span></span>  <span data-ttu-id="7259c-126">.NET Framework バージョン2.0 と共にインストールされるパフォーマンスカウンターカテゴリには、個別の共有メモリが使用されます。各パフォーマンスカウンターカテゴリには独自のメモリがあります。</span><span class="sxs-lookup"><span data-stu-id="7259c-126">Performance counter categories installed with the .NET Framework version 2.0 use separate shared memory, with each performance counter category having its own memory.</span></span>

<span data-ttu-id="7259c-127">グローバル共有メモリのサイズは、構成ファイルでのみ設定できます。</span><span class="sxs-lookup"><span data-stu-id="7259c-127">The size of global shared memory can be set only with a configuration file.</span></span>  <span data-ttu-id="7259c-128">既定のサイズは 524288 byes、最大サイズは33554432バイト、最小サイズは32768バイトです。</span><span class="sxs-lookup"><span data-stu-id="7259c-128">The default size is 524,288 byes, the maximum size is 33,554,432 bytes, and the minimum size is 32,768 bytes.</span></span>  <span data-ttu-id="7259c-129">グローバル共有メモリはすべてのプロセスとカテゴリによって共有されるため、最初の作成者はサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="7259c-129">Since the global shared memory is shared by all processes and categories, the first creator specifies the size.</span></span>  <span data-ttu-id="7259c-130">アプリケーション構成ファイルでサイズを定義する場合、そのサイズは、アプリケーションがパフォーマンスカウンターを実行する最初のアプリケーションである場合にのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="7259c-130">If you define the size in your application configuration file, that size is only used if your application is the first application that causes the performance counters to execute.</span></span>  <span data-ttu-id="7259c-131">そのため、値を指定する正しい場所 `filemappingsize` は machine.config ファイルです。</span><span class="sxs-lookup"><span data-stu-id="7259c-131">Therefore the correct location to specify the `filemappingsize` value is the Machine.config file.</span></span>  <span data-ttu-id="7259c-132">グローバル共有メモリ内のメモリは、個々のパフォーマンスカウンターによって解放されることはないため、異なる名前を持つ多数のパフォーマンスカウンターインスタンスが作成されると、最終的にグローバル共有メモリが使い果たされます。</span><span class="sxs-lookup"><span data-stu-id="7259c-132">Memory in the global shared memory cannot be released by individual performance counters, so eventually global shared memory is exhausted if a large number of performance counter instances with different names are created.</span></span>

<span data-ttu-id="7259c-133">個別の共有メモリのサイズについては、レジストリキー HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services \Performance の DWORD FileMappingSize 値 \\ *\<category name>* が最初に参照され、次に構成ファイル内のグローバル共有メモリに指定された値が続きます。</span><span class="sxs-lookup"><span data-stu-id="7259c-133">For the size of separate shared memory, the DWORD FileMappingSize value in the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<category name>* \Performance is referenced first, followed by the value specified for the global shared memory in the configuration file.</span></span> <span data-ttu-id="7259c-134">[FileMappingSize] の値が存在しない場合は、構成ファイルのグローバル設定の1つ目の共有メモリサイズが4番目 (1/4) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="7259c-134">If the FileMappingSize value does not exist, then the separate shared memory size is set to one fourth (1/4) the global setting in the configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="7259c-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="7259c-135">See also</span></span>

- <xref:System.Diagnostics.PerformanceCounter>
- <xref:System.Diagnostics.PerformanceCounterCategory>
- <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>
- <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
