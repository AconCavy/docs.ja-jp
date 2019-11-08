---
title: <security> の <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
ms.openlocfilehash: c8e4f2d000a155eecd2a6c7faaaf4af525b24ca3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738709"
---
# <a name="security-of-basichttpbinding"></a><span data-ttu-id="6c237-102">\<basicHttpBinding > の \<セキュリティ ></span><span class="sxs-lookup"><span data-stu-id="6c237-102">\<security> of \<basicHttpBinding></span></span>
<span data-ttu-id="6c237-103">[\<basicHttpBinding >](basichttpbinding.md)のセキュリティ機能を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c237-103">Defines the security capabilities of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="6c237-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6c237-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6c237-105">&nbsp; &nbsp;[ **\<system >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="6c237-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6c237-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**バインド**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="6c237-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6c237-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="6c237-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="6c237-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**バインド >** </span><span class="sxs-lookup"><span data-stu-id="6c237-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="6c237-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**セキュリティ >**</span><span class="sxs-lookup"><span data-stu-id="6c237-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c237-110">構文</span><span class="sxs-lookup"><span data-stu-id="6c237-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="string" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c237-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="6c237-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6c237-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="6c237-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c237-113">属性</span><span class="sxs-lookup"><span data-stu-id="6c237-113">Attributes</span></span>  
  
|<span data-ttu-id="6c237-114">属性</span><span class="sxs-lookup"><span data-stu-id="6c237-114">Attribute</span></span>|<span data-ttu-id="6c237-115">説明</span><span class="sxs-lookup"><span data-stu-id="6c237-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6c237-116">モード</span><span class="sxs-lookup"><span data-stu-id="6c237-116">mode</span></span>|<span data-ttu-id="6c237-117">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="6c237-117">Optional.</span></span> <span data-ttu-id="6c237-118">使用されるセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="6c237-118">Specifies the type of security that is used.</span></span> <span data-ttu-id="6c237-119">既定値は、 `None`です。</span><span class="sxs-lookup"><span data-stu-id="6c237-119">The default is `None`.</span></span> <span data-ttu-id="6c237-120">この属性は <xref:System.ServiceModel.BasicHttpSecurityMode> 型です。</span><span class="sxs-lookup"><span data-stu-id="6c237-120">This attribute is of type <xref:System.ServiceModel.BasicHttpSecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="6c237-121">mode 属性</span><span class="sxs-lookup"><span data-stu-id="6c237-121">mode Attribute</span></span>  
  
|<span data-ttu-id="6c237-122">[値]</span><span class="sxs-lookup"><span data-stu-id="6c237-122">Value</span></span>|<span data-ttu-id="6c237-123">説明</span><span class="sxs-lookup"><span data-stu-id="6c237-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6c237-124">None</span><span class="sxs-lookup"><span data-stu-id="6c237-124">None</span></span>|<span data-ttu-id="6c237-125">-メッセージは、転送中にセキュリティ保護されません。</span><span class="sxs-lookup"><span data-stu-id="6c237-125">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="6c237-126">Transport</span><span class="sxs-lookup"><span data-stu-id="6c237-126">Transport</span></span>|<span data-ttu-id="6c237-127">セキュリティは、HTTPS トランスポートを使用して提供されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-127">Security is provided using HTTPS transport.</span></span> <span data-ttu-id="6c237-128">SOAP メッセージは、HTTPS を使用したセキュリティで保護されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-128">The SOAP messages are secured using HTTPS.</span></span> <span data-ttu-id="6c237-129">サービスは、サービスの X.509 証明書を使用してクライアントに認証されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-129">The service is authenticated to the client using the service's X.509 certificate.</span></span> <span data-ttu-id="6c237-130">クライアントは、提供される ClientCredentialType を使用して認証されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-130">The client is authenticated using the ClientCredentialType supplied.</span></span> <span data-ttu-id="6c237-131">[\<トランスポート >](transport-of-basichttpbinding.md)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6c237-131">See the [\<transport>](transport-of-basichttpbinding.md).</span></span>|  
|<span data-ttu-id="6c237-132">[メッセージ]</span><span class="sxs-lookup"><span data-stu-id="6c237-132">Message</span></span>|<span data-ttu-id="6c237-133">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="6c237-134">既定では、本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-134">By default, the body is encrypted and signed.</span></span> <span data-ttu-id="6c237-135">このバインディングの場合、サーバー証明書をクライアントの帯域外で提供するように要求されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-135">For this binding, the system requires that the server certificate be provided to the client out of band.</span></span> <span data-ttu-id="6c237-136">このバインディングの唯一の有効な `ClientCredentialType` は、`Certificate` です。</span><span class="sxs-lookup"><span data-stu-id="6c237-136">The only valid `ClientCredentialType` for this binding is `Certificate`.</span></span>|  
|<span data-ttu-id="6c237-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="6c237-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="6c237-138">整合性、機密性、およびサーバー認証は、トランスポート セキュリティによって提供されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-138">Integrity, confidentiality and server authentication are provided by transport security.</span></span> <span data-ttu-id="6c237-139">クライアント認証は、SOAP メッセージ セキュリティで提供されます。</span><span class="sxs-lookup"><span data-stu-id="6c237-139">Client authentication is provided by means of SOAP message security.</span></span> <span data-ttu-id="6c237-140">このモードは、ユーザーがユーザー名およびパスワードを使用して認証し、メッセージ転送をセキュリティで保護するために既存の HTTP が配置されている場合に関連します。</span><span class="sxs-lookup"><span data-stu-id="6c237-140">This mode is relevant when the user is authenticating using username/password and there is an existing HTTP deployment for securing message transfer.</span></span>|  
|<span data-ttu-id="6c237-141">TransportCredentialOnly</span><span class="sxs-lookup"><span data-stu-id="6c237-141">TransportCredentialOnly</span></span>|<span data-ttu-id="6c237-142">このモードは、メッセージの整合性と機密性を提供しません。</span><span class="sxs-lookup"><span data-stu-id="6c237-142">This mode does not provide message integrity and confidentiality.</span></span> <span data-ttu-id="6c237-143">http ベースのクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="6c237-143">It provides http-based client authentication.</span></span> <span data-ttu-id="6c237-144">このモードを使用するときは、十分に注意する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c237-144">This mode should be used with caution.</span></span> <span data-ttu-id="6c237-145">トランスポートセキュリティが他の方法 (IPSec など) によって提供され、WCF インフラストラクチャによってクライアント認証のみが提供される環境で使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6c237-145">It should be used in environments where the transport security is being provided by other means (such as IPSec) and only client authentication is provided by the WCF infrastructure.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c237-146">子要素</span><span class="sxs-lookup"><span data-stu-id="6c237-146">Child Elements</span></span>  
  
