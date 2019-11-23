---
title: <trace> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 02fd794eb7b7b7f46f7f7bc4e43036cb4a4758ed
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699184"
---
# <a name="trace-element"></a><span data-ttu-id="a6a3f-102">トレース > 要素の \<</span><span class="sxs-lookup"><span data-stu-id="a6a3f-102">\<trace> Element</span></span>
<span data-ttu-id="a6a3f-103">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-103">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[<span data-ttu-id="a6a3f-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a6a3f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a6a3f-105">&nbsp;&nbsp;[ **\<の >** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6a3f-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>  
<span data-ttu-id="a6a3f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<トレース >**</span><span class="sxs-lookup"><span data-stu-id="a6a3f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a3f-107">構文</span><span class="sxs-lookup"><span data-stu-id="a6a3f-107">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"   
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6a3f-108">属性と要素</span><span class="sxs-lookup"><span data-stu-id="a6a3f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="a6a3f-109">次のセクションでは、属性、子要素、親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6a3f-110">属性</span><span class="sxs-lookup"><span data-stu-id="a6a3f-110">Attributes</span></span>  
  
|<span data-ttu-id="a6a3f-111">属性</span><span class="sxs-lookup"><span data-stu-id="a6a3f-111">Attribute</span></span>|<span data-ttu-id="a6a3f-112">説明</span><span class="sxs-lookup"><span data-stu-id="a6a3f-112">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="a6a3f-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a6a3f-114">書き込み操作が行われるたびに、トレースリスナーが出力バッファーを自動的にフラッシュするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-114">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="a6a3f-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a6a3f-116">インデントするスペースの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-116">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="a6a3f-117">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a6a3f-118">グローバルロックを使用する必要があるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-118">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="a6a3f-119">autoflush 属性</span><span class="sxs-lookup"><span data-stu-id="a6a3f-119">autoflush Attribute</span></span>  
  
|<span data-ttu-id="a6a3f-120">値</span><span class="sxs-lookup"><span data-stu-id="a6a3f-120">Value</span></span>|<span data-ttu-id="a6a3f-121">説明</span><span class="sxs-lookup"><span data-stu-id="a6a3f-121">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a6a3f-122">では、出力バッファーは自動的にはフラッシュされません。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-122">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="a6a3f-123">既定値です。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-123">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a6a3f-124">出力バッファーを自動的にフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-124">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="a6a3f-125">useGlobalLock 属性</span><span class="sxs-lookup"><span data-stu-id="a6a3f-125">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="a6a3f-126">値</span><span class="sxs-lookup"><span data-stu-id="a6a3f-126">Value</span></span>|<span data-ttu-id="a6a3f-127">説明</span><span class="sxs-lookup"><span data-stu-id="a6a3f-127">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a6a3f-128">リスナーがスレッドセーフである場合、はグローバルロックを使用しません。それ以外の場合、はグローバルロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-128">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="a6a3f-129">は、リスナーがスレッドセーフかどうかに関係なく、グローバルロックを使用します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-129">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="a6a3f-130">既定値です。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-130">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6a3f-131">子要素</span><span class="sxs-lookup"><span data-stu-id="a6a3f-131">Child Elements</span></span>  
  
|<span data-ttu-id="a6a3f-132">要素</span><span class="sxs-lookup"><span data-stu-id="a6a3f-132">Element</span></span>|<span data-ttu-id="a6a3f-133">説明</span><span class="sxs-lookup"><span data-stu-id="a6a3f-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6a3f-134">\<listeners></span><span class="sxs-lookup"><span data-stu-id="a6a3f-134">\<listeners></span></span>](listeners-element-for-trace.md)|<span data-ttu-id="a6a3f-135">メッセージを収集、格納、およびルーティングするリスナーを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-135">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6a3f-136">親要素</span><span class="sxs-lookup"><span data-stu-id="a6a3f-136">Parent Elements</span></span>  
  
|<span data-ttu-id="a6a3f-137">要素</span><span class="sxs-lookup"><span data-stu-id="a6a3f-137">Element</span></span>|<span data-ttu-id="a6a3f-138">説明</span><span class="sxs-lookup"><span data-stu-id="a6a3f-138">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a6a3f-139">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-139">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a6a3f-140">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-140">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a6a3f-141">例</span><span class="sxs-lookup"><span data-stu-id="a6a3f-141">Example</span></span>  
 <span data-ttu-id="a6a3f-142">次の例は、`<trace>` 要素を使用して、リスナー `MyListener` を `Listeners` コレクションに追加する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-142">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="a6a3f-143">`MyListener` によって `MyListener.log` という名前のファイルが作成され、出力がファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-143">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a6a3f-144">`useGlobalLock` 属性は `false`に設定されています。これにより、トレースリスナーがスレッドセーフである場合は、グローバルロックが使用されません。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-144">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="a6a3f-145">`autoflush` 属性は `true`に設定されます。これにより、<xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> メソッドが呼び出されているかどうかに関係なく、トレースリスナーがファイルに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-145">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a6a3f-146">`indentsize` 属性は 0 (ゼロ) に設定されます。これにより、<xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> メソッドが呼び出されたときにリスナーが0個のスペースにインデントを設定します。</span><span class="sxs-lookup"><span data-stu-id="a6a3f-146">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6a3f-147">参照</span><span class="sxs-lookup"><span data-stu-id="a6a3f-147">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="a6a3f-148">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="a6a3f-148">Trace and Debug Settings Schema</span></span>](index.md)
