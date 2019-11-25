---
title: authenticationModules の <clear> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/authenticationModules/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- clear element, authenticationModules
- <authenticationModules>, clear element
- <clear> element, authenticationModules
- authenticationModules, clear element
ms.assetid: dc522c45-4a80-4831-8955-f7b68a47edfd
ms.openlocfilehash: e3abd1b4c76ebda885703ccf961d58657b582f19
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087509"
---
# <a name="clear-element-for-authenticationmodules-network-settings"></a><span data-ttu-id="57d8b-102">authenticationModules の > 要素をクリア \<(ネットワーク設定)</span><span class="sxs-lookup"><span data-stu-id="57d8b-102">\<clear> Element for authenticationModules (Network Settings)</span></span>
<span data-ttu-id="57d8b-103">アプリケーションからすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="57d8b-103">Clears all authentication modules from the application.</span></span>  

<span data-ttu-id="57d8b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="57d8b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="57d8b-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="57d8b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="57d8b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<authenticationModules >** ](authenticationmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="57d8b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<authenticationModules>**](authenticationmodules-element-network-settings.md)</span></span>\
<span data-ttu-id="57d8b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**クリア >**</span><span class="sxs-lookup"><span data-stu-id="57d8b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="57d8b-108">構文</span><span class="sxs-lookup"><span data-stu-id="57d8b-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57d8b-109">属性および要素</span><span class="sxs-lookup"><span data-stu-id="57d8b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="57d8b-110">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="57d8b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57d8b-111">属性</span><span class="sxs-lookup"><span data-stu-id="57d8b-111">Attributes</span></span>  
 <span data-ttu-id="57d8b-112">なし。</span><span class="sxs-lookup"><span data-stu-id="57d8b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="57d8b-113">子要素</span><span class="sxs-lookup"><span data-stu-id="57d8b-113">Child Elements</span></span>  
 <span data-ttu-id="57d8b-114">なし。</span><span class="sxs-lookup"><span data-stu-id="57d8b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57d8b-115">親要素</span><span class="sxs-lookup"><span data-stu-id="57d8b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="57d8b-116">**要素**</span><span class="sxs-lookup"><span data-stu-id="57d8b-116">**Element**</span></span>|<span data-ttu-id="57d8b-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="57d8b-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="57d8b-118">authenticationModules</span><span class="sxs-lookup"><span data-stu-id="57d8b-118">authenticationModules</span></span>](authenticationmodules-element-network-settings.md)|<span data-ttu-id="57d8b-119">ネットワーク要求を認証するために使用するモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="57d8b-119">Specifies modules used to authenticate network requests.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57d8b-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="57d8b-120">Remarks</span></span>  
 <span data-ttu-id="57d8b-121">`clear` 要素は、構成ファイルまたは構成階層の上位レベルで定義されたすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="57d8b-121">The `clear` element removes all authentication modules that were defined earlier in the configuration file or at a higher level in the configuration hierarchy.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="57d8b-122">構成ファイル</span><span class="sxs-lookup"><span data-stu-id="57d8b-122">Configuration Files</span></span>  
 <span data-ttu-id="57d8b-123">この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。</span><span class="sxs-lookup"><span data-stu-id="57d8b-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57d8b-124">例</span><span class="sxs-lookup"><span data-stu-id="57d8b-124">Example</span></span>  
 <span data-ttu-id="57d8b-125">次の例では、構成されているすべての認証モジュールを削除します。</span><span class="sxs-lookup"><span data-stu-id="57d8b-125">The following example removes all configured authentication modules.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <authenticationModules>  
      <clear/>  
    </authenticationModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="57d8b-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="57d8b-126">See also</span></span>

- <xref:System.Net.IAuthenticationModule>
- <xref:System.Net.AuthenticationManager>
- [<span data-ttu-id="57d8b-127">ネットワーク設定スキーマ</span><span class="sxs-lookup"><span data-stu-id="57d8b-127">Network Settings Schema</span></span>](index.md)
