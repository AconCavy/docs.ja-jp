---
title: <assert> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
ms.openlocfilehash: f3c1a1670139a8262dea449bfff99c7c1c19f088
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088949"
---
# <a name="assert-element"></a><span data-ttu-id="f606e-102">\<assert > 要素</span><span class="sxs-lookup"><span data-stu-id="f606e-102">\<assert> Element</span></span>
<span data-ttu-id="f606e-103"><xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> メソッドの呼び出し時にメッセージ ボックスを表示するかどうかを指定し、メッセージの書き込み先のファイルの名前も指定します。</span><span class="sxs-lookup"><span data-stu-id="f606e-103">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>  

<span data-ttu-id="f606e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f606e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f606e-105">&nbsp;&nbsp;[ **\<system.diagnostics>** ](system-diagnostics-element.md)</span><span class="sxs-lookup"><span data-stu-id="f606e-105">&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)</span></span>\
<span data-ttu-id="f606e-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<assert>**</span><span class="sxs-lookup"><span data-stu-id="f606e-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<assert>**</span></span>

## <a name="syntax"></a><span data-ttu-id="f606e-107">構文</span><span class="sxs-lookup"><span data-stu-id="f606e-107">Syntax</span></span>  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f606e-108">属性および要素</span><span class="sxs-lookup"><span data-stu-id="f606e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f606e-109">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="f606e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f606e-110">属性</span><span class="sxs-lookup"><span data-stu-id="f606e-110">Attributes</span></span>  
  
|<span data-ttu-id="f606e-111">属性</span><span class="sxs-lookup"><span data-stu-id="f606e-111">Attribute</span></span>|<span data-ttu-id="f606e-112">説明</span><span class="sxs-lookup"><span data-stu-id="f606e-112">Description</span></span>|  
|---------------|-----------------|  
|`assertuienabled`|<span data-ttu-id="f606e-113">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="f606e-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f606e-114">**デバッグの Assert**メソッドが**false**と評価されたときにメッセージボックスを表示するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f606e-114">Specifies whether to display a message box when the **Debug.Assert** method evaluates to **false**.</span></span>|  
|`logfilename`|<span data-ttu-id="f606e-115">省略可能な属性です。</span><span class="sxs-lookup"><span data-stu-id="f606e-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f606e-116">**デバッグ**が**false**と評価された場合にメッセージを書き込むファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f606e-116">Specifies the name of the file to write the message to if **Debug.Assert** evaluates to **false**.</span></span>|  
  
## <a name="assertuienabled-attribute"></a><span data-ttu-id="f606e-117">assertuienabled 属性</span><span class="sxs-lookup"><span data-stu-id="f606e-117">assertuienabled Attribute</span></span>  
  
|<span data-ttu-id="f606e-118">[値]</span><span class="sxs-lookup"><span data-stu-id="f606e-118">Value</span></span>|<span data-ttu-id="f606e-119">説明</span><span class="sxs-lookup"><span data-stu-id="f606e-119">Description</span></span>|  
|-----------|-----------------|  
|`true`|<span data-ttu-id="f606e-120">メッセージボックスを表示します。</span><span class="sxs-lookup"><span data-stu-id="f606e-120">Displays the message box.</span></span> <span data-ttu-id="f606e-121">既定値です。</span><span class="sxs-lookup"><span data-stu-id="f606e-121">This is the default.</span></span>|  
|`false`|<span data-ttu-id="f606e-122">では、メッセージボックスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="f606e-122">Does not display the message box.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f606e-123">子要素</span><span class="sxs-lookup"><span data-stu-id="f606e-123">Child Elements</span></span>  
 <span data-ttu-id="f606e-124">なし。</span><span class="sxs-lookup"><span data-stu-id="f606e-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f606e-125">親要素</span><span class="sxs-lookup"><span data-stu-id="f606e-125">Parent Elements</span></span>  
  
|<span data-ttu-id="f606e-126">要素</span><span class="sxs-lookup"><span data-stu-id="f606e-126">Element</span></span>|<span data-ttu-id="f606e-127">説明</span><span class="sxs-lookup"><span data-stu-id="f606e-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f606e-128">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="f606e-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="f606e-129">メッセージを収集、格納、およびルーティングするトレース リスナーとトレース スイッチを設定するレベルを指定します。</span><span class="sxs-lookup"><span data-stu-id="f606e-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f606e-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="f606e-130">Remarks</span></span>  
 <span data-ttu-id="f606e-131">**\<assert >** 要素の両方の属性は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="f606e-131">Both attributes in the **\<assert>** element are optional.</span></span> <span data-ttu-id="f606e-132">メッセージを書き込むファイルを指定せずにメッセージボックスを無効にすることも、メッセージを有効にしたままメッセージを書き込むファイルを指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f606e-132">You can disable message boxes without specifying a file to write the messages to, or you can specify a file to write messages to while leaving message boxes enabled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f606e-133">例</span><span class="sxs-lookup"><span data-stu-id="f606e-133">Example</span></span>  
 <span data-ttu-id="f606e-134">次の例は、 **Assert**を呼び出し、メッセージを `c:\log.txt`に書き込むときに、メッセージボックスの表示を無効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="f606e-134">The following example shows how to disable displaying message boxes when you call **Debug.Assert** and write the messages to `c:\log.txt`.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f606e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="f606e-135">See also</span></span>

- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="f606e-136">トレースおよびデバッグ設定のスキーマ</span><span class="sxs-lookup"><span data-stu-id="f606e-136">Trace and Debug Settings Schema</span></span>](index.md)
