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
ms.openlocfilehash: 1435ee8ea887b5d7d3e785eef0f25ffed14b1b97
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2020
ms.locfileid: "91195273"
---
# <a name="probing-element"></a><span data-ttu-id="ecab4-102">\<probing> 要素</span><span class="sxs-lookup"><span data-stu-id="ecab4-102">\<probing> Element</span></span>

<span data-ttu-id="ecab4-103">アセンブリの読み込み時に共通言語ランタイムが検索するアプリケーションの基本サブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="ecab4-103">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="ecab4-104">構文</span><span class="sxs-lookup"><span data-stu-id="ecab4-104">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ecab4-105">属性および要素</span><span class="sxs-lookup"><span data-stu-id="ecab4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="ecab4-106">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="ecab4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ecab4-107">属性</span><span class="sxs-lookup"><span data-stu-id="ecab4-107">Attributes</span></span>  
  
|<span data-ttu-id="ecab4-108">属性</span><span class="sxs-lookup"><span data-stu-id="ecab4-108">Attribute</span></span>|<span data-ttu-id="ecab4-109">説明</span><span class="sxs-lookup"><span data-stu-id="ecab4-109">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="ecab4-110">必須の属性です。</span><span class="sxs-lookup"><span data-stu-id="ecab4-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="ecab4-111">アセンブリを含む可能性のあるアプリケーションのベースディレクトリのサブディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="ecab4-111">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="ecab4-112">各サブディレクトリをセミコロンで区切ります。</span><span class="sxs-lookup"><span data-stu-id="ecab4-112">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ecab4-113">子要素</span><span class="sxs-lookup"><span data-stu-id="ecab4-113">Child Elements</span></span>  

<span data-ttu-id="ecab4-114">なし。</span><span class="sxs-lookup"><span data-stu-id="ecab4-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ecab4-115">親要素</span><span class="sxs-lookup"><span data-stu-id="ecab4-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ecab4-116">要素</span><span class="sxs-lookup"><span data-stu-id="ecab4-116">Element</span></span>|<span data-ttu-id="ecab4-117">説明</span><span class="sxs-lookup"><span data-stu-id="ecab4-117">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ecab4-118">アセンブリ バージョンのリダイレクトおよびアセンブリの位置に関する情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="ecab4-118">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ecab4-119">共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。</span><span class="sxs-lookup"><span data-stu-id="ecab4-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ecab4-120">アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="ecab4-120">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ecab4-121">例</span><span class="sxs-lookup"><span data-stu-id="ecab4-121">Example</span></span>  

 <span data-ttu-id="ecab4-122">次の例では、ランタイムがアセンブリを検索するアプリケーションベースのサブディレクトリを指定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ecab4-122">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ecab4-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecab4-123">See also</span></span>

- [<span data-ttu-id="ecab4-124">ランタイム設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="ecab4-124">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="ecab4-125">構成ファイル スキーマ</span><span class="sxs-lookup"><span data-stu-id="ecab4-125">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="ecab4-126">アセンブリの場所を指定します</span><span class="sxs-lookup"><span data-stu-id="ecab4-126">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="ecab4-127">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="ecab4-127">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
