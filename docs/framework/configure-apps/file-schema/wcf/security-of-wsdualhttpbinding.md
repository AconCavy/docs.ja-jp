---
title: <security> の <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 869c05e7-4ebe-467d-95ab-c8f8de4e6b9e
ms.openlocfilehash: 4969c041678bbf3490975bc0ec53507b6cf762bb
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738608"
---
# <a name="security-of-wsdualhttpbinding"></a><span data-ttu-id="d6a74-102">\<wsDualHttpBinding > のセキュリティ > の \<</span><span class="sxs-lookup"><span data-stu-id="d6a74-102">\<security> of \<wsDualHttpBinding></span></span>
<span data-ttu-id="d6a74-103">[\<wsDualHttpBinding >](wsdualhttpbinding.md)のセキュリティ機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="d6a74-103">Defines the security capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>  
  
<span data-ttu-id="d6a74-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d6a74-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d6a74-105">&nbsp; &nbsp;[ **\<system >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="d6a74-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d6a74-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**バインド**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="d6a74-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="d6a74-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wsDualHttpBinding >** ](wsdualhttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="d6a74-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsDualHttpBinding>**](wsdualhttpbinding.md)</span></span>\
<span data-ttu-id="d6a74-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**バインド >** </span><span class="sxs-lookup"><span data-stu-id="d6a74-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="d6a74-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**セキュリティ >**</span><span class="sxs-lookup"><span data-stu-id="d6a74-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6a74-110">構文</span><span class="sxs-lookup"><span data-stu-id="d6a74-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None">
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           negotiateServiceCredential="Boolean"/>
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6a74-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="d6a74-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6a74-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="d6a74-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6a74-113">属性</span><span class="sxs-lookup"><span data-stu-id="d6a74-113">Attributes</span></span>  
  
|<span data-ttu-id="d6a74-114">属性</span><span class="sxs-lookup"><span data-stu-id="d6a74-114">Attribute</span></span>|<span data-ttu-id="d6a74-115">説明</span><span class="sxs-lookup"><span data-stu-id="d6a74-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d6a74-116">モード</span><span class="sxs-lookup"><span data-stu-id="d6a74-116">mode</span></span>|<span data-ttu-id="d6a74-117">Optional.</span><span class="sxs-lookup"><span data-stu-id="d6a74-117">-   Optional.</span></span> <span data-ttu-id="d6a74-118">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="d6a74-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="d6a74-119">既定値は `Message`です。</span><span class="sxs-lookup"><span data-stu-id="d6a74-119">The default value is `Message`.</span></span> <span data-ttu-id="d6a74-120">この属性は <xref:System.ServiceModel.WSDualHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="d6a74-120">This attribute is of type <xref:System.ServiceModel.WSDualHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="d6a74-121">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="d6a74-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="d6a74-122">[値]</span><span class="sxs-lookup"><span data-stu-id="d6a74-122">Value</span></span>|<span data-ttu-id="d6a74-123">説明</span><span class="sxs-lookup"><span data-stu-id="d6a74-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d6a74-124">None</span><span class="sxs-lookup"><span data-stu-id="d6a74-124">None</span></span>|<span data-ttu-id="d6a74-125">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="d6a74-125">Security is disabled.</span></span>|  
|<span data-ttu-id="d6a74-126">[メッセージ]</span><span class="sxs-lookup"><span data-stu-id="d6a74-126">Message</span></span>|<span data-ttu-id="d6a74-127">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="d6a74-127">Security is provided using SOAP message security.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6a74-128">子要素</span><span class="sxs-lookup"><span data-stu-id="d6a74-128">Child Elements</span></span>  
  
|<span data-ttu-id="d6a74-129">要素</span><span class="sxs-lookup"><span data-stu-id="d6a74-129">Element</span></span>|<span data-ttu-id="d6a74-130">説明</span><span class="sxs-lookup"><span data-stu-id="d6a74-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6a74-131">\< メッセージ ></span><span class="sxs-lookup"><span data-stu-id="d6a74-131">\<message></span></span>](message-of-wsdualhttpbinding.md)|<span data-ttu-id="d6a74-132">メッセージ レベル セキュリティの設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="d6a74-132">Defines the settings for the message-level security.</span></span> <span data-ttu-id="d6a74-133">この要素は <xref:System.ServiceModel.MessageSecurityOverHttp> 型です。</span><span class="sxs-lookup"><span data-stu-id="d6a74-133">This element is of type <xref:System.ServiceModel.MessageSecurityOverHttp>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6a74-134">親要素</span><span class="sxs-lookup"><span data-stu-id="d6a74-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d6a74-135">要素</span><span class="sxs-lookup"><span data-stu-id="d6a74-135">Element</span></span>|<span data-ttu-id="d6a74-136">説明</span><span class="sxs-lookup"><span data-stu-id="d6a74-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6a74-137">\<binding ></span><span class="sxs-lookup"><span data-stu-id="d6a74-137">\<binding></span></span>](bindings.md)|<span data-ttu-id="d6a74-138">[\<wsDualHttpBinding >](wsdualhttpbinding.md)のすべてのバインド機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="d6a74-138">Defines all binding capabilities of the [\<wsDualHttpBinding>](wsdualhttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6a74-139">Remarks</span><span class="sxs-lookup"><span data-stu-id="d6a74-139">Remarks</span></span>  
 <span data-ttu-id="d6a74-140">二重バインディングでは、クライアントの IP アドレスをサービスに公開します。</span><span class="sxs-lookup"><span data-stu-id="d6a74-140">A dual binding exposes the IP address of the client to the service.</span></span> <span data-ttu-id="d6a74-141">クライアントは、セキュリティを使用して信頼するサービスに対して接続のみを可能にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d6a74-141">The client should use security to ensure that it only connects to services it trusts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6a74-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6a74-142">See also</span></span>

- <xref:System.ServiceModel.WSDualHttpSecurity>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="d6a74-143">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="d6a74-143">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d6a74-144">バインディング</span><span class="sxs-lookup"><span data-stu-id="d6a74-144">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d6a74-145">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="d6a74-145">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d6a74-146">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="d6a74-146">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d6a74-147">\<binding ></span><span class="sxs-lookup"><span data-stu-id="d6a74-147">\<binding></span></span>](bindings.md)
