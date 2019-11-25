---
title: <trace> の <listeners> の <add> の <filter> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: cc970240ac07ad3ea72be50d1e9af452da638fa9
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088894"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="e9cbf-102">\<トレース > の \<リスナー > の > を追加 \<の \<フィルター > 要素</span><span class="sxs-lookup"><span data-stu-id="e9cbf-102">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>
<span data-ttu-id="e9cbf-103">トレースの `Listeners` コレクション内のリスナーにフィルターを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-103">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

<span data-ttu-id="e9cbf-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9cbf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e9cbf-105">&nbsp;&nbsp;[ **\<** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9cbf-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="e9cbf-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**トレース >** ](trace-element.md)</span><span class="sxs-lookup"><span data-stu-id="e9cbf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)</span></span>\
<span data-ttu-id="e9cbf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**リスナー >** ](listeners-element-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="e9cbf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)</span></span>\
<span data-ttu-id="e9cbf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**追加**](add-element-for-listeners-for-trace.md)</span><span class="sxs-lookup"><span data-stu-id="e9cbf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)</span></span>\
<span data-ttu-id="e9cbf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**フィルター >**</span><span class="sxs-lookup"><span data-stu-id="e9cbf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**</span></span>

## <a name="syntax"></a><span data-ttu-id="e9cbf-110">構文</span><span class="sxs-lookup"><span data-stu-id="e9cbf-110">Syntax</span></span>  
  
```xml  
<filter   
  type="traceFilterClassName"   
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e9cbf-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e9cbf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e9cbf-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e9cbf-113">属性</span><span class="sxs-lookup"><span data-stu-id="e9cbf-113">Attributes</span></span>  
  
|<span data-ttu-id="e9cbf-114">属性</span><span class="sxs-lookup"><span data-stu-id="e9cbf-114">Attribute</span></span>|<span data-ttu-id="e9cbf-115">説明</span><span class="sxs-lookup"><span data-stu-id="e9cbf-115">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e9cbf-116">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e9cbf-117">フィルターの種類を指定します。この型は <xref:System.Diagnostics.TraceFilter> クラスから継承する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-117">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="e9cbf-118">型の名前空間で修飾された名前 (型の <xref:System.Type.FullName%2A> プロパティに対応する) を使用することも、<xref:System.Type.AssemblyQualifiedName%2A> プロパティに対応するアセンブリ情報を含む完全修飾型名を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-118">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="e9cbf-119">完全修飾型名の詳細については、「[完全修飾型名の指定](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-119">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="e9cbf-120">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="e9cbf-121">指定されたフィルタークラスのコンストラクターに渡される文字列。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-121">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e9cbf-122">子要素</span><span class="sxs-lookup"><span data-stu-id="e9cbf-122">Child Elements</span></span>  
 <span data-ttu-id="e9cbf-123">なし。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e9cbf-124">親要素</span><span class="sxs-lookup"><span data-stu-id="e9cbf-124">Parent Elements</span></span>  
  
|<span data-ttu-id="e9cbf-125">要素</span><span class="sxs-lookup"><span data-stu-id="e9cbf-125">Element</span></span>|<span data-ttu-id="e9cbf-126">説明</span><span class="sxs-lookup"><span data-stu-id="e9cbf-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e9cbf-127">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e9cbf-128">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-128">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="e9cbf-129">トレース メッセージを収集、格納、およびルーティングするリスナーを保持します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-129">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="e9cbf-130">メッセージを収集、格納、およびルーティングするリスナーを格納します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-130">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="e9cbf-131">リスナーは、適切なターゲットにトレース出力を送信します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-131">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="e9cbf-132">`Listeners` コレクションにリスナーを追加します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-132">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9cbf-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="e9cbf-133">Remarks</span></span>  
 <span data-ttu-id="e9cbf-134">`<filter>` 要素は、 [\<sharedListeners >](sharedlisteners-element.md)で定義されているリスナーの名前だけでなく、リスナーの種類を指定するトレースリスナーの `<add>` 要素に格納されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-134">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="e9cbf-135">リスナーが[\<sharedListeners >](sharedlisteners-element.md)で定義されている場合は、そのリスナーのフィルターをその要素で定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-135">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="e9cbf-136">この要素は、コンピューターの構成ファイル (machine.config) とアプリケーション構成ファイルで使用できます。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-136">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9cbf-137">例</span><span class="sxs-lookup"><span data-stu-id="e9cbf-137">Example</span></span>  
 <span data-ttu-id="e9cbf-138">次の例は、`<filter>` 要素を使用して、トレースの `Listeners` コレクション内のリスナー `console` にフィルターを追加する方法を示しています。これは、フィルターイベントレベルを `Error`として指定します。</span><span class="sxs-lookup"><span data-stu-id="e9cbf-138">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"   
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"   
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e9cbf-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="e9cbf-139">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="e9cbf-140">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="e9cbf-140">Trace and Debug Settings Schema</span></span>](index.md)