|<span data-ttu-id="6c237-147">要素</span><span class="sxs-lookup"><span data-stu-id="6c237-147">Element</span></span>|<span data-ttu-id="6c237-148">説明</span><span class="sxs-lookup"><span data-stu-id="6c237-148">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6c237-149">\<transport ></span><span class="sxs-lookup"><span data-stu-id="6c237-149">\<transport></span></span>](transport-of-basichttpbinding.md)|<span data-ttu-id="6c237-150">基本 HTTP サービスのトランスポート セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c237-150">Defines the transport security settings for a basic HTTP service.</span></span> <span data-ttu-id="6c237-151">この要素は、<xref:System.ServiceModel.HttpTransportSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="6c237-151">This element corresponds to <xref:System.ServiceModel.HttpTransportSecurity>.</span></span>|  
|[<span data-ttu-id="6c237-152">\< メッセージ ></span><span class="sxs-lookup"><span data-stu-id="6c237-152">\<message></span></span>](message-of-basichttpbinding.md)|<span data-ttu-id="6c237-153">基本 HTTP サービスのメッセージ セキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="6c237-153">Defines the message security settings for a basic HTTP service.</span></span> <span data-ttu-id="6c237-154">この要素は、<xref:System.ServiceModel.BasicHttpMessageSecurity> に対応しています。</span><span class="sxs-lookup"><span data-stu-id="6c237-154">This element corresponds to <xref:System.ServiceModel.BasicHttpMessageSecurity>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c237-155">親要素</span><span class="sxs-lookup"><span data-stu-id="6c237-155">Parent Elements</span></span>  
  
|<span data-ttu-id="6c237-156">要素</span><span class="sxs-lookup"><span data-stu-id="6c237-156">Element</span></span>|<span data-ttu-id="6c237-157">説明</span><span class="sxs-lookup"><span data-stu-id="6c237-157">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c237-158">バインド</span><span class="sxs-lookup"><span data-stu-id="6c237-158">binding</span></span>|<span data-ttu-id="6c237-159">[\<basicHttpBinding >](basichttpbinding.md)のバインド要素。</span><span class="sxs-lookup"><span data-stu-id="6c237-159">The binding element of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c237-160">Remarks</span><span class="sxs-lookup"><span data-stu-id="6c237-160">Remarks</span></span>  
 <span data-ttu-id="6c237-161">既定では、SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。</span><span class="sxs-lookup"><span data-stu-id="6c237-161">By default, the SOAP message is not secured and the client is not authenticated.</span></span> <span data-ttu-id="6c237-162">この要素を使用すると、`basicHttpBinding` 要素に追加のセキュリティ設定を構成できます。</span><span class="sxs-lookup"><span data-stu-id="6c237-162">This element enables you to configure additional security settings for the `basicHttpBinding` element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c237-163">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c237-163">See also</span></span>

- <xref:System.ServiceModel.BasicHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [<span data-ttu-id="6c237-164">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="6c237-164">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="6c237-165">資格情報の種類の選択</span><span class="sxs-lookup"><span data-stu-id="6c237-165">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="6c237-166">バインディング</span><span class="sxs-lookup"><span data-stu-id="6c237-166">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6c237-167">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="6c237-167">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6c237-168">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="6c237-168">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6c237-169">\<binding ></span><span class="sxs-lookup"><span data-stu-id="6c237-169">\<binding></span></span>](bindings.md)
