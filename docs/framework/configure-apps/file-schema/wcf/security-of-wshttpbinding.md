---
title: <security> の <wsHttpBinding>
ms.date: 03/30/2017
ms.assetid: 8658b162-2ddf-4162-a869-aa517a42288a
ms.openlocfilehash: b66b5228cab9dbc35502a13a2d0fe56ce4c6a18d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738585"
---
# <a name="security-of-wshttpbinding"></a><span data-ttu-id="a6476-102">\<\<wsHttpBinding のセキュリティ > ></span><span class="sxs-lookup"><span data-stu-id="a6476-102">\<security> of \<wsHttpBinding></span></span>
<span data-ttu-id="a6476-103">[\<wsHttpBinding >](wshttpbinding.md)のセキュリティ機能を表します。</span><span class="sxs-lookup"><span data-stu-id="a6476-103">Represents the security capabilities of the [\<wsHttpBinding>](wshttpbinding.md).</span></span>  
  
<span data-ttu-id="a6476-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6476-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a6476-105">&nbsp; &nbsp;[ **\<system >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="a6476-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a6476-106">&nbsp;&nbsp;&nbsp;&nbsp;\<[**バインド**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="a6476-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="a6476-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**wsHttpBinding >** ](wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="a6476-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsHttpBinding>**](wshttpbinding.md)</span></span>\
<span data-ttu-id="a6476-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**バインド >** </span><span class="sxs-lookup"><span data-stu-id="a6476-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="a6476-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**セキュリティ >**</span><span class="sxs-lookup"><span data-stu-id="a6476-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6476-110">構文</span><span class="sxs-lookup"><span data-stu-id="a6476-110">Syntax</span></span>  
  
```xml  
<security mode="Message/None/Transport/TransportWithMessageCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             proxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             realm="String"
             defaultClientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             defaultProxyCredentialType="Basic/Digest/None/Ntlm/Windows"
             defaultRealm="String" />
  <message clientCredentialType="Certificate/IssuedToken/None/UserName/Windows"
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           establishSecurityContext="Boolean"
           negotiateServiceCredential="Boolean" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6476-111">属性および要素</span><span class="sxs-lookup"><span data-stu-id="a6476-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a6476-112">以降のセクションでは、属性、子要素、および親要素について説明します。</span><span class="sxs-lookup"><span data-stu-id="a6476-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6476-113">属性</span><span class="sxs-lookup"><span data-stu-id="a6476-113">Attributes</span></span>  
  
|<span data-ttu-id="a6476-114">属性</span><span class="sxs-lookup"><span data-stu-id="a6476-114">Attribute</span></span>|<span data-ttu-id="a6476-115">説明</span><span class="sxs-lookup"><span data-stu-id="a6476-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a6476-116">モード</span><span class="sxs-lookup"><span data-stu-id="a6476-116">mode</span></span>|<span data-ttu-id="a6476-117">Optional.</span><span class="sxs-lookup"><span data-stu-id="a6476-117">-   Optional.</span></span> <span data-ttu-id="a6476-118">適用するセキュリティの種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="a6476-118">Specifies the type of security that is applied.</span></span> <span data-ttu-id="a6476-119">既定値は、 `Message`です。</span><span class="sxs-lookup"><span data-stu-id="a6476-119">The default is `Message`.</span></span><br /><span data-ttu-id="a6476-120">-この属性の型は <xref:System.ServiceModel.SecurityMode>です。</span><span class="sxs-lookup"><span data-stu-id="a6476-120">-   This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="a6476-121">Mode 属性</span><span class="sxs-lookup"><span data-stu-id="a6476-121">Mode Attribute</span></span>  
  
|<span data-ttu-id="a6476-122">[値]</span><span class="sxs-lookup"><span data-stu-id="a6476-122">Value</span></span>|<span data-ttu-id="a6476-123">説明</span><span class="sxs-lookup"><span data-stu-id="a6476-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a6476-124">None</span><span class="sxs-lookup"><span data-stu-id="a6476-124">None</span></span>|<span data-ttu-id="a6476-125">セキュリティを無効にします。</span><span class="sxs-lookup"><span data-stu-id="a6476-125">Security is disabled.</span></span>|  
|<span data-ttu-id="a6476-126">Transport</span><span class="sxs-lookup"><span data-stu-id="a6476-126">Transport</span></span>|<span data-ttu-id="a6476-127">セキュリティは、HTTPS を使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="a6476-127">Security is provided using HTTPS.</span></span> <span data-ttu-id="a6476-128">サービスは、SSL 証明書を使用して構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a6476-128">The service needs to be configured with SSL certificates.</span></span> <span data-ttu-id="a6476-129">メッセージは、HTTPS を使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。</span><span class="sxs-lookup"><span data-stu-id="a6476-129">The message is entirely secured using HTTPS and is authenticated by the client using the service’s SSL certificate.</span></span> <span data-ttu-id="a6476-130">クライアント認証は、`ClientCredentials` 属性を使用して制御されます。</span><span class="sxs-lookup"><span data-stu-id="a6476-130">The client authentication is controlled through the `ClientCredentials` attribute.</span></span> <span data-ttu-id="a6476-131">[\<トランスポート >](transport-of-wshttpbinding.md)の。</span><span class="sxs-lookup"><span data-stu-id="a6476-131">of the [\<transport>](transport-of-wshttpbinding.md).</span></span>|  
|<span data-ttu-id="a6476-132">[メッセージ]</span><span class="sxs-lookup"><span data-stu-id="a6476-132">Message</span></span>|<span data-ttu-id="a6476-133">セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。</span><span class="sxs-lookup"><span data-stu-id="a6476-133">Security is provided using SOAP message security.</span></span> <span data-ttu-id="a6476-134">既定では、SOAP 本文は暗号化および署名されます。</span><span class="sxs-lookup"><span data-stu-id="a6476-134">By default, the SOAP body is Encrypted and Signed.</span></span> <span data-ttu-id="a6476-135">このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、Security.Message プロパティを使用してメッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="a6476-135">This mode offers a variety of features, such as whether the service credentials are available at the client out of band, the algorithm suite to use, and what level of protection to apply to the message body through the Security.Message property.</span></span> <span data-ttu-id="a6476-136">クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a6476-136">Client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
|<span data-ttu-id="a6476-137">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="a6476-137">TransportWithMessageCredential</span></span>|<span data-ttu-id="a6476-138">このモードでは、HTTPS は、整合性、機密性、およびサーバー認証を提供し、SOAP メッセージ セキュリティはクライアント認証を提供します。</span><span class="sxs-lookup"><span data-stu-id="a6476-138">In this mode, HTTPS provides integrity, confidentiality, and server authentication, and SOAP message security provides client authentication.</span></span> <span data-ttu-id="a6476-139">既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a6476-139">By default, client authentication is performed once per session and the results of authentication are cached for the duration of the session.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6476-140">子要素</span><span class="sxs-lookup"><span data-stu-id="a6476-140">Child Elements</span></span>  
  
|<span data-ttu-id="a6476-141">要素</span><span class="sxs-lookup"><span data-stu-id="a6476-141">Element</span></span>|<span data-ttu-id="a6476-142">説明</span><span class="sxs-lookup"><span data-stu-id="a6476-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6476-143">\<transport ></span><span class="sxs-lookup"><span data-stu-id="a6476-143">\<transport></span></span>](transport-of-wshttpbinding.md)|<span data-ttu-id="a6476-144">トランスポートのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a6476-144">Defines the transport security settings.</span></span> <span data-ttu-id="a6476-145">この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="a6476-145">This element corresponds to the <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> type.</span></span>|  
|[<span data-ttu-id="a6476-146">\< メッセージ ></span><span class="sxs-lookup"><span data-stu-id="a6476-146">\<message></span></span>](message-of-wshttpbinding.md)|<span data-ttu-id="a6476-147">メッセージのセキュリティ設定を定義します。</span><span class="sxs-lookup"><span data-stu-id="a6476-147">Defines the security settings for the message.</span></span> <span data-ttu-id="a6476-148">この要素は、<xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型に対応しています。</span><span class="sxs-lookup"><span data-stu-id="a6476-148">This element corresponds to the <xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> type.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a6476-149">親要素</span><span class="sxs-lookup"><span data-stu-id="a6476-149">Parent Elements</span></span>  
  
|<span data-ttu-id="a6476-150">要素</span><span class="sxs-lookup"><span data-stu-id="a6476-150">Element</span></span>|<span data-ttu-id="a6476-151">説明</span><span class="sxs-lookup"><span data-stu-id="a6476-151">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6476-152">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="a6476-152">\<wsHttpBinding></span></span>](wshttpbinding.md)|<span data-ttu-id="a6476-153">HTTP トランスポート アプリケーションのセキュリティで保護されたバインド。</span><span class="sxs-lookup"><span data-stu-id="a6476-153">A secure binding for HTTP transport applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6476-154">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6476-154">Remarks</span></span>  
 <span data-ttu-id="a6476-155">WSHttpBinding クラスは、WS-\* 仕様を実装するサービスと相互運用するようにデザインされています。</span><span class="sxs-lookup"><span data-stu-id="a6476-155">The WSHttpBinding class is designed for interoperation with services that implement WS-\* specifications.</span></span> <span data-ttu-id="a6476-156">このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。</span><span class="sxs-lookup"><span data-stu-id="a6476-156">The transport security for this binding is Secure Sockets Layer (SSL) over HTTP, or HTTPS.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6476-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="a6476-157">See also</span></span>

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- [<span data-ttu-id="a6476-158">サービスおよびクライアントのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="a6476-158">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="a6476-159">バインディング</span><span class="sxs-lookup"><span data-stu-id="a6476-159">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a6476-160">システムが提供するバインディングの構成</span><span class="sxs-lookup"><span data-stu-id="a6476-160">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="a6476-161">サービスとクライアントを構成するためのバインディングの使用</span><span class="sxs-lookup"><span data-stu-id="a6476-161">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="a6476-162">\<binding ></span><span class="sxs-lookup"><span data-stu-id="a6476-162">\<binding></span></span>](bindings.md)
