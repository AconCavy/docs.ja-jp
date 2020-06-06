---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152505"
---
# \<system.identityModel.services>
<span data-ttu-id="820ab-102">WS-FEDERATION プロトコルを使用した認証の構成セクション。</span><span class="sxs-lookup"><span data-stu-id="820ab-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="820ab-103">構文</span><span class="sxs-lookup"><span data-stu-id="820ab-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="820ab-104">属性および要素</span><span class="sxs-lookup"><span data-stu-id="820ab-104">Attributes and Elements</span></span>  
 <span data-ttu-id="820ab-105">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="820ab-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="820ab-106">属性</span><span class="sxs-lookup"><span data-stu-id="820ab-106">Attributes</span></span>  
 <span data-ttu-id="820ab-107">なし</span><span class="sxs-lookup"><span data-stu-id="820ab-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="820ab-108">子要素</span><span class="sxs-lookup"><span data-stu-id="820ab-108">Child Elements</span></span>  
  
|<span data-ttu-id="820ab-109">要素</span><span class="sxs-lookup"><span data-stu-id="820ab-109">Element</span></span>|<span data-ttu-id="820ab-110">説明</span><span class="sxs-lookup"><span data-stu-id="820ab-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="820ab-111"><xref:System.IdentityModel.Services.WSFederationAuthenticationModule>(Wsfam) および <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP モジュールを構成する設定が含まれています。</span><span class="sxs-lookup"><span data-stu-id="820ab-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="820ab-112">親要素</span><span class="sxs-lookup"><span data-stu-id="820ab-112">Parent Elements</span></span>  
 <span data-ttu-id="820ab-113">なし</span><span class="sxs-lookup"><span data-stu-id="820ab-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="820ab-114">解説</span><span class="sxs-lookup"><span data-stu-id="820ab-114">Remarks</span></span>  
 <span data-ttu-id="820ab-115">`<system.identityModel.services>`アプリケーションの構成ファイルにセクションを追加して、SAM と WSFAM の設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="820ab-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="820ab-116">クラスまたはクラスを使用して、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> コード内にクレームベースのアクセス制御を提供する場合、承認の決定に使用される要求承認マネージャー ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) とポリシーは、 `<identityConfiguration>` `<federationConfiguration>` このセクションの要素から暗黙的または明示的に参照される要素によって構成されます。</span><span class="sxs-lookup"><span data-stu-id="820ab-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="820ab-117">詳細については、要素の「**解説**」を参照してください [\<federationConfiguration>](federationconfiguration.md) 。</span><span class="sxs-lookup"><span data-stu-id="820ab-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="820ab-118">`<system.identityModel.services>`セクションは、クラスによって表され <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> ます。</span><span class="sxs-lookup"><span data-stu-id="820ab-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="820ab-119">`<federationConfiguration>`セクションで構成された子要素のコレクションは、クラスによって表され <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> ます。</span><span class="sxs-lookup"><span data-stu-id="820ab-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="820ab-120">例</span><span class="sxs-lookup"><span data-stu-id="820ab-120">Example</span></span>  
 <span data-ttu-id="820ab-121">次の XML は、構成ファイルにセクションを追加する方法を示して `<system.identityModel.services>` います。</span><span class="sxs-lookup"><span data-stu-id="820ab-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="820ab-122">まず、セクションとセクションの両方にセクション宣言を追加する必要があり `<system.identityModel.services>` `<system.identityModel>` ます。</span><span class="sxs-lookup"><span data-stu-id="820ab-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="820ab-123">(セクションを追加する場合は、必要に応じ `<system.identityModel.services>` `<system.identityModel>` て、ランタイムが既定のセクションを作成できるように、セクションの宣言も追加する必要があり `<identityConfiguration>` ます)。セクション宣言を追加した後、要素の下にフェデレーション認証設定を構成でき `<system.identityModel.services>` ます。</span><span class="sxs-lookup"><span data-stu-id="820ab-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"
        issuer="http://localhost:15839/wsFederationSTS/Issue"
        realm="http://localhost:50969/" reply="http://localhost:50969/"
        requireHttps="false"
        signOutReply="http://localhost:50969/SignedOutPage.html"
        signOutQueryString="Param1=value2&Param2=value2"
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
