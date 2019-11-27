---
title: <probing> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
ms.openlocfilehash: e9e48ea97e1b70fef7fcc78a113e18c5fec23b7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115860"
---
# <a name="probing-element"></a><span data-ttu-id="e1226-102">\<probing> 要素</span><span class="sxs-lookup"><span data-stu-id="e1226-102">\<probing> Element</span></span>
<span data-ttu-id="e1226-103">アセンブリの読み込み時に共通言語ランタイムが検索するアプリケーションの基本サブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e1226-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
<span data-ttu-id="e1226-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e1226-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e1226-105">&nbsp;&nbsp;[ **\<runtime>** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="e1226-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="e1226-106">&nbsp; &nbsp; &nbsp; &nbsp;[ **\<assemblyBinding**](assemblybinding-element-for-runtime.md) > </span><span class="sxs-lookup"><span data-stu-id="e1226-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)</span></span>\
<span data-ttu-id="e1226-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**probing>**</span><span class="sxs-lookup"><span data-stu-id="e1226-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1226-108">構文</span><span class="sxs-lookup"><span data-stu-id="e1226-108">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1226-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="e1226-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e1226-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="e1226-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1226-111">属性</span><span class="sxs-lookup"><span data-stu-id="e1226-111">Attributes</span></span>  
  
|<span data-ttu-id="e1226-112">属性</span><span class="sxs-lookup"><span data-stu-id="e1226-112">Attribute</span></span>|<span data-ttu-id="e1226-113">説明</span><span class="sxs-lookup"><span data-stu-id="e1226-113">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="e1226-114">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="e1226-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="e1226-115">アセンブリを含む可能性のあるアプリケーションのベースディレクトリのサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="e1226-115">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="e1226-116">各サブディレクトリをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="e1226-116">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1226-117">子要素</span><span class="sxs-lookup"><span data-stu-id="e1226-117">Child Elements</span></span>  

<span data-ttu-id="e1226-118">なし。</span><span class="sxs-lookup"><span data-stu-id="e1226-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1226-119">親要素</span><span class="sxs-lookup"><span data-stu-id="e1226-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e1226-120">要素</span><span class="sxs-lookup"><span data-stu-id="e1226-120">Element</span></span>|<span data-ttu-id="e1226-121">説明</span><span class="sxs-lookup"><span data-stu-id="e1226-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="e1226-122">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="e1226-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="e1226-123">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="e1226-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e1226-124">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="e1226-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e1226-125">例</span><span class="sxs-lookup"><span data-stu-id="e1226-125">Example</span></span>  
 <span data-ttu-id="e1226-126">次の例では、ランタイムがアセンブリを検索するアプリケーションベースのサブディレクトリを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e1226-126">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1226-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="e1226-127">See also</span></span>

- [<span data-ttu-id="e1226-128">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="e1226-128">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="e1226-129">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="e1226-129">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="e1226-130">アセンブリの場所を指定します</span><span class="sxs-lookup"><span data-stu-id="e1226-130">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="e1226-131">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="e1226-131">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
